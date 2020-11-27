---
title: 채널 확장성
ms.date: 03/30/2017
ms.assetid: 4cc3b20b-778a-4ae8-b58c-a3822fb13065
ms.openlocfilehash: 1a734c305e2a6f2fc759647ab5bdf380f7c7eeee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253842"
---
# <a name="channels-extensibility"></a><span data-ttu-id="319c0-102">채널 확장성</span><span class="sxs-lookup"><span data-stu-id="319c0-102">Channels Extensibility</span></span>

<span data-ttu-id="319c0-103">이 단원에는 사용자 지정 채널을 보여 주는 샘플이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-103">This section contains samples that demonstrate custom channels.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="319c0-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="319c0-104">In This Section</span></span>  

 [<span data-ttu-id="319c0-105">로컬 채널</span><span class="sxs-lookup"><span data-stu-id="319c0-105">Local Channel</span></span>](local-channel.md)  
 <span data-ttu-id="319c0-106">동일한 응용 프로그램 도메인 내에서 통신 하는 데 사용 되는 WCF 전송 채널 인 로컬 채널을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-106">Demonstrates the local channel, a WCF transport channel that is used for communication within the same application domain.</span></span>  
  
 [<span data-ttu-id="319c0-107">신뢰할 수 있는 보안 프로필</span><span class="sxs-lookup"><span data-stu-id="319c0-107">Reliable Secure Profile</span></span>](reliable-secure-profile.md)  
 <span data-ttu-id="319c0-108">WCF 및 RSP (신뢰할 수 있는 보안 프로필)를 구성 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-108">Demonstrates how to compose WCF and Reliable Secure Profile (RSP).</span></span>  
  
 [<span data-ttu-id="319c0-109">사용자 지정 채널 디스패처</span><span class="sxs-lookup"><span data-stu-id="319c0-109">Custom Channel Dispatcher</span></span>](custom-channel-dispatcher.md)  
 <span data-ttu-id="319c0-110"><xref:System.ServiceModel.ServiceHostBase>를 직접 구현하여 사용자 지정 방식으로 채널 스택을 빌드하는 방법과 웹 호스트 환경에서 사용자 지정 채널 디스패처를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-110">Demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span>  
  
 [<span data-ttu-id="319c0-111">청크 채널</span><span class="sxs-lookup"><span data-stu-id="319c0-111">Chunking Channel</span></span>](chunking-channel.md)  
 <span data-ttu-id="319c0-112">WCF를 사용 하 여 보낸 대용량 메시지를 버퍼링 하는 데 사용 되는 메모리 양을 제한 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-112">Demonstrates how to limit the amount of memory used to buffer large messages sent using WCF.</span></span>
  
 [<span data-ttu-id="319c0-113">HttpCookieSession</span><span class="sxs-lookup"><span data-stu-id="319c0-113">HttpCookieSession</span></span>](httpcookiesession.md)  
 <span data-ttu-id="319c0-114">사용자 지정 프로토콜 채널을 빌드하여 세션 관리에 HTTP 쿠키를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-114">Demonstrates how to build a custom protocol channel to use HTTP cookies for session management.</span></span>  
  
 [<span data-ttu-id="319c0-115">사용자 지정 메시지 인터셉터</span><span class="sxs-lookup"><span data-stu-id="319c0-115">Custom Message Interceptor</span></span>](custom-message-interceptor.md)  
 <span data-ttu-id="319c0-116">런타임 스택의 특정 지점에서 들어오고 나가는 모든 메시지를 가로채기 위해 채널 팩터리 및 채널 수신기를 만드는 사용자 지정 바인딩 요소의 구현 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="319c0-116">Demonstrates how to implement a custom binding element that creates channel factories and channel listeners to intercept all incoming and outgoing messages at a particular point in the run-time stack.</span></span>
