---
description: '자세히 알아보기: ICorProfilerInfo10:: RequestReJITWithInliners 메서드'
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: da3434926b36408adfdee2171d56f23ba764f0eb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753265"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a><span data-ttu-id="5a36a-103">ICorProfilerInfo10:: RequestReJITWithInliners 메서드</span><span class="sxs-lookup"><span data-stu-id="5a36a-103">ICorProfilerInfo10::RequestReJITWithInliners Method</span></span>

<span data-ttu-id="5a36a-104">요청 된 메서드 뿐 아니라 요청 된 메서드의 모든 inliners ReJITs 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-104">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>

## <a name="syntax"></a><span data-ttu-id="5a36a-105">구문</span><span class="sxs-lookup"><span data-stu-id="5a36a-105">Syntax</span></span>

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a><span data-ttu-id="5a36a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="5a36a-106">Parameters</span></span>

- `dwRejitFlags`

  <span data-ttu-id="5a36a-107">\[in] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)의 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-107">\[in] A bitmask of [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md).</span></span>

- `cFunctions`

  <span data-ttu-id="5a36a-108">\[in] 다시 컴파일할 함수 수입니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-108">\[in] The number of functions to recompile.</span></span>

- `moduleIds`

  <span data-ttu-id="5a36a-109">\[in] 다시 `moduleId` `module` `methodDef` 컴파일할 함수를 식별 하는 (,) 쌍의 부분을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-109">\[in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

- `methodIds`

  <span data-ttu-id="5a36a-110">\[in] 다시 `methodId` `module` `methodDef` 컴파일할 함수를 식별 하는 (,) 쌍의 부분을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-110">\[in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be recompiled.</span></span>

## <a name="remarks"></a><span data-ttu-id="5a36a-111">설명</span><span class="sxs-lookup"><span data-stu-id="5a36a-111">Remarks</span></span>

<span data-ttu-id="5a36a-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) 는 인라인 메서드를 추적 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-112">[RequestReJIT](icorprofilerinfo4-requestrejit-method.md) does not do any tracking of inlined methods.</span></span> <span data-ttu-id="5a36a-113">프로파일러에서 인라인 된 `RequestReJIT` 메서드의 모든 인스턴스가 ReJITted 하는지 확인 하기 위해 인라인 처리를 차단 하거나 인라이닝을 추적 하 고 모든 inliners에 대해를 호출 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-113">The profiler was expected to either block inlining or track inlining and call `RequestReJIT` for all inliners to make sure every instance of an inlined method was ReJITted.</span></span> <span data-ttu-id="5a36a-114">프로파일러가 인라인을 모니터링 하기 위해 제공 되지 않으므로 ReJIT on attach에 문제가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-114">This poses a problem with ReJIT on attach, since the profiler is not present to monitor inlining.</span></span> <span data-ttu-id="5a36a-115">이 메서드를 호출 하 여 inliners의 전체 집합을 ReJITted 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a36a-115">This method can be called to guarantee that the full set of inliners will be ReJITted as well.</span></span>

## <a name="requirements"></a><span data-ttu-id="5a36a-116">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5a36a-116">Requirements</span></span>

<span data-ttu-id="5a36a-117">**플랫폼:** [.Net Core 지원 운영 체제](../../../core/install/windows.md?pivots=os-windows)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5a36a-117">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="5a36a-118">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5a36a-118">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5a36a-119">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a36a-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5a36a-120">**.Net 버전:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a36a-120">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5a36a-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5a36a-121">See also</span></span>

- [<span data-ttu-id="5a36a-122">ICorProfilerInfo10 인터페이스</span><span class="sxs-lookup"><span data-stu-id="5a36a-122">ICorProfilerInfo10 Interface</span></span>](icorprofilerinfo10-interface.md)
