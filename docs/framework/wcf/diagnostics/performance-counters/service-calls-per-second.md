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
# <a name="service-calls-per-second"></a>서비스: Calls Per Second

카운터 이름: Calls Per Second  
  
## <a name="description"></a>설명  

 이 서비스에 대한 초당 호출 횟수입니다.  
  
 이 카운터는 다음 수식을 사용 하 여 값을 계산 하는 성능 카운터 유형 [PERF_COUNTER_COUNTER](/previous-versions/windows/it-pro/windows-server-2003/cc740048(v=ws.10))입니다.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)에서 분자(N)는 마지막 샘플 기간 동안 수행되는 작업 수를 나타내고, 분모(D)는 해당 기간 동안 경과되는 눈금 수를 나타내며 F는 눈금의 주기를 나타냅니다.
