---
title: ICLRTaskManager::SetUILocale 메서드
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
ms.openlocfilehash: a426fca1b7ca4bfb9cbb30a221859f7c114db682
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732427"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="312ff-102">ICLRTaskManager::SetUILocale 메서드</span><span class="sxs-lookup"><span data-stu-id="312ff-102">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="312ff-103">호스트가 현재 실행 중인 작업에서 UI (사용자 인터페이스) 로캘 또는 문화권을 수정 했음을 CLR (공용 언어 런타임)에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="312ff-104">구문</span><span class="sxs-lookup"><span data-stu-id="312ff-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="312ff-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="312ff-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="312ff-106">진행 사용자 인터페이스의 새로 할당 된 지리적 문화권과 언어에 매핑되는 로캘 식별자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="312ff-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="312ff-107">Return Value</span></span>  
  
|<span data-ttu-id="312ff-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="312ff-108">HRESULT</span></span>|<span data-ttu-id="312ff-109">설명</span><span class="sxs-lookup"><span data-stu-id="312ff-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="312ff-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="312ff-110">S_OK</span></span>|<span data-ttu-id="312ff-111">`SetUILocale` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="312ff-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="312ff-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="312ff-113">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="312ff-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="312ff-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="312ff-115">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-115">The call timed out.</span></span>|  
|<span data-ttu-id="312ff-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="312ff-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="312ff-117">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="312ff-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="312ff-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="312ff-119">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="312ff-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="312ff-120">E_FAIL</span></span>|<span data-ttu-id="312ff-121">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="312ff-122">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="312ff-123">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="312ff-124">설명</span><span class="sxs-lookup"><span data-stu-id="312ff-124">Remarks</span></span>  

 <span data-ttu-id="312ff-125">`SetUILocale` 호스트가 로캘 동기화에 대 한 메커니즘을 실행할 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="312ff-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="312ff-126">Requirements</span></span>  

 <span data-ttu-id="312ff-127">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="312ff-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="312ff-128">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="312ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="312ff-129">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="312ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="312ff-130">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="312ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="312ff-131">참조</span><span class="sxs-lookup"><span data-stu-id="312ff-131">See also</span></span>

- [<span data-ttu-id="312ff-132">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="312ff-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="312ff-133">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="312ff-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="312ff-134">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="312ff-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="312ff-135">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="312ff-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
