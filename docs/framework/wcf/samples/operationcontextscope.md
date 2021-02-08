---
description: '자세히 알아보기: OperationContextScope'
title: OperationContextScope
ms.date: 03/30/2017
ms.assetid: 11c11108-8eb4-4d49-95a0-83285a812262
ms.openlocfilehash: efe05bdf4071ef8dfd86cf4c393b2abb8d20ad31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793209"
---
# <a name="operationcontextscope"></a><span data-ttu-id="eb48a-103">OperationContextScope</span><span class="sxs-lookup"><span data-stu-id="eb48a-103">OperationContextScope</span></span>

<span data-ttu-id="eb48a-104">OperationContextScope 샘플에서는 헤더를 사용 하 여 WCF (Windows Communication Foundation) 호출에 대 한 추가 정보를 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-104">The OperationContextScope sample demonstrates how to send extra information on a Windows Communication Foundation (WCF) call using headers.</span></span> <span data-ttu-id="eb48a-105">이 샘플에서는 서버와 클라이언트 모두가 콘솔 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-105">In this sample, both the server and client are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb48a-106">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="eb48a-107">샘플에서는 클라이언트가 <xref:System.ServiceModel.Channels.MessageHeader>를 사용하여 <xref:System.ServiceModel.OperationContextScope>로 추가 정보를 보낼 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-107">The sample demonstrates how a client can send additional information as a <xref:System.ServiceModel.Channels.MessageHeader> using <xref:System.ServiceModel.OperationContextScope>.</span></span> <span data-ttu-id="eb48a-108"><xref:System.ServiceModel.OperationContextScope> 개체는 채널로 범위를 지정하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-108">An <xref:System.ServiceModel.OperationContextScope> object is created by scoping it to a channel.</span></span> <span data-ttu-id="eb48a-109">원격 서비스로 해석해야 하는 헤더는 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> 컬렉션에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-109">Headers that must be translated to the remote service can be added to the <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="eb48a-110">이 컬렉션에 추가된 헤더는 서비스에서 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>에 액세스하여 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-110">Headers added to this collection can be retrieved on the service by accessing <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A>.</span></span> <span data-ttu-id="eb48a-111">호출은 여러 채널에 대해 수행되며, 클라이언트에 추가된 헤더는 <xref:System.ServiceModel.OperationContextScope>를 만드는 데 사용된 채널에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-111">Its calls are made on multiple channels and then the headers added to the client only apply to the channel that was used to create the <xref:System.ServiceModel.OperationContextScope>.</span></span>  
  
## <a name="messageheaderreader"></a><span data-ttu-id="eb48a-112">MessageHeaderReader</span><span class="sxs-lookup"><span data-stu-id="eb48a-112">MessageHeaderReader</span></span>  

 <span data-ttu-id="eb48a-113">클라이언트에서 메시지를 받은 후 <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> 컬렉션에서 헤더 조회를 시도하는 샘플 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-113">This is the sample service that receives a message from the client and tries to look up the header in the <xref:System.ServiceModel.OperationContext.IncomingMessageHeaders%2A> collection.</span></span> <span data-ttu-id="eb48a-114">클라이언트에서는 전송한 GUID를 헤더에 전달하고 서비스에서는 사용자 지정 헤더를 검색하며, 있는 경우 클라이언트에서 인수로 전달한 GUID와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-114">The client passes the GUID that it sent in the header and the service retrieves the custom header and, if present, compares it with the GUID passed as the argument by the client.</span></span>  
  
```csharp
public bool RetrieveHeader(string guid)  
{  
     MessageHeaders messageHeaderCollection =
             OperationContext.Current.IncomingMessageHeaders;  
     String guidHeader = null;  
  
     Console.WriteLine("Trying to check if IncomingMessageHeader " +  
               " collection contains header with value {0}", guid);  
     if (messageHeaderCollection.FindHeader(  
                       CustomHeader.HeaderName,
                       CustomHeader.HeaderNamespace) != -1)  
     {  
          guidHeader = messageHeaderCollection.GetHeader<String>(  
           CustomHeader.HeaderName, CustomHeader.HeaderNamespace);  
     }  
     else  
     {  
          Console.WriteLine("No header was found");  
     }  
     if (guidHeader != null)  
     {  
          Console.WriteLine("Found header with value {0}. "+
         "Does it match with GUID sent as parameter: {1}",
          guidHeader, guidHeader.Equals(guid));  
      }  
  
      Console.WriteLine();  
      //Return true if header is present and equals the guid sent by  
      // client as argument  
      return (guidHeader != null && guidHeader.Equals(guid));  
}  
```  
  
