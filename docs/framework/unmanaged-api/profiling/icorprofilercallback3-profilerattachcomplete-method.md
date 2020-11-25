---
title: ICorProfilerCallback3::ProfilerAttachComplete 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: a16e77619ec85ebdf47a2b821309bbb3af63282b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705321"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="21b4e-102">ICorProfilerCallback3::ProfilerAttachComplete 메서드</span><span class="sxs-lookup"><span data-stu-id="21b4e-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>

<span data-ttu-id="21b4e-103">프로파일러가 [ICorProfilerInfo3:: EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) 및 [ICorProfilerInfo3:: enummodules](icorprofilerinfo3-enummodules-method.md) catch 메서드를 호출할 수 있음을 나타내기 위해 CLR (공용 언어 런타임)에 의해 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21b4e-104">구문</span><span class="sxs-lookup"><span data-stu-id="21b4e-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="21b4e-105">설명</span><span class="sxs-lookup"><span data-stu-id="21b4e-105">Remarks</span></span>  

 <span data-ttu-id="21b4e-106">`ProfilerAttachComplete`콜백은 [ICorProfilerCallback3:: InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) 메서드가 호출 된 후에 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="21b4e-107">다음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="21b4e-108">`InitializeForAttach`에서 프로파일러가 요청한 콜백이 활성화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="21b4e-109">이제 프로파일러가 누락된 알림에 대해 염려하지 않고 연결된 ID에서 후속 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="21b4e-110">CLR은 이 콜백의 반환 값을 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="21b4e-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21b4e-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="21b4e-111">Requirements</span></span>  

 <span data-ttu-id="21b4e-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21b4e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21b4e-113">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="21b4e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="21b4e-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21b4e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21b4e-115">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21b4e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21b4e-116">참조</span><span class="sxs-lookup"><span data-stu-id="21b4e-116">See also</span></span>

- [<span data-ttu-id="21b4e-117">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="21b4e-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="21b4e-118">ICorProfilerInfo3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="21b4e-118">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="21b4e-119">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="21b4e-119">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="21b4e-120">프로파일링</span><span class="sxs-lookup"><span data-stu-id="21b4e-120">Profiling</span></span>](index.md)
