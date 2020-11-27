---
title: WCF의 보안 동작
ms.date: 03/30/2017
ms.assetid: 513232c0-39fd-4409-bda6-5ebd5e0ea7b0
ms.openlocfilehash: 4e8452d2beb93c9ae59ef6535f45445352a48e22
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288335"
---
# <a name="security-behaviors-in-wcf"></a><span data-ttu-id="da2cf-102">WCF의 보안 동작</span><span class="sxs-lookup"><span data-stu-id="da2cf-102">Security Behaviors in WCF</span></span>

<span data-ttu-id="da2cf-103">WCF (Windows Communication Foundation)에서 동작은 서비스 수준 또는 끝점 수준에서 런타임 동작을 수정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-103">In Windows Communication Foundation (WCF), behaviors modify run-time behavior at the service level or at the endpoint level.</span></span> <span data-ttu-id="da2cf-104">일반적인 동작에 대 한 자세한 내용은 [서비스 Run-Time 동작 지정](../specifying-service-run-time-behavior.md)을 참조 하세요. *보안 동작* 을 통해 자격 증명, 인증, 권한 부여 및 감사 로그를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-104">(For more information about behaviors in general, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md).) *Security behaviors* allow control over credentials, authentication, authorization, and auditing logs.</span></span> <span data-ttu-id="da2cf-105">프로그래밍 또는 구성을 통해 동작을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-105">You can use behaviors either by programming or through configuration.</span></span> <span data-ttu-id="da2cf-106">이 항목에서는 보안 기능과 관련된 다음 동작의 구성에 대해 중점적으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-106">This topic focuses on configuring the following behaviors related to security functions:</span></span>  
  
- <span data-ttu-id="da2cf-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="da2cf-107">[\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
- <span data-ttu-id="da2cf-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span><span class="sxs-lookup"><span data-stu-id="da2cf-108">[\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md).</span></span>  
  
- <span data-ttu-id="da2cf-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span><span class="sxs-lookup"><span data-stu-id="da2cf-109">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md).</span></span>  
  
- <span data-ttu-id="da2cf-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span><span class="sxs-lookup"><span data-stu-id="da2cf-110">[\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md).</span></span>  
  
- <span data-ttu-id="da2cf-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md)를 사용 하면 클라이언트가 메타 데이터에 대해 액세스할 수 있는 보안 끝점을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-111">[\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md), which also enables you to specify a secure endpoint that clients can access for metadata.</span></span>  
  
