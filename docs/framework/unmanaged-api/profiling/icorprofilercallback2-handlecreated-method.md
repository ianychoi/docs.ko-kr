---
description: '자세히 알아보기: ICorProfilerCallback2:: HandleCreated 메서드'
title: ICorProfilerCallback2::HandleCreated 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.HandleCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::HandleCreated
helpviewer_keywords:
- HandleCreated method [.NET Framework profiling]
- ICorProfilerCallback2::HandleCreated method [.NET Framework profiling]
ms.assetid: 6bbb7786-7c38-490f-9834-91aa2795c355
topic_type:
- apiref
ms.openlocfilehash: 17f4ed83646907a229dcc6a30dcce1b52fa608d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657088"
---
# <a name="icorprofilercallback2handlecreated-method"></a><span data-ttu-id="752d0-103">ICorProfilerCallback2::HandleCreated 메서드</span><span class="sxs-lookup"><span data-stu-id="752d0-103">ICorProfilerCallback2::HandleCreated Method</span></span>

<span data-ttu-id="752d0-104">가비지 수집 핸들이 생성 되었음을 코드 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="752d0-104">Notifies the code profiler that a garbage collection handle has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="752d0-105">구문</span><span class="sxs-lookup"><span data-stu-id="752d0-105">Syntax</span></span>  
  
```cpp  
HRESULT HandleCreated(  
    [in] GCHandleID handleId,  
    [in] ObjectID initialObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="752d0-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="752d0-106">Parameters</span></span>  

 `handleId`  
 <span data-ttu-id="752d0-107">진행 가비지 컬렉션에 대 한 핸들의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="752d0-107">[in] The ID of the handle for the garbage collection.</span></span>  
  
 `initialObjectId`  
 <span data-ttu-id="752d0-108">진행 가비지 수집 핸들을 만든 개체의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="752d0-108">[in] The ID of the object for which the garbage collection handle was created.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="752d0-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="752d0-109">Requirements</span></span>  

 <span data-ttu-id="752d0-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="752d0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="752d0-111">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="752d0-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="752d0-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="752d0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="752d0-113">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="752d0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752d0-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="752d0-114">See also</span></span>

- [<span data-ttu-id="752d0-115">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="752d0-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="752d0-116">ICorProfilerCallback2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="752d0-116">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
