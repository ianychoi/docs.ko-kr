---
title: COR_PRF_MISC 열거형
ms.date: 03/30/2017
api_name:
- COR_PRF_MISC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MISC
helpviewer_keywords:
- COR_PRF_MISC enumeration [.NET Framework profiling]
ms.assetid: 619bb5de-e309-48b6-a3af-32d935a0ff46
topic_type:
- apiref
ms.openlocfilehash: 5a3c820b52ae9376d769ea9956edc0b8553a1f88
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682174"
---
# <a name="cor_prf_misc-enumeration"></a><span data-ttu-id="89b7a-102">COR_PRF_MISC 열거형</span><span class="sxs-lookup"><span data-stu-id="89b7a-102">COR_PRF_MISC Enumeration</span></span>

<span data-ttu-id="89b7a-103">특수 식별자를 지정하는 상수 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="89b7a-103">Contains constant values that specify special identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b7a-104">구문</span><span class="sxs-lookup"><span data-stu-id="89b7a-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    PROFILER_PARENT_UNKNOWN = 0xFFFFFFFD,  
    PROFILER_GLOBAL_CLASS   = 0xFFFFFFFE,  
    PROFILER_GLOBAL_MODULE  = 0xFFFFFFFF  
} COR_PRF_MISC;  
```  
  
## <a name="members"></a><span data-ttu-id="89b7a-105">멤버</span><span class="sxs-lookup"><span data-stu-id="89b7a-105">Members</span></span>  
  
|<span data-ttu-id="89b7a-106">멤버</span><span class="sxs-lookup"><span data-stu-id="89b7a-106">Member</span></span>|<span data-ttu-id="89b7a-107">설명</span><span class="sxs-lookup"><span data-stu-id="89b7a-107">Description</span></span>|  
|------------|-----------------|  
|`PROFILER_PARENT_UNKNOWN`|<span data-ttu-id="89b7a-108">아직 어셈블리에 연결 되지 않은 모듈에 대해 [ICorProfilerInfo:: GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) 에서 사용 하는 기본 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="89b7a-108">The default identifier used by [ICorProfilerInfo::GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md) for a module that has not yet been attached to an assembly.</span></span>|  
|`PROFILER_GLOBAL_CLASS`|<span data-ttu-id="89b7a-109">클래스에 속하지 않는 전역 상수에 대 한 기본 클래스 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="89b7a-109">The default class identifier for global constants that do not belong to a class.</span></span>|  
|`PROFILER_GLOBAL_MODULE`|<span data-ttu-id="89b7a-110">모듈에 속하지 않는 전역 개체에 대 한 기본 모듈 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="89b7a-110">The default module identifier for global objects that do not belong to a module.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89b7a-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="89b7a-111">Requirements</span></span>  

 <span data-ttu-id="89b7a-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="89b7a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89b7a-113">**헤더:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="89b7a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="89b7a-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89b7a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89b7a-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89b7a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89b7a-116">참조</span><span class="sxs-lookup"><span data-stu-id="89b7a-116">See also</span></span>

- [<span data-ttu-id="89b7a-117">프로파일링 열거형</span><span class="sxs-lookup"><span data-stu-id="89b7a-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
