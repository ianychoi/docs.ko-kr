---
title: ICorProfilerInfo::GetModuleInfo 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 863fa1bf50830bb46e5c2939c99fe1e15897ac3d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724132"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="8a33b-102">ICorProfilerInfo::GetModuleInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="8a33b-102">ICorProfilerInfo::GetModuleInfo Method</span></span>

<span data-ttu-id="8a33b-103">모듈 ID가 지정된 경우 모듈의 파일 이름 및 모듈의 부모 어셈블리 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a33b-104">구문</span><span class="sxs-lookup"><span data-stu-id="8a33b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a33b-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8a33b-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="8a33b-106">[in] 정보가 검색되는 모듈의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="8a33b-107">[out] 모듈이 로드되는 기본 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="8a33b-108">[in] `szName` 반환 버퍼의 길이(문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8a33b-109">[out] 반환되는 모듈 파일 이름의 총 문자 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a33b-110">[out] 호출자가 제공한 와이드 문자 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="8a33b-111">메서드가 반환되면 이 버퍼에 모듈의 파일 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="8a33b-112">[out] 모듈의 부모 어셈블리 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a33b-113">설명</span><span class="sxs-lookup"><span data-stu-id="8a33b-113">Remarks</span></span>  

 <span data-ttu-id="8a33b-114">동적 모듈의 경우 `szName` 매개 변수는 빈 문자열이고 기본 주소는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="8a33b-115">`GetModuleInfo`모듈 id가 존재 하는 즉시 메서드를 호출할 수 있지만, 프로파일러가 [ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) 콜백을 받을 때까지 부모 어셈블리의 id를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="8a33b-116">`GetModuleInfo`가 반환된 후 `szName` 버퍼가 모듈의 전체 파일 이름을 포함하기에 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="8a33b-117">이렇게 하려면 `pcchName`가 가리키는 값을 `cchName` 매개 변수의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="8a33b-118">`pcchName`이 `cchName`보다 큰 값을 가리키는 경우 더 큰 `szName` 버퍼를 할당하고 `cchName`을 더 큰 새 크기로 업데이트한 후 `GetModuleInfo`를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="8a33b-119">또는 길이가 0인 `szName` 버퍼로 `GetModuleInfo`를 먼저 호출하여 올바른 버퍼 크기를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="8a33b-120">그런 다음 버퍼 크기를 `pcchName`에 반환된 값으로 설정하고 `GetModuleInfo`을 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8a33b-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a33b-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8a33b-121">Requirements</span></span>  

 <span data-ttu-id="8a33b-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a33b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a33b-123">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a33b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a33b-124">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a33b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a33b-125">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a33b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a33b-126">참조</span><span class="sxs-lookup"><span data-stu-id="8a33b-126">See also</span></span>

- [<span data-ttu-id="8a33b-127">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8a33b-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8a33b-128">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8a33b-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8a33b-129">프로파일링</span><span class="sxs-lookup"><span data-stu-id="8a33b-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="8a33b-130">GetModuleInfo2 메서드</span><span class="sxs-lookup"><span data-stu-id="8a33b-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
