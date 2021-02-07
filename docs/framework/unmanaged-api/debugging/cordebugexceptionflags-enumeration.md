---
description: '다음에 대 한 자세한 정보: CorDebugExceptionFlags 열거형'
title: CorDebugExceptionFlags 열거형
ms.date: 03/30/2017
api_name:
- CorDebugExceptionFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionFlags
helpviewer_keywords:
- CorDebugExceptionFlags enumeration [.NET Framework debugging]
ms.assetid: b22687a8-e9cf-4e65-a1b0-f92a81bc524e
topic_type:
- apiref
ms.openlocfilehash: c0036c2674f3202623da1a8fdeea14165a2a6e62
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747051"
---
# <a name="cordebugexceptionflags-enumeration"></a><span data-ttu-id="f4f7c-103">CorDebugExceptionFlags 열거형</span><span class="sxs-lookup"><span data-stu-id="f4f7c-103">CorDebugExceptionFlags Enumeration</span></span>

<span data-ttu-id="f4f7c-104">예외에 대한 추가 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-104">Provides additional information about an exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4f7c-105">구문</span><span class="sxs-lookup"><span data-stu-id="f4f7c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionFlags {  
    DEBUG_EXCEPTION_NONE = 0,  
    DEBUG_EXCEPTION_CAN_BE_INTERCEPTED = 0x0001  
} CorDebugExceptionFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="f4f7c-106">구성원</span><span class="sxs-lookup"><span data-stu-id="f4f7c-106">Members</span></span>  
  
|<span data-ttu-id="f4f7c-107">멤버</span><span class="sxs-lookup"><span data-stu-id="f4f7c-107">Member</span></span>|<span data-ttu-id="f4f7c-108">설명</span><span class="sxs-lookup"><span data-stu-id="f4f7c-108">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_NONE`|<span data-ttu-id="f4f7c-109">예외가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-109">There is no exception.</span></span>|  
|`DEBUG_EXCEPTION_CAN_BE_INTERCEPTED`|<span data-ttu-id="f4f7c-110">예외를 가로챌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-110">The exception is interceptable.</span></span><br /><br /> <span data-ttu-id="f4f7c-111">시간상 디버거가 아직 예외를 가로챌 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-111">The timing of the exception may still be such that the debugger cannot intercept it.</span></span> <span data-ttu-id="f4f7c-112">예를 들어 현재 콜백 아래에 관리 코드가 없거나 예외 이벤트가 JIT(Just-In-Time) 연결에서 발생한 경우에는 예외를 가로챌 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-112">For example, if there is no managed code below the current callback or the exception event resulted from a just-in-time (JIT) attachment, the exception cannot be intercepted.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4f7c-113">설명</span><span class="sxs-lookup"><span data-stu-id="f4f7c-113">Remarks</span></span>  

 <span data-ttu-id="f4f7c-114">이후 버전에서는 이 열거형에 대해 새 값이 추가될 수 있으므로 예기치 않은 값에 대해 `CorDebugExceptionFlags`를 사용하는 코드를 준비해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-114">New values may be added to this enumeration in later versions, so you should prepare code that uses `CorDebugExceptionFlags` for unexpected values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4f7c-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f4f7c-115">Requirements</span></span>  

 <span data-ttu-id="f4f7c-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f4f7c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4f7c-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f4f7c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f4f7c-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4f7c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f4f7c-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4f7c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f7c-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4f7c-120">See also</span></span>

- [<span data-ttu-id="f4f7c-121">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="f4f7c-121">Debugging Enumerations</span></span>](debugging-enumerations.md)
