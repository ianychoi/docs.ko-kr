---
title: CorBindToRuntime 함수
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 426e95281b648217642ca06f04dfbd9ec991221e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733778"
---
# <a name="corbindtoruntime-function"></a><span data-ttu-id="02893-102">CorBindToRuntime 함수</span><span class="sxs-lookup"><span data-stu-id="02893-102">CorBindToRuntime Function</span></span>

<span data-ttu-id="02893-103">관리 되지 않는 호스트에서 CLR (공용 언어 런타임)을 프로세스로 로드할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="02893-103">Enables unmanaged hosts to load the common language runtime (CLR) into a process.</span></span>  
  
 <span data-ttu-id="02893-104">이 함수는 .NET Framework 4에서 더 이상 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02893-105">구문</span><span class="sxs-lookup"><span data-stu-id="02893-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,
    [in]  LPCWSTR     pwszBuildFlavor,
    [in]  REFCLSID    rclsid,
    [in]  REFIID      riid,
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02893-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="02893-106">Parameters</span></span>  

 `pwszVersion`  
 <span data-ttu-id="02893-107">진행 로드 하려는 CLR의 버전을 설명 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-107">[in] A string describing the version of the CLR you want to load.</span></span>  
  
 <span data-ttu-id="02893-108">.NET Framework의 버전 번호는 마침표로 구분 된 네 부분으로 구성 되어 있습니다. 주 버전. 부 버전. *빌드. 수정 버전*.</span><span class="sxs-lookup"><span data-stu-id="02893-108">A version number in the .NET Framework consists of four parts separated by periods: *major.minor.build.revision*.</span></span> <span data-ttu-id="02893-109">로 전달 된 문자열은 `pwszVersion` "v" 문자 뒤에 버전 번호의 처음 세 부분 (예: "v 1.0.1529")을 사용 하 여 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="02893-109">The string passed as `pwszVersion` must start with the character "v" followed by the first three parts of the version number (for example, "v1.0.1529").</span></span>  
  
 <span data-ttu-id="02893-110">CLR의 이전 버전과의 호환성을 지정 하는 정책 문과 함께 일부 CLR 버전이 설치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02893-110">Some versions of the CLR are installed with a policy statement that specifies compatibility with previous versions of the CLR.</span></span> <span data-ttu-id="02893-111">기본적으로 시작 shim은 `pwszVersion` 정책 문에 대해 평가 하 고 요청 되는 버전과 호환 되는 최신 버전의 런타임을 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="02893-111">By default, the startup shim evaluates `pwszVersion` against policy statements and loads the latest version of the runtime that is compatible with the version being requested.</span></span> <span data-ttu-id="02893-112">호스트는 `pwszVersion`  `STARTUP_LOADER_SAFEMODE` 아래에 `flags` 설명 된 대로 매개 변수에 대 한 값을 전달 하 여 shim이 정책 평가를 건너뛰고에 지정 된 정확한 버전을 로드 하도록 강제 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-112">A host can force the shim to skip policy evaluation and load the exact version specified in `pwszVersion` by passing a value of  `STARTUP_LOADER_SAFEMODE` for the `flags` parameter, as described below.</span></span>  
  
 <span data-ttu-id="02893-113">호출자가에 null을 지정 하면 `pwszVersion` 런타임의 최신 버전이 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02893-113">If the caller specifies null for `pwszVersion`, the latest version of the runtime is loaded.</span></span> <span data-ttu-id="02893-114">Null을 전달 하면 로드 되는 런타임 버전을 호스트에서 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-114">Passing null gives the host no control over which version of the runtime is loaded.</span></span> <span data-ttu-id="02893-115">이 방법은 일부 시나리오에서 적합할 수 있지만 호스트에서 로드할 특정 버전을 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-115">Although this approach may be appropriate in some scenarios, it is strongly recommended that the host supply a specific version to load.</span></span>  
  
 `pwszBuildFlavor`  
 <span data-ttu-id="02893-116">진행 CLR의 워크스테이션 빌드 또는 서버를 로드할지 여부를 지정 하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-116">[in] A string that specifies whether to load the server or the workstation build of the CLR.</span></span> <span data-ttu-id="02893-117">유효한 값은 `svr` 및 `wks`입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-117">Valid values are `svr` and `wks`.</span></span> <span data-ttu-id="02893-118">서버 빌드는 가비지 컬렉션에 대해 여러 프로세서를 활용 하도록 최적화 되며 워크스테이션 빌드는 단일 프로세서 컴퓨터에서 실행 되는 클라이언트 응용 프로그램에 최적화 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-118">The server build is optimized to take advantage of multiple processors for garbage collections, and the workstation build is optimized for client applications running on a single-processor machine.</span></span>  
  
 <span data-ttu-id="02893-119">`pwszBuildFlavor`가 null로 설정 된 경우 워크스테이션 빌드가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02893-119">If `pwszBuildFlavor` is set to null, the workstation build is loaded.</span></span> <span data-ttu-id="02893-120">단일 프로세서 컴퓨터에서 실행 되 `pwszBuildFlavor` 는 경우가로 설정 된 경우에도 워크스테이션 빌드가 항상 로드 됩니다 `svr` .</span><span class="sxs-lookup"><span data-stu-id="02893-120">When running on a single-processor machine, the workstation build is always loaded, even if `pwszBuildFlavor` is set to `svr`.</span></span> <span data-ttu-id="02893-121">그러나 `pwszBuildFlavor` 가로 설정 되 `svr` 고 동시 가비지 수집이 지정 된 경우 (매개 변수에 대 한 설명 참조 `flags` ) 서버 빌드가 로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02893-121">However, if `pwszBuildFlavor` is set to `svr` and concurrent garbage collection is specified (see the description of the `flags` parameter), the server build is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="02893-122">진행 [ICorRuntimeHost](icorruntimehost-interface.md) 또는 [ICLRRuntimeHost](iclrruntimehost-interface.md) 인터페이스를 구현 하는 coclass 의 `CLSID`입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-122">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="02893-123">지원 되는 값은 CLSID_CorRuntimeHost 또는 CLSID_CLRRuntimeHost입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-123">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="02893-124">진행 `IID` 에서 요청 된 인터페이스의입니다 `rclsid` .</span><span class="sxs-lookup"><span data-stu-id="02893-124">[in] The `IID` of the requested interface from `rclsid`.</span></span> <span data-ttu-id="02893-125">지원 되는 값은 IID_ICorRuntimeHost 또는 IID_ICLRRuntimeHost입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-125">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="02893-126">제한이 에 대해 반환 된 인터페이스 포인터 `riid` 입니다.</span><span class="sxs-lookup"><span data-stu-id="02893-126">[out] The returned interface pointer to `riid`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02893-127">설명</span><span class="sxs-lookup"><span data-stu-id="02893-127">Remarks</span></span>  

 <span data-ttu-id="02893-128">`pwszVersion`가 존재 하지 않는 런타임 버전을 지정 하는 경우 `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD HRESULT 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="02893-128">If `pwszVersion` specifies a runtime version that does not exist, `CorBindToRuntimeEx` returns an HRESULT value of CLR_E_SHIM_RUNTIMELOAD.</span></span>  
  
## <a name="execution-context-and-flow-of-windows-identity"></a><span data-ttu-id="02893-129">Windows Id의 실행 컨텍스트 및 흐름</span><span class="sxs-lookup"><span data-stu-id="02893-129">Execution Context and Flow of Windows Identity</span></span>  

 <span data-ttu-id="02893-130">CLR 버전 1에서 <xref:System.Security.Principal.WindowsIdentity> 개체는 새 스레드, 스레드 풀 또는 타이머 콜백과 같은 비동기 요소를 통해 전달 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-130">In version 1 of the CLR, the <xref:System.Security.Principal.WindowsIdentity> object does not flow across asynchronous points such as new threads, thread pools, or timer callbacks.</span></span> <span data-ttu-id="02893-131">CLR 버전 2.0에서 <xref:System.Threading.ExecutionContext> 개체는 현재 실행 중인 스레드에 대 한 일부 정보를 래핑하고 응용 프로그램 도메인 경계를 넘어 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="02893-131">In version 2.0 of the CLR, an <xref:System.Threading.ExecutionContext> object wraps some information about the currently executing thread and flows it across any asynchronous point, but not across application domain boundaries.</span></span> <span data-ttu-id="02893-132">마찬가지로, <xref:System.Security.Principal.WindowsIdentity> 개체도 모든 비동기 지점에서 흐릅니다.</span><span class="sxs-lookup"><span data-stu-id="02893-132">Similarly, the <xref:System.Security.Principal.WindowsIdentity> object also flows across any asynchronous point.</span></span> <span data-ttu-id="02893-133">따라서 스레드의 현재 가장 (있는 경우)는 흐름이 너무 많습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-133">Therefore, the current impersonation on the thread, if any, flows too.</span></span>  
  
 <span data-ttu-id="02893-134">흐름은 다음 두 가지 방법으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-134">You can alter the flow in two ways:</span></span>  
  
1. <span data-ttu-id="02893-135"><xref:System.Threading.ExecutionContext>스레드 단위로 흐름을 표시 하지 않도록 설정 수정 ( <xref:System.Threading.ExecutionContext.SuppressFlow%2A> , <xref:System.Security.SecurityContext.SuppressFlow%2A> 및 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 메서드 참조)</span><span class="sxs-lookup"><span data-stu-id="02893-135">By modifying the <xref:System.Threading.ExecutionContext> settings to suppress the flow on a per-thread basis (see the <xref:System.Threading.ExecutionContext.SuppressFlow%2A>, <xref:System.Security.SecurityContext.SuppressFlow%2A>, and <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> methods).</span></span>  
  
2. <span data-ttu-id="02893-136">프로세스 기본 모드를 버전 1 호환성 모드로 변경 하 여 <xref:System.Security.Principal.WindowsIdentity> 현재 스레드의 설정에 관계 없이 개체가 비동기 지점에서 이동 하지 않습니다 <xref:System.Threading.ExecutionContext> .</span><span class="sxs-lookup"><span data-stu-id="02893-136">By changing the process default mode to the version 1 compatibility mode, where the <xref:System.Security.Principal.WindowsIdentity> object does not flow across any asynchronous point, regardless of the <xref:System.Threading.ExecutionContext> settings on the current thread.</span></span> <span data-ttu-id="02893-137">기본 모드를 변경 하는 방법은 관리 되는 실행 파일 또는 관리 되지 않는 호스팅 인터페이스를 사용 하 여 CLR을 로드 하는지 여부에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="02893-137">How you change the default mode depends on whether you use a managed executable or an unmanaged hosting interface to load the CLR:</span></span>  
  
    1. <span data-ttu-id="02893-138">관리 되는 실행 파일의 경우 요소의 특성을로 설정 해야 합니다 `enabled` [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) `true` .</span><span class="sxs-lookup"><span data-stu-id="02893-138">For managed executables, you must set the `enabled` attribute of the [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) element to `true`.</span></span>  
  
    2. <span data-ttu-id="02893-139">관리 되지 않는 호스팅 인터페이스의 경우 `STARTUP_LEGACY_IMPERSONATION` `flags` 함수를 호출할 때 매개 변수에서 플래그를 설정 합니다 `CorBindToRuntimeEx` .</span><span class="sxs-lookup"><span data-stu-id="02893-139">For unmanaged hosting interfaces, set the `STARTUP_LEGACY_IMPERSONATION` flag in the `flags` parameter when calling the `CorBindToRuntimeEx` function.</span></span>  
  
     <span data-ttu-id="02893-140">버전 1 호환성 모드는 전체 프로세스와 프로세스의 모든 응용 프로그램 도메인에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="02893-140">The version 1 compatibility mode applies to the entire process and to all the application domains in the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02893-141">설명</span><span class="sxs-lookup"><span data-stu-id="02893-141">Remarks</span></span>  

 <span data-ttu-id="02893-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) 하 고 `CorBindToRuntime` 동일한 작업을 수행 하지만 함수를 사용 하 여 `CorBindToRuntimeEx` CLR의 동작을 지정 하는 플래그를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02893-142">[CorBindToRuntimeEx](corbindtoruntimeex-function.md) and `CorBindToRuntime` perform the same operation, but the `CorBindToRuntimeEx` function allows you to set flags to specify the behavior of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02893-143">요구 사항</span><span class="sxs-lookup"><span data-stu-id="02893-143">Requirements</span></span>  

 <span data-ttu-id="02893-144">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="02893-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02893-145">**헤더:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="02893-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="02893-146">**라이브러리:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02893-146">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02893-147">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02893-147">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02893-148">참조</span><span class="sxs-lookup"><span data-stu-id="02893-148">See also</span></span>

- [<span data-ttu-id="02893-149">CorBindToCurrentRuntime 함수</span><span class="sxs-lookup"><span data-stu-id="02893-149">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="02893-150">CorBindToRuntimeByCfg 함수</span><span class="sxs-lookup"><span data-stu-id="02893-150">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="02893-151">CorBindToRuntimeEx 함수</span><span class="sxs-lookup"><span data-stu-id="02893-151">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="02893-152">CorBindToRuntimeHost 함수</span><span class="sxs-lookup"><span data-stu-id="02893-152">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="02893-153">ICorRuntimeHost 인터페이스</span><span class="sxs-lookup"><span data-stu-id="02893-153">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="02893-154">사용되지 않는 CLR 호스팅 함수</span><span class="sxs-lookup"><span data-stu-id="02893-154">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
