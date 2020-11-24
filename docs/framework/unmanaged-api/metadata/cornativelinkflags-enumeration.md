---
title: CorNativeLinkFlags 열거형
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: ef9b177bee0651b6b8ea994610315ce93524e8e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676935"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="8a172-102">CorNativeLinkFlags 열거형</span><span class="sxs-lookup"><span data-stu-id="8a172-102">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="8a172-103">네이티브 코드를 연결할 때 링커에서 사용하는 플래그 값을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8a172-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a172-104">구문</span><span class="sxs-lookup"><span data-stu-id="8a172-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="8a172-105">멤버</span><span class="sxs-lookup"><span data-stu-id="8a172-105">Members</span></span>  
  
|<span data-ttu-id="8a172-106">멤버</span><span class="sxs-lookup"><span data-stu-id="8a172-106">Member</span></span>|<span data-ttu-id="8a172-107">설명</span><span class="sxs-lookup"><span data-stu-id="8a172-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="8a172-108">플래그가 없음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8a172-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="8a172-109">키워드를 나타냅니다 `setLastError` .</span><span class="sxs-lookup"><span data-stu-id="8a172-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="8a172-110">키워드를 나타냅니다 `nomangle` .</span><span class="sxs-lookup"><span data-stu-id="8a172-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="8a172-111">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8a172-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a172-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="8a172-112">Requirements</span></span>  

 <span data-ttu-id="8a172-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8a172-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a172-114">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="8a172-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a172-115">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="8a172-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a172-116">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a172-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a172-117">참조</span><span class="sxs-lookup"><span data-stu-id="8a172-117">See also</span></span>

- [<span data-ttu-id="8a172-118">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="8a172-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
