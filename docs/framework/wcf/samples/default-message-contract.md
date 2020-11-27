---
title: 기본 메시지 계약
ms.date: 03/30/2017
helpviewer_keywords:
- Message Contract
ms.assetid: 5a200b78-1a46-4104-b7fb-da6dbab33893
ms.openlocfilehash: 0a70fb519f3b3e8d9ce109c3b7bef0313e22eb50
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292828"
---
# <a name="default-message-contract"></a><span data-ttu-id="01d0e-102">기본 메시지 계약</span><span class="sxs-lookup"><span data-stu-id="01d0e-102">Default Message Contract</span></span>

<span data-ttu-id="01d0e-103">Default Message Contract 샘플에서는 사용자 지정 사용자 정의 메시지를 서비스 작업에 전달하고 전달받는 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-103">The Default Message Contract sample demonstrates a service where a custom user-defined message is passed to and from service operations.</span></span> <span data-ttu-id="01d0e-104">이 샘플은 형식화 된 서비스로 계산기 인터페이스를 구현 하는 [시작](getting-started-sample.md) 을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator interface as a typed service.</span></span> <span data-ttu-id="01d0e-105">[시작](getting-started-sample.md)부분에서 사용 되는 더하기, 빼기, 곱하기 및 나누기에 대 한 개별 서비스 작업 대신이 샘플에서는 피연산자와 연산자를 모두 포함 하는 사용자 지정 메시지를 전달 하 고 산술 계산 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-105">Instead of the individual service operations for addition, subtraction, multiplication, and division used in the [Getting Started](getting-started-sample.md), this sample passes a custom message that contains both the operands and the operator, and returns the result of the arithmetic calculation.</span></span>  
  
 <span data-ttu-id="01d0e-106">클라이언트는 콘솔 프로그램(.exe)이고 서비스 라이브러리(.dll)는 IIS(인터넷 정보 서비스)에서 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-106">The client is a console program (.exe) and the service library (.dll) is hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="01d0e-107">콘솔 창에는 클라이언트 동작이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-107">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d0e-108">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="01d0e-109">서비스에서는 `MyMessage` 형식의 사용자 지정 메시지를 수락하고 반환하는 단일 서비스 작업이 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-109">In the service, a single service operation is defined that accepts and returns custom messages of type `MyMessage`.</span></span> <span data-ttu-id="01d0e-110">이 샘플에서는 요청 및 응답 메시지의 형식이 동일하지만 필요한 경우 서로 다른 메시지 계약이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-110">Although in this sample the request and response messages are of the same type, they could of course be different message contracts if necessary.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract(Action="http://test/MyMessage_action",  
                  ReplyAction="http://test/MyMessage_action")]  
    MyMessage Calculate(MyMessage request);  
}  
```  
  
 <span data-ttu-id="01d0e-111">사용자 지정 메시지 `MyMessage`는 <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> 및 <xref:System.ServiceModel.MessageBodyMemberAttribute> 특성과 함께 주석 처리된 클래스에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-111">The custom message `MyMessage` is defined in a class annotated with <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="01d0e-112">이 샘플에서는 세 번째 생성자만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-112">Only the third constructor is used in this sample.</span></span> <span data-ttu-id="01d0e-113">메시지 계약을 사용하면 SOAP 메시지를 완전히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-113">Using message contracts allows you to exercise full control over the SOAP message.</span></span> <span data-ttu-id="01d0e-114">이 샘플에서는 <xref:System.ServiceModel.MessageHeaderAttribute> 특성을 사용하여 SOAP 헤더에 `Operation`을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-114">In this sample, the <xref:System.ServiceModel.MessageHeaderAttribute> attribute is used to put `Operation` in a SOAP header.</span></span> <span data-ttu-id="01d0e-115">피연산자 `N1`, `N2` 및 `Result`에는 <xref:System.ServiceModel.MessageBodyMemberAttribute> 특성이 적용되어 있으므로 이러한 피연산자는 SOAP 본문 내에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-115">The operands `N1`, `N2` and the `Result` appear within the SOAP body because they have the <xref:System.ServiceModel.MessageBodyMemberAttribute> attribute applied.</span></span>  
  
```csharp
[MessageContract]  
public class MyMessage  
{  
    private string operation;  
    private double n1;  
    private double n2;  
    private double result;  
  
    //Constructor - create an empty message.  
  
