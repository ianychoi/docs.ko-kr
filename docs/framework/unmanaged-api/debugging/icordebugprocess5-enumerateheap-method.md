---
title: ICorDebugProcess5::EnumerateHeap 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: 22ab29f8a204a4b27dafdefcd3652cc3dcf9769c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671137"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="8cc1d-102">ICorDebugProcess5::EnumerateHeap 메서드</span><span class="sxs-lookup"><span data-stu-id="8cc1d-102">ICorDebugProcess5::EnumerateHeap Method</span></span>

<span data-ttu-id="8cc1d-103">관리 되는 힙의 개체에 대 한 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-103">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cc1d-104">구문</span><span class="sxs-lookup"><span data-stu-id="8cc1d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cc1d-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8cc1d-105">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="8cc1d-106">제한이 관리 되는 힙에 있는 개체의 열거자 인 [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-106">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cc1d-107">설명</span><span class="sxs-lookup"><span data-stu-id="8cc1d-107">Remarks</span></span>  

 <span data-ttu-id="8cc1d-108">메서드를 호출 하기 전에 `ICorDebugProcess5::EnumerateHeap` [ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) 메서드를 호출 하 고 `areGCStructuresValid` 반환 된 [COR_HEAPINFO](cor-heapinfo-structure.md) 개체의 필드 값을 검사 하 여 현재 상태에서 가비지 컬렉션 힙을 열거 가능 하 게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-108">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="8cc1d-109">또한은 `ICorDebugProcess5::EnumerateHeap` `E_FAIL` 프로세스 수명 중 너무 일찍 연결 하는 경우에는 관리 되는 힙의 메모리를 할당 하기 전에를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-109">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="8cc1d-110">[ICorDebugHeapEnum](icordebugheapenum-interface.md) interface 개체는 개체 [COR_HEAPOBJECT](cor-heapobject-structure.md) 열거할 수 있도록 하는 ICorDebugEnum 인터페이스에서 파생 된 표준 열거자입니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-110">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="8cc1d-111">이 메서드는 모든 개체에 대 한 정보를 제공 하는 [COR_HEAPOBJECT](cor-heapobject-structure.md) 인스턴스로 [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection 개체를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-111">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="8cc1d-112">컬렉션에는 개체에 포함 되어 있지 않지만 가비지 수집기에서 아직 수집 되지 않은 개체에 대 한 정보를 제공 하는 [COR_HEAPOBJECT](cor-heapobject-structure.md) 인스턴스가 포함 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-112">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cc1d-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8cc1d-113">Requirements</span></span>  

 <span data-ttu-id="8cc1d-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8cc1d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cc1d-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cc1d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cc1d-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cc1d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cc1d-117">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cc1d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cc1d-118">참조</span><span class="sxs-lookup"><span data-stu-id="8cc1d-118">See also</span></span>

- [<span data-ttu-id="8cc1d-119">ICorDebugProcess5 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8cc1d-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="8cc1d-120">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8cc1d-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
