---
description: '자세한 정보: 반복기 (Visual Basic)'
title: 반복기
ms.date: 07/20/2015
ms.assetid: f26b5c1e-fe9d-4004-b287-da7919d717ae
ms.openlocfilehash: 9d12bd436a976e3f84dbd063ca746fc7e3b17bfb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462154"
---
# <a name="iterators-visual-basic"></a><span data-ttu-id="26463-103">반복기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26463-103">Iterators (Visual Basic)</span></span>

<span data-ttu-id="26463-104">*반복기* 는 목록 및 배열과 같은 컬렉션을 단계별로 실행하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-104">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="26463-105">반복기 메서드 또는 `get` 접근자는 컬렉션에 대해 사용자 지정 반복을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-105">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="26463-106">반복기 메서드는 [Yield](../../language-reference/statements/yield-statement.md) 문을 사용 하 여 각 요소를 한 번에 하나씩 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-106">An iterator method uses the [Yield](../../language-reference/statements/yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="26463-107">`Yield` 문에 도달하면 코드의 현재 위치가 기억됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-107">When a `Yield` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="26463-108">다음에 반복기 함수가 호출되면 해당 위치에서 실행이 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-108">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="26463-109">For Each ...를 사용 하 여 클라이언트 코드에서 반복기를 사용 합니다. [ 다음](../../language-reference/statements/for-each-next-statement.md) 문 또는 LINQ 쿼리 사용.</span><span class="sxs-lookup"><span data-stu-id="26463-109">You consume an iterator from client code by using a [For Each…Next](../../language-reference/statements/for-each-next-statement.md) statement, or by using a LINQ query.</span></span>

<span data-ttu-id="26463-110">다음 예제에서 `For Each` 루프의 첫 번째 반복은 첫 번째 `Yield` 문에 도달할 때까지 `SomeNumbers` 반복기 메서드에서 실행이 계속되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-110">In the following example, the first iteration of the `For Each` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `Yield` statement is reached.</span></span> <span data-ttu-id="26463-111">이 반복은 3 값을 반환하며 반복기 메서드에서 현재 위치는 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-111">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="26463-112">루프의 다음 반복에서는 반복기 메서드의 실행이 중지되었던 위치에서 계속되고 `Yield` 문에 도달하면 다시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-112">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `Yield` statement.</span></span> <span data-ttu-id="26463-113">이 반복은 값 5를 반환하며 반복기 메서드에서 현재 위치는 다시 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-113">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="26463-114">루프는 반복기 메서드의 끝에 도달하면 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-114">The loop completes when the end of the iterator method is reached.</span></span>

```vb
Sub Main()
    For Each number As Integer In SomeNumbers()
        Console.Write(number & " ")
    Next
    ' Output: 3 5 8
    Console.ReadKey()
End Sub

Private Iterator Function SomeNumbers() As System.Collections.IEnumerable
    Yield 3
    Yield 5
    Yield 8
End Function
```

<span data-ttu-id="26463-115">반복기 메서드 또는 `get` 접근자의 반환 형식은 <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator> 또는 <xref:System.Collections.Generic.IEnumerator%601>일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-115">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="26463-116">`Exit Function`또는 문을 사용 하 여 `Return` 반복을 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-116">You can use an `Exit Function` or `Return` statement to end the iteration.</span></span>

<span data-ttu-id="26463-117">Visual Basic 반복기 함수 또는 `get` 접근자 선언에는 [반복기](../../language-reference/modifiers/iterator.md) 한정자가 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-117">A Visual Basic iterator function or `get` accessor declaration includes an [Iterator](../../language-reference/modifiers/iterator.md) modifier.</span></span>

<span data-ttu-id="26463-118">반복기는 Visual Studio 2012의 Visual Basic에서 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-118">Iterators were introduced in Visual Basic in Visual Studio 2012.</span></span>

<span data-ttu-id="26463-119">**항목 내용**</span><span class="sxs-lookup"><span data-stu-id="26463-119">**In this topic**</span></span>

