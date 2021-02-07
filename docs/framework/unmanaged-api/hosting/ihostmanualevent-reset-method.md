---
description: '자세히 알아보기: IHostManualEvent:: Reset 메서드'
title: IHostManualEvent::Reset 메서드
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 84debb8b37c2cdfdbf294bff6736b081424f9e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708075"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="8592b-103">IHostManualEvent::Reset 메서드</span><span class="sxs-lookup"><span data-stu-id="8592b-103">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="8592b-104">현재 [IHostManualEvent](ihostmanualevent-interface.md) 인스턴스를 신호를 받지 않는 상태로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-104">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8592b-105">구문</span><span class="sxs-lookup"><span data-stu-id="8592b-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="8592b-106">Return Value</span><span class="sxs-lookup"><span data-stu-id="8592b-106">Return Value</span></span>  
  
|<span data-ttu-id="8592b-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8592b-107">HRESULT</span></span>|<span data-ttu-id="8592b-108">설명</span><span class="sxs-lookup"><span data-stu-id="8592b-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8592b-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="8592b-109">S_OK</span></span>|<span data-ttu-id="8592b-110">`Reset` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-110">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="8592b-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8592b-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8592b-112">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8592b-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8592b-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8592b-114">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-114">The call timed out.</span></span>|  
|<span data-ttu-id="8592b-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8592b-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8592b-116">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8592b-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8592b-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8592b-118">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8592b-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8592b-119">E_FAIL</span></span>|<span data-ttu-id="8592b-120">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8592b-121">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8592b-122">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8592b-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8592b-123">Requirements</span></span>  

 <span data-ttu-id="8592b-124">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8592b-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8592b-125">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8592b-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8592b-126">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8592b-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8592b-127">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8592b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8592b-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8592b-128">See also</span></span>

- [<span data-ttu-id="8592b-129">ICLRSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8592b-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="8592b-130">IHostAutoEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8592b-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="8592b-131">IHostManualEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8592b-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="8592b-132">IHostSemaphore 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8592b-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="8592b-133">IHostSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8592b-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
