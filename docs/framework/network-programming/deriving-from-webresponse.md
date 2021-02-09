---
description: '자세한 정보: WebResponse에서 파생'
title: WebResponse에서 파생
ms.date: 03/30/2017
helpviewer_keywords:
- Deriving from WebResponse
ms.assetid: f11d4866-a199-4087-9306-a5a4c18b13db
ms.openlocfilehash: 5e941ce055091c6034640733465020ff62ce3721
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747480"
---
# <a name="deriving-from-webresponse"></a><span data-ttu-id="74a77-103">WebResponse에서 파생</span><span class="sxs-lookup"><span data-stu-id="74a77-103">Deriving from WebResponse</span></span>

<span data-ttu-id="74a77-104"><xref:System.Net.WebResponse> 클래스는 .NET Framework 플러그형 프로토콜 모델에 적합한 프로토콜별 응답을 만들기 위한 기본 메서드 및 속성을 제공하는 추상 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-104">The <xref:System.Net.WebResponse> class is an abstract base class that provides the basic methods and properties for creating a protocol-specific response that fits the .NET Framework pluggable protocol model.</span></span> <span data-ttu-id="74a77-105"><xref:System.Net.WebRequest> 클래스를 사용하여 리소스의 데이터를 요청하는 애플리케이션은 **WebResponse** 로 응답을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-105">Applications that use the <xref:System.Net.WebRequest> class to request data from resources receive the responses in a **WebResponse**.</span></span> <span data-ttu-id="74a77-106">프로토콜별 **WebResponse** 하위 항목은 **WebResponse** 클래스의 추상 멤버를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-106">Protocol-specific **WebResponse** descendants must implement the abstract members of the **WebResponse** class.</span></span>  
  
 <span data-ttu-id="74a77-107">연결된 **WebRequest** 클래스는 **WebResponse** 하위 항목을 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-107">The associated **WebRequest** class must create **WebResponse** descendants.</span></span> <span data-ttu-id="74a77-108">예를 들어 <xref:System.Net.HttpWebResponse> 인스턴스는 <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> 또는 <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>를 호출한 결과로만 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-108">For example, <xref:System.Net.HttpWebResponse> instances are created only as the result of calling <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> or <xref:System.Net.HttpWebRequest.EndGetResponse%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="74a77-109">각 **WebResponse** 는 리소스에 대한 요청 결과를 포함하고 다시 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-109">Each **WebResponse** contains the result of a request to a resource and is not intended to be reused.</span></span>  
  
## <a name="contentlength-property"></a><span data-ttu-id="74a77-110">ContentLength 속성</span><span class="sxs-lookup"><span data-stu-id="74a77-110">ContentLength Property</span></span>  

 <span data-ttu-id="74a77-111"><xref:System.Net.WebResponse.ContentLength%2A> 속성은 <xref:System.Net.WebResponse.GetResponseStream%2A> 메서드에서 반환된 스트림에 사용 가능한 데이터 크기(바이트)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-111">The <xref:System.Net.WebResponse.ContentLength%2A> property indicates the number of bytes of data that are available from the stream returned by the <xref:System.Net.WebResponse.GetResponseStream%2A> method.</span></span> <span data-ttu-id="74a77-112">**ContentLength** 속성은 서버에서 반환된 헤더 또는 메타데이터 정보 크기(바이트)를 나타내지 않고, 요청된 리소스 자치의 데이터 크기(바이트)만 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-112">The **ContentLength** property does not indicate the number of bytes of header or metadata information returned by the server; it indicates only the number of bytes of data in the requested resource itself.</span></span>  
  
## <a name="contenttype-property"></a><span data-ttu-id="74a77-113">ContentType 속성</span><span class="sxs-lookup"><span data-stu-id="74a77-113">ContentType Property</span></span>  

 <span data-ttu-id="74a77-114"><xref:System.Net.WebResponse.ContentType%2A> 속성은 서버에서 보내는 콘텐츠 형식을 식별하기 위해 프로토콜을 통해 클라이언트에 보내야 하는 특수 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-114">The <xref:System.Net.WebResponse.ContentType%2A> property provides any special information that your protocol requires you to send to the client to identify the type of content being sent by the server.</span></span> <span data-ttu-id="74a77-115">일반적으로 이것은 반환된 데이터의 MIME 콘텐츠 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-115">Typically this is the MIME content type of any data returned.</span></span>  
  
