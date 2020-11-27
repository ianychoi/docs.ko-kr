---
title: 단일 ListenUri의 여러 엔드포인트
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: 09696ec8170915f29dae7510f8953565bcc67436
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260190"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="9204a-102">단일 ListenUri의 여러 엔드포인트</span><span class="sxs-lookup"><span data-stu-id="9204a-102">Multiple Endpoints at a Single ListenUri</span></span>

<span data-ttu-id="9204a-103">이 샘플에서는 단일 `ListenUri`에서 여러 엔드포인트를 호스팅하는 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="9204a-104">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9204a-105">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9204a-106">[여러 끝점](multiple-endpoints.md) 샘플에서 볼 수 있듯이 서비스는 각각 서로 다른 주소를 사용 하는 여러 끝점 및 다른 바인딩을 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-106">As demonstrated in the [Multiple Endpoints](multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="9204a-107">이 샘플에서는 동일한 주소에서 여러 엔드포인트를 호스팅할 수 있다는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="9204a-108">또한 이 샘플에서는 서비스 엔드포인트가 가지는 두 종류의 주소인 `EndpointAddress` 및 `ListenUri` 간의 차이점을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="9204a-109">`EndpointAddress`는 서비스의 논리 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="9204a-110">SOAP 메시지의 주소가 이 주소로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="9204a-111">`ListenUri`는 서비스의 실제 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="9204a-112">서비스 엔드포인트가 현재 컴퓨터에서 메시지를 실제로 수신 대기하는 포트 및 주소 정보가 이 주소에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="9204a-113">대부분의 경우 이러한 주소는 다를 필요가 없습니다. `ListenUri`가 명시적으로 지정되지 않은 경우 엔드포인트의 `EndpointAddress`의 URI가 기본값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="9204a-114">라우터를 구성하는 경우와 같은 일부 상황에서는 여러 다른 서비스로 주소가 지정된 메시지를 수락할 수 있도록 이러한 주소를 구별하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="9204a-115">서비스</span><span class="sxs-lookup"><span data-stu-id="9204a-115">Service</span></span>  

 <span data-ttu-id="9204a-116">이 샘플의 서비스에는 두 개의 계약인 `ICalculator` 및 `IEcho`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="9204a-117">다음 코드에 표시된 것처럼 일반적인 `IMetadataExchange` 엔드포인트 외에도 세 개의 애플리케이션 엔드포인트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="9204a-118">세 개의 엔드포인트는 모두 동일한 `ListenUri`에서 호스팅되고 동일한 `binding`을 사용합니다. 동일한 `ListenUri`에 있는 엔드포인트는 컴퓨터의 해당 실제 주소에서 메시지를 수신 대기하는 단일 채널 스택을 공유하므로 동일한 바인딩을 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="9204a-119">각 엔드포인트의 `address`는 URN입니다. 일반적으로 주소가 실제 위치를 나타내지만 이 샘플에 나온 것처럼 실제로 이 주소는 일치 및 필터링 목적에 사용되므로 모든 종류의 URI가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="9204a-120">3 개의 끝점이 모두 동일한를 공유 하기 때문에 `ListenUri` 메시지가 도착할 때 WCF (Windows Communication Foundation)는 메시지를 보낼 끝점을 결정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, Windows Communication Foundation (WCF) must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="9204a-121">각 엔드포인트에는 주소 필터와 계약 필터의 두 부분으로 구성된 메시지 필터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="9204a-122">주소 필터는 SOAP 메시지의 `To`를 서비스 엔드포인트의 주소에 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="9204a-123">예를 들어, `To "Urn:OtherEcho"`에 주소 지정된 메시지만 이 서비스의 세 번째 엔드포인트의 후보가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="9204a-124">계약 필터는 특정 계약의 작업과 연관된 작업을 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="9204a-125">예를 들면 `IEcho`의 작업을 가진 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="9204a-126">이 서비스의 두 번째 및 세 번째 엔드포인트가 `Echo` 계약을 호스팅하기 때문에 `IEcho`는 이러한 두 엔드포인트 모두의 계약 필터를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="9204a-127">따라서 주소 필터와 계약 필터를 조합하면 이 서비스의 `ListenUri`에 도착하는 각 메시지를 올바른 엔드포인트에 라우트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="9204a-128">세 번째 엔드포인트는 다른 엔드포인트에서 다른 주소로 보내진 메시지를 수락하기 때문에 다른 두 개와 구별됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="9204a-129">첫 번째 및 두 번째 엔드포인트는 해당 계약(들어오는 메시지의 작업)에 기초하여 서로 구별됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="9204a-130">클라이언트</span><span class="sxs-lookup"><span data-stu-id="9204a-130">Client</span></span>  

 <span data-ttu-id="9204a-131">서버의 엔드포인트가 두 개의 다른 주소를 가진 것처럼 클라이언트 엔드포인트도 두 개의 주소를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="9204a-132">서버 및 클라이언트 모두에서 논리 주소를 `EndpointAddress`라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="9204a-133">그러나 서버에서 물리 주소를 `ListenUri`라고 하는 것과 달리 클라이언트에서는 물리 주소를 `Via`라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="9204a-134">서버에서와 같이 기본적으로 이러한 두 주소는 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="9204a-135">엔드포인트 주소와 다른 클라이언트의 `Via`를 지정하려면 `ClientViaBehavior`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```csharp  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="9204a-136">일반적인 경우와 같이 주소는 Svcutil.exe에 의해 생성된 클라이언트 구성 파일에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="9204a-137">서비스의 `Via`에 해당하는 `ListenUri`는 서비스의 메타데이터에 나타나지 않으므로 이 정보는 서비스의 메타데이터 주소와 같이 out-of-band로 클라이언트에 전달되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="9204a-138">이 샘플에서 클라이언트는 서버의 세 개 엔드포인트가 모두 동일한 `Via`를 가진 경우에도 이러한 엔드포인트와 통신하고 구별할 수 있다는 것을 보여 주기 위해 각 엔드포인트에 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9204a-139">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="9204a-139">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9204a-140">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9204a-141">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9204a-142">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="9204a-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9204a-143">다중 컴퓨터 구성의 경우 Client.cs 파일의 localhost를 서비스 컴퓨터의 이름으로 대체해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9204a-144">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9204a-145">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9204a-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9204a-146">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9204a-147">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9204a-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
