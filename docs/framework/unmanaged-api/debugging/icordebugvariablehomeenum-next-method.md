---
title: 'ICorDebugVariableHomeEnum:: Next 메서드'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 4ef4ed19033b0857b9970ee8103bbd92f383898c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679535"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="ef8f3-102">ICorDebugVariableHomeEnum:: Next 메서드</span><span class="sxs-lookup"><span data-stu-id="ef8f3-102">ICorDebugVariableHomeEnum::Next Method</span></span>

<span data-ttu-id="ef8f3-103">함수의 지역 변수 및 인수에 대 한 정보를 포함 하는 지정 된 수의 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-103">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef8f3-104">구문</span><span class="sxs-lookup"><span data-stu-id="ef8f3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef8f3-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ef8f3-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="ef8f3-106">[in] 검색할 개체 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="ef8f3-107">각 포인터가 지역 변수 또는 함수의 인수에 대 한 정보를 제공 하는 [ICorDebugVariableHome](icordebugvariablehome-interface.md) 개체를 가리키는 포인터의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-107">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="ef8f3-108">제한이 개체에서 실제로 반환 되는 인스턴스 수입니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef8f3-109">반환 값</span><span class="sxs-lookup"><span data-stu-id="ef8f3-109">Return Value</span></span>  

 <span data-ttu-id="ef8f3-110">메서드는 다음 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="ef8f3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef8f3-111">HRESULT</span></span>|<span data-ttu-id="ef8f3-112">설명</span><span class="sxs-lookup"><span data-stu-id="ef8f3-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ef8f3-113">메서드가 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ef8f3-114">에 반영 된 대로 검색 된 인스턴스의 실제 수가 `pceltFetched` 요청 된 인스턴스 수보다 작은 경우</span><span class="sxs-lookup"><span data-stu-id="ef8f3-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef8f3-115">설명</span><span class="sxs-lookup"><span data-stu-id="ef8f3-115">Remarks</span></span>  

 <span data-ttu-id="ef8f3-116">[ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) 메서드는 `celt` 열거자의 현재 위치에서 시작 하 여 개체의 최대값을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-116">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="ef8f3-117">메서드가 반환 될 때 `pceltFetched` 검색 된 개체의 실제 수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef8f3-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ef8f3-118">Requirements</span></span>  

 <span data-ttu-id="ef8f3-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ef8f3-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef8f3-120">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef8f3-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef8f3-121">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef8f3-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef8f3-122">**.NET Framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef8f3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef8f3-123">참조</span><span class="sxs-lookup"><span data-stu-id="ef8f3-123">See also</span></span>

- [<span data-ttu-id="ef8f3-124">ICorDebugVariableHomeEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ef8f3-124">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="ef8f3-125">ICorDebugVariableHome 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ef8f3-125">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
