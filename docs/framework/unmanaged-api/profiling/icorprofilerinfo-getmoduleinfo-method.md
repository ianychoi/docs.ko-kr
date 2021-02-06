---
description: '자세히 알아보기: ICorProfilerInfo:: GetModuleInfo 메서드'
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
ms.openlocfilehash: 003f40e6637490be23e8bf87a6bac8ab76bc50e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647195"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="26bc4-103">ICorProfilerInfo::GetModuleInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="26bc4-103">ICorProfilerInfo::GetModuleInfo Method</span></span>

<span data-ttu-id="26bc4-104">모듈 ID가 지정된 경우 모듈의 파일 이름 및 모듈의 부모 어셈블리 ID를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-104">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26bc4-105">구문</span><span class="sxs-lookup"><span data-stu-id="26bc4-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="26bc4-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="26bc4-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="26bc4-107">[in] 정보가 검색되는 모듈의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-107">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="26bc4-108">[out] 모듈이 로드되는 기본 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-108">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="26bc4-109">[in] `szName` 반환 버퍼의 길이(문자)입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-109">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="26bc4-110">[out] 반환되는 모듈 파일 이름의 총 문자 길이에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-110">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="26bc4-111">[out] 호출자가 제공한 와이드 문자 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-111">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="26bc4-112">메서드가 반환되면 이 버퍼에 모듈의 파일 이름이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-112">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="26bc4-113">[out] 모듈의 부모 어셈블리 ID에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-113">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26bc4-114">설명</span><span class="sxs-lookup"><span data-stu-id="26bc4-114">Remarks</span></span>  

 <span data-ttu-id="26bc4-115">동적 모듈의 경우 `szName` 매개 변수는 빈 문자열이고 기본 주소는 0입니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-115">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="26bc4-116">`GetModuleInfo`모듈 id가 존재 하는 즉시 메서드를 호출할 수 있지만, 프로파일러가 [ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) 콜백을 받을 때까지 부모 어셈블리의 id를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-116">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="26bc4-117">`GetModuleInfo`가 반환된 후 `szName` 버퍼가 모듈의 전체 파일 이름을 포함하기에 충분히 큰지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-117">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="26bc4-118">이렇게 하려면 `pcchName`가 가리키는 값을 `cchName` 매개 변수의 값과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-118">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="26bc4-119">`pcchName`이 `cchName`보다 큰 값을 가리키는 경우 더 큰 `szName` 버퍼를 할당하고 `cchName`을 더 큰 새 크기로 업데이트한 후 `GetModuleInfo`를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-119">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="26bc4-120">또는 길이가 0인 `szName` 버퍼로 `GetModuleInfo`를 먼저 호출하여 올바른 버퍼 크기를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-120">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="26bc4-121">그런 다음 버퍼 크기를 `pcchName`에 반환된 값으로 설정하고 `GetModuleInfo`을 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="26bc4-121">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26bc4-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="26bc4-122">Requirements</span></span>  

 <span data-ttu-id="26bc4-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26bc4-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26bc4-124">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="26bc4-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26bc4-125">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26bc4-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26bc4-126">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26bc4-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26bc4-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26bc4-127">See also</span></span>

- [<span data-ttu-id="26bc4-128">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="26bc4-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="26bc4-129">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="26bc4-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="26bc4-130">프로파일링</span><span class="sxs-lookup"><span data-stu-id="26bc4-130">Profiling</span></span>](index.md)
- [<span data-ttu-id="26bc4-131">GetModuleInfo2 메서드</span><span class="sxs-lookup"><span data-stu-id="26bc4-131">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
