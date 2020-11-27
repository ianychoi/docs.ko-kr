---
title: Windows 클라이언트를 사용하는 메시지 보안
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: 1fe50f711c65871b811837a7f48cf6f45f4455b4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275608"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="ffa1a-102">Windows 클라이언트를 사용하는 메시지 보안</span><span class="sxs-lookup"><span data-stu-id="ffa1a-102">Message Security with a Windows Client</span></span>

<span data-ttu-id="ffa1a-103">이 시나리오에서는 메시지 보안 모드에서 보호 되는 WCF (Windows Communication Foundation) 클라이언트 및 서버를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="ffa1a-104">클라이언트와 서비스는 Windows 자격 증명을 사용하여 인증됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="ffa1a-105">![Windows 클라이언트를 사용 하는 메시지 보안](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="ffa1a-105">![Message security with a Windows client](media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="ffa1a-106">특성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-106">Characteristic</span></span>|<span data-ttu-id="ffa1a-107">Description</span><span class="sxs-lookup"><span data-stu-id="ffa1a-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ffa1a-108">보안 모드</span><span class="sxs-lookup"><span data-stu-id="ffa1a-108">Security Mode</span></span>|<span data-ttu-id="ffa1a-109">메시지</span><span class="sxs-lookup"><span data-stu-id="ffa1a-109">Message</span></span>|  
|<span data-ttu-id="ffa1a-110">상호 운용성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-110">Interoperability</span></span>|<span data-ttu-id="ffa1a-111">WCF만</span><span class="sxs-lookup"><span data-stu-id="ffa1a-111">WCF Only</span></span>|  
|<span data-ttu-id="ffa1a-112">인증(서버)</span><span class="sxs-lookup"><span data-stu-id="ffa1a-112">Authentication (Server)</span></span>|<span data-ttu-id="ffa1a-113">서버와 클라이언트의 상호 인증</span><span class="sxs-lookup"><span data-stu-id="ffa1a-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="ffa1a-114">인증(클라이언트)</span><span class="sxs-lookup"><span data-stu-id="ffa1a-114">Authentication (Client)</span></span>|<span data-ttu-id="ffa1a-115">서버와 클라이언트의 상호 인증</span><span class="sxs-lookup"><span data-stu-id="ffa1a-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="ffa1a-116">무결성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-116">Integrity</span></span>|<span data-ttu-id="ffa1a-117">예, 공유 보안 컨텍스트 사용</span><span class="sxs-lookup"><span data-stu-id="ffa1a-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="ffa1a-118">기밀성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-118">Confidentiality</span></span>|<span data-ttu-id="ffa1a-119">예, 공유 보안 컨텍스트 사용</span><span class="sxs-lookup"><span data-stu-id="ffa1a-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="ffa1a-120">전송</span><span class="sxs-lookup"><span data-stu-id="ffa1a-120">Transport</span></span>|<span data-ttu-id="ffa1a-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="ffa1a-121">NET.TCP</span></span>|  
|<span data-ttu-id="ffa1a-122">바인딩</span><span class="sxs-lookup"><span data-stu-id="ffa1a-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="ffa1a-123">서비스</span><span class="sxs-lookup"><span data-stu-id="ffa1a-123">Service</span></span>  

 <span data-ttu-id="ffa1a-124">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ffa1a-125">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="ffa1a-126">구성 없이 코드를 사용하여 독립 실행형 서비스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="ffa1a-127">제공된 구성을 사용하여 서비스를 만들지만 엔드포인트를 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="ffa1a-128">코드</span><span class="sxs-lookup"><span data-stu-id="ffa1a-128">Code</span></span>  

 <span data-ttu-id="ffa1a-129">다음 코드에서는 Windows 컴퓨터의 안전한 컨텍스트를 설정하기 위해 메시지 보안을 사용하는 서비스 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="ffa1a-130">구성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-130">Configuration</span></span>  

 <span data-ttu-id="ffa1a-131">다음 구성은 서비스를 설정하는 데 코드 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="ffa1a-132">클라이언트</span><span class="sxs-lookup"><span data-stu-id="ffa1a-132">Client</span></span>  

 <span data-ttu-id="ffa1a-133">다음 코드와 구성은 독립적으로 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="ffa1a-134">다음 중 하나를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="ffa1a-135">이 코드와 클라이언트 코드를 사용하여 독립 실행형 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="ffa1a-136">엔드포인트 주소를 정의하지 않는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="ffa1a-137">대신 구성 이름을 인수로 사용하는 클라이언트 생성자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="ffa1a-138">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="ffa1a-139">코드</span><span class="sxs-lookup"><span data-stu-id="ffa1a-139">Code</span></span>  

 <span data-ttu-id="ffa1a-140">다음 코드에서는 클라이언트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-140">The following code creates a client.</span></span> <span data-ttu-id="ffa1a-141">바인딩은 메시지 모드 보안으로 설정되며 클라이언트 자격 증명 형식은 `Windows`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="ffa1a-142">구성</span><span class="sxs-lookup"><span data-stu-id="ffa1a-142">Configuration</span></span>  

 <span data-ttu-id="ffa1a-143">다음 구성은 클라이언트 속성을 설정하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ffa1a-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffa1a-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ffa1a-144">See also</span></span>

- [<span data-ttu-id="ffa1a-145">보안 개요</span><span class="sxs-lookup"><span data-stu-id="ffa1a-145">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="ffa1a-146">[Windows Server AppFabric 보안 모델](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ffa1a-146">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
