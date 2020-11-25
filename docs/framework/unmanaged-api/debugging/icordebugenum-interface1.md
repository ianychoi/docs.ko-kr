---
title: ICorDebugEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
ms.openlocfilehash: b208444de3b427329988f27b9d252b54143b7240
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698795"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="05aca-102">ICorDebugEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="05aca-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="05aca-103">디버깅 응용 프로그램에서 사용 하는 열거자에 대 한 추상 기본 인터페이스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05aca-104">메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-104">Methods</span></span>  
  
|<span data-ttu-id="05aca-105">메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-105">Method</span></span>|<span data-ttu-id="05aca-106">설명</span><span class="sxs-lookup"><span data-stu-id="05aca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05aca-107">Clone 메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="05aca-108">이 `ICorDebugEnum` 개체의 복사본을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="05aca-109">GetCount 메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="05aca-110">열거형의 항목 수를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="05aca-111">Reset 메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="05aca-112">커서를 열거형의 시작 부분으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="05aca-113">Skip 메서드</span><span class="sxs-lookup"><span data-stu-id="05aca-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="05aca-114">지정 된 항목 수 만큼 열거에서 커서를 앞으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05aca-115">설명</span><span class="sxs-lookup"><span data-stu-id="05aca-115">Remarks</span></span>  

 <span data-ttu-id="05aca-116">다음 열거자는에서 파생 됩니다 `ICorDebugEnum` .</span><span class="sxs-lookup"><span data-stu-id="05aca-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="05aca-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="05aca-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="05aca-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="05aca-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="05aca-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="05aca-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="05aca-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="05aca-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="05aca-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="05aca-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="05aca-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="05aca-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="05aca-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="05aca-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="05aca-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="05aca-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="05aca-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="05aca-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="05aca-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="05aca-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="05aca-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="05aca-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="05aca-138">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="05aca-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05aca-139">요구 사항</span><span class="sxs-lookup"><span data-stu-id="05aca-139">Requirements</span></span>  

 <span data-ttu-id="05aca-140">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05aca-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05aca-141">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05aca-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05aca-142">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05aca-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05aca-143">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05aca-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05aca-144">참조</span><span class="sxs-lookup"><span data-stu-id="05aca-144">See also</span></span>

- [<span data-ttu-id="05aca-145">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="05aca-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
