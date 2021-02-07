---
description: '자세한 정보: 메시지 상관 관계'
title: 메시지 상관 관계
ms.date: 03/30/2017
ms.assetid: 3f62babd-c991-421f-bcd8-391655c82a1f
ms.openlocfilehash: e38e2e8d6936132e165fd3372ac57fef27240d1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704032"
---
# <a name="message-correlation"></a><span data-ttu-id="ad86c-103">메시지 상관 관계</span><span class="sxs-lookup"><span data-stu-id="ad86c-103">Message Correlation</span></span>

<span data-ttu-id="ad86c-104">이 샘플은 메시지 큐 (MSMQ) 응용 프로그램에서 WCF (Windows Communication Foundation) 서비스로 MSMQ 메시지를 보내는 방법과 요청/응답 시나리오에서 보낸 사람과 받는 사람 응용 프로그램 간에 메시지를 상호 연결 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-104">This sample demonstrates how a Message Queuing (MSMQ) application can send an MSMQ message to a Windows Communication Foundation (WCF) service and how messages can be correlated between sender and receiver applications in a request/response scenario.</span></span> <span data-ttu-id="ad86c-105">이 샘플에서는 msmqIntegrationBinding 바인딩을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-105">This sample uses the msmqIntegrationBinding binding.</span></span> <span data-ttu-id="ad86c-106">이 경우 서비스는 자체 호스팅 콘솔 애플리케이션으로, 이를 사용하여 대기 중인 메시지를 받는 서비스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-106">The service in this case is a self-hosted console application to allow you to observe the service that receives queued messages.</span></span> <span data-ttu-id="ad86c-107">k</span><span class="sxs-lookup"><span data-stu-id="ad86c-107">k</span></span>

 <span data-ttu-id="ad86c-108">서비스는 발신자로부터 받은 메시지를 처리하여 발신자에게 응답 메시지를 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-108">The service processes the message received from the sender and sends a response message back to the sender.</span></span> <span data-ttu-id="ad86c-109">발신자는 받은 응답을 원래 보낸 요청에 상호 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-109">The sender correlates the response it received to the request it sent originally.</span></span> <span data-ttu-id="ad86c-110">메시지의 `MessageID` 속성과 `CorrelationID` 속성은 요청 메시지와 응답 메시지를 상호 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-110">The `MessageID` and `CorrelationID` properties of the message are used to correlate the request and response messages.</span></span>

 <span data-ttu-id="ad86c-111">`IOrderProcessor` 서비스 계약은 큐에 사용하기 적합한 단방향 서비스 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-111">The `IOrderProcessor` service contract defines a one-way service operation that is suitable for use with queuing.</span></span> <span data-ttu-id="ad86c-112">MSMQ 메시지에는 동작 헤더가 없기 때문에 여러 MSMQ 메시지를 작업 계약에 자동으로 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-112">An MSMQ message does not have an Action header, so it is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="ad86c-113">따라서 이 경우에는 한 작업 계약만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-113">Therefore, there can be only one operation contract in this case.</span></span> <span data-ttu-id="ad86c-114">서비스에 좀더 많은 작업 계약을 정의하려는 경우 애플리케이션은 발송할 작업 계약을 결정하는 데 사용할 수 있는 MSMQ 메시지의 헤더에 대한 정보(예: 레이블 또는 correlationID)를 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-114">If you want to define more operation contracts in the service, the application must provide information as to which header in the MSMQ message (for example, the label, or correlationID) can be used to decide which operation contract to dispatch.</span></span>

 <span data-ttu-id="ad86c-115">MSMQ 메시지에는 작업 계약의 다른 매개 변수에 매핑되는 헤더에 대한 정보도 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-115">The MSMQ message also does not contain information as to which headers are mapped to the different parameters of the operation contract.</span></span> <span data-ttu-id="ad86c-116">따라서 작업 계약에는 한 매개 변수만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-116">Therefore, there can be only one parameter in the operation contract.</span></span> <span data-ttu-id="ad86c-117">매개 변수는 내부 MSMQ 메시지를 포함 하는 형식입니다 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> .</span><span class="sxs-lookup"><span data-stu-id="ad86c-117">The parameter is of type <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601>, which contains the underlying MSMQ message.</span></span> <span data-ttu-id="ad86c-118">`MsmqMessage<T>` 클래스의 "T" 형식은 MSMQ 메시지 본문에 serialize되는 데이터를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-118">The type "T" in the `MsmqMessage<T>` class represents the data that is serialized into the MSMQ message body.</span></span> <span data-ttu-id="ad86c-119">이 샘플에서는 `PurchaseOrder` 형식이 MSMQ 메시지 본문으로 serialize됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-119">In this sample, the `PurchaseOrder` type is serialized into the MSMQ message body.</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
