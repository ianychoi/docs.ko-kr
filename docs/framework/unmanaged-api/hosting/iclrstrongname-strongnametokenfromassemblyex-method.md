---
description: '자세히 알아보기: ICLRStrongName:: StrongNameTokenFromAssemblyEx 메서드'
title: ICLRStrongName::StrongNameTokenFromAssemblyEx 메서드
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type:
- apiref
ms.openlocfilehash: e0a05d2aa0b41c370bde2bbff5367f25a1b13322
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781807"
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="3d23c-103">ICLRStrongName::StrongNameTokenFromAssemblyEx 메서드</span><span class="sxs-lookup"><span data-stu-id="3d23c-103">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>

<span data-ttu-id="3d23c-104">지정 된 어셈블리 파일에서 강력한 이름 토큰을 만들고 토큰이 나타내는 공개 키를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-104">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d23c-105">구문</span><span class="sxs-lookup"><span data-stu-id="3d23c-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d23c-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="3d23c-106">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="3d23c-107">진행 어셈블리에 대 한 PE (이식 가능한 실행) 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-107">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3d23c-108">제한이 반환 된 강력한 이름 토큰입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-108">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3d23c-109">제한이 강력한 이름 토큰의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-109">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="3d23c-110">제한이 반환 된 공개 키입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-110">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="3d23c-111">제한이 공개 키의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-111">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d23c-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="3d23c-112">Return Value</span></span>  

 <span data-ttu-id="3d23c-113">`S_OK` 메서드가 성공적으로 완료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 오류를 나타내는 HRESULT 값입니다 (목록의 [일반적인 Hresult 값](/windows/win32/seccrypto/common-hresult-values) 참조).</span><span class="sxs-lookup"><span data-stu-id="3d23c-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d23c-114">설명</span><span class="sxs-lookup"><span data-stu-id="3d23c-114">Remarks</span></span>  

 <span data-ttu-id="3d23c-115">강력한 이름 토큰은 공개 키의 축약 된 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-115">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="3d23c-116">토큰은 어셈블리에 서명 하는 데 사용 되는 공개 키에서 만든 64 비트 해시입니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-116">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="3d23c-117">토큰은 어셈블리에 대 한 강력한 이름의 일부 이며 어셈블리 메타 데이터에서 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-117">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="3d23c-118">키를 검색 하 고 토큰을 만든 후에는 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) 메서드를 호출 하 여 할당 된 메모리를 해제 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-118">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d23c-119">요구 사항</span><span class="sxs-lookup"><span data-stu-id="3d23c-119">Requirements</span></span>  

 <span data-ttu-id="3d23c-120">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3d23c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d23c-121">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="3d23c-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="3d23c-122">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3d23c-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3d23c-123">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d23c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d23c-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3d23c-124">See also</span></span>

- [<span data-ttu-id="3d23c-125">StrongNameTokenFromAssembly 메서드</span><span class="sxs-lookup"><span data-stu-id="3d23c-125">StrongNameTokenFromAssembly Method</span></span>](iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="3d23c-126">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="3d23c-126">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
