---
title: <serviceBehaviors>의 <behavior>
ms.date: 03/30/2017
ms.assetid: 78fc0a08-55de-416a-ac12-a5e6ffc9a987
ms.openlocfilehash: 739f95f527fd73062c8cec43efc6777efeb077f3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195157"
---
# <a name="behavior-of-servicebehaviors"></a>\<serviceBehaviors>의 \<behavior>

`behavior` 요소는 서비스의 동작에 대한 설정 컬렉션을 포함합니다. 각 동작은 해당 `name`으로 인덱싱됩니다. 서비스는 요소의 특성을 사용 하 여이 이름을 통해 각 동작에 연결할 수 있습니다 `behaviorConfiguration` [\<endpoint>](endpoint-element.md) . 따라서 설정을 다시 정의하지 않고도 엔드포인트에서 일반 동작 구성을 공유할 수 있습니다. .NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다. 기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.  
  
> [!NOTE]
> 요소와 같은 Windows 워크플로 작업과 관련 된 동작 요소 [\<sendMessageChannelCache>](../windows-workflow-foundation/sendmessagechannelcache.md) 는 페이지 [ \<behavior> 의 \<serviceBehaviors> ](../windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md) 에 설명 되어 있습니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <serviceBehaviors>
       <behavior name="String" />
    </serviceBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|Description|  
|---------------|-----------------|  
|name|동작의 구성 이름을 포함하는 고유 문자열입니다. 이 값은 요소의 식별 문자열 역할을 하므로 고유한 사용자 정의 문자열이어야 합니다. .NET Framework 4부터 바인딩과 동작은 이름을 가질 필요가 없습니다. 기본 구성 및 이름이 없는 바인딩 및 동작에 대 한 자세한 내용은 [WCF 서비스에 대 한](../../../wcf/samples/simplified-configuration-for-wcf-services.md) [간소화 된 구성](../../../wcf/simplified-configuration.md) 및 단순화 된 구성을 참조 하세요.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-element.md)|DataContractSerializer에 대한 구성 데이터가 들어 있습니다.|  
|[\<persistenceProvider>](persistenceprovider.md)|사용할 지속성 공급자 구현 형식 및 지속성 작업에 사용할 제한 시간을 지정합니다.|  
|[\<routing>](routing-of-servicebehavior.md)|라우팅 서비스에 대한 런타임 액세스를 제공하여 라우팅 구성의 동적 수정을 허용합니다.|  
|[\<serviceAuthenticationManager>](serviceauthenticationmanager.md)|서비스 수준에서 전송, 메시지 또는 송신자의 유효성을 설정하는 워크플로 구성 요소를 제공합니다.|  
|[\<serviceAuthorization>](serviceauthorization-element.md)|서비스 작업에 대한 액세스 권한을 부여하는 설정을 지정합니다.|  
|[\<serviceCredentials>](servicecredentials.md)|서비스를 인증하는 데 사용되는 자격 증명 및 클라이언트 자격 증명 유효성 검사 관련 설정을 지정합니다.|  
|[\<serviceDebug>](servicedebug.md)|WCF (Windows Communication Foundation) 서비스에 대 한 디버깅 및 도움말 정보 기능을 지정 합니다.|  
|[\<serviceDiscovery>](servicediscovery.md)|서비스 엔드포인트의 검색 기능을 지정합니다.|  
|[\<serviceMetadata>](servicemetadata.md)|서비스 메타데이터 및 관련 정보의 게시를 지정합니다.|  
|[\<serviceSecurityAudit>](servicesecurityaudit.md)|서비스 작업 중에 보안 이벤트의 감사를 사용하도록 하는 설정을 지정합니다.|  
|[\<serviceThrottling>](servicethrottling.md)|WCF 서비스의 제한 메커니즘을 지정 합니다.|  
|[\<serviceTimeouts>](servicetimeouts.md)|서비스에 대한 제한 시간을 지정합니다.|  
|[\<workflowRuntime>](workflowruntime.md)|워크플로 기반 WCF 서비스를 호스팅하기 위한 WorkflowRuntime의 인스턴스에 대 한 설정을 지정 합니다.|  
|[\<useRequestHeadersForMetadataAddress>](userequestheadersformetadataaddress.md)|요청 메시지 헤더에서 메타데이터 주소 정보를 검색할 수 있도록 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors.md)|서비스 동작 요소의 컬렉션입니다.|
