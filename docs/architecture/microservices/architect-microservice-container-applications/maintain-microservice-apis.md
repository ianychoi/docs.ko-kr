---
title: 마이크로 서비스 API 및 계약 만들기, 개선 및 버전 관리
description: 요구 사항의 변화에 따라 발전과 버전을 고려하여 마이크로 서비스 API 및 계약을 작성하세요.
ms.date: 01/13/2021
ms.openlocfilehash: 84eeaa9776947abda6171949c730f8473e97b241
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189462"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a><span data-ttu-id="67dbd-103">마이크로 서비스 API 및 계약 만들기, 개선 및 버전 관리</span><span class="sxs-lookup"><span data-stu-id="67dbd-103">Creating, evolving, and versioning microservice APIs and contracts</span></span>

<span data-ttu-id="67dbd-104">마이크로 서비스 API는 서비스와 클라이언트 간 계약입니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-104">A microservice API is a contract between the service and its clients.</span></span> <span data-ttu-id="67dbd-105">API 계약을 위반하지 않는 경우에만 독립적으로 마이크로 서비스를 확대할 수 있습니다. 계약이 중요한 이유가 바로 여기에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-105">You'll be able to evolve a microservice independently only if you do not break its API contract, which is why the contract is so important.</span></span> <span data-ttu-id="67dbd-106">계약을 변경하면 클라이언트 애플리케이션이나 API 게이트웨이에 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-106">If you change the contract, it will impact your client applications or your API Gateway.</span></span>

<span data-ttu-id="67dbd-107">API 정의의 특성은 사용 중인 프로토콜에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-107">The nature of the API definition depends on which protocol you're using.</span></span> <span data-ttu-id="67dbd-108">예를 들어, 메시징을 사용할 경우(예: [AMQP](http://www.amqp.org/)) API는 메시지 유형으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-108">For instance, if you're using messaging (like [AMQP](http://www.amqp.org/)), the API consists of the message types.</span></span> <span data-ttu-id="67dbd-109">HTTP 및 RESTful 서비스를 사용할 경우 API는 URL과 요청 및 응답 JSON 형식으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-109">If you're using HTTP and RESTful services, the API consists of the URLs and the request and response JSON formats.</span></span>

<span data-ttu-id="67dbd-110">그러나 초기 계약에서 신중했다 하더라도 서비스 API는 시간에 따른 변화가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-110">However, even if you're thoughtful about your initial contract, a service API will need to change over time.</span></span> <span data-ttu-id="67dbd-111">이 상황에서, 특히 API가 여러 클라이언트 애플리케이션에서 사용하는 공개 API인 경우 보통은 모든 클라이언트가 새 API 계약으로 업그레이드하게 강제할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-111">When that happens—and especially if your API is a public API consumed by multiple client applications — you typically can't force all clients to upgrade to your new API contract.</span></span> <span data-ttu-id="67dbd-112">일반적으로 기존 및 새 서비스 계약 버전이 동시 실행되는 방식으로 서비스의 새 버전을 점진적으로 배포하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-112">You usually need to incrementally deploy new versions of a service in a way that both old and new versions of a service contract are running simultaneously.</span></span> <span data-ttu-id="67dbd-113">따라서 서비스 버전 관리를 위한 전략을 갖추는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-113">Therefore, it's important to have a strategy for your service versioning.</span></span>

<span data-ttu-id="67dbd-114">API에 특성이나 매개 변수를 추가하는 경우처럼 API 변경이 작은 경우 이전 API를 사용하는 클라이언트가 새 서비스 버전으로 전환하여 작업할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-114">When the API changes are small, like if you add attributes or parameters to your API, clients that use an older API should switch and work with the new version of the service.</span></span> <span data-ttu-id="67dbd-115">누락된 특성에 대해 필요한 기본값을 제공할 수 있고 클라이언트는 추가 응답 특성을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-115">You might be able to provide default values for any missing attributes that are required, and the clients might be able to ignore any extra response attributes.</span></span>

<span data-ttu-id="67dbd-116">그러나 때로는 서비스 API에 대한 대규모의 호환되지 않는 변경이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-116">However, sometimes you need to make major and incompatible changes to a service API.</span></span> <span data-ttu-id="67dbd-117">클라이언트 애플리케이션이나 서비스가 즉시 새 버전으로 업그레이드하도록 강제할 수 없으므로 서비스는 당분간 기존 API 버전을 지원해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-117">Because you might not be able to force client applications or services to upgrade immediately to the new version, a service must support older versions of the API for some period.</span></span> <span data-ttu-id="67dbd-118">REST와 같은 HTTP 기반 메커니즘을 사용한다면 URL이나 HTTP 헤더에 API 버전 번호를 포함하는 것이 한 방법이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-118">If you're using an HTTP-based mechanism such as REST, one approach is to embed the API version number in the URL or into an HTTP header.</span></span> <span data-ttu-id="67dbd-119">그런 다음, 동일한 서비스 인스턴스 안에서 동시에 두 버전을 모두 구현할지 또는 한 API 버전을 각각 처리하는 다른 인스턴스를 배포할지 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-119">Then you can decide between implementing both versions of the service simultaneously within the same service instance, or deploying different instances that each handle a version of the API.</span></span> <span data-ttu-id="67dbd-120">해당 기능을 위한 좋은 접근 방식은 [중재자 패턴](https://en.wikipedia.org/wiki/Mediator_pattern)(예: [MediatR 라이브러리](https://github.com/jbogard/MediatR))을 통해 서로 다른 구현 버전을 독립 처리기로 분할하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-120">A good approach for this functionality is the [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern) (for example, [MediatR library](https://github.com/jbogard/MediatR)) to decouple the different implementation versions into independent handlers.</span></span>

<span data-ttu-id="67dbd-121">마지막으로 REST 아키텍처를 사용할 경우 서비스 버전 관리와 확대 가능한 API를 위해서 [하이퍼미디어](https://www.infoq.com/articles/mark-baker-hypermedia)가 가장 좋은 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="67dbd-121">Finally, if you're using a REST architecture, [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) is the best solution for versioning your services and allowing evolvable APIs.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67dbd-122">추가 자료</span><span class="sxs-lookup"><span data-stu-id="67dbd-122">Additional resources</span></span>

- <span data-ttu-id="67dbd-123">**Scott Hanselman. 쉬워진 ASP.NET Core RESTful Web API 버전 관리** </span><span class="sxs-lookup"><span data-stu-id="67dbd-123">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="67dbd-124">**RESTful Web API 버전 관리** </span><span class="sxs-lookup"><span data-stu-id="67dbd-124">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="67dbd-125">**Roy Fielding. 버전 관리, 하이퍼미디어 및 REST** </span><span class="sxs-lookup"><span data-stu-id="67dbd-125">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

>[!div class="step-by-step"]
><span data-ttu-id="67dbd-126">[이전](asynchronous-message-based-communication.md)
>[다음](microservices-addressability-service-registry.md)</span><span class="sxs-lookup"><span data-stu-id="67dbd-126">[Previous](asynchronous-message-based-communication.md)
[Next](microservices-addressability-service-registry.md)</span></span>
