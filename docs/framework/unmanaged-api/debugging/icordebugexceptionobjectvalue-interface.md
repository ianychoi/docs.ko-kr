---
title: ICorDebugExceptionObjectValue 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: 6a0c33799b2b2aaa48e3b18b7b4bb37643508bd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678885"
---
# <a name="icordebugexceptionobjectvalue-interface"></a><span data-ttu-id="3c712-102">ICorDebugExceptionObjectValue 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3c712-102">ICorDebugExceptionObjectValue Interface</span></span>

<span data-ttu-id="3c712-103">"ICorDebugObjectValue" 인터페이스를 확장 하 여 관리 되는 예외 개체의 스택 추적 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3c712-103">Extends the "ICorDebugObjectValue" interface to provide stack trace information from a managed exception object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c712-104">메서드</span><span class="sxs-lookup"><span data-stu-id="3c712-104">Methods</span></span>  
  
|<span data-ttu-id="3c712-105">메서드</span><span class="sxs-lookup"><span data-stu-id="3c712-105">Method</span></span>|<span data-ttu-id="3c712-106">설명</span><span class="sxs-lookup"><span data-stu-id="3c712-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c712-107">EnumerateExceptionCallStack 메서드</span><span class="sxs-lookup"><span data-stu-id="3c712-107">EnumerateExceptionCallStack Method</span></span>](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|<span data-ttu-id="3c712-108">예외 개체에 포함 된 호출 스택에 대 한 열거자를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="3c712-108">Gets an enumerator to the call stack embedded in an exception object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c712-109">설명</span><span class="sxs-lookup"><span data-stu-id="3c712-109">Remarks</span></span>  

 <span data-ttu-id="3c712-110">`QueryInterface`에서 파생 된 관리 되는 개체에 대 한 호출이 성공 합니다 <xref:System.Exception?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3c712-110">The call to `QueryInterface` will succeed for managed objects that derive from <xref:System.Exception?displayProperty=nameWithType>.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c712-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3c712-111">Requirements</span></span>  

 <span data-ttu-id="3c712-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3c712-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c712-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c712-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c712-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c712-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c712-115">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c712-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c712-116">참조</span><span class="sxs-lookup"><span data-stu-id="3c712-116">See also</span></span>

- [<span data-ttu-id="3c712-117">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3c712-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="3c712-118">디버깅</span><span class="sxs-lookup"><span data-stu-id="3c712-118">Debugging</span></span>](index.md)
