---
description: '다음에 대 한 자세한 정보:: <security><netTcpBinding>'
title: <netTcpBinding>의 <security>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: ad924f5a6ea9e003f6427ee76d3aef3afde9d083
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683075"
---
# <a name="security-of-nettcpbinding"></a><span data-ttu-id="3727b-103">\<netTcpBinding>의 \<security></span><span class="sxs-lookup"><span data-stu-id="3727b-103">\<security> of \<netTcpBinding></span></span>

<span data-ttu-id="3727b-104">바인딩에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-104">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netTcpBinding>**](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="3727b-105">구문</span><span class="sxs-lookup"><span data-stu-id="3727b-105">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3727b-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3727b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3727b-107">다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3727b-108">특성</span><span class="sxs-lookup"><span data-stu-id="3727b-108">Attributes</span></span>  
  
|<span data-ttu-id="3727b-109">attribute</span><span class="sxs-lookup"><span data-stu-id="3727b-109">Attribute</span></span>|<span data-ttu-id="3727b-110">설명</span><span class="sxs-lookup"><span data-stu-id="3727b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3727b-111">mode</span><span class="sxs-lookup"><span data-stu-id="3727b-111">mode</span></span>|<span data-ttu-id="3727b-112">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-112">Optional.</span></span> <span data-ttu-id="3727b-113">적용되는 보안 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-113">Specifies the type of security that is applied.</span></span> <span data-ttu-id="3727b-114">유효한 값이 아래에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-114">Valid values are shown below.</span></span> <span data-ttu-id="3727b-115">기본값은 `Transport`입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-115">The default value is `Transport`.</span></span><br /><br /> <span data-ttu-id="3727b-116">이 특성은 <xref:System.ServiceModel.SecurityMode> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-116">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="3727b-117">mode 특성</span><span class="sxs-lookup"><span data-stu-id="3727b-117">mode Attribute</span></span>  
  
|<span data-ttu-id="3727b-118">값</span><span class="sxs-lookup"><span data-stu-id="3727b-118">Value</span></span>|<span data-ttu-id="3727b-119">설명</span><span class="sxs-lookup"><span data-stu-id="3727b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3727b-120">없음</span><span class="sxs-lookup"><span data-stu-id="3727b-120">None</span></span>|<span data-ttu-id="3727b-121">보안이 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-121">Security is disabled.</span></span>|  
|<span data-ttu-id="3727b-122">전송</span><span class="sxs-lookup"><span data-stu-id="3727b-122">Transport</span></span>|<span data-ttu-id="3727b-123">전송 보안은 TCP를 통한 TLS 또는 SPNego를 사용하여 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-123">Transport security is provided using TLS over TCP or SPNego.</span></span> <span data-ttu-id="3727b-124">서비스는 SSL 인증서로 구성해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-124">The service may need to be configured with SSL certificates.</span></span> <span data-ttu-id="3727b-125">이 모드에서는 보호 수준을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-125">It is possible to control the protection level with this mode.</span></span>|  
|<span data-ttu-id="3727b-126">메시지</span><span class="sxs-lookup"><span data-stu-id="3727b-126">Message</span></span>|<span data-ttu-id="3727b-127">SOAP 메시지 보안을 사용하여 보안이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-127">Security is provided using SOAP message security.</span></span> <span data-ttu-id="3727b-128">기본적으로 SOAP 본문은 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-128">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="3727b-129">이 모드는 서비스 자격 증명을 클라이언트에서 밴드 외 방식으로 사용할 수 있는지 여부, 사용할 알고리즘 모음, 메시지 본문에 적용될 보호 수준과 같은 다양한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-129">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body.</span></span> <span data-ttu-id="3727b-130">클라이언트 인증은 세션당 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-130">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="3727b-131">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="3727b-131">TransportWithMessageCredential</span></span>|<span data-ttu-id="3727b-132">전송 보안이 메시지 보안과 결합되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-132">Transport security is coupled with message security.</span></span> <span data-ttu-id="3727b-133">전송 보안은 TCP를 통한 TLS 또는 SPNego를 사용하여 제공되며 무결성, 기밀성 및 서버 인증을 보장합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-133">Transport security is provided by TLS over TCP, or SPNego, and ensures integrity, confidentiality, and server authentication.</span></span> <span data-ttu-id="3727b-134">SOAP 메시지 보안에서는 클라이언트 인증이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-134">SOAP message security provides client authentication.</span></span> <span data-ttu-id="3727b-135">기본적으로 클라이언트 인증은 세션당 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-135">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3727b-136">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3727b-136">Child Elements</span></span>  
  
