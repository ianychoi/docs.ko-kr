---
title: XMLSerializer 오류
ms.date: 03/30/2017
ms.assetid: c6b80f14-64f4-4162-ae76-71664cf42fd3
ms.openlocfilehash: 1eefa37d6d11e232bd4d0914eedab3ebb66b92ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237653"
---
# <a name="xmlserializer-faults"></a><span data-ttu-id="d82f2-102">XMLSerializer 오류</span><span class="sxs-lookup"><span data-stu-id="d82f2-102">XmlSerializer Faults</span></span>

<span data-ttu-id="d82f2-103"><xref:System.Xml.Serialization.XmlSerializer>Fault Contract 샘플은 <xref:System.Xml.Serialization.XmlSerializer>를 사용하여 오류 정보를 서비스에서 클라이언트로 전달하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-103">The <xref:System.Xml.Serialization.XmlSerializer> fault contract sample demonstrates how to communicate error information from a service to a client using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d82f2-104">이 샘플은 [시작](getting-started-sample.md)을 기반으로 하며 내부 예외를 오류로 변환 하기 위해 몇 가지 추가 코드를 서비스에 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-104">The sample is based on the [Getting Started](getting-started-sample.md), with some additional code added to the service to convert an internal exception to a fault.</span></span> <span data-ttu-id="d82f2-105">클라이언트는 서비스에서 오류 조건을 강제하기 위해 0으로 나누기를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-105">The client attempts to perform division by zero to force an error condition on the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d82f2-106">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d82f2-107">다음 샘플 코드와 같이 계산기 계약은 <xref:System.ServiceModel.FaultContractAttribute>를 포함하도록 수정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-107">The calculator contract has been modified to include a <xref:System.ServiceModel.FaultContractAttribute> as shown in the following sample code.</span></span> <span data-ttu-id="d82f2-108">또한 <xref:System.ServiceModel.XmlSerializerFormatAttribute>를 사용한 serialization을 지원하도록 <xref:System.Xml.Serialization.XmlSerializer>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-108">Also, the <xref:System.ServiceModel.XmlSerializerFormatAttribute> is used to enable serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="d82f2-109">이 특성에 대해 <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> 속성이 `true`로 설정되어 오류를 읽고 쓰는 데 <xref:System.Xml.Serialization.XmlSerializer>를 사용하도록 serializer에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-109">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A> property is set to `true` on this attribute, which instructs the serializer to use the <xref:System.Xml.Serialization.XmlSerializer> for reading and writing faults.</span></span>  
  
```csharp
[XmlSerializerFormat(SupportFaults=true)]  
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
  
 <span data-ttu-id="d82f2-110">클라이언트 프록시에 대 한 코드를 생성할 때 **/UseSerializerForFaults** 플래그를 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)에 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-110">When generating code for the client proxy, you must apply the **/UseSerializerForFaults** flag to [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d82f2-111">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d82f2-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d82f2-112">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d82f2-113">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d82f2-114">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="d82f2-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d82f2-115">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-115">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d82f2-116">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d82f2-116">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d82f2-117">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-117">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d82f2-118">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d82f2-118">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\XmlSerializerFaults`  
  
## <a name="see-also"></a><span data-ttu-id="d82f2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d82f2-119">See also</span></span>

- <xref:System.ServiceModel.XmlSerializerFormatAttribute>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute.SupportFaults%2A>
