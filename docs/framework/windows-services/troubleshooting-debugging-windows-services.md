---
title: '문제 해결: Windows 서비스 디버깅'
description: Windows 서비스에서 디버깅을 시작합니다. Windows 서비스 애플리케이션을 디버그할 때 서비스와 Windows 서비스 관리자가 상호 작용합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- troubleshooting service applications
- services, troubleshooting
- troubleshooting debugging, Windows Services
- Windows Service applications, debugging
- services, debugging
- Windows Service applications, troubleshooting
ms.assetid: cf859d4c-f04c-4cb7-81e3-bc7de8bea190
ms.openlocfilehash: 5846692fa0d90a62dd569253abbd81aa63b5798d
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91608896"
---
# <a name="troubleshooting-debugging-windows-services"></a>문제 해결: Windows 서비스 디버깅
Windows 서비스 애플리케이션을 디버그할 때 서비스와 **Windows 서비스 관리자**가 상호 작용합니다. **서비스 관리자**는 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 메서드를 호출하여 서비스를 시작한 다음, <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 메서드가 반환될 때까지 30초 기다립니다. 이 시간 이내에 메서드가 반환되지 않으면 관리자는 서비스를 시작할 수 없다는 오류를 표시합니다.  
  
 [방법: Windows 서비스 애플리케이션 디버깅](how-to-debug-windows-service-applications.md)에 설명된 대로 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 메서드를 디버그할 때는 이 30초 기간에 유의해야 합니다. <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 메서드에 중단점을 배치하고 메서드를 30초 이내에 단계별로 실행하지 못하면 관리자가 서비스를 시작하지 않습니다.  
  
## <a name="see-also"></a>참조

- [방법: Windows 서비스 애플리케이션 디버그](how-to-debug-windows-service-applications.md)
- [Windows 서비스 애플리케이션 소개](introduction-to-windows-service-applications.md)
