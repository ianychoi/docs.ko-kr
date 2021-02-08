---
description: '자세히 알아보기: ICLRMetaHostPolicy:: GetRequestedRuntime 메서드'
title: ICLRMetaHostPolicy::GetRequestedRuntime 메서드
ms.date: 03/30/2017
api_name:
- ICLRMetaHostPolicy.GetRequestedRuntime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHostPolicy::GetRequestedRuntime
helpviewer_keywords:
- GetRequestedRuntime method [.NET Framework hosting]
- ICLRMetaHostPolicy::GetRequestedRuntime method [.NET Framework hosting]
ms.assetid: 59ec1832-9cc1-4b5c-983d-03407e51de56
topic_type:
- apiref
ms.openlocfilehash: 0e11694b0cb66ad7fc28abf7bb9f7fc8c6931a19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789842"
---
# <a name="iclrmetahostpolicygetrequestedruntime-method"></a><span data-ttu-id="f1d3e-103">ICLRMetaHostPolicy::GetRequestedRuntime 메서드</span><span class="sxs-lookup"><span data-stu-id="f1d3e-103">ICLRMetaHostPolicy::GetRequestedRuntime Method</span></span>

<span data-ttu-id="f1d3e-104">호스팅 정책, 관리되는 어셈블리, 버전 문자열 및 구성 스트림에 따라 CLR(공용 언어 런타임)의 기본 버전에 대한 인터페이스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-104">Provides an interface to a preferred version of the common language runtime (CLR) based on a hosting policy, managed assembly, version string, and configuration stream.</span></span> <span data-ttu-id="f1d3e-105">이 메서드는 실제로 CLR을 로드 하거나 활성화 하지 않지만 정책 결과를 나타내는 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-105">This method does not actually load or activate the CLR, but simply returns the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that represents the policy result.</span></span> <span data-ttu-id="f1d3e-106">이 메서드는 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md)및 [getcorrequiredversion](getcorrequiredversion-function.md) 메서드를 대체 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-106">This method supersedes the [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md), [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md), [CorBindToRuntimeHost](corbindtoruntimehost-function.md), [CorBindToRuntimeByCfg](corbindtoruntimebycfg-function.md), and [GetCORRequiredVersion](getcorrequiredversion-function.md) methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="f1d3e-107">구문</span><span class="sxs-lookup"><span data-stu-id="f1d3e-107">Syntax</span></span>

```cpp
HRESULT GetRequestedRuntime(
    [in]  METAHOST_POLICY_FLAGS dwPolicyFlags,
    [in]  LPCWSTR pwzBinary,
    [in]  IStream *pCfgStream,
    [in, out, size_is(*pcchVersion)] LPWSTR pwzVersion,
    [in, out]  DWORD *pcchVersion,
    [out, size_is(*pcchImageVersion)] LPWSTR pwzImageVersion,
    [in, out]  DWORD *pcchImageVersion,
    [out] DWORD *pdwConfigFlags,
    [in]  REFIID  riid
    [out, iid_is(riid), retval] LPVOID *ppRuntime);
```

## <a name="parameters"></a><span data-ttu-id="f1d3e-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f1d3e-108">Parameters</span></span>

