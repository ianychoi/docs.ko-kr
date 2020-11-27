---
title: 래핑되지 않은 메시지
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: edecbc953cd3ade6135b4c76725e65d317d83132
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294982"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="ae533-102">래핑되지 않은 메시지</span><span class="sxs-lookup"><span data-stu-id="ae533-102">Unwrapped Messages</span></span>

<span data-ttu-id="ae533-103">이 샘플에서는 래핑되지 않은 메시지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="ae533-104">기본적으로 메시지 본문은 서비스 작업 매개 변수가 래핑되도록 서식이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="ae533-105">다음 샘플에서는 `Add` 서비스에 `ICalculator` 요청 메시지를 래핑된 모드로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="ae533-106">메시지 본문에 있는 `<Add>` 요소가 `n1` 및 `n2` 매개 변수를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="ae533-107">대조적으로, 다음 샘플에서는 같은 메시지를 래핑되지 않은 모드로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
```  
  
 <span data-ttu-id="ae533-108">래핑되지 않은 메시지는 포함하는 요소에 `n1` 및 `n2` 매개 변수를 래핑하지 않으며 SOAP 본문 요소의 직계 자식입니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae533-109">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ae533-110">이 샘플에서는 서비스 작업 매개 변수 형식에 <xref:System.ServiceModel.MessageContractAttribute>를 적용하고 다음 샘플 코드에 표시된 것과 같이 값 형식을 반환하여 래핑되지 않은 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="ae533-111">메시지를 보내고 받는 상황을 볼 수 있도록 이 샘플에서는 추적을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="ae533-112">또한 <xref:System.ServiceModel.WSHttpBinding>은 기록하는 메시지의 수를 줄이기 위해 보안 없이 구성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="ae533-113">C:\logs\Message.log ( [서비스 추적 뷰어 SvcTraceViewer.exe 도구)](../service-trace-viewer-tool-svctraceviewer-exe.md)를 사용 하 여 결과 추적 로그 ()를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="ae533-114">메시지 내용을 보려면 서비스 추적 뷰어 도구의 왼쪽 창과 오른쪽 창 모두에서 **메시지** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="ae533-115">이 샘플에서 추적 로그는 C:\LOGS 폴더에 생성되도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="ae533-116">샘플을 실행하기 전에 이 폴더를 만들고 사용자에게 이 디렉터리에 대한 네트워크 서비스 쓰기 권한을 부여해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ae533-117">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="ae533-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ae533-118">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ae533-119">메시지를 기록할 C:\LOGS 디렉터리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="ae533-120">사용자에게 이 디렉터리에 대한 네트워크 서비스 쓰기 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="ae533-121">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="ae533-122">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="ae533-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ae533-123">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ae533-124">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="ae533-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="ae533-125">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ae533-126">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae533-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
