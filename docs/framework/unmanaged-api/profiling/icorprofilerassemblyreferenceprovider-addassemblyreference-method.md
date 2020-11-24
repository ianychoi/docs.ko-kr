---
title: ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
ms.openlocfilehash: 56468fd38bc110318e04d9b1beda61e279f731d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685322"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="bc575-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference 메서드</span><span class="sxs-lookup"><span data-stu-id="bc575-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>

<span data-ttu-id="bc575-103">[.NET Framework 4.5.2 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="bc575-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="bc575-104">프로파일러가 [ICorProfilerCallback:: ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 콜백에서 추가할 어셈블리 참조의 CLR (공용 언어 런타임)에 대해 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bc575-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc575-105">구문</span><span class="sxs-lookup"><span data-stu-id="bc575-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc575-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="bc575-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="bc575-107">어셈블리 참조 클로저를 수행할 때 고려해 야 하는 어셈블리 참조에 대 한 정보를 CLR에 제공 하는 [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) 구조체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="bc575-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="bc575-108">설명</span><span class="sxs-lookup"><span data-stu-id="bc575-108">Remarks</span></span>  

 <span data-ttu-id="bc575-109">프로파일러는 `wszAssemblyPath` [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백의 인수에 지정 된 어셈블리에서 참조 하려는 각 대상 어셈블리에 대해이 메서드를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc575-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="bc575-110">[ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface 개체는 인수의 어셈블리 경로 및 이름과 함께 프로파일러의 [ICorProfilerCallback6:: getassemblyreferences](icorprofilercallback6-getassemblyreferences-method.md) 콜백으로 전달 됩니다 `wszAssemblyPath` .</span><span class="sxs-lookup"><span data-stu-id="bc575-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc575-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="bc575-111">Requirements</span></span>  

 <span data-ttu-id="bc575-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bc575-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc575-113">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bc575-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bc575-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc575-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc575-115">**.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc575-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc575-116">참조</span><span class="sxs-lookup"><span data-stu-id="bc575-116">See also</span></span>

- [<span data-ttu-id="bc575-117">ICorProfilerAssemblyReferenceProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="bc575-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="bc575-118">GetAssemblyReferences 메서드</span><span class="sxs-lookup"><span data-stu-id="bc575-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="bc575-119">ModuleLoadFinished 메서드</span><span class="sxs-lookup"><span data-stu-id="bc575-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
