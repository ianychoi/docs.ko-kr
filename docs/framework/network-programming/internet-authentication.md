---
title: 인터넷 인증
description: System.Net 클래스가 .NET Framework에서 애플리케이션에 대해 지원하는 다양한 클라이언트 인증 메커니즘에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 085ca27dd0cfedc90211b21c10cc8bc5cf1ecd21
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241592"
---
# <a name="internet-authentication"></a><span data-ttu-id="8ab3a-103">인터넷 인증</span><span class="sxs-lookup"><span data-stu-id="8ab3a-103">Internet Authentication</span></span>

<span data-ttu-id="8ab3a-104"><xref:System.Net> 클래스는 표준 인터넷 인증 방법인 기본, 다이제스트, 협상, NTLM 및 Kerberos 인증뿐 아니라 직접 만들 수 있는 사용자 지정 방법을 포함한 다양한 클라이언트 인증 메커니즘을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-104">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="8ab3a-105">인증 자격 증명은 <xref:System.Net.ICredentials> 인터페이스를 구현하는 <xref:System.Net.NetworkCredential> 및 <xref:System.Net.CredentialCache> 클래스에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-105">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="8ab3a-106">이러한 클래스 중 하나를 쿼리하여 자격 증명이 있는지 확인할 경우 해당 클래스는 **NetworkCredential** 클래스의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-106">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="8ab3a-107">인증 프로세스는 <xref:System.Net.AuthenticationManager> 클래스에서 관리되고 실제 인증 프로세스는 <xref:System.Net.IAuthenticationModule> 인터페이스를 구현하는 인증 모듈 클래스에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-107">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="8ab3a-108">사용자 지정 인증 모듈을 사용하기 전에 **AuthenticationManager** 에 등록해야 합니다. 기본, 다이제스트, 협상, NTLM 및 Kerberos 인증 방법용 모듈은 기본적으로 등록되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-108">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="8ab3a-109">**NetworkCredential** 은 URI로 식별되는 단일 인터넷 리소스와 연결된 자격 증명 집합을 저장하고 <xref:System.Net.NetworkCredential.GetCredential%2A> 메서드 호출에 대한 응답으로 자격 증명을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-109">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="8ab3a-110">**NetworkCredential** 클래스는 일반적으로 제한된 수의 인터넷 리소스에 액세스하는 애플리케이션에서 사용되거나 모든 경우에 동일한 자격 증명 집합을 사용하는 애플리케이션에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-110">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="8ab3a-111">**CredentialCache** 클래스는 다양한 웹 리소스에 대한 자격 증명 컬렉션을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-111">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="8ab3a-112"><xref:System.Net.CredentialCache.GetCredential%2A> 메서드가 호출되면 **CredentialCache** 는 웹 리소스의 URI 및 요청된 인증 체계를 통해 확인되는 적절한 자격 증명 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-112">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="8ab3a-113">다양한 인증 체계가 적용된 다양한 인터넷 리소스를 사용하는 애플리케이션은 **CredentialCache** 클래스를 사용하는 것이 유용합니다. 이 애플리케이션은 모든 자격 증명을 저장하고 요청 시 제공하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-113">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="8ab3a-114">인터넷 리소스가 인증을 요청하면 <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> 메서드는 <xref:System.Net.WebRequest>를 자격 증명 요청과 함께 **AuthenticationManager** 에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-114">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="8ab3a-115">그러면 요청이 다음 프로세스에 따라 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-115">The request is then authenticated according to the following process:</span></span>  
  
1. <span data-ttu-id="8ab3a-116">**AuthenticationManager** 는 각 등록된 인증 모듈에서 모듈이 등록된 순서대로 <xref:System.Net.IAuthenticationModule.Authenticate%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-116">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="8ab3a-117">**AuthenticationManager** 는 **null** 을 반환하지 않는 첫 번째 모듈을 사용하여 인증 프로세스를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-117">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="8ab3a-118">프로세스 세부 정보는 관련된 인증 모듈 형식에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-118">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2. <span data-ttu-id="8ab3a-119">인증 프로세스가 완료되면 인증 모듈은 <xref:System.Net.Authorization>을 인터넷 리소스에 액세스하는 데 필요한 정보가 포함된 **WebRequest** 에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-119">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="8ab3a-120">일부 인증 체계에서는 리소스에 대한 요청을 먼저 만들지 않고 사용자를 인증할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-120">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="8ab3a-121">애플리케이션은 리소스에서 사용자를 사전 인증하여 서버에 대한 하나 이상의 왕복을 제거하는 방식으로 시간을 단축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-121">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="8ab3a-122">또는 나중에 사용자에게 더 빨리 응답할 수 있도록 프로그램 시작 중에 인증을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-122">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="8ab3a-123">사전 인증을 사용하는 인증 체계는 <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> 속성을 **true** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ab3a-123">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ab3a-124">참조</span><span class="sxs-lookup"><span data-stu-id="8ab3a-124">See also</span></span>

- [<span data-ttu-id="8ab3a-125">기본 인증 및 다이제스트 인증</span><span class="sxs-lookup"><span data-stu-id="8ab3a-125">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="8ab3a-126">NTLM 및 Kerberos 인증</span><span class="sxs-lookup"><span data-stu-id="8ab3a-126">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="8ab3a-127">네트워크 프로그래밍의 보안</span><span class="sxs-lookup"><span data-stu-id="8ab3a-127">Security in Network Programming</span></span>](security-in-network-programming.md)
