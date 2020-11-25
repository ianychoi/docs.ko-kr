---
title: IMetaDataImport::FindTypeRef 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 3c96a9b601824cc4001568c4656f968fad70cf39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711288"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="c667f-102">IMetaDataImport::FindTypeRef 메서드</span><span class="sxs-lookup"><span data-stu-id="c667f-102">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="c667f-103">지정 된 <xref:System.Type> 범위에 있고 지정 된 이름을 가진 참조의 TypeRef 토큰에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="c667f-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c667f-104">구문</span><span class="sxs-lookup"><span data-stu-id="c667f-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c667f-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="c667f-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="c667f-106">진행 유형 참조가 정의 된 모듈, 어셈블리 또는 유형을 각각 지정 하는 ModuleRef, AssemblyRef 또는 TypeRef 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="c667f-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="c667f-107">진행 검색할 형식 참조의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c667f-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="c667f-108">제한이 일치 하는 TypeRef 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="c667f-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c667f-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="c667f-109">Requirements</span></span>  

 <span data-ttu-id="c667f-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c667f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c667f-111">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="c667f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c667f-112">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c667f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c667f-113">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c667f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c667f-114">참조</span><span class="sxs-lookup"><span data-stu-id="c667f-114">See also</span></span>

- [<span data-ttu-id="c667f-115">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c667f-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="c667f-116">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="c667f-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
