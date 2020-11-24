---
title: IGCHost::GetStats 메서드
ms.date: 03/30/2017
api_name:
- IGCHost.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetStats
helpviewer_keywords:
- GetStats method, IGCHost interface [.NET Framework hosting]
- IGCHost::GetStats method [.NET Framework hosting]
ms.assetid: c4ae022c-46ac-4f19-9ddd-09b955f19412
topic_type:
- apiref
ms.openlocfilehash: 7e664d88bf9f67e936e693b663f27ca490da13ed
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670110"
---
# <a name="igchostgetstats-method"></a><span data-ttu-id="18eca-102">IGCHost::GetStats 메서드</span><span class="sxs-lookup"><span data-stu-id="18eca-102">IGCHost::GetStats Method</span></span>

<span data-ttu-id="18eca-103">가비지 수집 시스템의 현재 상태에 대 한 통계를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="18eca-103">Gets the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18eca-104">구문</span><span class="sxs-lookup"><span data-stu-id="18eca-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18eca-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="18eca-105">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="18eca-106">[in, out] 가비지 수집 시스템의 현재 상태에 대 한 통계를 포함 하는 [COR_GC_STATS](cor-gc-stats-structure.md) 구조체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="18eca-106">[in, out] A pointer to a [COR_GC_STATS](cor-gc-stats-structure.md) structure that contains the statistics for the current state of the garbage collection system.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18eca-107">설명</span><span class="sxs-lookup"><span data-stu-id="18eca-107">Remarks</span></span>  

 <span data-ttu-id="18eca-108">통계는 가비지 수집 시스템이 작동 하는 데 도움이 되는 스마트 할당 시스템에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18eca-108">The statistics can be used by a smart allocation system to help the garbage collection system operate.</span></span> <span data-ttu-id="18eca-109">예를 들어 할당 시스템에서 통계를 검토 한 후 메모리를 더 추가 하거나 컬렉션을 강제 적용 해야 하는지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18eca-109">For example, the allocation system may determine, after reviewing the statistics, that it needs to add more memory or force a collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18eca-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="18eca-110">Requirements</span></span>  

 <span data-ttu-id="18eca-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="18eca-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18eca-112">**헤더:** GCHost, GCHost</span><span class="sxs-lookup"><span data-stu-id="18eca-112">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="18eca-113">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="18eca-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18eca-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18eca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18eca-115">참조</span><span class="sxs-lookup"><span data-stu-id="18eca-115">See also</span></span>

- [<span data-ttu-id="18eca-116">IGCHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="18eca-116">IGCHost Interface</span></span>](igchost-interface.md)
