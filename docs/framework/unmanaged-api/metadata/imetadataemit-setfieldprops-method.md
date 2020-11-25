---
title: IMetaDataEmit::SetFieldProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: 0f98fb64b43822c437c39df2f3c51a222ef386b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730398"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="be33d-102">IMetaDataEmit::SetFieldProps 메서드</span><span class="sxs-lookup"><span data-stu-id="be33d-102">IMetaDataEmit::SetFieldProps Method</span></span>

<span data-ttu-id="be33d-103">지정 된 필드 토큰이 참조 하는 필드의 기본값을 설정 하거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be33d-104">구문</span><span class="sxs-lookup"><span data-stu-id="be33d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be33d-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="be33d-105">Parameters</span></span>  

 `fd`  
 <span data-ttu-id="be33d-106">진행 대상 필드의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="be33d-107">진행 필드 특성.</span><span class="sxs-lookup"><span data-stu-id="be33d-107">[in] Field attributes.</span></span> <span data-ttu-id="be33d-108">값의 비트 마스크입니다 `CorFieldAttr` .</span><span class="sxs-lookup"><span data-stu-id="be33d-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="be33d-109">진행 `ELEMENT_TYPE_` *\** 상수 값에 대 한입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="be33d-110">`CorElementType`값입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="be33d-111">상수가 정의 되지 않은 경우이 값을로 설정 `ELEMENT_TYPE_END` 합니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="be33d-112">진행 필드의 상수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="be33d-113">진행 의 유니코드 문자 크기입니다 `pValue` .</span><span class="sxs-lookup"><span data-stu-id="be33d-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be33d-114">요구 사항</span><span class="sxs-lookup"><span data-stu-id="be33d-114">Requirements</span></span>  

 <span data-ttu-id="be33d-115">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="be33d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be33d-116">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="be33d-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be33d-117">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="be33d-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be33d-118">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be33d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be33d-119">참조</span><span class="sxs-lookup"><span data-stu-id="be33d-119">See also</span></span>

- [<span data-ttu-id="be33d-120">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="be33d-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="be33d-121">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="be33d-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
