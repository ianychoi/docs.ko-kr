---
description: '자세한 정보: 재귀 프로시저 (Visual Basic)'
title: 재귀 프로시저
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], that call themselves
- procedures [Visual Basic], recursive
- procedures [Visual Basic], calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
ms.openlocfilehash: 378b279a6664cd494fb2e26ff3276afcea56cc16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466564"
---
# <a name="recursive-procedures-visual-basic"></a><span data-ttu-id="bb341-103">재귀 프로시저(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bb341-103">Recursive Procedures (Visual Basic)</span></span>

<span data-ttu-id="bb341-104">*재귀* 프로시저는 자신을 호출 하는 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-104">A *recursive* procedure is one that calls itself.</span></span> <span data-ttu-id="bb341-105">일반적으로 Visual Basic 코드를 작성 하는 가장 효과적인 방법은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-105">In general, this is not the most effective way to write Visual Basic code.</span></span>  
  
 <span data-ttu-id="bb341-106">다음 절차에서는 재귀를 사용 하 여 원래 인수의 계승을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-106">The following procedure uses recursion to calculate the factorial of its original argument.</span></span>  
  
 [!code-vb[VbVbcnProcedures#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#51)]  
  
## <a name="considerations-with-recursive-procedures"></a><span data-ttu-id="bb341-107">재귀 프로시저에 대 한 고려 사항</span><span class="sxs-lookup"><span data-stu-id="bb341-107">Considerations with Recursive Procedures</span></span>

 <span data-ttu-id="bb341-108">**제한 조건**.</span><span class="sxs-lookup"><span data-stu-id="bb341-108">**Limiting Conditions**.</span></span> <span data-ttu-id="bb341-109">재귀를 종료할 수 있는 조건을 하나 이상 테스트 하는 재귀 프로시저를 디자인 해야 하며, 적절 한 수의 재귀 호출 내에서 이러한 조건이 충족 되지 않는 경우도 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-109">You must design a recursive procedure to test for at least one condition that can terminate the recursion, and you must also handle the case where no such condition is satisfied within a reasonable number of recursive calls.</span></span> <span data-ttu-id="bb341-110">실패 없이 충족 될 수 있는 조건이 하나 이상 없으면 프로시저에서 무한 루프에서 실행 될 위험이 높습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-110">Without at least one condition that can be met without fail, your procedure runs a high risk of executing in an infinite loop.</span></span>

 <span data-ttu-id="bb341-111">**메모리 사용**.</span><span class="sxs-lookup"><span data-stu-id="bb341-111">**Memory Usage**.</span></span> <span data-ttu-id="bb341-112">응용 프로그램에는 지역 변수에 대해 제한 된 공간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-112">Your application has a limited amount of space for local variables.</span></span> <span data-ttu-id="bb341-113">프로시저는 자신을 호출할 때마다 해당 지역 변수의 추가 복사본에 대해 더 많은 공간을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-113">Each time a procedure calls itself, it uses more of that space for additional copies of its local variables.</span></span> <span data-ttu-id="bb341-114">이 프로세스가 무기한 지속 되 면 결국 <xref:System.StackOverflowException> 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-114">If this process continues indefinitely, it eventually causes a <xref:System.StackOverflowException> error.</span></span>

 <span data-ttu-id="bb341-115">**효율성**</span><span class="sxs-lookup"><span data-stu-id="bb341-115">**Efficiency**.</span></span> <span data-ttu-id="bb341-116">루프를 거의 항상 재귀로 대체할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-116">You can almost always substitute a loop for recursion.</span></span> <span data-ttu-id="bb341-117">루프는 인수를 전달 하 고, 추가 저장소를 초기화 하 고, 값을 반환 하는 오버 헤드를 갖지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-117">A loop does not have the overhead of passing arguments, initializing additional storage, and returning values.</span></span> <span data-ttu-id="bb341-118">재귀 호출 없이 성능이 훨씬 더 좋을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-118">Your performance can be much better without recursive calls.</span></span>

 <span data-ttu-id="bb341-119">**상호 재귀**.</span><span class="sxs-lookup"><span data-stu-id="bb341-119">**Mutual Recursion**.</span></span> <span data-ttu-id="bb341-120">두 프로시저가 서로를 호출 하는 경우 성능이 저하 되거나 무한 루프가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-120">You might observe very poor performance, or even an infinite loop, if two procedures call each other.</span></span> <span data-ttu-id="bb341-121">이러한 디자인은 단일 재귀 프로시저와 동일한 문제를 표시 하지만 검색 하 고 디버깅 하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-121">Such a design presents the same problems as a single recursive procedure, but can be harder to detect and debug.</span></span>

 <span data-ttu-id="bb341-122">**괄호를 사용 하 여를 호출** 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-122">**Calling with Parentheses**.</span></span> <span data-ttu-id="bb341-123">프로시저 자체를 재귀적으로 호출 하는 경우에는 `Function` 인수 목록이 없는 경우에도 프로시저 이름 뒤에 괄호를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-123">When a `Function` procedure calls itself recursively, you must follow the procedure name with parentheses, even if there is no argument list.</span></span> <span data-ttu-id="bb341-124">그렇지 않으면 함수 이름은 함수의 반환 값을 나타내는 것으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-124">Otherwise, the function name is taken as representing the return value of the function.</span></span>

 <span data-ttu-id="bb341-125">**테스트**.</span><span class="sxs-lookup"><span data-stu-id="bb341-125">**Testing**.</span></span> <span data-ttu-id="bb341-126">재귀 프로시저를 작성 하는 경우이를 신중 하 게 테스트 하 여 항상 제한 조건을 충족 하는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-126">If you write a recursive procedure, you should test it very carefully to make sure it always meets some limiting condition.</span></span> <span data-ttu-id="bb341-127">또한 재귀 호출이 너무 많기 때문에 메모리가 부족 하지 않은지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb341-127">You should also ensure that you cannot run out of memory due to having too many recursive calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="bb341-128">추가 정보</span><span class="sxs-lookup"><span data-stu-id="bb341-128">See also</span></span>

- <xref:System.StackOverflowException>
- [<span data-ttu-id="bb341-129">절차</span><span class="sxs-lookup"><span data-stu-id="bb341-129">Procedures</span></span>](index.md)
- [<span data-ttu-id="bb341-130">하위 프로시저</span><span class="sxs-lookup"><span data-stu-id="bb341-130">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="bb341-131">함수 프로시저</span><span class="sxs-lookup"><span data-stu-id="bb341-131">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="bb341-132">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="bb341-132">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="bb341-133">연산자 프로시저</span><span class="sxs-lookup"><span data-stu-id="bb341-133">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="bb341-134">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="bb341-134">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="bb341-135">프로시저 오버로딩</span><span class="sxs-lookup"><span data-stu-id="bb341-135">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="bb341-136">프로시저 문제 해결</span><span class="sxs-lookup"><span data-stu-id="bb341-136">Troubleshooting Procedures</span></span>](troubleshooting-procedures.md)
- [<span data-ttu-id="bb341-137">루프 구조체</span><span class="sxs-lookup"><span data-stu-id="bb341-137">Loop Structures</span></span>](../control-flow/loop-structures.md)
