---
title: 기본 서비스 동작
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, defaults
- Default Service Behavior Sample [Windows Communication Foundation]
ms.assetid: 442d4f71-c64e-4c62-816a-a66c38e7d3ec
ms.openlocfilehash: acdb4652c0f49b610b8e7cad2aa5c0074fe00511
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292755"
---
# <a name="default-service-behavior"></a><span data-ttu-id="a12e8-102">기본 서비스 동작</span><span class="sxs-lookup"><span data-stu-id="a12e8-102">Default Service Behavior</span></span>

<span data-ttu-id="a12e8-103">이 샘플에서는 서비스 동작 설정을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-103">This sample demonstrates how service behavior settings can be configured.</span></span> <span data-ttu-id="a12e8-104">이 샘플은 서비스 계약을 구현 하는 [시작](getting-started-sample.md)을 기반으로 합니다 `ICalculator` .</span><span class="sxs-lookup"><span data-stu-id="a12e8-104">The sample is based on the [Getting Started](getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="a12e8-105">이 샘플에서는 <xref:System.ServiceModel.ServiceBehaviorAttribute> 및 <xref:System.ServiceModel.OperationBehaviorAttribute> 특성을 사용하여 서비스 동작 및 작업 동작을 명시적으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-105">This sample explicitly defines service behaviors and operation behaviors using the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes.</span></span> <span data-ttu-id="a12e8-106">동작은 구성 파일에서 구성할 수도 있고 코드에서 명령적으로 구성할 수도 있습니다. 이 샘플에서는 코드에서 명령적으로 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-106">You can configure behaviors in configuration files or imperatively in code (as this sample demonstrates).</span></span>  
  
 <span data-ttu-id="a12e8-107">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a12e8-108">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="a12e8-109">서비스 클래스에서는 다음 코드 샘플에 표시된 것과 같이 <xref:System.ServiceModel.ServiceBehaviorAttribute> 및 <xref:System.ServiceModel.OperationBehaviorAttribute>에 동작을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-109">The service class specifies behaviors with the <xref:System.ServiceModel.ServiceBehaviorAttribute> and the <xref:System.ServiceModel.OperationBehaviorAttribute> as shown in the following code sample.</span></span> <span data-ttu-id="a12e8-110">지정된 모든 값은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-110">All values specified are the defaults.</span></span>  
  
```csharp
[ServiceBehavior(  
    AutomaticSessionShutdown=true,  
    ConcurrencyMode=ConcurrencyMode.Single,  
    InstanceContextMode=InstanceContextMode.PerSession,  
    IncludeExceptionDetailInFaults=false,  
    UseSynchronizationContext=true,  
    ValidateMustUnderstand=true)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(  
        TransactionAutoComplete=true,  
        TransactionScopeRequired=false,  
        Impersonation=ImpersonationOption.NotAllowed)]  
    public double Add(double n1, double n2)  
    {  
        System.Threading.Thread.Sleep(1600);  
        return n1 + n2;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="a12e8-111">서비스 동작은 <xref:System.ServiceModel.ServiceBehaviorAttribute> 특성으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-111">Service behaviors are specified with the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a12e8-112">다음 표에서는 이러한 일부 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-112">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a12e8-113">서비스 동작</span><span class="sxs-lookup"><span data-stu-id="a12e8-113">Service behavior</span></span>|<span data-ttu-id="a12e8-114">Description</span><span class="sxs-lookup"><span data-stu-id="a12e8-114">Description</span></span>|  
|----------------------|-----------------|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.AutomaticSessionShutdown%2A>|<span data-ttu-id="a12e8-115">클라이언트 요청에 따라 세션을 자동으로 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-115">Automatically shuts down a session at the client's request.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>|<span data-ttu-id="a12e8-116">각 서비스 인스턴스의 동시성 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-116">Specifies the concurrency mode for each service instance.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>|<span data-ttu-id="a12e8-117">인스턴스 컨텍스트 모드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-117">Specifies the instance context mode.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.UseSynchronizationContext%2A>|<span data-ttu-id="a12e8-118">입력된 동기화 컨텍스트가 설정된 경우 사용 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-118">Determines whether to use the provided synchronization context, if one is set.</span></span> <span data-ttu-id="a12e8-119">Windows Forms 애플리케이션에서 `WindowsFormsSynchronizationContext`의 사용 여부를 제어하려는 경우에 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-119">Use this when you want to control whether to use a `WindowsFormsSynchronizationContext` in Windows Forms applications.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>|<span data-ttu-id="a12e8-120">처리되지 않은 일반적인 실행 예외를 `Fault<string>`로 변환하고 오류 메시지로 보내는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-120">Determines whether general unhandled execution exceptions are to be converted into a `Fault<string>` and sent as a fault message.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A>|<span data-ttu-id="a12e8-121">트랜잭션의 격리 수준을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-121">Specifies the isolation level for transactions.</span></span>|  
|<xref:System.ServiceModel.ServiceBehaviorAttribute.ValidateMustUnderstand%2A>|<span data-ttu-id="a12e8-122">예기치 않은 메시지 헤더가 오류 발생 조건이 되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-122">Determines whether unexpected message headers cause an error condition.</span></span>|  
  
 <span data-ttu-id="a12e8-123">작업 동작은 <xref:System.ServiceModel.OperationBehaviorAttribute> 특성을 사용하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-123">Operation behaviors are specified by using the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a12e8-124">다음 표에서는 이러한 일부 동작에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-124">The following table describes some of these behaviors.</span></span>  
  
|<span data-ttu-id="a12e8-125">작업 동작</span><span class="sxs-lookup"><span data-stu-id="a12e8-125">Operation Behavior</span></span>|<span data-ttu-id="a12e8-126">Description</span><span class="sxs-lookup"><span data-stu-id="a12e8-126">Description</span></span>|  
|------------------------|-----------------|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A>|<span data-ttu-id="a12e8-127">서비스 작업이 완료되면 현재 트랜잭션이 커밋되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-127">Determines whether service operation completion commits the current transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>|<span data-ttu-id="a12e8-128">서비스 작업이 클라이언트 흐름 트랜잭션에 참여하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-128">Determines whether the service operation enlists in a client-flowed transaction.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>|<span data-ttu-id="a12e8-129">서비스 작업에서 호출자의 ID를 가장하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-129">Determines whether the service operation impersonates the caller's identity.</span></span>|  
|<xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A>|<span data-ttu-id="a12e8-130">서비스 작업 호출을 시작하거나 끝낼 때 서비스 인스턴스가 재생되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-130">Determines whether service instances are recycled at the start or end of the service operation call.</span></span>|  
  
 <span data-ttu-id="a12e8-131">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-131">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a12e8-132">호출 사이의 지연은 서비스 작업에서 `System.Threading.Thread.Sleep()`에 대한 호출이 이루어진 결과로 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-132">The delay between the calls is the result of the calls to `System.Threading.Thread.Sleep()` made in the service operations.</span></span> <span data-ttu-id="a12e8-133">나머지 동작 샘플에서는 이런 동작에 대해 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-133">The rest of the behavior samples explain these behaviors in more detail.</span></span> <span data-ttu-id="a12e8-134">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-134">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a12e8-135">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="a12e8-135">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="a12e8-136">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-136">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="a12e8-137">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="a12e8-138">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="a12e8-138">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a12e8-139">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-139">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a12e8-140">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="a12e8-140">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a12e8-141">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a12e8-142">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a12e8-142">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Default`  
