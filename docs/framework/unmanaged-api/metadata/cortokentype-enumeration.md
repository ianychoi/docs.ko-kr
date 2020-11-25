---
title: CorTokenType 열거형
ms.date: 03/30/2017
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
ms.openlocfilehash: 70b28ab0ca73988093eadb9628142fecd9442948
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705477"
---
# <a name="cortokentype-enumeration"></a><span data-ttu-id="9945b-102">CorTokenType 열거형</span><span class="sxs-lookup"><span data-stu-id="9945b-102">CorTokenType Enumeration</span></span>

<span data-ttu-id="9945b-103">메타 데이터 토큰의 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-103">Indicates the type of a metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9945b-104">구문</span><span class="sxs-lookup"><span data-stu-id="9945b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a><span data-ttu-id="9945b-105">멤버</span><span class="sxs-lookup"><span data-stu-id="9945b-105">Members</span></span>  
  
|<span data-ttu-id="9945b-106">멤버</span><span class="sxs-lookup"><span data-stu-id="9945b-106">Member</span></span>|<span data-ttu-id="9945b-107">설명</span><span class="sxs-lookup"><span data-stu-id="9945b-107">Description</span></span>|  
|------------|-----------------|  
|`mdtModule`|<span data-ttu-id="9945b-108">`mdModule`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-108">An `mdModule` token.</span></span>|  
|`mdtTypeRef`|<span data-ttu-id="9945b-109">`mdTypeRef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-109">An `mdTypeRef` token.</span></span>|  
|`mdtTypeDef`|<span data-ttu-id="9945b-110">`mdTypeDef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-110">An `mdTypeDef` token.</span></span>|  
|`mdtFieldDef`|<span data-ttu-id="9945b-111">`mdFieldDef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-111">An `mdFieldDef` token.</span></span>|  
|`mdtMethodDef`|<span data-ttu-id="9945b-112">`mdMethodDef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-112">An `mdMethodDef` token.</span></span>|  
|`mdtParamDef`|<span data-ttu-id="9945b-113">`mdParamDef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-113">An `mdParamDef` token.</span></span>|  
|`mdtInterfaceImpl`|<span data-ttu-id="9945b-114">`mdInterfaceImpl`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-114">An `mdInterfaceImpl` token.</span></span>|  
|`mdtMemberRef`|<span data-ttu-id="9945b-115">`mdMemberRef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-115">An `mdMemberRef` token.</span></span>|  
|`mdtCustomAttribute`|<span data-ttu-id="9945b-116">`mdCustomAttribute`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-116">An `mdCustomAttribute` token.</span></span>|  
|`mdtPermission`|<span data-ttu-id="9945b-117">`mdPermission`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-117">An `mdPermission` token.</span></span>|  
|`mdtSignature`|<span data-ttu-id="9945b-118">`mdSignature`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-118">An `mdSignature` token.</span></span>|  
|`mdtEvent`|<span data-ttu-id="9945b-119">`mdEvent`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-119">An `mdEvent` token.</span></span>|  
|`mdtProperty`|<span data-ttu-id="9945b-120">`mdProperty`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-120">An `mdProperty` token.</span></span>|  
|`mdtModuleRef`|<span data-ttu-id="9945b-121">`mdModuleRef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-121">An `mdModuleRef` token.</span></span>|  
|`mdtTypeSpec`|<span data-ttu-id="9945b-122">`mdTypeSpec`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-122">An `mdTypeSpec` token.</span></span>|  
|`mdtAssembly`|<span data-ttu-id="9945b-123">`mdAssembly`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-123">An `mdAssembly` token.</span></span>|  
|`mdtAssemblyRef`|<span data-ttu-id="9945b-124">`mdAssemblyRef`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-124">An `mdAssemblyRef` token.</span></span>|  
|`mdtFile`|<span data-ttu-id="9945b-125">`mdFile`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-125">An `mdFile` token.</span></span>|  
|`mdtExportedType`|<span data-ttu-id="9945b-126">`mdExportedType`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-126">An `mdExportedType` token.</span></span>|  
|`mdtManifestResource`|<span data-ttu-id="9945b-127">`mdManifestResource`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-127">An `mdManifestResource` token.</span></span>|  
|`mdtGenericParam`|<span data-ttu-id="9945b-128">`mdGenericParam`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-128">An `mdGenericParam` token.</span></span>|  
|`mdtMethodSpec`|<span data-ttu-id="9945b-129">`mdMethodSpec`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-129">An `mdMethodSpec` token.</span></span>|  
|`mdtGenericParamConstraint`|<span data-ttu-id="9945b-130">`mdGenericParamConstraint`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-130">An `mdGenericParamConstraint` token.</span></span>|  
|`mdtString`|<span data-ttu-id="9945b-131">`mdString`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-131">An `mdString` token.</span></span>|  
|`mdtName`|<span data-ttu-id="9945b-132">`mdName`토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-132">An `mdName` token.</span></span>|  
|`mdtBaseType`|<span data-ttu-id="9945b-133">사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-133">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9945b-134">설명</span><span class="sxs-lookup"><span data-stu-id="9945b-134">Remarks</span></span>  

 <span data-ttu-id="9945b-135">각 값은 해당 하는 메타 데이터 토큰에서 최상위 바이트의 값과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9945b-135">Each value is equal to the value of the top byte in the corresponding metadata token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9945b-136">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9945b-136">Requirements</span></span>  

 <span data-ttu-id="9945b-137">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9945b-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9945b-138">**헤더:** CorHdr .h</span><span class="sxs-lookup"><span data-stu-id="9945b-138">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="9945b-139">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9945b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9945b-140">참조</span><span class="sxs-lookup"><span data-stu-id="9945b-140">See also</span></span>

- [<span data-ttu-id="9945b-141">메타데이터 열거형</span><span class="sxs-lookup"><span data-stu-id="9945b-141">Metadata Enumerations</span></span>](metadata-enumerations.md)
