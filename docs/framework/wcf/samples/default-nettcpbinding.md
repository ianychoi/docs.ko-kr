---
title: 기본 NetTcpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
ms.openlocfilehash: 7a1af17ef3c2176371a394ae8b63d9cc207d5b6f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292781"
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="c8b6a-102">기본 NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="c8b6a-102">Default NetTcpBinding</span></span>

<span data-ttu-id="c8b6a-103">이 샘플에서는 <xref:System.ServiceModel.NetTcpBinding> 바인딩을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="c8b6a-104">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="c8b6a-105">이 샘플에서 서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="c8b6a-106">서비스와 클라이언트 모두 콘솔 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c8b6a-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c8b6a-108">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c8b6a-109">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c8b6a-110">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c8b6a-111">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="c8b6a-112">클라이언트 및 서비스 구성 파일에 바인딩이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="c8b6a-113">`binding`다음 샘플 구성과 같이 요소의 특성에 바인딩 형식이 지정 됩니다 [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) .</span><span class="sxs-lookup"><span data-stu-id="c8b6a-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="c8b6a-114">위의 샘플에서는 기본 설정과 함께 `netTcpBinding` 바인딩을 사용하도록 엔드포인트를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="c8b6a-115">`netTcpBinding` 바인딩을 구성하고 일부 설정을 변경하려면 바인딩 구성을 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="c8b6a-116">엔드포인트는 `bindingConfiguration` 특성이 있는 이름으로 바인딩 구성을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="c8b6a-117">이 샘플에서 바인딩 구성은 이름이 `Binding1`로 지정되며 다음 샘플 구성과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              bindingConfiguration="Binding1"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding name="Binding1"
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"  
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"  
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="c8b6a-118">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c8b6a-119">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c8b6a-120">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="c8b6a-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c8b6a-121">다음 명령을 사용 하 여 ASP.NET 4.0을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-121">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="c8b6a-122">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="c8b6a-123">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="c8b6a-124">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c8b6a-125">서버가 자체 호스트되므로 샘플을 다중 컴퓨터 구성에서 실행하려면 클라이언트의 App.config 파일에 ID를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c8b6a-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name=""  
          address="net.tcp://servername:9000/servicemodelsamples/service"
          binding="netTcpBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator">  
            <identity>  
              <userPrincipalName value = "user_name@service_domain"/>  
            </identity>  
      </endpoint>  
    </client>  
    ```  
