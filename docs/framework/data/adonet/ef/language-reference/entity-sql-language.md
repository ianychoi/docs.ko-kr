---
description: Entity SQL 언어에 대해 자세히 알아보세요.
title: Entity SQL 언어
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: c05e561e5da3f9ee8788a25f8ca97b22444e109f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724572"
---
# <a name="entity-sql-language"></a><span data-ttu-id="71805-103">Entity SQL 언어</span><span class="sxs-lookup"><span data-stu-id="71805-103">Entity SQL Language</span></span>

<span data-ttu-id="71805-104">Entity SQL은 SQL과 유사한 스토리지 독립적 쿼리 언어입니다.</span><span class="sxs-lookup"><span data-stu-id="71805-104">Entity SQL is a storage-independent query language that is similar to SQL.</span></span> <span data-ttu-id="71805-105">Entity SQL을 사용하면 엔터티 데이터를 개체 또는 테이블 형식으로 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71805-105">Entity SQL allows you to query entity data, either as objects or in a tabular form.</span></span> <span data-ttu-id="71805-106">Entity SQL은 다음의 경우에 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71805-106">You should consider using Entity SQL in the following cases:</span></span>  
  
- <span data-ttu-id="71805-107">쿼리를 동적으로 런타임에 생성해야 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="71805-107">When a query must be dynamically constructed at runtime.</span></span> <span data-ttu-id="71805-108">이 경우에는 런타임에 Entity SQL 쿼리 문자열을 생성하는 대신 <xref:System.Data.Objects.ObjectQuery%601>의 쿼리 작성기 메서드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="71805-108">In this case, you should also consider using the query builder methods of <xref:System.Data.Objects.ObjectQuery%601> instead of constructing an Entity SQL query string at runtime.</span></span>  
  
