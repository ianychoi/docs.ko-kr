---
description: '자세한 정보: 표준 쿼리 연산자 개요 (Visual Basic)'
title: 표준 쿼리 연산자 개요
ms.date: 07/20/2015
ms.assetid: 302bd39e-2ec1-495b-94bf-37d370d6f05f
ms.openlocfilehash: febf0fa85c020504858587bdb080c1bd6725158e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434903"
---
# <a name="standard-query-operators-overview-visual-basic"></a><span data-ttu-id="0d30b-103">표준 쿼리 연산자 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-103">Standard Query Operators Overview (Visual Basic)</span></span>

<span data-ttu-id="0d30b-104">*표준 쿼리 연산자* 는 LINQ 패턴을 형성하는 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-104">The *standard query operators* are the methods that form the LINQ pattern.</span></span> <span data-ttu-id="0d30b-105">이 메서드 중 대부분은 시퀀스에서 작동합니다. 여기서 시퀀스란 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스 또는 <xref:System.Linq.IQueryable%601> 인터페이스를 구현하는 형식의 개체를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-105">Most of these methods operate on sequences, where a sequence is an object whose type implements the <xref:System.Collections.Generic.IEnumerable%601> interface or the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="0d30b-106">표준 쿼리 연산자는 필터링, 프로젝션, 집계, 정렬 등을 포함하여 다양한 쿼리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-106">The standard query operators provide query capabilities including filtering, projection, aggregation, sorting and more.</span></span>

<span data-ttu-id="0d30b-107"><xref:System.Collections.Generic.IEnumerable%601> 형식의 개체와 작동하는 연산자와 <xref:System.Linq.IQueryable%601> 형식의 개체와 작동하는 연산자로 두 가지 LINQ 표준 쿼리 연산자 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-107">There are two sets of LINQ standard query operators, one that operates on objects of type <xref:System.Collections.Generic.IEnumerable%601> and the other that operates on objects of type <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0d30b-108">각 집합을 구성하는 메서드는 각각 <xref:System.Linq.Enumerable> 및 <xref:System.Linq.Queryable> 클래스의 정적 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-108">The methods that make up each set are static members of the <xref:System.Linq.Enumerable> and <xref:System.Linq.Queryable> classes, respectively.</span></span> <span data-ttu-id="0d30b-109">작동하는 형식의 *확장 메서드* 로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-109">They are defined as *extension methods* of the type that they operate on.</span></span> <span data-ttu-id="0d30b-110">따라서 정적 메서드 구문 또는 인스턴스 메서드 구문을 사용하여 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-110">This means that they can be called by using either static method syntax or instance method syntax.</span></span>

<span data-ttu-id="0d30b-111">또한 여러 표준 쿼리 연산자 메서드는 <xref:System.Collections.Generic.IEnumerable%601> 또는 <xref:System.Linq.IQueryable%601>을 기반으로 하는 형식이 아닌 다른 형식에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-111">In addition, several standard query operator methods operate on types other than those based on <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="0d30b-112"><xref:System.Linq.Enumerable> 형식은 <xref:System.Collections.IEnumerable> 형식의 개체에서 작동하는 이러한 두 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-112">The <xref:System.Linq.Enumerable> type defines two such methods that both operate on objects of type <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="0d30b-113">두 메서드 <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> 및 <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>을 사용하면 LINQ 패턴에서 매개 변수가 없는 컬렉션이나 제네릭이 아닌 컬렉션을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-113">These methods, <xref:System.Linq.Enumerable.Cast%60%601%28System.Collections.IEnumerable%29> and <xref:System.Linq.Enumerable.OfType%60%601%28System.Collections.IEnumerable%29>, let you enable a non-parameterized, or non-generic, collection to be queried in the LINQ pattern.</span></span> <span data-ttu-id="0d30b-114">이 작업을 위해 강력한 형식의 개체 컬렉션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-114">They do this by creating a strongly typed collection of objects.</span></span> <span data-ttu-id="0d30b-115"><xref:System.Linq.Queryable> 클래스는 <xref:System.Linq.Queryable> 형식의 개체에서 작동하는 두 개의 유사한 메서드 <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> 및 <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-115">The <xref:System.Linq.Queryable> class defines two similar methods, <xref:System.Linq.Queryable.Cast%60%601%28System.Linq.IQueryable%29> and <xref:System.Linq.Queryable.OfType%60%601%28System.Linq.IQueryable%29>, that operate on objects of type <xref:System.Linq.Queryable>.</span></span>

