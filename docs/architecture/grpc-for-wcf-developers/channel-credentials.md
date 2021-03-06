---
title: 채널 자격 증명 - WCF 개발자를 위한 gRPC
description: ASP.NET Core 3.0에서 gRPC 채널 자격 증명을 구현하고 사용하는 방법.
ms.date: 09/02/2019
ms.openlocfilehash: 9ebe0aecb517e4cc2fe280632c4ecb593da9871c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148207"
---
# <a name="channel-credentials"></a>채널 자격 증명

이름에서 알 수 있듯이 채널 자격 증명은 기본 gRPC 채널에 연결됩니다. 채널 자격 증명의 표준 형식은 클라이언트 인증서 인증을 사용합니다. 이 과정에서 클라이언트는 연결을 할 때 TLS 인증서를 제공하고 호출을 허용하기 전에 서버가 이를 확인합니다.

채널 자격 증명을 통화 자격 증명과 결합하여 gRPC 서비스에 대한 포괄적인 보안을 제공할 수 있습니다. 채널 자격 증명은 클라이언트 응용 프로그램이 서비스에 액세스할 수 있음을 증명하고 호출 자격 증명은 클라이언트 응용 프로그램을 사용하는 사람에 대한 정보를 제공합니다.

클라이언트 인증서 인증은 gRPC에서 작동하며 ASP.NET Core에서 작동하는 것과 동일합니다. 자세한 내용은 [ASP.NET 코어에서 인증서 인증 구성을](/aspnet/core/security/authentication/certauth)참조하십시오.

개발을 위해 자체 서명된 인증서를 사용할 수 있지만 프로덕션에서는 신뢰할 수 있는 기관에서 서명한 적절한 HTTPS 인증서를 사용해야 합니다.

## <a name="add-certificate-authentication-to-the-server"></a>서버에 인증서 인증 추가

호스트 수준(예: Kestrel 서버)과 ASP.NET 코어 파이프라인모두에서 인증서 인증을 구성합니다.

### <a name="configure-certificate-validation-on-kestrel"></a>케스트렐에서 인증서 유효성 검사 구성

Kestrel(ASP.NET 코어 HTTP 서버)을 구성하여 클라이언트 인증서를 요구하고 선택적으로 들어오는 연결을 수락하기 전에 제공된 인증서의 일부 유효성 검사를 수행할 수 있습니다. 에서가 `CreateWebHostBuilder` 아니라 `Program` 클래스의 메서드에서 이 `Startup`작업을 수행합니다.

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            var serverCert = ObtainServerCertificate();
            webBuilder.UseStartup<Startup>()
                .ConfigureKestrel(kestrelServerOptions => {
                    kestrelServerOptions.ConfigureHttpsDefaults(opt =>
                    {
                        opt.ClientCertificateMode = ClientCertificateMode.RequireCertificate;

                        // Verify that client certificate was issued by same CA as server certificate
                        opt.ClientCertificateValidation = (certificate, chain, errors) =>
                            certificate.Issuer == serverCert.Issuer;
                    });
                });
        });

```

이 `ClientCertificateMode.RequireCertificate` 설정을 사용하면 Kestrel이 클라이언트 인증서를 제공하지 않는 연결 요청을 즉시 거부하지만 이 설정 자체는 제공된 인증서의 유효성을 검사하지 않습니다. ASP.NET `ClientCertificateValidation` 코어 파이프라인이 연결되기 전에 Kestrel이 연결이 이루어지는 시점에서 클라이언트 인증서의 유효성을 검사할 수 있도록 콜백을 추가합니다. 이 경우 콜백은 서버 인증서와 동일한 인증 *기관에서* 발급되었는지 확인합니다.

### <a name="add-aspnet-core-certificate-authentication"></a>ASP.NET 핵심 인증서 인증 추가

[Microsoft.AspNetCore.Authentication.Certificate](https://www.nuget.org/packages/Microsoft.AspNetCore.Authentication.Certificate) NuGet 패키지는 인증서 인증을 제공합니다.

`ConfigureServices` 메서드에 인증서 인증 서비스를 추가하고 메서드의 ASP.NET Core 파이프라인에 `Configure` 인증 및 권한 부여를 추가합니다.

```csharp
public class Startup
{
    private readonly bool _isDevelopment;