## <a name="setting-credentials-with-behaviors"></a><span data-ttu-id="da2cf-112">동작을 통한 자격 증명 설정</span><span class="sxs-lookup"><span data-stu-id="da2cf-112">Setting Credentials with Behaviors</span></span>  

 <span data-ttu-id="da2cf-113">및를 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 사용 [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) 하 여 서비스 또는 클라이언트에 대 한 자격 증명 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-113">Use the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) and [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md) to set credential values for a service or client.</span></span> <span data-ttu-id="da2cf-114">기본 바인딩 구성은 자격 증명을 설정해야 할지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-114">The underlying binding configuration determines whether a credential has to be set.</span></span> <span data-ttu-id="da2cf-115">예를 들어, 보안 모드가 `None`으로 설정된 경우 클라이언트 및 서비스 둘 다 서로 간에 인증되지 않으며 모든 형식의 자격 증명이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-115">For example, if the security mode is set to `None`, both clients and services do not authenticate each other and require no credentials of any type.</span></span>  
  
 <span data-ttu-id="da2cf-116">반면에 서비스 바인딩의 경우 클라이언트 자격 증명 형식이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-116">On the other hand, the service binding can require a client credential type.</span></span> <span data-ttu-id="da2cf-117">이러한 경우, 동작을 사용하여 자격 증명 값을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-117">In that case, you may have to set a credential value using a behavior.</span></span> <span data-ttu-id="da2cf-118">가능한 자격 증명 형식에 대 한 자세한 내용은 [자격 증명 형식 선택](selecting-a-credential-type.md)을 참조 하세요. Windows 자격 증명을 사용 하 여 인증 하는 경우와 같은 일부 경우에는 환경에서 자동으로 실제 자격 증명 값을 설정 하 고 자격 증명 값을 명시적으로 설정할 필요가 없습니다 (다른 자격 증명 집합을 지정 하려는 경우 제외).</span><span class="sxs-lookup"><span data-stu-id="da2cf-118">(For more information about the possible types of credentials, see [Selecting a Credential Type](selecting-a-credential-type.md).) In some cases, such as when Windows credentials are used to authenticate, the environment automatically establishes the actual credential value and you do not need to explicitly set the credential value (unless you want to specify a different set of credentials).</span></span>  
  
 <span data-ttu-id="da2cf-119">모든 서비스 자격 증명은의 자식 요소로 있습니다 [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="da2cf-119">All service credentials are found as child elements of the [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md).</span></span> <span data-ttu-id="da2cf-120">다음 예제에서는 서비스 자격 증명으로 사용되는 인증서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-120">The following example shows a certificate used as a service credential.</span></span>  
  
```xml  
<configuration>  
 <system.serviceModel>  
  <behaviors>  
   <serviceBehaviors>  
    <behavior name="ServiceBehavior1">  
     <serviceCredentials>  
      <serviceCertificate findValue="000000000000000000000000000"
                          storeLocation="CurrentUser"  
      storeName="Root" x509FindType="FindByThumbprint" />  
     </serviceCredentials>  
    </behavior>  
   </serviceBehaviors>  
  </behaviors>  
 </system.serviceModel>  
</configuration>  
```  
  
## <a name="service-credentials"></a><span data-ttu-id="da2cf-121">서비스 자격 증명</span><span class="sxs-lookup"><span data-stu-id="da2cf-121">Service Credentials</span></span>  

 <span data-ttu-id="da2cf-122">에는 [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) 네 개의 자식 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-122">The [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) contains four child elements.</span></span> <span data-ttu-id="da2cf-123">요소 및 사용법에 대해서는 다음 단원에서 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-123">The elements and their usages are discussed in the following sections.</span></span>  
  
### <a name="servicecertificate-element"></a><span data-ttu-id="da2cf-124">\<serviceCertificate> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-124">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="da2cf-125">이 요소를 사용하여 메시지 보안 모드를 사용하는 클라이언트에 대한 서비스를 인증하는 데 사용할 X.509 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-125">Use this element to specify an X.509 certificate that is used to authenticate the service to clients using Message security mode.</span></span> <span data-ttu-id="da2cf-126">주기적으로 갱신되는 인증서를 사용하는 경우 지문이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-126">If you are using a certificate that is periodically renewed, then its thumbprint changes.</span></span> <span data-ttu-id="da2cf-127">이러한 경우 인증서를 동일한 주체 이름으로 다시 발급할 수 있기 때문에 주체 이름으로 `X509FindType`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-127">In that case, use the subject name as the `X509FindType` because the certificate can be reissued with the same subject name.</span></span>  
  
 <span data-ttu-id="da2cf-128">요소를 사용 하는 방법에 대 한 자세한 내용은 [방법: 클라이언트 자격 증명 값 지정을](../how-to-specify-client-credential-values.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-128">For more information about using the element, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
### <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="da2cf-129">\<certificate> of \<clientCertificate> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-129">\<certificate> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="da2cf-130">[\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md)클라이언트와 안전 하 게 통신 하기 위해 서비스에 클라이언트 인증서가 있어야 하는 경우 요소를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-130">Use the [\<certificate>](../../configure-apps/file-schema/wcf/certificate-of-clientcertificate-element.md) element when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="da2cf-131">이는 양방향 통신 패턴을 사용하는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-131">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="da2cf-132">대부분의 일반적인 요청-회신 패턴의 경우, 클라이언트는 요청 시 서비스가 클라이언트에게 해당 응답을 안전하게 보내기 위해 사용하는 인증서를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-132">In the more typical request-reply pattern, the client includes its certificate in the request, which the service uses to secure its response back to the client.</span></span> <span data-ttu-id="da2cf-133">그러나 양방향 통신 패턴에는 요청 및 회신이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-133">The duplex communication pattern, however, has no requests and replies.</span></span> <span data-ttu-id="da2cf-134">서비스는 통신에서 클라이언트의 인증서를 유추할 수 없기 때문에 서비스는 클라이언트에 대해 메시지 보안을 유지하기 위해 클라이언트 인증서를 필요로 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-134">The service cannot infer the client's certificate from the communication and therefore the service requires the client's certificate in advance to secure the messages to the client.</span></span> <span data-ttu-id="da2cf-135">클라이언트 인증서를 out-of-band 방식으로 가져와서 이 요소를 사용하여 인증서를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-135">You must obtain the client's certificate in an out-of-band manner and specify the certificate using this element.</span></span> <span data-ttu-id="da2cf-136">이중 서비스에 대 한 자세한 내용은 [방법: 이중 계약 만들기](how-to-create-a-duplex-contract.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-136">For more information about duplex services, see [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
### <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="da2cf-137">\<authentication> of \<clientCertificate> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-137">\<authentication> of \<clientCertificate> Element</span></span>  

 <span data-ttu-id="da2cf-138">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)요소를 사용 하면 클라이언트가 인증 되는 방법을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-138">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) element enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="da2cf-139">`CertificateValidationMode` 특성을 `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust` 또는 `Custom`으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-139">You can set the `CertificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="da2cf-140">기본적으로 수준은로 설정 되며,이 `ChainTrust` 는 각 인증서가 체인 맨 위의 *루트 기관* 에서 종료 되는 인증서의 계층 구조에 있어야 함을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-140">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="da2cf-141">이 모드가 가장 안전한 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-141">This is the most secure mode.</span></span> <span data-ttu-id="da2cf-142">또한 값을 `PeerOrChainTrust`로 설정할 수 있으며, 이는 자체 발급된 인증서(신뢰 피어)가 신뢰 체인에 있는 인증서와 함께 수락됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-142">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="da2cf-143">자체 발급 인증서를 신뢰할 수 있는 기관에서 구입할 필요 없기 때문에 클라이언트 및 서비스를 개발 및 디버깅하는 경우 이 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-143">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="da2cf-144">클라이언트를 배포하는 경우 `ChainTrust` 값을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-144">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="da2cf-145">또한 값을 `Custom`으로 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-145">You can also set the value to `Custom`.</span></span> <span data-ttu-id="da2cf-146">`Custom` 값으로 설정할 경우 `CustomCertificateValidatorType` 특성도 인증서 유효성을 검사하는 데 사용되는 어셈블리 및 형식으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-146">When set to the `Custom` value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="da2cf-147">사용자 지정 유효성 검사기를 만들려면 추상 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 클래스에서 상속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-147">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
### <a name="issuedtokenauthentication-element"></a><span data-ttu-id="da2cf-148">\<issuedTokenAuthentication> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-148">\<issuedTokenAuthentication> Element</span></span>  

 <span data-ttu-id="da2cf-149">발급된 토큰 시나리오에는 3단계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-149">The issued token scenario has three stages.</span></span> <span data-ttu-id="da2cf-150">첫 번째 단계에서는 서비스에 액세스 하려는 클라이언트를 STS ( *보안 토큰 서비스* ) 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-150">In the first stage, a client trying to access a service is referred to a *secure token service* (STS).</span></span> <span data-ttu-id="da2cf-151">STS는 클라이언트를 인증한 다음 일반적으로 SAML(Security Assertions Markup Language) 토큰이라는 클라이언트 토큰을 발급합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-151">The STS then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="da2cf-152">클라이언트는 토큰을 통해 서비스에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-152">The client then returns to the service with the token.</span></span> <span data-ttu-id="da2cf-153">서비스는 토큰 및 해당 클라이언트를 인증할 수 있는 데이터의 토큰을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-153">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="da2cf-154">토큰을 인증하려면 보안 토큰 서비스가 사용하는 인증서를 서비스가 인식해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-154">To authenticate the token, the certificate that the secure token service uses must be known to the service.</span></span> <span data-ttu-id="da2cf-155">[\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)요소는 이러한 보안 토큰 서비스 인증서에 대 한 리포지토리입니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-155">The [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="da2cf-156">인증서를 추가 하려면를 사용 [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-156">To add certificates, use the [\<knownCertificates>](../../configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="da2cf-157">[\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md)다음 예제와 같이 각 인증서에 대해를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-157">Insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"
           storeLocation="LocalMachine" storeName="My"
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="da2cf-158">기본적으로 인증서는 보안 토큰 서비스에서 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-158">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="da2cf-159">이러한 "알려진" 인증서는 올바른 클라이언트만 서비스에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-159">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="da2cf-160">보안 토큰을 [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) 발급 하는 STS ( *보안 토큰 서비스* )를 활용 하는 페더레이션된 응용 프로그램에서 컬렉션을 사용 해야 합니다 `SamlSecurityToken` .</span><span class="sxs-lookup"><span data-stu-id="da2cf-160">You should use the [\<allowedAudienceUris>](../../configure-apps/file-schema/wcf/allowedaudienceuris.md) collection in a federated application that utilizes a *secure token service* (STS) that issues `SamlSecurityToken` security tokens.</span></span> <span data-ttu-id="da2cf-161">STS는 보안 토큰을 발급할 때 보안 토큰에 `SamlAudienceRestrictionCondition`을 추가하여 보안 토큰을 사용할 웹 서비스의 URI를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-161">When the STS issues the security token, it can specify the URI of the Web services for which the security token is intended by adding a `SamlAudienceRestrictionCondition` to the security token.</span></span> <span data-ttu-id="da2cf-162">따라서 발급된 보안 토큰이 해당 웹 서비스용인지 검사하도록 지정하여 수신자 웹 서비스의 `SamlSecurityTokenAuthenticator`가 이를 확인하도록 할 수 있습니다. 이렇게 하려면 다음을 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-162">That allows the `SamlSecurityTokenAuthenticator` for the recipient Web service to verify that the issued security token is intended for this Web service by specifying that this check should happen by doing the following:</span></span>  
  
- <span data-ttu-id="da2cf-163">`audienceUriMode`의 특성을 [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) 또는로 설정 합니다 `Always` `BearerKeyOnly` .</span><span class="sxs-lookup"><span data-stu-id="da2cf-163">Set the `audienceUriMode` attribute of [\<issuedTokenAuthentication>](../../configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) to `Always` or `BearerKeyOnly`.</span></span>  
  
- <span data-ttu-id="da2cf-164">이 컬렉션에 URI를 추가하여 유효한 URI 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-164">Specify the set of valid URIs, by adding the URIs to this collection.</span></span> <span data-ttu-id="da2cf-165">이렇게 하려면 [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) 각 URI에 대해를 삽입 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-165">To do this, insert an [\<add>](../../configure-apps/file-schema/wcf/add-of-allowedaudienceuris.md) for each URI</span></span>  
  
 <span data-ttu-id="da2cf-166">자세한 내용은 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-166">For more information, see <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>.</span></span>  
  
 <span data-ttu-id="da2cf-167">이 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 [방법: 페더레이션 서비스 자격 증명 구성](how-to-configure-credentials-on-a-federation-service.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-167">For more information about using this configuration element, see [How to: Configure Credentials on a Federation Service](how-to-configure-credentials-on-a-federation-service.md).</span></span>  
  
#### <a name="allowing-anonymous-cardspace-users"></a><span data-ttu-id="da2cf-168">익명 CardSpace 사용자 허용</span><span class="sxs-lookup"><span data-stu-id="da2cf-168">Allowing Anonymous CardSpace Users</span></span>  

 <span data-ttu-id="da2cf-169">`AllowUntrustedRsaIssuers` 요소의 `<IssuedTokenAuthentication>` 특성을 `true`로 설정하면 명시적으로 클라이언트가 임의 RSA 키 쌍으로 서명된 자체 발급 토큰을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-169">Setting the `AllowUntrustedRsaIssuers` attribute of the `<IssuedTokenAuthentication>` element to `true` explicitly allows any client to present a self-issued token signed with an arbitrary RSA key pair.</span></span> <span data-ttu-id="da2cf-170">키에 연결 된 발급자 데이터가 없으므로 발급자를 *신뢰할 수* 없습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-170">The issuer is *untrusted* because the key has no issuer data associated with it.</span></span> <span data-ttu-id="da2cf-171">CardSpace 사용자는 자체 제공 된 id 클레임이 포함 된 자체 발급 카드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-171">A CardSpace user can create a self-issued card that includes self-provided claims of identity.</span></span> <span data-ttu-id="da2cf-172">이 기능은 주의하여 사용하십시오.</span><span class="sxs-lookup"><span data-stu-id="da2cf-172">Use this capability with caution.</span></span> <span data-ttu-id="da2cf-173">이 기능을 사용하려면 사용자 이름과 함께 데이터베이스에 저장되어야 하는 보다 안전한 암호로 RSA 공개 키를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-173">To use this feature, think of the RSA public key as a more secure password that should be stored in a database along with a user name.</span></span> <span data-ttu-id="da2cf-174">클라이언트가 서비스에 액세스하도록 허용하기 전에 클라이언트에서 제공하는 RSA 공개 키를 제공된 사용자 이름에 대해 저장된 공개 키와 비교하여 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-174">Before allowing a client access to the service, verify the client-presented RSA public key by comparing it with the stored public key for the presented user name.</span></span> <span data-ttu-id="da2cf-175">이것은 사용자가 사용자 이름을 등록하고 자체 발급된 RSA 공개 키와 연결할 수 있는 등록 프로세스를 설정한 것으로 간주합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-175">This presumes that you have established a registration process whereby users can register their user names and associate them with the self-issued RSA public keys.</span></span>  
  
## <a name="client-credentials"></a><span data-ttu-id="da2cf-176">클라이언트 자격 증명</span><span class="sxs-lookup"><span data-stu-id="da2cf-176">Client Credentials</span></span>  

 <span data-ttu-id="da2cf-177">클라이언트 자격 증명은 상호 인증이 필요한 경우 서비스에 대해 클라이언트를 인증하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-177">Client credentials are used to authenticate the client to services in cases where mutual authentication is required.</span></span> <span data-ttu-id="da2cf-178">또한 클라이언트가 서비스 인증서를 사용하여 서비스에 대한 메시지 보안을 유지해야 하는 경우 서비스 인증서를 지정하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-178">You can use the section to specify service certificates for scenarios where the client must secure messages to a service with the service's certificate.</span></span>  
  
 <span data-ttu-id="da2cf-179">보안 토큰 서비스 또는 토큰 로컬 발급자로부터 발급된 토큰을 사용하도록 클라이언트를 페더레이션 시나리오의 일부로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-179">You can also configure a client as part of a federation scenario to use issued tokens from a secure token service or a local issuer of tokens.</span></span> <span data-ttu-id="da2cf-180">페더레이션된 시나리오에 대 한 자세한 내용은 [페더레이션 및 발급 된 토큰](federation-and-issued-tokens.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-180">For more information about federated scenarios, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span> <span data-ttu-id="da2cf-181">다음 코드와 같이 모든 클라이언트 자격 증명은 아래에 있습니다 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="da2cf-181">All client credentials are found under the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md), as shown in the following code.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="EndpointBehavior1">  
   <clientCredentials>  
    <clientCertificate findValue="cn=www.contoso.com"
        storeLocation="LocalMachine"  
        storeName="AuthRoot" x509FindType="FindBySubjectName" />  
    <serviceCertificate>  
     <defaultCertificate findValue="www.cohowinery.com"
                    storeLocation="LocalMachine"  
                    storeName="Root" x509FindType="FindByIssuerName" />  
    <authentication revocationMode="Online"  
                    trustedStoreLocation="LocalMachine" />  
    </serviceCertificate>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
</behaviors>  
```  
  
#### <a name="clientcertificate-element"></a><span data-ttu-id="da2cf-182">\<clientCertificate> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-182">\<clientCertificate> Element</span></span>  

 <span data-ttu-id="da2cf-183">이 요소로 클라이언트를 인증하는 데 사용하는 인증서를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-183">Set the certificate used to authenticate the client with this element.</span></span> <span data-ttu-id="da2cf-184">자세한 내용은 [방법: 클라이언트 자격 증명 값 지정을](../how-to-specify-client-credential-values.md)참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-184">For more information, see [How to: Specify Client Credential Values](../how-to-specify-client-credential-values.md).</span></span>  
  
#### \<httpDigest>  

 <span data-ttu-id="da2cf-185">이 기능은 Windows 및 IIS(인터넷 정보 서비스)의 Active Directory를 통해 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-185">This feature must be enabled with Active Directory on Windows and Internet Information Services (IIS).</span></span> <span data-ttu-id="da2cf-186">자세한 내용은 [IIS 6.0의 다이제스트 인증](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-186">For more information, see [Digest Authentication in IIS 6.0](/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)).</span></span>  
  
