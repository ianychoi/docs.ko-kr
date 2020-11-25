---
title: IMetaDataDispenser::DefineScope 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 87a39350986cb7bb62f76b0d9a6a9aae8f82e2f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726095"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="1d029-102">IMetaDataDispenser::DefineScope 메서드</span><span class="sxs-lookup"><span data-stu-id="1d029-102">IMetaDataDispenser::DefineScope Method</span></span>

<span data-ttu-id="1d029-103">새 메타 데이터를 만들 수 있는 메모리에 새 영역을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d029-104">구문</span><span class="sxs-lookup"><span data-stu-id="1d029-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d029-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="1d029-105">Parameters</span></span>  

 `rclsid`  
 <span data-ttu-id="1d029-106">진행 만들 메타 데이터 구조 버전의 CLSID입니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="1d029-107">.NET Framework 버전 2.0에 대해이 값을 CLSID_CorMetaDataRuntime 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="1d029-108">진행 옵션을 지정 하는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-108">[in] Flags that specify options.</span></span> <span data-ttu-id="1d029-109">.NET Framework 2.0의 경우이 값은 0 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="1d029-110">진행 반환할 원하는 메타 데이터 인터페이스의 IID입니다. 호출자는 인터페이스를 사용 하 여 새 메타 데이터를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="1d029-111">값은 `riid` "내보내기" 인터페이스 중 하나를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="1d029-112">유효한 값은 IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit 또는 IID_IMetaDataEmit2입니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="1d029-113">제한이 반환 된 인터페이스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d029-114">설명</span><span class="sxs-lookup"><span data-stu-id="1d029-114">Remarks</span></span>  

 <span data-ttu-id="1d029-115">`DefineScope` 는 메모리 내 메타 데이터 테이블 집합을 만들고, 메타 데이터에 대 한 고유 GUID (모듈 버전 식별자 또는 MVID)를 생성 하 고, 내보내는 컴파일 단위에 대 한 모듈 테이블에 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="1d029-116">[IMetaDataEmit:: SetModuleProps](imetadataemit-setmoduleprops-method.md) 또는 [IMetaDataEmit::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) 메서드를 적절 하 게 사용 하 여 전체 메타 데이터 범위에 특성을 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d029-117">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1d029-117">Requirements</span></span>  

 <span data-ttu-id="1d029-118">**플랫폼:** [시스템 요구 사항](../../get-started/system-requirements.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1d029-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d029-119">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="1d029-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d029-120">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1d029-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1d029-121">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d029-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d029-122">참조</span><span class="sxs-lookup"><span data-stu-id="1d029-122">See also</span></span>

- [<span data-ttu-id="1d029-123">IMetaDataDispenser 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d029-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="1d029-124">IMetaDataDispenserEx 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d029-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="1d029-125">IMetaDataAssemblyEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d029-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="1d029-126">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d029-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="1d029-127">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1d029-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
