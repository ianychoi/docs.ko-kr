---
description: '자세한 정보: 오류 계약'
title: 오류 계약
ms.date: 03/30/2017
ms.assetid: b31b140e-dc3b-408b-b3c7-10b6fe769725
ms.openlocfilehash: b7f6a30ff076eb56ebb0894c440fbc7937761410
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752355"
---
# <a name="fault-contract"></a><span data-ttu-id="e27cc-103">오류 계약</span><span class="sxs-lookup"><span data-stu-id="e27cc-103">Fault Contract</span></span>

<span data-ttu-id="e27cc-104">Fault Contract 샘플은 오류 정보를 서비스에서 클라이언트로 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-104">The Fault Contract sample demonstrates how to communicate error information from a service to a client.</span></span> <span data-ttu-id="e27cc-105">이 샘플은 [시작](getting-started-sample.md)을 기반으로 하며 내부 예외를 오류로 변환 하기 위해 몇 가지 추가 코드를 서비스에 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-105">The sample is based on the [Getting Started](getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="e27cc-106">클라이언트는 서비스에서 오류 조건을 강제하기 위해 0으로 나누기를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-106">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e27cc-107">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e27cc-108">다음 샘플 코드와 같이 계산기 계약은 <xref:System.ServiceModel.FaultContractAttribute>를 포함하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-108">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    [FaultContract(typeof(MathFault))]  
    int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="e27cc-109"><xref:System.ServiceModel.FaultContractAttribute> 특성은 `Divide` 작업이 `MathFault` 형식의 오류를 반환할 수 있다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-109">The <xref:System.ServiceModel.FaultContractAttribute> attribute indicates that the `Divide` operation may return a fault of type `MathFault`.</span></span> <span data-ttu-id="e27cc-110">오류는 serialize할 수 있는 모든 형식이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-110">A fault can be of any type that can be serialized.</span></span> <span data-ttu-id="e27cc-111">이 경우 `MathFault`는 다음과 같이 데이터 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-111">In this case, the `MathFault` is a data contract, as follows:</span></span>  
  
```csharp
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class MathFault  
{
    private string operation;  
    private string problemType;  
  
    [DataMember]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]
    public string ProblemType  
    {  
        get { return problemType; }  
        set { problemType = value; }  
    }  
}  
```  
  
 <span data-ttu-id="e27cc-112">다음 샘플 코드와 같이 0으로 나누기 예외가 발생할 경우 `Divide` 메서드는 <xref:System.ServiceModel.FaultException%601> 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-112">The `Divide` method throws a <xref:System.ServiceModel.FaultException%601> exception when a divide by zero exception occurs as shown in the following sample code.</span></span> <span data-ttu-id="e27cc-113">이 예외로 인해 오류가 클라이언트에게 보내집니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-113">This exception results in a fault being sent to the client.</span></span>  
  
```csharp
public int Divide(int n1, int n2)  
{  
    try  
    {  
        return n1 / n2;  
    }  
    catch (DivideByZeroException)  
    {  
        MathFault mf = new MathFault();  
        mf.operation = "division";  
        mf.problemType = "divide by zero";  
        throw new FaultException<MathFault>(mf);  
    }  
}  
```  
  
 <span data-ttu-id="e27cc-114">클라이언트 코드는 0으로 나누기를 요청하여 오류를 강제합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-114">The client code forces an error by requesting a division by zero.</span></span> <span data-ttu-id="e27cc-115">샘플을 실행하면 작업 요청 및 응답이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-115">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e27cc-116">0으로 나누기가 오류로 보고되는 것을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-116">You see the division by zero being reported as a fault.</span></span> <span data-ttu-id="e27cc-117">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
FaultException<MathFault>: Math fault while doing division. Problem: divide by zero  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="e27cc-118">클라이언트는 해당 `FaultException<MathFault>` 예외를 catch하여 이를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-118">The client does this by catching the appropriate `FaultException<MathFault>` exception:</span></span>  
  
```csharp
catch (FaultException<MathFault> e)  
{  
    Console.WriteLine("FaultException<MathFault>: Math fault while doing " + e.Detail.operation + ". Problem: " + e.Detail.problemType);  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="e27cc-119">서비스 구현의 세부 정보가 서비스의 보안 경계를 벗어나는 것을 방지하기 위해 기본적으로 예기치 않은 예외의 세부 정보는 클라이언트에게 보내지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-119">By default, the details of unexpected exceptions are not sent to the client to prevent details of the service implementation from escaping the secure boundary of the service.</span></span> <span data-ttu-id="e27cc-120">`FaultContract`는 계약의 오류를 설명하고 특정 형식의 예외를 클라이언트에게 전송하기 적합한 것으로 표시하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-120">`FaultContract` provides a way to describe faults in a contract and mark certain types of exceptions as appropriate for transmission to the client.</span></span> <span data-ttu-id="e27cc-121">`FaultException<T>`는 오류를 소비자에게 보내기 위한 런타임 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-121">`FaultException<T>` provides the run-time mechanism for sending faults to consumers.</span></span>  
  
 <span data-ttu-id="e27cc-122">그러나 디버깅 시에 서비스 오류의 내부 정보를 확인하는 것이 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-122">However, it is useful to see the internal details of a service failure when debugging.</span></span> <span data-ttu-id="e27cc-123">위에 설명된 보안 동작을 해제하려면 서버에서 처리되지 않은 모든 예외의 세부 정보를 클라이언트에게 보내는 오류에 포함해야 한다는 것을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-123">To turn off the secure behavior previously described, you can indicate that the details of every unhandled exception on the server should be included in the fault that is sent to the client.</span></span> <span data-ttu-id="e27cc-124">이렇게 하려면 <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A>를 `true`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-124">This is accomplished by setting <xref:System.ServiceModel.ServiceBehaviorAttribute.IncludeExceptionDetailInFaults%2A> to `true`.</span></span> <span data-ttu-id="e27cc-125">다음 샘플과 같이 구성이나 코드에서 이를 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-125">You can either set it in code, or in configuration as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="True" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="e27cc-126">또한 `behaviorConfiguration` 구성 파일에서 서비스의 특성을 "CalculatorServiceBehavior"로 설정 하 여 동작을 서비스와 연결 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-126">Further, the behavior must be associated with the service by setting the `behaviorConfiguration` attribute of the service in the configuration file to "CalculatorServiceBehavior".</span></span>  
  
 <span data-ttu-id="e27cc-127">클라이언트에서 이러한 오류를 catch하려면 제네릭이 아닌 <xref:System.ServiceModel.FaultException>을 catch해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-127">To catch such faults on the client, the non-generic <xref:System.ServiceModel.FaultException> must be caught.</span></span>  
  
 <span data-ttu-id="e27cc-128">이 동작은 디버깅 목적으로만 사용해야 하고 프로덕션 환경에서 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-128">This behavior should only be used for debugging purposes and should never be enabled in production.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e27cc-129">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="e27cc-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e27cc-130">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e27cc-131">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e27cc-132">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="e27cc-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e27cc-133">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e27cc-134">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="e27cc-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="e27cc-135">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e27cc-136">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e27cc-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Faults`  
