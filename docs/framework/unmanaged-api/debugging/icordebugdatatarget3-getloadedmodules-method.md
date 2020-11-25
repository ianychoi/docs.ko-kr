---
title: ICorDebugDataTarget3::GetLoadedModules 메서드
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: efbada02b7a24e0a7ed613b86b8a4a1a0b5b051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713753"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="8ce86-102">ICorDebugDataTarget3::GetLoadedModules 메서드</span><span class="sxs-lookup"><span data-stu-id="8ce86-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="8ce86-103">지금까지 로드된 모듈 목록을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="8ce86-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce86-104">구문</span><span class="sxs-lookup"><span data-stu-id="8ce86-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ce86-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="8ce86-105">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="8ce86-106">[in] 정보가 요청된 모듈 수입니다.</span><span class="sxs-lookup"><span data-stu-id="8ce86-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="8ce86-107">[out] 정보가 반환된 모듈 수에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8ce86-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="8ce86-108">제한이 로드 된 모듈에 대 한 정보를 제공 하는 [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) 개체의 배열에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="8ce86-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce86-109">설명</span><span class="sxs-lookup"><span data-stu-id="8ce86-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8ce86-110">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ce86-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ce86-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8ce86-111">Requirements</span></span>  

 <span data-ttu-id="8ce86-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8ce86-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ce86-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8ce86-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8ce86-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ce86-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ce86-115">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ce86-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce86-116">참조</span><span class="sxs-lookup"><span data-stu-id="8ce86-116">See also</span></span>

- [<span data-ttu-id="8ce86-117">ICorDebugDataTarget3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8ce86-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="8ce86-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="8ce86-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
