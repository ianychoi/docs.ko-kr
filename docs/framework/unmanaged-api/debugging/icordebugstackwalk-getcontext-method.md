---
description: '자세히 알아보기: ICorDebugStackWalk:: GetContext 메서드'
title: ICorDebugStackWalk::GetContext 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
ms.openlocfilehash: 30beefaa1e0e2e4c5043cae7213658ac24e8a1b6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649613"
---
# <a name="icordebugstackwalkgetcontext-method"></a><span data-ttu-id="e1290-103">ICorDebugStackWalk::GetContext 메서드</span><span class="sxs-lookup"><span data-stu-id="e1290-103">ICorDebugStackWalk::GetContext Method</span></span>

<span data-ttu-id="e1290-104">[ICorDebugStackWalk](icordebugstackwalk-interface.md) 개체의 현재 프레임에 대 한 컨텍스트를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-104">Returns the context for the current frame in the [ICorDebugStackWalk](icordebugstackwalk-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1290-105">구문</span><span class="sxs-lookup"><span data-stu-id="e1290-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1290-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e1290-106">Parameters</span></span>  

 `contextFlags`  
 <span data-ttu-id="e1290-107">진행 WinNT에 정의 된 컨텍스트 버퍼의 요청 된 콘텐츠를 나타내는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-107">[in] Flags that indicate the requested contents of the context buffer (defined in WinNT.h).</span></span>  
  
 `contextBufSize`  
 <span data-ttu-id="e1290-108">진행 할당 된 컨텍스트 버퍼 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-108">[in] The allocated size of the context buffer.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="e1290-109">제한이 컨텍스트의 실제 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-109">[out] The actual size of the context.</span></span> <span data-ttu-id="e1290-110">이 값은 컨텍스트 버퍼의 크기 보다 작거나 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-110">This value must be less than or equal to the size of the context buffer.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="e1290-111">제한이 컨텍스트 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-111">[out] The context buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e1290-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="e1290-112">Return Value</span></span>  

 <span data-ttu-id="e1290-113">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-113">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e1290-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e1290-114">HRESULT</span></span>|<span data-ttu-id="e1290-115">설명</span><span class="sxs-lookup"><span data-stu-id="e1290-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e1290-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="e1290-116">S_OK</span></span>|<span data-ttu-id="e1290-117">현재 프레임에 대 한 컨텍스트가 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-117">The context for the current frame was successfully returned.</span></span>|  
|<span data-ttu-id="e1290-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e1290-118">E_FAIL</span></span>|<span data-ttu-id="e1290-119">컨텍스트를 반환할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-119">The context could not be returned.</span></span>|  
|<span data-ttu-id="e1290-120">HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT 버퍼)</span><span class="sxs-lookup"><span data-stu-id="e1290-120">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)</span></span>|<span data-ttu-id="e1290-121">컨텍스트 버퍼가 너무 작습니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-121">The context buffer is too small.</span></span>|  
|<span data-ttu-id="e1290-122">CORDBG_E_PAST_END_OF_STACK</span><span class="sxs-lookup"><span data-stu-id="e1290-122">CORDBG_E_PAST_END_OF_STACK</span></span>|<span data-ttu-id="e1290-123">프레임 포인터가 이미 스택의 끝에 있습니다. 따라서 추가 프레임에는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-123">The frame pointer is already at the end of the stack; therefore, no additional frames can be accessed.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="e1290-124">예외</span><span class="sxs-lookup"><span data-stu-id="e1290-124">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1290-125">설명</span><span class="sxs-lookup"><span data-stu-id="e1290-125">Remarks</span></span>  

 <span data-ttu-id="e1290-126">해제 하면 비휘발성 레지스터와 같이 레지스터의 하위 집합만 복원 되므로 컨텍스트는 호출 시 등록 상태와 정확 하 게 일치 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e1290-126">Because unwinding restores only a subset of the registers, such as non-volatile registers, the context may not exactly match the register state at the time of the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1290-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e1290-127">Requirements</span></span>  

 <span data-ttu-id="e1290-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e1290-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1290-129">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1290-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1290-130">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1290-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1290-131">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1290-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1290-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e1290-132">See also</span></span>

- [<span data-ttu-id="e1290-133">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e1290-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="e1290-134">디버깅</span><span class="sxs-lookup"><span data-stu-id="e1290-134">Debugging</span></span>](index.md)
