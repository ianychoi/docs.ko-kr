---
description: '자세한 정보: 방법: 식 트리를 사용 하 여 동적 쿼리 빌드 (Visual Basic)'
title: '방법: 식 트리를 사용하여 동적 쿼리 빌드'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: bb8abb22749cbf7c15b72632f60a5bd08287378d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423097"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="4f431-103">방법: 식 트리를 사용 하 여 동적 쿼리 빌드 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f431-103">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="4f431-104">LINQ에서는 식 트리를 사용하여 <xref:System.Linq.IQueryable%601>을 구현하는 데이터 소스를 대상으로 하는 구조적 쿼리를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-104">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="4f431-105">예를 들어 LINQ 공급자는 관계형 데이터 저장소를 쿼리하기 위한 <xref:System.Linq.IQueryable%601> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-105">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="4f431-106">Visual Basic 컴파일러는 런타임에 식 트리를 작성 하는 코드로 이러한 데이터 소스를 대상으로 하는 쿼리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-106">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="4f431-107">그런 다음 쿼리 공급자는 식 트리 데이터 구조를 트래버스하고 데이터 소스에 적합한 쿼리 언어로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-107">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="4f431-108">식 트리는 LINQ에서 <xref:System.Linq.Expressions.Expression%601> 형식의 변수에 할당된 람다 식을 나타내는 데에도 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-108">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="4f431-109">이 항목에서는 식 트리를 사용하여 동적 LINQ 쿼리를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-109">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="4f431-110">동적 쿼리는 컴파일 시 쿼리의 세부 정보를 알 수 없는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-110">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="4f431-111">예를 들어 최종 사용자가 하나 이상의 조건자를 지정하여 데이터를 필터링할 수 있는 사용자 인터페이스를 애플리케이션에서 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-111">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="4f431-112">LINQ를 쿼리에 사용하려면 이러한 종류의 애플리케이션에서 식 트리를 사용하여 런타임에 LINQ 쿼리를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-112">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="4f431-113">예제</span><span class="sxs-lookup"><span data-stu-id="4f431-113">Example</span></span>

<span data-ttu-id="4f431-114">다음 예제에서는 식 트리를 사용하여 `IQueryable` 데이터 소스에 대한 쿼리를 생성한 다음 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-114">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="4f431-115">코드에서 다음 쿼리를 나타내는 식 트리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-115">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="4f431-116"><xref:System.Linq.Expressions> 네임스페이스의 팩터리 메서드는 전체 쿼리를 구성하는 식을 나타내는 식 트리를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-116">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="4f431-117">표준 쿼리 연산자 메서드 호출을 나타내는 식은 이러한 메서드의 <xref:System.Linq.Queryable> 구현을 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-117">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="4f431-118">최종 식 트리는 `IQueryable` 데이터 소스 공급자의 <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 구현에 전달되어 `IQueryable` 형식의 실행 가능한 쿼리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-118">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="4f431-119">해당 쿼리 변수를 열거하여 결과를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-119">The results are obtained by enumerating that query variable.</span></span>

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

<span data-ttu-id="4f431-120">이 코드는 `Queryable.Where` 메서드에 전달되는 조건자에 고정 개수의 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-120">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="4f431-121">그러나 사용자 입력에 따라 달라지는 가변 개수의 조건자 식을 결합하는 애플리케이션을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-121">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="4f431-122">사용자 입력에 따라 쿼리에서 호출되는 표준 쿼리 연산자를 변경할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-122">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="4f431-123">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="4f431-123">Compile the code</span></span>

- <span data-ttu-id="4f431-124">**콘솔 애플리케이션** 프로젝트를 새로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-124">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="4f431-125">System.Linq.Expressions 네임스페이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4f431-125">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="4f431-126">예제의 코드를 복사 하 여 프로시저에 붙여넣습니다 `Main` `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4f431-126">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f431-127">추가 정보</span><span class="sxs-lookup"><span data-stu-id="4f431-127">See also</span></span>

- [<span data-ttu-id="4f431-128">식 트리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f431-128">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="4f431-129">방법: 식 트리 실행(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f431-129">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
