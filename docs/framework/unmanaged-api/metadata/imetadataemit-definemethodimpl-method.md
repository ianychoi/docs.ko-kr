---
title: IMetaDataEmit::DefineMethodImpl 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethodImpl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethodImpl
helpviewer_keywords:
- DefineMethodImpl method [.NET Framework metadata]
- IMetaDataEmit::DefineMethodImpl method [.NET Framework metadata]
ms.assetid: 9dcc8b3d-33ee-4c7c-8d6f-322c57b94a0f
topic_type:
- apiref
ms.openlocfilehash: 24a7c5bca1287e55f3eb06d63e1fed8da37eb3b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719569"
---
# <a name="imetadataemitdefinemethodimpl-method"></a><span data-ttu-id="ccf33-102">IMetaDataEmit::DefineMethodImpl 메서드</span><span class="sxs-lookup"><span data-stu-id="ccf33-102">IMetaDataEmit::DefineMethodImpl Method</span></span>

<span data-ttu-id="ccf33-103">인터페이스에서 상속 된 메서드의 구현에 대 한 정의를 만들고 해당 메서드 구현 정의에 대 한 토큰을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccf33-103">Creates a definition for implementation of a method inherited from an interface, and returns a token to that method-implementation definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccf33-104">구문</span><span class="sxs-lookup"><span data-stu-id="ccf33-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodImpl (
    [in]  mdTypeDef         td,
    [in]  mdToken           tkBody,
    [in]  mdToken           tkDecl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccf33-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="ccf33-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="ccf33-106">진행 `mdTypedef` 구현 하는 클래스의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf33-106">[in] The `mdTypedef` token of the implementing class.</span></span>  
  
 `tkBody`  
 <span data-ttu-id="ccf33-107">진행 `mdMethodDef` `mdMemberRef` 코드 본문의 또는 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf33-107">[in] The `mdMethodDef` or `mdMemberRef` token of the code body.</span></span>  
  
 `tkDecl`  
 <span data-ttu-id="ccf33-108">진행 `mdMethodDef` `mdMemberRef` 구현 중인 인터페이스 메서드의 또는 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="ccf33-108">[in] The `mdMethodDef` or `mdMemberRef` token of the interface method being implemented.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccf33-109">요구 사항</span><span class="sxs-lookup"><span data-stu-id="ccf33-109">Requirements</span></span>  

 <span data-ttu-id="ccf33-110">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ccf33-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf33-111">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="ccf33-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ccf33-112">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccf33-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ccf33-113">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf33-114">참조</span><span class="sxs-lookup"><span data-stu-id="ccf33-114">See also</span></span>

- [<span data-ttu-id="ccf33-115">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ccf33-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="ccf33-116">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="ccf33-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
