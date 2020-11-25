---
title: ICorDebugCode3 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 609cd557db71fac53aadf613534a23e988b14bde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720760"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="f2750-102">ICorDebugCode3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f2750-102">ICorDebugCode3 Interface</span></span>

<span data-ttu-id="f2750-103">관리 되는 반환 값에 대 한 정보를 제공 하기 위해 "ICorDebugCode" 및 "ICorDebugCode2"를 확장 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f2750-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f2750-104">메서드</span><span class="sxs-lookup"><span data-stu-id="f2750-104">Methods</span></span>  
  
|<span data-ttu-id="f2750-105">메서드</span><span class="sxs-lookup"><span data-stu-id="f2750-105">Method</span></span>|<span data-ttu-id="f2750-106">설명</span><span class="sxs-lookup"><span data-stu-id="f2750-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f2750-107">GetReturnValueLiveOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="f2750-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="f2750-108">지정 된 IL 오프셋의 경우 디버거가 함수에서 반환 값을 가져올 수 있도록 중단점이 배치 되어야 하는 네이티브 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f2750-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f2750-109">설명</span><span class="sxs-lookup"><span data-stu-id="f2750-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f2750-110">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f2750-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2750-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f2750-111">Requirements</span></span>  

 <span data-ttu-id="f2750-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f2750-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2750-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2750-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2750-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2750-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2750-115">**.NET Framework 버전:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2750-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2750-116">참조</span><span class="sxs-lookup"><span data-stu-id="f2750-116">See also</span></span>

- [<span data-ttu-id="f2750-117">ICorDebugILFrame3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f2750-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="f2750-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f2750-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
