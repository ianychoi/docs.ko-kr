---
description: '자세히 알아보기: ICLRAppDomainResourceMonitor 인터페이스'
title: ICLRAppDomainResourceMonitor 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 85321eabedb6912efabe57553732f8c6a4063155
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753902"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="4b6a5-103">ICLRAppDomainResourceMonitor 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4b6a5-103">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="4b6a5-104">응용 프로그램 도메인의 메모리 및 CPU 사용량을 검사 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-104">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4b6a5-105">메서드</span><span class="sxs-lookup"><span data-stu-id="4b6a5-105">Methods</span></span>  
  
|<span data-ttu-id="4b6a5-106">메서드</span><span class="sxs-lookup"><span data-stu-id="4b6a5-106">Method</span></span>|<span data-ttu-id="4b6a5-107">설명</span><span class="sxs-lookup"><span data-stu-id="4b6a5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4b6a5-108">GetCurrentAllocated 메서드</span><span class="sxs-lookup"><span data-stu-id="4b6a5-108">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="4b6a5-109">가비지 수집 된 메모리를 빼서 응용 프로그램 도메인이 만들어진 후에 적용 된 모든 메모리 할당의 총 크기 (바이트)를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-109">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="4b6a5-110">GetCurrentSurvived 메서드</span><span class="sxs-lookup"><span data-stu-id="4b6a5-110">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="4b6a5-111">마지막 전체 차단 가비지 수집을 수행 하 고 현재 응용 프로그램 도메인에서 참조 하는 바이트 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-111">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="4b6a5-112">GetCurrentCpuTime 메서드</span><span class="sxs-lookup"><span data-stu-id="4b6a5-112">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="4b6a5-113">응용 프로그램 도메인이 만들어진 후 현재 응용 프로그램 도메인에서 실행 되는 동안 모든 스레드에서 사용 된 총 프로세서 시간을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-113">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b6a5-114">설명</span><span class="sxs-lookup"><span data-stu-id="4b6a5-114">Remarks</span></span>  

 <span data-ttu-id="4b6a5-115">`ICLRAppDomainResourceMonitor`인터페이스는 다음과 같은 관리 되는 속성과 비슷한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-115">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="4b6a5-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4b6a5-116">Requirements</span></span>  

 <span data-ttu-id="4b6a5-117">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b6a5-118">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="4b6a5-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4b6a5-119">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4b6a5-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b6a5-120">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b6a5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b6a5-121">참조</span><span class="sxs-lookup"><span data-stu-id="4b6a5-121">See also</span></span>

- [<span data-ttu-id="4b6a5-122">\<appDomainResourceMonitoring> 요소</span><span class="sxs-lookup"><span data-stu-id="4b6a5-122">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="4b6a5-123">응용 프로그램 도메인 리소스 모니터링</span><span class="sxs-lookup"><span data-stu-id="4b6a5-123">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="4b6a5-124">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4b6a5-124">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4b6a5-125">호스팅</span><span class="sxs-lookup"><span data-stu-id="4b6a5-125">Hosting</span></span>](index.md)
