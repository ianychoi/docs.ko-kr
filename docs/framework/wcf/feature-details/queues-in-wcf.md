---
title: Windows Communication Foundation의 큐
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: d63b03e519484ad6ec90b4267a49b77738593e45
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244654"
---
# <a name="queues-in-windows-communication-foundation"></a><span data-ttu-id="c4089-102">Windows Communication Foundation의 큐</span><span class="sxs-lookup"><span data-stu-id="c4089-102">Queues in Windows Communication Foundation</span></span>

<span data-ttu-id="c4089-103">이 단원의 항목에서는 큐에 대 한 WCF (Windows Communication Foundation) 지원에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-103">The topics in this section discuss Windows Communication Foundation (WCF) support for queues.</span></span> <span data-ttu-id="c4089-104">WCF는 Microsoft 메시지 큐 (이전에는 MSMQ 라고 함)를 전송으로 활용 하 여 큐에 대 한 지원을 제공 하 고 다음과 같은 시나리오를 가능 하 게 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-104">WCF provides support for queuing by leveraging Microsoft Message Queuing (previously known as MSMQ) as a transport and enables the following scenarios:</span></span>  
  
- <span data-ttu-id="c4089-105">느슨하게 결합된 애플리케이션.</span><span class="sxs-lookup"><span data-stu-id="c4089-105">Loosely coupled applications.</span></span> <span data-ttu-id="c4089-106">송신 애플리케이션은 수신 애플리케이션이 메시지를 처리할 수 있는지 여부를 확인할 필요 없이 큐에 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-106">Sending applications can send messages to queues without needing to know whether the receiving application is available to process the message.</span></span> <span data-ttu-id="c4089-107">큐는 수신 애플리케이션이 메시지를 처리할 수 있는 속도에 따라 변경되지 않는 일정한 속도로 송신 애플리케이션이 메시지를 큐에 보낼 수 있는 독립적인 프로세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-107">The queue provides processing independence that allows a sending application to send messages to the queue at a rate that does not depend on how fast the receiving applications can process the messages.</span></span> <span data-ttu-id="c4089-108">큐에 메시지를 보내는 작업이 메시지 처리 작업과 밀접하게 연결되지 않을 경우 전반적인 시스템 가용성이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-108">Overall system availability increases when sending messages to a queue is not tightly coupled to message processing.</span></span>  
  
- <span data-ttu-id="c4089-109">실패 격리.</span><span class="sxs-lookup"><span data-stu-id="c4089-109">Failure isolation.</span></span> <span data-ttu-id="c4089-110">메시지를 큐에 보내거나 받는 애플리케이션이 서로 간에 영향을 주지 않고 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-110">Applications sending or receiving messages to a queue can fail without affecting each other.</span></span> <span data-ttu-id="c4089-111">예를 들어 수신 애플리케이션이 실패하더라도 송신 애플리케이션은 계속해서 큐에 메시지를 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-111">If, for example, the receiving application fails, the sending application can continue to send messages to the queue.</span></span> <span data-ttu-id="c4089-112">수신 응용 프로그램이 다시 활성화되면 큐에서 메시지를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-112">When the receiver is up again, it can process the messages from the queue.</span></span> <span data-ttu-id="c4089-113">실패 격리는 전체 시스템 안정성 및 가용성을 향상시킵니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-113">Failure isolation increases the overall system reliability and availability.</span></span>  
  
- <span data-ttu-id="c4089-114">로드 조정.</span><span class="sxs-lookup"><span data-stu-id="c4089-114">Load leveling.</span></span> <span data-ttu-id="c4089-115">송신 애플리케이션이 수신 애플리케이션을 메시지로 가득 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-115">Sending applications can overwhelm receiving applications with messages.</span></span> <span data-ttu-id="c4089-116">큐는 수신 응용 프로그램이 과부하가 걸리지 않도록 일치하지 않는 메시지 작성 및 사용률을 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-116">Queues can manage mismatched message production and consumption rates so that a receiver is not overwhelmed.</span></span>  
  
