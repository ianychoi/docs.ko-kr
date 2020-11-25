---
title: IMetaDataImport::GetInterfaceImplProps 메서드
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
ms.openlocfilehash: e81816ce2194c2c1862cb997ad2c6e5baf301231
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704005"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="c98d3-102">IMetaDataImport::GetInterfaceImplProps 메서드</span><span class="sxs-lookup"><span data-stu-id="c98d3-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>

<span data-ttu-id="c98d3-103"><xref:System.Type>지정 된 메서드를 구현 하는 및 해당 메서드를 선언 하는 인터페이스에 대 한 메타 데이터 토큰에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="c98d3-104">구문</span><span class="sxs-lookup"><span data-stu-id="c98d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c98d3-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c98d3-105">Parameters</span></span>  

 `iiImpl`  
 <span data-ttu-id="c98d3-106">진행 클래스 및 인터페이스 토큰을 반환할 메서드를 나타내는 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c98d3-107">제한이 메서드를 구현 하는 클래스를 나타내는 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="c98d3-108">제한이 구현 된 메서드를 정의 하는 인터페이스를 나타내는 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  

## <a name="remarks"></a><span data-ttu-id="c98d3-109">설명</span><span class="sxs-lookup"><span data-stu-id="c98d3-109">Remarks</span></span>

 <span data-ttu-id="c98d3-110">`iImpl` [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) 메서드를 호출 하 여의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-110">You obtain the value for `iImpl` by calling the [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) method.</span></span>

 <span data-ttu-id="c98d3-111">예를 들어, 클래스의 `mdTypeDef` 토큰 값이 0x02000007이 고 형식에 토큰이 있는 세 개의 인터페이스를 구현 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-111">For example, suppose that a class has an `mdTypeDef` token value of 0x02000007 and that it implements three interfaces whose types have tokens:</span></span>

- <span data-ttu-id="c98d3-112">0x02000003 (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="c98d3-112">0x02000003 (TypeDef)</span></span>
- <span data-ttu-id="c98d3-113">0x0100000A (TypeRef)</span><span class="sxs-lookup"><span data-stu-id="c98d3-113">0x0100000A (TypeRef)</span></span>
- <span data-ttu-id="c98d3-114">0x0200001C (TypeDef)</span><span class="sxs-lookup"><span data-stu-id="c98d3-114">0x0200001C (TypeDef)</span></span>

<span data-ttu-id="c98d3-115">개념적으로이 정보는 다음과 같이 인터페이스 구현 테이블에 저장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-115">Conceptually, this information is stored into an interface implementation table as:</span></span>

| <span data-ttu-id="c98d3-116">행 번호</span><span class="sxs-lookup"><span data-stu-id="c98d3-116">Row number</span></span> | <span data-ttu-id="c98d3-117">클래스 토큰</span><span class="sxs-lookup"><span data-stu-id="c98d3-117">Class token</span></span> | <span data-ttu-id="c98d3-118">인터페이스 토큰</span><span class="sxs-lookup"><span data-stu-id="c98d3-118">Interface token</span></span> |
|------------|-------------|-----------------|
| <span data-ttu-id="c98d3-119">4</span><span class="sxs-lookup"><span data-stu-id="c98d3-119">4</span></span>          |             |                 |
| <span data-ttu-id="c98d3-120">5</span><span class="sxs-lookup"><span data-stu-id="c98d3-120">5</span></span>          | <span data-ttu-id="c98d3-121">02000007</span><span class="sxs-lookup"><span data-stu-id="c98d3-121">02000007</span></span>    | <span data-ttu-id="c98d3-122">02000003</span><span class="sxs-lookup"><span data-stu-id="c98d3-122">02000003</span></span>        |
| <span data-ttu-id="c98d3-123">6</span><span class="sxs-lookup"><span data-stu-id="c98d3-123">6</span></span>          | <span data-ttu-id="c98d3-124">02000007</span><span class="sxs-lookup"><span data-stu-id="c98d3-124">02000007</span></span>    | <span data-ttu-id="c98d3-125">0100000A</span><span class="sxs-lookup"><span data-stu-id="c98d3-125">0100000A</span></span>        |
| <span data-ttu-id="c98d3-126">7</span><span class="sxs-lookup"><span data-stu-id="c98d3-126">7</span></span>          |             |                 |
| <span data-ttu-id="c98d3-127">8</span><span class="sxs-lookup"><span data-stu-id="c98d3-127">8</span></span>          | <span data-ttu-id="c98d3-128">02000007</span><span class="sxs-lookup"><span data-stu-id="c98d3-128">02000007</span></span>    | <span data-ttu-id="c98d3-129">0200001C</span><span class="sxs-lookup"><span data-stu-id="c98d3-129">0200001C</span></span>        |

<span data-ttu-id="c98d3-130">리콜, 토큰은 4 바이트 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-130">Recall, the token is a 4-byte value:</span></span>

- <span data-ttu-id="c98d3-131">하위 3 바이트는 행 번호 또는 RID를 보유 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-131">The lower 3 bytes hold the row number, or RID.</span></span>
- <span data-ttu-id="c98d3-132">상위 바이트는 토큰 유형 – 0x09를 보유 `mdtInterfaceImpl` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-132">The upper byte holds the token type – 0x09 for `mdtInterfaceImpl`.</span></span>

<span data-ttu-id="c98d3-133">`GetInterfaceImplProps` 인수에 제공 하는 토큰을 포함 하는 행에 저장 된 정보를 반환 합니다 `iImpl` .</span><span class="sxs-lookup"><span data-stu-id="c98d3-133">`GetInterfaceImplProps` returns the information held in the row whose token you provide in the `iImpl` argument.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="c98d3-134">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c98d3-134">Requirements</span></span>  

 <span data-ttu-id="c98d3-135">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c98d3-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c98d3-136">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="c98d3-136">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c98d3-137">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c98d3-137">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c98d3-138">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c98d3-138">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98d3-139">참조</span><span class="sxs-lookup"><span data-stu-id="c98d3-139">See also</span></span>

- [<span data-ttu-id="c98d3-140">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c98d3-140">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c98d3-141">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c98d3-141">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
