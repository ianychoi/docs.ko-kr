---
description: '자세한 정보: 방법: 검색 프록시 구현'
title: '방법: 검색 프록시 구현'
ms.date: 03/30/2017
ms.assetid: 78d70e0a-f6c3-4cfb-a7ca-f66ebddadde0
ms.openlocfilehash: e7bd9833ac0d449eefd5e439b442ecb0eee121ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793755"
---
# <a name="how-to-implement-a-discovery-proxy"></a><span data-ttu-id="d5c2c-103">방법: 검색 프록시 구현</span><span class="sxs-lookup"><span data-stu-id="d5c2c-103">How to: Implement a Discovery Proxy</span></span>

<span data-ttu-id="d5c2c-104">이 항목에서는 검색 프록시를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-104">This topic explains how to implement a discovery proxy.</span></span> <span data-ttu-id="d5c2c-105">WCF (Windows Communication Foundation)의 검색 기능에 대 한 자세한 내용은 [Wcf 검색 개요](wcf-discovery-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-105">For more information about the discovery feature in Windows Communication Foundation (WCF), see [WCF Discovery Overview](wcf-discovery-overview.md).</span></span> <span data-ttu-id="d5c2c-106">검색 프록시는 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 추상 클래스를 확장하는 클래스를 만들어 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-106">A discovery proxy can be implemented by creating a class that extends the <xref:System.ServiceModel.Discovery.DiscoveryProxy> abstract class.</span></span> <span data-ttu-id="d5c2c-107">이 샘플에서는 많은 다른 지원 클래스가 정의되고 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-107">There are a number of other support classes defined and used in this sample.</span></span> <span data-ttu-id="d5c2c-108">`OnResolveAsyncResult`, `OnFindAsyncResult`및 `AsyncResult`.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-108">`OnResolveAsyncResult`, `OnFindAsyncResult`, and `AsyncResult`.</span></span> <span data-ttu-id="d5c2c-109">이러한 클래스는 <xref:System.IAsyncResult> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-109">These classes implement the <xref:System.IAsyncResult> interface.</span></span> <span data-ttu-id="d5c2c-110">에 대 한 자세한 <xref:System.IAsyncResult> 내용은 [system.web 인터페이스](xref:System.IAsyncResult)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-110">For more information about <xref:System.IAsyncResult> see [System.IAsyncResult interface](xref:System.IAsyncResult).</span></span>

 <span data-ttu-id="d5c2c-111">이 항목에서는 검색 프록시 구현을 크게 다음 세 부분으로 나누어서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-111">Implementing a discovery proxy is broken down into three main parts in this topic:</span></span>

- <span data-ttu-id="d5c2c-112">데이터 저장소를 포함하고 <xref:System.ServiceModel.Discovery.DiscoveryProxy> 추상 클래스를 확장하는 클래스 정의</span><span class="sxs-lookup"><span data-stu-id="d5c2c-112">Define a class that contains a data store and extends the abstract <xref:System.ServiceModel.Discovery.DiscoveryProxy> class.</span></span>

- <span data-ttu-id="d5c2c-113">`AsyncResult` 도우미 클래스 구현</span><span class="sxs-lookup"><span data-stu-id="d5c2c-113">Implement the helper `AsyncResult` class.</span></span>

- <span data-ttu-id="d5c2c-114">검색 프록시 호스팅</span><span class="sxs-lookup"><span data-stu-id="d5c2c-114">Host the Discovery Proxy.</span></span>

### <a name="to-create-a-new-console-application-project"></a><span data-ttu-id="d5c2c-115">새 콘솔 애플리케이션 프로젝트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-115">To create a new console application project</span></span>

1. <span data-ttu-id="d5c2c-116">Visual Studio 2012를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-116">Start Visual Studio 2012.</span></span>

