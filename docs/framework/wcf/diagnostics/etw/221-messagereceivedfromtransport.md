---
description: '자세한 정보: 221-MessageReceivedFromTransport'
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 0cc15fa95ae321083afa2792810807971e909e6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803505"
---
# <a name="221---messagereceivedfromtransport"></a>221 - MessageReceivedFromTransport

## <a name="properties"></a>속성  
  
|||  
|-|-|  
|ID|221|  
|키워드|EndToEndMonitoring, 문제 해결, ServiceModel|  
|Level|정보|  
|채널|Microsoft-Windows-애플리케이션 서버-애플리케이션/분석|  
  
## <a name="description"></a>설명  

 이 이벤트는 서비스 모델이 전송에서 메시지를 받을 때 내보내집니다.  
  
## <a name="message"></a>메시지  

 디스패처가 전송에서 메시지를 받았습니다. Correlation ID == '%1'.  
  
## <a name="details"></a>세부 정보  
  
|데이터 항목 이름|데이터 항목 형식|설명|  
|--------------------|--------------------|-----------------|  
|상관관계 ID|`xs:GUID`|서비스 또는 클라이언트의 `MessageSentToTransport` 이벤트를 다른 끝에 있는 해당 `MessageReceivedFromTransport`에 상호 연결하는 데 사용되는 동작 ID입니다.|  
|HostReference|`xs:string`|웹 호스팅 서비스의 경우 이 필드는 웹 계층의 서비스를 고유하게 식별합니다. 해당 형식은 ' 웹 사이트 이름 응용 프로그램 가상 경로&#124;서비스 가상 경로&#124;ServiceName '으로 정의 됩니다. 예: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService '.|  
|AppDomain|`xs:string`|AppDomain.CurrentDomain.FriendlyName에서 반환되는 문자열입니다.|
