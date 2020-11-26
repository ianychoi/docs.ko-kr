---
title: '방법: 스트리밍 사용'
description: 버퍼링 된 기본 전송이 아닌 WCF에서 스트리밍된 메시지를 사용 하도록 설정 하는 방법에 대해 알아봅니다. 이러한 메시지는 처리 되기 전에 완전히 받아야 합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 7f77c406e1cfd4def116a1abe24aa92be74c6abe
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96237744"
---
# <a name="how-to-enable-streaming"></a><span data-ttu-id="fe036-103">방법: 스트리밍 사용</span><span class="sxs-lookup"><span data-stu-id="fe036-103">How to: Enable Streaming</span></span>

<span data-ttu-id="fe036-104">WCF (Windows Communication Foundation)는 버퍼링 또는 스트리밍 전송 중 하나를 사용 하 여 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-104">Windows Communication Foundation (WCF) can send messages using either buffered or streamed transfers.</span></span> <span data-ttu-id="fe036-105">기본 설정인 버퍼링된 전송 모드에서는 메시지가 완전히 전달되어야 수신자가 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-105">In the default buffered-transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="fe036-106">스트리밍 전송 모드에서는 메시지가 완전히 전달되기 전에 수신자가 메시지 처리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-106">In streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="fe036-107">전달되는 정보가 길고 순차적으로 처리 가능한 경우 스트리밍 모드가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-107">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="fe036-108">또한 전체를 버퍼링하기에는 메시지가 너무 큰 경우에도 스트리밍 모드가 효과적입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-108">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
 <span data-ttu-id="fe036-109">스트리밍을 사용하려면 `OperationContract`를 적절히 정의하고 전송 수준에서 스트리밍을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-109">To enable streaming, define the `OperationContract` appropriately and enable streaming at the transport level.</span></span>  
  
### <a name="to-stream-data"></a><span data-ttu-id="fe036-110">데이터를 스트리밍하려면</span><span class="sxs-lookup"><span data-stu-id="fe036-110">To stream data</span></span>  
  
1. <span data-ttu-id="fe036-111">데이터를 스트리밍하려면 서비스에 대한 `OperationContract`가 두 가지 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-111">To stream data, the `OperationContract` for the service must satisfy two requirements:</span></span>  
  
    1. <span data-ttu-id="fe036-112">전송할 데이터를 보유하는 매개 변수가 메서드의 유일한 매개 변수이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-112">The parameter that holds the data to be streamed must be the only parameter in the method.</span></span> <span data-ttu-id="fe036-113">예를 들어, 입력 메시지를 스트리밍할 경우 해당 작업은 단 하나의 입력 매개 변수만 가져야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-113">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="fe036-114">마찬가지로, 출력 메시지를 스트리밍할 경우 해당 작업에는 출력 매개 변수 또는 반환 값이 하나만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-114">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span>  
  
    2. <span data-ttu-id="fe036-115">반환 값과 매개 변수 유형 중 하나 이상이 <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message> 또는 <xref:System.Xml.Serialization.IXmlSerializable>이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-115">At least one of the types of the parameter and return value must be either <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, or <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
     <span data-ttu-id="fe036-116">다음은 스트리밍된 데이터의 계약 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-116">The following is an example of a contract for streamed data.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     <span data-ttu-id="fe036-117">`GetStream` 작업은 버퍼링되는 `string`으로 버퍼링된 입력 데이터를 받고, 스트리밍되는 `Stream`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-117">The `GetStream` operation receives some buffered input data as a `string`, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="fe036-118">반대로 `UploadStream`은 스트리밍된 `Stream`을 받아 버퍼링된 `bool`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-118">Conversely `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="fe036-119">`EchoStream`은 `Stream`을 받고 반환하므로 입출력 메시지 모두 스트리밍되는 작업의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-119">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="fe036-120">마지막으로, `GetReversedStream`은 어떤 입력도 받지 않고 스트리밍되는 `Stream`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-120">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
