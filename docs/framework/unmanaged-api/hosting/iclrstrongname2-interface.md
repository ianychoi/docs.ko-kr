---
title: ICLRStrongName2 인터페이스
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: df570f32d694ec21e9642e75b4965e169afaccfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677650"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="1b664-102">ICLRStrongName2 인터페이스</span><span class="sxs-lookup"><span data-stu-id="1b664-102">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="1b664-103">에서는 sha-1 512 384 256 (Secure Hash algorithm)의 SHA-2 그룹을 사용 하 여 강력한 이름을 만들 수 있는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b664-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1b664-104">메서드</span><span class="sxs-lookup"><span data-stu-id="1b664-104">Methods</span></span>  
  
|<span data-ttu-id="1b664-105">메서드</span><span class="sxs-lookup"><span data-stu-id="1b664-105">Method</span></span>|<span data-ttu-id="1b664-106">설명</span><span class="sxs-lookup"><span data-stu-id="1b664-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1b664-107">StrongNameGetPublicKeyEx 메서드</span><span class="sxs-lookup"><span data-stu-id="1b664-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="1b664-108">공개/개인 키 쌍에서 공개 키를 가져오고 해시 알고리즘과 서명 알고리즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b664-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="1b664-109">StrongNameSignatureVerificationEx2 메서드</span><span class="sxs-lookup"><span data-stu-id="1b664-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="1b664-110">강력한 이름의 어셈블리에 대 한 서명을 확인 하 고 ECMA 키에서 실제 키로의 매핑을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b664-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b664-111">설명</span><span class="sxs-lookup"><span data-stu-id="1b664-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b664-112">요구 사항</span><span class="sxs-lookup"><span data-stu-id="1b664-112">Requirements</span></span>  

 <span data-ttu-id="1b664-113">**플랫폼:**[시스템 요구 사항](../../get-started/system-requirements.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1b664-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b664-114">**헤더:** MetaHost</span><span class="sxs-lookup"><span data-stu-id="1b664-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1b664-115">**라이브러리:** MSCorEE.dll의 리소스로 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b664-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1b664-116">**.NET Framework 버전:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b664-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
