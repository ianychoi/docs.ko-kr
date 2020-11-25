---
title: ICLRDebugging::OpenVirtualProcess 메서드
ms.date: 03/30/2017
api_name:
- ICLRDebugging.OpenVirtualProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging::OpenVirtualProcess
helpviewer_keywords:
- OpenVirtualProcess method [.NET Framework debugging]
- ICLRDebugging::OpenVirtualProcess method [.NET Framework debugging]
ms.assetid: e8ab7c41-d508-4ed9-8a31-ead072b5a314
topic_type:
- apiref
ms.openlocfilehash: 2edd7f628e17c8dc6cbcbb577d06269ba8c64cb1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723544"
---
# <a name="iclrdebuggingopenvirtualprocess-method"></a><span data-ttu-id="63571-102">ICLRDebugging::OpenVirtualProcess 메서드</span><span class="sxs-lookup"><span data-stu-id="63571-102">ICLRDebugging::OpenVirtualProcess Method</span></span>

<span data-ttu-id="63571-103">프로세스에 로드 된 CLR (공용 언어 런타임) 모듈에 해당 하는 ICorDebugProcess 인터페이스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="63571-103">Gets the ICorDebugProcess interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63571-104">구문</span><span class="sxs-lookup"><span data-stu-id="63571-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenVirtualProcess(  
    [in] ULONG64 moduleBaseAddress,  
    [in] IUnknown * pDataTarget,  
    [in] ICLRDebuggingLibraryProvider * pLibraryProvider,  
    [in] CLR_DEBUGGING_VERSION * pMaxDebuggerSupportedVersion,  
    [in] REFIID riidProcess,  
    [out, iid_is(riidProcess)] IUnknown ** ppProcess,  
    [in, out] CLR_DEBUGGING_VERSION * pVersion,  
    [out] CLR_DEBUGGING_PROCESS_FLAGS * pdwFlags);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63571-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="63571-105">Parameters</span></span>  

 `moduleBaseAddress`  
 <span data-ttu-id="63571-106">진행 대상 프로세스에 있는 모듈의 기본 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-106">[in] The base address of a module in the target process.</span></span> <span data-ttu-id="63571-107">지정 된 모듈이 CLR 모듈이 아닌 경우 COR_E_NOT_CLR 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63571-107">COR_E_NOT_CLR will be returned if the specified module is not a CLR module.</span></span>  
  
 `pDataTarget`  
 <span data-ttu-id="63571-108">진행 관리 되는 디버거가 프로세스 상태를 검사할 수 있도록 하는 데이터 대상 추상화입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-108">[in] A data target abstraction that allows the managed debugger to inspect process state.</span></span> <span data-ttu-id="63571-109">디버거는 [ICorDebugDataTarget](icordebugdatatarget-interface.md) 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63571-109">The debugger must implement the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface.</span></span> <span data-ttu-id="63571-110">디버깅 중인 CLR이 컴퓨터에 로컬로 설치 되지 않은 시나리오를 지원 하려면 [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) 인터페이스를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63571-110">You should implement the [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) interface to support scenarios where the CLR that is being debugged is not installed locally on the computer.</span></span>  
  
 `pLibraryProvider`  
 <span data-ttu-id="63571-111">진행 버전별 디버깅 라이브러리를 요청 시 배치 하 고 로드할 수 있도록 하는 라이브러리 공급자 콜백 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-111">[in] A library provider callback interface that allows version-specific debugging libraries to be located and loaded on demand.</span></span> <span data-ttu-id="63571-112">이 매개 변수는 또는가이 아닌 경우에만 필요 `ppProcess` `pFlags` `null` 합니다.</span><span class="sxs-lookup"><span data-stu-id="63571-112">This parameter is required only if `ppProcess` or `pFlags` is not `null`.</span></span>  
  
 `pMaxDebuggerSupportedVersion`  
 <span data-ttu-id="63571-113">진행 이 디버거가 디버그할 수 있는 가장 높은 버전의 CLR입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-113">[in] The highest version of the CLR that this debugger can debug.</span></span> <span data-ttu-id="63571-114">이 디버거를 지 원하는 최신 CLR 버전의 주 버전, 부 버전 및 빌드 버전을 지정 하 고 향후 현재 위치의 CLR 서비스 릴리스를 수용할 수 있도록 수정 번호를 65535으로 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="63571-114">You should specify the major, minor, and build versions from the latest CLR version this debugger supports, and set the revision number to 65535 to accommodate future in-place CLR servicing releases.</span></span>  
  
 `riidProcess`  
 <span data-ttu-id="63571-115">진행 검색할 ICorDebugProcess 인터페이스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-115">[in] The ID of the ICorDebugProcess interface to retrieve.</span></span> <span data-ttu-id="63571-116">현재 유일 하 게 허용 되는 값은 IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2 및 IID_CORDEBUGPROCESS입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-116">Currently, the only accepted values are IID_CORDEBUGPROCESS3, IID_CORDEBUGPROCESS2, and IID_CORDEBUGPROCESS.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="63571-117">제한이 로 식별 되는 COM 인터페이스에 대 한 포인터입니다 `riidProcess` .</span><span class="sxs-lookup"><span data-stu-id="63571-117">[out] A pointer to the COM interface that is identified by `riidProcess`.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="63571-118">[in, out] CLR의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-118">[in, out] The version of the CLR.</span></span> <span data-ttu-id="63571-119">입력 시이 값은 일 수 있습니다 `null` .</span><span class="sxs-lookup"><span data-stu-id="63571-119">On input, this value can be `null`.</span></span> <span data-ttu-id="63571-120">구조체의 필드를 [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) `wStructVersion` 0 (영)으로 초기화 해야 하는 CLR_DEBUGGING_VERSION 구조를 가리킬 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-120">It can also point to a [CLR_DEBUGGING_VERSION](clr-debugging-version-structure.md) structure, in which case the structure's `wStructVersion` field must be initialized to 0 (zero).</span></span>  
  
 <span data-ttu-id="63571-121">출력 시 반환 된 `CLR_DEBUGGING_VERSION` 구조체는 CLR의 버전 정보로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="63571-121">On output, the returned `CLR_DEBUGGING_VERSION` structure will be filled in with the version information for the CLR.</span></span>  
  
 `pdwFlags`  
 <span data-ttu-id="63571-122">제한이 지정 된 런타임에 대 한 정보 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-122">[out] Informational flags about the specified runtime.</span></span> <span data-ttu-id="63571-123">플래그에 대 한 설명은 [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="63571-123">See the [CLR_DEBUGGING_PROCESS_FLAGS](clr-debugging-process-flags-enumeration.md) topic for a description of the flags.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63571-124">반환 값</span><span class="sxs-lookup"><span data-stu-id="63571-124">Return Value</span></span>  

 <span data-ttu-id="63571-125">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="63571-125">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="63571-126">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63571-126">HRESULT</span></span>|<span data-ttu-id="63571-127">설명</span><span class="sxs-lookup"><span data-stu-id="63571-127">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63571-128">S_OK</span><span class="sxs-lookup"><span data-stu-id="63571-128">S_OK</span></span>|<span data-ttu-id="63571-129">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-129">The method completed successfully.</span></span>|  
