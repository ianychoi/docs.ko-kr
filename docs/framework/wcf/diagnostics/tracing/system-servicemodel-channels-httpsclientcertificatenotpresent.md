---
title: System.ServiceModel.Channels.HttpsClientCertificateNotPresent
ms.date: 03/30/2017
ms.assetid: b13ef1b6-e340-401d-93ca-2710c3842205
ms.openlocfilehash: 9ec25138130311f8cdd9af8fb32a3e80fb33ed68
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258090"
---
# <a name="systemservicemodelchannelshttpsclientcertificatenotpresent"></a><span data-ttu-id="f785c-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span><span class="sxs-lookup"><span data-stu-id="f785c-102">System.ServiceModel.Channels.HttpsClientCertificateNotPresent</span></span>

<span data-ttu-id="f785c-103">클라이언트 인증서가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f785c-103">Client certificate is required.</span></span> <span data-ttu-id="f785c-104">요청에서 인증서를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f785c-104">No certificate was found in the request.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f785c-105">Description</span><span class="sxs-lookup"><span data-stu-id="f785c-105">Description</span></span>  

 <span data-ttu-id="f785c-106">이 추적은 HTTPS 수신기가 클라이언트 인증서에 연결되지 않은 HTTPS 요청을 받았음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f785c-106">This trace indicates that the HTTPS listener received an HTTPS request that was not associated with a client certificate.</span></span> <span data-ttu-id="f785c-107">수신기가 모든 HTTPS 요청에서 클라이언트 인증서를 요구하도록 구성되어 있기 때문에 수신기가 클라이언트 인증의 유효성을 검사하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="f785c-107">Since the listener was configured to require client certificates on all HTTPS requests, the listener failed to validate the client’s authenticity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f785c-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f785c-108">See also</span></span>

- [<span data-ttu-id="f785c-109">추적</span><span class="sxs-lookup"><span data-stu-id="f785c-109">Tracing</span></span>](index.md)
- [<span data-ttu-id="f785c-110">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="f785c-110">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="f785c-111">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="f785c-111">Administration and Diagnostics</span></span>](../index.md)
