---
title: IMetaDataEmit::DefineEvent 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineEvent
helpviewer_keywords:
- IMetaDataEmit::DefineEvent method [.NET Framework metadata]
- DefineEvent method [.NET Framework metadata]
ms.assetid: cf064bac-9a9f-41c5-9e1d-108ff7af3afe
topic_type:
- apiref
ms.openlocfilehash: 3c03497f48b8199da545d796637e5f8a5c532362
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675700"
---
# <a name="imetadataemitdefineevent-method"></a><span data-ttu-id="a2ca4-102">IMetaDataEmit::DefineEvent 메서드</span><span class="sxs-lookup"><span data-stu-id="a2ca4-102">IMetaDataEmit::DefineEvent Method</span></span>

<span data-ttu-id="a2ca4-103">지정 된 메타 데이터 시그니처를 사용 하 여 이벤트에 대 한 정의를 만들고 해당 이벤트 정의에 대 한 토큰을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-103">Creates a definition for an event with the specified metadata signature, and gets a token to that event definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2ca4-104">구문</span><span class="sxs-lookup"><span data-stu-id="a2ca4-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineEvent (
    [in]  mdTypeDef    td,
    [in]  LPCWSTR      szEvent,
    [in]  DWORD        dwEventFlags,
    [in]  mdToken      tkEventType,
    [in]  mdMethodDef  mdAddOn,
    [in]  mdMethodDef  mdRemoveOn,
    [in]  mdMethodDef  mdFire,
    [in]  mdMethodDef  rmdOtherMethods[],
    [out] mdEvent      *pmdEvent
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2ca4-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a2ca4-105">Parameters</span></span>  

 `td`  
 <span data-ttu-id="a2ca4-106">진행 대상 클래스 또는 인터페이스에 대 한 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-106">[in] The token for the target class or interface.</span></span> <span data-ttu-id="a2ca4-107">이는 `mdTypeDef` 또는 토큰입니다 `mdTypeDefNil` .</span><span class="sxs-lookup"><span data-stu-id="a2ca4-107">This is either a `mdTypeDef` or `mdTypeDefNil` token.</span></span>  
  
 `szEvent`  
 <span data-ttu-id="a2ca4-108">진행 이벤트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-108">[in] The name of the event.</span></span>  
  
 `dwEventFlags`  
 <span data-ttu-id="a2ca4-109">진행 이벤트 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-109">[in] Event flags.</span></span>  
  
 `tkEventType`  
 <span data-ttu-id="a2ca4-110">진행 이벤트 클래스에 대 한 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-110">[in] The token for the event class.</span></span> <span data-ttu-id="a2ca4-111">`mdTypeDef`, `mdTypeRef` 또는 `mdTokenNil` 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-111">This is a `mdTypeDef`, a `mdTypeRef`, or a `mdTokenNil` token.</span></span>  
  
 `mdAddOn`  
 <span data-ttu-id="a2ca4-112">진행 이벤트를 구독 하는 데 사용 되는 메서드 이거나 null입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-112">[in] The method used to subscribe to the event, or null.</span></span>  
  
 `mdRemoveOn`  
 <span data-ttu-id="a2ca4-113">진행 이벤트를 구독 취소 하는 데 사용 되는 메서드 이거나 null입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-113">[in] The method used to unsubscribe to the event, or null.</span></span>  
  
 `mdFire`  
 <span data-ttu-id="a2ca4-114">진행 파생 클래스에서 이벤트를 발생 시키는 데 사용 되는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-114">[in] The method used (by a derived class) to raise the event.</span></span>  
  
 `rmdOtherMethods[]`  
 <span data-ttu-id="a2ca4-115">진행 이벤트와 연결 된 다른 메서드에 대 한 토큰의 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-115">[in] An array of tokens for other methods associated with the event.</span></span> <span data-ttu-id="a2ca4-116">배열은 토큰과 함께 종료 됩니다 `mdMethodDefNil` .</span><span class="sxs-lookup"><span data-stu-id="a2ca4-116">The array is terminated with a `mdMethodDefNil` token.</span></span>  
  
 `pmdEvent`  
 <span data-ttu-id="a2ca4-117">제한이 이벤트에 할당 된 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-117">[out] The metadata token assigned to the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2ca4-118">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a2ca4-118">Requirements</span></span>  

 <span data-ttu-id="a2ca4-119">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2ca4-120">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="a2ca4-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2ca4-121">**라이브러리:** MSCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a2ca4-121">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2ca4-122">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2ca4-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2ca4-123">참조</span><span class="sxs-lookup"><span data-stu-id="a2ca4-123">See also</span></span>

- [<span data-ttu-id="a2ca4-124">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a2ca4-124">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a2ca4-125">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a2ca4-125">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
