---
description: '자세한 정보: 118-WorkflowInstanceUnhandledExceptionRecordWithId'
title: 118 - WorkflowInstanceUnhandledExceptionRecordWithId
ms.date: 03/30/2017
ms.assetid: 2ce4b193-e141-4cc4-86a3-2e8c984c110d
ms.openlocfilehash: 9d39afb95db8a393b967d590ee37e9f3f2529ffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99703226"
---
# <a name="118---workflowinstanceunhandledexceptionrecordwithid"></a>118 - WorkflowInstanceUnhandledExceptionRecordWithId

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|ID|118|  
|키워드|HealthMonitoring, WFTracking|  
|Level|Error|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/분석|  
  
## <a name="description"></a>설명  

 워크플로 인스턴스가 WorkflowInstanceUnhandledExceptionRecord를 내보내면 ETW 추적 참가자가 이 이벤트를 내보냅니다.  
  
## <a name="message"></a>메시지  

 TrackRecord = WorkflowInstanceUnhandledExceptionRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, SourceName = %5, SourceId = %6, SourceInstanceId = %7, SourceTypeName=%8, Exception=%9, Annotations= %10, ProfileName = %11, WorkflowDefinitionIdentity = %12  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|워크플로의 인스턴스 ID|  
|RecordNumber|xs:long|내보낸 레코드의 시퀀스 번호|  
|EventTime|xs:dateTime|이벤트를 내보낸 시간(UTC)|  
|ActivityDefinitionId|xs:string|워크플로의 루트 활동 이름|  
|SourceName|xs:string|오류로 인해 unhandledException을 일으킨 소스 활동의 이름|  
|SourceId|xs:string|오류 소스 활동의 활동 ID|  
|SourceInstanceId|xs:string|오류 소스 활동의 활동 인스턴스 ID|  
|SourceTypeName|xs:string|오류로 인해 unhandledException을 일으킨 소스 활동의 형식 이름|  
|예외|xs:string|처리되지 않은 예외에 대한 예외 정보|  
|시스템 상태|xs:string|워크플로의 현재 상태|  
|주석|xs:string|이 이벤트에 추가된 주석입니다. 값은 xml 요소에 a 형식으로 저장 됩니다 \<items> \< item name = "annotationName" type="System.String"> \</item> \</items> . 주석을 지정 하지 않으면 문자열에가 포함 \<items/> 됩니다. ETW 이벤트 크기는 ETW 버퍼 크기 또는 ETW 이벤트의 최대 페이로드에 따라 제한됩니다. 이벤트 크기가 ETW 제한을 초과 하면 주석을 삭제 하 고 주석 값을 ...로 대체 하 여 이벤트를 자릅니다. \<items> \</items>|  
|ProfileName|xs:string|이 이벤트를 내보낸 이름 또는 추적 프로필|  
|WorkflowDefinitionIdentity|xs:string|워크플로 정의 ID입니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
