---
title: System.ServiceModel.Channels.FailedAcceptFromPool
ms.date: 03/30/2017
ms.assetid: d535b1b5-ee58-45e8-b400-7d9570f4eb9a
ms.openlocfilehash: 8615cca7d4ed8ea1f40baa9502e7136d4349eb9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256315"
---
# <a name="systemservicemodelchannelsfailedacceptfrompool"></a><span data-ttu-id="17daa-102">System.ServiceModel.Channels.FailedAcceptFromPool</span><span class="sxs-lookup"><span data-stu-id="17daa-102">System.ServiceModel.Channels.FailedAcceptFromPool</span></span>

<span data-ttu-id="17daa-103">풀 연결을 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17daa-103">An attempt to reuse a pooled connection failed.</span></span> <span data-ttu-id="17daa-104">지정된 제한 시간 동안 다시 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="17daa-104">Another attempt is made within the specified timeout period.</span></span>  
  
## <a name="description"></a><span data-ttu-id="17daa-105">Description</span><span class="sxs-lookup"><span data-stu-id="17daa-105">Description</span></span>  

 <span data-ttu-id="17daa-106">이 정보 추적은 풀 연결을 다시 사용하는 동안 오류가 발생했음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="17daa-106">This informational trace indicates that an error has occurred while attempting to reuse a pooled connection.</span></span> <span data-ttu-id="17daa-107">이는 풀 연결이 호환되지 않거나 준비되지 않았거나 아직 활성화되지 않은 경우 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17daa-107">This could happen because the pooled connection was not compatible, ready, or still active.</span></span> <span data-ttu-id="17daa-108">지정된 시간 제한 내에 다른 풀 연결을 다시 사용하려고 시도한 다음 사용할 수 있는 연결이 없는 경우 새 연결을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="17daa-108">Additional attempts to reuse other pooled connection are made within a given timeout and a new connection is created in case no usable connections are found.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17daa-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17daa-109">See also</span></span>

- [<span data-ttu-id="17daa-110">추적</span><span class="sxs-lookup"><span data-stu-id="17daa-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="17daa-111">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="17daa-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="17daa-112">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="17daa-112">Administration and Diagnostics</span></span>](../index.md)
