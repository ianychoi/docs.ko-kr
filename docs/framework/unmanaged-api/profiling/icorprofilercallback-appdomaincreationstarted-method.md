---
title: ICorProfilerCallback::AppDomainCreationStarted 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationStarted
helpviewer_keywords:
- AppDomainCreationStarted method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationStarted method [.NET Framework profiling]
ms.assetid: b2a8240b-07fe-4859-bb2b-7d3adbfa0a9f
topic_type:
- apiref
ms.openlocfilehash: 901546c80c3bee32afddfa8e8cffbd2b679bc43b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685398"
---
# <a name="icorprofilercallbackappdomaincreationstarted-method"></a><span data-ttu-id="2c396-102">ICorProfilerCallback::AppDomainCreationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="2c396-102">ICorProfilerCallback::AppDomainCreationStarted Method</span></span>

<span data-ttu-id="2c396-103">응용 프로그램 도메인이 생성 중임을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="2c396-103">Notifies the profiler that an application domain is being created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c396-104">구문</span><span class="sxs-lookup"><span data-stu-id="2c396-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationStarted(  
    [in] AppDomainID appDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c396-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2c396-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="2c396-106">\[in] 생성 되는 도메인을 식별 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c396-106">\[in] Identifies the domain which is being created.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="2c396-107">설명</span><span class="sxs-lookup"><span data-stu-id="2c396-107">Remarks</span></span>  

 <span data-ttu-id="2c396-108">[ICorProfilerCallback:: AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) 메서드가 호출 될 때까지 정보 요청에 대해 ID가 유효 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c396-108">The ID is not valid for any information request until the [ICorProfilerCallback::AppDomainCreationFinished](icorprofilercallback-appdomaincreationfinished-method.md) method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c396-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2c396-109">Requirements</span></span>  

 <span data-ttu-id="2c396-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c396-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c396-111">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c396-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c396-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c396-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c396-113">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c396-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c396-114">참조</span><span class="sxs-lookup"><span data-stu-id="2c396-114">See also</span></span>

- [<span data-ttu-id="2c396-115">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2c396-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
