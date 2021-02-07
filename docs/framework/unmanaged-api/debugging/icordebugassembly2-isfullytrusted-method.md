---
description: '자세히 알아보기: ICorDebugAssembly2:: IsFullyTrusted 메서드'
title: ICorDebugAssembly2::IsFullyTrusted 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: bc1c4d9a4fa84bac3469aafe8aaa061473e50413
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754110"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="73c6a-103">ICorDebugAssembly2::IsFullyTrusted 메서드</span><span class="sxs-lookup"><span data-stu-id="73c6a-103">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="73c6a-104">어셈블리에 런타임 보안 시스템에서 완전 신뢰를 부여 했는지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="73c6a-104">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73c6a-105">구문</span><span class="sxs-lookup"><span data-stu-id="73c6a-105">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73c6a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="73c6a-106">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="73c6a-107">[out] `true` 어셈블리에 런타임 보안 시스템에서 완전 신뢰가 부여 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="73c6a-107">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73c6a-108">설명</span><span class="sxs-lookup"><span data-stu-id="73c6a-108">Remarks</span></span>  

 <span data-ttu-id="73c6a-109">이 메서드는 어셈블리에 대 한 보안 정책이 아직 확인 되지 않은 경우 (즉, 어셈블리의 코드가 아직 실행 되지 않은 경우) CORDBG_E_NOTREADY HRESULT를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="73c6a-109">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73c6a-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="73c6a-110">Requirements</span></span>  

 <span data-ttu-id="73c6a-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="73c6a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73c6a-112">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73c6a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73c6a-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73c6a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73c6a-114">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73c6a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
