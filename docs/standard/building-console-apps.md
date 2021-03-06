---
title: .NET에서 콘솔 애플리케이션 만들기
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, creating console applications
- application development [.NET], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: b9c38e1311379037695879565b33ade29c6bf632
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687550"
---
# <a name="console-apps-in-net"></a>.NET의 콘솔 앱

.NET 애플리케이션은 <xref:System.Console?displayProperty=nameWithType> 클래스를 사용하여 콘솔로부터 문자를 읽거나 콘솔에 문자를 쓸 수 있습니다. 콘솔의 데이터는 표준 입력 스트림에서 읽혀지고 표준 출력 스트림으로 쓰여지며, 콘솔의 오류 데이터는 표준 오류 출력 스트림으로 쓰여집니다. 이러한 스트림은 애플리케이션이 시작될 때 콘솔과 자동으로 연결되며 <xref:System.Console.In%2A>, <xref:System.Console.Out%2A> 및 <xref:System.Console.Error%2A> 속성으로 나타납니다.

<xref:System.Console.In%2A?displayProperty=nameWithType> 속성의 값은 <xref:System.IO.TextReader?displayProperty=nameWithType> 개체인 반면 <xref:System.Console.Out%2A?displayProperty=nameWithType> 및 <xref:System.Console.Error%2A?displayProperty=nameWithType> 속성의 값은 <xref:System.IO.TextWriter?displayProperty=nameWithType> 개체입니다. 콘솔을 나타내지 않는 스트림과 이들 속성을 연결하여 스트림이 서로 다른 입력 또는 출력 위치를 향하도록 할 수 있습니다. 예를 들어 <xref:System.Console.Out%2A?displayProperty=nameWithType> 속성을 <xref:System.IO.StreamWriter?displayProperty=nameWithType>로 설정하여 출력을 파일로 리디렉션할 수 있습니다. 이 속성 값은 <xref:System.IO.FileStream?displayProperty=nameWithType>을 <xref:System.Console.SetOut%2A?displayProperty=nameWithType> 메서드로 캡슐화합니다. <xref:System.Console.In%2A?displayProperty=nameWithType> 및 <xref:System.Console.Out%2A?displayProperty=nameWithType> 속성은 동일한 스트림을 참조할 필요가 없습니다.

> [!NOTE]
> C#, Visual Basic 및 C++의 예제를 비롯하여 콘솔 애플리케이션을 빌드하는 방법에 대한 자세한 내용은 <xref:System.Console> 클래스 설명서를 참조하세요.

예를 들어 Windows Forms 애플리케이션에 콘솔이 존재하지 않을 경우 정보를 쓸 콘솔이 없으므로 표준 출력 스트림에 쓰여지는 출력은 보이지 않습니다. 액세스할 수 없는 콘솔에 정보를 쓸 경우 예외가 발생하지 않습니다. 예를 들어 Visual Studio의 프로젝트 속성 페이지에서는 항상 애플리케이션 유형을 **콘솔 애플리케이션** 으로 변경할 수 있습니다.

**System.Console** 클래스에는 콘솔에서 개별 문자나 전체 줄을 읽을 수 있는 메서드가 있습니다. 다른 메서드는 데이터 및 형식 문자열을 변환한 다음 형식 지정된 문자열을 콘솔에 씁니다. 문자열 형식 지정에 관한 자세한 내용은 [형식 서식 지정](base-types/formatting-types.md)을 참조하세요.

> [!TIP]
> 콘솔 애플리케이션에는 기본적으로 시작되는 메시지 펌프가 없습니다. 따라서 Microsoft Win32 타이머에 대한 콘솔 호출이 실패할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- <xref:System.Console?displayProperty=nameWithType>
- [형식 서식 지정](base-types/formatting-types.md)
