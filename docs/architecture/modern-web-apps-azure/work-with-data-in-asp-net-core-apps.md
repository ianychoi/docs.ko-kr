---
title: ASP.NET Core 앱에서 데이터 작업
description: ASP.NET Core 및 Azure를 사용하여 현대식 웹 애플리케이션 설계 | ASP.NET Core 앱에서 데이터 작업
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
no-loc:
- Blazor
- WebAssembly
ms.openlocfilehash: 9d85d700ecb8d6cbe7afd8d3c724f499ee5fed71
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851258"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="a85e8-103">ASP.NET Core 앱에서 데이터 작업</span><span class="sxs-lookup"><span data-stu-id="a85e8-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="a85e8-104">"데이터는 귀중한 자산이며 시스템 자체보다 더 오래 지속됩니다."</span><span class="sxs-lookup"><span data-stu-id="a85e8-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="a85e8-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="a85e8-105">Tim Berners-Lee</span></span>

<span data-ttu-id="a85e8-106">데이터 액세스는 거의 모든 소프트웨어 애플리케이션에서 중요한 부분입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="a85e8-107">ASP.NET Core는 Entity Framework Core(및 Entity Framework 6)를 포함한 다양한 데이터 액세스 옵션을 지원하며, 모든 .NET 데이터 액세스 프레임워크와 함께 작동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="a85e8-108">어떤 데이터 액세스 프레임워크를 선택할 것인지는 애플리케이션 요구 사항에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="a85e8-109">ApplicationCore 및 UI 프로젝트에서 이러한 옵션을 추상화하고, 인프라에서 구현 세부 사항을 캡슐화하면 느슨하게 결합된 테스트 가능 소프트웨어를 만드는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="a85e8-110">Entity Framework Core(관계형 데이터베이스용)</span><span class="sxs-lookup"><span data-stu-id="a85e8-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="a85e8-111">관계형 데이터와 함께 작동해야 하는 새 ASP.NET Core 애플리케이션을 작성하는 경우 애플리케이션이 Entity Framework Core(EF Core)를 통해 데이터에 액세스하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="a85e8-112">EF Core는 .NET 개발자가 데이터 원본에서 개체를 유지할 수 있게 해주는 개체 관계형 매퍼(O/RM)입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="a85e8-113">EF Core를 사용하면 개발자들이 일반적으로 작성해야 하는 데이터 액세스 코드가 대부분 필요하지 않게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="a85e8-114">ASP.NET Core와 마찬가지로, EF Core는 모듈식 플랫폼 간 애플리케이션을 지원하도록 처음부터 다시 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="a85e8-115">애플리케이션에 NuGet 패키지로 추가하고, 시작에서 구성하고, 필요할 때마다 종속성 주입을 통해 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="a85e8-116">EF Core를 SQL Server 데이터베이스와 함께 사용하려면 다음 dotnet CLI 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="a85e8-117">테스트를 목적으로 InMemory 데이터 원본에 대한 지원을 추가하려면:</span><span class="sxs-lookup"><span data-stu-id="a85e8-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="a85e8-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="a85e8-118">The DbContext</span></span>

<span data-ttu-id="a85e8-119">EF Core를 사용하려면 <xref:Microsoft.EntityFrameworkCore.DbContext>의 서브클래스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="a85e8-120">이 클래스는 애플리케이션에서 작업할 엔터티 컬렉션을 나타내는 속성을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="a85e8-121">EShopOnWeb 샘플에는 항목, 브랜드 및 형식에 대한 컬렉션을 제공하는 CatalogContext가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="a85e8-122">DbContext에는 DbContextOptions을 수락하고 이 인수를 기본 DbContext 생성자에게 전달하는 생성자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="a85e8-123">애플리케이션에 DbContext가 하나만 있는 경우 DbContextOptions 인스턴스를 전달할 수 있지만, 둘 이상 있는 경우에는 제네릭 DbContextOptions\<T> 형식을 사용하여 DbContext 형식을 제네릭 매개 변수로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="a85e8-124">EF Core 구성</span><span class="sxs-lookup"><span data-stu-id="a85e8-124">Configuring EF Core</span></span>

<span data-ttu-id="a85e8-125">ASP.NET Core 애플리케이션에서는 일반적으로 ConfigureServices 메서드에서 EF Core를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="a85e8-126">EF Core는 여러 유용한 확장 메서드를 지원하는 DbContextOptionsBuilder를 사용하여 구성을 간소화합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="a85e8-127">구성에 연결 문자열이 정의된 SQL Server 데이터베이스를 사용하도록 CatalogContext를 구성하려면 다음 코드를 ConfigureServices에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="a85e8-128">메모리 내 데이터베이스를 사용하려면:</span><span class="sxs-lookup"><span data-stu-id="a85e8-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="a85e8-129">EF Core를 설치하고, DbContext 자식 형식을 만들고, ConfigureServices에서 구성을 마쳤으면 EF 코어를 사용할 준비가 완료된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="a85e8-130">DbContext 형식의 인스턴스를 필요로 하는 모든 서비스에서 이 인스턴스를 요청할 수 있으며, 마치 컬렉션에 있는 것처럼 LINQ를 사용하여 지속형 엔터티 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="a85e8-131">EF Core는 LINQ 식을 SQL 쿼리로 변환하여 데이터를 저장하고 검색하는 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="a85e8-132">그림 8-1처럼 로거를 구성하고 그 수준을 정보 이상으로 설정하면 EF Core가 실행하는 쿼리를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![EF Core 쿼리를 콘솔에 로깅](./media/image8-1.png)

<span data-ttu-id="a85e8-134">**그림 8-1**.</span><span class="sxs-lookup"><span data-stu-id="a85e8-134">**Figure 8-1**.</span></span> <span data-ttu-id="a85e8-135">EF Core 쿼리를 콘솔에 로깅</span><span class="sxs-lookup"><span data-stu-id="a85e8-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="a85e8-136">데이터 가져오기 및 저장</span><span class="sxs-lookup"><span data-stu-id="a85e8-136">Fetching and storing Data</span></span>

