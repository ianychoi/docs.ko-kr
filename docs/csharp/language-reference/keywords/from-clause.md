---
description: from 절 - C# 참조
title: from 절 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- from_CSharpKeyword
- from
helpviewer_keywords:
- from clause [C#]
- from keyword [C#]
ms.assetid: 1aefd18c-1314-47f8-99ec-9bcefb09e699
ms.openlocfilehash: 474b22f5a9d8f12c8a4365159817f878761b563c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89140791"
---
# <a name="from-clause-c-reference"></a><span data-ttu-id="77a4d-103">from 절(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="77a4d-103">from clause (C# Reference)</span></span>

<span data-ttu-id="77a4d-104">쿼리 식은 `from` 절로 시작해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-104">A query expression must begin with a `from` clause.</span></span> <span data-ttu-id="77a4d-105">또한 쿼리 식은 `from` 절로 시작하는 하위 쿼리를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-105">Additionally, a query expression can contain sub-queries, which also begin with a `from` clause.</span></span> <span data-ttu-id="77a4d-106">`from` 절은 다음 내용을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-106">The `from` clause specifies the following:</span></span>

- <span data-ttu-id="77a4d-107">쿼리 또는 하위 쿼리가 실행될 데이터 소스.</span><span class="sxs-lookup"><span data-stu-id="77a4d-107">The data source on which the query or sub-query will be run.</span></span>

- <span data-ttu-id="77a4d-108">소스 시퀀스의 각 요소를 나타내는 지역 *범위 변수*.</span><span class="sxs-lookup"><span data-stu-id="77a4d-108">A local *range variable* that represents each element in the source sequence.</span></span>

<span data-ttu-id="77a4d-109">범위 변수 및 데이터 소스 모두 강력한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-109">Both the range variable and the data source are strongly typed.</span></span> <span data-ttu-id="77a4d-110">`from` 절에서 참조되는 데이터 소스는 <xref:System.Collections.IEnumerable> 또는 <xref:System.Collections.Generic.IEnumerable%601> 형식이거나 <xref:System.Linq.IQueryable%601>와 같은 파생 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-110">The data source referenced in the `from` clause must have a type of <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, or a derived type such as <xref:System.Linq.IQueryable%601>.</span></span>

<span data-ttu-id="77a4d-111">다음 예제에서 `numbers`는 데이터 소스이고 `num`은 범위 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-111">In the following example, `numbers` is the data source and `num` is the range variable.</span></span> <span data-ttu-id="77a4d-112">[var](var.md) 키워드가 사용되어도 두 변수는 모두 강력한 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-112">Note that both variables are strongly typed even though the [var](var.md) keyword is used.</span></span>

[!code-csharp[cscsrefQueryKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#1)]

## <a name="the-range-variable"></a><span data-ttu-id="77a4d-113">범위 변수</span><span class="sxs-lookup"><span data-stu-id="77a4d-113">The range variable</span></span>

<span data-ttu-id="77a4d-114">컴파일러는 데이터 소스가 <xref:System.Collections.Generic.IEnumerable%601>을 구현할 경우 범위 변수의 형식을 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-114">The compiler infers the type of the range variable when the data source implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="77a4d-115">예를 들어, 소스의 형식이 `IEnumerable<Customer>`일 경우 범위 변수는 `Customer`로 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-115">For example, if the source has a type of `IEnumerable<Customer>`, then the range variable is inferred to be `Customer`.</span></span> <span data-ttu-id="77a4d-116">소스가 <xref:System.Collections.ArrayList>와 같이 제네릭이 아닌 `IEnumerable` 형식인 경우에만 형식을 명시적으로 지정하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-116">The only time that you must specify the type explicitly is when the source is a non-generic `IEnumerable` type such as <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="77a4d-117">자세한 내용은 [LINQ를 사용하여 ArrayList를 쿼리하는 방법](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77a4d-117">For more information, see [How to query an ArrayList with LINQ](../../programming-guide/concepts/linq/how-to-query-an-arraylist-with-linq.md).</span></span>

<span data-ttu-id="77a4d-118">위의 예제에서 `num`은 `int` 형식으로 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-118">In the previous example `num` is inferred to be of type `int`.</span></span> <span data-ttu-id="77a4d-119">범위 변수가 강력한 형식이므로 범위 변수에서 메서드를 호출하거나 다른 작업에서 범위 변수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-119">Because the range variable is strongly typed, you can call methods on it or use it in other operations.</span></span> <span data-ttu-id="77a4d-120">예를 들어 `select num`을 작성하는 대신에 `select num.ToString()`을 작성하여 쿼리 식에서 정수 대신 문자열 시퀀스를 반환하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-120">For example, instead of writing `select num`, you could write `select num.ToString()` to cause the query expression to return a sequence of strings instead of integers.</span></span> <span data-ttu-id="77a4d-121">또는 `select num + 10`을 작성하여 식에서 14, 11, 13, 12, 10 시퀀스를 반환하게 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-121">Or you could write `select num + 10` to cause the expression to return the sequence 14, 11, 13, 12, 10.</span></span> <span data-ttu-id="77a4d-122">자세한 내용은 [select 절](select-clause.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77a4d-122">For more information, see [select clause](select-clause.md).</span></span>

<span data-ttu-id="77a4d-123">범위 변수가 소스의 데이터를 실제로 저장하지 않는다는 매우 중요한 한 가지 차이점을 제외하면 범위 변수는 [foreach](foreach-in.md) 문의 반복 변수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-123">The range variable is like an iteration variable in a [foreach](foreach-in.md) statement except for one very important difference: a range variable never actually stores data from the source.</span></span> <span data-ttu-id="77a4d-124">범위 변수는 단순히 쿼리 실행 시에 발생하는 작업을 쿼리에서 설명할 수 있게 하는 구문상의 편리함을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-124">It's just a syntactic convenience that enables the query to describe what will occur when the query is executed.</span></span> <span data-ttu-id="77a4d-125">자세한 내용은 [LINQ 쿼리 소개(C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77a4d-125">For more information, see [Introduction to LINQ Queries (C#)](../../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

## <a name="compound-from-clauses"></a><span data-ttu-id="77a4d-126">복합 from 절</span><span class="sxs-lookup"><span data-stu-id="77a4d-126">Compound from clauses</span></span>

<span data-ttu-id="77a4d-127">경우에 따라 소스 시퀀스의 각 요소 자체가 시퀀스이거나 시퀀스를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-127">In some cases, each element in the source sequence may itself be either a sequence or contain a sequence.</span></span> <span data-ttu-id="77a4d-128">예를 들어, 시퀀스의 각 학생 개체에 테스트 점수 목록이 포함된 `IEnumerable<Student>`가 데이터 소스일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-128">For example, your data source may be an `IEnumerable<Student>` where each student object in the sequence contains a list of test scores.</span></span> <span data-ttu-id="77a4d-129">각 `Student` 요소 내의 내부 목록에 액세스하려면 복합 `from` 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-129">To access the inner list within each `Student` element, you can use compound `from` clauses.</span></span> <span data-ttu-id="77a4d-130">이 기술은 중첩된 [foreach](foreach-in.md) 문을 사용하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-130">The technique is like using nested [foreach](foreach-in.md) statements.</span></span> <span data-ttu-id="77a4d-131">[where](partial-method.md) 또는 [orderby](orderby-clause.md) 절을 둘 중 하나의 `from` 절에 추가하여 결과를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-131">You can add [where](partial-method.md) or [orderby](orderby-clause.md) clauses to either `from` clause to filter the results.</span></span> <span data-ttu-id="77a4d-132">다음 예제에서는 테스트 점수를 나타내는 정수의 내부 `List`를 각각 포함하는 `Student` 개체의 시퀀스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-132">The following example shows a sequence of `Student` objects, each of which contains an inner `List` of integers representing test scores.</span></span> <span data-ttu-id="77a4d-133">내부 목록에 액세스하려면 복합 `from` 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-133">To access the inner list, use a compound `from` clause.</span></span> <span data-ttu-id="77a4d-134">필요한 경우 두 `from` 절 사이에 다른 절을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-134">You can insert clauses between the two `from` clauses if necessary.</span></span>

[!code-csharp[cscsrefQueryKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#2)]

## <a name="using-multiple-from-clauses-to-perform-joins"></a><span data-ttu-id="77a4d-135">여러 from 절을 사용하여 조인 수행</span><span class="sxs-lookup"><span data-stu-id="77a4d-135">Using Multiple from Clauses to Perform Joins</span></span>

<span data-ttu-id="77a4d-136">복합 `from` 절은 단일 데이터 소스의 내부 컬렉션에 액세스하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-136">A compound `from` clause is used to access inner collections in a single data source.</span></span> <span data-ttu-id="77a4d-137">그러나 독립 데이터 소스의 추가 쿼리를 생성하는 여러 `from` 절이 쿼리에 포함될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-137">However, a query can also contain multiple `from` clauses that generate supplemental queries from independent data sources.</span></span> <span data-ttu-id="77a4d-138">이 기술을 사용하면 [join 절](join-clause.md)로 수행할 수 없는 특정 형식의 조인 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-138">This technique enables you to perform certain types of join operations that are not possible by using the [join clause](join-clause.md).</span></span>

<span data-ttu-id="77a4d-139">다음 예제는 두 개의 `from` 절을 사용하여 두 개의 데이터 소스의 완전한 크로스 조인을 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="77a4d-139">The following example shows how two `from` clauses can be used to form a complete cross join of two data sources.</span></span>

[!code-csharp[cscsrefQueryKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/From.cs#3)]

<span data-ttu-id="77a4d-140">여러 `from` 절을 사용하는 조인 작업에 대한 자세한 내용은 [왼쪽 우선 외부 조인 수행](../../linq/perform-left-outer-joins.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="77a4d-140">For more information about join operations that use multiple `from` clauses, see [Perform left outer joins](../../linq/perform-left-outer-joins.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77a4d-141">참고 항목</span><span class="sxs-lookup"><span data-stu-id="77a4d-141">See also</span></span>

- [<span data-ttu-id="77a4d-142">쿼리 키워드(LINQ)</span><span class="sxs-lookup"><span data-stu-id="77a4d-142">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="77a4d-143">LINQ(Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="77a4d-143">Language Integrated Query (LINQ)</span></span>](../../linq/index.md)
