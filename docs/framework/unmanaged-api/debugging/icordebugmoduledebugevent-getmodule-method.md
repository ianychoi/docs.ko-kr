---
description: '자세히 알아보기: ICorDebugModuleDebugEvent:: GetModule 메서드'
title: ICorDebugModuleDebugEvent::GetModule Method
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: c6d7171da231576ff90f54aaefe4b473af0afd40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790739"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="a8aa4-103">ICorDebugModuleDebugEvent::GetModule Method</span><span class="sxs-lookup"><span data-stu-id="a8aa4-103">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="a8aa4-104">방금 로드 또는 언로드된 병합된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a8aa4-104">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8aa4-105">구문</span><span class="sxs-lookup"><span data-stu-id="a8aa4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8aa4-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a8aa4-106">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="a8aa4-107">[out] 방금 로드 또는 언로드된 병합된 모듈을 나타내는 ICorDebugModule 개체의 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a8aa4-107">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8aa4-108">설명</span><span class="sxs-lookup"><span data-stu-id="a8aa4-108">Remarks</span></span>  

 <span data-ttu-id="a8aa4-109">[Geteventkind](icordebugdebugevent-geteventkind-method.md) 메서드를 호출 하 여 모듈이 로드 또는 언로드 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8aa4-109">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8aa4-110">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a8aa4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8aa4-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a8aa4-111">Requirements</span></span>  

 <span data-ttu-id="a8aa4-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a8aa4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8aa4-113">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8aa4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8aa4-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8aa4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8aa4-115">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8aa4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8aa4-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a8aa4-116">See also</span></span>

- [<span data-ttu-id="a8aa4-117">ICorDebugModuleDebugEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a8aa4-117">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="a8aa4-118">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a8aa4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
