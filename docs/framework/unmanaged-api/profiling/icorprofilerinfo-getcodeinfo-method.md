---
title: ICorProfilerInfo::GetCodeInfo 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
ms.openlocfilehash: da3b0acefa68be3506567ad4742784943f4ec5ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722520"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="31f9c-102">ICorProfilerInfo::GetCodeInfo 메서드</span><span class="sxs-lookup"><span data-stu-id="31f9c-102">ICorProfilerInfo::GetCodeInfo Method</span></span>

<span data-ttu-id="31f9c-103">지정된 함수 ID와 연결된 네이티브 코드의 범위를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="31f9c-104">이 메서드는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-104">This method is obsolete.</span></span> <span data-ttu-id="31f9c-105">대신 [ICorProfilerInfo2:: GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) 메서드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f9c-106">구문</span><span class="sxs-lookup"><span data-stu-id="31f9c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f9c-107">매개 변수</span><span class="sxs-lookup"><span data-stu-id="31f9c-107">Parameters</span></span>  

 `functionId`  
 <span data-ttu-id="31f9c-108">[in] 네이티브 코드가 연결된 함수의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="31f9c-109">[out] 함수의 네이티브 코드를 구성하는 바이트 배열에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="31f9c-110">[out] 네이티브 코드의 크기(바이트)를 지정하는 정수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31f9c-111">설명</span><span class="sxs-lookup"><span data-stu-id="31f9c-111">Remarks</span></span>  

 <span data-ttu-id="31f9c-112">성능을 최적화하기 위해 .NET Framework 버전 2.0의 런타임은 함수의 미리 컴파일된 네이티브 코드를 여러 영역으로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="31f9c-113">결과적으로 `GetCodeInfo` 메서드는 함수의 네이티브 코드 범위를 처리할 수 없으므로 .NET Framework 2.0에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="31f9c-114">프로파일러가 보다 일반적인 `ICorProfilerInfo2::GetCodeInfo2` 메서드 사용으로 전환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="31f9c-115">이 함수는 호출자 할당 버퍼를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="31f9c-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f9c-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="31f9c-116">Requirements</span></span>  

 <span data-ttu-id="31f9c-117">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31f9c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f9c-118">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31f9c-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31f9c-119">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31f9c-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31f9c-120">**.NET Framework 버전:** 1.0</span><span class="sxs-lookup"><span data-stu-id="31f9c-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f9c-121">참조</span><span class="sxs-lookup"><span data-stu-id="31f9c-121">See also</span></span>

- [<span data-ttu-id="31f9c-122">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="31f9c-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="31f9c-123">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="31f9c-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="31f9c-124">프로파일링</span><span class="sxs-lookup"><span data-stu-id="31f9c-124">Profiling</span></span>](index.md)
