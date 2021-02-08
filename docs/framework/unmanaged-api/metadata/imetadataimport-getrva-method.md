---
description: '자세히 알아보기: IMetaDataImport:: GetRVA 메서드'
title: IMetaDataImport::GetRVA 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 8d6439bcad50a6311e7bb1408f4c86144a5026ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789166"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="d71f2-103">IMetaDataImport::GetRVA 메서드</span><span class="sxs-lookup"><span data-stu-id="d71f2-103">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="d71f2-104">지정 된 토큰이 나타내는 메서드나 필드의 RVA (상대 가상 주소) 및 구현 플래그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-104">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71f2-105">구문</span><span class="sxs-lookup"><span data-stu-id="d71f2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d71f2-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="d71f2-106">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d71f2-107">진행 RVA를 반환할 코드 개체를 나타내는 MethodDef 또는 FieldDef 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-107">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="d71f2-108">토큰이 FieldDef 경우 필드는 전역 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-108">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="d71f2-109">제한이 토큰이 나타내는 코드 개체의 상대 가상 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-109">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="d71f2-110">제한이 메서드에 대 한 구현 플래그에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-110">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="d71f2-111">이 값은 [Cormethodimpl](cormethodimpl-enumeration.md) 열거형의 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-111">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="d71f2-112">값은 `pdwImplFlags` 가 MethodDef 토큰 인 경우에만 유효 합니다 `tk` .</span><span class="sxs-lookup"><span data-stu-id="d71f2-112">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71f2-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="d71f2-113">Requirements</span></span>  

 <span data-ttu-id="d71f2-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d71f2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71f2-115">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="d71f2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d71f2-116">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d71f2-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d71f2-117">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d71f2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d71f2-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d71f2-118">See also</span></span>

- [<span data-ttu-id="d71f2-119">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d71f2-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="d71f2-120">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="d71f2-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