#### <a name="issuedtoken-element"></a><span data-ttu-id="da2cf-187">\<issuedToken> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-187">\<issuedToken> Element</span></span>  

 <span data-ttu-id="da2cf-188">에는 [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) 토큰의 로컬 발급자를 구성 하는 데 사용 되는 요소 또는 보안 토큰 서비스에 사용 되는 동작이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-188">The [\<issuedToken>](../../configure-apps/file-schema/wcf/issuedtoken.md) contains the elements used to configure a local issuer of tokens, or behaviors used with an security token service.</span></span> <span data-ttu-id="da2cf-189">로컬 발급자를 사용 하도록 클라이언트를 구성 하는 방법에 대 한 지침은 [방법: 로컬 발급자 구성](how-to-configure-a-local-issuer.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="da2cf-189">For instructions on configuring a client to use a local issuer, see [How to: Configure a Local Issuer](how-to-configure-a-local-issuer.md).</span></span>  
  
#### \<localIssuerAddress>  

 <span data-ttu-id="da2cf-190">기본 보안 토큰 서비스 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-190">Specifies a default security token service address.</span></span> <span data-ttu-id="da2cf-191">이는가 <xref:System.ServiceModel.WSFederationHttpBinding> 보안 토큰 서비스에 대 한 URL을 제공 하지 않거나 페더레이션된 바인딩의 발급자 주소가 또는 인 경우 사용 됩니다 `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` `null` .</span><span class="sxs-lookup"><span data-stu-id="da2cf-191">This is used when the <xref:System.ServiceModel.WSFederationHttpBinding> does not supply a URL for the security token service, or when the issuer address of a federated binding is `http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous` or `null`.</span></span> <span data-ttu-id="da2cf-192">이러한 경우 로컬 발급자의 주소와 이 발급자와 통신하는 데 사용할 바인딩을 사용하여 <xref:System.ServiceModel.Description.ClientCredentials>를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-192">In such cases, the <xref:System.ServiceModel.Description.ClientCredentials> must be configured with the address of the local issuer and the binding to use to communicate with that issuer.</span></span>  
  
