---
description: '자세한 정보: 방법: 보안 세션 만들기'
title: '방법: 보안 세션 만들기'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 7d1c76ed2925c3c4cca4242f3f02b8850fb64f19
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734713"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="8e53a-103">방법: 보안 세션 만들기</span><span class="sxs-lookup"><span data-stu-id="8e53a-103">How to: Create a Secure Session</span></span>

<span data-ttu-id="8e53a-104">바인딩을 제외 하 고 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , WCF (Windows Communication Foundation)의 시스템 제공 바인딩은 메시지 보안을 사용 하는 경우 자동으로 보안 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-104">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="8e53a-105">기본적으로 보안 세션은 재생된 웹 서버에 남지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-105">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="8e53a-106">보안 세션이 설정되면 클라이언트와 서비스에서 보안 세션과 연결된 키를 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-106">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="8e53a-107">메시지를 교환하면 캐시된 키의 식별자만 교환됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-107">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="8e53a-108">웹 서버가 재생되면 캐시도 재생되며, 이 때 웹 서버는 식별자의 캐시된 키를 검색할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-108">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="8e53a-109">이런 경우가 발생하면 클라이언트로 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-109">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="8e53a-110">상태 저장 SCT(보안 컨텍스트 토큰)을 사용하는 보안 세션은 웹 서버가 재생되는 동안 보안 세션을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-110">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="8e53a-111">보안 세션에서 상태 저장 SCT를 사용 하는 방법에 대 한 자세한 내용은 [방법: 보안 세션에 대 한 보안 컨텍스트 토큰 만들기](how-to-create-a-security-context-token-for-a-secure-session.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e53a-111">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="8e53a-112">서비스에서 시스템에서 제공되는 바인딩 중 하나를 사용하여 보안 세션을 사용하도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8e53a-112">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="8e53a-113">메시지 보안을 지원하는 시스템 제공 바인딩을 사용하도록 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-113">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="8e53a-114">바인딩을 제외 하 고 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) 시스템 제공 바인딩이 메시지 보안을 사용 하도록 구성 된 경우 WCF는 자동으로 보안 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-114">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="8e53a-115">다음 표에는 메시지 보안을 지원하는 시스템 제공 바인딩과 메시지 보안이 기본 보안 메커니즘인지 여부가 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-115">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="8e53a-116">시스템 제공 바인딩</span><span class="sxs-lookup"><span data-stu-id="8e53a-116">System-provided binding</span></span>|<span data-ttu-id="8e53a-117">구성 요소</span><span class="sxs-lookup"><span data-stu-id="8e53a-117">Configuration element</span></span>|<span data-ttu-id="8e53a-118">기본적으로 메시지 보안 사용</span><span class="sxs-lookup"><span data-stu-id="8e53a-118">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="8e53a-119">아니요</span><span class="sxs-lookup"><span data-stu-id="8e53a-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="8e53a-120">예</span><span class="sxs-lookup"><span data-stu-id="8e53a-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="8e53a-121">예</span><span class="sxs-lookup"><span data-stu-id="8e53a-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="8e53a-122">예</span><span class="sxs-lookup"><span data-stu-id="8e53a-122">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="8e53a-123">아니요</span><span class="sxs-lookup"><span data-stu-id="8e53a-123">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="8e53a-124">아니요</span><span class="sxs-lookup"><span data-stu-id="8e53a-124">No</span></span>|  
  
     <span data-ttu-id="8e53a-125">다음 코드 예제에서는 구성을 사용 하 여 `wsHttpBinding_Calculator` [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , 메시지 보안 및 보안 세션을 사용 하는 라는 바인딩을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-125">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="8e53a-126">다음 코드 예제에서는 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , 메시지 보안 및 보안 세션을 사용 하 여 서비스를 보호 하도록 지정 합니다 `secureCalculator` .</span><span class="sxs-lookup"><span data-stu-id="8e53a-126">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="8e53a-127">에서 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 특성을로 설정 하 여 보안 세션을 해제할 수 있습니다 `establishSecurityContext` `false` .</span><span class="sxs-lookup"><span data-stu-id="8e53a-127">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="8e53a-128">다른 시스템 제공 바인딩의 경우 사용자 지정 바인딩을 만들어야만 보안 세션을 끌 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-128">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="8e53a-129">사용자 지정 바인딩을 사용하여 서비스에서 보안 세션을 사용하도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="8e53a-129">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="8e53a-130">보안 세션을 통해 SOAP 메시지를 보호하도록 지정하는 사용자 지정 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-130">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="8e53a-131">사용자 지정 바인딩을 만드는 방법에 대 한 자세한 내용은 [방법: System-Provided 바인딩 사용자 지정](../extending/how-to-customize-a-system-provided-binding.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8e53a-131">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="8e53a-132">다음 코드 예제에서는 구성을 사용하여 보안 세션을 통해 메시지를 전송하는 사용자 지정 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-132">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="8e53a-133">다음 코드 예제에서는 <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 인증 모드를 사용하여 보안 세션을 부트스트랩하는 사용자 지정 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e53a-133">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8e53a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e53a-134">See also</span></span>

- [<span data-ttu-id="8e53a-135">WCF 바인딩 개요</span><span class="sxs-lookup"><span data-stu-id="8e53a-135">WCF Bindings Overview</span></span>](../bindings-overview.md)
