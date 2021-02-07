---
description: '자세히 알아보기: CorDebugHandleType 열거형'
title: CorDebugHandleType 열거형
ms.date: 03/30/2017
api_name:
- CorDebugHandleType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugHandleType
helpviewer_keywords:
- CorDebugHandleType enumeration [.NET Framework debugging]
ms.assetid: 84296b55-c2c5-424c-ac9c-8e28e2895945
topic_type:
- apiref
ms.openlocfilehash: 294fd7b04018331489e51d12930bcbbb81ec340a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662119"
---
# <a name="cordebughandletype-enumeration"></a><span data-ttu-id="2c0b0-103">CorDebugHandleType 열거형</span><span class="sxs-lookup"><span data-stu-id="2c0b0-103">CorDebugHandleType Enumeration</span></span>

<span data-ttu-id="2c0b0-104">핸들 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-104">Indicates the handle type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c0b0-105">구문</span><span class="sxs-lookup"><span data-stu-id="2c0b0-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugHandleType {  
    HANDLE_STRONG                  = 1,  
    HANDLE_WEAK_TRACK_RESURRECTION = 2  
} CorDebugHandleType;  
```  
  
## <a name="members"></a><span data-ttu-id="2c0b0-106">구성원</span><span class="sxs-lookup"><span data-stu-id="2c0b0-106">Members</span></span>  
  
|<span data-ttu-id="2c0b0-107">멤버</span><span class="sxs-lookup"><span data-stu-id="2c0b0-107">Member</span></span>|<span data-ttu-id="2c0b0-108">설명</span><span class="sxs-lookup"><span data-stu-id="2c0b0-108">Description</span></span>|  
|------------|-----------------|  
|`HANDLE_STRONG`|<span data-ttu-id="2c0b0-109">핸들이 강력 하므로 가비지 수집에 의해 개체가 회수 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-109">The handle is strong, which prevents an object from being reclaimed by garbage collection.</span></span>|  
|`HANDLE_WEAK_TRACK_RESURRECTION`|<span data-ttu-id="2c0b0-110">핸들은 weak 이며 가비지 수집에 의해 개체가 회수 되는 것을 방지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-110">The handle is weak, which does not prevent an object from being reclaimed by garbage collection.</span></span><br /><br /> <span data-ttu-id="2c0b0-111">개체를 수집 하면 핸들이 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-111">The handle becomes invalid when the object is collected.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c0b0-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2c0b0-112">Requirements</span></span>  

 <span data-ttu-id="2c0b0-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0b0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c0b0-114">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c0b0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c0b0-115">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c0b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c0b0-116">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c0b0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c0b0-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c0b0-117">See also</span></span>

- [<span data-ttu-id="2c0b0-118">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="2c0b0-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
