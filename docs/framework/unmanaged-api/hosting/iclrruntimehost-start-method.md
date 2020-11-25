---
title: ICLRRuntimeHost::Start 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::Start
helpviewer_keywords:
- ICLRRuntimeHost::Start method [.NET Framework hosting]
- Start method, ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: c0a6dce5-0a8d-42e8-808b-6ca14df9d289
topic_type:
- apiref
ms.openlocfilehash: 2358af3dff97dbe648da924bc929dd2f83b12df0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728812"
---
# <a name="iclrruntimehoststart-method"></a><span data-ttu-id="50297-102">ICLRRuntimeHost::Start 메서드</span><span class="sxs-lookup"><span data-stu-id="50297-102">ICLRRuntimeHost::Start Method</span></span>

<span data-ttu-id="50297-103">CLR (공용 언어 런타임)을 프로세스로 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="50297-103">Initializes the common language runtime (CLR) into a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50297-104">구문</span><span class="sxs-lookup"><span data-stu-id="50297-104">Syntax</span></span>  
  
```cpp  
HRESULT Start();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50297-105">Return Value</span><span class="sxs-lookup"><span data-stu-id="50297-105">Return Value</span></span>  
  
|<span data-ttu-id="50297-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="50297-106">HRESULT</span></span>|<span data-ttu-id="50297-107">설명</span><span class="sxs-lookup"><span data-stu-id="50297-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="50297-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="50297-108">S_OK</span></span>|<span data-ttu-id="50297-109">`Start` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-109">`Start` returned successfully.</span></span>|  
|<span data-ttu-id="50297-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="50297-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="50297-111">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-111">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="50297-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="50297-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="50297-113">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-113">The call timed out.</span></span>|  
|<span data-ttu-id="50297-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="50297-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="50297-115">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="50297-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="50297-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="50297-117">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="50297-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="50297-118">E_FAIL</span></span>|<span data-ttu-id="50297-119">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="50297-120">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-120">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="50297-121">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50297-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50297-122">설명</span><span class="sxs-lookup"><span data-stu-id="50297-122">Remarks</span></span>  

 <span data-ttu-id="50297-123">대부분의 시나리오에서는 `Start` 런타임이 관리 코드를 실행 하는 첫 번째 요청 시 자동으로 초기화 되기 때문에를 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-123">In many scenarios it is not necessary to call `Start`, because the runtime will initialize itself automatically upon the first request to run managed code.</span></span> <span data-ttu-id="50297-124">그러나를 사용 `Start` 하 여 런타임을 초기화 해야 하는 시기를 정확 하 게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50297-124">You can, however, use `Start` to specify exactly when the runtime should be initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50297-125">요구 사항</span><span class="sxs-lookup"><span data-stu-id="50297-125">Requirements</span></span>  

 <span data-ttu-id="50297-126">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="50297-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50297-127">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="50297-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50297-128">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50297-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50297-129">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50297-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50297-130">참조</span><span class="sxs-lookup"><span data-stu-id="50297-130">See also</span></span>

- <xref:System.AppDomain>
- [<span data-ttu-id="50297-131">ICLRRuntimeHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="50297-131">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
