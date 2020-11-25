---
title: ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 메서드
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: b3af44ec-7d41-425b-aed9-0c4379e5cbe9
ms.openlocfilehash: 750d2a2d69c74e147c34c9c496079ee48ac04b42
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732543"
---
# <a name="icordebugprocess8enableexceptioncallbacksoutsideofmycode-method"></a><span data-ttu-id="a766c-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode 메서드</span><span class="sxs-lookup"><span data-stu-id="a766c-102">ICorDebugProcess8::EnableExceptionCallbacksOutsideOfMyCode Method</span></span>

<span data-ttu-id="a766c-103">[.NET Framework 4.6 이상 버전에서 지원 됨]</span><span class="sxs-lookup"><span data-stu-id="a766c-103">[Supported in the .NET Framework 4.6 and later versions]</span></span>  
  
 <span data-ttu-id="a766c-104">특정 형식의 [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) 예외 콜백을 사용 하거나 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="a766c-104">Enables or disables certain types of [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) exception callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a766c-105">구문</span><span class="sxs-lookup"><span data-stu-id="a766c-105">Syntax</span></span>  
  
```cpp
HRESULT EnableExceptionCallbacksOutsideOfMyCode(  
   [in] BOOL enableExceptionsOutsideOfJMC  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a766c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a766c-106">Parameters</span></span>  

 `enableExceptionsOutsideOfJMC`  
 <span data-ttu-id="a766c-107">[in]</span><span class="sxs-lookup"><span data-stu-id="a766c-107">[in]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a766c-108">설명</span><span class="sxs-lookup"><span data-stu-id="a766c-108">Remarks</span></span>  

 <span data-ttu-id="a766c-109">`enableExceptionsOutsideOfJMC`의 값이 `false`인 경우:</span><span class="sxs-lookup"><span data-stu-id="a766c-109">If the value of `enableExceptionsOutsideOfJMC` is `false`:</span></span>  
  
- <span data-ttu-id="a766c-110">DEBUG_EXCEPTION_FIRST_CHANCE 예외로 인해 디버거 콜백이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a766c-110">A DEBUG_EXCEPTION_FIRST_CHANCE exception will not result in a callback to the debugger.</span></span>  
  
- <span data-ttu-id="a766c-111">예외가 사용자 코드로 이스케이프되지 않는 경우(즉, 예외 출처에서 예외 처리기로의 경로에 JustMyCode 또는 JMC로 표시된 메서드가 없음) DEBUG_EXCEPTION_CATCH_HANDLER_FOUND 예외로 인해 디버거 콜백이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a766c-111">A DEBUG_EXCEPTION_CATCH_HANDLER_FOUND exception will not result in a callback to the debugger if the exception never escapes into user code (that is, the path from an exception origin to an exception handler has no methods marked as JustMyCode, or JMC).</span></span>  
  
 <span data-ttu-id="a766c-112">`enableExceptionsOutsideOfJMC` 의 기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="a766c-112">The default value of `enableExceptionsOutsideOfJMC` is `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a766c-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a766c-113">Requirements</span></span>  

 <span data-ttu-id="a766c-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a766c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a766c-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a766c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a766c-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a766c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a766c-117">**.NET Framework 버전:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a766c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a766c-118">참조</span><span class="sxs-lookup"><span data-stu-id="a766c-118">See also</span></span>

- [<span data-ttu-id="a766c-119">ICorDebugProcess8 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a766c-119">ICorDebugProcess8 Interface</span></span>](icordebugprocess8-interface.md)
- [<span data-ttu-id="a766c-120">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a766c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
