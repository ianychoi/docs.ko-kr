---
title: 사용자 지정 찾기 조건
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 9271ae1ec4bbd555fe93df24c7d38f0f345a03ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241813"
---
# <a name="custom-find-criteria"></a><span data-ttu-id="5fc28-102">사용자 지정 찾기 조건</span><span class="sxs-lookup"><span data-stu-id="5fc28-102">Custom Find Criteria</span></span>

<span data-ttu-id="5fc28-103">이 샘플에서는 논리를 사용하여 사용자 지정 범위 일치를 만드는 방법과 사용자 지정 검색 서비스를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-103">This sample demonstrates how to create a custom scope match using logic and how to implement a custom discovery service.</span></span> <span data-ttu-id="5fc28-104">클라이언트에서는 사용자 지정 범위 일치 기능을 사용하여 WCF 검색의 시스템 제공 찾기 기능을 구체화하고 보다 세부적으로 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-104">Clients use custom scope matching functionality to refine and further build on top of the system-provided find functionality of WCF Discovery.</span></span> <span data-ttu-id="5fc28-105">이 샘플에서 다루는 시나리오는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-105">The scenario this sample covers is as follows:</span></span>  
  
1. <span data-ttu-id="5fc28-106">클라이언트에서 계산기 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-106">A client is looking for a calculator service.</span></span>  
  
2. <span data-ttu-id="5fc28-107">검색을 구체화하기 위해 클라이언트는 사용자 지정 범위 일치 규칙을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-107">To refine its search, the client must use a custom scope matching rule.</span></span>  
  
3. <span data-ttu-id="5fc28-108">이 규칙에 따라 엔드포인트가 클라이언트에서 지정한 범위와 일치하면 서비스에서는 클라이언트에 다시 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-108">According to this rule, a service responds back to the client if its endpoint matches any of the scopes specified by the client.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5fc28-109">데모</span><span class="sxs-lookup"><span data-stu-id="5fc28-109">Demonstrates</span></span>  
  
- <span data-ttu-id="5fc28-110">사용자 지정 검색 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="5fc28-110">Creating a custom discovery service.</span></span>  
  
- <span data-ttu-id="5fc28-111">알고리즘에 따른 사용자 지정 범위 일치 구현</span><span class="sxs-lookup"><span data-stu-id="5fc28-111">Implementing a custom scope match by algorithm.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="5fc28-112">토론(Discussion)</span><span class="sxs-lookup"><span data-stu-id="5fc28-112">Discussion</span></span>  

 <span data-ttu-id="5fc28-113">클라이언트에서 "OR" 형식 일치 조건을 찾고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-113">The client is looking for "OR" type matching criteria.</span></span> <span data-ttu-id="5fc28-114">엔드포인트의 범위가 클라이언트에서 제공한 범위와 일치하면 서비스가 다시 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-114">A service responds back if the scopes on its endpoints match any of the scopes provided by the client.</span></span> <span data-ttu-id="5fc28-115">이 경우 클라이언트는 다음 목록의 범위가 있는 계산기 서비스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-115">In this case, the client is looking for a calculator service that has any of the scopes in the following list:</span></span>  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 <span data-ttu-id="5fc28-116">이 작업을 수행하기 위해 클라이언트에서는 URI에 따른 사용자 지정 범위 일치를 전달하여 서비스에서 사용자 지정 범위 일치 규칙을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-116">To accomplish this, the client directs services to use a custom scope matching rule by passing in a custom scope match by URI.</span></span> <span data-ttu-id="5fc28-117">사용자 지정 범위 일치에 도움이 되도록 서비스에서는 사용자 지정 범위 규칙을 인식하고 관련 일치 논리를 구현하는 사용자 지정 검색 서비스를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-117">To facilitate the custom scope matching, the service must use a custom discovery service that understands the custom scope match rule and implements the associated matching logic.</span></span>  
  
 <span data-ttu-id="5fc28-118">클라이언트 프로젝트에서 Program.cs 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-118">In the client project, open the Program.cs file.</span></span> <span data-ttu-id="5fc28-119">`ScopeMatchBy` 개체의 `FindCriteria` 필드는 특정 URI로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-119">Note that the `ScopeMatchBy` field of the `FindCriteria` object is set to a specific URI.</span></span> <span data-ttu-id="5fc28-120">이 식별자는 서비스로 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-120">This identifier is sent to the service.</span></span> <span data-ttu-id="5fc28-121">서비스에서는 이 규칙을 인식하지 못하는 경우 클라이언트의 찾기 요청을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-121">If the service does not understand this rule, it ignores the client’s find request.</span></span>  
  
 <span data-ttu-id="5fc28-122">서비스 프로젝트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-122">Open the service project.</span></span> <span data-ttu-id="5fc28-123">다음 세 개의 파일은 사용자 지정 검색 서비스를 구현하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-123">Three files are used to implement the Custom Discovery Service:</span></span>  
  
1. <span data-ttu-id="5fc28-124">**AsyncResult.cs**: 검색 방법에 필요한의 구현입니다 `AsyncResult` .</span><span class="sxs-lookup"><span data-stu-id="5fc28-124">**AsyncResult.cs**: This is the implementation of the `AsyncResult` that is required by Discovery methods.</span></span>  
  
