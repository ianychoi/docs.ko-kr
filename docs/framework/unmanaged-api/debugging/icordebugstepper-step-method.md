---
description: '자세히 알아보기: ICorDebugStepper:: Step 메서드'
title: ICorDebugStepper::Step 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
ms.openlocfilehash: cb45575f7818784addf67eacda35442764e706af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717630"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="143ce-103">ICorDebugStepper::Step 메서드</span><span class="sxs-lookup"><span data-stu-id="143ce-103">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="143ce-104">이 ICorDebugStepper는 해당 스레드를 포함 하는 스레드를 한 단계씩 실행 하 고, 필요에 따라 스레드 내에서 호출 되는 함수를 통해 단일 단계를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="143ce-104">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="143ce-105">구문</span><span class="sxs-lookup"><span data-stu-id="143ce-105">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="143ce-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="143ce-106">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="143ce-107">진행 `true` 스레드 내에서 호출 되는 함수를 한 단계씩 실행 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="143ce-107">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="143ce-108">함수를 `false` 프로시저 단위로 실행 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="143ce-108">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="143ce-109">설명</span><span class="sxs-lookup"><span data-stu-id="143ce-109">Remarks</span></span>  

 <span data-ttu-id="143ce-110">공용 언어 런타임이이 스텝 퍼의 프레임에서 다음의 관리 되는 명령을 수행할 때 단계가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="143ce-110">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="143ce-111">`Step`관리 코드에 없는 스텝 퍼에 대해를 호출 하면 스레드에서 다음 관리 코드 명령이 실행 될 때 단계가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="143ce-111">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="143ce-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="143ce-112">Requirements</span></span>  

 <span data-ttu-id="143ce-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="143ce-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="143ce-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="143ce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="143ce-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="143ce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="143ce-116">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="143ce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
