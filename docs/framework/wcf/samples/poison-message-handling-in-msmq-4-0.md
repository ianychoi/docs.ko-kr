---
description: '자세한 정보: MSMQ의 포이즌 메시지 처리 4.0'
title: Poison Message Handling in MSMQ 4.0
ms.date: 03/30/2017
ms.assetid: ec8d59e3-9937-4391-bb8c-fdaaf2cbb73e
ms.openlocfilehash: fadbce9379b63f47f80c38551c1c71b81df5fee0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793170"
---
# <a name="poison-message-handling-in-msmq-40"></a><span data-ttu-id="f66ac-103">Poison Message Handling in MSMQ 4.0</span><span class="sxs-lookup"><span data-stu-id="f66ac-103">Poison Message Handling in MSMQ 4.0</span></span>

<span data-ttu-id="f66ac-104">이 샘플에서는 서비스에서 포이즌 메시지 처리를 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-104">This sample demonstrates how to perform poison message handling in a service.</span></span> <span data-ttu-id="f66ac-105">이 샘플은 [트랜잭션 된 MSMQ 바인딩](transacted-msmq-binding.md) 샘플을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-105">This sample is based on the [Transacted MSMQ Binding](transacted-msmq-binding.md) sample.</span></span> <span data-ttu-id="f66ac-106">이 샘플에서는 `netMsmqBinding`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-106">This sample uses the `netMsmqBinding`.</span></span> <span data-ttu-id="f66ac-107">이 서비스는 자체적으로 호스트되는 콘솔 애플리케이션으로서 이를 사용하여 서비스에서 대기된 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-107">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>

 <span data-ttu-id="f66ac-108">대기 중인 통신에서 클라이언트는 큐를 사용하여 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-108">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f66ac-109">좀더 정확하게 말하면 클라이언트는 큐에 메시지를 보내고,</span><span class="sxs-lookup"><span data-stu-id="f66ac-109">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f66ac-110">서비스는 큐에서 보낸 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-110">The service receives messages from the queue.</span></span> <span data-ttu-id="f66ac-111">따라서 서비스와 클라이언트가 동시에 실행되고 있지 않더라도 큐를 사용하여 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-111">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>

 <span data-ttu-id="f66ac-112">포이즌 메시지는 메시지를 읽는 서비스가 메시지를 처리할 수 없어 메시지를 읽는 트랜잭션을 종료할 때 큐에서 반복적으로 읽는 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-112">A poison message is a message that is repeatedly read from a queue when the service reading the message cannot process the message and therefore terminates the transaction under which the message is read.</span></span> <span data-ttu-id="f66ac-113">이런 경우 메시지가 다시 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-113">In such cases, the message is retried again.</span></span> <span data-ttu-id="f66ac-114">이론적으로는, 메시지에 문제가 있는 경우 이런 현상이 계속해서 발생할 수 있지만</span><span class="sxs-lookup"><span data-stu-id="f66ac-114">This can theoretically go on forever if there is a problem with the message.</span></span> <span data-ttu-id="f66ac-115">트랜잭션을 사용 하 여 큐에서 읽고 서비스 작업을 호출 하는 경우에만이 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-115">This can only occur when you use transactions to read from the queue and invoke the service operation.</span></span>

 <span data-ttu-id="f66ac-116">MSMQ의 버전에 따라 NetMsmqBinding에서는 포이즌 메시지의 제한적 검색부터 완전한 검색까지 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-116">Based on the version of MSMQ, the NetMsmqBinding supports limited detection to full detection of poison messages.</span></span> <span data-ttu-id="f66ac-117">포이즌 메시지로 검색된 메시지는 몇 가지 방법으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-117">After the message has been detected as poisoned, then it can be handled in several ways.</span></span> <span data-ttu-id="f66ac-118">또한 MSMQ의 버전에 따라 NetMsmqBinding에서는 포이즌 메시지의 제한된 처리부터 전체 처리까지를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-118">Again, based on the version of MSMQ, the NetMsmqBinding supports limited handling to full handling of poison messages.</span></span>

 <span data-ttu-id="f66ac-119">이 샘플은 windows Server 2003 및 Windows XP 플랫폼에서 제공 되는 제한 된 포이즌 기능과 Windows Vista에서 제공 하는 완전 한 포이즌 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-119">This sample illustrates the limited poison facilities provided on Windows Server 2003 and Windows XP platform and the full poison facilities provided on Windows Vista.</span></span> <span data-ttu-id="f66ac-120">두 샘플에서 목표는 포이즌 메시지를 큐에서 다른 큐로 이동 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-120">In both samples, the objective is to move the poison message out of the queue to another queue.</span></span> <span data-ttu-id="f66ac-121">그러면 포이즌 메시지 서비스에서 해당 큐에 서비스를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-121">That queue can then be serviced by a poison message service.</span></span>

