---
title: '방법: 메시지 재생 검색 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 4a4d304a1316fe534e09f02ac1cd2900bf798011
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265533"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="084b8-102">방법: 메시지 재생 검색 사용</span><span class="sxs-lookup"><span data-stu-id="084b8-102">How to: Enable Message Replay Detection</span></span>

<span data-ttu-id="084b8-103">공격자가 두 당사자 간에 메시지 스트림을 복사하고 하나 이상의 당사자에게 스트림을 재생하는 경우 재생 공격이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="084b8-104">완화되지 않은 경우 공격을 받기 쉬운 컴퓨터는 스트림을 올바른 메시지로 처리하여 항목에 대한 중복 주문과 같은 잘못된 결과의 범위에 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="084b8-105">메시지 재생 검색에 대 한 자세한 내용은 [메시지 재생 검색](/previous-versions/msp-n-p/ff649371(v=pandp.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="084b8-105">For more information about message replay detection, see [Message Replay Detection](/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="084b8-106">다음 절차에서는 Windows Communication Foundation (WCF)를 사용 하 여 재생 검색을 제어 하는 데 사용할 수 있는 다양 한 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="084b8-107">코드를 사용하여 클라이언트에서 재생 검색을 제어하려면</span><span class="sxs-lookup"><span data-stu-id="084b8-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="084b8-108"><xref:System.ServiceModel.Channels.SecurityBindingElement>에서 사용할 <xref:System.ServiceModel.Channels.CustomBinding>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="084b8-109">자세한 내용은 [방법: SecurityBindingElement를 사용 하 여 사용자 지정 바인딩 만들기](how-to-create-a-custom-binding-using-the-securitybindingelement.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="084b8-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="084b8-110">다음 예제에서는 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 클래스의 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>를 사용하여 만든 <xref:System.ServiceModel.Channels.SecurityBindingElement>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="084b8-111"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> 속성을 사용하여 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> 클래스에 대한 참조를 반환하고 다음 속성을 적절히 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="084b8-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="084b8-112">`DetectReplay`.</span></span> <span data-ttu-id="084b8-113">부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-113">A Boolean value.</span></span> <span data-ttu-id="084b8-114">이 값은 클라이언트가 서버로부터 재생을 검색해야 하는지 여부를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="084b8-115">기본값은 `true`입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="084b8-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="084b8-116">`MaxClockSkew`.</span></span> <span data-ttu-id="084b8-117"><xref:System.TimeSpan> 값입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="084b8-118">재생 메커니즘이 클라이언트와 서버 간에 허용하는 오차 횟수를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="084b8-119">보안 메커니즘은 보낸 타임스탬프를 검사하고 보낸 시간이 아주 오래되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="084b8-120">기본값은 5분입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="084b8-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="084b8-121">`ReplayWindow`.</span></span> <span data-ttu-id="084b8-122">`TimeSpan` 값입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-122">A `TimeSpan` value.</span></span> <span data-ttu-id="084b8-123">이 값은 매개자를 통해 서버에서 메시지를 보낸 후 클라이언트에 도달하기까지 메시지가 네트워크에 있을 수 있는 시간을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="084b8-124">클라이언트는 재생 검색을 위해 최신 `ReplayWindow` 내에서 보낸 메시지 서명을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="084b8-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="084b8-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="084b8-126">정수 값입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-126">An integer value.</span></span> <span data-ttu-id="084b8-127">클라이언트는 캐시에 메시지 서명을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="084b8-128">이 설정은 캐시에서 저장할 수 있는 서명 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="084b8-129">최신 재생 창 내에서 보낸 메시지 수가 캐시 한계에 도달하면 가장 오래 전에 캐시된 서명이 시간 제한에 도달할 때까지 새 메시지가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="084b8-130">기본값은 50만입니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="084b8-131">코드를 사용하여 서비스에서 재생 검색을 제어하려면</span><span class="sxs-lookup"><span data-stu-id="084b8-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="084b8-132"><xref:System.ServiceModel.Channels.SecurityBindingElement>에서 사용할 <xref:System.ServiceModel.Channels.CustomBinding>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="084b8-133"><xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> 속성을 사용하여 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> 클래스에 대한 참조를 반환하고 앞에서 설명한 대로 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="084b8-134">클라이언트나 서비스에 대한 구성에서 재생 검색을 제어하려면</span><span class="sxs-lookup"><span data-stu-id="084b8-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="084b8-135">을 만듭니다 [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="084b8-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="084b8-136">`<security>` 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="084b8-137">또는를 [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) 만듭니다 [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="084b8-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="084b8-138">`detectReplays`, `maxClockSkew`, `replayWindow` 및 `replayCacheSize` 특성 값을 적절히 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="084b8-139">다음 예제에서는 `<localServiceSettings>` 요소 모두의 특성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings
          replayCacheSize="800000"
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="084b8-140">예제</span><span class="sxs-lookup"><span data-stu-id="084b8-140">Example</span></span>  

 <span data-ttu-id="084b8-141">다음 예제에서는 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 메서드를 사용하여 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>를 만들고 바인딩의 재생 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="084b8-142">재생 범위: 메시지 보안만</span><span class="sxs-lookup"><span data-stu-id="084b8-142">Scope of Replay: Message Security Only</span></span>  

 <span data-ttu-id="084b8-143">다음 프로시저는 메시지 보안 모드에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="084b8-144">전송 모드 및 메시지 자격 증명을 사용한 전송 모드에서 전송 메커니즘은 재생을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="084b8-145">보안 대화 참고 사항</span><span class="sxs-lookup"><span data-stu-id="084b8-145">Secure Conversation Notes</span></span>  

 <span data-ttu-id="084b8-146">보안 대화를 사용하는 바인딩에서 보안 대화 부트스트랩 바인딩뿐만 아니라 애플리케이션 채널에 대해 이러한 설정을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="084b8-147">예를 들면 애플리케이션 채널에 대해 재생을 해제할 수 있지만 보안 대화를 설정하는 부트스트랩 채널에 대해서는 재생을 사용하도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="084b8-148">보안 대화 세션을 사용하지 않는 경우에는 서버 팜 시나리오에서, 그리고 프로세스가 재활용되는 경우 재생 검색이 작동하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="084b8-149">이 내용은 다음과 같은 시스템 제공 바인딩에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="084b8-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="084b8-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="084b8-151"><xref:System.ServiceModel.WSHttpBinding> 속성이 <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A>로 설정된 `false`</span><span class="sxs-lookup"><span data-stu-id="084b8-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="084b8-152">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="084b8-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="084b8-153">코드를 컴파일하려면 다음 네임스페이스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="084b8-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="084b8-154">참고 항목</span><span class="sxs-lookup"><span data-stu-id="084b8-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="084b8-155">보안 대화 및 보안 세션</span><span class="sxs-lookup"><span data-stu-id="084b8-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="084b8-156">방법: SecurityBindingElement를 사용하여 사용자 지정 바인딩 만들기</span><span class="sxs-lookup"><span data-stu-id="084b8-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
