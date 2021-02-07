---
description: '자세히 알아보기: 일시적으로 대기 중인 통신'
title: 일시 대기 통신
ms.date: 03/30/2017
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
ms.openlocfilehash: 8ced65dc28719416fb9b1059d2be8f29315013b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755722"
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="b35ae-103">일시 대기 통신</span><span class="sxs-lookup"><span data-stu-id="b35ae-103">Volatile Queued Communication</span></span>

<span data-ttu-id="b35ae-104">이 샘플에서는 MSMQ(메시지 큐) 전송을 통해 일시 대기 중인 통신을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-104">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="b35ae-105">이 샘플에서는 <xref:System.ServiceModel.NetMsmqBinding>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-105">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="b35ae-106">이 경우의 서비스는 자체 호스팅 콘솔 애플리케이션이며 이를 사용하여 서비스에서 대기 중인 메시지를 받는 것을 관찰할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-106">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

> [!NOTE]
> <span data-ttu-id="b35ae-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b35ae-108">대기 중인 통신에서 클라이언트는 큐를 사용하여 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="b35ae-109">좀더 정확하게 말하면 클라이언트는 큐에 메시지를 보내고,</span><span class="sxs-lookup"><span data-stu-id="b35ae-109">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="b35ae-110">서비스는 큐에서 보낸 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-110">The service receives messages from the queue.</span></span> <span data-ttu-id="b35ae-111">따라서 서비스와 클라이언트가 동시에 실행되고 있지 않더라도 큐를 사용하여 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-111">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

<span data-ttu-id="b35ae-112">보증 없이 메시지를 보내는 경우 ExactlyOnce 보증과 달리 MSMQ는 메시지를 배달하기 위해 최선의 노력을 다합니다. MSMQ는 메시지가 배달되었는지 확인하고, 배달할 수 없으면 이를 알린다는 점에서 ExactlyOnce 보증과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-112">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>

<span data-ttu-id="b35ae-113">일부 시나리오에서는 메시지가 손실되는지 여부보다 적시에 전달되는지가 더 중요한 경우 큐를 통해 보증 없이 일시적 메시지를 보낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-113">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="b35ae-114">큐 관리자의 작동이 중단되는 경우 일시적 메시지는 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-114">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="b35ae-115">따라서 큐 관리자가 충돌하면 일시 메시지의 저장에 사용된 비트랜잭션 큐는 보존되지만 메시지는 디스크에 저장되지 않기 때문에 보존되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-115">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>

> [!NOTE]
> <span data-ttu-id="b35ae-116">MSMQ를 사용하여 트랜잭션 범위 내에서 보증이 없는 일시 메시지를 보낼 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-116">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="b35ae-117">또한 일시 메시지를 보내려면 비트랜잭션 큐를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-117">You also must create a non-transactional queue to send volatile messages.</span></span>

<span data-ttu-id="b35ae-118">이 샘플에서 서비스 계약은 큐에서 사용하기에 가장 적합한 단방향 서비스를 정의하는 `IStockTicker`입니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-118">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void StockTick(string symbol, float price);
}
```

<span data-ttu-id="b35ae-119">서비스 작업에서는 다음 샘플 코드에 표시된 것과 같이 주식 기호와 주가를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-119">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>

```csharp
public class StockTickerService : IStockTicker
{
    public void StockTick(string symbol, float price)
    {
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);
     }
     …
}
```

<span data-ttu-id="b35ae-120">서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-120">The service is self hosted.</span></span> <span data-ttu-id="b35ae-121">MSMQ 전송을 사용하는 경우에는 사용되는 큐를 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-121">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="b35ae-122">수동으로 또는 코드를 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-122">This can be done manually or through code.</span></span> <span data-ttu-id="b35ae-123">이 샘플에서 서비스에는 큐가 있는지 확인하고 필요한 경우 큐를 만드는 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-123">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="b35ae-124">큐 이름은 구성 파일에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-124">The queue name is read from the configuration file.</span></span> <span data-ttu-id="b35ae-125">기본 주소는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 에서 서비스에 대 한 프록시를 생성 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-125">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>

```csharp
// Host the service within this EXE console application.
public static void Main()
{
    // Get MSMQ queue name from app settings in configuration.
    string queueName = ConfigurationManager.AppSettings["queueName"];

    // Create the transacted MSMQ queue if necessary.
    if (!MessageQueue.Exists(queueName))
        MessageQueue.Create(queueName);

    // Create a ServiceHost for the StockTickerService type.
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))
    {
        // Open the ServiceHost to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHost to shutdown the service.
        serviceHost.Close();
    }
}
```

<span data-ttu-id="b35ae-126">MSMQ 큐 이름은 구성 파일의 appSettings 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-126">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="b35ae-127">서비스의 엔드포인트는 구성 파일의 system.serviceModel 섹션에 정의되며 `netMsmqBinding` 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-127">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>

> [!NOTE]
> <span data-ttu-id="b35ae-128"><xref:System.Messaging>을 사용하여 큐를 만들 때 큐 이름은 로컬 컴퓨터에 점(.)을, 그 경로에는 백슬래시 구분 기호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-128">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="b35ae-129">WCF (Windows Communication Foundation) 끝점 주소는 net.pipe: 체계를 지정 하 고, 로컬 컴퓨터에는 "localhost"를 사용 하 고 경로에는 슬래시를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-129">The Windows Communication Foundation (WCF) endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>

<span data-ttu-id="b35ae-130">메시지의 보증과 함께 메시지가 지속적인지 또는 일시적인지도 구성에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-130">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>

```xml
<appSettings>
  <!-- use appSetting to configure MSMQ queue name -->
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />
</appSettings>

