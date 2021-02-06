---
description: '자세한 정보: 피어 채널 응용 프로그램 보안'
title: 피어 채널 애플리케이션 보안
ms.date: 03/30/2017
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
ms.openlocfilehash: cff94fe618ca25a6810d68efe8cb99b4316d95b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632661"
---
# <a name="securing-peer-channel-applications"></a><span data-ttu-id="0f515-103">피어 채널 애플리케이션 보안</span><span class="sxs-lookup"><span data-stu-id="0f515-103">Securing Peer Channel Applications</span></span>

<span data-ttu-id="0f515-104">WinFX의 다른 바인딩과 마찬가지로 `NetPeerTcpBinding` 은 기본적으로 보안을 사용 하도록 설정 하 고 전송 및 메시지 기반 보안 (또는 둘 다)을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-104">Like other bindings under the WinFX, `NetPeerTcpBinding` has security enabled by default and offers both transport- and message-based security (or both).</span></span> <span data-ttu-id="0f515-105">이 항목에서는 이러한 두 가지 보안 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-105">This topic discusses these two types of security.</span></span> <span data-ttu-id="0f515-106">보안 형식은 바인딩 사양의 보안 모드 태그(<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-106">The type of security is specified by the security mode tag in the binding specification (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).</span></span>  
  
## <a name="transport-based-security"></a><span data-ttu-id="0f515-107">전송 기반 보안</span><span class="sxs-lookup"><span data-stu-id="0f515-107">Transport-Based Security</span></span>  

 <span data-ttu-id="0f515-108">피어 채널은 전송 보안을 위한 두 가지 형식의 인증 자격 증명을 지원하며, 두 형식에서 모두 연결된 `ClientCredentialSettings.Peer`의 `ChannelFactory` 속성을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-108">Peer Channel supports two types of authentication credentials for securing transport, both of which require setting out the `ClientCredentialSettings.Peer` property on the associated `ChannelFactory`:</span></span>  
  
- <span data-ttu-id="0f515-109">Password.</span><span class="sxs-lookup"><span data-stu-id="0f515-109">Password.</span></span> <span data-ttu-id="0f515-110">클라이언트는 암호를 사용하여 연결을 인증합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-110">Clients use knowledge of a secret password to authenticate connections.</span></span> <span data-ttu-id="0f515-111">이 자격 증명 형식을 사용하는 경우 `ClientCredentialSettings.Peer.MeshPassword`에 올바른 암호와 선택적으로 `X509Certificate2` 인스턴스가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-111">When this credential type is used, `ClientCredentialSettings.Peer.MeshPassword` must carry a valid password and optionally an `X509Certificate2` instance.</span></span>  
  
- <span data-ttu-id="0f515-112">인증서</span><span class="sxs-lookup"><span data-stu-id="0f515-112">Certificate.</span></span> <span data-ttu-id="0f515-113">특정 애플리케이션 인증이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-113">Specific application authentication is used.</span></span> <span data-ttu-id="0f515-114">이 자격 증명 형식을 사용하는 경우 <xref:System.IdentityModel.Selectors.X509CertificateValidator>에서 `ClientCredentialSettings.Peer.PeerAuthentication`의 구체적 구현을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-114">When this credential type is used, you must use a concrete implementation of <xref:System.IdentityModel.Selectors.X509CertificateValidator> in `ClientCredentialSettings.Peer.PeerAuthentication`.</span></span>  
  
## <a name="message-based-security"></a><span data-ttu-id="0f515-115">메시지 기반 보안</span><span class="sxs-lookup"><span data-stu-id="0f515-115">Message-Based Security</span></span>  

 <span data-ttu-id="0f515-116">애플리케이션은 메시지 보안을 사용하여 보내는 메시지에 서명할 수 있습니다. 이 경우 모든 수신 당사자는 메시지가 신뢰할 수 있는 당사자에 의해 전송되었으며 메시지가 변조되지 않았음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-116">Using message security, an application can sign outgoing messages so that all receiving parties can verify the message is sent by a trusted party and that the message was not tampered with.</span></span> <span data-ttu-id="0f515-117">현재 피어 채널은 X.509 자격 증명 메시지 서명만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-117">Currently, Peer Channel supports only X.509 credential message signing.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="0f515-118">모범 사례</span><span class="sxs-lookup"><span data-stu-id="0f515-118">Best Practices</span></span>  
  
- <span data-ttu-id="0f515-119">이 단원에서는 피어 채널 애플리케이션에 보안을 설정하는 최선의 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-119">This section discusses the best practices for securing Peer Channel applications.</span></span>  
  
### <a name="enable-security-with-peer-channel-applications"></a><span data-ttu-id="0f515-120">피어 채널 애플리케이션을 사용하여 보안 설정</span><span class="sxs-lookup"><span data-stu-id="0f515-120">Enable Security with Peer Channel Applications</span></span>  

 <span data-ttu-id="0f515-121">피어 채널 프로토콜의 분산 특성 때문에 보안되지 않은 메시에서는 메시 멤버 자격, 기밀성 및 개인 정보를 적용하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-121">Due to the distributed nature of the Peer Channel protocols, it is hard to enforce mesh membership, confidentiality, and privacy in an unsecured mesh.</span></span> <span data-ttu-id="0f515-122">또한 클라이언트와 확인자 서비스 간에 통신 보안을 설정하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-122">It is also important to remember to secure communication between clients and the resolver service.</span></span> <span data-ttu-id="0f515-123">PNRP(Peer Name Resolution Protocol)에서 보안 이름을 사용하여 스푸핑 및 다른 일반적인 공격을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-123">Under Peer Name Resolution Protocol (PNRP), use secure names to avoid spoofing and other common attacks.</span></span> <span data-ttu-id="0f515-124">메시지 및 전송 기반 보안을 비롯하여 클라이언트가 확인자 서비스에 연결하는 데 사용하는 연결에 보안을 설정하여 사용자 지정 확인자 서비스에 보안을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-124">Secure a custom resolver service by enabling security on the connection clients use to contact the resolver service, including both message- and transport-based security.</span></span>  
  
### <a name="use-the-strongest-possible-security-model"></a><span data-ttu-id="0f515-125">가장 강력한 보안 모델 사용</span><span class="sxs-lookup"><span data-stu-id="0f515-125">Use the Strongest Possible Security Model</span></span>  

 <span data-ttu-id="0f515-126">예를 들어 메시의 각 멤버를 개별적으로 식별해야 하는 경우 인증서 기반 인증 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-126">For example, if each member of the mesh needs to be individually identified, use certificate-based authentication model.</span></span> <span data-ttu-id="0f515-127">사용할 수 없는 경우 현재 권장 사항에 따라 암호 기반 인증을 사용하여 보안을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-127">If that is not possible, use password-based authentication following current recommendations to keep them secure.</span></span> <span data-ttu-id="0f515-128">여기에는 신뢰할 수 있는 당사자하고만 암호 공유, 보안 매체를 사용하여 암호 전송, 자주 암호 변경, 강력한 암호(8자 이상으로 대/소문자의 한 문자 이상, 숫자 및 특수 문자 포함) 사용이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-128">This includes sharing passwords only with trusted parties, transmitting passwords using a secure medium, changing passwords frequently, and ensuring that passwords are strong (at least eight characters long, include at least one letter from both cases, a digit, and a special character).</span></span>  
  
### <a name="never-accept-self-signed-certificates"></a><span data-ttu-id="0f515-129">자체 서명된 인증서 허용 안 함</span><span class="sxs-lookup"><span data-stu-id="0f515-129">Never Accept Self-Signed Certificates</span></span>  

 <span data-ttu-id="0f515-130">주체 이름을 기반으로 인증서 자격 증명을 허용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="0f515-130">Never accept a certificate credential based on subject names.</span></span> <span data-ttu-id="0f515-131">누구든지 인증서를 만들 수 있으며 누구든지 유효성이 확인되는 이름을 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-131">Note that anyone can create a certificate, and anyone can choose a name that you are validating.</span></span> <span data-ttu-id="0f515-132">스푸핑을 방지하려면 발급 기관 자격 증명(신뢰할 수 있는 발급자 또는 루트 인증 기관)을 기반으로 인증서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-132">To avoid the possibility of spoofing, validate certificates based on issuing authority credentials (either a trusted issuer or a root certification authority).</span></span>  
  
### <a name="use-message-authentication"></a><span data-ttu-id="0f515-133">메시지 인증 사용</span><span class="sxs-lookup"><span data-stu-id="0f515-133">Use Message Authentication</span></span>  

 <span data-ttu-id="0f515-134">메시지 인증을 사용하여 신뢰할 수 있는 소스에서 메시지가 시작되었으며 전송 중에 메시지를 변조한 사람이 없음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-134">Use message authentication to verify that a message originated from a trusted source and that no one has tampered with the message during transmission.</span></span> <span data-ttu-id="0f515-135">메시지 인증을 사용하지 않으면 악성 클라이언트가 메시의 메시지를 쉽게 스푸핑하거나 변조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0f515-135">Without message authentication, it is easy for a malicious client to spoof or tamper with messages in the mesh.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="0f515-136">피어 채널 코드 예제</span><span class="sxs-lookup"><span data-stu-id="0f515-136">Peer Channel Code Examples</span></span>  

 [<span data-ttu-id="0f515-137">피어 채널 시나리오</span><span class="sxs-lookup"><span data-stu-id="0f515-137">Peer Channel Scenarios</span></span>](peer-channel-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="0f515-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0f515-138">See also</span></span>

- [<span data-ttu-id="0f515-139">피어 채널 보안</span><span class="sxs-lookup"><span data-stu-id="0f515-139">Peer Channel Security</span></span>](peer-channel-security.md)
- [<span data-ttu-id="0f515-140">피어 채널 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="0f515-140">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