<span data-ttu-id="a85e8-137">EF Core에서 데이터를 검색하려면 적절한 속성에 액세스한 후 LINQ를 사용하여 결과를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="a85e8-138">LINQ를 사용하여 프로젝션을 수행하고, 그 결과를 한 형식에서 다른 형식으로 변환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="a85e8-139">다음 예제는 이름순으로 정렬되고, [사용] 속성을 기준으로 필터링되고, SelectListItem 형식에 투영되는 CatalogBrands를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="a85e8-140">위의 예제에서 쿼리가 즉시 실행되도록 ToListAsync에 대한 호출을 추가하는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="a85e8-141">그렇지 않으면 명령문에서 IQueryable\<SelectListItem>을 brandItems에 할당하므로 열거될 때까지 실행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="a85e8-142">메서드에서 IQueryable 결과를 반환할 때의 장점과 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="a85e8-143">쿼리 EF Core가 추가 수정이 가능하도록 작성되지만, EF Core에서 변환할 수 없는 쿼리에 작업이 추가되면 런타임에만 발생하는 오류가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="a85e8-144">일반적으로 데이터 액세스를 수행하는 메서드에 필터를 전달하고 메모리 내 컬렉션(예: List\<T>)을 반환하는 것이 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="a85e8-145">EF Core는 지속성 저장소에서 가져오는 엔터티의 변경 내용을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="a85e8-146">추적된 엔터티의 변경 내용을 저장하려면 엔터티를 가져올 때 사용한 것과 동일한 DbContext 인스턴스가 되도록 DbContext에서 SaveChanges 메서드를 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="a85e8-147">엔터티 추가 및 제거는 적절한 DbSet 속성에서 직접 수행되며, 마찬가지로 SaveChanges를 호출하여 데이터베이스 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="a85e8-148">다음 예제에서는 지속성 저장소에서 엔터티를 추가, 업데이트 및 제거하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="a85e8-149">EF Core는 엔터티를 가져오고 저장하기 위한 동기 및 비동기 메서드를 모두 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="a85e8-150">웹 애플리케이션에서는 데이터 액세스 작업이 끝나기를 기다리는 동안 웹 서버 스레드가 차단되지 않도록 비동기 메서드에 async/await 패턴을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="a85e8-151">관련 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a85e8-151">Fetching related data</span></span>

<span data-ttu-id="a85e8-152">EF Core는 엔터티를 검색할 때 엔터티와 함께 데이터베이스에 직접 저장되는 모든 속성을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="a85e8-153">관련 엔터티 목록 같은 탐색 속성은 채워지지 않으며 값이 Null로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="a85e8-154">이 프로세스는 EF Core가 데이터를 필요 이상으로 가져오지 않게 하므로, 요청을 신속하게 처리하고 효율적인 방식으로 응답을 반환해야 하는 웹 애플리케이션에서 매우 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-154">This process ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="a85e8-155">_즉시 로드_ 를 사용하여 엔터티와의 관계를 포함하려면 다음과 같이 쿼리에서 Include 확장 메서드를 사용하여 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="a85e8-156">여러 관계를 포함할 수 있으며, ThenInclude를 사용하여 하위 관계를 포함할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="a85e8-157">EF Core는 엔터티의 결과 집합을 검색하는 단일 쿼리를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="a85e8-158">또는 다음과 같이 마침표('.')로 구분된 문자열을 `.Include()` 확장 메서드에 전달하여 탐색 속성을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="a85e8-159">사양은 필터링 논리를 캡슐화할 뿐 아니라 채울 속성을 포함하여 반환될 데이터의 모양을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="a85e8-160">eShopOnWeb 샘플에는 사양 내에서 즉시 로드 정보를 캡슐화하는 방법을 보여주는 몇 가지 사양이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="a85e8-161">여기에서 사양을 쿼리의 일부로 사용하는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="a85e8-162">관련 데이터를 로드하는 또 다른 옵션은 _명시적 로드_ 를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="a85e8-163">명시적 로드를 사용하면 이미 검색된 엔터티에 추가 데이터를 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="a85e8-164">이 방법은 데이터베이스에 대한 별도의 요청이 개입되므로 요청당 데이터베이스 왕복 횟수를 최소화해야 하는 웹 애플리케이션에는 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-164">Since this approach involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="a85e8-165">_지연 로드_ 는 애플리케이션에서 참조하는 관련 데이터를 자동으로 로드하는 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="a85e8-166">EF Core는 버전 2.1에서 지연 로드에 대한 지원이 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="a85e8-167">지연 로드는 기본적으로 사용하지 않도록 설정되어 있으며 `Microsoft.EntityFrameworkCore.Proxies`를 설치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="a85e8-168">명시적 로드와 마찬가지로 지연 로드는 각 웹 요청 내에서 수행되는 추가 데이터베이스 쿼리에서 사용되기 때문에 일반적으로 웹 애플리케이션에 대해 사용하지 않도록 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="a85e8-169">아쉽게도 지연 로드에서 발생하는 오버헤드는 대기 시간이 짧고 테스트에 사용되는 데이터 세트가 작은 경우 개발 시기에 종종 간과됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when the latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="a85e8-170">단, 더 많은 사용자, 더 많은 데이터 및 더 긴 대기 시간의 프로덕션에서는 추가 데이터베이스 요청으로 인해 웹 애플리케이션의 성능이 저하되어 지연 로드를 과도하게 사용하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="a85e8-171">웹 애플리케이션에서 지연 로드 엔터티 방지</span><span class="sxs-lookup"><span data-stu-id="a85e8-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="a85e8-172">데이터 캡슐화</span><span class="sxs-lookup"><span data-stu-id="a85e8-172">Encapsulating data</span></span>