[ServiceKnownType(typeof(PurchaseOrder))]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, Action = "*")]
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);
}
```

 <span data-ttu-id="ad86c-120">서비스 작업을 통해 구매 주문을 처리하고 구매 주문의 내용과 상태를 서비스 콘솔 창에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-120">The service operation processes the purchase order and displays the contents of the purchase order and its status in the service console window.</span></span> <span data-ttu-id="ad86c-121"><xref:System.ServiceModel.OperationBehaviorAttribute>를 통해 트랜잭션에 작업을 큐로 나열하고 작업이 반환되면 트랜잭션이 완료된 것으로 표시하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-121">The <xref:System.ServiceModel.OperationBehaviorAttribute> configures the operation to enlist in a transaction with the queue and to mark the transaction complete when the operation returns.</span></span> <span data-ttu-id="ad86c-122">`PurchaseOrder`에는 서비스에서 처리해야 할 주문 세부 정보가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-122">The `PurchaseOrder` contains the order details that must be processed by the service.</span></span>

```csharp
// Service class that implements the service contract.
public class OrderProcessorService : IOrderProcessor
{
   [OperationBehavior(TransactionScopeRequired = true,
          TransactionAutoComplete = true)]
   public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> ordermsg)
   {
       PurchaseOrder po = (PurchaseOrder)ordermsg.Body;
       Random statusIndexer = new Random();
       po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];
       Console.WriteLine("Processing {0} ", po);
       //Send a response to the client that the order has been received
         and is pending fullfillment.
       SendResponse(ordermsg);
    }

    private void SendResponse(MsmqMessage<PurchaseOrder> ordermsg)
    {
        OrderResponseClient client = new OrderResponseClient("OrderResponseEndpoint");

        //Set the correlation ID such that the client can correlate the response to the order.
        MsmqMessage<PurchaseOrder> orderResponsemsg = new MsmqMessage<PurchaseOrder>(ordermsg.Body);
        orderResponsemsg.CorrelationId = ordermsg.Id;
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.SendOrderResponse(orderResponsemsg);
            scope.Complete();
        }

        client.Close();
    }
}
```

 <span data-ttu-id="ad86c-123">서비스는 사용자 지정 클라이언트 `OrderResponseClient`를 사용하여 MSMQ 메시지를 큐에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-123">The service uses a custom client `OrderResponseClient` to send the MSMQ message to the queue.</span></span> <span data-ttu-id="ad86c-124">메시지를 수신 하 고 처리 하는 응용 프로그램은 WCF 응용 프로그램이 아니라 MSMQ 응용 프로그램 이므로 두 응용 프로그램 간에 암시적 서비스 계약이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-124">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="ad86c-125">따라서 이 시나리오에서는 Svcutil.exe 도구를 사용하여 프록시를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-125">So we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>

 <span data-ttu-id="ad86c-126">사용자 지정 프록시는 바인딩을 사용 하 여 메시지를 보내는 모든 WCF 응용 프로그램에 대해 기본적으로 동일 합니다 `msmqIntegrationBinding` .</span><span class="sxs-lookup"><span data-stu-id="ad86c-126">The custom proxy is essentially the same for all WCF applications that use the `msmqIntegrationBinding` binding to send messages.</span></span> <span data-ttu-id="ad86c-127">하지만 다른 프록시와 달리 사용자 지정 프록시에는 일정 범위의 서비스 작업이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-127">Unlike other proxies, it does not include a range of service operations.</span></span> <span data-ttu-id="ad86c-128">메시지 제출 작업으로만 한정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-128">It is a submit message operation only.</span></span>

```csharp
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]
public interface IOrderResponse
{

    [System.ServiceModel.OperationContractAttribute(IsOneWay = true, Action = "*")]
    void SendOrderResponse(MsmqMessage<PurchaseOrder> msg);
}

public partial class OrderResponseClient : System.ServiceModel.ClientBase<IOrderResponse>, IOrderResponse
{

    public OrderResponseClient()
    { }

