---
description: '자세한 정보: 전송: UDP를 통한 사용자 지정 트랜잭션 샘플'
title: '전송: UDP 샘플에 의한 사용자 지정 트랜잭션'
ms.date: 03/30/2017
ms.assetid: 6cebf975-41bd-443e-9540-fd2463c3eb23
ms.openlocfilehash: 609576c74a8a3c0cd55829335545818028d444bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668515"
---
# <a name="transport-custom-transactions-over-udp-sample"></a><span data-ttu-id="da274-103">전송: UDP 샘플에 의한 사용자 지정 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="da274-103">Transport: Custom Transactions over UDP Sample</span></span>

<span data-ttu-id="da274-104">이 샘플은 Windows Communication Foundation (WCF)[전송 확장성](transport-extensibility.md)의 [전송: UDP](transport-udp.md) 샘플을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-104">This sample is based on the [Transport: UDP](transport-udp.md) sample in the Windows Communication Foundation (WCF)[Transport Extensibility](transport-extensibility.md).</span></span> <span data-ttu-id="da274-105">이 샘플은 사용자 지정 트랜잭션 흐름을 지원하도록 UDP 전송 샘플을 확장하고 <xref:System.ServiceModel.Channels.TransactionMessageProperty> 속성의 사용 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="da274-105">It extends the UDP Transport sample to support custom transaction flow and demonstrates the use of the <xref:System.ServiceModel.Channels.TransactionMessageProperty> property.</span></span>  
  
## <a name="code-changes-in-the-udp-transport-sample"></a><span data-ttu-id="da274-106">UDP 전송 샘플의 코드 변경</span><span class="sxs-lookup"><span data-stu-id="da274-106">Code Changes in the UDP Transport Sample</span></span>  

 <span data-ttu-id="da274-107">트랜잭션 흐름을 보여 주기 위해 이 샘플에서는 `ICalculatorContract`의 트랜잭션 범위가 필요하도록 `CalculatorService.Add()`의 서비스 계약을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-107">To demonstrate transaction flow, the sample changes the service contract for `ICalculatorContract` to require a transaction scope for `CalculatorService.Add()`.</span></span> <span data-ttu-id="da274-108">또한 `System.Guid` 작업의 계약에 `Add` 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-108">The sample also adds an extra `System.Guid` parameter to the contract of the `Add` operation.</span></span> <span data-ttu-id="da274-109">이 매개 변수는 클라이언트 트랜잭션의 식별자를 서비스에 전달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-109">This parameter is used to pass the identifier of the client transaction to the service.</span></span>  
  
```csharp  
class CalculatorService : IDatagramContract, ICalculatorContract  
{  
    [OperationBehavior(TransactionScopeRequired=true)]  
    public int Add(int x, int y, Guid clientTransactionId)  
    {  
        if(Transaction.Current.TransactionInformation.DistributedIdentifier == clientTransactionId)  
    {  
        Console.WriteLine("The client transaction has flowed to the service");  
    }  
    else  
    {  
     Console.WriteLine("The client transaction has NOT flowed to the service");  
    }  
  
    Console.WriteLine("   adding {0} + {1}", x, y);
    return (x + y);  
    }  
  
    [...]  
}  
```  
  
 <span data-ttu-id="da274-110">[전송: udp](transport-udp.md) 샘플에서는 udp 패킷을 사용 하 여 클라이언트와 서비스 간에 메시지를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-110">The [Transport: UDP](transport-udp.md) sample uses UDP packets to pass messages between a client and a service.</span></span> <span data-ttu-id="da274-111">[전송: 사용자 지정 전송 예제](transport-custom-transactions-over-udp-sample.md) 는 동일한 메커니즘을 사용 하 여 메시지를 전송 하지만 트랜잭션이 이동 하면 인코딩된 메시지와 함께 UDP 패킷에 삽입 됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-111">The [Transport: Custom Transport Sample](transport-custom-transactions-over-udp-sample.md) uses the same mechanism to transport messages, but when a transaction is flowed, it is inserted into the UDP packet along with the encoded message.</span></span>  
  
