---
title: ICorDebugMutableDataTarget 인터페이스
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: cd22707832504ca2f08299872bc39bca2af782bb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709351"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="2bcbd-102">ICorDebugMutableDataTarget 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2bcbd-102">ICorDebugMutableDataTarget Interface</span></span>

<span data-ttu-id="2bcbd-103">[ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스를 확장 하 여 변경 가능한 데이터 대상을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bcbd-104">메서드</span><span class="sxs-lookup"><span data-stu-id="2bcbd-104">Methods</span></span>  
  
|<span data-ttu-id="2bcbd-105">메서드</span><span class="sxs-lookup"><span data-stu-id="2bcbd-105">Method</span></span>|<span data-ttu-id="2bcbd-106">설명</span><span class="sxs-lookup"><span data-stu-id="2bcbd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bcbd-107">ContinueStatusChanged 메서드</span><span class="sxs-lookup"><span data-stu-id="2bcbd-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="2bcbd-108">지정된 스레드에서 해결되지 않은 디버그 이벤트의 연속 상태를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="2bcbd-109">SetThreadContext 메서드</span><span class="sxs-lookup"><span data-stu-id="2bcbd-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="2bcbd-110">스레드에 대한 컨텍스트(레지스터 값)를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="2bcbd-111">WriteVirtual 메서드</span><span class="sxs-lookup"><span data-stu-id="2bcbd-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="2bcbd-112">대상 프로세스 주소 공간에 메모리를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2bcbd-113">설명</span><span class="sxs-lookup"><span data-stu-id="2bcbd-113">Remarks</span></span>  

 <span data-ttu-id="2bcbd-114">[ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스에 대 한이 확장은 대상 프로세스를 수정 하려는 디버깅 도구에 의해 구현 될 수 있습니다. 예를 들어 라이브 침입 디버깅을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="2bcbd-115">이러한 모든 메서드는 이 인터페이스를 구현하지 않거나 해당 메서드 호출에 실패해도 손실되는 핵심 검사 기반 디버깅 기능이 없다는 점에서 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="2bcbd-116">이러한 메서드의 모든 실패 `HRESULT`는 ICorDebug 메서드 호출의 `HRESULT`로 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="2bcbd-117">단일 ICorDebug 메서드 호출에서 여러 변경이 발생할 수 있으며, 관련 변경이 트랜잭션 방식으로 적용(전체 적용되거나 적용 안 함)되게 하는 메커니즘은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="2bcbd-118">즉, 동일한 ICorDebug 호출에 대한 다른 변경이 성공한 후 특정 변경이 실패할 경우 대상 프로세스가 불일치 상태로 남겨지고 디버깅이 불안정해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bcbd-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2bcbd-119">Requirements</span></span>  

 <span data-ttu-id="2bcbd-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2bcbd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bcbd-121">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bcbd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bcbd-122">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bcbd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bcbd-123">**.NET Framework 버전:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bcbd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bcbd-124">참조</span><span class="sxs-lookup"><span data-stu-id="2bcbd-124">See also</span></span>

- [<span data-ttu-id="2bcbd-125">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2bcbd-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2bcbd-126">디버깅</span><span class="sxs-lookup"><span data-stu-id="2bcbd-126">Debugging</span></span>](index.md)