<span data-ttu-id="0d30b-116">표준 쿼리 연산자는 단일 값을 반환하는지 또는 시퀀스를 반환하는지에 따라 실행되는 타이밍이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-116">The standard query operators differ in the timing of their execution, depending on whether they return a singleton value or a sequence of values.</span></span> <span data-ttu-id="0d30b-117">singleton 값(예: <xref:System.Linq.Enumerable.Average%2A> 및 <xref:System.Linq.Enumerable.Sum%2A>)을 반환하는 이러한 메서드는 즉시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-117">Those methods that return a singleton value (for example, <xref:System.Linq.Enumerable.Average%2A> and <xref:System.Linq.Enumerable.Sum%2A>) execute immediately.</span></span> <span data-ttu-id="0d30b-118">시퀀스를 반환하는 메서드는 쿼리 실행을 지연하고 열거 가능한 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-118">Methods that return a sequence defer the query execution and return an enumerable object.</span></span>

<span data-ttu-id="0d30b-119">메모리 내 컬렉션에 대해 작동하는 메서드, 즉 <xref:System.Collections.Generic.IEnumerable%601>을 확장하는 메서드의 경우 반환된 열거 가능한 개체는 메서드에 전달된 인수를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-119">In the case of the methods that operate on in-memory collections, that is, those methods that extend <xref:System.Collections.Generic.IEnumerable%601>, the returned enumerable object captures the arguments that were passed to the method.</span></span> <span data-ttu-id="0d30b-120">해당 개체를 열거하는 경우 쿼리 연산자의 논리가 사용되며 쿼리 결과가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-120">When that object is enumerated, the logic of the query operator is employed and the query results are returned.</span></span>

<span data-ttu-id="0d30b-121">반면, <xref:System.Linq.IQueryable%601>을 확장하는 메서드는 쿼리 동작을 구현하지 않고 수행할 쿼리를 나타내는 식 트리를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-121">In contrast, methods that extend <xref:System.Linq.IQueryable%601> do not implement any querying behavior, but build an expression tree that represents the query to be performed.</span></span> <span data-ttu-id="0d30b-122">쿼리 처리는 소스 <xref:System.Linq.IQueryable%601> 개체에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-122">The query processing is handled by the source <xref:System.Linq.IQueryable%601> object.</span></span>

<span data-ttu-id="0d30b-123">쿼리 메서드 호출을 연결하여 임의로 복잡해질 수 있는 한 쿼리로 연결될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-123">Calls to query methods can be chained together in one query, which enables queries to become arbitrarily complex.</span></span>

<span data-ttu-id="0d30b-124">다음 코드 예제에서는 표준 쿼리 연산자를 사용하여 시퀀스에 대한 정보를 가져올 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-124">The following code example demonstrates how the standard query operators can be used to obtain information about a sequence.</span></span>

```vb
Dim sentence = "the quick brown fox jumps over the lazy dog"
' Split the string into individual words to create a collection.
Dim words = sentence.Split(" "c)

Dim query = From word In words
            Group word.ToUpper() By word.Length Into gr = Group
            Order By Length _
            Select Length, GroupedWords = gr

Dim output As New System.Text.StringBuilder
For Each obj In query
    output.AppendLine(String.Format("Words of length {0}:", obj.Length))
    For Each word As String In obj.GroupedWords
        output.AppendLine(word)
    Next
Next

'Display the output
MsgBox(output.ToString())

' This code example produces the following output:
'
' Words of length 3:
' THE
' FOX
' THE
' DOG
' Words of length 4:
' OVER
' LAZY
' Words of length 5:
' QUICK
' BROWN
' JUMPS
```

## <a name="query-expression-syntax"></a><span data-ttu-id="0d30b-125">쿼리 식 구문</span><span class="sxs-lookup"><span data-stu-id="0d30b-125">Query Expression Syntax</span></span>

<span data-ttu-id="0d30b-126">자주 사용되는 표준 쿼리 연산자 중 일부에는 ‘쿼리 식’의 일부로 호출할 수 있는 전용 C# 및 Visual Basic 언어 키워드 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-126">Some of the more frequently used standard query operators have dedicated C# and Visual Basic language keyword syntax that enables them to be called as part of a *query* *expression*.</span></span> <span data-ttu-id="0d30b-127">전용 키워드와 해당 구문을 포함 하는 표준 쿼리 연산자에 대 한 자세한 내용은 [표준 쿼리 연산자의 쿼리 식 구문 (Visual Basic)](query-expression-syntax-for-standard-query-operators.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="0d30b-127">For more information about standard query operators that have dedicated keywords and their corresponding syntaxes, see [Query Expression Syntax for Standard Query Operators (Visual Basic)](query-expression-syntax-for-standard-query-operators.md).</span></span>

## <a name="extending-the-standard-query-operators"></a><span data-ttu-id="0d30b-128">표준 쿼리 연산자 확장</span><span class="sxs-lookup"><span data-stu-id="0d30b-128">Extending the Standard Query Operators</span></span>

