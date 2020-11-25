---
title: ICorDebugRegisterSet2 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712326"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="a730f-102">ICorDebugRegisterSet2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a730f-102">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="a730f-103">64 개 이상의 레지스터가 있는 하드웨어 플랫폼에 대 한 [ICorDebugRegisterSet](icordebugregisterset-interface.md) 인터페이스의 기능을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="a730f-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a730f-104">메서드</span><span class="sxs-lookup"><span data-stu-id="a730f-104">Methods</span></span>  
  
|<span data-ttu-id="a730f-105">메서드</span><span class="sxs-lookup"><span data-stu-id="a730f-105">Method</span></span>|<span data-ttu-id="a730f-106">설명</span><span class="sxs-lookup"><span data-stu-id="a730f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a730f-107">GetRegisters 메서드</span><span class="sxs-lookup"><span data-stu-id="a730f-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="a730f-108">비트 마스크로 지정 된 각 레지스터의 값 (현재 코드를 실행 중인 컴퓨터)을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a730f-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="a730f-109">GetRegistersAvailable 메서드</span><span class="sxs-lookup"><span data-stu-id="a730f-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="a730f-110">사용 가능한 레지스터의 비트맵을 제공 하는 바이트 배열을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a730f-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="a730f-111">SetRegisters 메서드</span><span class="sxs-lookup"><span data-stu-id="a730f-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="a730f-112">.NET Framework 버전 2.0에서 구현 되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="a730f-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a730f-113">설명</span><span class="sxs-lookup"><span data-stu-id="a730f-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a730f-114">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a730f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a730f-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a730f-115">Requirements</span></span>  

 <span data-ttu-id="a730f-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a730f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a730f-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a730f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a730f-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a730f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a730f-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a730f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a730f-120">참조</span><span class="sxs-lookup"><span data-stu-id="a730f-120">See also</span></span>

- [<span data-ttu-id="a730f-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a730f-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a730f-122">ICorDebugRegisterSet 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a730f-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