```csharp  
byte[] txmsgBuffer = TransactionMessageBuffer.WriteTransactionMessageBuffer(txPropToken, messageBuffer);  
  
int bytesSent = this.socket.SendTo(txmsgBuffer, 0, txmsgBuffer.Length, SocketFlags.None, this.remoteEndPoint);  
```  
  
 <span data-ttu-id="da274-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer`는 현재 트랜잭션의 전파 토큰을 메시지 엔터티와 병합하고 이를 버퍼에 배치하는 새로운 기능이 포함된 도우미 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="da274-112">`TransactionMessageBuffer.WriteTransactionMessageBuffer` is a helper method that contains new functionality to merge the propagation token for the current transaction with the message entity and place it into a buffer.</span></span>  
  
 <span data-ttu-id="da274-113">사용자 지정 트랜잭션 흐름 전송의 경우 클라이언트 구현에서 트랜잭션 흐름이 필요한 서비스 작업을 알고이 정보를 WCF에 전달 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-113">For custom transaction flow transport, the client implementation must know what service operations require transaction flow and to pass this information to WCF.</span></span> <span data-ttu-id="da274-114">또한 사용자 트랜잭션을 전송 계층으로 전송하기 위한 메커니즘도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-114">There should also be a mechanism for transmitting the user transaction to the transport layer.</span></span> <span data-ttu-id="da274-115">이 샘플에서는 "WCF 메시지 검사기"를 사용 하 여이 정보를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="da274-115">This sample uses "WCF message inspectors" to obtain this information.</span></span> <span data-ttu-id="da274-116">여기서 구현된 `TransactionFlowInspector`라는 클라이언트 메시지 검사자는 다음 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-116">The client message inspector implemented here, which is called `TransactionFlowInspector`, performs the following tasks:</span></span>  
  
- <span data-ttu-id="da274-117">지정된 메시지 작업에 대해 트랜잭션을 이동해야 하는지 여부를 결정합니다. 이 작업은 `IsTxFlowRequiredForThisOperation()`에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-117">Determines whether a transaction must be flowed for a given message action (this takes place in `IsTxFlowRequiredForThisOperation()`).</span></span>  
  
- <span data-ttu-id="da274-118">트랜잭션을 이동해야 하는 경우 `TransactionFlowProperty`를 사용하여 현재 앰비언트 트랜잭션을 메시지에 연결합니다. 이 작업은 `BeforeSendRequest()`에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-118">Attaches the current ambient transaction to the message using `TransactionFlowProperty`, if a transaction is required to be flowed (this is done in `BeforeSendRequest()`).</span></span>  
  
```csharp  
public class TransactionFlowInspector : IClientMessageInspector  
{  
   void IClientMessageInspector.AfterReceiveReply(ref           System.ServiceModel.Channels.Message reply, object correlationState)  
  {  
  }  
  
   public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
   {  
       // obtain the tx propagation token  
       byte[] propToken = null;
       if (Transaction.Current != null && IsTxFlowRequiredForThisOperation(request.Headers.Action))  
       {  
           try  
           {  
               propToken = TransactionInterop.GetTransmitterPropagationToken(Transaction.Current);  
           }  
           catch (TransactionException e)  
           {  
              throw new CommunicationException("TransactionInterop.GetTransmitterPropagationToken failed.", e);  
           }  
       }  
  
      // set the propToken on the message in a TransactionFlowProperty  
       TransactionFlowProperty.Set(propToken, request);  
  
       return null;
    }  
  }  
  
  static bool IsTxFlowRequiredForThisOperation(String action)  
 {  
       // In general, this should contain logic to identify which operations (actions)      require transaction flow.  
      [...]  
 }  
}  
```  
  
 <span data-ttu-id="da274-119">`TransactionFlowInspector` 자체는 사용자 지정 동작인 `TransactionFlowBehavior`를 사용하여 프레임워크에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-119">The `TransactionFlowInspector` itself is passed to the framework using a custom behavior: the `TransactionFlowBehavior`.</span></span>  
  
