---
description: '자세히 알아보기: ICorProfilerCallback:: ExceptionSearchFilterLeave 메서드'
title: ICorProfilerCallback::ExceptionSearchFilterLeave 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: d2195e8e055b25f71efbfbcc71e933daa07a4e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799124"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="27a90-103">ICorProfilerCallback::ExceptionSearchFilterLeave 메서드</span><span class="sxs-lookup"><span data-stu-id="27a90-103">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>

<span data-ttu-id="27a90-104">사용자 필터의 실행이 완료 되었음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="27a90-104">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27a90-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="27a90-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="27a90-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="27a90-106">Requirements</span></span>  

 <span data-ttu-id="27a90-107">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="27a90-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a90-108">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="27a90-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="27a90-109">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27a90-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27a90-110">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a90-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a90-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="27a90-111">See also</span></span>

- [<span data-ttu-id="27a90-112">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="27a90-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="27a90-113">ExceptionSearchFilterEnter 메서드</span><span class="sxs-lookup"><span data-stu-id="27a90-113">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
