---
title: CorArgType 열거형
ms.date: 03/30/2017
api_name:
- CorArgType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorArgType
helpviewer_keywords:
- CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type:
- apiref
ms.openlocfilehash: 6388d804df43964866073d7c3b32dca84fb2d06f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720427"
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="93971-102">CorArgType 열거형</span><span class="sxs-lookup"><span data-stu-id="93971-102">CorArgType Enumeration</span></span>

<span data-ttu-id="93971-103">런타임 핸들의 네이티브 형식을 설명하는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="93971-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93971-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="93971-104">Syntax</span></span>  
  
```cpp  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="93971-105">요구 사항</span><span class="sxs-lookup"><span data-stu-id="93971-105">Requirements</span></span>  

 <span data-ttu-id="93971-106">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="93971-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93971-107">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="93971-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="93971-108">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93971-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93971-109">참조</span><span class="sxs-lookup"><span data-stu-id="93971-109">See also</span></span>

- [<span data-ttu-id="93971-110">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="93971-110">Metadata Enumerations</span></span>](metadata-enumerations.md)
