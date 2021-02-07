---
description: '다음에 대 한 자세한 정보: 서비스: 초당 호출 수'
title: '서비스: Calls Per Second'
ms.date: 03/30/2017
ms.assetid: 6261d28d-d449-425a-b9fc-a4ee14079134
ms.openlocfilehash: f6e21f5f1c7a0d5d4ceeb11f954ebbc95f66a3ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99744034"
---
# <a name="service-calls-per-second"></a><span data-ttu-id="85954-103">서비스: Calls Per Second</span><span class="sxs-lookup"><span data-stu-id="85954-103">Service: Calls Per Second</span></span>

<span data-ttu-id="85954-104">카운터 이름: Calls Per Second</span><span class="sxs-lookup"><span data-stu-id="85954-104">Counter Name: Calls Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="85954-105">설명</span><span class="sxs-lookup"><span data-stu-id="85954-105">Description</span></span>  

 <span data-ttu-id="85954-106">이 서비스에 대한 초당 호출 횟수입니다.</span><span class="sxs-lookup"><span data-stu-id="85954-106">Number of calls to this service in a second.</span></span>  
  
 <span data-ttu-id="85954-107">이 카운터는 다음 수식을 사용 하 여 값을 계산 하는 성능 카운터 유형 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))입니다.</span><span class="sxs-lookup"><span data-stu-id="85954-107">This counter is of performance counter type [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10)), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="85954-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)에서 분자(N)는 마지막 샘플 기간 동안 수행되는 작업 수를 나타내고, 분모(D)는 해당 기간 동안 경과되는 눈금 수를 나타내며 F는 눈금의 주기를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="85954-108">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F) where the numerator (N) represents the number of operations performed during the last sample interval, the denominator (D) represents the number of ticks elapsed during the last sample interval, and F is the frequency of the ticks.</span></span>
