---
title: .NET Framework 및 Windows OS 버전
description: 기본 CLR 버전 및 Windows 운영 체제에 설치된 버전을 포함하여 각 .NET Framework 버전의 주요 기능에 대해 알아봅니다.
ms.date: 01/17/2020
helpviewer_keywords:
- versions, .NET Framework
ms.assetid: f75a72de-e2f2-4a7a-9574-3f278684ea90
ms.openlocfilehash: f807a9d9a7ccebf2ae71d47e01fbfba7338b1799
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471999"
---
# <a name="net-framework-versions-and-dependencies"></a>.NET Framework 버전 및 종속성

.NET Framework의 각 버전에는 CLR(공용 언어 런타임), 기본 클래스 라이브러리 및 기타 관리되는 라이브러리가 포함되어 있습니다. 이 문서에서는 버전별 .NET Framework의 주요 기능에 대해 설명하고 기본 CLR 버전 및 관련 개발 환경에 대한 정보를 제공하며 Windows 운영 체제별로 설치된 버전을 확인합니다.

새 .NET Framework 버전은 각각 새 기능을 추가하지만 이전 버전의 기능을 유지합니다.

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

CLR은 고유한 버전 번호로 식별됩니다. .NET Framework 버전 번호는 각 릴리스마다 증가하지만 CLR 버전은 매번 증가하지는 않습니다. 예를 들어 .NET Framework 4, 4.5 및 이후 릴리스에는 CLR 4가 포함되지만 .NET Framework 2.0, 3.0 및 3.5에는 CLR 2.0이 포함됩니다. CLR 버전 3이 포함된 .NET Framework 버전은 없습니다.

> [!TIP]
>
> - 지원되는 운영 체제의 전체 목록은 [시스템 요구 사항](../get-started/system-requirements.md)을 참조하세요.
> - 다운로드에 대해서는 [개발자용 .NET Framework 설치](../install/guide-for-developers.md)를 참조하세요.
> - 컴퓨터에 설치된 .NET Framework 버전을 확인하는 방법에 대한 자세한 내용은 [방법: 설치된 .NET Framework 버전 확인](how-to-determine-which-versions-are-installed.md)을 참조하세요.

## <a name="version-information"></a>버전 정보

다음 표에는 .NET Framework 버전 기록이 요약되어 있으며 Visual Studio, Windows 및 Windows Server와의 상관 관계가 나와 있습니다. Visual Studio에서는 나열된 .NET Framework 버전으로 사용이 제한되지 않도록 멀티 타기팅을 지원합니다.

- 확인 표시 아이콘(✔️)은️ .NET Framework가 기본적으로 설치되어 있는 OS 버전을 나타냅니다.
- 더하기 기호 아이콘(➕)은 .NET Framework가 미리 설치되지 않았지만 설치할 수 있는 OS 버전을 나타냅니다.
- 별표 * *\** _은 사전 설치 여부와 관계없이 [제어판](../install/dotnet-35-windows-10.md)이나 서버 관리자(Windows Server의 경우)를 통해 .NET Framework를 사용하도록 설정해야 하는 OS 버전을 나타냅니다.

