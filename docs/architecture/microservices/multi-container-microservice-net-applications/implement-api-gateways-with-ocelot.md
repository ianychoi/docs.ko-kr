---
title: Ocelot을 사용하여 API 게이트웨이 구현
description: Ocelot을 사용하여 API 게이트웨이를 구현하는 방법과 컨테이너 기반 환경에서 Ocelot을 사용하는 방법을 알아봅니다.
ms.date: 03/02/2020
ms.openlocfilehash: 6d9229228e228b664a602ce9a682d435505a8107
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718100"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="bfac2-103">Ocelot을 사용하여 API 게이트웨이 구현</span><span class="sxs-lookup"><span data-stu-id="bfac2-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bfac2-104">참조 마이크로 서비스 애플리케이션 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)는 현재 [Envoy](https://www.envoyproxy.io/)에서 제공하는 기능을 사용하여 이전에 참조된 [Ocelot](https://github.com/ThreeMammals/Ocelot) 대신 API 게이트웨이를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="bfac2-105">Envoy가 eShopOnContainers에서 구현되는 새로운 gRPC 서비스 간 통신에 필요한 WebSocket 프로토콜을 기본적으로 지원하기 때문에 이 디자인을 선택했습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="bfac2-106">그러나 가이드에서는 프로덕션 등급 시나리오에 적합한 간단하고, 사용할 수 있고, 가벼운 API 게이트웨이로 Ocelot을 고려할 수 있도록 이 섹션을 할애했습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>
> <span data-ttu-id="bfac2-107">또한 최신 Ocelot 버전의 json 스키마에는 호환성이 손상되는 변경 사항이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-107">Also, latest Ocelot version contains a breaking change on its json schema.</span></span> <span data-ttu-id="bfac2-108">Ocelot v16.0.0 이전 버전을 사용하거나 ReRoutes 대신 Routes 키를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-108">Consider using Ocelot < v16.0.0, or use the key Routes instead of ReRoutes.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="bfac2-109">API 게이트웨이 구성 및 설계</span><span class="sxs-lookup"><span data-stu-id="bfac2-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="bfac2-110">다음 아키텍처 다이어그램에서는 eShopOnContainers에서 Ocelot을 사용하여 API 게이트웨이를 구현한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-110">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![eShopOnContainers 아키텍처를 보여주는 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="bfac2-112">**그림 6-28**</span><span class="sxs-lookup"><span data-stu-id="bfac2-112">**Figure 6-28**.</span></span> <span data-ttu-id="bfac2-113">API 게이트웨이가 있는 eShopOnContainers 아키텍처</span><span class="sxs-lookup"><span data-stu-id="bfac2-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="bfac2-114">이 다이어그램에서는 "Windows용 Docker" 또는 "Mac용 Docker"를 사용하여 전체 애플리케이션을 단일 Docker 호스트 또는 개발 PC에 배포하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="bfac2-115">그러나 모든 오케스트레이터에 배포하는 것은 비슷하지만, 다이어그램의 모든 컨테이너는 오케스트레이터에서 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-115">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="bfac2-116">또한 데이터베이스, 캐시 및 메시지 broker와 같은 인프라 자산을 오케스트레이터에서 오프로드하여 인프라용 고가용성 시스템(예: Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus 또는 온-프레미스의 모든 HA 클러스터링 솔루션)에 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="bfac2-117">다이어그램에서 알 수 있듯이 여러 API 게이트웨이를 사용하면 마이크로 서비스와 관련 API 게이트웨이를 개발하고 배포할 때 여러 개발 팀에서 자율적으로 운영할 수 있습니다(이 경우 마케팅 기능 대 쇼핑 기능).</span><span class="sxs-lookup"><span data-stu-id="bfac2-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="bfac2-118">단일 모놀리식 API 게이트웨이가 있으면 여러 개발 팀에서 단일 지점을 업데이트해야 하므로 모든 마이크로 서비스를 애플리케이션의 단일 부분으로 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="bfac2-119">설계 측면에서 더 나아가, 때로는 세분화된 API 게이트웨이가 선택한 아키텍처에 따라 단일 비즈니스 마이크로 서비스로 제한될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="bfac2-120">API 게이트웨이의 경계가 비즈니스 또는 도메인에 의해 결정되면 더 나은 디자인을 얻는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-120">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="bfac2-121">예를 들어, 세분화된 API 게이트웨이 계층의 개념은 UI 컴퍼지션 서비스와 비슷하므로 세분화된 API 게이트웨이 계층은 마이크로 서비스 기반의 향상된 복합 UI 애플리케이션에 특히 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="bfac2-122">자세한 내용은 이전 섹션 [마이크로 서비스 기반 복합 UI 만들기](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)에서 자세히 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="bfac2-123">중요한 사항으로, 많은 중대형 애플리케이션의 경우 사용자 지정 API 게이트웨이 제품을 사용하는 것이 일반적으로 좋은 방법이지만, API 게이트웨이에서 자치 마이크로 서비스를 만드는 여러 개발 팀에 독립적인 여러 구성 영역을 허용하지 않는 한 단일 모놀리식 집계 또는 고유한 사용자 지정 중앙 API 게이트웨이가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="bfac2-124">API 게이트웨이를 통해 다시 라우팅하는 마이크로 서비스/컨테이너 샘플</span><span class="sxs-lookup"><span data-stu-id="bfac2-124">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="bfac2-125">예를 들어 eShopOnContainers에는 다음 이미지와 같이 API 게이트웨이를 통해 게시되어야 하는 약 6개의 내부 마이크로 서비스 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![하위 폴더가 표시된 서비스 폴더의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="bfac2-127">**그림 6-29**</span><span class="sxs-lookup"><span data-stu-id="bfac2-127">**Figure 6-29**.</span></span> <span data-ttu-id="bfac2-128">Visual Studio에서 eShopOnContainers 솔루션의 마이크로 서비스 폴더</span><span class="sxs-lookup"><span data-stu-id="bfac2-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="bfac2-129">ID 서비스에 대한 설계에서 이 서비스는 시스템에서 유일한 교차 편집 문제이므로 API 게이트웨이 라우팅에서 빠져 있지만 Ocelot을 사용하면 재라우팅 목록의 일부로 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="bfac2-130">코드에서 알 수 있듯이 이러한 모든 서비스는 현재 ASP.NET Core Web API 서비스로 구현되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="bfac2-131">Catalog 마이크로 서비스 코드와 같은 마이크로 서비스 중 하나를 중점적으로 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-131">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Catalog.API 프로젝트 콘텐츠가 표시된 솔루션 탐색기의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="bfac2-133">**그림 6-30**</span><span class="sxs-lookup"><span data-stu-id="bfac2-133">**Figure 6-30**.</span></span> <span data-ttu-id="bfac2-134">Web API 마이크로 서비스(Catalog 마이크로 서비스) 샘플</span><span class="sxs-lookup"><span data-stu-id="bfac2-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="bfac2-135">Catalog(카탈로그) 마이크로 서비스는 다음 코드와 같은 몇 가지 컨트롤러와 메서드가 있는 일반적인 ASP.NET Core Web API 프로젝트임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="bfac2-136">HTTP 요청은 마이크로 서비스 데이터베이스에 액세스하는 종류의 C# 코드 및 필수 추가 작업을 실행하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="bfac2-137">마이크로 서비스 URL과 관련하여 컨테이너가 로컬 개발 PC(로컬 Docker 호스트)에 배포되면 각 마이크로 서비스의 컨테이너에는 항상 다음 Dockerfile과 같이 Dockerfile에 지정된 내부 포트(일반적으로 포트 80)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container always has an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="bfac2-138">코드에 표시된 포트 80은 Docker 호스트 내부에 있으므로 클라이언트 앱에서 연결할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="bfac2-139">클라이언트 앱은 `docker-compose`를 사용하여 배포할 때 게시된 외부 포트(있는 경우)에만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="bfac2-140">프로덕션 환경에 배포하는 경우 이러한 외부 포트는 게시되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="bfac2-141">이는 정확히 클라이언트 응용 프로그램과 마이크로 서비스 간의 직접 통신을 방지하기 위해 API 게이트웨이를 사용하려는 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="bfac2-142">그러나 개발하는 경우에는 마이크로 서비스/컨테이너에 직접 액세스하여 Swagger를 통해 실행하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="bfac2-143">이로 인해 eShopOnContainers에서 외부 포트는 API 게이트웨이 또는 클라이언트 애플리케이션에서 사용되지 않는 경우에도 계속 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-143">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="bfac2-144">다음은 Catalog 마이크로 서비스에 대한 `docker-compose.override.yml` 파일의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-144">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="bfac2-145">docker-compose.override.yml 구성에서 Catalog 컨테이너에 대한 내부 포트는 80 포트이지만 외부 액세스에 대한 포트가 5101임을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="bfac2-146">그러나 이 포트는 API 게이트웨이를 사용할 때 애플리케이션에서 사용할 수 없으며, Catalog 마이크로 서비스만 디버그, 실행 및 테스트할 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-146">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="bfac2-147">일반적으로 마이크로 서비스에 적합한 프로덕션 배포 환경은 Kubernetes 또는 Service Fabric과 같은 오케스트레이터이므로 docker-compose를 사용하여 프로덕션 환경에 배포하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-147">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="bfac2-148">이러한 환경에 배포하는 경우에는 마이크로 서비스용 외부 포트를 직접 게시하지 않는 다른 구성 파일을 사용하지만 항상 API 게이트웨이로부터 역방향 프록시를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-148">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="bfac2-149">로컬 Docker 호스트에서 Catalog 마이크로 서비스를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-149">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="bfac2-150">Visual Studio에서 전체 eShopOnContainers 솔루션을 실행하거나(Docker-Compose 파일의 모든 서비스 실행) CMD 또는 PowerShell에서 `docker-compose.yml` 및 `docker-compose.override.yml`이 배치된 폴더에 있는 CMD 또는 PowerShell에서 다음 Docker-Compose 명령으로 Catalog 마이크로 서비스를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-150">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="bfac2-151">이 명령은 catalog-api 서비스 컨테이너와 docker-compose.yml에 지정된 종속성만 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-151">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="bfac2-152">이 경우 SQL Server 컨테이너와 RabbitMQ 컨테이너가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-152">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="bfac2-153">그런 다음, Catalog 마이크로 서비스에 직접 액세스하고 해당 "외부" 포트(이 경우 `http://localhost:5101/swagger`)를 통해 직접 액세스하는 Swagger UI를 통해 해당 메서드를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-153">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Catalog.API REST API가 표시된 Swagger UI의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="bfac2-155">**그림 6-31**</span><span class="sxs-lookup"><span data-stu-id="bfac2-155">**Figure 6-31**.</span></span> <span data-ttu-id="bfac2-156">Swagger UI를 사용하여 Catalog 마이크로 서비스 테스트</span><span class="sxs-lookup"><span data-stu-id="bfac2-156">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="bfac2-157">이 시점에서 Visual Studio에서 C# 코드에 중단점을 설정하고, Swagger UI에 노출된 메서드를 사용하여 마이크로 서비스를 테스트한 다음, 마지막으로 `docker-compose down` 명령을 사용하여 모든 항목을 정리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-157">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="bfac2-158">그러나 5101 외부 포트를 통한 경우 마이크로 서비스에 대한 직접 액세스 통신은 정확히 애플리케이션에서 방지하려는 내용입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-158">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="bfac2-159">그리고 API 게이트웨이(이 경우 Ocelot)의 간접 참조에 대한 추가 수준을 설정하여 이를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-159">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="bfac2-160">클라이언트 애플리케이션은 이러한 방식으로 마이크로 서비스에 직접 액세스하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-160">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="bfac2-161">Ocelot을 사용하여 API 게이트웨이 구현</span><span class="sxs-lookup"><span data-stu-id="bfac2-161">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="bfac2-162">Ocelot은 기본적으로 특정 순서로 적용할 수 있는 일단의 미들웨어입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-162">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="bfac2-163">Ocelot은 ASP.NET Core에서만 작동하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-163">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="bfac2-164">최신 버전의 패키지는 `.NETCoreApp 3.1`을 대상으로 하므로 .NET Framework 애플리케이션에 적합하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-164">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="bfac2-165">Visual Studio에서 [Ocelot의 NuGet 패키지](https://www.nuget.org/packages/Ocelot/)를 사용하여 ASP.NET Core 프로젝트에 Ocelot 및 해당 종속성을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-165">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="bfac2-166">eShopOnContainers에서 API 게이트웨이 구현은 간단한 ASP.NET Core WebHost 프로젝트이며, Ocelot의 미들웨어에서 다음 이미지와 같이 모든 API 게이트웨이 기능을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-166">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Ocelot API 게이트웨이 프로젝트가 표시된 솔루션 탐색기의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="bfac2-168">**그림 6-32**</span><span class="sxs-lookup"><span data-stu-id="bfac2-168">**Figure 6-32**.</span></span> <span data-ttu-id="bfac2-169">eShopOnContainers의 OcelotApiGw 기본 프로젝트</span><span class="sxs-lookup"><span data-stu-id="bfac2-169">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="bfac2-170">이 ASP.NET Core WebHost 프로젝트는 기본적으로 간단한 두 개의 파일(`Program.cs` 및 `Startup.cs`)로 빌드됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-170">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="bfac2-171">Program.cs는 일반적인 ASP.NET Core BuildWebHost를 만들고 구성하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-171">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="bfac2-172">여기서 Ocelot에 대해 중요한 점은 `AddJsonFile()` 메서드를 통해 작성기에 제공해야 하는 `configuration.json` 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-172">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="bfac2-173">이 `configuration.json`은 모든 API 게이트웨이 ReRoutes를 지정하는 곳입니다. 특정 포트가 있는 외부 엔드포인트 및 상관 관계가 있는 내부 엔드포인트를 의미하며, 일반적으로 서로 다른 포트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-173">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="bfac2-174">구성에는</span><span class="sxs-lookup"><span data-stu-id="bfac2-174">There are two sections to the configuration.</span></span> <span data-ttu-id="bfac2-175">재라우팅의 배열과 전역 구성의 두 가지 섹션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-175">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="bfac2-176">재라우팅은 업스트림 요청을 처리하는 방법을 Ocelot에 알려주는 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-176">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="bfac2-177">전역 구성을 사용하면 재라우팅 특정 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-177">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="bfac2-178">이는 많은 재라우팅 특정 설정을 관리하지 않으려는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-178">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="bfac2-179">eShopOnContainers의 API 게이트웨이 중 하나에 있는 [ 구성 파일](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)을 간단히 보여주는 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-179">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="bfac2-180">Ocelot API 게이트웨이의 주요 기능은 들어오는 HTTP 요청을 가져오고, 현재 다른 HTTP 요청으로 다운스트림 서비스에 전달하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-180">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="bfac2-181">Ocelot은 한 요청에서 다른 요청으로의 라우팅을 재라우팅으로 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-181">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="bfac2-182">예를 들어 위의 configuration.json에 있는 재라우팅 중 하나인 Basket 마이크로 서비스의 구성을 중점적으로 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-182">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="bfac2-183">DownstreamPathTemplate, Scheme 및 DownstreamHostAndPorts는 이 요청이 전달되는 내부 마이크로 서비스 URL을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-183">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="bfac2-184">포트는 서비스에서 사용하는 내부 포트입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-184">The port is the internal port used by the service.</span></span> <span data-ttu-id="bfac2-185">컨테이너를 사용하는 경우 포트는 dockerfile에 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-185">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="bfac2-186">`Host`는 사용하는 서비스 이름 확인에 따라 달라지는 서비스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-186">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="bfac2-187">docker-compose를 사용하는 경우 서비스 이름은 docker-compose 파일에 제공된 서비스 이름을 사용하는 Docker 호스트에서 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-187">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="bfac2-188">Kubernetes 또는 Service Fabric과 같은 오케스트레이터를 사용하는 경우 해당 이름은 각 오케스트레이터에서 제공한 DNS 또는 이름 확인을 통해 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-188">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="bfac2-189">DownstreamHostAndPorts는 요청을 전달하려는 모든 다운스트림 서비스의 호스트와 포트를 포함하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-189">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="bfac2-190">일반적으로 이 배열에는 하나의 항목만 포함되지만, 때로는 요청의 부하를 다운스트림 서비스에 분산하려는 경우가 있으며 Ocelot을 사용하면 둘 이상의 항목을 추가한 다음, 부하 분산 장치를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-190">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="bfac2-191">그러나 Azure와 모든 오케스트레이터를 사용하는 경우 클라우드 및 오케스트레이터 인프라의 부하를 분산하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-191">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="bfac2-192">UpstreamPathTemplate은 Ocelot에서 클라이언트로부터 지정된 요청에 사용할 DownstreamPathTemplate을 식별하는 데 사용할 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-192">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="bfac2-193">마지막으로, Ocelot에서 동일한 URL에 대한 다른 요청(GET, POST, PUT)을 구별할 수 있도록 UpstreamHttpMethod를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-193">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="bfac2-194">이 시점에서 하나 또는 여러 개의 [병합된 configuration.json 파일](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)을 사용하여 단일 Ocelot API 게이트웨이(ASP.NET Core WebHost)를 만들거나 [Consul KV 저장소에 구성을 저장](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-194">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="bfac2-195">그러나 구성 및 설계 섹션에서 소개한 대로 자치 마이크로 서비스를 실제로 원하는 경우, 단일 모놀리식 API 게이트웨이를 여러 API 게이트웨이 및/또는 BFF(프런트 엔드에 대한 백 엔드)로 분할하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-195">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="bfac2-196">이를 위해 Docker 컨테이너를 사용하여 이 방법을 구현하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-196">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="bfac2-197">단일 Docker 컨테이너 이미지를 사용하여 별도의 여러 API 게이트웨이/BFF 컨테이너 유형 실행</span><span class="sxs-lookup"><span data-stu-id="bfac2-197">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="bfac2-198">eShopOnContainers에서 Ocelot API 게이트웨이를 사용하여 단일 Docker 컨테이너 이미지를 사용하지만, 실행 시 각 서비스에 다른 PC 폴더에 액세스하기 위해 Docker 볼륨을 사용하는 다른 configuration.json 파일을 제공하여 각 형식의 API-Gateway/BFF에 대해 다른 서비스/컨테이너를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-198">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![모든 API 게이트웨이에 대한 단일 Ocelot 게이트웨이 Docker 이미지의 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="bfac2-200">**그림 6-33**</span><span class="sxs-lookup"><span data-stu-id="bfac2-200">**Figure 6-33**.</span></span> <span data-ttu-id="bfac2-201">여러 API 게이트웨이 유형에서 단일 Ocelot Docker 이미지 재사용</span><span class="sxs-lookup"><span data-stu-id="bfac2-201">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="bfac2-202">eShopOnContainers에서는 "OcelotApiGw"라는 프로젝트와 docker-compose.yml 파일에 지정된 "eshop/ocelotapigw" 이미지 이름을 사용하여 "제네릭 Ocelot API 게이트웨이 Docker 이미지"가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-202">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="bfac2-203">그런 다음, Docker에 배포하면 docker-compose.yml 파일에서 나오는 다음 추출과 같이 동일한 Docker 이미지에서 만들어진 네 개의 API 게이트웨이 컨테이너가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-203">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="bfac2-204">또한 다음 docker-compose.override.yml 파일에서 볼 수 있듯이 이러한 API 게이트웨이 컨테이너 간의 유일한 차이점은 Ocelot 구성 파일입니다. 이 파일은 각 서비스 컨테이너마다 다르며, 런타임 시 Docker 볼륨을 통해 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-204">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="bfac2-205">앞의 코드와 아래의 Visual Studio 탐색기에서 보여 주듯이 네 개의 API 게이트웨이가 동일한 Docker 이미지를 기반으로 하므로 각 특정 비즈니스/BFF API 게이트웨이를 정의하는 데 필요한 유일한 파일은 configuration.json 파일뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-205">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![configuration.json 파일을 사용하는 모든 API 게이트웨이를 보여주는 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="bfac2-207">**그림 6-34**</span><span class="sxs-lookup"><span data-stu-id="bfac2-207">**Figure 6-34**.</span></span> <span data-ttu-id="bfac2-208">Ocelot을 사용하여 각 API 게이트웨이/BFF를 정의하는 데 필요한 유일한 구성 파일</span><span class="sxs-lookup"><span data-stu-id="bfac2-208">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="bfac2-209">API 게이트웨이를 여러 API 게이트웨이로 분할하면 마이크로 서비스의 여러 하위 집합에 집중하는 여러 개발 팀에서 독립적인 Ocelot 구성 파일을 사용하여 자신의 API 게이트웨이를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-209">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="bfac2-210">이와 동시에 Ocelot Docker 이미지를 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-210">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="bfac2-211">이제 API 게이트웨이(eShopOnContainers-ServicesAndWebApps.sln 솔루션을 열거나 "docker-compose up"을 실행하는 경우 기본적으로 VS에 포함됨)를 사용하여 eShopOnContainers를 실행하면 다음과 같은 샘플 경로가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-211">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="bfac2-212">예를 들어 webshoppingapigw API 게이트웨이에서 제공하는 업스트림 URL(`http://localhost:5202/api/v1/c/catalog/items/2/`)을 방문하면 다음 브라우저와 같이 Docker 호스트 내의 내부 다운스트림 URL(`http://catalog-api/api/v1/2`)에서 동일한 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-212">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![API 게이트웨이를 통해 전달되는 응답을 보여주는 브라우저의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="bfac2-214">**그림 6-35**</span><span class="sxs-lookup"><span data-stu-id="bfac2-214">**Figure 6-35**.</span></span> <span data-ttu-id="bfac2-215">API 게이트웨이에서 제공하는 URL을 통해 마이크로 서비스에 액세스</span><span class="sxs-lookup"><span data-stu-id="bfac2-215">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="bfac2-216">테스트 또는 디버깅 이유로 인해 API 게이트웨이를 통과하지 않고 Catalog Docker 컨테이너에 직접 액세스하려는 경우(개발 환경에서만), 'catalog-api'는 Docker 호스트 내부의 DNS 확인(docker-compose 서비스 이름으로 처리되는 서비스 검색)이므로 컨테이너에 직접 액세스하는 유일한 방법은 다음 브라우저의 `http://localhost:5101/api/v1/Catalog/items/1`과 같이 개발 테스트용으로만 제공되는 docker-compose.override.yml에 게시된 외부 포트를 통해 액세스하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-216">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Catalog.api에 대한 직접적 응답을 보여주는 브라우저의 스크린샷입니다.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="bfac2-218">**그림 6-36**</span><span class="sxs-lookup"><span data-stu-id="bfac2-218">**Figure 6-36**.</span></span> <span data-ttu-id="bfac2-219">테스트 목적으로 마이크로 서비스에 직접 액세스</span><span class="sxs-lookup"><span data-stu-id="bfac2-219">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="bfac2-220">그러나 애플리케이션은 직접 포트 "바로 가기"가 아니라 API 게이트웨이를 통해 모든 마이크로 서비스에 액세스하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-220">But the application is configured so it accesses all the microservices through the API Gateways, not through the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="bfac2-221">eShopOnContainers의 게이트웨이 집계 패턴</span><span class="sxs-lookup"><span data-stu-id="bfac2-221">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="bfac2-222">앞에서 설명한 대로 요청 집계를 구현하는 유연한 방법은 코드에서 사용자 지정 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-222">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="bfac2-223">또한 [Ocelot의 요청 집계 기능](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)을 사용하여 요청 집계를 구현할 수 있지만 필요에 따라 유연하지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-223">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="bfac2-224">따라서 eShopOnContainers에서 집계를 구현하기 위해 선택한 방법은 각 집계에 대해 ASP.NET Core Web API 서비스를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-224">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="bfac2-225">이 방법에 따르면 앞에서 표시된 간소화된 글로벌 아키텍처 다이어그램에 표시되지 않은 집계 서비스를 고려하면 API 게이트웨이 컴퍼지션 다이어그램은 실제로 조금 더 확대됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-225">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="bfac2-226">다음 다이어그램에서는 집계 서비스에서 관련 API 게이트웨이를 사용하는 방식도 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-226">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![집계 서비스를 보여주는 eShopOnContainers 아키텍처의 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="bfac2-228">**그림 6-37**</span><span class="sxs-lookup"><span data-stu-id="bfac2-228">**Figure 6-37**.</span></span> <span data-ttu-id="bfac2-229">집계 서비스가 있는 eShopOnContainers 아키텍처</span><span class="sxs-lookup"><span data-stu-id="bfac2-229">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="bfac2-230">더 확대하면 다음 이미지의 "쇼핑" 비즈니스 영역에서 API 게이트웨이에서 수집기 서비스를 사용하는 경우 클라이언트 앱과 마이크로 서비스 간에 전송량이 감소되었음을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-230">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![eShopOnContainers 아키텍처 확대를 보여주는 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="bfac2-232">**그림 6-38**</span><span class="sxs-lookup"><span data-stu-id="bfac2-232">**Figure 6-38**.</span></span> <span data-ttu-id="bfac2-233">집계 서비스의 비전 확대</span><span class="sxs-lookup"><span data-stu-id="bfac2-233">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="bfac2-234">다이어그램에 API 게이트웨이에서 들어오는 가능한 요청이 표시되는 경우 이는 매우 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-234">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="bfac2-235">클라이언트 응용 프로그램 관점에서 청색 화살표가 간소화될 수 있는 방법을 알 수 있지만, 통신의 데이터 전송량과 대기 시간을 줄여 집계 패턴을 사용하는 경우 궁극적으로 특히 원격 응용 프로그램(모바일 및 SPA 응용 프로그램)의 사용자 환경이 크게 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-235">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="bfac2-236">"마케팅" 비즈니스 영역 및 마이크로 서비스의 경우 매우 간단한 사용 사례이므로 집계를 사용할 필요는 없지만 필요한 경우 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-236">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="bfac2-237">Ocelot API 게이트웨이의 인증 및 권한 부여</span><span class="sxs-lookup"><span data-stu-id="bfac2-237">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="bfac2-238">Ocelot API 게이트웨이에서 권한 부여 토큰을 제공하는 [IdentityServer](https://identityserver.io/)를 통해 API 게이트웨이 외부 또는 내부에 인증 서비스(예: ASP.NET Core Web API 서비스)를 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-238">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="bfac2-239">eShopOnContainers는 BFF 및 비즈니스 영역에 따른 경계가 있는 여러 개의 API 게이트웨이를 사용하므로 다음 다이어그램에서 노란색으로 강조 표시된 대로 Identity/Auth(ID/권한 부여) 서비스는 API 게이트웨이에서 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-239">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![API 게이트웨이 아래의 ID 마이크로 서비스를 보여주는 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="bfac2-241">**그림 6-39**</span><span class="sxs-lookup"><span data-stu-id="bfac2-241">**Figure 6-39**.</span></span> <span data-ttu-id="bfac2-242">eShopOnContainers에서 Identity 서비스의 위치</span><span class="sxs-lookup"><span data-stu-id="bfac2-242">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="bfac2-243">그러나 Ocelot은 다른 다이어그램과 같이 API 게이트웨이 경계 내에 ID/인증 마이크로 서비스를 배치하도록 지원할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-243">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Ocelot API 게이트웨이의 인증을 보여주는 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="bfac2-245">**그림 6-40**</span><span class="sxs-lookup"><span data-stu-id="bfac2-245">**Figure 6-40**.</span></span> <span data-ttu-id="bfac2-246">Ocelot에서 인증</span><span class="sxs-lookup"><span data-stu-id="bfac2-246">Authentication in Ocelot</span></span>

<span data-ttu-id="bfac2-247">이전 다이어그램에 표시된 것처럼 ID 마이크로 서비스가 API 게이트웨이(AG)의 아래에 있으면 다음과 같이 됩니다. 1) AG는 ID 마이크로 서비스에서 인증 토큰을 요청하고, 2) ID 마이크로 서비스는 AG에 토큰을 반환하고, 3-4) AG는 인증 토큰을 사용하여 마이크로 서비스에서 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-247">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="bfac2-248">eShopOnContainers 애플리케이션에서 API 게이트웨이를 여러 BFF(Backend for Frontend) 및 비즈니스 영역 API 게이트웨이로 분할했으므로 교차 편집 문제에 대한 추가 API 게이트웨이를 만드는 것이 또 다른 옵션이었습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-248">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="bfac2-249">이 선택은 여러 교차 편집 문제 마이크로 서비스가 있는 더 복잡한 마이크로 서비스 기반 아키텍처에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-249">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="bfac2-250">eShopOnContainers에는 하나의 교차 편집 문제만 있으므로 간단히 하기 위해 API 게이트웨이 영역에서 보안 서비스를 처리하기로 결정했습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-250">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="bfac2-251">어떤 경우이든 응용 프로그램이 API 게이트웨이 수준에서 보안이 설정되면 보안 마이크로 서비스를 사용하려고 할 때 Ocelot API 게이트웨이의 인증 모듈을 처음 방문합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-251">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="bfac2-252">이렇게 하면 액세스 토큰을 가져오기 위해 Identity 또는 Auth 마이크로 서비스를 방문하도록 HTTP 요청을 리디렉션하므로 access_token으로 보호된 서비스를 방문할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-252">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="bfac2-253">API 게이트웨이 수준에서 인증을 통해 모든 서비스를 보호하는 방법은 configuration.json의 관련 설정에서 AuthenticationProviderKey를 설정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-253">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="bfac2-254">Ocelot이 실행되면 AuthenticationOptions.AuthenticationProviderKey 재라우팅을 살펴보고 지정된 키에 등록된 인증 공급자가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-254">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="bfac2-255">해당 공급자가 없는 경우 Ocelot이 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-255">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="bfac2-256">있는 경우 실행할 때 재라우팅에서 해당 공급자를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-256">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="bfac2-257">Ocelot WebHost는 `authenticationProviderKey = "IdentityApiKey"`를 사용하여 구성되므로 권한 부여 토큰이 없는 요청이 서비스에 있을 때마다 인증이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-257">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="bfac2-258">그런 다음, 다음 Basket 마이크로 서비스 컨트롤러와 같이 마이크로 서비스처럼 액세스할 모든 리소스에 대해 [Authorize] 특성을 사용하여 권한 부여를 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-258">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="bfac2-259">"basket"과 같은 ValidAudiences는 아래 코드와 같이 스타트업 클래스의 ConfigureServices()에서 `AddJwtBearer()`를 사용하여 각 마이크로 서비스에 정의된 대상과 상관 관계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-259">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="bfac2-260">`http://localhost:5202/api/v1/b/basket/1`과 같은 API 게이트웨이를 기반으로 하는 재라우팅 URL을 사용하여 Basket 마이크로 서비스와 같은 보안 마이크로 서비스에 액세스하려고 할 때 유효한 토큰을 제공하지 않으면 401 권한 없음이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-260">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="bfac2-261">반면에 재라우팅 URL이 인증되면 Ocelot에서 이(내부 마이크로 서비스 URL)와 연결된 다운스트림 구성표를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-261">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="bfac2-262">**Ocelot의 재라우팅 계층에서 권한 부여**</span><span class="sxs-lookup"><span data-stu-id="bfac2-262">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="bfac2-263">Ocelot은 인증 후에 평가된 클레임 기반 권한 부여를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-263">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="bfac2-264">재라우팅 구성에 다음 줄을 추가하여 경로 수준에서 권한 부여를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-264">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="bfac2-265">이 예제에서 권한 부여 미들웨어가 호출되면 Ocelot에서 사용자의 토큰에 'UserType' 클레임 유형이 있고 해당 클레임의 값이 'employee'인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-265">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="bfac2-266">그렇지 않은 경우 해당 사용자에게 권한이 부여되지 않으며 응답은 403 사용할 수 없음이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-266">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="bfac2-267">Kubernetes 수신 및 Ocelot API 게이트웨이 사용</span><span class="sxs-lookup"><span data-stu-id="bfac2-267">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="bfac2-268">Azure Kubernetes Service 클러스터에서처럼 Kubernetes를 사용하는 경우 일반적으로 *Nginx* 를 기반으로 하는 [Kubernetes 수신 계층](https://kubernetes.io/docs/concepts/services-networking/ingress/)을 통해 모든 HTTP 요청을 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-268">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="bfac2-269">Kubernetes에서 수신 방식을 사용하지 않으면 서비스와 Pod에 클러스터 네트워크에서만 라우팅할 수 있는 IP가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-269">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="bfac2-270">하지만 수신 방식을 사용하는 경우 인터넷과 서비스(API 게이트웨이 포함) 사이에 역방향 프록시 역할을 하는 중간 계층이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-270">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="bfac2-271">정의에 따라 수신은 인바운드 연결이 클러스터 서비스에 도달할 수 있도록 하는 규칙 모음입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-271">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="bfac2-272">수신은 일반적으로 외부에서 연결할 수 있는 URL, 부하 분산 트래픽, SSL 종료 등의 서비스를 제공하도록 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-272">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="bfac2-273">사용자는 수신 리소스를 API 서버에 POST(게시)하여 수신을 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-273">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="bfac2-274">eShopOnContainers에서 로컬로 개발하고 개발 머신을 Docker 호스트로만 사용하는 경우 수신이 아니라 여러 API 게이트웨이만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-274">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="bfac2-275">그러나 Kubernetes를 기반으로 한 "프로덕션" 환경을 대상으로 하는 경우 eShopOnContainers에서는 API 게이트웨이 앞에 수신을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-275">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="bfac2-276">그러면 클라이언트에서 동일한 기본 URL을 계속 호출하지만 요청은 여러 API 게이트웨이 또는 BFF로 라우팅됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-276">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="bfac2-277">API 게이트웨이는 일반적으로 서비스 범위를 벗어나는 웹 애플리케이션이 아닌 서비스만 표시하는 프런트 엔드 또는 외관입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-277">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="bfac2-278">또한 API 게이트웨이는 특정 내부 마이크로 서비스를 숨길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-278">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="bfac2-279">하지만 수신은 HTTP 요청만 리디렉션하고, 마이크로 서비스 또는 웹앱을 숨기려고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-279">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="bfac2-280">다음 다이어그램과 같이 Kubernetes에서 웹 애플리케이션과 여러 Ocelot API 게이트웨이/BFF 앞에 수신 Nginx 계층이 있는 것이 이상적인 아키텍처입니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-280">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![수신 계층이 AKS 환경에 얼마나 적합한지 보여주는 다이어그램입니다.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="bfac2-282">**그림 6-41**</span><span class="sxs-lookup"><span data-stu-id="bfac2-282">**Figure 6-41**.</span></span> <span data-ttu-id="bfac2-283">Kubernetes에 배포 시 eShopOnContainers의 수신 계층</span><span class="sxs-lookup"><span data-stu-id="bfac2-283">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="bfac2-284">Kubernetes 수신은 일반적으로 API 게이트웨이 범위를 벗어난 웹 애플리케이션을 비롯한 앱의 모든 트래픽에 대해 역방향 프록시로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-284">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="bfac2-285">eShopOnContainers를 Kubernetes에 배포하면 _수신_ 을 통해 몇 가지 서비스 또는 엔드포인트만 노출되며, URL에 대한 접미사 목록은 기본적으로 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-285">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="bfac2-286">`/`: 클라이언트 SPA 웹 애플리케이션의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-286">`/` for the client SPA web application</span></span>
- <span data-ttu-id="bfac2-287">`/webmvc`: 클라이언트 MVC 웹 애플리케이션의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-287">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="bfac2-288">`/webstatus`: 상태/healthchecks를 표시하는 클라이언트 웹앱의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-288">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="bfac2-289">`/webshoppingapigw`: 웹 BFF 및 쇼핑 비즈니스 프로세스의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-289">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="bfac2-290">`/webmarketingapigw`: 웹 BFF 및 마케팅 비즈니스 프로세스의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-290">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="bfac2-291">`/mobileshoppingapigw`: 모바일 BFF 및 쇼핑 비즈니스 프로세스의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-291">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="bfac2-292">`/mobilemarketingapigw`: 모바일 BFF 및 마케팅 비즈니스 프로세스의 경우</span><span class="sxs-lookup"><span data-stu-id="bfac2-292">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="bfac2-293">Kubernetes에 배포하는 경우 각 Ocelot API 게이트웨이는 API 게이트웨이를 실행하는 각 _Pod_ 에 대해 서로 다른 "configuration.json" 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-293">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="bfac2-294">이러한 "configuration.json" 파일은 'ocelot'이라는 Kubernetes _구성 맵_ 에 따라 만들어진 볼륨을 탑재하여(원래는 deploy.ps1 스크립트 사용) 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-294">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="bfac2-295">각 컨테이너는 `/app/configuration`이라는 컨테이너 폴더에 관련 구성 파일을 탑재합니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-295">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="bfac2-296">eShopOnContainers의 소스 코드 파일에서 원래 "configuration.json" 파일은 `k8s/ocelot/` 폴더 내에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-296">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="bfac2-297">각 BFF/API 게이트웨이마다 하나의 구성 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-297">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="bfac2-298">Ocelot API 게이트웨이의 추가 교차 편집 기능</span><span class="sxs-lookup"><span data-stu-id="bfac2-298">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="bfac2-299">Ocelot API 게이트웨이를 사용하는 경우 연구하고 사용할 다른 중요한 기능이 있으며, 다음 링크에서 설명하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfac2-299">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="bfac2-300">**Consul 또는 Eureka와 Ocelot을 통합한 클라이언트 쪽 서비스 검색** </span><span class="sxs-lookup"><span data-stu-id="bfac2-300">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="bfac2-301">**API 게이트웨이 계층에서 캐싱** </span><span class="sxs-lookup"><span data-stu-id="bfac2-301">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="bfac2-302">**API 게이트웨이 계층에서 로깅** </span><span class="sxs-lookup"><span data-stu-id="bfac2-302">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="bfac2-303">**API 게이트웨이 계층의 서비스 품질(다시 시도 및 회로 차단기)**  </span><span class="sxs-lookup"><span data-stu-id="bfac2-303">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="bfac2-304">**속도 제한** </span><span class="sxs-lookup"><span data-stu-id="bfac2-304">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="bfac2-305">[이전](background-tasks-with-ihostedservice.md)
> [다음](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="bfac2-305">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
