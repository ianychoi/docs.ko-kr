---
description: 다음에 대해 자세히 알아보세요. <endpointDiscovery>
title: <endpointDiscovery>
ms.date: 03/30/2017
ms.assetid: 70812717-888a-4748-9640-0df6715ff029
ms.openlocfilehash: 01913de37ae426484d5bb1ff6a815a64302024fb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782132"
---
# \<endpointDiscovery>

검색 기능, 범위 및 해당 메타데이터에 대한 사용자 지정 확장 등 엔드포인트에 대한 다양한 검색 설정을 지정합니다.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointDiscovery>**  
  
## <a name="syntax"></a>구문  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enabled="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
        <extensions />
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  

 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|attribute|설명|  
|---------------|-----------------|  
|사용|이 끝점에서 검색 기능이 사용 되는지 여부를 지정 하는 부울 값입니다. 기본값은 `false`입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|엔드포인트에 대한 범위 URI의 컬렉션입니다. 단일 엔드포인트에 둘 이상의 범위 URI를 연결할 수 있습니다.|  
|[\<extensions>](extensions.md) [of \<endpointDiscovery> ]|엔드포인트에 대해 게시되는 사용자 지정 메타데이터를 지정할 수 있는 XML 요소의 컬렉션입니다.|  
|\<types>|검색할 인터페이스의 컬렉션입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|동작 요소를 지정합니다.|  
|||  
  
## <a name="remarks"></a>설명  

 엔드포인트의 동작 구성에 추가되고 `enabled` 특성이 `true`로 설정되면 이 구성 요소에 대한 검색 기능을 사용할 수 있습니다. 또한 자식 요소를 사용 하 여 [\<scopes>](scopes.md) 쿼리 중에 서비스 끝점을 필터링 하는 데 사용할 수 있는 사용자 지정 범위 uri를 지정 하 고, [\<extensions>](extensions.md) 표준 검색 가능 메타 데이터 (EPR, ContractTypeName, Bindingname, Scope 및 ListenURI)와 함께 게시 되어야 하는 사용자 지정 메타 데이터를 지정할 수 있습니다.  
  
 이 구성 요소는 검색 기능에 [\<serviceDiscovery>](servicediscovery.md) 대 한 서비스 수준 제어를 제공 하는 요소에 종속 됩니다. 즉, 구성에가 없는 경우에는이 요소의 설정이 무시 됩니다 [\<serviceDiscovery>](servicediscovery.md) .  
  
## <a name="example"></a>예제  

 다음 구성 예제에서는 필터링 범위 및 엔드포인트에 게시되는 확장 메타데이터를 지정합니다.  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService"
              behaviorConfiguration="calculatorEndpointBehavior" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDiscovery />
    </behavior>
  </serviceBehaviors>
  <endpointBehaviors>
    <behavior name="calculatorEndpointBehavior">
      <endpointDiscovery enabled="true">
        <scopes>
          <add scope="http://contoso/test1" />
          <add scope="http://contoso/test2" />
        </scopes>
        <extensions>
          <e:Publisher xmlns:e="http://example.org">
            <e:Name>The Example Organization</e:Name>
            <e:Address>One Example Way, ExampleTown, EX 12345</e:Address>
            <e:Contact>support@example.org</e:Contact>
          </e:Publisher>
          <AnotherCustomMetadata>Custom Metadata</AnotherCustomMetadata>
        </extensions>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
