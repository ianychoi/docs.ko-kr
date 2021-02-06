---
description: 다음에 대해 자세히 알아보세요. <channelPoolSettings>
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 85220cac360aaf32195c0b0f1d2866729e11c442
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99638979"
---
# \<channelPoolSettings>

<span data-ttu-id="e0da5-102">사용자 지정 바인딩의 채널 풀 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="e0da5-103">구문</span><span class="sxs-lookup"><span data-stu-id="e0da5-103">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0da5-104">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="e0da5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="e0da5-105">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0da5-106">특성</span><span class="sxs-lookup"><span data-stu-id="e0da5-106">Attributes</span></span>  
  
|<span data-ttu-id="e0da5-107">attribute</span><span class="sxs-lookup"><span data-stu-id="e0da5-107">Attribute</span></span>|<span data-ttu-id="e0da5-108">설명</span><span class="sxs-lookup"><span data-stu-id="e0da5-108">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="e0da5-109">연결이 끊어지기 전에 풀의 채널이 유휴 상태를 유지할 수 있는 최대 시간을 지정하는 <xref:System.TimeSpan>(양수)입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-109">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="e0da5-110">기본값은 00:02:00입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-110">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="e0da5-111">채널이 풀에 반환될 때 해당 기간이 경과하면 채널이 닫히는 시간 간격을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-111">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="e0da5-112">기본값은 00:10:00입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-112">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="e0da5-113">각 원격 엔드포인트에 대해 풀에 저장할 수 있는 최대 채널 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-113">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="e0da5-114">기본값은 10입니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-114">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0da5-115">자식 요소</span><span class="sxs-lookup"><span data-stu-id="e0da5-115">Child Elements</span></span>  

 <span data-ttu-id="e0da5-116">없음</span><span class="sxs-lookup"><span data-stu-id="e0da5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0da5-117">부모 요소</span><span class="sxs-lookup"><span data-stu-id="e0da5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e0da5-118">요소</span><span class="sxs-lookup"><span data-stu-id="e0da5-118">Element</span></span>|<span data-ttu-id="e0da5-119">설명</span><span class="sxs-lookup"><span data-stu-id="e0da5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="e0da5-120">사용자 지정 바인딩에 대한 패킷 라우팅을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-120">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0da5-121">설명</span><span class="sxs-lookup"><span data-stu-id="e0da5-121">Remarks</span></span>  

 <span data-ttu-id="e0da5-122">할당량은 과도한 리소스 소비를 방지하기 위한 정책 메커니즘으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-122">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="e0da5-123">할당량은 악의적이거나 의도하지 않은 DOS(서비스 거부) 공격을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-123">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="e0da5-124">사용자 지정 채널에서 채널 할당량을 설정할 때 이 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-124">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="e0da5-125">`ChannelPoolSettings`는 다음 세 가지 할당량을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-125">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="e0da5-126">`idleTimeout` 할당량을 사용하면 장기간 동안 제한된 리소스를 사용하는 서버에 대한 DOS(서비스 거부) 공격을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-126">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="e0da5-127">클라이언트에서 정확한 값을 설정하면 서비스 연결 안정성을 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-127">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="e0da5-128">기본값은 신중하고 적당한 리소스 할당을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-128">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="e0da5-129">이 값은 개발 환경 및 소규모 설치 시나리오에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-129">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="e0da5-130">설치로 인해 리소스가 부족해지거나 추가 리소스를 사용할 수 있더라도 연결이 제한되는 경우 서비스 관리자는 이 값을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-130">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="e0da5-131">`leaseTimeout` 할당량을 사용하면 부하 균형 도구와 통합되어 안정성을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-131">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="e0da5-132">기본값은 신중한 리소스 할당을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-132">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="e0da5-133">이 값은 개발 환경 및 소규모 설치 시나리오에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-133">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="e0da5-134">설치로 인해 리소스가 부족해지거나 추가 리소스를 사용할 수 있더라도 연결이 제한되는 경우 서비스 관리자는 이 값을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-134">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="e0da5-135">`maxOutboundChannelsPerEndpoint` 할당량은 서버와 클라이언트 양쪽에 캐시 제한을 설정하며 이를 사용하여 안정성을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-135">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="e0da5-136">기본값은 개발 환경 및 소규모 설치 시나리오에 적합한 신중하고 적당한 리소스 할당을 기준으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-136">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="e0da5-137">설치로 인해 리소스가 부족해지거나 추가 리소스를 사용할 수 있더라도 연결이 제한되는 경우 서비스 관리자는 이 값을 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e0da5-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0da5-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e0da5-138">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="e0da5-139">바인딩</span><span class="sxs-lookup"><span data-stu-id="e0da5-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="e0da5-140">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="e0da5-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="e0da5-141">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="e0da5-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