## <a name="msmq-v40-poison-handling-sample"></a><span data-ttu-id="f66ac-122">MSMQ v4.0 Poison Handling 샘플</span><span class="sxs-lookup"><span data-stu-id="f66ac-122">MSMQ v4.0 Poison Handling Sample</span></span>

 <span data-ttu-id="f66ac-123">Windows Vista에서 MSMQ는 포이즌 메시지를 저장 하는 데 사용할 수 있는 포이즌 하위 큐 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-123">In Windows Vista, MSMQ provides a poison subqueue facility that can be used to store poison messages.</span></span> <span data-ttu-id="f66ac-124">이 샘플에서는 Windows Vista를 사용 하는 포이즌 메시지를 처리 하는 최선의 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-124">This sample demonstrates the best practice of dealing with poison messages using Windows Vista.</span></span>

 <span data-ttu-id="f66ac-125">Windows Vista의 포이즌 메시지 검색은 정교 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-125">The poison message detection in Windows Vista is sophisticated.</span></span> <span data-ttu-id="f66ac-126">검색에 도움이 되는 속성은 세 가지입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-126">There are 3 properties that help with detection.</span></span> <span data-ttu-id="f66ac-127"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>는 큐에서 지정된 메시지를 다시 읽고 애플리케이션으로 디스패치하여 처리할 수 있는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-127">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is number of times a given message is re-read from the queue and dispatched to the application for processing.</span></span> <span data-ttu-id="f66ac-128">메시지를 애플리케이션으로 디스패치할 수 없어 큐에 다시 배치하거나 애플리케이션이 서비스 작업에서 트랜잭션을 롤백하는 경우에 큐의 메시지를 다시 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-128">A message is re-read from the queue when it is put back into the queue because the message cannot be dispatched to the application or the application rolls back the transaction in the service operation.</span></span> <span data-ttu-id="f66ac-129"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A>는 메시지를 재시도 큐로 이동하는 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-129"><xref:System.ServiceModel.MsmqBindingBase.MaxRetryCycles%2A> is the number of times the message is moved to the retry queue.</span></span> <span data-ttu-id="f66ac-130"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>에 도달하면 메시지가 재시도 큐로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-130">When <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reached, the message is moved to the retry queue.</span></span> <span data-ttu-id="f66ac-131"><xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> 속성은 메시지가 재시도 큐에서 다시 기본 큐로 이동한 후의 시간 지연입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-131">The property <xref:System.ServiceModel.MsmqBindingBase.RetryCycleDelay%2A> is the time delay after which the message is moved from the retry queue back to the main queue.</span></span> <span data-ttu-id="f66ac-132"><xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A>는 0으로 다시 설정되고,</span><span class="sxs-lookup"><span data-stu-id="f66ac-132">The <xref:System.ServiceModel.MsmqBindingBase.ReceiveRetryCount%2A> is reset to 0.</span></span> <span data-ttu-id="f66ac-133">메시지가 다시 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-133">The message is tried again.</span></span> <span data-ttu-id="f66ac-134">메시지를 읽으려는 시도가 모두 실패하면 메시지가 포이즌으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-134">If all attempts to read the message have failed, then the message is marked as poisoned.</span></span>

 <span data-ttu-id="f66ac-135">메시지가 포이즌으로 표시되면 메시지는 <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> 열거의 설정에 따라 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-135">Once the message is marked as poisoned, the message is dealt with according to the settings in the <xref:System.ServiceModel.MsmqBindingBase.ReceiveErrorHandling%2A> enumeration.</span></span> <span data-ttu-id="f66ac-136">반복하려는 경우 가능한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-136">To reiterate the possible values:</span></span>