## <a name="headers-property"></a><span data-ttu-id="74a77-116">Headers 속성</span><span class="sxs-lookup"><span data-stu-id="74a77-116">Headers Property</span></span>  

 <span data-ttu-id="74a77-117"><xref:System.Net.WebResponse.Headers%2A> 속성에는 응답과 연결된 메타데이터 이름/값 쌍의 임의 컬렉션이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-117">The <xref:System.Net.WebResponse.Headers%2A> property contains an arbitrary collection of name/value pairs of metadata associated with the response.</span></span> <span data-ttu-id="74a77-118">이름/값 쌍으로 표시될 수 있는 프로토콜에 필요한 모든 메타데이터가 **Headers** 속성에 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-118">Any metadata needed by the protocol that can be expressed as a name/value pair can be included in the **Headers** property.</span></span>  
  
 <span data-ttu-id="74a77-119">헤더 메타데이터를 사용하기 위해 **Headers** 속성을 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-119">You are not required to use the **Headers** property to use header metadata.</span></span> <span data-ttu-id="74a77-120">프로토콜별 메타데이터는 속성으로 노출됩니다. 예를 들어 <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> 속성은 **Last-Modified** HTTP 헤더를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-120">Protocol-specific metadata can be exposed as properties; for example, the <xref:System.Net.HttpWebResponse.LastModified%2A?displayProperty=nameWithType> property exposes the **Last-Modified** HTTP header.</span></span> <span data-ttu-id="74a77-121">헤더 메타데이터를 속성으로 노출할 경우 **Headers** 속성을 사용하여 동일한 속성을 설정하도록 허용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-121">When you expose header metadata as a property, you should not allow the same property to be set using the **Headers** property.</span></span>  
  
## <a name="responseuri-property"></a><span data-ttu-id="74a77-122">ResponseUri 속성</span><span class="sxs-lookup"><span data-stu-id="74a77-122">ResponseUri Property</span></span>  

 <span data-ttu-id="74a77-123"><xref:System.Net.WebResponse.ResponseUri%2A> 속성에는 실제로 응답을 제공하는 리소스의 URI가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-123">The <xref:System.Net.WebResponse.ResponseUri%2A> property contains the URI of the resource that actually provided the response.</span></span> <span data-ttu-id="74a77-124">리디렉션을 지원하지 않는 프로토콜이 경우 **ResponseUri** 는 응답을 만든 **WebRequest** 의 <xref:System.Net.WebRequest.RequestUri%2A> 속성과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-124">For protocols that do not support redirection, **ResponseUri** will be the same as the <xref:System.Net.WebRequest.RequestUri%2A> property of the **WebRequest** that created the response.</span></span> <span data-ttu-id="74a77-125">프로토콜이 요청 리디렉션을 지원할 경우 **ResponseUri** 에는 응답의 URI가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-125">If the protocol supports redirecting the request, **ResponseUri** will contain the URI of the response.</span></span>  
  
## <a name="close-method"></a><span data-ttu-id="74a77-126">Close 메서드</span><span class="sxs-lookup"><span data-stu-id="74a77-126">Close Method</span></span>  

 <span data-ttu-id="74a77-127"><xref:System.Net.WebResponse.Close%2A> 메서드는 요청 및 응답을 통해 생성된 모든 연결을 닫고 응답에서 사용된 리소스를 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-127">The <xref:System.Net.WebResponse.Close%2A> method closes any connections made by the request and response and cleans up resources used by the response.</span></span> <span data-ttu-id="74a77-128">**Close** 메서드는 응답에서 사용된 모든 스트림 인스턴스를 닫지만 응답 스트림이 이전에 <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> 메서드 호출을 통해 닫힌 경우 예외를 throw하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-128">The **Close** method closes any stream instances used by the response, but it does not throw an exception if the response stream was previously closed by a call to the <xref:System.IO.Stream.Close%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="getresponsestream-method"></a><span data-ttu-id="74a77-129">GetResponseStream 메서드</span><span class="sxs-lookup"><span data-stu-id="74a77-129">GetResponseStream Method</span></span>  

 <span data-ttu-id="74a77-130"><xref:System.Net.WebResponse.GetResponseStream%2A> 메서드는 요청된 리소스의 응답이 포함된 스트림을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-130">The <xref:System.Net.WebResponse.GetResponseStream%2A> method returns a stream containing the response from the requested resource.</span></span> <span data-ttu-id="74a77-131">응답 스트림에는 리소스에서 반환된 데이터만 포함되고 응답에 포함된 모든 헤더 또는 메타데이터는 프로토콜별 속성 또는 **Headers** 속성을 통해 응답에서 삭제되고 애플리케이션에 노출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-131">The response stream contains only the data returned by the resource; any header or metadata included in the response should be stripped from the response and exposed to the application through protocol-specific properties or the **Headers** property.</span></span>  
  
 <span data-ttu-id="74a77-132">**GetResponseStream** 메서드에서 반환되는 스트림 인스턴스는 애플리케이션이 소유하고 **WebResponse** 를 닫지 않고도 닫을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-132">The stream instance returned by the **GetResponseStream** method is owned by the application and can be closed without closing the **WebResponse**.</span></span> <span data-ttu-id="74a77-133">규칙에 따라 **WebResponse.Close** 메서드를 호출하면 **GetResponse** 에서 반환된 스트림도 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="74a77-133">By convention, calling the **WebResponse.Close** method also closes the stream returned by **GetResponse**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a77-134">참조</span><span class="sxs-lookup"><span data-stu-id="74a77-134">See also</span></span>

- <xref:System.Net.WebResponse>
- <xref:System.Net.HttpWebResponse>
- <xref:System.Net.FileWebResponse>
- [<span data-ttu-id="74a77-135">플러그형 프로토콜 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="74a77-135">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
- [<span data-ttu-id="74a77-136">WebRequest에서 파생</span><span class="sxs-lookup"><span data-stu-id="74a77-136">Deriving from WebRequest</span></span>](deriving-from-webrequest.md)
