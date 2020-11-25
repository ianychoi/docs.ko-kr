---
title: ICorProfilerCallback::RuntimeSuspendStarted 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: b778088f53a3c49def95d715f5fefcb26af81489
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731984"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a><span data-ttu-id="e7d71-102">ICorProfilerCallback::RuntimeSuspendStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="e7d71-102">ICorProfilerCallback::RuntimeSuspendStarted Method</span></span>

<span data-ttu-id="e7d71-103">런타임이 모든 런타임 스레드를 일시 중단 함을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-103">Notifies the profiler that the runtime is about to suspend all runtime threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7d71-104">구문</span><span class="sxs-lookup"><span data-stu-id="e7d71-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7d71-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e7d71-105">Parameters</span></span>  

 `suspendReason`  
 <span data-ttu-id="e7d71-106">진행 일시 중단 이유를 나타내는 [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-106">[in] A value of the [COR_PRF_SUSPEND_REASON](cor-prf-suspend-reason-enumeration.md) enumeration that indicates the reason for the suspension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e7d71-107">설명</span><span class="sxs-lookup"><span data-stu-id="e7d71-107">Remarks</span></span>  

 <span data-ttu-id="e7d71-108">비관리 코드에 있는 모든 런타임 스레드는 런타임을 다시 시작 하려고 할 때까지 계속 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-108">All runtime threads that are in unmanaged code are allowed to continue running until they try to re-enter the runtime.</span></span> <span data-ttu-id="e7d71-109">이 시점에서 런타임이 재개 될 때까지 일시 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-109">At that point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="e7d71-110">이는 런타임에 입력 하는 새 스레드에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-110">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="e7d71-111">런타임의 모든 스레드는 이미 인터럽트 가능 코드에 있는 경우 즉시 일시 중단 되거나, 인터럽트가 가능한 코드에 도달할 때 일시 중단 하 라는 메시지가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7d71-111">All threads in the runtime are either suspended immediately if they are already in interruptible code, or they are asked to suspend when they reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7d71-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e7d71-112">Requirements</span></span>  

 <span data-ttu-id="e7d71-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e7d71-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7d71-114">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e7d71-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7d71-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e7d71-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7d71-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7d71-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7d71-117">참조</span><span class="sxs-lookup"><span data-stu-id="e7d71-117">See also</span></span>

- [<span data-ttu-id="e7d71-118">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e7d71-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e7d71-119">RuntimeSuspendAborted 메서드</span><span class="sxs-lookup"><span data-stu-id="e7d71-119">RuntimeSuspendAborted Method</span></span>](icorprofilercallback-runtimesuspendaborted-method.md)
- [<span data-ttu-id="e7d71-120">RuntimeSuspendFinished 메서드</span><span class="sxs-lookup"><span data-stu-id="e7d71-120">RuntimeSuspendFinished Method</span></span>](icorprofilercallback-runtimesuspendfinished-method.md)
