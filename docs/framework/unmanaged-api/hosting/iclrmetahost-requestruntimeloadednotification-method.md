---
description: '자세히 알아보기: ICLRMetaHost:: RequestRuntimeLoadedNotification 메서드'
title: ICLRMetaHost::RequestRuntimeLoadedNotification 메서드
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.RequestRuntimeLoadedNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::RequestRuntimeLoadedNotification
helpviewer_keywords:
- RequestRuntimeLoadedNotification method [.NET Framework hosting]
- ICLRMetaHost::RequestRuntimeLoadedNotification method [.NET Framework hosting]
ms.assetid: 0d5ccc4d-0193-41f5-af54-45d7b70d5321
topic_type:
- apiref
ms.openlocfilehash: c385d2d845642605ad47944794f6274e8d472071
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637497"
---
# <a name="iclrmetahostrequestruntimeloadednotification-method"></a><span data-ttu-id="daaa3-103">ICLRMetaHost::RequestRuntimeLoadedNotification 메서드</span><span class="sxs-lookup"><span data-stu-id="daaa3-103">ICLRMetaHost::RequestRuntimeLoadedNotification Method</span></span>

<span data-ttu-id="daaa3-104">CLR (공용 언어 런타임) 버전이 처음 로드 되었지만 아직 시작 되지 않은 경우 호출 되도록 보장 되는 콜백 함수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-104">Provides a callback function that is guaranteed to be called when a common language runtime (CLR) version is first loaded, but not yet started.</span></span> <span data-ttu-id="daaa3-105">이 메서드는 [Lockclrversion](lockclrversion-function.md) 함수를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-105">This method supersedes the [LockClrVersion](lockclrversion-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="daaa3-106">구문</span><span class="sxs-lookup"><span data-stu-id="daaa3-106">Syntax</span></span>  
  
```cpp  
HRESULT RequestRuntimeLoadedNotification (  
    [in] RuntimeLoadedCallbackFnPtr pCallbackFunction);  
```  
  
## <a name="parameters"></a><span data-ttu-id="daaa3-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="daaa3-107">Parameters</span></span>  

 `pCallbackFunction`  
 <span data-ttu-id="daaa3-108">진행 새 런타임이 로드 될 때 호출 되는 콜백 함수입니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-108">[in] The callback function that is invoked when a new runtime has been loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="daaa3-109">Return Value</span><span class="sxs-lookup"><span data-stu-id="daaa3-109">Return Value</span></span>  

 <span data-ttu-id="daaa3-110">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="daaa3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="daaa3-111">HRESULT</span></span>|<span data-ttu-id="daaa3-112">설명</span><span class="sxs-lookup"><span data-stu-id="daaa3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="daaa3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="daaa3-113">S_OK</span></span>|<span data-ttu-id="daaa3-114">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="daaa3-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="daaa3-115">E_POINTER</span></span>|<span data-ttu-id="daaa3-116">`pCallbackFunction`가 null입니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-116">`pCallbackFunction` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="daaa3-117">설명</span><span class="sxs-lookup"><span data-stu-id="daaa3-117">Remarks</span></span>  

 <span data-ttu-id="daaa3-118">콜백은 다음과 같은 방식으로 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-118">The callback works in the following way:</span></span>  
  
- <span data-ttu-id="daaa3-119">콜백은 처음으로 런타임에 로드 된 경우에만 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-119">The callback is invoked only when a runtime is loaded for the first time.</span></span>  
  
- <span data-ttu-id="daaa3-120">콜백이 동일한 런타임의 재진입 로드에 대해 호출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-120">The callback is not invoked for reentrant loads of the same runtime.</span></span>  
  
- <span data-ttu-id="daaa3-121">재진입이 아닌 런타임 로드의 경우 콜백 함수에 대 한 호출이 serialize 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-121">For non-reentrant runtime loads, calls to the callback function are serialized.</span></span>  
  
 <span data-ttu-id="daaa3-122">콜백 함수에는 다음과 같은 프로토타입이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-122">The callback function has the following prototype:</span></span>  
  
```cpp  
typedef void (__stdcall *RuntimeLoadedCallbackFnPtr)(  
                     ICLRRuntimeInfo *pRuntimeInfo,  
                     CallbackThreadSetFnPtr pfnCallbackThreadSet,  
                     CallbackThreadUnsetFnPtr pfnCallbackThreadUnset);  
```  
  
 <span data-ttu-id="daaa3-123">콜백 함수 프로토타입은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-123">The callback function prototypes are as follows:</span></span>  
  
- <span data-ttu-id="daaa3-124">`pfnCallbackThreadSet`:</span><span class="sxs-lookup"><span data-stu-id="daaa3-124">`pfnCallbackThreadSet`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadSetFnPtr)();  
    ```  
  
- <span data-ttu-id="daaa3-125">`pfnCallbackThreadUnset`:</span><span class="sxs-lookup"><span data-stu-id="daaa3-125">`pfnCallbackThreadUnset`:</span></span>  
  
    ```cpp  
    typedef HRESULT (__stdcall *CallbackThreadUnsetFnPtr)();  
    ```  
  
 <span data-ttu-id="daaa3-126">호스트가 로드 되거나 재진입 방식으로 다른 런타임을 로드 하려는 경우 `pfnCallbackThreadSet` `pfnCallbackThreadUnset` 콜백 함수에 제공 된 및 매개 변수를 다음과 같은 방식으로 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-126">If the host intends to load or cause another runtime to be loaded in a reentrant manner, the `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` parameters that are provided in the callback function must be used in the following way:</span></span>  
  
- <span data-ttu-id="daaa3-127">`pfnCallbackThreadSet` 는 이러한 로드를 시도 하기 전에 런타임 로드를 발생 시킬 수 있는 스레드에서 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-127">`pfnCallbackThreadSet` must be called by the thread that might cause a runtime load before such a load is attempted.</span></span>  
  
- <span data-ttu-id="daaa3-128">`pfnCallbackThreadUnset` 스레드가 더 이상 이러한 런타임 로드를 발생 시 키 게 하지 않고 초기 콜백에서 반환 되기 전에를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-128">`pfnCallbackThreadUnset` must be called when the thread will no longer cause such a runtime load (and before returning from the initial callback).</span></span>  
  
- <span data-ttu-id="daaa3-129">`pfnCallbackThreadSet` 및 `pfnCallbackThreadUnset` 는 모두 재진입 성이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-129">`pfnCallbackThreadSet` and `pfnCallbackThreadUnset` are both non-reentrant.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="daaa3-130">호스트 응용 프로그램은 `pfnCallbackThreadSet` 매개 변수 범위 밖에 서를 호출 해서는 안 `pfnCallbackThreadUnset` `pCallbackFunction` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-130">Host applications must not call `pfnCallbackThreadSet` and `pfnCallbackThreadUnset` outside the scope of the `pCallbackFunction` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="daaa3-131">요구 사항</span><span class="sxs-lookup"><span data-stu-id="daaa3-131">Requirements</span></span>  

 <span data-ttu-id="daaa3-132">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="daaa3-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="daaa3-133">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="daaa3-133">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="daaa3-134">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="daaa3-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="daaa3-135">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="daaa3-135">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daaa3-136">참고 항목</span><span class="sxs-lookup"><span data-stu-id="daaa3-136">See also</span></span>

- [<span data-ttu-id="daaa3-137">ICLRMetaHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="daaa3-137">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="daaa3-138">호스팅</span><span class="sxs-lookup"><span data-stu-id="daaa3-138">Hosting</span></span>](index.md)
