---
description: '자세한 정보: ByteStream 인코더를 사용 하 여 이진 개체 인코딩'
title: ByteStream 인코더를 사용하여 이진 개체 인코딩
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 4ef3d3cd378abacd14dd502530a8090f3982e4ea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99704903"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a><span data-ttu-id="db4ab-103">ByteStream 인코더를 사용하여 이진 개체 인코딩</span><span class="sxs-lookup"><span data-stu-id="db4ab-103">Encoding Binary Objects with ByteStream Encoder</span></span>

<span data-ttu-id="db4ab-104">WCF (Windows Communication Foundation)를 사용 하 여 원시 이진 데이터를 보내고 받는 것은를 사용 하 여 구성 됩니다 <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="db4ab-104">Sending and receiving raw binary data with Windows Communication Foundation (WCF) is configured using <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.</span></span>  
  
## <a name="byte-stream-message-encoder-architecture"></a><span data-ttu-id="db4ab-105">바이트 스트림 메시지 인코더 아키텍처</span><span class="sxs-lookup"><span data-stu-id="db4ab-105">Byte Stream Message Encoder Architecture</span></span>  

 <span data-ttu-id="db4ab-106">WCF에서 사용 되는 이진 메시지 인코더에는 메시지의 기본 이진 데이터를 처리, 유효성 검사 또는 식별 하는 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-106">The binary message encoder used by WCF has no facility for processing, validating, or identifying the underlying binary data in the message.</span></span> <span data-ttu-id="db4ab-107">데이터 패키지는 XML로 인코딩된 후 보내기, 받기 및 디코딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-107">The data package is encoded into XML, sent, received, and decoded.</span></span> <span data-ttu-id="db4ab-108">인코더는 데이터가 전송에 전달된 후와 메시지가 메시지 큐에 보내지기 전에 데이터를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-108">The encoder processes the data after being passed to the transport and before the message is sent to the message queue.</span></span> <span data-ttu-id="db4ab-109">이진 인코더는 메시지 데이터를 `<binary>` 요소에 래핑하고 메시지를 받은 후 이 요소를 제거하는 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-109">Functionally, the binary encoder wraps the message data in `<binary>` elements for sending and removes the elements after the message is received.</span></span>  
  
## <a name="using-the-byte-stream-message-encoder"></a><span data-ttu-id="db4ab-110">바이트 스트림 메시지 인코더 사용</span><span class="sxs-lookup"><span data-stu-id="db4ab-110">Using the Byte Stream Message Encoder</span></span>  

 <span data-ttu-id="db4ab-111">다음 예제에서는 바이트 스트림 메시지 인코더를 구현하는 서비스 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-111">The following example shows a service contract that implements the byte stream message encoder.</span></span>  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 <span data-ttu-id="db4ab-112">다음 예제에서는 호출되는 서비스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-112">The following example shows the service being invoked.</span></span>  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 <span data-ttu-id="db4ab-113">라우터와 같은 메시지 인프라를 구현하는 서비스를 사용하는 경우 다음 예제와 같이 메시지가 검사, 유효성 검사 또는 상호 작용 없이 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-113">In the case of using a service that implements a message infrastructure (such as a router), the message is processed without inspecting, validating, or otherwise interacting with the message, as shown in the following example.</span></span>  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a><span data-ttu-id="db4ab-114">시나리오</span><span class="sxs-lookup"><span data-stu-id="db4ab-114">Scenarios</span></span>  

 <span data-ttu-id="db4ab-115">바이트 스트림 인코더는 다음과 같은 시나리오에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-115">The Byte Stream Encoder is useful in the following scenarios.</span></span>  
  
- <span data-ttu-id="db4ab-116">WCF를 사용 하 여 컴퓨터 간에 JPEG 이미지 전송</span><span class="sxs-lookup"><span data-stu-id="db4ab-116">Transferring a JPEG image between computers using WCF.</span></span> <span data-ttu-id="db4ab-117">이 시나리오에서는 이미지가 외부 소스에서의 전송을 통해 도착하며 전송된 데이터는 이미지를 구성하는 원시 바이트입니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-117">In this scenario, the image will arrive through the transport from an outside source, and the data sent will be the raw bytes that make up the image.</span></span> <span data-ttu-id="db4ab-118">서비스는 이진 데이터를 받고 이미지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-118">A service will receive the binary data and display the image.</span></span>  
  
- <span data-ttu-id="db4ab-119">메시지 큐에서 정보를 읽고 처리하는 경우.</span><span class="sxs-lookup"><span data-stu-id="db4ab-119">Reading information out of a message queue and processing it.</span></span> <span data-ttu-id="db4ab-120">메시지 큐 관리자에서 메시지를 읽으며 이 메시지는 처리되기 위해 메시지 큐 채널 위로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-120">The message will be read from a message queue manager, and passed up the message queue channel to be handled.</span></span> <span data-ttu-id="db4ab-121">메시지 큐 채널은 WCF 채널 스택에서 큐 관리자 역할을 합니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-121">The message queue channel will act as a queue manager in the WCF channel stack.</span></span>  
  
 <span data-ttu-id="db4ab-122">메시지 큐 채널을 통해 메시지를 보내는 경우 보낸 사람은 큐 관리자에서 받은 바이트를 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-122">In the case of sending a message over a message queue channel, the sender has no control over the bytes received from the queue manager.</span></span> <span data-ttu-id="db4ab-123">받는 프로세스에 원시 바이트를 읽는 기능이 없는 경우 메시지가 잘못된 형식으로 수신되고 처리되지 않습니다. 받는 프로세스에는 받은 바이트를 사용 가능한 형식으로 다시 변환하는 기능이 있다고 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="db4ab-123">If the receiving process has no capability to read raw bytes, the message will be received as badly formatted and will not be processed; it is assumed that the receiving process will have the capability of translating the received bytes back into a usable format.</span></span>
