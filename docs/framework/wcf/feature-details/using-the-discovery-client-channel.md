---
description: '자세한 정보: 검색 클라이언트 채널 사용'
title: Discovery 클라이언트 채널 사용
ms.date: 03/30/2017
ms.assetid: 1494242a-1d64-4035-8ecd-eb4f06c8d2ba
ms.openlocfilehash: f83068c248ab8e2f1e2b3bfba3eb29fcf8aa20ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779662"
---
# <a name="using-the-discovery-client-channel"></a><span data-ttu-id="57f4f-103">Discovery 클라이언트 채널 사용</span><span class="sxs-lookup"><span data-stu-id="57f4f-103">Using the Discovery Client Channel</span></span>

<span data-ttu-id="57f4f-104">WCF 클라이언트 애플리케이션을 작성하는 경우 호출할 서비스의 엔드포인트 주소를 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-104">When writing a WCF client application you need to know the endpoint address of the service you are calling.</span></span> <span data-ttu-id="57f4f-105">대부분의 경우 서비스의 엔드포인트 주소를 미리 알 수 없거나 시간 경과에 따라 서비스의 주소가 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-105">In many situations the endpoint address of a service is not known in advance or the address of the service changes over time.</span></span> <span data-ttu-id="57f4f-106">Discovery 클라이언트 채널을 사용하면 WCF 클라이언트 애플리케이션을 작성하고 호출할 서비스를 설명할 수 있습니다. 그러면 클라이언트 채널이 자동으로 프로브 요청을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-106">The Discovery Client Channel allows you to write a WCF client application, describe the service you want to call, and the client channel automatically sends a probe request.</span></span> <span data-ttu-id="57f4f-107">서비스가 응답하면 Discovery 클라이언트 채널은 프로브 응답에서 서비스의 엔드포인트 주소를 검색하고 이를 사용하여 서비스를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-107">When a service responds, the discovery client channel retrieves the endpoint address for the service from the probe response and uses it to call the service.</span></span>  
  
## <a name="using-the-discovery-client-channel"></a><span data-ttu-id="57f4f-108">Discovery 클라이언트 채널 사용</span><span class="sxs-lookup"><span data-stu-id="57f4f-108">Using the Discovery Client Channel</span></span>  

 <span data-ttu-id="57f4f-109">Discovery 클라이언트 채널을 사용하려면 클라이언트 채널 스택에 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>의 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-109">To use the Discovery Client Channel, add an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your client channel stack.</span></span> <span data-ttu-id="57f4f-110">또는 <xref:System.ServiceModel.Discovery.DynamicEndpoint>을 사용할 수도 있습니다. 그러면 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>가 아직 없는 경우 바인딩에 자동으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-110">Alternatively you can use the <xref:System.ServiceModel.Discovery.DynamicEndpoint> and a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is automatically added to your binding if not already present.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="57f4f-111"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>를 클라이언트 채널 스택의 맨 위에 추가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-111">It is recommended that the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> is the top-most element on your client channel stack.</span></span> <span data-ttu-id="57f4f-112"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>의 맨 위에 추가되는 바인딩 요소는 자신이 만드는 <xref:System.ServiceModel.ChannelFactory> 또는 채널이 엔드포인트 주소나 `Via` 주소(`CreateChannel` 메서드에 전달됨)를 사용하지 않는지 확인해야 합니다. 이는 이러한 주소에 올바른 주소가 포함되지 않을 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-112">Any binding element that is added on top of the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> must make sure that the <xref:System.ServiceModel.ChannelFactory> or channel it creates does not use the endpoint address or `Via` address (passed to the `CreateChannel` method) because they may not contain the correct address.</span></span>  
  
 <span data-ttu-id="57f4f-113"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 클래스에는 다음 두 개의 공용 속성이 들어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-113">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> class contains two public properties:</span></span>  
  
1. <span data-ttu-id="57f4f-114">호출할 서비스를 설명하는 데 사용되는 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A></span><span class="sxs-lookup"><span data-stu-id="57f4f-114"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.FindCriteria%2A>, which is used to describe the service you want to call.</span></span>  
  
