---
description: '자세한 정보: 사용자 지정 스트림 업그레이드'
title: 사용자 지정 스트림 업그레이드
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: fe52b99de382d5a5d5b41a0bff2c4a9a7698f6f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735246"
---
# <a name="custom-stream-upgrades"></a><span data-ttu-id="2e916-103">사용자 지정 스트림 업그레이드</span><span class="sxs-lookup"><span data-stu-id="2e916-103">Custom Stream Upgrades</span></span>

<span data-ttu-id="2e916-104">TCP, 명명된 파이프 등의 스트림 지향 전송은 클라이언트와 서버 간의 연속 바이트 스트림에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-104">Stream-oriented transports such as TCP and Named Pipes operate on a continuous stream of bytes between the client and server.</span></span> <span data-ttu-id="2e916-105">이 스트림은 <xref:System.IO.Stream> 개체에 의해 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-105">This stream is realized by a  <xref:System.IO.Stream> object.</span></span> <span data-ttu-id="2e916-106">스트림 업그레이드에서 클라이언트는 선택적 프로토콜 계층을 채널 스택에 추가하려고 하고 통신 채널의 반대쪽에서도 추가하도록 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-106">In a stream upgrade, the client wants to add an optional protocol layer to the channel stack, and asks the other end of the communication channel to do so.</span></span> <span data-ttu-id="2e916-107">스트림 업그레이드는 원래 <xref:System.IO.Stream> 개체를 업그레이드된 개체로 바꾸는 과정으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-107">The stream upgrade consists in replacing the original <xref:System.IO.Stream> object with an upgraded one.</span></span>  
  
 <span data-ttu-id="2e916-108">예를 들어 전송 스트림 바로 위에 압축 스트림을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-108">For example, you can build a compression stream directly on top of the transport stream.</span></span> <span data-ttu-id="2e916-109">이 경우 원래 전송 <xref:System.IO.Stream>은 원래 스트림을 중심으로 압축 <xref:System.IO.Stream>을 래핑하는 스트림으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-109">In this case the original transport <xref:System.IO.Stream> is replaced with one that wraps the compression <xref:System.IO.Stream> around the original one.</span></span>  
  
 <span data-ttu-id="2e916-110">각각 이전 업그레이드를 래핑하여 여러 스트림 업그레이드를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-110">You can apply multiple stream upgrades, each wrapping the preceding one.</span></span>  
  
## <a name="how-stream-upgrades-work"></a><span data-ttu-id="2e916-111">스트림 업그레이드의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="2e916-111">How Stream Upgrades Work</span></span>  

 <span data-ttu-id="2e916-112">스트림 업그레이드 프로세스에는 네 가지 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-112">There are four components to the stream upgrade process.</span></span>  
  
1. <span data-ttu-id="2e916-113">업그레이드 스트림 *개시자* 는 프로세스를 시작 합니다. 런타임에 채널 전송 계층을 업그레이드 하기 위해 연결의 다른 쪽 끝에 대 한 요청을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-113">An upgrade stream *Initiator* begins the process: at run-time it can initiate a request to the other end of its connection to upgrade the channel transport layer.</span></span>  
  
2. <span data-ttu-id="2e916-114">업그레이드 스트림 *수락자* 업그레이드를 수행 합니다. 런타임 시 다른 컴퓨터에서 업그레이드 요청을 수신 하 고 가능한 경우 업그레이드를 수락 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-114">An upgrade stream *Acceptor* carries out the upgrade: at run-time it receives the upgrade request from the other machine, and if possible, accepts the upgrade.</span></span>  
  
3. <span data-ttu-id="2e916-115">업그레이드 *공급자* 는 클라이언트에서 *초기자* 를 만들고 서버에 *수락자* 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-115">An upgrade *Provider* creates the *Initiator* on the client and the *Acceptor* on the server.</span></span>  
  
4. <span data-ttu-id="2e916-116">스트림 업그레이드 *바인딩 요소* 는 서비스와 클라이언트의 바인딩에 추가 되 고 런타임에 공급자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-116">A stream upgrade *Binding Element* is added to the bindings on the service and the client, and creates the provider at runtime.</span></span>  
  
 <span data-ttu-id="2e916-117">여러 업그레이드의 경우 개시자와 수락자는 상태 컴퓨터를 캡슐화하여 각 시작에 올바른 업그레이드 전환을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-117">Note that in the case of multiple upgrades, the Initiator and Acceptor encapsulate state machines to enforce which upgrade transitions are valid for each Initiation.</span></span>  
  