|<span data-ttu-id="3727b-137">요소</span><span class="sxs-lookup"><span data-stu-id="3727b-137">Element</span></span>|<span data-ttu-id="3727b-138">설명</span><span class="sxs-lookup"><span data-stu-id="3727b-138">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-nettcpbinding.md)|<span data-ttu-id="3727b-139">전송의 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-139">Defines the security settings for the transport.</span></span> <span data-ttu-id="3727b-140">이 요소는 <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-140">This element is of type <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.</span></span>|  
|[\<message>](message-element-of-nettcpbinding.md)|<span data-ttu-id="3727b-141">메시지에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-141">Defines the security settings for the message.</span></span> <span data-ttu-id="3727b-142">이 요소는 <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-142">This element is of type <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3727b-143">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3727b-143">Parent Elements</span></span>  
  
|<span data-ttu-id="3727b-144">요소</span><span class="sxs-lookup"><span data-stu-id="3727b-144">Element</span></span>|<span data-ttu-id="3727b-145">설명</span><span class="sxs-lookup"><span data-stu-id="3727b-145">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3727b-146">바인딩</span><span class="sxs-lookup"><span data-stu-id="3727b-146">binding</span></span>|<span data-ttu-id="3727b-147">의 바인딩 요소 [\<netTcpBinding>](nettcpbinding.md) 입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-147">The binding element of the [\<netTcpBinding>](nettcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3727b-148">설명</span><span class="sxs-lookup"><span data-stu-id="3727b-148">Remarks</span></span>  

 <span data-ttu-id="3727b-149">각 표준 바인딩은 전송 보안 요구 사항을 제어 하기 위한 매개 변수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-149">Each of the standard bindings provides parameters for controlling the transfer security requirements.</span></span> <span data-ttu-id="3727b-150">이러한 매개 변수에는 일반적으로 메시지 수준 또는 전송 수준 보안이 사용 되는지 여부와 선택 된 클라이언트 자격 증명 형식을 지정 하는 보안 모드가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-150">These parameters typically include the security mode that specified whether message-level or transport-level security is used and the choice of client credential type.</span></span> <span data-ttu-id="3727b-151">이러한 매개 변수가 제공 하는 옵션에 따라 적절 한 보안을 사용 하 여 채널 스택이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-151">Based on the choice of options these parameters present, a channel stack is constructed with appropriate security.</span></span>  
  
 <span data-ttu-id="3727b-152">WCF (Windows Communication Foundation)에서 제공 하는 시스템 제공 바인딩은 가장 일반적인 시나리오 요구 사항 중 일부를 충족 하도록 설계 된 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-152">The system-provided bindings supplied by Windows Communication Foundation (WCF) are a set designed to meet some of the most common scenario requirements.</span></span> <span data-ttu-id="3727b-153">이러한 각 바인딩은 특정 대상 시나리오에 대 한 보안 요구 사항을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-153">Each of these bindings allows the specification of security requirements for some specific targeted scenarios.</span></span>  
  
 <span data-ttu-id="3727b-154">이 구성 요소는 `netTcpBinding`의 보안 사양을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-154">This configuration element provides the security specifications for `netTcpBinding`.</span></span> <span data-ttu-id="3727b-155">이는 시스템 간 통신에 적합 한 안전 하 고 신뢰할 수 있으며 최적화 된 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-155">This is a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="3727b-156">기본적으로 메시지 배달을 위한 TCP, 메시지 보안 및 인증을 위한 Windows 보안, 안정성을 위한 WS-Reliable Messaging 및 이진 메시지 인코딩을 지원하는 런타임 통신 스택을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3727b-156">By default it generates a runtime communication stack supporting TCP for message delivery and Windows Security for message security and authentication, WS-ReliableMessaging for reliability, and binary message encoding.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3727b-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3727b-157">See also</span></span>

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [<span data-ttu-id="3727b-158">서비스 및 클라이언트에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="3727b-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="3727b-159">바인딩</span><span class="sxs-lookup"><span data-stu-id="3727b-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3727b-160">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="3727b-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3727b-161">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="3727b-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