2. <span data-ttu-id="5fc28-125">**CustomDiscoveryService.cs**:이 파일은 사용자 지정 검색 서비스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-125">**CustomDiscoveryService.cs**: This file implements the custom discovery service.</span></span> <span data-ttu-id="5fc28-126">이 구현에서는 <xref:System.ServiceModel.Discovery.DiscoveryService> 클래스를 확장하고 필요한 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-126">The implementation extends the <xref:System.ServiceModel.Discovery.DiscoveryService> class and overrides the necessary methods.</span></span> <span data-ttu-id="5fc28-127"><xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> 메서드의 구현에 주의하십시오.</span><span class="sxs-lookup"><span data-stu-id="5fc28-127">Note the implementation of the <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A> method.</span></span> <span data-ttu-id="5fc28-128">이 메서드는 클라이언트에서 규칙에 따른 사용자 지정 범위 일치를 지정했는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-128">The method checks to see whether the custom scope match by rule was specified by the client.</span></span> <span data-ttu-id="5fc28-129">이는 클라이언트에서 이전에 지정한 사용자 지정 URI와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-129">This is the same custom URI that the client specified previously.</span></span> <span data-ttu-id="5fc28-130">사용자 지정 규칙을 지정 하는 경우 "OR" 일치 논리를 구현 하는 코드 경로를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-130">If the custom rule is specified, the code path that implements the "OR" match logic is followed.</span></span>  
  
     <span data-ttu-id="5fc28-131">이 사용자 지정 논리는 서비스에 있는 각 엔드포인트의 모든 범위에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-131">This custom logic goes through all of the scopes on each of the endpoints that the service has.</span></span> <span data-ttu-id="5fc28-132">엔드포인트의 범위가 클라이언트에서 제공한 범위와 일치하면 검색 서비스에서는 클라이언트로 다시 보내는 응답에 해당 엔드포인트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-132">If any of the endpoint's scopes match any of the scopes provided by the client, the discovery service adds that endpoint to the response that is sent back to the client.</span></span>  
  
3. <span data-ttu-id="5fc28-133">**CustomDiscoveryExtension.cs**: 검색 서비스를 구현 하는 마지막 단계는이 사용자 지정 검색 서비스의 구현을 서비스 호스트에 연결 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-133">**CustomDiscoveryExtension.cs**: The last step in implementing the discovery service is to connect this implementation of the custom discover service to the service host.</span></span> <span data-ttu-id="5fc28-134">여기에 사용되는 도우미 클래스는 `CustomDiscoveryExtension` 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-134">The helper class used here is the `CustomDiscoveryExtension` class.</span></span> <span data-ttu-id="5fc28-135">이 클래스는 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> 클래스를 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-135">This class extends the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension> class.</span></span> <span data-ttu-id="5fc28-136">사용자는 <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> 메서드를 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-136">The user must override the <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A> method.</span></span> <span data-ttu-id="5fc28-137">이 경우 메서드는 이전에 생성된 사용자 지정 검색 서비스의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-137">In this case, the method returns an instance of the custom discovery service that was created before.</span></span> <span data-ttu-id="5fc28-138">`PublishedEndpoints`는 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>에 추가된 모든 애플리케이션 엔드포인트를 포함하는 <xref:System.ServiceModel.ServiceHost>입니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-138">`PublishedEndpoints` is a <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> that contains all of the application endpoints that are added to the <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5fc28-139">사용자 지정 검색 서비스에서는 이를 사용하여 해당 내부 목록을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-139">The custom discovery service uses this to populate its internal list.</span></span> <span data-ttu-id="5fc28-140">사용자가 다른 엔드포인트 메타데이터를 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-140">A user can to add other endpoint metadata as well.</span></span>  
  
 <span data-ttu-id="5fc28-141">마지막으로 Program.cs를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-141">Lastly, open Program.cs.</span></span> <span data-ttu-id="5fc28-142"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>와 `CustomDiscoveryExtension`이 모두 호스트에 추가되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-142">Note that both the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> and `CustomDiscoveryExtension` are added to the host.</span></span> <span data-ttu-id="5fc28-143">이 작업이 수행되고 호스트에 검색 메시지를 받는 데 사용할 엔드포인트가 있으면 애플리케이션에서 사용자 지정 검색 서비스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-143">Once this is done and the host has an endpoint over which to receive discovery messages, the application can use the custom discovery service.</span></span>  
  
 <span data-ttu-id="5fc28-144">클라이언트에서 주소를 모르고도 서비스를 찾을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-144">Observe that the client is able to find the service without knowing its address.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5fc28-145">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5fc28-145">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5fc28-146">프로젝트가 포함된 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-146">Open the solution that contains the project.</span></span>  
  
2. <span data-ttu-id="5fc28-147">프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-147">Build the project.</span></span>  
  
3. <span data-ttu-id="5fc28-148">서비스 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-148">Run the service application.</span></span>  
  
4. <span data-ttu-id="5fc28-149">클라이언트 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-149">Run the client application.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5fc28-150">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-150">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5fc28-151">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5fc28-151">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5fc28-152">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-152">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5fc28-153">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5fc28-153">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
