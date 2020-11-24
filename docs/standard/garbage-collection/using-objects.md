---
title: IDisposable을 구현하는 개체 사용
description: .NET에서 IDisposable 인터페이스를 구현하는 개체를 사용하는 방법을 알아봅니다. 비관리형 리소스를 사용하는 유형은 IDisposable을 구현하여 리소스 회수를 허용합니다.
ms.date: 05/13/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 50769bdf684f6eb3a51dc2bd00c6a774a02976b7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827453"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="a29f8-104">IDisposable을 구현하는 개체 사용</span><span class="sxs-lookup"><span data-stu-id="a29f8-104">Using objects that implement IDisposable</span></span>

<span data-ttu-id="a29f8-105">공용 언어 런타임의 가비지 수집기는 관리되는 개체에서 사용하는 메모리를 회수하지만, 관리되지 않는 리소스를 사용하는 유형에서는 이러한 관리되지 않는 리소스에 필요한 리소스를 회수할 수 있게 하는 <xref:System.IDisposable> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-105">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="a29f8-106"><xref:System.IDisposable>을 구현하는 개체의 사용을 마치면 해당 개체의 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현을 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-106">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="a29f8-107">이 작업은 다음 두 가지 방법 중 하나로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-107">You can do this in one of two ways:</span></span>

- <span data-ttu-id="a29f8-108">C# `using` 문(Visual Basic의 경우 `Using`)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-108">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="a29f8-109">`try/finally` 블록을 구현하고 `finally`에서 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-109">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="a29f8-110">using 문</span><span class="sxs-lookup"><span data-stu-id="a29f8-110">The using statement</span></span>

<span data-ttu-id="a29f8-111">C#의 [`using` 문](../../csharp/language-reference/keywords/using-statement.md)과 Visual Basic의 [`Using` 문](../../visual-basic/language-reference/statements/using-statement.md)은 개체를 정리하기 위해 작성해야 하는 코드를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-111">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="a29f8-112">`using` 문은 하나 이상의 리소스를 가져와서, 사용자가 지정하는 문을 실행한 다음, 개체를 자동으로 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-112">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="a29f8-113">그러나 `using` 문은 개체가 생성된 메서드의 범위 내에서 사용되는 개체에만 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-113">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="a29f8-114">다음 예제에서는 `using` 문을 사용하여 <xref:System.IO.StreamReader?displayProperty=nameWithType> 개체를 만들고 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-114">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="a29f8-115"><xref:System.IO.StreamReader> 클래스가 <xref:System.IDisposable> 인터페이스를 구현하며, 이는 관리되지 않는 리소스를 사용함을 나타내지만 예제에서는 <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> 메서드를 명시적으로 호출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-115">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a29f8-116">C# 또는 Visual Basic 컴파일러가 `using` 문을 발견하면 `try/finally` 블록을 명시적으로 포함하는 다음 코드와 동일한 중간 언어(IL)를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-116">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="a29f8-117">또한 C# `using` 문을 사용하면 단일 문으로 여러 리소스를 가져올 수 있으며, 이는 중첩된 `using` 문의 기능과 내부적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-117">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="a29f8-118">다음 예제에서는 서로 다른 두 파일의 내용을 읽을 수 있도록 두 개의 <xref:System.IO.StreamReader> 개체를 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-118">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="a29f8-119">Try/finally 블록</span><span class="sxs-lookup"><span data-stu-id="a29f8-119">Try/finally block</span></span>

<span data-ttu-id="a29f8-120">`using` 문에서 `try/finally` 블록을 래핑하는 대신 `try/finally` 블록을 직접 구현하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-120">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="a29f8-121">개인적인 코딩 스타일에 따라서 또는 다음 이유 중 하나로 이를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-121">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="a29f8-122">`catch` 블록에서 throw된 예외를 처리하기 위해 `try` 블록을 포함하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="a29f8-122">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="a29f8-123">그렇지 않으면 `using` 문 내에서 throw되는 모든 예외가 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-123">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="a29f8-124">범위가 선언된 범위 내의 블록에 대해 로컬이 아닌 <xref:System.IDisposable>을 구현하는 개체를 인스턴스화하려는 경우</span><span class="sxs-lookup"><span data-stu-id="a29f8-124">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="a29f8-125">`try/catch/finally` 블록을 사용하여 <xref:System.IO.StreamReader> 개체를 인스턴스화, 사용 및 삭제하고 <xref:System.IO.StreamReader> 생성자 및 해당 <xref:System.IO.StreamReader.ReadToEnd%2A> 메서드에서 throw된 예외를 처리한다는 점을 제외하면 다음 예제는 이전 예제와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-125">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="a29f8-126">`finally` 블록의 코드가 <xref:System.IDisposable> 메서드를 호출하기 전에 `null`을 구현하는 개체가 <xref:System.IDisposable.Dispose%2A>이 아닌지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-126">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="a29f8-127">이렇게 하지 않으면 런타임에 <xref:System.NullReferenceException> 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-127">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="a29f8-128">프로그래밍 언어가 `using` 문을 지원하지 않지만, <xref:System.IDisposable.Dispose%2A> 메서드에 대한 직접 호출을 허용하므로 `try/finally` 블록을 구현하도록 선택하거나 구현해야 하는 경우 이 기본 패턴을 따를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-128">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="a29f8-129">IDisposable 인스턴스 멤버</span><span class="sxs-lookup"><span data-stu-id="a29f8-129">IDisposable instance members</span></span>

<span data-ttu-id="a29f8-130">클래스가 <xref:System.IDisposable> 구현을 인스턴스 멤버(필드 또는 속성)로 포함하는 경우 클래스도 <xref:System.IDisposable>을 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a29f8-130">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="a29f8-131">자세한 내용은 [cascade dispose 구현](implementing-dispose.md#cascade-dispose-calls)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a29f8-131">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="a29f8-132">참조</span><span class="sxs-lookup"><span data-stu-id="a29f8-132">See also</span></span>

- [<span data-ttu-id="a29f8-133">관리되지 않는 리소스 정리</span><span class="sxs-lookup"><span data-stu-id="a29f8-133">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="a29f8-134">using 문(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="a29f8-134">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="a29f8-135">Using 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a29f8-135">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