2. <span data-ttu-id="d5c2c-117">새 콘솔 애플리케이션 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-117">Create a new console application project.</span></span> <span data-ttu-id="d5c2c-118">프로젝트 이름을 `DiscoveryProxy`로 지정하고 솔루션 이름을 `DiscoveryProxyExample`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-118">Name the project `DiscoveryProxy` and the name the solution `DiscoveryProxyExample`.</span></span>

3. <span data-ttu-id="d5c2c-119">프로젝트에 대한 다음 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-119">Add the following references to the project</span></span>

    1. <span data-ttu-id="d5c2c-120">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="d5c2c-120">System.ServiceModel.dll</span></span>

    2. <span data-ttu-id="d5c2c-121">System.Servicemodel.Discovery.dll</span><span class="sxs-lookup"><span data-stu-id="d5c2c-121">System.Servicemodel.Discovery.dll</span></span>

    > [!CAUTION]
    > <span data-ttu-id="d5c2c-122">이러한 어셈블리는 4.0 이상 버전이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-122">Ensure that you reference version 4.0 or greater of these assemblies.</span></span>

### <a name="to-implement-the-proxydiscoveryservice-class"></a><span data-ttu-id="d5c2c-123">ProxyDiscoveryService 클래스를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-123">To implement the ProxyDiscoveryService class</span></span>

1. <span data-ttu-id="d5c2c-124">프로젝트에 새 코드 파일을 추가하고 이름을 DiscoveryProxy.cs로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-124">Add a new code file to your project and name it DiscoveryProxy.cs.</span></span>

