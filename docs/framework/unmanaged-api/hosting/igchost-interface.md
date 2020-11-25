---
title: IGCHost 인터페이스
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 8965797321e68443c01d05f97d147f2320a76739
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724301"
---
# <a name="igchost-interface"></a><span data-ttu-id="51d55-102">IGCHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="51d55-102">IGCHost Interface</span></span>

<span data-ttu-id="51d55-103">가비지 컬렉션 시스템에 대 한 정보를 가져오고 가비지 수집의 일부 측면을 제어 하기 위한 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51d55-104">4.5 .NET Framework부터 [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) 메서드를 사용 하 여 가비지 수집 세그먼트의 크기와 가비지 수집 시스템의 최대 크기를 `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) 메서드에서 적용 되는 제한 보다 큰 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51d55-105">이 인터페이스는 전문 용도로만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-105">This interface is for expert usage only.</span></span> <span data-ttu-id="51d55-106">응용 프로그램의 성능에 영향을 줄 수 있습니다 (잘못 사용 되는 경우).</span><span class="sxs-lookup"><span data-stu-id="51d55-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="51d55-107">메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-107">Methods</span></span>  
  
|<span data-ttu-id="51d55-108">메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-108">Method</span></span>|<span data-ttu-id="51d55-109">설명</span><span class="sxs-lookup"><span data-stu-id="51d55-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="51d55-110">Collect 메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="51d55-111">현재 가비지 컬렉션의 상태에 관계 없이 지정 된 세대에 대해 컬렉션을 강제로 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="51d55-112">GetStats 메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="51d55-113">가비지 수집 시스템의 현재 상태에 대 한 통계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="51d55-114">GetThreadStats 메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="51d55-115">가비지 수집에 대 한 스레드별 통계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="51d55-116">SetGCStartupLimits 메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="51d55-117">0 세대의 세그먼트 크기와 최대 크기를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="51d55-118">SetVirtualMemLimit 메서드</span><span class="sxs-lookup"><span data-stu-id="51d55-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="51d55-119">런타임 가상 메모리의 최대 크기를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="51d55-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="51d55-120">Requirements</span></span>  

 <span data-ttu-id="51d55-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51d55-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d55-122">**헤더:** GCHost, GCHost</span><span class="sxs-lookup"><span data-stu-id="51d55-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="51d55-123">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51d55-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51d55-124">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d55-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d55-125">참조</span><span class="sxs-lookup"><span data-stu-id="51d55-125">See also</span></span>

- [<span data-ttu-id="51d55-126">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="51d55-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="51d55-127">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="51d55-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)