## <a name="messageheaderclient"></a><span data-ttu-id="eb48a-115">MessageHeaderClient</span><span class="sxs-lookup"><span data-stu-id="eb48a-115">MessageHeaderClient</span></span>  

 <span data-ttu-id="eb48a-116">이는 [ServiceModel Metadata 유틸리티 도구 (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) 에서 생성 된 프록시를 사용 하 여 원격 서비스와 통신 하는 클라이언트 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-116">This is the client implementation that uses the proxy generated by [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to communicate with the remote service.</span></span> <span data-ttu-id="eb48a-117">여기서는 먼저 `MessageHeaderReaderClient`의 프록시 개체 두 개를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-117">It first creates two proxy objects of `MessageHeaderReaderClient`.</span></span>  
  
```csharp
//Create two clients to the remote service.  
MessageHeaderReaderClient client1 = new MessageHeaderReaderClient();  
MessageHeaderReaderClient client2 = new MessageHeaderReaderClient();  
```  
  
 <span data-ttu-id="eb48a-118">그러면 클라이언트에서 OperationContextScope를 만들고 범위를 `client1`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-118">Client then creates an OperationContextScope and scopes it to `client1`.</span></span> <span data-ttu-id="eb48a-119">여기서는 <xref:System.ServiceModel.Channels.MessageHeader>를 <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A>에 추가하고 두 클라이언트 모두에 대해 한 번의 호출을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-119">It adds a <xref:System.ServiceModel.Channels.MessageHeader> to <xref:System.ServiceModel.OperationContext.OutgoingMessageHeaders%2A> and invokes one call on both clients.</span></span> <span data-ttu-id="eb48a-120">`client1` `client2` 호출에서 반환 값을 확인 하 여이 아닌 에서만 헤더를 보내고 사용 하지 않도록 합니다 `RetrieveHeader` .</span><span class="sxs-lookup"><span data-stu-id="eb48a-120">It ensures that the header is sent only on `client1` and not on `client2` by checking the return value from the `RetrieveHeader` call.</span></span>  
  
```csharp
using (new OperationContextScope(client1.InnerChannel))  
{  
    //Create a new GUID that is sent as the header.  
    String guid = Guid.NewGuid().ToString();  
  
    //Create a MessageHeader for the GUID we just created.  
    MessageHeader customHeader = MessageHeader.CreateHeader(CustomHeader.HeaderName, CustomHeader.HeaderNamespace, guid);  
  
    //Add the header to the OutgoingMessageHeader collection.  
    OperationContext.Current.OutgoingMessageHeaders.Add(customHeader);  
  
    //Now call RetrieveHeader on both the proxies. Since the OperationContextScope is tied to
    //client1's InnerChannel, the header should only be added to calls made on that client.  
    //Calls made on client2 should not be sending the header across even though the call  
    //is made in the same OperationContextScope.  
    Console.WriteLine("Using client1 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: True", client1.RetrieveHeader(guid));  
  
    Console.WriteLine();  
    Console.WriteLine("Using client2 to send message");  
    Console.WriteLine("Did server retrieve the header? : Actual: {0}, Expected: False", client2.RetrieveHeader(guid));  
}  
```  
  
 <span data-ttu-id="eb48a-121">이 샘플은 자체 호스팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-121">This sample is self-hosted.</span></span> <span data-ttu-id="eb48a-122">샘플을 실행한 결과 다음 샘플 출력이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-122">The following sample output from running the sample is provided:</span></span>  
  
```console  
Prompt> Service.exe  
The service is ready.  
Press <ENTER> to terminate service.  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
Found header with value 2239da67-546f-42d4-89dc-8eb3c06215d8. Does it match with GUID sent as parameter: True  
  
Trying to check if IncomingMessageHeader collection contains header with value 2239da67-546f-42d4-89dc-8eb3c06215d8  
No header was found  
  
Prompt>Client.exe  
Using client1 to send message  
Did server retrieve the header? : Actual: True, Expected: True  
  
Using client2 to send message  
Did server retrieve the header? : Actual: False, Expected: False  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eb48a-123">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="eb48a-123">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="eb48a-124">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="eb48a-125">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="eb48a-126">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="eb48a-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="eb48a-127">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eb48a-128">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="eb48a-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="eb48a-129">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eb48a-130">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb48a-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\OperationContextScope`  
