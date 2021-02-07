---
description: '자세히 알아보기: 방법: 필터 사용'
title: '방법: 필터 사용'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 0218685cae6fe8dc4c1e36e51075d58b041ae7fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734323"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="bfd6a-103">방법: 필터 사용</span><span class="sxs-lookup"><span data-stu-id="bfd6a-103">How To: Use Filters</span></span>

<span data-ttu-id="bfd6a-104">이 항목에서는 여러 필터를 사용하는 라우팅 구성을 만드는 데 필요한 기본 단계에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-104">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="bfd6a-105">이 예제에서 메시지는 regularCalc와 roundingCalc라는 두 계산기 서비스 구현으로 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-105">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="bfd6a-106">두 구현 모두 같은 연산을 지원하지만 한 서비스에서 반환 전에 가장 가까운 정수 값으로 모든 계산을 반올림합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-106">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="bfd6a-107">클라이언트 애플리케이션은 서비스의 반올림 버전을 사용할 것인지 여부를 지정해야 합니다. 서비스 기본 설정이 지정되지 않으면 메시지는 두 서비스 사이에서 부하 분산됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-107">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="bfd6a-108">두 서비스에 의해 노출되는 연산은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-108">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="bfd6a-109">추가</span><span class="sxs-lookup"><span data-stu-id="bfd6a-109">Add</span></span>  
  
- <span data-ttu-id="bfd6a-110">빼기</span><span class="sxs-lookup"><span data-stu-id="bfd6a-110">Subtract</span></span>  
  
- <span data-ttu-id="bfd6a-111">곱하기</span><span class="sxs-lookup"><span data-stu-id="bfd6a-111">Multiply</span></span>  
  
- <span data-ttu-id="bfd6a-112">나누기</span><span class="sxs-lookup"><span data-stu-id="bfd6a-112">Divide</span></span>  
  
 <span data-ttu-id="bfd6a-113">두 서비스 모두 같은 연산을 구현하고, 따라서 메시지에 지정된 작업이 고유하지 않으므로 Action 필터는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-113">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="bfd6a-114">대신 메시지가 올바른 엔드포인트로 라우트되도록 추가 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-114">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="bfd6a-115">고유 데이터 확인</span><span class="sxs-lookup"><span data-stu-id="bfd6a-115">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="bfd6a-116">두 서비스 구현은 모두 같은 연산을 처리하고 반환하는 데이터를 제외하면 본질적으로 동일하므로 클라이언트 애플리케이션에서 보낸 메시지에 포함된 기본 데이터는 요청을 라우트할 방법을 결정하기에는 고유성이 부족합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-116">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="bfd6a-117">그러나 클라이언트 애플리케이션이 메시지에 고유한 헤더 값을 추가하면 이 값을 사용하여 메시지를 라우트할 방법을 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-117">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="bfd6a-118">예를 들어 반올림 계산기에 의해 메시지를 처리해야 하는 경우 클라이언트 애플리케이션은 다음 코드를 사용하여 사용자 지정 헤더를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-118">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="bfd6a-119">이제 XPath 필터를 사용하여 메시지에서 이 헤더를 검사하고, 헤더를 포함하는 메시지를 roundCalc 서비스로 라우트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-119">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="bfd6a-120">또한 라우팅 서비스는 EndpointName, EndpointAddress 또는 PrefixEndpointAddress 필터와 함께 사용하여 클라이언트 애플리케이션이 요청을 제출하는 엔드포인트를 기반으로 들어오는 메시지를 특정 계산기 구현으로 고유하게 라우트할 수 있는 두 개의 가상 서비스 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-120">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="bfd6a-121">엔드포인트 정의</span><span class="sxs-lookup"><span data-stu-id="bfd6a-121">Define Endpoints</span></span>  
  
