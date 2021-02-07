---
description: '자세히 알아보기: 이중'
title: 이중
ms.date: 03/30/2017
helpviewer_keywords:
- Duplex Service Contract
ms.assetid: bc5de6b6-1a63-42a3-919a-67d21bae24e0
ms.openlocfilehash: 2681506e186cb38eedc1888987fa46ddf2c0b7b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755787"
---
# <a name="duplex"></a><span data-ttu-id="b8cd9-103">이중</span><span class="sxs-lookup"><span data-stu-id="b8cd9-103">Duplex</span></span>

<span data-ttu-id="b8cd9-104">Duplex 샘플은 이중 계약을 정의 및 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-104">The Duplex sample demonstrates how to define and implement a duplex contract.</span></span> <span data-ttu-id="b8cd9-105">이중 통신은 클라이언트가 서비스와의 세션을 설정할 때 이루어지며, 서비스가 클라이언트로 메시지를 다시 보낼 수 있는 채널을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-105">Duplex communication occurs when a client establishes a session with a service and gives the service a channel on which the service can send messages back to the client.</span></span> <span data-ttu-id="b8cd9-106">이 샘플은 [시작](getting-started-sample.md)을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="b8cd9-107">이중 계약은 클라이언트에서 서비스로의 기본 인터페이스와 서비스에서 클라이언트의 콜백 인터페이스의 쌍으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-107">A duplex contract is defined as a pair of interfaces—a primary interface from the client to the service and a callback interface from the service to the client.</span></span> <span data-ttu-id="b8cd9-108">이 샘플에서 `ICalculatorDuplex` 인터페이스를 사용하여 클라이언트는 수학 연산을 수행하고 세션 도중 결과를 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-108">In this sample, the `ICalculatorDuplex` interface allows the client to perform math operations, calculating the result over a session.</span></span> <span data-ttu-id="b8cd9-109">서비스는 `ICalculatorDuplexCallback` 인터페이스에서 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-109">The service returns results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="b8cd9-110">클라이언트와 서비스 간에 전송되는 메시지 집합을 서로 연결하기 위해 컨텍스트를 설정해야 하므로 이중 계약에는 세션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-110">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span>

> [!NOTE]
> <span data-ttu-id="b8cd9-111">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b8cd9-112">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-112">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b8cd9-113">이중 계약은 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-113">The duplex contract is defined as follows:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required,
                 CallbackContract=typeof(ICalculatorDuplexCallback))]
public interface ICalculatorDuplex
{
    [OperationContract(IsOneWay = true)]
    void Clear();
    [OperationContract(IsOneWay = true)]
    void AddTo(double n);
    [OperationContract(IsOneWay = true)]
    void SubtractFrom(double n);
    [OperationContract(IsOneWay = true)]
    void MultiplyBy(double n);
    [OperationContract(IsOneWay = true)]
    void DivideBy(double n);
}

public interface ICalculatorDuplexCallback
{
    [OperationContract(IsOneWay = true)]
    void Result(double result);
    [OperationContract(IsOneWay = true)]
    void Equation(string eqn);
}
```

<span data-ttu-id="b8cd9-114">`CalculatorService` 클래스는 기본 `ICalculatorDuplex` 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-114">The `CalculatorService` class implements the primary `ICalculatorDuplex` interface.</span></span> <span data-ttu-id="b8cd9-115">서비스는 <xref:System.ServiceModel.InstanceContextMode.PerSession> 인스턴스 모드를 사용하여 각 세션의 결과를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-115">The service uses the <xref:System.ServiceModel.InstanceContextMode.PerSession> instance mode to maintain the result for each session.</span></span> <span data-ttu-id="b8cd9-116">`Callback`이라는 private 속성은 클라이언트에 대한 콜백 채널에 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-116">A private property named `Callback` is used to access the callback channel to the client.</span></span> <span data-ttu-id="b8cd9-117">서비스는 콜백 인터페이스를 통해 클라이언트에 메시지를 다시 전송하기 위해 콜백을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-117">The service uses the callback for sending messages back to the client through the callback interface.</span></span>

```csharp
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]
public class CalculatorService : ICalculatorDuplex
{
    double result = 0.0D;
    string equation;

    public CalculatorService()
    {
        equation = result.ToString();
    }

    public void Clear()
    {
        Callback.Equation($"{equation} = {result}");
        equation = result.ToString();
    }

    public void AddTo(double n)
    {
        result += n;
        equation += $" + {n}";
        Callback.Result(result);
    }

    //...

    ICalculatorDuplexCallback Callback
    {
        get
        {
            return OperationContext.Current.GetCallbackChannel<ICalculatorDuplexCallback>();
        }
    }
}
```

<span data-ttu-id="b8cd9-118">클라이언트는 서비스에서 메시지를 수신하기 위해 이중 계약의 콜백 인터페이스를 구현하는 클래스를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-118">The client must provide a class that implements the callback interface of the duplex contract, for receiving messages from the service.</span></span> <span data-ttu-id="b8cd9-119">이 샘플에서는 `CallbackHandler` 인터페이스를 구현하기 위해 `ICalculatorDuplexCallback` 클래스가 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-119">In the sample, a `CallbackHandler` class is defined to implement the `ICalculatorDuplexCallback` interface.</span></span>

```csharp
public class CallbackHandler : ICalculatorDuplexCallback
{
   public void Result(double result)
   {
      Console.WriteLine("Result({0})", result);
   }