<span data-ttu-id="a85e8-173">EF Core는 모델이 적절하게 상태를 캡슐화할 수 있도록 여러 기능을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="a85e8-174">도메인 모델의 일반적인 문제는 컬렉션 탐색 속성을 공개적으로 액세스 가능한 목록 형식으로 노출한다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="a85e8-175">이 문제로 인해 협력자가 이 컬렉션 형식의 콘텐츠를 조작하여 컬렉션과 관련한 중요한 비즈니스 규칙을 무시할 수 있고 이에 따라 개체가 잘못된 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-175">This problem allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="a85e8-176">이 문제의 해결 방법은 이 예제와 같이 관련 컬렉션에 대해 읽기 전용 액세스만을 노출하고 명시적으로 클라이언트가 이를 조작할 수 있는 방법을 정의하는 메서드를 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-176">The solution to this problem is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="a85e8-177">이 엔터티 형식은 퍼블릭 `List` 또는 `ICollection` 속성을 공개하지 않지만 대신 기본 목록 형식을 래핑하는 `IReadOnlyCollection` 형식을 공개합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="a85e8-178">이 패턴을 사용하면 다음과 같이 지원 필드를 사용하도록 Entity Framework Core를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="a85e8-179">도메인 모델을 향상시킬 수 있는 다른 방법은 ID가 없고 해당 속성으로만 구별되는 형식에서 값 개체를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="a85e8-180">이러한 형식을 엔터티 속성으로 사용하면 논리가 속한 값 개체에 특정되도록 유지할 수 있고, 동일한 개념을 사용하는 여러 엔터티 간에 중복 논리를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="a85e8-181">Entity Framework Core에서는 다음과 같이 형식을 소유된 엔터티로 구성하여 소유하는 엔터티와 동일한 테이블에서 값 개체를 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="a85e8-182">다음 예제에서 `ShipToAddress` 속성은 `Address` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="a85e8-183">`Address`는 `Street` 및 `City`와 같은 여러 속성을 포함한 값 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="a85e8-184">EF Core는 `Order` 개체를 `Address` 속성당 하나의 열을 포함한 해당 테이블에 매핑하여 각 열 이름의 접두사를 속성의 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="a85e8-185">이 예제에서 `Order` 테이블에는 `ShipToAddress_Street` 및 `ShipToAddress_City`와 같은 열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="a85e8-186">원하는 경우 별도의 테이블에 소유된 형식을 저장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="a85e8-187">[EF Core에서 소유 엔터티 지원](/ef/core/modeling/owned-entities)에 대해 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="a85e8-188">복원력 있는 연결</span><span class="sxs-lookup"><span data-stu-id="a85e8-188">Resilient connections</span></span>

<span data-ttu-id="a85e8-189">SQL 데이터베이스 같은 외부 리소스를 사용할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="a85e8-190">일시적으로 사용할 수 없는 경우 예외가 발생하지 않도록 하기 위해 애플리케이션에서 재시도 논리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="a85e8-191">이 기술을 보통 _연결 복원력_ 이라고 부릅니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="a85e8-192">최대 다시 시도 횟수에 도달할 때까지 대기 시간이 기하급수적으로 증가하면서 다시 시도하는 [지수 백오프를 사용하여 다시 시도](/azure/architecture/patterns/retry) 기술을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-192">You can implement your [own retry with exponential backoff](/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="a85e8-193">이 기술에서는 클라우드 리소스가 어떤 이유로든 짧은 기간 일시적으로 사용할 수 없게 되어 일부 요청이 실패할 수 있다는 점을 받아들입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in the failure of some requests.</span></span>