2. <span data-ttu-id="d5c2c-125">DiscoveryProxy.cs에 다음 `using` 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-125">Add the following `using` statements to DiscoveryProxy.cs.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    using System.Xml;
    ```

3. <span data-ttu-id="d5c2c-126">`DiscoveryProxyService`에서 <xref:System.ServiceModel.Discovery.DiscoveryProxy>를 파생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-126">Derive the `DiscoveryProxyService` from <xref:System.ServiceModel.Discovery.DiscoveryProxy>.</span></span> <span data-ttu-id="d5c2c-127">다음 예제와 같이 이 클래스에 `ServiceBehavior` 특성을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-127">Apply the `ServiceBehavior` attribute to the class as shown in the following example.</span></span>

    ```csharp
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
    }
    ```

4. <span data-ttu-id="d5c2c-128">`DiscoveryProxy` 클래스 내에서 등록된 서비스를 저장할 사전을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-128">Inside the `DiscoveryProxy` class define a dictionary to hold the registered services.</span></span>

    ```csharp
    // Repository to store EndpointDiscoveryMetadata.
    Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;
    ```

5. <span data-ttu-id="d5c2c-129">사전을 초기화하는 생성자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-129">Define a constructor that initializes the dictionary.</span></span>

    ```csharp
    public DiscoveryProxyService()
            {
                this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
            }
    ```

### <a name="to-define-the-methods-used-to-update-the-discovery-proxy-cache"></a><span data-ttu-id="d5c2c-130">검색 프록시 캐시를 업데이트하는 데 사용되는 메서드를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-130">To define the methods used to update the discovery proxy cache</span></span>

1. <span data-ttu-id="d5c2c-131">`AddOnlineservice` 메서드를 구현하여 캐시에 서비스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-131">Implement the `AddOnlineservice` method to add services to the cache.</span></span> <span data-ttu-id="d5c2c-132">이 메서드는 프록시가 알림 메시지를 받을 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-132">This is called every time the proxy receives an announcement message.</span></span>

    ```csharp
    void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        lock (this.onlineServices)
        {
            this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
        }

        PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
    }
    ```

2. <span data-ttu-id="d5c2c-133">캐시에서 서비스를 제거하는 데 사용되는 `RemoveOnlineService` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-133">Implement the `RemoveOnlineService` method that is used to remove services from the cache.</span></span>

    ```csharp
    void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
    {
        if (endpointDiscoveryMetadata != null)
        {
            lock (this.onlineServices)
            {
                this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
        }
    }
    ```

3. <span data-ttu-id="d5c2c-134">서비스와 사전의 서비스를 일치시킬 `MatchFromOnlineService` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-134">Implement the `MatchFromOnlineService` methods that attempt to match a service with a service in the dictionary.</span></span>

    ```csharp
    void MatchFromOnlineService(FindRequestContext findRequestContext)
    {
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                {
                    findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                }
            }
        }
    }
    ```

    ```csharp
    EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
    {
        EndpointDiscoveryMetadata matchingEndpoint = null;
        lock (this.onlineServices)
        {
            foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
            {
                if (criteria.Address == endpointDiscoveryMetadata.Address)
                {
                    matchingEndpoint = endpointDiscoveryMetadata;
                }
            }
        }
        return matchingEndpoint;
    }
    ```

4. <span data-ttu-id="d5c2c-135">검색 프록시가 수행하는 작업을 콘솔에 텍스트로 출력하는 `PrintDiscoveryMetadata` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-135">Implement the `PrintDiscoveryMetadata` method that provides the user with console text output of what the discovery proxy is doing.</span></span>

    ```csharp
    void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
    {
        Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
        foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
        {
            Console.WriteLine("** " + contractName.ToString());
            break;
        }
        Console.WriteLine("**** Operation Completed");
    }
    ```

5. <span data-ttu-id="d5c2c-136">DiscoveryProxyService에 다음 AsyncResult 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-136">Add the following AsyncResult classes to the DiscoveryProxyService.</span></span> <span data-ttu-id="d5c2c-137">이러한 클래스는 다양한 비동기 작업 결과를 구별하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-137">These classes are used to differentiate between the different asynchronous operation results.</span></span>

    ```csharp
    sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
    {
        public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
    {
        public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
        }
    }

    sealed class OnFindAsyncResult : AsyncResult
    {
        public OnFindAsyncResult(AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.Complete(true);
        }

        public static void End(IAsyncResult result)
        {
            AsyncResult.End<OnFindAsyncResult>(result);
        }
    }

    sealed class OnResolveAsyncResult : AsyncResult
    {
        EndpointDiscoveryMetadata matchingEndpoint;

        public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
            : base(callback, state)
        {
            this.matchingEndpoint = matchingEndpoint;
            this.Complete(true);
        }

        public static EndpointDiscoveryMetadata End(IAsyncResult result)
        {
            OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
            return thisPtr.matchingEndpoint;
        }
    }
    ```

### <a name="to-define-the-methods-that-implement-the-discovery-proxy-functionality"></a><span data-ttu-id="d5c2c-138">검색 프록시 기능을 구현하는 메서드를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-138">To define the methods that implement the discovery proxy functionality</span></span>

1. <span data-ttu-id="d5c2c-139"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-139">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-140">이 메서드는 검색 프록시가 온라인 알림 메시지를 받을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-140">This method is called when the discovery proxy receives an online announcement message.</span></span>

    ```csharp
    // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
    protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.AddOnlineService(endpointDiscoveryMetadata);
        return new OnOnlineAnnouncementAsyncResult(callback, state);
    }
    ```

2. <span data-ttu-id="d5c2c-141"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-141">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOnlineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-142">이 메서드는 검색 프록시가 알림 메시지 처리를 완료할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-142">This method is called when the discovery proxy finishes processing an announcement message.</span></span>

    ```csharp
    protected override void OnEndOnlineAnnouncement(IAsyncResult result)
    {
        OnOnlineAnnouncementAsyncResult.End(result);
    }
    ```

3. <span data-ttu-id="d5c2c-143"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-143">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-144">이 메서드는 검색 프록시가 오프라인 알림 메시지를 받을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-144">This method is called with the discovery proxy receives an offline announcement message.</span></span>

    ```csharp
    // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
    protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
    {
        this.RemoveOnlineService(endpointDiscoveryMetadata);
        return new OnOfflineAnnouncementAsyncResult(callback, state);
    }
    ```

4. <span data-ttu-id="d5c2c-145"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-145">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndOfflineAnnouncement%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-146">이 메서드는 검색 프록시가 오프라인 알림 메시지 처리를 완료할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-146">This method is called when the discovery proxy finishes processing an offline announcement message.</span></span>

    ```csharp
    protected override void OnEndOfflineAnnouncement(IAsyncResult result)
    {
        OnOfflineAnnouncementAsyncResult.End(result);
    }
    ```

5. <span data-ttu-id="d5c2c-147"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-147">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-148">이 메서드는 검색 프록시가 찾기 요청을 받을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-148">This method is called when the discovery proxy receives a find request.</span></span>

    ```csharp
    // OnBeginFind method is called when a Probe request message is received by the Proxy
    protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
    {
        this.MatchFromOnlineService(findRequestContext);
        return new OnFindAsyncResult(callback, state);
    }
    protected override IAsyncResult OnBeginFind(FindRequest findRequest, AsyncCallback callback, object state)
    {
        Collection<EndpointDiscoveryMetadata> matchingEndpoints = MatchFromCache(findRequest.Criteria);
        return new OnFindAsyncResult(
                    matchingEndpoints,
                    callback,
                    state);
    }
    ```

6. <span data-ttu-id="d5c2c-149"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-149">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-150">이 메서드는 검색 프록시가 찾기 요청 처리를 완료할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-150">This method is called when the discovery proxy finishes processing a find request.</span></span>

    ```csharp
    protected override void OnEndFind(IAsyncResult result)
    {
        OnFindAsyncResult.End(result);
    }
    ```

7. <span data-ttu-id="d5c2c-151"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-151">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-152">이 메서드는 검색 프록시가 확인 메시지를 받을 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-152">This method is called when the discovery proxy receives a resolve message.</span></span>

    ```csharp
    // OnBeginFind method is called when a Resolve request message is received by the Proxy
    protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
    }
    protected override IAsyncResult OnBeginResolve(ResolveRequest resolveRequest, AsyncCallback callback, object state)
    {
        return new OnResolveAsyncResult(
            this.proxy.MatchFromOnlineService(resolveRequest.Criteria),
            callback,
            state);
    }
    ```

8. <span data-ttu-id="d5c2c-153"><xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-153">Override the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndResolve%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d5c2c-154">이 메서드는 검색 프록시가 확인 메시지 처리를 완료할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-154">This method is called when the discovery proxy finishes processing a resolve message.</span></span>

    ```csharp
    protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
    {
        return OnResolveAsyncResult.End(result);
    }
    ```

<span data-ttu-id="d5c2c-155">OnBegin.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-155">The OnBegin..</span></span> <span data-ttu-id="d5c2c-156">/ OnEnd.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-156">/ OnEnd..</span></span> <span data-ttu-id="d5c2c-157">메서드는 후속 검색 작업에 대한 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-157">methods provide the logic for the subsequent discovery operations.</span></span> <span data-ttu-id="d5c2c-158">예를 들어 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> 및 <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> 메서드는 검색 프록시에 대한 찾기 논리를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-158">For example the <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A> and <xref:System.ServiceModel.Discovery.DiscoveryProxy.OnEndFind%2A> methods implement the find logic for discovery proxy.</span></span> <span data-ttu-id="d5c2c-159">검색 프록시가 프로브 메시지를 받으면 클라이언트에 응답을 보내기 위해 이러한 메서드가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-159">When the discovery proxy receives a probe message these methods are executed to send a response back to the client.</span></span> <span data-ttu-id="d5c2c-160">찾기 논리는 원하는 대로 수정할 수 있습니다. 예를 들어 찾기 작업의 일부로 알고리즘 또는 애플리케이션별 XML 메타데이터 구문 분석을 통해 사용자 지정 범위 일치를 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-160">You may modify the find logic as you wish, for example you can incorporate custom scope matching by algorithms or application specific XML metadata parsing as part of your find operation.</span></span>

### <a name="to-implement-the-asyncresult-class"></a><span data-ttu-id="d5c2c-161">AsyncResult 클래스를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-161">To implement the AsyncResult class</span></span>

1. <span data-ttu-id="d5c2c-162">다양한 비동기 결과 클래스를 파생시키는 데 사용되는 추상 기본 클래스 AsyncResult를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-162">Define the abstract base class AsyncResult which is used to derive the various async result classes.</span></span>

2. <span data-ttu-id="d5c2c-163">AsyncResult.cs라는 새 코드 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-163">Create a new code file called AsyncResult.cs.</span></span>

3. <span data-ttu-id="d5c2c-164">AsyncResult.cs에 다음 `using` 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-164">Add the following `using` statements to AsyncResult.cs.</span></span>

    ```csharp
    using System;
    using System.Threading;
    ```

4. <span data-ttu-id="d5c2c-165">다음 AsyncResult 클래스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-165">Add the following AsyncResult class.</span></span>

    ```csharp
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
    ```

### <a name="to-host-the-discoveryproxy"></a><span data-ttu-id="d5c2c-166">DiscoveryProxy를 호스팅하려면</span><span class="sxs-lookup"><span data-stu-id="d5c2c-166">To host the DiscoveryProxy</span></span>

1. <span data-ttu-id="d5c2c-167">DiscoveryProxyExample 프로젝트에서 Program.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-167">Open the Program.cs file in the DiscoveryProxyExample project.</span></span>

2. <span data-ttu-id="d5c2c-168">다음 `using` 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-168">Add the following `using` statements.</span></span>

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Discovery;
    ```

