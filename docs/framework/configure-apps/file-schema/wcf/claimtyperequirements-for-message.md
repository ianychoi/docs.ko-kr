---
description: '에 대 한 자세한 <claimTypeRequirements> 정보: <message>'
title: <message>의 경우 <claimTypeRequirements>
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: a393a075c64f4a46e5ac055b3c417514861c9661
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638901"
---
# <a name="claimtyperequirements-for-message"></a><span data-ttu-id="51ef1-103">\<message>의 경우 \<claimTypeRequirements></span><span class="sxs-lookup"><span data-stu-id="51ef1-103">\<claimTypeRequirements> for \<message></span></span>

<span data-ttu-id="51ef1-104">필요한 클레임 형식의 컬렉션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="51ef1-104">Specifies a collection of required claim types.</span></span>  
  
 <span data-ttu-id="51ef1-105">컬렉션은 필수 및 선택적 클레임을 지정하는 데 서비스에서 사용됩니다. 이러한 클레임은 클라이언트에서 서비스에 액세스하는 데 사용하는 발급된 토큰에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ef1-105">The collection is used by the service to specify any required and optional claims which must be in the issued token the client uses to access the service.</span></span> <span data-ttu-id="51ef1-106">WSDL 게시가 활성화되어 있지만 WCF에서는 발급된 토큰이 지정된 클레임 형식을 포함하지 않아도 되는 경우 서비스는 필수 클레임 형식을 메타데이터로 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="51ef1-106">The service exposes the required claim types in metadata if WSDL publishing is enabled but WCF does not require the issued token contain the specified claim types.</span></span> <span data-ttu-id="51ef1-107">서비스에서 필수 클레임 형식을 표시하려면 인증 정책을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="51ef1-107">Services wishing to enforce required claim types are present should do using authorization policy.</span></span>  
  
 <span data-ttu-id="51ef1-108">페더레이션 클라이언트에서 이 컬렉션은 필수 및 선택적 클레임 목록을 포함하며, 이 목록은 발급된 토큰에 대한 클라이언트의 요청에서 보안 토큰 서비스로 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="51ef1-108">On federated clients, this collection contains the list of required and optional claims which is sent to the security token service in the client’s request for an issued token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ef1-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="51ef1-109">See also</span></span>

- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
