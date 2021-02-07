---
description: '자세한 정보: 검색 찾기 및 FindCriteria'
title: 찾기 및 FindCriteria
ms.date: 03/30/2017
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
ms.openlocfilehash: 3a4428a89ba4122f528d1c01e4b5a6b8ea8d2935
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99756320"
---
# <a name="discovery-find-and-findcriteria"></a><span data-ttu-id="690fa-103">찾기 및 FindCriteria</span><span class="sxs-lookup"><span data-stu-id="690fa-103">Discovery Find and FindCriteria</span></span>

<span data-ttu-id="690fa-104">찾기 작업은 하나 이상의 서비스를 검색하는 클라이언트에 의해 시작되며 검색 작업의 주요 동작 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-104">A discovery find operation is initiated by a client to discover one or more services and is one of the main actions in discovery.</span></span> <span data-ttu-id="690fa-105">찾기를 수행하면 네트워크를 통해 WS-Discovery Probe 메시지가 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-105">Performing a find sends a WS-Discovery Probe message over the network.</span></span> <span data-ttu-id="690fa-106">지정된 조건과 일치하는 서비스는 WS-Discovery ProbeMatch 메시지를 사용하여 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-106">Services that match the criteria specified reply with WS-Discovery ProbeMatch messages.</span></span> <span data-ttu-id="690fa-107">검색 메시지에 대 한 자세한 내용은 [WS 검색 사양을](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="690fa-107">For more information about discovery messages, see the [WS-Discovery specification](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf).</span></span>

## <a name="discoveryclient"></a><span data-ttu-id="690fa-108">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="690fa-108">DiscoveryClient</span></span>

<span data-ttu-id="690fa-109"><xref:System.ServiceModel.Discovery.DiscoveryClient> 클래스는 찾기 작업을 수행하는 메커니즘을 제공하고 검색 클라이언트 작업을 손쉽게 수행할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-109">The <xref:System.ServiceModel.Discovery.DiscoveryClient> class provides the mechanism to perform find operations and makes performing discovery client operations easy.</span></span> <span data-ttu-id="690fa-110">여기에는 동기(블로킹) 찾기를 수행하는 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 메서드와 비동기(비블로킹) 찾기를 시작하는 <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-110">It contains a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method, which performs a (blocking) synchronous find, and a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method, which initiates a non-blocking asynchronous find.</span></span> <span data-ttu-id="690fa-111">두 메서드는 모두 <xref:System.ServiceModel.Discovery.FindCriteria> 매개 변수를 사용하며 <xref:System.ServiceModel.Discovery.FindResponse> 개체를 통해 결과를 사용자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-111">Both methods take a <xref:System.ServiceModel.Discovery.FindCriteria> parameter, and provide results to the user through a <xref:System.ServiceModel.Discovery.FindResponse> object.</span></span>

## <a name="findcriteria"></a><span data-ttu-id="690fa-112">FindCriteria</span><span class="sxs-lookup"><span data-stu-id="690fa-112">FindCriteria</span></span>

<span data-ttu-id="690fa-113"><xref:System.ServiceModel.Discovery.FindCriteria>에는 찾을 서비스를 지정하는 검색 조건 및 검색 지속 기간을 지정하는 찾기 종료 조건으로 그룹화할 수 있는 여러 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-113"><xref:System.ServiceModel.Discovery.FindCriteria> has several properties, which can be grouped into search criteria, which specify what services you are looking for, and find termination criteria (how long the search should last).</span></span> <span data-ttu-id="690fa-114"><xref:System.ServiceModel.Discovery.FindCriteria>에는 여러 개의 검색 조건이 포함되어 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-114">A <xref:System.ServiceModel.Discovery.FindCriteria> can contain multiple search criteria.</span></span> <span data-ttu-id="690fa-115">기본적으로 서비스는 이러한 모든 검색 조건과 일치해야 합니다. 그렇지 않으면 스스로를 일치하는 서비스로 간주하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-115">By default, the service has to match all of the components otherwise it does not consider itself a matching service.</span></span> <span data-ttu-id="690fa-116">일부 조건만 일치하는 서비스를 찾으려면 서비스에 대해 사용자 지정 찾기 논리를 구현하거나 여러 쿼리를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-116">If you want to find services that only match some of the criteria, you can implement custom find logic on the service or you can use multiple queries.</span></span>

<span data-ttu-id="690fa-117">검색 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-117">Search criteria include:</span></span>

- <span data-ttu-id="690fa-118"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - 선택적 요소로서,</span><span class="sxs-lookup"><span data-stu-id="690fa-118"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - Optional.</span></span> <span data-ttu-id="690fa-119">검색할 서비스의 계약 이름이거나 서비스를 검색할 때 일반적으로 사용되는 조건입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-119">The contract name of the service being searched for and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="690fa-120">둘 이상의 계약 이름이 지정되면 모든 계약과 일치하는 서비스 엔드포인트만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-120">If more than one contract name is specified, only service endpoints matching ALL contracts reply.</span></span> <span data-ttu-id="690fa-121">WCF에서 끝점은 하나의 계약만 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-121">Note that in WCF an endpoint can only support one contract.</span></span>

