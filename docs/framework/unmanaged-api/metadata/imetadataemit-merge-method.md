---
title: IMetaDataEmit::병합 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
ms.openlocfilehash: e64d644b511f7c3249c48b9642bfd3163142af3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722013"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="26a5c-102">IMetaDataEmit::병합 메서드</span><span class="sxs-lookup"><span data-stu-id="26a5c-102">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="26a5c-103">병합할 범위 목록에 지정 된 가져온 범위를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26a5c-104">구문</span><span class="sxs-lookup"><span data-stu-id="26a5c-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26a5c-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="26a5c-105">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="26a5c-106">진행 병합할 가져온 범위를 식별 하는 [IMetaDataImport](imetadataimport-interface.md) 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="26a5c-107">진행 토큰 다시 매핑을 지정 하는 [IMapToken](imaptoken-interface.md) 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="26a5c-108">진행 오류를 지정 하는 [IUnknown](/cpp/atl/iunknown) 개체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26a5c-109">설명</span><span class="sxs-lookup"><span data-stu-id="26a5c-109">Remarks</span></span>  

 <span data-ttu-id="26a5c-110">[IMetaDataEmit:: MergeEnd](imetadataemit-mergeend-method.md) 를 호출 하 여 메타 데이터의 병합을 단일 범위로 트리거합니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26a5c-111">요구 사항</span><span class="sxs-lookup"><span data-stu-id="26a5c-111">Requirements</span></span>  

 <span data-ttu-id="26a5c-112">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26a5c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26a5c-113">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="26a5c-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26a5c-114">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26a5c-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26a5c-115">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26a5c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26a5c-116">참조</span><span class="sxs-lookup"><span data-stu-id="26a5c-116">See also</span></span>

- [<span data-ttu-id="26a5c-117">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="26a5c-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="26a5c-118">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="26a5c-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
