---
description: '자세히 알아보기: ICLRStrongName:: StrongNameSignatureVerificationFromImage 메서드'
title: ICLRStrongName::StrongNameSignatureVerificationFromImage 메서드
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureVerificationFromImage method [.NET Framework hosting]
- StrongNameSignatureVerificationFromImage method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: da91c138-ee30-4fd4-a040-464d97d7e41a
topic_type:
- apiref
ms.openlocfilehash: 5c1c3568dd0ad506c478525503f168d8b8c2dfbc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781833"
---
# <a name="iclrstrongnamestrongnamesignatureverificationfromimage-method"></a><span data-ttu-id="9ded5-103">ICLRStrongName::StrongNameSignatureVerificationFromImage 메서드</span><span class="sxs-lookup"><span data-stu-id="9ded5-103">ICLRStrongName::StrongNameSignatureVerificationFromImage Method</span></span>

<span data-ttu-id="9ded5-104">메모리에 이미 매핑된 어셈블리가 연결된 공개 키에 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-104">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ded5-105">구문</span><span class="sxs-lookup"><span data-stu-id="9ded5-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ded5-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="9ded5-106">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="9ded5-107">진행 매핑된 어셈블리 매니페스트의 상대 가상 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-107">[in] The relative virtual address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9ded5-108">진행 매핑된 이미지의 크기 (바이트)입니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-108">[in] The size, in bytes, of the mapped image.</span></span>  
  
 `dwInFlags`  
 <span data-ttu-id="9ded5-109">진행 확인 동작에 영향을 주는 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-109">[in] Flags that influence verification behavior.</span></span> <span data-ttu-id="9ded5-110">지원되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-110">The following values are supported:</span></span>  
  
- <span data-ttu-id="9ded5-111">`SN_INFLAG_FORCE_VER` (0x00000001)-레지스트리 설정을 재정의 해야 하는 경우에도 강제로 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-111">`SN_INFLAG_FORCE_VER` (0x00000001) - Forces verification even if it is necessary to override registry settings.</span></span>  
  
- <span data-ttu-id="9ded5-112">`SN_INFLAG_INSTALL` (0x00000002)-이 이미지에서 수행 되는 첫 번째 확인을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-112">`SN_INFLAG_INSTALL` (0x00000002) - Specifies that this is the first verification performed on this image.</span></span>  
  
- <span data-ttu-id="9ded5-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004)-캐시가 관리 권한이 있는 사용자 에게만 액세스를 허용 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-113">`SN_INFLAG_ADMIN_ACCESS` (0x00000004) - Specifies that the cache will allow access only to users who have administrative privileges.</span></span>  
  
- <span data-ttu-id="9ded5-114">`SN_INFLAG_USER_ACCESS` (0x00000008)-현재 사용자만 어셈블리에 액세스할 수 있도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-114">`SN_INFLAG_USER_ACCESS` (0x00000008) - Specifies that the assembly will be accessible only to the current user.</span></span>  
  
- <span data-ttu-id="9ded5-115">`SN_INFLAG_ALL_ACCESS` (0x00000010)-캐시가 액세스 제한에 대 한 보장을 제공 하지 않도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-115">`SN_INFLAG_ALL_ACCESS` (0x00000010) - Specifies that the cache will provide no guarantees of access restriction.</span></span>  
  
- <span data-ttu-id="9ded5-116">`SN_INFLAG_RUNTIME` (0x80000000)-내부 디버깅용으로 예약 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-116">`SN_INFLAG_RUNTIME` (0x80000000) - Reserved for internal debugging.</span></span>  
  
 `pdwOutFlags`  
 <span data-ttu-id="9ded5-117">제한이 추가 출력 정보에 대 한 플래그입니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-117">[out] A flag for additional output information.</span></span> <span data-ttu-id="9ded5-118">지원 되는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-118">The following value is supported:</span></span>  
  
- <span data-ttu-id="9ded5-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001)-이 값은 `false` 레지스트리 설정으로 인해 확인이 성공 하도록 지정 하기 위해로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-119">`SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - This value is set to `false` to specify that the verification succeeded due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ded5-120">Return Value</span><span class="sxs-lookup"><span data-stu-id="9ded5-120">Return Value</span></span>  

 <span data-ttu-id="9ded5-121">`S_OK` 메서드가 성공적으로 완료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 오류를 나타내는 HRESULT 값입니다 (목록의 [일반적인 Hresult 값](/windows/win32/seccrypto/common-hresult-values) 참조).</span><span class="sxs-lookup"><span data-stu-id="9ded5-121">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ded5-122">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9ded5-122">Requirements</span></span>  

 <span data-ttu-id="9ded5-123">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9ded5-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ded5-124">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="9ded5-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9ded5-125">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ded5-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ded5-126">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ded5-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ded5-127">참조</span><span class="sxs-lookup"><span data-stu-id="9ded5-127">See also</span></span>

- [<span data-ttu-id="9ded5-128">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="9ded5-128">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
