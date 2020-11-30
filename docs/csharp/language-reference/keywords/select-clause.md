---
description: select 절 - C# 참조
title: select 절 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: d67c99cc841c08a63cc83843a07a46e80199b9d1
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89136904"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="25342-103">select 절(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="25342-103">select clause (C# Reference)</span></span>

<span data-ttu-id="25342-104">쿼리 식에서 `select` 절은 쿼리를 실행할 때 생성되는 값의 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-104">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="25342-105">결과는 모든 이전 절의 평가와 `select` 절 자체의 모든 계산을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-105">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="25342-106">쿼리 식은 `select` 절이나 [group](group-clause.md) 절로 끝나야 합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-106">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="25342-107">다음 예제에서는 쿼리 식의 간단한 `select` 절을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25342-107">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="25342-108">`select` 절에서 생성된 시퀀스의 형식에 따라 쿼리 변수 `queryHighScores`의 형식이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="25342-108">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="25342-109">가장 단순한 경우에서는 `select` 절이 범위 변수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-109">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="25342-110">이렇게 하면 반환된 시퀀스에 데이터 소스와 동일한 형식의 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="25342-110">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="25342-111">자세한 내용은 [LINQ 쿼리 작업의 형식 관계](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25342-111">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="25342-112">그러나 `select` 절은 소스 데이터를 새 형식으로 변환(또는 *프로젝션*)하기 위한 강력한 메커니즘도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-112">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="25342-113">자세한 내용은 [LINQ를 통한 데이터 변환(C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25342-113">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="25342-114">예제</span><span class="sxs-lookup"><span data-stu-id="25342-114">Example</span></span>

<span data-ttu-id="25342-115">다음 예제에서는 `select` 절에 사용할 수 있는 모든 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="25342-115">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="25342-116">각 쿼리에서 `select` 절과 *쿼리 변수* 형식(`studentQuery1`, `studentQuery2` 등) 간의 관계를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="25342-116">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="25342-117">앞의 예제에서 `studentQuery8`에 표시된 대로 반환된 시퀀스의 요소에 소스 요소의 속성 하위 집합만 포함하려는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25342-117">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="25342-118">반환된 시퀀스를 최대한 작게 유지하면 메모리 요구 사항을 줄이고 쿼리 실행 속도를 높일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25342-118">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="25342-119">`select` 절에서 무명 형식을 만들고 개체 이니셜라이저를 사용하여 소스 요소의 적절한 속성으로 초기화하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25342-119">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="25342-120">이 작업을 수행하는 방법의 예를 보려면 [개체 및 컬렉션 이니셜라이저](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="25342-120">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="25342-121">설명</span><span class="sxs-lookup"><span data-stu-id="25342-121">Remarks</span></span>

<span data-ttu-id="25342-122">컴파일 시간에 `select` 절은 <xref:System.Linq.Enumerable.Select%2A> 표준 쿼리 연산자에 대한 메서드 호출로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="25342-122">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="25342-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="25342-123">See also</span></span>

- [<span data-ttu-id="25342-124">C# 참조</span><span class="sxs-lookup"><span data-stu-id="25342-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="25342-125">쿼리 키워드(LINQ)</span><span class="sxs-lookup"><span data-stu-id="25342-125">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="25342-126">from 절</span><span class="sxs-lookup"><span data-stu-id="25342-126">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="25342-127">partial(메서드)(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="25342-127">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="25342-128">익명 형식</span><span class="sxs-lookup"><span data-stu-id="25342-128">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="25342-129">C#의 LINQ</span><span class="sxs-lookup"><span data-stu-id="25342-129">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="25342-130">LINQ(Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="25342-130">Language Integrated Query (LINQ)</span></span>](../../programming-guide/concepts/linq/index.md)
