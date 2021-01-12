---
description: yield 상황별 키워드 - C# 참조
title: yield 상황별 키워드 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- yield
- yield_CSharpKeyword
helpviewer_keywords:
- yield keyword [C#]
ms.assetid: 1089194f-9e53-46a2-8642-53ccbe9d414d
ms.openlocfilehash: e0efad959d5212f6c07d4c4b5344761490018a4c
ms.sourcegitcommit: 88fbb019b84c2d044d11fb4f6004aec07f2b25b1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97899667"
---
# <a name="yield-c-reference"></a><span data-ttu-id="efb4a-103">yield(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="efb4a-103">yield (C# Reference)</span></span>

<span data-ttu-id="efb4a-104">문에 `yield` [상황별 키워드](index.md#contextual-keywords)를 사용하는 경우 해당 메서드, 연산자 또는 이 키워드가 나타나는 `get` 접근자가 반복기임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-104">When you use the `yield` [contextual keyword](index.md#contextual-keywords) in a statement, you indicate that the method, operator, or `get` accessor in which it appears is an iterator.</span></span> <span data-ttu-id="efb4a-105">`yield`를 사용하여 반복기를 정의할 경우 사용자 지정 컬렉션 형식에 <xref:System.Collections.Generic.IEnumerator%601> 및 <xref:System.Collections.IEnumerable> 패턴을 구현하면 명시적 추가 클래스(열거형의 상태를 보관하는 클래스, 예제는 <xref:System.Collections.IEnumerator> 참조)를 사용하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-105">Using `yield` to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see <xref:System.Collections.Generic.IEnumerator%601> for an example) when you implement the <xref:System.Collections.IEnumerable> and <xref:System.Collections.IEnumerator> pattern for a custom collection type.</span></span>

<span data-ttu-id="efb4a-106">다음 예제에서는 두 가지 형태의 `yield` 문을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-106">The following example shows the two forms of the `yield` statement.</span></span>

```csharp
yield return <expression>;
yield break;
```

## <a name="remarks"></a><span data-ttu-id="efb4a-107">설명</span><span class="sxs-lookup"><span data-stu-id="efb4a-107">Remarks</span></span>

<span data-ttu-id="efb4a-108">`yield return` 문을 사용하여 각 요소를 따로따로 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-108">You use a `yield return` statement to return each element one at a time.</span></span>

<span data-ttu-id="efb4a-109">반복기 메서드에서 반환된 시퀀스는 [foreach](foreach-in.md) 문 또는 LINQ 쿼리를 통해 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-109">The sequence returned from an iterator method can be consumed by using a [foreach](foreach-in.md) statement or LINQ query.</span></span> <span data-ttu-id="efb4a-110">각각의 `foreach` 루프의 반복이 반복기 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-110">Each iteration of the `foreach` loop calls the iterator method.</span></span> <span data-ttu-id="efb4a-111">`yield return` 문이 반복기 메서드에 도달하면 `expression` 이 반환되고 코드에서 현재 위치는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-111">When a `yield return` statement is reached in the iterator method, `expression` is returned, and the current location in code is retained.</span></span> <span data-ttu-id="efb4a-112">다음에 반복기 함수가 호출되면 해당 위치에서 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-112">Execution is restarted from that location the next time that the iterator function is called.</span></span>

<span data-ttu-id="efb4a-113">`yield break` 문을 사용하여 반복기를 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-113">You can use a `yield break` statement to end the iteration.</span></span>

<span data-ttu-id="efb4a-114">반복기에 대한 자세한 내용은 [반복기](../../iterators.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efb4a-114">For more information about iterators, see [Iterators](../../iterators.md).</span></span>

## <a name="iterator-methods-and-get-accessors"></a><span data-ttu-id="efb4a-115">반복기 메서드 및 Get 접근자</span><span class="sxs-lookup"><span data-stu-id="efb4a-115">Iterator methods and get accessors</span></span>

<span data-ttu-id="efb4a-116">반복기 선언은 다음과 같은 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-116">The declaration of an iterator must meet the following requirements:</span></span>

- <span data-ttu-id="efb4a-117">반환 형식은 <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, 또는 <xref:System.Collections.Generic.IEnumerator%601>여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-117">The return type must be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

- <span data-ttu-id="efb4a-118">선언에 [in](in-parameter-modifier.md), [ref](ref.md) 또는 [out](out-parameter-modifier.md) 매개 변수가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-118">The declaration can't have any [in](in-parameter-modifier.md), [ref](ref.md), or [out](out-parameter-modifier.md) parameters.</span></span>

<span data-ttu-id="efb4a-119">`yield` 또는 <xref:System.Collections.IEnumerable>를 반환하는 반복기의 <xref:System.Collections.IEnumerator> 형식은 `object`입니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-119">The `yield` type of an iterator that returns <xref:System.Collections.IEnumerable> or <xref:System.Collections.IEnumerator> is `object`.</span></span>  <span data-ttu-id="efb4a-120">반복기가 <xref:System.Collections.Generic.IEnumerable%601> 또는 <xref:System.Collections.Generic.IEnumerator%601>를 반환할 경우 `yield return` 문의 식 형식에서 제네릭 형식 매개 변수로 암시적 변환이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-120">If the iterator returns <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Collections.Generic.IEnumerator%601>, there must be an implicit conversion from the type of the expression in the `yield return` statement to the generic type parameter .</span></span>

<span data-ttu-id="efb4a-121">`yield return` 또는 `yield break` 식을</span><span class="sxs-lookup"><span data-stu-id="efb4a-121">You can't include a `yield return` or `yield break` statement in:</span></span>

- <span data-ttu-id="efb4a-122">[람다 식](../operators/lambda-expressions.md) 및 [무명 메서드](../operators/delegate-operator.md)에 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-122">[Lambda expressions](../operators/lambda-expressions.md) and [anonymous methods](../operators/delegate-operator.md).</span></span>

- <span data-ttu-id="efb4a-123">안전하지 않은 블록을 포함하는 메서드</span><span class="sxs-lookup"><span data-stu-id="efb4a-123">Methods that contain unsafe blocks.</span></span> <span data-ttu-id="efb4a-124">자세한 내용은 [unsafe](unsafe.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="efb4a-124">For more information, see [unsafe](unsafe.md).</span></span>

## <a name="exception-handling"></a><span data-ttu-id="efb4a-125">예외 처리</span><span class="sxs-lookup"><span data-stu-id="efb4a-125">Exception handling</span></span>

<span data-ttu-id="efb4a-126">`yield return` 문은 try-catch 블록에서 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-126">A `yield return` statement can't be located in a try-catch block.</span></span> <span data-ttu-id="efb4a-127">`yield return` 문은 try-finally 문의 try 블록에서 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-127">A `yield return` statement can be located in the try block of a try-finally statement.</span></span>

<span data-ttu-id="efb4a-128">`yield break` 문은 try 블록이나 catch 블록에서 찾을 수 있지만 finally 블록에서는 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-128">A `yield break` statement can be located in a try block or a catch block but not a finally block.</span></span>

<span data-ttu-id="efb4a-129">`foreach` 본문(반복기 메서드 외부)에서 예외를 throw한 경우, 반복기 메서드의 `finally` 블록이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-129">If the `foreach` body (outside of the iterator method) throws an exception, a `finally` block in the iterator method is executed.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="efb4a-130">기술 구현</span><span class="sxs-lookup"><span data-stu-id="efb4a-130">Technical implementation</span></span>

<span data-ttu-id="efb4a-131">다음 코드는 반복기 메서드에서 `IEnumerable<string>`을 반환하고 해당 요소를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-131">The following code returns an `IEnumerable<string>` from an iterator method and then iterates through its elements.</span></span>

```csharp
IEnumerable<string> elements = MyIteratorMethod();
foreach (string element in elements)
{
   ...
}
```

<span data-ttu-id="efb4a-132">`MyIteratorMethod` 호출은 메서드의 본문을 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-132">The call to `MyIteratorMethod` doesn't execute the body of the method.</span></span> <span data-ttu-id="efb4a-133">대신에 `IEnumerable<string>` 변수에 `elements`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-133">Instead the call returns an `IEnumerable<string>` into the `elements` variable.</span></span>

<span data-ttu-id="efb4a-134">`foreach` 루프 반복에서 <xref:System.Collections.IEnumerator.MoveNext%2A>에 대한 `elements` 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-134">On an iteration of the `foreach` loop, the <xref:System.Collections.IEnumerator.MoveNext%2A> method is called for `elements`.</span></span> <span data-ttu-id="efb4a-135">이 호출은 다음 `MyIteratorMethod` 문에 도달할 때까지 `yield return` 본문을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-135">This call executes the body of `MyIteratorMethod` until the next `yield return` statement is reached.</span></span> <span data-ttu-id="efb4a-136">`yield return` 문에서 반환하는 식은 루프 본문에서 사용하는 `element` 변수 값뿐만 아니라 `IEnumerable<string>`인 `elements`의 <xref:System.Collections.Generic.IEnumerator%601.Current%2A> 속성도 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-136">The expression returned by the `yield return` statement determines not only the value of the `element` variable for consumption by the loop body but also the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property of `elements`, which is an `IEnumerable<string>`.</span></span>

<span data-ttu-id="efb4a-137">이후에 `foreach` 루프가 반복될 때마다 중지되었던 위치에서 반복기 본문 실행이 계속되고 `yield return` 문에 도달하면 다시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-137">On each subsequent iteration of the `foreach` loop, the execution of the iterator body continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="efb4a-138">`foreach` 루프는 반복기 메서드가 종료되거나 `yield break` 문에 도달하면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-138">The `foreach` loop completes when the end of the iterator method or a `yield break` statement is reached.</span></span>

## <a name="example"></a><span data-ttu-id="efb4a-139">예제</span><span class="sxs-lookup"><span data-stu-id="efb4a-139">Example</span></span>

<span data-ttu-id="efb4a-140">다음 예제에는 `yield return` 루프 내에 `for` 문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-140">The following example has a `yield return` statement that's inside a `for` loop.</span></span> <span data-ttu-id="efb4a-141">`Main` 메서드에서 `foreach` 문의 본문을 반복할 때마다 `Power` 반복기 함수에 대한 호출이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-141">Each iteration of the `foreach` statement body in the `Main` method creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="efb4a-142">반복기 함수를 호출할 때마다 다음에 `yield return` 루프를 반복하는 도중에 `for` 문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-142">Each call to the iterator function proceeds to the next execution of the `yield return` statement, which occurs during the next iteration of the `for` loop.</span></span>

<span data-ttu-id="efb4a-143">반복기 메서드의 반환 형식은 반복기 인터페이스 형식인 <xref:System.Collections.IEnumerable>입니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-143">The return type of the iterator method is <xref:System.Collections.IEnumerable>, which is an iterator interface type.</span></span> <span data-ttu-id="efb4a-144">반복기 메서드가 호출되면 숫자의 거듭제곱이 들어 있는 열거형 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-144">When the iterator method is called, it returns an enumerable object that contains the powers of a number.</span></span>

[!code-csharp[csrefKeywordsContextual#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#5)]

## <a name="example"></a><span data-ttu-id="efb4a-145">예제</span><span class="sxs-lookup"><span data-stu-id="efb4a-145">Example</span></span>

<span data-ttu-id="efb4a-146">다음 예제는 반복기인 `get` 접근자에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-146">The following example demonstrates a `get` accessor that is an iterator.</span></span> <span data-ttu-id="efb4a-147">이 예제에서는 각 `yield return` 문이 사용자 정의 클래스의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="efb4a-147">In the example, each `yield return` statement returns an instance of a user-defined class.</span></span>

[!code-csharp[csrefKeywordsContextual#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#21)]

## <a name="c-language-specification"></a><span data-ttu-id="efb4a-148">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="efb4a-148">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="efb4a-149">참조</span><span class="sxs-lookup"><span data-stu-id="efb4a-149">See also</span></span>

- [<span data-ttu-id="efb4a-150">C# 참조</span><span class="sxs-lookup"><span data-stu-id="efb4a-150">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="efb4a-151">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="efb4a-151">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="efb4a-152">foreach, in</span><span class="sxs-lookup"><span data-stu-id="efb4a-152">foreach, in</span></span>](foreach-in.md)
- [<span data-ttu-id="efb4a-153">반복기</span><span class="sxs-lookup"><span data-stu-id="efb4a-153">Iterators</span></span>](../../iterators.md)