    public MyMessage() {}  
  
    //Constructor - create a message and populate its members.  
  
    public MyMessage(double n1, double n2, string operation,
                     double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    //Constructor - create a message from another message.  
  
    public MyMessage(MyMessage message)  
    {  
        this.n1 = message.n1;  
        this.n2 = message.n2;  
        this.operation = message.operation;  
        this.result = message.result;  
    }  
  
    [MessageHeader]  
    public string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [MessageBodyMember]  
    public double N1  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [MessageBodyMember]  
    public double N2  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [MessageBodyMember]  
    public double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
}  
```  
  
 <span data-ttu-id="01d0e-116">구현 클래스에는 `Calculate` 서비스 작업의 코드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-116">The implementation class contains the code for the `Calculate` service operation.</span></span> <span data-ttu-id="01d0e-117">다음 샘플 코드에서와 같이 `CalculateService` 클래스는 요청 메시지로부터 피연산자와 연산자를 받고 요청된 계산의 결과가 포함된 응답 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-117">The `CalculateService` class obtains the operands and operator from the request message and creates a response message that contains the result of the requested calculation, as shown in the following sample code.</span></span>  
  
```csharp
// Service class which implements the service contract.  
public class CalculatorService : ICalculator  
{  
    // Perform a calculation.  
  
    public MyMessage Calculate(MyMessage request)  
    {  
        MyMessage response = new MyMessage(request);  
        switch (request.Operation)  
        {  
            case "+":  
                response.Result = request.N1 + request.N2;  
                break;  
            case "-":  
                response.Result = request.N1 - request.N2;  
                break;  
            case "*":  
                response.Result = request.N1 * request.N2;  
                break;  
            case "/":  
                response.Result = request.N1 / request.N2;  
                break;  
            default:  
                response.Result = 0.0D;  
                break;  
        }  
        return response;  
    }  
}  
```  
  
 <span data-ttu-id="01d0e-118">클라이언트에 대해 생성 된 클라이언트 코드는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 도구를 사용 하 여 만들어졌습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-118">The generated client code for the client was created with the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span> <span data-ttu-id="01d0e-119">필요한 경우 이 도구는 생성된 클라이언트 코드에 자동으로 메시지 계약 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-119">The tool automatically creates message contract types in the generated client code if necessary.</span></span> <span data-ttu-id="01d0e-120">`/messageContract` 명령 옵션을 지정하여 메시지 계약을 강제로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-120">The `/messageContract` command option may be specified to force the generation of message contracts.</span></span>  
  
```console  
svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" /o:client\generatedClient.cs http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="01d0e-121">다음 샘플 코드에서는 `MyMessage` 메시지를 사용하는 클라이언트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-121">The following sample code demonstrates the client using the `MyMessage` message.</span></span>  
  
```csharp
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
// Perform addition using a typed message.  
  
MyMessage request = new MyMessage()
                    {  
                        N1 = 100D,  
                        N2 = 15.99D,  
                        Operation = "+"  
                    };
MyMessage response = ((ICalculator)client).Calculate(request);  
Console.WriteLine("Add({0},{1}) = {2}", request.N1, request.N2, response.Result);  
```  
  
 <span data-ttu-id="01d0e-122">샘플을 실행하면 계산이 클라이언트 콘솔 창에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-122">When you run the sample, the calculations are displayed in the client console window.</span></span> <span data-ttu-id="01d0e-123">클라이언트를 종료하려면 클라이언트 창에서 Enter 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="01d0e-124">여기서 클라이언트와 서비스 작업 간에 사용자 지정 사용자 정의 메시지가 전달되었습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-124">At this point, custom user-defined messages have passed between the client and the service operation.</span></span> <span data-ttu-id="01d0e-125">메시지 계약은 피연산자와 결과가 메시지 본문에 있고 연산자는 메시지 헤더에 있는 것으로 정의했습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-125">The message contract defined that the operands and results were in the message body and that the operator was in a message header.</span></span> <span data-ttu-id="01d0e-126">메시지 로깅을 구성하여 이 메시지 구조를 살펴볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-126">Message logging can be configured to observe this message structure.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01d0e-127">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="01d0e-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="01d0e-128">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="01d0e-129">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="01d0e-130">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="01d0e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="01d0e-131">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01d0e-132">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="01d0e-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="01d0e-133">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01d0e-134">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="01d0e-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Default`  
