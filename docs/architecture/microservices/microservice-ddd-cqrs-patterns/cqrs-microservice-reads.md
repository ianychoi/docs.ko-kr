---
title: CQRS 마이크로 서비스에서 읽기/쿼리 구현
description: 컨테이너화된 .NET 애플리케이션용 .NET 마이크로 서비스 아키텍처 | Dapper를 사용하여 eShopOnContainers의 주문 마이크로 서비스에서 CQRS 쿼리 측면의 구현을 이해합니다.
ms.date: 01/13/2021
ms.openlocfilehash: 047fc3893dcaf72a17d29f5560c928879757d024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188922"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="1f667-103">CQRS 마이크로 서비스에서 읽기/쿼리 구현</span><span class="sxs-lookup"><span data-stu-id="1f667-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="1f667-104">읽기/쿼리의 경우 eShopOnContainers 참조 애플리케이션의 주문 마이크로 서비스에서 DDD 모델 및 트랜잭션 영역과 별도로 쿼리를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="1f667-105">해당 구현은 주로 쿼리와 트랜잭션에 대한 요구가 매우 다르기 때문에 수행되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-105">This implementation was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="1f667-106">쓰기는 도메인 논리와 호환되어야 하는 트랜잭션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="1f667-107">반면에 쿼리는 idempotent(멱등원)이며 도메인 규칙과 분리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="1f667-108">이 접근 방식은 그림 7-3과 같이 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="1f667-109">API 인터페이스는 마이크로 ORM(Object Relational Mapper)(예: Dapper)과 같은 인프라를 사용하는 웹 API 컨트롤러에서 구현되며, UI 애플리케이션의 필요에 따라 동적 ViewModel을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![단순화된 CQRS에서 상위 수준 쿼리 쪽을 보여 주는 다이어그램](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="1f667-111">**그림 7-3**.</span><span class="sxs-lookup"><span data-stu-id="1f667-111">**Figure 7-3**.</span></span> <span data-ttu-id="1f667-112">CQRS 마이크로 서비스에서 가장 간단한 쿼리 방법</span><span class="sxs-lookup"><span data-stu-id="1f667-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="1f667-113">간소화된 CQRS 접근 방식에서 쿼리 측면에 대한 가장 간단한 방법은 데이터베이스를 Dapper 같은 Micro-ORM으로 쿼리하고 동적 ViewModels를 반환함으로써 구현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="1f667-114">쿼리 정의는 데이터베이스를 쿼리하고 각 쿼리에 대해 즉시 작성된 동적 ViewModel을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="1f667-115">쿼리는 idempotent이므로 쿼리 실행 횟수와 관계없이 데이터를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="1f667-116">따라서 집계 및 다른 패턴과 같은 트랜잭션 측면에서 사용되는 DDD 패턴으로 제한할 필요가 없으므로 쿼리가 트랜잭션 영역과 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="1f667-117">데이터베이스에 대해 UI에 필요한 데이터를 쿼리하면, SQL 문 자체를 제외하고 어디서든 정적으로 정의할 필요가 없는 동적 ViewModel(ViewModel에 대한 클래스 없음)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-117">You query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="1f667-118">이 방법은 간단하므로 쿼리 측면(예: [Dapper](https://github.com/StackExchange/Dapper)와 같은 마이크로 ORM을 사용하는 코드)에 필요한 코드는 [동일한 웹 API 프로젝트 내에서](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs) 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-118">Since this approach is simple, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="1f667-119">그림 7-4에서는 해당 접근 방식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-119">Figure 7-4 shows this approach.</span></span> <span data-ttu-id="1f667-120">쿼리는 eShopOnContainers 솔루션 내의 **Ordering.API** 마이크로 서비스 프로젝트에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Ordering.API 프로젝트의 Queries 폴더를 보여 주는 스크린샷](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="1f667-122">**그림 7-4**.</span><span class="sxs-lookup"><span data-stu-id="1f667-122">**Figure 7-4**.</span></span> <span data-ttu-id="1f667-123">eShopOnContainers에서 주문 마이크로 서비스의 쿼리</span><span class="sxs-lookup"><span data-stu-id="1f667-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="1f667-124">도메인 모델 제약 조건과 별도로 클라이언트 앱용으로 특별히 제작된 ViewModels 사용</span><span class="sxs-lookup"><span data-stu-id="1f667-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="1f667-125">쿼리는 클라이언트 애플리케이션에 필요한 데이터를 가져오기 위해 수행되므로 쿼리에서 반환된 데이터에 기반하여 클라이언트에 대해 반환되는 형식을 구체적으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="1f667-126">이러한 모델 또는 DTO(데이터 전송 개체)를 ViewModel이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="1f667-127">반환된 데이터(ViewModel)는 데이터베이스의 여러 엔터티 또는 테이블의 데이터, 심지어 트랜잭션 영역에 대한 도메인 모델에 정의된 여러 집계 간의 데이터를 조인한 결과일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="1f667-128">이 경우 도메인 모델과 별도로 쿼리를 만들기 때문에 집계 경계와 제약 조건은 무시되며 필요한 테이블과 열을 자유롭게 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="1f667-129">이 방법은 쿼리를 만들거나 업데이트하는 데 있어 뛰어난 유연성과 생산성을 개발자에게 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="1f667-130">ViewModels는 주문 마이크로 서비스에서 구현된 것처럼 클래스에 정의된 정적 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-130">The ViewModels can be static types defined in classes (as is implemented in the ordering microservice).</span></span> <span data-ttu-id="1f667-131">또는 수행한 쿼리에 따라 동적으로 생성되어 개발자에게 민첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-131">Or they can be created dynamically based on the queries performed, which is agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="1f667-132">Dapper를 마이크로 ORM으로 사용하여 쿼리를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="1f667-133">마이크로 ORM, Entity Framework Core 또는 일반 ADO.NET을 쿼리에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="1f667-134">샘플 애플리케이션에서 Dapper는 인기 있는 마이크로 ORM의 좋은 예인 eShopOnContainers에서 주문 마이크로 서비스로 선택되었습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="1f667-135">경량 프레임워크이므로 뛰어난 성능으로 일반 SQL 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-135">It can run plain SQL queries with great performance, because it's a light framework.</span></span> <span data-ttu-id="1f667-136">Dapper를 사용하면 여러 테이블에 액세스하고 조인할 수 있는 SQL 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="1f667-137">Dapper는 오픈 소스 프로젝트(원래 Sam Saffron이 만듦)이며 [Stack Overflow](https://stackoverflow.com/)에서 사용되는 구성 요소의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="1f667-138">Dapper를 사용하려면 다음 그림과 같이 [Dapper NuGet 패키지](https://www.nuget.org/packages/Dapper)를 통해 이를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![NuGet 패키지 뷰의 Dapper 패키지를 보여 주는 스크린샷](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="1f667-140">또한 코드에서 Dapper 확장 메서드에 액세스할 수 있도록 `using` 지시문도 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-140">You also need to add a `using` directive so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="1f667-141">코드에서 Dapper를 사용하면 <xref:System.Data.SqlClient> 네임스페이스에서 사용할 수 있는 <xref:System.Data.SqlClient.SqlConnection> 클래스를 직접 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="1f667-142">QueryAsync 메서드 및 <xref:System.Data.SqlClient.SqlConnection> 클래스를 확장하는 다른 확장 메서드를 통해 간단하고 성능이 뛰어난 방식으로 쿼리를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="1f667-143">동적 및 정적 ViewModel</span><span class="sxs-lookup"><span data-stu-id="1f667-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="1f667-144">ViewModels를 서버 쪽에서 클라이언트 앱으로 반환할 때, ViewModels는 클라이언트 앱이 요구하는 방식으로 데이터를 저장하기 때문에 해당 ViewModels를 엔터티 모델의 내부 도메인 엔터티와 다를 수 있는 DTO(데이터 전송 개체)로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="1f667-145">따라서 대부분의 경우 여러 도메인 엔터티에서 가져온 데이터를 집계하고, 클라이언트 앱에서 해당 데이터가 필요한 방식에 따라 ViewModel을 정확하게 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="1f667-146">이러한 ViewModel 또는 DTO는 나중에 코드 조각에 표시된 `OrderSummary` 클래스와 같이 명시적으로(데이터 소유자 클래스로) 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes), like the `OrderSummary` class shown in a later code snippet.</span></span> <span data-ttu-id="1f667-147">또는 쿼리에서 동적 형식으로 반환된 특성에 따라 동적 ViewModel 또는 동적 DTO를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-147">Or, you could just return dynamic ViewModels or dynamic DTOs based on the attributes returned by your queries as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="1f667-148">동적 형식으로 ViewModel 반환</span><span class="sxs-lookup"><span data-stu-id="1f667-148">ViewModel as dynamic type</span></span>

