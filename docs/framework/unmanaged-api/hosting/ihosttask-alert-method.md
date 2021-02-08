---
description: '자세한 정보: IHostTask:: Alert 메서드'
title: IHostTask::Alert 메서드
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
ms.openlocfilehash: 378552db882aada0b6d0f531a871f2deb02132d0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784712"
---
# <a name="ihosttaskalert-method"></a><span data-ttu-id="1d94a-103">IHostTask::Alert 메서드</span><span class="sxs-lookup"><span data-stu-id="1d94a-103">IHostTask::Alert Method</span></span>

<span data-ttu-id="1d94a-104">호스트가 현재 [IHostTask](ihosttask-interface.md) 인스턴스로 표시 되는 작업의 절전 모드를 해제 하도록 요청 하므로 작업이 중단 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-104">Requests that the host wake the task represented by the current [IHostTask](ihosttask-interface.md) instance, so the task can be aborted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d94a-105">구문</span><span class="sxs-lookup"><span data-stu-id="1d94a-105">Syntax</span></span>  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1d94a-106">Return Value</span><span class="sxs-lookup"><span data-stu-id="1d94a-106">Return Value</span></span>  
  
|<span data-ttu-id="1d94a-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d94a-107">HRESULT</span></span>|<span data-ttu-id="1d94a-108">설명</span><span class="sxs-lookup"><span data-stu-id="1d94a-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d94a-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d94a-109">S_OK</span></span>|<span data-ttu-id="1d94a-110">메서드가 성공적으로 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-110">The method returned successfully.</span></span>|  
|<span data-ttu-id="1d94a-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d94a-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d94a-112">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d94a-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d94a-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d94a-114">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-114">The call timed out.</span></span>|  
|<span data-ttu-id="1d94a-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d94a-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d94a-116">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d94a-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d94a-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d94a-118">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d94a-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d94a-119">E_FAIL</span></span>|<span data-ttu-id="1d94a-120">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d94a-121">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d94a-122">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d94a-123">설명</span><span class="sxs-lookup"><span data-stu-id="1d94a-123">Remarks</span></span>  

 <span data-ttu-id="1d94a-124">CLR은 `Alert` <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 사용자 코드에서가 호출 될 때 또는 현재와 연결 된가 종료 될 때 메서드를 호출 합니다 <xref:System.AppDomain> <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="1d94a-124">The CLR calls the `Alert` method when <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> is called from user code, or when the <xref:System.AppDomain> associated with the current <xref:System.Threading.Thread> shuts down.</span></span> <span data-ttu-id="1d94a-125">호출이 비동기적으로 수행 되므로 호스트는를 즉시 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-125">The host must return immediately, because the call is made asynchronously.</span></span> <span data-ttu-id="1d94a-126">호스트가 작업을 즉시 경고할 수 없는 경우 다음에 경고가 표시 될 수 있는 상태로 전환 될 때 절전 모드를 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-126">If the host cannot alert the task immediately, it must wake up the next time it enters a state in which it can be alerted.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d94a-127">`Alert` 런타임이 WAIT_ALERTABLE의 [WAIT_OPTION](wait-option-enumeration.md) 값을 [Join](ihosttask-join-method.md)과 같은 메서드에 전달 하는 작업에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-127">`Alert` affects only those tasks to which the runtime has passed a [WAIT_OPTION](wait-option-enumeration.md) value of WAIT_ALERTABLE to methods such as [Join](ihosttask-join-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d94a-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1d94a-128">Requirements</span></span>  

 <span data-ttu-id="1d94a-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d94a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d94a-130">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="1d94a-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d94a-131">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d94a-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d94a-132">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d94a-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d94a-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d94a-133">See also</span></span>

- [<span data-ttu-id="1d94a-134">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d94a-134">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="1d94a-135">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d94a-135">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="1d94a-136">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d94a-136">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="1d94a-137">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d94a-137">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
