---
description: try-finally - C# 참조
title: try-finally - C# 참조
ms.date: 07/20/2015
f1_keywords:
- finally
- finally_CSharpKeyword
helpviewer_keywords:
- finally keyword [C#]
- try-finally statement [C#]
ms.assetid: c27623fb-7261-4464-862c-7a369d3c8f0a
ms.openlocfilehash: 03e5fa46cef6b30a0af15c113ec6b141a61bee47
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639418"
---
# <a name="try-finally-c-reference"></a><span data-ttu-id="ceee8-103">try-finally(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="ceee8-103">try-finally (C# Reference)</span></span>

<span data-ttu-id="ceee8-104">`finally` 블록을 사용하면 [try](try-catch.md) 블록에서 할당된 리소스를 정리할 수 있으며, `try` 블록에서 예외가 발생하는 경우에도 코드를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-104">By using a `finally` block, you can clean up any resources that are allocated in a [try](try-catch.md) block, and you can run code even if an exception occurs in the `try` block.</span></span> <span data-ttu-id="ceee8-105">일반적으로 `finally` 블록의 문은 제어가 `try` 문을 벗어날 때 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-105">Typically, the statements of a `finally` block run when control leaves a `try` statement.</span></span> <span data-ttu-id="ceee8-106">제어 전송은 정상적인 실행 결과, `break`, `continue`, `goto` 또는 `return` 문의 실행 결과 또는 `try` 문에서 예외 전파의 결과로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-106">The transfer of control can occur as a result of normal execution, of execution of a `break`, `continue`, `goto`, or `return` statement, or of propagation of an exception out of the `try` statement.</span></span>

<span data-ttu-id="ceee8-107">처리된 예외 내에서는 연결된 `finally` 블록이 항상 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-107">Within a handled exception, the associated `finally` block is guaranteed to be run.</span></span> <span data-ttu-id="ceee8-108">그러나 예외가 처리되지 않은 경우 `finally` 블록의 실행 여부는 예외 해제 작업의 트리거 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-108">However, if the exception is unhandled, execution of the `finally` block is dependent on how the exception unwind operation is triggered.</span></span> <span data-ttu-id="ceee8-109">트리거 방법은 다시 사용자 컴퓨터의 설정 방법에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-109">That, in turn, is dependent on how your computer is set up.</span></span> <span data-ttu-id="ceee8-110">`finally` 절이 실행되지 않는 유일한 경우는 프로그램이 즉시 중지될 때입니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-110">The only cases where `finally` clauses don't run involve a program being immediately stopped.</span></span> <span data-ttu-id="ceee8-111">이러한 예로는 IL 문이 손상되어 <xref:System.InvalidProgramException>이 throw되는 경우를 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-111">An example of this would be when <xref:System.InvalidProgramException> gets thrown because of the IL statements being corrupt.</span></span> <span data-ttu-id="ceee8-112">대부분의 운영 체제에서 적절한 리소스 정리는 프로세스를 중지하고 언로드하는 과정에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-112">On most operating systems, reasonable resource cleanup will take place as part of stopping and unloading the process.</span></span>

<span data-ttu-id="ceee8-113">일반적으로 처리되지 않은 예외로 애플리케이션이 종료되는 경우 `finally` 블록의 실행 여부는 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-113">Usually, when an unhandled exception ends an application, whether or not the `finally` block is run is not important.</span></span> <span data-ttu-id="ceee8-114">그러나 해당 상황에서도 실행해야 하는 문이 `finally` 블록에 있는 경우 한 가지 솔루션은 `catch` 블록을 `try`-`finally` 문에 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-114">However, if you have statements in a `finally` block that must be run even in that situation, one solution is to add a `catch` block to the `try`-`finally` statement.</span></span> <span data-ttu-id="ceee8-115">또는 호출 스택에서 상위 `try`-`finally` 문의 `try` 블록에 throw될 수 있는 예외를 catch할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-115">Alternatively, you can catch the exception that might be thrown in the `try` block of a `try`-`finally` statement higher up the call stack.</span></span> <span data-ttu-id="ceee8-116">즉, `try`-`finally` 문을 포함하는 메서드를 호출하는 메서드, 해당 메서드를 호출하는 메서드 또는 호출 스택의 임의 메서드에 예외를 catch할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-116">That is, you can catch the exception in the method that calls the method that contains the `try`-`finally` statement, or in the method that calls that method, or in any method in the call stack.</span></span> <span data-ttu-id="ceee8-117">예외가 catch되지 않는 경우 `finally`의 실행은 운영 체제에서 예외 해제 작업 트리거를 선택하는지 여부에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-117">If the exception is not caught, execution of the `finally` block depends on whether the operating system chooses to trigger an exception unwind operation.</span></span>

## <a name="example"></a><span data-ttu-id="ceee8-118">예제</span><span class="sxs-lookup"><span data-stu-id="ceee8-118">Example</span></span>

<span data-ttu-id="ceee8-119">다음 예제에서는 잘못된 변환 문으로 인해 `System.InvalidCastException` 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-119">In the following example, an invalid conversion statement causes a `System.InvalidCastException` exception.</span></span> <span data-ttu-id="ceee8-120">예외가 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-120">The exception is unhandled.</span></span>

[!code-csharp[csrefKeywordsExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#4)]

<span data-ttu-id="ceee8-121">다음 예제에서는 `TryCast` 메서드의 예외가 호출 스택의 위에 있는 메서드에서 catch됩니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-121">In the following example, an exception from the `TryCast` method is caught in a method farther up the call stack.</span></span>

[!code-csharp[csrefKeywordsExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#6)]

<span data-ttu-id="ceee8-122">`finally`에 대한 자세한 내용은 [try-catch-finally](try-catch-finally.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceee8-122">For more information about `finally`, see [try-catch-finally](try-catch-finally.md).</span></span>

<span data-ttu-id="ceee8-123">C#에는 <xref:System.IDisposable> 개체에 대한 유사한 기능을 편리한 구문으로 제공하는 [using 문](using-statement.md)도 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ceee8-123">C# also contains the [using statement](using-statement.md), which provides similar functionality for <xref:System.IDisposable> objects in a convenient syntax.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ceee8-124">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="ceee8-124">C# language specification</span></span>

<span data-ttu-id="ceee8-125">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [try 문](~/_csharplang/spec/statements.md#the-try-statement) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ceee8-125">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ceee8-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ceee8-126">See also</span></span>

- [<span data-ttu-id="ceee8-127">C# 참조</span><span class="sxs-lookup"><span data-stu-id="ceee8-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ceee8-128">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="ceee8-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ceee8-129">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="ceee8-129">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ceee8-130">try, throw 및 catch 문(C++)</span><span class="sxs-lookup"><span data-stu-id="ceee8-130">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="ceee8-131">throw</span><span class="sxs-lookup"><span data-stu-id="ceee8-131">throw</span></span>](throw.md)
- [<span data-ttu-id="ceee8-132">try-catch</span><span class="sxs-lookup"><span data-stu-id="ceee8-132">try-catch</span></span>](try-catch.md)
- [<span data-ttu-id="ceee8-133">방법: 명시적으로 예외 Throw</span><span class="sxs-lookup"><span data-stu-id="ceee8-133">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
