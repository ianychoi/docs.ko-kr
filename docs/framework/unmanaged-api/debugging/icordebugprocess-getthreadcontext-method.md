---
description: '자세히 알아보기: ICorDebugProcess:: GetThreadContext 메서드'
title: ICorDebugProcess::GetThreadContext 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 4cb926183522548e924013580f207d1d0677a0d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746869"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="4151a-103">ICorDebugProcess::GetThreadContext 메서드</span><span class="sxs-lookup"><span data-stu-id="4151a-103">ICorDebugProcess::GetThreadContext Method</span></span>

<span data-ttu-id="4151a-104">이 프로세스의 지정 된 스레드에 대 한 컨텍스트를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-104">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4151a-105">구문</span><span class="sxs-lookup"><span data-stu-id="4151a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4151a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4151a-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="4151a-107">진행 컨텍스트를 검색할 스레드의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-107">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="4151a-108">[in] `context` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-108">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="4151a-109">[in, out] 스레드의 컨텍스트를 설명 하는 바이트 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-109">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="4151a-110">컨텍스트는 스레드가 실행 되는 프로세서의 아키텍처를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-110">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4151a-111">설명</span><span class="sxs-lookup"><span data-stu-id="4151a-111">Remarks</span></span>  

 <span data-ttu-id="4151a-112">`GetThreadContext`스레드가 실제로 해당 컨텍스트가 일시적으로 변경 된 "하이재킹" 상태가 될 수 있으므로 디버거가 Win32 메서드가 아닌이 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-112">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="4151a-113">이 메서드는 스레드가 네이티브 코드에 있는 경우에만 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-113">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="4151a-114">관리 코드에서 스레드에 대해 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-114">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="4151a-115">반환 된 데이터는 현재 플랫폼에 대 한 컨텍스트 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-115">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="4151a-116">Win32 `GetThreadContext` 메서드와 마찬가지로 호출자는 `context` 이 메서드를 호출 하기 전에 매개 변수를 초기화 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4151a-116">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4151a-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4151a-117">Requirements</span></span>  

 <span data-ttu-id="4151a-118">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4151a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4151a-119">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4151a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4151a-120">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4151a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4151a-121">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4151a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
