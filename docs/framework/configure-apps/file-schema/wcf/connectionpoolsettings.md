---
description: 다음에 대해 자세히 알아보세요. <connectionPoolSettings>
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 5acf2d800f1a18f45750d0fabd23516f987b2c5e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782171"
---
# \<connectionPoolSettings>

<span data-ttu-id="3acad-102">명명된 파이프 바인딩의 추가 연결 풀 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="3acad-103">구문</span><span class="sxs-lookup"><span data-stu-id="3acad-103">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3acad-104">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="3acad-104">Attributes and Elements</span></span>  

 <span data-ttu-id="3acad-105">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3acad-106">특성</span><span class="sxs-lookup"><span data-stu-id="3acad-106">Attributes</span></span>  
  
|<span data-ttu-id="3acad-107">attribute</span><span class="sxs-lookup"><span data-stu-id="3acad-107">Attribute</span></span>|<span data-ttu-id="3acad-108">설명</span><span class="sxs-lookup"><span data-stu-id="3acad-108">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="3acad-109">나가는 채널에 사용되는 연결 풀의 이름을 정의하는 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-109">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="3acad-110">스트리밍 모드에서는 연결이 공유되지 않습니다. 즉 연결 풀링이 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-110">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="3acad-111">기본값은 "default" 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-111">The default is a "default" string.</span></span> <span data-ttu-id="3acad-112">이 값을 수정하여 특정 클라이언트의 연결을 별도의 그룹으로 격리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-112">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="3acad-113">연결이 끊어지기 전에 유휴 상태를 유지할 수 있는 최대 시간을 지정하는 <xref:System.TimeSpan>(양수)입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-113">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="3acad-114">기본값은 00:02:00입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-114">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="3acad-115">서비스에서 시작된 원격 엔드포인트와의 최대 연결 수를 지정하는 양의 정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-115">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="3acad-116">이 제한을 초과하는 연결은 채널 수가 제한 아래로 내려갈 때까지 큐에 대기됩니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-116">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="3acad-117">`idleTimeout`은 예외가 throw되기 전에 연결이 큐에 대기할 수 있는 시간을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-117">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="3acad-118">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-118">The default is 10.</span></span><br /><br /> <span data-ttu-id="3acad-119">이 특성은 클라이언트에서 특정 서비스 엔드포인트로의 동시 활성 연결 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-119">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="3acad-120">활성 클라이언트 연결 수가 이 값을 초과할 경우 해당 서비스가 클라이언트에 응답하지 않는 것처럼 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-120">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="3acad-121">이러한 경우 이 값을 특정 엔드포인트에 대해 예상되는 동시 클라이언트 최대 연결 수보다 크게 조정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-121">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3acad-122">자식 요소</span><span class="sxs-lookup"><span data-stu-id="3acad-122">Child Elements</span></span>  

 <span data-ttu-id="3acad-123">없음</span><span class="sxs-lookup"><span data-stu-id="3acad-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3acad-124">부모 요소</span><span class="sxs-lookup"><span data-stu-id="3acad-124">Parent Elements</span></span>  
  
|<span data-ttu-id="3acad-125">요소</span><span class="sxs-lookup"><span data-stu-id="3acad-125">Element</span></span>|<span data-ttu-id="3acad-126">설명</span><span class="sxs-lookup"><span data-stu-id="3acad-126">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="3acad-127">채널이 명명된 파이프를 사용하여 메시지를 전송하게 하는 전송을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3acad-127">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3acad-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3acad-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3acad-129">전송</span><span class="sxs-lookup"><span data-stu-id="3acad-129">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="3acad-130">전송 선택</span><span class="sxs-lookup"><span data-stu-id="3acad-130">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="3acad-131">바인딩</span><span class="sxs-lookup"><span data-stu-id="3acad-131">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3acad-132">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="3acad-132">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3acad-133">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="3acad-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
