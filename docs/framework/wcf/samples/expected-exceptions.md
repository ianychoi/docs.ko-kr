---
description: '자세한 정보: 예상 되는 예외'
title: 예상되는 예외
ms.date: 03/30/2017
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
ms.openlocfilehash: 9ccb857da76143a37ed520f2fac8c515b332a565
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752407"
---
# <a name="expected-exceptions"></a><span data-ttu-id="af34f-103">예상되는 예외</span><span class="sxs-lookup"><span data-stu-id="af34f-103">Expected Exceptions</span></span>

<span data-ttu-id="af34f-104">이 샘플에서는 형식화된 클라이언트를 사용할 때 예상되는 예외를 catch하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-104">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="af34f-105">이 샘플은 계산기 서비스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-105">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="af34f-106">이 샘플에서 클라이언트는 콘솔 애플리케이션(.exe)이고 서비스는 IIS(인터넷 정보 서비스)를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-106">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="af34f-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="af34f-108">이 샘플에서는 올바른 프로그램에서 처리해야 하는 두 가지 예상되는 예외 형식 `TimeoutException` 및 `CommunicationException`을 catch하고 처리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-108">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="af34f-109">WCF (Windows Communication Foundation) 클라이언트의 통신 메서드에서 throw 되는 예외는 예상 된 예외 이거나 예기치 않은 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-109">Exceptions that are thrown from communication methods on a Windows Communication Foundation (WCF) client are either expected or unexpected.</span></span> <span data-ttu-id="af34f-110">예기치 않은 예외에는 `OutOfMemoryException`과 같은 치명적인 실패와 `ArgumentNullException` 또는 `InvalidOperationException` 등의 프로그래밍 오류가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-110">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="af34f-111">일반적으로 예기치 않은 오류를 처리 하는 데 유용한 방법이 없으므로 WCF 클라이언트 통신 메서드를 호출할 때 일반적으로 catch 하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-111">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a WCF client communication method.</span></span>  
  
 <span data-ttu-id="af34f-112">WCF 클라이언트의 통신 메서드에서 예상 되는 예외에는 `TimeoutException` , `CommunicationException` 및의 파생 클래스가 포함 됩니다 `CommunicationException` .</span><span class="sxs-lookup"><span data-stu-id="af34f-112">Expected exceptions from communication methods on a WCF client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="af34f-113">이러한 오류는 WCF 클라이언트를 중단 하 고 통신 오류를 보고 하 여 안전 하 게 처리할 수 있는 통신 중에 발생 하는 문제를 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-113">These indicate a problem during communication that can be safely handled by aborting the WCF client and reporting a communication failure.</span></span> <span data-ttu-id="af34f-114">어느 애플리케이션에서나 외부 요소에 의해 이런 오류가 발생할 수 있기 때문에 올바른 애플리케이션에서는 이런 예외를 catch할 수 있어야 하며, 이런 예외가 발생한 경우 복구할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-114">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="af34f-115">클라이언트에서 throw할 수 있는 `CommunicationException`의 파생 클래스가 몇 가지 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-115">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="af34f-116">경우에 따라 애플리케이션에서 이 중 일부를 catch하여 특수 처리를 수행하고, 나머지는 `CommunicationException`으로 처리할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-116">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="af34f-117">보다 한정된 예외 형식을 먼저 catch한 다음 이후의 catch 절에서 `CommunicationException`을 catch하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-117">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="af34f-118">클라이언트 통신 메서드를 호출하는 코드는 `TimeoutException` 및 `CommunicationException`을 캐치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-118">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="af34f-119">그런 오류를 처리하는 방법 중 하나는 클라이언트를 중단하고 통신 오류를 보고하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-119">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```csharp
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="af34f-120">예상된 예외가 발생한 경우 이후에 클라이언트를 사용할 수 있거나 사용하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-120">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="af34f-121">클라이언트를 여전히 사용할 수 있는지 확인하려면 `State` 속성이 `CommunicationState`.Opened인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-121">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="af34f-122">아직 열려 있다면 여전히 사용 가능한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-122">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="af34f-123">그렇지 않다면 클라이언트를 중단하고 이에 대한 참조를 모두 해제해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-123">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="af34f-124">예외가 발생한 후에 세션이 있는 클라이언트를 더 이상 사용하지 못하게 되는 경우가 많으며, 세션이 없는 클라이언트는 예외가 발생한 후에도 계속 사용 가능한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-124">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="af34f-125">하지만 항상 적용되는 사항은 아니기 때문에 예외가 발생한 후에도 클라이언트를 계속 사용해 보려면 `State` 속성을 확인하여 클라이언트가 아직 열려 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-125">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="af34f-126">샘플을 실행하면 작업 응답 및 예외가 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-126">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="af34f-127">클라이언트 프로세스에서는 두 개의 시나리오를 실행하며, 각 시나리오에서는 `Add` 뒤에 `Divide`를 호출하려 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-127">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="af34f-128">첫 번째 시나리오에서는 `Divide`에 대한 호출을 수행하기 전에 클라이언트를 중단하여 네트워크 문제를 시뮬레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-128">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="af34f-129">두 번째 시나리오에서는 시간 제한을 메서드가 완료되기에 충분하지 않은 짧은 값으로 설정하여 시간 초과 조건을 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-129">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="af34f-130">클라이언트 프로세스로부터의 예상 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-130">The expected output from the client process is:</span></span>  
  
```output
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af34f-131">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="af34f-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="af34f-132">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="af34f-133">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="af34f-134">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="af34f-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="af34f-135">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af34f-136">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="af34f-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="af34f-137">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af34f-138">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af34f-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
