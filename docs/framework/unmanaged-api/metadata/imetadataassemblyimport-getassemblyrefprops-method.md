---
description: '자세히 알아보기: IMetaDataAssemblyImport:: GetAssemblyRefProps 메서드'
title: IMetaDataAssemblyImport::GetAssemblyRefProps 메서드
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: f7011806920ba37ca84b1a48f12da3a5557fa464
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784134"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="a09f7-103">IMetaDataAssemblyImport::GetAssemblyRefProps 메서드</span><span class="sxs-lookup"><span data-stu-id="a09f7-103">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="a09f7-104">지정 된 메타 데이터 시그니처를 사용 하는 어셈블리 참조의 속성 집합을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-104">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a09f7-105">구문</span><span class="sxs-lookup"><span data-stu-id="a09f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a09f7-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="a09f7-106">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="a09f7-107">진행 `mdAssemblyRef` 속성을 가져올 어셈블리 참조를 나타내는 메타 데이터 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-107">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="a09f7-108">제한이 공개 키 또는 메타 데이터 토큰에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="a09f7-109">제한이 반환 된 공개 키 또는 토큰의 바이트 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-109">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="a09f7-110">제한이 어셈블리의 단순한 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-110">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="a09f7-111">진행 와이드 문자의 크기 (와이드 문자)입니다 `szName` .</span><span class="sxs-lookup"><span data-stu-id="a09f7-111">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="a09f7-112">제한이 에 실제로 반환 된 와이드 문자 수에 대 한 포인터입니다 `szName` .</span><span class="sxs-lookup"><span data-stu-id="a09f7-112">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="a09f7-113">제한이 어셈블리 메타 데이터를 포함 하는 ASSEMBLYMETADATA 구조체에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-113">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="a09f7-114">제한이 해시 값에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-114">[out] A pointer to the hash value.</span></span> <span data-ttu-id="a09f7-115">이는 `PublicKey` [Assemblyrefflags](assemblyrefflags-enumeration.md) 열거의 arfFullOriginator 플래그가 설정 되지 않은 경우 참조 되는 어셈블리의 속성에 대 한 sha-1 알고리즘을 사용 하는 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-115">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="a09f7-116">제한이 반환 된 해시 값의 와이드 문자 수입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-116">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="a09f7-117">제한이 어셈블리에 적용 된 메타 데이터를 설명 하는 플래그에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-117">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="a09f7-118">Flags 값은 하나 이상의 [Corassemblyflags](corassemblyflags-enumeration.md) 값의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-118">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a09f7-119">Return Value</span><span class="sxs-lookup"><span data-stu-id="a09f7-119">Return Value</span></span>  

 <span data-ttu-id="a09f7-120">성공 하면이 메서드는 S_OK를 반환 합니다. 그렇지 않으면 Winerror.h 헤더 파일에 정의 된 오류 코드 중 하나를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-120">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a09f7-121">요구 사항</span><span class="sxs-lookup"><span data-stu-id="a09f7-121">Requirements</span></span>  

 <span data-ttu-id="a09f7-122">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a09f7-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a09f7-123">**헤더:** Cor</span><span class="sxs-lookup"><span data-stu-id="a09f7-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a09f7-124">**라이브러리:** MsCorEE.dll에서 리소스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a09f7-124">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a09f7-125">**.NET Framework 버전:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a09f7-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09f7-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a09f7-126">See also</span></span>

- [<span data-ttu-id="a09f7-127">IMetaDataAssemblyImport 인터페이스</span><span class="sxs-lookup"><span data-stu-id="a09f7-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