3. <span data-ttu-id="d5c2c-169">`Main()` 메서드 안에서 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-169">Within the `Main()` method, add the following code.</span></span> <span data-ttu-id="d5c2c-170">그러면 `DiscoveryProxy` 클래스의 인스턴스가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-170">This creates an instance of the `DiscoveryProxy` class.</span></span>

    ```csharp
    Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
    Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

    // Host the DiscoveryProxy service
    ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());
    ```

4. <span data-ttu-id="d5c2c-171">다음 코드를 추가하여 검색 엔드포인트 및 알림 엔드포인트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-171">Next add the following code to add a discovery endpoint and an announcement endpoint.</span></span>

    ```csharp
    try
    {
        // Add DiscoveryEndpoint to receive Probe and Resolve messages
        DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
        discoveryEndpoint.IsSystemEndpoint = false;

        // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
        AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

        proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
        proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

        proxyServiceHost.Open();

        Console.WriteLine("Proxy Service started.");
        Console.WriteLine();
        Console.WriteLine("Press <ENTER> to terminate the service.");
        Console.WriteLine();
        Console.ReadLine();

        proxyServiceHost.Close();
    }
    catch (CommunicationException e)
    {
        Console.WriteLine(e.Message);
    }
    catch (TimeoutException e)
    {
        Console.WriteLine(e.Message);
    }

    if (proxyServiceHost.State != CommunicationState.Closed)
    {
        Console.WriteLine("Aborting the service...");
        proxyServiceHost.Abort();
    }
    ```

