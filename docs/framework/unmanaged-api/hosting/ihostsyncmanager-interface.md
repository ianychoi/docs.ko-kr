---
title: IHostSyncManager 인터페이스
ms.date: 03/30/2017
api_name:
- IHostSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager
helpviewer_keywords:
- IHostSyncManager interface [.NET Framework hosting]
ms.assetid: 2e081a37-6a28-4c93-b7ab-1c96a464637c
topic_type:
- apiref
ms.openlocfilehash: 8a5fc42191634a2e5a441baecc4b78212ffad687
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720497"
---
# <a name="ihostsyncmanager-interface"></a><span data-ttu-id="c293f-102">IHostSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c293f-102">IHostSyncManager Interface</span></span>

<span data-ttu-id="c293f-103">Win32 동기화 함수를 사용 하는 대신 호스트를 호출 하 여 CLR (공용 언어 런타임)에서 동기화 기본 형식을 만들 수 있도록 하는 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-103">Provides methods that allow the common language runtime (CLR) to create synchronization primitives by calling the host instead of using the Win32 synchronization functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c293f-104">메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-104">Methods</span></span>  
  
|<span data-ttu-id="c293f-105">메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-105">Method</span></span>|<span data-ttu-id="c293f-106">설명</span><span class="sxs-lookup"><span data-stu-id="c293f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c293f-107">CreateAutoEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-107">CreateAutoEvent Method</span></span>](ihostsyncmanager-createautoevent-method.md)|<span data-ttu-id="c293f-108">자동 다시 설정 이벤트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-108">Creates an auto-reset event object.</span></span>|  
|[<span data-ttu-id="c293f-109">CreateCrst 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-109">CreateCrst Method</span></span>](ihostsyncmanager-createcrst-method.md)|<span data-ttu-id="c293f-110">동기화에 대 한 임계 영역 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-110">Creates a critical section object for synchronization.</span></span>|  
|[<span data-ttu-id="c293f-111">CreateCrstWithSpinCount 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-111">CreateCrstWithSpinCount Method</span></span>](ihostsyncmanager-createcrstwithspincount-method.md)|<span data-ttu-id="c293f-112">동기화에 대 한 회전 수를 사용 하 여 임계 영역 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-112">Creates a critical section object with spin count for synchronization.</span></span>|  
|[<span data-ttu-id="c293f-113">CreateManualEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-113">CreateManualEvent Method</span></span>](ihostsyncmanager-createmanualevent-method.md)|<span data-ttu-id="c293f-114">수동 다시 설정 이벤트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-114">Creates a manual-reset event object.</span></span>|  
|[<span data-ttu-id="c293f-115">CreateMonitorEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-115">CreateMonitorEvent Method</span></span>](ihostsyncmanager-createmonitorevent-method.md)|<span data-ttu-id="c293f-116">모니터링 되는 자동 다시 설정 이벤트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-116">Creates a monitored auto-reset event object.</span></span>|  
|[<span data-ttu-id="c293f-117">CreateRWLockReaderEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-117">CreateRWLockReaderEvent Method</span></span>](ihostsyncmanager-createrwlockreaderevent-method.md)|<span data-ttu-id="c293f-118">판독기 잠금 구현에 대 한 수동 다시 설정 이벤트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-118">Creates a manual-reset event object for the implementation of a reader lock.</span></span>|  
|[<span data-ttu-id="c293f-119">CreateRWLockWriterEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-119">CreateRWLockWriterEvent Method</span></span>](ihostsyncmanager-createrwlockwriterevent-method.md)|<span data-ttu-id="c293f-120">작성기 잠금 구현에 대 한 자동 다시 설정 이벤트 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-120">Creates an auto-reset event object for the implementation of a writer lock.</span></span>|  
|[<span data-ttu-id="c293f-121">CreateSemaphore 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-121">CreateSemaphore Method</span></span>](ihostsyncmanager-createsemaphore-method.md)|<span data-ttu-id="c293f-122">대기 이벤트에 대 한 세마포에 사용할 CLR에 대 한 [IHostSemaphore](ihostsemaphore-interface.md) 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-122">Creates an [IHostSemaphore](ihostsemaphore-interface.md) object for the CLR to use as a semaphore for wait events.</span></span>|  
|[<span data-ttu-id="c293f-123">SetCLRSyncManager 메서드</span><span class="sxs-lookup"><span data-stu-id="c293f-123">SetCLRSyncManager Method</span></span>](ihostsyncmanager-setclrsyncmanager-method.md)|<span data-ttu-id="c293f-124">현재 인스턴스와 연결할 [ICLRSyncManager](iclrsyncmanager-interface.md) 인스턴스를 설정 합니다 `IHostSyncManager` .</span><span class="sxs-lookup"><span data-stu-id="c293f-124">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current `IHostSyncManager` instance.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c293f-125">설명</span><span class="sxs-lookup"><span data-stu-id="c293f-125">Remarks</span></span>  

 <span data-ttu-id="c293f-126">CLR은 IID_IHostSyncManager의를 사용 하 여 `IHostSyncManager` [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) 메서드를 호출 하 여 호스트의 구현을 검색 합니다 `IID` .</span><span class="sxs-lookup"><span data-stu-id="c293f-126">The CLR discovers the host's implementation of `IHostSyncManager` by calling the [IHostControl::GetHostManager](ihostcontrol-gethostmanager-method.md) method with an `IID` of IID_IHostSyncManager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c293f-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c293f-127">Requirements</span></span>  

 <span data-ttu-id="c293f-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c293f-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c293f-129">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c293f-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c293f-130">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c293f-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c293f-131">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c293f-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c293f-132">참조</span><span class="sxs-lookup"><span data-stu-id="c293f-132">See also</span></span>

- [<span data-ttu-id="c293f-133">ICLRSyncManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c293f-133">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="c293f-134">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c293f-134">Hosting Interfaces</span></span>](hosting-interfaces.md)
