---
ms.openlocfilehash: 086dac69d085d070511fcfd5820bd2644ee4598e
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497953"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a>Marshal.SizeOf와 Marshal.PtrToStructure 오버로드가 동적 코드를 중단시킵니다.

#### <a name="details"></a>설명

.NET Framework 4.5.1부터 <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> 또는 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> 메서드에 동적으로 바인딩하면(예: Windows PowerShell, IronPython 또는 C# dynamic 키워드를 통해) 이러한 메서드의 새 오버로드가 추가되어 스크립팅 엔진에 모호하게 될 수 있으므로 <code>MethodInvocationExceptions</code>를 발생시킬 수 있습니다.

#### <a name="suggestion"></a>제안 해결 방법

사용해야 하는 오버로드를 명확히 표시하도록 스크립트를 업데이트합니다. 이것은 일반적으로 메서드의 형식 매개 변수를 <xref:System.Type>로 명시적 캐스팅하여 수행할 수 있습니다. 문제를 해결하는 예제와 자세한 정보는 [이 링크](https://support.microsoft.com/kb/2909958/)를 참조하십시오.

| 이름    | 값       |
|:--------|:------------|
| Scope   |부|
|버전|4.5.1|
|형식|런타임|

#### <a name="affected-apis"></a>영향을 받는 API

API 분석을 통해 검색할 수 없습니다.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
