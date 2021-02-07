---
description: '자세히 알아보기: IHostAssemblyManager:: GetNonHostStoreAssemblies 메서드'
title: IHostAssemblyManager::GetNonHostStoreAssemblies 메서드
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetNonHostStoreAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies
helpviewer_keywords:
- IHostAssemblyManager::GetNonHostStoreAssemblies method [.NET Framework hosting]
- GetNonHostStoreAssemblies method [.NET Framework hosting]
ms.assetid: d2250b38-c76a-40ce-80c8-ba45149886e8
topic_type:
- apiref
ms.openlocfilehash: ef551db45428b2381dfeae8f722257241a4deaf0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709050"
---
# <a name="ihostassemblymanagergetnonhoststoreassemblies-method"></a><span data-ttu-id="99714-103">IHostAssemblyManager::GetNonHostStoreAssemblies 메서드</span><span class="sxs-lookup"><span data-stu-id="99714-103">IHostAssemblyManager::GetNonHostStoreAssemblies Method</span></span>

<span data-ttu-id="99714-104">호스트에서 CLR (공용 언어 런타임)을 로드 하는 데 필요한 어셈블리 목록을 나타내는 [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) 에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="99714-104">Gets an interface pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that represents the list of assemblies that the host expects the common language runtime (CLR) to load.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99714-105">구문</span><span class="sxs-lookup"><span data-stu-id="99714-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNonHostStoreAssemblies (  
    [out] ICLRAssemblyReferenceList **ppReferenceList  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99714-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="99714-106">Parameters</span></span>  

 `ppReferenceList`  
 <span data-ttu-id="99714-107">제한이 `ICLRAssemblyReferenceList` 호스트가 CLR에서 로드할 것으로 예상 하는 어셈블리에 대 한 참조 목록을 포함 하는의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="99714-107">[out] A pointer to the address of an `ICLRAssemblyReferenceList` that contains a list of references to assemblies that the host expects the CLR to load.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99714-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="99714-108">Return Value</span></span>  
  
|<span data-ttu-id="99714-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99714-109">HRESULT</span></span>|<span data-ttu-id="99714-110">설명</span><span class="sxs-lookup"><span data-stu-id="99714-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99714-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="99714-111">S_OK</span></span>|<span data-ttu-id="99714-112">`GetNonHostStoreAssemblies` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-112">`GetNonHostStoreAssemblies` returned successfully.</span></span>|  
|<span data-ttu-id="99714-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99714-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99714-114">CLR이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99714-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99714-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99714-116">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-116">The call timed out.</span></span>|  
|<span data-ttu-id="99714-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99714-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99714-118">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99714-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99714-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99714-120">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99714-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99714-121">E_FAIL</span></span>|<span data-ttu-id="99714-122">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99714-123">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99714-124">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99714-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99714-125">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="99714-125">E_OUTOFMEMORY</span></span>|<span data-ttu-id="99714-126">요청한에 대 한 참조 목록을 만드는 데 사용할 수 있는 메모리가 부족 `ICLRAssemblyReferenceList` 합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-126">Not enough memory was available to create the list of references for the requested `ICLRAssemblyReferenceList`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99714-127">설명</span><span class="sxs-lookup"><span data-stu-id="99714-127">Remarks</span></span>  

 <span data-ttu-id="99714-128">CLR은 다음 지침 집합을 사용 하 여 참조를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-128">The CLR resolves references using the following set of guidelines:</span></span>  
  
- <span data-ttu-id="99714-129">먼저에서 반환 하는 어셈블리 참조의 목록을 참조 합니다 `GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="99714-129">First, it consults the list of assembly references returned by `GetNonHostStoreAssemblies`.</span></span>  
  
- <span data-ttu-id="99714-130">어셈블리가 목록에 표시 되 면 CLR은이를 정상적으로 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-130">If the assembly appears in the list, the CLR binds to it normally.</span></span>  
  
- <span data-ttu-id="99714-131">어셈블리가 목록에 표시 되지 않고 호스트에서 [IHostAssemblyStore](ihostassemblystore-interface.md)의 구현을 제공한 경우 CLR은 [IHostAssemblyStore::P rovideassembly](ihostassemblystore-provideassembly-method.md) 를 호출 하 여 호스트가 바인딩할 어셈블리를 제공할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-131">If the assembly does not appear in the list and the host has provided an implementation of [IHostAssemblyStore](ihostassemblystore-interface.md), the CLR calls [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) to allow the host to supply the assembly to bind to.</span></span>  
  
- <span data-ttu-id="99714-132">그렇지 않으면 CLR이 어셈블리에 바인딩하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-132">Otherwise, the CLR fails to bind to the assembly.</span></span>  
  
 <span data-ttu-id="99714-133">호스트가 null로 설정 된 경우 `ppReferenceList` CLR은 먼저 전역 어셈블리 캐시를 검색 하 고를 호출한 `ProvideAssembly` 다음 응용 프로그램 기반을 검색 하 여 어셈블리 참조를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-133">If the host sets `ppReferenceList` to null, the CLR first probes the global assembly cache, calls `ProvideAssembly`, and then probes the application base to resolve an assembly reference.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99714-134">초기화 되 면 CLR은 `GetNonHostStoreAssemblies` 한 번만 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="99714-134">Upon initialization, the CLR calls `GetNonHostStoreAssemblies` only once.</span></span> <span data-ttu-id="99714-135">메서드가 다시 호출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="99714-135">The method is not called again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99714-136">요구 사항</span><span class="sxs-lookup"><span data-stu-id="99714-136">Requirements</span></span>  

 <span data-ttu-id="99714-137">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="99714-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99714-138">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="99714-138">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99714-139">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="99714-139">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99714-140">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99714-140">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99714-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="99714-141">See also</span></span>

- [<span data-ttu-id="99714-142">ICLRAssemblyReferenceList 인터페이스</span><span class="sxs-lookup"><span data-stu-id="99714-142">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="99714-143">IHostAssemblyManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="99714-143">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="99714-144">IHostAssemblyStore 인터페이스</span><span class="sxs-lookup"><span data-stu-id="99714-144">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
