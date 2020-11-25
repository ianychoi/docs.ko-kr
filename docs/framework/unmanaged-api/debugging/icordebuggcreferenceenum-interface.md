---
title: ICorDebugGCReferenceEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
ms.openlocfilehash: 12ce800cb83ef4f79710aa441b50be860526023c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728123"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="13079-102">ICorDebugGCReferenceEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="13079-102">ICorDebugGCReferenceEnum Interface</span></span>

<span data-ttu-id="13079-103">가비지 수집되는 개체에 대한 열거자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="13079-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13079-104">메서드</span><span class="sxs-lookup"><span data-stu-id="13079-104">Methods</span></span>  
  
|<span data-ttu-id="13079-105">메서드</span><span class="sxs-lookup"><span data-stu-id="13079-105">Method</span></span>|<span data-ttu-id="13079-106">설명</span><span class="sxs-lookup"><span data-stu-id="13079-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13079-107">Next 메서드</span><span class="sxs-lookup"><span data-stu-id="13079-107">Next Method</span></span>](icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="13079-108">가비지 수집 되는 개체에 대 한 정보를 포함 하는 지정 된 수의 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="13079-108">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13079-109">설명</span><span class="sxs-lookup"><span data-stu-id="13079-109">Remarks</span></span>  

 <span data-ttu-id="13079-110">이 `ICorDebugGCReferenceEnum` 인터페이스는 "ICorDebugEnum" 인터페이스를 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="13079-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="13079-111">`ICorDebugGCReferenceEnum` [ICorDebugProcess5:: EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) 메서드를 호출 하 여 인스턴스가 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 인스턴스로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="13079-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="13079-112">[ICorDebugGCReference:: Next](icordebuggcreferenceenum-next-method.md) 메서드를 호출 하 여 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 개체를 열거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13079-112">[COR_GC_REFERENCE](cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="13079-113">이 메서드로 채워진 컬렉션의 [COR_GC_REFERENCE](cor-gc-reference-structure.md) 개체는 다음과 같은 세 가지 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="13079-113">The [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
- <span data-ttu-id="13079-114">모든 관리 되는 스택의 개체</span><span class="sxs-lookup"><span data-stu-id="13079-114">Objects from all managed stacks.</span></span> <span data-ttu-id="13079-115">여기에는 공용 언어 런타임에서 만든 개체 뿐만 아니라 관리 코드의 라이브 참조도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13079-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
- <span data-ttu-id="13079-116">핸들 테이블의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="13079-116">Objects from the handle table.</span></span> <span data-ttu-id="13079-117">여기에는 모듈의 강력한 참조 ( `HNDTYPE_STRONG` 및 `HNDTYPE_REFCOUNT` ) 및 정적 변수가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="13079-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
- <span data-ttu-id="13079-118">종료자 큐의 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="13079-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="13079-119">종료자는 종료 자가 실행 될 때까지 개체를 큐에 대기 합니다.</span><span class="sxs-lookup"><span data-stu-id="13079-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13079-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="13079-120">Requirements</span></span>  

 <span data-ttu-id="13079-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="13079-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13079-122">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13079-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13079-123">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13079-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13079-124">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13079-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13079-125">참조</span><span class="sxs-lookup"><span data-stu-id="13079-125">See also</span></span>

- [<span data-ttu-id="13079-126">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="13079-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