2. <span data-ttu-id="57f4f-115"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> 검색 메시지를 보낼 검색 끝점을 지정 하는입니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-115"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> which specifies the discovery endpoint to send discovery messages to.</span></span>  
  
 <span data-ttu-id="57f4f-116"><xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> 속성을 사용하면 검색할 서비스 계약, 필요한 모든 범위 URI 및 채널 열기를 시도하는 최대 횟수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-116">The <xref:System.ServiceModel.Discovery.FindCriteria.%23ctor%2A> property allows you to specify the service contract you are searching for, any required scope URIs, and the maximum number of time to attempt to open the channel.</span></span> <span data-ttu-id="57f4f-117">계약 형식은 생성자를 호출 하 여 지정 합니다  <xref:System.ServiceModel.Discovery.FindCriteria> .</span><span class="sxs-lookup"><span data-stu-id="57f4f-117">The contract type is specified by calling the constructor  <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span> <span data-ttu-id="57f4f-118">범위 URI는 <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> 속성에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-118">Scope URIs can be added to the <xref:System.ServiceModel.Discovery.FindCriteria.Scopes%2A> property.</span></span> <span data-ttu-id="57f4f-119"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> 속성을 사용하면 클라이언트가 연결을 시도하는 최대 결과 수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-119">The <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> property allows you to specify the maximum number of results to which the client tries to connect to.</span></span> <span data-ttu-id="57f4f-120">프로브 응답을 받으면 클라이언트는 프로브 응답의 엔드포인트 주소를 사용하여 채널을 열려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-120">When a probe response is received the client attempts to open the channel using the endpoint address from the probe response.</span></span> <span data-ttu-id="57f4f-121">예외가 발생하면 클라이언트는 다음 프로브 응답으로 이동하고 필요한 경우 더 많은 응답이 수신될 때까지 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-121">If an exception occurs the client moves on to the next probe response, waiting for more responses to be received if necessary.</span></span> <span data-ttu-id="57f4f-122">클라이언트는 채널이 성공적으로 열리거나 최대 결과 수에 도달할 때까지 이 작업을 계속 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-122">It continues to do this until the channel is successfully opened or the maximum number of results is reached.</span></span> <span data-ttu-id="57f4f-123">이러한 설정에 대한 자세한 내용은 <xref:System.ServiceModel.Discovery.FindCriteria>을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="57f4f-123">For more information about these settings, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>  
  
 <span data-ttu-id="57f4f-124">ph x="1" /&gt; 속성을 사용하면 사용할 검색 엔드포인트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-124">The <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement.DiscoveryEndpointProvider%2A> property allows you to specify the discovery endpoint to use.</span></span> <span data-ttu-id="57f4f-125">일반적으로 이 엔드포인트는 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>이지만 유효한 모든 엔드포인트일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-125">Normally this is a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, but it can be any valid endpoint.</span></span>  
  
 <span data-ttu-id="57f4f-126">서비스와 통신하기 위해 사용할 바인딩을 만들 때는 해당 서비스와 똑같은 바인딩을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-126">When you are creating the binding to use to communicate with the service, you must be careful to use the exact same binding as the service.</span></span> <span data-ttu-id="57f4f-127">유일한 차이점은 클라이언트 바인딩에는 스택의 최상위 요소인 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>가 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-127">The only difference is the client binding has a <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> on the top of the stack.</span></span> <span data-ttu-id="57f4f-128">서비스에서 시스템 제공 바인딩을 사용하는 경우 새 <xref:System.ServiceModel.Channels.CustomBinding>을 만들고 시스템 제공 바인딩을 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 생성자에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-128">If service is using one of the system-provided bindings, create a new <xref:System.ServiceModel.Channels.CustomBinding> and pass in the system-provided binding to the <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> constructor.</span></span> <span data-ttu-id="57f4f-129">그러면 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> 속성에 대해 `Insert`를 호출하여 <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A>를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-129">Then you can add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> by calling `Insert` on the <xref:System.ServiceModel.Channels.CustomBinding.Elements%2A> property.</span></span>  
  
 <span data-ttu-id="57f4f-130"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>를 바인딩에 추가하고 구성한 후에는 WCF 클라이언트 클래스의 인스턴스를 만들어서 연 다음 해당 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-130">Once you have added the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement> to your binding and configured it, you can create an instance of the WCF client class, open it, and call its methods.</span></span> <span data-ttu-id="57f4f-131">다음 예제에서는 Discovery 클라이언트 채널을 사용하여 `ICalculator` 클래스(WCF 시작 자습서에 사용됨)를 구현하고 해당 `Add` 메서드를 호출하는 WCF 서비스를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-131">The following example uses the Discovery Client Channel to discover a WCF service that implements the `ICalculator` class (used in the Getting Started WCF tutorial) and calls its `Add` method.</span></span>  
  
```csharp
// Create the DiscoveryClientBindingElement  
DiscoveryClientBindingElement bindingElement = new DiscoveryClientBindingElement();  
// Search for a service that implements the ICalculator interface, attempting to open  
// the channel a maximum of 2 times  
bindingElement.FindCriteria = new FindCriteria(typeof(ICalculator)) { MaxResults = 2 };  
// Use the UdpDiscoveryEndpoint  
bindingElement.DiscoveryEndpoint = new UdpDiscoveryEndpoint();  
  
// The service uses the BasicHttpBinding, so use that and insert the DiscoveryClientBindingElement at the
// top of the stack  
CustomBinding binding = new CustomBinding(new BasicHttpBinding());  
binding.Elements.Insert(0,bindingElement);  
  
try  
{  
    // Create the WCF client and call a method  
    CalculatorClient client = new CalculatorClient(binding, new EndpointAddress("http://schemas.microsoft.com/dynamic"));  
    client.Open();  
    client.Add(1, 1);  
}  
catch (EndpointNotFoundException ex)  
{  
    Console.WriteLine("An exception occurred: " + ex.Message);  
}  
```  
  
## <a name="security-and-the-discovery-client-channel"></a><span data-ttu-id="57f4f-132">보안 및 Discovery 클라이언트 채널</span><span class="sxs-lookup"><span data-stu-id="57f4f-132">Security and the Discovery Client Channel</span></span>  

 <span data-ttu-id="57f4f-133">Discovery 클라이언트 채널을 사용하는 경우 두 개의 엔드포인트가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-133">When using the discovery client channel, two endpoints are being specified.</span></span> <span data-ttu-id="57f4f-134">하나는 대개 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>인 검색 메시지에 사용되고, 다른 하나는 애플리케이션 엔드포인트입니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-134">One is used for discovery messages, usually <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, and the other is the application endpoint.</span></span> <span data-ttu-id="57f4f-135">보안 서비스를 구현할 때는 이러한 두 엔드포인트에 보안을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="57f4f-135">When implementing a secure service, care must be taken to secure both endpoints.</span></span> <span data-ttu-id="57f4f-136">보안에 대 한 자세한 내용은 [서비스 및 클라이언트 보안](securing-services-and-clients.md)설정을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57f4f-136">For more information about security, see [Securing Services and Clients](securing-services-and-clients.md).</span></span>
