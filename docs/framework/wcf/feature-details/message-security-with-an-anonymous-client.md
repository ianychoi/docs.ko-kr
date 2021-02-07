---
description: '자세한 정보: 익명 클라이언트를 사용 하는 메시지 보안'
title: 익명 클라이언트를 사용하는 메시지 보안
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: 921ddd9e8e7d2a860f3516c452870bc2bb150911
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726977"
---
# <a name="message-security-with-an-anonymous-client"></a><span data-ttu-id="ae43c-103">익명 클라이언트를 사용하는 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="ae43c-103">Message Security with an Anonymous Client</span></span>

<span data-ttu-id="ae43c-104">다음 시나리오에서는 WCF (Windows Communication Foundation) 메시지 보안을 통해 보호 되는 클라이언트 및 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-104">The following scenario shows a client and service secured by Windows Communication Foundation (WCF) message security.</span></span> <span data-ttu-id="ae43c-105">이 디자인은 전송 보안 대신 메시지 보안을 사용하여 나중에 보다 다양한 클레임 기반 모델을 지원할 수 있도록 하는 것을 목적으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-105">A design goal is to use message security rather than transport security, so that in the future it can support a richer claims-based model.</span></span> <span data-ttu-id="ae43c-106">권한 부여에 대 한 다양 한 클레임 사용에 대 한 자세한 내용은 [Id 모델을 사용 하 여 클레임 및 권한 부여 관리](managing-claims-and-authorization-with-the-identity-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae43c-106">For more information about using rich claims for authorization, see [Managing Claims and Authorization with the Identity Model](managing-claims-and-authorization-with-the-identity-model.md).</span></span>

<span data-ttu-id="ae43c-107">응용 프로그램 예제는 [메시지 보안 익명](../samples/message-security-anonymous.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae43c-107">For a sample application, see [Message Security Anonymous](../samples/message-security-anonymous.md).</span></span>

<span data-ttu-id="ae43c-108">![익명 클라이언트를 사용 하는 메시지 보안](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span><span class="sxs-lookup"><span data-stu-id="ae43c-108">![Message security with an anonymous client](media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")</span></span>

|<span data-ttu-id="ae43c-109">특성</span><span class="sxs-lookup"><span data-stu-id="ae43c-109">Characteristic</span></span>|<span data-ttu-id="ae43c-110">설명</span><span class="sxs-lookup"><span data-stu-id="ae43c-110">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="ae43c-111">보안 모드</span><span class="sxs-lookup"><span data-stu-id="ae43c-111">Security Mode</span></span>|<span data-ttu-id="ae43c-112">메시지</span><span class="sxs-lookup"><span data-stu-id="ae43c-112">Message</span></span>|
|<span data-ttu-id="ae43c-113">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="ae43c-113">Interoperability</span></span>|<span data-ttu-id="ae43c-114">WCF만</span><span class="sxs-lookup"><span data-stu-id="ae43c-114">WCF only</span></span>|
|<span data-ttu-id="ae43c-115">인증(서버)</span><span class="sxs-lookup"><span data-stu-id="ae43c-115">Authentication (Server)</span></span>|<span data-ttu-id="ae43c-116">초기 협상에 서버 인증이 필요하지만 클라이언트 인증은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-116">Initial negotiation requires server authentication, but not client authentication</span></span>|
|<span data-ttu-id="ae43c-117">인증(클라이언트)</span><span class="sxs-lookup"><span data-stu-id="ae43c-117">Authentication (Client)</span></span>|<span data-ttu-id="ae43c-118">없음</span><span class="sxs-lookup"><span data-stu-id="ae43c-118">None</span></span>|
|<span data-ttu-id="ae43c-119">무결성</span><span class="sxs-lookup"><span data-stu-id="ae43c-119">Integrity</span></span>|<span data-ttu-id="ae43c-120">예, 공유 보안 컨텍스트 사용</span><span class="sxs-lookup"><span data-stu-id="ae43c-120">Yes, using shared security context</span></span>|
|<span data-ttu-id="ae43c-121">기밀성</span><span class="sxs-lookup"><span data-stu-id="ae43c-121">Confidentiality</span></span>|<span data-ttu-id="ae43c-122">예, 공유 보안 컨텍스트 사용</span><span class="sxs-lookup"><span data-stu-id="ae43c-122">Yes, using shared security context</span></span>|
|<span data-ttu-id="ae43c-123">전송</span><span class="sxs-lookup"><span data-stu-id="ae43c-123">Transport</span></span>|<span data-ttu-id="ae43c-124">HTTP</span><span class="sxs-lookup"><span data-stu-id="ae43c-124">HTTP</span></span>|

## <a name="service"></a><span data-ttu-id="ae43c-125">서비스</span><span class="sxs-lookup"><span data-stu-id="ae43c-125">Service</span></span>

<span data-ttu-id="ae43c-126">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ae43c-127">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-127">Do one of the following:</span></span>

- <span data-ttu-id="ae43c-128">구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-128">Create a stand-alone service using the code with no configuration.</span></span>

- <span data-ttu-id="ae43c-129">제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>

### <a name="code"></a><span data-ttu-id="ae43c-130">코드</span><span class="sxs-lookup"><span data-stu-id="ae43c-130">Code</span></span>

<span data-ttu-id="ae43c-131">다음 코드에서는 메시지 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-131">The following code shows how to create a service endpoint that uses message security.</span></span>

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a><span data-ttu-id="ae43c-132">Configuration</span><span class="sxs-lookup"><span data-stu-id="ae43c-132">Configuration</span></span>

<span data-ttu-id="ae43c-133">코드 대신 다음 구성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-133">The following configuration can be used instead of the code.</span></span> <span data-ttu-id="ae43c-134">서비스 동작 요소를 사용하여 서비스를 클라이언트에 인증하는 데 사용되는 인증서를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-134">The service behavior element is used to specify a certificate that is used to authenticate the service to the client.</span></span> <span data-ttu-id="ae43c-135">서비스 요소는 `behaviorConfiguration` 특성을 사용하여 동작을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-135">The service element must specify the behavior using the `behaviorConfiguration` attribute.</span></span> <span data-ttu-id="ae43c-136">바인딩 요소는 클라이언트 자격 증명 형식을 `None`으로 지정하여 익명 클라이언트가 서비스를 사용할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-136">The binding element specifies that the client credential type is `None`, allowing anonymous clients to use the service.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a><span data-ttu-id="ae43c-137">클라이언트</span><span class="sxs-lookup"><span data-stu-id="ae43c-137">Client</span></span>

<span data-ttu-id="ae43c-138">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-138">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ae43c-139">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-139">Do one of the following:</span></span>

- <span data-ttu-id="ae43c-140">이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-140">Create a stand-alone client using the code (and client code).</span></span>

- <span data-ttu-id="ae43c-141">엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-141">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ae43c-142">대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-142">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ae43c-143">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="ae43c-143">For example:</span></span>

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a><span data-ttu-id="ae43c-144">코드</span><span class="sxs-lookup"><span data-stu-id="ae43c-144">Code</span></span>

<span data-ttu-id="ae43c-145">다음 코드에서는 클라이언트 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-145">The following code creates an instance of the client.</span></span> <span data-ttu-id="ae43c-146">바인딩은 메시지 모드 보안을 사용하며 클라이언트 자격 증명 형식은 none으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-146">The binding uses message mode security, and the client credential type is set to none.</span></span>

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a><span data-ttu-id="ae43c-147">Configuration</span><span class="sxs-lookup"><span data-stu-id="ae43c-147">Configuration</span></span>

<span data-ttu-id="ae43c-148">다음 코드에서는 클라이언트를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ae43c-148">The following code configures the client.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ae43c-149">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae43c-149">See also</span></span>

- [<span data-ttu-id="ae43c-150">보안 개요</span><span class="sxs-lookup"><span data-stu-id="ae43c-150">Security Overview</span></span>](security-overview.md)
- [<span data-ttu-id="ae43c-151">분산 애플리케이션 보안</span><span class="sxs-lookup"><span data-stu-id="ae43c-151">Distributed Application Security</span></span>](distributed-application-security.md)
- [<span data-ttu-id="ae43c-152">Message Security Anonymous</span><span class="sxs-lookup"><span data-stu-id="ae43c-152">Message Security Anonymous</span></span>](../samples/message-security-anonymous.md)
- [<span data-ttu-id="ae43c-153">서비스 ID 및 인증</span><span class="sxs-lookup"><span data-stu-id="ae43c-153">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)
- <span data-ttu-id="ae43c-154">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ae43c-154">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