- <span data-ttu-id="f66ac-137">Fault(기본값): 수신기와 서비스 호스트에 오류를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-137">Fault (default): To fault the listener and also the service host.</span></span>

- <span data-ttu-id="f66ac-138">Drop: 메시지를 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-138">Drop: To drop the message.</span></span>

- <span data-ttu-id="f66ac-139">이동: 메시지를 포이즌 메시지 하위 큐로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-139">Move: To move the message to the poison message subqueue.</span></span> <span data-ttu-id="f66ac-140">이 값은 Windows Vista 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-140">This value is available only on Windows Vista.</span></span>

- <span data-ttu-id="f66ac-141">Reject: 메시지를 보낸 사람의 배달 못 한 편지 큐로 돌려보내는 방법으로 메시지를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-141">Reject: To reject the message, sending the message back to the sender's dead-letter queue.</span></span> <span data-ttu-id="f66ac-142">이 값은 Windows Vista 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-142">This value is available only on Windows Vista.</span></span>

 <span data-ttu-id="f66ac-143">이 샘플에서는 포이즌 메시지에 `Move` 처리를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-143">The sample demonstrates using the `Move` disposition for the poison message.</span></span> <span data-ttu-id="f66ac-144">`Move` 메시지를 포이즌 하위 큐로 이동 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-144">`Move` causes the message to move to the poison subqueue.</span></span>

 <span data-ttu-id="f66ac-145">서비스 계약은 `IOrderProcessor`이며, 이는 큐에 사용하기에 적합한 단방향 서비스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-145">The service contract is `IOrderProcessor`, which defines a one-way service that is suitable for use with queues.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 <span data-ttu-id="f66ac-146">서비스 작업에는 주문을 처리하고 있다는 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-146">The service operation displays a message stating it is processing the order.</span></span> <span data-ttu-id="f66ac-147">포이즌 메시지 기능을 보여 주기 위해 서비스 `SubmitPurchaseOrder` 작업에서 예외를 throw 하 여 서비스의 임의 호출에서 트랜잭션을 롤백합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-147">To demonstrate the poison message functionality, the `SubmitPurchaseOrder` service operation throws an exception to roll back the transaction on a random invocation of the service.</span></span> <span data-ttu-id="f66ac-148">그러면 메시지는 큐로 돌아가서,</span><span class="sxs-lookup"><span data-stu-id="f66ac-148">This causes the message to be put back in the queue.</span></span> <span data-ttu-id="f66ac-149">포이즌 메시지로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-149">Eventually the message is marked as poison.</span></span> <span data-ttu-id="f66ac-150">포이즌 메시지를 포이즌 하위 큐로 이동 하도록 구성이 설정 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-150">The configuration is set to move the poison message to the poison subqueue.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    static Random r = new Random(137);

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {

        int randomNumber = r.Next(10);

        if (randomNumber % 2 == 0)
        {
            Orders.Add(po);
            Console.WriteLine("Processing {0} ", po);
        }
        else
        {
            Console.WriteLine("Aborting transaction, cannot process purchase order: " + po.PONumber);
            Console.WriteLine();
            throw new Exception("Cannot process purchase order: " + po.PONumber);
        }
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted");
    }

    // Host the service within this EXE console application.
    public static void Main()
    {
        // Get MSMQ queue name from app settings in configuration.
        string queueName = ConfigurationManager.AppSettings["queueName"];

        // Create the transacted MSMQ queue if necessary.
        if (!System.Messaging.MessageQueue.Exists(queueName))
            System.Messaging.MessageQueue.Create(queueName, true);

        // Get the base address that is used to listen for WS-MetaDataExchange requests.
        // This is useful to generate a proxy for the client.
        string baseAddress = ConfigurationManager.AppSettings["baseAddress"];

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService), new Uri(baseAddress));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        // Open the ServiceHostBase to create listeners and start listening for messages.
        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        if(serviceHost.State != CommunicationState.Faulted) {
            serviceHost.Close();
        }

    }
}
```

 <span data-ttu-id="f66ac-151">서비스 구성에는 다음 구성 파일에 표시된 `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay` 및 `receiveErrorHandling`와 같은 포이즌 메시지 속성이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-151">The service configuration includes the following poison message properties: `receiveRetryCount`, `maxRetryCycles`, `retryCycleDelay`, and `receiveErrorHandling` as shown in the following configuration file.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesPoison" />
    <add key="baseAddress" value="http://localhost:8000/orderProcessor/poisonSample"/>
  </appSettings>
  <system.serviceModel>
    <services>
      <service
              name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison"
                  binding="netMsmqBinding"
                  bindingConfiguration="PoisonBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
      </service>
    </services>

    <bindings>
      <netMsmqBinding>
        <binding name="PoisonBinding"
                 receiveRetryCount="0"
                 maxRetryCycles="1"
                 retryCycleDelay="00:00:05"
                 receiveErrorHandling="Move">
        </binding>
      </netMsmqBinding>
    </bindings>
  </system.serviceModel>
</configuration>
```

