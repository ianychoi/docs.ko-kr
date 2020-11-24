---
title: ICorDebugManagedCallback2::ExceptionUnwind 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ExceptionUnwind
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind
helpviewer_keywords:
- ICorDebugManagedCallback2::ExceptionUnwind method [.NET Framework debugging]
- ExceptionUnwind method [.NET Framework debugging]
ms.assetid: aaf5938d-179c-4eaa-8d35-8523a4fadded
topic_type:
- apiref
ms.openlocfilehash: a15391b63012fec3d0e6a0aa67540c3d2541944c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671319"
---
# <a name="icordebugmanagedcallback2exceptionunwind-method"></a><span data-ttu-id="cc227-102">ICorDebugManagedCallback2::ExceptionUnwind 메서드</span><span class="sxs-lookup"><span data-stu-id="cc227-102">ICorDebugManagedCallback2::ExceptionUnwind Method</span></span>

<span data-ttu-id="cc227-103">예외 해제 프로세스 중에 상태 알림을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-103">Provides a status notification during the exception unwinding process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc227-104">구문</span><span class="sxs-lookup"><span data-stu-id="cc227-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionUnwind (  
    [in] ICorDebugAppDomain                  *pAppDomain,  
    [in] ICorDebugThread                     *pThread,  
    [in] CorDebugExceptionUnwindCallbackType  dwEventType,  
    [in] DWORD                                dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc227-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="cc227-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="cc227-106">진행 예외가 throw 된 스레드를 포함 하는 응용 프로그램 도메인을 나타내는 ICorDebugAppDomain 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the thread on which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="cc227-107">진행 예외가 throw 된 스레드를 나타내는 ICorDebugThread 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-107">[in] A pointer to an ICorDebugThread object that represents the thread on which the exception was thrown.</span></span>  
  
 `dwEventType`  
 <span data-ttu-id="cc227-108">진행 해제 단계에서 콜백이 신호를 받는 이벤트를 지정 하는 CorDebugExceptionUnwindCallbackType 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-108">[in] A value of the CorDebugExceptionUnwindCallbackType enumeration that specifies the event that is being signaled by the callback during the unwind phase.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="cc227-109">진행 예외에 대 한 추가 정보를 지정 하는 [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-109">[in] A value of the [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) enumeration that specifies additional information about the exception.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc227-110">설명</span><span class="sxs-lookup"><span data-stu-id="cc227-110">Remarks</span></span>  

 <span data-ttu-id="cc227-111">`ExceptionUnwind` 는 예외 처리 프로세스의 해제 단계 중 다양 한 지점에서 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-111">`ExceptionUnwind` is called at various points during the unwind phase of the exception-handling process.</span></span> <span data-ttu-id="cc227-112">`ExceptionUnwind` 단일 예외를 해제 하는 동안 두 번 이상 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-112">`ExceptionUnwind` can be called more than once while unwinding a single exception.</span></span>  
  
 <span data-ttu-id="cc227-113">`dwEventType`= DEBUG_EXCEPTION_INTERCEPTED 이면 명령 포인터가 스레드의 리프 프레임에 있습니다. 앞의 시퀀스 위치 (이전에는 몇 가지 지침 일 수 있음)가 예외를 발생 시킨 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="cc227-113">If `dwEventType` = DEBUG_EXCEPTION_INTERCEPTED, the instruction pointer will be in the leaf frame of the thread, at the sequence point before (this may be several instructions before) the instruction that led to the exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc227-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="cc227-114">Requirements</span></span>  

 <span data-ttu-id="cc227-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cc227-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc227-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc227-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc227-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc227-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc227-118">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc227-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc227-119">참조</span><span class="sxs-lookup"><span data-stu-id="cc227-119">See also</span></span>

- [<span data-ttu-id="cc227-120">ICorDebugManagedCallback2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="cc227-120">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="cc227-121">ICorDebugManagedCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="cc227-121">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
