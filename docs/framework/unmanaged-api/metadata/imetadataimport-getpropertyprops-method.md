---
description: '자세히 알아보기: IMetaDataImport:: GetPropertyProps 메서드'
title: IMetaDataImport::GetPropertyProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPropertyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPropertyProps
helpviewer_keywords:
- GetPropertyProps method [.NET Framework metadata]
- IMetaDataImport::GetPropertyProps method [.NET Framework metadata]
ms.assetid: dc0ff3e6-7e7d-4f6c-948d-52b28f5cb78c
topic_type:
- apiref
ms.openlocfilehash: 25fae4488117a35d94479ce501154679b6b536ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789179"
---
# <a name="imetadataimportgetpropertyprops-method"></a><span data-ttu-id="caf2a-103">IMetaDataImport::GetPropertyProps 메서드</span><span class="sxs-lookup"><span data-stu-id="caf2a-103">IMetaDataImport::GetPropertyProps Method</span></span>

<span data-ttu-id="caf2a-104">지정 된 토큰이 나타내는 속성의 메타 데이터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-104">Gets the metadata for the property represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="caf2a-105">구문</span><span class="sxs-lookup"><span data-stu-id="caf2a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPropertyProps (  
   [in]  mdProperty        prop,  
   [out] mdTypeDef         *pClass,
   [out] LPCWSTR           szProperty,
   [in]  ULONG             cchProperty,
   [out] ULONG             *pchProperty,
   [out] DWORD             *pdwPropFlags,
   [out] PCCOR_SIGNATURE   *ppvSig,
   [out] ULONG             *pbSig,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppDefaultValue,  
   [out] ULONG             *pcchDefaultValue,  
   [out] mdMethodDef       *pmdSetter,
   [out] mdMethodDef       *pmdGetter,
   [out] mdMethodDef       rmdOtherMethod[],  
   [in]  ULONG             cMax,
   [out] ULONG             *pcOtherMethod
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="caf2a-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="caf2a-106">Parameters</span></span>  

 `prop`  
 <span data-ttu-id="caf2a-107">진행 메타 데이터를 반환할 속성을 나타내는 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-107">[in] A token that represents the property to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="caf2a-108">제한이 속성을 구현 하는 형식을 나타내는 TypeDef 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-108">[out] A pointer to the TypeDef token that represents the type that implements the property.</span></span>  
  
 `szProperty`  
 <span data-ttu-id="caf2a-109">제한이 속성 이름을 보유할 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-109">[out] A buffer to hold the property name.</span></span>  
  
 `cchProperty`  
 <span data-ttu-id="caf2a-110">진행 의 와이드 문자 크기입니다 `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="caf2a-110">[in] The size in wide characters of `szProperty`.</span></span>  
  
 `pchProperty`  
 <span data-ttu-id="caf2a-111">제한이 에서 반환 되는 와이드 문자 수입니다 `szProperty` .</span><span class="sxs-lookup"><span data-stu-id="caf2a-111">[out] The number of wide characters returned in `szProperty`.</span></span>  
  
 `pdwPropFlags`  
 <span data-ttu-id="caf2a-112">제한이 속성에 적용 된 특성 플래그에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-112">[out] A pointer to any attribute flags applied to the property.</span></span> <span data-ttu-id="caf2a-113">이 값은 [Corpropertyattr](corpropertyattr-enumeration.md) 열거형의 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-113">This value is a bitmask from the [CorPropertyAttr](corpropertyattr-enumeration.md) enumeration.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="caf2a-114">제한이 속성의 메타 데이터 서명에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-114">[out] A pointer to the metadata signature of the property.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="caf2a-115">제한이 에서 반환 된 바이트 수입니다 `ppvSig` .</span><span class="sxs-lookup"><span data-stu-id="caf2a-115">[out] The number of bytes returned in `ppvSig`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="caf2a-116">제한이 속성의 기본값 인 상수의 형식을 지정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-116">[out] A flag specifying the type of the constant that is the default value of the property.</span></span> <span data-ttu-id="caf2a-117">이 값은 CorElementType 열거형에서 가져온 값입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-117">This value is from the CorElementType enumeration.</span></span>  
  
 `ppDefaultValue`  
 <span data-ttu-id="caf2a-118">제한이 이 속성의 기본값을 저장 하는 바이트에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-118">[out] A pointer to the bytes that store the default value for this property.</span></span>  
  
 `pcchDefaultValue`  
 <span data-ttu-id="caf2a-119">제한이 가 ELEMENT_TYPE_STRING 경우의 와이드 문자 크기 `ppDefaultValue` `pdwCPlusTypeFlag` 이 고, 그렇지 않으면이 값은 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-119">[out] The size in wide characters of `ppDefaultValue`, if `pdwCPlusTypeFlag` is ELEMENT_TYPE_STRING; otherwise, this value is not relevant.</span></span> <span data-ttu-id="caf2a-120">이 경우의 길이는에 `ppDefaultValue` 의해 지정 된 형식에서 유추 됩니다 `pdwCPlusTypeFlag` .</span><span class="sxs-lookup"><span data-stu-id="caf2a-120">In that case, the length of `ppDefaultValue` is inferred from the type that is specified by `pdwCPlusTypeFlag`.</span></span>  
  
 `pmdSetter`  
 <span data-ttu-id="caf2a-121">제한이 속성의 set 접근자 메서드를 나타내는 MethodDef 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-121">[out] A pointer to the MethodDef token that represents the set accessor method for the property.</span></span>  
  
 `pmdGetter`  
 <span data-ttu-id="caf2a-122">제한이 속성의 get 접근자 메서드를 나타내는 MethodDef 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-122">[out] A pointer to the MethodDef token that represents the get accessor method for the property.</span></span>  
  
 `rmdOtherMethod`  
 <span data-ttu-id="caf2a-123">제한이 속성과 연결 된 다른 메서드를 나타내는 MethodDef 토큰의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-123">[out] An array of MethodDef tokens that represent other methods associated with the property.</span></span>  
  
 `cMax`  
 <span data-ttu-id="caf2a-124">[in] `rmdOtherMethod` 배열의 최대 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-124">[in] The maximum size of the `rmdOtherMethod` array.</span></span> <span data-ttu-id="caf2a-125">모든 메서드를 저장할 수 있을 만큼 충분히 크지 않은 배열을 제공 하지 않으면 경고 없이 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-125">If you do not provide an array large enough to hold all the methods, they are skipped without warning.</span></span>  
  
 `pcOtherMethod`  
 <span data-ttu-id="caf2a-126">제한이 에서 반환 된 MethodDef 토큰의 수입니다 `rmdOtherMethod` .</span><span class="sxs-lookup"><span data-stu-id="caf2a-126">[out] The number of MethodDef tokens returned in `rmdOtherMethod`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="caf2a-127">요구 사항</span><span class="sxs-lookup"><span data-stu-id="caf2a-127">Requirements</span></span>  

 <span data-ttu-id="caf2a-128">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="caf2a-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="caf2a-129">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="caf2a-129">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="caf2a-130">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf2a-130">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="caf2a-131">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="caf2a-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="caf2a-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="caf2a-132">See also</span></span>

- [<span data-ttu-id="caf2a-133">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="caf2a-133">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="caf2a-134">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="caf2a-134">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
