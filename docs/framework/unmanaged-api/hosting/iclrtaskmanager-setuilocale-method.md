---
description: '자세히 알아보기: ICLRTaskManager:: SetUILocale 메서드'
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
ms.openlocfilehash: f4fcc916c520489bd1e39f6a44bc1bb971df4bba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799462"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="d6cf1-103">ICLRTaskManager::SetUILocale 메서드</span><span class="sxs-lookup"><span data-stu-id="d6cf1-103">ICLRTaskManager::SetUILocale Method</span></span>

<span data-ttu-id="d6cf1-104">호스트가 현재 실행 중인 작업에서 UI (사용자 인터페이스) 로캘 또는 문화권을 수정 했음을 CLR (공용 언어 런타임)에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-104">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6cf1-105">구문</span><span class="sxs-lookup"><span data-stu-id="d6cf1-105">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6cf1-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d6cf1-106">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="d6cf1-107">진행 사용자 인터페이스의 새로 할당 된 지리적 문화권과 언어에 매핑되는 로캘 식별자 값입니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-107">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6cf1-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="d6cf1-108">Return Value</span></span>  
  
|<span data-ttu-id="d6cf1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d6cf1-109">HRESULT</span></span>|<span data-ttu-id="d6cf1-110">설명</span><span class="sxs-lookup"><span data-stu-id="d6cf1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d6cf1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="d6cf1-111">S_OK</span></span>|<span data-ttu-id="d6cf1-112">`SetUILocale` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-112">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="d6cf1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d6cf1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d6cf1-114">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d6cf1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d6cf1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d6cf1-116">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-116">The call timed out.</span></span>|  
|<span data-ttu-id="d6cf1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d6cf1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d6cf1-118">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d6cf1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d6cf1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d6cf1-120">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d6cf1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d6cf1-121">E_FAIL</span></span>|<span data-ttu-id="d6cf1-122">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d6cf1-123">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d6cf1-124">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6cf1-125">설명</span><span class="sxs-lookup"><span data-stu-id="d6cf1-125">Remarks</span></span>  

 <span data-ttu-id="d6cf1-126">`SetUILocale` 호스트가 로캘 동기화에 대 한 메커니즘을 실행할 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-126">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6cf1-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d6cf1-127">Requirements</span></span>  

 <span data-ttu-id="d6cf1-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6cf1-129">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d6cf1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6cf1-130">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6cf1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6cf1-131">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6cf1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6cf1-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d6cf1-132">See also</span></span>

- [<span data-ttu-id="d6cf1-133">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6cf1-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="d6cf1-134">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6cf1-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="d6cf1-135">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6cf1-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="d6cf1-136">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d6cf1-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
