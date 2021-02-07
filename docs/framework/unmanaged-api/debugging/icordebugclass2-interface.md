---
description: '자세히 알아보기: ICorDebugClass2 인터페이스'
title: ICorDebugClass2 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: 80aa8e59ccc774141e7fcea130d1fc6a38fa37da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711474"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="d74e1-103">ICorDebugClass2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d74e1-103">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="d74e1-104">제네릭 클래스나 <xref:System.Type> 형식의 메서드 매개 변수를 사용하는 클래스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d74e1-104">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="d74e1-105">이 인터페이스는 [ICorDebugClass](icordebugclass-interface.md)를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="d74e1-105">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d74e1-106">메서드</span><span class="sxs-lookup"><span data-stu-id="d74e1-106">Methods</span></span>  
  
|<span data-ttu-id="d74e1-107">메서드</span><span class="sxs-lookup"><span data-stu-id="d74e1-107">Method</span></span>|<span data-ttu-id="d74e1-108">설명</span><span class="sxs-lookup"><span data-stu-id="d74e1-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d74e1-109">GetParameterizedType 메서드</span><span class="sxs-lookup"><span data-stu-id="d74e1-109">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="d74e1-110">이 클래스에 대 한 형식 선언을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d74e1-110">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="d74e1-111">SetJMCStatus 메서드</span><span class="sxs-lookup"><span data-stu-id="d74e1-111">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="d74e1-112">이 클래스의 각 메서드에 대해 메서드가 사용자 정의 코드 인지 여부를 나타내는 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="d74e1-112">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d74e1-113">설명</span><span class="sxs-lookup"><span data-stu-id="d74e1-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d74e1-114">이 인터페이스는 크로스 시스템 또는 크로스 프로세스 원격 호출을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d74e1-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d74e1-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d74e1-115">Requirements</span></span>  

 <span data-ttu-id="d74e1-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d74e1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d74e1-117">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d74e1-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d74e1-118">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d74e1-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d74e1-119">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d74e1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d74e1-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d74e1-120">See also</span></span>

- [<span data-ttu-id="d74e1-121">ICorDebugClass 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d74e1-121">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="d74e1-122">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d74e1-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
