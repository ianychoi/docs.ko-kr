---
title: IHostTaskManager::SetCLRTaskManager 메서드
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: 23d0679599c681468caa2507518d0ae3144ac26a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669798"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="bb235-102">IHostTaskManager::SetCLRTaskManager 메서드</span><span class="sxs-lookup"><span data-stu-id="bb235-102">IHostTaskManager::SetCLRTaskManager Method</span></span>

<span data-ttu-id="bb235-103">호스트에 CLR (공용 언어 런타임)에 의해 구현 된 [ICLRTaskManager](iclrtaskmanager-interface.md) 인스턴스에 대 한 인터페이스 포인터를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb235-104">구문</span><span class="sxs-lookup"><span data-stu-id="bb235-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb235-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bb235-105">Parameters</span></span>  

 `pManager`  
 <span data-ttu-id="bb235-106">진행 `ICLRTaskManager` 공용 언어 런타임에서 구현 하는 인스턴스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb235-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="bb235-107">Return Value</span></span>  
  
|<span data-ttu-id="bb235-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb235-108">HRESULT</span></span>|<span data-ttu-id="bb235-109">설명</span><span class="sxs-lookup"><span data-stu-id="bb235-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb235-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb235-110">S_OK</span></span>|<span data-ttu-id="bb235-111">`SetCLRTaskManager` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="bb235-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb235-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb235-113">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb235-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb235-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb235-115">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-115">The call timed out.</span></span>|  
|<span data-ttu-id="bb235-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb235-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb235-117">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb235-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb235-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb235-119">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb235-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb235-120">E_FAIL</span></span>|<span data-ttu-id="bb235-121">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb235-122">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb235-123">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb235-124">설명</span><span class="sxs-lookup"><span data-stu-id="bb235-124">Remarks</span></span>  

 <span data-ttu-id="bb235-125">런타임에서는 `SetCLRTaskManager` 를 호출 하 여 인스턴스에 대 한 인터페이스 포인터를 호스트에 제공 합니다 `ICLRTaskManager` .</span><span class="sxs-lookup"><span data-stu-id="bb235-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb235-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bb235-126">Requirements</span></span>  

 <span data-ttu-id="bb235-127">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb235-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb235-128">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb235-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb235-129">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb235-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb235-130">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb235-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb235-131">참조</span><span class="sxs-lookup"><span data-stu-id="bb235-131">See also</span></span>

- [<span data-ttu-id="bb235-132">ICLRTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bb235-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="bb235-133">ICLRTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bb235-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="bb235-134">IHostTask 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bb235-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="bb235-135">IHostTaskManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bb235-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
