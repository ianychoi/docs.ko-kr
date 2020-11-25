---
title: IHostIoCompletionManager::CloseIoCompletionPort 메서드
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
ms.openlocfilehash: a45f8ab6372776bece09e408bc9887bfaddb0955
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727369"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="c7872-102">IHostIoCompletionManager::CloseIoCompletionPort 메서드</span><span class="sxs-lookup"><span data-stu-id="c7872-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>

<span data-ttu-id="c7872-103">호스트에서 [Createio이상 포트](ihostiocompletionmanager-createiocompletionport-method.md)에 대 한 이전 호출을 통해 열린 포트를 닫도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7872-104">구문</span><span class="sxs-lookup"><span data-stu-id="c7872-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7872-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c7872-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="c7872-106">진행 닫을 포트의 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7872-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="c7872-107">Return Value</span></span>  
  
|<span data-ttu-id="c7872-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7872-108">HRESULT</span></span>|<span data-ttu-id="c7872-109">설명</span><span class="sxs-lookup"><span data-stu-id="c7872-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7872-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7872-110">S_OK</span></span>|<span data-ttu-id="c7872-111">`CloseIoCompletionPort` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="c7872-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7872-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7872-113">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7872-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7872-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7872-115">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-115">The call timed out.</span></span>|  
|<span data-ttu-id="c7872-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7872-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7872-117">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7872-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7872-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7872-119">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7872-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7872-120">E_FAIL</span></span>|<span data-ttu-id="c7872-121">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7872-122">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7872-123">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c7872-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="c7872-124">E_INVALIDARG</span></span>|<span data-ttu-id="c7872-125">잘못 된 포트 핸들이 전달 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7872-126">설명</span><span class="sxs-lookup"><span data-stu-id="c7872-126">Remarks</span></span>  

 <span data-ttu-id="c7872-127">`hPort` 는에 대 한 이전 호출에 의해 생성 된 포트에 대 한 핸들 이어야 합니다 `CreateIoCompletionPort` .</span><span class="sxs-lookup"><span data-stu-id="c7872-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7872-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c7872-128">Requirements</span></span>  

 <span data-ttu-id="c7872-129">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c7872-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7872-130">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c7872-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7872-131">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7872-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7872-132">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7872-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7872-133">참조</span><span class="sxs-lookup"><span data-stu-id="c7872-133">See also</span></span>

- [<span data-ttu-id="c7872-134">ICLRIoCompletionManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c7872-134">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="c7872-135">IHostIoCompletionManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c7872-135">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
