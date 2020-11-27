---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 1cb0cd4e7300920afb900af0291b9e3d3dc778b2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268289"
---
# <a name="srmp"></a><span data-ttu-id="5f810-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="5f810-102">SRMP</span></span>

<span data-ttu-id="5f810-103">이 샘플에서는 HTTP를 통해 MSMQ(메시지 큐)를 사용하여 트랜잭션된 대기 중인 통신을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="5f810-104">대기 중인 통신에서 클라이언트는 큐를 사용하여 서비스와 통신합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="5f810-105">좀더 정확하게 말하면 클라이언트는 큐에 메시지를 보내고,</span><span class="sxs-lookup"><span data-stu-id="5f810-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="5f810-106">서비스는 큐에서 보낸 메시지를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-106">The service receives messages from the queue.</span></span> <span data-ttu-id="5f810-107">따라서 서비스와 클라이언트가 동시에 실행되고 있지 않더라도 큐를 사용하여 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="5f810-108">MSMQ는 HTTP 사용(HTTPS 사용 포함)을 통해 큐에 메시지를 보낼 수 있게 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="5f810-109">이 예제에서는 Windows Communication Foundation (WCF) 대기 중인 통신을 사용 하 고 HTTP를 통해 메시지를 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="5f810-110">MSMQ는 HTTP를 통한 통신에 사용되는 SOAP 기반 프로토콜인 SRMP라는 프로토콜을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5f810-111">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5f810-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5f810-112">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="5f810-113">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="5f810-114">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="5f810-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5f810-115">**Windows 구성 요소 추가/제거** 에서 샘플을 실행 하기 전에 MSMQ가 HTTP 지원과 함께 설치 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="5f810-116">HTTP 지원을 설치하면 IIS(인터넷 정보 서비스)가 자동으로 설치되고 MSMQ용 IIS에서 프로토콜 지원이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="5f810-117">HTTP를 통신에 사용하도록 하려면 MSMQ를 강화된 모드에서 실행할 수 있도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="5f810-118">이렇게 하면 컴퓨터에서 호스트되는 큐에 보내는 어떠한 메시지도 HTTP가 아닌 전송을 사용하여 도달할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="5f810-119">강화 된 모드에서 MSMQ를 실행 하도록 선택한 후에는 Windows Server 2003에서 컴퓨터를 다시 부팅 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on Windows Server 2003.</span></span>  
  
7. <span data-ttu-id="5f810-120">서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-120">Run the service.</span></span>  
  
8. <span data-ttu-id="5f810-121">클라이언트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-121">Run the client.</span></span> <span data-ttu-id="5f810-122">localhost 대신 컴퓨터 이름이나 IP 주소를 가리키도록 엔드포인트 주소를 변경해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="5f810-123">클라이언트는 메시지를 보내고 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f810-124">요구 사항</span><span class="sxs-lookup"><span data-stu-id="5f810-124">Requirements</span></span>  

 <span data-ttu-id="5f810-125">이 샘플을 실행하려면 MSMQ 외에 서비스와 클라이언트 컴퓨터 둘 다에 IIS가 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="5f810-126">데모</span><span class="sxs-lookup"><span data-stu-id="5f810-126">Demonstrates</span></span>  

 <span data-ttu-id="5f810-127">이 샘플에서는 HTTP를 통해 MSMQ를 사용 하 여 대기 중인 WCF 메시지를 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="5f810-128">이를 SRMP 메시징이라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="5f810-129">대기 중인 메시지를 보낼 경우 보내는 컴퓨터의 MSMQ는 TCP 또는 HTTP 전송을 통해 수신 큐 관리자에게 메시지를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="5f810-130">사용자는 SRMP를 선택하여 큐 전송을 위한 전송 프로토콜로 HTTP가 사용된다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="5f810-131">SRMP 보안에서는 HTTPS 사용이 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f810-132">예제</span><span class="sxs-lookup"><span data-stu-id="5f810-132">Example</span></span>  

 <span data-ttu-id="5f810-133">이 샘플 코드는 트랜잭션된 샘플에 기반을 둡니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="5f810-134">SRMP를 사용하여 큐에 메시지를 보내고 큐에서 메시지를 받는 방법은 네이티브 프로토콜을 사용하여 메시지를 보내고 받는 방법과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="5f810-135">클라이언트에 대한 구성은 선택된 큐 전송 프로토콜을 나타내도록 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="5f810-136">큐 전송 프로토콜은 Native, SRMP 또는 SrmpSecure 중 하나가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="5f810-137">기본적으로 전송 프로토콜은 Native입니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="5f810-138">이 예제에서 클라이언트와 서비스는 SRMP를 사용한다는 것을 구성에서 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="5f810-139">전송 보안과 관련하여 SRMP에는 몇 가지 제한 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="5f810-140">기본 MSMQ 전송 보안의 경우 전송 큐 관리자와 수신 큐 관리자가 동일한 Windows 도메인에 있어야 한다는 것을 요구하는 Active Directory가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="5f810-141">HTTP 경계를 통해 메시지를 보낼 경우 이 요구 사항을 충족할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="5f810-142">따라서 기본 전송 보안이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="5f810-143">이 경우 전송 보안을 사용하려면 전송 보안을 Certificate로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="5f810-144">또한 메시지 보안을 사용하여 메시지를 보안할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="5f810-145">이 샘플에서는 SRMP 메시징을 보여 주기 위해 전송 보안과 메시지 보안이 모두 해제됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="5f810-146">샘플을 실행하면 다음 출력이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="5f810-147">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5f810-148">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="5f810-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5f810-149">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f810-150">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f810-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
