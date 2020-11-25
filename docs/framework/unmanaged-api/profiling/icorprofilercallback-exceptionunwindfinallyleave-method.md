---
title: ICorProfilerCallback::ExceptionUnwindFinallyLeave 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionUnwindFinallyLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionUnwindFinallyLeave method [.NET Framework profiling]
- ExceptionUnwindFinallyLeave method [.NET Framework profiling]
ms.assetid: 2350351e-f253-4c0c-a191-f952bc5700e6
topic_type:
- apiref
ms.openlocfilehash: e02716350aa2bf32bdd7c4b2e01841405de6dc14
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720401"
---
# <a name="icorprofilercallbackexceptionunwindfinallyleave-method"></a><span data-ttu-id="522fe-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave 메서드</span><span class="sxs-lookup"><span data-stu-id="522fe-102">ICorProfilerCallback::ExceptionUnwindFinallyLeave Method</span></span>

<span data-ttu-id="522fe-103">예외 처리의 해제 단계에 절이 남아 있음을 프로파일러에 알립니다 `finally` .</span><span class="sxs-lookup"><span data-stu-id="522fe-103">Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="522fe-104">구문</span><span class="sxs-lookup"><span data-stu-id="522fe-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwindFinallyLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="522fe-105">설명</span><span class="sxs-lookup"><span data-stu-id="522fe-105">Remarks</span></span>  

 <span data-ttu-id="522fe-106">스택이 가비지 수집을 허용 하는 상태에 있지 않아 선점형 가비지 수집을 사용 하도록 설정할 수 없으므로이 호출 중에 프로파일러가 차단 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="522fe-106">The profiler should not block during this call because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="522fe-107">프로파일러가 여기에서 차단 되 고 가비지 수집이 시도 되는 경우이 콜백이 반환 될 때까지 런타임이 차단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="522fe-107">If the profiler blocks here and a garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="522fe-108">또한이 호출 중에 프로파일러는 관리 코드를 호출 하거나 관리 되는 메모리 할당을 발생 시 키 지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="522fe-108">Also, during this call, the profiler must not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="522fe-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="522fe-109">Requirements</span></span>  

 <span data-ttu-id="522fe-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="522fe-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="522fe-111">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="522fe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="522fe-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="522fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="522fe-113">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="522fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522fe-114">참조</span><span class="sxs-lookup"><span data-stu-id="522fe-114">See also</span></span>

- [<span data-ttu-id="522fe-115">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="522fe-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="522fe-116">ExceptionUnwindFinallyEnter 메서드</span><span class="sxs-lookup"><span data-stu-id="522fe-116">ExceptionUnwindFinallyEnter Method</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)