## <a name="processing-messages-from-the-poison-message-queue"></a><span data-ttu-id="f66ac-152">포이즌 메시지 큐의 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="f66ac-152">Processing messages from the poison message queue</span></span>

 <span data-ttu-id="f66ac-153">포이즌 메시지 서비스에서는 최종 포이즌 메시지 큐로부터 메시지를 읽어 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-153">The poison message service reads messages from the final poison message queue and processes them.</span></span>

 <span data-ttu-id="f66ac-154">포이즌 메시지 큐의 메시지는 메시지를 처리 중인 서비스로 주소가 지정되는 메시지입니다. 이 서비스는 포이즌 메시지 서비스 엔드포인트와 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-154">Messages in the poison message queue are messages that are addressed to the service that is processing the message, which could be different from the poison message service endpoint.</span></span> <span data-ttu-id="f66ac-155">따라서 포이즌 메시지 서비스가 큐에서 메시지를 읽으면 WCF 채널 계층은 끝점에서 불일치를 찾아 메시지를 디스패치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-155">Therefore, when the poison message service reads messages from the queue, the WCF channel layer finds the mismatch in endpoints and does not dispatch the message.</span></span> <span data-ttu-id="f66ac-156">이 경우 메시지의 주소는 주문 처리 서비스로 지정되지만 포이즌 메시지 서비스에서 메시지를 받게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-156">In this case, the message is addressed to the order processing service but is being received by the poison message service.</span></span> <span data-ttu-id="f66ac-157">메시지의 주소가 다른 엔드포인트로 지정되는 경우에도 메시지를 계속 받으려면 `ServiceBehavior`를 추가하여 메시지 주소가 지정된 서비스 엔드포인트와 일치하는 주소를 필터링해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-157">To continue to receive the message even if the message is addressed to a different endpoint, we must add a `ServiceBehavior` to filter addresses where the match criterion is to match any service endpoint the message is addressed to.</span></span> <span data-ttu-id="f66ac-158">포이즌 메시지 큐에서 읽은 메시지를 성공적으로 처리하려면 이러한 구성이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-158">This is required to successfully process messages that you read from the poison message queue.</span></span>

 <span data-ttu-id="f66ac-159">포이즌 메시지 서비스 구현 자체는 서비스 구현과 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-159">The poison message service implementation itself is very similar to the service implementation.</span></span> <span data-ttu-id="f66ac-160">이 구현에서는 계약을 구현하고 주문을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-160">It implements the contract and processes the orders.</span></span> <span data-ttu-id="f66ac-161">코드 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-161">The code example is as follows.</span></span>

