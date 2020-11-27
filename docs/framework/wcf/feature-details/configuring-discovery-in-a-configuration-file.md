---
title: 구성 파일에서 검색 구성
ms.date: 03/30/2017
ms.assetid: b9884c11-8011-4763-bc2c-c526b80175d0
ms.openlocfilehash: 1ffd5cb2e884b6eeae292326cb0dc1586995ba38
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96284188"
---
# <a name="configuring-discovery-in-a-configuration-file"></a><span data-ttu-id="d4c9c-102">구성 파일에서 검색 구성</span><span class="sxs-lookup"><span data-stu-id="d4c9c-102">Configuring Discovery in a Configuration File</span></span>

<span data-ttu-id="d4c9c-103">검색에 사용되는 구성 설정에는 네 가지 기본 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-103">There are four major groups of configuration settings used in discovery.</span></span> <span data-ttu-id="d4c9c-104">이 항목에서는 각 그룹에 대해 간략하게 설명하고 이러한 그룹을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-104">This topic will briefly describe each and show examples of how to configure them.</span></span> <span data-ttu-id="d4c9c-105">아래에 나오는 각 단원은 각 영역에 대해 보다 자세히 설명하는 문서로 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-105">Following each section will be a link to more in-depth documentation about each area.</span></span>  
  
## <a name="behavior-configuration"></a><span data-ttu-id="d4c9c-106">동작 구성</span><span class="sxs-lookup"><span data-stu-id="d4c9c-106">Behavior Configuration</span></span>  

 <span data-ttu-id="d4c9c-107">검색에는 서비스 동작과 엔드포인트 동작이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-107">Discovery uses service behaviors and endpoint behaviors.</span></span> <span data-ttu-id="d4c9c-108"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>동작을 사용하면 모든 서비스의 엔드포인트를 검색하고 알림 엔드포인트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-108">The <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> behavior enables discovery for all of a service’s endpoints and allows you to specify announcement endpoints.</span></span>  <span data-ttu-id="d4c9c-109">다음 예제에서는 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>를 추가하고 알림 엔드포인트를 지정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-109">The following example shows how to add the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and specify an announcement endpoint.</span></span>  
  
