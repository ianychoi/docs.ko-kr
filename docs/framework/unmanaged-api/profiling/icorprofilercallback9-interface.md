---
description: '자세히 알아보기: ICorProfilerCallback9 인터페이스'
title: ICorProfilerCallback9 인터페이스
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4bfcaf6f8985909ef9142ef4d08535a19facd7e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781651"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="ea85b-103">ICorProfilerCallback9 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ea85b-103">ICorProfilerCallback9 Interface</span></span>

<span data-ttu-id="ea85b-104">[.NET Framework 4.7.2 이상 버전에서 지원 됨]</span><span class="sxs-lookup"><span data-stu-id="ea85b-104">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="ea85b-105">공용 언어 런타임에서 동적 메서드가 가비지 수집 되 고 이후에 언로드되는 것을 프로파일러에 알리는 데 사용 하는 콜백 메서드를 제공 하는 [ICorProfilerCallback8](icorprofilercallback8-interface.md) 의 서브 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="ea85b-105">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea85b-106">메서드</span><span class="sxs-lookup"><span data-stu-id="ea85b-106">Methods</span></span>  
  
|<span data-ttu-id="ea85b-107">메서드</span><span class="sxs-lookup"><span data-stu-id="ea85b-107">Method</span></span>|<span data-ttu-id="ea85b-108">설명</span><span class="sxs-lookup"><span data-stu-id="ea85b-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea85b-109">DynamicMethodUnloaded 메서드</span><span class="sxs-lookup"><span data-stu-id="ea85b-109">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="ea85b-110">동적 메서드가 가비지 수집 되 고 이후에 언로드되는 것을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="ea85b-110">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea85b-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ea85b-111">Requirements</span></span>  

 <span data-ttu-id="ea85b-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ea85b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea85b-113">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea85b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="ea85b-114">**.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea85b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ea85b-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ea85b-115">See also</span></span>

- [<span data-ttu-id="ea85b-116">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ea85b-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="ea85b-117">ICorProfilerCallback8 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ea85b-117">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="ea85b-118">ICorProfilerCallback8 DynamicMethodJITCompilationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="ea85b-118">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="ea85b-119">ICorProfilerCallback8 DynamicMethodJITCompilationFinished 메서드</span><span class="sxs-lookup"><span data-stu-id="ea85b-119">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
