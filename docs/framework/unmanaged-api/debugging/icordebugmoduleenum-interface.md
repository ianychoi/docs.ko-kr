---
title: ICorDebugModuleEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: 08d16393a04888cd3f1a03fa209a1fceac28520b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724756"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="878bd-102">ICorDebugModuleEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="878bd-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="878bd-103">ICorDebugEnum 메서드를 구현 하 고 ICorDebugModule 배열을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="878bd-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="878bd-104">메서드</span><span class="sxs-lookup"><span data-stu-id="878bd-104">Methods</span></span>  
  
|<span data-ttu-id="878bd-105">메서드</span><span class="sxs-lookup"><span data-stu-id="878bd-105">Method</span></span>|<span data-ttu-id="878bd-106">설명</span><span class="sxs-lookup"><span data-stu-id="878bd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="878bd-107">Next 메서드</span><span class="sxs-lookup"><span data-stu-id="878bd-107">Next Method</span></span>](icordebugmoduleenum-next-method.md)|<span data-ttu-id="878bd-108">`ICorDebugModule`현재 위치에서 시작 하 여 열거형에서 지정 된 수의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="878bd-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="878bd-109">설명</span><span class="sxs-lookup"><span data-stu-id="878bd-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="878bd-110">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="878bd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="878bd-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="878bd-111">Requirements</span></span>  

 <span data-ttu-id="878bd-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="878bd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="878bd-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="878bd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="878bd-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="878bd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="878bd-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="878bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878bd-116">참조</span><span class="sxs-lookup"><span data-stu-id="878bd-116">See also</span></span>

- [<span data-ttu-id="878bd-117">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="878bd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
