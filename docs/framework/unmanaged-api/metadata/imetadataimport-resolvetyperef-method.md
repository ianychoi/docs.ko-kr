---
description: '자세히 알아보기: IMetaDataImport:: ResolveTypeRef 메서드'
title: IMetaDataImport::ResolveTypeRef 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: 0634bac77f457432948d0c2887d676e95430d05d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677563"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="793b8-103">IMetaDataImport::ResolveTypeRef 메서드</span><span class="sxs-lookup"><span data-stu-id="793b8-103">IMetaDataImport::ResolveTypeRef Method</span></span>

<span data-ttu-id="793b8-104">지정 된 <xref:System.Type> TypeRef 토큰이 나타내는 참조를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-104">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793b8-105">구문</span><span class="sxs-lookup"><span data-stu-id="793b8-105">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="793b8-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="793b8-106">Parameters</span></span>  

 `tr`  
 <span data-ttu-id="793b8-107">진행 참조 된 형식 정보를 반환할 TypeRef 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-107">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="793b8-108">진행 에서 반환할 인터페이스의 IID입니다 `ppIScope` .</span><span class="sxs-lookup"><span data-stu-id="793b8-108">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="793b8-109">일반적으로 IID_IMetaDataImport 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-109">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="793b8-110">제한이 참조 된 형식이 정의 된 모듈 범위에 대 한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-110">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="793b8-111">제한이 참조 된 형식을 나타내는 TypeDef 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-111">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="793b8-112">설명</span><span class="sxs-lookup"><span data-stu-id="793b8-112">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="793b8-113">여러 응용 프로그램 도메인을 로드 하는 경우에는이 메서드를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="793b8-113">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="793b8-114">이 메서드는 응용 프로그램 도메인 경계를 고려 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-114">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="793b8-115">어셈블리의 여러 버전이 로드 되 고 동일한 네임 스페이스를 가진 동일한 형식을 포함 하는 경우 메서드는 찾은 첫 번째 형식의 모듈 범위를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-115">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="793b8-116">`ResolveTypeRef`메서드는 다른 모듈의 형식 정의를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-116">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="793b8-117">형식 정의가 있으면에서 `ResolveTypeRef` 해당 모듈 범위에 대 한 인터페이스와 형식에 대 한 TypeDef 토큰을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-117">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="793b8-118">확인할 형식 참조의 확인 범위가 AssemblyRef 인 경우 `ResolveTypeRef` 메서드는 [IMetaDataDispenser:: openscope](imetadatadispenser-openscope-method.md) 메서드 또는 [IMetaDataDispenser:: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) 메서드를 호출 하 여 이미 열려 있는 메타 데이터 범위 에서만 일치 하는 항목을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-118">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="793b8-119">이는 `ResolveTypeRef` 에서 디스크 또는 전역 어셈블리 캐시에서 어셈블리가 저장 된 AssemblyRef 범위만 확인할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-119">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="793b8-120">요구 사항</span><span class="sxs-lookup"><span data-stu-id="793b8-120">Requirements</span></span>  

 <span data-ttu-id="793b8-121">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="793b8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="793b8-122">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="793b8-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="793b8-123">**라이브러리:** MsCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="793b8-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="793b8-124">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="793b8-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793b8-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="793b8-125">See also</span></span>

- [<span data-ttu-id="793b8-126">IMetaDataImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="793b8-126">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="793b8-127">IMetaDataImport2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="793b8-127">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
