---
title: ICorDebug::SetManagedHandler 메서드
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 97a4a464d3dfb7b333f44ac4206bd880fd171e16
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723417"
---
# <a name="icordebugsetmanagedhandler-method"></a><span data-ttu-id="5db27-102">ICorDebug::SetManagedHandler 메서드</span><span class="sxs-lookup"><span data-stu-id="5db27-102">ICorDebug::SetManagedHandler Method</span></span>

<span data-ttu-id="5db27-103">관리 되는 이벤트에 대 한 이벤트 처리기 개체를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db27-103">Specifies the event handler object for managed events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5db27-104">구문</span><span class="sxs-lookup"><span data-stu-id="5db27-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5db27-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5db27-105">Parameters</span></span>  

 `pCallback`  
 <span data-ttu-id="5db27-106">진행 이벤트 처리기 개체인 [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="5db27-106">[in] A pointer to an [ICorDebugManagedCallback](icordebugmanagedcallback-interface.md) object, which is the event handler object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5db27-107">설명</span><span class="sxs-lookup"><span data-stu-id="5db27-107">Remarks</span></span>  

 <span data-ttu-id="5db27-108">`SetManagedHandler` 만들 때를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db27-108">`SetManagedHandler` must be called at creation time.</span></span>  
  
 <span data-ttu-id="5db27-109">구현에 디버깅 `ICorDebugManagedCallback` 중인 응용 프로그램에 대 한 디버깅 이벤트를 처리 하기에 충분 한 인터페이스가 포함 되지 않은 경우 `SetManagedHandler` E_NOINTERFACE의 HRESULT를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5db27-109">If the `ICorDebugManagedCallback` implementation does not contain sufficient interfaces to handle debugging events for the application that is being debugged, `SetManagedHandler` returns an HRESULT of E_NOINTERFACE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5db27-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5db27-110">Requirements</span></span>  

 <span data-ttu-id="5db27-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5db27-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5db27-112">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5db27-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5db27-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5db27-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5db27-114">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5db27-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5db27-115">참조</span><span class="sxs-lookup"><span data-stu-id="5db27-115">See also</span></span>

- [<span data-ttu-id="5db27-116">ICorDebug 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5db27-116">ICorDebug Interface</span></span>](icordebug-interface.md)
