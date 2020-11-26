---
title: '방법: WAS에서 WCF 서비스 호스팅'
ms.date: 03/30/2017
ms.assetid: 9e3e213e-2dce-4f98-81a3-f62f44caeb54
ms.openlocfilehash: 640cfdd7525fb9877c6f3551a1456fed29c99b8a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244407"
---
# <a name="how-to-host-a-wcf-service-in-was"></a><span data-ttu-id="46ffc-102">방법: WAS에서 WCF 서비스 호스팅</span><span class="sxs-lookup"><span data-stu-id="46ffc-102">How to: Host a WCF Service in WAS</span></span>

<span data-ttu-id="46ffc-103">이 항목에서는 WAS (Windows Process Activation service)에서 호스팅된 WCF (Windows Communication Foundation) 서비스를 만드는 데 필요한 기본 단계에 대해 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-103">This topic outlines the basic steps required to create a Windows Process Activation Services (also known as WAS) hosted Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="46ffc-104">WAS는 HTTP가 아닌 전송 프로토콜에서 사용하는 IIS(Internet Information Services) 기능의 일반화인 새 프로세스 활성화 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-104">WAS is the new process activation service that is a generalization of Internet Information Services (IIS) features that work with non-HTTP transport protocols.</span></span> <span data-ttu-id="46ffc-105">WCF는 수신기 어댑터 인터페이스를 사용 하 여 WCF (예: TCP, 명명 된 파이프 및 메시지 큐)에서 지 원하는 HTTP가 아닌 프로토콜을 통해 수신 되는 활성화 요청을 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-105">WCF uses the listener adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, named pipes, and Message Queuing.</span></span>  
  
 <span data-ttu-id="46ffc-106">이 호스팅 옵션을 사용하려면 WAS 활성화 구성 요소를 적절히 설치하여 구성해야 하지만 호스팅 코드를 애플리케이션의 일부로 작성하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-106">This hosting option requires that WAS activation components are properly installed and configured, but it does not require any hosting code to be written as part of the application.</span></span> <span data-ttu-id="46ffc-107">WAS를 설치 및 구성 하는 방법에 대 한 자세한 내용은 [방법: WCF 정품 인증 구성 요소 설치 및 구성](how-to-install-and-configure-wcf-activation-components.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46ffc-107">For more information about installing and configuring WAS, see [How to: Install and Configure WCF Activation Components](how-to-install-and-configure-wcf-activation-components.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="46ffc-108">웹 서버의 요청 처리 파이프라인이 클래식 모드로 설정된 경우 WAS 활성화가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-108">WAS activation is not supported if the web server’s request processing pipeline is set to Classic mode.</span></span> <span data-ttu-id="46ffc-109">WAS 활성화를 사용할 경우 웹 서버의 요청 처리 파이프라인이 통합 모드로 설정되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-109">The web server’s request processing pipeline must be set to Integrated mode if WAS activation is to be used.</span></span>  
  
 <span data-ttu-id="46ffc-110">WCF 서비스가 WAS에서 호스팅되는 경우 표준 바인딩이 일반적인 방법으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-110">When a WCF service is hosted in WAS, the standard bindings are used in the usual way.</span></span> <span data-ttu-id="46ffc-111">그러나 WAS에서 호스팅되는 서비스를 구성하기 위해 <xref:System.ServiceModel.NetTcpBinding> 및 <xref:System.ServiceModel.NetNamedPipeBinding>을 사용하는 경우 제약 조건을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-111">However, when using the <xref:System.ServiceModel.NetTcpBinding> and the <xref:System.ServiceModel.NetNamedPipeBinding> to configure a WAS-hosted service, a constraint must be satisfied.</span></span> <span data-ttu-id="46ffc-112">서로 다른 엔드포인트가 동일한 전송을 사용하는 경우 바인딩 설정은 다음 7개의 속성과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-112">When different endpoints use the same transport, the binding settings have to match on the following seven properties:</span></span>  
  
- <span data-ttu-id="46ffc-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="46ffc-113">ConnectionBufferSize</span></span>  
  
- <span data-ttu-id="46ffc-114">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="46ffc-114">ChannelInitializationTimeout</span></span>  
  
- <span data-ttu-id="46ffc-115">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="46ffc-115">MaxPendingConnections</span></span>  
  
- <span data-ttu-id="46ffc-116">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="46ffc-116">MaxOutputDelay</span></span>  
  
- <span data-ttu-id="46ffc-117">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="46ffc-117">MaxPendingAccepts</span></span>  
  
- <span data-ttu-id="46ffc-118">ConnectionPoolSettings.IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="46ffc-118">ConnectionPoolSettings.IdleTimeout</span></span>  
  
- <span data-ttu-id="46ffc-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="46ffc-119">ConnectionPoolSettings.MaxOutboundConnectionsPerEndpoint</span></span>  
  
 <span data-ttu-id="46ffc-120">그렇지 않으면 첫 번째로 초기화된 엔드포인트가 항상 해당 속성 값을 결정하고 나중에 추가된 엔드포인트가 이러한 설정과 일치하지 않을 경우 <xref:System.ServiceModel.ServiceActivationException>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-120">Otherwise, the endpoint that is initialized first always determines the values of these properties, and endpoints added later throw a <xref:System.ServiceModel.ServiceActivationException> if they do not match those settings.</span></span>  
  
 <span data-ttu-id="46ffc-121">이 예제의 소스 복사에 대해서는 [TCP 활성화](../samples/tcp-activation.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="46ffc-121">For the source copy of this example, see [TCP Activation](../samples/tcp-activation.md).</span></span>  
  
### <a name="to-create-a-basic-service-hosted-by-was"></a><span data-ttu-id="46ffc-122">WAS에서 호스팅되는 기본 서비스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="46ffc-122">To create a basic service hosted by WAS</span></span>  
  
1. <span data-ttu-id="46ffc-123">서비스 유형에 대한 서비스 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-123">Define a service contract for the type of service.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1121)]  
  
2. <span data-ttu-id="46ffc-124">서비스 클래스에 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-124">Implement the service contract in a service class.</span></span> <span data-ttu-id="46ffc-125">주소 또는 바인딩 정보는 서비스 구현 내에 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-125">Note that address or binding information is not specified inside the implementation of the service.</span></span> <span data-ttu-id="46ffc-126">또한 구성 파일에서 해당 정보를 검색하기 위해 코드를 쓰지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-126">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/service.cs#1122)]  
  
3. <span data-ttu-id="46ffc-127">Web.config 파일을 만들어 <xref:System.ServiceModel.NetTcpBinding> 엔드포인트에서 사용할 `CalculatorService` 바인딩을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-127">Create a Web.config file to define the <xref:System.ServiceModel.NetTcpBinding> binding to be used by the `CalculatorService` endpoints.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="utf-8" ?>  
    <configuration>  
      <system.serviceModel>  
        <bindings>  
          <netTcpBinding>  
            <binding portSharingEnabled="true">  
              <security mode="None" />  
            </binding>  
          </netTcpBinding>  
        </bindings>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
4. <span data-ttu-id="46ffc-128">다음 코드가 포함된 Service.svc 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-128">Create a Service.svc file that contains the following code.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Service="CalculatorService" %>
   ```
  
5. <span data-ttu-id="46ffc-129">Service.svc 파일을 IIS 가상 디렉터리에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-129">Place the Service.svc file in your IIS virtual directory.</span></span>  
  
### <a name="to-create-a-client-to-use-the-service"></a><span data-ttu-id="46ffc-130">서비스를 사용할 클라이언트를 만들려면</span><span class="sxs-lookup"><span data-stu-id="46ffc-130">To create a client to use the service</span></span>  
  
1. <span data-ttu-id="46ffc-131">명령줄에서 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 서비스 메타 데이터에서 코드를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-131">Use [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) from the command line to generate code from service metadata.</span></span>  
  
    ```console
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>
    ```  
  
2. <span data-ttu-id="46ffc-132">생성된 클라이언트에는 클라이언트 구현에서 충족해야 하는 서비스 계약을 정의하는 `ICalculator` 인터페이스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-132">The client that is generated contains the `ICalculator` interface that defines the service contract that the client implementation must satisfy.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1221)]  
  
3. <span data-ttu-id="46ffc-133">또한 생성된 클라이언트 애플리케이션에는 `ClientCalculator`의 구현이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-133">The generated client application also contains the implementation of the `ClientCalculator`.</span></span> <span data-ttu-id="46ffc-134">주소 및 바인딩 정보는 서비스 구현 내에 지정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-134">Note that the address and binding information is not specified anywhere inside the implementation of the service.</span></span> <span data-ttu-id="46ffc-135">또한 구성 파일에서 해당 정보를 검색하기 위해 코드를 쓰지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-135">Also, code does not have to be written to retrieve that information from the configuration file.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1222)]  
  
4. <span data-ttu-id="46ffc-136">또한 <xref:System.ServiceModel.NetTcpBinding>을 사용하는 클라이언트의 구성도 Svcutil.exe를 통해 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-136">The configuration for the client that uses the <xref:System.ServiceModel.NetTcpBinding> is also generated by Svcutil.exe.</span></span> <span data-ttu-id="46ffc-137">이 파일은 Visual Studio를 사용하는 경우 이름을 App.config로 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-137">This file should be named in the App.config file when using Visual Studio.</span></span>  
  
     [!code-xml[C_HowTo_HostInWAS#2211](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/common/app.config#2211)]
  
5. <span data-ttu-id="46ffc-138">애플리케이션에서 `ClientCalculator`의 인스턴스를 만든 다음 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-138">Create an instance of the `ClientCalculator` in an application and then call the service operations.</span></span>  
  
     [!code-csharp[C_HowTo_HostInWAS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinwas/cs/client.cs#1223)]  
  
6. <span data-ttu-id="46ffc-139">클라이언트를 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="46ffc-139">Compile and run the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ffc-140">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46ffc-140">See also</span></span>

- [<span data-ttu-id="46ffc-141">TCP 활성화</span><span class="sxs-lookup"><span data-stu-id="46ffc-141">TCP Activation</span></span>](../samples/tcp-activation.md)
- <span data-ttu-id="46ffc-142">[Windows Server App Fabric 호스팅 기능](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="46ffc-142">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
