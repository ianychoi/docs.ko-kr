---
description: '다음에 대 한 자세한 정보: <applicationPool> 요소 (웹 설정)'
title: <applicationPool> 요소(웹 설정)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: e70b804fbad506f98d5356828843208e5ef9e515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681996"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="f266f-103">\<applicationPool> 요소(웹 설정)</span><span class="sxs-lookup"><span data-stu-id="f266f-103">\<applicationPool> Element (Web Settings)</span></span>

<span data-ttu-id="f266f-104">ASP.NET 응용 프로그램이 IIS 7.0 이상 버전에서 통합 모드로 실행 되는 경우 프로세스 전체 동작을 관리 하기 위해 ASP.NET에서 사용 하는 구성 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-104">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f266f-105">이 요소와이 요소는 ASP.NET 응용 프로그램이 IIS 7.0 이상 버전에서 호스팅되는 경우에만 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-105">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**  
  
## <a name="syntax"></a><span data-ttu-id="f266f-106">구문</span><span class="sxs-lookup"><span data-stu-id="f266f-106">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f266f-107">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f266f-107">Attributes and Elements</span></span>  

<span data-ttu-id="f266f-108">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f266f-109">특성</span><span class="sxs-lookup"><span data-stu-id="f266f-109">Attributes</span></span>  
  
|<span data-ttu-id="f266f-110">attribute</span><span class="sxs-lookup"><span data-stu-id="f266f-110">Attribute</span></span>|<span data-ttu-id="f266f-111">설명</span><span class="sxs-lookup"><span data-stu-id="f266f-111">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="f266f-112">ASP.NET에서 CPU 당 허용 하는 동시 요청 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-112">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="f266f-113">각 CPU의 응용 프로그램 풀에 대해 실행 될 수 있는 동시 스레드 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-113">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="f266f-114">이는 CPU 당 사용 하 여 요청을 처리할 수 있는 관리 되는 스레드 수를 제한할 수 있으므로 ASP.NET 동시성을 제어 하는 대체 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-114">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="f266f-115">기본적으로이 설정은 0입니다. 즉, ASP.NET는 CPU 당 만들 수 있는 스레드 수를 제한 하지 않습니다 .이는 CLR 스레드 풀도 만들 수 있는 스레드 수를 제한 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-115">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="f266f-116">단일 프로세스에서 ASP.NET에 대해 큐에 대기할 수 있는 최대 요청 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-116">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="f266f-117">ASP.NET 응용 프로그램을 둘 이상 단일 응용 프로그램 풀에서 실행 하는 경우 응용 프로그램 풀의 응용 프로그램에 대 한 누적 요청 집합은이 설정이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-117">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f266f-118">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f266f-118">Child Elements</span></span>  

 <span data-ttu-id="f266f-119">없음</span><span class="sxs-lookup"><span data-stu-id="f266f-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f266f-120">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f266f-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f266f-121">요소</span><span class="sxs-lookup"><span data-stu-id="f266f-121">Element</span></span>|<span data-ttu-id="f266f-122">설명</span><span class="sxs-lookup"><span data-stu-id="f266f-122">Description</span></span>|  
|-------------|-----------------|  
|[\<system.web>](system-web-element-web-settings.md)|<span data-ttu-id="f266f-123">ASP.NET가 호스트 응용 프로그램과 상호 작용 하는 방법에 대 한 정보를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-123">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f266f-124">설명</span><span class="sxs-lookup"><span data-stu-id="f266f-124">Remarks</span></span>  