| | |
| - | - |
| [.NET Framework 4.8](#net-framework-48) | [.NET Framework 4.7.2](#net-framework-472) | [.NET Framework 4.7.1](#net-framework-471) | [.NET Framework 4.7](#net-framework-47) |
| [.NET Framework 4.6.2](#net-framework-462) | [.NET Framework 4.6.1](#net-framework-461) | [.NET Framework 4.6](#net-framework-46) | [.NET Framework 4.5.2](#net-framework-452) |
| [.NET Framework 4.5.1](#net-framework-451) | [.NET Framework 4.5](#net-framework-45) | [.NET Framework 4](#net-framework-4) | [.NET Framework 3.5](#net-framework-35) |
| [.NET Framework 3.0](#net-framework-30) | [.NET Framework 2.0](#net-framework-20) | [.NET Framework 1.1](#net-framework-11) | [.NET Framework 1.0](#net-framework-10) |

### <a name="net-framework-48"></a>.NET Framework 4.8

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-48)
- [내게 필요한 옵션의 새로운 기능](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-48)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net48/README.md)

|||
|-|-|
|_ *CLR 버전**|4|
|**Windows 버전**|✔️ 10 2019년 5월 업데이트<br/>➕ 10 2018년 10월 업데이트(버전 1809)<br/>➕ 10 2018년 4월 업데이트(버전 1803)<br/>➕ 10 Fall Creators Update(버전 1709)<br/>➕ 10 Creators Update(버전 1703)<br/>➕ 10 1주년 업데이트(버전 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server 버전**|➕ Windows Server 2019<br/>➕ Windows Server, 버전 1809<br/>➕ Windows Server, 버전 1803<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br/>- 528040(Windows 10 2019년 5월 업데이트)<br/>- 528049(다른 모든 OS 버전)<br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-472"></a>.NET Framework 4.7.2

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-472)
- [내게 필요한 옵션의 새로운 기능](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-472)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net472/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2019<sup>1</sup>|
|**Windows 버전**|✔️ 10 2018년 10월 업데이트(버전 1809)<br/>✔️ 10 2018년 4월 업데이트(버전 1803)<br/>➕ 10 Fall Creators Update(버전 1709)<br/>➕ 10 Creators Update(버전 1703)<br/>➕ 10 1주년 업데이트(버전 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server 버전**|✔️ Windows Server 2019<br/>✔️ Windows Server, 버전 1809<br/>✔️ Windows Server, 버전 1803<br/>➕ Windows Server, 버전 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br/>- 461814(Windows 10 2018년 10월 업데이트)<br/>- 461808(Windows 10 2018년 4월 업데이트 및 Windows Server, 버전 1803)<br/>- 461814(다른 모든 OS 버전)<br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

<sup>1</sup> **.NET 데스크톱 개발** , **ASP.NET 및 웹 개발** , **Azure 개발** , **Office/SharePoint 개발** , **.NET을 사용한 모바일 개발** 또는 **.NET Core 플랫폼 간 개발** 워크로드를 설치해야 합니다.

### <a name="net-framework-471"></a>.NET Framework 4.7.1

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-471)
- [내게 필요한 옵션의 새로운 기능](../whats-new/whats-new-in-accessibility.md#whats-new-in-accessibility-in-net-framework-471)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net471/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**Windows 버전**|✔️ 10 Fall Creators Update(버전 1709)<br/>➕ 10 Creators Update(버전 1703)<br/>➕ 10 1주년 업데이트(버전 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server 버전**|➕ Windows Server, 버전 1803<br/>✔️ Windows Server, 버전 1709<br/>➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br/>- 461308(Windows 10 Creators Update 및 Windows Server, 버전 1709)<br/>- 461310(다른 모든 OS 버전)<br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-47"></a>.NET Framework 4.7

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-47)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net47/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**Windows 버전**|✔️ 10 Creators Update(버전 1703)<br/>➕ 10 1주년 업데이트(버전 1607)<br/>➕ 8.1<br/>➕7|
|**Windows Server 버전**|➕ 2016<br/>➕ 2012 R2<br/>➕ 2012<br/>➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br/>- 460798(Windows 10 크리에이터 업데이트)<br/>- 460805(다른 모든 OS 버전)<br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-462"></a>.NET Framework 4.6.2

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-462)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net462/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**Windows 버전**|✔️ 10 1주년 업데이트(버전 1607)<br/>➕ 10 11월 업데이트(버전 1511)<br/>➕ 10<br/>➕ 8.1<br />➕ 7|
|**Windows Server 버전**|✔️ 2016<br /><br/>➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br /><br/>- 394802(Windows 10 1주년 업데이트 및 Windows Server 2016)<br/>- 394806(다른 모든 OS 버전)<br /><br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-461"></a>.NET Framework 4.6.1

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-461)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net461/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2017<sup>1</sup>|
|**Windows 버전**|✔️ 10 11월 업데이트(버전 1511)<br/>➕ 10<br />➕ 8.1<br />➕ 8<br />➕ 7|
|**Windows Server 버전**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br /><br/>- 394254(Windows 10 11월 업데이트)<br />- 394271(다른 모든 OS 버전)<br /><br/>([지침](how-to-determine-which-versions-are-installed.md) 참조)|

<sup>1</sup> **.NET 데스크톱 개발** , **ASP.NET 및 웹 개발** , **Azure 개발** , **Office/SharePoint 개발** , **.NET을 사용한 모바일 개발** 또는 **.NET Core 플랫폼 간 개발** 워크로드를 설치해야 합니다.

