---
title: ICorProfilerInfo2::GetRVAStaticAddress 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: ea4f6f129cf2919124b1bef1fd837f2b1e13760e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727057"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="c698c-102">ICorProfilerInfo2::GetRVAStaticAddress 메서드</span><span class="sxs-lookup"><span data-stu-id="c698c-102">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="c698c-103">지정 된 RVA (상대 가상 주소) 정적 필드의 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-103">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c698c-104">구문</span><span class="sxs-lookup"><span data-stu-id="c698c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c698c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c698c-105">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="c698c-106">진행 요청 된 RVA 정적 필드를 포함 하는 클래스의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-106">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="c698c-107">진행 요청 된 RVA-정적 필드에 대 한 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-107">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="c698c-108">제한이 RVA 정적 필드의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-108">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c698c-109">설명</span><span class="sxs-lookup"><span data-stu-id="c698c-109">Remarks</span></span>  

 <span data-ttu-id="c698c-110">`GetRVAStaticAddress`메서드는 다음 중 하나를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-110">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="c698c-111">지정 된 컨텍스트에서 지정 된 정적 필드에 주소가 할당 되지 않은 경우 HRESULT CORPROF_E_DATAINCOMPLETE입니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-111">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="c698c-112">가비지 컬렉션 힙에 있을 수 있는 개체의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-112">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="c698c-113">이러한 주소는 가비지 수집 후에 무효화 될 수 있으므로 가비지 수집 후 프로파일러는 이러한 주소를 유효한 것으로 가정 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-113">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="c698c-114">클래스의 클래스 생성자가 완료 되기 전에는 `GetRVAStaticAddress` 모든 정적 필드에 대 한 CORPROF_E_DATAINCOMPLETE를 반환 하지만, 일부 정적 필드는 이미 초기화 되어 가비지 수집 개체를 루 팅 하 고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c698c-114">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c698c-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c698c-115">Requirements</span></span>  

 <span data-ttu-id="c698c-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c698c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c698c-117">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c698c-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c698c-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c698c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c698c-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c698c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c698c-120">참조</span><span class="sxs-lookup"><span data-stu-id="c698c-120">See also</span></span>

- [<span data-ttu-id="c698c-121">ICorProfilerInfo 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c698c-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="c698c-122">ICorProfilerInfo2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c698c-122">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
