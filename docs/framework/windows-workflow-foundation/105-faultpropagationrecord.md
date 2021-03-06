---
description: '자세한 정보: 105-FaultPropagationRecord'
title: 105 - FaultPropagationRecord
ms.date: 03/30/2017
ms.assetid: 168473b1-b1e5-4e9f-8a2a-35bbdb2ef531
ms.openlocfilehash: 95f82763606bf16219fa4234b5f6e7101c0954fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99667683"
---
# <a name="105---faultpropagationrecord"></a>105 - FaultPropagationRecord

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|Id|105|  
|키워드|EndToEndMonitoring, 문제 해결, HealthMonitoring, WFTracking|  
|Level|경고|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/분석|  
  
## <a name="description"></a>설명  

 워크플로 인스턴스가 포함된 활동에서 FaultPropagationRecord를 내보내면 ETW 추적 참여자가 이 이벤트를 내보냅니다.  
  
## <a name="message"></a>메시지  

 TrackRecord = FaultPropagationRecord, InstanceID=%1, RecordNumber=%2, EventTime=%3, FaultSourceActivityName=%4, FaultSourceActivityId=%5, FaultSourceActivityInstanceId=%6, FaultSourceActivityTypeName=%7, FaultHandlerActivityName=%8,  FaultHandlerActivityId = %9, FaultHandlerActivityInstanceId =%10, FaultHandlerActivityTypeName=%11, Fault=%12, IsFaultSource=%13, Annotations=%14, ProfileName = %15  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|워크플로의 인스턴스 ID|  
|RecordNumber|xs:long|내보낸 레코드의 시퀀스 번호|  
|EventTime|xs:dateTime|이벤트를 내보낸 시간(UTC)|  
|FaultSourceActivityName|xs:string|오류를 내보낸 활동 이름|  
|FaultSourceActivityId|xs:string|오류를 내보낸 활동의 ID|  
|FaultSourceActivityInstanceId|xs:string|오류를 내보낸 활동의 인스턴스 ID|  
|FaultSourceActivityTypeName|xs:string|오류를 내보낸 활동의 유형|  
|FaultHandlerActivityName|xs:string|오류 처리기 활동의 표시 이름|  
|FaultHandlerActivityId|xs:string|오류 처리기 활동의 ID|  
|FaultHandlerActivityInstanceId|xs:string|오류 처리기 활동의 인스턴스 ID|  
|FaultHandlerActivityTypeName|xs:string|오류 처리기 활동의 유형|  
|오류|xs:string|오류 세부 사항|  
|IsFaultSource|xs:unsignedByte|이벤트를 오류 소스에서 내보냈는지 여부를 나타냅니다.|  
|주석|xs:string|이 이벤트에 추가된 주석입니다.  값은 xml 요소에 a 형식으로 저장 됩니다 \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> .  주석을 지정 하지 않으면 문자열에가 포함 \<items/> 됩니다. ETW 이벤트 크기는 ETW 버퍼 크기 또는 ETW 이벤트의 최대 페이로드에 따라 제한됩니다. 이벤트 크기가 ETW 제한을 초과 하면 주석을 삭제 하 고 주석 값을 ...로 대체 하 여 이벤트를 자릅니다. \<items> \</items>|  
|ProfileName|xs:string|이 이벤트를 내보낸 이름 또는 추적 프로필|  
|HostReference|xs:string|웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다.  해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName ' 예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '로 정의 됩니다.|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
