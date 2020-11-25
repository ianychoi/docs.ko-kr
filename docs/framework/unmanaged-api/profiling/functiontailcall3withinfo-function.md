---
title: FunctionTailcall3WithInfo 함수
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
ms.openlocfilehash: c23c791197c9925038f71e70409e4ca3ebabb23e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722867"
---
# <a name="functiontailcall3withinfo-function"></a><span data-ttu-id="1fce5-102">FunctionTailcall3WithInfo 함수</span><span class="sxs-lookup"><span data-stu-id="1fce5-102">FunctionTailcall3WithInfo Function</span></span>

<span data-ttu-id="1fce5-103">현재 실행 중인 함수가 다른 함수에 대 한 마무리 호출을 수행 하려고 함을 프로파일러에 알리고 [ICorProfilerInfo3:: GetFunctionTailcall3Info 메서드에](icorprofilerinfo3-getfunctiontailcall3info-method.md) 전달 하 여 스택 프레임을 검색 하는 핸들을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-103">Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fce5-104">구문</span><span class="sxs-lookup"><span data-stu-id="1fce5-104">Syntax</span></span>  
  
```cpp  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1fce5-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1fce5-105">Parameters</span></span>  

- `functionIDOrClientID`

  <span data-ttu-id="1fce5-106">\[in] 마무리 호출을 수행 하려고 하는 현재 실행 중인 함수의 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-106">\[in] The identifier of the currently executing function that is about to make a tail call.</span></span>

- `eltInfo`

  <span data-ttu-id="1fce5-107">\[in] 지정 된 스택 프레임에 대 한 정보를 나타내는 불투명 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-107">\[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="1fce5-108">이 핸들은 전달 되는 콜백 중에만 유효 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-108">This handle is valid only during the callback to which it is passed.</span></span>

## <a name="remarks"></a><span data-ttu-id="1fce5-109">설명</span><span class="sxs-lookup"><span data-stu-id="1fce5-109">Remarks</span></span>  

 <span data-ttu-id="1fce5-110">`FunctionTailcall3WithInfo`콜백 메서드는 함수가 호출 될 때 프로파일러에 게 알리고 [ICorProfilerInfo3:: GetFunctionTailcall3Info 메서드](icorprofilerinfo3-getfunctiontailcall3info-method.md) 를 사용 하 여 스택 프레임을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-110">The `FunctionTailcall3WithInfo` callback method notifies the profiler as functions are called, and allows the profiler to use the [ICorProfilerInfo3::GetFunctionTailcall3Info method](icorprofilerinfo3-getfunctiontailcall3info-method.md) to inspect the stack frame.</span></span> <span data-ttu-id="1fce5-111">스택 프레임 정보에 액세스 하려면 `COR_PRF_ENABLE_FRAME_INFO` 플래그를 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-111">To access stack frame information, the `COR_PRF_ENABLE_FRAME_INFO` flag has to be set.</span></span> <span data-ttu-id="1fce5-112">프로파일러는 [ICorProfilerInfo:: SetEventMask 메서드](icorprofilerinfo-seteventmask-method.md) 를 사용 하 여 이벤트 플래그를 설정한 다음 [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo 메서드](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) 를 사용 하 여이 함수의 구현을 등록할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-112">The profiler can use the [ICorProfilerInfo::SetEventMask method](icorprofilerinfo-seteventmask-method.md) to set the event flags, and then use the [ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) to register your implementation of this function.</span></span>  
  
 <span data-ttu-id="1fce5-113">`FunctionTailcall3WithInfo`함수는 콜백입니다. 함수를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-113">The `FunctionTailcall3WithInfo` function is a callback; you must implement it.</span></span> <span data-ttu-id="1fce5-114">구현에서는 저장소 클래스 특성을 사용 해야 합니다 `__declspec(naked)` .</span><span class="sxs-lookup"><span data-stu-id="1fce5-114">The implementation must use the `__declspec(naked)` storage-class attribute.</span></span>  
  
 <span data-ttu-id="1fce5-115">실행 엔진은이 함수를 호출 하기 전에 레지스터를 저장 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-115">The execution engine does not save any registers before calling this function.</span></span>  
  
- <span data-ttu-id="1fce5-116">항목에서 FPU (부동 소수점 단위)의 항목을 포함 하 여 사용 하는 모든 레지스터를 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-116">On entry, you must save all registers that you use, including those in the floating-point unit (FPU).</span></span>  
  
- <span data-ttu-id="1fce5-117">종료 시 호출자에 의해 푸시되는 모든 매개 변수를 팝 하 여 스택을 복원 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-117">On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.</span></span>  
  
 <span data-ttu-id="1fce5-118">의 구현은 `FunctionTailcall3WithInfo` 가비지 수집을 지연 하므로를 차단 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-118">The implementation of `FunctionTailcall3WithInfo` should not block, because it will delay garbage collection.</span></span> <span data-ttu-id="1fce5-119">스택이 가비지 컬렉션에 대 한 상태에 있지 않을 수 있기 때문에 구현에서 가비지 수집을 시도 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-119">The implementation should not attempt a garbage collection, because the stack may not be in a garbage collection-friendly state.</span></span> <span data-ttu-id="1fce5-120">가비지 수집을 시도 하면 런타임이 반환 될 때까지 차단 됩니다 `FunctionTailcall3WithInfo` .</span><span class="sxs-lookup"><span data-stu-id="1fce5-120">If a garbage collection is attempted, the runtime will block until `FunctionTailcall3WithInfo` returns.</span></span>  
  
 <span data-ttu-id="1fce5-121">또한 FunctionTailcall3WithInfo 함수는 관리 코드를 호출 하거나 다른 방식으로 관리 되는 메모리 할당을 발생 시 키 지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1fce5-121">Also, the FunctionTailcall3WithInfo function must not call into managed code or cause a managed memory allocation in any way.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fce5-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1fce5-122">Requirements</span></span>  

 <span data-ttu-id="1fce5-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1fce5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fce5-124">**헤더:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="1fce5-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="1fce5-125">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fce5-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1fce5-126">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fce5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fce5-127">참조</span><span class="sxs-lookup"><span data-stu-id="1fce5-127">See also</span></span>

- [<span data-ttu-id="1fce5-128">FunctionEnter3</span><span class="sxs-lookup"><span data-stu-id="1fce5-128">FunctionEnter3</span></span>](functionenter3-function.md)
- [<span data-ttu-id="1fce5-129">FunctionLeave3</span><span class="sxs-lookup"><span data-stu-id="1fce5-129">FunctionLeave3</span></span>](functionleave3-function.md)
- [<span data-ttu-id="1fce5-130">FunctionTailcall3</span><span class="sxs-lookup"><span data-stu-id="1fce5-130">FunctionTailcall3</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="1fce5-131">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1fce5-131">FunctionEnter3WithInfo</span></span>](functiontailcall3-function.md)
- [<span data-ttu-id="1fce5-132">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1fce5-132">FunctionLeave3WithInfo</span></span>](functionleave3withinfo-function.md)
- [<span data-ttu-id="1fce5-133">SetEnterLeaveFunctionHooks3</span><span class="sxs-lookup"><span data-stu-id="1fce5-133">SetEnterLeaveFunctionHooks3</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [<span data-ttu-id="1fce5-134">SetEnterLeaveFunctionHooks3WithInfo</span><span class="sxs-lookup"><span data-stu-id="1fce5-134">SetEnterLeaveFunctionHooks3WithInfo</span></span>](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [<span data-ttu-id="1fce5-135">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="1fce5-135">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="1fce5-136">SetFunctionIDMapper2</span><span class="sxs-lookup"><span data-stu-id="1fce5-136">SetFunctionIDMapper2</span></span>](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [<span data-ttu-id="1fce5-137">프로파일링 전역 정적 함수</span><span class="sxs-lookup"><span data-stu-id="1fce5-137">Profiling Global Static Functions</span></span>](profiling-global-static-functions.md)
