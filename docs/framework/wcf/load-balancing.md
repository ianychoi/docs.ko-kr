---
title: 부하 분산
ms.date: 03/30/2017
helpviewer_keywords:
- load balancing [WCF]
ms.assetid: 148e0168-c08d-4886-8769-776d0953b80f
ms.openlocfilehash: ccafce51cadba588dc6c4e8fc8b476f3cd8ee699
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262712"
---
# <a name="load-balancing"></a><span data-ttu-id="b4f27-102">부하 분산</span><span class="sxs-lookup"><span data-stu-id="b4f27-102">Load Balancing</span></span>

<span data-ttu-id="b4f27-103">WCF (Windows Communication Foundation) 응용 프로그램의 용량을 높이는 한 가지 방법은 부하 분산 된 서버 팜에 배포 하 여 확장 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-103">One way to increase the capacity of Windows Communication Foundation (WCF) applications is to scale them out by deploying them into a load-balanced server farm.</span></span> <span data-ttu-id="b4f27-104">WCF 응용 프로그램은 Windows 네트워크 부하 분산과 같은 소프트웨어 부하 분산 장치 및 하드웨어 기반 부하 분산 어플라이언스를 비롯 한 표준 부하 분산 기술을 사용 하 여 부하를 분산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-104">WCF applications can be load balanced using standard load balancing techniques, including software load balancers such as Windows Network Load Balancing as well as hardware-based load balancing appliances.</span></span>  
  
 <span data-ttu-id="b4f27-105">다음 섹션에서는 다양 한 시스템 제공 바인딩을 사용 하 여 빌드된 WCF 응용 프로그램의 부하 분산에 대 한 고려 사항을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-105">The following sections discuss considerations for load balancing WCF applications built using various system-provided bindings.</span></span>  
  
