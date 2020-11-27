---
title: 전송 보안 개요
description: WCF 시스템 제공 바인딩의 주요 전송 보안 메커니즘에 대해 알아봅니다. 이러한 보안 메커니즘은 사용 되는 바인딩 및 전송에 따라 달라 집니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 100af5cd7bc8fe91c7498902177f47d88a25c2ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261438"
---
# <a name="transport-security-overview"></a><span data-ttu-id="bf246-104">전송 보안 개요</span><span class="sxs-lookup"><span data-stu-id="bf246-104">Transport Security Overview</span></span>

<span data-ttu-id="bf246-105">WCF (Windows Communication Foundation)의 전송 보안 메커니즘은 사용 되는 바인딩 및 전송에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-105">Transport security mechanisms in Windows Communication Foundation (WCF) depend on the binding and transport being used.</span></span> <span data-ttu-id="bf246-106">예를 들어 <xref:System.ServiceModel.WSHttpBinding> 클래스를 사용할 경우 전송은 HTTP이며, 전송 보안을 위한 기본 메커니즘은 HTTPS라고 알려진 HTTP를 통한 SSL(Secure Sockets Layer)입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-106">For example, when using the <xref:System.ServiceModel.WSHttpBinding> class, the transport is HTTP, and the primary mechanism for securing the transport is Secure Sockets Layer (SSL) over HTTP, commonly called HTTPS.</span></span> <span data-ttu-id="bf246-107">이 항목에서는 WCF 시스템에서 제공 하는 바인딩에 사용 되는 주요 전송 보안 메커니즘에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-107">This topic discusses the major transport security mechanisms used in the WCF system-provided bindings.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf246-108">.NET Framework 3.5 이상에서 SSL 보안을 사용 하는 경우 WCF 클라이언트는 인증서 저장소의 중간 인증서와 SSL 협상 중에 받은 중간 인증서를 모두 사용 하 여 서비스의 인증서에서 인증서 체인 유효성 검사를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-108">When SSL security is used with .NET Framework 3.5 and later an WCF client uses both the intermediate certificates in its certificate store and the intermediate certificates received during SSL negotiation to perform certificate chain validation on the service's certificate.</span></span> <span data-ttu-id="bf246-109">.NET Framework 3.0은 로컬 인증서 저장소에 설치된 중간 인증서만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-109">.NET Framework 3.0 only uses the intermediate certificates installed in the local certificate store.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="bf246-110">전송 보안이 사용되는 경우에는 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 속성이 덮어쓰일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-110">When transport security is used, the <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> property may be overwritten.</span></span> <span data-ttu-id="bf246-111">이러한 상황이 발생 하지 않도록 하려면 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> 를로 설정 <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType> 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-111">To prevent this from happening set the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> to <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bf246-112"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>는 서비스 설명에 설정할 수 있는 서비스 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-112"><xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> is a service behavior that can be set on the service description.</span></span>  
  
## <a name="basichttpbinding"></a><span data-ttu-id="bf246-113">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-113">BasicHttpBinding</span></span>  

 <span data-ttu-id="bf246-114">기본적으로 <xref:System.ServiceModel.BasicHttpBinding> 클래스는 보안을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-114">By default, the <xref:System.ServiceModel.BasicHttpBinding> class does not provide security.</span></span> <span data-ttu-id="bf246-115">이 바인딩은 보안을 구현하지 않는 웹 서비스 공급자와의 상호 운용성을 위해 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-115">This binding is designed for interoperability with Web service providers that do not implement security.</span></span> <span data-ttu-id="bf246-116">하지만 <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> 속성을 <xref:System.ServiceModel.BasicHttpSecurityMode.None> 이외의 값으로 설정하여 보안으로 전환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-116">However, you can switch on security by setting the <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> property to any value except <xref:System.ServiceModel.BasicHttpSecurityMode.None>.</span></span> <span data-ttu-id="bf246-117">전송 보안을 사용하려면 속성을 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-117">To enable transport security, set the property to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.</span></span>  
  
