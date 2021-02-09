---
description: '자세한 정보: 네트워크 애플리케이션에 대한 캐시 관리'
title: 네트워크 애플리케이션에 대한 캐시 관리
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 6383403b41440f26b29fbb5a22c5b25ee6aab465
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791675"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="e3f10-103">네트워크 애플리케이션에 대한 캐시 관리</span><span class="sxs-lookup"><span data-stu-id="e3f10-103">Cache Management for Network Applications</span></span>

<span data-ttu-id="e3f10-104">이 항목 및 관련 하위 항목에서는 <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> 및 <xref:System.Net.FtpWebRequest> 클래스를 사용하여 얻은 리소스에 대한 캐싱을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-104">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="e3f10-105">캐시는 애플리케이션에서 요청된 리소스의 임시 스토리지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-105">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="e3f10-106">애플리케이션이 동일한 리소스를 두 번 이상 요청하는 경우 캐시에서 리소스를 반환하여 서버에서 다시 요청하는 오버헤드를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-106">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="e3f10-107">캐싱은 요청된 리소스를 가져오는 데 필요한 시간을 줄여 애플리케이션 성능을 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-107">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="e3f10-108">또한 캐싱은 서버로의 트립 수를 줄여 네트워크 트래픽을 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-108">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="e3f10-109">캐싱은 성능을 개선하지만 애플리케이션에 반환되는 리소스가 부실할 위험, 즉 캐싱을 사용하지 않을 경우 서버에서 전송될 리소스와 동일하지 않을 위험이 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-109">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="e3f10-110">캐싱으로 인해 권한 없는 사용자 또는 프로세스가 중요한 데이터를 읽을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-110">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="e3f10-111">캐시된 인증된 응답을 추가 인증 없이 캐시에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-111">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="e3f10-112">캐싱을 사용하는 경우 <xref:System.Net.WebRequest.CachePolicy%2A>를 <xref:System.Net.Cache.RequestCacheLevel.BypassCache> 또는 <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore>로 변경하여 이 요청에 대해 캐싱을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-112">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="e3f10-113">보안 문제로 인해 중간 계층 시나리오에는 캐싱이 권장되지 **않습니다**.</span><span class="sxs-lookup"><span data-stu-id="e3f10-113">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3f10-114">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="e3f10-114">In This Section</span></span>  

 [<span data-ttu-id="e3f10-115">캐시 정책</span><span class="sxs-lookup"><span data-stu-id="e3f10-115">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="e3f10-116">캐시 정책이란 무엇이고 어떻게 정의하는지를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-116">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="e3f10-117">위치 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="e3f10-117">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="e3f10-118">Hypertext Transfer Protocol(http 및 https) 리소스에 사용 가능한 각 위치 기반 캐시 정책 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-118">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="e3f10-119">시간 기반 캐시 정책</span><span class="sxs-lookup"><span data-stu-id="e3f10-119">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="e3f10-120">시간 기반 캐시 정책을 사용자 지정하는 데 사용할 수 있는 조건을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-120">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="e3f10-121">네트워크 애플리케이션에서 캐싱 구성</span><span class="sxs-lookup"><span data-stu-id="e3f10-121">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="e3f10-122">프로그래밍 방식으로 캐시 정책 및 캐싱을 사용하는 요청을 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-122">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e3f10-123">참조</span><span class="sxs-lookup"><span data-stu-id="e3f10-123">Reference</span></span>  

 <xref:System.Net.Cache>  
 <span data-ttu-id="e3f10-124"><xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest> 및 <xref:System.Net.FtpWebRequest> 클래스를 사용하여 얻은 리소스에 대한 캐시 정책을 정의하는 데 사용되는 형식과 열거형을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e3f10-124">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>
