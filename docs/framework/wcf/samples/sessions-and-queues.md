---
description: '자세한 정보: 세션 및 큐'
title: 세션 및 큐
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: 94ff58fca628e44b78b002291fa78a39cc10a14f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793014"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="9ac96-103">세션 및 큐</span><span class="sxs-lookup"><span data-stu-id="9ac96-103">Sessions and queues</span></span>

<span data-ttu-id="9ac96-104">이 샘플에서는 MSMQ(메시지 큐) 전송을 통해 대기 중인 통신으로 일련의 관련된 메시지를 보내고 받는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-104">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="9ac96-105">이 샘플에서는 `netMsmqBinding` 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-105">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="9ac96-106">이 서비스는 자체적으로 호스트되는 콘솔 애플리케이션으로서 이를 사용하여 서비스에서 대기된 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-106">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9ac96-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9ac96-108">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9ac96-109">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9ac96-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9ac96-110">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9ac96-111">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="9ac96-112">대기 중인 통신에서 클라이언트는 큐를 사용하여 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-112">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="9ac96-113">좀더 정확하게 말하면 클라이언트는 큐에 메시지를 보내고,</span><span class="sxs-lookup"><span data-stu-id="9ac96-113">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="9ac96-114">서비스는 큐에서 보낸 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-114">The service receives messages from the queue.</span></span> <span data-ttu-id="9ac96-115">따라서 서비스와 클라이언트가 동시에 실행되고 있지 않더라도 큐를 사용하여 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-115">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="9ac96-116">클라이언트가 관련 메시지 집합을 그룹 내의 다른 클라이언트에게 보내는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-116">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="9ac96-117">메시지를 함께 또는 지정된 순서에 따라 처리해야 하는 경우에는 단일 수신 애플리케이션에서 처리할 수 있도록 큐를 사용하여 메시지를 그룹화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-117">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="9ac96-118">이 기능은 서버 그룹에 여러 개의 수신 애플리케이션이 있고 메시지 그룹을 같은 수신 애플리케이션에서 처리해야 하는 경우 특히 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-118">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="9ac96-119">대기 중인 세션은 한꺼번에 처리해야 할 관련된 메시지 집합을 보내고 받는 데 사용되는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-119">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="9ac96-120">대기 중인 세션에는 이 패턴을 보이는 트랜잭션이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-120">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="9ac96-121">샘플에서 클라이언트는 단일 트랜잭션 범위 내에서 세션의 일부로 서비스에 몇 개의 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-121">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="9ac96-122">서비스 계약은 `IOrderTaker`이며, 이는 큐에 사용하기에 적합한 단방향 서비스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-122">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="9ac96-123">다음 샘플 코드에 표시된 계약에 사용된 <xref:System.ServiceModel.SessionMode>는 메시지가 세션의 일부임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-123">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="9ac96-124">서비스에서는 첫 작업으로 트랜잭션을 참여시키지만 트랜잭션을 자동으로 완료하지는 않는 방식으로 서비스 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-124">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="9ac96-125">후속 작업에서도 같은 트랜잭션을 참여시키지만 자동으로 완료하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-125">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="9ac96-126">세션의 마지막 작업에서는 트랜잭션을 자동으로 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-126">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="9ac96-127">따라서 서비스 계약의 몇 가지 작업 호출에 같은 트랜잭션이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-127">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="9ac96-128">작업에서 예외가 throw되면 트랜잭션이 롤백되고 세션이 다시 큐로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-128">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="9ac96-129">마지막 작업을 성공적으로 완료하고 나면 트랜잭션이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-129">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="9ac96-130">서비스에서는 `PerSession`을 <xref:System.ServiceModel.InstanceContextMode>로 사용하여 같은 서비스 인스턴스의 세션에서 모든 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-130">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="9ac96-131">서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-131">The service is self hosted.</span></span> <span data-ttu-id="9ac96-132">MSMQ 전송을 사용하는 경우에는 사용되는 큐를 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-132">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="9ac96-133">수동으로 또는 코드를 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-133">This can be done manually or through code.</span></span> <span data-ttu-id="9ac96-134">이 샘플에서 서비스는 큐가 있는지 확인하고 필요한 경우 큐를 만드는 <xref:System.Messaging> 코드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-134">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="9ac96-135">큐 이름은 <xref:System.Configuration.ConfigurationManager.AppSettings%2A> 클래스를 사용하여 구성 파일로부터 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-135">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
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

 <span data-ttu-id="9ac96-136">MSMQ 큐 이름은 구성 파일의 appSettings 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-136">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="9ac96-137">서비스의 엔드포인트는 구성 파일의 system.serviceModel 섹션에 정의되며 `netMsmqBinding` 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-137">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9ac96-138">클라이언트는 트랜잭션 범위를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-138">The client creates a transaction scope.</span></span> <span data-ttu-id="9ac96-139">세션에 있는 모든 메시지가 트랜잭션 범위 내의 큐로 전송되기 때문에 트랜잭션 범위는 모든 메시지가 성공하거나 실패하는 원자 단위로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-139">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="9ac96-140">트랜잭션은 <xref:System.Transactions.TransactionScope.Complete%2A>를 호출하여 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-140">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