#### \<issuerChannelBehaviors>  

 <span data-ttu-id="da2cf-193">를 사용 [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) 하 여 보안 토큰 서비스와 통신할 때 사용 되는 WCF 클라이언트 동작을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-193">Use the [\<issuerChannelBehaviors>](../../configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md) to add WCF client behaviors used when communicating with a security token service.</span></span> <span data-ttu-id="da2cf-194">섹션에서 클라이언트 동작을 정의 [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-194">Define client behaviors in the [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) section.</span></span> <span data-ttu-id="da2cf-195">정의 된 동작을 사용 하려면 `add` `<issuerChannelBehaviors>` 두 개의 특성이 있는 요소에 <> 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-195">To use a defined behavior, add an <`add`> element to the `<issuerChannelBehaviors>` element with two attributes.</span></span> <span data-ttu-id="da2cf-196">다음 예제와 같이 `issuerAddress`를 보안 토큰 서비스의 URL로 설정하고 `behaviorConfiguration` 특성을 정의된 엔드포인트 동작 이름으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-196">Set the `issuerAddress` to the URL of the security token service and set the `behaviorConfiguration` attribute to the name of the defined endpoint behavior, as shown in the following example.</span></span>  
  
```xml  
<clientCredentials>  
   <issuedToken>  
      <issuerChannelBehaviors>  
         <add issuerAddress="http://www.contoso.com"  
               behaviorConfiguration="clientBehavior1" />
      </issuerChannelBehaviors>  
   </issuedToken>  
</clientCredentials>
```  
  
