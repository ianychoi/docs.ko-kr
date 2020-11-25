---
title: ICorDebugILFrame4::GetCodeEx 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: a88bb02626dc125c494e4bbe68bfe6ed8bfd3b7b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719647"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="8097c-102">ICorDebugILFrame4::GetCodeEx 메서드</span><span class="sxs-lookup"><span data-stu-id="8097c-102">ICorDebugILFrame4::GetCodeEx Method</span></span>

<span data-ttu-id="8097c-103">[.NET Framework 4.5.2 이상 버전에서 지원됨]</span><span class="sxs-lookup"><span data-stu-id="8097c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="8097c-104">이 스택 프레임에서 실행 중인 코드에 대한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-104">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8097c-105">구문</span><span class="sxs-lookup"><span data-stu-id="8097c-105">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8097c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8097c-106">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="8097c-107">진행 프로파일러에서 ReJIT 요청에 의해 정의 된 IL (중간 언어)이 프레임에 포함 되는지 여부를 지정 하는 [Ilcodekind](ilcodekind-enumeration.md) 열거형 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-107">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="8097c-108">제한이 이 스택 프레임이 실행 되는 코드를 나타내는 "ICorDebugCode" 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-108">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8097c-109">설명</span><span class="sxs-lookup"><span data-stu-id="8097c-109">Remarks</span></span>  

 <span data-ttu-id="8097c-110">이 메서드는 선택적으로 프로파일러의 ReJIT 요청으로 정의 된 코드에 액세스 한다는 점을 제외 하 고 [ICorDebugFrame:: GetCode](icordebugframe-getcode-method.md) 메서드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-110">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8097c-111">값을 사용 하 여이 메서드를 호출 `flags` `ILCODE_ORIGINAL_IL` 하는 것은 [getcode](icordebugframe-getcode-method.md)를 호출 하는 것과 같습니다. 메서드가 계측 되는 경우 해당 IL에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-111">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="8097c-112">`ILCODE_REJIT_IL`을 사용하는 경우 디버거가 프로파일러 ReJIT 요청에 의해 정의된 IL에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8097c-112">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="8097c-113">IL이 계측 되지 않는 경우 `ppCode` 가 **null** 이 고 메서드는를 반환 합니다 `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="8097c-113">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8097c-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8097c-114">Requirements</span></span>  

 <span data-ttu-id="8097c-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8097c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8097c-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8097c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8097c-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8097c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8097c-118">**.NET Framework 버전:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8097c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8097c-119">참조</span><span class="sxs-lookup"><span data-stu-id="8097c-119">See also</span></span>

- [<span data-ttu-id="8097c-120">ICorDebugILFrame4 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8097c-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="8097c-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8097c-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8097c-122">ReJIT: How-To 가이드</span><span class="sxs-lookup"><span data-stu-id="8097c-122">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