<span data-ttu-id="d5c2c-172">검색 프록시의 구현을 완료했습니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-172">You have completed implementing the discovery proxy.</span></span> <span data-ttu-id="d5c2c-173">[방법: 검색 프록시에 등록 하는 검색 가능한 서비스 구현](discoverable-service-that-registers-with-the-discovery-proxy.md)을 계속 진행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-173">Continue on to [How to: Implement a Discoverable Service that Registers with the Discovery Proxy](discoverable-service-that-registers-with-the-discovery-proxy.md).</span></span>

## <a name="example"></a><span data-ttu-id="d5c2c-174">예제</span><span class="sxs-lookup"><span data-stu-id="d5c2c-174">Example</span></span>

<span data-ttu-id="d5c2c-175">다음은 이 항목에서 사용되는 전체 코드 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="d5c2c-175">This is the full listing of the code used in this topic.</span></span>

```csharp
// DiscoveryProxy.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Collections.Generic;
using System.ServiceModel;
using System.ServiceModel.Discovery;
using System.Xml;

namespace Microsoft.Samples.Discovery
{
    // Implement DiscoveryProxy by extending the DiscoveryProxy class and overriding the abstract methods
    [ServiceBehavior(InstanceContextMode = InstanceContextMode.Single, ConcurrencyMode = ConcurrencyMode.Multiple)]
    public class DiscoveryProxyService : DiscoveryProxy
    {
        // Repository to store EndpointDiscoveryMetadata. A database or a flat file could also be used instead.
        Dictionary<EndpointAddress, EndpointDiscoveryMetadata> onlineServices;

        public DiscoveryProxyService()
        {
            this.onlineServices = new Dictionary<EndpointAddress, EndpointDiscoveryMetadata>();
        }

        // OnBeginOnlineAnnouncement method is called when a Hello message is received by the Proxy
        protected override IAsyncResult OnBeginOnlineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.AddOnlineService(endpointDiscoveryMetadata);
            return new OnOnlineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOnlineAnnouncement(IAsyncResult result)
        {
            OnOnlineAnnouncementAsyncResult.End(result);
        }

        // OnBeginOfflineAnnouncement method is called when a Bye message is received by the Proxy
        protected override IAsyncResult OnBeginOfflineAnnouncement(DiscoveryMessageSequence messageSequence, EndpointDiscoveryMetadata endpointDiscoveryMetadata, AsyncCallback callback, object state)
        {
            this.RemoveOnlineService(endpointDiscoveryMetadata);
            return new OnOfflineAnnouncementAsyncResult(callback, state);
        }

        protected override void OnEndOfflineAnnouncement(IAsyncResult result)
        {
            OnOfflineAnnouncementAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Probe request message is received by the Proxy
        protected override IAsyncResult OnBeginFind(FindRequestContext findRequestContext, AsyncCallback callback, object state)
        {
            this.MatchFromOnlineService(findRequestContext);
            return new OnFindAsyncResult(callback, state);
        }

        protected override void OnEndFind(IAsyncResult result)
        {
            OnFindAsyncResult.End(result);
        }

        // OnBeginFind method is called when a Resolve request message is received by the Proxy
        protected override IAsyncResult OnBeginResolve(ResolveCriteria resolveCriteria, AsyncCallback callback, object state)
        {
            return new OnResolveAsyncResult(this.MatchFromOnlineService(resolveCriteria), callback, state);
        }

        protected override EndpointDiscoveryMetadata OnEndResolve(IAsyncResult result)
        {
            return OnResolveAsyncResult.End(result);
        }

        // The following are helper methods required by the Proxy implementation
        void AddOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            lock (this.onlineServices)
            {
                this.onlineServices[endpointDiscoveryMetadata.Address] = endpointDiscoveryMetadata;
            }

            PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Adding");
        }

        void RemoveOnlineService(EndpointDiscoveryMetadata endpointDiscoveryMetadata)
        {
            if (endpointDiscoveryMetadata != null)
            {
                lock (this.onlineServices)
                {
                    this.onlineServices.Remove(endpointDiscoveryMetadata.Address);
                }

                PrintDiscoveryMetadata(endpointDiscoveryMetadata, "Removing");
            }
        }

        void MatchFromOnlineService(FindRequestContext findRequestContext)
        {
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (findRequestContext.Criteria.IsMatch(endpointDiscoveryMetadata))
                    {
                        findRequestContext.AddMatchingEndpoint(endpointDiscoveryMetadata);
                    }
                }
            }
        }

        EndpointDiscoveryMetadata MatchFromOnlineService(ResolveCriteria criteria)
        {
            EndpointDiscoveryMetadata matchingEndpoint = null;
            lock (this.onlineServices)
            {
                foreach (EndpointDiscoveryMetadata endpointDiscoveryMetadata in this.onlineServices.Values)
                {
                    if (criteria.Address == endpointDiscoveryMetadata.Address)
                    {
                        matchingEndpoint = endpointDiscoveryMetadata;
                    }
                }
            }
            return matchingEndpoint;
        }

        void PrintDiscoveryMetadata(EndpointDiscoveryMetadata endpointDiscoveryMetadata, string verb)
        {
            Console.WriteLine("\n**** " + verb + " service of the following type from cache. ");
            foreach (XmlQualifiedName contractName in endpointDiscoveryMetadata.ContractTypeNames)
            {
                Console.WriteLine("** " + contractName.ToString());
                break;
            }
            Console.WriteLine("**** Operation Completed");
        }

        sealed class OnOnlineAnnouncementAsyncResult : AsyncResult
        {
            public OnOnlineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOnlineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnOfflineAnnouncementAsyncResult : AsyncResult
        {
            public OnOfflineAnnouncementAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnOfflineAnnouncementAsyncResult>(result);
            }
        }

        sealed class OnFindAsyncResult : AsyncResult
        {
            public OnFindAsyncResult(AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.Complete(true);
            }

            public static void End(IAsyncResult result)
            {
                AsyncResult.End<OnFindAsyncResult>(result);
            }
        }

        sealed class OnResolveAsyncResult : AsyncResult
        {
            EndpointDiscoveryMetadata matchingEndpoint;

            public OnResolveAsyncResult(EndpointDiscoveryMetadata matchingEndpoint, AsyncCallback callback, object state)
                : base(callback, state)
            {
                this.matchingEndpoint = matchingEndpoint;
                this.Complete(true);
            }

            public static EndpointDiscoveryMetadata End(IAsyncResult result)
            {
                OnResolveAsyncResult thisPtr = AsyncResult.End<OnResolveAsyncResult>(result);
                return thisPtr.matchingEndpoint;
            }
        }
    }
}
```

