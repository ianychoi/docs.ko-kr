---
description: '자세한 정보: 연산자의 효율적인 조합 (Visual Basic)'
title: 연산자의 효율적 결합
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: a4d2d0c1caeea95dd8d34b2033a398d26bcf63ef
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476269"
---
# <a name="efficient-combination-of-operators-visual-basic"></a><span data-ttu-id="9f5f6-103">연산자의 효율적 결합(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f5f6-103">Efficient Combination of Operators (Visual Basic)</span></span>

<span data-ttu-id="9f5f6-104">복잡 한 식에는 여러 연산자가 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-104">Complex expressions can contain many different operators.</span></span> <span data-ttu-id="9f5f6-105">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-105">The following example illustrates this.</span></span>  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 <span data-ttu-id="9f5f6-106">위의 예에 나와 있는 것과 같은 복잡 한 식을 만들려면 연산자 우선 순위 규칙을 철저 하 게 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-106">Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence.</span></span> <span data-ttu-id="9f5f6-107">자세한 내용은 [Visual Basic 연산자 우선 순위](../../../language-reference/operators/operator-precedence.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-107">For more information, see [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="9f5f6-108">괄호 식</span><span class="sxs-lookup"><span data-stu-id="9f5f6-108">Parenthetical Expressions</span></span>  

 <span data-ttu-id="9f5f6-109">연산자 우선 순위에 따라 결정 되는 것과 다른 순서로 작업을 진행 하려는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-109">Often you want operations to proceed in a different order from that determined by operator precedence.</span></span> <span data-ttu-id="9f5f6-110">다음 예제를 살펴보십시오.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-110">Consider the following example.</span></span>  
  
 `x = z * y + 4`  
  
 <span data-ttu-id="9f5f6-111">앞의 예제에서는를에 곱한 `z` `y` 다음 결과를에 추가 `4` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-111">The preceding example multiplies `z` by `y`, then adds the result to `4`.</span></span> <span data-ttu-id="9f5f6-112">그러나 결과를에 곱하여를 추가 하려면 `y` `4` 괄호를 사용 하 `z` 여 일반적인 연산자 우선 순위를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-112">But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses.</span></span> <span data-ttu-id="9f5f6-113">식을 괄호로 묶으면 연산자 우선 순위에 관계 없이 식이 먼저 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-113">By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence.</span></span> <span data-ttu-id="9f5f6-114">앞의 예제에서 더하기를 먼저 수행 하도록 하려면 다음 예제와 같이 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-114">To force the preceding example to do the addition first, you could rewrite it as in the following example.</span></span>  
  
 `x = z * (y + 4)`  
  
 <span data-ttu-id="9f5f6-115">앞의 예제에서는 `y` 및 `4` 를 추가한 다음이 합계를에 곱합니다 `z` .</span><span class="sxs-lookup"><span data-stu-id="9f5f6-115">The preceding example adds `y` and `4`, then multiplies that sum by `z`.</span></span>  
  
### <a name="nested-parenthetical-expressions"></a><span data-ttu-id="9f5f6-116">중첩 된 괄호 식</span><span class="sxs-lookup"><span data-stu-id="9f5f6-116">Nested Parenthetical Expressions</span></span>  

 <span data-ttu-id="9f5f6-117">여러 수준의 괄호에 식을 중첩 하 여 우선 순위를 추가로 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-117">You can nest expressions in multiple levels of parentheses to override precedence even further.</span></span> <span data-ttu-id="9f5f6-118">괄호 안의 가장 안쪽에 중첩 된 식은 먼저 계산 된 다음 가장 안쪽에 중첩 된 다음으로 가장 많이 중첩 된 식과 괄호 외부에 있는 식의 순서로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-118">The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses.</span></span> <span data-ttu-id="9f5f6-119">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-119">The following example illustrates this.</span></span>  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 <span data-ttu-id="9f5f6-120">앞의 예제에서 `z + 2` 는 먼저 계산 된 다음 다른 괄호 식이 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-120">In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions.</span></span> <span data-ttu-id="9f5f6-121">더하기 또는 곱하기 보다 우선 순위가 높은 지 수는 다른 식이 괄호로 묶여 있기 때문에이 예제에서는 마지막으로 계산 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9f5f6-121">Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f5f6-122">추가 정보</span><span class="sxs-lookup"><span data-stu-id="9f5f6-122">See also</span></span>

- [<span data-ttu-id="9f5f6-123">Visual Basic의 산술 연산자</span><span class="sxs-lookup"><span data-stu-id="9f5f6-123">Arithmetic Operators in Visual Basic</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="9f5f6-124">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f5f6-124">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="9f5f6-125">Visual Basic의 논리 및 비트 연산자</span><span class="sxs-lookup"><span data-stu-id="9f5f6-125">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="9f5f6-126">논리/비트 연산자(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9f5f6-126">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9f5f6-127">부울 식</span><span class="sxs-lookup"><span data-stu-id="9f5f6-127">Boolean Expressions</span></span>](boolean-expressions.md)
- [<span data-ttu-id="9f5f6-128">값 비교</span><span class="sxs-lookup"><span data-stu-id="9f5f6-128">Value Comparisons</span></span>](value-comparisons.md)
- [<span data-ttu-id="9f5f6-129">방법: 숫자 값 계산</span><span class="sxs-lookup"><span data-stu-id="9f5f6-129">How to: Calculate Numeric Values</span></span>](how-to-calculate-numeric-values.md)
- [<span data-ttu-id="9f5f6-130">Visual Basic에서의 연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="9f5f6-130">Operator Precedence in Visual Basic</span></span>](../../../language-reference/operators/operator-precedence.md)