### <a name="interoperation-with-iis"></a><span data-ttu-id="bf246-118">IIS와의 상호 운용</span><span class="sxs-lookup"><span data-stu-id="bf246-118">Interoperation with IIS</span></span>  

 <span data-ttu-id="bf246-119"><xref:System.ServiceModel.BasicHttpBinding> 클래스는 기존의 웹 서비스와 상호 운용하는 데 주로 사용되고, 이러한 서비스의 대부분은 IIS(인터넷 정보 서비스)에 의해 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-119">The <xref:System.ServiceModel.BasicHttpBinding> class is primarily used to interoperate with existing Web services, and many of those services are hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="bf246-120">따라서 이 바인딩에 대한 전송 보안은 IIS 사이트와 매끄럽게 상호 운용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-120">Consequently, the transport security for this binding is designed for seamless interoperation with IIS sites.</span></span> <span data-ttu-id="bf246-121">이를 위해서는 보안 모드를<xref:System.ServiceModel.BasicHttpSecurityMode.Transport>로 설정한 다음 클라이언트 자격 증명 형식을 설정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-121">This is done by setting the security mode to <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> and then setting the client credential type.</span></span> <span data-ttu-id="bf246-122">자격 증명 형식 값은 IIS 디렉터리 보안 메커니즘에 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-122">The credential type values correspond to IIS directory security mechanisms.</span></span> <span data-ttu-id="bf246-123">다음 코드에서는 설정되는 모드와 Windows로 설정된 자격 증명 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-123">The following code shows the mode being set and the credential type set to Windows.</span></span> <span data-ttu-id="bf246-124">이러한 구성은 클라이언트와 서버가 같은 Windows 도메인에 있는 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-124">You can use this configuration when both client and server are on the same Windows domain.</span></span>  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 <span data-ttu-id="bf246-125">또는 다음 구성을 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-125">Or, in configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="bf246-126">다음 단원에서는 기타 다른 클라이언트 자격 증명 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-126">The following sections discuss other client credential types.</span></span>  
  
