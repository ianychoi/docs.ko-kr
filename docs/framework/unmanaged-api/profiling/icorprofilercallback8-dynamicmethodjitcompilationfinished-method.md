---
description: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished 메서드에 대해 자세히 알아보세요.
title: ICorProfilerCallback8::D ynamicMethodJITCompilationFinished 메서드
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: d076307b9e57c27753297cad8eebc1b9aa9433f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781716"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a><span data-ttu-id="e5414-103">ICorProfilerCallback8::D ynamicMethodJITCompilationFinished 메서드</span><span class="sxs-lookup"><span data-stu-id="e5414-103">ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method</span></span>

<span data-ttu-id="e5414-104">[.NET Framework 4.7 이상 버전에서 지원 됨]</span><span class="sxs-lookup"><span data-stu-id="e5414-104">[Supported in the .NET Framework 4.7 and later versions]</span></span>  
  
<span data-ttu-id="e5414-105">동적 메서드의 JIT 컴파일이 완료 될 때마다 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-105">Notifies the profiler whenever JIT compilation of a dynamic method has completed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5414-106">구문</span><span class="sxs-lookup"><span data-stu-id="e5414-106">Syntax</span></span>  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5414-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e5414-107">Parameters</span></span>  

<span data-ttu-id="e5414-108">[in] `functionId`</span><span class="sxs-lookup"><span data-stu-id="e5414-108">[in] `functionId`</span></span>  
<span data-ttu-id="e5414-109">JIT 컴파일이 시작 되는 메모리 내 함수의 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-109">The identifier of the in-memory function for which JIT compilation is started.</span></span>

<span data-ttu-id="e5414-110">[in] `hrStatus` JIT 컴파일에 성공 했는지 여부를 나타내는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-110">[in] `hrStatus` A value that indicates whether the JIT compilation was successful.</span></span>

<span data-ttu-id="e5414-111">[in] `fIsSafeToBlock` 
 `true` 차단으로 인해 런타임에서 호출 스레드가이 콜백에서 반환 될 때까지 대기 하 게 될 수 있음을 나타내려면이 고, `false`를 지정 하면 차단이 런타임 작업에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-111">[in] `fIsSafeToBlock`
`true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span>  

## <a name="remarks"></a><span data-ttu-id="e5414-112">설명</span><span class="sxs-lookup"><span data-stu-id="e5414-112">Remarks</span></span>  

<span data-ttu-id="e5414-113">이 콜백은 동적 메서드의 JIT 컴파일이 완료 될 때마다 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-113">This callback is triggered whenever JIT compilation of a dynamic method has finished.</span></span> <span data-ttu-id="e5414-114">여기에는 다양 한 IL 스텁 및 LCG 메서드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-114">This includes various IL stubs and LCG methods.</span></span> <span data-ttu-id="e5414-115">이는 사용자에 게 컴파일된 메서드를 식별 하는 데 충분 한 정보를 제공 하는 프로파일러 작성기를 제공 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-115">Its goal is to provide profiler writers with enough information to identify the compiled method to users.</span></span>

> [!NOTE]
> <span data-ttu-id="e5414-116">`functionId` 동적 메서드에 메타 데이터가 없으므로 값을 사용 하 여 메타 데이터 토큰을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e5414-116">`functionId` values cannot be used to resolve to their metadata tokens, because dynamic methods have no metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="e5414-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e5414-117">Requirements</span></span>  

 <span data-ttu-id="e5414-118">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e5414-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5414-119">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e5414-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e5414-120">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5414-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5414-121">**.NET Framework 버전:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e5414-121">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5414-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e5414-122">See also</span></span>

- [<span data-ttu-id="e5414-123">DynamicMethodJITCompilationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="e5414-123">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="e5414-124">ICorProfilerCallback8 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e5414-124">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback8-interface.md)
