---
title: ICLRRuntimeHost::GetCurrentAppDomainId 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCurrentAppDomainId
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId
helpviewer_keywords:
- ICLRRuntimeHost::GetCurrentAppDomainId method [.NET Framework hosting]
- GetCurrentAppDomainId method [.NET Framework hosting]
ms.assetid: 33800475-7815-4976-8aca-a1038761a2ef
topic_type:
- apiref
ms.openlocfilehash: 2b1c9e99604664c99960a0741de6eae6b38fe963
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728851"
---
# <a name="iclrruntimehostgetcurrentappdomainid-method"></a><span data-ttu-id="af9e3-102">ICLRRuntimeHost::GetCurrentAppDomainId 메서드</span><span class="sxs-lookup"><span data-stu-id="af9e3-102">ICLRRuntimeHost::GetCurrentAppDomainId Method</span></span>

<span data-ttu-id="af9e3-103">현재 실행 중인의 숫자 식별자를 가져옵니다 <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="af9e3-103">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af9e3-104">구문</span><span class="sxs-lookup"><span data-stu-id="af9e3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAppDomainId(  
    [out] DWORD* pdwAppDomainId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af9e3-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="af9e3-105">Parameters</span></span>  

 `pdwAppDomainId`  
 <span data-ttu-id="af9e3-106">제한이 현재 실행 중인의 숫자 식별자입니다 <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="af9e3-106">[out] The numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="af9e3-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="af9e3-107">Return Value</span></span>  
  
|<span data-ttu-id="af9e3-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="af9e3-108">HRESULT</span></span>|<span data-ttu-id="af9e3-109">설명</span><span class="sxs-lookup"><span data-stu-id="af9e3-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="af9e3-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="af9e3-110">S_OK</span></span>|<span data-ttu-id="af9e3-111">`GetCurrentAppDomainId` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-111">`GetCurrentAppDomainId` returned successfully.</span></span>|  
|<span data-ttu-id="af9e3-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="af9e3-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="af9e3-113">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="af9e3-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="af9e3-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="af9e3-115">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-115">The call timed out.</span></span>|  
|<span data-ttu-id="af9e3-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="af9e3-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="af9e3-117">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="af9e3-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="af9e3-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="af9e3-119">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="af9e3-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="af9e3-120">E_FAIL</span></span>|<span data-ttu-id="af9e3-121">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="af9e3-122">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="af9e3-123">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="af9e3-124">설명</span><span class="sxs-lookup"><span data-stu-id="af9e3-124">Remarks</span></span>  

 <span data-ttu-id="af9e3-125">`pdwAppDomainId`매개 변수는 <xref:System.AppDomain.Id%2A> 현재 스레드가 실행 중인의 속성 값으로 설정 됩니다 <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="af9e3-125">The `pdwAppDomainId` parameter is set to the value of the <xref:System.AppDomain.Id%2A> property of the <xref:System.AppDomain> in which the current thread is executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af9e3-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="af9e3-126">Requirements</span></span>  

 <span data-ttu-id="af9e3-127">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="af9e3-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af9e3-128">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="af9e3-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af9e3-129">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af9e3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af9e3-130">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af9e3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af9e3-131">참조</span><span class="sxs-lookup"><span data-stu-id="af9e3-131">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="af9e3-132">ICLRRuntimeHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="af9e3-132">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
