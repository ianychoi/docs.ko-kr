---
title: ICorDebugModule3 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 543a1a3c79b6cf3eb799da5844f35286dfa91940
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709559"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="7ba56-102">ICorDebugModule3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7ba56-102">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="7ba56-103">동적 모듈에 대한 기호 판독기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ba56-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba56-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ba56-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ba56-105">메서드</span><span class="sxs-lookup"><span data-stu-id="7ba56-105">Methods</span></span>  
  
|<span data-ttu-id="7ba56-106">메서드</span><span class="sxs-lookup"><span data-stu-id="7ba56-106">Method</span></span>|<span data-ttu-id="7ba56-107">설명</span><span class="sxs-lookup"><span data-stu-id="7ba56-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ba56-108">ICorDebugModule3::CreateReaderForInMemorySymbols 메서드</span><span class="sxs-lookup"><span data-stu-id="7ba56-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="7ba56-109">동적 모듈에 대 한 기호 판독기 (일반적으로 [ISymUnmanagedReader 인터페이스](../diagnostics/isymunmanagedreader-interface.md))를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7ba56-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba56-110">설명</span><span class="sxs-lookup"><span data-stu-id="7ba56-110">Remarks</span></span>  

 <span data-ttu-id="7ba56-111">이 인터페이스는 "ICorDebugModule" 및 "ICorDebugModule2" 인터페이스를 논리적으로 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="7ba56-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ba56-112">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7ba56-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ba56-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="7ba56-113">Requirements</span></span>  

 <span data-ttu-id="7ba56-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7ba56-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ba56-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ba56-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ba56-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ba56-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ba56-117">**.NET Framework 버전:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7ba56-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7ba56-118">참조</span><span class="sxs-lookup"><span data-stu-id="7ba56-118">See also</span></span>

- [<span data-ttu-id="7ba56-119">ICorDebugRemoteTarget 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7ba56-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="7ba56-120">ICorDebug 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7ba56-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="7ba56-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7ba56-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
