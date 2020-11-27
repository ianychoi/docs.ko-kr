---
title: 인증서 클라이언트를 사용하는 메시지 보안
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
ms.openlocfilehash: 4a1cb6d804d313f438fc8e7a92946d55f73b9ee5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96288582"
---
# <a name="message-security-with-a-certificate-client"></a><span data-ttu-id="47387-102">인증서 클라이언트를 사용하는 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="47387-102">Message Security with a Certificate Client</span></span>

<span data-ttu-id="47387-103">다음 시나리오에서는 메시지 보안 모드를 사용 하 여 보호 되는 WCF (Windows Communication Foundation) 클라이언트 및 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="47387-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured using message security mode.</span></span> <span data-ttu-id="47387-104">클라이언트 및 서비스는 인증서를 사용하여 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="47387-104">Both the client and the service are authenticated with certificates.</span></span> <span data-ttu-id="47387-105">자세한 내용은 [배포 응용 프로그램 보안](distributed-application-security.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47387-105">For more information, see [Distributed Application Security](distributed-application-security.md).</span></span>

 ![인증서가 있는 클라이언트를 보여 주는 스크린샷](./media/message-security-with-a-certificate-client/client-with-certificate.gif)  
  
 <span data-ttu-id="47387-107">응용 프로그램 예제는 [메시지 보안 인증서](../samples/message-security-certificate.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47387-107">For a sample application, see [Message Security Certificate](../samples/message-security-certificate.md).</span></span>  

|<span data-ttu-id="47387-108">특성</span><span class="sxs-lookup"><span data-stu-id="47387-108">Characteristic</span></span>|<span data-ttu-id="47387-109">Description</span><span class="sxs-lookup"><span data-stu-id="47387-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="47387-110">보안 모드</span><span class="sxs-lookup"><span data-stu-id="47387-110">Security Mode</span></span>|<span data-ttu-id="47387-111">메시지</span><span class="sxs-lookup"><span data-stu-id="47387-111">Message</span></span>|  
|<span data-ttu-id="47387-112">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="47387-112">Interoperability</span></span>|<span data-ttu-id="47387-113">WCF만</span><span class="sxs-lookup"><span data-stu-id="47387-113">WCF only</span></span>|  
|<span data-ttu-id="47387-114">인증(서버)</span><span class="sxs-lookup"><span data-stu-id="47387-114">Authentication (Server)</span></span>|<span data-ttu-id="47387-115">서비스 인증서 사용</span><span class="sxs-lookup"><span data-stu-id="47387-115">Using service certificate</span></span>|  
|<span data-ttu-id="47387-116">인증(클라이언트)</span><span class="sxs-lookup"><span data-stu-id="47387-116">Authentication (Client)</span></span>|<span data-ttu-id="47387-117">클라이언트 인증서 사용</span><span class="sxs-lookup"><span data-stu-id="47387-117">Using client certificate</span></span>|  
|<span data-ttu-id="47387-118">무결성</span><span class="sxs-lookup"><span data-stu-id="47387-118">Integrity</span></span>|<span data-ttu-id="47387-119">예</span><span class="sxs-lookup"><span data-stu-id="47387-119">Yes</span></span>|  
|<span data-ttu-id="47387-120">기밀성</span><span class="sxs-lookup"><span data-stu-id="47387-120">Confidentiality</span></span>|<span data-ttu-id="47387-121">Yes</span><span class="sxs-lookup"><span data-stu-id="47387-121">Yes</span></span>|  
|<span data-ttu-id="47387-122">전송</span><span class="sxs-lookup"><span data-stu-id="47387-122">Transport</span></span>|<span data-ttu-id="47387-123">HTTP</span><span class="sxs-lookup"><span data-stu-id="47387-123">HTTP</span></span>|  
|<span data-ttu-id="47387-124">바인딩</span><span class="sxs-lookup"><span data-stu-id="47387-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="47387-125">서비스</span><span class="sxs-lookup"><span data-stu-id="47387-125">Service</span></span>  

 <span data-ttu-id="47387-126">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="47387-127">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="47387-128">구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47387-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="47387-129">제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="47387-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="47387-130">코드</span><span class="sxs-lookup"><span data-stu-id="47387-130">Code</span></span>  

 <span data-ttu-id="47387-131">다음 코드에서는 안전한 컨텍스트를 설정하기 위해 메시지 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="47387-131">The following code shows how to create a service endpoint that uses message security to establish a secure context.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### <a name="configuration"></a><span data-ttu-id="47387-132">구성</span><span class="sxs-lookup"><span data-stu-id="47387-132">Configuration</span></span>  

 <span data-ttu-id="47387-133">코드 대신 다음 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="47387-133">The following configuration can be used instead of the code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCertificateClient"
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="47387-134">클라이언트</span><span class="sxs-lookup"><span data-stu-id="47387-134">Client</span></span>  

 <span data-ttu-id="47387-135">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-135">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="47387-136">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-136">Do one of the following:</span></span>  
  
- <span data-ttu-id="47387-137">이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47387-137">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="47387-138">엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47387-138">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="47387-139">대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-139">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="47387-140">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="47387-140">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="47387-141">코드</span><span class="sxs-lookup"><span data-stu-id="47387-141">Code</span></span>  

 <span data-ttu-id="47387-142">다음 코드에서는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="47387-142">The following code creates the client.</span></span> <span data-ttu-id="47387-143">바인딩은 메시지 모드 보안으로 설정되며 클라이언트 자격 증명 형식은 `Certificate`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="47387-143">The binding is to message mode security, and the client credential type is set to `Certificate`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### <a name="configuration"></a><span data-ttu-id="47387-144">구성</span><span class="sxs-lookup"><span data-stu-id="47387-144">Configuration</span></span>  

 <span data-ttu-id="47387-145">다음 구성에서는 엔드포인트 동작을 사용하는 클라이언트 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-145">The following configuration specifies the client certificate using an endpoint behavior.</span></span> <span data-ttu-id="47387-146">자세한 내용은 [인증서 작업](working-with-certificates.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="47387-146">For more information about certificates, see [Working with Certificates](working-with-certificates.md).</span></span> <span data-ttu-id="47387-147">또한이 코드는 <`identity`> 요소를 사용 하 여 필요한 서버 id의 DNS (Domain Name System)를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="47387-147">The code also uses an <`identity`> element to specify a Domain Name System (DNS) of the expected server identity.</span></span> <span data-ttu-id="47387-148">Id에 대 한 자세한 내용은 [서비스 id 및 인증](service-identity-and-authentication.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="47387-148">For more information about identity, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="47387-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="47387-149">See also</span></span>

- [<span data-ttu-id="47387-150">보안 개요</span><span class="sxs-lookup"><span data-stu-id="47387-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="47387-151">서비스 ID 및 인증</span><span class="sxs-lookup"><span data-stu-id="47387-151">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- [<span data-ttu-id="47387-152">인증서 사용</span><span class="sxs-lookup"><span data-stu-id="47387-152">Working with Certificates</span></span>](working-with-certificates.md)
- <span data-ttu-id="47387-153">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="47387-153">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