    public Startup(IWebHostEnvironment env)
    {
        _isDevelopment = env.IsDevelopment();
    }

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddAuthentication(CertificateAuthenticationDefaults.AuthenticationScheme)
            .AddCertificate(options =>
            {
                if (_isDevelopment)
                {
                    // DO NOT DO THIS IN PRODUCTION!
                    options.RevocationMode = X509RevocationMode.NoCheck;
                }
            });
        services.AddAuthorization();
        services.AddGrpc();
    }

    public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
    {
        app.UseRouting();

        app.UseAuthentication();
        app.UseAuthorization();

        app.UseEndpoints(endpoints => { endpoints.MapGrpcService<GreeterService>(); });
    }
}
```

## <a name="provide-channel-credentials-in-the-client-application"></a>클라이언트 응용 프로그램에서 채널 자격 증명 제공

`Grpc.Net.Client` 패키지를 사용하면 연결에 사용되는 인스턴스에 <xref:System.Net.Http.HttpClient> 제공되는 인증서를 `GrpcChannel` 구성할 수 있습니다.

```csharp
class Program
{
    static async Task Main(string[] args)
    {
        // Assume path to a client .pfx file and password are passed from command line
        // On Windows this would probably be a reference to the Certificate Store
        var cert = new X509Certificate2(args[0], args[1]);

        var handler = new HttpClientHandler();
        handler.ClientCertificates.Add(cert);
        var httpClient = new HttpClient(handler);

        var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
        {
            HttpClient = httpClient
        });

        var grpc = new Greeter.GreeterClient(channel);
        var response = await grpc.SayHelloAsync(new HelloRequest { Name = "Bob" });
        System.Console.WriteLine(response.Message);
    }
}
```

## <a name="combine-channelcredentials-and-callcredentials"></a>채널 자격 증명 및 호출 자격 증명 결합

인증서 와 토큰 인증을 모두 사용하도록 서버를 구성할 수 있습니다. 이 작업을 수행하려면 인증서 변경 사항을 Kestrel 서버에 적용하고 ASP.NET 코어에서 JWT 베어러 미들웨어를 사용하십시오.

클라이언트와 `ChannelCredentials` `CallCredentials` 클라이언트 모두를 제공하려면 `ChannelCredentials.Create` 메서드를 사용하여 호출 자격 증명을 적용합니다. 인스턴스를 사용하여 <xref:System.Net.Http.HttpClient> 인증서 인증을 적용해야 합니다. 인수를 `SslCredentials` 생성자에게 전달하면 내부 클라이언트 코드에서 예외를 throw합니다. `SslCredentials` 매개 변수는 패키지와의 `Grpc.Net.Client` 호환성을 `Create` 유지하기 위해 패키지의 메서드에만 포함됩니다. `Grpc.Core`

```csharp
var handler = new HttpClientHandler();
handler.ClientCertificates.Add(cert);

var httpClient = new HttpClient(handler);

var callCredentials = CallCredentials.FromInterceptor(((context, metadata) =>
    {
        metadata.Add("Authorization", $"Bearer {_token}");
    }));

var channelCredentials = ChannelCredentials.Create(new SslCredentials(), callCredentials);

var channel = GrpcChannel.ForAddress("https://localhost:5001/", new GrpcChannelOptions
{
    HttpClient = httpClient,
    Credentials = channelCredentials
});

var grpc = new Portfolios.PortfoliosClient(channel);
```

> [!TIP]
> 인증서 인증 `ChannelCredentials.Create` 없이 클라이언트에 대 한 메서드를 사용할 수 있습니다. 이는 채널에서 이루어지는 모든 호출을 통해 토큰 자격 증명을 전달하는 유용한 방법입니다.

[인증서 인증이 추가된 FullStockTicker 샘플 gRPC 응용 프로그램의](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/FullStockTickerSample/grpc/FullStockTickerAuth/FullStockTicker) 버전은 GitHub에 있습니다.

>[!div class="step-by-step"]
>[이전](call-credentials.md)
>[다음](encryption.md)
