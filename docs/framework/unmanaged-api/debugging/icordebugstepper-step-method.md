---
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
ms.openlocfilehash: 234705e4495a1a582f3801ad1e645f923cd6f4b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727694"
---
# <a name="icordebugstepperstep-method"></a><span data-ttu-id="f0723-102">ICorDebugStepper::Step 메서드</span><span class="sxs-lookup"><span data-stu-id="f0723-102">ICorDebugStepper::Step Method</span></span>

<span data-ttu-id="f0723-103">이 ICorDebugStepper는 해당 스레드를 포함 하는 스레드를 한 단계씩 실행 하 고, 필요에 따라 스레드 내에서 호출 되는 함수를 통해 단일 단계를 계속 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0723-103">Causes this ICorDebugStepper to single-step through its containing thread, and optionally, to continue single-stepping through functions that are called within the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0723-104">구문</span><span class="sxs-lookup"><span data-stu-id="f0723-104">Syntax</span></span>  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0723-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f0723-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="f0723-106">진행 `true` 스레드 내에서 호출 되는 함수를 한 단계씩 실행 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0723-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="f0723-107">함수를 `false` 프로시저 단위로 실행 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0723-107">Set to `false` to step over the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0723-108">설명</span><span class="sxs-lookup"><span data-stu-id="f0723-108">Remarks</span></span>  

 <span data-ttu-id="f0723-109">공용 언어 런타임이이 스텝 퍼의 프레임에서 다음의 관리 되는 명령을 수행할 때 단계가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0723-109">The step completes when the common language runtime performs the next managed instruction in this stepper's frame.</span></span> <span data-ttu-id="f0723-110">`Step`관리 코드에 없는 스텝 퍼에 대해를 호출 하면 스레드에서 다음 관리 코드 명령이 실행 될 때 단계가 완료 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0723-110">If `Step` is called on a stepper, which is not in managed code, the step will complete when the next managed code instruction is executed by the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0723-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f0723-111">Requirements</span></span>  

 <span data-ttu-id="f0723-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0723-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0723-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0723-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0723-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0723-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0723-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0723-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
