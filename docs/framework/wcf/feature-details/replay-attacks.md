---
title: 재생 공격
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 4325b3747074f13cf02752f99b25fa02e4117b4c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239083"
---
# <a name="replay-attacks"></a><span data-ttu-id="ddc79-102">재생 공격</span><span class="sxs-lookup"><span data-stu-id="ddc79-102">Replay Attacks</span></span>

<span data-ttu-id="ddc79-103">공격자가 두 당사자 간에 메시지 스트림을 복사 하 고 하나 이상의 당사자에 게 스트림을 재생 하는 경우 *재생 공격이* 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-103">A *replay attack* occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="ddc79-104">완화되지 않은 경우 공격을 받기 쉬운 컴퓨터는 스트림을 올바른 메시지로 처리하여 항목에 대한 중복 주문과 같은 잘못된 결과의 범위에 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-104">Unless mitigated, the computers subject to the attack process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a><span data-ttu-id="ddc79-105">바인딩이 반사 공격을 받기 쉬운 경우</span><span class="sxs-lookup"><span data-stu-id="ddc79-105">Bindings May Be Subject to Reflection Attacks</span></span>  

 <span data-ttu-id="ddc79-106">*리플렉션 공격은* 메시지를 받는 사람에 게 회신으로 보낸 것 처럼 메시지를 다시 보낸 사람에 게 다시 재생 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-106">*Reflection attacks* are replays of messages back to a sender as if they came from the receiver as the reply.</span></span> <span data-ttu-id="ddc79-107">WCF (Windows Communication Foundation) 메커니즘에서 표준 *재생 검색* 은이를 자동으로 처리 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-107">The standard *replay detection* in the Windows Communication Foundation (WCF) mechanism does not automatically handle this.</span></span>  
  
 <span data-ttu-id="ddc79-108">WCF 서비스 모델은 메시지를 요청 하 고 응답 메시지에 서명 된 헤더를 필요로 하는 서명 된 메시지 ID를 추가 하기 때문에 기본적으로 리플렉션 공격이 완화 됩니다 `relates-to` .</span><span class="sxs-lookup"><span data-stu-id="ddc79-108">Reflection attacks are mitigated by default because the WCF service model adds a signed message ID to request messages and expects a signed `relates-to` header on response messages.</span></span> <span data-ttu-id="ddc79-109">따라서 요청 메시지를 응답으로 재생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-109">Consequently, the request message cannot be replayed as a response.</span></span> <span data-ttu-id="ddc79-110">보안 RM(신뢰할 수 있는 메시지) 시나리오에서 반사 공격은 다음과 같은 이유로 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-110">In secure reliable message (RM) scenarios, reflection attacks are mitigated because:</span></span>  
  
- <span data-ttu-id="ddc79-111">시퀀스 만들기 및 시퀀스 만들기 응답 메시지 스키마는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-111">The create sequence and create sequence response message schemas are different.</span></span>  
  
- <span data-ttu-id="ddc79-112">단면 시퀀스의 경우 클라이언트가 보내는 시퀀스 메시지는 클라이언트가 그러한 메시지를 인식할 수 없으므로 재생될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-112">For simplex sequences, sequence messages the client sends cannot be replayed back to it because the client cannot understand such messages.</span></span>  
  