#### <a name="servicecertificate-element"></a><span data-ttu-id="da2cf-197">\<serviceCertificate> 요소</span><span class="sxs-lookup"><span data-stu-id="da2cf-197">\<serviceCertificate> Element</span></span>  

 <span data-ttu-id="da2cf-198">이 요소를 사용하여 서비스 인증서의 인증을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-198">Use this element to control authentication of service certificates.</span></span>  
  
 <span data-ttu-id="da2cf-199">[\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md)요소는 서비스에서 인증서를 지정 하지 않을 때 사용 되는 단일 인증서를 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-199">The [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) element can store a single certificate used when the service specifies no certificate.</span></span>  
  
 <span data-ttu-id="da2cf-200">및를 [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) 사용 [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) 하 여 특정 서비스와 연결 된 서비스 인증서를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-200">Use the [\<scopedCertificates>](../../configure-apps/file-schema/wcf/scopedcertificates-element.md) and [\<add>](../../configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md) to set service certificates that are associated with specific services.</span></span> <span data-ttu-id="da2cf-201">`<add>` 요소에는 인증서를 서비스와 연결하는 데 사용되는 `targetUri` 특성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-201">The `<add>` element includes a `targetUri` attribute that is used to associate the certificate with the service.</span></span>  
  
 <span data-ttu-id="da2cf-202">[\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)요소는 인증서를 인증 하는 데 사용 되는 신뢰 수준을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-202">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="da2cf-203">기본적으로 수준은 "ChainTrust"로 설정되며 이는 각 인증서가 체인 맨 위의 신뢰할 수 있는 인증 기관에서 종료되는 인증서의 계층 구조에 있어야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-203">By default, the level is set to "ChainTrust," which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="da2cf-204">이 모드가 가장 안전한 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-204">This is the most secure mode.</span></span> <span data-ttu-id="da2cf-205">또한 값을 "PeerOrChainTrust"로 설정할 수 있으며, 이는 자체 발급된 인증서(신뢰 피어)가 신뢰 체인에 있는 인증서와 함께 수락됨을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-205">You can also set the value to "PeerOrChainTrust", which specifies that self-issued certificates (peer trust) are accepted, as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="da2cf-206">자체 발급 인증서를 신뢰할 수 있는 기관에서 구입할 필요 없기 때문에 클라이언트 및 서비스를 개발 및 디버깅하는 경우 이 값이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-206">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="da2cf-207">클라이언트를 배포하는 경우 "ChainTrust" 값을 대신 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-207">When deploying a client, use the "ChainTrust" value instead.</span></span> <span data-ttu-id="da2cf-208">또한 값을 "Custom" 또는 "None"으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-208">You can also set the value to "Custom" or "None."</span></span> <span data-ttu-id="da2cf-209">"Custom" 값을 사용하려면 `CustomCertificateValidatorType` 특성도 인증서 유효성을 검증하는 데 사용되는 어셈블리 및 형식으로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-209">To use the "Custom" value, you must also set the `CustomCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="da2cf-210">사용자 지정 유효성 검사기를 만들려면 추상 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 클래스에서 상속해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-210">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="da2cf-211">자세한 내용은 [방법: 사용자 지정 인증서 유효성 검사기를 사용 하는 서비스 만들기](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-211">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="da2cf-212">요소에는 [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) `RevocationMode` 해지를 위해 인증서를 확인 하는 방법을 지정 하는 특성이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-212">The [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) element includes a `RevocationMode` attribute that specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="da2cf-213">기본값은 "online"이며, 이는 인증서 해지 여부를 자동으로 검사함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-213">The default is "online", which indicates that certificates are automatically checked for revocation.</span></span> <span data-ttu-id="da2cf-214">자세한 내용은 [Working with Certificates](working-with-certificates.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-214">For more information, see [Working with Certificates](working-with-certificates.md).</span></span>  
  
## <a name="serviceauthorization"></a><span data-ttu-id="da2cf-215">ServiceAuthorization</span><span class="sxs-lookup"><span data-stu-id="da2cf-215">ServiceAuthorization</span></span>  

 <span data-ttu-id="da2cf-216">[\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)요소에는 권한 부여, 사용자 지정 역할 공급자 및 가장에 영향을 주는 요소가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-216">The [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) element contains elements that affect authorization, custom role providers, and impersonation.</span></span>  
  
 <span data-ttu-id="da2cf-217"><xref:System.Security.Permissions.PrincipalPermissionAttribute> 클래스는 서비스 메서드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-217">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> class is applied to a service method.</span></span> <span data-ttu-id="da2cf-218">특성은 보호된 메서드의 사용 권한을 부여할 때 사용할 사용자 그룹을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-218">The attribute specifies the groups of users to use when authorizing use of a protected method.</span></span> <span data-ttu-id="da2cf-219">기본값은 "UseWindowsGroups"이며 리소스에 액세스하려는 ID에 대해 "Administrators" 또는 "Users"와 같은 Windows 그룹을 검색하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-219">The default value is "UseWindowsGroups" and specifies that Windows groups, such as "Administrators" or "Users," are searched for an identity trying to access a resource.</span></span> <span data-ttu-id="da2cf-220">다음 코드와 같이 <> 요소 아래에서 구성 된 사용자 지정 역할 공급자를 사용 하도록 "UseAspNetRoles"를 지정할 수도 있습니다 `system.web` .</span><span class="sxs-lookup"><span data-stu-id="da2cf-220">You can also specify "UseAspNetRoles" to use a custom role provider that is configured under the <`system.web` > element, as shown in the following code.</span></span>  
  
```xml  
<system.web>  
  <membership defaultProvider="SqlProvider"
   userIsOnlineTimeWindow="15">  
     <providers>  
       <clear />  
       <add
          name="SqlProvider"
          type="System.Web.Security.SqlMembershipProvider"
          connectionStringName="SqlConn"  
          applicationName="MembershipProvider"  
          enablePasswordRetrieval="false"  
          enablePasswordReset="false"  
          requiresQuestionAndAnswer="false"  
          requiresUniqueEmail="true"  
          passwordFormat="Hashed" />  
     </providers>  
   </membership>  
  <!-- Other configuration code not shown.-->  
