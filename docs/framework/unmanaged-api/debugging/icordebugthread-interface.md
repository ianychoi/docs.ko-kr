---
title: ICorDebugThread 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread
helpviewer_keywords:
- ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3930fd9b-2bc3-4b72-80a0-b6eeb94d60c6
topic_type:
- apiref
ms.openlocfilehash: 5165ef081aad849c11747807d8cc76b2df0a6c74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729319"
---
# <a name="icordebugthread-interface"></a><span data-ttu-id="fe239-102">ICorDebugThread 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe239-102">ICorDebugThread Interface</span></span>

<span data-ttu-id="fe239-103">프로세스의 스레드를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="fe239-103">Represents a thread in a process.</span></span> <span data-ttu-id="fe239-104">`ICorDebugThread` 인스턴스의 수명은 이 인스턴스가 나타내는 스레드의 수명과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="fe239-104">The lifetime of an `ICorDebugThread` instance is the same as the lifetime of the thread it represents.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe239-105">메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-105">Methods</span></span>  
  
|<span data-ttu-id="fe239-106">메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-106">Method</span></span>|<span data-ttu-id="fe239-107">설명</span><span class="sxs-lookup"><span data-stu-id="fe239-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe239-108">ClearCurrentException 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-108">ClearCurrentException Method</span></span>](icordebugthread-clearcurrentexception-method.md)|<span data-ttu-id="fe239-109">이 메서드가 구현되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="fe239-109">This method is not implemented.</span></span> <span data-ttu-id="fe239-110">이 메서드를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fe239-110">Do not use it.</span></span>|  
|[<span data-ttu-id="fe239-111">CreateEval 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-111">CreateEval Method</span></span>](icordebugthread-createeval-method.md)|<span data-ttu-id="fe239-112">이에 대해 작동 하는 ICorDebugEval 개체를 만듭니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-112">Creates an ICorDebugEval object that operates on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-113">CreateStepper 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-113">CreateStepper Method</span></span>](icordebugthread-createstepper-method.md)|<span data-ttu-id="fe239-114">이에서 활성 프레임을 단계별로 실행할 수 있도록 하는 ICorDebugStepper 개체를 만듭니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-114">Creates an ICorDebugStepper object that allows stepping through the active frame in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-115">EnumerateChains 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-115">EnumerateChains Method</span></span>](icordebugthread-enumeratechains-method.md)|<span data-ttu-id="fe239-116">이의 모든 스택 체인을 포함 하는 ICorDebugChainEnum 열거자에 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-116">Gets an interface pointer to an ICorDebugChainEnum enumerator that contains all the stack chains in this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-117">GetActiveChain 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-117">GetActiveChain Method</span></span>](icordebugthread-getactivechain-method.md)|<span data-ttu-id="fe239-118">이에 대 한 활성 ICorDebugChain 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-118">Gets an interface pointer to the active ICorDebugChain on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-119">GetActiveFrame 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-119">GetActiveFrame Method</span></span>](icordebugthread-getactiveframe-method.md)|<span data-ttu-id="fe239-120">이에 대 한 활성 ICorDebugFrame 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-120">Gets an interface pointer to the active ICorDebugFrame on this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-121">GetAppDomain 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-121">GetAppDomain Method</span></span>](icordebugthread-getappdomain-method.md)|<span data-ttu-id="fe239-122">현재 실행 중인 응용 프로그램 도메인에 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-122">Gets an interface pointer to the application domain in which this `ICorDebugThread` is currently executing.</span></span>|  
|[<span data-ttu-id="fe239-123">GetCurrentException 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-123">GetCurrentException Method</span></span>](icordebugthread-getcurrentexception-method.md)|<span data-ttu-id="fe239-124">관리 코드에서 현재 throw 되는 예외를 나타내는 ICorDebugValue 개체에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe239-124">Gets an interface pointer to an ICorDebugValue object that represents an exception currently being thrown by managed code.</span></span>|  
|[<span data-ttu-id="fe239-125">GetDebugState 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-125">GetDebugState Method</span></span>](icordebugthread-getdebugstate-method.md)|<span data-ttu-id="fe239-126">이의 현재 디버그 상태를 설명 하는 CorDebugThreadState 값을 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-126">Gets a CorDebugThreadState value that describes the current debug state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-127">GetHandle 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-127">GetHandle Method</span></span>](icordebugthread-gethandle-method.md)|<span data-ttu-id="fe239-128">이의 활성 부분에 대 한 현재 핸들을 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-128">Gets the current handle for the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-129">GetID 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-129">GetID Method</span></span>](icordebugthread-getid-method.md)|<span data-ttu-id="fe239-130">이의 활성 부분에 대 한 현재 운영 체제 식별자를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-130">Gets the current operating system identifier of the active part of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-131">GetObject 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-131">GetObject Method</span></span>](icordebugthread-getobject-method.md)|<span data-ttu-id="fe239-132">CLR (공용 언어 런타임) 스레드에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="fe239-132">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>|  
|[<span data-ttu-id="fe239-133">GetProcess 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-133">GetProcess Method</span></span>](icordebugthread-getprocess-method.md)|<span data-ttu-id="fe239-134">파트를 구성 하는 프로세스에 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-134">Gets an interface pointer to the process of which this `ICorDebugThread` forms a part.</span></span>|  
|[<span data-ttu-id="fe239-135">GetRegisterSet 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-135">GetRegisterSet Method</span></span>](icordebugthread-getregisterset-method.md)|<span data-ttu-id="fe239-136">이와 연결 된 레지스터 집합에 대 한 인터페이스 포인터를 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-136">Gets an interface pointer to the register set associated with this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-137">GetUserState 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-137">GetUserState Method</span></span>](icordebugthread-getuserstate-method.md)|<span data-ttu-id="fe239-138">이의 현재 상태를 설명 하는 CorDebugUserState 값의 비트 조합을 가져옵니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-138">Gets a bitwise combination of CorDebugUserState values that describe the current state of this `ICorDebugThread`.</span></span>|  
|[<span data-ttu-id="fe239-139">SetDebugState 메서드</span><span class="sxs-lookup"><span data-stu-id="fe239-139">SetDebugState Method</span></span>](icordebugthread-setdebugstate-method.md)|<span data-ttu-id="fe239-140">`CorDebugThreadState`이의 디버깅 상태를 설명 하는 값의 비트 조합을 설정 합니다 `ICorDebugThread` .</span><span class="sxs-lookup"><span data-stu-id="fe239-140">Sets a bitwise combination of `CorDebugThreadState` values that describe the debugging state of this `ICorDebugThread`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe239-141">설명</span><span class="sxs-lookup"><span data-stu-id="fe239-141">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe239-142">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe239-142">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe239-143">요구 사항</span><span class="sxs-lookup"><span data-stu-id="fe239-143">Requirements</span></span>  

 <span data-ttu-id="fe239-144">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe239-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe239-145">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe239-145">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe239-146">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe239-146">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe239-147">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe239-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe239-148">참조</span><span class="sxs-lookup"><span data-stu-id="fe239-148">See also</span></span>

- [<span data-ttu-id="fe239-149">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe239-149">Debugging Interfaces</span></span>](debugging-interfaces.md)
