---
title: IHostSemaphore::Wait 메서드
ms.date: 03/30/2017
api_name:
- IHostSemaphore.Wait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSemaphore::Wait
helpviewer_keywords:
- IHostSemaphore::Wait method [.NET Framework hosting]
- Wait method, IHostSemaphore interface [.NET Framework hosting]
ms.assetid: 0da962a3-ce55-44dd-ab7a-14ad7105af4a
topic_type:
- apiref
ms.openlocfilehash: 69b2338e6992c386a3cd34a632d69b73a67f14fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683006"
---
# <a name="ihostsemaphorewait-method"></a><span data-ttu-id="e699a-102">IHostSemaphore::Wait 메서드</span><span class="sxs-lookup"><span data-stu-id="e699a-102">IHostSemaphore::Wait Method</span></span>

<span data-ttu-id="e699a-103">현재 [IHostSemaphore](ihostsemaphore-interface.md) 인스턴스가 소유 될 때까지 또는 지정 된 시간이 경과할 때까지 대기 하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-103">Causes the current [IHostSemaphore](ihostsemaphore-interface.md) instance to wait until it is owned or the specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e699a-104">구문</span><span class="sxs-lookup"><span data-stu-id="e699a-104">Syntax</span></span>  
  
```cpp  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e699a-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e699a-105">Parameters</span></span>  

 `dwMilliseconds`  
 <span data-ttu-id="e699a-106">진행 현재 인스턴스를 소유 하 고 있지 않은 경우를 반환 하기 전에 대기 하는 시간 (밀리초)입니다 `IHostSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="e699a-106">[in] The number of milliseconds to wait before returning, if the current `IHostSemaphore` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="e699a-107">진행 이 작업이 차단 되는 경우 호스트에서 수행할 작업을 지정 하는 [WAIT_OPTION](wait-option-enumeration.md) 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-107">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, specifying what action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e699a-108">반환 값</span><span class="sxs-lookup"><span data-stu-id="e699a-108">Return Value</span></span>  
  
|<span data-ttu-id="e699a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e699a-109">HRESULT</span></span>|<span data-ttu-id="e699a-110">설명</span><span class="sxs-lookup"><span data-stu-id="e699a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e699a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e699a-111">S_OK</span></span>|<span data-ttu-id="e699a-112">`Wait` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="e699a-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e699a-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e699a-114">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e699a-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e699a-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e699a-116">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-116">The call timed out.</span></span>|  
|<span data-ttu-id="e699a-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e699a-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e699a-118">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e699a-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e699a-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e699a-120">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e699a-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e699a-121">E_FAIL</span></span>|<span data-ttu-id="e699a-122">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e699a-123">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e699a-124">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e699a-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="e699a-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="e699a-126">호스트가 대기 간격 중에 교착 상태를 감지 하 여 교착 상태에서 현재 인스턴스를 선택 했습니다 `IHostSemaphore` .</span><span class="sxs-lookup"><span data-stu-id="e699a-126">The host detected a deadlock during the wait interval, and chose the current `IHostSemaphore` instance as a deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e699a-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e699a-127">Requirements</span></span>  

 <span data-ttu-id="e699a-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e699a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e699a-129">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e699a-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e699a-130">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e699a-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e699a-131">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e699a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e699a-132">참조</span><span class="sxs-lookup"><span data-stu-id="e699a-132">See also</span></span>

- [<span data-ttu-id="e699a-133">ICLRSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e699a-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="e699a-134">IHostAutoEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e699a-134">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="e699a-135">IHostManualEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e699a-135">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="e699a-136">IHostSemaphore 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e699a-136">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="e699a-137">IHostSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e699a-137">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