#### <a name="basic"></a><span data-ttu-id="bf246-127">기본</span><span class="sxs-lookup"><span data-stu-id="bf246-127">Basic</span></span>  

 <span data-ttu-id="bf246-128">IIS의 기본 인증 방식입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-128">This corresponds to the Basic authentication method in IIS.</span></span> <span data-ttu-id="bf246-129">이 모드를 사용하려면 Windows 사용자 계정과 적절한 NTFS 파일 시스템 권한으로 IIS 서버를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-129">When using this mode, the IIS server must be configured with Windows user accounts and appropriate NTFS file system permissions.</span></span> <span data-ttu-id="bf246-130">IIS 6.0에 대 한 자세한 내용은 [기본 인증 사용 및 영역 이름 구성](/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-130">For more information about IIS 6.0, see [Enabling Basic Authentication and Configuring the Realm Name](/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)).</span></span> <span data-ttu-id="bf246-131">IIS 7.0에 대 한 자세한 내용은 [기본 인증 구성 (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-131">For more information about IIS 7.0, see [Configure Basic Authentication (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).</span></span>  
  
#### <a name="certificate"></a><span data-ttu-id="bf246-132">인증서</span><span class="sxs-lookup"><span data-stu-id="bf246-132">Certificate</span></span>  

 <span data-ttu-id="bf246-133">IIS에는 클라이언트가 인증서를 사용하여 로그온해야 하는 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-133">IIS has an option to require clients to log on with a certificate.</span></span> <span data-ttu-id="bf246-134">또한 이 기능을 사용하면 IIS에서 클라이언트 인증서를 Windows 계정에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-134">The feature also enables IIS to map a client certificate to a Windows account.</span></span> <span data-ttu-id="bf246-135">IIS 6.0에 대 한 자세한 내용은 [iis 6.0에서 클라이언트 인증서 사용](/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10))을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf246-135">For more information about IIS 6.0, see [Enabling Client Certificates in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)).</span></span> <span data-ttu-id="bf246-136">IIS 7.0에 대 한 자세한 내용은 [iis 7에서 서버 인증서 구성](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf246-136">For more information about IIS 7.0, see [Configuring Server Certificates in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).</span></span>  
  
#### <a name="digest"></a><span data-ttu-id="bf246-137">다이제스트</span><span class="sxs-lookup"><span data-stu-id="bf246-137">Digest</span></span>  

 <span data-ttu-id="bf246-138">다이제스트 인증은 기본 인증과 비슷하지만 자격 증명을 일반 텍스트가 아닌 해시로 보낼 수 있는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-138">Digest authentication is similar to Basic authentication, but offers the advantage of sending the credentials as a hash, instead of in clear text.</span></span> <span data-ttu-id="bf246-139">IIS 6.0에 대 한 자세한 내용은 [iis 6.0의 다이제스트 인증](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-139">For more information about IIS 6.0, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span> <span data-ttu-id="bf246-140">IIS 7.0에 대 한 자세한 내용은 [다이제스트 인증 구성 (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-140">For more information about IIS 7.0, see [Configure Digest Authentication (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).</span></span>  
  
#### <a name="windows"></a><span data-ttu-id="bf246-141">Windows</span><span class="sxs-lookup"><span data-stu-id="bf246-141">Windows</span></span>  

 <span data-ttu-id="bf246-142">IIS의 Windows 통합 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-142">This corresponds to integrated Windows authentication in IIS.</span></span> <span data-ttu-id="bf246-143">이 값으로 설정하는 경우 도메인 컨트롤러가 Kerberos 프로토콜인 Windows 도메인에 서버가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-143">When set to this value, the server is also expected to exist on a Windows domain that uses the Kerberos protocol as its domain controller.</span></span> <span data-ttu-id="bf246-144">서버가 Kerberos 기반 도메인에 있지 않거나 Kerberos 시스템에 오류가 있는 경우에는 다음 단원에 설명되어 있는 NTLM(NT LAN Manager) 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-144">If the server is not on a Kerberos-backed domain, or if the Kerberos system fails, you can use the NT LAN Manager (NTLM) value described in the next section.</span></span> <span data-ttu-id="bf246-145">IIS 6.0에 대 한 자세한 내용은 [iis 6.0의 Windows 통합 인증](/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-145">For more information about IIS 6.0, see [Integrated Windows Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)).</span></span> <span data-ttu-id="bf246-146">IIS 7.0에 대 한 자세한 내용은 [iis 7에서 서버 인증서 구성](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf246-146">For more information about IIS 7.0, see [Configuring Server Certificates in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).</span></span>
  
#### <a name="ntlm"></a><span data-ttu-id="bf246-147">NTLM</span><span class="sxs-lookup"><span data-stu-id="bf246-147">NTLM</span></span>  

 <span data-ttu-id="bf246-148">Kerberos 프로토콜에 오류가 있는 경우 이를 통해 서버가 인증에 NTLM을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-148">This enables the server to use NTLM for authentication if the Kerberos protocol fails.</span></span> <span data-ttu-id="bf246-149">IIS 6.0에서 IIS를 구성 하는 방법에 대 한 자세한 내용은 [NTLM 인증 강제](/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10))적용을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-149">For more information about configuring IIS in IIS 6.0, see [Forcing NTLM Authentication](/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)).</span></span> <span data-ttu-id="bf246-150">IIS 7.0의 경우 Windows 인증에 NTLM 인증이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-150">For IIS 7.0, the Windows authentication includes NTLM authentication.</span></span> <span data-ttu-id="bf246-151">자세한 내용은 [IIS 7에서 서버 인증서 구성](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10))을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="bf246-151">For more information, see [Configuring Server Certificates in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).</span></span>
  
## <a name="wshttpbinding"></a><span data-ttu-id="bf246-152">WsHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-152">WsHttpBinding</span></span>  

 <span data-ttu-id="bf246-153"><xref:System.ServiceModel.WSHttpBinding> 클래스는 WS-\* 사양을 구현하는 서비스와 상호 운용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-153">The <xref:System.ServiceModel.WSHttpBinding> class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="bf246-154">이 바인딩의 전송 보안은 HTTP 또는 SSL(Secure Sockets Layer) over HTTP입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-154">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span> <span data-ttu-id="bf246-155">SSL을 사용 하는 WCF 응용 프로그램을 만들려면 IIS를 사용 하 여 응용 프로그램을 호스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-155">To create an WCF application that uses SSL, use IIS to host the application.</span></span> <span data-ttu-id="bf246-156">또는 자체 호스팅 애플리케이션을 만들려면 HttpCfg.exe 도구를 사용하여 X.509 인증서를 컴퓨터의 특정 포트에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-156">Alternatively, if you are creating a self-hosted application, use the HttpCfg.exe tool to bind an X.509 certificate to a specific port on a computer.</span></span> <span data-ttu-id="bf246-157">포트 번호는 WCF 응용 프로그램의 일부로 끝점 주소로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-157">The port number is specified as part of the WCF application as an endpoint address.</span></span> <span data-ttu-id="bf246-158">전송 모드 사용 시 엔드포인트 주소에 HTTPS 프로토콜이 포함되어야 하고, 그렇지 않으면 런타임에 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-158">When using transport mode, the endpoint address must include the HTTPS protocol or an exception will be thrown at run time.</span></span> <span data-ttu-id="bf246-159">자세한 내용은 [HTTP 전송 보안](http-transport-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-159">For more information, see [HTTP Transport Security](http-transport-security.md).</span></span>  
  
 <span data-ttu-id="bf246-160">클라이언트 인증의 경우 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 클래스의 <xref:System.ServiceModel.HttpTransportSecurity> 속성을 <xref:System.ServiceModel.HttpClientCredentialType> 열거형 값 중 하나로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-160">For client authentication, set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to one of the <xref:System.ServiceModel.HttpClientCredentialType> enumeration values.</span></span> <span data-ttu-id="bf246-161">열거형 값은 <xref:System.ServiceModel.BasicHttpBinding>에 대한 클라이언트 자격 증명 형식과 같으며 IIS 서비스와 호스팅되도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-161">The enumeration values are identical to the client credential types for <xref:System.ServiceModel.BasicHttpBinding> and are designed to be hosted with IIS services.</span></span>  
  
 <span data-ttu-id="bf246-162">다음 예제에서는 Windows 클라이언트 자격 증명 형식과 함께 사용되는 바인딩을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-162">The following example shows the binding being used with a client credential type of Windows.</span></span>  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a><span data-ttu-id="bf246-163">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-163">WSDualHttpBinding</span></span>  

 <span data-ttu-id="bf246-164">이 바인딩에서는 전송 수준 보안이 아닌 메시지 수준 보안만을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-164">This binding provides only message-level security, not transport-level security.</span></span>  
  
## <a name="nettcpbinding"></a><span data-ttu-id="bf246-165">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-165">NetTcpBinding</span></span>  

 <span data-ttu-id="bf246-166"><xref:System.ServiceModel.NetTcpBinding> 클래스는 메시지 전송에 TCP를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-166">The <xref:System.ServiceModel.NetTcpBinding> class uses TCP for message transport.</span></span> <span data-ttu-id="bf246-167">전송 모드에 대한 보안은 TCP를 통한 TLS(전송 계층 보안) 구현을 통해 제공되며</span><span class="sxs-lookup"><span data-stu-id="bf246-167">Security for the transport mode is provided by implementing Transport Layer Security (TLS) over TCP.</span></span> <span data-ttu-id="bf246-168">TLS 구현은 운영 체제에 의해 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-168">The TLS implementation is provided by the operating system.</span></span>  
  
 <span data-ttu-id="bf246-169">다음 코드에서와 같이<xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 클래스의 <xref:System.ServiceModel.TcpTransportSecurity> 속성을 <xref:System.ServiceModel.TcpClientCredentialType> 값 중 하나로 설정하여 클라이언트의 자격 증명 형식을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-169">You can also specify the client's credential type by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.TcpTransportSecurity> class to one of the <xref:System.ServiceModel.TcpClientCredentialType> values, as shown in the following code.</span></span>  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a><span data-ttu-id="bf246-170">클라이언트</span><span class="sxs-lookup"><span data-stu-id="bf246-170">Client</span></span>  

 <span data-ttu-id="bf246-171">클라이언트에서는 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 클래스의 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 메서드를 사용하여 인증서를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-171">On the client, you must specify a certificate using the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf246-172">Windows 보안을 사용하는 경우 인증서는 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-172">If you are using Windows security, a certificate is not required.</span></span>  
  
 <span data-ttu-id="bf246-173">다음 코드에서는 인증서를 고유하게 식별하는 인증서의 지문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-173">The following code uses the thumbprint of the certificate, which uniquely identifies it.</span></span> <span data-ttu-id="bf246-174">자세한 내용은 [인증서 작업](working-with-certificates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-174">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 <span data-ttu-id="bf246-175">또는 동작 섹션의 요소를 사용 하 여 클라이언트의 구성에서 인증서를 지정 합니다 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="bf246-175">Alternatively, specify the certificate in the client's configuration using a [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) element in the behaviors section.</span></span>  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"
      storeLocation="LocalMachine" storeName="My"
      X509FindType="FindByThumbPrint">  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>
```  
  
## <a name="netnamedpipebinding"></a><span data-ttu-id="bf246-176">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-176">NetNamedPipeBinding</span></span>  

 <span data-ttu-id="bf246-177"><xref:System.ServiceModel.NetNamedPipeBinding> 클래스는 컴퓨터 내의 효율적 통신을 위해 디자인되었습니다. 명명된 파이프 채널을 동일한 네트워크에 있는 두 컴퓨터 간에 만들 수도 있지만, 이 클래스는 동일한 컴퓨터에서 실행되는 프로세스를 위해 만들어진 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-177">The <xref:System.ServiceModel.NetNamedPipeBinding> class is designed for efficient intra-machine communication; that is, for processes running on the same computer, although named pipe channels can be created between two computers on the same network.</span></span> <span data-ttu-id="bf246-178">이 바인딩에서는 전송 수준 보안만을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-178">This binding provides only transport-level security.</span></span> <span data-ttu-id="bf246-179">이 바인딩을 사용하는 애플리케이션을 만들려면 엔드포인트 주소에는 &quot;net.pipe&quot;가 엔드포인트 주소의 프로토콜로 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-179">When creating applications using this binding, the endpoint addresses must include "net.pipe" as the protocol of the endpoint address.</span></span>  
  
## <a name="wsfederationhttpbinding"></a><span data-ttu-id="bf246-180">WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-180">WSFederationHttpBinding</span></span>  

 <span data-ttu-id="bf246-181">이 바인딩에서는 전송 보안을 사용할 때 HTTPS라고도 하는 HTTP를 통한 SSL을 발급된 토큰(<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>)과 함께 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-181">When using transport security, this binding uses SSL over HTTP, known as HTTPS with an issued token (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>).</span></span> <span data-ttu-id="bf246-182">페더레이션 응용 프로그램에 대 한 자세한 내용은 [페더레이션 및 발급 된 토큰](federation-and-issued-tokens.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-182">For more information about federation applications, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span>  
  
## <a name="netpeertcpbinding"></a><span data-ttu-id="bf246-183">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-183">NetPeerTcpBinding</span></span>  

 <span data-ttu-id="bf246-184"><xref:System.ServiceModel.NetPeerTcpBinding> 클래스는 피어 투 피어 네트워킹 기능을 사용하는 효율적인 통신을 위해 디자인된 보안 전송입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-184">The <xref:System.ServiceModel.NetPeerTcpBinding> class is a secure transport that is designed for efficient communication using the peer-to-peer networking feature.</span></span> <span data-ttu-id="bf246-185">클래스 및 바인딩의 이름에서 알 수 있듯이 TCP가 프로토콜입니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-185">As indicated by the name of the class and binding, TCP is the protocol.</span></span> <span data-ttu-id="bf246-186">보안 모드가 전송으로 설정되어 있는 경우 바인딩은 TCP를 통한 TLS를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="bf246-186">When the security mode is set to Transport, the binding implements TLS over TCP.</span></span> <span data-ttu-id="bf246-187">피어 투 피어 기능에 대 한 자세한 내용은 [피어 투 피어 네트워킹](peer-to-peer-networking.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-187">For more information about the peer-to-peer feature, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a><span data-ttu-id="bf246-188">MsmqIntegrationBinding 및 NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="bf246-188">MsmqIntegrationBinding and NetMsmqBinding</span></span>  

 <span data-ttu-id="bf246-189">메시지 큐 (이전에는 MSMQ 라고 함)를 사용한 전송 보안에 대 한 자세한 설명은 [전송 보안을 사용 하 여 메시지 보안](securing-messages-using-transport-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bf246-189">For a complete discussion of transport security with Message Queuing (previously called MSMQ), see [Securing Messages Using Transport Security](securing-messages-using-transport-security.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf246-190">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bf246-190">See also</span></span>

- [<span data-ttu-id="bf246-191">WCF 보안 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="bf246-191">Programming WCF Security</span></span>](programming-wcf-security.md)
