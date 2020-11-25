---
title: ICLRDebuggingLibraryProvider 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRDebuggingLibraryProvider
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebuggingLibraryProvider
helpviewer_keywords:
- ICLRDebuggingLibraryProvider interface [.NET Framework debugging]
ms.assetid: 67739617-6add-41a9-9de5-a3200c3109ce
topic_type:
- apiref
ms.openlocfilehash: cd17cbc808b7f8381ac320bb55999c6b0466c3d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723541"
---
# <a name="iclrdebugginglibraryprovider-interface"></a><span data-ttu-id="2bf49-102">ICLRDebuggingLibraryProvider 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2bf49-102">ICLRDebuggingLibraryProvider Interface</span></span>

<span data-ttu-id="2bf49-103">요청 시 공용 언어 런타임 버전별 디버깅 라이브러리를 찾고 로드 하는 데 사용할 수 있는 라이브러리 공급자 콜백 인터페이스를 가져오는 [ProvideLibrary method](iclrdebugginglibraryprovider-providelibrary-method.md) 메서드를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf49-103">Includes the [ProvideLibrary Method](iclrdebugginglibraryprovider-providelibrary-method.md) method, which gets a library provider callback interface that allows common language runtime version-specific debugging libraries to be located and loaded on demand.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2bf49-104">메서드</span><span class="sxs-lookup"><span data-stu-id="2bf49-104">Methods</span></span>  
  
|<span data-ttu-id="2bf49-105">메서드</span><span class="sxs-lookup"><span data-stu-id="2bf49-105">Method</span></span>|<span data-ttu-id="2bf49-106">설명</span><span class="sxs-lookup"><span data-stu-id="2bf49-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2bf49-107">ProvideLibrary 메서드</span><span class="sxs-lookup"><span data-stu-id="2bf49-107">ProvideLibrary Method</span></span>](iclrdebugginglibraryprovider-providelibrary-method.md)|<span data-ttu-id="2bf49-108">디버거가 디버그 라이브러리를 로드 하는 데 사용할 수 있는 모듈에 대 한 핸들을 제공할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="2bf49-108">Allows the debugger to provide a handle to a module which can be used to load a debug library.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2bf49-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2bf49-109">Requirements</span></span>  

 <span data-ttu-id="2bf49-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2bf49-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf49-111">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bf49-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bf49-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bf49-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bf49-113">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf49-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf49-114">참조</span><span class="sxs-lookup"><span data-stu-id="2bf49-114">See also</span></span>

- [<span data-ttu-id="2bf49-115">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2bf49-115">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2bf49-116">디버깅</span><span class="sxs-lookup"><span data-stu-id="2bf49-116">Debugging</span></span>](index.md)
