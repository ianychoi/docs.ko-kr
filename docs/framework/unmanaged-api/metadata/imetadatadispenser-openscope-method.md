---
title: IMetaDataDispenser::OpenScope 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: f2a85bafc3e2f25b2ed6116a46a9938d869dbaae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726082"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="3f5ab-102">IMetaDataDispenser::OpenScope 메서드</span><span class="sxs-lookup"><span data-stu-id="3f5ab-102">IMetaDataDispenser::OpenScope Method</span></span>

<span data-ttu-id="3f5ab-103">기존 디스크에 있는 기존 파일을 열고 해당 메타 데이터를 메모리에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5ab-104">구문</span><span class="sxs-lookup"><span data-stu-id="3f5ab-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f5ab-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3f5ab-105">Parameters</span></span>  

 `szScope`  
 <span data-ttu-id="3f5ab-106">진행 열 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="3f5ab-107">이 파일은 CLR (공용 언어 런타임) 메타 데이터를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="3f5ab-108">진행 열기에 대 한 모드 (읽기, 쓰기 등)를 지정 하는 [Coropenflags](coropenflags-enumeration.md) 열거형의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="3f5ab-109">진행 반환할 원하는 메타 데이터 인터페이스의 IID입니다. 호출자는 인터페이스를 사용 하 여 메타 데이터를 가져오거나 (읽기) 내보내기 (쓰기) 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="3f5ab-110">값은 `riid` "가져오기" 또는 "내보내기" 인터페이스 중 하나를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="3f5ab-111">유효한 값은 IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 또는 IID_IMetaDataImport2입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="3f5ab-112">제한이 반환 된 인터페이스에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f5ab-113">설명</span><span class="sxs-lookup"><span data-stu-id="3f5ab-113">Remarks</span></span>  

 <span data-ttu-id="3f5ab-114">메타 데이터의 메모리 내 복사본은 "가져오기" 인터페이스 중 하나에서 메서드를 사용 하 여 쿼리하거나 "내보내기" 인터페이스 중 하나에서 메서드를 사용 하 여 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="3f5ab-115">대상 파일에 CLR 메타 데이터가 없는 경우이 메서드는 `OpenScope` 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="3f5ab-116">.NET Framework 버전 1.0 및 버전 1.1에서 ofRead로 설정 된 범위를 열면 `dwOpenFlags` 공유에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="3f5ab-117">즉, 이전에를 호출 하 여 `OpenScope` 이전에 연 파일의 이름을 전달 하는 경우 기존 범위가 다시 사용 되며 새 데이터 구조 집합이 생성 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="3f5ab-118">그러나 이러한 공유로 인해 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="3f5ab-119">.NET Framework 버전 2.0에서는 ofRead로 설정 된 상태에서 열린 범위가 `dwOpenFlags` 더 이상 공유 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="3f5ab-120">OfReadOnly 값을 사용 하 여 범위를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="3f5ab-121">범위가 공유 되 면 "읽기/쓰기" 메타 데이터 인터페이스를 사용 하는 쿼리는 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f5ab-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3f5ab-122">Requirements</span></span>  

 <span data-ttu-id="3f5ab-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f5ab-124">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="3f5ab-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f5ab-125">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f5ab-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f5ab-126">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f5ab-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5ab-127">참조</span><span class="sxs-lookup"><span data-stu-id="3f5ab-127">See also</span></span>

- [<span data-ttu-id="3f5ab-128">IMetaDataDispenser 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="3f5ab-129">IMetaDataDispenserEx 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="3f5ab-130">IMetaDataAssemblyEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="3f5ab-131">IMetaDataAssemblyImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="3f5ab-132">IMetaDataEmit 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3f5ab-133">IMetaDataEmit2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="3f5ab-134">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3f5ab-135">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3f5ab-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
