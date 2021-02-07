---
description: '자세히 알아보기: ICorDebugProcess:: SetThreadContext 메서드'
title: ICorDebugProcess::SetThreadContext 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 3576c3bf3159e3960e7d2d4601ac2fb67d7218f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753980"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="cd60f-103">ICorDebugProcess::SetThreadContext 메서드</span><span class="sxs-lookup"><span data-stu-id="cd60f-103">ICorDebugProcess::SetThreadContext Method</span></span>

<span data-ttu-id="cd60f-104">이 프로세스의 지정 된 스레드에 대 한 컨텍스트를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-104">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd60f-105">구문</span><span class="sxs-lookup"><span data-stu-id="cd60f-105">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd60f-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cd60f-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="cd60f-107">진행 컨텍스트를 설정할 스레드의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-107">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cd60f-108">[in] `context` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="cd60f-109">진행 스레드의 컨텍스트를 설명 하는 바이트 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-109">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="cd60f-110">컨텍스트는 스레드가 실행 되는 프로세서의 아키텍처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd60f-111">설명</span><span class="sxs-lookup"><span data-stu-id="cd60f-111">Remarks</span></span>  

 <span data-ttu-id="cd60f-112">`SetThreadContext`스레드가 실제로 해당 컨텍스트가 일시적으로 변경 된 "하이재킹" 상태가 될 수 있으므로 디버거가 Win32 함수 대신이 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-112">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="cd60f-113">이 메서드는 스레드가 네이티브 코드에 있는 경우에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="cd60f-114">관리 코드에서 스레드에 대해 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="cd60f-115">OOB (대역 외) 디버그 이벤트 중에는 스레드의 컨텍스트를 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-115">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="cd60f-116">전달 된 데이터는 현재 플랫폼에 대 한 컨텍스트 구조 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-116">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="cd60f-117">이 메서드는 부적절 하 게 사용 되는 경우 런타임을 손상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cd60f-117">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd60f-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cd60f-118">Requirements</span></span>  

 <span data-ttu-id="cd60f-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cd60f-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd60f-120">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd60f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd60f-121">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd60f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd60f-122">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd60f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
