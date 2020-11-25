---
title: ICorProfilerInfo2::GetClassLayout 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
ms.openlocfilehash: a2bac05e7471a0df8d624bf5dfbe2aa58c25cf4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727174"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="dba80-102">ICorProfilerInfo2::GetClassLayout 메서드</span><span class="sxs-lookup"><span data-stu-id="dba80-102">ICorProfilerInfo2::GetClassLayout Method</span></span>

<span data-ttu-id="dba80-103">지정된 클래스에서 정의된 필드의 레이아웃(메모리)에 대한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="dba80-104">즉, 이 메서드는 클래스의 필드 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba80-105">구문</span><span class="sxs-lookup"><span data-stu-id="dba80-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dba80-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dba80-106">Parameters</span></span>  

 `classID`  
 <span data-ttu-id="dba80-107">[in] 레이아웃이 검색되는 클래스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="dba80-108">[in, out] 각각 클래스 필드의 토큰과 오프셋을 포함 하는 [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) 구조체의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-108">[in, out] An array of [COR_FIELD_OFFSET](../metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="dba80-109">[in] `rFieldOffset` 배열의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="dba80-110">[out] 사용 가능한 요소의 총수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="dba80-111">`cFieldOffset`이 0인 경우 이 값은 필요한 요소 수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="dba80-112">[out] 클래스의 크기(바이트)를 포함하는 위치에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dba80-113">설명</span><span class="sxs-lookup"><span data-stu-id="dba80-113">Remarks</span></span>  

 <span data-ttu-id="dba80-114">`GetClassLayout` 메서드는 클래스 자체에서 정의된 필드만 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="dba80-115">클래스의 부모 클래스에도 정의된 필드가 있는 경우 프로파일러가 부모 클래스에 대해 `GetClassLayout`을 호출하여 해당 필드를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="dba80-116">문자열 클래스와 함께 `GetClassLayout`을 사용하는 경우 메서드가 E_INVALIDARG 오류 코드로 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="dba80-117">[ICorProfilerInfo2:: GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) 을 사용 하 여 문자열의 레이아웃에 대 한 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-117">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="dba80-118">배열 클래스를 사용하여 호출된 경우 `GetClassLayout`도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="dba80-119">`GetClassLayout`이 반환된 후 `rFieldOffset` 버퍼가 사용 가능한 모든 `COR_FIELD_OFFSET` 구조체를 포함하기에 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="dba80-120">이렇게 하려면 `pcFieldOffset`이 가리키는 값을 `rFieldOffset`의 크기를 `COR_FIELD_OFFSET` 구조체의 크기로 나눈 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="dba80-121">`rFieldOffset`이 충분히 크지 않은 경우 더 큰 `rFieldOffset` 버퍼를 할당하고 `cFieldOffset`을 더 큰 새 크기로 업데이트한 후 `GetClassLayout`을 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="dba80-122">또는 길이가 0인 `rFieldOffset` 버퍼로 `GetClassLayout`를 먼저 호출하여 올바른 버퍼 크기를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="dba80-123">그런 다음 버퍼 크기를 `pcFieldOffset`에 반환된 값으로 설정하고 `GetClassLayout`을 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="dba80-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba80-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dba80-124">Requirements</span></span>  

 <span data-ttu-id="dba80-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dba80-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba80-126">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dba80-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dba80-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba80-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba80-128">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba80-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba80-129">참조</span><span class="sxs-lookup"><span data-stu-id="dba80-129">See also</span></span>

- [<span data-ttu-id="dba80-130">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dba80-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="dba80-131">ICorProfilerInfo2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dba80-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="dba80-132">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="dba80-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="dba80-133">프로파일링</span><span class="sxs-lookup"><span data-stu-id="dba80-133">Profiling</span></span>](index.md)
