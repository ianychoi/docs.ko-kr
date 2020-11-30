---
title: 피어 이름 확인 프로토콜
description: 보안성과 확장성이 있으며 동적인 이름 등록 및 이름 확인 프로토콜인 PNRP(피어 이름 확인 프로토콜)에 대해 알아봅니다.
ms.date: 03/30/2017
ms.assetid: 11940511-c124-4d91-ae31-d4ed6e81ee58
ms.openlocfilehash: d50514569d066d04391ce65522df789ed421dbed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239395"
---
# <a name="peer-name-resolution-protocol"></a><span data-ttu-id="f8924-103">피어 이름 확인 프로토콜</span><span class="sxs-lookup"><span data-stu-id="f8924-103">Peer Name Resolution Protocol</span></span>

<span data-ttu-id="f8924-104">피어 투 피어 환경에서 각 피어는 이름 또는 기타 유형의 식별자로 서로의 네트워크 위치(주소, 프로토콜 및 포트)를 확인하기 위해 고유한 이름 확인 시스템을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-104">In peer-to-peer environments, peers use specific name resolution systems to resolve each other's network locations (addresses, protocols, and ports) from names or other types of identifiers.</span></span> <span data-ttu-id="f8924-105">과거에는 기본적으로 일시적이었던 연결과 DNS(Domain Name System)의 다른 단점으로 인해 피어 이름 확인이 복잡했습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-105">In the past, peer name resolution has been complicated by the inherently transient connectivity as well as other shortcomings within the Domain Name System (DNS).</span></span>  
  
 <span data-ttu-id="f8924-106">Microsoft® Windows® 피어 투 피어 네트워킹 플랫폼은 안전하고 확장 가능한 동적 이름 등록 및 이름 확인 프로토콜인 PNRP(피어 이름 확인 프로토콜)를 사용하여 이러한 이름 확인 문제를 해결합니다. Windows XP용으로 처음 개발되어 Windows Vista™에서 업그레이드된</span><span class="sxs-lookup"><span data-stu-id="f8924-106">The Microsoft® Windows® Peer-to-Peer Networking platform solves this problem with the Peer Name Resolution Protocol (PNRP), a secure, scalable, and dynamic name registration and name resolution protocol first developed for Windows XP and then upgraded in Windows Vista™.</span></span> <span data-ttu-id="f8924-107">PNRP는 기존의 이름 확인 시스템과는 전혀 다른 작동 방식으로 애플리케이션 개발자에게 새로운 가능성을 열어 주고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-107">PNRP works very differently from traditional name resolution systems, opening up exciting new possibilities for application developers.</span></span>  
  
 <span data-ttu-id="f8924-108">PNRP를 사용하면 피어 이름을 컴퓨터 또는 컴퓨터의 개별 애플리케이션이나 서비스에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-108">With PNRP, peer names can be applied to the machine, or individual applications or services on the machine.</span></span> <span data-ttu-id="f8924-109">피어 이름 확인 방식의 경우 주소, 포트 및 확장될 수 있는 페이로드까지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-109">A peer name resolution includes an address, port, and possibly an extended payload.</span></span> <span data-ttu-id="f8924-110">이 시스템의 이점에는 내결함성, 병목 현상 없음, 오래된 주소를 반환하지 않는 이름 확인이 포함되며, 프로토콜 사용이 모바일 사용자를 찾는 뛰어난 솔루션이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-110">Benefits of this system include fault tolerance, no bottlenecks, and name resolutions that will never return stale addresses; making the protocol an excellent solution for locating mobile users.</span></span>  
  
 <span data-ttu-id="f8924-111">보안과 관련하여 피어 이름을 보안됨(보호) 또는 보안되지 않음(보호되지 않음)으로 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-111">In terms of security, peer names can be published as secured (protected) or unsecured (unprotected).</span></span> <span data-ttu-id="f8924-112">PNRP에서는 공개 키 암호화를 사용하여 보안 피어 이름을 스푸핑으로부터 보호합니다. 컴퓨터와 서비스 모두 PNRP를 사용하여 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-112">PNRP uses public key cryptography to protect secure peer names against spoofing; both computers and services can be named with PNRP.</span></span>  
  
<span data-ttu-id="f8924-113">피어 이름 확인 프로토콜은 다음 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-113">The Peer Name Resolution Protocol demonstrates the following properties:</span></span>  
  
- <span data-ttu-id="f8924-114">분산되어 있으며 거의 완전히 서버가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-114">Distributed and almost entirely serverless.</span></span> <span data-ttu-id="f8924-115">서버는 부트스트랩 프로세스에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-115">Servers are only required for the bootstrapping process.</span></span>  
  
