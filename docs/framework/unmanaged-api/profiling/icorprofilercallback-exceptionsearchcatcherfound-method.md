---
title: ICorProfilerCallback::ExceptionSearchCatcherFound 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: ef25d55defee2fdcfc7d744e481060eb7a7782ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699887"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="e0f19-102">ICorProfilerCallback::ExceptionSearchCatcherFound 메서드</span><span class="sxs-lookup"><span data-stu-id="e0f19-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="e0f19-103">예외 처리의 검색 단계에서 throw 된 예외에 대 한 처리기를 찾을 때 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="e0f19-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0f19-104">구문</span><span class="sxs-lookup"><span data-stu-id="e0f19-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0f19-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e0f19-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="e0f19-106">\[in] 예외 처리기를 포함 하는 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="e0f19-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0f19-107">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e0f19-107">Requirements</span></span>  

 <span data-ttu-id="e0f19-108">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e0f19-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0f19-109">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0f19-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0f19-110">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0f19-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0f19-111">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0f19-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f19-112">참조</span><span class="sxs-lookup"><span data-stu-id="e0f19-112">See also</span></span>

- [<span data-ttu-id="e0f19-113">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e0f19-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
