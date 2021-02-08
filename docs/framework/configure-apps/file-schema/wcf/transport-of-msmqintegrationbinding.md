---
description: '다음에 대 한 자세한 정보:: <transport><msmqIntegrationBinding>'
title: <msmqIntegrationBinding>의 <transport>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: bcca714320f333a16d518248531efe8039ff566e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99773526"
---
# <a name="transport-of-msmqintegrationbinding"></a><span data-ttu-id="232d9-103">\<msmqIntegrationBinding>의 \<transport></span><span class="sxs-lookup"><span data-stu-id="232d9-103">\<transport> of \<msmqIntegrationBinding></span></span>

<span data-ttu-id="232d9-104">메시지 큐 통합 전송을 위한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-104">Defines the security settings for the Message Queuing integration transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<msmqIntegrationBinding>**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="232d9-105">구문</span><span class="sxs-lookup"><span data-stu-id="232d9-105">Syntax</span></span>  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="232d9-106">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="232d9-106">Attributes and Elements</span></span>  

 <span data-ttu-id="232d9-107">다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="232d9-108">특성</span><span class="sxs-lookup"><span data-stu-id="232d9-108">Attributes</span></span>  
  
|<span data-ttu-id="232d9-109">attribute</span><span class="sxs-lookup"><span data-stu-id="232d9-109">Attribute</span></span>|<span data-ttu-id="232d9-110">설명</span><span class="sxs-lookup"><span data-stu-id="232d9-110">Description</span></span>|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|<span data-ttu-id="232d9-111">메시지가 MSMQ 전송에 의해 인증되는 방법을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-111">Specifies how the message must be authenticated by the MSMQ transport.</span></span> <span data-ttu-id="232d9-112">이 특성이 `None`으로 설정되면 `msmqProtectionLevel` 특성 값도 `None`으로 설정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-112">If this is set to `None`, the value of the `msmqProtectionLevel` attribute must also be set to `None`.</span></span><br /><br /> <span data-ttu-id="232d9-113">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-113">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="232d9-114">-없음: 인증 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-114">-   None: No authentication.</span></span><br /><span data-ttu-id="232d9-115">-WindowsDomain:이 인증 메커니즘은 Active Directory를 사용 하 여 메시지와 연결 된 SID에 대 한 x.509 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-115">-   WindowsDomain: The authentication mechanism uses Active Directory to get the X.509 certificate for the SID associated with the message.</span></span> <span data-ttu-id="232d9-116">그런 다음 이 인증서는 사용자에게 큐에 대한 쓰기 권한이 있는지 확인하기 위해 큐의 ACL을 검사하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-116">This is then used to check the ACL of the queue to ensure the user has permission to write to the queue.</span></span><br /><span data-ttu-id="232d9-117">-Certificate: 채널은 인증서 저장소에서 인증서를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-117">-   Certificate: The channel gets the certificate from the certificate store.</span></span><br /><br /> <span data-ttu-id="232d9-118">기본값은 WindowsDomain입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-118">The default value is WindowsDomain.</span></span> <span data-ttu-id="232d9-119">이 특성은 <xref:System.ServiceModel.MsmqAuthenticationMode> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-119">This attribute is of type <xref:System.ServiceModel.MsmqAuthenticationMode>.</span></span>|  
|`msmqEncryptionAlgorithm`|<span data-ttu-id="232d9-120">메시지 큐 관리자 간에 메시지를 전송할 때 통신 중에 메시지 암호화에 사용할 알고리즘을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-120">Specifies the algorithm to be used for message encryption on the wire when transferring messages between message queue managers.</span></span> <span data-ttu-id="232d9-121">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="232d9-122">-RC4Stream</span><span class="sxs-lookup"><span data-stu-id="232d9-122">-   RC4Stream</span></span><br /><span data-ttu-id="232d9-123">-AES</span><span class="sxs-lookup"><span data-stu-id="232d9-123">-   AES</span></span><br /><br /> <span data-ttu-id="232d9-124">기본값은 RC4Stream입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-124">The default value is RC4Stream.</span></span> <span data-ttu-id="232d9-125">이 특성은 <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-125">This attribute is of type <xref:System.ServiceModel.MsmqEncryptionAlgorithm>.</span></span>|  
|`msmqProtectionLevel`|<span data-ttu-id="232d9-126">메시지가 MSMQ 전송 수준에서 보호되는 방식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-126">Specifies how the message is secured at the level of the MSMQ transport.</span></span> <span data-ttu-id="232d9-127">암호화는 메시지 무결성을 보장 하는 반면 EncryptAndSign는 메시지 무결성 및 부인 방지를 모두 보장 합니다. 즉, 메시지는 보낸 사람 으로부터 전송 되 고 보낸 사람은 보낸 사람입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-127">Encryption ensures message integrity while EncryptAndSign ensures both message integrity and non-repudiation; that is, the message indeed comes from the sender and the sender is who they say they are.</span></span><br /><br /> <span data-ttu-id="232d9-128">-유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-128">-   Valid values include the following:</span></span><br /><span data-ttu-id="232d9-129">-없음: 보호 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-129">-   None: No protection.</span></span><br /><span data-ttu-id="232d9-130">-서명: 메시지가 서명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-130">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="232d9-131">-EncryptAndSign: 메시지가 암호화 되 고 서명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-131">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="232d9-132">기본값은 Sign입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-132">The default value is Sign.</span></span> <span data-ttu-id="232d9-133">이 특성은 ProtectionLevel 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-133">This attribute is of type ProtectionLevel.</span></span>|  
|`msmqSecureHashAlgorithm`|<span data-ttu-id="232d9-134">-시그니처의 일부로 다이제스트를 계산 하는 데 사용할 알고리즘을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-134">-   Specifies the algorithm to be used in computing the digest as part of signatures.</span></span> <span data-ttu-id="232d9-135">유효한 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-135">Valid values include the following:</span></span><br /><span data-ttu-id="232d9-136">-MD5</span><span class="sxs-lookup"><span data-stu-id="232d9-136">-   MD5</span></span><br /><span data-ttu-id="232d9-137">-SHA1</span><span class="sxs-lookup"><span data-stu-id="232d9-137">-   SHA1</span></span><br /><span data-ttu-id="232d9-138">-SHA256</span><span class="sxs-lookup"><span data-stu-id="232d9-138">-   SHA256</span></span><br /><span data-ttu-id="232d9-139">-SHA512</span><span class="sxs-lookup"><span data-stu-id="232d9-139">-   SHA512</span></span><br /><br /> <span data-ttu-id="232d9-140">기본값은 SHA1입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-140">The default value is SHA1.</span></span> <span data-ttu-id="232d9-141">이 특성은 <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-141">This attribute is of type <xref:System.ServiceModel.MsmqSecureHashAlgorithm>.</span></span><br><span data-ttu-id="232d9-142">MD5 및 s h a 1의 충돌 문제로 인해 s h a 1 이상을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-142">Due to collision problems with MD5 and SHA1, Microsoft recommends SHA256 or better.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="232d9-143">자식 요소</span><span class="sxs-lookup"><span data-stu-id="232d9-143">Child Elements</span></span>  

 <span data-ttu-id="232d9-144">없음</span><span class="sxs-lookup"><span data-stu-id="232d9-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="232d9-145">부모 요소</span><span class="sxs-lookup"><span data-stu-id="232d9-145">Parent Elements</span></span>  
  
