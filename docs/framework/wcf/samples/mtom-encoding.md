---
title: MTOM 인코딩
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: c2b5cc59f2e2a80a323070e452dfcf7c4c0cc4d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260216"
---
# <a name="mtom-encoding"></a><span data-ttu-id="5d094-102">MTOM 인코딩</span><span class="sxs-lookup"><span data-stu-id="5d094-102">MTOM Encoding</span></span>

<span data-ttu-id="5d094-103">이 샘플에서는 WSHttpBinding과 함께 MTOM(Message Transmission Optimization Mechanism) 메시지 인코딩을 사용하는 것을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="5d094-104">MTOM은 SOAP 메시지와 함께 큰 이진 첨부 파일을 원시 바이트로 전송함으로써 더 작은 크기의 메시지를 허용하는 메커니즘입니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5d094-105">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5d094-106">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5d094-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5d094-107">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5d094-108">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="5d094-109">기본적으로 WSHttpBinding은 메시지를 일반 텍스트 XML로 보내고 받습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="5d094-110">MTOM 메시지를 보내고 받을 수 있도록 다음 예제 코드에서 보여 주는 것처럼 바인딩의 구성에서 또는 `messageEncoding` 속성을 사용하여 직접 바인딩에서 `MessageEncoding` 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="5d094-111">이제 서비스 또는 클라이언트에서 MTOM 메시지를 보내고 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="5d094-112">MTOM 인코더는 바이트 및 스트림의 배열을 최적화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="5d094-113">이 샘플의 작업에서는 `Stream` 매개 변수를 사용하므로 최적화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="5d094-114">이 샘플에서 선택된 계약은 이진 데이터를 서비스에 전송하고 업로드된 바이트 수를 반환 값으로 받습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="5d094-115">서비스가 설치되고 클라이언트가 실행될 때 숫자 1000을 출력하는데, 이는 총 1000바이트를 수신했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="5d094-116">출력의 나머지에서는 다양한 페이로드에 대해 최적화되고 최적화되지 않은 메시지 크기를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="5d094-117">MTOM을 사용하는 목적은 큰 이진 페이로드의 전송을 최적화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="5d094-118">MTOM을 사용하여 SOAP 메시지를 보낼 경우 작은 이진 페이로드에서는 상당한 오버헤드가 되지만, 몇 천 바이트 이상으로 늘어날 경우 상당한 절감 효과를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="5d094-119">일반 텍스트 XML이 3바이트마다 4개의 문자가 필요한 Base64를 사용하여 이진 데이터를 인코딩하므로 데이터의 크기가 1/3 증가하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="5d094-120">MTOM에서는 이진 데이터를 원시 바이트로 전송할 수 있으므로 인코딩/디코딩 시간 및 메시지 크기가 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="5d094-121">오늘날의 비즈니스 문서 및 디지털 사진에 비하면 몇 천 바이트 임계값은 작습니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5d094-122">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5d094-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5d094-123">다음 명령을 사용 하 여 ASP.NET 4.0을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5d094-124">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="5d094-125">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5d094-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5d094-126">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="5d094-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
