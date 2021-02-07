---
description: '자세히 알아보기: IMetaDataImport:: EnumCustomAttributes 메서드'
title: IMetaDataImport::EnumCustomAttributes 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
ms.openlocfilehash: 1c55ea4b72483e5dc30425172b95be7f77e8a62a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677589"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="aa8bf-103">IMetaDataImport::EnumCustomAttributes 메서드</span><span class="sxs-lookup"><span data-stu-id="aa8bf-103">IMetaDataImport::EnumCustomAttributes Method</span></span>

<span data-ttu-id="aa8bf-104">지정 된 형식 또는 멤버와 연결 된 사용자 지정 특성 정의 토큰을 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-104">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa8bf-105">구문</span><span class="sxs-lookup"><span data-stu-id="aa8bf-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,
   [in]  mdToken            tkType,
   [out] mdCustomAttribute  rCustomAttributes[],
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa8bf-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="aa8bf-106">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="aa8bf-107">[in, out] 반환 된 열거자에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-107">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="aa8bf-108">진행 열거형의 범위에 대 한 토큰 이거나 모든 사용자 지정 특성의 경우 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-108">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="aa8bf-109">진행 열거할 특성 형식의 생성자 또는 모든 형식에 대 한 토큰입니다 `null` .</span><span class="sxs-lookup"><span data-stu-id="aa8bf-109">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="aa8bf-110">제한이 사용자 지정 특성 토큰의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-110">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="aa8bf-111">[in] `rCustomAttributes` 배열의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-111">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="aa8bf-112">[out, 선택 사항] 에서 반환 된 실제 토큰 값 수입니다 `rCustomAttributes` .</span><span class="sxs-lookup"><span data-stu-id="aa8bf-112">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa8bf-113">Return Value</span><span class="sxs-lookup"><span data-stu-id="aa8bf-113">Return Value</span></span>  
  
|<span data-ttu-id="aa8bf-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa8bf-114">HRESULT</span></span>|<span data-ttu-id="aa8bf-115">설명</span><span class="sxs-lookup"><span data-stu-id="aa8bf-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="aa8bf-116">`EnumCustomAttributes` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-116">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="aa8bf-117">열거할 사용자 지정 특성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-117">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="aa8bf-118">이 경우는 `pcCustomAttributes` 0입니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-118">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa8bf-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="aa8bf-119">Requirements</span></span>  

 <span data-ttu-id="aa8bf-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa8bf-121">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="aa8bf-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="aa8bf-122">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa8bf-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="aa8bf-123">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa8bf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa8bf-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="aa8bf-124">See also</span></span>

- [<span data-ttu-id="aa8bf-125">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa8bf-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="aa8bf-126">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="aa8bf-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
