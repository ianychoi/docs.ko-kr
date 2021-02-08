---
description: '다음에 대 한 자세한 정보:: <security><ws2007HttpBinding>'
title: <ws2007HttpBinding>의 <security>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: ef8b82d34b318db79db061b9c01b147e619d39c4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786813"
---
# <a name="security-of-ws2007httpbinding"></a><span data-ttu-id="f6091-103">\<ws2007HttpBinding>의 \<security></span><span class="sxs-lookup"><span data-stu-id="f6091-103">\<security> of \<ws2007HttpBinding></span></span>

<span data-ttu-id="f6091-104">요소에 사용 되는 보안 설정을 나타냅니다 [\<ws2007HttpBinding>](ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f6091-104">Represents the security settings used with the [\<ws2007HttpBinding>](ws2007httpbinding.md) element.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ws2007HttpBinding>**](ws2007httpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="f6091-105">구문</span><span class="sxs-lookup"><span data-stu-id="f6091-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6091-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="f6091-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f6091-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6091-108">특성</span><span class="sxs-lookup"><span data-stu-id="f6091-108">Attributes</span></span>  
  
|<span data-ttu-id="f6091-109">attribute</span><span class="sxs-lookup"><span data-stu-id="f6091-109">Attribute</span></span>|<span data-ttu-id="f6091-110">설명</span><span class="sxs-lookup"><span data-stu-id="f6091-110">Description</span></span>|  
|---------------|-----------------|  
|`mode`|<span data-ttu-id="f6091-111">필드.</span><span class="sxs-lookup"><span data-stu-id="f6091-111">-   Optional.</span></span> <span data-ttu-id="f6091-112">적용되는 보안 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-112">Specifies the type of security that is applied.</span></span> <span data-ttu-id="f6091-113">기본값은 `Message`입니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-113">The default is `Message`.</span></span><br /><br /> <span data-ttu-id="f6091-114">이 특성은 <xref:System.ServiceModel.SecurityMode> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="f6091-115">Mode 특성</span><span class="sxs-lookup"><span data-stu-id="f6091-115">Mode Attribute</span></span>  
  
|<span data-ttu-id="f6091-116">값</span><span class="sxs-lookup"><span data-stu-id="f6091-116">Value</span></span>|<span data-ttu-id="f6091-117">설명</span><span class="sxs-lookup"><span data-stu-id="f6091-117">Description</span></span>|  
|-----------|-----------------|  
|`None`|<span data-ttu-id="f6091-118">보안이 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-118">Security is disabled.</span></span>|  
|`Transport`|<span data-ttu-id="f6091-119">HTTPS를 사용하여 보안이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-119">Security is provided using HTTPS.</span></span> <span data-ttu-id="f6091-120">SSL(Secure Sockets Layer) 인증서를 사용하여 서비스를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-120">The service must be configured with Secure Sockets Layer (SSL) certificates.</span></span> <span data-ttu-id="f6091-121">메시지는 HTTPS를 사용하여 완전하게 보안 처리되며, 서비스는 서비스의 SSL 인증서를 사용하여 클라이언트에 의해 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-121">The message is entirely secured using HTTPS and the service is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="f6091-122">클라이언트 인증은 요소의 특성을 통해 제어 됩니다 `ClientCredentials` [\<transport>](transport-of-ws2007httpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="f6091-122">The client authentication is controlled through the `ClientCredentials` attribute of the [\<transport>](transport-of-ws2007httpbinding.md) element.</span></span>|  
|`Message`|<span data-ttu-id="f6091-123">SOAP 메시지 보안을 사용하여 보안이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-123">Security is provided using SOAP message security.</span></span> <span data-ttu-id="f6091-124">기본적으로 SOAP 본문은 암호화되고 서명됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-124">By default, the SOAP body is encrypted and signed.</span></span> <span data-ttu-id="f6091-125">이 모드는 서비스 자격 증명을 out-of-band 클라이언트에서 사용할 수 있는지 여부, 사용할 알고리즘 모음 및 <xref:System.ServiceModel.Security.SecurityMessageProperty>를 통해 메시지 본문에 적용할 보호 수준과 같은 다양한 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-125">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the <xref:System.ServiceModel.Security.SecurityMessageProperty>.</span></span> <span data-ttu-id="f6091-126">클라이언트 인증은 각 세션에 대해 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-126">Client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
|`TransportWithMessageCredential`|<span data-ttu-id="f6091-127">이 모드에서 HTTPS는 무결성, 기밀성 및 서버 인증을 제공하고 SOAP 메시지 보안은 클라이언트 인증을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-127">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="f6091-128">기본적으로 클라이언트 인증은 각 세션에 대해 한 번씩 수행되며 세션 기간 동안 인증 결과가 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-128">By default, client authentication is performed once for each session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6091-129">자식 요소</span><span class="sxs-lookup"><span data-stu-id="f6091-129">Child Elements</span></span>  
  
|<span data-ttu-id="f6091-130">요소</span><span class="sxs-lookup"><span data-stu-id="f6091-130">Element</span></span>|<span data-ttu-id="f6091-131">설명</span><span class="sxs-lookup"><span data-stu-id="f6091-131">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|<span data-ttu-id="f6091-132">전송 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-132">Defines the transport security settings.</span></span> <span data-ttu-id="f6091-133">이 요소는 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 형식에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-133">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span> <span data-ttu-id="f6091-134">이 설정은 모드를 Transport로 설정한 경우에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-134">These settings are applied only when the mode is set to Transport.</span></span>|  
|[\<message>](message-of-ws2007httpbinding.md)|<span data-ttu-id="f6091-135">메시지에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-135">Defines the security settings for the message.</span></span> <span data-ttu-id="f6091-136">이 요소는 <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 형식에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-136">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span> <span data-ttu-id="f6091-137">이 설정은 모드를 Transport로 설정한 경우에 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-137">These settings are not applied when the mode is set to Transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f6091-138">부모 요소</span><span class="sxs-lookup"><span data-stu-id="f6091-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f6091-139">요소</span><span class="sxs-lookup"><span data-stu-id="f6091-139">Element</span></span>|<span data-ttu-id="f6091-140">설명</span><span class="sxs-lookup"><span data-stu-id="f6091-140">Description</span></span>|  
|-------------|-----------------|  
|[\<ws2007HttpBinding>](ws2007httpbinding.md)|<span data-ttu-id="f6091-141">HTTP 전송 애플리케이션에 대한 보안 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-141">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6091-142">설명</span><span class="sxs-lookup"><span data-stu-id="f6091-142">Remarks</span></span>  

 <span data-ttu-id="f6091-143">이 요소는 WS-\* 사양을 구현하는 서비스와 상호 운용하도록 디자인되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-143">This element is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="f6091-144">이 바인딩의 전송 보안은 HTTP 또는 SSL(Secure Sockets Layer) over HTTP입니다.</span><span class="sxs-lookup"><span data-stu-id="f6091-144">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6091-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6091-145">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="f6091-146">서비스 및 클라이언트에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="f6091-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f6091-147">바인딩</span><span class="sxs-lookup"><span data-stu-id="f6091-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f6091-148">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="f6091-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f6091-149">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="f6091-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