   public void Equation(string equation)
   {
      Console.WriteLine("Equation({0}", equation);
   }
}
```

<span data-ttu-id="b8cd9-120">이중 계약에 대해 생성된 프록시의 경우 생성 시 <xref:System.ServiceModel.InstanceContext>를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-120">The proxy that is generated for a duplex contract requires a <xref:System.ServiceModel.InstanceContext> to be provided upon construction.</span></span> <span data-ttu-id="b8cd9-121">이 <xref:System.ServiceModel.InstanceContext>는 콜백 인터페이스를 구현하는 개체의 사이트로 사용되고 서비스에서 다시 전송된 메시지를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-121">This <xref:System.ServiceModel.InstanceContext> is used as the site for an object that implements the callback interface and handles messages that are sent back from the service.</span></span> <span data-ttu-id="b8cd9-122"><xref:System.ServiceModel.InstanceContext>는 `CallbackHandler` 클래스의 인스턴스를 사용하여 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-122">An <xref:System.ServiceModel.InstanceContext> is constructed with an instance of the `CallbackHandler` class.</span></span> <span data-ttu-id="b8cd9-123">이 개체는 콜백 인터페이스를 통해 서비스에서 클라이언트로 전송된 메시지를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-123">This object handles messages sent from the service to the client on the callback interface.</span></span>

```csharp
// Construct InstanceContext to handle messages on callback interface.
InstanceContext instanceContext = new InstanceContext(new CallbackHandler());

// Create a client.
CalculatorDuplexClient client = new CalculatorDuplexClient(instanceContext);

Console.WriteLine("Press <ENTER> to terminate client once the output is displayed.");
Console.WriteLine();

// Call the AddTo service operation.
double value = 100.00D;
client.AddTo(value);

// Call the SubtractFrom service operation.
value = 50.00D;
client.SubtractFrom(value);

// Call the MultiplyBy service operation.
value = 17.65D;
client.MultiplyBy(value);

// Call the DivideBy service operation.
value = 2.00D;
client.DivideBy(value);

// Complete equation.
client.Clear();

Console.ReadLine();

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();
```

<span data-ttu-id="b8cd9-124">세션 통신 및 이중 통신 모두를 지원하는 바인딩을 제공하도록 구성이 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-124">The configuration has been modified to provide a binding that supports both session communication and duplex communication.</span></span> <span data-ttu-id="b8cd9-125">`wsDualHttpBinding`은 세션 통신을 지원하며 각 방향에 대해 하나씩, 이중 HTTP 연결을 제공하여 이중 통신을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-125">The `wsDualHttpBinding` supports session communication and allows duplex communication by providing dual HTTP connections, one for each direction.</span></span> <span data-ttu-id="b8cd9-126">서비스에서 유일한 구성 차이는 사용되는 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-126">On the service, the only difference in configuration is the binding that is used.</span></span> <span data-ttu-id="b8cd9-127">클라이언트에서는 다음 샘플 구성과 같이 서버가 클라이언트에 연결하는 데 사용할 수 있는 주소를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-127">On the client, you must configure an address that the server can use to connect to the client as shown in the following sample configuration.</span></span>

```xml
<client>
  <endpoint name=""
            address="http://localhost/servicemodelsamples/service.svc"
            binding="wsDualHttpBinding"
            bindingConfiguration="DuplexBinding"
            contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />
</client>

<bindings>
  <!-- Configure a binding that support duplex communication. -->
  <wsDualHttpBinding>
    <binding name="DuplexBinding"
             clientBaseAddress="http://localhost:8000/myClient/">
    </binding>
  </wsDualHttpBinding>
</bindings>
```

<span data-ttu-id="b8cd9-128">샘플을 실행하면 서비스에서 전송된 콜백 인터페이스에서 클라이언트에 반환된 메시지를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-128">When you run the sample, you see the messages that are returned to the client on the callback interface that is sent from the service.</span></span> <span data-ttu-id="b8cd9-129">각 중간 결과가 표시된 다음 모든 작업이 완료되면 전체 수식이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-129">Each intermediate result is displayed, followed by the entire equation upon the completion of all operations.</span></span> <span data-ttu-id="b8cd9-130">클라이언트를 종료하려면 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-130">Press ENTER to shut down the client.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8cd9-131">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="b8cd9-131">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b8cd9-132">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b8cd9-133">C #, c + + 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-133">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b8cd9-134">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b8cd9-135">다중 컴퓨터 구성에서 클라이언트를 실행 하는 경우 `address` 다음에 표시 된 것 처럼 [ \<endpoint> \<client> 요소의](../../configure-apps/file-schema/wcf/endpoint-of-client.md) 특성 및 요소의 특성에서 "localhost"를 `clientBaseAddress` [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) 해당 컴퓨터의 이름으로 바꾸어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-135">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint> of \<client>](../../configure-apps/file-schema/wcf/endpoint-of-client.md) element and the `clientBaseAddress` attribute of the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element of the [\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md) element with the name of the appropriate machine, as shown in the following:</span></span>

    ```xml
    <client>
        <endpoint name = ""
        address="http://service_machine_name/servicemodelsamples/service.svc"
        ... />
    </client>
    ...
    <wsDualHttpBinding>
        <binding name="DuplexBinding" clientBaseAddress="http://client_machine_name:8000/myClient/">
        </binding>
    </wsDualHttpBinding>
    ```

> [!IMPORTANT]
> <span data-ttu-id="b8cd9-136">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8cd9-137">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-137">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b8cd9-138">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8cd9-139">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8cd9-139">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Duplex`