```csharp
// AsyncResult.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.Threading;

namespace Microsoft.Samples.Discovery
{
    abstract class AsyncResult : IAsyncResult
    {
        AsyncCallback callback;
        bool completedSynchronously;
        bool endCalled;
        Exception exception;
        bool isCompleted;
        ManualResetEvent manualResetEvent;
        object state;
        object thisLock;

        protected AsyncResult(AsyncCallback callback, object state)
        {
            this.callback = callback;
            this.state = state;
            this.thisLock = new object();
        }

        public object AsyncState
        {
            get
            {
                return state;
            }
        }

        public WaitHandle AsyncWaitHandle
        {
            get
            {
                if (manualResetEvent != null)
                {
                    return manualResetEvent;
                }
                lock (ThisLock)
                {
                    manualResetEvent ??= new ManualResetEvent(isCompleted);
                }
                return manualResetEvent;
            }
        }

        public bool CompletedSynchronously
        {
            get
            {
                return completedSynchronously;
            }
        }

        public bool IsCompleted
        {
            get
            {
                return isCompleted;
            }
        }

        object ThisLock
        {
            get
            {
                return this.thisLock;
            }
        }

        protected static TAsyncResult End<TAsyncResult>(IAsyncResult result)
            where TAsyncResult : AsyncResult
        {
            if (result == null)
            {
                throw new ArgumentNullException("result");
            }

            TAsyncResult asyncResult = result as TAsyncResult;

            if (asyncResult == null)
            {
                throw new ArgumentException("Invalid async result.", "result");
            }

            if (asyncResult.endCalled)
            {
                throw new InvalidOperationException("Async object already ended.");
            }

            asyncResult.endCalled = true;

            if (!asyncResult.isCompleted)
            {
                asyncResult.AsyncWaitHandle.WaitOne();
            }

            if (asyncResult.manualResetEvent != null)
            {
                asyncResult.manualResetEvent.Close();
            }

            if (asyncResult.exception != null)
            {
                throw asyncResult.exception;
            }

            return asyncResult;
        }

        protected void Complete(bool completedSynchronously)
        {
            if (isCompleted)
            {
                throw new InvalidOperationException("This async result is already completed.");
            }

            this.completedSynchronously = completedSynchronously;

            if (completedSynchronously)
            {
                this.isCompleted = true;
            }
            else
            {
                lock (ThisLock)
                {
                    this.isCompleted = true;
                    if (this.manualResetEvent != null)
                    {
                        this.manualResetEvent.Set();
                    }
                }
            }

            if (callback != null)
            {
                callback(this);
            }
        }

        protected void Complete(bool completedSynchronously, Exception exception)
        {
            this.exception = exception;
            Complete(completedSynchronously);
        }
    }
}
```

