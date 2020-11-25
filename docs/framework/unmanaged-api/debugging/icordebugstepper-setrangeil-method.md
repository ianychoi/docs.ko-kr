---
title: ICorDebugStepper::SetRangeIL 메서드
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 5a27f155021661022b27022bbb252e00dfa67255
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698782"
---
# <a name="icordebugsteppersetrangeil-method"></a><span data-ttu-id="c94eb-102">ICorDebugStepper::SetRangeIL 메서드</span><span class="sxs-lookup"><span data-stu-id="c94eb-102">ICorDebugStepper::SetRangeIL Method</span></span>

<span data-ttu-id="c94eb-103">[ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) 에 대 한 호출이 단계별로 진행 중인 메서드의 MSIL (Microsoft 중간 언어) 코드에 상대적인 인수 값을 전달 하는지 아니면 네이티브 코드에 상대적인 인수 값을 전달 하는지 여부를 지정 하는 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94eb-103">Sets a value that specifies whether calls to [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) pass argument values that are relative to the native code or relative to Microsoft intermediate language (MSIL) code of the method that is being stepped through.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c94eb-104">구문</span><span class="sxs-lookup"><span data-stu-id="c94eb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c94eb-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c94eb-105">Parameters</span></span>  

 `bIL`  
 <span data-ttu-id="c94eb-106">진행 `true` 범위가 MSIL 코드를 기준으로 하도록 지정 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94eb-106">[in] Set to `true` to specify that the ranges are relative to the MSIL code.</span></span> <span data-ttu-id="c94eb-107">`false`범위가 네이티브 코드를 기준으로 하도록 지정 하려면로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c94eb-107">Set to `false` to specify that the ranges are relative to the native code.</span></span> <span data-ttu-id="c94eb-108">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="c94eb-108">The default value is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c94eb-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c94eb-109">Requirements</span></span>  

 <span data-ttu-id="c94eb-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c94eb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c94eb-111">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c94eb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c94eb-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c94eb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c94eb-113">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c94eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
