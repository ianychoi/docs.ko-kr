---
title: ICorProfilerInfo3::RequestProfilerDetach 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
ms.openlocfilehash: 2ea39c94a5a0f3d24d4123d6405115ac75105e26
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721584"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="90778-102">ICorProfilerInfo3::RequestProfilerDetach 메서드</span><span class="sxs-lookup"><span data-stu-id="90778-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>

<span data-ttu-id="90778-103">런타임에 프로파일러를 분리하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90778-104">구문</span><span class="sxs-lookup"><span data-stu-id="90778-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90778-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="90778-105">Parameters</span></span>  

 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="90778-106">[in] 프로파일러를 언로드하기에 안전한지를 확인하기 전에 CLR(공용 언어 런타임)이 대기해야 하는 시간(밀리초)입니다.</span><span class="sxs-lookup"><span data-stu-id="90778-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90778-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="90778-107">Return Value</span></span>  

 <span data-ttu-id="90778-108">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="90778-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="90778-109">HRESULT</span></span>|<span data-ttu-id="90778-110">설명</span><span class="sxs-lookup"><span data-stu-id="90778-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90778-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="90778-111">S_OK</span></span>|<span data-ttu-id="90778-112">분리 요청이 유효하고 분리 절차는 다른 스레드에서 계속 진행됩니다.</span><span class="sxs-lookup"><span data-stu-id="90778-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="90778-113">분리가 완료되면 `ProfilerDetachSucceeded` 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="90778-114">E_CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="90778-114">E_CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="90778-115">프로파일러가 분리 작업을 지원 하기 위해 구현 해야 하는 [ICorProfilerCallback3](icorprofilercallback3-interface.md) 인터페이스에 대 한 [IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) 시도에 실패 했습니다.</span><span class="sxs-lookup"><span data-stu-id="90778-115">The profiler failed an [IUnknown::QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) attempt for the [ICorProfilerCallback3](icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="90778-116">분리가 시도되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="90778-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="90778-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="90778-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="90778-118">프로파일러가 시작 시 변경할 수 없는 플래그를 설정하므로 분리가 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="90778-119">분리가 시도되지 않았고 프로파일러가 완전히 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="90778-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="90778-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="90778-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="90778-121">프로파일러가 계측 된 MSIL (Microsoft 중간 언어) 코드 또는 삽입 된 후크를 사용 했기 때문에 분리이 불가능 합니다 `enter` / `leave` .</span><span class="sxs-lookup"><span data-stu-id="90778-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="90778-122">분리가 시도되지 않았고 프로파일러가 완전히 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="90778-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="90778-123">**참고** 계측 된 MSIL은 [Setilfunctionbody](icorprofilerinfo-setilfunctionbody-method.md) 메서드를 사용 하 여 프로파일러에서 제공 하는 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="90778-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="90778-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="90778-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="90778-125">관리되는 애플리케이션에서 런타임이 아직 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="90778-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="90778-126">즉, 런타임이 완전히 로드 되지 않았습니다. 이 오류 코드는 프로파일러 콜백의 [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) 메서드 내에서 분리가 요청 될 때 반환 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="90778-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="90778-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="90778-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="90778-128">지원되지 않는 시간에 `RequestProfilerDetach`가 호출되었습니다.</span><span class="sxs-lookup"><span data-stu-id="90778-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="90778-129">이는 가비지 수집을 허용할 수 없는 [ICorProfilerCallback](icorprofilercallback-interface.md) [메서드 내](icorprofilercallback-interface.md) 에서 또는 관리 되는 스레드에서 메서드가 호출 되지 않는 경우에 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="90778-130">자세한 내용은 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="90778-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90778-131">설명</span><span class="sxs-lookup"><span data-stu-id="90778-131">Remarks</span></span>  

 <span data-ttu-id="90778-132">분리 절차 중에 분리 스레드(프로파일러 분리를 위해 특별히 만들어진 스레드)는 가끔 모든 스레드가 프로파일러 코드를 종료했는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="90778-133">프로파일러는 `dwExpectedCompletionMilliseconds` 매개 변수를 통해 소요 시간 예상 값을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="90778-134">프로파일러가 특정 `ICorProfilerCallback*` 메서드 내에서 사용하는 일반적인 시간을 값으로 사용하는 것이 좋습니다. 이 값은 프로파일러의 최대 소요 예상 시간의 절반 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="90778-135">분리 스레드에서는 `dwExpectedCompletionMilliseconds`를 사용하여 프로파일러 콜백 코드가 스택에서 모두 제거되었는지를 확인하기 전의 대기 기간을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="90778-136">다음 알고리즘의 세부 정보는 CLR의 미래 릴리스에 변경될 수 있지만 프로파일러를 안전하게 언로드할 수 있는 시점을 결정할 때 `dwExpectedCompletionMilliseconds`를 사용할 수 있는 한 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="90778-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="90778-137">분리 스레드는 먼저 `dwExpectedCompletionMilliseconds`밀리초 동안 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="90778-138">활성화가 중지 된 후에 CLR에서 프로파일러 콜백 코드가 아직 있다는 것을 알게 되 면 분리 스레드는 다시 대기 하 고이 시간은 2 시간 밀리초로 표시 됩니다 `dwExpectedCompletionMilliseconds` .</span><span class="sxs-lookup"><span data-stu-id="90778-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="90778-139">이 두 번째 대기에서 활성화된 후 분리 스레드는 프로파일러 콜백 코드가 아직 있다는 것을 확인하면 다시 확인하기 전에 10분 동안 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="90778-140">분리 스레드는 10분마다 계속 다시 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="90778-141">프로파일러가 `dwExpectedCompletionMilliseconds`를 0(영)으로 지정하면 CLR은 5초 후, 다시 10초 후, 이후 10분마다 확인을 수행할 것임을 의미하는 기본값 5000을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="90778-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90778-142">요구 사항</span><span class="sxs-lookup"><span data-stu-id="90778-142">Requirements</span></span>  

 <span data-ttu-id="90778-143">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="90778-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90778-144">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90778-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90778-145">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90778-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90778-146">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90778-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90778-147">참조</span><span class="sxs-lookup"><span data-stu-id="90778-147">See also</span></span>

- [<span data-ttu-id="90778-148">ICorProfilerInfo3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="90778-148">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="90778-149">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="90778-149">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="90778-150">프로파일링</span><span class="sxs-lookup"><span data-stu-id="90778-150">Profiling</span></span>](index.md)
