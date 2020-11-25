---
title: IHostTaskManager::SetLocale 메서드
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
ms.openlocfilehash: 7730c2dddaca98e4cb06cdb381e8a46ff23c97f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699211"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="fe3ee-102">IHostTaskManager::SetLocale 메서드</span><span class="sxs-lookup"><span data-stu-id="fe3ee-102">IHostTaskManager::SetLocale Method</span></span>

<span data-ttu-id="fe3ee-103">CLR (공용 언어 런타임)이 현재 실행 중인 작업에 대해 로캘 또는 문화권을 변경 했음을 호스트에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe3ee-104">구문</span><span class="sxs-lookup"><span data-stu-id="fe3ee-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe3ee-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="fe3ee-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="fe3ee-106">진행 새로 할당 된 지리적 문화권과 언어에 매핑되는 로캘 식별자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe3ee-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="fe3ee-107">Return Value</span></span>  
  
|<span data-ttu-id="fe3ee-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fe3ee-108">HRESULT</span></span>|<span data-ttu-id="fe3ee-109">설명</span><span class="sxs-lookup"><span data-stu-id="fe3ee-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fe3ee-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fe3ee-110">S_OK</span></span>|<span data-ttu-id="fe3ee-111">`SetLocale` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="fe3ee-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fe3ee-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fe3ee-113">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fe3ee-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fe3ee-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fe3ee-115">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-115">The call timed out.</span></span>|  
|<span data-ttu-id="fe3ee-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fe3ee-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fe3ee-117">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fe3ee-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fe3ee-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fe3ee-119">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fe3ee-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fe3ee-120">E_FAIL</span></span>|<span data-ttu-id="fe3ee-121">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fe3ee-122">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fe3ee-123">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fe3ee-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="fe3ee-124">E_NOTIMPL</span></span>|<span data-ttu-id="fe3ee-125">호스트에서 관리 되는 사용자 코드를 사용 하 여 로캘을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe3ee-126">설명</span><span class="sxs-lookup"><span data-stu-id="fe3ee-126">Remarks</span></span>  

 <span data-ttu-id="fe3ee-127">`SetLocale` <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 관리 코드에 의해 속성 값이 변경 되 면 런타임에서를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="fe3ee-128">이 메서드는 호스트가 로캘 동기화에 대 한 메커니즘을 실행할 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="fe3ee-129">호스트가 관리 코드에서 로캘을 변경할 수 없도록 허용 하지 않거나 로캘을 동기화 하는 메커니즘을 구현 하지 않는 경우이 메서드에서 E_NOTIMPL을 반환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe3ee-130">요구 사항</span><span class="sxs-lookup"><span data-stu-id="fe3ee-130">Requirements</span></span>  

 <span data-ttu-id="fe3ee-131">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe3ee-132">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="fe3ee-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fe3ee-133">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fe3ee-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fe3ee-134">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe3ee-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe3ee-135">참조</span><span class="sxs-lookup"><span data-stu-id="fe3ee-135">See also</span></span>

- [<span data-ttu-id="fe3ee-136">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe3ee-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="fe3ee-137">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe3ee-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="fe3ee-138">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe3ee-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="fe3ee-139">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="fe3ee-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="fe3ee-140">SetUILocale 메서드</span><span class="sxs-lookup"><span data-stu-id="fe3ee-140">SetUILocale Method</span></span>](ihosttaskmanager-setuilocale-method.md)
