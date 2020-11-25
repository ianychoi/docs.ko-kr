---
title: IMetaDataEmit::GetTokenFromTypeSpec 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 3a8f369728b8464850259518981bf6690cb17a01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722039"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="604ff-102">IMetaDataEmit::GetTokenFromTypeSpec 메서드</span><span class="sxs-lookup"><span data-stu-id="604ff-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="604ff-103">지정 된 메타 데이터 서명을 사용 하 여 형식에 대 한 메타 데이터 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="604ff-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="604ff-104">구문</span><span class="sxs-lookup"><span data-stu-id="604ff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="604ff-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="604ff-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="604ff-106">진행 정의 되는 서명입니다.</span><span class="sxs-lookup"><span data-stu-id="604ff-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="604ff-107">진행 의 바이트 수 `pvSig` 입니다.</span><span class="sxs-lookup"><span data-stu-id="604ff-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="604ff-108">제한이 `mdTypeSpec` 할당 된 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="604ff-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="604ff-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="604ff-109">Requirements</span></span>  

 <span data-ttu-id="604ff-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="604ff-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="604ff-111">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="604ff-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="604ff-112">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="604ff-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="604ff-113">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="604ff-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604ff-114">참조</span><span class="sxs-lookup"><span data-stu-id="604ff-114">See also</span></span>

- [<span data-ttu-id="604ff-115">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="604ff-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="604ff-116">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="604ff-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
