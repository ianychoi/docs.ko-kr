---
title: ICorRuntimeHost::Start 메서드
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Start
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Start
helpviewer_keywords:
- Start method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Start method [.NET Framework hosting]
ms.assetid: c66f3ac5-6489-484a-9bed-c31b711cee01
topic_type:
- apiref
ms.openlocfilehash: bc647ad025b5e22187b476383ed0128761cb632f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721038"
---
# <a name="icorruntimehoststart-method"></a><span data-ttu-id="3036c-102">ICorRuntimeHost::Start 메서드</span><span class="sxs-lookup"><span data-stu-id="3036c-102">ICorRuntimeHost::Start Method</span></span>

<span data-ttu-id="3036c-103">CLR (공용 언어 런타임)을 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-103">Starts the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3036c-104">구문</span><span class="sxs-lookup"><span data-stu-id="3036c-104">Syntax</span></span>  
  
```cpp  
HRESULT Start ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="3036c-105">Return Value</span><span class="sxs-lookup"><span data-stu-id="3036c-105">Return Value</span></span>  
  
|<span data-ttu-id="3036c-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3036c-106">HRESULT</span></span>|<span data-ttu-id="3036c-107">설명</span><span class="sxs-lookup"><span data-stu-id="3036c-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3036c-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="3036c-108">S_OK</span></span>|<span data-ttu-id="3036c-109">작업이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-109">The operation was successful.</span></span>|  
|<span data-ttu-id="3036c-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3036c-110">S_FALSE</span></span>|<span data-ttu-id="3036c-111">작업을 완료 하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3036c-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3036c-112">E_FAIL</span></span>|<span data-ttu-id="3036c-113">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3036c-114">메서드가 E_FAIL 반환 하는 경우 해당 프로세스에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-114">If a method returns E_FAIL, the CLR is no longer usable in the process.</span></span> <span data-ttu-id="3036c-115">호스팅 Api에 대 한 후속 호출은 HOST_E_CLRNOTAVAILABLE을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3036c-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3036c-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3036c-117">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3036c-118">설명</span><span class="sxs-lookup"><span data-stu-id="3036c-118">Remarks</span></span>  

 <span data-ttu-id="3036c-119">`Start`CLR은 관리 코드를 실행 하는 첫 번째 요청 시 자동으로 시작 되기 때문에 일반적으로 메서드를 호출할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-119">It is typically not necessary to call the `Start` method, because the CLR starts automatically upon the first request to run managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3036c-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3036c-120">Requirements</span></span>  

 <span data-ttu-id="3036c-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3036c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3036c-122">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="3036c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3036c-123">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3036c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3036c-124">**.NET Framework 버전:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3036c-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3036c-125">참조</span><span class="sxs-lookup"><span data-stu-id="3036c-125">See also</span></span>

- [<span data-ttu-id="3036c-126">ICorRuntimeHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3036c-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
