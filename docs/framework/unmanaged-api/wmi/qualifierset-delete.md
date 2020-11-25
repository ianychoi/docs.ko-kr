---
title: QualifierSet_Delete 함수 (관리 되지 않는 API 참조)
description: QualifierSet_Delete 함수는 이름으로 한정자를 삭제 합니다.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 2000de77903c3dabb43116fa1700b4ed393aeb5a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721155"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="88c8a-103">QualifierSet_Delete 함수</span><span class="sxs-lookup"><span data-stu-id="88c8a-103">QualifierSet_Delete function</span></span>

<span data-ttu-id="88c8a-104">지정된 한정자를 이름으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="88c8a-105">구문</span><span class="sxs-lookup"><span data-stu-id="88c8a-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="88c8a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="88c8a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="88c8a-107">진행 이 매개 변수는 사용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="88c8a-108">`ptr` 진행 [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) 인스턴스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="88c8a-109">`wszName` 진행 삭제할 한정자의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="88c8a-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="88c8a-110">Return value</span></span>

<span data-ttu-id="88c8a-111">이 함수에서 반환 되는 다음 값은 *WbemCli* 헤더 파일에 정의 되어 있거나 코드에서 상수로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="88c8a-112">상수</span><span class="sxs-lookup"><span data-stu-id="88c8a-112">Constant</span></span>  |<span data-ttu-id="88c8a-113">값</span><span class="sxs-lookup"><span data-stu-id="88c8a-113">Value</span></span>  |<span data-ttu-id="88c8a-114">설명</span><span class="sxs-lookup"><span data-stu-id="88c8a-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="88c8a-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="88c8a-115">0x80041008</span></span> | <span data-ttu-id="88c8a-116">`wszName` 매개 변수가 잘못된 경우</span><span class="sxs-lookup"><span data-stu-id="88c8a-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="88c8a-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="88c8a-117">0x80041016</span></span> | <span data-ttu-id="88c8a-118">이 한정자를 삭제 하는 것은 잘못 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="88c8a-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="88c8a-119">0x80041002</span></span> | <span data-ttu-id="88c8a-120">지정 된 한정자를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="88c8a-121">0</span><span class="sxs-lookup"><span data-stu-id="88c8a-121">0</span></span> | <span data-ttu-id="88c8a-122">함수 호출에 성공 했습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="88c8a-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="88c8a-123">0x40002</span></span> | <span data-ttu-id="88c8a-124">로컬 재정의가 삭제 되었으며 부모 개체의 원래 한정자가 범위를 다시 시작 했습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="88c8a-125">설명</span><span class="sxs-lookup"><span data-stu-id="88c8a-125">Remarks</span></span>

<span data-ttu-id="88c8a-126">이 함수는 [IWbemQualifierSet::D e)](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) 메서드에 대 한 호출을 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="88c8a-127">한정자 전파 규칙으로 인해 특정 한정자는 다른 개체에서 상속 되 고 단순히 현재 클래스 또는 인스턴스에서 재정의 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="88c8a-128">이 경우 `QualifierSet_Delete` 메서드는 한정자를 원래 상속 된 값으로 다시 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="88c8a-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="88c8a-129">이 경우 함수는 상태 코드를 반환 합니다 `WBEM_S_RESET_TO_DEFAULT` .</span><span class="sxs-lookup"><span data-stu-id="88c8a-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="88c8a-130">요구 사항</span><span class="sxs-lookup"><span data-stu-id="88c8a-130">Requirements</span></span>  

 <span data-ttu-id="88c8a-131">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="88c8a-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88c8a-132">**헤더:** WMINet_Utils idl</span><span class="sxs-lookup"><span data-stu-id="88c8a-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="88c8a-133">**.NET Framework 버전:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88c8a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88c8a-134">참조</span><span class="sxs-lookup"><span data-stu-id="88c8a-134">See also</span></span>

- [<span data-ttu-id="88c8a-135">WMI 및 성능 카운터(관리되지 않는 API 참조)</span><span class="sxs-lookup"><span data-stu-id="88c8a-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
