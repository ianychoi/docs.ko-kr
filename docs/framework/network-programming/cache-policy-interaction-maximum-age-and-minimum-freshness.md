---
title: 캐시 정책 상호 작용 - 최대 보존 기간 및 최소 새로 고침
ms.date: 03/30/2017
helpviewer_keywords:
- time-based cache policies
- Revalidate policy
- cache [.NET Framework], time-based policies
- freshness of cached resources
- maximum age policy
- minimum freshness policy
- age of cached resources
ms.assetid: 6567d451-ecec-496c-95a3-a415b99ba52a
ms.openlocfilehash: d4182268341f4a4334a627fc8c9e24fa235f003f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287555"
---
# <a name="cache-policy-interactionmaximum-age-and-minimum-freshness"></a><span data-ttu-id="d5b9f-102">캐시 정책 상호 작용 - 최대 보존 기간 및 최소 새로 고침</span><span class="sxs-lookup"><span data-stu-id="d5b9f-102">Cache Policy Interaction—Maximum Age and Minimum Freshness</span></span>

<span data-ttu-id="d5b9f-103">최신 콘텐츠가 클라이언트 애플리케이션에 반환되도록 돕기 위해 클라이언트 캐시 정책 및 서버 유효성 재검사 요구 사항의 상호 작용 결과로 항상 가장 보수적인 캐시 정책이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-103">To help ensure that the freshest content is returned to the client application, the interaction of client cache policy and server revalidation requirements always results in the most conservative cache policy.</span></span> <span data-ttu-id="d5b9f-104">이 항목의 모든 예제에서는 1월 1일에 캐시되었으며 1월 4일에 만료되는 리소스에 대한 캐시 정책을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-104">All the examples in this topic illustrate the cache policy for a resource that is cached on January 1 and expires on January 4.</span></span>  
  
 <span data-ttu-id="d5b9f-105">다음 예제에서는 최대 사용 기간(`maxAge`) 및 최소 새로 고침(`minFresh`) 값의 상호 작용 결과로 생성되는 캐시 정책을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-105">The following examples illustrate the cache policy that results from the interaction of the maximum age (`maxAge`) and minimum freshness (`minFresh`) values.</span></span>  
  
- <span data-ttu-id="d5b9f-106">캐시 정책이 `maxAge` = 2일을 설정하고 `minFresh`를 지정하지 않을 경우 1월 3일에 콘텐츠 유효성이 재검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-106">If the cache policy sets `maxAge` = 2 days and `minFresh` is not specified, the content is revalidated on January 3.</span></span>  
  
- <span data-ttu-id="d5b9f-107">캐시 정책이 `maxAge` = 2일, `minFresh` = 1일을 설정하는 경우 `maxAge`에 따라 1월 3일까지 콘텐츠가 최신 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-107">If the cache policy sets `maxAge` = 2 days and `minFresh` = 1 day, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d5b9f-108">`minFresh`에 따라 콘텐츠가 1월 3일까지 최신 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-108">According to `minFresh`, the content is fresh until January 3.</span></span> <span data-ttu-id="d5b9f-109">따라서 1월 3일에 콘텐츠 유효성을 재검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-109">Therefore, the content must be revalidated on January 3.</span></span>  
  
- <span data-ttu-id="d5b9f-110">캐시 정책이 `maxAge` = 2일, `minFresh` = 2일을 설정하는 경우 `maxAge`에 따라 1월 3일까지 콘텐츠가 최신 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-110">If the cache policy sets `maxAge` = 2 days and `minFresh` = 2 days, according to `maxAge`, the content is fresh until January 3.</span></span> <span data-ttu-id="d5b9f-111">`minFresh`에 따라 콘텐츠가 1월 2일까지 최신 상태입니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-111">According to `minFresh` the content is fresh until January 2.</span></span> <span data-ttu-id="d5b9f-112">따라서 1월 2일에 콘텐츠 유효성을 재검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5b9f-112">Therefore, the content must be revalidated on January 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b9f-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d5b9f-113">See also</span></span>

- [<span data-ttu-id="d5b9f-114">네트워크 애플리케이션에 대한 캐시 관리</span><span class="sxs-lookup"><span data-stu-id="d5b9f-114">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="d5b9f-115">캐시 정책</span><span class="sxs-lookup"><span data-stu-id="d5b9f-115">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="d5b9f-116">위치 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="d5b9f-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="d5b9f-117">시간 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="d5b9f-117">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="d5b9f-118">네트워크 애플리케이션에서 캐싱 구성</span><span class="sxs-lookup"><span data-stu-id="d5b9f-118">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)
- [<span data-ttu-id="d5b9f-119">캐시 정책 조작 -최대 사용 기간 및 최대 부실</span><span class="sxs-lookup"><span data-stu-id="d5b9f-119">Cache Policy Interaction—Maximum Age and Maximum Staleness</span></span>](cache-policy-interaction-maximum-age-and-maximum-staleness.md)
