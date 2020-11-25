---
title: ICorDebugExceptionDebugEvent::GetStackPointer 메서드
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 46906e7d3ce7f257eb776e50dc6097946eb77d1f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697404"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="d73ac-102">ICorDebugExceptionDebugEvent::GetStackPointer 메서드</span><span class="sxs-lookup"><span data-stu-id="d73ac-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>

<span data-ttu-id="d73ac-103">이 예외 디버그 이벤트에 대한 스택 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d73ac-104">구문</span><span class="sxs-lookup"><span data-stu-id="d73ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d73ac-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d73ac-105">Parameters</span></span>  

 `pStackPointer`  
 <span data-ttu-id="d73ac-106">[out] 이 예외 디버그 이벤트의 스택 포인터에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="d73ac-107">자세한 내용은 설명 부분을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d73ac-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d73ac-108">설명</span><span class="sxs-lookup"><span data-stu-id="d73ac-108">Remarks</span></span>  

 <span data-ttu-id="d73ac-109">이 스택 포인터의 의미는 다음 표와 같이 이벤트 유형에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d73ac-110">이벤트 유형</span><span class="sxs-lookup"><span data-stu-id="d73ac-110">Event type</span></span>|<span data-ttu-id="d73ac-111">`pStackPointer` 값의 의미</span><span class="sxs-lookup"><span data-stu-id="d73ac-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="d73ac-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d73ac-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="d73ac-113">예외를 throw한 프레임에 대한 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="d73ac-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="d73ac-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="d73ac-115">예외가 throw된 지점과 가장 가까운 사용자 코드 프레임에 대한 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="d73ac-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="d73ac-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="d73ac-117">catch 처리기가 포함된 프레임에 대한 스택 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="d73ac-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="d73ac-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="d73ac-119">`pStackPointer`가 **null** 인 경우</span><span class="sxs-lookup"><span data-stu-id="d73ac-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="d73ac-120">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="d73ac-121">이벤트 유형은 [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) 메서드에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d73ac-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d73ac-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d73ac-122">Requirements</span></span>  

 <span data-ttu-id="d73ac-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d73ac-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d73ac-124">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d73ac-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d73ac-125">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d73ac-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d73ac-126">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d73ac-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d73ac-127">참조</span><span class="sxs-lookup"><span data-stu-id="d73ac-127">See also</span></span>

- [<span data-ttu-id="d73ac-128">ICorDebugExceptionDebugEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d73ac-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="d73ac-129">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d73ac-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
