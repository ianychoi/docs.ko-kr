---
title: ICorProfilerCallback::ExceptionUnwindFunctionLeave 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFunctionLeave method [.NET Framework profiling]
- ExceptionUnwindFunctionLeave method [.NET Framework profiling]
ms.assetid: ebaad1d5-ee0a-4cb0-96bc-8ba5d371b747
topic_type:
- apiref
ms.openlocfilehash: 9f88a3fde7d7cb5941e3a7f44a7d94056a959ab8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733921"
---
# <a name="icorprofilercallbackexceptionunwindfunctionleave-method"></a><span data-ttu-id="8689f-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave 메서드</span><span class="sxs-lookup"><span data-stu-id="8689f-102">ICorProfilerCallback::ExceptionUnwindFunctionLeave Method</span></span>

<span data-ttu-id="8689f-103">예외 처리의 해제 단계에서 함수 해제가 완료 되었음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="8689f-103">Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8689f-104">구문</span><span class="sxs-lookup"><span data-stu-id="8689f-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFunctionLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="8689f-105">설명</span><span class="sxs-lookup"><span data-stu-id="8689f-105">Remarks</span></span>  

 <span data-ttu-id="8689f-106">`ExceptionUnwindFunctionLeave`메서드가 호출 되 면 함수 인스턴스와 해당 스택 데이터가 스택에서 제거 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8689f-106">When the `ExceptionUnwindFunctionLeave` method is called, the function instance and its stack data are removed from the stack.</span></span>  
  
 <span data-ttu-id="8689f-107">스택이 가비지 수집을 허용 하는 상태에 있지 않아 선점형 가비지 수집을 사용 하도록 설정할 수 없으므로이 호출 중에 프로파일러가 차단 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8689f-107">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="8689f-108">프로파일러가 여기에서 차단 되 고 가비지 수집이 시도 되는 경우이 콜백이 반환 될 때까지 런타임이 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8689f-108">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="8689f-109">또한이 호출 중에 프로파일러는 관리 코드를 호출 하거나 관리 되는 메모리 할당을 발생 시 키 지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8689f-109">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8689f-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8689f-110">Requirements</span></span>  

 <span data-ttu-id="8689f-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8689f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8689f-112">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8689f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8689f-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8689f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8689f-114">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8689f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8689f-115">참조</span><span class="sxs-lookup"><span data-stu-id="8689f-115">See also</span></span>

- [<span data-ttu-id="8689f-116">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8689f-116">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8689f-117">ExceptionUnwindFunctionEnter 메서드</span><span class="sxs-lookup"><span data-stu-id="8689f-117">ExceptionUnwindFunctionEnter Method</span></span>](icorprofilercallback-exceptionunwindfunctionenter-method.md)
