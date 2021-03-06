---
title: 기본 클래스 라이브러리 호환성이 손상되는 변경
description: 핵심 .NET 라이브러리의 호환성이 손상되는 변경을 나열합니다.
ms.date: 07/27/2020
ms.openlocfilehash: 900fd4e0e071f19aa286dec84632006870822f26
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434920"
---
# <a name="core-net-libraries-breaking-changes"></a>핵심 .NET 라이브러리의 호환성이 손상되는 변경

핵심 .NET 라이브러리는 .NET Core에서 사용되는 기본 형식과 기타 일반 형식을 제공합니다.

이 페이지에는 다음과 같은 주요 변경 사항이 설명되어 있습니다.

| 주요 변경 내용 | 도입된 버전 |
| - | :-: |
| [전역 어셈블리 캐시 API가 사용되지 않음](#global-assembly-cache-apis-are-obsolete) | 5.0 |
| [원격 API가 사용되지 않음](#remoting-apis-are-obsolete) | 5.0 |
| [대부분의 코드 액세스 보안 API가 사용되지 않음](#most-code-access-security-apis-are-obsolete) | 5.0 |
| [기본이 아닌 진단 ID를 사용하는 API 사용되지 않음](#api-obsoletions-with-non-default-diagnostic-ids) | 5.0 |
| [FrameworkDescription의 값은 .NET Core가 아닌 .NET입니다.](#frameworkdescriptions-value-is-net-instead-of-net-core) | 5.0 |
| [단일 파일 게시 형식에 대한 어셈블리 관련 API 동작 변경](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | 5.0 |
| [Activity.Tags의 태그 순서가 반대로 표시됨](#order-of-tags-in-activitytags-is-reversed) | 5.0 |
| [RC1에서 매개 변수 이름이 변경됨](#parameter-names-changed-in-rc1) | 5.0 |
| [OSPlatform 특성이 제거되었거나 특성 이름이 바뀜](#osplatform-attributes-renamed-or-removed) | 5.0 |
| [Thread.Abort는 사용되지 않음](#threadabort-is-obsolete) | 5.0 |
| [ConsoleLoggerOptions에서 사용되지 않는 속성](#obsolete-properties-on-consoleloggeroptions) | 5.0 |
| [중첩 형식의 경우 하드웨어 내장 IsSupported 검사가 다를 수 있음](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | 5.0 |
| [참조 어셈블리의 매개 변수 이름 변경됨](#parameter-names-changed-in-reference-assemblies) | 5.0 |
| [Unix에서 비ASCII 문자를 포함하는 URI 경로가 올바르게 구문 분석됨](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | 5.0 |
| [Unix에서 UNC 경로의 URI 인식](#uri-recognition-of-unc-paths-on-unix) | 5.0 |
| [Environment.OSVersion에서 올바른 운영 체제 버전이 반환됨](#environmentosversion-returns-the-correct-operating-system-version) | 5.0 |
| [LINQ OrderBy.First{OrDefault}의 복잡성이 증가함](#complexity-of-linq-orderbyfirstordefault-increased) | 5.0 |
| [IntPtr 및 UIntPtr에서 IFormattable 구현](#intptr-and-uintptr-implement-iformattable) | 5.0 |
| [PrincipalPermissionAttribute는 오류로 인해 사용되지 않습니다.](#principalpermissionattribute-is-obsolete-as-error) | 5.0 |
| [ASP.NET 앱에서 BinaryFormatter serialization 메서드가 사용되지 않고 금지됨](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | 5.0 |
| [UTF-7 코드 경로가 사용되지 않음](#utf-7-code-paths-are-obsolete) | 5.0 |
| [Vector\<T>가 지원되지 않는 형식에 대해 항상 NotSupportedException을 throw](#vectort-always-throws-notsupportedexception-for-unsupported-types) | 5.0 |
| [기본 ActivityIdFormat이 W3C임](#default-activityidformat-is-w3c) | 5.0 |
| [Vector2.Lerp 및 Vector4.Lerp의 동작 변경](#behavior-change-for-vector2lerp-and-vector4lerp) | 5.0 |
| [SSE 및 SSE2 CompareGreaterThan 메서드가 NaN 입력을 올바르게 처리함](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | 5.0 |
| [CounterSet.CreateCounterSetInstance는 인스턴스가 이미 있는 경우 이제 InvalidOperationException을 throw함](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | 5.0 |
| [Microsoft.DotNet.PlatformAbstractions 패키지가 제거됨](#microsoftdotnetplatformabstractions-package-removed) | 5.0 |
| [버전을 보고하는 API가 이제 파일 버전이 아닌 제품 버전을 보고함](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [사용자 지정 EncoderFallbackBuffer 인스턴스는 재귀적으로 대체될 수 없음](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [부동 소수점 서식 및 구문 분석 동작 변경](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [부동 소수점 구문 분석 작업은 더 이상 실패하거나 OverflowException을 throw하지 않음](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException이 다른 어셈블리로 이동됨](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [잘못된 형식의 UTF-8바이트 시퀀스 교체는 유니코드 지침을 따름](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | 3.0 |
| [TypeDescriptionProviderAttribute가 다른 어셈블리로 이동됨](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry가 더 이상 일치하지 않는 항목 크기의 아카이브를 처리하지 않음](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [FieldInfo.SetValue가 초기화 전용 정적 필드에 대해 예외를 throw](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [기본 제공 구조체 형식에 추가된 프라이빗 필드](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [UseShellExecute의 기본값 변경](#change-in-default-value-of-useshellexecute) | 2.1 |
| [macOS의 OpenSSL 버전](#openssl-versions-on-macos) | 2.1 |
| [FileSystemInfo.Attributes가 throw하는 UnauthorizedAccessException](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |
| [손상된 프로세스 상태 예외 처리는 지원되지 않음](#handling-corrupted-state-exceptions-is-not-supported) | 1.0 |
| [UriBuilder 속성은 더 이상 앞에 선행 문자를 추가하지 않음](#uribuilder-properties-no-longer-prepend-leading-characters) | 1.0 |
| [Process.StartInfo는 코드가 시작하지 않은 프로세스에 대해 InvalidOperationException을 throw함](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | 1.0 |

## <a name="net-50"></a>.NET 5.0

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

***

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

**_

[!INCLUDE [code-access-security-apis-obsolete](../../../includes/core-changes/corefx/5.0/code-access-security-apis-obsolete.md)]

_*_

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

_*_

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

_*_

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

_*_

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

_*_

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

_*_

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

_*_

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

_*_

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

_*_

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

_*_

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

_*_

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

_*_

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

_*_

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

_*_

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

_*_

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

_*_

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

_*_

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

_*_

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

_*_

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

_*_

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

_*_

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

_*_

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

_**