## <a name="how-to-implement-a-stream-upgrade"></a><span data-ttu-id="2e916-118">스트림 업그레이드 구현 방법</span><span class="sxs-lookup"><span data-stu-id="2e916-118">How to Implement a Stream Upgrade</span></span>  

 <span data-ttu-id="2e916-119">WCF (Windows Communication Foundation)에서는 `abstract` 구현할 수 있는 네 가지 클래스를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-119">Windows Communication Foundation (WCF) provides four `abstract` classes that you can implement:</span></span>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 <span data-ttu-id="2e916-120">사용자 지정 스트림 업그레이드를 구현하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-120">To implement a custom stream upgrade, do the following.</span></span> <span data-ttu-id="2e916-121">이 절차에서는 클라이언트 및 서버 컴퓨터 둘 다에 최소 스트림 업그레이드 프로세스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-121">This procedure implements a minimal stream upgrade process on both the client and server machines.</span></span>  
  
1. <span data-ttu-id="2e916-122"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator>를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-122">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.</span></span>  
  
    1. <span data-ttu-id="2e916-123"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> 메서드를 재정의하여 업그레이드할 스트림을 사용하고 업그레이드된 스트림을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-123">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="2e916-124">이 메서드는 동기적으로 작동합니다. 비동기적으로 업그레이드를 시작하는 유사한 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-124">This method works synchronously; there are analogous methods to initiate the upgrade asynchronously.</span></span>  
  
    2. <span data-ttu-id="2e916-125"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> 메서드를 재정의하여 추가 업그레이드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-125">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to check for additional upgrades.</span></span>  
  
2. <span data-ttu-id="2e916-126"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-126">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.</span></span>  
  
    1. <span data-ttu-id="2e916-127"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> 메서드를 재정의하여 업그레이드할 스트림을 사용하고 업그레이드된 스트림을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-127">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="2e916-128">이 메서드는 동기적으로 작동합니다. 비동기적으로 업그레이드를 수락하는 유사한 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-128">This method works synchronously; there are analogous methods to accept the upgrade asynchronously.</span></span>  
  
    2. <span data-ttu-id="2e916-129"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> 메서드를 재정의하여 업그레이드 프로세스의 이 시점에서 이 업그레이드 수락자가 요청된 업그레이드를 지원하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-129">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method to determine if the upgrade requested is supported by this upgrade acceptor at this point in the upgrade process.</span></span>  
  
3. <span data-ttu-id="2e916-130"><xref:System.ServiceModel.Channels.StreamUpgradeProvider>를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-130">Create a class the implements <xref:System.ServiceModel.Channels.StreamUpgradeProvider>.</span></span> <span data-ttu-id="2e916-131"><xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> 및 <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> 메서드를 재정의하여 2단계와 1단계에서 정의된 수락자와 개시자의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-131">Override the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> and the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> methods to return instances of the acceptor and initiator defined in steps 2 and 1.</span></span>  
  
4. <span data-ttu-id="2e916-132"><xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>를 구현하는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-132">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.</span></span>  
  
    1. <span data-ttu-id="2e916-133">클라이언트의 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> 메서드와 서비스의 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-133">Override the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> method on the client and the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> method on the service.</span></span>  
  
    2. <span data-ttu-id="2e916-134">클라이언트의 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 메서드와 서비스의 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> 메서드를 재정의하여 업그레이드 바인딩 요소를 <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-134">Override the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> method on the client and the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> method on the service to add the upgrade Binding Element to <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.</span></span>  
  
5. <span data-ttu-id="2e916-135">서버 및 클라이언트 컴퓨터의 바인딩에 새 스트림 업그레이드 바인딩 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-135">Add the new stream upgrade binding element to bindings on the server and client machines.</span></span>  
  
