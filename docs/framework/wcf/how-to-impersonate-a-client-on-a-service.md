---
description: '방법에 대 한 자세한 정보: 방법: 서비스에서 클라이언트 가장'
title: '방법: 서비스에서 클라이언트 가장'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 84d50b0c22161a829da66e42b4b3bbf004b68487
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99779376"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a><span data-ttu-id="22f86-103">방법: 서비스에서 클라이언트 가장</span><span class="sxs-lookup"><span data-stu-id="22f86-103">How to: Impersonate a Client on a Service</span></span>

<span data-ttu-id="22f86-104">WCF (Windows Communication Foundation) 서비스에서 클라이언트를 가장 하면 서비스가 클라이언트를 대신 하 여 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-104">Impersonating a client on a Windows Communication Foundation (WCF) service enables the service to perform actions on behalf of the client.</span></span> <span data-ttu-id="22f86-105">예를 들어, 시스템의 디렉터리 및 파일에 대한 액세스 또는 SQL Server 데이터베이스에 대한 액세스와 같이 ACL(액세스 제어 목록) 검사 관련 작업의 경우 ACL 검사는 클라이언트 사용자 계정에 대해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-105">For actions subject to access control list (ACL) checks, such as access to directories and files on a machine or access to a SQL Server database, the ACL check is against the client user account.</span></span> <span data-ttu-id="22f86-106">이 항목에서는 Windows 도메인의 클라이언트를 사용하여 클라이언트 가장 수준을 설정하는 데 필요한 기본적인 단계에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-106">This topic shows the basic steps required to enable a client in a Windows domain to set a client impersonation level.</span></span> <span data-ttu-id="22f86-107">이와 관련된 작업 예제는 [Impersonating the Client](./samples/impersonating-the-client.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="22f86-107">For a working example of this, see [Impersonating the Client](./samples/impersonating-the-client.md).</span></span> <span data-ttu-id="22f86-108">클라이언트 가장에 대 한 자세한 내용은 [위임 및 가장](./feature-details/delegation-and-impersonation-with-wcf.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22f86-108">For more information about client impersonation, see [Delegation and Impersonation](./feature-details/delegation-and-impersonation-with-wcf.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22f86-109">클라이언트 및 서비스가 동일한 컴퓨터에서 실행 중이고 클라이언트가 시스템 계정( `Local System` 또는 `Network Service`)으로 실행 중인 경우, 상태 저장 보안 컨텍스트 토큰을 사용하여 보안 세션을 설정할 때 클라이언트를 가장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-109">When the client and service are running on the same computer and the client is running under a system account (that is, `Local System` or `Network Service`), the client cannot be impersonated when a secure session is established with stateful Security Context tokens.</span></span> <span data-ttu-id="22f86-110">일반적으로 WinForms 또는 콘솔 애플리케이션은 현재 계정에 로그인된 상태에서 실행되기 때문에 기본적으로 계정을 가장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-110">A WinForms or console application typically is run under the currently logged in account, so that account can be impersonated by default.</span></span> <span data-ttu-id="22f86-111">그러나 클라이언트가 ASP.NET 페이지이 고 해당 페이지가 IIS 6.0 또는 IIS 7.0에서 호스트 되는 경우 클라이언트는 `Network Service` 기본적으로 계정으로 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-111">However, when the client is an ASP.NET page and that page is hosted in IIS 6.0 or IIS 7.0, then the client does run under the `Network Service` account by default.</span></span> <span data-ttu-id="22f86-112">보안 세션을 지원하는 모든 시스템 제공 바인딩은 기본적으로 상태 비저장 보안 컨텍스트 토큰을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-112">All of the system-provided bindings that support secure sessions use a stateless Security Context token by default.</span></span> <span data-ttu-id="22f86-113">그러나 클라이언트가 ASP.NET 페이지이 고 상태 저장 보안 컨텍스트 토큰을 사용 하는 보안 세션을 사용 하는 경우 클라이언트를 가장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-113">However, if the client is an ASP.NET page and secure sessions with stateful Security Context tokens are used, the client cannot be impersonated.</span></span> <span data-ttu-id="22f86-114">보안 세션에서 상태 저장 보안 컨텍스트 토큰을 사용 하는 방법에 대 한 자세한 내용은 [방법: 보안 세션에 대 한 보안 컨텍스트 토큰 만들기](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22f86-114">For more information about using stateful Security Context tokens in a secure session, see [How to: Create a Security Context Token for a Secure Session](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a><span data-ttu-id="22f86-115">서비스에서 캐시된 Windows 토큰에서 클라이언트 가장을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="22f86-115">To enable impersonation of a client from a cached Windows token on a service</span></span>  
  
1. <span data-ttu-id="22f86-116">서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-116">Create the service.</span></span> <span data-ttu-id="22f86-117">이 기본 프로시저에 대한 자습서는 [Getting Started Tutorial](getting-started-tutorial.md)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="22f86-117">For a tutorial of this basic procedure, see [Getting Started Tutorial](getting-started-tutorial.md).</span></span>  
  
2. <span data-ttu-id="22f86-118"><xref:System.ServiceModel.NetTcpBinding> 또는 <xref:System.ServiceModel.WSHttpBinding>과 같이 Windows 인증을 사용하여 세션을 만드는 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-118">Use a binding that uses Windows authentication and creates a session, such as <xref:System.ServiceModel.NetTcpBinding> or <xref:System.ServiceModel.WSHttpBinding>.</span></span>  
  
3. <span data-ttu-id="22f86-119">서비스 인터페이스의 가장을 만드는 경우 <xref:System.ServiceModel.OperationBehaviorAttribute> 클래스를 클라이언트 가장이 필요한 메서드에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-119">When creating the implementation of the service's interface, apply the <xref:System.ServiceModel.OperationBehaviorAttribute> class to the method that requires client impersonation.</span></span> <span data-ttu-id="22f86-120"><xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> 속성을 <xref:System.ServiceModel.ImpersonationOption.Required>으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-120">Set the <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> property to <xref:System.ServiceModel.ImpersonationOption.Required>.</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a><span data-ttu-id="22f86-121">클라이언트에서 허용된 가장 수준으로 설정하려면</span><span class="sxs-lookup"><span data-stu-id="22f86-121">To set the allowed impersonation level on the client</span></span>  
  
1. <span data-ttu-id="22f86-122">[ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)를 사용하여 서비스 클라이언트 코드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-122">Create service client code by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="22f86-123">자세한 내용은 [WCF 클라이언트를 사용 하 여 서비스 액세스](accessing-services-using-a-wcf-client.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22f86-123">For more information, see [Accessing Services Using a WCF Client](accessing-services-using-a-wcf-client.md).</span></span>  
  
2. <span data-ttu-id="22f86-124">WCF 클라이언트를 만든 후 <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> 클래스의 속성을 <xref:System.ServiceModel.Security.WindowsClientCredential> 열거형 값 중 하나로 설정 합니다 <xref:System.Security.Principal.TokenImpersonationLevel> .</span><span class="sxs-lookup"><span data-stu-id="22f86-124">After creating the WCF client, set the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property of the <xref:System.ServiceModel.Security.WindowsClientCredential> class to one of the <xref:System.Security.Principal.TokenImpersonationLevel> enumeration values.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="22f86-125"><xref:System.Security.Principal.TokenImpersonationLevel.Delegation>을 사용하려면 협상된 Kerberos 인증( *multi-leg* 또는 *multi-step* Kerberos라고도 함)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22f86-125">To use <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, negotiated Kerberos authentication (sometimes called *multi-leg* or *multi-step* Kerberos) must be used.</span></span> <span data-ttu-id="22f86-126">이를 구현 하는 방법에 대 한 설명은 [보안에 대 한 모범 사례](./feature-details/best-practices-for-security-in-wcf.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22f86-126">For a description of how to implement this, see [Best Practices for Security](./feature-details/best-practices-for-security-in-wcf.md).</span></span>  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="22f86-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22f86-127">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [<span data-ttu-id="22f86-128">Impersonating the Client</span><span class="sxs-lookup"><span data-stu-id="22f86-128">Impersonating the Client</span></span>](./samples/impersonating-the-client.md)
- [<span data-ttu-id="22f86-129">위임 및 가장</span><span class="sxs-lookup"><span data-stu-id="22f86-129">Delegation and Impersonation</span></span>](./feature-details/delegation-and-impersonation-with-wcf.md)
