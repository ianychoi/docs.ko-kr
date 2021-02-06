---
description: '자세한 정보: 신뢰할 수 있는 세션 개요'
title: 신뢰할 수 있는 세션 개요
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 51de6012245b4fc0a367069d02fe69ee031f2b30
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99632895"
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="88ea2-103">신뢰할 수 있는 세션 개요</span><span class="sxs-lookup"><span data-stu-id="88ea2-103">Reliable Sessions Overview</span></span>

<span data-ttu-id="88ea2-104">WCF (Windows Communication Foundation) SOAP 신뢰할 수 있는 메시징은 SOAP 끝점 간의 종단 간 메시지 전송 안정성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-104">Windows Communication Foundation (WCF) SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="88ea2-105">전송 오류 및 SOAP 메시지 수준 오류를 극복하여 신뢰할 수 없는 네트워크에서 이를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-105">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="88ea2-106">특히 SOAP 또는 전송 매개자를 통해 보낸 메시지에 대해 세션 기반, 단일 및 필요에 따라 순서가 지정된 배달을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-106">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="88ea2-107">세션 기반 배달은 메시지를 선택적으로 정렬 하 여 세션에서 메시지를 그룹화 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-107">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="88ea2-108">이 항목에서는 신뢰할 수 있는 세션, 사용 방법 및 사용 시기와 이러한 세션을 보호 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-108">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="88ea2-109">WCF 신뢰할 수 있는 세션</span><span class="sxs-lookup"><span data-stu-id="88ea2-109">WCF reliable sessions</span></span>

<span data-ttu-id="88ea2-110">WCF 신뢰할 수 있는 세션은 WS-ReliableMessaging 프로토콜에서 정의한 SOAP 신뢰할 수 있는 메시징 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-110">WCF reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

<span data-ttu-id="88ea2-111">WCF SOAP 신뢰할 수 있는 메시징은 메시징 끝점을 분리 하는 중개의 수 나 유형에 관계 없이 두 끝점 사이에 종단 간 신뢰할 수 있는 세션을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-111">WCF SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="88ea2-112">여기에는 끝점 간에 메시지를 전달 하는 데 필요한 soap (예: HTTP 프록시) 또는 soap를 사용 하는 중개 (예: SOAP 기반 라우터 또는 브리지)를 사용 하지 않는 모든 전송 중개자가 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-112">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="88ea2-113">신뢰할 수 있는 세션 채널은 이러한 채널에서 연결 된 서비스가 동시에 실행 되 고 짧은 대기 시간, 즉 비교적 짧은 시간 간격 내에서 메시지를 교환 하 고 처리 하도록 *대화형* 통신을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-113">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="88ea2-114">이러한 결합은 이러한 구성 요소가 함께 진행 되거나 장애 조치 (failover) 되는 것을 의미 하기 때문에 격리를 제공 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-114">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="88ea2-115">신뢰할 수 있는 세션에서는 다음 두 가지 유형의 오류를 마스킹합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-115">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="88ea2-116">손실되거나 중복된 메시지 및 보낸 순서와 다른 순서로 도착한 메시지를 포함하는 SOAP 메시지 수준 오류</span><span class="sxs-lookup"><span data-stu-id="88ea2-116">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="88ea2-117">전송 오류</span><span class="sxs-lookup"><span data-stu-id="88ea2-117">Transport failures.</span></span>