<span data-ttu-id="f266f-125">통합 모드에서 IIS 7.0 이상 버전을 실행 하는 경우이 요소 조합을 사용 하면 응용 프로그램이 IIS 응용 프로그램 풀에서 호스팅될 때 ASP.NET에서 스레드를 관리 하 고 요청을 큐에 대기 하는 방법을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-125">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="f266f-126">IIS 6을 실행 하거나 클래식 모드나 ISAPI 모드에서 IIS 7.0를 실행 하는 경우 이러한 설정은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-126">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="f266f-127">`applicationPool`설정은 특정 버전의 .NET Framework에서 실행 되는 모든 응용 프로그램 풀에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-127">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="f266f-128">설정은 aspnet.config 파일에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-128">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="f266f-129">.NET Framework 버전 2.0 및 4.0에 대 한이 파일 버전이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-129">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="f266f-130">.NET Framework 버전 3.0 및 3.5은 버전 2.0와 aspnet.config 파일을 공유 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-130">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f266f-131">Windows 7에서 IIS 7.0를 실행 하는 경우 모든 응용 프로그램 풀에 대해 별도의 aspnet.config 파일을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-131">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="f266f-132">이렇게 하면 각 응용 프로그램 풀에 대 한 스레드의 성능을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-132">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="f266f-133">설정의 경우 `maxConcurrentRequestsPerCPU` .NET Framework 4에서 "5000"의 기본 설정은 실제로 CPU 당 5000 이상의 요청이 있는 경우를 제외 하 고 ASP.NET에 의해 제어 되는 요청 제한을 효과적으로 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-133">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="f266f-134">기본 설정은 CPU 당 동시성을 자동으로 관리 하기 위해 CLR 스레드 풀에 대신 종속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-134">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="f266f-135">비동기 요청 처리를 광범위 하 게 사용 하는 응용 프로그램이 나 네트워크 i/o에서 차단 된 많은 장기 실행 요청이 있는 응용 프로그램은 .NET Framework 4의 기본 제한 값을 높입니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-135">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="f266f-136">`maxConcurrentRequestsPerCPU`를 0으로 설정 하면 ASP.NET 요청을 처리 하기 위해 관리 되는 스레드를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-136">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="f266f-137">응용 프로그램이 IIS 응용 프로그램 풀에서 실행 되는 경우 요청은 IIS i/o 스레드에 남아 있으므로 동시성이 IIS 스레드 설정에 의해 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-137">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="f266f-138">`requestQueueLimit`설정은 ASP.NET 응용 프로그램의 web.config 파일에 설정된 [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) 요소의 `requestQueueLimit`특성과 동일한 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-138">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="f266f-139">그러나 `requestQueueLimit` aspnet.config 파일의 설정은 `requestQueueLimit` Web.config 파일의 설정을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-139">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="f266f-140">즉, 두 특성이 모두 설정 되 면 (기본적으로 true 임) `requestQueueLimit` aspnet.config 파일의 설정이 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-140">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f266f-141">예제</span><span class="sxs-lookup"><span data-stu-id="f266f-141">Example</span></span>  

<span data-ttu-id="f266f-142">다음 예제에서는 다음과 같은 경우 aspnet.config 파일에서 ASP.NET 프로세스 전체 동작을 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-142">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="f266f-143">응용 프로그램은 IIS 7.0 응용 프로그램 풀에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-143">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="f266f-144">IIS 7.0가 통합 모드로 실행 되 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-144">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="f266f-145">응용 프로그램에서 .NET Framework 3.5 SP1 이상 버전을 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-145">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="f266f-146">이 예제의 값은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="f266f-146">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool
        maxConcurrentRequestsPerCPU="5000"  
        maxConcurrentThreadsPerCPU="0"
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="f266f-147">요소 정보</span><span class="sxs-lookup"><span data-stu-id="f266f-147">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f266f-148">네임스페이스</span><span class="sxs-lookup"><span data-stu-id="f266f-148">Namespace</span></span>||  
|<span data-ttu-id="f266f-149">Schema Name</span><span class="sxs-lookup"><span data-stu-id="f266f-149">Schema Name</span></span>||  
|<span data-ttu-id="f266f-150">유효성 검사 파일</span><span class="sxs-lookup"><span data-stu-id="f266f-150">Validation File</span></span>||  
|<span data-ttu-id="f266f-151">비워 둘 수 있음</span><span class="sxs-lookup"><span data-stu-id="f266f-151">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="f266f-152">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f266f-152">See also</span></span>

- [<span data-ttu-id="f266f-153">\<system.web> 요소 (웹 설정)</span><span class="sxs-lookup"><span data-stu-id="f266f-153">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
