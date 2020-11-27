---
title: 신뢰할 수 있는 서비스
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: d028af80a30fd18b6aa6e9678e7fd8788e7b7b95
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249750"
---
# <a name="reliable-services"></a><span data-ttu-id="22a78-102">신뢰할 수 있는 서비스</span><span class="sxs-lookup"><span data-stu-id="22a78-102">Reliable Services</span></span>

<span data-ttu-id="22a78-103">큐 및 신뢰할 수 있는 세션은 신뢰할 수 있는 메시징을 구현 하는 WCF (Windows Communication Foundation) 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-103">Queues and reliable sessions are the Windows Communication Foundation (WCF) features that implement reliable messaging.</span></span> <span data-ttu-id="22a78-104">이 항목에서는 WCF의 신뢰할 수 있는 메시징 기능에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-104">This topic explains the reliable messaging features of WCF.</span></span>  
  
 <span data-ttu-id="22a78-105">안정적인 메시징은 신뢰할 수 있는 메시징 원본 ( *원본* *)이 신뢰할* 수 있는 메시징 대상 ( *대상* 이라고 함)에 메시지를 안정적으로 전송 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-105">*Reliable messaging* is how a reliable messaging source (called the *source*) transfers messages reliably to a reliable messaging destination (called the *destination*).</span></span>  
  
 <span data-ttu-id="22a78-106">신뢰할 수 있는 메시징에서는 다음 기능을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-106">Reliable messaging performs the following functions:</span></span>  
  
- <span data-ttu-id="22a78-107">메시지 전송 또는 전송 실패와 상관없이 소스에서 대상으로 보낸 메시지에 대한 보증을 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-107">Transfers assurances for messages sent from a source to a destination regardless of message transfer or transport failures.</span></span>  
  
- <span data-ttu-id="22a78-108">소스와 대상을 서로 분리합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-108">Separates the source and the destination from each other.</span></span> <span data-ttu-id="22a78-109">따라서 소스 및 대상의 실패와 복구를 따로 관리할 수 있으며 소스나 대상을 사용할 수 없는 경우라도 메시지를 안전하게 전송 및 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-109">This provides independent failure and recovery of the source and the destination, as well as reliable transfer and delivery of messages, even when the source or destination is unavailable.</span></span>  
  
 <span data-ttu-id="22a78-110">하지만 신뢰할 수 있는 메시징에는 대기 시간이 길다는 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-110">Reliable messaging frequently comes at the cost of high latency.</span></span> <span data-ttu-id="22a78-111">*대기 시간은* 메시지가 원본에서 대상에 도달 하는 데 걸리는 시간입니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-111">*Latency* is the time it takes for the message to reach the destination from the source.</span></span> <span data-ttu-id="22a78-112">따라서 WCF는 다음과 같은 종류의 신뢰할 수 있는 메시징을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-112">WCF, therefore, provides the following types of reliable messaging:</span></span>  
  
- <span data-ttu-id="22a78-113">안정적인 [세션](./feature-details/reliable-sessions.md)은 대기 시간이 긴 경우를 제외 하 고 신뢰할 수 있는 전송을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-113">[Reliable Sessions](./feature-details/reliable-sessions.md), which offers reliable transfer without the cost of high latency.</span></span>  
  
