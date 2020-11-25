---
title: ICorDebugCode3::GetReturnValueLiveOffset 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugCode3.GetReturnValueLiveOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset
helpviewer_keywords:
- ICorDebugCode3::GetReturnValueLiveOffset method [.NET Framework debugging]
- GetReturnValueLiveOffset method [.NET Framework debugging]
ms.assetid: 8c2ff5d8-8c04-4423-b1e1-e1c8764b36d3
topic_type:
- apiref
ms.openlocfilehash: 6153ebf24ae939a50d71cad2d4323090aa905851
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720817"
---
# <a name="icordebugcode3getreturnvalueliveoffset-method"></a><span data-ttu-id="29ba1-102">ICorDebugCode3::GetReturnValueLiveOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="29ba1-102">ICorDebugCode3::GetReturnValueLiveOffset Method</span></span>

<span data-ttu-id="29ba1-103">지정 된 IL 오프셋의 경우 디버거가 함수에서 반환 값을 가져올 수 있도록 중단점이 배치 되어야 하는 네이티브 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-103">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ba1-104">구문</span><span class="sxs-lookup"><span data-stu-id="29ba1-104">Syntax</span></span>  
  
```cpp
HRESULT GetReturnValueLiveOffset(  
    [in] ULONG32 ILoffset,  
    [in] ULONG32 bufferSize,
    [out] ULONG32 *pFetched,
    [out, size_is(buffersize), length_is(*pFetched)] ULong32 pOffsets[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ba1-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="29ba1-105">Parameters</span></span>  

 `ILoffset`  
 <span data-ttu-id="29ba1-106">IL 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-106">The IL offset.</span></span> <span data-ttu-id="29ba1-107">함수 호출 사이트 여야 합니다. 그렇지 않으면 함수 호출이 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-107">It must be a function call site or the function call will fail.</span></span>  
  
 `bufferSize`  
 <span data-ttu-id="29ba1-108">저장 하는 데 사용할 수 있는 바이트 수 `pOffsets` 입니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-108">The number of bytes available to store `pOffsets`.</span></span>  
  
 `pFetched`  
 <span data-ttu-id="29ba1-109">실제로 반환 된 오프셋 수에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-109">A pointer to the number of offsets actually returned.</span></span> <span data-ttu-id="29ba1-110">일반적으로 해당 값은 1 이지만 단일 IL 명령은 여러 어셈블리 명령에 매핑할 수 있습니다 `CALL` .</span><span class="sxs-lookup"><span data-stu-id="29ba1-110">Usually, its value is 1, but a single IL instruction can map to multiple `CALL` assembly instructions.</span></span>  
  
 `pOffsets`  
 <span data-ttu-id="29ba1-111">네이티브 오프셋의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-111">An array of native offsets.</span></span> <span data-ttu-id="29ba1-112">일반적으로에는 단일 `pOffsets` 오프셋이 포함 되지만 단일 IL 명령은 여러 어셈블리 명령에 매핑할 수 있습니다 `CALL` .</span><span class="sxs-lookup"><span data-stu-id="29ba1-112">Typically, `pOffsets` contains a single offset, although a single IL instruction can map to multiple map to multiple `CALL` assembly instructions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ba1-113">설명</span><span class="sxs-lookup"><span data-stu-id="29ba1-113">Remarks</span></span>  

 <span data-ttu-id="29ba1-114">이 메서드는 [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) 메서드와 함께 사용 되어 참조 형식을 반환 하는 메서드의 반환 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-114">This method is used along with the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value of a method that returns a reference type.</span></span> <span data-ttu-id="29ba1-115">함수 호출 사이트에 대 한 IL 오프셋을이 메서드에 전달 하면 하나 이상의 네이티브 오프셋을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-115">Passing an IL offset to a function call site to this method returns one or more native offsets.</span></span> <span data-ttu-id="29ba1-116">그런 다음 디버거는 함수에서 이러한 네이티브 오프셋에 중단점을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-116">The debugger can then set breakpoints on these native offsets in the function.</span></span> <span data-ttu-id="29ba1-117">디버거가 중단점 중 하나에 적중 하면이 메서드에 전달 된 것과 동일한 IL 오프셋을 [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) 메서드에 전달 하 여 반환 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-117">When the debugger hits one of the breakpoints, you can then pass the same IL offset that you passed to this method to the [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) method to get the return value.</span></span> <span data-ttu-id="29ba1-118">그런 다음 디버거는 설정 된 모든 중단점을 지워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-118">The debugger should then clear all the breakpoints that it set.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="29ba1-119">`ICorDebugCode3::GetReturnValueLiveOffset`및 [ICorDebugILFrame3:: GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) 메서드를 사용 하 여 참조 형식에 대해서만 반환 값 정보를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-119">The `ICorDebugCode3::GetReturnValueLiveOffset` and [ICorDebugILFrame3::GetReturnValueForILOffset](icordebugilframe3-getreturnvalueforiloffset-method.md) methods allow you to get return value information for reference types only.</span></span> <span data-ttu-id="29ba1-120">값 형식에서 반환 값 정보를 검색 하는 경우 (즉,에서 파생 되는 모든 형식 <xref:System.ValueType> )은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-120">Retrieving return value information from value types (that is, all types that derive from <xref:System.ValueType>) is not supported.</span></span>  
  
 <span data-ttu-id="29ba1-121">함수는 `HRESULT` 다음 표에 나와 있는 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-121">The function returns the `HRESULT` values shown in the following table.</span></span>  
  
|<span data-ttu-id="29ba1-122">`HRESULT` 값</span><span class="sxs-lookup"><span data-stu-id="29ba1-122">`HRESULT` value</span></span>|<span data-ttu-id="29ba1-123">설명</span><span class="sxs-lookup"><span data-stu-id="29ba1-123">Description</span></span>|  
|---------------------|-----------------|  
|`S_OK`|<span data-ttu-id="29ba1-124">성공했습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-124">Success.</span></span>|  
|`CORDBG_E_INVALID_OPCODE`|<span data-ttu-id="29ba1-125">지정 된 IL 오프셋 사이트가 호출 명령이 아니거나 함수가를 반환 `void` 합니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-125">The given IL offset site is not a call instruction, or the function returns `void`.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="29ba1-126">지정 된 IL 오프셋은 적절 한 호출 이지만 반환 형식은 반환 값을 가져오는 데 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-126">The given IL offset is a proper call, but the return type is unsupported for getting a return value.</span></span>|  
  
 <span data-ttu-id="29ba1-127">`ICorDebugCode3::GetReturnValueLiveOffset`메서드는 x86 기반 및 AMD64 시스템 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="29ba1-127">The `ICorDebugCode3::GetReturnValueLiveOffset` method is available only on x86-based and AMD64 systems.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ba1-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="29ba1-128">Requirements</span></span>  

 <span data-ttu-id="29ba1-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="29ba1-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ba1-130">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29ba1-130">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29ba1-131">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29ba1-131">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ba1-132">**.NET Framework 버전:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ba1-132">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ba1-133">참조</span><span class="sxs-lookup"><span data-stu-id="29ba1-133">See also</span></span>

- [<span data-ttu-id="29ba1-134">GetReturnValueForILOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="29ba1-134">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)
- [<span data-ttu-id="29ba1-135">ICorDebugCode3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="29ba1-135">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
