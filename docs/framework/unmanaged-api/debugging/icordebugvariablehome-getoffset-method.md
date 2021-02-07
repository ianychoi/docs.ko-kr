---
description: '자세히 알아보기: ICorDebugVariableHome:: GetOffset 메서드'
title: 'ICorDebugVariableHome:: GetOffset 메서드'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 48b57856d2825dd2ea9328064a28783b4b36029b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728771"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="0df26-103">ICorDebugVariableHome:: GetOffset 메서드</span><span class="sxs-lookup"><span data-stu-id="0df26-103">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="0df26-104">변수에 대 한 기본 레지스터에서 오프셋을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="0df26-104">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df26-105">구문</span><span class="sxs-lookup"><span data-stu-id="0df26-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0df26-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0df26-106">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="0df26-107">제한이 기본 레지스터의 오프셋입니다.</span><span class="sxs-lookup"><span data-stu-id="0df26-107">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0df26-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="0df26-108">Return Value</span></span>  

 <span data-ttu-id="0df26-109">메서드는 다음 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="0df26-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="0df26-110">값</span><span class="sxs-lookup"><span data-stu-id="0df26-110">Value</span></span>|<span data-ttu-id="0df26-111">설명</span><span class="sxs-lookup"><span data-stu-id="0df26-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="0df26-112">변수가 등록 관련 메모리 위치에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0df26-112">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="0df26-113">변수가 등록 관련 메모리 위치에 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0df26-113">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0df26-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="0df26-114">Requirements</span></span>  

 <span data-ttu-id="0df26-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0df26-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df26-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0df26-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0df26-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df26-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df26-118">**.NET Framework 버전:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df26-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df26-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0df26-119">See also</span></span>

- [<span data-ttu-id="0df26-120">ICorDebugVariableHome 인터페이스</span><span class="sxs-lookup"><span data-stu-id="0df26-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
