---
description: '자세히 알아보기: 방법: 최대 클럭 오차 설정'
title: '방법: 최대 클럭 오차 설정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 688be1bb42dd7b30fce577082992741b76819e3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643204"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="2d0f7-103">방법: 최대 클럭 오차 설정</span><span class="sxs-lookup"><span data-stu-id="2d0f7-103">How to: Set a Max Clock Skew</span></span>

<span data-ttu-id="2d0f7-104">두 개의 컴퓨터에서 클록 설정이 서로 다른 경우 시간 중심 기능이 비활성화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-104">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="2d0f7-105">이 가능성을 줄이기 위해 `MaxClockSkew` 설정을 <xref:System.TimeSpan>으로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-105">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="2d0f7-106">이 속성은 다음 두 개의 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-106">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="2d0f7-107">보안 대화의 경우 `MaxClockSkew` 서비스 또는 클라이언트가 부트스트랩 되 면 속성을 변경 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-107">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="2d0f7-108">이렇게 하려면 속성에서 반환 된에 대 한 속성을 설정 해야 합니다 <xref:System.ServiceModel.Channels.SecurityBindingElement> <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2d0f7-108">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="2d0f7-109">시스템 제공 바인딩 중 하나에서 속성을 변경하려면 바인딩 컬렉션에서 보안 바인딩 요소를 찾아 `MaxClockSkew` 속성을 새 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-109">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="2d0f7-110">두 개의 클래스는 <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 및 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>에서 파생됩니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-110">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="2d0f7-111">컬렉션에서 보안 바인딩을 검색하는 경우 `MaxClockSkew` 속성을 제대로 설정하기 위해 이러한 형식 중 하나를 캐스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-111">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="2d0f7-112">다음 예제에서는 <xref:System.ServiceModel.WSHttpBinding>를 사용하는 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-112">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="2d0f7-113">각 시스템 제공 바인딩에 사용할 보안 바인딩 형식을 지정 하는 목록은 [시스템 제공 바인딩](../system-provided-bindings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-113">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="2d0f7-114">코드에서 새 클럭 오차 값으로 사용자 지정 바인딩을 만들려면</span><span class="sxs-lookup"><span data-stu-id="2d0f7-114">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2d0f7-115">코드에서,, 및 네임 스페이스에 대 한 참조를 추가 <xref:System.ServiceModel.Channels> <xref:System.ServiceModel.Description> <xref:System.Security.Permissions> <xref:System.ServiceModel.Security.Tokens> 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-115">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="2d0f7-116"><xref:System.ServiceModel.WSHttpBinding> 클래스의 인스턴스를 만들고 보안 모드를 <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-116">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="2d0f7-117"><xref:System.ServiceModel.Channels.BindingElementCollection> 메서드를 호출하여 <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> 클래스의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-117">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="2d0f7-118"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 클래스의 <xref:System.ServiceModel.Channels.BindingElementCollection> 메서드를 사용하여 보안 바인딩 요소를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-118">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="2d0f7-119"><xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> 메서드를 사용하는 경우 실제 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-119">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="2d0f7-120">아래 예제에서는 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> 형식으로 캐스팅합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-120">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="2d0f7-121">보안 바인딩 요소에서 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-121">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="2d0f7-122">적절한 서비스 형식 및 기본 주소로 <xref:System.ServiceModel.ServiceHost>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-122">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="2d0f7-123">ph x="1" /&gt; 메서드를 사용하여 엔드포인트를 추가하고 <xref:System.ServiceModel.Channels.CustomBinding>을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-123">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="2d0f7-124">구성에서 MaxClockSkew를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2d0f7-124">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="2d0f7-125">[\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md)요소 섹션에서를 만듭니다 [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="2d0f7-125">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="2d0f7-126">요소를 만들고 [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) `name` 특성을 적절 한 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-126">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="2d0f7-127">다음 예제에서는 이 특성을 `MaxClockSkewBinding`으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-127">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="2d0f7-128">인코딩 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-128">Add an encoding element.</span></span> <span data-ttu-id="2d0f7-129">아래 예제에서는를 추가 [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-129">The example below adds a [\<textMessageEncoding>](../../configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="2d0f7-130">요소를 추가 하 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) 고 `authenticationMode` 특성을 적절 한 설정으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-130">Add a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="2d0f7-131">다음 예제에서는 특성을 `Kerberos`로 설정하여 서비스가 Windows 인증을 사용하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-131">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="2d0f7-132">를 추가 [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) 하 고 `maxClockSkew` 특성을 형식의 값으로 설정 합니다 `"##:##:##"` .</span><span class="sxs-lookup"><span data-stu-id="2d0f7-132">Add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="2d0f7-133">다음 예제에서는 이 특성을 7분으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-133">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="2d0f7-134">필요에 따라를 추가 하 [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) 고 `maxClockSkew` 특성을 적절 한 설정으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-134">Optionally, add a [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="2d0f7-135">전송 요소를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-135">Add a transport element.</span></span> <span data-ttu-id="2d0f7-136">다음 예제에서는를 사용 [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="2d0f7-136">The following example uses an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="2d0f7-137">보안 대화의 경우 보안 설정이 요소의 부트스트랩에서 발생 해야 합니다 [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="2d0f7-137">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2d0f7-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2d0f7-138">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="2d0f7-139">방법: SecurityBindingElement를 사용하여 사용자 지정 바인딩 만들기</span><span class="sxs-lookup"><span data-stu-id="2d0f7-139">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
