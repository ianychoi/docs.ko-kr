---
description: '자세한 정보: 서비스 트랜잭션 동작'
title: 서비스 트랜잭션 동작
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 1f8b76de250ef87ec5ca2d4ea4353a9a28bac248
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793066"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="8b032-103">서비스 트랜잭션 동작</span><span class="sxs-lookup"><span data-stu-id="8b032-103">Service Transaction Behavior</span></span>

<span data-ttu-id="8b032-104">이 샘플에서는 클라이언트에서 조정하는 트랜잭션과 ServiceBehaviorAttribute 및 OperationBehaviorAttribute의 설정을 사용하여 서비스 트랜잭션 동작을 제어하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-104">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="8b032-105">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 하지만, 수행 된 작업의 서버 로그를 데이터베이스 테이블에 유지 관리 하 고 계산기 작업의 상태 저장 누계를 유지 관리 하도록 확장 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="8b032-106">서버 로그 테이블에 대한 지속적인 쓰기는 클라이언트에서 조정하는 트랜잭션의 결과에 영향을 받습니다. 즉, 클라이언트 트랜잭션이 완료되지 않은 경우 웹 서비스 트랜잭션은 데이터베이스의 업데이트가 커밋되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-106">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="8b032-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="8b032-108">다음 서비스 계약에서는 모든 작업을 수행하려면 트랜잭션이 요청과 함께 이동해야 한다고 정의하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-108">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",
                    SessionMode = SessionMode.Required)]
