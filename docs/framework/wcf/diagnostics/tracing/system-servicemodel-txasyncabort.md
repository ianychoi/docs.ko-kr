---
title: System.ServiceModel.TxAsyncAbort
ms.date: 03/30/2017
ms.assetid: bce47ff2-abd0-4b58-8667-ebf1ef3580b8
ms.openlocfilehash: fd21428279a68cd8480b6ff0617bb2a70033a40d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269953"
---
# <a name="systemservicemodeltxasyncabort"></a><span data-ttu-id="06fa4-102">System.ServiceModel.TxAsyncAbort</span><span class="sxs-lookup"><span data-stu-id="06fa4-102">System.ServiceModel.TxAsyncAbort</span></span>

<span data-ttu-id="06fa4-103">지정한 트랜잭션이 비동기적으로 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06fa4-103">The specified transaction was asynchronously aborted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="06fa4-104">Description</span><span class="sxs-lookup"><span data-stu-id="06fa4-104">Description</span></span>  

 <span data-ttu-id="06fa4-105">다른 참가자가 중단을 응답하거나, 시간 초과가 발생하거나, 트랜잭션 참가자 내부에서 다른 오류가 발생하여 현재 트랜잭션이 중단되었습니다.</span><span class="sxs-lookup"><span data-stu-id="06fa4-105">The current transaction was aborted due to another participant voting for Abort, time-outs occurring, or another error inside the participant of a transaction.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="06fa4-106">문제 해결</span><span class="sxs-lookup"><span data-stu-id="06fa4-106">Troubleshooting</span></span>  

 <span data-ttu-id="06fa4-107">이 중단이 예기치 않은 동작인 경우 모든 시스템 로그에서 실제 중단 이유를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="06fa4-107">Check all system logs if this abort is unexpected to determine the real reason for the abort.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06fa4-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="06fa4-108">See also</span></span>

- [<span data-ttu-id="06fa4-109">추적</span><span class="sxs-lookup"><span data-stu-id="06fa4-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="06fa4-110">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="06fa4-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="06fa4-111">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="06fa4-111">Administration and Diagnostics</span></span>](../index.md)