- [<span data-ttu-id="26463-120">단순 반복기</span><span class="sxs-lookup"><span data-stu-id="26463-120">Simple Iterator</span></span>](#BKMK_SimpleIterator)

- [<span data-ttu-id="26463-121">컬렉션 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="26463-121">Creating a Collection Class</span></span>](#BKMK_CollectionClass)

- [<span data-ttu-id="26463-122">Try 블록</span><span class="sxs-lookup"><span data-stu-id="26463-122">Try Blocks</span></span>](#BKMK_TryBlocks)

- [<span data-ttu-id="26463-123">무명 메서드</span><span class="sxs-lookup"><span data-stu-id="26463-123">Anonymous Methods</span></span>](#BKMK_AnonymousMethods)

- [<span data-ttu-id="26463-124">제네릭 목록과 함께 반복기 사용</span><span class="sxs-lookup"><span data-stu-id="26463-124">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)

- [<span data-ttu-id="26463-125">구문 정보</span><span class="sxs-lookup"><span data-stu-id="26463-125">Syntax Information</span></span>](#BKMK_SyntaxInformation)

- [<span data-ttu-id="26463-126">기술 구현</span><span class="sxs-lookup"><span data-stu-id="26463-126">Technical Implementation</span></span>](#BKMK_Technical)

- [<span data-ttu-id="26463-127">반복기 사용</span><span class="sxs-lookup"><span data-stu-id="26463-127">Use of Iterators</span></span>](#BKMK_UseOfIterators)

> [!NOTE]
> <span data-ttu-id="26463-128">간단한 반복기 예제를 제외한 항목의 모든 예제에 대해서는 및 네임 스페이스에 대 한 [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) 문을 포함 `System.Collections` `System.Collections.Generic` 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-128">For all examples in the topic except the Simple Iterator example, include [Imports](../../language-reference/statements/imports-statement-net-namespace-and-type.md) statements for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><a name="BKMK_SimpleIterator"></a> <span data-ttu-id="26463-129">단순 반복기</span><span class="sxs-lookup"><span data-stu-id="26463-129">Simple Iterator</span></span>

<span data-ttu-id="26463-130">다음 예제에는 `Yield` [에 대 한 단일 문이 있습니다 ... Next](../../language-reference/statements/for-next-statement.md) 루프.</span><span class="sxs-lookup"><span data-stu-id="26463-130">The following example has a single `Yield` statement that is inside a [For…Next](../../language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="26463-131">`Main`에서 `For Each` 문 본문을 반복할 때마다 다음 `Yield` 문으로 진행하는 반복기 함수에 대한 호출이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-131">In `Main`, each iteration of the `For Each` statement body creates a call to the iterator function, which proceeds to the next `Yield` statement.</span></span>

```vb
Sub Main()
    For Each number As Integer In EvenSequence(5, 18)
        Console.Write(number & " ")
    Next
    ' Output: 6 8 10 12 14 16 18
    Console.ReadKey()
End Sub

Private Iterator Function EvenSequence(
ByVal firstNumber As Integer, ByVal lastNumber As Integer) _
As System.Collections.Generic.IEnumerable(Of Integer)

    ' Yield even numbers in the range.
    For number As Integer = firstNumber To lastNumber
        If number Mod 2 = 0 Then
            Yield number
        End If
    Next
End Function
```

## <a name="creating-a-collection-class"></a><a name="BKMK_CollectionClass"></a> <span data-ttu-id="26463-132">컬렉션 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="26463-132">Creating a Collection Class</span></span>

<span data-ttu-id="26463-133">다음 예제에서 `DaysOfTheWeek` 클래스는 <xref:System.Collections.IEnumerable> 인터페이스를 구현하며, <xref:System.Collections.IEnumerable.GetEnumerator%2A> 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-133">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="26463-134">컴파일러는 `GetEnumerator` 메서드를 암시적으로 호출하며, <xref:System.Collections.IEnumerator>가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-134">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="26463-135">`GetEnumerator`메서드는 문을 사용 하 여 각 문자열을 한 번에 하나씩 반환 `Yield` 하 고, `Iterator` 한정자는 함수 선언에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-135">The `GetEnumerator` method returns each string one at a time by using the `Yield` statement, and  an `Iterator` modifier is in the function declaration.</span></span>

```vb
Sub Main()
    Dim days As New DaysOfTheWeek()
    For Each day As String In days
        Console.Write(day & " ")
    Next
    ' Output: Sun Mon Tue Wed Thu Fri Sat
    Console.ReadKey()
End Sub

Private Class DaysOfTheWeek
    Implements IEnumerable

    Public days =
        New String() {"Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat"}

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        ' Yield each day of the week.
        For i As Integer = 0 To days.Length - 1
            Yield days(i)
        Next
    End Function
End Class
```

<span data-ttu-id="26463-136">다음 예제에서는 동물 컬렉션을 포함하는 `Zoo` 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="26463-136">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="26463-137">클래스 인스턴스(`theZoo`)를 참조하는 `For Each` 문은 `GetEnumerator` 메서드를 암시적으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-137">The `For Each` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="26463-138">`Birds` 및 `Mammals` 속성을 참조하는 `For Each` 문은 `AnimalsForType` 명명된 반복기 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-138">The `For Each` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

```vb
Sub Main()
    Dim theZoo As New Zoo()

    theZoo.AddMammal("Whale")
    theZoo.AddMammal("Rhinoceros")
    theZoo.AddBird("Penguin")
    theZoo.AddBird("Warbler")

    For Each name As String In theZoo
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros Penguin Warbler

    For Each name As String In theZoo.Birds
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Penguin Warbler

    For Each name As String In theZoo.Mammals
        Console.Write(name & " ")
    Next
    Console.WriteLine()
    ' Output: Whale Rhinoceros

    Console.ReadKey()
End Sub

Public Class Zoo
    Implements IEnumerable

    ' Private members.
    Private animals As New List(Of Animal)

    ' Public methods.
    Public Sub AddMammal(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Mammal})
    End Sub

    Public Sub AddBird(ByVal name As String)
        animals.Add(New Animal With {.Name = name, .Type = Animal.TypeEnum.Bird})
    End Sub

    Public Iterator Function GetEnumerator() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        For Each theAnimal As Animal In animals
            Yield theAnimal.Name
        Next
    End Function

    ' Public members.
    Public ReadOnly Property Mammals As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Mammal)
        End Get
    End Property

    Public ReadOnly Property Birds As IEnumerable
        Get
            Return AnimalsForType(Animal.TypeEnum.Bird)
        End Get
    End Property

    ' Private methods.
    Private Iterator Function AnimalsForType( _
    ByVal type As Animal.TypeEnum) As IEnumerable
        For Each theAnimal As Animal In animals
            If (theAnimal.Type = type) Then
                Yield theAnimal.Name
            End If
        Next
    End Function

    ' Private class.
    Private Class Animal
        Public Enum TypeEnum
            Bird
            Mammal
        End Enum

        Public Property Name As String
        Public Property Type As TypeEnum
    End Class
End Class
```

## <a name="try-blocks"></a><a name="BKMK_TryBlocks"></a> <span data-ttu-id="26463-139">Try 블록</span><span class="sxs-lookup"><span data-stu-id="26463-139">Try Blocks</span></span>

<span data-ttu-id="26463-140">`Yield`Try 블록에 문을 사용할 수 있는 Visual Basic. `Try` [ Catch ... Finally 문](../../language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="26463-140">Visual Basic allows a `Yield` statement in the `Try` block of a [Try...Catch...Finally Statement](../../language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="26463-141">`Try`문이 있는 블록은 블록 `Yield` 을 포함할 수 있으며 블록을 `Catch` 포함할 수 있습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="26463-141">A `Try` block that has a `Yield` statement can have `Catch` blocks, and can have a `Finally` block.</span></span>

<span data-ttu-id="26463-142">다음 예제에서는 `Try` `Catch` 반복기 함수에, 및 블록을 포함 합니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="26463-142">The following example includes `Try`, `Catch`, and `Finally` blocks in an iterator function.</span></span> <span data-ttu-id="26463-143">`Finally`반복기 함수의 블록은 반복이 완료 되기 전에 실행 `For Each` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-143">The `Finally` block in the iterator function executes before the `For Each` iteration finishes.</span></span>

```vb
Sub Main()
    For Each number As Integer In Test()
        Console.WriteLine(number)
    Next
    Console.WriteLine("For Each is done.")

    ' Output:
    '  3
    '  4
    '  Something happened. Yields are done.
    '  Finally is called.
    '  For Each is done.
    Console.ReadKey()
End Sub

Private Iterator Function Test() As IEnumerable(Of Integer)
    Try
        Yield 3
        Yield 4
        Throw New Exception("Something happened. Yields are done.")
        Yield 5
        Yield 6
    Catch ex As Exception
        Console.WriteLine(ex.Message)
    Finally
        Console.WriteLine("Finally is called.")
    End Try
End Function
```

<span data-ttu-id="26463-144">`Yield`문은 `Catch` 블록이 나 블록 안에 있을 수 없습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="26463-144">A `Yield` statement cannot be inside a `Catch` block or a `Finally` block.</span></span>

<span data-ttu-id="26463-145">`For Each`반복기 메서드 대신 본문이 예외를 throw 하는 경우 `Catch` 에는 반복기 함수의 블록이 실행 되지 않지만 `Finally` 반복기 함수의 블록이 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-145">If the `For Each` body (instead of the iterator method) throws an exception, a `Catch` block in the iterator function is not executed, but a `Finally` block in the iterator function is executed.</span></span> <span data-ttu-id="26463-146">`Catch`반복기 함수 내의 블록은 반복기 함수 내에서 발생 하는 예외만 catch 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-146">A `Catch` block inside an iterator function catches only exceptions that occur inside the iterator function.</span></span>

## <a name="anonymous-methods"></a><a name="BKMK_AnonymousMethods"></a> <span data-ttu-id="26463-147">무명 메서드</span><span class="sxs-lookup"><span data-stu-id="26463-147">Anonymous Methods</span></span>

<span data-ttu-id="26463-148">Visual Basic에서 익명 함수는 반복기 함수 일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-148">In Visual Basic, an anonymous function can be an iterator function.</span></span> <span data-ttu-id="26463-149">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="26463-149">The following example illustrates this.</span></span>

```vb
Dim iterateSequence = Iterator Function() _
                      As IEnumerable(Of Integer)
                          Yield 1
                          Yield 2
                      End Function

For Each number As Integer In iterateSequence()
    Console.Write(number & " ")
Next
' Output: 1 2
Console.ReadKey()
```

<span data-ttu-id="26463-150">다음 예제에는 인수의 유효성을 검사 하는 비 반복기 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-150">The following example has a non-iterator method that validates the arguments.</span></span> <span data-ttu-id="26463-151">메서드는 컬렉션 요소를 설명 하는 익명 반복기의 결과를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-151">The method returns the result of an anonymous iterator that describes the collection elements.</span></span>

```vb
Sub Main()
    For Each number As Integer In GetSequence(5, 10)
        Console.Write(number & " ")
    Next
    ' Output: 5 6 7 8 9 10
    Console.ReadKey()
End Sub

Public Function GetSequence(ByVal low As Integer, ByVal high As Integer) _
As IEnumerable
    ' Validate the arguments.
    If low < 1 Then
        Throw New ArgumentException("low is too low")
    End If
    If high > 140 Then
        Throw New ArgumentException("high is too high")
    End If

    ' Return an anonymous iterator function.
    Dim iterateSequence = Iterator Function() As IEnumerable
                              For index = low To high
                                  Yield index
                              Next
                          End Function
    Return iterateSequence()
End Function
```

<span data-ttu-id="26463-152">유효성 검사가 반복기 함수 내에 있는 경우 본문의 첫 번째 반복이 시작 될 때까지 유효성 검사를 수행할 수 없습니다 `For Each` .</span><span class="sxs-lookup"><span data-stu-id="26463-152">If validation is instead inside the iterator function, the validation cannot be performed until the start of the first iteration of the `For Each` body.</span></span>

## <a name="using-iterators-with-a-generic-list"></a><a name="BKMK_GenericList"></a> <span data-ttu-id="26463-153">제네릭 목록과 함께 반복기 사용</span><span class="sxs-lookup"><span data-stu-id="26463-153">Using Iterators with a Generic List</span></span>

<span data-ttu-id="26463-154">다음 예제에서 `Stack(Of T)` 제네릭 클래스는 <xref:System.Collections.Generic.IEnumerable%601> 제네릭 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-154">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="26463-155">`Push` 메서드는 `T` 형식의 배열에 값을 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-155">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="26463-156"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 메서드는 `Yield` 문을 사용하여 배열 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-156">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `Yield` statement.</span></span>

<span data-ttu-id="26463-157">제네릭 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 메서드뿐 아니라 제네릭이 아닌 <xref:System.Collections.IEnumerable.GetEnumerator%2A> 메서드도 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-157">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="26463-158"><xref:System.Collections.Generic.IEnumerable%601>이 <xref:System.Collections.IEnumerable>에서 상속하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="26463-158">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="26463-159">제네릭이 아닌 구현은 제네릭 구현을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="26463-159">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="26463-160">예제에서는 명명된 반복기를 사용하여 동일한 데이터 컬렉션을 반복하는 다양한 방법을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-160">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="26463-161">이러한 명명된 반복기는 `TopToBottom` 및 `BottomToTop` 속성과 `TopN` 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="26463-161">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="26463-162">`BottomToTop`속성 선언에는 키워드가 포함 됩니다 `Iterator` .</span><span class="sxs-lookup"><span data-stu-id="26463-162">The `BottomToTop` property declaration includes the `Iterator` keyword.</span></span>

```vb
Sub Main()
    Dim theStack As New Stack(Of Integer)

    ' Add items to the stack.
    For number As Integer = 0 To 9
        theStack.Push(number)
    Next

    ' Retrieve items from the stack.
    ' For Each is allowed because theStack implements
    ' IEnumerable(Of Integer).
    For Each number As Integer In theStack
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    ' For Each is allowed, because theStack.TopToBottom
    ' returns IEnumerable(Of Integer).
    For Each number As Integer In theStack.TopToBottom
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3 2 1 0

    For Each number As Integer In theStack.BottomToTop
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 0 1 2 3 4 5 6 7 8 9

    For Each number As Integer In theStack.TopN(7)
        Console.Write("{0} ", number)
    Next
    Console.WriteLine()
    ' Output: 9 8 7 6 5 4 3

    Console.ReadKey()
End Sub

Public Class Stack(Of T)
    Implements IEnumerable(Of T)

    Private values As T() = New T(99) {}
    Private top As Integer = 0

    Public Sub Push(ByVal t As T)
        values(top) = t
        top = top + 1
    End Sub

    Public Function Pop() As T
        top = top - 1
        Return values(top)
    End Function

    ' This function implements the GetEnumerator method. It allows
    ' an instance of the class to be used in a For Each statement.
    Public Iterator Function GetEnumerator() As IEnumerator(Of T) _
        Implements IEnumerable(Of T).GetEnumerator

        For index As Integer = top - 1 To 0 Step -1
            Yield values(index)
        Next
    End Function

    Public Iterator Function GetEnumerator1() As IEnumerator _
        Implements IEnumerable.GetEnumerator

        Yield GetEnumerator()
    End Function

    Public ReadOnly Property TopToBottom() As IEnumerable(Of T)
        Get
            Return Me
        End Get
    End Property

    Public ReadOnly Iterator Property BottomToTop As IEnumerable(Of T)
        Get
            For index As Integer = 0 To top - 1
                Yield values(index)
            Next
        End Get
    End Property

    Public Iterator Function TopN(ByVal itemsFromTop As Integer) _
        As IEnumerable(Of T)

        ' Return less than itemsFromTop if necessary.
        Dim startIndex As Integer =
            If(itemsFromTop >= top, 0, top - itemsFromTop)

        For index As Integer = top - 1 To startIndex Step -1
            Yield values(index)
        Next
    End Function
End Class
```

## <a name="syntax-information"></a><a name="BKMK_SyntaxInformation"></a> <span data-ttu-id="26463-163">구문 정보</span><span class="sxs-lookup"><span data-stu-id="26463-163">Syntax Information</span></span>

<span data-ttu-id="26463-164">반복기는 메서드 또는 `get` 접근자로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-164">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="26463-165">반복기는 이벤트, 인스턴스 생성자, 정적 생성자 또는 정적 소멸자에서 발생할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-165">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>

<span data-ttu-id="26463-166">`Yield` 문의 식 형식에서 반복기의 반환 형식으로 암시적 변환이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-166">An implicit conversion must exist from the expression type in the `Yield` statement to the return type of the iterator.</span></span>

<span data-ttu-id="26463-167">Visual Basic 반복기 메서드에는 매개 변수를 사용할 수 없습니다 `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="26463-167">In Visual Basic, an iterator method cannot have any `ByRef` parameters.</span></span>

<span data-ttu-id="26463-168">Visual Basic에서 "Yield"는 예약 된 단어가 아니므로 메서드나 접근자에서 사용 되는 경우에만 특별 한 의미가 있습니다 `Iterator` `get` .</span><span class="sxs-lookup"><span data-stu-id="26463-168">In Visual Basic, "Yield" is not a reserved word and has special meaning only when it is used in an `Iterator` method or `get` accessor.</span></span>

## <a name="technical-implementation"></a><a name="BKMK_Technical"></a> <span data-ttu-id="26463-169">기술 구현</span><span class="sxs-lookup"><span data-stu-id="26463-169">Technical Implementation</span></span>

<span data-ttu-id="26463-170">반복기를 메서드로 작성하는 경우에도 컴파일러는 실제로 상태 시스템인 중첩 클래스로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-170">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="26463-171">이 클래스는 클라이언트 코드의 `For Each...Next` 루프가 계속되는 한 반복기의 위치를 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-171">This class keeps track of the position of the iterator as long the `For Each...Next` loop in the client code continues.</span></span>

<span data-ttu-id="26463-172">컴파일러의 용도를 확인하려면 Ildasm.exe 도구를 사용하여 반복기 메서드에 대해 생성되는 Microsoft Intermediate Language 코드를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-172">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>

<span data-ttu-id="26463-173">[클래스](../../language-reference/statements/class-statement.md) 또는 [구조체](../../language-reference/statements/structure-statement.md)에 대 한 반복기를 만들 때 전체 인터페이스를 구현할 필요가 없습니다 <xref:System.Collections.IEnumerator> .</span><span class="sxs-lookup"><span data-stu-id="26463-173">When you create an iterator for a [class](../../language-reference/statements/class-statement.md) or [struct](../../language-reference/statements/structure-statement.md), you do not have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="26463-174">컴파일러는 반복기를 검색할 경우 <xref:System.Collections.IEnumerator> 또는 <xref:System.Collections.Generic.IEnumerator%601> 인터페이스의 `Current`, `MoveNext` 및 `Dispose` 메서드를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-174">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="26463-175">`For Each…Next` 루프를 연속 반복하거나 `IEnumerator.MoveNext`를 직접 호출하면 다음 반복기 코드 본문이 이전 `Yield` 문 다음에 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="26463-175">On each successive iteration of the `For Each…Next` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `Yield` statement.</span></span> <span data-ttu-id="26463-176">그런 다음 `Yield` 반복기 본문의 끝에 도달 하거나 `Exit Function` 또는 문이 발생할 때까지 다음 문으로 계속 합니다 `Return` .</span><span class="sxs-lookup"><span data-stu-id="26463-176">It then continues to the next `Yield` statement until the end of the iterator body is reached, or until an `Exit Function` or `Return` statement is encountered.</span></span>

<span data-ttu-id="26463-177">반복기는 메서드를 지원 하지 않습니다 <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="26463-177">Iterators do not support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="26463-178">처음부터 다시 반복하려면 새 반복기를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-178">To re-iterate from the start, you must obtain a new iterator.</span></span>

<span data-ttu-id="26463-179">자세한 내용은 [Visual Basic 언어 사양](../../reference/language-specification/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="26463-179">For additional information, see the [Visual Basic Language Specification](../../reference/language-specification/index.md).</span></span>

## <a name="use-of-iterators"></a><a name="BKMK_UseOfIterators"></a> <span data-ttu-id="26463-180">반복기 사용</span><span class="sxs-lookup"><span data-stu-id="26463-180">Use of Iterators</span></span>

<span data-ttu-id="26463-181">반복기를 사용하면 복잡한 코드를 사용하여 목록 시퀀스를 채워야 하는 경우 `For Each` 루프의 단순성을 유지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-181">Iterators enable you to maintain the simplicity of a `For Each` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="26463-182">이 기능은 다음을 수행하려는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-182">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="26463-183">첫 번째 `For Each` 루프 반복 후 목록 시퀀스를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-183">Modify the list sequence after the first `For Each` loop iteration.</span></span>

- <span data-ttu-id="26463-184">첫 번째 `For Each` 루프 반복 전에 큰 목록이 완전히 로드되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-184">Avoid fully loading a large list before the first iteration of a `For Each` loop.</span></span> <span data-ttu-id="26463-185">한 가지 예로 테이블 행을 일괄 로드하는 페이징 페치가 있으며,</span><span class="sxs-lookup"><span data-stu-id="26463-185">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="26463-186">또 다른 예로 .NET Framework 내에서 반복기를 구현하는 <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-186">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="26463-187">반복기에서 목록 작성을 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="26463-187">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="26463-188">반복기 메서드에서 목록을 빌드한 후 루프에서 각 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26463-188">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="26463-189">참조</span><span class="sxs-lookup"><span data-stu-id="26463-189">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="26463-190">For Each...Next 문</span><span class="sxs-lookup"><span data-stu-id="26463-190">For Each...Next Statement</span></span>](../../language-reference/statements/for-each-next-statement.md)
- [<span data-ttu-id="26463-191">Yield 문</span><span class="sxs-lookup"><span data-stu-id="26463-191">Yield Statement</span></span>](../../language-reference/statements/yield-statement.md)
- [<span data-ttu-id="26463-192">Iterator</span><span class="sxs-lookup"><span data-stu-id="26463-192">Iterator</span></span>](../../language-reference/modifiers/iterator.md)
