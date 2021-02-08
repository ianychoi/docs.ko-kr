---
description: '자세히 알아보기: POX 응용 프로그램과의 상호 운용성'
title: POX 응용 프로그램과의 상호 운용성
ms.date: 03/30/2017
ms.assetid: 449276b8-4633-46f0-85c9-81f01d127636
ms.openlocfilehash: 832b9ae93f6046ca9995b57bdcbbfbfeb46d2a09
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802712"
---
# <a name="interoperability-with-pox-applications"></a><span data-ttu-id="2c1a7-103">POX 응용 프로그램과의 상호 운용성</span><span class="sxs-lookup"><span data-stu-id="2c1a7-103">Interoperability with POX applications</span></span>

<span data-ttu-id="2c1a7-104">"일반 이전 XML" (POX) 응용 프로그램은 SOAP 봉투 (envelope)에 포함 되지 않은 XML 응용 프로그램 데이터만 포함 하는 원시 HTTP 메시지를 교환 하 여 통신 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-104">"Plain Old XML" (POX) applications communicate by exchanging raw HTTP messages that contain only XML application data that is not enclosed within a SOAP envelope.</span></span> <span data-ttu-id="2c1a7-105">WCF (Windows Communication Foundation)는 POX 메시지를 사용 하는 서비스와 클라이언트를 둘 다 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-105">Windows Communication Foundation (WCF) can provide both services and clients that use POX messages.</span></span> <span data-ttu-id="2c1a7-106">서비스에서 WCF를 사용 하 여 웹 브라우저와 같은 클라이언트에 끝점을 노출 하는 서비스를 구현 하 고 POX 메시지를 보내고 받는 스크립트 언어를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-106">On the service, WCF can be used to implement services that expose endpoints to clients such as Web browsers and scripting languages that send and receive POX messages.</span></span> <span data-ttu-id="2c1a7-107">클라이언트에서 WCF 프로그래밍 모델을 사용 하 여 POX 기반 서비스와 통신 하는 클라이언트를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-107">On the client, the WCF programming model can be used to implement clients that communicate with POX-based services.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c1a7-108">이 문서는 처음에 .NET Framework 3.0 용으로 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-108">This document was originally written for the .NET Framework 3.0.</span></span>  <span data-ttu-id="2c1a7-109">.NET Framework 3.5에는 POX 응용 프로그램 작업에 대 한 기본 제공 지원이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-109">.NET Framework 3.5 has built-in support for working with POX applications.</span></span> <span data-ttu-id="2c1a7-110">에 대 한 자세한 내용은 [WCF 웹 HTTP 프로그래밍 모델](wcf-web-http-programming-model.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-110">For more information about see [WCF Web HTTP Programming Model](wcf-web-http-programming-model.md).</span></span>
  
## <a name="pox-programming-with-wcf"></a><span data-ttu-id="2c1a7-111">WCF를 사용 하 여 POX 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="2c1a7-111">POX programming with WCF</span></span>

<span data-ttu-id="2c1a7-112">POX 메시지를 사용 하 여 HTTP를 통해 통신 하는 WCF 서비스는를 사용 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-112">WCF services that communicate over HTTP using POX messages use a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>

```xml
<customBinding>
   <binding name="poxServerBinding">
       <textMessageEncoding messageVersion="None" />
       <httpTransport />
   </binding>
</customBinding>
```

<span data-ttu-id="2c1a7-113">이 사용자 지정 바인딩에는 다음과 같은 두 가지 요소가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-113">This custom binding contains two elements:</span></span>

- [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md)

- [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md)

<span data-ttu-id="2c1a7-114">표준 WCF 텍스트 메시지 인코더는 값을 사용 하도록 특별히 구성 되어 있으며 <xref:System.ServiceModel.Channels.MessageVersion.None%2A> ,이를 통해 SOAP 봉투에 래핑되지 않은 XML 메시지 페이로드를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-114">The standard WCF Text Message Encoder is specially configured to use the <xref:System.ServiceModel.Channels.MessageVersion.None%2A> value, which allows it to process XML message payloads that do not arrive wrapped in a SOAP envelope.</span></span>

<span data-ttu-id="2c1a7-115">POX 메시지를 사용 하 여 HTTP를 통해 통신 하는 WCF 클라이언트는 유사한 바인딩을 사용 합니다 (다음 명령적 코드에 표시 됨).</span><span class="sxs-lookup"><span data-stu-id="2c1a7-115">WCF clients that communicate over HTTP using POX messages use a similar binding (shown in the following imperative code).</span></span>

```csharp
private static Binding CreatePoxBinding()
{
    TextMessageEncodingBindingElement encoder =
        new TextMessageEncodingBindingElement( MessageVersion.None, Encoding.UTF8 );
    HttpTransportBindingElement transport = new HttpTransportBindingElement();
    transport.ManualAddressing = true;
    return new CustomBinding( new BindingElement[] { encoder, transport } );
}
```

<span data-ttu-id="2c1a7-116">POX 클라이언트는 메시지를 보내는 대상 URI를 명시적으로 지정해야 하기 때문에 일반적으로 POX 클라이언트는 요소에서 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> 속성을 <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A>로 설정하여 `true`를 수동 주소 지정 모드로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-116">Because POX clients must explicitly specify the URIs to which they send messages, they usually must configure the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> to a manual addressing mode by setting the <xref:System.ServiceModel.Channels.TransportBindingElement.ManualAddressing%2A> property to `true` on the element.</span></span> <span data-ttu-id="2c1a7-117">이를 통해 메시지 주소를 애플리케이션 코드에 따라 명시적으로 지정할 수 있으며 애플리케이션이 메시지를 다른 HTTP URI로 보낼 때마다 새 <xref:System.ServiceModel.ChannelFactory>를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-117">This allows messages to be addressed explicitly by application code and it is not necessary to create a new <xref:System.ServiceModel.ChannelFactory> every time an application sends a message to a different HTTP URI.</span></span>

