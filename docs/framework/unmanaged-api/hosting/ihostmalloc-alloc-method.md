---
description: '자세히 알아보기: IHostMAlloc:: Alloc 메서드'
title: IHostMAlloc::Alloc 메서드
ms.date: 03/30/2017
api_name:
- IHostMAlloc.Alloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::Alloc
helpviewer_keywords:
- Alloc method, IHostMAlloc interface [.NET Framework hosting]
- IHostMAlloc::Alloc method [.NET Framework hosting]
ms.assetid: a3007f5e-d75d-4b37-842b-704e9edced5e
topic_type:
- apiref
ms.openlocfilehash: e0349c273ef9e3194bb8bad167510dd8fefcab62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708237"
---
# <a name="ihostmallocalloc-method"></a><span data-ttu-id="e2377-103">IHostMAlloc::Alloc 메서드</span><span class="sxs-lookup"><span data-stu-id="e2377-103">IHostMAlloc::Alloc Method</span></span>

<span data-ttu-id="e2377-104">호스트가 힙에서 지정 된 양의 메모리를 할당 하도록 요청 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-104">Requests that the host allocate the specified amount of memory from the heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2377-105">구문</span><span class="sxs-lookup"><span data-stu-id="e2377-105">Syntax</span></span>  
  
```cpp  
HRESULT Alloc (  
    [in] SIZE_T  cbSize,
    [in] EMemoryCriticalLevel dwCriticalLevel,
    [out] void** ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2377-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e2377-106">Parameters</span></span>  

 `cbSize`  
 <span data-ttu-id="e2377-107">진행 현재 메모리 할당 요청의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-107">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="e2377-108">진행 할당 오류의 영향을 나타내는 [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) 값 중 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-108">[in] One of the [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="e2377-109">제한이 할당 된 메모리에 대 한 포인터 이거나, 요청을 완료할 수 없는 경우 null입니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-109">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2377-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="e2377-110">Return Value</span></span>  
  
|<span data-ttu-id="e2377-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e2377-111">HRESULT</span></span>|<span data-ttu-id="e2377-112">설명</span><span class="sxs-lookup"><span data-stu-id="e2377-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2377-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="e2377-113">S_OK</span></span>|<span data-ttu-id="e2377-114">`Alloc` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-114">`Alloc` returned successfully.</span></span>|  
|<span data-ttu-id="e2377-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e2377-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e2377-116">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e2377-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e2377-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e2377-118">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-118">The call timed out.</span></span>|  
|<span data-ttu-id="e2377-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e2377-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e2377-120">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e2377-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e2377-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e2377-122">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e2377-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e2377-123">E_FAIL</span></span>|<span data-ttu-id="e2377-124">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e2377-125">메서드가 E_FAIL 반환 하는 경우 해당 프로세스 내에서 더 이상 CLR을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e2377-126">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e2377-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e2377-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e2377-128">할당 요청을 완료 하는 데 사용할 수 있는 메모리가 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-128">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2377-129">설명</span><span class="sxs-lookup"><span data-stu-id="e2377-129">Remarks</span></span>  

 <span data-ttu-id="e2377-130">CLR은 `IHostMalloc` [IHostMemoryManager:: CreateMalloc](ihostmemorymanager-createmalloc-method.md) 메서드를 호출 하 여 인스턴스에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-130">The CLR gets an interface pointer to an `IHostMalloc` instance by calling the [IHostMemoryManager::CreateMalloc](ihostmemorymanager-createmalloc-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2377-131">요구 사항</span><span class="sxs-lookup"><span data-stu-id="e2377-131">Requirements</span></span>  

 <span data-ttu-id="e2377-132">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e2377-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2377-133">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e2377-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2377-134">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2377-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2377-135">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2377-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2377-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e2377-136">See also</span></span>

- [<span data-ttu-id="e2377-137">IHostMemoryManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e2377-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="e2377-138">IHostMalloc 인터페이스</span><span class="sxs-lookup"><span data-stu-id="e2377-138">IHostMalloc Interface</span></span>](ihostmalloc-interface.md)
