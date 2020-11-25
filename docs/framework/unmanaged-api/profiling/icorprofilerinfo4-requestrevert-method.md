---
title: ICorProfilerInfo4::RequestRevert 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: b80de5e0e03f6b3a424ac59a099e361dd6c50c86
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733817"
---
# <a name="icorprofilerinfo4requestrevert-method"></a><span data-ttu-id="78f22-102">ICorProfilerInfo4::RequestRevert 메서드</span><span class="sxs-lookup"><span data-stu-id="78f22-102">ICorProfilerInfo4::RequestRevert Method</span></span>

<span data-ttu-id="78f22-103">지정된 함수의 모든 인스턴스를 원래 버전으로 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-103">Reverts all instances of the specified functions to their original versions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f22-104">구문</span><span class="sxs-lookup"><span data-stu-id="78f22-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78f22-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="78f22-105">Parameters</span></span>  

 `cFunctions`  
 <span data-ttu-id="78f22-106">[in] 되돌릴 함수 개수입니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-106">[in] The number of functions to revert.</span></span>  
  
 `moduleIds`  
 <span data-ttu-id="78f22-107">[in] 되돌릴 함수를 식별하는 (`module`, `methodDef`) 쌍의 `moduleId` 부분을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-107">[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `methodIds`  
 <span data-ttu-id="78f22-108">[in] 되돌릴 함수를 식별하는 (`module`, `methodDef`) 쌍의 `methodId` 부분을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-108">[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.</span></span>  
  
 `status`  
 <span data-ttu-id="78f22-109">[out] 이 항목의 뒷부분에 있는 "상태 HRESULT" 섹션에 나열된 HRESULT 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-109">[out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic.</span></span> <span data-ttu-id="78f22-110">각 HRESULT는 병렬 배열 `moduleIds` 및 `methodIds`에 지정된 각 함수의 되돌리기 성공 또는 실패를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-110">Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f22-111">반환 값</span><span class="sxs-lookup"><span data-stu-id="78f22-111">Return Value</span></span>  

 <span data-ttu-id="78f22-112">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="78f22-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78f22-113">HRESULT</span></span>|<span data-ttu-id="78f22-114">설명</span><span class="sxs-lookup"><span data-stu-id="78f22-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78f22-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="78f22-115">S_OK</span></span>|<span data-ttu-id="78f22-116">모든 요청을 되돌리려고 했습니다. 그러나 반환된 상태 배열을 검사하여 성공적으로 되돌려진 함수를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-116">An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.</span></span>|  
|<span data-ttu-id="78f22-117">CORPROF_E_CALLBACK4_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="78f22-117">CORPROF_E_CALLBACK4_REQUIRED</span></span>|<span data-ttu-id="78f22-118">이 호출이 지원 되려면 프로파일러가 [ICorProfilerCallback4](icorprofilercallback4-interface.md) 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-118">The profiler must implement the [ICorProfilerCallback4](icorprofilercallback4-interface.md) interface for this call to be supported.</span></span>|  
|<span data-ttu-id="78f22-119">CORPROF_E_REJIT_NOT_ENABLED</span><span class="sxs-lookup"><span data-stu-id="78f22-119">CORPROF_E_REJIT_NOT_ENABLED</span></span>|<span data-ttu-id="78f22-120">JIT 다시 컴파일이 사용하도록 설정되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-120">JIT recompilation has not been enabled.</span></span> <span data-ttu-id="78f22-121">[ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) 메서드를 사용 하 여 플래그를 설정 하 여 초기화 하는 동안 JIT 재컴파일을 사용 하도록 설정 해야 합니다 `COR_PRF_ENABLE_REJIT` .</span><span class="sxs-lookup"><span data-stu-id="78f22-121">You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.</span></span>|  
|<span data-ttu-id="78f22-122">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="78f22-122">E_INVALIDARG</span></span>|<span data-ttu-id="78f22-123">`cFunctions`가 0이거나 `moduleIds` 또는 `methodIds`가 `NULL`입니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-123">`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.</span></span>|  
|<span data-ttu-id="78f22-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="78f22-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="78f22-125">메모리 부족 때문에 CLR에서 요청을 완료하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-125">The CLR was unable to complete the request because it ran out of memory.</span></span>|  
  
