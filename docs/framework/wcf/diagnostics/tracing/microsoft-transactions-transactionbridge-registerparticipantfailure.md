---
description: 자세한 내용은 RegisterParticipantFailure를 확인 하세요.
title: Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure
ms.date: 03/30/2017
ms.assetid: 3a4ead79-8550-4037-84e3-fd70ff56e001
ms.openlocfilehash: e930ee66720a9f397999d729e8d680fce9a37e29
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99770627"
---
# <a name="microsofttransactionstransactionbridgeregisterparticipantfailure"></a><span data-ttu-id="d9155-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span><span class="sxs-lookup"><span data-stu-id="d9155-103">Microsoft.Transactions.TransactionBridge.RegisterParticipantFailure</span></span>

<span data-ttu-id="d9155-104">WS-AT 프로토콜 서비스가 제어 프로토콜에 대한 참가자를 등록하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="d9155-104">The WS-AT protocol service failed to register a participant for a control protocol.</span></span>  
  
## <a name="description"></a><span data-ttu-id="d9155-105">설명</span><span class="sxs-lookup"><span data-stu-id="d9155-105">Description</span></span>  

 <span data-ttu-id="d9155-106">MSDTC가 잘못된 등록 요청을 감지하는 경우 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9155-106">Traced if MSDTC detects an invalid Registration request.</span></span> <span data-ttu-id="d9155-107">이는 여러 완료 등록 요청 및 내부 오류에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9155-107">This can be caused by  multiple Completion registration requests and internal errors.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="d9155-108">문제 해결</span><span class="sxs-lookup"><span data-stu-id="d9155-108">Troubleshooting</span></span>  

 <span data-ttu-id="d9155-109">완료를 두 번 이상 등록하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d9155-109">Do not try to Register for Completion more than once.</span></span>  <span data-ttu-id="d9155-110">또한 추적 메시지 내의 상태 문자열을 검사하여 실행 가능한 항목이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="d9155-110">Also, inspect the status string within the trace message to determine if any actionable item exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9155-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9155-111">See also</span></span>

- [<span data-ttu-id="d9155-112">추적</span><span class="sxs-lookup"><span data-stu-id="d9155-112">Tracing</span></span>](index.md)
- [<span data-ttu-id="d9155-113">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="d9155-113">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="d9155-114">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="d9155-114">Administration and Diagnostics</span></span>](../index.md)