    public OrderResponseClient(string configurationName)
        : base(configurationName)
    { }

    public OrderResponseClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)
        : base(binding, address)
    { }

    public void SendOrderResponse(MsmqMessage<PurchaseOrder> msg)
    {
        base.Channel.SendOrderResponse(msg);
    }
}
```

 <span data-ttu-id="ad86c-129">서비스는 자체 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-129">The service is self hosted.</span></span> <span data-ttu-id="ad86c-130">MSMQ 통합 전송을 사용하는 경우에는 사용되는 큐를 미리 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-130">When using the MSMQ integration transport, the queue used must be created in advance.</span></span> <span data-ttu-id="ad86c-131">수동으로 또는 코드를 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-131">This can be done manually or through code.</span></span> <span data-ttu-id="ad86c-132">이 샘플의 서비스에는 큐가 있는지 확인하고 필요한 경우 만드는 <xref:System.Messaging> 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-132">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and create it if necessary.</span></span> <span data-ttu-id="ad86c-133">큐 이름은 구성 파일에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-133">The queue name is read from the configuration file.</span></span>

```csharp
public static void Main()
{
       // Get the MSMQ queue name from application settings in configuration.
      string queueName =
                ConfigurationManager.AppSettings["orderQueueName"];
      // Create the transacted MSMQ queue if necessary.
      if (!MessageQueue.Exists(queueName))
                MessageQueue.Create(queueName, true);
     // Create a ServiceHost for the OrderProcessorService type.
     using (ServiceHost serviceHost = new
                   ServiceHost(typeof(OrderProcessorService)))
     {
            serviceHost.Open();
            // The service can now be accessed.
            Console.WriteLine("The service is ready.");
            Console.WriteLine("Press <ENTER> to terminate service.");
            Console.ReadLine();
            // Close the ServiceHost to shutdown the service.
            serviceHost.Close();
      }
}
```

 <span data-ttu-id="ad86c-134">주문 요청을 받는 MSMQ 큐는 구성 파일의 appSettings 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-134">The MSMQ queue to which the order requests are sent is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="ad86c-135">클라이언트 엔드포인트와 서비스 엔드포인트는 구성 파일의 system.serviceModel 섹션에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-135">The client and service endpoints are defined in the system.serviceModel section of the configuration file.</span></span> <span data-ttu-id="ad86c-136">둘 다 `msmqIntegrationbinding` 바인딩을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-136">Both specify the `msmqIntegrationbinding` binding.</span></span>

```xml
<appSettings>
  <add key="orderQueueName" value=".\private$\Orders" />
</appSettings>

<system.serviceModel>
  <client>
    <endpoint    name="OrderResponseEndpoint"
              address="msmq.formatname:DIRECT=OS:.\private$\OrderResponse"
              binding="msmqIntegrationBinding"
              bindingConfiguration="OrderProcessorBinding"
              contract="Microsoft.ServiceModel.Samples.IOrderResponse">
    </endpoint>
  </client>

  <services>
    <service
      name="Microsoft.ServiceModel.Samples.OrderProcessorService">
      <endpoint address="msmq.formatname:DIRECT=OS:.\private$\Orders"
                            binding="msmqIntegrationBinding"
                bindingConfiguration="OrderProcessorBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor">
      </endpoint>
    </service>
  </services>

  <bindings>
    <msmqIntegrationBinding>
      <binding name="OrderProcessorBinding" >
        <security mode="None" />
      </binding>
    </msmqIntegrationBinding>
  </bindings>