<span data-ttu-id="a85e8-194">Azure SQL DB의 경우, Entity Framework Core는 이미 내부 데이터베이스 연결 복원력과 다시 시도 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="a85e8-195">그러나 복원력 있는 EF 코어 연결을 원할 경우 각 DbContext 연결에 대한 Entity Framework 실행 전략을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="a85e8-196">예를 들어, EF 코어 연결 수준의 다음 코드는 연결이 실패할 경우 다시 시도되는 복원력 있는 SQL 연결을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30),
            errorNumbersToAdd: null);
        });
    });
}
//...
```

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="a85e8-197">BeginTransaction 및 여러 DbContexts를 사용한 실행 전략 및 명시적 트랜잭션</span><span class="sxs-lookup"><span data-stu-id="a85e8-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="a85e8-198">EF Core 연결에서 다시 시도를 사용하도록 설정되면 EF Core를 사용하여 수행하는 각 작업이 자체적으로 다시 시도할 수 있는 작업이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="a85e8-199">일시적인 오류가 발생할 경우 SaveChanges에 대한 각 쿼리와 각 호출이 하나의 단위로 다시 시도됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="a85e8-200">그러나 코드가 BeginTransaction을 사용하여 트랜잭션을 시작한 경우, 하나의 단위로 처리해야 하는 자신만의 작업 그룹을 정의하게 됩니다. 오류가 발생하면 트랜잭션 내부의 모든 항목이 롤백되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="a85e8-201">EF 실행 전략(다시 시도 정책)을 사용할 때 해당 트랜잭션을 실행하려고 시도하고 여러 DbContexts의 여러 SaveChanges를 포함하면 다음과 같은 예외가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="a85e8-202">System.InvalidOperationException: 구성된 실행 전략 ‘SqlServerRetryingExecutionStrategy’는 사용자가 시작한 트랜잭션을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="a85e8-203">'DbContext.Database.CreateExecutionStrategy()'에서 반환된 실행 전략을 사용하여 다시 시도가 가능한 단위로 트랜잭션의 모든 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="a85e8-204">해결책은 실행해야 하는 모든 것을 나타내는 대리자를 사용하여 EF 실행 전략을 수동으로 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="a85e8-205">일시적인 오류가 발생하면, 실행 전략에서 대리자를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="a85e8-206">다음 코드는 이 방식을 구현하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-206">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy();
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();

        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
            await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="a85e8-207">첫 번째 DbContext는 \_catalogContext이고 두 번째 DbContext는 \_integrationEventLogService 개체 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="a85e8-208">마지막으로, 커밋 작업은 EF 실행 전략을 사용하여 여러 DbContexts를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="a85e8-209">참조 - Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="a85e8-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="a85e8-210">**EF Core Docs**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="a85e8-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="a85e8-211">**EF Core: 관련 데이터**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="a85e8-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="a85e8-212">**ASPNET 애플리케이션에서 엔터티 지연 로드 방지**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="a85e8-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="a85e8-213">EF Core 또는 마이크로 ORM</span><span class="sxs-lookup"><span data-stu-id="a85e8-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="a85e8-214">EF Core는 지속성 관리에 매우 유용하고 대부분 애플리케이션 개발자의 데이터베이스 세부 정보를 캡슐화하지만, 유일한 방법은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="a85e8-215">또 다른 인기 있는 오픈 소스는 마이크로 ORM이라고도 하는 [Dapper](https://github.com/StackExchange/Dapper)입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="a85e8-216">마이크로 ORM은 개체를 데이터 구조에 매핑하는 데 사용되며 기능이 약간 적은 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="a85e8-217">Dapper의 디자인 목표는 데이터를 검색하고 업데이트하는 데 사용되는 기본 쿼리를 완전히 캡슐화하는 것이 아니라 성능에 집중하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="a85e8-218">Dapper는 개발자의 SQL을 추상화하지 않으므로 "금속에 가깝고" 개발자가 특정 데이터 액세스 작업에 사용할 정확한 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="a85e8-219">EF Core에는 Dapper과 구별되지만 성능 오버헤드를 제공하는 두 가지 중요한 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="a85e8-220">첫 번째는 LINQ 식에서 SQL로의 변환입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-220">The first is the translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="a85e8-221">이러한 변환은 캐시되지만, 그럼에도 불구하고 처음으로 수행할 때 오버헤드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="a85e8-222">두 번째는 엔터티 변경 내용 추적(효율적인 update 문을 생성할 수 있도록)입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="a85e8-223">특정 쿼리의 경우 <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> 확장명을 사용하여 이 동작을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-223">This behavior can be turned off for specific queries by using the <xref:System.Data.Entity.DbExtensions.AsNoTracking%2A> extension.</span></span> <span data-ttu-id="a85e8-224">또한 EF 코어는 일반적으로 매우 효율적이고 어떤 경우에도 성능의 관점에서 완벽하게 허용되는 SQL 쿼리를 생성하지만, 실행할 정확한 쿼리를 세부적으로 제어해야 하는 경우 EF Core를 사용하여 사용자 지정 SQL을 전달(또는 저장 프로시저를 실행)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="a85e8-225">이 경우 Dapper는 여전히 EF Core보다 성능이 우수하지만, 그 차이는 미미합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="a85e8-226">Julie Lerman은 2016년 5월에 작성한 MSDN 문서 [Dapper, Entity Framework 및 하이브리드 앱](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps)에서 몇 가지 성능 데이터를 제시했습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="a85e8-227">다양한 데이터 액세스 방법에 대한 추가 성능 벤치마크 데이터는 [Dapper 사이트](https://github.com/StackExchange/Dapper)에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="a85e8-228">Dapper 구문이 EF Core에서 어떻게 달라지는지 살펴보려면 항목의 목록 검색에 사용되는 다음 두 동일한 메서드 버전을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="a85e8-229">Dapper를 사용하여 좀 더 복잡한 개체 그래프를 작성해야 하는 경우 관련 쿼리를 직접 작성해야 합니다(EF Core에서 Include를 추가하는 것과는 달리).</span><span class="sxs-lookup"><span data-stu-id="a85e8-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="a85e8-230">이 기능은 개발 행을 여러 매핑된 개체에 매핑할 수 있는 다중 매핑이라는 기능을 포함하여 다양한 구문을 통해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-230">This functionality is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="a85e8-231">예를 들어 속성은 Owner, 형식은 User인 Post라는 클래스가 있다고 할 때, 다음 SQL은 모든 필요한 데이터를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="a85e8-232">반환된 각 행에는 User 및 Post 데이터가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="a85e8-233">User 데이터는 Owner 속성을 통해 Post 데이터에 연결되어야 하므로 다음 함수가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="a85e8-234">연결된 사용자 데이터로 Owner 속성이 채워진 게시물 컬렉션을 반환하는 전체 코드 목록은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="a85e8-235">Dapper는 캡슐화가 덜 이루어지므로 개발자는 데이터가 저장되는 방식, 데이터를 효과적으로 쿼리하는 방법, 데이터를 가져오는 더 많은 코드를 작성하는 방법을 잘 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="a85e8-236">모델이 바뀌면 단순히 새 마이그레이션을 만들고(EF Core의 또 다른 기능) DbContext의 한 장소에 매핑 정보를 업데이트하는 대신, 영향을 받는 모든 쿼리를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="a85e8-237">이러한 쿼리는 컴파일 시간을 보장하지 않으므로 모델 또는 데이터베이스 변경에 대한 응답으로 런타임에 중단될 수 있으며, 오류를 신속하게 감지하기가 더 어려워질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="a85e8-238">이러한 단점을 대가로, Dapper는 매우 빠른 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="a85e8-239">EF Core는 대부분의 애플리케이션에서, 그리고 애플리케이션의 대부분에서 납득할 만한 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="a85e8-240">따라서 개발자 생산성 이점이 성능 오버헤드보다 클 가능성이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="a85e8-241">캐싱으로 이점을 얻을 수 있는 쿼리의 경우 실제 쿼리가 실행되는 시간은 극히 일부에 불과할 수 있으며, 무시해도 될 정도로 쿼리 성능 차이가 비교적 작을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="a85e8-242">SQL 또는 NoSQL</span><span class="sxs-lookup"><span data-stu-id="a85e8-242">SQL or NoSQL</span></span>

<span data-ttu-id="a85e8-243">전통적으로 SQL Server 같은 관계형 데이터베이스가 영구 데이터 스토리지 시장을 지배해 왔지만, 유일한 솔루션은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="a85e8-244">[MongoDB](https://www.mongodb.com/what-is-mongodb) 같은 NoSQL 데이터베이스는 개체를 저장하는 다른 접근 방식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="a85e8-245">개체를 테이블 및 행에 매핑하는 대신, 전체 개체 그래프를 직렬화하고 결과를 저장하는 또 다른 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="a85e8-246">이 방법의 이점은 적어도 처음에는 간단하고 성능이 우수하다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="a85e8-247">개체를 관계가 있는 여러 테이블로 분해하고 데이터베이스에서 개체가 마지막으로 검색된 이후에 변경되었을 수 있는 행을 업데이트하는 것보다 키를 사용하여 직렬화된 단일 개체를 저장하는 방법이 더 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="a85e8-248">마찬가지로, 관계형 데이터베이스에서 동일한 개체를 완전히 작성하는 데 필요한 복잡한 조인 또는 여러 데이터베이스 쿼리보다는 키 기반 저장소에서 단일 개체를 가져와서 역직렬화하는 방법이 훨씬 쉽고 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="a85e8-249">또한 잠금이나 트랜잭션 또는 고정된 스키마가 없으면 여러 머신에서 NoSQL 데이터베이스를 확장할 수 있으므로 대규모 데이터 세트를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="a85e8-250">반면, NoSQL 데이터베이스는(일반적으로 그 이름처럼) 고유한 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="a85e8-251">관계형 데이터베이스는 정규화를 사용하여 일관성을 유지하고 데이터 중복을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="a85e8-252">이 방법으로 데이터베이스의 전체 크기를 줄이고 즉시 전체 데이터베이스에서 공유 데이터 업데이트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-252">This approach reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="a85e8-253">관계형 데이터베이스에서 주소 테이블은 ID별로 국가 테이블을 참조할 수 있으며, 이를 통해 국가/지역의 이름이 변경되면 주소 레코드 자체를 업데이트할 필요 없이 업데이트의 이점을 누릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="a85e8-254">그러나 NoSQL 데이터베이스에는 주소 및 주소와 연결된 국가는 여러 저장된 개체의 일부로 직렬화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-254">However, in a NoSQL database, Address, and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="a85e8-255">국가/지역 이름을 업데이트하려면 단일 행이 아닌 모든 개체를 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="a85e8-256">관계형 데이터베이스는 외래 키 같은 규칙을 적용하여 관계 무결성을 보장할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="a85e8-257">일반적으로 NoSQL 데이터베이스는 데이터에 대한 이러한 제약 조건을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="a85e8-258">처리해야 하는 또 다른 복잡성 NoSQL 데이터베이스는 버전 관리입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="a85e8-259">개체의 속성이 변경되면 저장된 이전 버전에서 개체를 역직렬화할 수 없을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="a85e8-260">따라서 직렬화된(이전) 개체 버전을 갖고 있는 모든 기존 개체를 새 스키마에 맞게 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="a85e8-261">이 방법은 스키마 변경 시 가끔 업데이트 스크립트나 매핑 업데이트가 필요한 관계형 데이터베이스와 개념적 차이는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-261">This approach is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="a85e8-262">그러나 NoSQL 방식에서는 데이터 중복 때문에 수정해야 하는 항목 수가 훨씬 많은 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="a85e8-263">NoSQL 데이터베이스에서는 개체의 여러 버전을 저장할 수 있으며, 무언가 고정된 스키마 관계형 데이터베이스는 일반적으로 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="a85e8-264">그러나 이 경우 애플리케이션 코드에서 개체의 이전 버전이 존재하여 복잡성이 추가되는지 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-264">However, in this case, your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="a85e8-265">NoSQL 데이터베이스는 일반적으로 [ACID](https://en.wikipedia.org/wiki/ACID)를 적용하지 않습니다. 즉, 관계형 데이터베이스보다 성능과 확장성이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="a85e8-266">정규화된 테이블 구조의 스토리지에 적합하지 않은 매우 큰 데이터 세트 및 개체에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="a85e8-267">각 데이터베이스를 적합하게 사용한다면 단일 애플리케이션으로 관계형 데이터베이스와 NoSQL 데이터베이스의 장점을 모두 취하지 못할 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="a85e8-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="a85e8-268">Azure Cosmos DB</span></span>

<span data-ttu-id="a85e8-269">Azure Cosmos DB는 완전히 관리되는 NoSQL 데이터베이스 서비스로 스키마 없는 클라우드 기반 데이터 스토리지를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="a85e8-270">Azure Cosmos DB는 신속하고 예측 가능한 성능, 고가용성, 탄력적인 크기 조정, 글로벌 배포를 위해 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="a85e8-271">NoSQL 데이터베이스임에도 불구하고, 개발자가 풍부하고 친숙한 SQL 쿼리 기능을 JSON 데이터에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="a85e8-272">Azure Cosmos DB의 모든 리소스는 JSON 문서로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="a85e8-273">리소스는 메타데이터를 포함하고 있는 _항목_ 및 항목 컬렉션인 _피드_ 로 관리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="a85e8-274">그림 8-2는 여러 Azure Cosmos DB 리소스 간의 관계를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![NoSQL JSON 데이터베이스인 Azure Cosmos DB의 리소스 간 계층 관계](./media/image8-2.png)

<span data-ttu-id="a85e8-276">**그림 8-2.**</span><span class="sxs-lookup"><span data-stu-id="a85e8-276">**Figure 8-2.**</span></span> <span data-ttu-id="a85e8-277">Azure Cosmos DB 리소스 조직입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="a85e8-278">Azure Cosmos DB 쿼리 언어는 JSON 문서를 쿼리하는 단순하지만 강력한 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="a85e8-279">이 언어는 ANSI SQL 문법의 하위 집합을 지원하고 JavaScript 개체, 배열, 개체 생성 및 함수 호출을 긴밀하게 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="a85e8-280">**참조 – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="a85e8-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="a85e8-281">Azure Cosmos DB 소개 <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="a85e8-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="a85e8-282">다른 지속성 옵션</span><span class="sxs-lookup"><span data-stu-id="a85e8-282">Other persistence options</span></span>

<span data-ttu-id="a85e8-283">관계형 및 NoSQL 저장소 옵션 외에도, ASP.NET Core 애플리케이션은 Azure Storage를 사용하여 다양한 데이터 형식 및 파일을 클라우드 기반의 확장 가능한 방식으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="a85e8-284">Azure Storage는 대규모로 확장할 수 있으므로 처음에는 적은 양의 데이터를 저장하는 것으로 시작하고, 이후에 애플리케이션에 필요하면 수백 테라바이트를 저장하도록 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="a85e8-285">Azure Storage는 다음과 같은 네 가지 데이터를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="a85e8-286">구조화되지 않은 텍스트 또는 이진 스토리지를 위한 Blob Storage로 개체 스토리지라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="a85e8-287">행 키를 통해 액세스할 수 있는 구조화된 데이터 세트를 위한 Table Storage.</span><span class="sxs-lookup"><span data-stu-id="a85e8-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="a85e8-288">신뢰할 수 있는 큐 기반 메시지를 위한 Queue Storage.</span><span class="sxs-lookup"><span data-stu-id="a85e8-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="a85e8-289">Azure 가상 머신과 온-프레미스 애플리케이션 간의 공유 파일 액세스를 위한 File Storage.</span><span class="sxs-lookup"><span data-stu-id="a85e8-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="a85e8-290">**참조 – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="a85e8-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="a85e8-291">Azure Storage 소개 <https://docs.microsoft.com/azure/storage/common/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="a85e8-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/common/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="a85e8-292">캐싱</span><span class="sxs-lookup"><span data-stu-id="a85e8-292">Caching</span></span>

<span data-ttu-id="a85e8-293">웹 애플리케이션에서 각 웹 요청을 최대한 짧은 시간 내에 완료해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="a85e8-294">이 기능을 얻는 한 가지 방법은 서버가 요청을 완료하기 위해 만들어야 하는 외부 호출의 수를 제한하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-294">One way to achieve this functionality is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="a85e8-295">캐싱에는 서버(또는 데이터 원본보다 쉽게 쿼리할 수 있는 또 다른 데이터 저장소)에 데이터 복사본을 저장하는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="a85e8-296">웹 애플리케이션, 특히 SPA가 아닌 기존 웹 애플리케이션은 모든 요청에서 전체 사용자 인터페이스를 빌드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="a85e8-297">이 방법에서는 사용자 요청 간에 많은 수의 같은 데이터베이스 쿼리를 반복해야 하는 경우가 자주 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-297">This approach frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="a85e8-298">대부분의 경우 이 데이터가 변경되는 일은 거의 없으므로 데이터베이스에서 이 데이터를 지속적으로 요청할 이유가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="a85e8-299">ASP.NET Core는 전체 페이지를 캐싱하기 위한 응답 캐싱, 그리고 보다 세부적인 캐싱 동작을 지원하는 데이터 캐싱을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="a85e8-300">캐싱을 구현할 때 문제 격리를 염두에 두어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="a85e8-301">데이터 액세스 논리 또는 사용자 인터페이스에 캐싱 논리를 구현하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="a85e8-302">그 대신, 캐싱을 자체 클래스에서 캡슐화하고 구성을 사용하여 해당 동작을 관리하세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="a85e8-303">이 방법을 통해 개방/폐쇄 및 단일 책임 원칙을 준수하며, 애플리케이션의 성장에 따라 애플리케이션에서 캐싱을 사용하는 방법을 좀 더 간편하게 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-303">This approach follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="a85e8-304">ASP.NET Core 응답 캐싱</span><span class="sxs-lookup"><span data-stu-id="a85e8-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="a85e8-305">ASP.NET Core는 두 가지 수준의 응답 캐시를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="a85e8-306">첫 번째 수준은 서버의 어떤 항목도 캐시하지 않지만, 클라이언트와 프록시 서버에 응답을 캐시하라고 지시하는 HTTP 헤더를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="a85e8-307">이 기능은 개별 컨트롤러 또는 작업에 ResponseCache 특성을 추가하여 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-307">This functionality is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="a85e8-308">이전 예제에서는 응답에 다음 헤더가 추가되어 클라이언트가 최대 60초 동안 결과를 캐시하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="a85e8-309">Cache-Control: public,max-age=60</span><span class="sxs-lookup"><span data-stu-id="a85e8-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="a85e8-310">서버측 메모리 내 캐싱을 애플리케이션에 추가하려면 Microsoft.AspNetCore.ResponseCaching NuGet 패키지를 참조한 다음, 응답 캐싱 미들웨어를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="a85e8-311">이 미들웨어는 스타트업에서 ConfigureServices 및 Configure 모두에 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="a85e8-312">응답 캐싱 미들웨어는 사용자 지정할 수 있는 조건 집합에 따라 자동으로 응답을 캐싱합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="a85e8-313">기본적으로 GET 또는 HEAD 메서드를 통해 요청된 200(확인) 응답만 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="a85e8-314">또한 요청에는 캐시 컨트롤: 공용 헤더가 포함된 응답이 있어야 하고, 권한 부여 또는 Set-Cookie에 대한 헤더를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="a85e8-315">[응답 캐싱 미들웨어에서 사용하는 캐싱 조건 전체 목록](/aspnet/core/performance/caching/middleware#conditions-for-caching)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="a85e8-316">데이터 캐싱</span><span class="sxs-lookup"><span data-stu-id="a85e8-316">Data caching</span></span>

<span data-ttu-id="a85e8-317">전체 웹 응답 캐싱 대신(또는 외에도) 개별 데이터 쿼리의 결과를 캐싱할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="a85e8-318">이 기능의 경우 웹 서버에서 메모리 내 캐싱을 사용하거나 [분산된 캐시](/aspnet/core/performance/caching/distributed)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-318">For this functionality, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="a85e8-319">이 섹션에서는 메모리 내 캐싱을 구현하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="a85e8-320">ConfigureServices에서 메모리(또는 분산) 캐싱 지원 추가:</span><span class="sxs-lookup"><span data-stu-id="a85e8-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="a85e8-321">Microsoft.Extensions.Caching.Memory NuGet 패키지를 추가하는 것을 잊지 마세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="a85e8-322">서비스를 추가한 후에는 캐시에 액세스해야 할 때마다 종속성 주입을 통해 IMemoryCache를 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="a85e8-323">이 예제에서는 기본 CatalogService 구현에 대한 액세스를 제어하는(또는 CatalogService 구현에 동작을 추가) ICatalogService 대안 구현을 제공함으로써 CachedCatalogService에서 프록시(또는 Decorator) 디자인 패턴을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }

    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }

    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }

    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="a85e8-324">서비스의 캐시된 버전을 사용하지만 서비스가 여전히 생성자에 필요한 CatalogService 인스턴스를 가져올 수 있도록 애플리케이션을 구성하려면 ConfigureServices에 다음 줄을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following lines in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="a85e8-325">이 코드에서 카탈로그 데이터를 가져오는 데이터베이스 호출은 요청마다 만들어지는 것이 아니라 분당 한 번만 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-325">With this code in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="a85e8-326">사이트의 트래픽에 따라, 이는 데이터베이스에 대해 이루어지는 쿼리 수, 현재 이 서비스에서 노출하는 세 쿼리에 의존하는 홈페이지의 평균 페이지 로드 시간에 큰 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="a85e8-327">캐싱이 구현될 때 발생하는 문제는 _부실 데이터_, 즉 원본에서는 변경되었지만 캐시에는 오래된 버전이 남아 있는 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="a85e8-328">이 문제를 완화하는 간단한 방법은 캐시 기간을 짧게 하는 것입니다. 사용량이 많은 애플리케이션의 경우 데이터가 캐시되는 길이를 연장해서 얻을 수 있는 이점이 제한적이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is a limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="a85e8-329">예를 들어 단일 데이터베이스 쿼리를 만들고 초당 10회 요청되는 페이지를 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="a85e8-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="a85e8-330">이 페이지가 1분 동안 캐시되면 분당 데이터베이스 쿼리 수가 600에서 1로 99.8% 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="a85e8-331">그 대신 캐시 기간을 1시간으로 하면 전체 감소율이 99.997%가 되겠지만, 부실 데이터 가능성 및 잠재적 연령이 엄청나게 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-331">If instead the cache duration was made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="a85e8-332">또 다른 방법은 캐시에 포함된 데이터가 업데이트될 때 선제적으로 캐시 항목을 제거하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="a85e8-333">키를 알고 있으면 개별 항목을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="a85e8-334">애플리케이션이 캐시하는 항목을 업데이트하기 위한 기능을 노출하는 경우 업데이트를 수행하는 코드에서 해당 캐시 항목을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="a85e8-335">경우에 따라 특정 데이터 집합에 종속된 여러 항목이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="a85e8-336">이 경우 CancellationChangeToken을 사용하여 캐시 항목 간의 종속성을 만드는 것이 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="a85e8-337">CancellationChangeToken을 사용하면 토큰을 취소하여 여러 캐시 항목을 한꺼번에 만료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

<span data-ttu-id="a85e8-338">캐싱은 반복해서 데이터베이스에서 동일한 값을 요청하는 웹 페이지의 성능을 크게 향상시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="a85e8-339">캐싱을 적용하기 전에 데이터 액세스 및 페이지 성능을 측정하고, 개선이 필요한 경우에만 캐싱을 적용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="a85e8-340">캐싱은 웹 서버 메모리 리소스를 사용하고 애플리케이션의 복잡성을 증가시키므로 이 기술을 조급하게 활용하지 않는 것이 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

## <a name="getting-data-to-no-locblazor-no-locwebassembly-apps"></a><span data-ttu-id="a85e8-341">Blazor WebAssembly 앱으로 데이터 가져오기</span><span class="sxs-lookup"><span data-stu-id="a85e8-341">Getting data to Blazor WebAssembly apps</span></span>

<span data-ttu-id="a85e8-342">Blazor 서버를 사용하는 앱을 빌드하는 경우 이 장에서 지금까지 설명한 대로 Entity Framework 및 기타 직접 데이터 액세스 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-342">If you're building apps that use Blazor Server, you can use Entity Framework and other direct data access technologies as they've been discussed thus far in this chapter.</span></span> <span data-ttu-id="a85e8-343">그러나 다른 SPA 프레임워크처럼 Blazor WebAssembly 앱을 빌드하는 경우 다른 데이터 액세스 전략이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-343">However, when building Blazor WebAssembly apps, like other SPA frameworks, you will need a different strategy for data access.</span></span> <span data-ttu-id="a85e8-344">일반적으로 해당 애플리케이션은 데이터에 액세스하고 웹 API 엔드포인트를 통해 서버와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-344">Typically, these applications access data and interact with the server through web API endpoints.</span></span>

<span data-ttu-id="a85e8-345">수행 중인 데이터 또는 작업이 중요한 경우 [이전 장](develop-asp-net-core-mvc-apps.md)에서 보안 관련 섹션을 검토하고 무단 액세스로부터 API를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-345">If the data or operations being performed are sensitive, be sure to review the section on security in the [previous chapter](develop-asp-net-core-mvc-apps.md) and protect your APIs against unauthorized access.</span></span>

<span data-ttu-id="a85e8-346">Blazor관리 프로젝트의 [eShopOnWeb 참조 애플리케이션](https://github.com/dotnet-architecture/eShopOnWeb)에서 Blazor WebAssembly 앱의 예를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-346">You'll find an example of a Blazor WebAssembly app in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb), in the BlazorAdmin project.</span></span> <span data-ttu-id="a85e8-347">이 프로젝트는 eShopOnWeb 웹 프로젝트 내에 호스트되며 Administrators 그룹의 사용자가 저장소의 항목을 관리하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-347">This project is hosted within the eShopOnWeb Web project, and allows users in the Administrators group to manage the items in the store.</span></span> <span data-ttu-id="a85e8-348">그림 8-3에서 애플리케이션의 스크린샷을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-348">You can see a screenshot of the application in Figure 8-3.</span></span>

![eShopOnWeb 카탈로그 관리 스크린샷](./media/image8-3.jpg)

<span data-ttu-id="a85e8-350">**그림 8-3.**</span><span class="sxs-lookup"><span data-stu-id="a85e8-350">**Figure 8-3.**</span></span> <span data-ttu-id="a85e8-351">eShopOnWeb 카탈로그 관리 스크린샷</span><span class="sxs-lookup"><span data-stu-id="a85e8-351">eShopOnWeb Catalog Admin Screenshot.</span></span>

<span data-ttu-id="a85e8-352">Blazor WebAssembly 앱 내의 웹 API에서 데이터를 가져오는 경우 모든 .NET 애플리케이션에서 사용하는 것처럼 `HttpClient` 인스턴스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-352">When fetching data from web APIs within a Blazor WebAssembly app, you just use an instance of `HttpClient` as you would in any .NET application.</span></span> <span data-ttu-id="a85e8-353">포함된 기본 단계는 보낼 요청을 만들고(필요시 일반적으로 POST 또는 PUT 요청의 경우), 요청 자체를 기다리고, 상태 코드를 확인하며, 응답을 역직렬화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-353">The basic steps involved are to create the request to send (if necessary, usually for POST or PUT requests), await the request itself, verify the status code, and deserialize the response.</span></span> <span data-ttu-id="a85e8-354">지정된 API 세트에 대한 많은 요청을 만들려는 경우 API를 캡슐화하고 `HttpClient` 기준 주소를 중앙에서 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-354">If you're going to make many requests to a given set of APIs, it's a good idea to encapsulate your APIs and configure the `HttpClient` base address centrally.</span></span> <span data-ttu-id="a85e8-355">이렇게 하면 환경 간에 해당 설정을 조정해야 하는 경우 한 곳에서만 변경 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-355">This way, if you need to adjust any of these settings between environments, you can make the changes in just one place.</span></span> <span data-ttu-id="a85e8-356">`Program.Main`에서 해당 서비스 지원을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-356">You should add support for this service in your `Program.Main`:</span></span>

```csharp
builder.Services.AddScoped(sp =>
    new HttpClient
    {
        BaseAddress = new Uri(builder.HostEnvironment.BaseAddress)
    });
