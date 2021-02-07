---
description: '자세히 알아보기: ICorDebugEval:: GetThread 메서드'
title: ICorDebugEval::GetThread 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 3e7120f618abce31b9940a886fd6b2b2f8639d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694151"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="545df-103">ICorDebugEval::GetThread 메서드</span><span class="sxs-lookup"><span data-stu-id="545df-103">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="545df-104">이 계산이 실행 되거나 실행 될 스레드를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="545df-104">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="545df-105">구문</span><span class="sxs-lookup"><span data-stu-id="545df-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="545df-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="545df-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="545df-107">제한이 스레드를 나타내는 ICorDebugThread 개체의 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="545df-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="545df-108">요구 사항</span><span class="sxs-lookup"><span data-stu-id="545df-108">Requirements</span></span>  

 <span data-ttu-id="545df-109">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="545df-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="545df-110">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="545df-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="545df-111">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="545df-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="545df-112">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="545df-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
