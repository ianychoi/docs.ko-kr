---
description: '자세한 정보: 방법: 식 트리 실행 (Visual Basic)'
title: '방법: 식 트리 실행'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: debd850f35d8239c20d9b848a43dafd76ac19bbc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430705"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="48a63-103">방법: 식 트리 실행(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a63-103">How to: Execute Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="48a63-104">이 항목에서는 식 트리를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="48a63-105">식 트리를 실행할 때 값이 반환될 수 있거나, 메서드 호출 등의 작업만 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="48a63-106">람다 식을 나타내는 식 트리만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="48a63-107">람다 식을 나타내는 식 트리는 <xref:System.Linq.Expressions.LambdaExpression> 또는 <xref:System.Linq.Expressions.Expression%601> 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="48a63-108">이러한 식 트리를 실행하려면 <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> 메서드를 호출하여 실행 가능한 대리자를 만든 후 대리자를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="48a63-109">대리자의 형식을 알 수 없는 경우, 즉 람다 식이 <xref:System.Linq.Expressions.Expression%601> 형식이 아니라 <xref:System.Linq.Expressions.LambdaExpression> 형식인 경우 대리자를 직접 호출하는 대신 대리자의 <xref:System.Delegate.DynamicInvoke%2A> 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="48a63-110">식 트리가 람다 식을 나타내지 않는 경우 <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> 메서드를 호출하여 원래 식 트리가 본문으로 포함된 새 람다 식을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="48a63-111">그런 다음 이 섹션의 앞부분에서 설명한 대로 람다 식을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48a63-112">예제</span><span class="sxs-lookup"><span data-stu-id="48a63-112">Example</span></span>  

 <span data-ttu-id="48a63-113">다음 코드 예제에서는 람다 식을 만들고 실행하여 숫자의 거듭제곱을 나타내는 식 트리를 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="48a63-114">숫자의 거듭제곱을 나타내는 결과가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="48a63-115">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="48a63-115">Compile the code</span></span>  
  
- <span data-ttu-id="48a63-116">System.Linq.Expressions 네임스페이스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="48a63-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a63-117">참조</span><span class="sxs-lookup"><span data-stu-id="48a63-117">See also</span></span>

- [<span data-ttu-id="48a63-118">식 트리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a63-118">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="48a63-119">방법: 식 트리 수정(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48a63-119">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
