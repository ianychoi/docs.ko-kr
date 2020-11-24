---
title: ICLRStrongName::StrongNameGetBlob 메서드
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 824dcf89bacec27ced7cc431a9646d00fb879430
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674673"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="01067-102">ICLRStrongName::StrongNameGetBlob 메서드</span><span class="sxs-lookup"><span data-stu-id="01067-102">ICLRStrongName::StrongNameGetBlob Method</span></span>

<span data-ttu-id="01067-103">지정된 주소에 있는 실행 파일의 이진 표현으로 지정된 버퍼를 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="01067-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01067-104">구문</span><span class="sxs-lookup"><span data-stu-id="01067-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01067-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="01067-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="01067-106">진행 로드할 실행 파일의 올바른 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="01067-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="01067-107">진행 실행 파일을 로드할 버퍼입니다.</span><span class="sxs-lookup"><span data-stu-id="01067-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="01067-108">[in, out] 요청 된 최대 크기 (바이트)입니다 `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="01067-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="01067-109">반환 시의 실제 크기 (바이트)입니다 `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="01067-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01067-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="01067-110">Return Value</span></span>  

 <span data-ttu-id="01067-111">`S_OK` 메서드가 성공적으로 완료 되었으면이 고, 그렇지 않으면입니다. 그렇지 않으면 오류를 나타내는 HRESULT 값입니다 (목록의 [일반적인 Hresult 값](/windows/win32/seccrypto/common-hresult-values) 참조).</span><span class="sxs-lookup"><span data-stu-id="01067-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01067-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="01067-112">Requirements</span></span>  

 <span data-ttu-id="01067-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="01067-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01067-114">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="01067-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="01067-115">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="01067-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01067-116">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01067-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01067-117">참조</span><span class="sxs-lookup"><span data-stu-id="01067-117">See also</span></span>

- [<span data-ttu-id="01067-118">StrongNameGetBlobFromImage 메서드</span><span class="sxs-lookup"><span data-stu-id="01067-118">StrongNameGetBlobFromImage Method</span></span>](iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="01067-119">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="01067-119">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