- <span data-ttu-id="690fa-122"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - 선택적 요소로서,</span><span class="sxs-lookup"><span data-stu-id="690fa-122"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - Optional.</span></span> <span data-ttu-id="690fa-123">개별 서비스 엔드포인트를 분류하는 데 사용되는 절대 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-123">Scopes are absolute URIs that are used to categorize individual service endpoints.</span></span> <span data-ttu-id="690fa-124">여러 엔드포인트가 동일한 계약을 노출하는 상태에서 엔드포인트의 하위 집합을 검색하려는 경우 이 조건을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-124">You may want to use this in scenarios where multiple endpoints expose the same contract and you want a way to search for a subset of the endpoints.</span></span> <span data-ttu-id="690fa-125">둘 이상의 범위가 지정되면 모든 범위와 일치하는 서비스 엔드포인트만 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-125">If more than one scope is specified, only service endpoints matching ALL scopes reply.</span></span>

- <span data-ttu-id="690fa-126"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Probe 메시지의 범위와 엔드포인트의 범위를 일치시키는 동안 사용할 일치 알고리즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-126"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Specifies the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span> <span data-ttu-id="690fa-127">다음과 같은 다섯 가지 범위 일치 규칙이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-127">There are five supported scope-matching rules:</span></span>

  - <span data-ttu-id="690fa-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType>는 기본 대/소문자 구분 문자열 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> does a basic case-sensitive string comparison.</span></span>

  - <span data-ttu-id="690fa-129"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> "/"로 구분 된 세그먼트로 일치 합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-129"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> matches by segments separated by "/".</span></span> <span data-ttu-id="690fa-130">검색은 `http://contoso/building1` 범위가 있는 서비스와 일치 `http://contoso/building/floor1` 합니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-130">A search for `http://contoso/building1` matches a service with scope `http://contoso/building/floor1`.</span></span> <span data-ttu-id="690fa-131">`http://contoso/building100`마지막 두 세그먼트가 일치 하지 않기 때문에 일치 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-131">Note that it does not match `http://contoso/building100` because the last two segments do not match.</span></span>

  - <span data-ttu-id="690fa-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType>는 LDAP URL을 사용하여 세그먼트별로 범위를 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> matches scopes by segments using an LDAP URL.</span></span>

  - <span data-ttu-id="690fa-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType>는 UUID 문자열을 사용하여 범위를 정확히 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> matches scopes exactly using a UUID string.</span></span>

  - <span data-ttu-id="690fa-134"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType>은 범위를 지정하지 않은 서비스만 일치시킵니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-134"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> matches only those services that do not specify a scope.</span></span>

  <span data-ttu-id="690fa-135">범위 일치 규칙이 지정되지 않은 경우 <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix>가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-135">If a scope-matching rule is not specified, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> is used.</span></span>

<span data-ttu-id="690fa-136">종료 조건은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-136">Termination criteria include:</span></span>

1. <span data-ttu-id="690fa-137"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - 네트워크에서 서비스의 응답을 기다리는 최대 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-137"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - The maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="690fa-138">기본 시간은 20초입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-138">The default duration is 20 seconds.</span></span>

2. <span data-ttu-id="690fa-139"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - 기다릴 응답의 최대 수입니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-139"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - The maximum number of replies to wait for.</span></span> <span data-ttu-id="690fa-140"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A>이 경과하기 전에 <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> 응답을 받으면 찾기 작업이 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-140">If <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> replies are received before <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed, the find operation ends.</span></span>

## <a name="findresponse"></a><span data-ttu-id="690fa-141">FindResponse</span><span class="sxs-lookup"><span data-stu-id="690fa-141">FindResponse</span></span>

<span data-ttu-id="690fa-142"><xref:System.ServiceModel.Discovery.FindResponse>에는 네트워크에서 일치하는 서비스가 보낸 응답을 포함하는 <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> 컬렉션 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-142"><xref:System.ServiceModel.Discovery.FindResponse> has an <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> collection property that contains any replies sent by matching services on the network.</span></span> <span data-ttu-id="690fa-143">응답하는 서비스가 없으면 컬렉션이 비어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-143">If no services replied, the collection is empty.</span></span> <span data-ttu-id="690fa-144">하나 이상의 서비스가 응답하면 서비스 주소 및 계약을 비롯한 서비스에 대한 일부 추가 정보가 포함된 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 개체에 각 응답이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-144">If one or more services replied, each reply is stored in an <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> object, which contains the address, contract, and some additional information about the service.</span></span>

<span data-ttu-id="690fa-145">다음 예제에서는 코드에서 찾기 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="690fa-145">The following example shows how to perform a find operation in code.</span></span>

```csharp
// Create DiscoveryClient
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());

// Create FindCriteria
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));
findCriteria.Duration = TimeSpan.FromSeconds(10);

// Find ICalculatorService endpoints
FindResponse findResponse = discoveryClient.Find(findCriteria);

Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)
```

## <a name="see-also"></a><span data-ttu-id="690fa-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="690fa-146">See also</span></span>

- [<span data-ttu-id="690fa-147">WCF Discovery 개요</span><span class="sxs-lookup"><span data-stu-id="690fa-147">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="690fa-148">Discovery 클라이언트 채널 사용</span><span class="sxs-lookup"><span data-stu-id="690fa-148">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
- [<span data-ttu-id="690fa-149">범위를 사용한 검색</span><span class="sxs-lookup"><span data-stu-id="690fa-149">Discovery with Scopes</span></span>](../samples/discovery-with-scopes-sample.md)
- [<span data-ttu-id="690fa-150">기본</span><span class="sxs-lookup"><span data-stu-id="690fa-150">Basic</span></span>](../samples/basic-sample.md)
