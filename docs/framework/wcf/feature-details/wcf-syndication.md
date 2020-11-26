---
title: WCF 배포
ms.date: 03/30/2017
helpviewer_keywords:
- syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
ms.openlocfilehash: 825990c6c1690281af65d53c76dcca0f3e2ffb67
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239044"
---
# <a name="wcf-syndication"></a><span data-ttu-id="7babe-102">WCF 배포</span><span class="sxs-lookup"><span data-stu-id="7babe-102">WCF Syndication</span></span>

<span data-ttu-id="7babe-103">WCF (Windows Communication Foundation)는 Atom, RSS 또는 기타 사용자 지정 형식에서 배포 피드를 쉽게 사용할 수 있도록 지원 합니다 .이를 통해 서비스 끝점에 노출 하 고 읽고 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-103">Windows Communication Foundation (WCF) provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="7babe-104">이 단원의 항목에서는 배포에 대한 이 프로그래밍 모델에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7babe-105">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="7babe-105">In This Section</span></span>  

 [<span data-ttu-id="7babe-106">WCF 배포 개요</span><span class="sxs-lookup"><span data-stu-id="7babe-106">WCF Syndication Overview</span></span>](wcf-syndication-overview.md)  
 <span data-ttu-id="7babe-107">WCF에서 제공 하는 배포 지원에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-107">Provides an overview of syndication support provided by WCF.</span></span>  
  
 [<span data-ttu-id="7babe-108">배포 아키텍처</span><span class="sxs-lookup"><span data-stu-id="7babe-108">Architecture of Syndication</span></span>](architecture-of-syndication.md)  
 <span data-ttu-id="7babe-109">개체 모델의 클래스와 배포 확장성에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="7babe-110">WCF 배포 개체 모델을 Atom 및 RSS로 매핑하는 방법</span><span class="sxs-lookup"><span data-stu-id="7babe-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="7babe-111">피드를 WCF 배포 개체 모델로 등록하는 방법과 RSS 및 Atom 피드로 변환하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="7babe-112">방법: 기본 RSS 피드 만들기</span><span class="sxs-lookup"><span data-stu-id="7babe-112">How to: Create a Basic RSS Feed</span></span>](how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="7babe-113">기본 RSS 피드를 사용 가능하도록 지정하는 서비스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="7babe-114">방법: 기본 Atom 피드 만들기</span><span class="sxs-lookup"><span data-stu-id="7babe-114">How to: Create a Basic Atom Feed</span></span>](how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="7babe-115">기본 ATOM 피드를 사용 가능하도록 지정하는 서비스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="7babe-116">방법: Atom 및 RSS로 피드 공개</span><span class="sxs-lookup"><span data-stu-id="7babe-116">How to: Expose a Feed as Both Atom and RSS</span></span>](how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="7babe-117">ATOM 및 RSS에서 동일한 피드를 사용 가능하도록 지정하는 서비스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="7babe-118">배포 확장성</span><span class="sxs-lookup"><span data-stu-id="7babe-118">Syndication Extensibility</span></span>](syndication-extensibility.md)  
 <span data-ttu-id="7babe-119">사용자 지정 요소와 특성을 배포 피드에 추가하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7babe-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7babe-120">참고</span><span class="sxs-lookup"><span data-stu-id="7babe-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7babe-121">관련 단원</span><span class="sxs-lookup"><span data-stu-id="7babe-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7babe-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7babe-122">See also</span></span>

- [<span data-ttu-id="7babe-123">WCF 웹 HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="7babe-123">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="7babe-124">부분 신뢰</span><span class="sxs-lookup"><span data-stu-id="7babe-124">Partial Trust</span></span>](partial-trust.md)
