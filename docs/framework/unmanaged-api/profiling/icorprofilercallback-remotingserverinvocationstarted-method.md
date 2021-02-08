---
description: '자세히 알아보기: ICorProfilerCallback:: RemotingServerInvocationStarted 메서드'
title: ICorProfilerCallback::RemotingServerInvocationStarted 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerInvocationStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerInvocationStarted
helpviewer_keywords:
- RemotingServerInvocationStarted method [.NET Framework profiling]
- ICorProfilerCallback::RemotingServerInvocationStarted method [.NET Framework profiling]
ms.assetid: 86051a11-ad8e-4ace-9a11-ff0f982a5e11
topic_type:
- apiref
ms.openlocfilehash: 8a27e3e545b9ff2812561f5faa7ebfe70d41f015
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788906"
---
# <a name="icorprofilercallbackremotingserverinvocationstarted-method"></a><span data-ttu-id="df959-103">ICorProfilerCallback::RemotingServerInvocationStarted 메서드</span><span class="sxs-lookup"><span data-stu-id="df959-103">ICorProfilerCallback::RemotingServerInvocationStarted Method</span></span>

<span data-ttu-id="df959-104">프로세스가 원격 메서드 호출 요청에 대 한 응답으로 메서드를 호출 하 고 있음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="df959-104">Notifies the profiler that the process is invoking a method in response to a remote method invocation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df959-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="df959-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingServerInvocationStarted();  
```  
  
## <a name="requirements"></a><span data-ttu-id="df959-106">요구 사항</span><span class="sxs-lookup"><span data-stu-id="df959-106">Requirements</span></span>  

 <span data-ttu-id="df959-107">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df959-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df959-108">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df959-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df959-109">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df959-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df959-110">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df959-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df959-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df959-111">See also</span></span>

- [<span data-ttu-id="df959-112">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="df959-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
