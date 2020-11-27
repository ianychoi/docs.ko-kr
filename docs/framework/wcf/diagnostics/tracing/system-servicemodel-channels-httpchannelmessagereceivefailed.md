---
title: System.ServiceModel.Channels.HttpChannelMessageReceiveFailed
ms.date: 03/30/2017
ms.assetid: 9eb311da-fdcc-4dd3-9d85-05b3280dfdda
ms.openlocfilehash: 97f22a01df84c39915f74fa7677e5dd18154b952
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96256224"
---
# <a name="systemservicemodelchannelshttpchannelmessagereceivefailed"></a><span data-ttu-id="69547-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span><span class="sxs-lookup"><span data-stu-id="69547-102">System.ServiceModel.Channels.HttpChannelMessageReceiveFailed</span></span>

<span data-ttu-id="69547-103">HTTP 채널을 통해 메시지를 받지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="69547-103">Failed to receive a message over an HTTP channel.</span></span>  
  
## <a name="description"></a><span data-ttu-id="69547-104">Description</span><span class="sxs-lookup"><span data-stu-id="69547-104">Description</span></span>  

 <span data-ttu-id="69547-105">이 추적은 경고 또는 오류로 내보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69547-105">This trace can be emitted as a warning or an error.</span></span> <span data-ttu-id="69547-106">두 가지 경우 모두, 들어오는 HTTP 요청에 대해 호환되는 수신기가 없고 HTTP 요청이 삭제되는 경우 추적을 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="69547-106">In both cases, the trace is emitted when a compatible listener is not found for an incoming HTTP request and the HTTP request is discarded.</span></span> <span data-ttu-id="69547-107">이 동작은 요청의 HTTP 동사를 HTTP 수신기가 인식하지 않거나 수신기가 요청 대상 주소에서 수신 대기하지 않기 때문에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69547-107">This could happen because the request’s HTTP verb was not recognized by any HTTP listener, or because no listener was listening on the address the request was targeted for.</span></span> <span data-ttu-id="69547-108">추적은 자체 호스팅 환경에서는 경고로 내보내지고 서비스가 IIS에서 호스팅되는 경우에는 오류로 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="69547-108">The trace is emitted as a warning in the self-hosted case, and as an error when the service is hosted in IIS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69547-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="69547-109">See also</span></span>

- [<span data-ttu-id="69547-110">추적</span><span class="sxs-lookup"><span data-stu-id="69547-110">Tracing</span></span>](index.md)
- [<span data-ttu-id="69547-111">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="69547-111">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="69547-112">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="69547-112">Administration and Diagnostics</span></span>](../index.md)
