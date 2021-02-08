---
description: '다음에 대 한 자세한 정보: <localServiceSettings> 요소'
title: <localServiceSettings> 요소
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: ee3306588d6a86ed9ced9c66624cd34f18e2c5c6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802205"
---
# <a name="localservicesettings-element"></a><span data-ttu-id="abfd1-103">\<localServiceSettings> 요소</span><span class="sxs-lookup"><span data-stu-id="abfd1-103">\<localServiceSettings> element</span></span>

<span data-ttu-id="abfd1-104">이 바인딩에 대한 로컬 서비스의 보안 설정을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-104">Specifies the security settings of a local service for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localServiceSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="abfd1-105">구문</span><span class="sxs-lookup"><span data-stu-id="abfd1-105">Syntax</span></span>  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="abfd1-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="abfd1-106">Attributes and Elements</span></span>  

 <span data-ttu-id="abfd1-107">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="abfd1-108">특성</span><span class="sxs-lookup"><span data-stu-id="abfd1-108">Attributes</span></span>  
  
|<span data-ttu-id="abfd1-109">attribute</span><span class="sxs-lookup"><span data-stu-id="abfd1-109">Attribute</span></span>|<span data-ttu-id="abfd1-110">설명</span><span class="sxs-lookup"><span data-stu-id="abfd1-110">Description</span></span>|  
|---------------|-----------------|  
|`detectReplays`|<span data-ttu-id="abfd1-111">채널에 대한 재생 공격이 검색되어 자동으로 처리되는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-111">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="abfd1-112">기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-112">The default is `false`.</span></span>|  
|`inactivityTimeout`|<span data-ttu-id="abfd1-113">채널에서 제한 시간이 초과되기 전에 대기하는 비활성 기간을 지정하는 <xref:System.TimeSpan>(양수)입니다. 기본값은 "01:00:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-113">A positive <xref:System.TimeSpan> that specifies the duration of inactivity the channel waits before it times out. The default is "01:00:00".</span></span>|  
|`issuedCookieLifeTime`|<span data-ttu-id="abfd1-114">새로운 모든 보안 쿠키에 발급되는 수명을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-114">A <xref:System.TimeSpan> that specifies the lifetime issued to all new security cookies.</span></span> <span data-ttu-id="abfd1-115">수명이 지난 쿠키는 재활용되며 다시 협상되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-115">Cookies that exceed their lifetime are recycled and need to be negotiated again.</span></span> <span data-ttu-id="abfd1-116">기본값은 "10:00:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-116">The default value is "10:00:00".</span></span>|  
|`maxCachedCookies`|<span data-ttu-id="abfd1-117">캐시할 수 있는 최대 쿠키 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-117">A positive integer that specifies the maximum number of cookies that can be cached.</span></span> <span data-ttu-id="abfd1-118">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-118">The default is 1000.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="abfd1-119">서로 통신하는 양쪽의 시스템 클록 간의 최대 시간 차이를 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-119">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="abfd1-120">기본값은 "00:05:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-120">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="abfd1-121">이 값을 기본값으로 설정하면 수신자는 메시지를 받은 시간을 기준으로 보낸 시간 타임스탬프가 전후 5분 이내인 메시지를 수신 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-121">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="abfd1-122">보낸 시간 테스트를 통과하지 못한 메시지는 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-122">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="abfd1-123">이 설정은 `replayWindow` 특성과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-123">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxPendingSessions`|<span data-ttu-id="abfd1-124">서비스에서 지원하는 보류 중인 보안 세션의 최대 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-124">A positive integer that specifies the maximum number of pending security sessions that the service supports.</span></span> <span data-ttu-id="abfd1-125">이 한도에 도달하면 모든 새 클라이언트가 SOAP 오류를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-125">When this limit is reached, all new clients receive SOAP faults.</span></span> <span data-ttu-id="abfd1-126">기본값은 1000입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-126">The default value is 1000.</span></span>|  
|`maxStatefulNegotiations`|<span data-ttu-id="abfd1-127">동시에 활성 상태를 유지할 수 있는 보안 협상 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-127">A positive integer that specifies the number of security negotiations that can be active concurrently.</span></span> <span data-ttu-id="abfd1-128">한도를 초과하는 협상 세션은 큐에 대기되며 한도 아래로 떨어져야 완료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-128">Negotiation sessions in excess of the limit are queued and can only be completed when a space below the limit becomes available.</span></span> <span data-ttu-id="abfd1-129">기본값은 1024입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-129">The default value is 1024.</span></span>|  
|`negotiationTimeout`|<span data-ttu-id="abfd1-130">채널에서 사용하는 보안 정책의 수명을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-130">A <xref:System.TimeSpan> that specifies the lifetime of the security policy used by channel.</span></span> <span data-ttu-id="abfd1-131">시간이 만료되면 채널이 새로운 보안 정책에 대해 클라이언트와 재협상합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-131">When the time expires, the channel renegotiates with the client for a new security policy.</span></span> <span data-ttu-id="abfd1-132">기본값은 "00:02:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-132">The default value is "00:02:00".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="abfd1-133">WS-Reliable Messaging을 사용하는 연결에서 전송 실패 후 다시 연결을 시도할지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-133">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="abfd1-134">기본값은 `true`로, 다시 연결이 무한히 시도된다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-134">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="abfd1-135">이 순환은 비활성 제한 시간이 초과되어야만 중단되며, 이 경우 채널에서 다시 연결할 수 없으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-135">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="abfd1-136">재생 검색에 사용되는 캐시된 Nonce의 수를 지정하는 양의 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-136">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="abfd1-137">이 제한을 초과하면 가장 오래된 Nonce가 제거되고 새 메시지에 대해 새로운 Nonce가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-137">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="abfd1-138">기본값은 500000입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-138">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="abfd1-139">개별 메시지 Nonce의 유효 기간을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-139">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="abfd1-140">이 속성에서 지정한 시간이 지나면 이전에 보낸 메시지와 동일한 Nonce를 갖는 메시지는 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-140">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="abfd1-141">이 특성은 `maxClockSkew` 특성과 함께 사용되어 재생 공격을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-141">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="abfd1-142">메시지 재생 창이 만료된 후에 공격자가 그 메시지를 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-142">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="abfd1-143">그러나 이 메시지는 `maxClockSkew` 테스트를 통과하지 못합니다. 해당 테스트는 메시지의 보낸 시간 타임스탬프가 메시지를 받은 시간보다 지정된 시간 이상으로 늦거나 빠르면 그 메시지를 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-143">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="abfd1-144">개시자가 보안 세션을 위해 키를 갱신하는 시간 간격을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-144">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="abfd1-145">기본값은 "10:00:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-145">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="abfd1-146">키 갱신 중에 들어오는 메시지에서 이전 세션 키를 사용할 수 있는 시간 간격을 지정하는 <xref:System.TimeSpan>입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-146">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="abfd1-147">기본값은 "00:05:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-147">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="abfd1-148">키 갱신 중에 클라이언트와 서버는 반드시 사용 가능한 최신 키를 사용하여 메시지를 보내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-148">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="abfd1-149">양쪽 모두 롤오버 시간이 만료될 때까지는 이전 세션 키를 사용하여 보안되는 메시지를 수락할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-149">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="abfd1-150">타임스탬프의 유효 기간을 지정하는 <xref:System.TimeSpan>(양수)입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-150">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="abfd1-151">기본값은 "00:15:00"입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-151">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="abfd1-152">자식 요소</span><span class="sxs-lookup"><span data-stu-id="abfd1-152">Child Elements</span></span>  

 <span data-ttu-id="abfd1-153">없음</span><span class="sxs-lookup"><span data-stu-id="abfd1-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="abfd1-154">부모 요소</span><span class="sxs-lookup"><span data-stu-id="abfd1-154">Parent Elements</span></span>  
  
|<span data-ttu-id="abfd1-155">요소</span><span class="sxs-lookup"><span data-stu-id="abfd1-155">Element</span></span>|<span data-ttu-id="abfd1-156">설명</span><span class="sxs-lookup"><span data-stu-id="abfd1-156">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="abfd1-157">사용자 지정 바인딩에 대한 보안 옵션을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-157">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="abfd1-158">보안 대화 서비스 개시에 사용되는 기본값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-158">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abfd1-159">설명</span><span class="sxs-lookup"><span data-stu-id="abfd1-159">Remarks</span></span>  

 <span data-ttu-id="abfd1-160">설정은 서비스 보안 정책의 일부로 게시 되지 않으며 클라이언트의 바인딩에 영향을 주지 않으므로 로컬 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-160">The settings are local because they are not published as part of the security policy of the service and do not affect the client's binding.</span></span>  
  
 <span data-ttu-id="abfd1-161">`localServiceSecuritySettings` 요소의 다음 특성을 사용하면 DOS(서비스 거부) 보안 공격을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-161">The following attributes of the `localServiceSecuritySettings` element can help mitigate a denial-of-service (DOS) security attack:</span></span>  
  
- <span data-ttu-id="abfd1-162">`maxCachedCookies`: SPNEGO 또는 SSL 협상 후에 서버에서 캐시하는 시간 제한 SecurityContextToken의 최대 개수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-162">`maxCachedCookies`: controls the maximum number of time-bounded SecurityContextTokens that are cached by the server after doing SPNEGO or SSL negotiation.</span></span>  
  
- <span data-ttu-id="abfd1-163">`issuedCookieLifetime`: SPNEGO 또는 SSL 협상 후에 서버에서 발급하는 SecurityContextToken의 수명을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-163">`issuedCookieLifetime`: controls the lifetime of the SecurityContextTokens that are issued by the server following SPNEGO or SSL negotiation.</span></span> <span data-ttu-id="abfd1-164">서버는 이 기간 동안 SecurityContextToken을 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-164">The server caches the SecurityContextTokens for this period of time.</span></span>  
  
- <span data-ttu-id="abfd1-165">`maxPendingSessions`: 서버에서 설정되었지만 애플리케이션 메시지가 처리되지 않은 보안 대화의 최대 개수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-165">`maxPendingSessions`: controls the maximum number of secure conversations that are established at the server but for which no application messages have been processed.</span></span> <span data-ttu-id="abfd1-166">이 할당량은 클라이언트가 서비스에서 보안 대화를 설정할 수 없도록 하 여 서비스에서 각 클라이언트의 상태를 유지 하지만 사용 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-166">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
- <span data-ttu-id="abfd1-167">`inactivityTimeout`: 애플리케이션 메시지가 수신되지 않을 때 서비스에서 보안 대화를 활성 상태로 유지하는 최대 시간을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-167">`inactivityTimeout`: controls the maximum time that the service keeps a secure conversation alive without ever receiving an application message on it.</span></span> <span data-ttu-id="abfd1-168">이 할당량은 클라이언트가 서비스에서 보안 대화를 설정할 수 없도록 하 여 서비스에서 각 클라이언트의 상태를 유지 하지만 사용 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-168">This quota prevents clients from establishing secure conversations at the service, thereby causing the service to maintain state for each client, but never using them.</span></span>  
  
 <span data-ttu-id="abfd1-169">보안 대화 세션에서 바인딩의 `inactivityTimeout` 및 `receiveTimeout` 특성은 모두 세션 시간 제한에 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-169">In a secure conversation session, note that both `inactivityTimeout` and the `receiveTimeout` attributes on the binding affect session timeout.</span></span> <span data-ttu-id="abfd1-170">제한 시간은 두 속성 값 중 짧은 시간으로 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="abfd1-170">The shorter of the two determines when timeouts occur.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abfd1-171">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abfd1-171">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="abfd1-172">바인딩</span><span class="sxs-lookup"><span data-stu-id="abfd1-172">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="abfd1-173">바인딩 확장명</span><span class="sxs-lookup"><span data-stu-id="abfd1-173">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="abfd1-174">사용자 지정 바인딩</span><span class="sxs-lookup"><span data-stu-id="abfd1-174">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="abfd1-175">방법: SecurityBindingElement를 사용하여 사용자 지정 바인딩 만들기</span><span class="sxs-lookup"><span data-stu-id="abfd1-175">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="abfd1-176">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="abfd1-176">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