```csharp  
public class TransactionFlowBehavior : IEndpointBehavior  
{  
       public void AddBindingParameters(ServiceEndpoint endpoint,            System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
      {  
      }  
  
       public void ApplyClientBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
      {  
            TransactionFlowInspector inspector = new TransactionFlowInspector();  
            clientRuntime.MessageInspectors.Add(inspector);  
      }  
  
      public void ApplyDispatchBehavior(ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.EndpointDispatcher endpointDispatcher)  
     {  
     }  
  
      public void Validate(ServiceEndpoint endpoint)  
      {  
      }  
}  
```  
  
 <span data-ttu-id="da274-120">위 메커니즘을 유지한 상태에서 사용자 코드는 서비스 작업을 호출하기 전에 `TransactionScope`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="da274-120">With the preceding mechanism in place, the user code creates a `TransactionScope` before calling the service operation.</span></span> <span data-ttu-id="da274-121">트랜잭션을 서비스 작업으로 이동해야 하는 경우 메시지 검사자는 트랜잭션이 전송에 전달되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-121">The message inspector ensures that the transaction is passed to the transport in case it is required to be flowed to the service operation.</span></span>  
  
```csharp  
CalculatorContractClient calculatorClient = new CalculatorContractClient("SampleProfileUdpBinding_ICalculatorContract");  
calculatorClient.Endpoint.Behaviors.Add(new TransactionFlowBehavior());
  
try  
{  
       for (int i = 0; i < 5; ++i)  
      {  
              // call the 'Add' service operation under a transaction scope  
             using (TransactionScope ts = new TransactionScope())  
             {  
        [...]  
        Console.WriteLine(calculatorClient.Add(i, i * 2));  
         }  
      }
       calculatorClient.Close();  
}  
catch (TimeoutException)  
{  
    calculatorClient.Abort();  
}  
catch (CommunicationException)  
{  
    calculatorClient.Abort();  
}  
catch (Exception)  
{  
    calculatorClient.Abort();  
    throw;  
}  
```  
  
 <span data-ttu-id="da274-122">서비스는 클라이언트로부터 UDP 패킷을 수신한 다음 이 패킷을 역직렬화하여 메시지와 트랜잭션을 추출합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-122">Upon receiving a UDP packet from the client, the service deserializes it to extract the message and possibly a transaction.</span></span>  
  
```csharp  
count = listenSocket.EndReceiveFrom(result, ref dummy);  
  
// read the transaction and message                       TransactionMessageBuffer.ReadTransactionMessageBuffer(buffer, count, out transaction, out msg);  
```  
  
 <span data-ttu-id="da274-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()`는 `TransactionMessageBuffer.WriteTransactionMessageBuffer()`가 수행한 serialization 프로세스를 반대로 하는 도우미 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="da274-123">`TransactionMessageBuffer.ReadTransactionMessageBuffer()` is the helper method that reverses the serialization process performed by `TransactionMessageBuffer.WriteTransactionMessageBuffer()`.</span></span>  
  
 <span data-ttu-id="da274-124">트랜잭션이 이동하면 `TransactionMessageProperty`의 메시지에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-124">If a transaction was flowed in, it is appended to the message in the `TransactionMessageProperty`.</span></span>  
  
```csharp  
message = MessageEncoderFactory.Encoder.ReadMessage(msg, bufferManager);  
  
if (transaction != null)  
{  
       TransactionMessageProperty.Set(transaction, message);  
}  
```  
  
 <span data-ttu-id="da274-125">이렇게 하면 디스패처가 디스패치할 때 트랜잭션을 선택한 다음 메시지에 설명된 서비스 작업을 호출할 때 이 트랜잭션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-125">This ensures that the dispatcher picks up the transaction at dispatch time and uses it when calling the service operation addressed by the message.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="da274-126">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="da274-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="da274-127">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="da274-127">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="da274-128">현재 샘플은 [전송: UDP](transport-udp.md) 샘플과 유사 하 게 실행 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-128">The current sample should be run similarly to the [Transport: UDP](transport-udp.md) sample.</span></span> <span data-ttu-id="da274-129">이 샘플을 실행하려면 UdpTestService.exe를 실행하여 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-129">To run it, start the service with UdpTestService.exe.</span></span> <span data-ttu-id="da274-130">Windows Vista를 실행 하는 경우에는 상승 된 권한으로 서비스를 시작 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-130">If you are running Windows Vista, you must start the service with elevated privileges.</span></span> <span data-ttu-id="da274-131">이렇게 하려면 파일 탐색기에서 UdpTestService.exe을 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-131">To do so, right-click UdpTestService.exe in File Explorer and click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="da274-132">다음과 같은 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-132">This produces the following output.</span></span>  
  
    ```console  
    Testing Udp From Code.  
    Service is started from code...  
    Press <ENTER> to terminate the service and start service from config...  
    ```  
  