### <a name="net-framework-46"></a>.NET Framework 4.6

- [새로운 기능](../whats-new/index.md#whats-new-in-net-2015)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net46/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2015|
|**Windows 버전**|✔️ 10<br /><br />➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server 버전**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br /><br />- 393295(Windows 10)<br />- 393297(다른 모든 OS 버전)<br /><br />([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-452"></a>.NET Framework 4.5.2

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-452)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net452/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**Windows 버전**|➕ 8.1<br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server 버전**|➕ 2012 R2<br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 379893 사용<br /><br />([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-451"></a>.NET Framework 4.5.1

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-451)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net451/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2013|
|**Windows 버전**|✔️ 8.1<br /><br />➕ 8<br />➕ 7<br />➕ Vista|
|**Windows Server 버전**|✔️ 2012 R2<br /><br />➕ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 사용:<br /><br />- 378675(Windows 8.1)<br />- 378758(다른 모든 버전)<br /><br />([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-45"></a>.NET Framework 4.5

- [새로운 기능](../whats-new/index.md#whats-new-in-net-framework-45)
- [릴리스 정보](https://github.com/Microsoft/dotnet/tree/master/releases/net45/README.md)

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2012|
|**Windows 버전**|✔️ 8<br />➕ 7<br />➕ Vista|
|**Windows Server 버전**|✔️ 2012<br />➕ 2008 R2 SP1<br />➕ 2008 SP2|
|**설치된 .NET 버전 확인 방법**|`Release` DWORD 378389 사용<br /><br />([지침](how-to-determine-which-versions-are-installed.md) 참조)|

### <a name="net-framework-4"></a>.NET Framework 4

[새로운 기능](/previous-versions/dotnet/netframework-4.0/ms171868(v=vs.100))

|||
|-|-|
|**CLR 버전**|4|
|**포함된 Visual Studio 버전**|2010|
|**Windows 버전**|➕ 7<br />➕ Vista|
|**Windows Server 버전**|➕ 2008 R2 SP1<br />➕ 2008 SP2<br />➕ 2003|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md) 참조|

### <a name="net-framework-35"></a>.NET Framework 3.5

[새 기능](/previous-versions/visualstudio/visual-studio-2008/ms171868\(v=vs.90\)):

- LINQ
- 식 트리
- AJAX 개발을 위한 향상된 ASP.NET 지원
- HashSet 컬렉션
- DateTimeOffset
- WCF 및 WF 통합
- 피어 투 피어 네트워킹
- 확장성을 위한 추가 기능

|||
|-|-|
|**CLR 버전**|2.0|
|**포함된 Visual Studio 버전**|2008|
|**Windows 버전**|✔️ 10\*<br/>✔️ 8.1\*<br />✔️ 8\*<br />✔️ 7<br /><br />➕ Vista|
|**Windows Server 버전**|➕ Windows Server, 버전 1803\*<br/>➕ Windows Server, 버전 1709\*<br/>➕ 2016\*<br/>➕ 2012 R2\*<br />➕ 2012\*<br /><br />✔️2008 R2 SP1\*<br /><br/>➕ 2008 SP2<br />➕ 2003|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md) 참조|

### <a name="net-framework-30"></a>.NET Framework 3.0

[새 기능](/previous-versions/visualstudio/visual-studio-2008/bb822048(v=vs.90)):

- Windows Presentation Foundation
- Windows Communication Foundation
- Windows Workflow Foundation
- Windows CardSpace

|||
|-|-|
|**CLR 버전**|2.0|
|**Windows 버전**|✔️ Vista|
|**Windows Server 버전**|✔️ 2008 R2 SP1*<br />✔️ 2008 SP2\*<br /><br />➕ 2003|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md)을 참조하세요.|

### <a name="net-framework-20"></a>.NET Framework 2.0

[새 기능](/previous-versions/visualstudio/visual-studio-2008/t357fb32(v=vs.90)):

- 제네릭
- 디버거 편집하며 계속하기
- 향상된 확장성 및 성능
- ClickOnce 배포
- ASP.NET 2.0에서 광범위한 브라우저에 대한 새로운 컨트롤 및 지원
- 64비트 지원

|||
|-|-|
|**CLR 버전**|2.0|
|**포함된 Visual Studio 버전**|2005|
|**Windows 버전**|N/A|
|**Windows Server 버전**|✔️ 2008 R2 SP1<br />✔️ 2008 SP2<br />✔️ 2003|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md) 참조|

### <a name="net-framework-11"></a>.NET Framework 1.1

[새 기능](/previous-versions/visualstudio/visual-studio-2008/h88tthh0(v=vs.90)):

- ASP.NET 모바일 컨트롤
- Side-by-Side 실행
- IPv6 지원

|||
|-|-|
|**CLR 버전**|1.1|
|**포함된 Visual Studio 버전**|2003|
|**Windows 버전**|N/A|
|**Windows Server 버전**|✔️ 2003|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md) 참조|

### <a name="net-framework-10"></a>.NET Framework 1.0

|||
|-|-|
|**CLR 버전**|1.0|
|**포함된 Visual Studio 버전**|Visual Studio .NET|
|**Windows 버전**|N/A|
|**Windows Server 버전**|N/A|
|**설치된 .NET 버전 확인 방법**|[지침](how-to-determine-which-versions-are-installed.md) 참조|

> [!NOTE]
>
> - [제어판(Windows) 또는 서버 관리자(Windows Server)](../install/dotnet-35-windows-10.md#enable-the-net-framework-35-in-control-panel)를 통해 이 운영 체제에서 .NET Framework를 사용하도록 설정해야 합니다.
> - 사용 중인 애플리케이션이 특정 버전에 종속적일 수 있고 해당 버전 제거 시 애플리케이션이 중단될 수 있으므로 컴퓨터에 설치된 .NET Framework의 모든 버전은 일반적으로 제거하면 안 됩니다. 여러 버전의 .NET Framework를 단일 컴퓨터에서 동시에 로드할 수 있습니다. 즉, 이전 버전을 제거하지 않고도 .NET Framework를 설치할 수 있습니다. 자세한 내용은 [시작](../get-started/index.md)을 참조하십시오.

## <a name="remarks-for-version-45-and-later"></a>버전 4.5 이상에 대한 설명

.NET Framework 4.5는 컴퓨터에서 .NET Framework 4를 대체하는 현재 위치 업데이트이고, 마찬가지로 .NET Framework 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 및 4.8은 .NET Framework 4.5의 현재 위치 업데이트입니다. 현재 위치 업데이트는 동일한 런타임 버전을 사용하지만 어셈블리 버전이 업데이트되고 새 형식과 멤버가 포함된다는 의미입니다. 이러한 업데이트 중 하나를 설치한 후 .NET Framework 4, .NET Framework 4.5, .NET Framework 4.6 또는 .NET Framework 4.7용 앱은 다시 컴파일하지 않고도 계속 실행되어야 합니다. 하지만 그 반대의 경우는 성립되지 않습니다. 이전 버전의 .NET Framework에서 이후 버전의 .NET Framework를 대상으로 하는 앱을 실행하지 않는 것이 좋습니다. 예를 들어 .NET Framework 4.5에서 .NET Framework 4.6을 대상으로 하는 앱을 실행하지 않는 것이 좋습니다.

다음과 같은 지침이 적용됩니다.

- Visual Studio에서는 프로젝트에 대한 대상 프레임워크로 .NET Framework 4.5를 선택(<xref:Microsoft.Build.Tasks.GetReferenceAssemblyPaths.TargetFrameworkMoniker%2A?displayProperty=nameWithType> 속성을 설정)하여 .NET Framework 4.5 어셈블리 또는 실행 파일로 프로젝트를 컴파일할 수 있습니다. 이 어셈블리 또는 실행 파일은 .NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 또는 4.8이 설치된 모든 컴퓨터에서 사용할 수 있습니다.

- Visual Studio에서는 프로젝트에 대한 대상 프레임워크로 .NET Framework 4.5.1을 선택하여 .NET Framework 4.5.1 어셈블리 또는 실행 파일로 프로젝트를 컴파일할 수 있습니다. .NET Framework 4.5.1 이상이 설치된 컴퓨터에서 이 어셈블리 또는 실행 파일만을 실행합니다. .NET Framework 4.5.1을 대상으로 하는 실행 파일은 .NET Framework 4.5와 같은 이전 버전의 .NET Framework만 설치된 컴퓨터에서 실행되는 것이 차단됩니다. .NET Framework 4.5.1을 설치하라는 메시지가 표시됩니다. 또한 .NET Framework 4.5 같은 이전 버전의 .NET Framework를 대상으로 하는 앱에서 .NET Framework 4.5.1 어셈블리를 호출하지 않아야 합니다.

  > [!NOTE]
  > 여기서의 .NET framework 4.5.1 및.NET Framework 4.5는 예제로만 사용되었습니다. 설명된 원칙은 실행 중인 시스템에 설치된 것보다 이후 버전의 .NET Framework를 대상으로 하는 모든 앱에 적용됩니다.

.NET Framework의 일부 변경 내용으로 인해 앱 코드를 변경해야 할 수 있습니다. .NET Framework 4.5 이상 버전에서 기존 앱을 실행하기 전에 [애플리케이션 호환성](application-compatibility.md)을 참조하세요. 현재 버전 설치에 대한 자세한 내용은 [개발자용 .NET Framework 설치](../install/guide-for-developers.md)를 참조하세요. .NET Framework 지원의 자세한 내용은 .NET 웹 사이트에서 [.NET Framework 공식 지원 정책](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)을 참조하세요.

## <a name="remarks-for-older-versions"></a>이전 버전에 대한 설명

.NET Framework 버전 2.0, 3.0 및 3.5는 동일한 버전의 CLR(CLR 2.0)로 빌드됩니다. 이러한 버전은 단일 설치의 후속 레이어를 나타냅니다. 각 버전은 이전 버전 위에 증분 방식으로 빌드됩니다. 컴퓨터에서 버전 2.0, 3.0 및 3.5를 병렬 실행할 수는 없습니다. 버전 3.5를 설치하면 2.0 및 3.0 레이어가 자동으로 설치되며 버전 2.0, 3.0 및 3.5용으로 빌드된 앱 모두를 3.5 버전에서 실행할 수 있습니다. 그러나 .NET Framework 4에서는 이 계층적 접근 방법을 종료하고 이후 릴리스(.NET Framework 4.5, 4.5.1, 4.5.2, 4.6, 4.6.1, 4.6.2, 4.7, 4.7.1, 4.7.2 및 4.8)에서도 단일 설치의 후속 레이어를 나타냅니다. .NET Framework 4부터는 프로세스 내 병렬 호스팅을 사용하여 단일 프로세스에서 여러 버전의 CLR을 실행할 수 있습니다. 자세한 내용은 [어셈블리 및 Side-by-Side 실행](../../standard/assembly/side-by-side-execution.md)을 참조하십시오.

또한 앱이 버전 2.0, 3.0 또는 3.5를 대상으로 하는 경우 사용자는 앱을 실행하기 전에 Windows 8, Windows 8.1 또는 Windows 10 컴퓨터에서 .NET Framework 3.5를 사용하도록 설정해야 합니다. 자세한 내용은 [Windows 10, Windows 8.1 및 Windows 8에 .NET Framework 3.5 설치](../install/dotnet-35-windows-10.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- .NET Framework를 처음 사용하는 경우 [개요](../get-started/overview.md)에서 주요 개념 및 기능에 대한 소개를 참조하십시오.

- .NET Framework 4.5 및 해당 포인트 릴리스의 새로운 기능과 개선 사항을 확인하려면 [.NET Framework의 새로운 기능](../whats-new/index.md)을 참조하세요.

- 앱을 새로운 버전의 NET Framework로 마이그레이션하는 방법에 대한 자세한 내용은 [마이그레이션 가이드](index.md)를 참조하세요.

- 컴퓨터에 설치된 버전 또는 업데이트 확인에 대한 자세한 내용은 [방법: 설치된 .NET Framework 버전 확인](how-to-determine-which-versions-are-installed.md) 및 [방법: 설치된 .NET Framework 업데이트 확인](how-to-determine-which-net-framework-updates-are-installed.md)을 참조하십시오.

## <a name="see-also"></a>참조

- [버전 호환성](version-compatibility.md)
| [.NET Framework 공식 지원 정책](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework)
- [차단된 .NET Framework 설치 및 제거 문제 해결](../install/troubleshoot-blocked-installations-and-uninstallations.md)
