---
description: '자세히 알아보기: 상호 인증서를 사용 하는 메시지 보안'
title: 상호 인증서를 사용하는 메시지 보안
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99d7a528-7ae4-4d39-a0f9-3066ea237de0
ms.openlocfilehash: c894f457dcd0fdc449c2f94eaee15004300df5fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726990"
---
# <a name="message-security-with-mutual-certificates"></a><span data-ttu-id="86c34-103">상호 인증서를 사용하는 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="86c34-103">Message Security with Mutual Certificates</span></span>

<span data-ttu-id="86c34-104">다음 시나리오에서는 메시지 보안 모드를 사용 하 여 보호 되는 Windows Communication Foundation (WCF) 서비스 및 클라이언트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-104">The following scenario shows a Windows Communication Foundation (WCF) service and client secured using message security mode.</span></span> <span data-ttu-id="86c34-105">클라이언트 및 서비스는 인증서를 사용하여 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-105">The client and the service are authenticated with certificates.</span></span>  
  
 <span data-ttu-id="86c34-106">이 시나리오는 X.509 인증서 토큰 프로필과 함께 WS-Security를 사용하므로 상호 운용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-106">This scenario is interoperable because it uses WS-Security with the X.509 certificate token profile.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="86c34-107">이 시나리오에서는 서비스 인증서의 협상을 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-107">This scenario does not perform negotiation of the service certificate.</span></span> <span data-ttu-id="86c34-108">서비스 인증서는 통신을 수행하기 전에 클라이언트에 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-108">The service certificate must be provided to the client in advance of any communication.</span></span> <span data-ttu-id="86c34-109">서버 인증서는 애플리케이션과 함께 배포하거나 대역 외 통신에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-109">The server certificate can be distributed with the application or provided in an out-of-band communication.</span></span>  
  
 <span data-ttu-id="86c34-110">![상호 인증서를 사용 하는 메시지 보안](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span><span class="sxs-lookup"><span data-stu-id="86c34-110">![Message security with mutual certificates](media/f4157312-b17c-416c-a5ee-fa7b54db211b.gif "f4157312-b17c-416c-a5ee-fa7b54db211b")</span></span>  
  
|<span data-ttu-id="86c34-111">특성</span><span class="sxs-lookup"><span data-stu-id="86c34-111">Characteristic</span></span>|<span data-ttu-id="86c34-112">설명</span><span class="sxs-lookup"><span data-stu-id="86c34-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="86c34-113">보안 모드</span><span class="sxs-lookup"><span data-stu-id="86c34-113">Security Mode</span></span>|<span data-ttu-id="86c34-114">메시지</span><span class="sxs-lookup"><span data-stu-id="86c34-114">Message</span></span>|  
|<span data-ttu-id="86c34-115">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="86c34-115">Interoperability</span></span>|<span data-ttu-id="86c34-116">예, 클라이언트 및 서비스와 호환되는 WS-Security 및 X.509 인증서 토큰 프로필과 상호 운용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-116">Yes, with WS-Security and X.509 certificate token profile compatible clients and services.</span></span>|  
|<span data-ttu-id="86c34-117">인증</span><span class="sxs-lookup"><span data-stu-id="86c34-117">Authentication</span></span>|<span data-ttu-id="86c34-118">서버와 클라이언트의 상호 인증입니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-118">Mutual authentication of the server and client.</span></span>|  
|<span data-ttu-id="86c34-119">무결성</span><span class="sxs-lookup"><span data-stu-id="86c34-119">Integrity</span></span>|<span data-ttu-id="86c34-120">예</span><span class="sxs-lookup"><span data-stu-id="86c34-120">Yes</span></span>|  
|<span data-ttu-id="86c34-121">기밀성</span><span class="sxs-lookup"><span data-stu-id="86c34-121">Confidentiality</span></span>|<span data-ttu-id="86c34-122">Yes</span><span class="sxs-lookup"><span data-stu-id="86c34-122">Yes</span></span>|  
|<span data-ttu-id="86c34-123">전송</span><span class="sxs-lookup"><span data-stu-id="86c34-123">Transport</span></span>|<span data-ttu-id="86c34-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="86c34-124">HTTP</span></span>|  
|<span data-ttu-id="86c34-125">바인딩</span><span class="sxs-lookup"><span data-stu-id="86c34-125">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="86c34-126">서비스</span><span class="sxs-lookup"><span data-stu-id="86c34-126">Service</span></span>  

 <span data-ttu-id="86c34-127">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="86c34-128">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="86c34-129">구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="86c34-130">제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="86c34-131">코드</span><span class="sxs-lookup"><span data-stu-id="86c34-131">Code</span></span>  

 <span data-ttu-id="86c34-132">다음 코드에서는 메시지 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-132">The following code shows creates a service endpoint that uses message security.</span></span> <span data-ttu-id="86c34-133">서비스는 자신을 인증하기 위한 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-133">The service requires a certificate to authenticate itself.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#13)]
 [!code-vb[C_SecurityScenarios#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#13)]  
  
### <a name="configuration"></a><span data-ttu-id="86c34-134">Configuration</span><span class="sxs-lookup"><span data-stu-id="86c34-134">Configuration</span></span>  

 <span data-ttu-id="86c34-135">다음 구성은 동일한 서비스를 만드는 데 코드 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-135">The following configuration can be used instead of the code to create the same service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="serviceCredentialBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"
                                storeLocation="LocalMachine"  
                                storeName="My"
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="serviceCredentialBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="InteropCertificateBinding"  
                  name="WSHttpBinding_ICalculator"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="InteropCertificateBinding">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"  
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="86c34-136">클라이언트</span><span class="sxs-lookup"><span data-stu-id="86c34-136">Client</span></span>  

 <span data-ttu-id="86c34-137">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-137">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="86c34-138">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-138">Do one of the following:</span></span>  
  
- <span data-ttu-id="86c34-139">이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-139">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="86c34-140">엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-140">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="86c34-141">대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-141">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="86c34-142">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="86c34-142">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="86c34-143">코드</span><span class="sxs-lookup"><span data-stu-id="86c34-143">Code</span></span>  

 <span data-ttu-id="86c34-144">다음 코드에서는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-144">The following code creates the client.</span></span> <span data-ttu-id="86c34-145">보안 모드는 Message로 설정되며 클라이언트 자격 증명 형식은 Certificate로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-145">The security mode is set to Message, and the client credential type is set to Certificate.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#20](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#20)]
 [!code-vb[C_SecurityScenarios#20](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#20)]  
  
### <a name="configuration"></a><span data-ttu-id="86c34-146">Configuration</span><span class="sxs-lookup"><span data-stu-id="86c34-146">Configuration</span></span>  

 <span data-ttu-id="86c34-147">다음과 같이 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="86c34-147">The following configures the client.</span></span> <span data-ttu-id="86c34-148">클라이언트 인증서는를 사용 하 여 지정 해야 합니다 [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="86c34-148">A client certificate must be specified using the [\<clientCertificate>](../../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span> <span data-ttu-id="86c34-149">또한 서비스 인증서는를 사용 하 여 지정 합니다 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="86c34-149">Also, the service certificate is specified using the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
                 storeLocation="CurrentUser"  
                 storeName="My"  
                 x509FindType="FindBySubjectName" />  
            <serviceCertificate>  
              <defaultCertificate findValue="Contoso.com"
                                  storeLocation="CurrentUser"  
                                  storeName="TrustedPeople"  
                                  x509FindType="FindBySubjectName" />  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate"
                     negotiateServiceCredential="false"  
                     establishSecurityContext="false" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="ClientCredentialsBehavior"  
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <certificate encodedValue="Encoded_Value_Not_Shown" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="86c34-150">참고 항목</span><span class="sxs-lookup"><span data-stu-id="86c34-150">See also</span></span>

- [<span data-ttu-id="86c34-151">보안 개요</span><span class="sxs-lookup"><span data-stu-id="86c34-151">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="86c34-152">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="86c34-152">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
- <span data-ttu-id="86c34-153">[방법: 개발 중 전송 보안을 위해 WCF에서 임시 인증서 만들기 및 설치](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="86c34-153">[How to: Create and Install Temporary Certificates in WCF for Transport Security During Development](/previous-versions/msp-n-p/ff648498(v=pandp.10))</span></span>
