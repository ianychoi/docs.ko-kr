---
description: '자세히 알아보기: 1009-ActivityScheduled 됨'
title: 1009 - ActivityScheduled
ms.date: 03/30/2017
ms.assetid: 307e38b6-d47e-47a4-9708-e74d8314b1a1
ms.openlocfilehash: 80ee250955a03927fb9db2b1242d420be77a6df8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755553"
---
# <a name="1009---activityscheduled"></a>1009 - ActivityScheduled

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|ID|1009|  
|키워드|WFRuntime|  
|Level|정보|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/디버그|  
  
## <a name="description"></a>설명  

 실행 예약되는 작업을 나타냅니다.  
  
## <a name="message"></a>메시지  

 Parent Activity '%1', DisplayName: '%2', InstanceId: '%3' scheduled child Activity '%4', DisplayName: '%5', InstanceId: '%6'.  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|--------------------|--------------------|-----------------|  
|ParentActivity|xs:string|부모 작업의 형식 이름입니다.|  
|ParentDisplayName|xs:string|부모 작업의 표시 이름입니다.|  
|ParentInstanceId|xs:string|부모 작업의 인스턴스 ID입니다.|  
|ChildActivity|xs:string|예약된 자식 작업의 형식 이름입니다.|  
|ChildDisplayName|xs:string|예약된 자식 작업의 표시 이름입니다.|  
|ChildInstanceId|xs:string|예약된 자식 작업의 인스턴스 ID입니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
