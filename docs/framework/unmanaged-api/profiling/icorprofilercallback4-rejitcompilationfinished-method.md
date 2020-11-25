---
title: ICorProfilerCallback4::ReJITCompilationFinished 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITCompilationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished
helpviewer_keywords:
- ICorProfilerCallback4::ReJITCompilationFinished method [.NET Framework profiling]
- ReJITCompilationFinished method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 3b5cff02-2005-44eb-a2bc-50214c4b0e1d
topic_type:
- apiref
ms.openlocfilehash: a6c2209433a652523fd8e3a7cc2db1272600e1bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730268"
---
# <a name="icorprofilercallback4rejitcompilationfinished-method"></a><span data-ttu-id="4a9d7-102">ICorProfilerCallback4::ReJITCompilationFinished 메서드</span><span class="sxs-lookup"><span data-stu-id="4a9d7-102">ICorProfilerCallback4::ReJITCompilationFinished Method</span></span>

<span data-ttu-id="4a9d7-103">JIT (just-in-time) 컴파일러가 함수를 다시 컴파일 했음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-103">Notifies the profiler that the just-in-time (JIT) compiler has finished recompiling a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a9d7-104">구문</span><span class="sxs-lookup"><span data-stu-id="4a9d7-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITCompilationFinished(  
    [in] FunctionID functionId,    [in] ReJITID rejitId,  
    [in] HRESULT    hrStatus,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a9d7-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="4a9d7-105">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="4a9d7-106">진행 다시 컴파일된 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-106">[in] The ID of the function that was recompiled.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="4a9d7-107">[in] JIT 다시 컴파일된 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="4a9d7-108">진행 JIT 다시 컴파일 성공 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-108">[in] A value that indicates whether the JIT recompilation was successful.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="4a9d7-109">[in] `true` 차단으로 인해 런타임에서 호출 스레드가이 콜백에서 반환 될 때까지 대기 하 게 될 수 있음을 나타내려면이 고, `false` 를 지정 하면 차단이 런타임 작업에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-109">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  
  
 <span data-ttu-id="4a9d7-110">값은 `true` 런타임에 영향을 주지 않지만 프로 파일링 결과에 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-110">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a9d7-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="4a9d7-111">Requirements</span></span>  

 <span data-ttu-id="4a9d7-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4a9d7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a9d7-113">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a9d7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a9d7-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a9d7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a9d7-115">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a9d7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a9d7-116">참조</span><span class="sxs-lookup"><span data-stu-id="4a9d7-116">See also</span></span>

- [<span data-ttu-id="4a9d7-117">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4a9d7-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="4a9d7-118">ICorProfilerCallback4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="4a9d7-118">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
- [<span data-ttu-id="4a9d7-119">JITCompilationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="4a9d7-119">JITCompilationStarted Method</span></span>](icorprofilercallback-jitcompilationstarted-method.md)
- [<span data-ttu-id="4a9d7-120">ReJITCompilationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="4a9d7-120">ReJITCompilationStarted Method</span></span>](icorprofilercallback4-rejitcompilationstarted-method.md)