1. <span data-ttu-id="bfd6a-122">라우팅 서비스에 사용되는 엔드포인트를 정의할 때는 먼저 클라이언트와 서비스에 사용되는 채널의 셰이프를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-122">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="bfd6a-123">이 시나리오에서는 두 대상 서비스 모두 요청-회신 패턴을 사용하므로 <xref:System.ServiceModel.Routing.IRequestReplyRouter>가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-123">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="bfd6a-124">다음 예제에서는 라우팅 서비스에 의해 노출되는 서비스 엔드포인트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-124">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="bfd6a-125">이 구성을 통해 라우팅 서비스는 세 개의 개별 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-125">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="bfd6a-126">런타임에서의 선택에 따라 클라이언트 애플리케이션은 이러한 주소 중 하나에 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-126">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="bfd6a-127">"가상" 서비스 끝점 ("반올림/계산기" 또는 "일반/계산기") 중 하나에 도착 하는 메시지는 해당 계산기 구현으로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-127">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="bfd6a-128">클라이언트 애플리케이션이 특정 엔드포인트로 요청을 보내지 않는 경우 메시지는 일반 엔드포인트로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-128">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="bfd6a-129">엔드포인트 선택에 관계없이 클라이언트 애플리케이션은 사용자 지정 헤더를 포함하여 메시지가 반올림 계산기 구현으로 전달되어야 함을 나타내도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-129">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="bfd6a-130">다음 예제에서는 라우팅 서비스가 메시지를 라우트하는 클라이언트(대상) 엔드포인트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-130">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="bfd6a-131">이러한 엔드포인트는 필터 테이블에 사용되어 특정 필터에 일치할 경우 메시지를 보내는 대상 엔드포인트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-131">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="bfd6a-132">필터 정의</span><span class="sxs-lookup"><span data-stu-id="bfd6a-132">Define Filters</span></span>  
  
