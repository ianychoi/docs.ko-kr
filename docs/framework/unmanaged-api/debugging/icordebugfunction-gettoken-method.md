---
description: '자세히 알아보기: ICorDebugFunction:: GetToken 메서드'
title: ICorDebugFunction::GetToken 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetToken
helpviewer_keywords:
- ICorDebugFunction::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: c6bbf479-062e-48e9-9c70-0f92e293e36a
topic_type:
- apiref
ms.openlocfilehash: 75c8680252c5047aa7263940da76166597e5a283
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692422"
---
# <a name="icordebugfunctiongettoken-method"></a><span data-ttu-id="dff86-103">ICorDebugFunction::GetToken 메서드</span><span class="sxs-lookup"><span data-stu-id="dff86-103">ICorDebugFunction::GetToken Method</span></span>

<span data-ttu-id="dff86-104">이 함수에 대 한 메타 데이터 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="dff86-104">Gets the metadata token for this function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dff86-105">구문</span><span class="sxs-lookup"><span data-stu-id="dff86-105">Syntax</span></span>  
  
```cpp  
HRESULT GetToken (  
    [out] mdMethodDef *pMethodDef  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dff86-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dff86-106">Parameters</span></span>  

 `pMethodDef`  
 <span data-ttu-id="dff86-107">제한이 `mdMethodDef` 이 함수에 대 한 메타 데이터를 참조 하는 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="dff86-107">[out] A pointer to an `mdMethodDef` token that references the metadata for this function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dff86-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dff86-108">Requirements</span></span>  

 <span data-ttu-id="dff86-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dff86-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dff86-110">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dff86-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dff86-111">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dff86-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dff86-112">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dff86-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