<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"
             behaviorConfiguration="CalculatorServiceBehavior">
    ...
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                binding="netMsmqBinding"
                bindingConfiguration="volatileBinding"
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />
    ...
    </service>
  </services>

  <bindings>
    <netMsmqBinding>
      <binding name="volatileBinding"
             durable="false"
           exactlyOnce="false"/>
    </netMsmqBinding>
  </bindings>
  ...
</system.serviceModel>
```

<span data-ttu-id="b35ae-131">샘플에서 비트랜잭션 큐를 사용하여 대기 중인 메시지를 보내기 때문에 트랜잭션된 메시지를 큐로 보낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-131">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>

```csharp
// Create a client.
Random r = new Random(137);

StockTickerClient client = new StockTickerClient();

float price = 43.23F;
for (int i = 0; i < 10; i++)
{
    float increment = 0.01f * (r.Next(10));
    client.StockTick("zzz" + i, price + increment);
}

//Closing the client gracefully cleans up resources.
client.Close();
```

<span data-ttu-id="b35ae-132">샘플을 실행하면 클라이언트 및 서비스 동작이 서비스 콘솔 창과 클라이언트 콘솔 창에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-132">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="b35ae-133">서비스에서 클라이언트가 보내는 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-133">You can see the service receive messages from the client.</span></span> <span data-ttu-id="b35ae-134">서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-134">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="b35ae-135">큐를 사용하므로 클라이언트와 서비스가 동시에 실행 중일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-135">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="b35ae-136">클라이언트를 실행하고 종료한 다음 서비스를 다시 시작해도 서비스에서 계속 메시지를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-136">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Stock Tick zzz0:43.25
Stock Tick zzz1:43.23
Stock Tick zzz2:43.28
Stock Tick zzz3:43.3
Stock Tick zzz4:43.23
Stock Tick zzz5:43.25
Stock Tick zzz6:43.25
Stock Tick zzz7:43.24
Stock Tick zzz8:43.32
Stock Tick zzz9:43.3
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b35ae-137">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="b35ae-137">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b35ae-138">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b35ae-139">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-139">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="b35ae-140">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="b35ae-140">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="b35ae-141">기본적으로 <xref:System.ServiceModel.NetMsmqBinding>을 사용하여 전송 보안이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-141">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="b35ae-142">MSMQ 전송 보안에는 두 가지 관련 속성이 있으며 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` 기본적으로 인증 모드는로 설정 되 `Windows` 고 보호 수준은로 설정 됩니다 `Sign` .</span><span class="sxs-lookup"><span data-stu-id="b35ae-142">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="b35ae-143">MSMQ에서 인증 및 서명 기능을 제공하려면 도메인에 속해 있어야 하며 MSMQ의 Active Directory 통합 옵션이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-143">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="b35ae-144">이 기준에 맞지 않는 컴퓨터에서 이 샘플을 실행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-144">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="b35ae-145">작업 그룹에 속해 있거나 Active Directory 통합이 없는 컴퓨터에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="b35ae-145">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>

1. <span data-ttu-id="b35ae-146">컴퓨터가 도메인에 속해 있지 않거나 Active Directory 통합이 설치되어 있지 않은 경우에는 다음 샘플 구성 코드에 표시된 것과 같이 인증 모드와 보호 수준을 `None`으로 설정하여 전송 보안을 끕니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-146">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>

    ```xml
    <system.serviceModel>
        <services>
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"
                   behaviorConfiguration="StockTickerServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>

            <!-- Define NetMsmqEndpoint -->
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"
                      binding="netMsmqBinding"
                      bindingConfiguration="volatileBinding"
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />

          </service>
        </services>

        <bindings>
          <netMsmqBinding>
            <binding name="volatileBinding"
                  durable="false"
                  exactlyOnce="false">
              <security mode="None" />
            </binding>
          </netMsmqBinding>
        </bindings>

        <behaviors>
          <serviceBehaviors>
            <behavior name="StockTickerServiceBehavior">
              <serviceMetadata httpGetEnabled="True"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>

      </system.serviceModel>
    ```

2. <span data-ttu-id="b35ae-147">샘플을 실행하기 전에 서버와 클라이언트 모두에서 구성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-147">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b35ae-148">`security mode`를 `None`으로 설정하는 것은 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 및 `Message` 보안을 `None`으로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-148">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b35ae-149">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-149">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b35ae-150">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="b35ae-150">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b35ae-151">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-151">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b35ae-152">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b35ae-152">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`
