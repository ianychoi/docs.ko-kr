---
title: IMetaDataEmit::SetMethodProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetMethodProps
helpviewer_keywords:
- SetMethodProps method [.NET Framework metadata]
- IMetaDataEmit::SetMethodProps method [.NET Framework metadata]
ms.assetid: e0c6ac12-22ea-43f5-b799-8cda0faf3336
topic_type:
- apiref
ms.openlocfilehash: c461582cc22f7185ee2707db91be83bc1aa0ba4c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706842"
---
# <a name="imetadataemitsetmethodprops-method"></a><span data-ttu-id="39677-102">IMetaDataEmit::SetMethodProps 메서드</span><span class="sxs-lookup"><span data-stu-id="39677-102">IMetaDataEmit::SetMethodProps Method</span></span>

<span data-ttu-id="39677-103">[IMetaDataEmit::D efinemethod](imetadataemit-definemethod-method.md)에 대 한 이전 호출로 정의 된 메서드의 지정 된 상대 가상 주소에 저장 된 기능을 설정 하거나 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="39677-103">Sets or updates the feature, stored at the specified relative virtual address, of a method defined by a prior call to [IMetaDataEmit::DefineMethod](imetadataemit-definemethod-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39677-104">구문</span><span class="sxs-lookup"><span data-stu-id="39677-104">Syntax</span></span>  
  
```cpp  
HRESULT SetMethodProps (
    [in]  mdMethodDef md,
    [in]  DWORD       dwMethodFlags,  
    [in]  ULONG       ulCodeRVA,
    [in]  DWORD       dwImplFlags
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39677-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="39677-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="39677-106">진행 변경할 메서드의 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="39677-106">[in] The token for the method to be changed.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="39677-107">진행 멤버 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="39677-107">[in] The member attributes.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="39677-108">진행 코드의 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="39677-108">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="39677-109">진행 메서드에 대 한 구현 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="39677-109">[in] The implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39677-110">요구 사항</span><span class="sxs-lookup"><span data-stu-id="39677-110">Requirements</span></span>  

 <span data-ttu-id="39677-111">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="39677-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39677-112">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="39677-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="39677-113">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="39677-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39677-114">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39677-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39677-115">참조</span><span class="sxs-lookup"><span data-stu-id="39677-115">See also</span></span>

- [<span data-ttu-id="39677-116">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="39677-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="39677-117">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="39677-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
