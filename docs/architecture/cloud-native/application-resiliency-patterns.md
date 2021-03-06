---
title: 애플리케이션 복원력 패턴
description: Azure 용 클라우드 네이티브 .NET 앱 설계 | 응용 프로그램 복원 력 패턴
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: e81d6e1d6b95cf0053de3ba557068ff458a59dc9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161154"
---
# <a name="application-resiliency-patterns"></a>애플리케이션 복원력 패턴

첫 번째 방어 줄은 응용 프로그램 복원 력입니다.

사용자 고유의 복원 력 프레임 워크를 작성 하는 데 상당한 시간을 투자할 수 있지만 이러한 제품은 이미 존재 합니다. [이는 개발자가 흐름](http://www.thepollyproject.org/) 및 스레드로부터 안전한 방식으로 복원 력을 표현할 수 있도록 하는 포괄적인 .net 복원 력 및 일시적인 오류 처리 라이브러리입니다. 응용 프로그램은 .NET Framework 또는 .NET Core를 사용 하 여 빌드된 응용 프로그램을 대상으로 합니다. 다음 표에서는 기능을 제공 하는 `policies` 라이브러리에서 사용할 수 있는 복원 력 기능에 대해 설명 합니다. 개별적으로 적용 하거나 그룹화 할 수 있습니다.

| 정책 | 환경 |
| :-------- | :-------- |
| 재시도 | 지정 된 작업에 대 한 재시도 작업을 구성 합니다. |
| 회로 차단기 | 오류가 구성 된 임계값을 초과 하는 경우 미리 정의 된 기간 동안 요청 된 작업을 차단 합니다. |
| 제한 시간 | 호출자가 응답을 기다릴 수 있는 기간에 제한을 배치 합니다. |
| 격벽 | 리소스를 swamping 하는 실패 한 호출을 방지 하기 위해 작업을 고정 크기 리소스 풀로 제한 합니다. |
| 캐시 | 응답을 자동으로 저장 합니다. |
| 대체 | 실패 시 구조화 된 동작을 정의 합니다. |

이전 그림에서 복원 력 정책은 외부 클라이언트나 백 엔드 서비스에서 들어오는 요청 메시지에 적용 됩니다. 목표는 일시적으로 사용할 수 없는 서비스에 대 한 요청을 보정 하는 것입니다. 이러한 단기 중단은 일반적으로 다음 표에 나와 있는 HTTP 상태 코드를 사용 하 여 매니페스트 합니다.

| HTTP 상태 코드| 원인 |
| :-------- | :-------- |
| 404 | 찾을 수 없음 |
| 408 | 요청 시간 초과 |
| 429 | 요청이 너무 많음 (최대 제한 됨) |
| 502 | 나쁜 게이트웨이 |
| 503 | 서비스를 사용할 수 없음 |
| 504 | 게이트웨이 시간 제한 |

질문: 403-금지 된 HTTP 상태 코드를 다시 시도 하나요? 아니요. 여기에서 시스템이 제대로 작동 하지만 요청 된 작업을 수행할 수 있는 권한이 호출자에 게 알려 줍니다. 오류로 인해 발생 하는 작업만 다시 시도해 야 합니다.

1 장에서 권장 한 대로 클라우드 네이티브 응용 프로그램을 구성 하는 Microsoft 개발자는 .NET Core 플랫폼을 대상으로 해야 합니다. 버전 2.1에는 URL 기반 리소스와 상호 작용 하기 위한 HTTP 클라이언트 인스턴스를 만들기 위한 [Httpclientfactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore) 라이브러리가 도입 되었습니다. 원래 HTTPClient 클래스를 대체 하는 팩터리 클래스는 향상 된 많은 기능을 지원 하며, 그 중 하나는이 기능을 사용 하는 것 [이 좋습니다.](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md) 이를 통해 응용 프로그램 시작 클래스에서 복원 력 정책을 쉽게 정의 하 여 부분 오류 및 연결 문제를 처리할 수 있습니다.

다음으로 다시 시도 및 회로 차단기 패턴을 살펴보겠습니다.

### <a name="retry-pattern"></a>다시 시도 패턴

분산 클라우드 기본 환경에서 서비스 및 클라우드 리소스에 대 한 호출은 일시적 (단기) 오류로 인해 실패할 수 있습니다. 일반적으로 잠시 후에 자체적으로 해결 됩니다. 재시도 전략을 구현 하면 클라우드 네이티브 서비스에서 이러한 시나리오를 완화할 수 있습니다.

[다시 시도 패턴](/azure/architecture/patterns/retry) 을 사용 하면 서비스에서 실패 한 요청 작업 (구성 가능)을 지 수 많은 대기 시간으로 다시 시도할 수 있습니다. 그림 6-2에서는 다시 시도 하는 작업을 보여 줍니다.

![재시도 패턴 실행](./media/retry-pattern.png)

**그림 6-2**. 재시도 패턴 실행

위의 그림에서 재시도 패턴은 요청 작업에 대해 구현 되었습니다. 백오프 간격 (대기 시간)이 2 초에서 시작 하 여 실패 하기 전까지 최대 4 번의 재시도를 허용 하도록 구성 되며,이는 각 후속 시도에 대해 두 배가 됩니다.

- 첫 번째 호출이 실패 하 고 HTTP 상태 코드 500을 반환 합니다. 응용 프로그램은 2 초 동안 대기한 후 호출을 다시 시도 합니다.
- 두 번째 호출도 실패 하 고 HTTP 상태 코드 500을 반환 합니다. 이제 응용 프로그램은 백오프 간격을 4 초로 두 배로 증가 하 고 호출을 다시 시도 합니다.
- 마지막으로 세 번째 호출은 성공 합니다.
- 이 시나리오에서 재시도 작업은 호출을 실패 하기 전에 백오프 기간을 두 배로 하는 동시에 최대 4 번의 재시도를 시도 했습니다.
- 네 번째 다시 시도 시도가 실패 한 경우 문제를 정상적으로 처리 하기 위해 대체 정책이 호출 됩니다.

서비스 시간을 자체 수정할 수 있도록 호출을 다시 시도 하기 전에 백오프 기간을 늘려야 합니다. 백오프을 구현 하 여 적절 한 수정 시간을 허용 하는 것이 좋습니다. 즉, 재시도 마다 마침표를 두 배로 늘립니다.

## <a name="circuit-breaker-pattern"></a>회로 차단기 패턴

재시도 패턴은 부분 실패에 대 한 요청을 복구 하는 데 도움이 되지만, 해결 하는 데 시간이 더 오래 걸릴 수 있는 예기치 않은 이벤트로 인해 오류가 발생할 수 있는 경우가 있습니다. 이러한 오류의 심각도는 부분적 연결 손실에서부터 전체 서비스 오류에까지 이를 수 있습니다. 이러한 상황에서는 응용 프로그램이 성공할 가능성이 없는 작업을 계속 해 서 다시 시도 하는 것은 무의미 합니다.

과도 한 작업을 수행 하기 위해 응답성이 없는 서비스에 대 한 지속적인 재시도 작업을 실행 하면 메모리, 스레드 및 데이터베이스 연결과 같은 리소스를 지속적으로 사용 하 여 서비스를 제한 하 여 동일한 리소스를 사용 하는 시스템의 관련 되지 않은 부분에서 오류가 발생 하는 자체 서비스 거부 시나리오로 이동할 수 있습니다.

이러한 경우에는 작업이 즉시 실패 하 고 성공할 가능성이 있는 경우에만 서비스를 호출 하려고 시도 하는 것이 좋습니다.

[회로 차단기 패턴](/azure/architecture/patterns/circuit-breaker) 은 응용 프로그램이 실패할 가능성이 있는 작업을 반복적으로 실행 하는 것을 방지할 수 있습니다. 미리 정의 된 수의 실패 한 호출 후에는 서비스에 대 한 모든 트래픽을 차단 합니다. 정기적으로 평가판 호출을 통해 오류가 해결 되었는지 여부를 확인할 수 있습니다. 그림 6-3은 작동 중인 회로 차단기 패턴을 보여 줍니다.

![작동 중인 회로 차단기 패턴](./media/circuit-breaker-pattern.png)

**그림 6-3**. 작동 중인 회로 차단기 패턴

위의 그림에서 회로 차단기 패턴은 원래 재시도 패턴에 추가 되었습니다. 100 실패 한 후에는 회로 차단기가 열리고 더 이상 서비스에 대 한 호출을 허용 하지 않습니다. CheckCircuit 값 (30 초)은 라이브러리에서 한 요청이 서비스를 진행 하도록 허용 하는 빈도를 지정 합니다. 해당 호출이 성공 하면 회로가 닫히고 서비스는 다시 트래픽에 사용할 수 있습니다.

회로 차단기 패턴의 의도는 재시도 패턴과 *다르다는* 점에 유의 하세요. 재시도 패턴을 사용 하면 응용 프로그램이 성공 하다 고 가정 하에 작업을 다시 시도할 수 있습니다. 회로 차단기 패턴은 응용 프로그램이 실패할 가능성이 있는 작업을 수행할 수 없도록 합니다. 일반적으로 응용 프로그램은 회로 차단기를 통해 작업을 호출 하기 위해 재시도 패턴을 사용 하 여 이러한 두 가지 패턴을 *결합* 합니다.

## <a name="testing-for-resiliency"></a>복원력 테스트

단위 테스트, 통합 테스트 등을 실행 하 여 응용 프로그램 기능을 테스트 하는 것과 동일한 방식으로 복원 력 테스트를 수행할 수 없습니다. 그 대신, 간헐적으로 발생하는 오류 조건 하에서 엔드투엔드 워크로드가 수행되는 방식을 테스트해야 합니다. 예: 충돌 하는 프로세스, 만료 된 인증서로 오류 삽입, 종속 서비스를 사용할 수 없도록 설정 등 혼란 스러운 [원숭이](https://github.com/Netflix/chaosmonkey) 와 같은 프레임 워크는 이러한 비정상 테스트에 사용할 수 있습니다.

응용 프로그램 복원 력을 통해 문제가 있는 요청 된 작업을 처리 해야 합니다. 그러나이는 스토리의 절반에 불과합니다. 다음으로, Azure 클라우드에서 사용할 수 있는 복원 력 기능을 다룹니다.

>[!div class="step-by-step"]
>[이전](resiliency.md)
>[다음](infrastructure-resiliency-azure.md)