## <a name="security-upgrades"></a><span data-ttu-id="2e916-136">보안 업그레이드</span><span class="sxs-lookup"><span data-stu-id="2e916-136">Security Upgrades</span></span>  

 <span data-ttu-id="2e916-137">보안 업그레이드 추가는 일반적인 스트림 업그레이드 프로세스의 특수화된 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-137">Adding a security upgrade is a specialized version of the general stream upgrade process.</span></span>  
  
 <span data-ttu-id="2e916-138">WCF는 스트림 보안을 업그레이드 하기 위한 두 개의 바인딩 요소를 이미 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-138">WCF already provides two binding elements for upgrading stream security.</span></span> <span data-ttu-id="2e916-139">전송 수준 보안의 구성은 구성하여 사용자 지정 바인딩에 추가할 수 있는 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> 및 <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>에 의해 캡슐화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-139">The configuration of transport-level security is encapsulated by the <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> and the <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> which can be configured and added to a custom binding.</span></span> <span data-ttu-id="2e916-140">이러한 바인딩 요소는 클라이언트 및 서버 스트림 업그레이드 공급자를 빌드하는 <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> 클래스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-140">These binding elements extend the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> class that builds the client and server stream upgrade providers.</span></span> <span data-ttu-id="2e916-141">두 바인딩 요소에는 특수화된 보안 스트림 업그레이드 공급자 클래스를 만드는 메서드가 있습니다. 이 메서드는 `public`이 아니므로 두 경우 모두 바인딩 요소를 바인딩에 추가하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-141">These binding elements have methods that create the specialized security stream upgrade provider classes, which are not `public`, so for these two cases all you need to do is to add the binding element to the binding.</span></span>  
  
 <span data-ttu-id="2e916-142">위의 두 바인딩 요소가 만족하지 않는 보안 시나리오의 경우 위의 개시자, 수락자 및 공급자 기본 클래스에서 보안과 관련된 세 개의 `abstract` 클래스가 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-142">For security scenarios not met by the above two binding elements, three security-related `abstract` classes are derived from the above initiator, acceptor and provider base classes:</span></span>  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 <span data-ttu-id="2e916-143">보안 스트림 업그레이드를 구현하는 프로세스는 이러한 세 클래스에서 파생된다는 차이를 제외하고 이전과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-143">The process of implementing a security stream upgrade is the same as before, with the difference that you would derive from these three classes.</span></span> <span data-ttu-id="2e916-144">이 클래스의 추가 속성을 재정의하여 런타임에 보안 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-144">Override the additional properties in these classes to supply security information to the runtime.</span></span>  
  
## <a name="multiple-upgrades"></a><span data-ttu-id="2e916-145">여러 업그레이드</span><span class="sxs-lookup"><span data-stu-id="2e916-145">Multiple Upgrades</span></span>  

 <span data-ttu-id="2e916-146">추가 업그레이드를 만들려면 요청이 위의 프로세스를 반복합니다. <xref:System.ServiceModel.Channels.StreamUpgradeProvider> 및 바인딩 요소의 추가 확장을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-146">To create additional upgrade requests repeat the above process: create additional extensions of <xref:System.ServiceModel.Channels.StreamUpgradeProvider> and binding elements.</span></span> <span data-ttu-id="2e916-147">바인딩에 바인딩 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-147">Add the binding elements to the binding.</span></span> <span data-ttu-id="2e916-148">추가 바인딩 요소는 바인딩에 추가된 첫 번째 바인딩 요소에서 시작하여 순차적으로 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-148">The additional binding elements are processed sequentially, starting with the first binding element added to the binding.</span></span> <span data-ttu-id="2e916-149"><xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> 및<xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>에서 각 업그레이드 공급자는 기존의 업그레이드 바인딩 매개 변수에 해당 공급자의 계층을 설정하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-149">In <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> and <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> each upgrade provider can determine how to layer itself on any pre-existing upgrade binding parameters.</span></span> <span data-ttu-id="2e916-150">그런 다음 기존의 업그레이드 바인딩 매개 변수를 새 복합 업그레이드 바인딩 매개 변수로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-150">It should then replace the existing upgrade binding parameter with a new composite upgrade binding parameter.</span></span>  
  
 <span data-ttu-id="2e916-151">또는 한 업그레이드 공급자가 여러 업그레이드를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-151">Alternatively, one upgrade provider can support multiple upgrades.</span></span> <span data-ttu-id="2e916-152">예를 들어 보안과 압축을 모두 지원하는 사용자 지정 스트림 업그레이드 공급자를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-152">For example, you might want to implement a custom stream upgrade provider that supports both security and compression.</span></span> <span data-ttu-id="2e916-153">다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-153">Do the following steps:</span></span>  
  
1. <span data-ttu-id="2e916-154">개시자와 수락자를 만드는 공급자 클래스를 쓰도록 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>를 서브클래싱합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-154">Subclass <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> to write the provider class that creates the Initiator and Acceptor.</span></span>  
  
2. <span data-ttu-id="2e916-155">압축 스트림과 보안 스트림의 콘텐츠 형식을 순서대로 반환하도록 <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> 메서드를 재정의하여 <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A>를 서브클래싱합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-155">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> making sure to override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to return the content types for the compression stream and the secure stream in order.</span></span>  
  
3. <span data-ttu-id="2e916-156"><xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> 메서드의 사용자 지정 콘텐츠 형식을 이해하는 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>를 서브클래싱합니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-156">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> that understands the custom content types in its <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method.</span></span>  
  
4. <span data-ttu-id="2e916-157"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> 및 <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>에 대한 각 호출 후에 스트림이 업그레이드됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e916-157">The stream will be upgraded after each call to <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> and <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e916-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e916-158">See also</span></span>

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