2. <span data-ttu-id="fe036-121">바인딩에서 스트리밍을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-121">Streaming must be enabled on the binding.</span></span> <span data-ttu-id="fe036-122">다음 값 중 하나를 가져올 수 있는 `TransferMode` 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-122">You set a `TransferMode` property, which can take one of the following values:</span></span>  
  
    1. <span data-ttu-id="fe036-123">`Buffered`,</span><span class="sxs-lookup"><span data-stu-id="fe036-123">`Buffered`,</span></span>  
  
    2. <span data-ttu-id="fe036-124">`Streamed`. 양 방향으로 스트리밍 통신이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-124">`Streamed`, which enables streaming communication in both directions.</span></span>  
  
    3. <span data-ttu-id="fe036-125">`StreamedRequest`. 요청만 스트리밍이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-125">`StreamedRequest`, which enables streaming the request only.</span></span>  
  
    4. <span data-ttu-id="fe036-126">`StreamedResponse`. 응답만 스트리밍이 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-126">`StreamedResponse`, which enables streaming the response only.</span></span>  
  
     <span data-ttu-id="fe036-127">`BasicHttpBinding`은 `TransferMode` 및 `NetTcpBinding`과 같이 바인딩에 `NetNamedPipeBinding` 속성을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-127">The `BasicHttpBinding` exposes the `TransferMode` property on the binding, as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="fe036-128">`TransferMode` 속성은 전송 바인딩 요소에서 설정하고 사용자 지정 바인딩에서 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-128">The `TransferMode` property can also be set on the transport binding element and used in a custom binding.</span></span>  
  
     <span data-ttu-id="fe036-129">다음 샘플에서는 코드를 사용하거나 구성 파일을 변경하여 `TransferMode`를 설정하는 방법에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-129">The following samples show how to set `TransferMode` by code and by changing the configuration file.</span></span> <span data-ttu-id="fe036-130">또한 이 샘플에서는 두 방법 모두 `maxReceivedMessageSize` 속성을 64MB로 설정하여 받을 수 있는 최대 메시지 크기를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-130">The samples also both set the `maxReceivedMessageSize` property to 64 MB, which places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="fe036-131">기본 `maxReceivedMessageSize`는 64KB이며, 이는 스트리밍 시나리오에서는 일반적으로 너무 낮은 수준입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-131">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span> <span data-ttu-id="fe036-132">이 할당량을 애플리케이션이 받을 최대 메시지 크기에 따라 적절히 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-132">Set this quota setting as appropriate depending on the maximum size of messages your application expects to receive.</span></span> <span data-ttu-id="fe036-133">또한 `maxBufferSize`는 버퍼링되는 최대 크기를 제어하고 이를 적절히 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-133">Also note that `maxBufferSize` controls the maximum size that is buffered, and set it appropriately.</span></span>  
  
    1. <span data-ttu-id="fe036-134">샘플 중 다음 구성 조각은 `TransferMode` 및 사용자 지정 HTTP 바인딩에서 `basicHttpBinding` 속성을 스트리밍으로 설정하는 방법에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-134">The following configuration snippet from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. <span data-ttu-id="fe036-135">다음 코드 조각은 `TransferMode` 및 사용자 지정 HTTP 바인딩에서 `basicHttpBinding` 속성을 스트리밍으로 설정하는 방법에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-135">The following code snippet shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. <span data-ttu-id="fe036-136">다음 코드 조각은 사용자 지정 HTTP 바인딩에서 `TransferMode` 속성을 스트리밍으로 설정하는 것 방법에 대해 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-136">The following code snippet shows setting the `TransferMode` property to streaming on a custom TCP binding.</span></span>  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. <span data-ttu-id="fe036-137">`GetStream`, `UploadStream` 및 `EchoStream` 작업 모두 파일로부터 데이터를 직접 보내거나 받은 데이터를 파일에 바로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-137">The operations `GetStream`, `UploadStream`, and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="fe036-138">다음 코드는 `GetStream`에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-138">The following code is for `GetStream`.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a><span data-ttu-id="fe036-139">사용자 지정 스트림 쓰기</span><span class="sxs-lookup"><span data-stu-id="fe036-139">Writing a custom stream</span></span>  
  
1. <span data-ttu-id="fe036-140">데이터 스트림의 각 청크에서 데이터를 보내고 받을 때 특수한 처리를 수행하려면 <xref:System.IO.Stream>에서 사용자 지정 스트림 클래스를 파생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-140">To do special processing on each chunk of a data stream as it is being sent or received, derive a custom stream class from <xref:System.IO.Stream>.</span></span> <span data-ttu-id="fe036-141">사용자 지정 스트림의 예로 다음 코드에 `GetReversedStream` 메서드와 `ReverseStream` 클래스가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-141">As an example of a custom stream, the following code contains a `GetReversedStream` method and a `ReverseStream` class-.</span></span>  
  
     <span data-ttu-id="fe036-142">`GetReversedStream`은 `ReverseStream`의 새 인스턴스를 만들어 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-142">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="fe036-143">시스템이 `ReverseStream` 개체에서 읽을 때 실제 처리가 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-143">The actual processing happens as the system reads from the `ReverseStream` object.</span></span> <span data-ttu-id="fe036-144">`ReverseStream.Read` 메서드는 기본 파일에서 바이트 청크를 읽고 이를 되돌린 다음, 되돌린 해당 바이트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-144">The `ReverseStream.Read` method reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="fe036-145">이 메서드는 파일의 전체 내용을 되돌리지 않으며, 한 번에 하나의 바이트 청크를 되돌립니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-145">This method does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="fe036-146">이는 스트림에서 콘텐츠를 읽거나 쓰는 중에 스트림 처리를 수행하는 방법에 대해 보여 주는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="fe036-146">This example shows how you can perform stream processing as the content is being read to or written from the stream.</span></span>  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fe036-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fe036-147">See also</span></span>

- [<span data-ttu-id="fe036-148">큰 데이터 및 스트리밍</span><span class="sxs-lookup"><span data-stu-id="fe036-148">Large Data and Streaming</span></span>](large-data-and-streaming.md)
- [<span data-ttu-id="fe036-149">스트림</span><span class="sxs-lookup"><span data-stu-id="fe036-149">Stream</span></span>](../samples/stream.md)