<span data-ttu-id="1f667-149">다음 코드에서 볼 수 있듯이 `ViewModel`은 쿼리에서 반환된 속성에 따라 내부적으로 *동적* 유형을 반환하기만 하면 쿼리에서 직접 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-149">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="1f667-150">즉 반환될 특성의 하위 집합은 쿼리 자체를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-150">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="1f667-151">따라서 쿼리 또는 조인에 새 열을 추가하면 해당 데이터가 반환된 `ViewModel`에 동적으로 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-151">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="1f667-152">중요한 점은 동적 형식을 사용하면 반환되는 데이터 컬렉션이 ViewModel로 동적으로 어셈블된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-152">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="1f667-153">**장점:** 이 방법은 쿼리의 SQL 문장을 업데이트할 때마다 정적 ViewModel 클래스를 수정할 필요성을 줄이므로 이후의 변경과 관련하여 간단하고 빠르게 진화할 수 있도록 코딩할 때 이 디자인 방법을 민첩하게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-153">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="1f667-154">**단점:** 장기적으로 동적 유형은 클라이언트 앱과 서비스의 명확성 및 호환성에 부정적인 영향을 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-154">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="1f667-155">또한 Swashbuckle과 같은 미들웨어 소프트웨어는 동적 유형을 사용하는 경우 반환되는 형식에 대해 동일한 수준의 문서를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-155">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="1f667-156">미리 정의된 DTO 클래스인 ViewModel</span><span class="sxs-lookup"><span data-stu-id="1f667-156">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="1f667-157">**장점**: 명시적 DTO 클래스를 기반으로 하는 "계약"과 같이 미리 정의된 정적 ViewModel 클래스를 사용하면, 동일한 애플리케이션에서만 사용되는 경우에도 퍼블릭 API뿐만 아니라 장기적인 마이크로 서비스에도 확실히 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-157">**Pros**: Having static, predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long-term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="1f667-158">Swagger에 대한 응답 형식을 지정하려면 명시적 DTO 클래스를 반환 형식으로 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-158">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="1f667-159">따라서 미리 정의된 DTO 클래스를 사용하면 Swagger에서 더 많은 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-159">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="1f667-160">API를 사용할 때 API 문서화 및 호환성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-160">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="1f667-161">**단점**: 앞에서 언급했듯이 코드를 업데이트할 때 DTO 클래스를 업데이트하는 데 몇 가지 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-161">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="1f667-162">경험을 기반으로 한 팁: eShopOnContainers의 주문 마이크로 서비스에서 구현된 쿼리에서, 초기 개발 단계에서 간단하고 민첩했기 때문에 동적 ViewModel을 사용하여 개발하기 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-162">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was straightforward and agile on the early development stages.</span></span> <span data-ttu-id="1f667-163">그러나 개발이 안정화된 후에는 API를 리팩터링하고 ViewModel에 정적 또는 미리 정의된 DTO를 사용하도록 했습니다. 이는 마이크로 서비스 소비자에서 명시적 DTO 형식을 인식하고 “계약”으로 사용하는 것이 더 명확하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-163">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="1f667-164">다음 예제에서는 명시적 ViewModel DTO 클래스인 OrderSummary 클래스를 사용하여 쿼리에서 데이터를 반환하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-164">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber,
                  o.[OrderDate] as [date],os.[Name] as [status],
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    }
}
```

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="1f667-165">Web API의 응답 형식 설명</span><span class="sxs-lookup"><span data-stu-id="1f667-165">Describe response types of Web APIs</span></span>

<span data-ttu-id="1f667-166">웹 API 및 마이크로 서비스를 사용하는 개발자는 반환되는 항목, 특히 응답 형식 및 오류 코드 (표준이 아닌 경우)에 많은 관심을 가지고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-166">Developers consuming web APIs and microservices are most concerned with what is returned—specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="1f667-167">응답 형식은 XML 주석과 데이터 주석에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-167">The response types are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="1f667-168">Swagger UI에 적절한 문서화가 없으면 반환되는 형식 또는 반환될 수 있는 HTTP 코드에 대한 정보가 부족하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-168">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="1f667-169">해당 문제는 <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>을 추가하여 해결되므로 다음 코드에서와 같이 Swashbuckle API 반환 모델과 값에 대한 더 풍부한 정보를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-169">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="1f667-170">그러나 `ProducesResponseType` 특성은 다음과 같이 동적 형식을 사용할 수 없지만 `OrderSummary` ViewModel DTO와 같은 명시적 형식을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-170">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="1f667-171">이는 반환된 명시적 형식이 장기적으로 동적 형식보다 더 나은 또 다른 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-171">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="1f667-172">`ProducesResponseType` 특성을 사용할 때 200, 400 등과 같이 가능한 HTTP 오류/코드와 관련하여 예상되는 결과를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-172">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome regarding possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="1f667-173">다음 이미지에서 Swagger UI에서 ResponseType 정보를 표시하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-173">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Ordering API의 Swagger UI 페이지를 보여 주는 스크린샷](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="1f667-175">**그림 7-5**.</span><span class="sxs-lookup"><span data-stu-id="1f667-175">**Figure 7-5**.</span></span> <span data-ttu-id="1f667-176">웹 API에서 응답 형식 및 가능한 HTTP 상태 코드를 보여 주는 Swagger UI</span><span class="sxs-lookup"><span data-stu-id="1f667-176">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="1f667-177">이미지에서는 ViewModel 형식에 기반한 몇 가지 예제 값과 반환될 수 있는 가능한 HTTP 상태 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1f667-177">The image shows some example values based on the ViewModel types and the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1f667-178">추가 자료</span><span class="sxs-lookup"><span data-stu-id="1f667-178">Additional resources</span></span>

- <span data-ttu-id="1f667-179">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="1f667-179">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="1f667-180">**Julie Lerman. 데이터 요소 - Dapper, Entity Framework 및 하이브리드 앱(MSDN 매거진 문서)**</span><span class="sxs-lookup"><span data-stu-id="1f667-180">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="1f667-181">**Swagger를 사용한 ASP.NET Core Web API 도움말 페이지**</span><span class="sxs-lookup"><span data-stu-id="1f667-181">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="1f667-182">[이전](eshoponcontainers-cqrs-ddd-microservice.md)
>[다음](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="1f667-182">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
