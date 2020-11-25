---
title: ICorProfilerFunctionEnum::Clone 메서드
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 092c3b328887b7d36ead77c64d31310b614b616a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707531"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="55f3d-102">ICorProfilerFunctionEnum::Clone 메서드</span><span class="sxs-lookup"><span data-stu-id="55f3d-102">ICorProfilerFunctionEnum::Clone Method</span></span>

<span data-ttu-id="55f3d-103">이 [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) 인터페이스의 복사본에 대 한 인터페이스 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="55f3d-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55f3d-104">구문</span><span class="sxs-lookup"><span data-stu-id="55f3d-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="55f3d-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="55f3d-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="55f3d-106">제한이 이 [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) 인터페이스의 복사본을 가리키는 인터페이스 포인터에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="55f3d-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="55f3d-107">열거자의 복사본은이 열거자와 별도로 고유한 열거형 상태를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f3d-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="55f3d-108">그러나 복사본의 초기 커서 위치는이 열거자의 현재 커서 위치와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="55f3d-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55f3d-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="55f3d-109">Requirements</span></span>  

 <span data-ttu-id="55f3d-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55f3d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55f3d-111">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="55f3d-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="55f3d-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55f3d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55f3d-113">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55f3d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55f3d-114">참조</span><span class="sxs-lookup"><span data-stu-id="55f3d-114">See also</span></span>

- [<span data-ttu-id="55f3d-115">ICorProfilerFunctionEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="55f3d-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="55f3d-116">프로파일링 인터페이스</span><span class="sxs-lookup"><span data-stu-id="55f3d-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
