---
description: '자세히 알아보기: 채널 팩터리'
title: 채널 팩터리
ms.date: 03/30/2017
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
ms.openlocfilehash: fad406e14887524fc69900e9775f1b6fbbcbecda
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704136"
---
# <a name="channel-factory"></a><span data-ttu-id="6bc4d-103">채널 팩터리</span><span class="sxs-lookup"><span data-stu-id="6bc4d-103">Channel Factory</span></span>

<span data-ttu-id="6bc4d-104">이 샘플에서는 클라이언트 애플리케이션에서 생성된 클라이언트 대신 <xref:System.ServiceModel.ChannelFactory> 클래스가 있는 채널을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-104">This sample demonstrates how a client application can create a channel with the <xref:System.ServiceModel.ChannelFactory> class instead of a generated client.</span></span> <span data-ttu-id="6bc4d-105">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>

> [!NOTE]
> <span data-ttu-id="6bc4d-106">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6bc4d-107">이 샘플에서는 <xref:System.ServiceModel.ChannelFactory%601> 클래스를 사용하여 서비스 엔드포인트에 채널을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-107">This sample uses the <xref:System.ServiceModel.ChannelFactory%601> class to create a channel to a service endpoint.</span></span> <span data-ttu-id="6bc4d-108">일반적으로 서비스 끝점에 대 한 채널을 만들려면 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 를 사용 하 여 클라이언트 형식을 생성 하 고 생성 된 형식의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-108">Typically, to create a channel to a service endpoint you generate a client type with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) and create an instance of the generated type.</span></span> <span data-ttu-id="6bc4d-109">이 샘플에서와 같이 <xref:System.ServiceModel.ChannelFactory%601> 클래스를 사용하여 채널을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-109">You can also create a channel by using the <xref:System.ServiceModel.ChannelFactory%601> class, as demonstrated in this sample.</span></span> <span data-ttu-id="6bc4d-110">다음 샘플 코드에서 만든 서비스는 [시작](getting-started-sample.md)의 서비스와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-110">The service created by the following sample code is identical to the service in the [Getting Started](getting-started-sample.md).</span></span>

```csharp
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
WSHttpBinding binding = new WSHttpBinding();
ChannelFactory<ICalculator> factory = new
                    ChannelFactory<ICalculator>(binding, address);
ICalculator channel = factory.CreateChannel();
```

> [!IMPORTANT]
> <span data-ttu-id="6bc4d-111">다중 컴퓨터 시나리오에서 이 샘플을 실행하는 경우에는 앞의 코드에서 "localhost"를 서비스를 실행하는 컴퓨터의 정규화된 이름으로 바꿔야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-111">If you are running this sample in a cross-machine scenario, you must replace "localhost" in the preceding code with the fully-qualified name of the machine that is running the service.</span></span> <span data-ttu-id="6bc4d-112">이 샘플에서는 구성을 사용하여 엔드포인트 주소를 설정하지 않기 때문에 코드에서 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-112">This sample does not use configuration to set the endpoint address, so this must be done in code.</span></span>

<span data-ttu-id="6bc4d-113">채널이 만들어지면 생성된 클라이언트의 경우와 마찬가지로 서비스 작업을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-113">Once the channel is created, service operations can be invoked just as with a generated client.</span></span>

```csharp
// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = channel.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
```

<span data-ttu-id="6bc4d-114">채널을 닫으려면 먼저 <xref:System.ServiceModel.IClientChannel> 인터페이스로 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-114">To close the channel, it must first be cast to an <xref:System.ServiceModel.IClientChannel> interface.</span></span> <span data-ttu-id="6bc4d-115">이는 생성된 채널이 `ICalculator` 및 `Add` 등의 메서드가 있지만 `Subtract`는 없는 `Close` 인터페이스를 사용하여 클라이언트 애플리케이션에 선언되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-115">This is because the channel as generated is declared in the client application using the `ICalculator` interface, which has methods like `Add` and `Subtract` but not `Close`.</span></span> <span data-ttu-id="6bc4d-116">`Close` 메서드는 <xref:System.ServiceModel.ICommunicationObject> 인터페이스에서 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-116">The `Close` method originates on the <xref:System.ServiceModel.ICommunicationObject> interface.</span></span>

```csharp
// Close the channel.
 ((IClientChannel)client).Close();
```

<span data-ttu-id="6bc4d-117">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="6bc4d-118">클라이언트 애플리케이션을 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-118">Press ENTER in the client window to shut down the client application.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6bc4d-119">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="6bc4d-119">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6bc4d-120">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6bc4d-121">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span> <span data-ttu-id="6bc4d-122">이 샘플에서는 메타데이터 게시를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-122">Note that this sample does not enable metadata publishing.</span></span> <span data-ttu-id="6bc4d-123">먼저 이 샘플의 메타데이터 게시를 사용하여 클라이언트 형식을 다시 생성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-123">You must first enable metadata publishing for this sample to regenerate the client type.</span></span>

3. <span data-ttu-id="6bc4d-124">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

### <a name="to-run-the-sample-cross-machine"></a><span data-ttu-id="6bc4d-125">다중 컴퓨터 구성에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="6bc4d-125">To run the sample cross machine</span></span>

1. <span data-ttu-id="6bc4d-126">다음 코드에서 "localhost"를 서비스를 실행하는 컴퓨터의 정규화된 이름으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-126">Replace "localhost" in the following code with the fully-qualified name of the machine that is running the service.</span></span>

    ```csharp
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");
    ```

> [!IMPORTANT]
> <span data-ttu-id="6bc4d-127">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6bc4d-128">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-128">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6bc4d-129">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6bc4d-130">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6bc4d-130">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`