1. <span data-ttu-id="bfd6a-133">클라이언트 응용 프로그램이 메시지에 추가 하는 "RoundingCalculator" 사용자 지정 헤더를 기반으로 메시지를 라우팅하려면 XPath 쿼리를 사용 하 여이 헤더의 존재 여부를 확인 하는 필터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-133">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="bfd6a-134">이 헤더는 사용자 지정 네임 스페이스를 사용 하 여 정의 되므로 XPath 쿼리에 사용 되는 사용자 지정 네임 스페이스 접두사 "custom"을 정의 하는 네임 스페이스 항목도 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-134">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="bfd6a-135">다음 예제에서는 필요한 라우팅 섹션, 네임스페이스 테이블 및 XPath 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-135">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="bfd6a-136">이 **Messagefilter** 는 "반올림" 값을 포함 하는 메시지에서 RoundingCalculator 헤더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-136">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="bfd6a-137">이 헤더는 클라이언트에 의해 설정되어 메시지가 roundingCalc 서비스로 라우트되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-137">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bfd6a-138">S 12 네임 스페이스 접두사는 네임 스페이스 테이블에서 기본적으로 정의 되며 네임 스페이스를 나타냅니다 `http://www.w3.org/2003/05/soap-envelope` .</span><span class="sxs-lookup"><span data-stu-id="bfd6a-138">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="bfd6a-139">또한 두 가상 엔드포인트에 수신된 메시지를 찾는 필터도 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-139">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="bfd6a-140">첫 번째 가상 끝점은 "regular/계산기" 끝점입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-140">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="bfd6a-141">클라이언트는 이 엔드포인트에 요청을 보내 메시지가 regularCalc 서비스로 라우트되어야 함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-141">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="bfd6a-142">다음 구성에서는 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>를 사용하여 메시지가 filterData에 지정된 이름을 가진 엔드포인트를 통해 도착했는지 확인하는 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-142">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="bfd6a-143">"CalculatorEndpoint" 라는 서비스 끝점에서 메시지를 수신 하는 경우이 필터는로 평가 `true` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-143">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="bfd6a-144">다음으로 roundingEndpoint의 주소로 전송된 메시지를 찾는 필터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-144">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="bfd6a-145">클라이언트는 이 엔드포인트에 요청을 보내 메시지가 roundingCalc 서비스로 라우트되어야 함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-145">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="bfd6a-146">다음 구성에서는를 사용 하 여 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> 메시지가 "반올림/계산기" 끝점에 도착 했는지 확인 하는 필터를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-146">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="bfd6a-147">로 시작 하는 주소에서 메시지를 수신 하는 경우 `http://localhost/routingservice/router/rounding/` 이 필터는 **true** 로 평가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-147">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="bfd6a-148">이 구성에서 사용 하는 기본 주소는이 `http://localhost/routingservice/router` 고 roundingEndpoint에 지정 된 주소는 "반올림/계산기" 이므로이 끝점과 통신 하는 데 사용 되는 전체 주소는 `http://localhost/routingservice/router/rounding/calculator` 이 필터와 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-148">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bfd6a-149">PrefixEndpointAddress 필터는 일치를 수행할 때 호스트 이름을 평가하지 않습니다. 하나의 호스트가 다양한 호스트 이름을 사용하여 참조될 수 있고, 이러한 다양한 이름은 모두 클라이언트 애플리케이션에서 호스트를 참조하는 유효한 방법일 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-149">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="bfd6a-150">예를 들어 다음 항목은 모두 같은 호스트를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-150">For example, all of the following may refer to the same host:</span></span>  
    >
    > - <span data-ttu-id="bfd6a-151">localhost</span><span class="sxs-lookup"><span data-stu-id="bfd6a-151">localhost</span></span>  
    > - <span data-ttu-id="bfd6a-152">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="bfd6a-152">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="bfd6a-153">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="bfd6a-153">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="bfd6a-154">마지막 필터는 사용자 지정 헤더 없이 일반 엔드포인트에 도착하는 메시지의 라우팅을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-154">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="bfd6a-155">이 시나리오의 경우 메시지는 regularCalc 서비스와 roundingCalc 서비스 사이를 번갈아 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-155">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="bfd6a-156">이러한 메시지의 "라운드 로빈" 라우팅을 지원 하려면 처리 된 각 메시지에 대해 하나의 필터 인스턴스가 일치 하도록 허용 하는 사용자 지정 필터를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-156">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="bfd6a-157">다음 예제에서는 RoundRobinMessageFilter의 두 인스턴스를 정의하며, 이 두 인스턴스는 하나로 그룹화되어 서로 번갈아 전환되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-157">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="bfd6a-158">런타임 중에 이 필터 형식은 동일한 그룹으로 하나의 컬렉션에 구성된, 이 형식의 정의된 모든 필터 인스턴스 사이를 번갈아 전환합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-158">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="bfd6a-159">이로 인해이 사용자 지정 필터에 의해 처리 된 메시지가 및에 대해 반환 되는 간을 대체 `true` `RoundRobinFilter1` `RoundRobinFilter2` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-159">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="bfd6a-160">필터 테이블 정의</span><span class="sxs-lookup"><span data-stu-id="bfd6a-160">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="bfd6a-161">필터를 특정 클라이언트 엔드포인트에 연결하려면 해당 필터를 필터 테이블 내에 배치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-161">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="bfd6a-162">이 예제 시나리오에서는 필터가 처리되는 순서를 나타낼 수 있도록 하는 선택적인 설정인 필터 우선 순위 설정도 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-162">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="bfd6a-163">필터 우선 순위를 지정하지 않으면 모든 필터가 동시에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-163">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="bfd6a-164">필터 우선 순위를 지정하면 필터가 처리되는 순서를 제어할 수 있지만 라우팅 서비스의 성능에는 부정적인 영향을 미치게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-164">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="bfd6a-165">가능한 경우 필터 우선 순위를 사용할 필요가 없도록 필터 논리를 생성하세요.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-165">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="bfd6a-166">다음은 필터 테이블을 정의 하 고 우선 순위가 2 인 이전에 정의 된 "XPathFilter"를 테이블에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-166">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="bfd6a-167">또한이 항목은가 `XPathFilter` 메시지와 일치 하는 경우 메시지가로 라우팅되도록 지정 합니다 `roundingCalcEndpoint` .</span><span class="sxs-lookup"><span data-stu-id="bfd6a-167">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          </filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="bfd6a-168">필터 우선 순위를 지정하면 우선 순위가 가장 높은 필터가 가장 먼저 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-168">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="bfd6a-169">특정 우선 순위 수준에서 하나 이상의 필터가 일치하면 그 아래 우선 순위 수준의 필터는 평가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-169">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="bfd6a-170">이 시나리오의 경우 2가 지정된 가장 높은 우선 순위이며, 이 필터가 이 수준에서 유일한 필터입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-170">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="bfd6a-171">필터 항목은 엔드포인트 이름 또는 주소 접두사를 검사하여 특정 엔드포인트에 메시지가 수신되었는지 확인하도록 정의되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-171">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="bfd6a-172">다음 항목은 필터 테이블에 이러한 두 필터 항목을 모두 추가하고 메시지가 라우트되는 대상 엔드포인트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-172">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="bfd6a-173">이러한 필터는 우선 순위 1로 설정되어 이전 XPath 필터가 메시지와 일치하지 않은 경우에만 실행되어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-173">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="bfd6a-174">이러한 필터는 우선 순위가 1이므로 우선 순위 수준 2의 필터가 메시지와 일치하지 않는 경우에만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-174">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="bfd6a-175">또한 두 필터의 우선 순위 수준이 같으므로 두 필터는 동시에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-175">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="bfd6a-176">두 필터 모두 상호 배타적이므로 둘 중 하나의 필터만 메시지와 일치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-176">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="bfd6a-177">이전 필터 중 메시지와 일치하는 필터가 없는 경우 메시지는 제네릭 서비스 엔드포인트를 통해 수신되며, 라우트될 지점을 나타내는 헤더 정보를 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-177">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="bfd6a-178">이러한 메시지는 두 계산기 서비스로 메시지 부하를 분산하는 사용자 지정 필터에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-178">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="bfd6a-179">다음 예제에서는 필터 테이블에 필터 항목을 추가하는 방법을 보여 줍니다. 각 필터는 두 대상 엔드포인트 중 하나와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-179">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="bfd6a-180">이러한 항목은 우선 순위 0을 지정하므로 메시지와 일치하는 더 높은 우선 순위의 필터가 없는 경우에만 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-180">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="bfd6a-181">또한 두 필터는 우선 순위가 같으므로 동시에 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-181">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="bfd6a-182">앞서 설명한 바와 같이 이러한 필터 정의에 사용되는 사용자 지정 필터는 수신되는 각 메시지에 대해 둘 중 하나만 `true`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-182">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="bfd6a-183">두 개의 필터만 동일한 그룹 설정이 지정되어 이 필터로 정의되므로 라우팅 서비스는 regularCalcEndpoint와 RoundingCalcEndpoint로 번갈아 전송하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-183">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="bfd6a-184">필터를 기준으로 메시지를 평가하려면 먼저 메시지를 수신하는 데 사용될 서비스 엔드포인트에 필터 테이블을 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-184">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="bfd6a-185">다음 예제에서는 라우팅 동작을 사용하여 라우팅 테이블과 서비스 엔드포인트를 연결하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-185">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="bfd6a-186">예제</span><span class="sxs-lookup"><span data-stu-id="bfd6a-186">Example</span></span>  

 <span data-ttu-id="bfd6a-187">다음은 구성 파일의 전체 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="bfd6a-187">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bfd6a-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfd6a-188">See also</span></span>

- [<span data-ttu-id="bfd6a-189">라우팅 서비스</span><span class="sxs-lookup"><span data-stu-id="bfd6a-189">Routing Services</span></span>](../samples/routing-services.md)
