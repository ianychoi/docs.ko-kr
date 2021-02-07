---
description: '다음에 대 한 자세한 정보: CorCallingConvention 열거형'
title: CorCallingConvention 열거형
ms.date: 03/30/2017
api_name:
- CorCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCallingConvention
helpviewer_keywords:
- CorCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 69156fbf-7219-43bf-b4b8-b13f1a2fcb86
topic_type:
- apiref
ms.openlocfilehash: 2e823fe3566ef7a54f759cd5debbbd7d5dcf3ceb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99678447"
---
# <a name="corcallingconvention-enumeration"></a><span data-ttu-id="b0dae-103">CorCallingConvention 열거형</span><span class="sxs-lookup"><span data-stu-id="b0dae-103">CorCallingConvention Enumeration</span></span>

<span data-ttu-id="b0dae-104">관리 코드에서 수행된 호출 규칙의 형식을 설명하는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-104">Contains values that describe the types of calling conventions that are made in managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0dae-105">구문</span><span class="sxs-lookup"><span data-stu-id="b0dae-105">Syntax</span></span>  
  
```cpp  
typedef enum CorCallingConvention  
{  
    IMAGE_CEE_CS_CALLCONV_DEFAULT       = 0x0,  
  
    IMAGE_CEE_CS_CALLCONV_VARARG        = 0x5,  
    IMAGE_CEE_CS_CALLCONV_FIELD         = 0x6,  
    IMAGE_CEE_CS_CALLCONV_LOCAL_SIG     = 0x7,  
    IMAGE_CEE_CS_CALLCONV_PROPERTY      = 0x8,  
    IMAGE_CEE_CS_CALLCONV_UNMGD         = 0x9,  
    IMAGE_CEE_CS_CALLCONV_GENERICINST   = 0xa,  
    IMAGE_CEE_CS_CALLCONV_NATIVEVARARG  = 0xb,  
    IMAGE_CEE_CS_CALLCONV_MAX           = 0xc,  
  
    IMAGE_CEE_CS_CALLCONV_MASK          = 0x0f,  
    IMAGE_CEE_CS_CALLCONV_HASTHIS       = 0x20,  
    IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS  = 0x40,  
    IMAGE_CEE_CS_CALLCONV_GENERIC       = 0x10  
  
} CorCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="b0dae-106">구성원</span><span class="sxs-lookup"><span data-stu-id="b0dae-106">Members</span></span>  
  
|<span data-ttu-id="b0dae-107">멤버</span><span class="sxs-lookup"><span data-stu-id="b0dae-107">Member</span></span>|<span data-ttu-id="b0dae-108">설명</span><span class="sxs-lookup"><span data-stu-id="b0dae-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_CS_CALLCONV_DEFAULT`|<span data-ttu-id="b0dae-109">기본 호출 규칙을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-109">Indicates a default calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_VARARG`|<span data-ttu-id="b0dae-110">메서드가 가변적인 개수의 매개 변수를 사용 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-110">Indicates that the method takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FIELD`|<span data-ttu-id="b0dae-111">필드에 대 한 호출 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-111">Indicates that the call is to a field.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_LOCAL_SIG`|<span data-ttu-id="b0dae-112">로컬 메서드에 대 한 호출 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-112">Indicates that the call is to a local method.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_PROPERTY`|<span data-ttu-id="b0dae-113">속성에 대 한 호출 임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-113">Indicates that the call is to a property.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_UNMGD`|<span data-ttu-id="b0dae-114">호출이 관리 되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-114">Indicates that the call is unmanaged.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERICINST`|<span data-ttu-id="b0dae-115">제네릭 메서드 인스턴스화를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-115">Indicates a generic method instantiation.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_NATIVEVARARG`|<span data-ttu-id="b0dae-116">가변 개수의 매개 변수를 사용 하는 메서드에 대 한 64 비트 PInvoke 호출을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-116">Indicates a 64-bit PInvoke call to a method that takes a variable number of parameters.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MAX`|<span data-ttu-id="b0dae-117">잘못 된 4 비트 값을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-117">Describes an invalid 4-bit value.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_MASK`|<span data-ttu-id="b0dae-118">호출 규칙이 아래쪽 4 비트로 설명 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-118">Indicates that the calling convention is described by the bottom four bits.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_HASTHIS`|<span data-ttu-id="b0dae-119">상위 비트가 매개 변수를 설명 함을 나타냅니다 `this` .</span><span class="sxs-lookup"><span data-stu-id="b0dae-119">Indicates that the top bit describes a `this` parameter.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_EXPLICITTHIS`|<span data-ttu-id="b0dae-120">`this`매개 변수가 시그니처에 명시적으로 설명 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-120">Indicates that a `this` parameter is explicitly described in the signature.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_GENERIC`|<span data-ttu-id="b0dae-121">명시적 개수의 형식 인수가 있는 제네릭 메서드 시그니처를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-121">Indicates a generic method signature with an explicit number of type arguments.</span></span> <span data-ttu-id="b0dae-122">이는 일반 매개 변수 개수 앞에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="b0dae-122">This precedes an ordinary parameter count.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0dae-123">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b0dae-123">Requirements</span></span>  

 <span data-ttu-id="b0dae-124">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b0dae-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0dae-125">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="b0dae-125">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b0dae-126">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0dae-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0dae-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0dae-127">See also</span></span>

- [<span data-ttu-id="b0dae-128">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="b0dae-128">Metadata Enumerations</span></span>](metadata-enumerations.md)