- <span data-ttu-id="22a78-114">원본 및 대상 간의 분리 및 분리를 모두 제공 하는 [WCF의 큐](./feature-details/queues-in-wcf.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-114">[Queues in WCF](./feature-details/queues-in-wcf.md), which offers both reliable transfers and separation between the source and the destination.</span></span>  
  
## <a name="reliable-sessions"></a><span data-ttu-id="22a78-115">신뢰할 수 있는 세션</span><span class="sxs-lookup"><span data-stu-id="22a78-115">Reliable Sessions</span></span>  

 <span data-ttu-id="22a78-116">신뢰할 수 있는 세션에서는 메시징 엔드포인트(소스와 대상)를 분리하는 매개자의 형식이나 개수에 상관없이, WS-Reliable Messaging 프로토콜을 사용하여 소스와 대상 간의 안전한 엔드투엔드 메시지 전송을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-116">Reliable sessions provide end-to-end reliable transfer of messages between a source and a destination using the WS-Reliable Messaging protocol, regardless of the number or type of intermediaries that separate the messaging (source and destination) endpoints.</span></span> <span data-ttu-id="22a78-117">여기에는 엔드포인트 간의 메시지 흐름에 필요한, SOAP를 사용하지 않는 전송 매개자(예: HTTP 프록시) 또는 SOAP를 사용하는 매개자(예: SOAP 기반 라우터나 브리지)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-117">This includes any transport intermediaries that do not use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="22a78-118">전송에 실패한 경우 신뢰할 수 있는 세션은 메모리 내 전송 창을 사용하여 SOAP 메시지 수준 오류를 마스킹하고 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-118">Reliable sessions use an in-memory transfer window to mask SOAP message-level failures and re-establish connections in the case of transport failures.</span></span>  
  
 <span data-ttu-id="22a78-119">신뢰할 수 있는 세션은 대기 시간이 짧은 안전한 메시지 전송을 제공하며,</span><span class="sxs-lookup"><span data-stu-id="22a78-119">Reliable sessions provide low-latency reliable message transfers.</span></span> <span data-ttu-id="22a78-120">TCP가 IP 브리지를 통해 패킷을 지원하는 것과 같이, 프록시나 매개자를 통해 SOAP 메시지를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-120">They provide for SOAP messages over any proxies or intermediaries, equivalent to what TCP provides for packets over IP bridges.</span></span> <span data-ttu-id="22a78-121">신뢰할 수 있는 세션에 대 한 자세한 내용은 [신뢰할 수 있는 세션](./feature-details/reliable-sessions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="22a78-121">For more information about reliable sessions, see [Reliable Sessions](./feature-details/reliable-sessions.md).</span></span>  
  
### <a name="queues"></a><span data-ttu-id="22a78-122">큐</span><span class="sxs-lookup"><span data-stu-id="22a78-122">Queues</span></span>  

 <span data-ttu-id="22a78-123">WCF의 큐는 메시지를 안정적으로 전송 하 고, 원본과 대상 간의 분리를 제공 하 여 대기 시간이 깁니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-123">Queues in WCF provide both reliable transfers of messages and separation between sources and destinations at the cost of high latency.</span></span> <span data-ttu-id="22a78-124">WCF 대기 중인 통신은 MSMQ (메시지 큐)를 기반으로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-124">WCF queued communication is built on top of Message Queuing (MSMQ).</span></span>  
  
 <span data-ttu-id="22a78-125">MSMQ는 Windows의 선택적 구성 요소로 제공되며</span><span class="sxs-lookup"><span data-stu-id="22a78-125">MSMQ ships as an optional component with Windows.</span></span> <span data-ttu-id="22a78-126">MSMQ 서비스는 Windows 서비스로 실행되고,</span><span class="sxs-lookup"><span data-stu-id="22a78-126">The MSMQ service runs as a Windows Service.</span></span> <span data-ttu-id="22a78-127">소스 대신 전송 큐에서 전송할 메시지를 캡처하여 대상 큐로 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-127">It captures messages for transmission in a transmission queue on behalf of the source and delivers it to a target queue.</span></span> <span data-ttu-id="22a78-128">대상 큐는 대상을 대신해 메시지를 수락하고 나중에 대상에서 메시지를 요청할 때 배달합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-128">The target queue accepts messages on behalf of the destination for later delivery whenever the destination requests messages.</span></span> <span data-ttu-id="22a78-129">MSMQ 관리자는 전송 중에 메시지가 손실되지 않도록 안전한 메시지 전송 프로토콜을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-129">The MSMQ managers implement a reliable message-transfer protocol so that messages are not lost in transmission.</span></span> <span data-ttu-id="22a78-130">이러한 프로토콜에는 네이티브 프로토콜 또는 SRMP(SOAP Reliable Messaging Protocol)라고 하는 SOAP 기반 프로토콜이 해당됩니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-130">The protocol can be native or a SOAP-based protocol called SOAP Reliable Messaging Protocol (SRMP).</span></span>  
  
 <span data-ttu-id="22a78-131">큐 간의 안전한 메시지 전송과 결합된 분리를 통해, 느슨하게 결합된 애플리케이션이 안전하게 통신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-131">The separation, coupled with reliable message transfers between queues, enables applications that are loosely coupled to communicate reliably.</span></span> <span data-ttu-id="22a78-132">신뢰할 수 있는 세션과 달리 소스와 대상은 동시에 실행될 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-132">Unlike reliable sessions, the source and destination do not have to be running at the same time.</span></span> <span data-ttu-id="22a78-133">따라서 소스의 메시지 생산율과 대상의 메시지 소비율이 맞지 않을 경우, 큐가 부하 평준화 메커니즘으로 효과적으로 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22a78-133">This implicitly enables scenarios where queues are, in effect, used as a load-leveling mechanism when the source's rate of message production and the destination's rate of the message consumption do not match.</span></span> <span data-ttu-id="22a78-134">큐에 대 한 자세한 내용은 [WCF의 큐](./feature-details/queues-in-wcf.md)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="22a78-134">For more information about queues, see [Queues in WCF](./feature-details/queues-in-wcf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22a78-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22a78-135">See also</span></span>

- [<span data-ttu-id="22a78-136">신뢰할 수 있는 세션 개요</span><span class="sxs-lookup"><span data-stu-id="22a78-136">Reliable Sessions Overview</span></span>](./feature-details/reliable-sessions-overview.md)
- [<span data-ttu-id="22a78-137">WCF의 큐</span><span class="sxs-lookup"><span data-stu-id="22a78-137">Queuing in WCF</span></span>](./feature-details/queuing-in-wcf.md)
