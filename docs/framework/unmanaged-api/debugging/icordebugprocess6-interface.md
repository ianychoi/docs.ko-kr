---
title: ICorDebugProcess6 인터페이스
ms.date: 03/30/2017
ms.assetid: 34a10ac2-882c-4797-8369-f120e8e640c7
ms.openlocfilehash: ba70bab28eeddad6e3cf3c2b82b196a69ce68647
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732608"
---
# <a name="icordebugprocess6-interface"></a><span data-ttu-id="63975-102">ICorDebugProcess6 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63975-102">ICorDebugProcess6 Interface</span></span>

<span data-ttu-id="63975-103">네이티브 예외 디버그 이벤트에서 인코딩되는 관리되는 디버그 이벤트 디코딩, 가상 모듈 분할 등의 기능을 사용할 수 있도록 ICorDebugProcess 인터페이스를 논리적으로 확장합니다.</span><span class="sxs-lookup"><span data-stu-id="63975-103">Logically extends the ICorDebugProcess interface to enable features such as decoding managed debug events that are encoded in native exception debug events and virtual module splitting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63975-104">메서드</span><span class="sxs-lookup"><span data-stu-id="63975-104">Methods</span></span>  
  
|<span data-ttu-id="63975-105">메서드</span><span class="sxs-lookup"><span data-stu-id="63975-105">Method</span></span>|<span data-ttu-id="63975-106">설명</span><span class="sxs-lookup"><span data-stu-id="63975-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63975-107">DecodeEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-107">DecodeEvent Method</span></span>](icordebugprocess6-decodeevent-method.md)|<span data-ttu-id="63975-108">특수하게 작성된 네이티브 예외 디버그 이벤트의 페이로드에서 캡슐화된 관리되는 디버그 이벤트를 디코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="63975-108">Decodes managed debug events that have been encapsulated in the payload of specially crafted native exception debug events.</span></span>|  
|[<span data-ttu-id="63975-109">EnableVirtualModuleSplitting 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-109">EnableVirtualModuleSplitting Method</span></span>](icordebugprocess6-enablevirtualmodulesplitting-method.md)|<span data-ttu-id="63975-110">가상 모듈 분할을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="63975-110">Enables or disables virtual module splitting.</span></span>|  
|[<span data-ttu-id="63975-111">GetCode 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-111">GetCode Method</span></span>](icordebugprocess6-getcode-method.md)|<span data-ttu-id="63975-112">특정 코드 주소에서 관리 코드에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="63975-112">Gets information about the managed code at a particular code address.</span></span>|  
|[<span data-ttu-id="63975-113">GetExportStepInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-113">GetExportStepInfo Method</span></span>](icordebugprocess6-getexportstepinfo-method.md)|<span data-ttu-id="63975-114">관리 코드를 단계별로 실행할 수 있도록 런타임에 내보낸 함수에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="63975-114">Provides information on runtime exported functions to help step through managed code.</span></span>|  
|[<span data-ttu-id="63975-115">MarkDebuggerAttached 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-115">MarkDebuggerAttached Method</span></span>](icordebugprocess6-markdebuggerattached-method.md)|<span data-ttu-id="63975-116">.NET Framework 클래스 라이브러리의 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 메서드가 `true`를 반환하도록 디버기의 내부 상태를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="63975-116">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>|  
|[<span data-ttu-id="63975-117">ProcessStateChanged 메서드</span><span class="sxs-lookup"><span data-stu-id="63975-117">ProcessStateChanged Method</span></span>](icordebugprocess6-processstatechanged-method.md)|<span data-ttu-id="63975-118">프로세스가 실행 중임을 [ICorDebug](icordebug-interface.md) 에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="63975-118">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63975-119">설명</span><span class="sxs-lookup"><span data-stu-id="63975-119">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63975-120">이 인터페이스는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63975-120">The interface is available with .NET Native only.</span></span> <span data-ttu-id="63975-121">.NET 네이티브 외부의 ICorDebug 시나리오에 대해 `QueryInterface`를 호출하여 인터페이스 포인터를 검색하려고 하면 `E_NOINTERFACE`가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="63975-121">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63975-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="63975-122">Requirements</span></span>  

 <span data-ttu-id="63975-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63975-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63975-124">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63975-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63975-125">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63975-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63975-126">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63975-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63975-127">참조</span><span class="sxs-lookup"><span data-stu-id="63975-127">See also</span></span>

- [<span data-ttu-id="63975-128">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63975-128">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="63975-129">디버깅</span><span class="sxs-lookup"><span data-stu-id="63975-129">Debugging</span></span>](index.md)
