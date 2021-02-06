---
description: '자세한 정보: System.servicemodel. PeerNodeAuthenticationFailure'
title: System.ServiceModel.Channels.PeerNodeAuthenticationFailure
ms.date: 03/30/2017
ms.assetid: 0b50f782-ca06-4a82-aa7f-71f78ddc5177
ms.openlocfilehash: 751202abd3e199a03fc4ee0bf1252d4a8027e0cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99634936"
---
# <a name="systemservicemodelchannelspeernodeauthenticationfailure"></a><span data-ttu-id="ca385-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span><span class="sxs-lookup"><span data-stu-id="ca385-103">System.ServiceModel.Channels.PeerNodeAuthenticationFailure</span></span>

<span data-ttu-id="ca385-104">잠재적인 환경이 있는 보안 핸드셰이크가 성공하지 못했습니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-104">The security handshake with a potential neighbor was not successful.</span></span>  
  
## <a name="description"></a><span data-ttu-id="ca385-105">설명</span><span class="sxs-lookup"><span data-stu-id="ca385-105">Description</span></span>  

 <span data-ttu-id="ca385-106">이 추적은 보안 환경 연결을 설정하는 동안 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-106">This trace occurs while attempting to establish a secure neighbor connection.</span></span> <span data-ttu-id="ca385-107">이는 자격 증명이 충분하지 않거나 올바르지 않기 때문일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-107">This can happen due to insufficient or incorrect credentials.</span></span>  
  
 <span data-ttu-id="ca385-108">PeerChannel은 강력한 ID인 X.509 인증서에 대한 단일 토큰 형식을 인식합니다. 이는 구현 가능한 인증 및 권한 부여의 형식을 기반으로 강력한 ID 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-108">PeerChannel recognizes a single token type for strong identification, X.509 certificates, which provide a strong identity model based on the type of authentication and authorization that can be implemented.</span></span> <span data-ttu-id="ca385-109">PeerChannel은 암호를 사용하여 간단한 애플리케이션에 대한 지원도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-109">PeerChannel also provides support for simple applications through the use of passwords.</span></span> <span data-ttu-id="ca385-110">암호는 세션 입장을 허용하는 용도로만 사용할 수 있으며, 메시지 인증에는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-110">Passwords can be used only to allow entry to the session; they cannot be used to perform message authentication.</span></span> <span data-ttu-id="ca385-111">이는 피어 그룹이 공유하는 대칭 토큰을 소스 인증에 사용하기에는 어렵고 적절하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ca385-111">This is because a symmetric token that a group of peers share is difficult and inappropriate to use for source authentication.</span></span>  
  
## <a name="troubleshooting"></a><span data-ttu-id="ca385-112">문제 해결</span><span class="sxs-lookup"><span data-stu-id="ca385-112">Troubleshooting</span></span>  

 <span data-ttu-id="ca385-113">모든 환경에 적합한 보안 자격 증명이 있는지 확인하십시오.</span><span class="sxs-lookup"><span data-stu-id="ca385-113">Ensure that all neighbors have the appropriate security credentials.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca385-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca385-114">See also</span></span>

- [<span data-ttu-id="ca385-115">피어 채널 보안</span><span class="sxs-lookup"><span data-stu-id="ca385-115">Peer Channel Security</span></span>](../../feature-details/peer-channel-security.md)
- [<span data-ttu-id="ca385-116">추적</span><span class="sxs-lookup"><span data-stu-id="ca385-116">Tracing</span></span>](index.md)
- [<span data-ttu-id="ca385-117">추적을 사용하여 애플리케이션 문제 해결</span><span class="sxs-lookup"><span data-stu-id="ca385-117">Using Tracing to Troubleshoot Your Application</span></span>](using-tracing-to-troubleshoot-your-application.md)
- [<span data-ttu-id="ca385-118">관리 및 진단</span><span class="sxs-lookup"><span data-stu-id="ca385-118">Administration and Diagnostics</span></span>](../index.md)
