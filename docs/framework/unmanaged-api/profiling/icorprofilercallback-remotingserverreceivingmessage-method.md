---
description: '자세히 알아보기: ICorProfilerCallback:: RemotingServerReceivingMessage 메서드'
title: ICorProfilerCallback::RemotingServerReceivingMessage 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingServerReceivingMessage
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage
helpviewer_keywords:
- ICorProfilerCallback::RemotingServerReceivingMessage method [.NET Framework profiling]
- RemotingServerReceivingMessage method [.NET Framework profiling]
ms.assetid: 5604d21f-e6b7-490e-b469-42122a7568e1
topic_type:
- apiref
ms.openlocfilehash: 5efa706d934158d09796dfab40b132a334c10ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788893"
---
# <a name="icorprofilercallbackremotingserverreceivingmessage-method"></a><span data-ttu-id="f6613-103">ICorProfilerCallback::RemotingServerReceivingMessage 메서드</span><span class="sxs-lookup"><span data-stu-id="f6613-103">ICorProfilerCallback::RemotingServerReceivingMessage Method</span></span>

<span data-ttu-id="f6613-104">프로세스에서 원격 메서드 호출 또는 활성화 요청을 받았음을 프로파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-104">Notifies the profiler that the process has received a remote method invocation or activation request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6613-105">구문</span><span class="sxs-lookup"><span data-stu-id="f6613-105">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6613-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f6613-106">Parameters</span></span>  

 `pCookie`  
 <span data-ttu-id="f6613-107">진행 다음 조건에서 [ICorProfilerCallback:: Remo Clientsendingmessage](icorprofilercallback-remotingclientsendingmessage-method.md) 에 제공 된 값에 해당 하는 값입니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-107">[in] A value that will correspond with the value provided in [ICorProfilerCallback::RemotingClientSendingMessage](icorprofilercallback-remotingclientsendingmessage-method.md) under these conditions:</span></span>  
  
- <span data-ttu-id="f6613-108">원격 GUID 쿠키가 활성 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-108">Remoting GUID cookies are active.</span></span>  
  
- <span data-ttu-id="f6613-109">채널에서 메시지를 전송 하는 데 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-109">The channel succeeds in transmitting the message.</span></span>  
  
- <span data-ttu-id="f6613-110">GUID 쿠키는 클라이언트 쪽 프로세스에서 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-110">GUID cookies are active on the client-side process.</span></span>  
  
 <span data-ttu-id="f6613-111">이렇게 하면 원격 호출을 쉽게 페어링 하 고 논리 호출 스택을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-111">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="f6613-112">진행 `true` 호출이 비동기 이면이 고, 그렇지 않으면 인 값입니다 `false` .</span><span class="sxs-lookup"><span data-stu-id="f6613-112">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6613-113">설명</span><span class="sxs-lookup"><span data-stu-id="f6613-113">Remarks</span></span>  

 <span data-ttu-id="f6613-114">메시지 요청이 비동기 인 경우 임의의 스레드에서 요청을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6613-114">If the message request is asynchronous, the request can be serviced by any arbitrary thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6613-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f6613-115">Requirements</span></span>  

 <span data-ttu-id="f6613-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f6613-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6613-117">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f6613-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6613-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6613-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6613-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6613-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6613-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6613-120">See also</span></span>

- [<span data-ttu-id="f6613-121">ICorProfilerCallback 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f6613-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
