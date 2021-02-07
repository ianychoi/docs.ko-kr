---
description: '자세한 정보: 사용자 지정 바인딩 신뢰할 수 있는 세션'
title: 사용자 지정 바인딩 신뢰할 수 있는 세션
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 0799e10c0fb86727bc21553584646031dc6f3606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752518"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="56305-103">사용자 지정 바인딩 신뢰할 수 있는 세션</span><span class="sxs-lookup"><span data-stu-id="56305-103">Custom Binding Reliable Session</span></span>

<span data-ttu-id="56305-104">사용자 지정 바인딩은 개별 바인딩 요소의 순서 있는 목록에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="56305-104">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="56305-105">이 샘플에서는 특히 신뢰할 수 있는 세션을 사용하도록 설정하는 것을 비롯하여 다양한 전송 및 메시지 인코딩 요소와 함께 사용자 지정 바인딩을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="56305-105">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="56305-106">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56305-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="56305-107">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="56305-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="56305-108">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="56305-109">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56305-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="56305-110">샘플 세부 정보</span><span class="sxs-lookup"><span data-stu-id="56305-110">Sample Details</span></span>

<span data-ttu-id="56305-111">신뢰할 수 있는 세션은 신뢰할 수 있는 메시징 및 세션 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-111">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="56305-112">신뢰할 수 있는 메시징 기능은 실패 시 통신을 다시 시도하고 메시지 차례로 도착과 같은 배달 보증을 지정할 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-112">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="56305-113">세션은 호출 간에 클라이언트의 상태를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-113">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="56305-114">이 샘플에서는 클라이언트 상태를 유지 관리하기 위한 세션을 구현하고 차례로 배달 보증을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-114">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="56305-115">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-115">The sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="56305-116">신뢰할 수 있는 세션 기능은 클라이언트와 서비스의 애플리케이션 구성 파일에서 사용하도록 설정 및 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="56305-116">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="56305-117">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="56305-117">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="56305-118">바인딩 요소의 순서는 사용자 지정 바인딩을 정의 하는 데 중요 합니다. 각는 채널 스택의 계층을 나타냅니다 ( [사용자 지정 바인딩](../extending/custom-bindings.md)참조).</span><span class="sxs-lookup"><span data-stu-id="56305-118">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../extending/custom-bindings.md)).</span></span>

<span data-ttu-id="56305-119">샘플의 서비스 구성은 다음 코드 예제와 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="56305-119">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="56305-120">다중 컴퓨터 구성에서 실행할 경우 서비스의 호스트 이름을 반영하도록 클라이언트의 엔드포인트 주소를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-120">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="56305-121">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="56305-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="56305-122">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="56305-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="56305-123">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="56305-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="56305-124">다음 명령을 사용 하 여 ASP.NET 4.0을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-124">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="56305-125">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="56305-126">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="56305-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="56305-127">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="56305-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="56305-128">다중 컴퓨터 구성에서 클라이언트를 실행 하는 경우 `address` [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) `clientBaseAddress` 다음 예제에 표시 된 것 처럼 요소의 특성과의 특성에서 "localhost"를 [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) 해당 컴퓨터의 이름으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="56305-128">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
