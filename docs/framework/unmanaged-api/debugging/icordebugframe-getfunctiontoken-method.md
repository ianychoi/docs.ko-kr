---
description: '자세히 알아보기: ICorDebugFrame:: GetFunctionToken 메서드'
title: ICorDebugFrame::GetFunctionToken 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunctionToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunctionToken
helpviewer_keywords:
- ICorDebugFrame::GetFunctionToken method [.NET Framework debugging]
- GetFunctionToken method [.NET Framework debugging]
ms.assetid: a46925b3-3bf8-404f-9f30-a86ae41032c1
topic_type:
- apiref
ms.openlocfilehash: c64bb8d59c8de03c3d8c667384ffe4118c996d8e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692942"
---
# <a name="icordebugframegetfunctiontoken-method"></a><span data-ttu-id="2682d-103">ICorDebugFrame::GetFunctionToken 메서드</span><span class="sxs-lookup"><span data-stu-id="2682d-103">ICorDebugFrame::GetFunctionToken Method</span></span>

<span data-ttu-id="2682d-104">이 스택 프레임과 연결 된 코드를 포함 하는 함수에 대 한 메타 데이터 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2682d-104">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2682d-105">구문</span><span class="sxs-lookup"><span data-stu-id="2682d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionToken (  
    [out] mdMethodDef        *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2682d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2682d-106">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="2682d-107">제한이 `mdMethodDef` 함수에 대 한 메타 데이터를 참조 하는 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2682d-107">[out] A pointer to an `mdMethodDef` token that references the metadata for the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2682d-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2682d-108">Requirements</span></span>  

 <span data-ttu-id="2682d-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2682d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2682d-110">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2682d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2682d-111">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2682d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2682d-112">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2682d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