</system.serviceModel>
```

 <span data-ttu-id="ad86c-137">클라이언트 애플리케이션은 <xref:System.Messaging>을 사용하여 지속적인 메시지와 트랜잭션 메시지를 큐로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-137">The client application uses <xref:System.Messaging> to send a durable and transactional message to the queue.</span></span> <span data-ttu-id="ad86c-138">메시지 본문에는 구매 주문이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-138">The message's body contains the purchase order.</span></span>

```csharp
static void PlaceOrder()
{
    //Connect to the queue
    MessageQueue orderQueue =
            new MessageQueue(
                    ConfigurationManager.AppSettings["orderQueueName"])
    // Create the purchase order.
    PurchaseOrder po = new PurchaseOrder();
    po.CustomerId = "somecustomer.com";
    po.PONumber = Guid.NewGuid().ToString();
    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
    lineItem1.ProductId = "Blue Widget";
    lineItem1.Quantity = 54;
    lineItem1.UnitCost = 29.99F;

    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
    lineItem2.ProductId = "Red Widget";
    lineItem2.Quantity = 890;
    lineItem2.UnitCost = 45.89F;

    po.orderLineItems = new PurchaseOrderLineItem[2];
    po.orderLineItems[0] = lineItem1;
    po.orderLineItems[1] = lineItem2;

    Message msg = new Message();
    msg.UseDeadLetterQueue = true;
    msg.Body = po;

    //Create a transaction scope.
    using (TransactionScope scope = new
     TransactionScope(TransactionScopeOption.Required))
    {
        // Submit the purchase order.
        orderQueue.Send(msg, MessageQueueTransactionType.Automatic);
        // Complete the transaction.
        scope.Complete();
    }
    //Save the messageID for order response correlation.
    orderMessageID = msg.Id;
    Console.WriteLine("Placed the order, waiting for response...");
}
```

 <span data-ttu-id="ad86c-139">주문 응답을 받는 MSMQ 큐는 다음 샘플 구성에 표시된 것처럼 구성 파일의 appSettings 섹션에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-139">The MSMQ queue from which the order responses are received is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="ad86c-140">큐 이름은 로컬 컴퓨터에 점(.)을, 그 경로에는 백슬래시 구분 기호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-140">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="ad86c-141">WCF 끝점 주소는 msmq.formatname 체계를 지정 하며 로컬 컴퓨터에 대해 "localhost"를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-141">The WCF endpoint address specifies a msmq.formatname scheme, and uses "localhost" for the local computer.</span></span> <span data-ttu-id="ad86c-142">적절한 형식의 형식 이름은 MSMQ 지침에 따라 URI에서 msmq.formatname을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-142">A properly formed format name follows msmq.formatname in the URI according to MSMQ guidelines.</span></span>

```xml
<appSettings>
    <add key=" orderResponseQueueName" value=".\private$\Orders" />
