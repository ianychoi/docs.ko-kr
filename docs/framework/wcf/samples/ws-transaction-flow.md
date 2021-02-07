---
description: WS 트랜잭션 흐름에 대해 자세히 알아보세요.
title: WS Transaction Flow
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 4d0a0af77dd516bf98c5dc8318ac110a31e731e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99668372"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="4f344-103">WS Transaction Flow</span><span class="sxs-lookup"><span data-stu-id="4f344-103">WS Transaction Flow</span></span>

<span data-ttu-id="4f344-104">이 샘플에서는 클라이언트에서 조정하는 트랜잭션의 사용법과 WS-Atomic Transaction 또는 OleTransactions 프로토콜을 사용하는 트랜잭션 흐름의 클라이언트 및 서버 옵션을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-104">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="4f344-105">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 하지만 작업에는 `TransactionFlowAttribute` **TransactionFlowOption** 열거형과 함께를 사용 하 여 트랜잭션 흐름을 사용할 수 있는 정도를 결정 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="4f344-106">흐름이 지정된 트랜잭션의 범위 내에서는 요청한 작업에 대한 로그가 데이터베이스에 기록되고 클라이언트에서 조정하는 트랜잭션이 완료될 때까지 유지됩니다. 클라이언트 트랜잭션이 완료되지 않으면 웹 서비스 트랜잭션에서 데이터베이스에 적합한 업데이트가 커밋되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-106">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f344-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4f344-108">서비스 및 트랜잭션에 대한 연결을 시작하면 클라이언트에서 여러 가지 서비스 작업에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-108">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="4f344-109">서비스에 대한 계약은 서로 다른 `TransactionFlowOption` 설정을 보여 주는 각 작업을 사용하여 다음과 같이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-109">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);
}  
```

 <span data-ttu-id="4f344-110">여기서는 처리될 순서대로 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-110">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="4f344-111">`Add` 연산 요청에는 흐름이 지정된 트랜잭션이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-111">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="4f344-112">`Subtract` 연산 요청에는 흐름이 지정된 트랜잭션이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-112">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="4f344-113">`Multiply` 연산 요청에는 명시적으로 NotAllowed를 설정하여 흐름이 지정된 트랜잭션을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-113">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="4f344-114">`Divide` 연산 요청에는`TransactionFlow` 특성을 생략하여 흐름이 지정된 트랜잭션을 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-114">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="4f344-115">트랜잭션 흐름을 사용 하도록 설정 하려면 [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) 적절 한 작업 특성 외에도 속성이 활성화 된 바인딩을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-115">To enable transaction flow, bindings with the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="4f344-116">이 샘플의 서비스 구성에서는 메타데이터 교환 엔드포인트뿐만 아니라 TCP 엔드포인트와 HTTP 엔드포인트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-116">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="4f344-117">TCP 끝점과 HTTP 끝점은 모두 속성이 활성화 된 다음 바인딩을 사용 합니다 [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) .</span><span class="sxs-lookup"><span data-stu-id="4f344-117">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
> <span data-ttu-id="4f344-118">시스템 제공 netTcpBinding을 사용하면 transactionProtocol을 지정할 수 있지만 시스템 제공 wsHttpBinding에서는 상호 운용성이 보다 뛰어난 WSAtomicTransactionOctober2004 프로토콜만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-118">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="4f344-119">OleTransactions 프로토콜은 WCF (Windows Communication Foundation) 클라이언트 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-119">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="4f344-120">`ICalculator` 인터페이스를 구현하는 클래스에 대한 모든 메서드의 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 속성은 `true`로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-120">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="4f344-121">이 설정은 메서드 내에서 수행되는 모든 작업이 트랜잭션의 범위 내에서 발생하도록 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-121">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="4f344-122">이 경우 수행되는 작업에는 로그 데이터베이스에 기록하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-122">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="4f344-123">작업 요청에 흐름이 지정된 트랜잭션이 포함되면 들어오는 트랜잭션의 범위 내에서 작업이 발생하거나 새 트랜잭션 범위가 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-123">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f344-124"><xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> 속성은 서비스 메서드 구현에 로컬인 동작을 정의하며 트랜잭션 흐름에 대한 클라이언트의 기능이나 요구 사항은 정의하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-124">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="4f344-125">클라이언트에서 작업에 대한 서비스의 `TransactionFlowOption`설정은`ICalculator` 인터페이스에 대해 클라이언트에서 생성한 정의에 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-125">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="4f344-126">또한 서비스의 `transactionFlow` 속성 설정은 클라이언트의 애플리케이션 구성에 반영됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-126">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="4f344-127">클라이언트는 다음과 같이 적합한 `endpointConfigurationName`을 선택하여 전송 및 프로토콜을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-127">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="4f344-128">이 샘플의 실제 동작은 선택한 프로토콜이나 전송에 관계없이 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-128">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="4f344-129">서비스에 대한 연결을 시작하면 클라이언트는 다음과 같이 서비스 작업에 대한 호출에 따라 `TransactionScope`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-129">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="4f344-130">다음과 같이 작업이 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-130">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="4f344-131">`Add` 요청에서 필요한 트랜잭션의 흐름을 서비스로 지정하고 서비스의 작업은 클라이언트의 트랜잭션 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-131">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="4f344-132">첫 번째 `Subtract` 요청에서도 허용된 트랜잭션의 흐름을 서비스로 지정하고 서비스의 작업도 클라이언트의 트랜잭션 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-132">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="4f344-133">두 번째 `Subtract` 요청은 `TransactionScopeOption.Suppress` 옵션으로 선언된 새 트랜잭션 범위 내에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-133">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="4f344-134">따라서 클라이언트의 초기 외부 트랜잭션이 표시되지 않고 요청에서 트랜잭션의 흐름을 서비스로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-134">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="4f344-135">이 접근 방식을 사용하면 필요하지 않은 경우 클라이언트에서 트랜잭션 흐름이 실행되지 않도록 하고 트랜잭션 흐름이 서비스로 지정되지 않도록 보호할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-135">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="4f344-136">서비스의 작업은 새 트랜잭션과 연결되지 않은 트랜잭션의 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-136">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="4f344-137">`Multiply` 요청에서는`ICalculator` 인터페이스에 대해 클라이언트에서 생성한 정의에 <xref:System.ServiceModel.TransactionFlowAttribute>이<xref:System.ServiceModel.TransactionFlowOption>로 설정된 `NotAllowed`가 포함되므로 트랜잭션의 흐름을 서비스로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-137">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="4f344-138">`Divide` 요청에서도 `ICalculator` 인터페이스에 대해 클라이언트에서 생성한 정의에 `TransactionFlowAttribute`가 포함되지 않으므로 트랜잭션의 흐름을 서비스로 지정하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-138">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="4f344-139">또한 서비스의 작업은 또 다른 새 트랜잭션과 연결되지 않은 트랜잭션의 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-139">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="4f344-140">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-140">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4f344-141">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-141">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="4f344-142">서비스 작업 요청의 로깅은 서비스의 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-142">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="4f344-143">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-143">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="4f344-144">성공적으로 실행되면 클라이언트의 트랜잭션 범위가 완료되고 해당 범위 내에서 수행된 모든 작업이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-144">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="4f344-145">특히 표시된 레코드 다섯 개는 서비스의 데이터베이스에 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-145">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="4f344-146">이러한 레코드 중 처음 두 개는 클라이언트의 트랜잭션 범위 내에서 발생한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-146">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="4f344-147">클라이언트의 `TransactionScope`내 임의 지점에서 예외가 발생하면 트랜잭션이 완료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-147">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="4f344-148">따라서 레코드는 데이터베이스로 커밋되지 않고 해당 범위 내에서 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-148">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="4f344-149">이 효과는 호출을 주석으로 처리하여 외부 `TransactionScope`를 완료한 후 샘플 실행을 반복하여 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-149">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="4f344-150">이러한 실행에서는 클라이언트 트랜잭션의 흐름이 마지막 세 연산으로 지정되지 않기 때문에 해당 연산(두 번째 `Subtract`, `Multiply` 및 `Divide` 요청)만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-150">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f344-151">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="4f344-151">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4f344-152">C # 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md) 의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="4f344-152">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="4f344-153">SQL Server Express Edition 또는 SQL Server를 설치했고 연결 문자열이 서비스의 애플리케이션 구성 파일에서 올바르게 설정되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-153">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="4f344-154">데이터베이스를 사용하지 않고 샘플을 실행하려면 서비스의 애플리케이션 구성 파일에서 `usingSql` 값을 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-154">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="4f344-155">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="4f344-155">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4f344-156">다중 컴퓨터 구성의 경우 아래의 지침을 사용하여 DTC(Distributed Transaction Coordinator)를 사용하도록 설정하고 Windows SDK에서 WsatConfig.exe 도구를 사용하여 WCF 트랜잭션 네트워크 지원을 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-156">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="4f344-157">WsatConfig.exe 설정에 대 한 자세한 내용은 [WS-Atomic 트랜잭션 지원 구성](../feature-details/configuring-ws-atomic-transaction-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4f344-157">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="4f344-158">샘플을 동일한 컴퓨터에서 실행 하 든 다른 컴퓨터에서 실행 하 든, 네트워크 트랜잭션 흐름을 사용 하도록 MSDTC (Microsoft DTC(Distributed Transaction Coordinator))를 구성 하 고 WsatConfig.exe 도구를 사용 하 여 WCF 트랜잭션 네트워크 지원을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-158">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="4f344-159">샘플을 실행할 수 있도록 MSDTC(Microsoft Distributed Transaction Coordinator)를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="4f344-159">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="4f344-160">Windows Server 2003 또는 Windows XP를 실행하는 서비스 컴퓨터에서 다음 지침에 따라 들어오는 네트워크 트랜잭션을 허용하도록 MSDTC를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-160">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="4f344-161">**시작** 메뉴에서 **제어판**, **관리 도구**, **구성 요소 서비스** 로 차례로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-161">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4f344-162">**구성 요소 서비스** 를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-162">Expand **Component Services**.</span></span> <span data-ttu-id="4f344-163">**컴퓨터** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-163">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="4f344-164">**내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-164">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="4f344-165">**MSDTC** 탭에서 **보안 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-165">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="4f344-166">**네트워크 DTC 액세스** 를 확인 하 고 **인바운드를 허용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-166">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="4f344-167">**확인** 을 클릭 한 다음 **예** 를 클릭 하 여 MSDTC 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-167">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="4f344-168">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-168">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="4f344-169">Windows Server 2008 또는 Windows Vista를 실행하는 서비스 컴퓨터에서 다음 지침에 따라 들어오는 네트워크 트랜잭션을 허용하도록 MSDTC를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-169">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="4f344-170">**시작** 메뉴에서 **제어판**, **관리 도구**, **구성 요소 서비스** 로 차례로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4f344-171">**구성 요소 서비스** 를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-171">Expand **Component Services**.</span></span> <span data-ttu-id="4f344-172">**컴퓨터** 폴더를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-172">Open the **Computers** folder.</span></span> <span data-ttu-id="4f344-173">**DTC(Distributed Transaction Coordinator)** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-173">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="4f344-174">**DTC 코디네이터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-174">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="4f344-175">**보안** 탭에서 **네트워크 DTC 액세스** 및 **인바운드 허용** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-175">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="4f344-176">**확인** 을 클릭 한 다음 **예** 를 클릭 하 여 MSDTC 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-176">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="4f344-177">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-177">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="4f344-178">클라이언트 컴퓨터에서 나가는 네트워크 트랜잭션을 허용하도록 MSDTC를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-178">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="4f344-179">**시작** 메뉴에서로 이동한 `Control Panel` 다음 **관리 도구**, **구성 요소 서비스** 를 차례로 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-179">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="4f344-180">**내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-180">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="4f344-181">**MSDTC** 탭에서 **보안 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-181">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="4f344-182">**네트워크 DTC 액세스** 를 확인 하 고 **아웃 바운드를 허용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-182">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="4f344-183">**확인** 을 클릭 한 다음 **예** 를 클릭 하 여 MSDTC 서비스를 다시 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-183">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="4f344-184">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-184">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f344-185">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-185">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f344-186">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="4f344-186">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4f344-187">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-187">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f344-188">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f344-188">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
