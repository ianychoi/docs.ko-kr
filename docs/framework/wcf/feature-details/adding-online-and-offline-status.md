---
title: 온라인 및 오프라인 상태 추가
ms.date: 03/30/2017
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
ms.openlocfilehash: 08ae4a20ced9626504c9fd2045416460e0878c5b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96292924"
---
# <a name="adding-online-and-offline-status"></a><span data-ttu-id="ef49b-102">온라인 및 오프라인 상태 추가</span><span class="sxs-lookup"><span data-stu-id="ef49b-102">Adding Online and Offline Status</span></span>

<span data-ttu-id="ef49b-103">대부분의 경우 애플리케이션에서 피어 채널 연결 상태에 대한 자세한 내용을 모니터링하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-103">In many cases, it is important for an application to monitor specific details about the status of a Peer Channel connection.</span></span> <span data-ttu-id="ef49b-104">이러한 정보는 `GetProperty` 인터페이스 구현에서 <xref:System.ServiceModel.IOnlineStatus> 메서드를 호출하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-104">You can obtain this information by calling the `GetProperty` method on an implementation of the <xref:System.ServiceModel.IOnlineStatus> interface.</span></span> <span data-ttu-id="ef49b-105">이러한 인터페이스가 구현된 개체는 연결 상태를 모니터링하거나 `OnOnline`과 `OnOffline`과 같은 이벤트 처리기를 등록할 수 있으며 온라인 상태가 변경되는 즉시 반응할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-105">An object with an implementation of this interface can monitor connection status or register for event handlers, such as `OnOnline` and `OnOffline`, and react immediately as changes to online status occur.</span></span>  
  
 <span data-ttu-id="ef49b-106">피어 채널 인프라에서 클라이언트는 하나 이상의 다른 피어와 연결되어 있으면 온라인으로, 그렇지 않으면 오프라인으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-106">In the Peer Channel infrastructure, a client is considered to be online if it is connected to at least one other peer and offline otherwise.</span></span> <span data-ttu-id="ef49b-107">이 점은 개발 애플리케이션을 디버깅하거나 자세한 정보를 최종 사용자에게 표시하는 데 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-107">This can be particularly useful in both debugging a developing applications or displaying detailed information to the end user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef49b-108">온라인 이벤트 처리기는 메시지를 보내기 전에 먼저 노드가 열려 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ef49b-108">An online event handler should first ensure that the node is open before sending any messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef49b-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ef49b-109">See also</span></span>

- [<span data-ttu-id="ef49b-110">피어 채널 애플리케이션 빌드</span><span class="sxs-lookup"><span data-stu-id="ef49b-110">Building a Peer Channel Application</span></span>](building-a-peer-channel-application.md)
