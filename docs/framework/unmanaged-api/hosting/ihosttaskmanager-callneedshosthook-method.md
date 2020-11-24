---
title: IHostTaskManager::CallNeedsHostHook 메서드
ms.date: 03/30/2017
api_name:
- IHostTaskManager.CallNeedsHostHook
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::CallNeedsHostHook
helpviewer_keywords:
- CallNeedsHostHook method [.NET Framework hosting]
- IHostTaskManager::CallNeedsHostHook method [.NET Framework hosting]
ms.assetid: b60f1f59-9825-4b57-961f-d2979518e6a7
topic_type:
- apiref
ms.openlocfilehash: 7c7af1bbf3d13c3f66d525dfce69d8b49fbe045c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675141"
---
# <a name="ihosttaskmanagercallneedshosthook-method"></a><span data-ttu-id="d7112-102">IHostTaskManager::CallNeedsHostHook 메서드</span><span class="sxs-lookup"><span data-stu-id="d7112-102">IHostTaskManager::CallNeedsHostHook Method</span></span>

<span data-ttu-id="d7112-103">호스트에서 CLR (공용 언어 런타임)이 관리 되지 않는 함수에 대 한 지정 된 호출을 인라인 할 수 있는지 여부를 지정할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-103">Enables the host to specify whether the common language runtime (CLR) can inline the specified call to an unmanaged function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7112-104">구문</span><span class="sxs-lookup"><span data-stu-id="d7112-104">Syntax</span></span>  
  
```cpp  
HRESULT CallNeedsHostHook (  
    [in]  SIZE_T target,
    [out] BOOL   *pbCallNeedsHostHook  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7112-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d7112-105">Parameters</span></span>  

 `target`  
 <span data-ttu-id="d7112-106">진행 호출 될 관리 되지 않는 함수의 매핑된 PE (이식 가능한 실행) 파일 내 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-106">[in] The address within the mapped portable executable (PE) file of the unmanaged function that is to be called.</span></span>  
  
 `pbCallNeedsHostHook`  
 <span data-ttu-id="d7112-107">제한이 호스트에서 후크를 호출 해야 하는지 여부를 나타내는 부울 값에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-107">[out] A pointer to a Boolean value that indicates whether the host requires the call to be hooked.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7112-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="d7112-108">Return Value</span></span>  
  
|<span data-ttu-id="d7112-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d7112-109">HRESULT</span></span>|<span data-ttu-id="d7112-110">설명</span><span class="sxs-lookup"><span data-stu-id="d7112-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d7112-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d7112-111">S_OK</span></span>|<span data-ttu-id="d7112-112">`CallNeedsHostHook` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-112">`CallNeedsHostHook` returned successfully.</span></span>|  
|<span data-ttu-id="d7112-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d7112-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d7112-114">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d7112-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d7112-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d7112-116">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-116">The call timed out.</span></span>|  
|<span data-ttu-id="d7112-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d7112-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d7112-118">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d7112-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d7112-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d7112-120">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d7112-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d7112-121">E_FAIL</span></span>|<span data-ttu-id="d7112-122">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-122">An unknown catastrophic failure has occurred.</span></span> <span data-ttu-id="d7112-123">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d7112-124">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7112-125">설명</span><span class="sxs-lookup"><span data-stu-id="d7112-125">Remarks</span></span>  

 <span data-ttu-id="d7112-126">CLR은 코드 실행을 최적화 하는 데 도움이 되도록 컴파일하는 동안 각 플랫폼 호출에 대 한 분석을 수행 하 여 호출이 인라인 될 수 있는지 여부를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-126">To help optimize code execution, the CLR performs an analysis of each platform invoke call during compilation to determine whether the call can be inlined.</span></span> <span data-ttu-id="d7112-127">`CallNeedsHostHook` 관리 되지 않는 함수에 대 한 호출이 후크 되도록 요구 하 여 호스트가 해당 결정을 재정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-127">`CallNeedsHostHook` enables the host to override that decision by requiring that a call to an unmanaged function be hooked.</span></span> <span data-ttu-id="d7112-128">호스트에 후크가 필요 하면 런타임에서 호출을 인라인 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-128">If the host requires a hook, the runtime does not inline the call.</span></span>  
  
 <span data-ttu-id="d7112-129">호스트에는 일반적으로 부동 소수점 상태를 조정 해야 하는 후크가 필요 합니다. 또는 호출이 호스트에서 메모리 또는 사용 된 모든 잠금에 대 한 런타임 요청을 추적할 수 없는 상태를 호출 한다는 알림이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-129">The host typically would require a hook where it must adjust a floating-point state, or upon receiving notification that a call is entering a state where the host cannot track the runtime's requests for memory or any locks taken.</span></span> <span data-ttu-id="d7112-130">호스트에서 호출이 후크 되어야 하는 경우 런타임은 [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md)및 [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md)에 대 한 호출을 사용 하 여 관리 코드와의 전환을 호스트에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-130">When the host requires that the call be hooked, the runtime notifies the host of transitions to and from managed code by using calls to [EnterRuntime](ihosttaskmanager-enterruntime-method.md), [LeaveRuntime](ihosttaskmanager-leaveruntime-method.md), [ReverseEnterRuntime](ihosttaskmanager-reverseenterruntime-method.md), and [ReverseLeaveRuntime](ihosttaskmanager-reverseleaveruntime-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7112-131">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d7112-131">Requirements</span></span>  

 <span data-ttu-id="d7112-132">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d7112-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7112-133">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d7112-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d7112-134">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d7112-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d7112-135">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7112-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7112-136">참조</span><span class="sxs-lookup"><span data-stu-id="d7112-136">See also</span></span>

- [<span data-ttu-id="d7112-137">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d7112-137">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d7112-138">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d7112-138">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d7112-139">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d7112-139">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d7112-140">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d7112-140">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
