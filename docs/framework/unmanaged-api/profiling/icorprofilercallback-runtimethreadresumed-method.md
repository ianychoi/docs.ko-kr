---
title: ICorProfilerCallback::RuntimeThreadResumed 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
ms.openlocfilehash: 0996d7eb5b7354a67106ec7aa8818d5e4d46232e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717269"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="1ece0-102">ICorProfilerCallback::RuntimeThreadResumed 메서드</span><span class="sxs-lookup"><span data-stu-id="1ece0-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>

<span data-ttu-id="1ece0-103">지정 된 스레드가 일시 중단 된 후 다시 시작 되었음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="1ece0-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ece0-104">구문</span><span class="sxs-lookup"><span data-stu-id="1ece0-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ece0-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1ece0-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="1ece0-106">진행 다시 시작 된 스레드의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="1ece0-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ece0-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1ece0-107">Requirements</span></span>  

 <span data-ttu-id="1ece0-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ece0-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ece0-109">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1ece0-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ece0-110">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ece0-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ece0-111">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ece0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ece0-112">참조</span><span class="sxs-lookup"><span data-stu-id="1ece0-112">See also</span></span>

- [<span data-ttu-id="1ece0-113">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1ece0-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1ece0-114">RuntimeThreadSuspended 메서드</span><span class="sxs-lookup"><span data-stu-id="1ece0-114">RuntimeThreadSuspended Method</span></span>](icorprofilercallback-runtimethreadsuspended-method.md)
