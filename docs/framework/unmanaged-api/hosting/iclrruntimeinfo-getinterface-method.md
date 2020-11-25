---
title: ICLRRuntimeInfo::GetInterface 메서드
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetInterface
helpviewer_keywords:
- GetInterface method [.NET Framework hosting]
- ICLRRuntimeInfo::GetInterface method [.NET Framework hosting]
ms.assetid: cc7b0e5b-48c3-4509-8ebb-611ddb1f7ec2
topic_type:
- apiref
ms.openlocfilehash: 192163ed8af680e39f7f3a03aee3f46546bc7450
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732075"
---
# <a name="iclrruntimeinfogetinterface-method"></a><span data-ttu-id="ece8e-102">ICLRRuntimeInfo::GetInterface 메서드</span><span class="sxs-lookup"><span data-stu-id="ece8e-102">ICLRRuntimeInfo::GetInterface Method</span></span>

<span data-ttu-id="ece8e-103">CLR을 현재 프로세스로 로드 하 고 [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md)및 [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md)와 같은 런타임 인터페이스 포인터를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-103">Loads the CLR into the current process and returns runtime interface pointers, such as [ICLRRuntimeHost](iclrruntimehost-interface.md), [ICLRStrongName](iclrstrongname-interface.md), and [IMetaDataDispenserEx](../metadata/imetadatadispenser-interface.md).</span></span>  
  
 <span data-ttu-id="ece8e-104">이 메서드는 `CorBindTo` [사용 되지 않는 CLR 호스팅 함수](deprecated-clr-hosting-functions.md) 섹션의 모든 \* 함수를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-104">This method supersedes all the `CorBindTo`\* functions in the [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece8e-105">구문</span><span class="sxs-lookup"><span data-stu-id="ece8e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInterface(  
[in]  REFCLSID rclsid,  
[in]  REFIID   riid,  
[out, iid_is(riid), retval] LPVOID *ppUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ece8e-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ece8e-106">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="ece8e-107">진행 Coclass의 CLSID 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-107">[in] The CLSID interface for the coclass.</span></span>  
  
 `riid`  
 <span data-ttu-id="ece8e-108">진행 요청 된 인터페이스의 IID입니다 `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="ece8e-108">[in] The IID of the requested `rclsid` interface.</span></span>  
  
 `ppUnk`  
 <span data-ttu-id="ece8e-109">제한이 쿼리 된 인터페이스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-109">[out] A pointer to the queried interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ece8e-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="ece8e-110">Return Value</span></span>  

 <span data-ttu-id="ece8e-111">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-111">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ece8e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ece8e-112">HRESULT</span></span>|<span data-ttu-id="ece8e-113">설명</span><span class="sxs-lookup"><span data-stu-id="ece8e-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ece8e-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="ece8e-114">S_OK</span></span>|<span data-ttu-id="ece8e-115">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-115">The method completed successfully.</span></span>|  
|<span data-ttu-id="ece8e-116">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ece8e-116">E_POINTER</span></span>|<span data-ttu-id="ece8e-117">`ppUnk`가 null입니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-117">`ppUnk` is null.</span></span>|  
|<span data-ttu-id="ece8e-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="ece8e-118">E_OUTOFMEMORY</span></span>|<span data-ttu-id="ece8e-119">메모리가 부족 하 여 요청을 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-119">Not enough memory is available to handle the request.</span></span>|  
|<span data-ttu-id="ece8e-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span><span class="sxs-lookup"><span data-stu-id="ece8e-120">CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND</span></span>|<span data-ttu-id="ece8e-121">다른 런타임이 이미 레거시 CLR 버전 2 활성화 정책에 바인딩되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-121">A different runtime was already bound to the legacy CLR version 2 activation policy.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ece8e-122">설명</span><span class="sxs-lookup"><span data-stu-id="ece8e-122">Remarks</span></span>  

 <span data-ttu-id="ece8e-123">이 메서드로 인해 CLR이 로드 되지만 초기화 되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-123">This method causes the CLR to be loaded but not initialized.</span></span>  
  
 <span data-ttu-id="ece8e-124">다음 표에서는 및에 대해 지원 되는 조합을 보여 줍니다 `rclsid` `riid` .</span><span class="sxs-lookup"><span data-stu-id="ece8e-124">The following table shows the supported combinations for `rclsid` and `riid`.</span></span>  
  
|`rclsid`|`riid`|  
|--------------|------------|  
|<span data-ttu-id="ece8e-125">CLSID_CorMetaDataDispenser</span><span class="sxs-lookup"><span data-stu-id="ece8e-125">CLSID_CorMetaDataDispenser</span></span>|<span data-ttu-id="ece8e-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="ece8e-126">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="ece8e-127">CLSID_CorMetaDataDispenserRuntime</span><span class="sxs-lookup"><span data-stu-id="ece8e-127">CLSID_CorMetaDataDispenserRuntime</span></span>|<span data-ttu-id="ece8e-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span><span class="sxs-lookup"><span data-stu-id="ece8e-128">IID_IMetaDataDispenser, IID_IMetaDataDispenserEx</span></span>|  
|<span data-ttu-id="ece8e-129">CLSID_CorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ece8e-129">CLSID_CorRuntimeHost</span></span>|<span data-ttu-id="ece8e-130">IID_ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ece8e-130">IID_ICorRuntimeHost</span></span>|  
|<span data-ttu-id="ece8e-131">CLSID_CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ece8e-131">CLSID_CLRRuntimeHost</span></span>|<span data-ttu-id="ece8e-132">IID_ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="ece8e-132">IID_ICLRRuntimeHost</span></span>|  
|<span data-ttu-id="ece8e-133">CLSID_TypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="ece8e-133">CLSID_TypeNameFactory</span></span>|<span data-ttu-id="ece8e-134">IID_ITypeNameFactory</span><span class="sxs-lookup"><span data-stu-id="ece8e-134">IID_ITypeNameFactory</span></span>|  
|<span data-ttu-id="ece8e-135">CLSID_CLRDebuggingLegacy</span><span class="sxs-lookup"><span data-stu-id="ece8e-135">CLSID_CLRDebuggingLegacy</span></span>|<span data-ttu-id="ece8e-136">IID_ICorDebug</span><span class="sxs-lookup"><span data-stu-id="ece8e-136">IID_ICorDebug</span></span>|  
|||  
|<span data-ttu-id="ece8e-137">CLSID_CLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ece8e-137">CLSID_CLRStrongName</span></span>|<span data-ttu-id="ece8e-138">IID_ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ece8e-138">IID_ICLRStrongName</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ece8e-139">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ece8e-139">Requirements</span></span>  

 <span data-ttu-id="ece8e-140">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ece8e-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece8e-141">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="ece8e-141">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ece8e-142">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ece8e-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ece8e-143">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ece8e-143">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ece8e-144">참조</span><span class="sxs-lookup"><span data-stu-id="ece8e-144">See also</span></span>

- [<span data-ttu-id="ece8e-145">ICLRRuntimeInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ece8e-145">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ece8e-146">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ece8e-146">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ece8e-147">호스팅</span><span class="sxs-lookup"><span data-stu-id="ece8e-147">Hosting</span></span>](index.md)
