---
title: ICorProfilerInfo4::GetILToNativeMapping2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
ms.openlocfilehash: 37d6b6d5112089df18fb138086db5e138a69629c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697755"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="d89d2-102">ICorProfilerInfo4::GetILToNativeMapping2 메서드</span><span class="sxs-lookup"><span data-stu-id="d89d2-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>

<span data-ttu-id="d89d2-103">지정된 함수의 JIT 다시 컴파일된 버전에 포함된 코드에 대한 MSIL(Microsoft Intermediate Language) 오프셋과 네이티브 오프셋 간의 맵을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89d2-104">구문</span><span class="sxs-lookup"><span data-stu-id="d89d2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d89d2-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d89d2-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="d89d2-106">[in] 코드를 포함하는 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="d89d2-107">[in] JIT 다시 컴파일된 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="d89d2-108">Id는 .NET Framework 4.5에서 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="d89d2-109">[in] `map` 배열의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="d89d2-110">[out] 사용 가능한 COR_DEBUG_IL_TO_NATIVE_MAP 구조체의 총수입니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="d89d2-111">[out] 각각 오프셋을 지정하는 `COR_DEBUG_IL_TO_NATIVE_MAP` 구조체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="d89d2-112">`GetILToNativeMapping2` 메서드가 반환되면 `map`에 `COR_DEBUG_IL_TO_NATIVE_MAP` 구조체가 일부 또는 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d89d2-113">설명</span><span class="sxs-lookup"><span data-stu-id="d89d2-113">Remarks</span></span>  

 <span data-ttu-id="d89d2-114">`GetILToNativeMapping2` 는 [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) 메서드와 유사 합니다. 단, 프로파일러는 이후 릴리스에서 다시 컴파일된 함수의 ID를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d89d2-115">[ICorProfilerFunctionControl:: SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) 메서드는 .NET Framework 4.5에서 구현 되지 않으므로 JIT 다시 컴파일된 함수는 원래 컴파일된 함수와 다른 IL-네이티브 매핑을 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="d89d2-116">따라서 `GetILToNativeMapping2` .NET Framework 4.5에서 0이 아닌 JIT 다시 컴파일된 ID를 사용 하 여를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="d89d2-117">`GetILToNativeMapping2` 메서드는 `COR_DEBUG_IL_TO_NATIVE_MAP` 구조체의 배열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d89d2-118">특정 범위의 네이티브 지침이 프롤로그와 같은 특정 코드 영역에 해당 하는 것을 전달 하기 위해 배열의 항목은 해당 `ilOffset` 필드를 [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) 열거형의 값으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="d89d2-119">`GetILToNativeMapping2`가 반환된 후 `map` 버퍼가 모든 `COR_DEBUG_IL_TO_NATIVE_MAP` 구조체를 포함하기에 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="d89d2-120">이렇게 하려면 `cMap` 값을 `pcMap` 매개 변수의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="d89d2-121">`COR_DEBUG_IL_TO_NATIVE_MAP` 구조체의 크기를 곱한 `pcMap` 값이 `cMap`보다 크면 더 큰 `map` 버퍼를 할당하고 `cMap`를 더 큰 새 크기로 업데이트한 다음 `GetILToNativeMapping2`를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="d89d2-122">또는 길이가 0인 `map` 버퍼로 `GetILToNativeMapping2`를 먼저 호출하여 올바른 버퍼 크기를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="d89d2-123">그런 다음 버퍼 크기를 `pcMap`에 반환된 값으로 설정하고 `GetILToNativeMapping2`을 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d89d2-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89d2-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d89d2-124">Requirements</span></span>  

 <span data-ttu-id="d89d2-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d89d2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89d2-126">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d89d2-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d89d2-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d89d2-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d89d2-128">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89d2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89d2-129">참조</span><span class="sxs-lookup"><span data-stu-id="d89d2-129">See also</span></span>

- [<span data-ttu-id="d89d2-130">GetILToNativeMapping 메서드</span><span class="sxs-lookup"><span data-stu-id="d89d2-130">GetILToNativeMapping Method</span></span>](icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="d89d2-131">ICorProfilerInfo4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d89d2-131">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="d89d2-132">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d89d2-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d89d2-133">프로파일링</span><span class="sxs-lookup"><span data-stu-id="d89d2-133">Profiling</span></span>](index.md)