</system.web>  
```  
  
 <span data-ttu-id="da2cf-221">다음 코드에서는 `roleProviderName` 특성과 함께 사용되는 `principalPermissionMode`을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-221">The following code shows the `roleProviderName` used with the `principalPermissionMode` attribute.</span></span>  
  
```xml  
<behaviors>  
 <behavior name="ServiceBehaviour">
  <serviceAuthorization principalPermissionMode ="UseAspNetRoles"
                        roleProviderName ="SqlProvider" />  
</behavior>
   <!-- Other configuration code not shown. -->  
</behaviors>  
```  
  
## <a name="configuring-security-audits"></a><span data-ttu-id="da2cf-222">보안 감사 구성</span><span class="sxs-lookup"><span data-stu-id="da2cf-222">Configuring Security Audits</span></span>  

 <span data-ttu-id="da2cf-223">을 사용 하 여 기록할 [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) 로그와 로깅할 이벤트 유형을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-223">Use the [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) to specify the log written to, and what types of events to log.</span></span> <span data-ttu-id="da2cf-224">자세한 내용은 [감사](auditing-security-events.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-224">For more information, see [Auditing](auditing-security-events.md).</span></span>  
  
```xml  
<behaviors>
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceSecurityAudit auditLogLocation="Application"
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"
             messageAuthenticationAuditLevel="Success" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="secure-metadata-exchange"></a><span data-ttu-id="da2cf-225">보안 메타데이터 교환</span><span class="sxs-lookup"><span data-stu-id="da2cf-225">Secure Metadata Exchange</span></span>  

 <span data-ttu-id="da2cf-226">메타데이터를 클라이언트로 내보내기는 구성 및 클라이언트 코드를 다운로드할 수 있기 때문에 서비스 및 클라이언트 개발자에게 편리한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-226">Exporting metadata to clients is convenient for service and client developers, as it enables downloads of configuration and client code.</span></span> <span data-ttu-id="da2cf-227">악의적인 사용자에 대한 서비스 노출을 줄이기 위해 HTTPS(HTTP를 통한 SSL) 메커니즘을 사용하여 전송 보안을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-227">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="da2cf-228">이렇게 하려면 먼저 적절한 X.509 인증서를 서비스를 호스트하는 컴퓨터의 특정 포트에 바인딩해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-228">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="da2cf-229">자세한 내용은 [인증서 작업](working-with-certificates.md)을 참조 하세요. 그런 [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) 다음를 서비스 구성에 추가 하 고 특성을 `HttpsGetEnabled` 로 설정 `true` 합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-229">(For more information, see [Working with Certificates](working-with-certificates.md).) Second, add a [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) to the service configuration and set the `HttpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="da2cf-230">마지막으로 다음 예제와 같이 `HttpsGetUrl` 특성을 서비스 메타데이터 엔드포인트의 URL로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="da2cf-230">Finally, set the `HttpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>  
 <serviceBehaviors>  
  <behavior name="NewBehavior">  
    <serviceMetadata httpsGetEnabled="true"
     httpsGetUrl="https://myComputerName/myEndpoint" />  
  </behavior>  
 </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="da2cf-231">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da2cf-231">See also</span></span>

- [<span data-ttu-id="da2cf-232">감사</span><span class="sxs-lookup"><span data-stu-id="da2cf-232">Auditing</span></span>](auditing-security-events.md)
- <span data-ttu-id="da2cf-233">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="da2cf-233">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