```

<span data-ttu-id="a85e8-357">서비스에 안전하게 액세스해야 하는 경우 보안 토큰에 액세스하고 모든 요청에서 해당 토큰을 인증 헤더로 전달하도록 `HttpClient`를 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-357">If you need to access services securely, you should access a secure token and configure the `HttpClient` to pass this token as an Authentication header with every request:</span></span>

```csharp
_httpClient.DefaultRequestHeaders.Authorization =
    new AuthenticationHeaderValue("Bearer", token);
```

<span data-ttu-id="a85e8-358">`HttpClient`가 `Transient` 수명을 사용하여 애플리케이션 서비스에 추가되지 않은 경우 `HttpClient`가 삽입된 모든 구성 요소에서 해당 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-358">This activity can be done from any component that has the `HttpClient` injected into it, provided that `HttpClient` wasn't added to the application's services with a `Transient` lifetime.</span></span> <span data-ttu-id="a85e8-359">애플리케이션의 `HttpClient`에 대한 모든 참조는 동일한 인스턴스를 참조하므로 한 구성 요소의 변경 내용은 전체 애플리케이션에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-359">Every reference to `HttpClient` in the application references the same instance, so changes to it in one component flow through the entire application.</span></span> <span data-ttu-id="a85e8-360">토큰을 지정하여 해당 인증 검사를 수행할 좋은 위치는 사이트의 주 탐색 같은 공유 구성 요소에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-360">A good place to perform this authentication check (followed by specifying the token) is in a shared component like the main navigation for the site.</span></span> <span data-ttu-id="a85e8-361">[eShopOnWeb 참조 애플리케이션](https://github.com/dotnet-architecture/eShopOnWeb)의 `BlazorAdmin` 프로젝트에서 해당 접근 방식을 자세히 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-361">Learn more about this approach in the `BlazorAdmin` project in the [eShopOnWeb reference application](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

<span data-ttu-id="a85e8-362">기존 JavaScript SPA를 통한 Blazor WebAssembly의 한 가지 이점은 DTO(데이터 전송 개체)의 복사본을 계속 동기화하지 않아도 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-362">One benefit of Blazor WebAssembly over traditional JavaScript SPAs is that you don't need to keep to copies of your data transfer objects(DTOs) synchronized.</span></span> <span data-ttu-id="a85e8-363">Blazor WebAssembly 프로젝트와 웹 API 프로젝트는 둘 다 공통 공유 프로젝트에서 동일한 DTO를 공유할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-363">Your Blazor WebAssembly project and your web API project can both share the same DTOs in a common shared project.</span></span> <span data-ttu-id="a85e8-364">이렇게 하면 SPA 개발과 관련된 일부 충돌이 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-364">This approach eliminates some of the friction involved in developing SPAs.</span></span>

<span data-ttu-id="a85e8-365">API 엔드포인트에서 데이터를 빠르게 가져오는 데는 기본 제공 도우미 메서드인 `GetFromJsonAsync`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-365">To quickly get data from an API endpoint, you can use the built-in helper method, `GetFromJsonAsync`.</span></span> <span data-ttu-id="a85e8-366">POST, PUT 등을 위한 유사한 메서드가 있습니다. 다음은 Blazor WebAssembly 앱에서 구성된 `HttpClient`를 사용하여 API 엔드포인트에서 CatalogItem을 가져오는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-366">There are similar methods for POST, PUT, etc. The following shows how to get a CatalogItem from an API endpoint using a configured `HttpClient` in a Blazor WebAssembly app:</span></span>

```csharp
var item = await _httpClient.GetFromJsonAsync<CatalogItem>($"catalog-items/{id}");
```

<span data-ttu-id="a85e8-367">필요한 데이터가 있으면 일반적으로 변경 내용을 로컬에서 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-367">Once you have the data you need, you'll typically track changes locally.</span></span> <span data-ttu-id="a85e8-368">백 엔드 데이터 저장소를 업데이트하려는 경우 해당 목적을 위해 추가 웹 API를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a85e8-368">When you want to make updates to the backend data store, you'll call additional web APIs for this purpose.</span></span>

<span data-ttu-id="a85e8-369">**참조 – Blazor 데이터**</span><span class="sxs-lookup"><span data-stu-id="a85e8-369">**References – Blazor Data**</span></span>

- <span data-ttu-id="a85e8-370">ASP.NET Core Blazor에서 웹 API 호출</span><span class="sxs-lookup"><span data-stu-id="a85e8-370">Call a web API from ASP.NET Core Blazor</span></span>
  <https://docs.microsoft.com/aspnet/core/blazor/call-web-api>

>[!div class="step-by-step"]
><span data-ttu-id="a85e8-371">[이전](develop-asp-net-core-mvc-apps.md)
>[다음](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a85e8-371">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
