---
title: PLINQ 및 TPL의 람다 식
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: 9d884bbcb248effa41b24788d530151783280a53
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817122"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="8e295-102">PLINQ 및 TPL의 람다 식</span><span class="sxs-lookup"><span data-stu-id="8e295-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="8e295-103">TPL(작업 병렬 라이브러리)에는 대리자의 <xref:System.Func%601?displayProperty=nameWithType> 또는 <xref:System.Action?displayProperty=nameWithType> 패밀리 중 하나를 입력 매개 변수로 사용하는 많은 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="8e295-104">이러한 대리자를 사용하여 병렬 루프, 작업 또는 쿼리에 사용자 지정 프로그램 논리를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="8e295-105">TPL 및 PLINQ에 대한 코드 예제는 람다 식을 사용하여 인라인 코드 블록으로 해당 대리자의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="8e295-106">이 항목에서는 Func 및 Action에 대한 간략한 소개를 제공하고 작업 병렬 라이브러리 및 PLINQ에서 람다 식을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="8e295-107">일반적인 대리자에 대한 자세한 내용은 [대리자](../../csharp/programming-guide/delegates/index.md) 및 [대리자](../../visual-basic/programming-guide/language-features/delegates/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e295-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="8e295-108">C# 및 Visual Basic의 람다 식에 대한 자세한 내용은 [람다 식](../../csharp/language-reference/operators/lambda-expressions.md) 및 [람다 식](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8e295-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/language-reference/operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="8e295-109">Func 대리자</span><span class="sxs-lookup"><span data-stu-id="8e295-109">Func Delegate</span></span>

<span data-ttu-id="8e295-110">`Func` 대리자는 값을 반환하는 메서드를 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="8e295-111">`Func` 서명에서 마지막 또는 가장 오른쪽에 있는 형식 매개 변수는 항상 반환 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-111">In a `Func` signature, the last, or rightmost, type parameter always specifies the return type.</span></span> <span data-ttu-id="8e295-112">컴파일러 오류의 일반적인 원인 중 하나는 두 개의 입력 매개 변수를 <xref:System.Func%602?displayProperty=nameWithType>에 전달하려고 하기 때문입니다. 실제로 이 형식은 하나의 입력 매개 변수만 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="8e295-113">.NET은 <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType> 등에서 <xref:System.Func%6017?displayProperty=nameWithType>까지 17개 버전의 `Func`를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-113">.NET defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="8e295-114">Action 대리자</span><span class="sxs-lookup"><span data-stu-id="8e295-114">Action Delegate</span></span>

<span data-ttu-id="8e295-115"><xref:System.Action?displayProperty=nameWithType> 대리자는 값을 반환하지 않는 메서드(Visual Basic의 하위)를 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value.</span></span> <span data-ttu-id="8e295-116">`Action` 형식 서명에서 형식 매개 변수는 입력 매개 변수만을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-116">In an `Action` type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="8e295-117">`Func`와 마찬가지로 .NET은 형식 매개 변수가 없는 버전에서 16개 형식 매개 변수가 있는 버전까지 17개 버전의 `Action`을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-117">Like `Func`, .NET defines 17 versions of `Action`, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="8e295-118">예제</span><span class="sxs-lookup"><span data-stu-id="8e295-118">Example</span></span>

<span data-ttu-id="8e295-119"><xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> 메서드의 다음 예제는 람다 식을 사용하여 Func 및 Action 대리자를 모두 표현하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="8e295-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="8e295-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8e295-120">See also</span></span>

- [<span data-ttu-id="8e295-121">병렬 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="8e295-121">Parallel Programming</span></span>](index.md)