<span data-ttu-id="2c1a7-118">POX 메시지는 중요한 프로토콜 정보를 전달하기 위해 SOAP 헤더를 사용하지 않기 때문에 POX 클라이언트 및 서비스가 메시지를 보내거나 받는 데 사용되는 기본 HTTP 요청 일부를 종종 조작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-118">Because POX messages do not use SOAP headers to convey important protocol information, POX clients and services often must manipulate pieces of the underlying HTTP request used to send or receive a message.</span></span> <span data-ttu-id="2c1a7-119">HTTP 헤더 및 상태 코드와 같은 HTTP 관련 프로토콜 정보는 다음 두 클래스를 통해 WCF 프로그래밍 모델에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-119">HTTP-specific protocol information such as the HTTP headers and status codes are surfaced in the WCF programming model through two classes:</span></span>

- <span data-ttu-id="2c1a7-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, 여기에는 HTTP 메서드 및 요청 헤더와 같은 HTTP 요청에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-120"><xref:System.ServiceModel.Channels.HttpRequestMessageProperty>, which contains information about the HTTP request, such as the HTTP method and request headers.</span></span>

- <span data-ttu-id="2c1a7-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, 여기에는 HTTP 응답 헤더뿐만 아니라 HTTP 상태 코드 및 상태 설명과 같은 HTTP 응답에 대한 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-121"><xref:System.ServiceModel.Channels.HttpResponseMessageProperty>, which contains information about the HTTP response, such as the HTTP status code and status description, as well as any HTTP response headers.</span></span>
  
<span data-ttu-id="2c1a7-122">다음 코드 예제에서는로 주소가 지정 된 HTTP GET 요청 메시지를 만드는 방법을 보여 줍니다 `http://localhost:8100/customers` .</span><span class="sxs-lookup"><span data-stu-id="2c1a7-122">The following code example shows how to create an HTTP GET request message that is addressed to `http://localhost:8100/customers`.</span></span>

```csharp
Message request = Message.CreateMessage( MessageVersion.None, String.Empty );
request.Headers.To = "http://localhost:8100/customers";

HttpRequestMessageProperty property = new HttpRequestMessageProperty();
property.Method = "GET";
property.SuppressEntityBody = true;
request.Properties.Add( HttpRequestMessageProperty.Name, property );
```

<span data-ttu-id="2c1a7-123">먼저 <xref:System.ServiceModel.Channels.Message>를 호출하여 빈 요청 <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-123">First, an empty request <xref:System.ServiceModel.Channels.Message> is created by calling <xref:System.ServiceModel.Channels.Message.CreateMessage%28System.ServiceModel.Channels.MessageVersion%2CSystem.String%29>.</span></span> <span data-ttu-id="2c1a7-124"><xref:System.ServiceModel.Channels.MessageVersion.None%2A> 매개 변수는 SOAP 봉투가 필요 없음을 나타내는 데 사용되며 <xref:System.String.Empty> 매개 변수는 작업으로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-124">The <xref:System.ServiceModel.Channels.MessageVersion.None%2A> parameter is used to indicate that a SOAP envelope is not required and <xref:System.String.Empty> parameter is passed as the Action.</span></span> <span data-ttu-id="2c1a7-125">그런 다음 <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> 헤더를 원하는 URI로 설정하여 요청 메시지의 주소가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-125">The request message is then addressed by setting <xref:System.ServiceModel.Channels.MessageHeaders.To%2A> header to the desired URI.</span></span> <span data-ttu-id="2c1a7-126">그런 후 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>가 만들어지고 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A>가 HTTP verb GET 메서드로 설정되며, <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A>가 `true`로 설정되어 나가는 HTTP 요청 메시지의 본문에 보낼 데이터가 없어야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-126">Next, an <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> is created and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.Method%2A> is set to the HTTP verb GET method and the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty.SuppressEntityBody%2A> is set to `true` to indicate that no data should be sent in the body of the outgoing HTTP request message.</span></span> <span data-ttu-id="2c1a7-127">마지막으로, HTTP 전송이 요청을 보내는 방법에 영향을 줄 수 있도록 요청 속성이 요청 메시지의 <xref:System.ServiceModel.Channels.Message.Properties%2A> 컬렉션에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-127">Finally, the request property is added to the <xref:System.ServiceModel.Channels.Message.Properties%2A> collection of the request message so it can influence how the HTTP Transport sends the request.</span></span> <span data-ttu-id="2c1a7-128">그런 다음 메시지를 <xref:System.ServiceModel.Channels.IRequestChannel>의 해당 인스턴스를 통해 보낼 준비를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-128">The message is then ready to be sent over an appropriate instance of the <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span>

<span data-ttu-id="2c1a7-129">서비스에 대해 유사한 방법을 사용하여 들어오는 메시지에서 <xref:System.ServiceModel.Channels.HttpRequestMessageProperty>를 추출하고 응답을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c1a7-129">Similar techniques can be used on the service to extract the <xref:System.ServiceModel.Channels.HttpRequestMessageProperty> from an incoming message and construct a response.</span></span>