<span data-ttu-id="88ea2-118">신뢰할 수 있는 세션은 WS-ReliableMessaging 프로토콜 및 내장 메모리 전송 창을 구현하여 SOAP 메시지 수준 오류를 마스킹하고 전송 오류가 발생할 경우 다시 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-118">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="88ea2-119">신뢰할 수 있는 세션은 TCP가 IP 패킷에 대해 제공하는 SOAP 메시지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-119">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="88ea2-120">TCP 소켓 연결은 노드 간에 IP 패킷에 대한 단수형의 순서가 지정된 전송을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-120">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="88ea2-121">신뢰할 수 있는 채널은 신뢰할 수 있는 전송과 동일한 유형을 제공하지만 다음과 같은 방법에서 TCP 소켓 안정성이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-121">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="88ea2-122">안정성은 임의 크기 패킷(바이트)이 아닌 SOAP 메시지 수준에서 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-122">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="88ea2-123">안정성은 TCP를 통한 전송 뿐만 아니라 전송 중립적입니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-123">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="88ea2-124">안정성은 특정 전송 세션 (예: TCP 연결이 제공 하는 세션)에 연결 되지 않고 신뢰할 수 있는 세션의 수명 동안 동시에 또는 순차적으로 여러 전송 세션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-124">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="88ea2-125">신뢰할 수 있는 세션은 SOAP 엔드포인트 간의 연결에 필요한 전송 연결 수에 관계없이 발신자 및 수신자 SOAP 엔드포인트 사이에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-125">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="88ea2-126">즉, 신뢰할 수 있는 세션이 종단 간 안정성을 제공 하는 반면, TCP 안정성은 전송 연결이 끝나는 위치를 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-126">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="88ea2-127">신뢰할 수 있는 세션 및 바인딩</span><span class="sxs-lookup"><span data-stu-id="88ea2-127">Reliable sessions and bindings</span></span>

<span data-ttu-id="88ea2-128">앞서 설명한 것 처럼 신뢰할 수 있는 세션은 전송 중립적입니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-128">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="88ea2-129">또한 요청-회신 또는 이중과 같은 여러 메시지 교환 패턴에 대해 신뢰할 수 있는 세션을 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-129">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="88ea2-130">WCF 신뢰할 수 있는 세션은 바인딩 집합의 속성으로 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-130">A WCF reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="88ea2-131">다음을 사용 하는 끝점에서 신뢰할 수 있는 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-131">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="88ea2-132">HTTP 기반 전송 표준 바인딩:</span><span class="sxs-lookup"><span data-stu-id="88ea2-132">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="88ea2-133">`WsHttpBinding` 및 요청-회신 또는 단방향 계약을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-133">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="88ea2-134">요청-회신 또는 간단한 단방향 서비스 계약을 통해 신뢰할 수 있는 세션을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="88ea2-134">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="88ea2-135">`WsDualHttpBinding` 및 이중, 요청-회신 또는 단방향 계약을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-135">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="88ea2-136">`WsFederationHttpBinding` 및 요청-회신 또는 단방향 계약을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-136">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="88ea2-137">TCP 기반 전송 표준 바인딩:</span><span class="sxs-lookup"><span data-stu-id="88ea2-137">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="88ea2-138">`NetTcpBinding` 및 이중, 요청-회신 또는 단방향 계약을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-138">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="88ea2-139">HTTPS (문제에 대 한 자세한 내용은 <a href="#reliable-sessions-and-security">신뢰할 수 있는 세션 및 보안</a>참조) 또는 명명 된 파이프 바인딩과 같은 사용자 지정 바인딩을 만들어 다른 바인딩에서 신뢰할 수 있는 세션을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-139">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="88ea2-140">서로 다른 기본 채널 형식에 대해 신뢰할 수 있는 세션을 쌓을 수 있으며, 결과적으로 신뢰할 수 있는 세션 채널 셰이프가 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-140">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="88ea2-141">클라이언트와 서버 모두에서 지원 되는 신뢰할 수 있는 세션 채널 형식은 사용 되는 기본 채널의 형식에 따라 달라 집니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-141">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="88ea2-142">다음 표에서는 기본 채널 형식의 기능으로서 클라이언트에서 지원되는 세션 채널 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-142">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="88ea2-143">지원 되는 신뢰할 수 있는 세션 채널 형식&#8224;</span><span class="sxs-lookup"><span data-stu-id="88ea2-143">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="88ea2-144">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-144">Yes</span></span>               | <span data-ttu-id="88ea2-145">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-145">Yes</span></span>                      | <span data-ttu-id="88ea2-146">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-146">Yes</span></span>              | <span data-ttu-id="88ea2-147">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-147">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="88ea2-148">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-148">Yes</span></span>               | <span data-ttu-id="88ea2-149">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-149">Yes</span></span>                      | <span data-ttu-id="88ea2-150">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-150">No</span></span>               | <span data-ttu-id="88ea2-151">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-151">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="88ea2-152">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-152">No</span></span>                | <span data-ttu-id="88ea2-153">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-153">No</span></span>                       | <span data-ttu-id="88ea2-154">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-154">Yes</span></span>              | <span data-ttu-id="88ea2-155">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-155">Yes</span></span>                     |

