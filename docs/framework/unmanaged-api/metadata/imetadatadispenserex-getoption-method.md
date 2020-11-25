---
title: IMetaDataDispenserEx::GetOption 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
ms.openlocfilehash: 0ceadf42ac49fd3fc89c78a6a26b2f529afeeaf0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700563"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="2d2b8-102">IMetaDataDispenserEx::GetOption 메서드</span><span class="sxs-lookup"><span data-stu-id="2d2b8-102">IMetaDataDispenserEx::GetOption Method</span></span>

<span data-ttu-id="2d2b8-103">현재 메타 데이터 범위에 지정 된 옵션의 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="2d2b8-104">옵션은 현재 메타 데이터 범위에 대 한 호출을 처리 하는 방법을 제어 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d2b8-105">구문</span><span class="sxs-lookup"><span data-stu-id="2d2b8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d2b8-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="2d2b8-106">Parameters</span></span>  

 `optionId`  
 <span data-ttu-id="2d2b8-107">진행 검색할 옵션을 지정 하는 GUID에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="2d2b8-108">지원 되는 Guid 목록은 설명 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2d2b8-109">제한이 반환 된 옵션의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-109">[out] The value of the returned option.</span></span> <span data-ttu-id="2d2b8-110">이 값의 형식은 지정 된 옵션 형식의 변형이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d2b8-111">설명</span><span class="sxs-lookup"><span data-stu-id="2d2b8-111">Remarks</span></span>  

 <span data-ttu-id="2d2b8-112">다음 목록에서는이 방법에 대해 지원 되는 Guid를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="2d2b8-113">설명에 대 한 자세한 내용은 [IMetaDataDispenserEx:: SetOption](imetadatadispenserex-setoption-method.md) 메서드를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="2d2b8-114">이 `optionId` 목록에 없는 경우이 메서드는 `E_INVALIDARG` 잘못 된 매개 변수를 나타내는 HRESULT를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="2d2b8-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="2d2b8-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="2d2b8-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="2d2b8-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="2d2b8-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="2d2b8-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="2d2b8-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="2d2b8-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="2d2b8-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="2d2b8-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="2d2b8-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="2d2b8-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="2d2b8-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="2d2b8-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d2b8-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="2d2b8-122">Requirements</span></span>  

 <span data-ttu-id="2d2b8-123">**플랫폼:** [시스템 요구 사항](../../get-started/system-requirements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d2b8-124">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="2d2b8-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2d2b8-125">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d2b8-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2d2b8-126">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d2b8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d2b8-127">참조</span><span class="sxs-lookup"><span data-stu-id="2d2b8-127">See also</span></span>

- [<span data-ttu-id="2d2b8-128">IMetaDataDispenserEx 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2d2b8-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="2d2b8-129">IMetaDataDispenser 인터페이스</span><span class="sxs-lookup"><span data-stu-id="2d2b8-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