</appSettings>
```

 <span data-ttu-id="ad86c-143">클라이언트 애플리케이션은 서비스로 보내는 주문 요청 메시지의 `messageID`를 저장하고 서비스의 응답을 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-143">The client application saves the `messageID` of the order request message that it sends to the service and waits for a response from the service.</span></span> <span data-ttu-id="ad86c-144">큐에 응답이 도착하면 클라이언트는 메시지의 `correlationID` 속성을 사용하여 보낸 주문 메시지와 응답 메시지를 상호 연결합니다. 여기에는 클라이언트에서 원래 서비스로 보낸 주문 메시지의 `messageID`가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-144">Once a response arrives in the queue the client correlates it with the order message it sent using the `correlationID` property of the message, which contains the `messageID` of the order message that the client sent to the service originally.</span></span>

```csharp
static void DisplayOrderStatus()
{
    MessageQueue orderResponseQueue = new
     MessageQueue(ConfigurationManager.AppSettings
                  ["orderResponseQueueName"]);
    //Create a transaction scope.
    bool responseReceived = false;
    orderResponseQueue.MessageReadPropertyFilter.CorrelationId = true;
    while (!responseReceived)
    {
       Message responseMsg;
       using (TransactionScope scope2 = new
         TransactionScope(TransactionScopeOption.Required))
       {
          //Receive the Order Response message.
          responseMsg =
              orderResponseQueue.Receive
                   (MessageQueueTransactionType.Automatic);
          scope2.Complete();
     }
     responseMsg.Formatter = new
     System.Messaging.XmlMessageFormatter(new Type[] {
         typeof(PurchaseOrder) });
     PurchaseOrder responsepo = (PurchaseOrder)responseMsg.Body;
    //Check if the response is for the order placed.
    if (orderMessageID == responseMsg.CorrelationId)
    {
       responseReceived = true;
       Console.WriteLine("Status of current Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
    else
    {
       Console.WriteLine("Status of previous Order: OrderID-{0},Order
            Status-{1}", responsepo.PONumber, responsepo.Status);
    }
  }
}
```

 <span data-ttu-id="ad86c-145">샘플을 실행하면 클라이언트 및 서비스 동작이 서비스 콘솔 창과 클라이언트 콘솔 창에 모두 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-145">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="ad86c-146">클라이언트의 서비스 수신 메시지를 확인하고 클라이언트로 다시 응답을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-146">You can see the service receive messages from the client and sends a response back to the client.</span></span> <span data-ttu-id="ad86c-147">클라이언트는 서비스로부터 받은 응답을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-147">The client displays the response received from the service.</span></span> <span data-ttu-id="ad86c-148">서비스와 클라이언트를 종료하려면 각 콘솔 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-148">Press ENTER in each console window to shut down the service and client.</span></span>

> [!NOTE]
> <span data-ttu-id="ad86c-149">이 샘플을 사용하려면 MSMQ(메시지 큐)를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-149">This sample requires the installation of Message Queuing (MSMQ).</span></span> <span data-ttu-id="ad86c-150">참고 항목 단원의 MSMQ 설치 지침을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="ad86c-150">See the MSMQ installation instructions in the See Also section.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="ad86c-151">샘플 설정, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="ad86c-151">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="ad86c-152">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="ad86c-153">서비스가 처음 실행되는 경우 서비스에서는 큐가 있는지 확인하고</span><span class="sxs-lookup"><span data-stu-id="ad86c-153">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="ad86c-154">큐가 없으면 큐를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-154">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="ad86c-155">서비스를 처음 실행하여 큐를 만들거나 MSMQ 큐 관리자를 통해 큐를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-155">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="ad86c-156">Windows 2008에서 큐를 만들려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="ad86c-156">Follow these steps to create a queue in Windows 2008.</span></span>

    1. <span data-ttu-id="ad86c-157">Visual Studio 2012에서 서버 관리자를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-157">Open Server Manager in Visual Studio 2012.</span></span>

    2. <span data-ttu-id="ad86c-158">**기능** 탭을 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-158">Expand the **Features** tab.</span></span>

    3. <span data-ttu-id="ad86c-159">**개인 메시지 큐** 를 마우스 오른쪽 단추로 클릭 하 고 **새로 만들기**, **개인 큐** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-159">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>

    4. <span data-ttu-id="ad86c-160">**트랜잭션** 상자를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-160">Check the **Transactional** box.</span></span>

    5. <span data-ttu-id="ad86c-161">`ServiceModelSamplesTransacted`새 큐의 이름으로을 입력 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-161">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>

3. <span data-ttu-id="ad86c-162">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="ad86c-163">단일 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="ad86c-163">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

## <a name="run-the-sample-across-computers"></a><span data-ttu-id="ad86c-164">컴퓨터에서 샘플 실행</span><span class="sxs-lookup"><span data-stu-id="ad86c-164">Run the sample across computers</span></span>

1. <span data-ttu-id="ad86c-165">언어별 폴더의 \service\bin\ 폴더에서 서비스 컴퓨터로 서비스 프로그램 파일을 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-165">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>

2. <span data-ttu-id="ad86c-166">언어별 폴더의 \client\bin\ 폴더에서 클라이언트 프로그램 파일을 클라이언트 컴퓨터로 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-166">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>

3. <span data-ttu-id="ad86c-167">Client.exe.config 파일에서 orderQueueName을 변경하여 "." 대신 서비스 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-167">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>

4. <span data-ttu-id="ad86c-168">Service.exe.config 파일에서 클라이언트 엔드포인트 주소를 변경하여 "." 대신 클라이언트 컴퓨터 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-168">In the Service.exe.config file, change the client endpoint address to specify the client computer name instead of ".".</span></span>

5. <span data-ttu-id="ad86c-169">서비스 컴퓨터의 명령 프롬프트에서 Service.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-169">On the service computer, launch Service.exe from a command prompt.</span></span>

6. <span data-ttu-id="ad86c-170">클라이언트 컴퓨터의 명령 프롬프트에서 Client.exe를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-170">On the client computer, launch Client.exe from a command prompt.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ad86c-171">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-171">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ad86c-172">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ad86c-172">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="ad86c-173">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-173">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ad86c-174">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad86c-174">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\MessageCorrelation`

## <a name="see-also"></a><span data-ttu-id="ad86c-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad86c-175">See also</span></span>

- [<span data-ttu-id="ad86c-176">WCF의 큐</span><span class="sxs-lookup"><span data-stu-id="ad86c-176">Queuing in WCF</span></span>](../feature-details/queuing-in-wcf.md)
- <span data-ttu-id="ad86c-177">[메시지 큐](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="ad86c-177">[Message Queuing](/previous-versions/windows/desktop/legacy/ms711472(v=vs.85))</span></span>