> <span data-ttu-id="9ac96-141">세션에 있는 모든 메시지에 대해 단일 트랜잭션만 사용할 수 있으며 세션에 있는 모든 메시지는 트랜잭션을 커밋하기 전에 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-141">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="9ac96-142">클라이언트를 닫으면 세션이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-142">Closing the client closes the session.</span></span> <span data-ttu-id="9ac96-143">따라서 트랜잭션을 완료하여 세션에 있는 모든 메시지를 큐로 보내기 전에 클라이언트를 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-143">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="9ac96-144">샘플을 실행하면 클라이언트 및 서비스 동작이 서비스 콘솔 창과 클라이언트 콘솔 창에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-144">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9ac96-145">서비스에서 클라이언트가 보내는 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-145">You can see the service receive messages from the client.</span></span> <span data-ttu-id="9ac96-146">서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-146">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="9ac96-147">큐를 사용하므로 클라이언트와 서비스가 동시에 실행 중일 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-147">Because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="9ac96-148">클라이언트를 실행하고 종료한 다음 서비스를 다시 시작해도 서비스에서 계속 메시지를 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-148">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="9ac96-149">클라이언트에서:</span><span class="sxs-lookup"><span data-stu-id="9ac96-149">On the client.</span></span>  
  
```console  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="9ac96-150">서비스에서:</span><span class="sxs-lookup"><span data-stu-id="9ac96-150">On the service.</span></span>  
  
```console  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="9ac96-151">샘플 설정, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="9ac96-151">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9ac96-152">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9ac96-153">C #, c + + 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="9ac96-153">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9ac96-154">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="9ac96-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
 <span data-ttu-id="9ac96-155">기본적으로 <xref:System.ServiceModel.NetMsmqBinding>을 사용하여 전송 보안이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-155">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="9ac96-156">MSMQ 전송 보안에 대 한 두 가지 관련 속성이 있으며 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> , <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` 기본적으로 인증 모드는로 설정 되 `Windows` 고 보호 수준은로 설정 됩니다 `Sign` .</span><span class="sxs-lookup"><span data-stu-id="9ac96-156">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="9ac96-157">MSMQ에서 인증 및 서명 기능을 제공하려면 도메인에 속해 있어야 하며 MSMQ의 Active Directory 통합 옵션이 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-157">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="9ac96-158">이 기준에 맞지 않는 컴퓨터에서 이 샘플을 실행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-158">If you run this sample on a computer that does not satisfy these criteria, you receive an error.</span></span>  
  
### <a name="run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="9ac96-159">작업 그룹에 가입 된 컴퓨터에서 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="9ac96-159">Run the sample on a computer joined to a workgroup</span></span>  
  
1. <span data-ttu-id="9ac96-160">컴퓨터가 도메인에 속해 있지 않거나 Active Directory 통합이 설치되어 있지 않은 경우에는 다음 샘플 구성과 같이 인증 모드와 보호 수준을 `None`으로 설정하여 전송 보안을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-160">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="9ac96-161">샘플을 실행하기 전에 서버와 클라이언트 모두에서 구성을 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-161">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="9ac96-162">보안 모드를 `None`으로 설정하는 것은 <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> 및 `Message` 보안을 `None`으로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="9ac96-162">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
