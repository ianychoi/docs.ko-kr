---
description: '자세히 알아보기: ICorDebugModule:: IsDynamic 메서드'
title: ICorDebugModule::IsDynamic 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 06ecb7aaffbe73da29bbdbba9446839db54c58c3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660104"
---
# <a name="icordebugmoduleisdynamic-method"></a><span data-ttu-id="6cafb-103">ICorDebugModule::IsDynamic 메서드</span><span class="sxs-lookup"><span data-stu-id="6cafb-103">ICorDebugModule::IsDynamic Method</span></span>

<span data-ttu-id="6cafb-104">이 모듈이 동적 모듈 인지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="6cafb-104">Gets a value that indicates whether this module is dynamic.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cafb-105">구문</span><span class="sxs-lookup"><span data-stu-id="6cafb-105">Syntax</span></span>  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cafb-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="6cafb-106">Parameters</span></span>  

 `pDynamic`  
 <span data-ttu-id="6cafb-107">[out] `true` 이 모듈이 동적 이면이 고, 그렇지 않으면입니다. 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="6cafb-107">[out] `true` if this module is dynamic; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cafb-108">설명</span><span class="sxs-lookup"><span data-stu-id="6cafb-108">Remarks</span></span>  

 <span data-ttu-id="6cafb-109">모듈이 로드 된 후에도 동적 모듈에서 새 클래스를 추가 하 고 기존 클래스를 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6cafb-109">A dynamic module can add new classes and delete existing classes even after the module has been loaded.</span></span> <span data-ttu-id="6cafb-110">[ICorDebugManagedCallback:: LoadClass](icordebugmanagedcallback-loadclass-method.md) 및 [ICorDebugManagedCallback:: UnloadClass](icordebugmanagedcallback-unloadclass-method.md) 콜백은 클래스가 추가 되거나 삭제 된 경우 디버거에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="6cafb-110">The [ICorDebugManagedCallback::LoadClass](icordebugmanagedcallback-loadclass-method.md) and [ICorDebugManagedCallback::UnloadClass](icordebugmanagedcallback-unloadclass-method.md) callbacks inform the debugger when a class has been added or deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cafb-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="6cafb-111">Requirements</span></span>  

 <span data-ttu-id="6cafb-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6cafb-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cafb-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6cafb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6cafb-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cafb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cafb-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cafb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
