---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077594"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a>Blazor: JSObjectReference 및 JSInProcessObjectReference 형식을 internal로 변경함

ASP.NET Core 5.0 RC1에서 도입된 새로운 `Microsoft.JSInterop.JSObjectReference` 및 `Microsoft.JSInterop.JSInProcessObjectReference` 형식이 `internal`로 표시되었습니다.

#### <a name="version-introduced"></a>도입된 버전

5.0 RC2

#### <a name="old-behavior"></a>이전 동작

`JSObjectReference`는 `IJSRuntime`를 통해 JavaScript interop 호출에서 가져올 수 있습니다. 예를 들면 다음과 같습니다.

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a>새 동작

`JSObjectReference`는 [internal](../../../../docs/csharp/language-reference/keywords/internal.md) 액세스 한정자를 사용합니다. 대신 `public` `IJSObjectReference` 인터페이스를 사용해야 합니다. 예를 들면 다음과 같습니다.

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

`JSInProcessObjectReference` 또한 `internal`로 표시되었으며 `IJSInProcessObjectReference`로 대체되었습니다.

#### <a name="reason-for-change"></a>변경 이유

이 변경으로 인해 JavaScript interop 기능이 Blazor 내의 다른 패턴과 더 일관되게 적용됩니다. `IJSObjectReference`는 유사한 용도로 사용되고 유사한 메서드 및 확장을 포함한다는 점에서 `IJSRuntime`과 비슷합니다.

#### <a name="recommended-action"></a>권장 조치

`JSObjectReference` 및 `JSInProcessObjectReference` 항목을 각각 `IJSObjectReference` 및 `IJSInProcessObjectReference`로 바꿉니다.

#### <a name="category"></a>범주

ASP.NET Core

#### <a name="affected-apis"></a>영향을 받는 API

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
