---
description: '자세히 알아보기: ICorDebugController:: Continue 메서드'
title: ICorDebugController::Continue 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
ms.openlocfilehash: e5858a8c287e8dd5a493a85c9f427ad8acd9ecc5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710805"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="48853-103">ICorDebugController::Continue 메서드</span><span class="sxs-lookup"><span data-stu-id="48853-103">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="48853-104">[Stop 메서드](icordebugcontroller-stop-method.md)를 호출한 후 관리 되는 스레드의 실행을 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="48853-104">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="48853-105">구문</span><span class="sxs-lookup"><span data-stu-id="48853-105">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="48853-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="48853-106">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="48853-107">진행 `true` Out-of-band 이벤트에서 계속 하면로 설정 하 고, 그렇지 않으면로 설정 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="48853-107">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="48853-108">설명</span><span class="sxs-lookup"><span data-stu-id="48853-108">Remarks</span></span>

<span data-ttu-id="48853-109">`Continue` 메서드를 호출한 후 프로세스를 계속 합니다 `ICorDebugController::Stop` .</span><span class="sxs-lookup"><span data-stu-id="48853-109">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="48853-110">혼합 모드 디버깅을 수행 하는 경우 `Continue` 대역 외 이벤트에서 계속 하지 않으면 Win32 이벤트 스레드에서를 호출 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="48853-110">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="48853-111">*대역내 이벤트* 는 관리 되는 이벤트 이거나 디버거가 프로세스의 관리 되는 상태와의 상호 작용을 지 원하는 동안 관리 되는 이벤트 또는 일반적인 관리 되지 않는 이벤트입니다.</span><span class="sxs-lookup"><span data-stu-id="48853-111">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="48853-112">이 경우 디버거는 매개 변수를로 설정 하 여 [ICorDebugUnmanagedCallback::D E버그 이벤트](icordebugunmanagedcallback-debugevent-method.md) 콜백을 수신 합니다 `fOutOfBand` `false` .</span><span class="sxs-lookup"><span data-stu-id="48853-112">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="48853-113">*Out-of-band 이벤트* 는 관리 되지 않는 이벤트로, 프로세스의 관리 되는 상태와의 상호 작용은 이벤트로 인해 중지 되는 동안에는 불가능 합니다.</span><span class="sxs-lookup"><span data-stu-id="48853-113">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="48853-114">이 경우 디버거는 `ICorDebugUnmanagedCallback::DebugEvent` `fOutOfBand` 매개 변수를로 설정 하 여 콜백을 받습니다 `true` .</span><span class="sxs-lookup"><span data-stu-id="48853-114">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="48853-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="48853-115">Requirements</span></span>

<span data-ttu-id="48853-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="48853-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="48853-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48853-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="48853-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48853-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="48853-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48853-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
