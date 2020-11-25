---
title: ICorDebugGuidToTypeEnum 인터페이스
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
ms.openlocfilehash: 149c5b09639c8809e736ade09566e7b1b530e3eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705717"
---
# <a name="icordebugguidtotypeenum-interface"></a><span data-ttu-id="ed0c5-102">ICorDebugGuidToTypeEnum 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ed0c5-102">ICorDebugGuidToTypeEnum Interface</span></span>

<span data-ttu-id="ed0c5-103">ICorDebugType 인스턴스로 표시 되는 Guid 집합과 해당 형식 간의 매핑을 정의 하는 열거자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0c5-103">Provides an enumerator that defines the mapping between a set of GUIDs and their corresponding types, which are represented by ICorDebugType instances.</span></span> <span data-ttu-id="ed0c5-104">이 인터페이스는 ICorDebugEnum 인터페이스의 메서드를 상속 합니다.</span><span class="sxs-lookup"><span data-stu-id="ed0c5-104">This interface inherits the methods from the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ed0c5-105">메서드</span><span class="sxs-lookup"><span data-stu-id="ed0c5-105">Methods</span></span>  
  
|<span data-ttu-id="ed0c5-106">메서드</span><span class="sxs-lookup"><span data-stu-id="ed0c5-106">Method</span></span>|<span data-ttu-id="ed0c5-107">설명</span><span class="sxs-lookup"><span data-stu-id="ed0c5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ed0c5-108">ICorDebugGuidToTypeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="ed0c5-108">ICorDebugGuidToTypeEnum::Next</span></span>](icordebugguidtotypeenum-next-method.md)|<span data-ttu-id="ed0c5-109">Guid를 형식 정보에 매핑하는 지정 된 수의 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 인스턴스를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="ed0c5-109">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed0c5-110">설명</span><span class="sxs-lookup"><span data-stu-id="ed0c5-110">Remarks</span></span>  

 <span data-ttu-id="ed0c5-111">`ICorDebugGuidToTypeEnum`인터페이스 개체는 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 메서드를 호출 하 여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed0c5-111">An `ICorDebugGuidToTypeEnum` interface object can be retrieved by calling the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span> <span data-ttu-id="ed0c5-112">디버거는이 인터페이스의 [다음](icordebugguidtotypeenum-next-method.md) 메서드를 호출 하 여 [ICorDebugAppDomain3:: GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) 메서드 호출에 사용 되는 응용 프로그램 도메인에 로드 된 Windows 런타임 형식의 관리 되는 표현에 대 한 매핑을 나타내는 [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) 개체를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ed0c5-112">A debugger can call this interface's [Next](icordebugguidtotypeenum-next-method.md) method to retrieve [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects that represent mappings of managed representations of Windows Runtime types loaded in the application domain used for the call to the [ICorDebugAppDomain3::GetCachedWinRTTypes](icordebugappdomain3-getcachedwinrttypes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed0c5-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ed0c5-113">Requirements</span></span>  

 <span data-ttu-id="ed0c5-114">**플랫폼:** Windows 런타임</span><span class="sxs-lookup"><span data-stu-id="ed0c5-114">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="ed0c5-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed0c5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed0c5-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed0c5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed0c5-117">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed0c5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed0c5-118">참조</span><span class="sxs-lookup"><span data-stu-id="ed0c5-118">See also</span></span>

- [<span data-ttu-id="ed0c5-119">디버깅 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ed0c5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