<span data-ttu-id="88ea2-156">&#8224;지원 되는 채널 형식은 `TChannel` 메서드에 전달 되는 제네릭 매개 변수 값에 사용할 수 있는 값입니다 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> .</span><span class="sxs-lookup"><span data-stu-id="88ea2-156">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="88ea2-157">다음 표에서는 기본 채널 형식의 기능으로서 서버에서 지원되는 세션 채널 형식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-157">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="88ea2-158">지원 되는 신뢰할 수 있는 세션 채널 형식&#8225;</span><span class="sxs-lookup"><span data-stu-id="88ea2-158">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="88ea2-159">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-159">Yes</span></span>             | <span data-ttu-id="88ea2-160">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-160">Yes</span></span>                    | <span data-ttu-id="88ea2-161">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-161">Yes</span></span>              | <span data-ttu-id="88ea2-162">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-162">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="88ea2-163">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-163">Yes</span></span>             | <span data-ttu-id="88ea2-164">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-164">Yes</span></span>                    | <span data-ttu-id="88ea2-165">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-165">No</span></span>               | <span data-ttu-id="88ea2-166">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-166">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="88ea2-167">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-167">No</span></span>              | <span data-ttu-id="88ea2-168">아니요</span><span class="sxs-lookup"><span data-stu-id="88ea2-168">No</span></span>                     | <span data-ttu-id="88ea2-169">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-169">Yes</span></span>              | <span data-ttu-id="88ea2-170">예</span><span class="sxs-lookup"><span data-stu-id="88ea2-170">Yes</span></span>                     |

<span data-ttu-id="88ea2-171">&#8225;지원 되는 채널 형식은 `TChannel` 메서드에 전달 되는 제네릭 매개 변수 값에 사용할 수 있는 값입니다 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> .</span><span class="sxs-lookup"><span data-stu-id="88ea2-171">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="88ea2-172">신뢰할 수 있는 세션 및 보안</span><span class="sxs-lookup"><span data-stu-id="88ea2-172">Reliable sessions and security</span></span>

<span data-ttu-id="88ea2-173">통신 당사자 (서비스 및 클라이언트)가 인증 되 고 세션에서 교환 되는 메시지가 변조 되지 않도록 하려면 신뢰할 수 있는 세션의 보안을 유지 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-173">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="88ea2-174">또한 신뢰할 수 있는 개별 세션의 무결성을 보장 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-174">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="88ea2-175">신뢰할 수 있는 세션은 보안 세션 채널에서 표시 하 고 관리 하는 보안 컨텍스트에 바인딩하여 보안이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-175">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="88ea2-176">보안 채널은 보안 세션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-176">The security channel provides a security session.</span></span> <span data-ttu-id="88ea2-177">세션 설정 동안 교환된 보안 토큰은 신뢰할 수 있는 세션의 메시지 보안을 유지하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-177">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="88ea2-178">TCP-S를 통해 신뢰할 수 있는 세션의 경우 TCP 세션은 신뢰할 수 있는 세션에 연결 됩니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-178">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="88ea2-179">따라서 전송 보안은 보안도 신뢰할 수 있는 세션에 연결 되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-179">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="88ea2-180">이 경우 연결 재설정이 꺼집니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-180">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="88ea2-181">HTTPS를 사용하는 경우에만 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-181">The only exception is when using HTTPS.</span></span> <span data-ttu-id="88ea2-182">SSL(Secure Sockets Layer) (SSL) 세션이 신뢰할 수 있는 세션에 바인딩되어 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-182">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="88ea2-183">보안 컨텍스트 (SSL 세션)를 공유 하는 세션은 서로 보호 되지 않으므로이로 인해 위협이 발생 합니다. 이는 응용 프로그램에 따라 실제 위협이 될 수도 있고 그렇지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-183">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="88ea2-184">신뢰할 수 있는 세션 사용</span><span class="sxs-lookup"><span data-stu-id="88ea2-184">Using reliable sessions</span></span>

