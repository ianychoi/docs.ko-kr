---
description: '자세히 알아보기: ICorDebugHeapValue 인터페이스'
title: ICorDebugHeapValue 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: 7c65cbce530f0d1f00d8610031fb604a0118ee29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803687"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="85588-103">ICorDebugHeapValue 인터페이스</span><span class="sxs-lookup"><span data-stu-id="85588-103">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="85588-104">CLR (공용 언어 런타임) 가비지 수집기에 의해 수집 된 개체를 나타내는 "ICorDebugValue"의 서브 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="85588-104">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="85588-105">메서드</span><span class="sxs-lookup"><span data-stu-id="85588-105">Methods</span></span>  
  
|<span data-ttu-id="85588-106">메서드</span><span class="sxs-lookup"><span data-stu-id="85588-106">Method</span></span>|<span data-ttu-id="85588-107">설명</span><span class="sxs-lookup"><span data-stu-id="85588-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85588-108">CreateRelocBreakpoint 메서드</span><span class="sxs-lookup"><span data-stu-id="85588-108">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="85588-109">구현되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="85588-109">Not implemented.</span></span>|  
|[<span data-ttu-id="85588-110">IsValid 메서드</span><span class="sxs-lookup"><span data-stu-id="85588-110">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="85588-111">이가 나타내는 개체가 `ICorDebugHeapValue` 유효한 지, 아니면 가비지 수집기에서 회수 되었는지를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="85588-111">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="85588-112">이 메서드는 .NET Framework 버전 2.0에서 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85588-112">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85588-113">설명</span><span class="sxs-lookup"><span data-stu-id="85588-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="85588-114">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="85588-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85588-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="85588-115">Requirements</span></span>  

 <span data-ttu-id="85588-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="85588-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85588-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="85588-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="85588-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85588-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85588-119">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85588-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85588-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="85588-120">See also</span></span>

- [<span data-ttu-id="85588-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="85588-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
