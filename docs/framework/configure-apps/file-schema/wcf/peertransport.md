---
description: 다음에 대해 자세히 알아보세요. <peerTransport>
title: <peerTransport>
ms.date: 03/30/2017
ms.assetid: c1a5013a-9dd4-4a27-b114-795b8b323177
ms.openlocfilehash: babc4196c63d46b7515ac67812d5d584eb3ffcac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683621"
---
# \<peerTransport>

<span data-ttu-id="437c3-102">사용자 지정 바인딩에 대한 피어 전송을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-102">Defines a peer transport for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="437c3-103">구문</span><span class="sxs-lookup"><span data-stu-id="437c3-103">Syntax</span></span>  
  
```xml  
<peerTransport listenIpAddress="String"
               maxBufferPoolSize="Integer"
               maxReceivedMessageSize="Integer"
               port="Integer">
  <security>
  </security>
</peerTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="437c3-104">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="437c3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="437c3-105">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="437c3-106">특성</span><span class="sxs-lookup"><span data-stu-id="437c3-106">Attributes</span></span>  
  
|<span data-ttu-id="437c3-107">attribute</span><span class="sxs-lookup"><span data-stu-id="437c3-107">Attribute</span></span>|<span data-ttu-id="437c3-108">설명</span><span class="sxs-lookup"><span data-stu-id="437c3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="437c3-109">listenIpAddress</span><span class="sxs-lookup"><span data-stu-id="437c3-109">listenIpAddress</span></span>|<span data-ttu-id="437c3-110">피어 노드가 TCP 메시지를 수신하는 IP 주소를 지정하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-110">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="437c3-111">기본값은 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-111">The default is `null`.</span></span>|  
|<span data-ttu-id="437c3-112">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="437c3-112">maxBufferPoolSize</span></span>|<span data-ttu-id="437c3-113">버퍼 풀의 최대 크기를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-113">A positive integer that specifies the maximum size of the buffer pool.</span></span> <span data-ttu-id="437c3-114">기본값은 524288입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-114">The default is 524288.</span></span><br /><br /> <span data-ttu-id="437c3-115">WCF의 많은 부분에서 버퍼를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-115">Many parts of WCF use buffers.</span></span> <span data-ttu-id="437c3-116">버퍼를 사용할 때마다 만들고 삭제하면 비용이 많이 들며, 버퍼에 대한 가비지 수집 역시 비용이 많이 듭니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-116">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="437c3-117">버퍼 풀이 있으면 이 풀로부터 버퍼를 가져와 사용한 다음 다시 풀로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-117">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="437c3-118">따라서 버퍼를 만들고 제거하는 데 오버헤드를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-118">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="437c3-119">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="437c3-119">maxReceivedMessageSize</span></span>|<span data-ttu-id="437c3-120">헤더를 포함하는 최대 메시지 크기(바이트)를 정의하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-120">A positive integer that defines the maximum message size in bytes including headers.</span></span> <span data-ttu-id="437c3-121">수신자에게 너무 큰 메시지를 보내면 메시지의 발신자에게 SOAP 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-121">The sender of a message receives a SOAP fault when the message is too large for the receiver.</span></span> <span data-ttu-id="437c3-122">수신자는 메시지를 삭제하고 추적 로그에 이벤트 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-122">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="437c3-123">기본값은 65536입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-123">The default is 65536.</span></span>|  
|<span data-ttu-id="437c3-124">포트</span><span class="sxs-lookup"><span data-stu-id="437c3-124">port</span></span>|<span data-ttu-id="437c3-125">이 바인딩이 피어 채널 TCP 메시지를 처리할 네트워크 인터페이스 포트를 지정하는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-125">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="437c3-126">이 값은 <xref:System.Net.IPEndPoint.MinPort>와 <xref:System.Net.IPEndPoint.MaxPort> 사이의 값이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-126">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="437c3-127">기본값은 0입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-127">The default is 0.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="437c3-128">자식 요소</span><span class="sxs-lookup"><span data-stu-id="437c3-128">Child Elements</span></span>  
  
|<span data-ttu-id="437c3-129">요소</span><span class="sxs-lookup"><span data-stu-id="437c3-129">Element</span></span>|<span data-ttu-id="437c3-130">설명</span><span class="sxs-lookup"><span data-stu-id="437c3-130">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="437c3-131">이 전송의 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-131">Defines the security settings for this transport.</span></span> <span data-ttu-id="437c3-132">이 요소는 <xref:System.ServiceModel.Configuration.PeerSecurityElement> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-132">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="437c3-133">부모 요소</span><span class="sxs-lookup"><span data-stu-id="437c3-133">Parent Elements</span></span>  
  
|<span data-ttu-id="437c3-134">요소</span><span class="sxs-lookup"><span data-stu-id="437c3-134">Element</span></span>|<span data-ttu-id="437c3-135">설명</span><span class="sxs-lookup"><span data-stu-id="437c3-135">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="437c3-136">사용자 지정 바인딩의 모든 바인딩 기능을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-136">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="437c3-137">설명</span><span class="sxs-lookup"><span data-stu-id="437c3-137">Remarks</span></span>  

 <span data-ttu-id="437c3-138">request/reply 작업이 있는 계약에서는 이 전송을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="437c3-138">This transport cannot be used with contracts that have request/reply operations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437c3-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="437c3-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportElement>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="437c3-140">전송</span><span class="sxs-lookup"><span data-stu-id="437c3-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="437c3-141">전송 선택</span><span class="sxs-lookup"><span data-stu-id="437c3-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="437c3-142">바인딩</span><span class="sxs-lookup"><span data-stu-id="437c3-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="437c3-143">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="437c3-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="437c3-144">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="437c3-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