|<span data-ttu-id="63571-130">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="63571-130">E_POINTER</span></span>|<span data-ttu-id="63571-131">`pDataTarget`이(가) `null`인 경우.</span><span class="sxs-lookup"><span data-stu-id="63571-131">`pDataTarget` is `null`.</span></span>|  
|<span data-ttu-id="63571-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span><span class="sxs-lookup"><span data-stu-id="63571-132">CORDBG_E_LIBRARY_PROVIDER_ERROR</span></span>|<span data-ttu-id="63571-133">[ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) 콜백에서 오류를 반환 하거나 올바른 핸들을 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-133">The [ICLRDebuggingLibraryProvider](iclrdebugginglibraryprovider-interface.md) callback returns an error or does not provide a valid handle.</span></span>|  
|<span data-ttu-id="63571-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="63571-134">CORDBG_E_MISSING_DATA_TARGET_INTERFACE</span></span>|<span data-ttu-id="63571-135">`pDataTarget` 는이 버전의 런타임에 필요한 데이터 대상 인터페이스를 구현 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-135">`pDataTarget` does not implement the required data target interfaces for this version of the runtime.</span></span>|  
|<span data-ttu-id="63571-136">CORDBG_E_NOT_CLR</span><span class="sxs-lookup"><span data-stu-id="63571-136">CORDBG_E_NOT_CLR</span></span>|<span data-ttu-id="63571-137">표시 된 모듈이 CLR 모듈이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="63571-137">The indicated module is not a CLR module.</span></span> <span data-ttu-id="63571-138">이 HRESULT는 메모리가 손상 되었거나, 모듈을 사용할 수 없거나, CLR 버전이 shim 버전 보다 이후 CLR 모듈을 검색할 수 없는 경우에도 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63571-138">This HRESULT is also returned when a CLR module cannot be detected because memory has been corrupted, the module is not available, or the CLR version is later than the shim version.</span></span>|  
|<span data-ttu-id="63571-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span><span class="sxs-lookup"><span data-stu-id="63571-139">CORDBG_E_UNSUPPORTED_DEBUGGING_MODEL</span></span>|<span data-ttu-id="63571-140">이 런타임 버전은이 디버깅 모델을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-140">This runtime version does not support this debugging model.</span></span> <span data-ttu-id="63571-141">현재 디버깅 모델은 .NET Framework 4 이전 CLR 버전에서 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-141">Currently, the debugging model is not supported by CLR versions before the .NET Framework 4.</span></span> <span data-ttu-id="63571-142">`pwszVersion`출력 매개 변수는이 오류가 발생 한 후에도 올바른 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63571-142">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="63571-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span><span class="sxs-lookup"><span data-stu-id="63571-143">CORDBG_E_UNSUPPORTED_FORWARD_COMPAT</span></span>|<span data-ttu-id="63571-144">CLR 버전이이 디버거가 지원 하기 위해 클레임 하는 버전 보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="63571-144">The version of the CLR is greater than the version this debugger claims to support.</span></span> <span data-ttu-id="63571-145">`pwszVersion`출력 매개 변수는이 오류가 발생 한 후에도 올바른 값으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="63571-145">The `pwszVersion` output parameter is still set to the correct value after this error.</span></span>|  
|<span data-ttu-id="63571-146">E_NO_INTERFACE</span><span class="sxs-lookup"><span data-stu-id="63571-146">E_NO_INTERFACE</span></span>|<span data-ttu-id="63571-147">`riidProcess`인터페이스를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="63571-147">The `riidProcess` interface is not available.</span></span>|  
|<span data-ttu-id="63571-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span><span class="sxs-lookup"><span data-stu-id="63571-148">CORDBG_E_UNSUPPORTED_VERSION_STRUCT</span></span>|<span data-ttu-id="63571-149">`CLR_DEBUGGING_VERSION`구조에에 대해 인식 되는 값이 없는 경우 `wStructVersion`</span><span class="sxs-lookup"><span data-stu-id="63571-149">The `CLR_DEBUGGING_VERSION` structure does not have a recognized value for `wStructVersion`.</span></span> <span data-ttu-id="63571-150">지금은 허용 되는 값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="63571-150">The only accepted value at this time is 0.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="63571-151">예외</span><span class="sxs-lookup"><span data-stu-id="63571-151">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="63571-152">설명</span><span class="sxs-lookup"><span data-stu-id="63571-152">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63571-153">요구 사항</span><span class="sxs-lookup"><span data-stu-id="63571-153">Requirements</span></span>  

 <span data-ttu-id="63571-154">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="63571-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63571-155">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63571-155">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63571-156">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63571-156">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63571-157">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63571-157">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63571-158">참조</span><span class="sxs-lookup"><span data-stu-id="63571-158">See also</span></span>

- [<span data-ttu-id="63571-159">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="63571-159">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="63571-160">디버깅</span><span class="sxs-lookup"><span data-stu-id="63571-160">Debugging</span></span>](index.md)
