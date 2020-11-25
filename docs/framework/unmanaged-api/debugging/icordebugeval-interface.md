---
title: ICorDebugEval 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
ms.openlocfilehash: 5d8fd79b242f2b88b82c5c3d78dfe45d80f1194f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729787"
---
# <a name="icordebugeval-interface"></a><span data-ttu-id="006fd-102">ICorDebugEval 인터페이스</span><span class="sxs-lookup"><span data-stu-id="006fd-102">ICorDebugEval Interface</span></span>

<span data-ttu-id="006fd-103">디버깅 중인 코드의 컨텍스트 내에서 디버거가 코드를 실행할 수 있도록 하는 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-103">Provides methods to enable the debugger to execute code within the context of the code being debugged.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="006fd-104">메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-104">Methods</span></span>  
  
|<span data-ttu-id="006fd-105">메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-105">Method</span></span>|<span data-ttu-id="006fd-106">설명</span><span class="sxs-lookup"><span data-stu-id="006fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="006fd-107">Abort 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-107">Abort Method</span></span>](icordebugeval-abort-method.md)|<span data-ttu-id="006fd-108">이 개체가 현재 수행 하 고 있는 계산을 중단 `ICorDebugEval` 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-108">Aborts the computation this `ICorDebugEval` object is currently performing.</span></span>|  
|[<span data-ttu-id="006fd-109">CallFunction 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-109">CallFunction Method</span></span>](icordebugeval-callfunction-method.md)|<span data-ttu-id="006fd-110">지정 된 함수에 대 한 호출을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-110">Sets up a call to the specified function.</span></span> <span data-ttu-id="006fd-111">.NET Framework 버전 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-111">(Obsolete in the .NET Framework version 2.0; use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.)</span></span>|  
|[<span data-ttu-id="006fd-112">CreateValue 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-112">CreateValue Method</span></span>](icordebugeval-createvalue-method.md)|<span data-ttu-id="006fd-113">초기 값이 0 또는 null 인 지정 된 형식의 "ICorDebugValue" 개체에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-113">Gets an interface pointer to an "ICorDebugValue" object of the specified type, with an initial value of zero or null.</span></span> <span data-ttu-id="006fd-114">.NET Framework 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: CreateValueForType](icordebugeval2-createvaluefortype-method.md) 을 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="006fd-114">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::CreateValueForType](icordebugeval2-createvaluefortype-method.md) instead.)</span></span>|  
|[<span data-ttu-id="006fd-115">GetResult 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-115">GetResult Method</span></span>](icordebugeval-getresult-method.md)|<span data-ttu-id="006fd-116">`ICorDebugValue`계산 결과를 포함 하는에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-116">Gets an interface pointer to an `ICorDebugValue` that contains the results of the evaluation.</span></span>|  
|[<span data-ttu-id="006fd-117">GetThread 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-117">GetThread Method</span></span>](icordebugeval-getthread-method.md)|<span data-ttu-id="006fd-118">이 평가가 실행 되거나 실행 되는 "ICorDebugThread"에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-118">Gets an interface pointer to the "ICorDebugThread" where this evaluation is executing or will execute.</span></span>|  
|[<span data-ttu-id="006fd-119">IsActive 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-119">IsActive Method</span></span>](icordebugeval-isactive-method.md)|<span data-ttu-id="006fd-120">이 개체가 현재 실행 중인지 여부를 나타내는 값을 가져옵니다 `ICorDebugEval` .</span><span class="sxs-lookup"><span data-stu-id="006fd-120">Gets a value that indicates whether this `ICorDebugEval` object is currently executing.</span></span>|  
|[<span data-ttu-id="006fd-121">NewArray 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-121">NewArray Method</span></span>](icordebugeval-newarray-method.md)|<span data-ttu-id="006fd-122">지정 된 요소 형식 및 차원의 새 배열을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-122">Allocates a new array of the specified element type and dimensions.</span></span> <span data-ttu-id="006fd-123">.NET Framework 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) 를 사용 하십시오.</span><span class="sxs-lookup"><span data-stu-id="006fd-123">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedArray](icordebugeval2-newparameterizedarray-method.md) instead.)</span></span>|  
|[<span data-ttu-id="006fd-124">NewObject 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-124">NewObject Method</span></span>](icordebugeval-newobject-method.md)|<span data-ttu-id="006fd-125">새 개체 인스턴스를 할당 하 고 지정 된 생성자 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-125">Allocates a new object instance and calls the specified constructor method.</span></span> <span data-ttu-id="006fd-126">.NET Framework 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-126">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.)</span></span>|  
|[<span data-ttu-id="006fd-127">NewObjectNoConstructor 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-127">NewObjectNoConstructor Method</span></span>](icordebugeval-newobjectnoconstructor-method.md)|<span data-ttu-id="006fd-128">생성자 메서드 호출을 시도 하지 않고 지정 된 형식의 새 개체 인스턴스를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-128">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span> <span data-ttu-id="006fd-129">.NET Framework 2.0에서 사용 되지 않습니다. 대신 [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-129">(Obsolete in the .NET Framework 2.0; use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.)</span></span>|  
|[<span data-ttu-id="006fd-130">NewString 메서드</span><span class="sxs-lookup"><span data-stu-id="006fd-130">NewString Method</span></span>](icordebugeval-newstring-method.md)|<span data-ttu-id="006fd-131">지정 된 내용을 사용 하 여 새 문자열 개체를 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-131">Allocates a new string object with the specified contents.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="006fd-132">설명</span><span class="sxs-lookup"><span data-stu-id="006fd-132">Remarks</span></span>  

 <span data-ttu-id="006fd-133">`ICorDebugEval`개체는 평가를 수행 하는 데 사용 되는 특정 스레드의 컨텍스트에서 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-133">An `ICorDebugEval` object is created in the context of a specific thread that is used to perform the evaluations.</span></span> <span data-ttu-id="006fd-134">지정 된 평가에 사용 되는 모든 개체와 유형은 동일한 응용 프로그램 도메인 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-134">All objects and types used in a given evaluation must reside within the same application domain.</span></span> <span data-ttu-id="006fd-135">해당 응용 프로그램 도메인은 스레드의 현재 응용 프로그램 도메인과 같을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-135">That application domain need not be the same as the current application domain of the thread.</span></span> <span data-ttu-id="006fd-136">평가는 중첩 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-136">Evaluations can be nested.</span></span>  
  
 <span data-ttu-id="006fd-137">디버거에서 [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)를 호출 하 고 [ICorDebugManagedCallback:: EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) callback을 받을 때까지 평가 작업이 완료 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-137">The evaluation's operations do not complete until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md), and then receives an [ICorDebugManagedCallback::EvalComplete](icordebugmanagedcallback-evalcomplete-method.md) callback.</span></span> <span data-ttu-id="006fd-138">다른 스레드를 실행 하도록 허용 하지 않고 평가 기능을 사용 해야 하는 경우 [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)를 호출하기 전에 [ICorDebugController:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) 또는 [ICorDebugController:: Stop](icordebugcontroller-stop-method.md)을 사용하여 스레드를 일시 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-138">If you need to use the evaluation functionality without allowing other threads to run, suspend the threads by using either [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) or [ICorDebugController::Stop](icordebugcontroller-stop-method.md) before calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
 <span data-ttu-id="006fd-139">평가가 진행 중일 때 사용자 코드가 실행 되기 때문에 클래스 로드 및 중단점을 포함 하 여 모든 디버그 이벤트가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-139">Because user code is running when the evaluation is in progress, any debug events can occur, including class loads and breakpoints.</span></span> <span data-ttu-id="006fd-140">디버거에서는 이러한 이벤트에 대 한 콜백을 정상적으로 수신 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-140">The debugger will receive callbacks, as normal, for these events.</span></span> <span data-ttu-id="006fd-141">평가 상태는 일반적인 프로그램 상태 검사의 일부로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-141">The state of the evaluation will be seen as part of the inspection of the normal program state.</span></span> <span data-ttu-id="006fd-142">스택 체인은 `CHAIN_FUNC_EVAL` 체인이 됩니다 ("CorDebugStepReason" 열거 및 [ICorDebugChain:: getreason](icordebugchain-getreason-method.md) 메서드 참조).</span><span class="sxs-lookup"><span data-stu-id="006fd-142">The stack chain will be a `CHAIN_FUNC_EVAL` chain (see the "CorDebugStepReason" enumeration and the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method).</span></span> <span data-ttu-id="006fd-143">전체 디버거 API는 정상적으로 계속 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-143">The full debugger API will continue to operate as normal.</span></span>  
  
 <span data-ttu-id="006fd-144">교착 상태 또는 무한 반복 상황이 발생 하면 사용자 코드가 완료 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-144">If a deadlocked or infinite looping situation arises, the user code may never complete.</span></span> <span data-ttu-id="006fd-145">이러한 경우 프로그램을 다시 시작 하기 전에 [ICorDebugEval:: Abort](icordebugeval-abort-method.md) 를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-145">In such a case, you must call [ICorDebugEval::Abort](icordebugeval-abort-method.md) before resuming the program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="006fd-146">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="006fd-146">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="006fd-147">요구 사항</span><span class="sxs-lookup"><span data-stu-id="006fd-147">Requirements</span></span>  

 <span data-ttu-id="006fd-148">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="006fd-148">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="006fd-149">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="006fd-149">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="006fd-150">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="006fd-150">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="006fd-151">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="006fd-151">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="006fd-152">참조</span><span class="sxs-lookup"><span data-stu-id="006fd-152">See also</span></span>

- [<span data-ttu-id="006fd-153">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="006fd-153">Debugging Interfaces</span></span>](debugging-interfaces.md)
