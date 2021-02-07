---
description: '자세히 알아보기: ICorProfilerInfo3:: SetFunctionIDMapper2 메서드'
title: ICorProfilerInfo3::SetFunctionIDMapper2 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
ms.openlocfilehash: 4847d3bd7b8bf6142da0f32c3558016b2c758087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99686988"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a><span data-ttu-id="d6c18-103">ICorProfilerInfo3::SetFunctionIDMapper2 메서드</span><span class="sxs-lookup"><span data-stu-id="d6c18-103">ICorProfilerInfo3::SetFunctionIDMapper2 Method</span></span>

<span data-ttu-id="d6c18-104">`FunctionID` 값을 대체 값에 매핑하기 위해 호출되는 프로파일러 구현 함수를 지정합니다. 대체 값은 프로파일러의 함수 진입점/종료점 후크에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6c18-104">Specifies the profiler-implemented function that will be called to map `FunctionID` values to alternative values, which are passed to the profiler's function entry/exit hooks.</span></span> <span data-ttu-id="d6c18-105">이 메서드는 추가 데이터 매개 변수를 사용 하 여 [ICorProfilerInfo:: SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) 메서드를 확장 합니다 .이 메서드는 프로파일러를 사용 하 여 런타임을 명확 하 게 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6c18-105">This method extends the [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md) method with an additional data parameter, which profilers may use to disambiguate among runtimes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6c18-106">구문</span><span class="sxs-lookup"><span data-stu-id="d6c18-106">Syntax</span></span>  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6c18-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d6c18-107">Parameters</span></span>  

 `pFunc`  
 <span data-ttu-id="d6c18-108">진행 값을 대체 값에 매핑하기 위해 호출 되는 [FunctionIDMapper2](functionidmapper2-function.md) 구현에 대 한 포인터입니다 `FunctionID` .</span><span class="sxs-lookup"><span data-stu-id="d6c18-108">[in] A pointer to a [FunctionIDMapper2](functionidmapper2-function.md) implementation that will be called to map the `FunctionID` values to their alternative values.</span></span>  
  
 `clientData`  
 <span data-ttu-id="d6c18-109">진행 현재 런타임에서 만든 모든 [FunctionIDMapper2](functionidmapper2-function.md) 함수 호출에 전달 되는 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d6c18-109">[in] A pointer that is passed to every [FunctionIDMapper2](functionidmapper2-function.md) function call made by the current runtime.</span></span> <span data-ttu-id="d6c18-110">프로파일러는이 정보를 사용 하 여 런타임 중에 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6c18-110">The profiler can use this information to disambiguate among runtimes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6c18-111">Return Value</span><span class="sxs-lookup"><span data-stu-id="d6c18-111">Return Value</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6c18-112">설명</span><span class="sxs-lookup"><span data-stu-id="d6c18-112">Remarks</span></span>  

 <span data-ttu-id="d6c18-113">FunctionID 값의 대안은 [](functionenter3withinfo-function.md) [FunctionLeave3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) 또는 [FunctionTailcall3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) 메서드에서 지정 하는 프로파일러의 함수 진입/종료 후크 ([FunctionEnter3](functionenter3-function.md), [](functionleave3withinfo-function.md) [FunctionLeave3](functionleave3-function.md), and [SetEnterLeaveFunctionHooks3](functiontailcall3withinfo-function.md))에 전달 됩니다. [](functiontailcall3-function.md)</span><span class="sxs-lookup"><span data-stu-id="d6c18-113">The alternatives for the FunctionID values will be passed to the profiler's function entry/exit hooks ([FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md), and [FunctionTailcall3](functiontailcall3-function.md); or [FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)) that are specified by the [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) or [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) method.</span></span>  
  
 <span data-ttu-id="d6c18-114">`FunctionIDMapper2`메서드는 한 번만 설정할 수 있으며, [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) 콜백에서 설정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d6c18-114">The `FunctionIDMapper2` method can be set only once; we recommend that you set it in the [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6c18-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d6c18-115">Requirements</span></span>  

 <span data-ttu-id="d6c18-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6c18-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6c18-117">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6c18-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6c18-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6c18-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6c18-119">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6c18-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c18-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6c18-120">See also</span></span>

- [<span data-ttu-id="d6c18-121">SetFunctionIDMapper</span><span class="sxs-lookup"><span data-stu-id="d6c18-121">SetFunctionIDMapper</span></span>](icorprofilerinfo-setfunctionidmapper-method.md)
- [<span data-ttu-id="d6c18-122">ICorProfilerInfo3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6c18-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d6c18-123">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6c18-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d6c18-124">프로파일링</span><span class="sxs-lookup"><span data-stu-id="d6c18-124">Profiling</span></span>](index.md)
