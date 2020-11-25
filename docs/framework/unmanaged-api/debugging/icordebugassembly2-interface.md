---
title: ICorDebugAssembly2 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
ms.openlocfilehash: 5add8f18a91f2ea1a2833ffa2cf3dc4bf3b644bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728474"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="9b327-102">ICorDebugAssembly2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9b327-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="9b327-103">어셈블리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9b327-103">Represents an assembly.</span></span> <span data-ttu-id="9b327-104">이 인터페이스는 ICorDebugAssembly 인터페이스의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="9b327-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b327-105">메서드</span><span class="sxs-lookup"><span data-stu-id="9b327-105">Methods</span></span>  
  
|<span data-ttu-id="9b327-106">메서드</span><span class="sxs-lookup"><span data-stu-id="9b327-106">Method</span></span>|<span data-ttu-id="9b327-107">설명</span><span class="sxs-lookup"><span data-stu-id="9b327-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b327-108">IsFullyTrusted 메서드</span><span class="sxs-lookup"><span data-stu-id="9b327-108">IsFullyTrusted Method</span></span>](icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="9b327-109">어셈블리에 런타임 보안 시스템에서 완전 신뢰를 부여 했는지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9b327-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b327-110">설명</span><span class="sxs-lookup"><span data-stu-id="9b327-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b327-111">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9b327-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b327-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9b327-112">Requirements</span></span>  

 <span data-ttu-id="9b327-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b327-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b327-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b327-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b327-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b327-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b327-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b327-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b327-117">참조</span><span class="sxs-lookup"><span data-stu-id="9b327-117">See also</span></span>

- [<span data-ttu-id="9b327-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9b327-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
