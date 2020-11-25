---
title: ICorDebugHeapSegmentEnum::Next 메서드
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 6398fa2962b347a260e23e4fed8cf272a2916a9e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704619"
---
# <a name="icordebugheapsegmentenumnext-method"></a><span data-ttu-id="34aaa-102">ICorDebugHeapSegmentEnum::Next 메서드</span><span class="sxs-lookup"><span data-stu-id="34aaa-102">ICorDebugHeapSegmentEnum::Next Method</span></span>

<span data-ttu-id="34aaa-103">관리 되는 힙의 메모리 영역에 대 한 정보를 포함 하는 지정 된 수의 [COR_SEGMENT](cor-segment-structure.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="34aaa-103">Gets the specified number of [COR_SEGMENT](cor-segment-structure.md) instances that contain information about memory regions of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34aaa-104">구문</span><span class="sxs-lookup"><span data-stu-id="34aaa-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="34aaa-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="34aaa-105">Parameters</span></span>  

 <span data-ttu-id="34aaa-106">celt</span><span class="sxs-lookup"><span data-stu-id="34aaa-106">celt</span></span>  
 <span data-ttu-id="34aaa-107">진행 검색할 세그먼트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="34aaa-107">[in] The number of segments to be retrieved.</span></span>  
  
 <span data-ttu-id="34aaa-108">세그먼트</span><span class="sxs-lookup"><span data-stu-id="34aaa-108">segments</span></span>  
 <span data-ttu-id="34aaa-109">제한이 각각 관리 되는 힙에서 메모리 영역에 대 한 정보를 제공 하는 [COR_SEGMENT](cor-segment-structure.md) 개체를 가리키는 포인터의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="34aaa-109">[out] An array of pointers, each of which points to a [COR_SEGMENT](cor-segment-structure.md) object that provides information about a region of memory in the managed heap.</span></span>  
  
 <span data-ttu-id="34aaa-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="34aaa-110">pceltFetched</span></span>  
 <span data-ttu-id="34aaa-111">제한이 에 실제로 반환 된 [COR_SEGMENT](cor-segment-structure.md) 개체 수에 대 한 포인터 `segments` 입니다.</span><span class="sxs-lookup"><span data-stu-id="34aaa-111">[out] A pointer to the number of [COR_SEGMENT](cor-segment-structure.md) objects actually returned in `segments`.</span></span> <span data-ttu-id="34aaa-112">`celt`가 1이면 이 값은 `null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34aaa-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="34aaa-113">설명</span><span class="sxs-lookup"><span data-stu-id="34aaa-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34aaa-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="34aaa-114">Requirements</span></span>  

 <span data-ttu-id="34aaa-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="34aaa-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34aaa-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="34aaa-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34aaa-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="34aaa-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34aaa-118">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34aaa-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34aaa-119">참조</span><span class="sxs-lookup"><span data-stu-id="34aaa-119">See also</span></span>

- [<span data-ttu-id="34aaa-120">ICorDebugHeapSegmentEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="34aaa-120">ICorDebugHeapSegmentEnum Interface</span></span>](icordebugheapsegmentenum-interface.md)
- [<span data-ttu-id="34aaa-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="34aaa-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
