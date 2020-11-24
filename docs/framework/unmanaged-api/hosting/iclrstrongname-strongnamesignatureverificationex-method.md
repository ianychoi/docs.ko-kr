---
title: ICLRStrongName::StrongNameSignatureVerificationEx 메서드
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
ms.openlocfilehash: 9caeb72c57260012ae2b459950bf19d907da1d98
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671553"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a><span data-ttu-id="b4e75-102">ICLRStrongName::StrongNameSignatureVerificationEx 메서드</span><span class="sxs-lookup"><span data-stu-id="b4e75-102">ICLRStrongName::StrongNameSignatureVerificationEx Method</span></span>

<span data-ttu-id="b4e75-103">제공 된 경로의 어셈블리 매니페스트에 강력한 이름 시그니처가 포함 되어 있는지 여부를 나타내는 값을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-103">Gets a value that indicates whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4e75-104">구문</span><span class="sxs-lookup"><span data-stu-id="b4e75-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4e75-105">매개 변수</span><span class="sxs-lookup"><span data-stu-id="b4e75-105">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="b4e75-106">진행 확인할 어셈블리의 이식 가능한 실행 파일 (.exe 또는 .dll) 파일에 대 한 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-106">[in] The path to the portable executable (.exe or .dll) file for the assembly to be verified.</span></span>  
  
 `fForceVerification`  
 <span data-ttu-id="b4e75-107">[in] `true` 레지스트리 설정을 재정의 해야 하는 경우에도 유효성 검사를 수행 하려면 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-107">[in] `true` to perform verification, even if it is necessary to override registry settings; otherwise, `false`.</span></span>  
  
 `pfWasVerified`  
 <span data-ttu-id="b4e75-108">[out] `true` 강력한 이름 서명을 확인 했으면이 고, 그렇지 않으면입니다. 그렇지 않으면 `false` 입니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-108">[out] `true` if the strong name signature was verified; otherwise, `false`.</span></span> <span data-ttu-id="b4e75-109">`pfWasVerified``false`레지스트리 설정으로 인해 확인이 성공적으로 수행 된 경우에도로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-109">`pfWasVerified` is also set to `false` if the verification was successful due to registry settings.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4e75-110">반환 값</span><span class="sxs-lookup"><span data-stu-id="b4e75-110">Return Value</span></span>  

 <span data-ttu-id="b4e75-111">`S_OK` 확인에 성공 했으면이 고, 그렇지 않으면입니다. 그렇지 않으면 오류를 나타내는 HRESULT 값입니다 (목록의 [일반적인 Hresult 값](/windows/win32/seccrypto/common-hresult-values) 참조).</span><span class="sxs-lookup"><span data-stu-id="b4e75-111">`S_OK` if the verification was successful; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4e75-112">설명</span><span class="sxs-lookup"><span data-stu-id="b4e75-112">Remarks</span></span>  

 <span data-ttu-id="b4e75-113">[ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) 메서드는 [ICLRStrongName:: StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) 메서드와 비슷한 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-113">The [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) method provides a capability similar to the [ICLRStrongName::StrongNameSignatureVerification](iclrstrongname-strongnamesignatureverification-method.md) method.</span></span> <span data-ttu-id="b4e75-114">그러나 [ICLRStrongName:: StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) 에 대 한 두 번째 입력 매개 변수 및 출력 매개 변수는 `BOOLEAN` 대신 형식입니다 `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="b4e75-114">However, the second input parameter and the output parameter for [ICLRStrongName::StrongNameSignatureVerificationEx](iclrstrongname-strongnamesignatureverificationex-method.md) are of type `BOOLEAN` instead of `DWORD`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4e75-115">요구 사항</span><span class="sxs-lookup"><span data-stu-id="b4e75-115">Requirements</span></span>  

 <span data-ttu-id="b4e75-116">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4e75-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4e75-117">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="b4e75-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b4e75-118">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4e75-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4e75-119">**.NET Framework 버전:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4e75-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4e75-120">참조</span><span class="sxs-lookup"><span data-stu-id="b4e75-120">See also</span></span>

- [<span data-ttu-id="b4e75-121">StrongNameSignatureVerification 메서드</span><span class="sxs-lookup"><span data-stu-id="b4e75-121">StrongNameSignatureVerification Method</span></span>](iclrstrongname-strongnamesignatureverification-method.md)
- [<span data-ttu-id="b4e75-122">ICLRStrongName 인터페이스</span><span class="sxs-lookup"><span data-stu-id="b4e75-122">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
