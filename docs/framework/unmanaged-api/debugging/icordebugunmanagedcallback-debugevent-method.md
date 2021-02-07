---
description: ICorDebugUnmanagedCallback::D ebugEvent 메서드에 대해 자세히 알아보세요.
title: ICorDebugUnmanagedCallback::DebugEvent 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugUnmanagedCallback.DebugEvent
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugUnmanagedCallback::DebugEvent
helpviewer_keywords:
- DebugEvent method [.NET Framework debugging]
- ICorDebugUnmanagedCallback::DebugEvent method [.NET Framework debugging]
ms.assetid: be9cab04-65ec-44d5-a39a-f90709fdd043
topic_type:
- apiref
ms.openlocfilehash: fcd7bc3b380add7465473cb01585eb1656d00aad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690576"
---
# <a name="icordebugunmanagedcallbackdebugevent-method"></a><span data-ttu-id="0cb53-103">ICorDebugUnmanagedCallback::DebugEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="0cb53-103">ICorDebugUnmanagedCallback::DebugEvent Method</span></span>

<span data-ttu-id="0cb53-104">네이티브 이벤트가 발생 했음을 디버거에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-104">Notifies the debugger that a native event has been fired.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb53-105">구문</span><span class="sxs-lookup"><span data-stu-id="0cb53-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugEvent (  
    [in] LPDEBUG_EVENT  pDebugEvent,  
    [in] BOOL           fOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0cb53-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0cb53-106">Parameters</span></span>  

 `pDebugEvent`  
 <span data-ttu-id="0cb53-107">진행 네이티브 이벤트에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-107">[in] A pointer to the native event.</span></span>  
  
 `fOutOfBand`  
 <span data-ttu-id="0cb53-108">[in] `true` 디버거가 [ICorDebugController:: Continue](icordebugcontroller-continue-method.md)를 호출할 때까지 관리 되는 프로세스 상태와의 상호 작용을 할 수 없는 경우이 고, 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-108">[in] `true`, if interaction with the managed process state is impossible after an unmanaged event occurs, until the debugger calls [ICorDebugController::Continue](icordebugcontroller-continue-method.md); otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cb53-109">설명</span><span class="sxs-lookup"><span data-stu-id="0cb53-109">Remarks</span></span>  

 <span data-ttu-id="0cb53-110">디버깅 중인 스레드가 Win32 스레드 이면 Win32 디버깅 인터페이스의 멤버를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="0cb53-110">If the thread being debugged is a Win32 thread, do not use any members of the Win32 debugging interface.</span></span> <span data-ttu-id="0cb53-111">`ICorDebugController::Continue`대역 외 이벤트를 계속 진행 하는 경우에만 Win32 스레드에서만를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-111">You can call `ICorDebugController::Continue` only on a Win32 thread and only when continuing past an out-of-band event.</span></span>  
  
 <span data-ttu-id="0cb53-112">콜백은 `DebugEvent` 콜백에 대 한 표준 규칙을 따르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-112">The `DebugEvent` callback does not follow the standard rules for callbacks.</span></span> <span data-ttu-id="0cb53-113">를 호출 하면 `DebugEvent` 프로세스가 RAW OS-debug 중지 됨 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-113">When you call `DebugEvent`, the process will be in the raw, OS-debug stopped state.</span></span> <span data-ttu-id="0cb53-114">프로세스는 동기화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-114">The process will not be synchronized.</span></span> <span data-ttu-id="0cb53-115">관리 코드에 대 한 정보 요청을 충족 하기 위해 필요한 경우 자동으로 동기화 된 상태가 자동으로 입력 되므로 다른 중첩 된 콜백이 발생할 수 있습니다 `DebugEvent` .</span><span class="sxs-lookup"><span data-stu-id="0cb53-115">It will automatically enter the synchronized state when necessary to satisfy requests for information about managed code, which may result in other nested `DebugEvent` callbacks.</span></span>  
  
 <span data-ttu-id="0cb53-116">프로세스를 계속 하기 전에 예외 이벤트를 무시 하려면 프로세스에서 [ICorDebugProcess:: ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) 을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-116">Call [ICorDebugProcess::ClearCurrentException](icordebugprocess-clearcurrentexception-method.md) on the process to ignore an exception event before continuing the process.</span></span> <span data-ttu-id="0cb53-117">이 메서드를 호출 하면 CONTINUE 요청에서 DBG_EXCEPTION_NOT_HANDLED 대신 DBG_CONTINUE를 보내고, 대역 외 중단점과 단일 단계 예외를 자동으로 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-117">Calling this method sends DBG_CONTINUE instead of DBG_EXCEPTION_NOT_HANDLED on the continue request, and automatically clears out-of-band breakpoints and single-step exceptions.</span></span> <span data-ttu-id="0cb53-118">Out-of-band 이벤트는 디버깅 중인 응용 프로그램이 중지 되 고 처리 중인 대역 내 이벤트가 이미 있는 경우에도 언제 든 지 제공 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-118">Out-of-band events can come at any time, even when the application being debugged appears stopped and when an outstanding in-band event already exists.</span></span>  
  
 <span data-ttu-id="0cb53-119">.NET Framework 버전 2.0에서 디버거는 대역 외 중단점 이벤트를 즉시 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-119">In the .NET Framework version 2.0, the debugger should immediately continue past an out-of-band breakpoint event.</span></span> <span data-ttu-id="0cb53-120">디버거는 [ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) 및 [ICorDebugProcess2:: ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) 메서드를 사용 하 여 중단점을 추가 하 고 제거 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-120">The debugger should be using the [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) and [ICorDebugProcess2::ClearUnmanagedBreakpoint](icordebugprocess2-clearunmanagedbreakpoint-method.md) methods to add and remove breakpoints.</span></span> <span data-ttu-id="0cb53-121">이러한 메서드는 대역 외 중단점을 자동으로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="0cb53-121">These methods will skip over any out-of-band breakpoints automatically.</span></span> <span data-ttu-id="0cb53-122">따라서 디스패치되는 대역 외 중단점은 Win32 함수에 대 한 호출과 같이 명령 스트림에 이미 있는 원시 중단점 이어야 합니다 `DebugBreak` .</span><span class="sxs-lookup"><span data-stu-id="0cb53-122">Thus, the only out-of-band breakpoints that get dispatched should be raw breakpoints that are already in the instruction stream, such as a call to the Win32 `DebugBreak` function.</span></span> <span data-ttu-id="0cb53-123">`ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess:: getthreadcontext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess:: setthreadcontext](icordebugprocess-setthreadcontext-method.md)또는 [디버깅 API](index.md)의 다른 멤버를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="0cb53-123">Do not try to use `ICorDebugProcess::ClearCurrentException`, [ICorDebugProcess::GetThreadContext](icordebugprocess-getthreadcontext-method.md), [ICorDebugProcess::SetThreadContext](icordebugprocess-setthreadcontext-method.md), or any other member of the [debugging API](index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb53-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0cb53-124">Requirements</span></span>  

 <span data-ttu-id="0cb53-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0cb53-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb53-126">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0cb53-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cb53-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0cb53-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cb53-128">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb53-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb53-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0cb53-129">See also</span></span>

- [<span data-ttu-id="0cb53-130">ICorDebugUnmanagedCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0cb53-130">ICorDebugUnmanagedCallback Interface</span></span>](icordebugunmanagedcallback-interface.md)
