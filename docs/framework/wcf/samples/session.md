---
description: '자세한 정보: 세션'
title: 세션
ms.date: 03/30/2017
helpviewer_keywords:
- Sessions
ms.assetid: 36e1db50-008c-4b32-8d09-b56e790b8417
ms.openlocfilehash: ba8d2d44d0be22243bd1562f9bd499d68a1112af
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793027"
---
# <a name="session"></a><span data-ttu-id="26f91-103">세션</span><span class="sxs-lookup"><span data-stu-id="26f91-103">Session</span></span>

<span data-ttu-id="26f91-104">Session 샘플에서는 세션이 필요한 계약을 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-104">The Session sample demonstrates how to implement a contract that requires a session.</span></span> <span data-ttu-id="26f91-105">세션에서는 여러 작업을 수행하기 위한 컨텍스트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-105">A session provides context for performing multiple operations.</span></span> <span data-ttu-id="26f91-106">그러면 서비스에서 상태를 특정 세션에 연결하여 이후의 작업에서 이전 작업의 상태를 사용할 수 있게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-106">This allows a service to associate state with a given session, such that subsequent operations can use the state of a previous operation.</span></span> <span data-ttu-id="26f91-107">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md)을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-107">This sample is based on the [Getting Started](getting-started-sample.md), which implements a calculator service.</span></span> <span data-ttu-id="26f91-108">`ICalculator` 계약은 실행 결과를 유지하면서 일련의 산술 작업을 수행할 수 있도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-108">The `ICalculator` contract has been modified to allow a set of arithmetic operations to be performed, while keeping a running result.</span></span> <span data-ttu-id="26f91-109">이 기능은 `ICalculatorSession` 계약에 의해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-109">This functionality is defined by the `ICalculatorSession` contract.</span></span> <span data-ttu-id="26f91-110">서비스에서는 계산 수행을 위해 여러 서비스 작업이 호출되는 동안 클라이언트의 상태를 유지 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-110">The service maintains the state for a client as multiple service operations are called to perform a calculation.</span></span> <span data-ttu-id="26f91-111">클라이언트에서는 `Result()`를 호출하여 현재 결과를 검색하고 `Clear()`를 호출하여 결과를 0으로 지울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-111">The client can retrieve the current result by calling `Result()` and clear the result to zero by calling `Clear()`.</span></span>  
  
 <span data-ttu-id="26f91-112">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-112">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26f91-113">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="26f91-114">계약의 <xref:System.ServiceModel.SessionMode>를 `Required`로 설정하면 특정 바인딩을 통해 계약이 노출된 경우에 바인딩에서 세션이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-114">Setting the <xref:System.ServiceModel.SessionMode> of the contract to `Required` ensures that when the contract is exposed over a particular binding, the binding supports sessions.</span></span> <span data-ttu-id="26f91-115">바인딩에서 세션을 지원하지 않으면 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-115">If the binding does not support sessions an exception is thrown.</span></span> <span data-ttu-id="26f91-116">`ICalculatorSession` 인터페이스는 다음 샘플 코드에 표시된 것과 같이 실행 결과를 수정하는 하나 이상의 작업을 호출할 수 있도록 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-116">The `ICalculatorSession` interface is defined such that one or more operations can be called, which modifies a running result, as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface ICalculatorSession  
{  
    [OperationContract(IsOneWay=true)]  
    void Clear();  
    [OperationContract(IsOneWay = true)]  
    void AddTo(double n);  
    [OperationContract(IsOneWay = true)]  
    void SubtractFrom(double n);  
    [OperationContract(IsOneWay = true)]  
    void MultiplyBy(double n);  
    [OperationContract(IsOneWay = true)]  
    void DivideBy(double n);  
    [OperationContract]  
    double Result();  
}  
```  
  
 <span data-ttu-id="26f91-117">서비스에서는 <xref:System.ServiceModel.InstanceContextMode>의 <xref:System.ServiceModel.InstanceContextMode.PerSession>를 사용하여 특정 서비스 인스턴스 컨텍스트를 들어오는 각 세션에 바인드합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-117">The service uses a <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession> to bind a given service instance context to each incoming session.</span></span> <span data-ttu-id="26f91-118">그러면 서비스에서 각 세션의 결과를 로컬 멤버 변수에서 유지 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-118">This allows the service to maintain the running result for each session in a local member variable.</span></span>  
  
```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class CalculatorService : ICalculatorSession  
{  
    double result = 0.0D;  
  
    public void Clear()  
    {  result = 0.0D; }  
  
    public void AddTo(double n)  
    {  result += n;   }  
  
    public void SubtractFrom(double n)  
    {  result -= n;   }  
  
    public void MultiplyBy(double n)  
    {  result *= n;   }  
  
    public void DivideBy(double n)  
    {  result /= n;   }  
  
    public double Result()  
    {  return result; }  
}  
```  
  
 <span data-ttu-id="26f91-119">샘플을 실행하면 클라이언트에서 서버에 대한 몇 개의 요청을 수행하고 결과를 요청하며, 그러면 결과가 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-119">When you run the sample, the client makes several requests to the server and requests the result, which it then displays in the client console window.</span></span> <span data-ttu-id="26f91-120">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-120">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
(((0 + 100) - 50) * 17.65) / 2 = 441.25  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="26f91-121">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="26f91-121">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="26f91-122">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="26f91-123">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="26f91-124">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="26f91-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="26f91-125">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="26f91-126">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="26f91-126">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="26f91-127">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="26f91-128">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26f91-128">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Session`  
