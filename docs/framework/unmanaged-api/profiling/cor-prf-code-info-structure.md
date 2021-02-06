---
description: '다음에 대 한 자세한 정보: COR_PRF_CODE_INFO 구조체'
title: COR_PRF_CODE_INFO 구조체
ms.date: 03/30/2017
api_name:
- COR_PRF_CODE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_CODE_INFO
helpviewer_keywords:
- COR_PRF_CODE_INFO structure [.NET Framework profiling]
ms.assetid: cf30e27c-1f7e-43a2-ba1e-01e4137301db
topic_type:
- apiref
ms.openlocfilehash: 11eae032424a039cac1136c08409b5b4712e6db1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649249"
---
# <a name="cor_prf_code_info-structure"></a><span data-ttu-id="dedf6-103">COR_PRF_CODE_INFO 구조체</span><span class="sxs-lookup"><span data-stu-id="dedf6-103">COR_PRF_CODE_INFO Structure</span></span>

<span data-ttu-id="dedf6-104">메모리 내에 저장된 연속하는 네이티브 코드 블록 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dedf6-104">Represents one contiguous block of native code stored in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedf6-105">구문</span><span class="sxs-lookup"><span data-stu-id="dedf6-105">Syntax</span></span>  
  
```cpp  
typedef struct _COR_PRF_CODE_INFO {  
    UINT_PTR startAddress;  
    SIZE_T size;  
} COR_PRF_CODE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="dedf6-106">구성원</span><span class="sxs-lookup"><span data-stu-id="dedf6-106">Members</span></span>  
  
|<span data-ttu-id="dedf6-107">멤버</span><span class="sxs-lookup"><span data-stu-id="dedf6-107">Member</span></span>|<span data-ttu-id="dedf6-108">설명</span><span class="sxs-lookup"><span data-stu-id="dedf6-108">Description</span></span>|  
|------------|-----------------|  
|`startAddress`|<span data-ttu-id="dedf6-109">연속 된 코드 블록의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="dedf6-109">The starting address of the contiguous block of code.</span></span>|  
|`size`|<span data-ttu-id="dedf6-110">블록의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="dedf6-110">The size of the block.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dedf6-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="dedf6-111">Requirements</span></span>  

 <span data-ttu-id="dedf6-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dedf6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dedf6-113">**헤더:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="dedf6-113">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="dedf6-114">**라이브러리:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dedf6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dedf6-115">**.NET Framework 버전:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dedf6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedf6-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dedf6-116">See also</span></span>

- [<span data-ttu-id="dedf6-117">프로파일링 구조체</span><span class="sxs-lookup"><span data-stu-id="dedf6-117">Profiling Structures</span></span>](profiling-structures.md)
