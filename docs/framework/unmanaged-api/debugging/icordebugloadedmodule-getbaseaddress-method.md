---
title: ICorDebugLoadedModule::GetBaseAddress 메서드
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 29153da86812583a0ea789da0c0816f08e0a6b43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698080"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="58dd5-102">ICorDebugLoadedModule::GetBaseAddress 메서드</span><span class="sxs-lookup"><span data-stu-id="58dd5-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="58dd5-103">로드된 모듈의 기본 주소를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="58dd5-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58dd5-104">구문</span><span class="sxs-lookup"><span data-stu-id="58dd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58dd5-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="58dd5-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="58dd5-106">[out] 로드된 모듈의 기본 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="58dd5-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58dd5-107">설명</span><span class="sxs-lookup"><span data-stu-id="58dd5-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58dd5-108">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58dd5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58dd5-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="58dd5-109">Requirements</span></span>  

 <span data-ttu-id="58dd5-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="58dd5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58dd5-111">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58dd5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58dd5-112">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58dd5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58dd5-113">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58dd5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58dd5-114">참조</span><span class="sxs-lookup"><span data-stu-id="58dd5-114">See also</span></span>

- [<span data-ttu-id="58dd5-115">ICorDebugLoadedModule 인터페이스</span><span class="sxs-lookup"><span data-stu-id="58dd5-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="58dd5-116">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="58dd5-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