|<span data-ttu-id="232d9-146">요소</span><span class="sxs-lookup"><span data-stu-id="232d9-146">Element</span></span>|<span data-ttu-id="232d9-147">설명</span><span class="sxs-lookup"><span data-stu-id="232d9-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="232d9-148">MSMQ 바인딩에 대한 보안 설정을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-148">Defines the security settings for a MSMQ binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="232d9-149">설명</span><span class="sxs-lookup"><span data-stu-id="232d9-149">Remarks</span></span>  

 <span data-ttu-id="232d9-150">이 요소는 메시지 큐 통합 전송을 위한 보안 설정을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-150">This element encapsulates the security settings for the Message Queuing integration transport.</span></span> <span data-ttu-id="232d9-151">설정은 메시지 큐 통합 및 대기 중인 전송에서 모두 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-151">The settings are the same for both the Message Queuing integration and queued transports.</span></span> <span data-ttu-id="232d9-152">이 요소를 사용하여 인증 모드, 암호화 알고리즘, 보안 해시 알고리즘 및 보호 수준을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="232d9-152">It enables you to set the Authentication Mode, Encryption Algorithm, Secure Hash Algorithm, and Protection Level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232d9-153">참고 항목</span><span class="sxs-lookup"><span data-stu-id="232d9-153">See also</span></span>

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [<span data-ttu-id="232d9-154">서비스 및 클라이언트에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="232d9-154">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="232d9-155">바인딩</span><span class="sxs-lookup"><span data-stu-id="232d9-155">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="232d9-156">시스템 제공 바인딩 구성</span><span class="sxs-lookup"><span data-stu-id="232d9-156">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="232d9-157">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="232d9-157">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