public interface ICalculator
{
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Add(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Subtract(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Multiply(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Divide(double n);
}
```

<span data-ttu-id="8b032-109">들어오는 트랜잭션 흐름을 사용하도록 설정하기 위해 서비스는 transactionFlow 특성이 `true`로 설정된 시스템 제공 wsHttpBinding으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-109">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="8b032-110">이 바인딩은 상호 운용 가능한 WSAtomicTransactionOctober2004 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-110">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="8b032-111">서비스와 트랜잭션에 대한 연결을 모두 시작한 후에 클라이언트는 이 트랜잭션 범위 내의 몇몇 서비스 작업에 액세스한 다음 트랜잭션을 완료하고 연결을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-111">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
// Create a client
CalculatorClient client = new CalculatorClient();

// Create a transaction scope with the default isolation level of Serializable
using (TransactionScope tx = new TransactionScope())
{
    Console.WriteLine("Starting transaction");

    // Call the Add service operation.
    double value = 100.00D;
    Console.WriteLine("  Adding {0}, running total={1}",
                                        value, client.Add(value));

    // Call the Subtract service operation.
    value = 45.00D;
    Console.WriteLine("  Subtracting {0}, running total={1}",
                                        value, client.Subtract(value));

    // Call the Multiply service operation.
    value = 9.00D;
    Console.WriteLine("  Multiplying by {0}, running total={1}",
                                        value, client.Multiply(value));

    // Call the Divide service operation.
    value = 15.00D;
    Console.WriteLine("  Dividing by {0}, running total={1}",
                                        value, client.Divide(value));

    Console.WriteLine("  Completing transaction");
    tx.Complete();
}

Console.WriteLine("Transaction committed");

// Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

<span data-ttu-id="8b032-112">서비스에는 서비스 트랜잭션 동작에 영향을 주는 세 가지 특성이 있으며 영향을 주는 방식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-112">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="8b032-113">`ServiceBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="8b032-113">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="8b032-114">`TransactionTimeout` 속성은 트랜잭션을 완료해야 하는 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-114">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="8b032-115">이 샘플에서는 30초로 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-115">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="8b032-116">`TransactionIsolationLevel` 속성은 서비스가 지원하는 격리 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-116">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="8b032-117">이 속성은 클라이언트의 격리 수준을 일치시키는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-117">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="8b032-118">`ReleaseServiceInstanceOnTransactionComplete` 속성은 트랜잭션이 완료될 때 서비스 인스턴스를 재활용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-118">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="8b032-119">이 속성을 `false`로 설정하면 서비스는 전체 작업 요청에 대해 동일한 서비스 인스턴스를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-119">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="8b032-120">이 설정은 누계를 유지 관리하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-120">This is required to maintain the running total.</span></span> <span data-ttu-id="8b032-121">이 속성을 `true`로 설정하면 각 작업이 완료된 후에 새 인스턴스가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-121">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="8b032-122">`TransactionAutoCompleteOnSessionClose` 속성에서는 세션을 닫을 때 처리되지 않은 트랜잭션을 완료할 것인지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-122">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="8b032-123">이 속성을로 설정 하면 속성을로 `false` 설정 <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> `true` 하거나 명시적으로 메서드를 호출 하 여 트랜잭션을 완료 해야 하는 개별 작업이 필요 합니다 <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8b032-123">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="8b032-124">이 샘플에서는 두 가지 접근 방식을 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-124">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="8b032-125">`ServiceContractAttribute`:</span><span class="sxs-lookup"><span data-stu-id="8b032-125">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="8b032-126">`SessionMode` 속성은 서비스가 적절한 요청을 논리 세션에 상호 연결시킬지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-126">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="8b032-127">이 서비스에는 OperationBehaviorAttribute TransactionAutoComplete 속성이 `false`로 설정된 작업(Multiply 및 Divide)이 포함되기 때문에 `SessionMode.Required`를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-127">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="8b032-128">예를 들어 Multiply 작업은 트랜잭션을 완료하는 대신 `SetTransactionComplete` 메서드를 사용하여 완료할 Divide에 대한 이후의 호출에 의존합니다. 서비스는 이러한 작업이 동일한 세션 내에서 발생하는지 확인할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-128">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="8b032-129">`OperationBehaviorAttribute`:</span><span class="sxs-lookup"><span data-stu-id="8b032-129">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="8b032-130">`TransactionScopeRequired` 속성은 작업의 동작이 트랜잭션 범위 내에서 실행되어야 하는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-130">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="8b032-131">이 속성은 이 샘플의 모든 작업에 대해 `true`로 설정되며, 클라이언트는 해당 트랜잭션을 모든 작업으로 이동하므로 동작은 해당 클라이언트 트랜잭션의 범위 내에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-131">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="8b032-132">`TransactionAutoComplete` 속성은 처리되지 않은 예외가 발생하지 않는 경우 메서드가 실행되는 트랜잭션을 자동으로 완료할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-132">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="8b032-133">이전에 설명한 대로 이 속성은 Add 및 Subtract 작업에 대해 `true`로 설정되지만 Multiply 및 Divide 작업에 대해서는 `false`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-133">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="8b032-134">Add 및 Subtract 작업은 자동으로 동작을 완료하고, Divide는 `SetTransactionComplete` 메서드에 대한 명시적 호출을 통해 동작을 완료하며, Multiply는 동작을 완료하는 대신 Divide와 같은 이후의 호출에 의존하고 요청하여 동작을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-134">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="8b032-135">특성을 사용하는 서비스 구현은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-135">The attributed service implementation is as follows:</span></span>

```csharp
[ServiceBehavior(
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,
    TransactionTimeout = "00:00:30",
    ReleaseServiceInstanceOnTransactionComplete = false,
    TransactionAutoCompleteOnSessionClose = false)]
public class CalculatorService : ICalculator
{
    double runningTotal;

    public CalculatorService()
    {
        Console.WriteLine("Creating new service instance...");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Add(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));
        runningTotal = runningTotal + n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Subtract(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));
        runningTotal = runningTotal - n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Multiply(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));
        runningTotal = runningTotal * n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Divide(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));
        runningTotal = runningTotal / n;
        OperationContext.Current.SetTransactionComplete();
        return runningTotal;
    }

    // Logging method omitted for brevity
}
```

<span data-ttu-id="8b032-136">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-136">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="8b032-137">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-137">Press ENTER in the client window to shut down the client.</span></span>

```console
Starting transaction
Performing calculations...
  Adding 100, running total=100
  Subtracting 45, running total=55
  Multiplying by 9, running total=495
  Dividing by 15, running total=33
  Completing transaction
Transaction committed
Press <ENTER> to terminate client.
```

<span data-ttu-id="8b032-138">서비스 작업 요청의 로깅은 서비스의 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-138">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="8b032-139">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-139">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="8b032-140">서비스는 계산의 누계를 유지하는 것 외에도 인스턴스 만들기를 보고하고(이 샘플의 경우 인스턴스 하나) 작업 요청을 데이터베이스에 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-140">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="8b032-141">모든 요청이 클라이언트의 트랜잭션으로 이동하기 때문에 트랜잭션을 완료하지 못하면 모든 데이터베이스 작업이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-141">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="8b032-142">이에 대해서는 다음과 같은 여러 가지 방법을 통해 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-142">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="8b032-143">`tx.Complete`()에 대한 클라이언트의 호출을 주석으로 처리하고 다시 실행 - 그러면 클라이언트가 트랜잭션을 완료하지 않고 트랜잭션 범위를 끝냅니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-143">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="8b032-144">Divide 서비스 작업에 대한 호출을 주석으로 처리 - 그러면 Multiply 작업에서 시작된 작업이 완료되지 못하고 결과적으로 클라이언트의 트랜잭션도 완료되지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-144">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="8b032-145">클라이언트의 트랜잭션 범위 내 임의의 위치에서 처리되지 않은 예외 throw - 마찬가지로 클라이언트가 트랜잭션을 완료하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-145">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="8b032-146">이 중 어느 방법을 사용해도 해당 범위 내에서 수행된 작업이 커밋되지 않으며 데이터베이스와 연결된 행 수가 증가하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-146">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="8b032-147">빌드 프로세스의 일부로 데이터베이스 파일이 bin 폴더에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-147">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="8b032-148">데이터베이스 파일의 이 복사본을 확인하여 Visual Studio 프로젝트에 포함된 파일이 아닌 로그와 관련된 행을 살펴보아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-148">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b032-149">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="8b032-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="8b032-150">SQL Server 2005 Express Edition 또는 SQL Server 2005를 설치했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-150">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="8b032-151">서비스의 App.config 파일에서 데이터베이스 `connectionString` 을 설정하거나 appSettings `usingSql` 값을 `false`로 설정하여 데이터베이스 상호 작용을 비활성화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-151">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="8b032-152">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-152">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="8b032-153">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="8b032-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="8b032-154">여러 컴퓨터에서 샘플을 실행 하는 경우 네트워크 트랜잭션 흐름을 사용 하도록 MSDTC (Microsoft DTC(Distributed Transaction Coordinator))를 구성 하 고 WsatConfig.exe 도구를 사용 하 여 WCF (Windows Communication Foundation) 트랜잭션 네트워크 지원을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-154">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="8b032-155">여러 컴퓨터에서 샘플을 실행할 수 있도록 MSDTC(Microsoft Distributed Transaction Coordinator)를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="8b032-155">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="8b032-156">서비스 컴퓨터에서 들어오는 네트워크 트랜잭션을 허용하도록 MSDTC를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-156">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="8b032-157">**시작** 메뉴에서 **제어판**, **관리 도구**, **구성 요소 서비스** 로 차례로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-157">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="8b032-158">**내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-158">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="8b032-159">**MSDTC** 탭에서 **보안 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-159">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="8b032-160">**네트워크 DTC 액세스** 를 확인 하 고 **인바운드를 허용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-160">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="8b032-161">**예** 를 클릭 하 여 MS DTC 서비스를 다시 시작한 다음 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-161">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="8b032-162">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-162">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="8b032-163">서비스 컴퓨터와 클라이언트 컴퓨터에서 예외 애플리케이션 목록에 Microsoft Distributed Transaction Coordinator(MSDTC)가 포함되도록 Windows 방화벽을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-163">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="8b032-164">제어판에서 Windows 방화벽 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-164">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="8b032-165">**예외** 탭에서 **프로그램 추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-165">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="8b032-166">C:\WINDOWS\System32 폴더로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-166">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="8b032-167">Msdtc.exe를 선택 하 고 **열기** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-167">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="8b032-168">**확인** 을 클릭 하 여 **프로그램 추가** 대화 상자를 닫고 **확인** 을 다시 클릭 하 여 Windows 방화벽 애플릿을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-168">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="8b032-169">클라이언트 컴퓨터에서 나가는 네트워크 트랜잭션을 허용하도록 MSDTC를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-169">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="8b032-170">**시작** 메뉴에서 **제어판**, **관리 도구**, **구성 요소 서비스** 로 차례로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-170">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="8b032-171">**내 컴퓨터** 를 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-171">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="8b032-172">**MSDTC** 탭에서 **보안 구성** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-172">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="8b032-173">**네트워크 DTC 액세스** 를 확인 하 고 **아웃 바운드를 허용** 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-173">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="8b032-174">**예** 를 클릭 하 여 MS DTC 서비스를 다시 시작한 다음 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-174">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="8b032-175">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-175">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b032-176">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b032-177">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="8b032-177">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="8b032-178">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b032-179">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b032-179">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
