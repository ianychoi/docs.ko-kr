---
title: IAsyncResult를 사용하는 비동기 메서드 호출
ms.date: 03/30/2017
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 20aafd45c323a609b3cc7fb5a1a6378d43548fcb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830456"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a>IAsyncResult를 사용하는 비동기 메서드 호출

.NET 라이브러리 및 타사 클래스 라이브러리의 유형은 주 애플리케이션 스레드가 아닌 다른 스레드에서 비동기 작업을 수행하는 동안 애플리케이션이 계속 실행할 수 있도록 하는 메서드를 제공할 수 있습니다. 다음 섹션에서는 <xref:System.IAsyncResult> 디자인 패턴을 사용하는 비동기 메서드를 호출할 수 있는 다양한 방법을 보여주는 코드 예제를 설명하고 제공합니다.  
  
- [비동기 작업을 종료하여 애플리케이션 실행 차단](blocking-application-execution-by-ending-an-async-operation.md).  
  
- [AsyncWaitHandle을 사용하는 애플리케이션 실행 차단](blocking-application-execution-using-an-asyncwaithandle.md).  
  
- [비동기 작업의 상태에 대한 폴링](polling-for-the-status-of-an-asynchronous-operation.md).  
  
- [AsyncCallback 대리자를 사용하여 비동기 작업 종료](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).  
  
## <a name="see-also"></a>참고 항목

- [이벤트 기반 비동기 패턴(EAP)](event-based-asynchronous-pattern-eap.md)
- [이벤트 기반 비동기 패턴 개요](event-based-asynchronous-pattern-overview.md)
