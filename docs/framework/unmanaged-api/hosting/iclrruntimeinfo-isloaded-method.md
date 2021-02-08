---
description: '자세히 알아보기: ICLRRuntimeInfo:: IsLoaded 메서드'
title: ICLRRuntimeInfo::IsLoaded 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: e6a5984dbd2340fe07af546dd48ae6760d5b4271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799706"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="88513-103">ICLRRuntimeInfo::IsLoaded 메서드</span><span class="sxs-lookup"><span data-stu-id="88513-103">ICLRRuntimeInfo::IsLoaded Method</span></span>

<span data-ttu-id="88513-104">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스와 연결 된 CLR (공용 언어 런타임)이 프로세스에 로드 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="88513-104">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="88513-105">런타임을 시작 하지 않고도 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88513-105">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88513-106">구문</span><span class="sxs-lookup"><span data-stu-id="88513-106">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88513-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="88513-107">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="88513-108">진행 프로세스에 대 한 핸들입니다.</span><span class="sxs-lookup"><span data-stu-id="88513-108">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="88513-109">[out] `true` CLR이 프로세스에 로드 되 면이 고, 그렇지 않으면입니다. 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="88513-109">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88513-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="88513-110">Return Value</span></span>  

 <span data-ttu-id="88513-111">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="88513-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="88513-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88513-112">HRESULT</span></span>|<span data-ttu-id="88513-113">설명</span><span class="sxs-lookup"><span data-stu-id="88513-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88513-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="88513-114">S_OK</span></span>|<span data-ttu-id="88513-115">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88513-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="88513-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="88513-116">E_POINTER</span></span>|<span data-ttu-id="88513-117">`pbLoaded`가 null입니다.</span><span class="sxs-lookup"><span data-stu-id="88513-117">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88513-118">설명</span><span class="sxs-lookup"><span data-stu-id="88513-118">Remarks</span></span>  

 <span data-ttu-id="88513-119">이 메서드는 다음 함수와 인터페이스와 이전 버전과 호환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88513-119">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="88513-120">[ICorRuntimeHost](icorruntimehost-interface.md) 인터페이스 (.NET Framework 버전 1 호스팅 API)</span><span class="sxs-lookup"><span data-stu-id="88513-120">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="88513-121">[ICLRRuntimeHost](iclrruntimehost-interface.md) 인터페이스 (.NET Framework 2.0 호스팅 API)</span><span class="sxs-lookup"><span data-stu-id="88513-121">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="88513-122">사용 되지 않는 `CorBindTo*` 함수 (.NET Framework 2.0 호스팅 API에서 [사용 되지 않는 CLR 호스팅 함수](deprecated-clr-hosting-functions.md) 참조)</span><span class="sxs-lookup"><span data-stu-id="88513-122">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="88513-123">호스트는 CorBindToRuntime 함수와 같은 사용 되지 않는 함수 중 하나를 호출 `CorBindTo*` 하 여 특정 버전의 CLR을 인스턴스화할 수 있습니다. [](corbindtoruntime-function.md)</span><span class="sxs-lookup"><span data-stu-id="88513-123">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="88513-124">그러면 호스트에서 [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) 메서드를 호출 하 고 동일한 버전 번호를 지정 하 여 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88513-124">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="88513-125">그런 다음 호스트에서 반환 된 `IsLoaded` [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스에 대해 메서드를 호출 하면 `pbLoaded` 이 반환 되 고, `true` 그렇지 않으면를 반환 `false` 합니다.</span><span class="sxs-lookup"><span data-stu-id="88513-125">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88513-126">요구 사항</span><span class="sxs-lookup"><span data-stu-id="88513-126">Requirements</span></span>  

 <span data-ttu-id="88513-127">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88513-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88513-128">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="88513-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="88513-129">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88513-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="88513-130">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88513-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88513-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88513-131">See also</span></span>

- [<span data-ttu-id="88513-132">ICLRRuntimeInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="88513-132">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="88513-133">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="88513-133">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="88513-134">호스팅</span><span class="sxs-lookup"><span data-stu-id="88513-134">Hosting</span></span>](index.md)
