---
description: 다음에 대해 자세히 알아보세요. <exposedMethod>
title: <exposedMethod>
ms.date: 03/30/2017
ms.assetid: 61c938cd-4ee9-4b06-ab28-922ef491ab11
ms.openlocfilehash: 7bf271ba03ee16c6a45726e2bcb522bf6f55d441
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664732"
---
# \<exposedMethod>

COM+ 구성 요소의 인터페이스가 웹 서비스로 노출될 때 노출되는 COM+ 메서드를 나타냅니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<exposedMethods>**](exposedmethods.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<exposedMethod>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<comContracts>
  <comContract>
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|name|COM+ 구성 요소의 인터페이스가 웹 서비스로 공개될 때 노출되는 COM+ 메서드를 포함하는 문자열입니다.|  
  
### <a name="child-elements"></a>자식 요소  

 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<exposedMethods>](exposedmethods.md)|[\<exposedMethod>](exposedmethod.md)요소의 컬렉션입니다.|  
  
## <a name="remarks"></a>설명  

 COM+ 통합 구성 도구(ComSvcConfig.exe)는 COM 인터페이스의 특정 메서드를 생성된 서비스 계약에 나타나도록 추가하는 데 사용할 수 있습니다.  
  
 예를 들어, 다음 명령을 사용하여 생성된 서비스 계약에 `IFinances`.Financial 구성 요소의 `ItemOrders` COM 인터페이스에 있는 명명된 메서드 3개를 추가할 수 있습니다.  
  
 `ComSvcConfig.exe /i /application:OnlineStore /contract:ItemOrders.Financial,IFinances.{TransferFunds,AddFunds,RemoveFunds} /hosting:complus`  
  
 또한 ComSvcConfig.exe를 실행 하면 앞에서 설명한 메서드를 요소로 나열 하는 다음 서비스 계약이 생성 됩니다 [\<exposedMethod>](exposedmethod.md) .  
  
```xml  
<comContract contractType="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"
             name="IFinances"
             namespace="http://contoso.com/services/financial">
  <exposedMethod name="TransferFunds"/>
  <exposedMethod name="AddFunds"/>
  <exposedMethod name="RemoveFunds"/>
</comContract>
```  
  
 서비스 초기화 시 런타임에서는 요소 목록에 포함 된 메서드만 반영 하 고 추가 하 여 서비스 계약을 생성 하려고 시도 [\<exposedMethod>](exposedmethod.md) 합니다. 서비스 계약에 포함되지 않은 모든 인터페이스 메서드에 대해서는 추적이 생성됩니다.  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Configuration.ComMethodElementCollection>
- <xref:System.ServiceModel.Configuration.ComMethodElement>
- [\<comContracts>](comcontracts.md)
- [COM + 응용 프로그램과 통합](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [방법: COM+ 서비스 설정 구성](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