- <span data-ttu-id="f8924-116">제3자의 개입 없이도 이름 게시를 보호합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-116">Secure name publication without the involvement of third parties.</span></span> <span data-ttu-id="f8924-117">DNS 이름 게시와 달리 PNRP 이름 게시는 즉각적이며 재정적으로 비용이 들지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-117">Unlike DNS name publication, PNRP name publication is instantaneous and without financial cost.</span></span>  
  
- <span data-ttu-id="f8924-118">실시간 PNRP 업데이트를 통해 오래된 주소의 확인을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-118">PNRP updates in real-time, which prevents the resolution of stale addresses.</span></span>  
  
- <span data-ttu-id="f8924-119">PNRP를 통한 이름 확인은 서비스를 위한 이름 확인도 허용하여 컴퓨터 이상으로 확대됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-119">The resolution of names via PNRP extends beyond computers by also allowing name resolution for services.</span></span>  
  
## <a name="the-systemnetpeertopeer-namespace"></a><span data-ttu-id="f8924-120">System.Net.PeerToPeer 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="f8924-120">The System.Net.PeerToPeer namespace</span></span>  
  
- <span data-ttu-id="f8924-121">PNRP 기능은 .NET Framework 버전 3.5에 있는 <xref:System.Net.PeerToPeer> 네임스페이스를 통해 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-121">PNRP functionality is defined by the <xref:System.Net.PeerToPeer> namespace within the .NET Framework version 3.5.</span></span> <span data-ttu-id="f8924-122">사용 가능한 PNRP 서비스로 피어 이름을 등록하고 확인하는 데 사용할 수 있는 형식 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-122">It provides a set of types that can be used to register and resolve peer names with an available PNRP service.</span></span>  
  
- <span data-ttu-id="f8924-123">(PNRP 및 사용자 지정 피어 확인자는 <xref:System.ServiceModel.PeerResolvers> 네임스페이스에 제공된 형식을 사용하여 만들고 인스턴스화할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="f8924-123">(PNRP and custom peer resolvers can be created and instantiated using the types provided in the <xref:System.ServiceModel.PeerResolvers> namespace.)</span></span>  
  
- <span data-ttu-id="f8924-124">사용 가능한 PNRP 서비스로 이름을 등록하고 해결하는 데 사용하는 기본 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-124">The basic types used to register and resolve names with an available PNRP service are as follows:</span></span>  
  
- <span data-ttu-id="f8924-125"><xref:System.Net.PeerToPeer.Cloud>: 해당 범위를 포함하여 사용 가능한 PNRP 클라우드를 설명하는 정보를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-125"><xref:System.Net.PeerToPeer.Cloud>: Defines the information describing an available PNRP cloud, including its scope.</span></span>  
  
- <span data-ttu-id="f8924-126"><xref:System.Net.PeerToPeer.PeerName>: 클라우드 내에서 피어를 등록하고 이후에 확인하는 데 사용할 수 있는 피어 이름을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-126"><xref:System.Net.PeerToPeer.PeerName>: Defines a peer name that can be used to register and subsequently resolve a peer within a cloud.</span></span>  
  
- <span data-ttu-id="f8924-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: 피어의 등록 정보를 포함하는 레코드를 PNRP 클라우드에 정의합니다. 이 레코드에는 피어에 연결할 수 있는 네트워크 엔드포인트가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-127"><xref:System.Net.PeerToPeer.PeerNameRecord>: Defines the record in PNRP cloud that contains the registration information for a peer, which includes the network endpoints at which the peer can be contacted.</span></span>  
  
- <span data-ttu-id="f8924-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: 피어 이름 등록을 시작하고 중지하는 메서드를 포함하여 피어 이름의 등록 프로세스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-128"><xref:System.Net.PeerToPeer.PeerNameRegistration>: Defines the registration process for a peer name, including methods to start and stop peer name registration.</span></span>  
  
- <span data-ttu-id="f8924-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: 확인할 동기 및 비동기 메서드를 포함하여 피어 이름을 네트워크 엔드포인트로 확인하는 프로세스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f8924-129"><xref:System.Net.PeerToPeer.PeerNameResolver>: Defines the process for resolving a peer name to its network endpoint(s), including both synchronous and asynchronous methods for resolution.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8924-130">참조</span><span class="sxs-lookup"><span data-stu-id="f8924-130">See also</span></span>

- <xref:System.ServiceModel.PeerResolvers>
- <xref:System.Net.PeerToPeer>
- [<span data-ttu-id="f8924-131">네트워크 프로그래밍 샘플</span><span class="sxs-lookup"><span data-stu-id="f8924-131">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [PeerToPeer Technology Sample](https://go.microsoft.com/fwlink/?LinkID=179571)
-->
