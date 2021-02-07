---
description: MessageProcessingPaused에 대해 자세히 알아보세요.
title: System.ServiceModel.MessageProcessingPaused
ms.date: 03/30/2017
ms.assetid: 36b5302a-93cc-478a-9bb2-8a1601fba1df
ms.openlocfilehash: 77e4742bc5617904136b2ddd9cb90fe886d38b10
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716182"
---
# <a name="systemservicemodelmessageprocessingpaused"></a><span data-ttu-id="704e4-103">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="704e4-103">System.ServiceModel.MessageProcessingPaused</span></span>

<span data-ttu-id="704e4-104">System.ServiceModel.MessageProcessingPaused</span><span class="sxs-lookup"><span data-stu-id="704e4-104">System.ServiceModel.MessageProcessingPaused</span></span>  
  
## <a name="description"></a><span data-ttu-id="704e4-105">설명</span><span class="sxs-lookup"><span data-stu-id="704e4-105">Description</span></span>  

 <span data-ttu-id="704e4-106">메시지를 처리하는 동안 스레드가 전환되었습니다.</span><span class="sxs-lookup"><span data-stu-id="704e4-106">The threads were switched while processing a message.</span></span>  
  
 <span data-ttu-id="704e4-107">메시지 처리는 다음 이유로 인해 일시 중지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704e4-107">Message processing can be paused by the following reasons:</span></span>  
  
- <span data-ttu-id="704e4-108">ConcurrencyMode가 단일하거나 재진입할 수 있으며, 서비스가 다른 메시지를 처리하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704e4-108">ConcurrencyMode is single or reentrant, and the service is processing another message.</span></span>  
  
- <span data-ttu-id="704e4-109">트랜잭션이 사용하도록 설정되어 있으며, 서비스가 다른 트랜잭션을 처리하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="704e4-109">Transaction is enabled and the service is processing another transaction.</span></span>  
  
- <span data-ttu-id="704e4-110">현재 동기화 컨텍스트가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="704e4-110">Synchronization context is not current.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="704e4-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="704e4-111">See also</span></span>

- [<span data-ttu-id="704e4-112">추적</span><span class="sxs-lookup"><span data-stu-id="704e4-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="704e4-113">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="704e4-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="704e4-114">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="704e4-114">Administration and Diagnostics</span></span>](../index.md)
