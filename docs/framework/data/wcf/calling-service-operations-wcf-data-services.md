---
description: '자세한 정보: 서비스 작업 호출 (WCF Data Services)'
title: 서비스 작업 호출(WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 49b08581e42fcd20b9d560d73379eb43ebbf2eb4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766467"
---
# <a name="calling-service-operations-wcf-data-services"></a><span data-ttu-id="83a22-103">서비스 작업 호출(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="83a22-103">Calling Service Operations (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="83a22-104">OData (Open Data Protocol)는 데이터 서비스에 대 한 서비스 작업을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-104">The Open Data Protocol (OData) defines service operations for a data service.</span></span> <span data-ttu-id="83a22-105">WCF Data Services를 사용 하면 데이터 서비스에서 메서드로 이러한 작업을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-105">WCF Data Services enables you to define such operations as methods on the data service.</span></span> <span data-ttu-id="83a22-106">다른 데이터 서비스 리소스와 마찬가지로, 이러한 서비스 작업도 URI를 사용하여 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-106">Like other data service resources, these service operations are addressed by using URIs.</span></span> <span data-ttu-id="83a22-107">서비스 작업은 엔터티 형식의 컬렉션, 단일 엔터티 형식 인스턴스, 그리고 정수, 문자열과 같은 기본 형식을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-107">A service operation can return collections of entity types, single entity type instances, and primitive types, such as integer and string.</span></span> <span data-ttu-id="83a22-108">서비스 작업은 `null`(Visual Basic에서 `Nothing`)도 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-108">A service operation can also return `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="83a22-109">WCF Data Services 클라이언트 라이브러리를 사용 하 여 HTTP GET 요청을 지 원하는 서비스 작업에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-109">The WCF Data Services client library can be used to access service operations that support HTTP GET requests.</span></span> <span data-ttu-id="83a22-110">이러한 종류의 서비스 작업은 <xref:System.ServiceModel.Web.WebGetAttribute>가 적용된 메서드로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-110">These kinds of service operations are defined as methods that have the <xref:System.ServiceModel.Web.WebGetAttribute> applied.</span></span> <span data-ttu-id="83a22-111">자세한 내용은 [서비스 작업](service-operations-wcf-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a22-111">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="83a22-112">서비스 작업은 OData를 구현 하는 데이터 서비스에서 반환 하는 메타 데이터에 노출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-112">Service operations are exposed in the metadata returned by a data service that implements the OData.</span></span> <span data-ttu-id="83a22-113">메타데이터에서 서비스 작업은 `FunctionImport` 요소로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-113">In the metadata, service operations are represented as `FunctionImport` elements.</span></span> <span data-ttu-id="83a22-114">강력한 형식의를 생성할 때 <xref:System.Data.Services.Client.DataServiceContext> 서비스 참조 추가 및 DataSvcUtil.exe 도구는이 요소를 무시 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-114">When generating the strongly typed <xref:System.Data.Services.Client.DataServiceContext>, the Add Service Reference and DataSvcUtil.exe tools ignore this element.</span></span> <span data-ttu-id="83a22-115">이 때문에 서비스 작업을 직접 호출하는 데 사용할 수 있는 컨텍스트에서 메서드를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-115">Because of this, you will not find a method on the context that can be used to call a service operation directly.</span></span> <span data-ttu-id="83a22-116">그러나 다음 두 가지 방법 중 하나로 WCF Data Services 클라이언트를 사용 하 여 서비스 작업을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-116">However, you can still use the WCF Data Services client to call service operations in one of these two ways:</span></span>  
  
- <span data-ttu-id="83a22-117">기타 매개 변수와 함께 서비스 작업의 URI를 제공하여 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A>에 <xref:System.Data.Services.Client.DataServiceContext> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-117">By calling the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method on the <xref:System.Data.Services.Client.DataServiceContext>, supplying the URI of the service operation, along with any parameters.</span></span> <span data-ttu-id="83a22-118">이 메서드는 모든 GET 서비스 작업을 호출하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-118">This method is used to call any GET service operation.</span></span>  
  
- <span data-ttu-id="83a22-119"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>에서 <xref:System.Data.Services.Client.DataServiceContext> 메서드를 사용하여 <xref:System.Data.Services.Client.DataServiceQuery%601> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-119">By using the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> method on the <xref:System.Data.Services.Client.DataServiceContext> to create a <xref:System.Data.Services.Client.DataServiceQuery%601> object.</span></span> <span data-ttu-id="83a22-120"><xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>를 호출하면 서비스 작업의 이름이 `entitySetName` 매개 변수에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-120">When calling <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>, the name of the service operation is supplied to the `entitySetName` parameter.</span></span> <span data-ttu-id="83a22-121">이 메서드는 열거될 때 또는 <xref:System.Data.Services.Client.DataServiceQuery%601> 메서드가 호출될 때 서비스 작업을 호출하는 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-121">This method returns a <xref:System.Data.Services.Client.DataServiceQuery%601> object that calls the service operation when enumerated or when the <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> method is called.</span></span> <span data-ttu-id="83a22-122">이 메서드는 컬렉션을 반환하는 GET 서비스 작업을 호출하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-122">This method is used to call GET service operations that return a collection.</span></span> <span data-ttu-id="83a22-123"><xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 메서드를 사용하면 단일 매개 변수를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-123">A single parameter can be supplied by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="83a22-124">이 메서드에서 반환한 <xref:System.Data.Services.Client.DataServiceQuery%601> 개체는 모든 쿼리 개체와 같이 추가 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-124">The <xref:System.Data.Services.Client.DataServiceQuery%601> object returned by this method can be further composed against like any query object.</span></span> <span data-ttu-id="83a22-125">자세한 내용은 [데이터 서비스 쿼리](querying-the-data-service-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a22-125">For more information, see [Querying the Data Service](querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="considerations-for-calling-service-operations"></a><span data-ttu-id="83a22-126">서비스 작업 호출에 대한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="83a22-126">Considerations for Calling Service Operations</span></span>  

 <span data-ttu-id="83a22-127">WCF Data Services 클라이언트를 사용 하 여 서비스 작업을 호출 하는 경우 다음 사항을 고려해 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-127">The following considerations apply when using the WCF Data Services client to call service operations.</span></span>  
  
- <span data-ttu-id="83a22-128">데이터 서비스에 비동기적으로 액세스 하는 경우에는 해당 비동기 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> 메서드 <xref:System.Data.Services.Client.DataServiceContext> 또는의 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> / <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 메서드 <xref:System.Data.Services.Client.DataServiceQuery%601> 를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-128">When accessing the data service asynchronously, you must use the equivalent asynchronous <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceContext> or the <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> methods on <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span>  
  
- <span data-ttu-id="83a22-129">WCF Data Services 클라이언트 라이브러리는 기본 형식의 컬렉션을 반환 하는 서비스 작업의 결과를 구체화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-129">The WCF Data Services client library cannot materialize the results from a service operation that returns a collection of primitive types.</span></span>  
  
- <span data-ttu-id="83a22-130">WCF Data Services 클라이언트 라이브러리는 사후 서비스 작업 호출을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-130">The WCF Data Services client library does not support calling POST service operations.</span></span> <span data-ttu-id="83a22-131">HTTP POST에서 호출하는 서비스 작업은 <xref:System.ServiceModel.Web.WebInvokeAttribute> 매개 변수와 `Method="POST"`를 사용하여 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-131">Service operations that are called by an HTTP POST are defined by using the <xref:System.ServiceModel.Web.WebInvokeAttribute> with the `Method="POST"` parameter.</span></span> <span data-ttu-id="83a22-132">HTTP POST 요청을 사용하여 서비스 작업을 호출하려면 대신 <xref:System.Net.HttpWebRequest>를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-132">To call a service operation by using an HTTP POST request, you must instead use an <xref:System.Net.HttpWebRequest>.</span></span>  
  
- <span data-ttu-id="83a22-133">엔터티 또는 기본 형식의 단일 결과 또는 두 개 이상의 입력 매개 변수가 필요한 단일 결과를 반환하는 GET 서비스 작업을 호출하기 위해 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-133">You cannot use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a GET service operation that returns a single result, of either entity or primitive type, or that requires more than one input parameter.</span></span> <span data-ttu-id="83a22-134">대신 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-134">You must instead call the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method.</span></span>  
  
- <span data-ttu-id="83a22-135"><xref:System.Data.Services.Client.DataServiceContext>도구에서 생성 되 고 또는 메서드를 사용 하 여 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 서비스 작업을 호출 하는 강력한 형식의 부분 클래스에 확장 메서드를 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-135">Consider creating an extension method on the strongly typed <xref:System.Data.Services.Client.DataServiceContext> partial class, which is generated by the tools, that uses either the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> or the <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> method to call a service operation.</span></span> <span data-ttu-id="83a22-136">이렇게 하면 컨텍스트에서 직접 서비스 작업을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-136">This enables you to call service operations directly from the context.</span></span> <span data-ttu-id="83a22-137">자세한 내용은 블로그 게시물 [서비스 작업 및 WCF Data Services 클라이언트](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="83a22-137">For more information, see the blog post [Service Operations and the WCF Data Services Client](/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client).</span></span>  
  
- <span data-ttu-id="83a22-138">를 사용 하 여 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 서비스 작업을 호출 하는 경우 클라이언트 라이브러리는 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 앰퍼샌드 (&)와 같은 예약 문자의 백분율 인코딩 및 문자열의 작은따옴표 이스케이프를 수행 하 여에 제공 된 문자를 자동으로 이스케이프 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-138">When you use <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to call a service operation, the client library automatically escapes characters supplied to the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> by performing percent-encoding of reserved characters, such as ampersand (&), and escaping of single-quotes in strings.</span></span> <span data-ttu-id="83a22-139">그러나 *Execute* 메서드 중 하나를 호출 하 여 서비스 작업을 호출 하는 경우 사용자가 제공 하는 문자열 값의 이스케이프를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-139">However, when you call one of the *Execute* methods to call a service operation, you must remember to perform this escaping of any user-supplied string values.</span></span> <span data-ttu-id="83a22-140">URI의 작은 따옴표는 작은 따옴표의 쌍으로 이스케이프됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-140">Single-quotes in URIs are escaped as pairs of single-quotes.</span></span>  
  
## <a name="examples-of-calling-service-operations"></a><span data-ttu-id="83a22-141">서비스 작업 호출 예제</span><span class="sxs-lookup"><span data-stu-id="83a22-141">Examples of Calling Service Operations</span></span>  

 <span data-ttu-id="83a22-142">이 섹션에는 WCF Data Services 클라이언트 라이브러리를 사용 하 여 서비스 작업을 호출 하는 방법에 대 한 다음 예제가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-142">This section contains the following examples of how to call service operations by using the WCF Data Services client library:</span></span>  
  
- [<span data-ttu-id="83a22-143">T 실행 &lt; &gt; 을 호출 하 여 엔터티 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-143">Calling Execute&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [<span data-ttu-id="83a22-144">CreateQuery T를 사용 하 여 &lt; &gt; 엔터티 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-144">Using CreateQuery&lt;T&gt; to Return a Collection of Entities</span></span>](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [<span data-ttu-id="83a22-145">&lt; &gt; 단일 엔터티를 반환 하기 위해 T 실행 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-145">Calling Execute&lt;T&gt; to Return a Single Entity</span></span>](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [<span data-ttu-id="83a22-146">T 실행 &lt; &gt; 을 호출 하 여 기본 값 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-146">Calling Execute&lt;T&gt; to Return a Collection of Primitive Values</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [<span data-ttu-id="83a22-147">&lt; &gt; 단일 기본 값을 반환 하기 위해 T 실행을 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-147">Calling Execute&lt;T&gt; to Return a Single Primitive Value</span></span>](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [<span data-ttu-id="83a22-148">데이터를 반환하지 않는 서비스 작업 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-148">Calling a Service Operation that Returns No Data</span></span>](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [<span data-ttu-id="83a22-149">서비스 작업을 비동기적으로 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-149">Calling a Service Operation Asynchronously</span></span>](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>

### <a name="calling-executet-to-return-a-collection-of-entities"></a><span data-ttu-id="83a22-150">Execute \<T> 를 호출 하 여 엔터티 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-150">Calling Execute\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="83a22-151">다음 예제는 `city` 문자열 매개 변수를 사용하고 <xref:System.Linq.IQueryable%601>을 반환하는 GetOrdersByCity라는 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-151">The following example calls a service operation named GetOrdersByCity, which takes a string parameter of `city` and returns an <xref:System.Linq.IQueryable%601>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 <span data-ttu-id="83a22-152">이 예제에서는 서비스 작업이 관련 `Order` 개체를 사용하여 `Order_Detail` 개체의 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-152">In this example, the service operation returns a collection of `Order` objects with related `Order_Detail` objects.</span></span>  
  
<a name="CreateQueryIQueryable"></a>

### <a name="using-createqueryt-to-return-a-collection-of-entities"></a><span data-ttu-id="83a22-153">CreateQuery를 사용 하 여 \<T> 엔터티 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-153">Using CreateQuery\<T> to Return a Collection of Entities</span></span>  

 <span data-ttu-id="83a22-154">다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>를 사용하여 동일한 GetOrdersByCity 서비스 작업을 호출하는 데 사용되는 <xref:System.Data.Services.Client.DataServiceQuery%601>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-154">The following example uses the <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> to return a <xref:System.Data.Services.Client.DataServiceQuery%601> that is used to call the same GetOrdersByCity service operation:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 <span data-ttu-id="83a22-155">이 예제에서 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 메서드는 쿼리에 매개 변수를 추가하는 데 사용되고 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드는 관련 Order_Details 개체를 결과에 포함하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-155">In this example, the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method is used to add the parameter to the query, and the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is used to include related Order_Details objects in the results.</span></span>  
  
<a name="ExecuteSingleEntity"></a>

### <a name="calling-executet-to-return-a-single-entity"></a><span data-ttu-id="83a22-156">Execute \<T> 를 호출 하 여 단일 엔터티 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-156">Calling Execute\<T> to Return a Single Entity</span></span>  

 <span data-ttu-id="83a22-157">다음 예제에서는 단일 Order 엔터티만 반환하는 GetNewestOrder라는 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-157">The following example calls a service operation named GetNewestOrder that returns only a single Order entity:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 <span data-ttu-id="83a22-158">이 예제에서 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 메서드는 실행 시 단일 Order 엔터티만 요청하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-158">In this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single Order entity on execution.</span></span>  
  
<a name="ExecutePrimitiveCollection"></a>

### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a><span data-ttu-id="83a22-159">Execute \<T> 를 호출 하 여 기본 값 컬렉션 반환</span><span class="sxs-lookup"><span data-stu-id="83a22-159">Calling Execute\<T> to Return a Collection of Primitive Values</span></span>  

 <span data-ttu-id="83a22-160">다음 예제에서는 문자열 값의 컬렉션을 반환하는 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-160">The following example calls a service operation that returns a collection of string values:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>

### <a name="calling-executet-to-return-a-single-primitive-value"></a><span data-ttu-id="83a22-161">\<T>단일 기본 값을 반환 하려면 Execute 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-161">Calling Execute\<T> to Return a Single Primitive Value</span></span>  

 <span data-ttu-id="83a22-162">다음 예제에서는 단일 문자열 값을 반환하는 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-162">The following example calls a service operation that returns a single string value:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 <span data-ttu-id="83a22-163">이 예제에서는 다시 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 메서드를 사용하여 실행 시 단일 정수 값만 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-163">Again in this example, the <xref:System.Linq.Enumerable.FirstOrDefault%2A> method is used to request only a single integer value on execution.</span></span>  
  
<a name="ExecuteVoid"></a>

### <a name="calling-a-service-operation-that-returns-no-data"></a><span data-ttu-id="83a22-164">데이터를 반환하지 않는 서비스 작업 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-164">Calling a Service Operation that Returns No Data</span></span>  

 <span data-ttu-id="83a22-165">다음 예제에서는 데이터를 반환하지 않는 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-165">The following example calls a service operation that returns no data:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 <span data-ttu-id="83a22-166">데이터가 반환되지 않기 때문에 실행 값이 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-166">Because not data is returned, the value of the execution is not assigned.</span></span> <span data-ttu-id="83a22-167">요청이 성공했다는 유일한 표시는 <xref:System.Data.Services.Client.DataServiceQueryException>이 발생하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-167">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
<a name="ExecuteAsync"></a>

### <a name="calling-a-service-operation-asynchronously"></a><span data-ttu-id="83a22-168">서비스 작업을 비동기적으로 호출</span><span class="sxs-lookup"><span data-stu-id="83a22-168">Calling a Service Operation Asynchronously</span></span>  

 <span data-ttu-id="83a22-169">다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> 및 <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>를 호출하여 서비스 작업을 비동기적으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-169">The following example calls a service operation asynchronously by calling <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> and <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 <span data-ttu-id="83a22-170">데이터가 반환되지 않기 때문에 실행으로 반환된 값이 할당되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-170">Because no data is returned, the value returned by the execution is not assigned.</span></span> <span data-ttu-id="83a22-171">요청이 성공했다는 유일한 표시는 <xref:System.Data.Services.Client.DataServiceQueryException>이 발생하지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-171">The only indication that the request has succeeded is that no <xref:System.Data.Services.Client.DataServiceQueryException> is raised.</span></span>  
  
 <span data-ttu-id="83a22-172">다음 예제에서는 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>를 사용하여 동일한 서비스 작업을 비동기적으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="83a22-172">The following example calls the same service operation asynchronously by using <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>:</span></span>  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a><span data-ttu-id="83a22-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="83a22-173">See also</span></span>

- [<span data-ttu-id="83a22-174">WCF Data Services 클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="83a22-174">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)
