---
title: Queue Dropped Messages Per Second
ms.date: 03/30/2017
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
ms.openlocfilehash: 81ba15965676ba7ffe5ca2aaac5e1d0e94e27962
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266040"
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="faeff-102">Queue Dropped Messages Per Second</span><span class="sxs-lookup"><span data-stu-id="faeff-102">Queue Dropped Messages Per Second</span></span>

<span data-ttu-id="faeff-103">카운터 이름: Queued Messages Dropped Per Second</span><span class="sxs-lookup"><span data-stu-id="faeff-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="faeff-104">Description</span><span class="sxs-lookup"><span data-stu-id="faeff-104">Description</span></span>  

 <span data-ttu-id="faeff-105">초당 이 서비스에 대기 중인 전송에서 손실된 메시지 수입니다.</span><span class="sxs-lookup"><span data-stu-id="faeff-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="faeff-106">이 카운터는 다음 수식을 사용 하 여 값을 계산 하는 성능 카운터 유형 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))입니다.</span><span class="sxs-lookup"><span data-stu-id="faeff-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="faeff-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="faeff-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
