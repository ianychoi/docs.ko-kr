---
title: System.ServiceModel.Channels.MsmqPoisonMessageRejected
ms.date: 03/30/2017
ms.assetid: 0e64b9bd-1f12-43df-a189-d7be3c2bace1
ms.openlocfilehash: 69da35f65e04a3cba15885c4fe6e57d63762cb1c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96260346"
---
# <a name="systemservicemodelchannelsmsmqpoisonmessagerejected"></a><span data-ttu-id="d1756-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span><span class="sxs-lookup"><span data-stu-id="d1756-102">System.ServiceModel.Channels.MsmqPoisonMessageRejected</span></span>

<span data-ttu-id="d1756-103">포이즌 메시지가 거부되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d1756-103">Poison message rejected.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d1756-104">Description</span><span class="sxs-lookup"><span data-stu-id="d1756-104">Description</span></span>  

 <span data-ttu-id="d1756-105">이 추적은 포이즌 메시지가 발생되어 거부되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d1756-105">The trace indicates that a poison message was encountered and subsequently rejected.</span></span> <span data-ttu-id="d1756-106">이는 NetMsmqBinding 또는 MsmqIntegrationBinding의 `ReceiveErrorHandling` 속성을 `Reject`로 설정할 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="d1756-106">This occurs when the `ReceiveErrorHandling` property on the NetMsmqBinding or MsmqIntegrationBinding is set to `Reject`.</span></span> <span data-ttu-id="d1756-107">거부 된 메시지는 보낸 사람의 [배달 못 한 편지 큐](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)로 다시 배달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d1756-107">A rejected message is delivered back to the sender’s [Dead-Letter Queue](../../feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md).</span></span>  
  
 <span data-ttu-id="d1756-108">메시지가 포이즌 메시지를 처리 하 고 적절 하 게 처리 하도록 서비스를 구성 하는 방법에 대 한 자세한 내용은 [포이즌 메시지 처리](../../feature-details/poison-message-handling.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1756-108">For more information on when messages become poison and how to configure your service to handle them appropriately, see [Poison-Message Handling](../../feature-details/poison-message-handling.md).</span></span> <span data-ttu-id="d1756-109">MSMQ에서 거부 된 메시지의 의미에 대 한 자세한 내용은 [Mqmarkmessagerejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))않음을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d1756-109">For more information on what a rejected message means in MSMQ, see [MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1756-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d1756-110">See also</span></span>

- [<span data-ttu-id="d1756-111">추적</span><span class="sxs-lookup"><span data-stu-id="d1756-111">Tracing</span></span>](index.md)
- [<span data-ttu-id="d1756-112">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="d1756-112">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d1756-113">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="d1756-113">Administration and Diagnostics</span></span>](../index.md)
- [<span data-ttu-id="d1756-114">포이즌 메시지 처리</span><span class="sxs-lookup"><span data-stu-id="d1756-114">Poison-Message Handling</span></span>](../../feature-details/poison-message-handling.md)
- <span data-ttu-id="d1756-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="d1756-115">[MQMarkMessageRejected](/previous-versions/windows/desktop/msmq/ms707071(v=vs.85))</span></span>
