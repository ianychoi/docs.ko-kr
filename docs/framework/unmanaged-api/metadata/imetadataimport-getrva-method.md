---
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
ms.openlocfilehash: b4e7209c357f21a3f0de5770b483b673d5a5570b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729215"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="9a695-102">IMetaDataImport::GetRVA 메서드</span><span class="sxs-lookup"><span data-stu-id="9a695-102">IMetaDataImport::GetRVA Method</span></span>

<span data-ttu-id="9a695-103">지정 된 토큰이 나타내는 메서드나 필드의 RVA (상대 가상 주소) 및 구현 플래그를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a695-104">구문</span><span class="sxs-lookup"><span data-stu-id="9a695-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a695-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9a695-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="9a695-106">진행 RVA를 반환할 코드 개체를 나타내는 MethodDef 또는 FieldDef 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="9a695-107">토큰이 FieldDef 경우 필드는 전역 변수 여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="9a695-108">제한이 토큰이 나타내는 코드 개체의 상대 가상 주소에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="9a695-109">제한이 메서드에 대 한 구현 플래그에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="9a695-110">이 값은 [Cormethodimpl](cormethodimpl-enumeration.md) 열거형의 비트 마스크입니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="9a695-111">값은 `pdwImplFlags` 가 MethodDef 토큰 인 경우에만 유효 합니다 `tk` .</span><span class="sxs-lookup"><span data-stu-id="9a695-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a695-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9a695-112">Requirements</span></span>  

 <span data-ttu-id="9a695-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a695-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a695-114">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="9a695-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a695-115">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a695-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a695-116">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a695-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a695-117">참조</span><span class="sxs-lookup"><span data-stu-id="9a695-117">See also</span></span>

- [<span data-ttu-id="9a695-118">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9a695-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="9a695-119">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9a695-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
