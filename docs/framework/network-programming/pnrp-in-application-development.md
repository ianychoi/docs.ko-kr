---
title: 애플리케이션 개발의 PNRP
ms.date: 03/30/2017
ms.assetid: 265615d6-4423-4b5d-8626-752e456f4f4e
ms.openlocfilehash: 7c59b2be8384c8f8cc6bbdc4546a678cfe1c538d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263193"
---
# <a name="pnrp-in-application-development"></a><span data-ttu-id="8ff14-102">애플리케이션 개발의 PNRP</span><span class="sxs-lookup"><span data-stu-id="8ff14-102">PNRP in Application Development</span></span>

<span data-ttu-id="8ff14-103">Windows Vista에서 네트워킹 애플리케이션은 단순화된 PNRP API(애플리케이션 프로그래밍 인터페이스)를 통해 PNRP 이름 게시 및 확인 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-103">In Windows Vista, networking applications can access name publication and resolution functions through a simplified PNRP application programming interface (API).</span></span>  
  
## <a name="implementing-the-peer-name-resolution-protocol"></a><span data-ttu-id="8ff14-104">피어 이름 확인 프로토콜의 구현</span><span class="sxs-lookup"><span data-stu-id="8ff14-104">Implementing the Peer Name Resolution Protocol</span></span>  

 <span data-ttu-id="8ff14-105">간소화된 PNRP API를 사용하면 이름과 주소를 등록하도록 클라우드가 명시적으로 지정되지 않습니다. PNRP 구성 요소를 통해 조인하는 데 적절한 클라우드와 클라우드에서 게시할 주소를 자동으로 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-105">With the simplified PNRP API, clouds are not explicitly specified to register the name and addresses; the PNRP component automatically determines the appropriate clouds to join and the addresses to publish within the clouds.</span></span>  
  
 <span data-ttu-id="8ff14-106">Windows Vista에서 상당히 단순화된 형태의 PNRP 이름 확인 기능의 경우 PNRP 이름이 getaddrinfo() Windows 소켓 함수에 통합되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-106">For highly simplified PNRP name resolution in Windows Vista, PNRP names are now integrated into the getaddrinfo() Windows Sockets function.</span></span> <span data-ttu-id="8ff14-107">따라서 애플리케이션이 PNRP를 이용하여 IPv6 주소에 해당하는 이름을 확인할 때 getaddrinfo() 함수를 사용하여 FQDN(정규화된 도메인 이름) name.prnp.net(여기서 name은 확인할 피어 이름)을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-107">To use PNRP to resolve a name to an IPv6 address, applications can use the getaddrinfo() function to resolve the Fully Qualified Domain Name (FQDN) name.prnp.net, in which name is peer name being resolved.</span></span> <span data-ttu-id="8ff14-108">pnrp.net 도메인은 Windows Vista에서 PNRP 이름 확인에 사용하도록 예약된 도메인입니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-108">The pnrp.net domain is a reserved domain in Windows Vista for PNRP name resolution.</span></span>  
  
 <span data-ttu-id="8ff14-109">PeerToPeer 애플리케이션 간에 전달되는 메시지는 여전히 PeerChannel 및 WCF [대형 데이터 및 스트리밍](../wcf/feature-details/large-data-and-streaming.md) 등의 기본 아키텍처에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="8ff14-109">Message passing between PeerToPeer applications is still handled by underlying architectures such as PeerChannel and WCF [Large Data and Streaming](../wcf/feature-details/large-data-and-streaming.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff14-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8ff14-110">See also</span></span>

- <xref:System.Net.PeerToPeer>