<span data-ttu-id="88ea2-185">WCF 신뢰할 수 있는 세션을 사용 하려면 신뢰할 수 있는 세션을 지 원하는 바인딩을 사용 하 여 끝점을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-185">To use WCF reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="88ea2-186">WCF가 신뢰할 수 있는 세션을 사용 하 여 제공 하는 시스템 제공 바인딩 중 하나를 사용 하거나이를 수행 하는 사용자 지정 바인딩을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-186">Use one of the system-provided bindings that WCF provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="88ea2-187">기본적으로 신뢰할 수 있는 세션을 지원하고 사용하도록 설정하는 시스템 정의 바인딩은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-187">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="88ea2-188">옵션으로 신뢰할 수 있는 세션을 지 원하는 시스템 제공 바인딩은 기본적으로 다음을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-188">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="88ea2-189">사용자 지정 바인딩을 만드는 방법에 대 한 예제는 [방법: HTTPS를 사용 하 여 신뢰할 수 있는 사용자 지정 세션 바인딩 만들기](how-to-create-a-custom-reliable-session-binding-with-https.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="88ea2-189">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="88ea2-190">신뢰할 수 있는 세션을 지 원하는 WCF 바인딩에 대 한 자세한 내용은 [시스템 제공 바인딩](../system-provided-bindings.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="88ea2-190">For a discussion of WCF bindings that support reliable sessions, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="88ea2-191">신뢰할 수 있는 세션을 사용 하는 경우</span><span class="sxs-lookup"><span data-stu-id="88ea2-191">When to use reliable sessions</span></span>

<span data-ttu-id="88ea2-192">응용 프로그램에서 신뢰할 수 있는 세션을 사용 해야 하는 경우를 이해 하는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-192">It's important to understand when to use reliable sessions in your application.</span></span> <span data-ttu-id="88ea2-193">WCF는 동시에 활성 상태이 고 활성 상태인 끝점 간에 신뢰할 수 있는 세션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-193">WCF supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="88ea2-194">응용 프로그램에서 기간 중 하나를 사용할 수 없는 경우에는 큐를 사용 하 여 안정성을 확보 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-194">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="88ea2-195">시나리오에 TCP를 통해 연결 된 두 개의 끝점이 필요한 경우 TCP는 신뢰할 수 있는 메시지 교환을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-195">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="88ea2-196">그러나 TCP는 패킷이 한 번만 도착 하도록 보장 하기 때문에 신뢰할 수 있는 세션을 사용할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-196">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="88ea2-197">시나리오에 다음과 같은 특징이 있는 경우 신뢰할 수 있는 세션을 사용 하는 것이 심각 하 게 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="88ea2-197">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="88ea2-198">Soap 중개 (예: SOAP 라우터)</span><span class="sxs-lookup"><span data-stu-id="88ea2-198">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="88ea2-199">프록시 중개 또는 전송 브리지</span><span class="sxs-lookup"><span data-stu-id="88ea2-199">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="88ea2-200">간헐적 연결</span><span class="sxs-lookup"><span data-stu-id="88ea2-200">Intermittent connectivity</span></span>

- <span data-ttu-id="88ea2-201">HTTP를 통한 세션</span><span class="sxs-lookup"><span data-stu-id="88ea2-201">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="88ea2-202">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88ea2-202">See also</span></span>

- [<span data-ttu-id="88ea2-203">바인딩을 사용하여 서비스 및 클라이언트 구성</span><span class="sxs-lookup"><span data-stu-id="88ea2-203">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="88ea2-204">WS 신뢰할 수 있는 세션</span><span class="sxs-lookup"><span data-stu-id="88ea2-204">WS Reliable Session</span></span>](../samples/ws-reliable-session.md)
