---
description: '자세히 알아보기: 라우팅 소개'
title: 라우팅 소개
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 86f5b5dcc0bea067ac3dcfc8a87331da42c642aa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779896"
---
# <a name="routing-introduction"></a><span data-ttu-id="52a8d-103">라우팅 소개</span><span class="sxs-lookup"><span data-stu-id="52a8d-103">Routing Introduction</span></span>

<span data-ttu-id="52a8d-104">라우팅 서비스는 메시지 내용에 따라 메시지를 라우트할 수 있는 제네릭 플러그형 SOAP 매개자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-104">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="52a8d-105">라우팅 서비스를 사용하면 서비스 집계, 서비스 버전 관리, 우선 순위 라우팅 및 멀티캐스트 라우팅과 같은 시나리오를 구현할 수 있도록 하는 복합적인 라우팅 논리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-105">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="52a8d-106">또한 라우팅 서비스는 오류 처리 기능을 제공하므로 기본 대상 엔드포인트로 메시지를 보내는 중 오류가 발생할 경우 이 기능을 통해 메시지를 보낼 백업 엔드포인트 목록을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-106">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="52a8d-107">이 항목은 라우팅 서비스를 새로 접하는 사용자를 대상으로 하며 기본적인 구성과 라우팅 서비스의 호스팅에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-107">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="52a8d-108">Configuration</span><span class="sxs-lookup"><span data-stu-id="52a8d-108">Configuration</span></span>

<span data-ttu-id="52a8d-109">라우팅 서비스는 클라이언트 애플리케이션으로부터 메시지를 수신하여 이 메시지를 하나 이상의 대상 엔드포인트로 라우트하는 하나 이상의 서비스 엔드포인트를 노출하는 WCF 서비스로 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-109">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="52a8d-110">이 서비스는 서비스에 의해 노출되는 서비스 엔드포인트에 적용되는 <xref:System.ServiceModel.Routing.RoutingBehavior>를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-110">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="52a8d-111">이 동작은 서비스 작동 방식의 다양한 측면을 구성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-111">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="52a8d-112">구성 파일을 사용 하는 경우 구성의 용이성을 위해 **Routingbehavior** 에서 매개 변수가 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-112">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="52a8d-113">코드 기반 시나리오에서는 이러한 매개 변수를 개체의 일부로 지정 하 여 <xref:System.ServiceModel.Routing.RoutingConfiguration> **routingbehavior** 에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-113">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="52a8d-114">이러한 동작은 시작 시 SOAP 메시지 처리를 수행하는 데 사용되는 <xref:System.ServiceModel.Routing.SoapProcessingBehavior>를 클라이언트 엔드포인트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-114">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="52a8d-115">이를 통해 라우팅 서비스는 메시지를 받은 끝점과 다른 **MessageVersion** 가 필요한 끝점으로 메시지를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-115">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="52a8d-116">또한 **Routingbehavior** 는 <xref:System.ServiceModel.Routing.RoutingExtension> 런타임에 라우팅 서비스 구성을 수정 하기 위한 액세스 가능성 지점을 제공 하는 서비스 확장인를 등록 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-116">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="52a8d-117">**Routingconfiguration** 클래스는 라우팅 서비스의 구성을 구성 하 고 업데이트 하는 일관 된 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-117">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="52a8d-118">여기에는 라우팅 서비스의 설정 역할을 하는 매개 변수가 포함 되며, 서비스가 시작 될 때 **Routingbehavior** 를 구성 하는 데 사용 되 고, 런타임에 라우팅 구성을 수정 하기 위해 **routingbehavior** 으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-118">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="52a8d-119">내용을 기반으로 메시지를 라우트하는 데 사용되는 라우팅 논리는 여러 <xref:System.ServiceModel.Dispatcher.MessageFilter> 개체를 필터 테이블(<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> 개체)로 그룹화하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-119">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="52a8d-120">들어오는 메시지는 필터 테이블에 포함 된 메시지 필터 및 메시지와 일치 하는 각 **Messagefilter** 에 대해 평가 되 고 대상 끝점으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-120">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="52a8d-121">메시지를 라우팅하는 데 사용 해야 하는 필터 테이블은 구성에서 **Routingbehavior** 를 사용 하거나 **routingbehavior** 개체를 사용 하 여 코드를 통해 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-121">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="52a8d-122">엔드포인트 정의</span><span class="sxs-lookup"><span data-stu-id="52a8d-122">Defining Endpoints</span></span>

