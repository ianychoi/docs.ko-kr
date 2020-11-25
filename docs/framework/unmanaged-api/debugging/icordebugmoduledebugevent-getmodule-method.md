---
title: ICorDebugModuleDebugEvent::GetModule Method
ms.date: 03/30/2017
ms.assetid: b1141c35-4253-4e34-b3e4-ed406a9dea4f
ms.openlocfilehash: ec23cda02ff689a3365fe96fb5280054a9795caa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709507"
---
# <a name="icordebugmoduledebugeventgetmodule-method"></a><span data-ttu-id="f367a-102">ICorDebugModuleDebugEvent::GetModule Method</span><span class="sxs-lookup"><span data-stu-id="f367a-102">ICorDebugModuleDebugEvent::GetModule Method</span></span>

<span data-ttu-id="f367a-103">방금 로드 또는 언로드된 병합된 모듈을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="f367a-103">Gets the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f367a-104">구문</span><span class="sxs-lookup"><span data-stu-id="f367a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule(  
   [out]ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f367a-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="f367a-105">Parameters</span></span>  

 `ppModule`  
 <span data-ttu-id="f367a-106">[out] 방금 로드 또는 언로드된 병합된 모듈을 나타내는 ICorDebugModule 개체의 주소에 대한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="f367a-106">[out] A pointer to the address of an ICorDebugModule object that represents the merged module that was just loaded or unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f367a-107">설명</span><span class="sxs-lookup"><span data-stu-id="f367a-107">Remarks</span></span>  

 <span data-ttu-id="f367a-108">[Geteventkind](icordebugdebugevent-geteventkind-method.md) 메서드를 호출 하 여 모듈이 로드 또는 언로드 되었는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367a-108">You can call the [GetEventKind](icordebugdebugevent-geteventkind-method.md) method to determine whether the module was loaded or unloaded.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f367a-109">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f367a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f367a-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="f367a-110">Requirements</span></span>  

 <span data-ttu-id="f367a-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f367a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f367a-112">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f367a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f367a-113">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f367a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f367a-114">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f367a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f367a-115">참조</span><span class="sxs-lookup"><span data-stu-id="f367a-115">See also</span></span>

- [<span data-ttu-id="f367a-116">ICorDebugModuleDebugEvent 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f367a-116">ICorDebugModuleDebugEvent Interface</span></span>](icordebugmoduledebugevent-interface.md)
- [<span data-ttu-id="f367a-117">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="f367a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
