---
title: CorDebugExceptionCallbackType 열거형
ms.date: 03/30/2017
api_name:
- CorDebugExceptionCallbackType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionCallbackType
helpviewer_keywords:
- CorDebugExceptionCallbackType enumeration [.NET Framework debugging]
ms.assetid: 4d946ad4-3c19-42cb-bec9-8633325ba769
topic_type:
- apiref
ms.openlocfilehash: cddcf66939a2ae7ab9e7f63a6fd61b72c56f6c7a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712731"
---
# <a name="cordebugexceptioncallbacktype-enumeration"></a><span data-ttu-id="1236d-102">CorDebugExceptionCallbackType 열거형</span><span class="sxs-lookup"><span data-stu-id="1236d-102">CorDebugExceptionCallbackType Enumeration</span></span>

<span data-ttu-id="1236d-103">[ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md) 이벤트에서 생성 된 콜백의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="1236d-103">Indicates the type of callback that is made from an [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md) event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1236d-104">구문</span><span class="sxs-lookup"><span data-stu-id="1236d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugExceptionCallbackType {  
    DEBUG_EXCEPTION_FIRST_CHANCE         = 1,  
    DEBUG_EXCEPTION_USER_FIRST_CHANCE    = 2,  
    DEBUG_EXCEPTION_CATCH_HANDLER_FOUND  = 3,  
    DEBUG_EXCEPTION_UNHANDLED            = 4  
} CorDebugExceptionCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="1236d-105">멤버</span><span class="sxs-lookup"><span data-stu-id="1236d-105">Members</span></span>  
  
|<span data-ttu-id="1236d-106">멤버</span><span class="sxs-lookup"><span data-stu-id="1236d-106">Member</span></span>|<span data-ttu-id="1236d-107">설명</span><span class="sxs-lookup"><span data-stu-id="1236d-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_FIRST_CHANCE`|<span data-ttu-id="1236d-108">예외가 throw 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1236d-108">An exception was thrown.</span></span>|  
|`DEBUG_EXCEPTION_USER_FIRST_CHANCE`|<span data-ttu-id="1236d-109">예외 windup 프로세스에서 사용자 코드를 입력 했습니다.</span><span class="sxs-lookup"><span data-stu-id="1236d-109">The exception windup process entered user code.</span></span>|  
|`DEBUG_EXCEPTION_CATCH_HANDLER_FOUND`|<span data-ttu-id="1236d-110">예외 windup 프로세스가 `catch` 사용자 코드에서 블록을 찾았습니다.</span><span class="sxs-lookup"><span data-stu-id="1236d-110">The exception windup process found a `catch` block in user code.</span></span>|  
|`DEBUG_EXCEPTION_UNHANDLED`|<span data-ttu-id="1236d-111">예외가 처리 되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="1236d-111">The exception was not handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1236d-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1236d-112">Requirements</span></span>  

 <span data-ttu-id="1236d-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1236d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1236d-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1236d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1236d-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1236d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1236d-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1236d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1236d-117">참조</span><span class="sxs-lookup"><span data-stu-id="1236d-117">See also</span></span>

- [<span data-ttu-id="1236d-118">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="1236d-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
