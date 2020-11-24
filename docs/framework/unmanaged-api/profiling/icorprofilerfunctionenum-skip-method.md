---
title: ICorProfilerFunctionEnum::Skip 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: da578e02db0744b1f64c1d392844aa020721e784
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669261"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="bf912-102">ICorProfilerFunctionEnum::Skip 메서드</span><span class="sxs-lookup"><span data-stu-id="bf912-102">ICorProfilerFunctionEnum::Skip Method</span></span>

<span data-ttu-id="bf912-103">지정한 개수의 요소를 건너뛰도록 현재 위치에서 열거자의 커서를 진행합니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf912-104">구문</span><span class="sxs-lookup"><span data-stu-id="bf912-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf912-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bf912-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="bf912-106">진행 건너뛸 요소의 수입니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bf912-107">반환 값</span><span class="sxs-lookup"><span data-stu-id="bf912-107">Return Value</span></span>  

 <span data-ttu-id="bf912-108">이 메서드는 다음과 같은 특정 HRESULT뿐만 아니라 메서드 오류를 나타내는 HRESULT 오류도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="bf912-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bf912-109">HRESULT</span></span>|<span data-ttu-id="bf912-110">설명</span><span class="sxs-lookup"><span data-stu-id="bf912-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bf912-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="bf912-111">S_OK</span></span>|<span data-ttu-id="bf912-112">`celt` 요소를 건너뛰었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="bf912-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="bf912-113">S_FALSE</span></span>|<span data-ttu-id="bf912-114">요소 `celt` 수를 건너 뛰 었으 며 더 이상 요소가 없다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf912-115">설명</span><span class="sxs-lookup"><span data-stu-id="bf912-115">Remarks</span></span>  

 <span data-ttu-id="bf912-116">이 열거자 커서의 새 위치는 (현재 위치) + `celt` 입니다.</span><span class="sxs-lookup"><span data-stu-id="bf912-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf912-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bf912-117">Requirements</span></span>  

 <span data-ttu-id="bf912-118">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf912-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf912-119">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bf912-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bf912-120">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf912-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf912-121">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf912-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf912-122">참조</span><span class="sxs-lookup"><span data-stu-id="bf912-122">See also</span></span>

- [<span data-ttu-id="bf912-123">ICorProfilerFunctionEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bf912-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="bf912-124">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bf912-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