## <a name="status-hresults"></a><span data-ttu-id="78f22-126">상태 HRESULTS</span><span class="sxs-lookup"><span data-stu-id="78f22-126">Status HRESULTS</span></span>  
  
|<span data-ttu-id="78f22-127">상태 배열 HRESULT</span><span class="sxs-lookup"><span data-stu-id="78f22-127">Status array HRESULT</span></span>|<span data-ttu-id="78f22-128">설명</span><span class="sxs-lookup"><span data-stu-id="78f22-128">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="78f22-129">S_OK</span><span class="sxs-lookup"><span data-stu-id="78f22-129">S_OK</span></span>|<span data-ttu-id="78f22-130">해당 함수를 성공적으로 되돌렸습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-130">The corresponding function was successfully reverted.</span></span>|  
|<span data-ttu-id="78f22-131">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="78f22-131">E_INVALIDARG</span></span>|<span data-ttu-id="78f22-132">`moduleID` 또는 `methodDef` 매개 변수가 `NULL`인 경우</span><span class="sxs-lookup"><span data-stu-id="78f22-132">The `moduleID` or `methodDef` parameter is `NULL`.</span></span>|  
|<span data-ttu-id="78f22-133">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="78f22-133">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="78f22-134">모듈은 아직 완전히 로드되지 않았거나 언로드되는 중입니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-134">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="78f22-135">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="78f22-135">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="78f22-136">지정한 모듈은 동적으로 생성되었습니다(예: `Reflection.Emit`에 의해).</span><span class="sxs-lookup"><span data-stu-id="78f22-136">The specified module was dynamically generated (for example by `Reflection.Emit`).</span></span> <span data-ttu-id="78f22-137">따라서 이 메서드가 모듈을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-137">Therefore, it is not supported by this method.</span></span>|  
|<span data-ttu-id="78f22-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span><span class="sxs-lookup"><span data-stu-id="78f22-138">CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND</span></span>|<span data-ttu-id="78f22-139">해당하는 활성 다시 컴파일 요청이 없기 때문에 CLR이 지정한 함수를 되돌리지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-139">The CLR could not revert the specified function, because a corresponding active recompilation request was not found.</span></span> <span data-ttu-id="78f22-140">다시 컴파일이 요청되지 않았거나 함수가 이미 되돌려졌습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-140">Either the recompilation was never requested or the function was already reverted.</span></span>|  
|<span data-ttu-id="78f22-141">기타</span><span class="sxs-lookup"><span data-stu-id="78f22-141">Other</span></span>|<span data-ttu-id="78f22-142">운영 체제가 CLR의 제어 범위를 벗어난 오류를 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-142">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="78f22-143">예를 들어 메모리 페이지의 액세스 보호를 변경하려는 시스템 호출이 실패하면 운영 체제 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-143">For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78f22-144">설명</span><span class="sxs-lookup"><span data-stu-id="78f22-144">Remarks</span></span>  

 <span data-ttu-id="78f22-145">되돌려진 함수 인스턴스 중 하나를 다음에 호출하면 함수의 원래 버전이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-145">The next time any of the revereted function instances are called, the original versions of the functions will be run.</span></span> <span data-ttu-id="78f22-146">함수가 이미 실행되고 있으면 실행 중인 버전의 실행을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="78f22-146">If a function is already running, it will finish executing the version that is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f22-147">요구 사항</span><span class="sxs-lookup"><span data-stu-id="78f22-147">Requirements</span></span>  

 <span data-ttu-id="78f22-148">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="78f22-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f22-149">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78f22-149">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78f22-150">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78f22-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78f22-151">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f22-151">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f22-152">참조</span><span class="sxs-lookup"><span data-stu-id="78f22-152">See also</span></span>

- [<span data-ttu-id="78f22-153">ICorProfilerInfo4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="78f22-153">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="78f22-154">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="78f22-154">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="78f22-155">프로파일링</span><span class="sxs-lookup"><span data-stu-id="78f22-155">Profiling</span></span>](index.md)
