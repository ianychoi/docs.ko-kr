---
title: '방법: 직렬화된 데이터 청크'
description: 데이터를 청크하여 대규모 데이터 세트의 문제를 방지할 수 있습니다. IXmlSerializable 인터페이스를 구현하여 serialization 및 deserialization을 제어합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: ee8bab4fe7659b1fe5b7edeabc81187d0a13e5bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679002"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="b9913-104">방법: 직렬화된 데이터 청크</span><span class="sxs-lookup"><span data-stu-id="b9913-104">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="b9913-105">대용량 데이터 집합을 웹 서비스 메시지에서 전송할 때 발생하는 두 가지 문제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-105">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="b9913-106">serialization 엔진의 버퍼링으로 인한 대용량 작업 집합(메모리)</span><span class="sxs-lookup"><span data-stu-id="b9913-106">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="b9913-107">Base64 인코딩 후 33퍼센트 확장으로 인한 과도한 대역폭 소비</span><span class="sxs-lookup"><span data-stu-id="b9913-107">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="b9913-108">이러한 문제를 해결하려면 <xref:System.Xml.Serialization.IXmlSerializable> 인터페이스를 구현하여 serialization과 deserialization을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-108">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="b9913-109">특히 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 및 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 메서드를 구현하여 데이터를 청크합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-109">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="b9913-110">서버측 청크를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="b9913-110">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="b9913-111">서버 시스템에서 웹 메서드는 ASP.NET 버퍼링을 끄고 <xref:System.Xml.Serialization.IXmlSerializable>을 구현하는 형식을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-111">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="b9913-112"><xref:System.Xml.Serialization.IXmlSerializable>을 구현하는 형식이 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 메서드의 데이터를 청크합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-112">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="b9913-113">클라이언트측 처리를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="b9913-113">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="b9913-114">클라이언트 프록시에서 웹 메서드를 변경하여 <xref:System.Xml.Serialization.IXmlSerializable>을 구현하는 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-114">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="b9913-115"><xref:System.Xml.Serialization.Advanced.SchemaImporterExtension>을 사용하여 이 작업을 자동으로 수행할 수 있지만 여기에는 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-115">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="b9913-116"><xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 메서드를 구현하여 청크된 데이터 스트림을 읽고 바이트를 디스크에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-116">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="b9913-117">또한 이 구현은 진행률 표시줄 등과 같은 그래픽 컨트롤에서 사용할 수 있는 진행률 이벤트도 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-117">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9913-118">예제</span><span class="sxs-lookup"><span data-stu-id="b9913-118">Example</span></span>  

<span data-ttu-id="b9913-119">다음 코드 예제에서는 ASP.NET 버퍼링을 끄는 클라이언트의 웹 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-119">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="b9913-120">또한 <xref:System.Xml.Serialization.IXmlSerializable> 메서드의 데이터를 청크하는 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 인터페이스의 클라이언트측 구현도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-120">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9913-121">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="b9913-121">Compiling the code</span></span>  
  
- <span data-ttu-id="b9913-122">코드에서는 <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> 및 <xref:System.Xml.Schema> 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b9913-122">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9913-123">참조</span><span class="sxs-lookup"><span data-stu-id="b9913-123">See also</span></span>

- [<span data-ttu-id="b9913-124">사용자 지정 serialization</span><span class="sxs-lookup"><span data-stu-id="b9913-124">Custom Serialization</span></span>](custom-serialization.md)
