---
title: COR_PRF_SNAPSHOT_INFO 열거형
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
ms.openlocfilehash: 5290db008bfe5727ed5899c2ed6f7e41ae9a353a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716358"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="06811-102">COR_PRF_SNAPSHOT_INFO 열거형</span><span class="sxs-lookup"><span data-stu-id="06811-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>

<span data-ttu-id="06811-103">프로파일러에서 [StackSnapshotCallback](stacksnapshotcallback-function.md) 함수를 호출할 때마다 스택 스냅숏으로 다시 전달할 데이터의 양을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06811-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06811-104">구문</span><span class="sxs-lookup"><span data-stu-id="06811-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="06811-105">멤버</span><span class="sxs-lookup"><span data-stu-id="06811-105">Members</span></span>  
  
|<span data-ttu-id="06811-106">멤버</span><span class="sxs-lookup"><span data-stu-id="06811-106">Members</span></span>|<span data-ttu-id="06811-107">설명</span><span class="sxs-lookup"><span data-stu-id="06811-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="06811-108">매개 변수를 제외 하 고 모든 매개 변수에 대 한 값을 전달 해야 함을 나타냅니다 `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="06811-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="06811-109">매개 변수를 포함 하 여 모든 매개 변수에 대 한 값을 전달 해야 함을 나타냅니다 `StackSnapshotCallback` `context` .</span><span class="sxs-lookup"><span data-stu-id="06811-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="06811-110">더 간단한 다른 스택 탐색 알고리즘이 사용 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="06811-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06811-111">설명</span><span class="sxs-lookup"><span data-stu-id="06811-111">Remarks</span></span>  

 <span data-ttu-id="06811-112">열거형에서 제공 되는 값 `COR_PRF_SNAPSHOT_INFO` 은 [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 메서드에 매개 변수로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="06811-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06811-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="06811-113">Requirements</span></span>  

 <span data-ttu-id="06811-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="06811-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06811-115">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06811-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06811-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06811-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06811-117">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06811-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06811-118">참조</span><span class="sxs-lookup"><span data-stu-id="06811-118">See also</span></span>

- [<span data-ttu-id="06811-119">DoStackSnapshot 메서드</span><span class="sxs-lookup"><span data-stu-id="06811-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="06811-120">프로파일링 열거형</span><span class="sxs-lookup"><span data-stu-id="06811-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