|<span data-ttu-id="f1d3e-109">속성</span><span class="sxs-lookup"><span data-stu-id="f1d3e-109">Name</span></span>|<span data-ttu-id="f1d3e-110">설명</span><span class="sxs-lookup"><span data-stu-id="f1d3e-110">Description</span></span>|
|----------|-----------------|
|`dwPolicyFlags`|<span data-ttu-id="f1d3e-111">[in] 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-111">[in] Required.</span></span> <span data-ttu-id="f1d3e-112">바인딩 정책을 나타내는 [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) 열거형의 멤버와 임의의 한정자 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-112">Specifies a member of the [METAHOST_POLICY_FLAGS](metahost-policy-flags-enumeration.md) enumeration, representing a binding policy, and any number of modifiers.</span></span> <span data-ttu-id="f1d3e-113">현재 사용할 수 있는 유일한 정책은 [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-113">The only policy that is currently available is [METAHOST_POLICY_HIGHCOMPAT](metahost-policy-flags-enumeration.md).</span></span><br /><br /> <span data-ttu-id="f1d3e-114">한정자는 [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md)및 [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md)를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-114">Modifiers include [METAHOST_POLICY_EMULATE_EXE_LAUNCH](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_APPLY_UPGRADE_POLICY](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_SHOW_ERROR_DIALOG](metahost-policy-flags-enumeration.md), [METAHOST_POLICY_USE_PROCESS_IMAGE_PATH](metahost-policy-flags-enumeration.md), and [METAHOST_POLICY_ENSURE_SKU_SUPPORTED](metahost-policy-flags-enumeration.md).</span></span>|
|`pwzBinary`|<span data-ttu-id="f1d3e-115">[in] 선택적 항목으로,</span><span class="sxs-lookup"><span data-stu-id="f1d3e-115">[in] Optional.</span></span> <span data-ttu-id="f1d3e-116">어셈블리 파일 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-116">Specifies the assembly file path.</span></span>|
|`pCfgStream`|<span data-ttu-id="f1d3e-117">[in] 선택적 항목으로,</span><span class="sxs-lookup"><span data-stu-id="f1d3e-117">[in] Optional.</span></span> <span data-ttu-id="f1d3e-118">구성 파일을 <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-118">Specifies the configuration file as a <xref:System.Runtime.InteropServices.ComTypes.IStream?displayProperty=nameWithType>.</span></span>|
|`pwzVersion`|<span data-ttu-id="f1d3e-119">[in, out] 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-119">[in, out] Optional.</span></span> <span data-ttu-id="f1d3e-120">로드할 기본 CLR 버전을 지정하거나 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-120">Specifies or returns the preferred CLR version to be loaded.</span></span>|
|`pcchVersion`|<span data-ttu-id="f1d3e-121">[in, out] 필수입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-121">[in, out] Required.</span></span> <span data-ttu-id="f1d3e-122">버퍼 오버런을 방지하기 위해 `pwzVersion`의 예상 크기를 입력으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-122">Specifies the expected size of `pwzVersion` as input, to avoid buffer overruns.</span></span> <span data-ttu-id="f1d3e-123">`pwzVersion`이 null이면 사전 할당을 허용하기 위해 `GetRequestedRuntime`이 반환될 때 `pcchVersion`에 `pwzVersion`의 예상 크기가 포함됩니다. 그러지 않으면 `pcchVersion`에 `pwzVersion`에 기록된 문자 수가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-123">If `pwzVersion` is null, `pcchVersion` contains the expected size of `pwzVersion` when `GetRequestedRuntime` returns, to allow pre-allocation; otherwise, `pcchVersion` contains the number of characters written to `pwzVersion`.</span></span>|
|`pwzImageVersion`|<span data-ttu-id="f1d3e-124">[out] 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-124">[out] Optional.</span></span> <span data-ttu-id="f1d3e-125">`GetRequestedRuntime`가 반환 되 면 반환 되는 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스에 해당 하는 CLR 버전을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-125">When `GetRequestedRuntime` returns, contains the CLR version corresponding to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that is returned.</span></span>|
|`pcchImageVersion`|<span data-ttu-id="f1d3e-126">[in, out] 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-126">[in, out] Optional.</span></span> <span data-ttu-id="f1d3e-127">버퍼 오버런을 방지하기 위해 `pwzImageVersion`의 크기를 입력으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-127">Specifies the size of `pwzImageVersion` as input to avoid buffer overruns.</span></span> <span data-ttu-id="f1d3e-128">`pwzImageVersion`이 null이면 사전 할당을 허용하기 위해 `GetRequestedRuntime`이 반환될 때 `pcchImageVersion`에 `pwzImageVersion`의 필수 크기가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-128">If `pwzImageVersion` is null, `pcchImageVersion` contains the required size of `pwzImageVersion` when `GetRequestedRuntime` returns, to allow pre-allocation.</span></span>|
|`pdwConfigFlags`|<span data-ttu-id="f1d3e-129">[out] 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-129">[out] Optional.</span></span> <span data-ttu-id="f1d3e-130">에서 `GetRequestedRuntime` 바인딩 프로세스 중에 구성 파일을 사용 하는 경우 반환 될 때 `pdwConfigFlags` 요소에 특성 집합이 있는지 여부를 나타내는 [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) 값 [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) `useLegacyV2RuntimeActivationPolicy` 과 특성의 값이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-130">If `GetRequestedRuntime` uses a configuration file during the binding process, when it returns, `pdwConfigFlags` contains a [METAHOST_CONFIG_FLAGS](metahost-config-flags-enumeration.md) value that indicates whether the [\<startup>](../../configure-apps/file-schema/startup/startup-element.md) element has the `useLegacyV2RuntimeActivationPolicy` attribute set, and the value of the attribute.</span></span> <span data-ttu-id="f1d3e-131">[METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) 마스크를에 적용 하 여 `pdwConfigFlags` 와 관련 된 값을 가져옵니다 `useLegacyV2RuntimeActivationPolicy` .</span><span class="sxs-lookup"><span data-stu-id="f1d3e-131">Apply the [METAHOST_CONFIG_FLAGS_LEGACY_V2_ACTIVATION_POLICY_MASK](metahost-config-flags-enumeration.md) mask to `pdwConfigFlags` to get the values relevant to `useLegacyV2RuntimeActivationPolicy`.</span></span>|
|`riid`|<span data-ttu-id="f1d3e-132">진행 요청 된 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스에 대 한 IID_ICLRRuntimeInfo 인터페이스 식별자를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-132">[in] Specifies the interface identifier IID_ICLRRuntimeInfo for the requested [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|
|`ppRuntime`|<span data-ttu-id="f1d3e-133">제한이 `GetRequestedRuntime` 가 반환 될 때 해당 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 인터페이스에 대 한 포인터를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-133">[out] When `GetRequestedRuntime` returns, contains a pointer to the corresponding [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f1d3e-134">설명</span><span class="sxs-lookup"><span data-stu-id="f1d3e-134">Remarks</span></span>

<span data-ttu-id="f1d3e-135">이 메서드가 성공하면 다음 요소 중 하나가 `<configuration><runtime>` 섹션 내의 구성 스트림에 있는 경우에만 반환된 런타임 인터페이스의 현재 기본 시작 플래그와 추가 플래그가 결합되는 부작용이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-135">When this method succeeds, it has the side effect of combining additional flags with the current default startup flags of the returned runtime interface, if and only if one or more of the following elements exist in the configuration stream within the `<configuration><runtime>` section:</span></span>

- <span data-ttu-id="f1d3e-136">`<gcServer enabled="true"/>`로 인해 `STARTUP_SERVER_GC`가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-136">`<gcServer enabled="true"/>` causes `STARTUP_SERVER_GC` to be set.</span></span>

- <span data-ttu-id="f1d3e-137">`<etwEnable enabled="true"/>`로 인해 `STARTUP_ETW`가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-137">`<etwEnable enabled="true"/>` causes `STARTUP_ETW` to be set.</span></span>

- <span data-ttu-id="f1d3e-138">`<appDomainResourceMonitoring enabled="true"/>`로 인해 `STARTUP_ARM`가 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-138">`<appDomainResourceMonitoring enabled="true"/>` causes `STARTUP_ARM` to be set.</span></span>

<span data-ttu-id="f1d3e-139">결과 기본 `STARTUP_FLAGS` 값은 기본 시작 플래그를 사용하여 이전 목록에서 설정된 값의 비트 OR 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-139">The resulting default `STARTUP_FLAGS` value is the bitwise OR combination of the values that are set from the preceding list with the default startup flags.</span></span>

## <a name="return-value"></a><span data-ttu-id="f1d3e-140">Return Value</span><span class="sxs-lookup"><span data-stu-id="f1d3e-140">Return Value</span></span>

<span data-ttu-id="f1d3e-141">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-141">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>

|<span data-ttu-id="f1d3e-142">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f1d3e-142">HRESULT</span></span>|<span data-ttu-id="f1d3e-143">설명</span><span class="sxs-lookup"><span data-stu-id="f1d3e-143">Description</span></span>|
|-------------|-----------------|
|<span data-ttu-id="f1d3e-144">S_OK</span><span class="sxs-lookup"><span data-stu-id="f1d3e-144">S_OK</span></span>|<span data-ttu-id="f1d3e-145">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-145">The method completed successfully.</span></span>|
|<span data-ttu-id="f1d3e-146">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f1d3e-146">E_POINTER</span></span>|<span data-ttu-id="f1d3e-147">`pwzVersion`은 null이 아니고 `pcchVersion`은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-147">`pwzVersion` is not null and `pcchVersion` is null.</span></span><br /><br /> <span data-ttu-id="f1d3e-148">또는</span><span class="sxs-lookup"><span data-stu-id="f1d3e-148">-or-</span></span><br /><br /> <span data-ttu-id="f1d3e-149">`pwzImageVersion`은 null이 아니고 `pcchImageVersion`은 null입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-149">`pwzImageVersion` is not null and `pcchImageVersion` is null.</span></span>|
|<span data-ttu-id="f1d3e-150">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="f1d3e-150">E_INVALIDARG</span></span>|<span data-ttu-id="f1d3e-151">`dwPolicyFlags`가 `METAHOST_POLICY_HIGHCOMPAT`를 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-151">`dwPolicyFlags` does not specify `METAHOST_POLICY_HIGHCOMPAT`.</span></span>|
|<span data-ttu-id="f1d3e-152">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="f1d3e-152">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="f1d3e-153">`pwzVersion`에 할당된 메모리가 부적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-153">The memory allocated to `pwzVersion` is inadequate.</span></span><br /><br /> <span data-ttu-id="f1d3e-154">또는</span><span class="sxs-lookup"><span data-stu-id="f1d3e-154">-or-</span></span><br /><br /> <span data-ttu-id="f1d3e-155">`pwzImageVersion`에 할당된 메모리가 부적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-155">The memory allocated to `pwzImageVersion` is inadequate.</span></span>|
|<span data-ttu-id="f1d3e-156">CLR_E_SHIM_RUNTIMELOAD</span><span class="sxs-lookup"><span data-stu-id="f1d3e-156">CLR_E_SHIM_RUNTIMELOAD</span></span>|<span data-ttu-id="f1d3e-157">`dwPolicyFlags`에 METAHOST_POLICY_APPLY_UPGRADE_POLICY가 포함되어 있고, `pwzVersion` 및 `pcchVersion`이 둘 다 null입니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-157">`dwPolicyFlags` includes METAHOST_POLICY_APPLY_UPGRADE_POLICY, and both `pwzVersion` and `pcchVersion` are null.</span></span>|

## <a name="requirements"></a><span data-ttu-id="f1d3e-158">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f1d3e-158">Requirements</span></span>

<span data-ttu-id="f1d3e-159">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-159">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f1d3e-160">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="f1d3e-160">**Header:** MetaHost.h</span></span>

<span data-ttu-id="f1d3e-161">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f1d3e-161">**Library:** Included as a resource in MSCorEE.dll</span></span>

<span data-ttu-id="f1d3e-162">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1d3e-162">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f1d3e-163">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f1d3e-163">See also</span></span>

- [<span data-ttu-id="f1d3e-164">ICLRMetaHostPolicy 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f1d3e-164">ICLRMetaHostPolicy Interface</span></span>](iclrmetahostpolicy-interface.md)
- [<span data-ttu-id="f1d3e-165">.NET Framework 4 및 4.5에 추가된 CLR 호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f1d3e-165">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="f1d3e-166">호스팅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f1d3e-166">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f1d3e-167">호스팅</span><span class="sxs-lookup"><span data-stu-id="f1d3e-167">Hosting</span></span>](index.md)
