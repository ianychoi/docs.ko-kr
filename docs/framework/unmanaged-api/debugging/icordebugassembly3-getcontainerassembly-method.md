---
description: '자세히 알아보기: ICorDebugAssembly3:: GetContainerAssembly 메서드'
title: ICorDebugAssembly3::GetContainerAssembly 메서드
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 5a6bc6dfb1c8403137a9444ff1cc4f64e75da65d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791519"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="ec0b8-103">ICorDebugAssembly3::GetContainerAssembly 메서드</span><span class="sxs-lookup"><span data-stu-id="ec0b8-103">ICorDebugAssembly3::GetContainerAssembly Method</span></span>

<span data-ttu-id="ec0b8-104">이 `ICorDebugAssembly3` 개체의 컨테이너 어셈블리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-104">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec0b8-105">구문</span><span class="sxs-lookup"><span data-stu-id="ec0b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec0b8-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ec0b8-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="ec0b8-107">컨테이너 어셈블리를 나타내는 ICorDebugAssembly 개체의 주소에 대 한 포인터 이거나, 메서드 호출이 실패할 경우 **null** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-107">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec0b8-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="ec0b8-108">Return Value</span></span>  

 <span data-ttu-id="ec0b8-109">`S_OK` 메서드 호출이 성공 하면이 고, 그렇지 않으면입니다. 그렇지 않으면, `S_FALSE` 및 `ppAssembly` 가 **null** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-109">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ec0b8-110">설명</span><span class="sxs-lookup"><span data-stu-id="ec0b8-110">Remarks</span></span>  

 <span data-ttu-id="ec0b8-111">이 어셈블리를 단일 컨테이너 어셈블리 내의 다른 어셈블리와 병합한 경우 이 메서드는 컨테이너 어셈블리를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-111">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="ec0b8-112">자세한 내용과 용어에 대 한 자세한 내용은 [ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-112">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec0b8-113">이 메서드는 .NET 네이티브에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec0b8-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ec0b8-114">Requirements</span></span>  

 <span data-ttu-id="ec0b8-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ec0b8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec0b8-116">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec0b8-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec0b8-117">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec0b8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec0b8-118">**.NET Framework 버전:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec0b8-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec0b8-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ec0b8-119">See also</span></span>

- [<span data-ttu-id="ec0b8-120">ICorDebugAssembly3 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ec0b8-120">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="ec0b8-121">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ec0b8-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