<span data-ttu-id="0d30b-129">대상 도메인 또는 기술에 적합한 도메인 특정 메서드를 만들어 표준 쿼리 연산자 집합을 강화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-129">You can augment the set of standard query operators by creating domain-specific methods that are appropriate for your target domain or technology.</span></span> <span data-ttu-id="0d30b-130">또한 원격 평가, 쿼리 변환, 최적화 등의 추가 서비스를 제공하는 고유한 구현으로 표준 쿼리 연산자를 바꿀 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-130">You can also replace the standard query operators with your own implementations that provide additional services such as remote evaluation, query translation, and optimization.</span></span> <span data-ttu-id="0d30b-131">예제는 <xref:System.Linq.Enumerable.AsEnumerable%2A>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0d30b-131">See <xref:System.Linq.Enumerable.AsEnumerable%2A> for an example.</span></span>

## <a name="related-sections"></a><span data-ttu-id="0d30b-132">관련 단원</span><span class="sxs-lookup"><span data-stu-id="0d30b-132">Related Sections</span></span>

<span data-ttu-id="0d30b-133">다음 링크는 기능에 따라 다양한 표준 쿼리 연산자에 대한 추가 정보를 제공하는 항목으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="0d30b-133">The following links take you to topics that provide additional information about the various standard query operators based on functionality.</span></span>

- [<span data-ttu-id="0d30b-134">데이터 정렬</span><span class="sxs-lookup"><span data-stu-id="0d30b-134">Sorting Data</span></span>](sorting-data.md)

- [<span data-ttu-id="0d30b-135">Set 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-135">Set Operations (Visual Basic)</span></span>](set-operations.md)

- [<span data-ttu-id="0d30b-136">데이터 필터링 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-136">Filtering Data (Visual Basic)</span></span>](filtering-data.md)

- [<span data-ttu-id="0d30b-137">수량자 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-137">Quantifier Operations (Visual Basic)</span></span>](quantifier-operations.md)

- [<span data-ttu-id="0d30b-138">프로젝션 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-138">Projection Operations (Visual Basic)</span></span>](projection-operations.md)

- [<span data-ttu-id="0d30b-139">데이터 분할 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-139">Partitioning Data (Visual Basic)</span></span>](partitioning-data.md)

- [<span data-ttu-id="0d30b-140">조인 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-140">Join Operations (Visual Basic)</span></span>](join-operations.md)

- [<span data-ttu-id="0d30b-141">데이터 그룹화 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-141">Grouping Data (Visual Basic)</span></span>](grouping-data.md)

- [<span data-ttu-id="0d30b-142">생성 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-142">Generation Operations (Visual Basic)</span></span>](generation-operations.md)

- [<span data-ttu-id="0d30b-143">같음 연산 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-143">Equality Operations (Visual Basic)</span></span>](equality-operations.md)

- [<span data-ttu-id="0d30b-144">요소 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-144">Element Operations (Visual Basic)</span></span>](element-operations.md)

- [<span data-ttu-id="0d30b-145">데이터 형식 변환 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-145">Converting Data Types (Visual Basic)</span></span>](converting-data-types.md)

- [<span data-ttu-id="0d30b-146">연결 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-146">Concatenation Operations (Visual Basic)</span></span>](concatenation-operations.md)

- [<span data-ttu-id="0d30b-147">집계 작업 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-147">Aggregation Operations (Visual Basic)</span></span>](aggregation-operations.md)

## <a name="see-also"></a><span data-ttu-id="0d30b-148">추가 정보</span><span class="sxs-lookup"><span data-stu-id="0d30b-148">See also</span></span>

- <xref:System.Linq.Enumerable>
- <xref:System.Linq.Queryable>
- [<span data-ttu-id="0d30b-149">LINQ 소개(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-149">Introduction to LINQ (Visual Basic)</span></span>](introduction-to-linq.md)
- [<span data-ttu-id="0d30b-150">표준 쿼리 연산자 (Visual Basic)에 대 한 쿼리 식 구문</span><span class="sxs-lookup"><span data-stu-id="0d30b-150">Query Expression Syntax for Standard Query Operators (Visual Basic)</span></span>](query-expression-syntax-for-standard-query-operators.md)
- [<span data-ttu-id="0d30b-151">실행 방식에 따라 표준 쿼리 연산자 분류 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d30b-151">Classification of Standard Query Operators by Manner of Execution (Visual Basic)</span></span>](classification-of-standard-query-operators-by-manner-of-execution.md)
- [<span data-ttu-id="0d30b-152">확장명 메서드</span><span class="sxs-lookup"><span data-stu-id="0d30b-152">Extension Methods</span></span>](../../language-features/procedures/extension-methods.md)