```xml  
<behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
        </behavior>  
      </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="d4c9c-110">동작을 지정한 후에는 다음 샘플과 같이 <> 요소에서 해당 동작을 참조 `service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-110">Once you specify the behavior, reference it from a <`service`> element as shown in the following sample.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
         <!-- Application Endpoint -->  
         <endpoint address="endpoint0"  
                   binding="basicHttpBinding"  
                   contract="IHelloWorldService" />  
         <!-- Discovery Endpoints -->  
         <endpoint kind="udpDiscoveryEndpoint" />  
        </service>  
    </services>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d4c9c-111">서비스를 검색 가능하게 만들려면 검색 엔드포인트도 추가해야 합니다. 위의 예제에서는 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 표준 엔드포인트를 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-111">In order for a service to be discoverable, you must also add a discovery endpoint, the example above adds a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> standard endpoint.</span></span>  
  
 <span data-ttu-id="d4c9c-112">알림 끝점을 추가할 때는 다음 예제와 같이 <> 요소에 알림 수신기 서비스도 추가 해야 합니다 `services` .</span><span class="sxs-lookup"><span data-stu-id="d4c9c-112">When you add announcement endpoints you must also add an announcement listener service to the <`services`> element as shown in the following example.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService" behaviorConfiguration="helloWorldServiceBehavior">  
      <!-- Application Endpoint -->  
      <endpoint address="endpoint0"  
                binding="basicHttpBinding"  
                contract="IHelloWorldService" />  
      <!-- Discovery Endpoints -->  
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <!-- Announcement Listener Configuration -->  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>
```  
  
 <span data-ttu-id="d4c9c-113"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>동작은 특정 엔드포인트의 검색을 사용하거나 사용하지 않도록 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-113">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is used to enable or disable discovery of a specific endpoint.</span></span>  <span data-ttu-id="d4c9c-114">다음 예제에서는 하나는 검색이 가능하고 다른 하나는 검색이 가능하지 않은 두 개의 애플리케이션 엔드포인트가 있는 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-114">The following example configures a service with two application endpoints, one with discovery enabled and one with discovery disabled.</span></span> <span data-ttu-id="d4c9c-115">각 엔드포인트에는 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 동작이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-115">For each endpoint an <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior is added.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service name="HelloWorldService"  
               behaviorConfiguration="helloWorldServiceBehavior">  
  
        <!-- Application Endpoints -->  
        <endpoint address="endpoint0"  
                 binding="basicHttpBinding"  
                 contract="IHelloWorldService"
                 behaviorConfiguration="ep0Behavior" />  
  
        <endpoint address="endpoint1"  
                  binding="basicHttpBinding"  
                  contract="IHelloWorldService"  
                  behaviorConfiguration="ep1Behavior" />  
  
        <!-- Discovery Endpoints -->  
        <endpoint kind="udpDiscoveryEndpoint" />  
      </service>  
   </services>  
   <behaviors>  
      <serviceBehaviors>  
        <behavior name="helloWorldServiceBehavior">  
          <serviceDiscovery />  
        </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="ep0Behavior">  
          <endpointDiscovery enabled="true"/>  
        </behavior>  
        <behavior name="ep1Behavior">  
          <endpointDiscovery enabled="false"/>  
        </behavior>  
     </endpointBehaviors>  
   </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="d4c9c-116"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 동작을 사용하여 서비스에서 반환되는 엔드포인트 메타데이터에 사용자 지정 메타데이터를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-116">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add custom metadata to the endpoint metadata returned by the service.</span></span> <span data-ttu-id="d4c9c-117">다음 예제에 이 작업을 수행하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-117">The following example shows how to do this.</span></span>  
  
```xml  
<behavior name="ep4Behavior">  
   <endpointDiscovery enabled="true">  
      <extensions>  
         <CustomMetadata>This is custom metadata.</CustomMetadata>  
         <d:Types xmlns:d="http://schemas.xmlsoap.org/ws/2005/04/discovery" xmlns:i="http://printer.example.org/2003/imaging">i:PrintBasic</d:Types>  
         <CustomMetadata netsted="true">  
            <NestedMetadata>This is a nested custom metadata.</NestedMetadata>  
         </CustomMetadata>  
      </extensions>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="d4c9c-118"><xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> 동작을 사용하여 클라이언트에서 서비스를 검색하는 데 사용하는 범위와 형식을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-118">The <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> behavior can also be used to add scopes and types that clients use to search for services.</span></span> <span data-ttu-id="d4c9c-119">다음 예제에서는 클라이언트측 구성 파일에서 이 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-119">The following example shows how to do this in a client side configuration file.</span></span>  
  
