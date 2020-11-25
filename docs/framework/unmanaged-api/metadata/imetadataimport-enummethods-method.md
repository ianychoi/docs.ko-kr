---
title: IMetaDataImport::EnumMethods 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 00726b7e74bdedc658886cccbc4329eaf3ae76d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696806"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="15414-102">IMetaDataImport::EnumMethods 메서드</span><span class="sxs-lookup"><span data-stu-id="15414-102">IMetaDataImport::EnumMethods Method</span></span>

<span data-ttu-id="15414-103">지정한 형식의 메서드를 나타내는 MethodDef 토큰을 열거합니다.</span><span class="sxs-lookup"><span data-stu-id="15414-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15414-104">구문</span><span class="sxs-lookup"><span data-stu-id="15414-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15414-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="15414-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="15414-106">[in, out] 열거자에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="15414-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="15414-107">이 메서드의 첫 번째 호출에서는 NULL 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="15414-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="15414-108">진행 열거할 메서드가 포함 된 형식을 나타내는 TypeDef 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="15414-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="15414-109">제한이 MethodDef 토큰을 저장할 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="15414-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="15414-110">진행 MethodDef 배열의 최대 크기 `rMethods` 입니다.</span><span class="sxs-lookup"><span data-stu-id="15414-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="15414-111">제한이 에서 반환 된 MethodDef 토큰의 수입니다 `rMethods` .</span><span class="sxs-lookup"><span data-stu-id="15414-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15414-112">반환 값</span><span class="sxs-lookup"><span data-stu-id="15414-112">Return Value</span></span>  
  
|<span data-ttu-id="15414-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15414-113">HRESULT</span></span>|<span data-ttu-id="15414-114">설명</span><span class="sxs-lookup"><span data-stu-id="15414-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="15414-115">`EnumMethods` 성공적으로 반환 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="15414-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="15414-116">열거할 MethodDef 토큰이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="15414-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="15414-117">이 경우는 `pcTokens` 0입니다.</span><span class="sxs-lookup"><span data-stu-id="15414-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15414-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="15414-118">Requirements</span></span>  

 <span data-ttu-id="15414-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="15414-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15414-120">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="15414-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="15414-121">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="15414-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="15414-122">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15414-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15414-123">참조</span><span class="sxs-lookup"><span data-stu-id="15414-123">See also</span></span>

- [<span data-ttu-id="15414-124">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="15414-124">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="15414-125">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="15414-125">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
