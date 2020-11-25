---
title: ICorDebugProcessEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
ms.openlocfilehash: 31f26a40294857701b151cd2fce35b061da28238
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732530"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="c5626-102">ICorDebugProcessEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c5626-102">ICorDebugProcessEnum Interface</span></span>

<span data-ttu-id="c5626-103">ICorDebugEnum 메서드를 구현 하 고 ICorDebugProcess 배열을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5626-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c5626-104">메서드</span><span class="sxs-lookup"><span data-stu-id="c5626-104">Methods</span></span>  
  
|<span data-ttu-id="c5626-105">메서드</span><span class="sxs-lookup"><span data-stu-id="c5626-105">Method</span></span>|<span data-ttu-id="c5626-106">설명</span><span class="sxs-lookup"><span data-stu-id="c5626-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c5626-107">Next 메서드</span><span class="sxs-lookup"><span data-stu-id="c5626-107">Next Method</span></span>](icordebugprocessenum-next-method.md)|<span data-ttu-id="c5626-108">`ICorDebugProcess`현재 위치에서 시작 하 여 열거형에서 지정 된 수의 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c5626-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5626-109">설명</span><span class="sxs-lookup"><span data-stu-id="c5626-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5626-110">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c5626-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5626-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c5626-111">Requirements</span></span>  

 <span data-ttu-id="c5626-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5626-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5626-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5626-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5626-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5626-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5626-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5626-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5626-116">참조</span><span class="sxs-lookup"><span data-stu-id="c5626-116">See also</span></span>

- [<span data-ttu-id="c5626-117">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c5626-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
