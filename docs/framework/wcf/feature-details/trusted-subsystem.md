---
title: 신뢰할 수 있는 하위 시스템
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1f5ce46b-e259-4bc9-a0b9-89d06fc9341c
ms.openlocfilehash: 93770c8f4d92a12dcfe29290c84708949d9a1d4a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293392"
---
# <a name="trusted-subsystem"></a><span data-ttu-id="6b273-102">신뢰할 수 있는 하위 시스템</span><span class="sxs-lookup"><span data-stu-id="6b273-102">Trusted Subsystem</span></span>

<span data-ttu-id="6b273-103">클라이언트는 네트워크에 분산되어 있는 하나 이상의 웹 서비스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-103">A client accesses one or more Web services that are distributed across a network.</span></span> <span data-ttu-id="6b273-104">웹 서비스는 데이터베이스 또는 기타 웹 서비스와 같은 추가 리소스에 대한 액세스가 해당 웹 서비스의 비즈니스 논리에 캡슐화되도록 디자인되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-104">The Web services are designed so that access to additional resources (such as databases or other Web services) is encapsulated in the business logic of the Web service.</span></span> <span data-ttu-id="6b273-105">이러한 리소스는 권한이 없는 액세스로부터 보호되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-105">These resources must be protected against unauthorized access.</span></span> <span data-ttu-id="6b273-106">다음 그림은 신뢰할 수 있는 하위 시스템 프로세스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-106">The following illustration depicts a trusted subsystem process.</span></span>  
  
 <span data-ttu-id="6b273-107">![신뢰할 수 있는 하위 시스템](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span><span class="sxs-lookup"><span data-stu-id="6b273-107">![Trusted subsystem](media/wcfc-trustedsubsystemc.gif "wcfc_TrustedSubsystemc")</span></span>  
  
 <span data-ttu-id="6b273-108">그림에서처럼 다음 단계에서는 신뢰할 수 있는 하위 시스템 프로세스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-108">The following steps describe the trusted subsystem process as illustrated:</span></span>  
  
1. <span data-ttu-id="6b273-109">클라이언트는 자격 증명과 함께 신뢰할 수 있는 하위 시스템에 대한 요청을 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-109">The client submits a request to the trusted subsystem, along with credentials.</span></span>  
  
2. <span data-ttu-id="6b273-110">신뢰할 수 있는 하위 시스템은 사용자를 인증하고 사용자에게 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-110">The trusted subsystem authenticates and authorizes the user.</span></span>  
  
3. <span data-ttu-id="6b273-111">신뢰할 수 있는 하위 시스템은 원격 리소스로 요청 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-111">The trusted subsystem sends a request message to the remote resource.</span></span> <span data-ttu-id="6b273-112">이 요청은 신뢰할 수 있는 하위 시스템 또는 신뢰할 수 있는 하위 시스템 프로세스가 실행 중인 서비스 계정에 대한 자격 증명과 함께 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-112">This request is accompanied by the credentials for the trusted subsystem (or the service account under which the trusted subsystem process is being executed).</span></span>  
  
4. <span data-ttu-id="6b273-113">백 엔드 리소스는 신뢰할 수 있는 하위 시스템을 인증하고 해당 시스템에 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-113">The back-end resource authenticates and authorizes the trusted subsystem.</span></span> <span data-ttu-id="6b273-114">그런 다음 해당 요청을 처리하고 신뢰할 수 있는 하위 시스템에 대한 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-114">It then processes the request and issues a response to the trusted subsystem.</span></span>  
  
5. <span data-ttu-id="6b273-115">신뢰할 수 있는 하위 시스템은 해당 응답을 처리하고 클라이언트에 자체 응답을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-115">The trusted subsystem processes the response and issues its own response to the client.</span></span>  
  
|<span data-ttu-id="6b273-116">특성</span><span class="sxs-lookup"><span data-stu-id="6b273-116">Characteristic</span></span>|<span data-ttu-id="6b273-117">Description</span><span class="sxs-lookup"><span data-stu-id="6b273-117">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6b273-118">보안 모드</span><span class="sxs-lookup"><span data-stu-id="6b273-118">Security Mode</span></span>|<span data-ttu-id="6b273-119">메시지</span><span class="sxs-lookup"><span data-stu-id="6b273-119">Message</span></span>|  
|<span data-ttu-id="6b273-120">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="6b273-120">Interoperability</span></span>|<span data-ttu-id="6b273-121">Windows Communication Foundation (WCF)만 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-121">Windows Communication Foundation (WCF) only.</span></span>|  
|<span data-ttu-id="6b273-122">인증(서비스)</span><span class="sxs-lookup"><span data-stu-id="6b273-122">Authentication (service)</span></span>|<span data-ttu-id="6b273-123">보안 토큰 서비스는 클라이언트를 인증하고 클라이언트에게 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-123">Security token service authenticates and authorizes clients.</span></span>|  
|<span data-ttu-id="6b273-124">인증(클라이언트)</span><span class="sxs-lookup"><span data-stu-id="6b273-124">Authentication (client)</span></span>|<span data-ttu-id="6b273-125">신뢰할 수 있는 하위 시스템은 클라이언트를 인증하고, 리소스는 신뢰할 수 있는 하위 시스템 서비스를 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-125">The trusted subsystem authenticates the client and the resource authenticates the trusted subsystem service.</span></span>|  
|<span data-ttu-id="6b273-126">무결성</span><span class="sxs-lookup"><span data-stu-id="6b273-126">Integrity</span></span>|<span data-ttu-id="6b273-127">예</span><span class="sxs-lookup"><span data-stu-id="6b273-127">Yes</span></span>|  
|<span data-ttu-id="6b273-128">기밀성</span><span class="sxs-lookup"><span data-stu-id="6b273-128">Confidentiality</span></span>|<span data-ttu-id="6b273-129">Yes</span><span class="sxs-lookup"><span data-stu-id="6b273-129">Yes</span></span>|  
|<span data-ttu-id="6b273-130">전송</span><span class="sxs-lookup"><span data-stu-id="6b273-130">Transport</span></span>|<span data-ttu-id="6b273-131">클라이언트와 신뢰할 수 있는 하위 시스템 서비스 간의 HTTP입니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-131">HTTP between client and the trusted subsystem service.</span></span><br /><br /> <span data-ttu-id="6b273-132">신뢰할 수 있는 하위 시스템 서비스와 리소스(백 엔드 서비스) 간의 NET.TCP입니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-132">NET.TCP between trusted subsystem service and the resource (back-end service).</span></span>|  
|<span data-ttu-id="6b273-133">바인딩</span><span class="sxs-lookup"><span data-stu-id="6b273-133">Binding</span></span>|<span data-ttu-id="6b273-134"><xref:System.ServiceModel.WSHttpBinding> 하거나 <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6b273-134"><xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding>[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)</span></span>|  
  
## <a name="resource-back-end-service"></a><span data-ttu-id="6b273-135">리소스(백 엔드 서비스)</span><span class="sxs-lookup"><span data-stu-id="6b273-135">Resource (Back-End Service)</span></span>  
  
### <a name="code"></a><span data-ttu-id="6b273-136">코드</span><span class="sxs-lookup"><span data-stu-id="6b273-136">Code</span></span>  

 <span data-ttu-id="6b273-137">다음 코드에서는 TCP 전송 프로토콜에서 전송 보안을 사용하는 리소스의 서비스 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-137">The following code shows how to create a service endpoint for the resource, which uses transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystemsResource#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsresource/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsResource#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsresource/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="6b273-138">구성</span><span class="sxs-lookup"><span data-stu-id="6b273-138">Configuration</span></span>  

 <span data-ttu-id="6b273-139">다음 구성에서는 구성을 사용하여 동일한 엔드포인트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-139">The following configuration sets up the same endpoint using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.BackendService"  
               behaviorConfiguration="BackendServiceBehavior">  
        <endpoint address="net.tcp://localhost.com:8001/BackendService"  
                  binding="customBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <bindings>  
      <customBinding>  
        <binding name="Binding1">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="BackendServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, BackendService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="trusted-subsystem"></a><span data-ttu-id="6b273-140">신뢰할 수 있는 하위 시스템</span><span class="sxs-lookup"><span data-stu-id="6b273-140">Trusted Subsystem</span></span>  
  
### <a name="code"></a><span data-ttu-id="6b273-141">코드</span><span class="sxs-lookup"><span data-stu-id="6b273-141">Code</span></span>  

 <span data-ttu-id="6b273-142">다음 코드에서는 HTTP 프로토콜에서 메시지 보안을 사용하는 신뢰할 수 있는 하위 시스템에 대한 서비스 엔드포인트와 인증용 사용자 이름 및 암호를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-142">The following code shows how to create a service endpoint for the trusted subsystem that uses message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystems#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#1)]
 [!code-vb[TrustedSubSystems#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#1)]  
  
 <span data-ttu-id="6b273-143">다음 코드에서는 TCP 전송 프로토콜에서 전송 보안을 사용하여 백 엔드 서비스와 통신하는 신뢰할 수 있는 하위 시스템의 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-143">The following code shows a service in a trusted subsystem that communicates with a back-end service using transport security over the TCP transport protocol.</span></span>  
  
 [!code-csharp[TrustedSubSystems#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystems/cs/source.cs#2)]
 [!code-vb[TrustedSubSystems#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystems/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="6b273-144">구성</span><span class="sxs-lookup"><span data-stu-id="6b273-144">Configuration</span></span>  

 <span data-ttu-id="6b273-145">다음 구성에서는 구성을 사용하여 동일한 엔드포인트를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-145">The following configuration sets up the same endpoint using configuration.</span></span> <span data-ttu-id="6b273-146">두 개의 바인딩 중 하나는 신뢰할 수 있는 하위 시스템에서 호스팅되는 서비스를 보안하고, 다른 하나는 신뢰할 수 있는 하위 시스템과 백 엔드 서비스 간의 통신을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-146">Note the two bindings: One secures the service hosted in the trusted subsystem and the other communicates between the trusted subsystem and the back-end service.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.FacadeService"  
               behaviorConfiguration="FacadeServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/FacadeService"/>  
          </baseAddresses>  
        </host>  
        <endpoint address="http://localhost:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
      </service>  
    </services>  
    <client>  
      <endpoint name=""
                address="net.tcp://contoso.com:8001/BackendService"  
                binding="customBinding"  
                bindingConfiguration="ClientBinding"  
                contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
      <customBinding>  
        <binding name="ClientBinding">  
          <security authenticationMode="UserNameOverTransport"/>  
          <windowsStreamSecurity/>  
          <tcpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="FacadeServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                storeLocation="LocalMachine"  
                                storeName="My"  
                                x509FindType="FindBySubjectName" />  
            <userNameAuthentication userNamePasswordValidationMode="Custom"  
                                    customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator, FacadeService"/>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="6b273-147">클라이언트</span><span class="sxs-lookup"><span data-stu-id="6b273-147">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="6b273-148">코드</span><span class="sxs-lookup"><span data-stu-id="6b273-148">Code</span></span>  

 <span data-ttu-id="6b273-149">다음 코드에서는 HTTP 프로토콜에서 메시지 보안을 사용하여 신뢰할 수 있는 하위 시스템과 통신하는 클라이언트와 인증용 사용자 이름 및 암호를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-149">The following code shows how to create the client that communicates with the trusted subsystem by using message security over the HTTP protocol and a user name and password for authentication.</span></span>  
  
 [!code-csharp[TrustedSubSystemsClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/trustedsubsystemsclient/cs/source.cs#1)]
 [!code-vb[TrustedSubSystemsClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/trustedsubsystemsclient/vb/source.vb#1)]  
  
### <a name="configuration"></a><span data-ttu-id="6b273-150">구성</span><span class="sxs-lookup"><span data-stu-id="6b273-150">Configuration</span></span>  

 <span data-ttu-id="6b273-151">다음 코드에서는 HTTP 프로토콜에서 메시지 보안을 사용하고, 인증용 사용자 이름과 암호를 사용하도록 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-151">The following code configures the client to use message security over the HTTP protocol and a user name and password for authentication.</span></span> <span data-ttu-id="6b273-152">사용자 이름 및 암호는 코드(구성할 수 없음)를 사용해서만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6b273-152">The user name and password can only be specified using code (it is not configurable).</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <client>  
        <endpoint name=""
                  address="http://www.cohowinery.com:8000/FacadeService"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientUserNameBehavior"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator"/>  
    </client>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientUserNameBehavior">  
          <clientCredentials>  
            <serviceCertificate>  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b273-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6b273-153">See also</span></span>

- [<span data-ttu-id="6b273-154">보안 개요</span><span class="sxs-lookup"><span data-stu-id="6b273-154">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="6b273-155">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6b273-155">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
