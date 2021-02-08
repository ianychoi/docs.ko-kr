---
description: 다음에 대 한 자세한 정보:-= 연산자 (Visual Basic)
title: -= 연산자
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 55574fa56d0ebe02fa5aef1a2711dfb3e5161a9e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795276"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="44152-103">-= 연산자(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44152-103">-= Operator (Visual Basic)</span></span>

<span data-ttu-id="44152-104">변수 또는 속성 값에서 식의 값을 빼고 결과를 변수 또는 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="44152-104">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44152-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44152-105">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="44152-106">부분</span><span class="sxs-lookup"><span data-stu-id="44152-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="44152-107">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="44152-107">Required.</span></span> <span data-ttu-id="44152-108">임의의 숫자 변수 또는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="44152-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="44152-109">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="44152-109">Required.</span></span> <span data-ttu-id="44152-110">임의의 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="44152-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44152-111">설명</span><span class="sxs-lookup"><span data-stu-id="44152-111">Remarks</span></span>  

 <span data-ttu-id="44152-112">연산자의 좌 변에 있는 요소는 `-=` 간단한 스칼라 변수, 속성 또는 배열의 요소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44152-112">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="44152-113">변수 또는 속성은 [ReadOnly](../modifiers/readonly.md)일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="44152-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="44152-114">연산자는 먼저 연산자의 오른쪽에 있는 `-=` 식의 값을 해당 연산자의 왼쪽에 있는 변수 또는 속성의 값에서 뺍니다.</span><span class="sxs-lookup"><span data-stu-id="44152-114">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="44152-115">그런 다음 연산자는 해당 작업의 결과를 변수나 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="44152-115">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="44152-116">오버로딩</span><span class="sxs-lookup"><span data-stu-id="44152-116">Overloading</span></span>  

 <span data-ttu-id="44152-117">[-연산자 (Visual Basic)](subtraction-operator.md) 를 *오버 로드할* 수 있습니다. 즉, 피연산자가 해당 클래스 또는 구조체의 형식일 때 클래스 또는 구조체에서 해당 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44152-117">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="44152-118">연산자를 오버 로드 하면 `-` 연산자의 동작에 영향을 줍니다 `-=` .</span><span class="sxs-lookup"><span data-stu-id="44152-118">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="44152-119">`-=`오버 로드 하는 클래스 또는 구조체에서 코드를 사용 하는 경우 다시 `-` 정의 된 동작을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="44152-119">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="44152-120">자세한 내용은 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="44152-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44152-121">예제</span><span class="sxs-lookup"><span data-stu-id="44152-121">Example</span></span>  

 <span data-ttu-id="44152-122">다음 예에서는 연산자를 사용 하 여 `-=` `Integer` 다른 변수에서 하나의 변수를 빼고 결과를 후자 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="44152-122">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="44152-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44152-123">See also</span></span>

- [<span data-ttu-id="44152-124">-연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44152-124">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="44152-125">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="44152-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="44152-126">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="44152-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="44152-127">Visual Basic에서의 연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="44152-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="44152-128">기능별 연산자 목록</span><span class="sxs-lookup"><span data-stu-id="44152-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="44152-129">문</span><span class="sxs-lookup"><span data-stu-id="44152-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