## <a name="load-balancing-with-the-basic-http-binding"></a><span data-ttu-id="b4f27-106">기본 HTTP 바인딩을 사용한 부하 분산</span><span class="sxs-lookup"><span data-stu-id="b4f27-106">Load Balancing with the Basic HTTP Binding</span></span>  

 <span data-ttu-id="b4f27-107">부하 분산 측면에서,를 사용 하 여 통신 하는 WCF 응용 프로그램 <xref:System.ServiceModel.BasicHttpBinding> 은 다른 공용 형식의 HTTP 네트워크 트래픽 (정적 HTML 콘텐츠, ASP.NET 페이지 또는 ASMX 웹 서비스)과 다르지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-107">From the perspective of load balancing, WCF applications that communicate using the <xref:System.ServiceModel.BasicHttpBinding> are no different than other common types of HTTP network traffic (static HTML content, ASP.NET pages, or ASMX Web Services).</span></span> <span data-ttu-id="b4f27-108">이 바인딩을 사용 하는 WCF 채널은 기본적으로 상태 비저장 이며 채널이 닫힐 때 연결을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-108">WCF channels that use this binding are inherently stateless, and terminate their connections when the channel closes.</span></span> <span data-ttu-id="b4f27-109">따라서 <xref:System.ServiceModel.BasicHttpBinding>은 기존의 HTTP 부하 분산 기술과 호환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-109">As such, the <xref:System.ServiceModel.BasicHttpBinding> works well with existing HTTP load balancing techniques.</span></span>  
  
 <span data-ttu-id="b4f27-110">기본적으로 <xref:System.ServiceModel.BasicHttpBinding>은 `Keep-Alive` 값을 사용하여 메시지의 연결 HTTP 헤더를 보내는데, 이를 통해 클라이언트는 영구 연결을 지원하는 서비스에 대해 이러한 연결을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-110">By default, the <xref:System.ServiceModel.BasicHttpBinding> sends a connection HTTP header in messages with a `Keep-Alive` value, which enables clients to establish persistent connections to the services that support them.</span></span> <span data-ttu-id="b4f27-111">또한 이 구성에서는 이전에 설정된 연결을 다시 사용하여 이후 메시지를 동일한 서버에 보낼 수 있으므로 처리량을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-111">This configuration offers enhanced throughput because previously established connections can be reused to send subsequent messages to the same server.</span></span> <span data-ttu-id="b4f27-112">하지만 연결을 다시 사용하면 클라이언트가 부하 분산 팜의 특정 서버에만 강력하게 연결되어 라운드 로빈 부하 분산의 효율성이 떨어집니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-112">However, connection reuse may cause clients to become strongly associated to a specific server within the load-balanced farm, which reduces the effectiveness of round-robin load balancing.</span></span> <span data-ttu-id="b4f27-113">이를 방지하려면, `Keep-Alive` 또는 사용자 정의 <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A>에 <xref:System.ServiceModel.Channels.CustomBinding> 속성을 사용하여 서버에서 HTTP <xref:System.ServiceModel.Channels.Binding>를 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-113">If this behavior is undesirable, HTTP `Keep-Alive` can be disabled on the server using the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> property with a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="b4f27-114">다음 예제에서는 구성을 사용하여 이 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-114">The following example shows how to do this using configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
 <system.serviceModel>  
  <services>  
   <service
     name="Microsoft.ServiceModel.Samples.CalculatorService"  
     behaviorConfiguration="CalculatorServiceBehavior">  
     <host>  
      <baseAddresses>  
       <add baseAddress="http://localhost:8000/servicemodelsamples/service"/>  
      </baseAddresses>  
     </host>  
    <!-- configure http endpoint, use base address provided by host  
         And the customBinding -->  
     <endpoint address=""  
           binding="customBinding"  
           bindingConfiguration="HttpBinding"
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
   </service>  
  </services>  
  
  <bindings>  
    <customBinding>  
  
    <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
      <binding name="HttpBinding" keepAliveEnabled="False"/>  
  
    </customBinding>  
  </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b4f27-115">.NET Framework 4에서 도입 된 단순화 된 구성을 사용 하 여 다음과 같은 간소화 된 구성을 사용 하 여 동일한 동작을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-115">Using the simplified configuration introduced in .NET Framework 4, the same behavior can be accomplished using the following simplified configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
 <system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="customBinding" />  
    </protocolMapping>  
    <bindings>  
      <customBinding>  
  
      <!-- Configure a CustomBinding that disables keepAliveEnabled-->  
        <binding keepAliveEnabled="False"/>  
  
      </customBinding>  
    </bindings>  
 </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="b4f27-116">기본 엔드포인트, 바인딩 및 동작에 대한 자세한 내용은 [단순화된 구성](simplified-configuration.md) 및 [WCF 서비스를 위한 단순화된 구성](./samples/simplified-configuration-for-wcf-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4f27-116">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="load-balancing-with-the-wshttp-binding-and-the-wsdualhttp-binding"></a><span data-ttu-id="b4f27-117">WSHttp 바인딩 및 WSDualHttp 바인딩을 사용한 부하 분산</span><span class="sxs-lookup"><span data-stu-id="b4f27-117">Load Balancing with the WSHttp Binding and the WSDualHttp Binding</span></span>  

 <span data-ttu-id="b4f27-118">기본 바인딩 구성을 일부 수정한다면, HTTP 부하 분산 기술을 사용하여 <xref:System.ServiceModel.WSHttpBinding>과 <xref:System.ServiceModel.WSDualHttpBinding>을 모두 부하 분산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-118">Both the <xref:System.ServiceModel.WSHttpBinding> and the <xref:System.ServiceModel.WSDualHttpBinding> can be load balanced using HTTP load balancing techniques provided several modifications are made to the default binding configuration.</span></span>  
  
- <span data-ttu-id="b4f27-119">보안 컨텍스트 설정 해제: 이 작업은 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>의 <xref:System.ServiceModel.WSHttpBinding> 속성을 `false`로 설정하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-119">Turn off Security Context Establishment: this can be accomplished by the setting the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property on the <xref:System.ServiceModel.WSHttpBinding> to `false`.</span></span> <span data-ttu-id="b4f27-120">또는 보안 세션이 필요한 경우 보안 [세션](./feature-details/secure-sessions.md) 항목의 설명에 따라 상태 저장 보안 세션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-120">Alternatively, if security sessions are required, it is possible to use stateful security sessions as described in the [Secure Sessions](./feature-details/secure-sessions.md) topic.</span></span> <span data-ttu-id="b4f27-121">상태 저장 보안 세션을 사용하면 보안 세션을 각 요청과 함께 보호 보안 토큰의 일부로 전송할 때 서비스의 상태를 비저장 상태로 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-121">Stateful security sessions enable the service to remain stateless as all of the state for the security session is transmitted with each request as a part of the protection security token.</span></span> <span data-ttu-id="b4f27-122">상태 저장 보안 세션을 사용하려면, 필요한 구성 설정이 시스템에서 제공되는 <xref:System.ServiceModel.Channels.CustomBinding> 및 <xref:System.ServiceModel.Channels.Binding>에 노출되지 않으므로 <xref:System.ServiceModel.WSHttpBinding> 또는 사용자 정의 <xref:System.ServiceModel.WSDualHttpBinding>을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-122">Note that to enable a stateful security session, it is necessary to use a <xref:System.ServiceModel.Channels.CustomBinding> or user-defined <xref:System.ServiceModel.Channels.Binding> as the necessary configuration settings are not exposed on <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.WSDualHttpBinding> that are provided by the system.</span></span>  
  
- <span data-ttu-id="b4f27-123">신뢰할 수 있는 세션은 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b4f27-123">Do not use reliable sessions.</span></span> <span data-ttu-id="b4f27-124">이 기능은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-124">This feature is off by default.</span></span>  
  
## <a name="load-balancing-the-nettcp-binding"></a><span data-ttu-id="b4f27-125">Net.TCP 바인딩을 사용한 부하 분산</span><span class="sxs-lookup"><span data-stu-id="b4f27-125">Load Balancing the Net.TCP Binding</span></span>  

 <span data-ttu-id="b4f27-126"><xref:System.ServiceModel.NetTcpBinding>은 IP 계층 부하 분산 기술을 사용하여 부하 분산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-126">The <xref:System.ServiceModel.NetTcpBinding> can be load balanced using IP-layer load balancing techniques.</span></span> <span data-ttu-id="b4f27-127">하지만 <xref:System.ServiceModel.NetTcpBinding>은 연결 대기 시간을 줄이기 위해 기본적으로 TCP 연결을 풀링합니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-127">However, the <xref:System.ServiceModel.NetTcpBinding> pools TCP connections by default to reduce connection latency.</span></span> <span data-ttu-id="b4f27-128">이러한 최적화 작업은 기본 부하 분산 메커니즘과 충돌하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-128">This is an optimization that interferes with the basic mechanism of load balancing.</span></span> <span data-ttu-id="b4f27-129"><xref:System.ServiceModel.NetTcpBinding>을 최적화하기 위한 기본 구성 값은 연결 풀 설정의 일부인 대여 시간 제한입니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-129">The primary configuration value for optimizing the <xref:System.ServiceModel.NetTcpBinding> is the lease timeout, which is part of the Connection Pool Settings.</span></span> <span data-ttu-id="b4f27-130">연결을 풀링하면 클라이언트 연결이 팜 내의 특정 서버와 이루어지게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-130">Connection pooling causes client connections to become associated to specific servers within the farm.</span></span> <span data-ttu-id="b4f27-131">이러한 연결 수명은 대여 시간 제한 설정으로 제어할 수 있지만 수명이 늘어나면 팜 내 여러 서버 간에 부하 분산 균형이 맞지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-131">As the lifetime of those connections increase (a factor controlled by the lease timeout setting), the load distribution across various servers in the farm becomes unbalanced.</span></span> <span data-ttu-id="b4f27-132">결과적으로 평균 호출 시간이 늘어납니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-132">As a result the average call time increases.</span></span> <span data-ttu-id="b4f27-133">따라서 <xref:System.ServiceModel.NetTcpBinding>을 부하 분산 시나리오에 사용할 때는 이 바인딩에서 사용하는 기본 대여 시간 제한을 줄이는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-133">So when using the <xref:System.ServiceModel.NetTcpBinding> in load-balanced scenarios, consider reducing the default lease timeout used by the binding.</span></span> <span data-ttu-id="b4f27-134">애플리케이션에 따라 최적 값이 다르겠지만 부하 분산 시나리오에 적절한 대여 시간 제한은 30초부터입니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-134">A 30-second lease timeout is a reasonable starting point for load-balanced scenarios, although the optimal value is application-dependent.</span></span> <span data-ttu-id="b4f27-135">채널 임대 시간 제한 및 기타 전송 할당량에 대 한 자세한 내용은 [전송 할당량](./feature-details/transport-quotas.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b4f27-135">For more information about the channel lease timeout and other transport quotas, see [Transport Quotas](./feature-details/transport-quotas.md).</span></span>  
  
 <span data-ttu-id="b4f27-136">부하 분산 시나리오에서 성능을 최대화하려면 <xref:System.ServiceModel.NetTcpSecurity>(<xref:System.ServiceModel.SecurityMode.Transport> 또는 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4f27-136">For best performance in load-balanced scenarios, consider using <xref:System.ServiceModel.NetTcpSecurity> (either <xref:System.ServiceModel.SecurityMode.Transport> or <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f27-137">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b4f27-137">See also</span></span>

- [<span data-ttu-id="b4f27-138">인터넷 정보 서비스 호스팅을 위한 최선의 방법</span><span class="sxs-lookup"><span data-stu-id="b4f27-138">Internet Information Services Hosting Best Practices</span></span>](./feature-details/internet-information-services-hosting-best-practices.md)