```csharp
// Service class that implements the service contract.
// Added code to write output to the console window.
[ServiceBehavior(AddressFilterMode=AddressFilterMode.Any)]
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }

    public static void OnServiceFaulted(object sender, EventArgs e)
    {
        Console.WriteLine("Service Faulted...exiting app");
        Environment.Exit(1);
    }

    // Host the service within this EXE console application.
    public static void Main()
    {

        // Create a ServiceHost for the OrderProcessorService type.
        ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService));

        // Hook on to the service host faulted events.
        serviceHost.Faulted += new EventHandler(OnServiceFaulted);

        serviceHost.Open();

        // The service can now be accessed.
        Console.WriteLine("The poison message service is ready.");
        Console.WriteLine("Press <ENTER> to terminate service.");
        Console.WriteLine();
        Console.ReadLine();

        // Close the ServiceHostBase to shutdown the service.
        if(serviceHost.State != CommunicationState.Faulted)
        {
            serviceHost.Close();
        }
    }
```

 <span data-ttu-id="f66ac-162">주문 큐에서 메시지를 읽는 주문 처리 서비스와 달리 포이즌 메시지 서비스는 포이즌 하위 큐에서 메시지를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-162">Unlike the order processing service that reads messages from the order queue, the poison message service reads messages from the poison subqueue.</span></span> <span data-ttu-id="f66ac-163">포이즌 큐는 주 큐의 하위 큐 이며,은 "포이즌"으로 이름이 지정 되 고 MSMQ에서 자동으로 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-163">The poison queue is a subqueue of the main queue, is named "poison" and is automatically generated by MSMQ.</span></span> <span data-ttu-id="f66ac-164">이 파일에 액세스 하려면 다음 샘플 구성에 표시 된 것 처럼 기본 큐 이름 뒤에 ";" 및 하위 큐 이름 (이 경우 "포이즌")을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-164">To access it, provide the main queue name followed by a ";" and the subqueue name, in this case -"poison", as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="f66ac-165">MSMQ v3.0 샘플에서 포이즌 큐 이름은 하위 큐가 아닌 메시지를 이동한 큐입니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-165">In the sample for MSMQ v3.0, the poison queue name is not a sub-queue, rather the queue that we moved the message to.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.OrderProcessorService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesPoison;poison"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" >
        </endpoint>
      </service>
    </services>

  </system.serviceModel>
</configuration>
```

 <span data-ttu-id="f66ac-166">샘플을 실행하면 클라이언트, 서비스 및 포이즌 메시지 서비스 동작이 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-166">When you run the sample, the client, service, and poison message service activities are displayed in console windows.</span></span> <span data-ttu-id="f66ac-167">서비스에서 클라이언트가 보내는 메시지를 받는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-167">You can see the service receive messages from the client.</span></span> <span data-ttu-id="f66ac-168">서비스를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-168">Press ENTER in each console window to shut down the services.</span></span>

 <span data-ttu-id="f66ac-169">서비스가 실행되어 주문 처리를 시작하고 임의로 처리를 종료하기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-169">The service starts running, processing orders and at random starts to terminate processing.</span></span> <span data-ttu-id="f66ac-170">주문을 처리했다는 메시지가 나타나면 클라이언트를 다시 실행하여 서비스에서 실제로 메시지를 종료한 것이 확인될 때까지 다른 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-170">If the message indicates it has processed the order, you can run the client again to send another message until you see the service has actually terminated a message.</span></span> <span data-ttu-id="f66ac-171">구성된 포이즌 설정에 따라 최종 포이즌 큐로 이동하기 전에 메시지 처리가 한 번 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-171">Based on the configured poison settings, the message is tried once for processing before moving it to the final poison queue.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 0f063b71-93e0-42a1-aa3b-bca6c7a89546
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Processing Purchase Order: 5ef9a4fa-5a30-4175-b455-2fb1396095fa
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending

Aborting transaction, cannot process purchase order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
```

 <span data-ttu-id="f66ac-172">포이즌 메시지 서비스를 시작하여 포이즌 큐에서 포이즌 메시지를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-172">Start up the poison message service to read the poisoned message from the poison queue.</span></span> <span data-ttu-id="f66ac-173">이 예제에서는 포이즌 메시지 서비스가 메시지를 읽고 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-173">In this example, the poison message service reads the message and processes it.</span></span> <span data-ttu-id="f66ac-174">종료되어 포이즌 메시지가 된 구매 주문을 포이즌 메시지 서비스에서 읽는 것을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-174">You could see that the purchase order that was terminated and poisoned is read by the poison message service.</span></span>

