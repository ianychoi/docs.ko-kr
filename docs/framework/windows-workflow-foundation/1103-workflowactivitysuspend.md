---
description: '자세한 정보: 1103-WorkflowActivitySuspend'
title: 1103 - WorkflowActivitySuspend
ms.date: 03/30/2017
ms.assetid: b64e15c2-cb2c-4314-9074-ce2c6717232e
ms.openlocfilehash: 2d46c31ee86dd39216294e6b7cd3785f2361f18b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667527"
---
# <a name="1103---workflowactivitysuspend"></a>1103 - WorkflowActivitySuspend

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|ID|1103|  
|키워드|WFRuntime|  
|Level|정보|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/디버그|  
  
## <a name="description"></a>설명  

 워크플로 작업이 일시 중단되었음을 나타냅니다.  
  
## <a name="message"></a>메시지  

 WorkflowInstance Id: '%1' E2E 작업  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|--------------------|--------------------|-----------------|  
|WorkflowInstanceId|xs:string|워크플로 인스턴스 ID입니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