- <span data-ttu-id="ddc79-113">이중 시퀀스의 경우 두 시퀀스 ID는 고유해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-113">For duplex sequences, the two sequence IDs must be unique.</span></span> <span data-ttu-id="ddc79-114">따라서 나가는 시퀀스 메시지를 들어오는 시퀀스 메시지로 재생할 수 없습니다(모든 시퀀스 헤더 및 본문도 서명됨).</span><span class="sxs-lookup"><span data-stu-id="ddc79-114">Thus, an outgoing sequence message cannot be replayed back as an incoming sequence message (all sequence headers and bodies are signed, too).</span></span>  
  
 <span data-ttu-id="ddc79-115">반사 공격을 받기 쉬운 바인딩은 WS-Addressing이 없는 바인딩 즉, WS-Addressing이 사용되지 않는 바인딩을 사용자 지정하고 대칭 키 기반 보안을 사용하는 바인딩입니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-115">The only bindings that are susceptible to reflection attacks are those without WS-Addressing: custom bindings that have WS-Addressing disabled and use the symmetric key-based security.</span></span> <span data-ttu-id="ddc79-116"><xref:System.ServiceModel.BasicHttpBinding>은 기본적으로 WS-Addressing을 사용하지 않지만, 이 공격에 노출될 수 있는 방식으로는 대칭 키 기반 보안을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-116">The <xref:System.ServiceModel.BasicHttpBinding> does not use WS-Addressing by default, but it does not use symmetric key-based security in a way that allows it to be vulnerable to this attack.</span></span>  
  
 <span data-ttu-id="ddc79-117">사용자 지정 바인딩을 완화하는 것은 보안 컨텍스트를 설정하지 않거나 WS-Addressing 헤더를 요청하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-117">The mitigation for custom bindings is to not establish security context or to require WS-Addressing headers.</span></span>  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a><span data-ttu-id="ddc79-118">웹 팜: 공격자가 여러 노드에 요청 재생</span><span class="sxs-lookup"><span data-stu-id="ddc79-118">Web Farm: Attacker Replays Request to Multiple Nodes</span></span>  

 <span data-ttu-id="ddc79-119">클라이언트는 웹 팜에 구현된 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-119">A client uses a service that is implemented on a Web farm.</span></span> <span data-ttu-id="ddc79-120">공격자는 팜의 한 노드로 보내진 요청을 팜의 다른 노드에 재생합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-120">An attacker replays a request that was sent to one node in the farm to another node in the farm.</span></span> <span data-ttu-id="ddc79-121">또한, 서비스를 다시 시작하는 경우 재생 캐시가 플러시되어 공격자가 요청을 재생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-121">In addition, if a service is restarted, the replay cache is flushed, allowing an attacker to replay the request.</span></span> <span data-ttu-id="ddc79-122">캐시에 이전에 사용된 메시지 서명 값이 있고 캐시가 재생되지 않으므로 그러한 서명은 한 번만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-122">(The cache contains used, previously seen message signature values and prevents replays so those signatures can be used only once.</span></span> <span data-ttu-id="ddc79-123">재생 캐시는 웹 팜에서 공유되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-123">Replay caches are not shared across a Web farm.)</span></span>  
  
 <span data-ttu-id="ddc79-124">완화 방안은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-124">Mitigations include:</span></span>  
  
- <span data-ttu-id="ddc79-125">상태 저장 보안 컨텍스트 토큰(보안 대화 사용 또는 사용 안 함)과 함께 메시지 모드 보안을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-125">Use message mode security with stateful security context tokens (with or without secure conversation enabled).</span></span> <span data-ttu-id="ddc79-126">자세한 내용은 [방법: 보안 세션에 대 한 보안 컨텍스트 토큰 만들기](how-to-create-a-security-context-token-for-a-secure-session.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ddc79-126">For more information, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
- <span data-ttu-id="ddc79-127">전송 수준 보안을 사용하도록 서비스를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="ddc79-127">Configure the service to use transport-level security.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddc79-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ddc79-128">See also</span></span>

- [<span data-ttu-id="ddc79-129">Security Considerations</span><span class="sxs-lookup"><span data-stu-id="ddc79-129">Security Considerations</span></span>](security-considerations-in-wcf.md)
- [<span data-ttu-id="ddc79-130">정보 공개</span><span class="sxs-lookup"><span data-stu-id="ddc79-130">Information Disclosure</span></span>](information-disclosure.md)
- [<span data-ttu-id="ddc79-131">권한 상승</span><span class="sxs-lookup"><span data-stu-id="ddc79-131">Elevation of Privilege</span></span>](elevation-of-privilege.md)
- [<span data-ttu-id="ddc79-132">서비스 거부</span><span class="sxs-lookup"><span data-stu-id="ddc79-132">Denial of Service</span></span>](denial-of-service.md)
- [<span data-ttu-id="ddc79-133">변조</span><span class="sxs-lookup"><span data-stu-id="ddc79-133">Tampering</span></span>](tampering.md)
- [<span data-ttu-id="ddc79-134">지원되지 않는 시나리오</span><span class="sxs-lookup"><span data-stu-id="ddc79-134">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
