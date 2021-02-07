---
description: '자세히 알아보기: IMetaDataAssemblyImport:: FindExportedTypeByName 메서드'
title: IMetaDataAssemblyImport::FindExportedTypeByName 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindExportedTypeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindExportedTypeByName
helpviewer_keywords:
- FindExportedTypeByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindExportedTypeByName method [.NET Framework metadata]
ms.assetid: 46264b2c-574d-4dde-aafc-77187a104fdd
topic_type:
- apiref
ms.openlocfilehash: 4a2dc2b65b7f7fe6d5f2e120c635214d457991bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99677992"
---
# <a name="imetadataassemblyimportfindexportedtypebyname-method"></a><span data-ttu-id="a26fa-103">IMetaDataAssemblyImport::FindExportedTypeByName 메서드</span><span class="sxs-lookup"><span data-stu-id="a26fa-103">IMetaDataAssemblyImport::FindExportedTypeByName Method</span></span>

<span data-ttu-id="a26fa-104">이름 및 바깥쪽 형식이 지정 된 경우 내보낸 형식에 대 한 포인터를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-104">Gets a pointer to an exported type, given its name and enclosing type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a26fa-105">구문</span><span class="sxs-lookup"><span data-stu-id="a26fa-105">Syntax</span></span>  
  
```cpp  
HRESULT FindExportedTypeByName (  
    [in]  LPCWSTR           szName,
    [in]  mdToken           mdtExportedType,
    [out] mdExportedType    *ptkExportedType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a26fa-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a26fa-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="a26fa-107">진행 내보낸 형식의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-107">[in] The name of the exported type.</span></span>  
  
 `mdtExportedType`  
 <span data-ttu-id="a26fa-108">진행 내보낸 형식의 바깥쪽 클래스에 대 한 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-108">[in] The metadata token for the enclosing class of the exported type.</span></span> <span data-ttu-id="a26fa-109">`mdExportedTypeNil`요청 된 내보낸 형식이 중첩 형식이 아닌 경우이 값은입니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-109">This value is `mdExportedTypeNil` if the requested exported type is not a nested type.</span></span>  
  
 `ptkExportedType`  
 <span data-ttu-id="a26fa-110">제한이 내보낸 형식을 나타내는 토큰에 대 한 포인터입니다 `mdExportedType` .</span><span class="sxs-lookup"><span data-stu-id="a26fa-110">[out] A pointer to the `mdExportedType` token that represents the exported type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a26fa-111">설명</span><span class="sxs-lookup"><span data-stu-id="a26fa-111">Remarks</span></span>  

 <span data-ttu-id="a26fa-112">`FindExportedTypeByName`메서드는 참조를 확인 하기 위해 공용 언어 런타임에서 사용 하는 표준 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-112">The `FindExportedTypeByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a26fa-113">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a26fa-113">Requirements</span></span>  

 <span data-ttu-id="a26fa-114">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a26fa-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a26fa-115">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="a26fa-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a26fa-116">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a26fa-116">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a26fa-117">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a26fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a26fa-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a26fa-118">See also</span></span>

- [<span data-ttu-id="a26fa-119">IMetaDataAssemblyImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a26fa-119">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="a26fa-120">런타임에서 어셈블리를 찾는 방법</span><span class="sxs-lookup"><span data-stu-id="a26fa-120">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