- <span data-ttu-id="71805-109">쿼리를 모델 정의의 일부로 정의할 경우.</span><span class="sxs-lookup"><span data-stu-id="71805-109">When you want to define a query as part of the model definition.</span></span> <span data-ttu-id="71805-110">Entity SQL만 데이터 모델에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="71805-110">Only Entity SQL is supported in a data model.</span></span> <span data-ttu-id="71805-111">자세한 내용은 [QueryView 요소 (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="71805-111">For more information, see [QueryView Element (MSL)](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)</span></span>  
  
- <span data-ttu-id="71805-112">EntityClient에서 <xref:System.Data.EntityClient.EntityDataReader>를 사용하여 읽기 전용 엔터티 데이터를 행 집합으로 반환할 경우.</span><span class="sxs-lookup"><span data-stu-id="71805-112">When using EntityClient to return read-only entity data as rowsets using a <xref:System.Data.EntityClient.EntityDataReader>.</span></span> <span data-ttu-id="71805-113">자세한 내용은 [Entity Framework용 EntityClient 공급자](../entityclient-provider-for-the-entity-framework.md)(영문)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71805-113">For more information, see [EntityClient Provider for the Entity Framework](../entityclient-provider-for-the-entity-framework.md).</span></span>  
  
- <span data-ttu-id="71805-114">SQL 기반 쿼리 언어의 전문가에게는 Entity SQL이 가장 편할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="71805-114">If you are already an expert in SQL-based query languages, Entity SQL may seem the most natural to you.</span></span>  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a><span data-ttu-id="71805-115">EntityClient 공급자와 함께 Entity SQL 사용</span><span class="sxs-lookup"><span data-stu-id="71805-115">Using Entity SQL with the EntityClient provider</span></span>  

 <span data-ttu-id="71805-116">EntityClient 공급자와 함께 Entity SQL을 사용하려는 경우 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71805-116">If you want to use Entity SQL with the EntityClient provider, see the following topics for more information:</span></span>  
  
 [<span data-ttu-id="71805-117">Entity Framework용 EntityClient 공급자</span><span class="sxs-lookup"><span data-stu-id="71805-117">EntityClient Provider for the Entity Framework</span></span>](../entityclient-provider-for-the-entity-framework.md)  
  
 [<span data-ttu-id="71805-118">방법: EntityConnection 연결 문자열 빌드</span><span class="sxs-lookup"><span data-stu-id="71805-118">How to: Build an EntityConnection Connection String</span></span>](../how-to-build-an-entityconnection-connection-string.md)  
  
 [<span data-ttu-id="71805-119">방법: PrimitiveType 결과를 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-119">How to: Execute a Query that Returns PrimitiveType Results</span></span>](../how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [<span data-ttu-id="71805-120">방법: StructuralType 결과를 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-120">How to: Execute a Query that Returns StructuralType Results</span></span>](../how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [<span data-ttu-id="71805-121">방법: RefType 결과를 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-121">How to: Execute a Query that Returns RefType Results</span></span>](../how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [<span data-ttu-id="71805-122">방법: 복합 형식을 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-122">How to: Execute a Query that Returns Complex Types</span></span>](../how-to-execute-a-query-that-returns-complex-types.md)  
  
 [<span data-ttu-id="71805-123">방법: 중첩 컬렉션을 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-123">How to: Execute a Query that Returns Nested Collections</span></span>](../how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [<span data-ttu-id="71805-124">방법: EntityCommand를 사용하여 매개 변수가 있는 Entity SQL 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-124">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>](../how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [<span data-ttu-id="71805-125">방법: EntityCommand를 사용하여 매개 변수 있는 저장 프로시저 실행</span><span class="sxs-lookup"><span data-stu-id="71805-125">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>](../how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [<span data-ttu-id="71805-126">방법: 다형성 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="71805-126">How to: Execute a Polymorphic Query</span></span>](../how-to-execute-a-polymorphic-query.md)  
  
 [<span data-ttu-id="71805-127">방법: 탐색 연산자로 관계 탐색</span><span class="sxs-lookup"><span data-stu-id="71805-127">How to: Navigate Relationships with the Navigate Operator</span></span>](../how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a><span data-ttu-id="71805-128">개체 쿼리와 함께 Entity SQL 사용</span><span class="sxs-lookup"><span data-stu-id="71805-128">Using Entity SQL with object queries</span></span>  

 <span data-ttu-id="71805-129">개체 쿼리와 함께 Entity SQL을 사용하려는 경우 자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="71805-129">If you want to use Entity SQL with object queries, see the following topics for more information:</span></span>  
  
 <span data-ttu-id="71805-130">[방법: 엔터티 형식 개체를 반환하는 쿼리 실행](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-130">[How to: Execute a Query that Returns Entity Type Objects](/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-131">[방법: 매개 변수가 있는 쿼리 실행](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-131">[How to: Execute a Parameterized Query](/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-132">[방법: 탐색 속성을 사용하여 관계 탐색](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-132">[How to: Navigate Relationships Using Navigation Properties](/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-133">[방법: 사용자 정의 함수 호출](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-133">[How to: Call a User-Defined Function](/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-134">[방법: 데이터 필터링](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-134">[How to: Filter Data](/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-135">[방법: 데이터 정렬](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-135">[How to: Sort Data](/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-136">[방법: 데이터 그룹화](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-136">[How to: Group Data](/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-137">[방법: 데이터 집계](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-137">[How to: Aggregate Data](/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-138">[방법: 익명 형식 개체를 반환하는 쿼리 실행](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-138">[How to: Execute a Query that Returns Anonymous Type Objects](/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-139">[방법: 기본 형식의 컬렉션을 반환하는 쿼리 실행](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-139">[How to: Execute a Query that Returns a Collection of Primitive Types](/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-140">[방법: EntityCollection에서 관련 개체 쿼리](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-140">[How to: Query Related Objects in an EntityCollection](/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-141">[방법: 두 개의 쿼리의 공용 구조체 정렬](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-141">[How to: Order the Union of Two Queries](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))</span></span>  
  
 <span data-ttu-id="71805-142">[방법: 쿼리 결과를 통해 페이징](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="71805-142">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71805-143">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="71805-143">In This Section</span></span>  

 [<span data-ttu-id="71805-144">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="71805-144">Entity SQL Overview</span></span>](entity-sql-overview.md)  
  
 [<span data-ttu-id="71805-145">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="71805-145">Entity SQL Reference</span></span>](entity-sql-reference.md)  
  
## <a name="see-also"></a><span data-ttu-id="71805-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="71805-146">See also</span></span>

- [<span data-ttu-id="71805-147">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="71805-147">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="71805-148">언어 참조</span><span class="sxs-lookup"><span data-stu-id="71805-148">Language Reference</span></span>](index.md)