```xml  
<behavior name="ep2Behavior">  
   <endpointDiscovery enabled="true">  
      <scopes>  
         <add scope="http://www.microsoft.com/building42/floor1"/>  
         <add scope="ldap:///ou=engineeringo=examplecomc=us"/>  
      </scopes>  
      <types>  
         <add name="test" namespace="http://example.microsoft.com/" />  
         <add name="additionalContract" namespace="http://example.microsoft.com/" />  
      </types>  
   </endpointDiscovery>  
</behavior>  
```  
  
 <span data-ttu-id="d4c9c-120">및에 대 한 자세한 내용은 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> [WCF 검색 개요](wcf-discovery-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-120">For more information about <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span>  
  
## <a name="binding-element-configuration"></a><span data-ttu-id="d4c9c-121">바인딩 요소 구성</span><span class="sxs-lookup"><span data-stu-id="d4c9c-121">Binding Element Configuration</span></span>  

 <span data-ttu-id="d4c9c-122">바인딩 요소 구성은 클라이언트측에서 가장 흥미로운 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-122">Binding element configuration is most interesting on the client side.</span></span> <span data-ttu-id="d4c9c-123">구성을 사용하면 WCF 클라이언트 애플리케이션에서 서비스를 검색하는 데 사용되는 찾기 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-123">You can use configuration to specify the find criteria used to discover services from a WCF client application.</span></span>  <span data-ttu-id="d4c9c-124">다음 예제에서는 <xref:System.ServiceModel.Discovery.DiscoveryClient> 채널을 사용하여 사용자 지정 바인딩을 만들고 형식과 범위가 포함된 찾기 조건을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-124">The following example creates a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClient> channel and specifies find criteria that includes a type and scope.</span></span> <span data-ttu-id="d4c9c-125">또한 이 예제에서는 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 및 <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 속성의 값도 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-125">In addition it specifies values for the <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> and <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> properties.</span></span>  
  
```xml  
<bindings>  
   <customBinding>  
      <!-- Binding Configuration for the Application Endpoint -->  
      <binding name="discoBindingConfiguration">  
         <discoveryClient>  
            <endpoint kind="discoveryEndpoint"  
                      address="http://localhost:8000/ConfigTest/Discovery"  
                      binding="customBinding"  
                      bindingConfiguration="httpSoap12WSAddressing10"/>  
            <findCriteria duration="00:00:10" maxResults="2">  
              <types>  
                <add name="IHelloWorldService"/>  
              </types>  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>
            </findCriteria>  
          </discoveryClient>  
          <textMessageEncoding messageVersion="Soap11"/>  
          <httpTransport />  
      </binding>
   </customBinding>
</bindings>  
```  
  
 <span data-ttu-id="d4c9c-126">이 사용자 지정 바인딩 구성은 다음과 같이 클라이언트 엔드포인트에서 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-126">This custom binding configuration must be referenced by a client endpoint:</span></span>  
  
```xml  
<client>  
      <endpoint address="http://schemas.microsoft.com/discovery/dynamic"  
                binding="customBinding"  
                bindingConfiguration="discoBindingConfiguration"  
                contract="IHelloWorldService" />  
</client>  
```  
  
 <span data-ttu-id="d4c9c-127">찾기 조건에 대 한 자세한 내용은 [검색 찾기 및 FindCriteria](discovery-find-and-findcriteria.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-127">For more information about find criteria see [Discovery Find and FindCriteria](discovery-find-and-findcriteria.md).</span></span> <span data-ttu-id="d4c9c-128">검색 및 바인딩 요소에 대 한 자세한 내용은 [WCF 검색 개요](wcf-discovery-overview.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-128">For more information about discovery and binding elements see, [WCF Discovery Overview](wcf-discovery-overview.md)</span></span>  
  
## <a name="standard-endpoint-configuration"></a><span data-ttu-id="d4c9c-129">표준 엔드포인트 구성</span><span class="sxs-lookup"><span data-stu-id="d4c9c-129">Standard Endpoint Configuration</span></span>  

 <span data-ttu-id="d4c9c-130">표준 엔드포인트는 하나 이상의 속성(주소, 바인딩 또는 계약)에 대한 기본값이나 변경할 수 없는 하나 이상의 속성 값이 있는 미리 정의된 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-130">Standard endpoints are predefined endpoints that have default values for one or more properties (address, binding, or contract) or one or more property values that cannot change.</span></span> <span data-ttu-id="d4c9c-131">.NET 4에는 세 개의 검색 관련 표준 엔드포인트인 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 및 <xref:System.ServiceModel.Discovery.DynamicEndpoint>가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-131">.NET 4 ships with 3 discovery related standard endpoints: <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>, and <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  <span data-ttu-id="d4c9c-132"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>는 UDP 멀티캐스트 바인딩을 통한 검색 작업에 대해 미리 구성된 표준 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-132">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="d4c9c-133"><xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>는 UDP 바인딩을 통해 알림 메시지를 보내기 위해 미리 구성된 표준 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-133">The <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> is a standard endpoint that is pre-configured to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="d4c9c-134"><xref:System.ServiceModel.Discovery.DynamicEndpoint>는 런타임에 동적으로 검색을 사용하여 검색된 서비스의 엔드포인트 주소를 찾는 데 사용되는 표준 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-134">The <xref:System.ServiceModel.Discovery.DynamicEndpoint> is a standard endpoint that uses discovery to find the endpoint address of a discovered service dynamically at runtime.</span></span>  <span data-ttu-id="d4c9c-135">표준 바인딩은 `endpoint` 추가할 표준 끝점의 형식을 지정 하는 kind 특성이 포함 된 <> 요소로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-135">Standard bindings are specified with an <`endpoint`> element that contains kind attribute that specified the type of standard endpoint to add.</span></span> <span data-ttu-id="d4c9c-136">다음 예제에서는 및를 추가 하는 방법을 보여 줍니다 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> .</span><span class="sxs-lookup"><span data-stu-id="d4c9c-136">The following example shows how to add a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" />  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" />  
   </service>  
</services>  
```  
  
 <span data-ttu-id="d4c9c-137">표준 끝점은 <> 요소에서 구성 됩니다 `standardEndpoints` .</span><span class="sxs-lookup"><span data-stu-id="d4c9c-137">Standard endpoints are configured in a <`standardEndpoints`> element.</span></span> <span data-ttu-id="d4c9c-138">다음 예제에서는 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 및 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-138">The following example shows how to configure the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> and the <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>.</span></span>  
  
```xml  
<standardEndpoints>  
      <udpAnnouncementEndpoint>  
        <standardEndpoint
            name="udpAnnouncementEndpointSettings"
            multicastAddress="soap.udp://239.255.255.250:3703"
            maxAnnouncementDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="1028"  
            maxPendingMessageCount="10"  
            maxMulticastRetransmitCount="3"  
            maxUnicastRetransmitCount="2"  
            socketReceiveBufferSize="131072"  
            timeToLive="2" />  
        </standardEndpoint>  
      </udpAnnouncementEndpoint>  
      <udpDiscoveryEndpoint>  
        <standardEndpoint  
            name="udpDiscoveryEndpointSettings"  
            multicastAddress="soap.udp://239.255.255.252:3704"  
            maxResponseDelay="00:00:00.800">  
          <transportSettings  
            duplicateMessageHistoryLength="2048"  
            maxPendingMessageCount="5"  
            maxReceivedMessageSize="8192"  
            maxBufferPoolSize="262144"/>  
        </standardEndpoint>  
      </udpDiscoveryEndpoint>
</standardEndpoints>
```  
  
 <span data-ttu-id="d4c9c-139">표준 끝점 구성을 추가 했으면 `endpoint` 다음 샘플과 같이 각 끝점에 대 한 <> 요소에서 구성을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-139">Once you’ve added the standard endpoint configuration, reference the configuration in the <`endpoint`> element for each endpoint as shown in the following sample.</span></span>  
  
```xml  
<services>  
   <service name="HelloWorldService">  
      <!-- ...  -->
      <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="udpDiscoveryEndpointSettings"/>  
   </service>  
   <service name="AnnouncementListener">  
      <endpoint kind="udpAnnouncementEndpoint" endpointConfiguration="udpAnnouncementEndpointSettings" >  
   </service>  
</services>  
```  
  
 <span data-ttu-id="d4c9c-140">검색에 사용되는 다른 표준 엔드포인트와 달리 <xref:System.ServiceModel.Discovery.DynamicEndpoint>에는 바인딩과 계약을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-140">Unlike the other standard endpoints used in discovery, you specify a binding and contract for <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span> <span data-ttu-id="d4c9c-141">다음 예제에서는 <xref:System.ServiceModel.Discovery.DynamicEndpoint>를 추가하고 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-141">The following example shows how to add and configure a <xref:System.ServiceModel.Discovery.DynamicEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <endpoint kind="dynamicEndpoint" binding="basicHttpBinding" contract="IHelloWorldService" endpointConfiguration="dynamicEndpointConfiguration" />  
    </client>
   <standardEndpoints>  
      <dynamicEndpoint>  
         <standardEndpoint name="dynamicEndpointConfiguration">  
             <discoveryClientSettings>  
              <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="2">  
                 <types>  
                   <add name="IHelloWorldService"/>  
                 </types>  
                 <scopes>  
                   <add scope="http://www.microsoft.com/building42/floor1"/>  
                 </scopes>  
                 <extensions>  
                   <CustomMetadata>This is custom metadata.</CustomMetadata>
                 </extensions>  
               </findCriteria>  
             </discoveryClientSettings>  
           </standardEndpoint>  
         </dynamicEndpoint>  
   </standardEndpoints>  
</system.ServiceModel>  
```  
  
 <span data-ttu-id="d4c9c-142">표준 끝점에 대 한 자세한 내용은 [표준 끝점](standard-endpoints.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4c9c-142">For more information about standard endpoints see [Standard Endpoints](standard-endpoints.md).</span></span>
