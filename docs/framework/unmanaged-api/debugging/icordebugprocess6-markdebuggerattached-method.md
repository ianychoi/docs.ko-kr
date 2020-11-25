---
title: ICorDebugProcess6::MarkDebuggerAttached 메서드
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c6543a89a375d4a2887dbe8cff56d66a15650811
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732595"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="73199-102">ICorDebugProcess6::MarkDebuggerAttached 메서드</span><span class="sxs-lookup"><span data-stu-id="73199-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>

<span data-ttu-id="73199-103">.NET Framework 클래스 라이브러리의 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 메서드가 `true`를 반환하도록 디버기의 내부 상태를 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="73199-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73199-104">구문</span><span class="sxs-lookup"><span data-stu-id="73199-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73199-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="73199-105">Parameters</span></span>  

 `fIsAttached`  
 <span data-ttu-id="73199-106">`true` 메서드가 디버거가 연결되어 있음을 나타내야 하는 경우 <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType>이고, 그러지 않으면 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="73199-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73199-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="73199-107">Return Value</span></span>  

 <span data-ttu-id="73199-108">이 메서드는 다음 표에 나와 있는 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="73199-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="73199-109">Return value</span></span>|<span data-ttu-id="73199-110">설명</span><span class="sxs-lookup"><span data-stu-id="73199-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="73199-111">디버기를 정상적으로 업데이트했습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="73199-112"><xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> 메서드를 포함하는 어셈블리가 로드되지 않았거나 메타데이터 누락 등의 기타 오류로 인해 어셈블리를 인식할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="73199-113">이 오류는 흔히 발생하며 심각하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-113">This error is common and benign.</span></span> <span data-ttu-id="73199-114">추가 어셈블리가 로드되면 메서드를 다시 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="73199-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="73199-115">기타 오류 `HRESULT` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="73199-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="73199-116">다른 값이 반환되는 경우 디버거나 컴파일러 구성 요소가 오동작하는 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73199-117">설명</span><span class="sxs-lookup"><span data-stu-id="73199-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73199-118">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73199-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73199-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="73199-119">Requirements</span></span>  

 <span data-ttu-id="73199-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73199-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73199-121">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73199-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73199-122">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73199-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73199-123">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73199-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73199-124">참조</span><span class="sxs-lookup"><span data-stu-id="73199-124">See also</span></span>

- [<span data-ttu-id="73199-125">ICorDebugProcess6 인터페이스</span><span class="sxs-lookup"><span data-stu-id="73199-125">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="73199-126">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="73199-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