```csharp
// program.cs
//----------------------------------------------------------------
// Copyright (c) Microsoft Corporation.  All rights reserved.
//----------------------------------------------------------------

using System;
using System.ServiceModel;
using System.ServiceModel.Discovery;

namespace Microsoft.Samples.Discovery
{
    class Program
    {
        public static void Main()
        {
            Uri probeEndpointAddress = new Uri("net.tcp://localhost:8001/Probe");
            Uri announcementEndpointAddress = new Uri("net.tcp://localhost:9021/Announcement");

            // Host the DiscoveryProxy service
            ServiceHost proxyServiceHost = new ServiceHost(new DiscoveryProxyService());

            try
            {
                // Add DiscoveryEndpoint to receive Probe and Resolve messages
                DiscoveryEndpoint discoveryEndpoint = new DiscoveryEndpoint(new NetTcpBinding(), new EndpointAddress(probeEndpointAddress));
                discoveryEndpoint.IsSystemEndpoint = false;

                // Add AnnouncementEndpoint to receive Hello and Bye announcement messages
                AnnouncementEndpoint announcementEndpoint = new AnnouncementEndpoint(new NetTcpBinding(), new EndpointAddress(announcementEndpointAddress));

                proxyServiceHost.AddServiceEndpoint(discoveryEndpoint);
                proxyServiceHost.AddServiceEndpoint(announcementEndpoint);

                proxyServiceHost.Open();

                Console.WriteLine("Proxy Service started.");
                Console.WriteLine();
                Console.WriteLine("Press <ENTER> to terminate the service.");
                Console.WriteLine();
                Console.ReadLine();

                proxyServiceHost.Close();
            }
            catch (CommunicationException e)
            {
                Console.WriteLine(e.Message);
            }
            catch (TimeoutException e)
            {
                Console.WriteLine(e.Message);
            }

            if (proxyServiceHost.State != CommunicationState.Closed)
            {
                Console.WriteLine("Aborting the service...");
                proxyServiceHost.Abort();
            }
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="d5c2c-176">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5c2c-176">See also</span></span>

- [<span data-ttu-id="d5c2c-177">WCF Discovery 개요</span><span class="sxs-lookup"><span data-stu-id="d5c2c-177">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="d5c2c-178">방법: 검색 프록시에 등록할 검색 가능한 서비스 구현</span><span class="sxs-lookup"><span data-stu-id="d5c2c-178">How to: Implement a Discoverable Service that Registers with the Discovery Proxy</span></span>](discoverable-service-that-registers-with-the-discovery-proxy.md)
- [<span data-ttu-id="d5c2c-179">방법: 검색 프록시를 사용하여 서비스를 찾는 클라이언트 애플리케이션 구현</span><span class="sxs-lookup"><span data-stu-id="d5c2c-179">How to: Implement a Client Application that Uses the Discovery Proxy to Find a Service</span></span>](client-app-discovery-proxy-to-find-a-service.md)
- [<span data-ttu-id="d5c2c-180">방법: 검색 프록시 테스트</span><span class="sxs-lookup"><span data-stu-id="d5c2c-180">How to: Test the Discovery Proxy</span></span>](how-to-test-the-discovery-proxy.md)
