---
title: COR_GC_THREAD_STATS 구조체
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 25a90965dc5466b7cf1a07140705424cf2ba4cd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699237"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="8afea-102">COR_GC_THREAD_STATS 구조체</span><span class="sxs-lookup"><span data-stu-id="8afea-102">COR_GC_THREAD_STATS Structure</span></span>

<span data-ttu-id="8afea-103">가비지 수집과 관련 된 스레드별 통계를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afea-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8afea-104">구문</span><span class="sxs-lookup"><span data-stu-id="8afea-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="8afea-105">멤버</span><span class="sxs-lookup"><span data-stu-id="8afea-105">Members</span></span>  
  
|<span data-ttu-id="8afea-106">멤버</span><span class="sxs-lookup"><span data-stu-id="8afea-106">Member</span></span>|<span data-ttu-id="8afea-107">설명</span><span class="sxs-lookup"><span data-stu-id="8afea-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="8afea-108">현재 인스턴스와 연결 된 스레드에 할당 된 메모리의 바이트 수입니다 `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="8afea-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="8afea-109">0 세대 가비지 수집이 발생 될 때마다이 숫자는 0으로 지워집니다.</span><span class="sxs-lookup"><span data-stu-id="8afea-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="8afea-110">최신 가비지 수집에서 더 높은 세대로 승격 된 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8afea-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8afea-111">설명</span><span class="sxs-lookup"><span data-stu-id="8afea-111">Remarks</span></span>  

 <span data-ttu-id="8afea-112">[ICLRTask:: GetMemStats](iclrtask-getmemstats-method.md) 는 형식의 출력 매개 변수를 사용 `COR_GC_THREAD_STATS` 합니다.</span><span class="sxs-lookup"><span data-stu-id="8afea-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8afea-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8afea-113">Requirements</span></span>  

 <span data-ttu-id="8afea-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8afea-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8afea-115">**헤더:** GCHost</span><span class="sxs-lookup"><span data-stu-id="8afea-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="8afea-116">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8afea-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8afea-117">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8afea-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8afea-118">참조</span><span class="sxs-lookup"><span data-stu-id="8afea-118">See also</span></span>

- [<span data-ttu-id="8afea-119">호스팅 구조체</span><span class="sxs-lookup"><span data-stu-id="8afea-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="8afea-120">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8afea-120">IHostTask Interface</span></span>](ihosttask-interface.md)
