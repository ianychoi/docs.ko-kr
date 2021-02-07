---
description: 다음에 대해 자세히 알아보세요. <namedPipeTransport>
title: <namedPipeTransport>
ms.date: 03/30/2017
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
ms.openlocfilehash: 68714404492be92ce789dbde95a39199f5de16d4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684102"
---
# \<namedPipeTransport>

<span data-ttu-id="19eb5-102">사용자 지정 바인딩에 포함될 때 채널에서 명명된 파이프를 사용하여 메시지를 전송하도록 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-102">Defines a transport that causes a channel to transfer messages using named pipes when it is included in a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedPipeTransport>**  
  
## <a name="syntax"></a><span data-ttu-id="19eb5-103">구문</span><span class="sxs-lookup"><span data-stu-id="19eb5-103">Syntax</span></span>  
  
```xml  
<namedPipeTransport channelInitializationTimeout="TimeSpan"
                    connectionBufferSize="Integer"
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"
                    manualAddressing="Boolean"
                    maxBufferPoolSize="Integer"
                    maxBufferSize="Integer"
                    maxOutputDelay="TimeSpan"
                    maxPendingAccepts="Integer"
                    maxPendingConnections="Integer"
                    maxReceivedMessageSize="Integer"
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
  <connectionPoolSettings groupName="String"
                          idleTimeout="TimeSpan"
                          maxOutboundConnectionsPerEndpoint="Integer" />
</namedPipeTransport>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19eb5-104">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="19eb5-104">Attributes and Elements</span></span>  

<span data-ttu-id="19eb5-105">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19eb5-106">특성</span><span class="sxs-lookup"><span data-stu-id="19eb5-106">Attributes</span></span>  

<span data-ttu-id="19eb5-107">없음</span><span class="sxs-lookup"><span data-stu-id="19eb5-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="19eb5-108">자식 요소</span><span class="sxs-lookup"><span data-stu-id="19eb5-108">Child Elements</span></span>  
  
|<span data-ttu-id="19eb5-109">요소</span><span class="sxs-lookup"><span data-stu-id="19eb5-109">Element</span></span>|<span data-ttu-id="19eb5-110">설명</span><span class="sxs-lookup"><span data-stu-id="19eb5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="19eb5-111">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="19eb5-111">ChannelInitializationTimeout</span></span>|<span data-ttu-id="19eb5-112">연결이 끊어지기 전에 채널이 초기화 상태를 유지할 수 있는 최대 시간을 결정하는 <xref:System.TimeSpan>을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-112">Gets or sets a <xref:System.TimeSpan> that determines the maximum time a channel can be in the initialization status before being disconnected.</span></span>|  
|<span data-ttu-id="19eb5-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="19eb5-113">ConnectionBufferSize</span></span>|<span data-ttu-id="19eb5-114">통신 중에 클라이언트나 서비스로부터 serialize된 메시지 청크를 전송할 때 사용되는 버퍼의 크기를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-114">Gets or sets the size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>|  
|<span data-ttu-id="19eb5-115">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="19eb5-115">hostNameComparisonMode</span></span>|<span data-ttu-id="19eb5-116">URI 비교 시 서비스에 액세스하는 데 호스트 이름이 사용되는지 여부를 나타내는 값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-116">Gets or sets a value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>|  
|<span data-ttu-id="19eb5-117">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="19eb5-117">manualAddressing</span></span>|<span data-ttu-id="19eb5-118">메시지의 주소를 수동으로 지정해야 하는지 여부를 나타내는 값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-118">Gets or sets a value that indicates whether manual addressing of the message is required.</span></span>|  
|<span data-ttu-id="19eb5-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="19eb5-119">maxBufferPoolSize</span></span>|<span data-ttu-id="19eb5-120">전송에 사용되는 버퍼 풀의 최대 크기(바이트)를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-120">Gets or sets the maximum size, in bytes, of any buffer pools used by the transport.</span></span>|  
|<span data-ttu-id="19eb5-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="19eb5-121">maxBufferSize</span></span>|<span data-ttu-id="19eb5-122">사용할 버퍼의 최대 크기를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-122">Gets or sets the maximum size of the buffer to use.</span></span> <span data-ttu-id="19eb5-123">스트리밍된 메시지의 경우 이 값은 버퍼링된 모드에서 읽어오는 메시지 헤더의 최대 예상 크기 이상이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-123">For streamed messages, this value should be at least the maximum possible size of the message headers, which are read in buffered mode.</span></span>|  
|<span data-ttu-id="19eb5-124">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="19eb5-124">maxOutputDelay</span></span>|<span data-ttu-id="19eb5-125">메시지 청크 또는 전체 메시지를 보내기 전에 메모리에 버퍼링된 상태로 유지할 수 있는 최대 시간 간격을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-125">Gets or sets the maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>|  
|<span data-ttu-id="19eb5-126">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="19eb5-126">maxPendingAccepts</span></span>|<span data-ttu-id="19eb5-127">서비스에 들어오는 연결을 처리하기 위해 수신기에서 서비스가 대기할 수 있는 최대 채널 수를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-127">Gets or sets the maximum number of channels a service can have waiting on a listener for processing incoming connections to the service.</span></span>|  
|<span data-ttu-id="19eb5-128">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="19eb5-128">maxPendingConnections</span></span>|<span data-ttu-id="19eb5-129">서비스에서 디스패치를 대기하는 최대 연결 수를 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-129">Gets or sets the maximum number of connections awaiting dispatch on the service.</span></span>|  
|<span data-ttu-id="19eb5-130">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="19eb5-130">maxReceivedMessageSize</span></span>|<span data-ttu-id="19eb5-131">받을 수 있는 최대 메시지 크기 (바이트)를 가져오거나 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-131">Gets and sets the maximum allowable message size, in bytes, that can be received.</span></span>|  
|<span data-ttu-id="19eb5-132">transferMode</span><span class="sxs-lookup"><span data-stu-id="19eb5-132">transferMode</span></span>|<span data-ttu-id="19eb5-133">메시지가 연결 지향 전송을 사용하여 버퍼링되는지 아니면 스트리밍되는지를 나타내는 값을 가져오거나 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-133">Gets or sets a value that indicates whether the messages are buffered or streamed with the connection-oriented transport.</span></span>|  
|[<span data-ttu-id="19eb5-134">\<namedPipeTransport>의 \<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="19eb5-134">\<connectionPoolSettings> of \<namedPipeTransport></span></span>](connectionpoolsettings.md)|<span data-ttu-id="19eb5-135">명명된 파이프 바인딩의 추가 연결 풀 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-135">Specifies additional connection pool settings for a Named Pipe binding.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="19eb5-136">부모 요소</span><span class="sxs-lookup"><span data-stu-id="19eb5-136">Parent Elements</span></span>  
  
|<span data-ttu-id="19eb5-137">요소</span><span class="sxs-lookup"><span data-stu-id="19eb5-137">Element</span></span>|<span data-ttu-id="19eb5-138">설명</span><span class="sxs-lookup"><span data-stu-id="19eb5-138">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="19eb5-139">사용자 지정 바인딩의 모든 바인딩 기능을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-139">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19eb5-140">설명</span><span class="sxs-lookup"><span data-stu-id="19eb5-140">Remarks</span></span>  

<span data-ttu-id="19eb5-141">이 전송은 "net.pipe://hostname/path" 형식의 URI를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-141">This transport uses URIs of the form "net.pipe://hostname/path".</span></span> <span data-ttu-id="19eb5-142">다른 URI 구성 요소는 선택적입니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-142">Other URI components are optional.</span></span>  
  
<span data-ttu-id="19eb5-143">`namedPipeTransport` 요소는 명명된 파이프 전송 프로토콜을 구현하는 사용자 지정 바인딩을 만들기 위한 시작점입니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-143">The `namedPipeTransport` element is the starting point for creating a custom binding that implements the named pipes transport protocol.</span></span> <span data-ttu-id="19eb5-144">이 전송은 WCF(Windows Communication Foundation)와 WCF 사이의 컴퓨터 통신에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="19eb5-144">This transport is used for on-machine Windows Communication Foundation (WCF)-to-WCF communication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19eb5-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="19eb5-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeTransportElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="19eb5-146">전송</span><span class="sxs-lookup"><span data-stu-id="19eb5-146">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="19eb5-147">전송 선택</span><span class="sxs-lookup"><span data-stu-id="19eb5-147">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="19eb5-148">바인딩</span><span class="sxs-lookup"><span data-stu-id="19eb5-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="19eb5-149">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="19eb5-149">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="19eb5-150">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="19eb5-150">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
