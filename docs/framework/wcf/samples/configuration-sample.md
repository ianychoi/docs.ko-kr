---
description: '자세히 알아보기: 구성 샘플'
title: 구성 샘플
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: e11237fbc32b203c9b661288dbccab01745928d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778388"
---
# <a name="configuration-sample"></a><span data-ttu-id="d2963-103">구성 샘플</span><span class="sxs-lookup"><span data-stu-id="d2963-103">Configuration Sample</span></span>

<span data-ttu-id="d2963-104">이 샘플에서는 구성 파일을 사용하여 서비스를 검색 가능하게 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-104">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2963-105">이 샘플은 구성에서 검색을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-105">This sample implements discovery in configuration.</span></span> <span data-ttu-id="d2963-106">코드에서 검색을 구현 하는 샘플은 [Basic](basic-sample.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2963-106">For a sample that implements discovery in code, see [Basic](basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d2963-107">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d2963-108">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d2963-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d2963-109">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2963-110">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="d2963-111">서비스 구성</span><span class="sxs-lookup"><span data-stu-id="d2963-111">Service Configuration</span></span>  

 <span data-ttu-id="d2963-112">이 샘플의 구성 파일에서는 다음 두 가지 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-112">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="d2963-113">표준 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>를 통해 서비스를 검색할 수 있게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-113">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="d2963-114">서비스의 애플리케이션 엔드포인트에 대한 검색 관련 정보를 조정하고 표준 엔드포인트의 검색 관련 설정 중 일부를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-114">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="d2963-115">검색 가능하도록 설정하려면 서비스의 애플리케이션 구성 파일에서 몇 가지 변경 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-115">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="d2963-116">ph x="1" /&gt; 요소에 검색 엔드포인트를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-116">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="d2963-117">이는 표준 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 엔드포인트로서,</span><span class="sxs-lookup"><span data-stu-id="d2963-117">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="d2963-118">런타임에서 검색 서비스와 연결하는 시스템 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-118">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="d2963-119">검색 서비스는 이 엔드포인트에서 메시지를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-119">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="d2963-120">`<serviceDiscovery>` 섹션에 `<serviceBehaviors>` 동작을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-120">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="d2963-121">이 동작은 런타임에 서비스를 검색할 수 있게 해 주며, 앞에서 설명한 검색 엔드포인트를 사용하여 검색 `Probe` 및 `Resolve` 메시지를 수신 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-121">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="d2963-122">이 두 가지 항목을 추가하면 서비스를 지정된 검색 엔드포인트에서 검색할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-122">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="d2963-123">다음 구성 코드 조각에서는 애플리케이션 엔드포인트와 검색 엔드포인트가 정의된 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-123">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"
                    kind="udpDiscoveryEndpoint"
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="d2963-124">알림을 사용하려면 알림 엔드포인트를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-124">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="d2963-125">이렇게 하려면 다음 코드와 같이 구성 파일을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-125">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="d2963-126">알림 엔드포인트를 검색 서비스 동작에 추가하면 서비스에 대한 기본 알림 클라이언트가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-126">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="d2963-127">이렇게 되면 서비스에서 서비스가 열리거나 닫힐 때 각각 온라인 및 오프라인 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-127">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="d2963-128">이 구성 파일에서는 추가 동작을 수정하여 이러한 간단한 단계 외의 작업도 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-128">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="d2963-129">특정 엔드포인트를 사용하여 검색 관련 정보를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-129">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="d2963-130">즉, 사용자가 엔드포인트의 검색 가능 여부를 제어할 수 있으며 해당 엔드포인트를 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> 및 사용자 지정 XML 메타데이터로 표시할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-130">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="d2963-131">이렇게 하려면 애플리케이션 엔드포인트에 `behaviorConfiguration` 속성을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-131">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="d2963-132">이 경우 다음 속성이 애플리케이션 엔드포인트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-132">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="d2963-133">이제 동작 구성 요소를 통해 검색 관련 특성을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-133">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="d2963-134">이 경우 두 개의 범위가 애플리케이션 엔드포인트에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-134">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="d2963-135">범위에 대 한 자세한 내용은 [Discovery 찾기 및 FindCriteria](../feature-details/discovery-find-and-findcriteria.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2963-135">For more information about scopes, see [Discovery Find and FindCriteria](../feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="d2963-136">검색 엔드포인트의 특정 세부 정보를 제어할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-136">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="d2963-137">이 작업은 <xref:System.ServiceModel.Configuration.StandardEndpointsSection>을 통해 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-137">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="d2963-138">이 샘플에서는 다음 코드 예제와 같이 사용되는 프로토콜 버전을 수정할 뿐 아니라 `maxResponseDelay` 특성도 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-138">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="d2963-139">다음은 이 예제에 사용되는 전체 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-139">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="d2963-140">클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="d2963-140">Client Configuration</span></span>  

 <span data-ttu-id="d2963-141">클라이언트의 애플리케이션 구성 파일에서 `standardEndpoint` 형식의 `dynamicEndpoint`는 다음 구성 코드 조각과 같이 검색을 활용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-141">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="d2963-142">클라이언트에서 `dynamicEndpoint`를 사용하는 경우 런타임에서는 검색을 자동으로 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-142">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="d2963-143">사용할 검색 엔드포인트의 형식을 지정하는 `discoveryClientSettings` 섹션에 정의된 설정과 같은 다양한 설정이 검색 중에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-143">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="d2963-144">서비스를 검색하는 데 사용되는 찾기 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-144">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="d2963-145">이 샘플에서는 이 기능을 확장하고, 클라이언트에서 사용하는 <xref:System.ServiceModel.Discovery.FindCriteria>뿐 아니라 검색에 사용되는 표준 `updDiscoveryEndpoint`의 일부 속성도 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-145">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="d2963-146">범위, 특정 <xref:System.ServiceModel.Discovery.FindCriteria> 알고리즘 및 사용자 지정 종료 조건을 사용하도록 `scopeMatchBy`를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-146">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="d2963-147">또한 이 샘플에서는 클라이언트가 `Probe` 메시지를 사용하여 XML 요소를 보내는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-147">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="d2963-148">마지막으로 다음 구성 파일과 같이 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>에 대해 사용되는 프로토콜 버전 및 UDP 관련 설정 등의 사항을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-148">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="d2963-149">다음은 샘플에 사용되는 전체 클라이언트 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-149">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>
        <!-- Specify the discovery protocol version and UDP transport settings. -->
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>
</configuration>
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d2963-150">이 샘플을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="d2963-150">To use this sample</span></span>  
  
1. <span data-ttu-id="d2963-151">이 샘플에서는 HTTP 엔드포인트를 사용하며 이 샘플을 실행하려면 적절한 URL ACL을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-151">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="d2963-152">자세한 내용은 [HTTP 및 HTTPS 구성](../feature-details/configuring-http-and-https.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d2963-152">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="d2963-153">높은 권한으로 다음 명령을 실행하면 적절한 ACL이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-153">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="d2963-154">명령이 지정한 대로 작동하지 않는 경우 다음 인수의 도메인과 사용자 이름을 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-154">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="d2963-155">솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-155">Build the solution.</span></span>  
  
3. <span data-ttu-id="d2963-156">빌드 디렉터리에서 서비스 실행 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-156">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="d2963-157">클라이언트 실행 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-157">Run the client executable.</span></span> <span data-ttu-id="d2963-158">클라이언트에서 서비스를 찾을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d2963-158">Note that the client is able to locate the service.</span></span>  
