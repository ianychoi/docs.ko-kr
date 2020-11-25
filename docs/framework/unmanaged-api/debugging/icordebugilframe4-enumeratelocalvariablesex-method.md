---
title: ICorDebugILFrame4::EnumerateLocalVariablesEx 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.EnumerateLocalVariablesEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6f60aae6-70ec-4c4c-963a-138df98c4668
topic_type:
- apiref
ms.openlocfilehash: 86a3b22851aa07a546cba5a0c0b69c81ec580cee
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724977"
---
# <a name="icordebugilframe4enumeratelocalvariablesex-method"></a><span data-ttu-id="75dd8-102">ICorDebugILFrame4::EnumerateLocalVariablesEx 메서드</span><span class="sxs-lookup"><span data-stu-id="75dd8-102">ICorDebugILFrame4::EnumerateLocalVariablesEx Method</span></span>

<span data-ttu-id="75dd8-103">[.NET Framework 4.5.2 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="75dd8-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="75dd8-104">프레임의 로컬 변수에 대한 열거자를 가져오고 필요에 따라 프로파일러 ReJIT 계측에 추가된 변수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-104">Gets an enumerator for the local variable in the frame, and optionally includes variables added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75dd8-105">구문</span><span class="sxs-lookup"><span data-stu-id="75dd8-105">Syntax</span></span>  
  
```cpp
HRESULT EnumerateLocalVariablesEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugValueEnum **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75dd8-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="75dd8-106">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="75dd8-107">진행 프로파일러 ReJIT 계측에 추가 된 변수가 프레임에 포함 되는지 여부를 지정 하는 [Ilcodekind](ilcodekind-enumeration.md) 열거형 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether variables added in profiler ReJIT instrumentation are included in the frame.</span></span>  
  
 `ppValueEnum`  
 <span data-ttu-id="75dd8-108">제한이 이 프레임에 있는 지역 변수의 열거자 인 "ICorDebugValueEnum" 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-108">[out] A pointer to the address of an "ICorDebugValueEnum" object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75dd8-109">설명</span><span class="sxs-lookup"><span data-stu-id="75dd8-109">Remarks</span></span>  

 <span data-ttu-id="75dd8-110">이 메서드는 선택적으로 profiler ReJIT 계측에 추가 된 변수에 액세스 한다는 점을 제외 하 고 [Enumeratelocalvariables](icordebugilframe-enumeratelocalvariables-method.md) 메서드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-110">This method is similar to the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md) method, except that it optionally accesses variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="75dd8-111">로 설정 하 `flags` `ILCODE_ORIGINAL_IL` 는 것은 [ICorDebugILFrame:: EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)를 호출 하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-111">Setting `flags` to `ILCODE_ORIGINAL_IL` is equivalent to calling [ICorDebugILFrame::EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md).</span></span> <span data-ttu-id="75dd8-112">`flags`을 `ILCODE_REJIT_IL`로 설정하면 디버거가 프로파일러 ReJIT 계측에 추가된 로컬 변수에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-112">Setting `flags` to `ILCODE_REJIT_IL` allows the debugger to access the local variables added in profiler ReJIT instrumentation.</span></span> <span data-ttu-id="75dd8-113">IL(중간 언어)이 계측되지 않는 경우 열거형은 비어 있으며 메서드는 `S_OK`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-113">If the intermediate language (IL) is not instrumented, the enumeration is empty and the method returns `S_OK`.</span></span>  
  
 <span data-ttu-id="75dd8-114">열거자는 실행 중인 메서드의 모든 로컬 변수를 포함하지 않을 수 있습니다. 이러한 변수 중 일부는 활성 상태가 아닐 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="75dd8-114">The enumerator may not include all of the local variables in the running method, since some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75dd8-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="75dd8-115">Requirements</span></span>  

 <span data-ttu-id="75dd8-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="75dd8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75dd8-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75dd8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75dd8-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75dd8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75dd8-119">**.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75dd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75dd8-120">참조</span><span class="sxs-lookup"><span data-stu-id="75dd8-120">See also</span></span>

- [<span data-ttu-id="75dd8-121">ICorDebugILFrame4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="75dd8-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="75dd8-122">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="75dd8-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="75dd8-123">ReJIT: How-To 가이드</span><span class="sxs-lookup"><span data-stu-id="75dd8-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
