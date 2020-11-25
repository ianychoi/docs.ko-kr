---
title: CorFieldAttr 열거형
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: 4e40f684cc1578672cb8ff474972ce9cdc39efb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718828"
---
# <a name="corfieldattr-enumeration"></a><span data-ttu-id="60046-102">CorFieldAttr 열거형</span><span class="sxs-lookup"><span data-stu-id="60046-102">CorFieldAttr Enumeration</span></span>

<span data-ttu-id="60046-103">필드에 대한 메타데이터를 설명하는 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-103">Contains values that describe metadata about a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60046-104">구문</span><span class="sxs-lookup"><span data-stu-id="60046-104">Syntax</span></span>  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="60046-105">멤버</span><span class="sxs-lookup"><span data-stu-id="60046-105">Members</span></span>  
  
|<span data-ttu-id="60046-106">멤버</span><span class="sxs-lookup"><span data-stu-id="60046-106">Member</span></span>|<span data-ttu-id="60046-107">설명</span><span class="sxs-lookup"><span data-stu-id="60046-107">Description</span></span>|  
|------------|-----------------|  
|`fdFieldAccessMask`|<span data-ttu-id="60046-108">내게 필요한 옵션 정보를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-108">Specifies accessibility information.</span></span>|  
|`fdPrivateScope`|<span data-ttu-id="60046-109">필드를 참조할 수 없도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-109">Specifies that the field cannot be referenced.</span></span>|  
|`fdPrivate`|<span data-ttu-id="60046-110">부모 형식 에서만 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-110">Specifies that the field is accessible only by its parent type.</span></span>|  
|`fdFamANDAssem`|<span data-ttu-id="60046-111">해당 어셈블리의 파생 클래스에서 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-111">Specifies that the field is accessible by derived classes in its assembly.</span></span>|  
|`fdAssembly`|<span data-ttu-id="60046-112">해당 어셈블리의 모든 형식에서 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-112">Specifies that the field is accessible by all types in its assembly.</span></span>|  
|`fdFamily`|<span data-ttu-id="60046-113">해당 형식 및 파생 클래스만 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-113">Specifies that the field is accessible only by its type and derived classes.</span></span>|  
|`fdFamORAssem`|<span data-ttu-id="60046-114">파생 클래스와 해당 어셈블리의 모든 형식에서 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-114">Specifies that the field is accessible by derived classes and by all types in its assembly.</span></span>|  
|`fdPublic`|<span data-ttu-id="60046-115">이 범위를 표시 하는 모든 형식에서 필드에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-115">Specifies that the field is accessible by all types with visibility of this scope.</span></span>|  
|`fdStatic`|<span data-ttu-id="60046-116">필드가 인스턴스 멤버가 아니라 해당 형식의 멤버 임을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-116">Specifies that the field is a member of its type rather than an instance member.</span></span>|  
|`fdInitOnly`|<span data-ttu-id="60046-117">필드를 초기화 한 후에 변경할 수 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-117">Specifies that the field cannot be changed after it is initialized.</span></span>|  
|`fdLiteral`|<span data-ttu-id="60046-118">필드 값이 컴파일 타임 상수인 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-118">Specifies that the field value is a compile-time constant.</span></span>|  
|`fdNotSerialized`|<span data-ttu-id="60046-119">필드가 원격 형식이 면 필드가 serialize 되지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-119">Specifies that the field is not serialized when its type is remoted.</span></span>|  
|`fdSpecialName`|<span data-ttu-id="60046-120">필드를 특수 하 게 지정 하 고 해당 이름에서 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-120">Specifies that the field is special, and that its name describes how.</span></span>|  
|`fdPinvokeImpl`|<span data-ttu-id="60046-121">PInvoke를 통해 필드 구현이 전달 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-121">Specifies that the field implementation is forwarded through PInvoke.</span></span>|  
|`fdReservedMask`|<span data-ttu-id="60046-122">공용 언어 런타임에서 내부용으로 사용 하도록 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60046-122">Reserved for internal use by the common language runtime.</span></span>|  
|`fdRTSpecialName`|<span data-ttu-id="60046-123">공용 언어 런타임 메타 데이터 내부 Api가 이름의 인코딩을 확인 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-123">Specifies that the common language runtime metadata internal APIs should check the encoding of the name.</span></span>|  
|`fdHasFieldMarshal`|<span data-ttu-id="60046-124">필드에 마샬링 정보를 포함 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-124">Specifies that the field contains marshaling information.</span></span>|  
|`fdHasDefault`|<span data-ttu-id="60046-125">필드가 기본값을 갖도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-125">Specifies that the field has a default value.</span></span>|  
|`fdHasFieldRVA`|<span data-ttu-id="60046-126">필드에 상대 가상 주소를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="60046-126">Specifies that the field has a relative virtual address.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60046-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="60046-127">Requirements</span></span>  

 <span data-ttu-id="60046-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="60046-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60046-129">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="60046-129">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="60046-130">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60046-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60046-131">참조</span><span class="sxs-lookup"><span data-stu-id="60046-131">See also</span></span>

- [<span data-ttu-id="60046-132">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="60046-132">Metadata Enumerations</span></span>](metadata-enumerations.md)
