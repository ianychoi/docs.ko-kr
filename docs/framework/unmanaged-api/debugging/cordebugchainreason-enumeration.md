---
description: '자세히 알아보기: CorDebugChainReason 열거형'
title: CorDebugChainReason 열거형
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
ms.openlocfilehash: 18b6ac9c50c3a44a77a0f63a680b84c70e667e9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801750"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="01f2a-103">CorDebugChainReason 열거형</span><span class="sxs-lookup"><span data-stu-id="01f2a-103">CorDebugChainReason Enumeration</span></span>

<span data-ttu-id="01f2a-104">호출 체인의 시작 이유를 하나 이상 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-104">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f2a-105">구문</span><span class="sxs-lookup"><span data-stu-id="01f2a-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="01f2a-106">구성원</span><span class="sxs-lookup"><span data-stu-id="01f2a-106">Members</span></span>  
  
|<span data-ttu-id="01f2a-107">멤버</span><span class="sxs-lookup"><span data-stu-id="01f2a-107">Member</span></span>|<span data-ttu-id="01f2a-108">설명</span><span class="sxs-lookup"><span data-stu-id="01f2a-108">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="01f2a-109">호출 체인이 시작되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-109">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="01f2a-110">생성자를 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-110">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="01f2a-111">예외 필터를 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-111">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="01f2a-112">보안을 적용하는 코드를 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-112">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="01f2a-113">컨텍스트 정책을 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-113">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="01f2a-114">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-114">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="01f2a-115">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-115">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="01f2a-116">스레드 실행 시작을 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-116">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="01f2a-117">관리 코드에 대한 입력을 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-117">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="01f2a-118">비관리 코드에 대한 입력을 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-118">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="01f2a-119">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-119">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="01f2a-120">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-120">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="01f2a-121">함수 평가를 통해 체인이 시작되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-121">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01f2a-122">설명</span><span class="sxs-lookup"><span data-stu-id="01f2a-122">Remarks</span></span>  

 <span data-ttu-id="01f2a-123">[ICorDebugChain:: GetReason](icordebugchain-getreason-method.md) 메서드를 사용 하 여 호출 체인을 시작 하는 이유를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="01f2a-123">Use the [ICorDebugChain::GetReason](icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f2a-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="01f2a-124">Requirements</span></span>  

 <span data-ttu-id="01f2a-125">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01f2a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f2a-126">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01f2a-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01f2a-127">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01f2a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f2a-128">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f2a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f2a-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="01f2a-129">See also</span></span>

- [<span data-ttu-id="01f2a-130">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="01f2a-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
