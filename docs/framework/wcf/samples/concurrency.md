---
description: '자세히 알아보기: 동시성'
title: 동시성
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
ms.openlocfilehash: 2fbb6f9fc5ee2807ed0ca0592c364f048d5d8b14
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99778544"
---
# <a name="concurrency"></a><span data-ttu-id="e12f7-103">동시성</span><span class="sxs-lookup"><span data-stu-id="e12f7-103">Concurrency</span></span>

<span data-ttu-id="e12f7-104">Concurrency 샘플에서는 <xref:System.ServiceModel.ServiceBehaviorAttribute> 열거와 함께 <xref:System.ServiceModel.ConcurrencyMode>를 사용하여 서비스 인스턴스가 메시지를 순차적으로 처리하는지, 동시에 처리하는지를 제어하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-104">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e12f7-105">이 샘플은 서비스 계약을 구현 하는 [시작](getting-started-sample.md)을 기반으로 합니다 `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="e12f7-105">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e12f7-106">이 샘플에서는 `ICalculatorConcurrency`에서 상속되는 새 계약 `ICalculator`를 정의하여 서비스 동시성의 상태를 검사하는 두 가지 추가 작업을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-106">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="e12f7-107">동시성 설정을 변경하여 클라이언트를 실행하면 동작의 변화를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-107">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="e12f7-108">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-108">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e12f7-109">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e12f7-110">다음과 같은 세 가지 동시성 모드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-110">There are three concurrency modes available:</span></span>  
  
- <span data-ttu-id="e12f7-111">`Single`: 각 서비스 인스턴스에서 한 번에 하나의 메시지를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-111">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="e12f7-112">이 모드가 기본 동시성 모드입니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-112">This is the default concurrency mode.</span></span>  
  
- <span data-ttu-id="e12f7-113">`Multiple`: 각 서비스 인스턴스에서 동시에 여러 메시지를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-113">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="e12f7-114">이 동시성 모드를 사용하려면 스레드로부터 안전하게 서비스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-114">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
- <span data-ttu-id="e12f7-115">`Reentrant`: 각 서비스 인스턴스에서 한 번에 하나의 메시지를 처리하지만 재진입 호출을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-115">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="e12f7-116">서비스는 호출 될 때만 이러한 호출을 허용 합니다. 재진입은 [ConcurrencyMode](concurrencymode-reentrant.md) 샘플에서 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-116">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="e12f7-117">동시성 사용은 인스턴스 만들기 모드와 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-117">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="e12f7-118"><xref:System.ServiceModel.InstanceContextMode.PerCall> 인스턴스 만들기에서는 각 메시지가 새 서비스 인스턴스에 의해 처리되므로 동시성이 관련되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-118">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="e12f7-119"><xref:System.ServiceModel.InstanceContextMode.Single> 인스턴스 만들기에서는 단일 인스턴스에서 메시지를 순차적으로 처리하는지, 동시에 처리하는지에 따라 <xref:System.ServiceModel.ConcurrencyMode.Single> 또는 <xref:System.ServiceModel.ConcurrencyMode.Multiple> 동시성이 관련됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-119">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="e12f7-120"><xref:System.ServiceModel.InstanceContextMode.PerSession> 인스턴스 만들기에서는 모든 동시성 모드가 관련될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-120">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="e12f7-121">서비스 클래스에서는 다음 코드 샘플과 같이 `[ServiceBehavior(ConcurrencyMode=<setting>)]` 특성을 사용하여 동시성 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-121">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="e12f7-122">주석으로 처리할 줄을 변경하면 `Single` 및 `Multiple` 동시성 모드를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-122">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="e12f7-123">동시성 모드를 변경한 후에는 서비스를 다시 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-123">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```csharp
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="e12f7-124">기본적으로 이 샘플에서는 <xref:System.ServiceModel.ConcurrencyMode.Multiple> 인스턴스 만들기에 <xref:System.ServiceModel.InstanceContextMode.Single> 동시성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-124">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="e12f7-125">비동기 프록시를 사용하도록 클라이언트 코드가 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-125">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="e12f7-126">따라서 클라이언트는 각 호출 사이에서 응답을 기다리지 않고 서비스를 여러 번 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-126">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="e12f7-127">서비스 동시성 모드 동작의 차이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-127">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="e12f7-128">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e12f7-129">서비스가 실행되는 동시성 모드가 표시되고 각 작업이 호출된 다음 작업 카운트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-129">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="e12f7-130">동시성 모드가 `Multiple`이면 서비스에서 여러 메시지를 동시에 처리하므로 메시지가 호출된 방식과 다른 순서로 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-130">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="e12f7-131">동시성 모드를 `Single`로 변경하면 서비스에서 각 메시지를 순차적으로 처리하므로 메시지가 호출된 순서대로 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-131">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="e12f7-132">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e12f7-133">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="e12f7-133">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e12f7-134">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e12f7-135">Svcutil.exe를 사용 하 여 프록시 클라이언트를 생성 하는 경우 옵션을 포함 해야 `/async` 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-135">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3. <span data-ttu-id="e12f7-136">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="e12f7-137">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e12f7-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e12f7-138">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e12f7-139">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e12f7-139">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e12f7-140">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e12f7-141">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e12f7-141">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
