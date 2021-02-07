---
description: '다음에 대 한 자세한 정보: AXL_AUTHENTICODE_TIMESTAMPER_INFO 구조체'
title: AXL_AUTHENTICODE_TIMESTAMPER_INFO 구조
ms.date: 03/30/2017
ms.assetid: 89e41a81-0f41-45ad-8f20-a120e4ff24fb
ms.openlocfilehash: 35e30241c3c3b5747e247c57183e28e726c0cae3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747415"
---
# <a name="axl_authenticode_timestamper_info-structure"></a><span data-ttu-id="e3e4e-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO 구조</span><span class="sxs-lookup"><span data-stu-id="e3e4e-103">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>

<span data-ttu-id="e3e4e-104">Authenticode 타임스탬퍼 정보를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-104">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3e4e-105">구문</span><span class="sxs-lookup"><span data-stu-id="e3e4e-105">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    FILETIME ftTimestamp  
    PCCERT_CHAIN_CONTEXT pChainContext;  
} AXL_AUTHENTICODE_TIMESTAMPER_INFO, * PAXL_AUTHENTICODE_TIMESTAMPER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="e3e4e-106">구성원</span><span class="sxs-lookup"><span data-stu-id="e3e4e-106">Members</span></span>  
  
|<span data-ttu-id="e3e4e-107">멤버</span><span class="sxs-lookup"><span data-stu-id="e3e4e-107">Member</span></span>|<span data-ttu-id="e3e4e-108">설명</span><span class="sxs-lookup"><span data-stu-id="e3e4e-108">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="e3e4e-109">이 구조체의 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-109">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="e3e4e-110">오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-110">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="e3e4e-111">해시 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-111">The hash algorithm.</span></span>|  
|`ftTimestamp`|<span data-ttu-id="e3e4e-112">타임스탬프의 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-112">The time of the time stamp.</span></span>|  
|`pChainContext`|<span data-ttu-id="e3e4e-113">타임스탬퍼의 체인 컨텍스트입니다.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-113">The time stamper’s chain context.</span></span>  <span data-ttu-id="e3e4e-114">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) 구조체를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e3e4e-114">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3e4e-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e3e4e-115">See also</span></span>

- [<span data-ttu-id="e3e4e-116">Authenticode</span><span class="sxs-lookup"><span data-stu-id="e3e4e-116">Authenticode</span></span>](index.md)