- <span data-ttu-id="c4089-117">연결이 끊긴 작업.</span><span class="sxs-lookup"><span data-stu-id="c4089-117">Disconnected operations.</span></span> <span data-ttu-id="c4089-118">송신, 수신 및 처리 작업은 모바일 디바이스의 경우처럼 대기 시간이 긴 네트워크 또는 가용성이 제한된 네트워크에서 통신하는 경우 연결이 끊어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-118">Sending, receiving, and processing operations can become disconnected when communicating over high-latency networks or limited-availability networks, such as in the case of mobile devices.</span></span> <span data-ttu-id="c4089-119">큐를 사용하면 엔드포인트의 연결이 끊어지더라도 이러한 작업을 계속 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-119">Queues allow these operations to continue, even when the endpoints are disconnected.</span></span> <span data-ttu-id="c4089-120">다시 연결이 되면 큐가 메시지를 수신 애플리케이션으로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-120">When the connection is reestablished, the queue forwards messages to the receiving application.</span></span>  
  
 <span data-ttu-id="c4089-121">WCF 응용 프로그램에서 큐 기능을 사용 하려면 표준 바인딩 중 하나를 사용 하거나 표준 바인딩 중 하나가 요구 사항을 충족 하지 않는 경우 사용자 지정 바인딩을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-121">To use the queues feature in a WCF application, you can use one of the standard bindings, or you can create a custom binding if one of the standard bindings does not satisfy your requirements.</span></span> <span data-ttu-id="c4089-122">관련 표준 바인딩과이 바인딩에 대 한 자세한 내용은 [방법: WCF 끝점 및 메시지 큐 응용 프로그램과 메시지 교환](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4089-122">For more information about relevant standard bindings and how to choose one, see [How to: Exchange Messages with WCF Endpoints and Message Queuing Applications](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md).</span></span> <span data-ttu-id="c4089-123">사용자 지정 바인딩을 만드는 방법에 대한 자세한 내용은 [사용자 지정 바인딩](../extending/custom-bindings.md)을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="c4089-123">For more information about creating custom bindings, see [Custom Bindings](../extending/custom-bindings.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c4089-124">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="c4089-124">In This Section</span></span>  

 [<span data-ttu-id="c4089-125">큐 개요</span><span class="sxs-lookup"><span data-stu-id="c4089-125">Queues Overview</span></span>](queues-overview.md)  
 <span data-ttu-id="c4089-126">메시지 큐 개념의 개요.</span><span class="sxs-lookup"><span data-stu-id="c4089-126">An overview of message queuing concepts.</span></span>  
  
 [<span data-ttu-id="c4089-127">WCF의 큐</span><span class="sxs-lookup"><span data-stu-id="c4089-127">Queuing in WCF</span></span>](queuing-in-wcf.md)  
 <span data-ttu-id="c4089-128">WCF 큐 지원에 대 한 개요입니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-128">An overview of WCF queue support.</span></span>  
  
 [<span data-ttu-id="c4089-129">방법: WCF 엔드포인트와 대기 중인 메시지 교환</span><span class="sxs-lookup"><span data-stu-id="c4089-129">How to: Exchange Queued Messages with WCF Endpoints</span></span>](how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 <span data-ttu-id="c4089-130">클래스를 사용 하 여 <xref:System.ServiceModel.NetMsmqBinding> wcf 클라이언트와 wcf 서비스 간에 통신 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-130">Explains how to use the <xref:System.ServiceModel.NetMsmqBinding> class to communicate between a WCF client and WCF service.</span></span>  
  
 [<span data-ttu-id="c4089-131">방법: WCF 엔드포인트 및 메시지 큐 애플리케이션과 메시지 교환</span><span class="sxs-lookup"><span data-stu-id="c4089-131">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 <span data-ttu-id="c4089-132">를 사용 하 여 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> WCF와 메시지 큐 응용 프로그램 간에 통신 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-132">Explains how to use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> to communicate between WCF and Message Queuing applications.</span></span>  
  
 [<span data-ttu-id="c4089-133">세션의 대기 중인 메시지 그룹화</span><span class="sxs-lookup"><span data-stu-id="c4089-133">Grouping Queued Messages in a Session</span></span>](grouping-queued-messages-in-a-session.md)  
 <span data-ttu-id="c4089-134">단일 수신 애플리케이션으로 상호 관련된 메시지 처리를 용이하게 하기 위해 큐의 메시지를 그룹화하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-134">Explains how to group messages in a queue to facilitate correlated message processing by a single receiving application.</span></span>  
  
 [<span data-ttu-id="c4089-135">트랜잭션에서 메시지 일괄 처리</span><span class="sxs-lookup"><span data-stu-id="c4089-135">Batching Messages in a Transaction</span></span>](batching-messages-in-a-transaction.md)  
 <span data-ttu-id="c4089-136">메시지를 트랜잭션으로 일괄 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-136">Explains how to batch messages in a transaction.</span></span>  
  
 [<span data-ttu-id="c4089-137">배달 못 한 편지 큐를 사용하여 메시지 전송 오류 처리</span><span class="sxs-lookup"><span data-stu-id="c4089-137">Using Dead-Letter Queues to Handle Message Transfer Failures</span></span>](using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 <span data-ttu-id="c4089-138">배달 못 한 편지 큐를 사용하여 메시지 전송 및 배달 실패를 처리하고 배달 못 한 편지 큐에서 메시지를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-138">Explains how to handle message transfer and delivery failures using dead letter queues and how to process messages from the dead letter queue.</span></span>  
  
 [<span data-ttu-id="c4089-139">포이즌 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="c4089-139">Poison Message Handling</span></span>](poison-message-handling.md)  
 <span data-ttu-id="c4089-140">포이즌 메시지(수신 애플리케이션에 전달하는 최대 배달 시도 횟수를 초과한 메시지)를 처리하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-140">Explains how to handle poison messages (messages that have exceeded the maximum number of delivery attempts to the receiving application).</span></span>  
  
 [<span data-ttu-id="c4089-141">Windows Vista, Windows Server 2003 및 Windows XP의 큐 기능 차이점</span><span class="sxs-lookup"><span data-stu-id="c4089-141">Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP</span></span>](diff-in-queue-in-vista-server-2003-windows-xp.md)  
 <span data-ttu-id="c4089-142">Windows Vista, Windows Server 2003 및 Windows XP 간의 WCF 큐 기능 차이를 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-142">Summarizes the differences in the WCF queues feature between Windows Vista, Windows Server 2003, and Windows XP.</span></span>  
  
 [<span data-ttu-id="c4089-143">전송 보안을 사용하여 메시지에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="c4089-143">Securing Messages Using Transport Security</span></span>](securing-messages-using-transport-security.md)  
 <span data-ttu-id="c4089-144">전송 보안을 사용하여 대기 중인 메시지의 보안을 유지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-144">Describes how to use transport security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="c4089-145">메시지 보안을 사용하여 메시지에 보안 설정</span><span class="sxs-lookup"><span data-stu-id="c4089-145">Securing Messages Using Message Security</span></span>](securing-messages-using-message-security.md)  
 <span data-ttu-id="c4089-146">메시지 보안을 사용하여 대기 중인 메시지의 보안을 유지하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-146">Describes how to use message security to secure queued messages.</span></span>  
  
 [<span data-ttu-id="c4089-147">대기 중인 메시지 문제 해결</span><span class="sxs-lookup"><span data-stu-id="c4089-147">Troubleshooting Queued Messaging</span></span>](troubleshooting-queued-messaging.md)  
 <span data-ttu-id="c4089-148">일반적인 큐 문제를 해결하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-148">Explains how to troubleshoot common queuing problems.</span></span>  
  
 [<span data-ttu-id="c4089-149">대기 중인 통신을 위한 최선의 방법</span><span class="sxs-lookup"><span data-stu-id="c4089-149">Best Practices for Queued Communication</span></span>](best-practices-for-queued-communication.md)  
 <span data-ttu-id="c4089-150">WCF의 대기 중인 통신 사용에 대 한 모범 사례를 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4089-150">Explains best practices for using WCF queued communication.</span></span>  