```console
The service is ready.
Press <ENTER> to terminate service.

Processing Purchase Order: 23e0b991-fbf9-4438-a0e2-20adf93a4f89
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f66ac-175">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="f66ac-175">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="f66ac-176">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="f66ac-177">서비스가 처음 실행되는 경우 서비스에서는 큐가 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="f66ac-177">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="f66ac-178">큐가 없으면 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-178">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="f66ac-179">서비스를 처음 실행하여 큐를 만들거나 MSMQ 큐 관리자를 통해 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-179">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="f66ac-180">Windows 2008에서 큐를 만들려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="f66ac-180">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="f66ac-181">Visual Studio 2012에서 서버 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-181">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="f66ac-182">**기능** 탭을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-182">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="f66ac-183">**개인 메시지 큐** 를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**, **개인 큐** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-183">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="f66ac-184">**트랜잭션** 상자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-184">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="f66ac-185">`ServiceModelSamplesTransacted`새 큐의 이름으로을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-185">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="f66ac-186">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-186">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="f66ac-187">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 localhost 대신 실제 호스트 이름을 반영 하도록 큐 이름을 변경 하 고 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="f66ac-187">To run the sample in a single- or cross-computer configuration, change the queue names to reflect the actual hostname instead of localhost and follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

 <span data-ttu-id="f66ac-188">기본적으로 `netMsmqBinding` 바인딩 전송을 사용하여 보안이 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-188">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="f66ac-189">`MsmqAuthenticationMode` 및 `MsmqProtectionLevel` 속성은 모두 전송 보안의 형식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-189">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="f66ac-190">기본적으로 인증 모드는 `Windows`로 설정되고 보호 수준은 `Sign`으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-190">By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="f66ac-191">MSMQ에서 인증 및 서명 기능을 제공하려면 도메인에 속해 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-191">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="f66ac-192">도메인에 속하지 않은 컴퓨터에서 이 샘플을 실행할 경우 "사용자의 내부 메시지 큐 인증서가 없습니다."라는 오류 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-192">If you run this sample on a computer that is not part of a domain, you receive the following error: "User's internal message queuing certificate does not exist".</span></span>

#### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="f66ac-193">작업 그룹에 가입된 컴퓨터에서 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="f66ac-193">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="f66ac-194">컴퓨터가 도메인에 속하지 않는 경우 다음 샘플 구성과 같이 인증 모드와 보호 수준을 `None`으로 설정하여 전송 보안을 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-194">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding name="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

     <span data-ttu-id="f66ac-195">엔드포인트의 bindingConfiguration 특성을 설정하여 엔드포인트가 바인딩에 연결되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-195">Ensure the endpoint is associated with the binding by setting the endpoint's bindingConfiguration attribute.</span></span>

2. <span data-ttu-id="f66ac-196">샘플을 실행 하기 전에 PoisonMessageServer, 서버 및 클라이언트에서 구성을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-196">Ensure that you change the configuration on the PoisonMessageServer, server, and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f66ac-197">`security mode`를 `None`으로 설정하는 것은 `MsmqAuthenticationMode`, `MsmqProtectionLevel` 및 `Message` 보안을 `None`으로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-197">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel`, and `Message` security to `None`.</span></span>  
  
3. <span data-ttu-id="f66ac-198">메타데이터 교환을 작동하기 위해 http 바인딩을 사용하여 URL을 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-198">In order for Meta Data Exchange to work, we register a URL with http binding.</span></span> <span data-ttu-id="f66ac-199">이렇게 하려면 권한이 높은 명령 창에서 서비스를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-199">This requires that the service run in an elevated command window.</span></span> <span data-ttu-id="f66ac-200">그렇지 않으면와 같은 예외가 발생 `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-200">Otherwise, you get an exception such as: `Unhandled Exception: System.ServiceModel.AddressAccessDeniedException: HTTP could not register URL http://+:8000/ServiceModelSamples/service/. Your process does not have access rights to this namespace (see https://go.microsoft.com/fwlink/?LinkId=70353 for details). ---> System.Net.HttpListenerException: Access is denied`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f66ac-201">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-201">The samples may already be installed on your computer.</span></span> <span data-ttu-id="f66ac-202">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="f66ac-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f66ac-203">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f66ac-204">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f66ac-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Poison\MSMQ4`
