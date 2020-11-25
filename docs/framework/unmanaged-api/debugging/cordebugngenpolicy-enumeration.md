---
title: CorDebugNGenPolicy 열거형
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugNGenPolicy
helpviewer_keywords:
- CorDebugNgenPolicy enumeration [.NET Framework debugging]
ms.assetid: edb4e4d2-3166-44d4-8b17-bf302f7ea093
topic_type:
- apiref
ms.openlocfilehash: b64de0fa2ecbddd2decf69a4099d9897ec42a563
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696429"
---
# <a name="cordebugngenpolicy-enumeration"></a><span data-ttu-id="51c63-102">CorDebugNGenPolicy 열거형</span><span class="sxs-lookup"><span data-stu-id="51c63-102">CorDebugNGenPolicy Enumeration</span></span>

<span data-ttu-id="51c63-103">디버거가 네이티브 이미지 캐시에서 네이티브(NGen) 이미지를 로드하는지 여부를 결정하는 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51c63-103">Provides a value that determines whether a debugger loads native (NGen) images from the native image cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51c63-104">구문</span><span class="sxs-lookup"><span data-stu-id="51c63-104">Syntax</span></span>  
  
```cpp
enum CorDebugNGENPolicy {  
    DISABLE_LOCAL_NIC = 1  
} CorDebugNGENPolicy;  
```  
  
## <a name="members"></a><span data-ttu-id="51c63-105">멤버</span><span class="sxs-lookup"><span data-stu-id="51c63-105">Members</span></span>  
  
|<span data-ttu-id="51c63-106">멤버 이름</span><span class="sxs-lookup"><span data-stu-id="51c63-106">Member name</span></span>|<span data-ttu-id="51c63-107">설명</span><span class="sxs-lookup"><span data-stu-id="51c63-107">Description</span></span>|  
|-----------------|-----------------|  
|`DISABLE_LOCAL_NIC`|<span data-ttu-id="51c63-108">Windows 8.x 스토어 앱에서 로컬 네이티브 이미지 캐시의 이미지 사용은 사용 하지 않도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c63-108">In a Windows 8.x Store app, the use of images from the local native image cache is disabled.</span></span> <span data-ttu-id="51c63-109">데스크톱 앱에서는이 설정이 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51c63-109">In a desktop app, this setting has no effect.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="51c63-110">설명</span><span class="sxs-lookup"><span data-stu-id="51c63-110">Remarks</span></span>  

 <span data-ttu-id="51c63-111">`CorDebugNGENPolicy`열거형은 [ICorDebugProcess5:: EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) 메서드에서 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="51c63-111">The `CorDebugNGENPolicy` enumeration is used by the [ICorDebugProcess5::EnableNGENPolicy](icordebugprocess5-enablengenpolicy-method.md) method.</span></span> <span data-ttu-id="51c63-112">로컬 네이티브 이미지 캐시에서 이미지를 사용 하지 않도록 설정 하면 디버거가 최적화 된 네이티브 이미지 대신 디버깅 가능한 JIT 컴파일된 이미지를 로드 하 여 일관 된 디버깅 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="51c63-112">Disabling the use of images from the local native image cache provides for a consistent debugging experience by ensuring that the debugger loads debuggable JIT-compiled images instead of optimized native images.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51c63-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="51c63-113">Requirements</span></span>  

 <span data-ttu-id="51c63-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="51c63-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51c63-115">**헤더:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51c63-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51c63-116">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51c63-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51c63-117">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51c63-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51c63-118">참조</span><span class="sxs-lookup"><span data-stu-id="51c63-118">See also</span></span>

- [<span data-ttu-id="51c63-119">디버깅 열거형</span><span class="sxs-lookup"><span data-stu-id="51c63-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
