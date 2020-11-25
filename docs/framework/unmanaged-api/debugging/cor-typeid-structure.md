---
title: COR_TYPEID 구조체
ms.date: 03/30/2017
api_name:
- COR_TYPEID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPEID
helpviewer_keywords:
- COR_TYPEID structure [.NET Framework debugging]
ms.assetid: 1e172b14-ee22-4943-b3b8-3740e7bdcd2e
topic_type:
- apiref
ms.openlocfilehash: 5eeb5aef7edaa23385190a309144e1477da741e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697443"
---
# <a name="cor_typeid-structure"></a><span data-ttu-id="3674b-102">COR_TYPEID 구조체</span><span class="sxs-lookup"><span data-stu-id="3674b-102">COR_TYPEID Structure</span></span>

<span data-ttu-id="3674b-103">유형 식별자를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-103">Contains a type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3674b-104">구문</span><span class="sxs-lookup"><span data-stu-id="3674b-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPEID{  
    UINT64 token1;  
    UINT64 token2;  
} COR_TYPEID;  
```  
  
## <a name="members"></a><span data-ttu-id="3674b-105">멤버</span><span class="sxs-lookup"><span data-stu-id="3674b-105">Members</span></span>  
  
|<span data-ttu-id="3674b-106">멤버</span><span class="sxs-lookup"><span data-stu-id="3674b-106">Member</span></span>|<span data-ttu-id="3674b-107">설명</span><span class="sxs-lookup"><span data-stu-id="3674b-107">Description</span></span>|  
|------------|-----------------|  
|`token1`|<span data-ttu-id="3674b-108">첫 번째 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-108">The first token.</span></span>|  
|`token2`|<span data-ttu-id="3674b-109">두 번째 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-109">The second token.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3674b-110">설명</span><span class="sxs-lookup"><span data-stu-id="3674b-110">Remarks</span></span>  

 <span data-ttu-id="3674b-111">`COR_TYPEID`구조체는 가비지 수집 될 개체에 대 한 정보를 제공 하는 다양 한 디버깅 메서드에서 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-111">The `COR_TYPEID` structure is returned by a number of debugging methods that provide information about objects to be garbage-collected.</span></span> <span data-ttu-id="3674b-112">그런 다음 해당 항목에 대 한 추가 정보를 제공 하는 다른 디버깅 메서드에 인수로 전달 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-112">It can then be passed as an argument to other debugging methods that provide additional information about that item.</span></span> <span data-ttu-id="3674b-113">예를 들어 [ICorDebugHeapEnum](icordebugheapenum-interface.md) 개체를 열거 하 여 관리 되는 힙에서 개별 개체를 나타내는 개별 [COR_HEAPOBJECT](cor-heapobject-structure.md) 개체를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-113">For example, by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) object, you can retrieve individual [COR_HEAPOBJECT](cor-heapobject-structure.md) objects that represent individual objects on the managed heap.</span></span> <span data-ttu-id="3674b-114">그런 다음 `COR_TYPEID` 필드의 값을 `COR_HEAPOBJECT.type` [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) 메서드로 전달 하 여 개체에 대 한 형식 정보를 제공 하는 ICorDebugType 개체를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-114">You can then pass the `COR_TYPEID` value from the `COR_HEAPOBJECT.type` field to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method to retrieve an ICorDebugType object that provides type information about the object.</span></span>  
  
 <span data-ttu-id="3674b-115">`COR_TYPEID`개체는 불투명 하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-115">A `COR_TYPEID` object is intended to be opaque.</span></span> <span data-ttu-id="3674b-116">개별 필드에 액세스 하거나 조작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-116">Its individual fields should not be accessed or manipulated.</span></span> <span data-ttu-id="3674b-117">유일한 용도는 메서드 호출에서 매개 변수로 제공 되는 식별자로 서, `out` 추가 정보를 제공 하기 위해 다른 메서드에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3674b-117">Its sole use is as an identifier that is provided as an `out` parameter in a method call and that can, in turn, be passed to other methods to provide additional information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3674b-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3674b-118">Requirements</span></span>  

 <span data-ttu-id="3674b-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3674b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3674b-120">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3674b-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3674b-121">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3674b-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3674b-122">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3674b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3674b-123">참조</span><span class="sxs-lookup"><span data-stu-id="3674b-123">See also</span></span>

- [<span data-ttu-id="3674b-124">디버깅 구조체</span><span class="sxs-lookup"><span data-stu-id="3674b-124">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3674b-125">디버깅</span><span class="sxs-lookup"><span data-stu-id="3674b-125">Debugging</span></span>](index.md)