4. <span data-ttu-id="da274-133">이때 UdpTestClient.exe를 실행하여 클라이언트를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da274-133">At this time, you can start the client by running UdpTestClient.exe.</span></span> <span data-ttu-id="da274-134">클라이언트에서 생성되는 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="da274-134">The output produced by the client is as follows.</span></span>  
  
    ```console
    0  
    3  
    6  
    9  
    12  
    Press <ENTER> to complete test.  
    ```  
  
5. <span data-ttu-id="da274-135">서비스 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="da274-135">The service output is as follows.</span></span>  
  
    ```console
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    Hello, world!  
    The client transaction has flowed to the service  
       adding 0 + 0  
    The client transaction has flowed to the service  
       adding 1 + 2  
    The client transaction has flowed to the service  
       adding 2 + 4  
    The client transaction has flowed to the service  
       adding 3 + 6  
    The client transaction has flowed to the service  
       adding 4 + 8  
    ```  
  
6. <span data-ttu-id="da274-136">서비스 애플리케이션은 클라이언트가 보낸, `The client transaction has flowed to the service` 작업의 `clientTransactionId` 매개 변수에 포함된 트랜잭션 식별자를 서비스 트랜잭션의 식별자와 일치시킬 수 있는 경우 `CalculatorService.Add()`라는 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-136">The service application displays the message `The client transaction has flowed to the service` if it can match the transaction identifier sent by the client, in the `clientTransactionId` parameter of the `CalculatorService.Add()` operation, to the identifier of the service transaction.</span></span> <span data-ttu-id="da274-137">이 두 식별자는 클라이언트 트랜잭션이 서비스로 이동한 경우에만 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-137">A match is obtained only if the client transaction has flowed to the service.</span></span>  
  
7. <span data-ttu-id="da274-138">구성을 사용하여 게시된 엔드포인트에 대해 클라이언트 애플리케이션을 실행하려면 서비스 애플리케이션 창에서 Enter 키를 누른 다음 테스트 클라이언트를 다시 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-138">To run the client application against endpoints published using configuration, press ENTER on the service application window and then run the test client again.</span></span> <span data-ttu-id="da274-139">서비스에서 다음과 같이 출력되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-139">You should see the following output on the service.</span></span>  
  
    ```console  
    Testing Udp From Config.  
    Service is started from config...  
    Press <ENTER> to terminate the service and exit...  
    ```  
  
8. <span data-ttu-id="da274-140">서비스에 대해 클라이언트를 실행하면 이전과 비슷한 출력이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="da274-140">Running the client against the service now produces similar output as before.</span></span>  
  
9. <span data-ttu-id="da274-141">Svcutil.exe를 사용하여 클라이언트 코드 및 구성을 다시 생성하려면 서비스 애플리케이션을 시작한 다음 샘플의 루트 디렉터리에서 다음 Svcutil.exe 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-141">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe command from the root directory of the sample.</span></span>  
  
    ```console  
    svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
    ```  
  
10. <span data-ttu-id="da274-142">Svcutil.exe는 `sampleProfileUdpBinding`에 대한 바인딩 확장명 구성을 생성하지 않으므로 직접 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-142">Note that Svcutil.exe does not generate the binding extension configuration for the `sampleProfileUdpBinding`; you must add it manually.</span></span>  
  
    ```xml  
    <configuration>  
        <system.serviceModel>
            …  
            <extensions>  
                <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
                <bindingExtensions>  
                    <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
                </bindingExtensions>  
            </extensions>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
> [!IMPORTANT]
> <span data-ttu-id="da274-143">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da274-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="da274-144">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="da274-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="da274-145">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="da274-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="da274-146">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="da274-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transactions\TransactionMessagePropertyUDPTransport`  
  
## <a name="see-also"></a><span data-ttu-id="da274-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="da274-147">See also</span></span>

- [<span data-ttu-id="da274-148">전송: UDP</span><span class="sxs-lookup"><span data-stu-id="da274-148">Transport: UDP</span></span>](transport-udp.md)