<span data-ttu-id="52a8d-123">구성의 첫 작업은 사용할 라우팅 논리를 정의하는 것이라고 생각하기 쉽지만 사실 수행해야 할 첫 번째 단계는 메시지를 라우트할 엔드포인트의 셰이프를 결정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-123">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="52a8d-124">라우팅 서비스는 메시지를 보내고 받는 데 사용되는 채널의 셰이프를 정의하는 계약을 사용하므로 입력 채널의 셰이프는 출력 채널의 셰이프와 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-124">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="52a8d-125">예를 들어 요청-회신 채널 셰이프를 사용하는 엔드포인트로 라우트하는 경우 인바운드 엔드포인트에 호환되는 계약을 사용해야 합니다(예: <xref:System.ServiceModel.Routing.IRequestReplyRouter>).</span><span class="sxs-lookup"><span data-stu-id="52a8d-125">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="52a8d-126">이는 대상 엔드포인트가 여러 통신 패턴을 가진 계약을 사용하는 경우(예: 단방향과 양방향 작업의 혼합) 이러한 모든 엔드포인트에서 메시지를 수신하고 라우트할 수 있는 하나의 서비스 엔드포인트를 만들 수 없음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-126">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="52a8d-127">호환되는 셰이프를 가진 엔드포인트를 확인하고 대상 엔드포인트로 라우트될 메시지를 수신하는 데 사용될 하나 이상의 서비스 엔드포인트를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-127">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="52a8d-128">여러 통신 패턴을 지정하는 계약을 사용하는 경우(예: 단방향과 양방향 작업의 혼합) 해결 방법은 라우팅 서비스에서 이중 계약을 사용하는 것입니다(예: <xref:System.ServiceModel.Routing.IDuplexSessionRouter>).</span><span class="sxs-lookup"><span data-stu-id="52a8d-128">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="52a8d-129">그러나 이는 바인딩이 이중 통신을 수행할 수 있어야 함을 의미하므로 이 방법이 가능하지 않은 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-129">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="52a8d-130">이 방법이 가능하지 않은 시나리오에서는 통신을 여러 엔드포인트로 팩터링하거나 애플리케이션을 수정해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-130">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="52a8d-131">라우팅 계약에 대 한 자세한 내용은 [라우팅 계약](routing-contracts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-131">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="52a8d-132">서비스 끝점이 정의 된 후에는 **Routingbehavior** 를 사용 하 여 특정 **routingbehavior** 을 끝점과 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-132">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="52a8d-133">구성 파일을 사용 하 여 라우팅 서비스를 구성 하는 경우 **Routingbehavior** 는이 끝점에서 받은 메시지를 처리 하는 데 사용 되는 라우팅 논리를 포함 하는 필터 테이블을 지정 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-133">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="52a8d-134">라우팅 서비스를 프로그래밍 방식으로 구성 하는 경우 **Routingconfiguration** 을 사용 하 여 필터 테이블을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-134">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="52a8d-135">다음 예제에서는 라우팅 서비스에서 프로그래밍 방식으로, 구성 파일을 통해 사용되는 서비스와 클라이언트 엔드포인트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-135">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

<span data-ttu-id="52a8d-136">이 예제에서는 `http://localhost:8000/routingservice/router` 라우팅할 메시지를 수신 하는 데 사용 되는 주소를 사용 하 여 단일 끝점을 노출 하도록 라우팅 서비스를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-136">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="52a8d-137">메시지는 요청-회신 엔드포인트로 라우트되므로 서비스 엔드포인트는 <xref:System.ServiceModel.Routing.IRequestReplyRouter> 계약을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-137">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="52a8d-138">또한이 구성은 메시지가 라우팅되는의 단일 클라이언트 엔드포인트를 정의 `http://localhost:8000/servicemodelsample/service` 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-138">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="52a8d-139">"RoutingTable1" 라는 필터 테이블은 메시지를 라우팅하는 데 사용 되는 라우팅 논리를 포함 하며, **Routingbehavior** (구성 파일의 경우) 또는 **routingbehavior** (프로그래밍 방식 구성의 경우)을 사용 하 여 서비스 끝점과 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-139">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="52a8d-140">라우팅 논리</span><span class="sxs-lookup"><span data-stu-id="52a8d-140">Routing Logic</span></span>

<span data-ttu-id="52a8d-141">메시지를 라우트하는 데 사용되는 라우팅 논리를 정의하려면 들어오는 메시지에 포함된, 고유한 작업 대상이 될 수 있는 데이터를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-141">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="52a8d-142">예를 들어 라우트하는 모든 대상 엔드포인트가 동일한 SOAP 작업을 공유하는 경우 메시지 내에 포함된 Action 값은 메시지를 라우트해야 할 특정 엔드포인트를 나타내는 지표로 적절하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-142">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="52a8d-143">하나의 특정 엔드포인트로 메시지를 고유하게 라우트해야 하는 경우 메시지가 라우트되는 대상 엔드포인트를 고유하게 식별하는 데이터를 대상으로 필터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-143">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="52a8d-144">라우팅 서비스는 주소, 동작, 끝점 이름 또는 XPath 쿼리와 같은 메시지 내의 특정 값을 검사 하는 여러 **Messagefilter** 구현을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-144">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="52a8d-145">이러한 구현에서 요구 사항을 충족 하지 않는 경우 사용자 지정 **Messagefilter** 구현을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-145">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="52a8d-146">메시지 필터에 대 한 자세한 내용과 라우팅 서비스에서 사용 하는 구현을 비교한 내용은 [메시지 필터](message-filters.md) 및 [필터 선택](choosing-a-filter.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-146">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="52a8d-147">여러 메시지 필터는 각 **Messagefilter** 를 대상 끝점과 연결 하는 필터 테이블로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-147">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="52a8d-148">또한 필요에 따라 필터 테이블은 전송 오류가 발생할 경우 라우팅 서비스가 메시지 보내기를 시도할 백업 엔드포인트 목록을 지정하는 데 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-148">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="52a8d-149">기본적으로 필터 테이블 내의 모든 메시지 필터는 동시에 평가되지만 메시지 필터가 특정 순서에 따라 평가되도록 하는 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A>를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-149">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="52a8d-150">우선 순위가 가장 높은 모든 항목이 가장 먼저 평가되며, 상대적으로 더 높은 우선 순위 수준에서 일치하는 항목이 발견될 경우 이에 비해 우선 순위가 낮은 메시지 필터는 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-150">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="52a8d-151">필터 테이블에 대 한 자세한 내용은 [메시지 필터](message-filters.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-151">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="52a8d-152">다음 예제에서는 모든 메시지에 대해 <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>를 반환하는 `true`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-152">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="52a8d-153">이 **Messagefilter** 는 "routingTable1" 필터 테이블에 추가 되며이는 **Messagefilter** 를 "CalculatorService" 라는 클라이언트 끝점과 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-153">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="52a8d-154">그런 다음 **Routingbehavior** 는 서비스 끝점에서 처리 하는 메시지를 라우팅하는 데이 테이블을 사용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-154">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> <span data-ttu-id="52a8d-155">기본적으로 라우팅 서비스는 메시지의 헤더만 평가합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-155">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="52a8d-156">필터에서 메시지 본문에 액세스하도록 허용하려면 <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A>를 `false`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-156">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="52a8d-157">**멀티캐스트**</span><span class="sxs-lookup"><span data-stu-id="52a8d-157">**Multicast**</span></span>

<span data-ttu-id="52a8d-158">많은 라우팅 서비스 구성에서 하나의 특정 엔드포인트로만 메시지를 라우트하는 단독 필터 논리를 사용하지만 주어진 메시지를 여러 대상 엔드포인트로 라우트해야 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-158">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="52a8d-159">메시지를 여러 대상으로 멀티캐스트하려면 다음 조건이 충족되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-159">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="52a8d-160">클라이언트 애플리케이션은 요청에 대한 응답으로 하나의 회신만 수신할 수 있으므로 채널 셰이프가 요청-회신이면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-160">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="52a8d-161">메시지를 평가할 때 여러 필터에서 `true`를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-161">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="52a8d-162">이러한 조건이 충족되면 `true`를 반환하는 모든 필터의 모든 엔드포인트로 메시지가 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-162">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="52a8d-163">다음 예제에서는 메시지의 끝점 주소가 인 경우 메시지가 두 끝점으로 라우팅되는 라우팅 구성을 정의 합니다 `http://localhost:8000/routingservice/router/rounding` .</span><span class="sxs-lookup"><span data-stu-id="52a8d-163">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a><span data-ttu-id="52a8d-164">SOAP 처리</span><span class="sxs-lookup"><span data-stu-id="52a8d-164">SOAP Processing</span></span>

<span data-ttu-id="52a8d-165">서로 다른 프로토콜 간의 메시지 라우팅을 지원 하기 위해 **Routingbehavior** 는 기본적으로 <xref:System.ServiceModel.Routing.SoapProcessingBehavior> 메시지를 라우팅하는 모든 클라이언트 끝점에를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-165">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="52a8d-166">이 동작은 메시지를 끝점으로 라우팅하기 전에 새 **MessageVersion** 를 자동으로 만들고, 요청 하는 클라이언트 응용 프로그램으로 반환 하기 전에 응답 문서에 대해 호환 되는 **MessageVersion** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-166">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="52a8d-167">아웃 바운드 메시지에 대 한 새 **MessageVersion** 를 만드는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-167">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="52a8d-168">**요청 처리**</span><span class="sxs-lookup"><span data-stu-id="52a8d-168">**Request processing**</span></span>

- <span data-ttu-id="52a8d-169">아웃 바운드 바인딩/채널의 **MessageVersion** 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-169">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="52a8d-170">원본 메시지에 대한 본문 판독기를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-170">Get the body reader for the original message.</span></span>

- <span data-ttu-id="52a8d-171">동일한 작업, 본문 판독기 및 새 **MessageVersion** 를 사용 하 여 새 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-171">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="52a8d-172"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **주소 지정. None** 이면 To, From, FaultTo 및 RelatesTo 헤더를 새 메시지에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-172">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="52a8d-173">모든 메시지 속성을 새 메시지에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-173">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="52a8d-174">응답을 처리할 때 사용할 원본 요청 메시지를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-174">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="52a8d-175">새 요청 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-175">Return the new request message.</span></span>

<span data-ttu-id="52a8d-176">**응답 처리**</span><span class="sxs-lookup"><span data-stu-id="52a8d-176">**Response processing**</span></span>

- <span data-ttu-id="52a8d-177">원래 요청 메시지의 **MessageVersion** 를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-177">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="52a8d-178">수신한 응답 메시지에 대한 본문 판독기를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-178">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="52a8d-179">동일한 작업, 본문 판독기 및 원래 요청 메시지의 **MessageVersion** 를 사용 하 여 새 응답 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-179">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="52a8d-180"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = **주소 지정. None** 이면 To, From, FaultTo 및 RelatesTo 헤더를 새 메시지에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-180">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="52a8d-181">메시지 속성을 새 메시지에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-181">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="52a8d-182">새 응답 메시지를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-182">Return the new response message.</span></span>

<span data-ttu-id="52a8d-183">기본적으로 **SoapProcessingBehavior** 는 서비스가 시작 될 때에 의해 클라이언트 끝점에 자동으로 추가 되지만 <xref:System.ServiceModel.Routing.RoutingBehavior> , 속성을 사용 하 여 SOAP 처리가 모든 클라이언트 끝점에 추가 되는지 여부를 제어할 수 있습니다 <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> .</span><span class="sxs-lookup"><span data-stu-id="52a8d-183">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="52a8d-184">또한 SOAP 처리에 대한 더 세부적인 제어가 필요한 경우에는 특정 엔드포인트에 동작을 직접 추가하고 엔드포인트 수준에서 이 동작을 사용하거나 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-184">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="52a8d-185">원본 요청 메시지와 다른 MessageVersion을 요구하는 엔드포인트에 대해 SOAP 처리를 사용하지 않도록 설정할 경우 메시지를 대상 엔드포인트로 보내기 전에 필요한 SOAP 수정 작업을 수행하기 위한 사용자 지정 메커니즘을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-185">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="52a8d-186">다음 예에서는 **soapProcessingEnabled** 속성을 사용 하 여 **SoapProcessingBehavior** 가 모든 클라이언트 끝점에 자동으로 추가 되는 것을 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-186">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a><span data-ttu-id="52a8d-187">동적 구성</span><span class="sxs-lookup"><span data-stu-id="52a8d-187">Dynamic Configuration</span></span>

<span data-ttu-id="52a8d-188">부가적인 클라이언트 엔드포인트를 추가하는 경우 또는 메시지를 라우트하는 데 사용되는 필터를 수정해야 하는 경우 현재 라우팅 서비스를 통해 메시지를 수신하는 엔드포인트에 대한 서비스를 중단시키지 않도록 런타임에 동적으로 구성을 업데이트하는 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-188">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="52a8d-189">구성 파일이나 호스트 애플리케이션의 코드를 수정하는 것으로는 부족한 경우가 있습니다. 두 방법에는 모두 애플리케이션 재활용이 필요하고, 이 경우 현재 전송 중인 메시지가 손실될 가능성, 그리고 서비스가 다시 시작될 때까지 대기하는 동안 작동 중단이 발생할 가능성이 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-189">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="52a8d-190">**Routingconfiguration** 은 프로그래밍 방식 으로만 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-190">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="52a8d-191">처음에 구성 파일을 사용 하 여 서비스를 구성할 수 있지만, 새 **Routingconfiguration** 을 생성 하 고 <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> 서비스 확장에서 노출 하는 메서드에 매개 변수로 전달 하 여 런타임에만 구성을 수정할 수 있습니다 <xref:System.ServiceModel.Routing.RoutingExtension> .</span><span class="sxs-lookup"><span data-stu-id="52a8d-191">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="52a8d-192">현재 전송 중인 모든 메시지는 이전 구성을 사용 하 여 계속 라우팅됩니다. 반면 **ApplyConfiguration** 를 호출한 후 받은 메시지는 새 구성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-192">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="52a8d-193">다음 예제에서는 라우팅 서비스의 인스턴스를 만들고 그 후 구성을 수정하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-193">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> <span data-ttu-id="52a8d-194">이 방법으로 라우팅 서비스를 업데이트하는 경우 새 구성을 전달하는 것만 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-194">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="52a8d-195">현재 구성에서 선택한 요소만 수정하거나 현재 구성에 새 항목을 추가하는 것은 불가능합니다. 즉, 기존 구성을 대체하는 새 구성을 만들어 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-195">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="52a8d-196">이전 구성을 사용하여 열린 세션은 계속 이전 구성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-196">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="52a8d-197">새 구성은 새 세션에서만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-197">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="52a8d-198">오류 처리</span><span class="sxs-lookup"><span data-stu-id="52a8d-198">Error Handling</span></span>

<span data-ttu-id="52a8d-199">메시지를 보내려고 시도하는 중에 <xref:System.ServiceModel.CommunicationException>이 발생하는 경우 오류 처리가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-199">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="52a8d-200">일반적으로 이러한 예외는 정의된 클라이언트 엔드포인트와 통신을 시도하는 중에 문제가 발생했음을 나타냅니다(예: <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException> 또는 <xref:System.ServiceModel.CommunicationObjectFaultedException>).</span><span class="sxs-lookup"><span data-stu-id="52a8d-200">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="52a8d-201">오류 처리 코드는 <xref:System.TimeoutException> **CommunicationException** 에서 파생 되지 않는 또 다른 일반적인 예외인이 발생 하는 경우에도를 catch 하 고 보내기를 다시 시도 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-201">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="52a8d-202">앞서 언급한 예외 중 하나가 발생하면 라우팅 서비스는 백업 엔드포인트 목록으로 장애 조치됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-202">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="52a8d-203">모든 백업 엔드포인트가 통신 오류로 인해 실패하거나 엔드포인트에서 대상 서비스 내의 오류를 나타내는 예외를 반환하는 경우 라우팅 서비스는 클라이언트 애플리케이션에 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-203">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="52a8d-204">오류 처리 기능은 메시지 보내기를 시도할 때와 채널 닫기를 시도할 때 발생하는 예외를 캡처하여 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-204">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="52a8d-205">오류 처리 코드는 통신 중인 응용 프로그램 끝점에 의해 생성 된 예외를 검색 하거나 처리 하기 위한 것이 아닙니다. <xref:System.ServiceModel.FaultException> 서비스에서 throw 된는 라우팅 서비스에서 **faultmessage** 로 나타나고 클라이언트에 다시 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-205">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="52a8d-206">라우팅 서비스에서 메시지를 릴레이하려고 할 때 오류가 발생하는 경우 라우팅 서비스가 없을 때 일반적으로 발생하는 <xref:System.ServiceModel.FaultException> 대신 <xref:System.ServiceModel.EndpointNotFoundException>이 클라이언트측에서 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-206">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="52a8d-207">따라서 중첩된 예외를 검사하지 않는 한 라우팅 서비스는 예외를 마스킹하고 완전한 투명성을 제공하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-207">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="52a8d-208">예외 추적</span><span class="sxs-lookup"><span data-stu-id="52a8d-208">Tracing Exceptions</span></span>

<span data-ttu-id="52a8d-209">목록의 끝점으로 메시지를 보낼 수 없는 경우 라우팅 서비스는 결과 예외 데이터를 추적 하 고 예외 정보를 **예외** 라는 메시지 속성으로 첨부 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-209">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="52a8d-210">이 속성은 예외 데이터를 보존하며 사용자가 메시지 검사자를 통해 프로그래밍 방식으로 액세스하도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-210">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="52a8d-211">예외 데이터는 메시지를 보내려고 시도할 때 발생하는 예외 정보에 엔드포인트 이름을 매핑하는 사전에 메시지별로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-211">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="52a8d-212">백업 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="52a8d-212">Backup Endpoints</span></span>

<span data-ttu-id="52a8d-213">필터 테이블 내의 각 필터 항목은 기본 엔드포인트로 보낼 때 전송 오류가 발생하는 경우 사용되는 백업 엔드포인트 목록을 선택적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-213">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="52a8d-214">이러한 오류가 발생하는 경우 라우팅 서비스는 백업 엔드포인트 목록의 첫 번째 항목으로 메시지를 전송하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-214">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="52a8d-215">이 시도에서도 전송 오류가 발생하면 백업 목록의 다음 엔드포인트에 대해 전송을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-215">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="52a8d-216">라우팅 서비스는 메시지가 성공적으로 수신되거나 모든 엔드포인트가 전송 오류를 반환하거나 엔드포인트에서 전송 오류 이외의 오류를 반환할 때까지 목록의 각 엔드포인트로 계속 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-216">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="52a8d-217">다음 예제에서는 백업 목록을 사용하도록 라우팅 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-217">The following examples configure the Routing Service to use a backup list.</span></span>

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <!-- Set up the Routing Service's Message Filter Table -->
    <filterTable name="filterTable1">
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
        <!-- Listed in the backupEndpointList -->
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
    </filterTable>
  </filterTables>
  <!-- Create the backup endpoint list -->
  <backupLists>
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a><span data-ttu-id="52a8d-218">지원되는 오류 패턴</span><span class="sxs-lookup"><span data-stu-id="52a8d-218">Supported Error Patterns</span></span>

<span data-ttu-id="52a8d-219">다음 표에서는 백업 엔드포인트 목록 사용과 호환되는 패턴에 대해 설명하고 특정 패턴에 대한 오류 처리의 세부 정보를 설명하는 참고 사항을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-219">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="52a8d-220">무늬</span><span class="sxs-lookup"><span data-stu-id="52a8d-220">Pattern</span></span>|<span data-ttu-id="52a8d-221">세션</span><span class="sxs-lookup"><span data-stu-id="52a8d-221">Session</span></span>|<span data-ttu-id="52a8d-222">트랜잭션</span><span class="sxs-lookup"><span data-stu-id="52a8d-222">Transaction</span></span>|<span data-ttu-id="52a8d-223">받기 컨텍스트</span><span class="sxs-lookup"><span data-stu-id="52a8d-223">Receive Context</span></span>|<span data-ttu-id="52a8d-224">백업 목록 지원</span><span class="sxs-lookup"><span data-stu-id="52a8d-224">Backup List Supported</span></span>|<span data-ttu-id="52a8d-225">참고</span><span class="sxs-lookup"><span data-stu-id="52a8d-225">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="52a8d-226">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-226">One-Way</span></span>||||<span data-ttu-id="52a8d-227">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-227">Yes</span></span>|<span data-ttu-id="52a8d-228">백업 엔드포인트에 메시지를 다시 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-228">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="52a8d-229">이 메시지가 멀티캐스트되는 경우 실패한 채널의 메시지만 백업 대상으로 이동됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-229">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="52a8d-230">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-230">One-Way</span></span>||<span data-ttu-id="52a8d-231">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-231">✔️</span></span>||<span data-ttu-id="52a8d-232">아니요</span><span class="sxs-lookup"><span data-stu-id="52a8d-232">No</span></span>|<span data-ttu-id="52a8d-233">예외가 throw되고 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-233">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="52a8d-234">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-234">One-Way</span></span>|||<span data-ttu-id="52a8d-235">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-235">✔️</span></span>|<span data-ttu-id="52a8d-236">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-236">Yes</span></span>|<span data-ttu-id="52a8d-237">백업 엔드포인트에 메시지를 다시 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-237">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="52a8d-238">메시지가 성공적으로 수신된 후 모든 받기 컨텍스트를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-238">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="52a8d-239">메시지가 성공적으로 수신된 엔드포인트가 없는 경우 받기 컨텍스트를 완료하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-239">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="52a8d-240">이 메시지가 멀티캐스트되는 경우 받기 컨텍스트는 메시지가 최소 하나의 엔드포인트(기본 또는 백업)에 성공적으로 수신된 경우에만 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-240">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="52a8d-241">모든 멀티캐스트 경로의 어떠한 엔드포인트에서도 메시지를 성공적으로 수신하지 못한 경우 받기 컨텍스트를 완료하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-241">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="52a8d-242">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-242">One-Way</span></span>||<span data-ttu-id="52a8d-243">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-243">✔️</span></span>|<span data-ttu-id="52a8d-244">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-244">✔️</span></span>|<span data-ttu-id="52a8d-245">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-245">Yes</span></span>|<span data-ttu-id="52a8d-246">이전 트랜잭션을 중단하고 새 트랜잭션을 만들고 모든 메시지를 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-246">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="52a8d-247">오류가 발생한 메시지는 백업 대상으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-247">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="52a8d-248">모든 전송이 성공한 트랜잭션이 만들어진 후 받기 컨텍스트를 완료하고 트랜잭션을 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-248">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="52a8d-249">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-249">One-Way</span></span>|<span data-ttu-id="52a8d-250">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-250">✔️</span></span>|||<span data-ttu-id="52a8d-251">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-251">Yes</span></span>|<span data-ttu-id="52a8d-252">백업 엔드포인트에 메시지를 다시 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-252">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="52a8d-253">멀티캐스트 시나리오에서는 오류가 발생한 세션 또는 세션 닫기가 실패한 세션의 메시지만 백업 대상으로 다시 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-253">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="52a8d-254">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-254">One-Way</span></span>|<span data-ttu-id="52a8d-255">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-255">✔️</span></span>|<span data-ttu-id="52a8d-256">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-256">✔️</span></span>||<span data-ttu-id="52a8d-257">아니요</span><span class="sxs-lookup"><span data-stu-id="52a8d-257">No</span></span>|<span data-ttu-id="52a8d-258">예외가 throw되고 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-258">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="52a8d-259">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-259">One-Way</span></span>|<span data-ttu-id="52a8d-260">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-260">✔️</span></span>||<span data-ttu-id="52a8d-261">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-261">✔️</span></span>|<span data-ttu-id="52a8d-262">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-262">Yes</span></span>|<span data-ttu-id="52a8d-263">백업 엔드포인트에 메시지를 다시 보내려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-263">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="52a8d-264">오류 없이 모든 메시지 보내기가 완료된 후 세션은 더 이상 메시지가 없음을 나타내고 라우팅 서비스는 모든 아웃바운드 세션 채널을 성공적으로 닫고 모든 받기 컨텍스트가 완료되며 인바운드 세션 채널이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-264">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="52a8d-265">단방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-265">One-Way</span></span>|<span data-ttu-id="52a8d-266">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-266">✔️</span></span>|<span data-ttu-id="52a8d-267">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-267">✔️</span></span>|<span data-ttu-id="52a8d-268">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-268">✔️</span></span>|<span data-ttu-id="52a8d-269">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-269">Yes</span></span>|<span data-ttu-id="52a8d-270">현재 트랜잭션을 중단하고 새 트랜잭션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-270">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="52a8d-271">세션의 모든 이전 메시지를 다시 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-271">Resend all previous messages in the session.</span></span> <span data-ttu-id="52a8d-272">모든 메시지가 성공적으로 전송된 트랜잭션이 만들어진 후 세션은 더 이상 메시지가 없음을 나타내고 모든 아웃바운드 세션 채널이 닫히고 트랜잭션과 함께 받기 컨텍스트가 모두 완료되고 인바운드 세션 채널이 닫히고 트랜잭션이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-272">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="52a8d-273">세션이 멀티캐스트되는 경우 오류가 발생하지 않은 메시지는 이전과 같은 대상으로 다시 전송되고 오류가 발생한 메시지는 백업 대상으로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-273">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="52a8d-274">양방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-274">Two-Way</span></span>||||<span data-ttu-id="52a8d-275">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-275">Yes</span></span>|<span data-ttu-id="52a8d-276">백업 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-276">Send to a backup destination.</span></span>  <span data-ttu-id="52a8d-277">채널이 응답 메시지를 반환한 후 응답을 원래 클라이언트로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-277">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="52a8d-278">양방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-278">Two-Way</span></span>|<span data-ttu-id="52a8d-279">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-279">✔️</span></span>|||<span data-ttu-id="52a8d-280">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-280">Yes</span></span>|<span data-ttu-id="52a8d-281">채널의 모든 메시지를 백업 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-281">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="52a8d-282">채널이 응답 메시지를 반환한 후 응답을 원래 클라이언트로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-282">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="52a8d-283">양방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-283">Two-Way</span></span>||<span data-ttu-id="52a8d-284">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-284">✔️</span></span>||<span data-ttu-id="52a8d-285">아니요</span><span class="sxs-lookup"><span data-stu-id="52a8d-285">No</span></span>|<span data-ttu-id="52a8d-286">예외가 throw되고 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-286">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="52a8d-287">양방향</span><span class="sxs-lookup"><span data-stu-id="52a8d-287">Two-Way</span></span>|<span data-ttu-id="52a8d-288">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-288">✔️</span></span>|<span data-ttu-id="52a8d-289">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-289">✔️</span></span>||<span data-ttu-id="52a8d-290">아니요</span><span class="sxs-lookup"><span data-stu-id="52a8d-290">No</span></span>|<span data-ttu-id="52a8d-291">예외가 throw되고 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-291">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="52a8d-292">이중</span><span class="sxs-lookup"><span data-stu-id="52a8d-292">Duplex</span></span>||||<span data-ttu-id="52a8d-293">아니요</span><span class="sxs-lookup"><span data-stu-id="52a8d-293">No</span></span>|<span data-ttu-id="52a8d-294">비-세션 이중 통신은 현재 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-294">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="52a8d-295">이중</span><span class="sxs-lookup"><span data-stu-id="52a8d-295">Duplex</span></span>|<span data-ttu-id="52a8d-296">✔️</span><span class="sxs-lookup"><span data-stu-id="52a8d-296">✔️</span></span>|||<span data-ttu-id="52a8d-297">예</span><span class="sxs-lookup"><span data-stu-id="52a8d-297">Yes</span></span>|<span data-ttu-id="52a8d-298">백업 대상으로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-298">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="52a8d-299">Hosting</span><span class="sxs-lookup"><span data-stu-id="52a8d-299">Hosting</span></span>

<span data-ttu-id="52a8d-300">라우팅 서비스는 WCF 서비스로 구현되므로 애플리케이션 내에서 자체 호스트되거나 IIS 또는 WAS에서 호스트되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-300">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="52a8d-301">자동 시작 및 수명 주기 관리 기능을 사용하려면 호스팅 환경에서 이러한 기능을 제공하는 IIS, WAS 또는 Windows 서비스 애플리케이션에서 라우팅 서비스를 호스트하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-301">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="52a8d-302">다음 예제에서는 애플리케이션에서 라우팅 서비스를 호스트하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-302">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="52a8d-303">IIS 또는 WAS 내에서 라우팅 서비스를 호스트하려면 서비스 파일(.svc)을 만들거나 서비스의 구성 기반 활성화를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-303">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="52a8d-304">서비스 파일을 사용하는 경우 Service 매개 변수를 사용하여 <xref:System.ServiceModel.Routing.RoutingService>를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-304">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="52a8d-305">다음 예제에는 IIS 또는 WAS를 사용하여 라우팅 서비스를 호스트하는 데 사용할 수 있는 샘플 서비스 파일이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-305">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="52a8d-306">라우팅 서비스 및 가장</span><span class="sxs-lookup"><span data-stu-id="52a8d-306">Routing Service and Impersonation</span></span>

<span data-ttu-id="52a8d-307">WCF 라우팅 서비스는 메시지 보내기 및 받기 모두에 대해 가장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-307">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="52a8d-308">가장에 대한 일반적인 모든 Windows 제약 조건이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-308">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="52a8d-309">자신의 서비스를 작성할 때 가장을 사용하기 위한 서비스 또는 계정 권한을 설정해야 하는 경우 라우팅 서비스에서 가장을 사용하려면 같은 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-309">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="52a8d-310">자세한 내용은 [위임 및 가장](delegation-and-impersonation-with-wcf.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-310">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="52a8d-311">라우팅 서비스에서 가장을 사용하려면 ASP.NET 호환 모드에서 ASP.NET 가장을 사용하거나 가장을 허용하도록 구성된 Windows 자격 증명을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-311">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="52a8d-312">ASP.NET 호환 모드에 대 한 자세한 내용은 [WCF 서비스 및 ASP.NET](wcf-services-and-aspnet.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52a8d-312">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="52a8d-313">WCF 라우팅 서비스는 기본 인증의 가장을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-313">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="52a8d-314">라우팅 서비스에서 ASP.NET 가장을 사용하려면 서비스 호스팅 환경에서 ASP.NET 호환 모드를 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-314">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="52a8d-315">라우팅 서비스는 이미 ASP.NET 호환 모드를 허용하는 것으로 표시되었으며 가장이 자동으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-315">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="52a8d-316">가장은 라우팅 서비스에서 유일하게 지원되는 ASP.NET 통합 사용 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-316">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="52a8d-317">라우팅 서비스에서 Windows 자격 증명 가장을 사용하려면 자격 증명과 서비스 둘 다를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-317">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="52a8d-318">클라이언트 자격 증명 개체(<xref:System.ServiceModel.Security.WindowsClientCredential>, <xref:System.ServiceModel.ChannelFactory>에서 액세스)는 가장을 허용하기 위해 반드시 설정해야 하는 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 속성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-318">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="52a8d-319">마지막으로, 서비스에서 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 동작을 구성해서 `ImpersonateCallerForAllOperations`를 `true`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-319">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="52a8d-320">라우팅 서비스는 이 플래그를 사용하여 가장을 사용하는 메시지를 전달하기 위한 클라이언트를 만들지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="52a8d-320">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="52a8d-321">참고 항목</span><span class="sxs-lookup"><span data-stu-id="52a8d-321">See also</span></span>

- [<span data-ttu-id="52a8d-322">메시지 필터</span><span class="sxs-lookup"><span data-stu-id="52a8d-322">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="52a8d-323">라우팅 계약</span><span class="sxs-lookup"><span data-stu-id="52a8d-323">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="52a8d-324">필터 선택</span><span class="sxs-lookup"><span data-stu-id="52a8d-324">Choosing a Filter</span></span>](choosing-a-filter.md)
