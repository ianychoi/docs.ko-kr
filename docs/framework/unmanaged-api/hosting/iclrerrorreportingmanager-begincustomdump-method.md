---
description: '자세히 알아보기: ICLRErrorReportingManager:: BeginCustomDump 메서드'
title: ICLRErrorReportingManager::BeginCustomDump 메서드
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 3f8498068d50ffc6ea00cf4f08f969c92f010d6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689484"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="c96ea-103">ICLRErrorReportingManager::BeginCustomDump 메서드</span><span class="sxs-lookup"><span data-stu-id="c96ea-103">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="c96ea-104">오류 보고에 대 한 사용자 지정 힙 덤프의 구성을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-104">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c96ea-105">구문</span><span class="sxs-lookup"><span data-stu-id="c96ea-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c96ea-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c96ea-106">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="c96ea-107">진행 사용자 지정 힙 덤프를 빌드할 힙 덤프의 종류를 나타내는 [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-107">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="c96ea-108">진행 `items` 배열의 길이입니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-108">[in] The length of the `items` array.</span></span> <span data-ttu-id="c96ea-109">`dwFlavor`가 DUMP_FLAVOR_Mini 되지 않은 경우는 `dwNumItems` 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-109">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="c96ea-110">진행 미니 덤프에 추가할 항목을 지정 하는 [Custom덤프 항목](customdumpitem-structure.md) 인스턴스의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-110">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="c96ea-111">`dwFlavor`가 DUMP_FLAVOR_Mini 되지 않은 경우는 `items` null 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-111">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="c96ea-112">진행 나중에 사용 하도록 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-112">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c96ea-113">Return Value</span><span class="sxs-lookup"><span data-stu-id="c96ea-113">Return Value</span></span>  
  
|<span data-ttu-id="c96ea-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c96ea-114">HRESULT</span></span>|<span data-ttu-id="c96ea-115">설명</span><span class="sxs-lookup"><span data-stu-id="c96ea-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c96ea-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="c96ea-116">S_OK</span></span>|<span data-ttu-id="c96ea-117">메서드가 성공적으로 반환했습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="c96ea-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c96ea-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c96ea-119">CLR (공용 언어 런타임)이 프로세스에 로드 되지 않았거나 CLR이 관리 코드를 실행할 수 없거나 호출을 성공적으로 처리할 수 없는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c96ea-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c96ea-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c96ea-121">호출 시간이 초과 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-121">The call timed out.</span></span>|  
|<span data-ttu-id="c96ea-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c96ea-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c96ea-123">호출자가 잠금을 소유 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c96ea-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c96ea-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c96ea-125">차단 된 스레드나 파이버에서 대기 하는 동안 이벤트를 취소 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c96ea-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c96ea-126">E_FAIL</span></span>|<span data-ttu-id="c96ea-127">알 수 없는 치명적인 오류가 발생 했습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c96ea-128">메서드가 E_FAIL 반환 된 후에는 프로세스 내에서 CLR을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c96ea-129">호스팅 메서드를 이후에 호출 하면 HOST_E_CLRNOTAVAILABLE 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c96ea-130">설명</span><span class="sxs-lookup"><span data-stu-id="c96ea-130">Remarks</span></span>  

 <span data-ttu-id="c96ea-131">`BeginCustomDump`메서드는 사용자 지정 힙 덤프 구성을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-131">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="c96ea-132">[Endcustomdump](iclrerrorreportingmanager-endcustomdump-method.md) 메서드는 사용자 지정 힙 덤프 구성을 지우고 연결 된 상태를 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-132">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="c96ea-133">사용자 지정 힙 덤프가 완료 된 후이 메서드를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-133">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c96ea-134">호출 하지 못하면 `EndCustomDump` 메모리 누수가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-134">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c96ea-135">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c96ea-135">Requirements</span></span>  

 <span data-ttu-id="c96ea-136">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c96ea-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c96ea-137">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c96ea-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c96ea-138">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c96ea-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c96ea-139">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c96ea-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96ea-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c96ea-140">See also</span></span>

- [<span data-ttu-id="c96ea-141">CustomDumpItem 구조체</span><span class="sxs-lookup"><span data-stu-id="c96ea-141">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="c96ea-142">ECustomDumpFlavor 열거형</span><span class="sxs-lookup"><span data-stu-id="c96ea-142">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="c96ea-143">ICLRErrorReportingManager 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c96ea-143">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
