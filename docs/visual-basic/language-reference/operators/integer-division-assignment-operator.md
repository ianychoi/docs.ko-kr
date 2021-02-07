---
description: ': = 연산자에 대 한 자세한 정보'
title: '\= 연산자'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a05e136cbf17eaf7102fb2213993adf9cf0e06be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99665811"
---
# <a name="-operator"></a><span data-ttu-id="917b5-103">\\= 연산자</span><span class="sxs-lookup"><span data-stu-id="917b5-103">\\= Operator</span></span>

<span data-ttu-id="917b5-104">변수 또는 속성의 값을 식의 값으로 나누고 정수 결과를 변수 또는 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-104">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917b5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="917b5-105">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="917b5-106">부분</span><span class="sxs-lookup"><span data-stu-id="917b5-106">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="917b5-107">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-107">Required.</span></span> <span data-ttu-id="917b5-108">임의의 숫자 변수 또는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-108">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="917b5-109">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="917b5-109">Required.</span></span> <span data-ttu-id="917b5-110">임의의 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-110">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917b5-111">설명</span><span class="sxs-lookup"><span data-stu-id="917b5-111">Remarks</span></span>  

 <span data-ttu-id="917b5-112">연산자의 좌 변에 있는 요소는 `\=` 간단한 스칼라 변수, 속성 또는 배열의 요소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-112">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="917b5-113">변수 또는 속성은 [ReadOnly](../modifiers/readonly.md)일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-113">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="917b5-114">연산자는 왼쪽에 있는 `\=` 변수나 속성의 값을 오른쪽의 값으로 나누고 정수 결과를 왼쪽의 변수나 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-114">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="917b5-115">정수 나누기에 대 한 자세한 내용은 [\ 연산자 (Visual Basic)](integer-division-operator.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="917b5-115">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="917b5-116">오버로딩</span><span class="sxs-lookup"><span data-stu-id="917b5-116">Overloading</span></span>  

 <span data-ttu-id="917b5-117">`\`연산자를 *오버 로드할* 수 있습니다. 즉, 피연산자가 해당 클래스 또는 구조체의 형식일 때 클래스 또는 구조체의 동작을 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-117">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="917b5-118">연산자를 오버 로드 하면 `\` 연산자의 동작에 영향을 줍니다 `\=` .</span><span class="sxs-lookup"><span data-stu-id="917b5-118">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="917b5-119">`\=`오버 로드 하는 클래스 또는 구조체에서 코드를 사용 하는 경우 다시 `\` 정의 된 동작을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-119">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="917b5-120">자세한 내용은 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="917b5-120">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="917b5-121">예제</span><span class="sxs-lookup"><span data-stu-id="917b5-121">Example</span></span>  

 <span data-ttu-id="917b5-122">다음 예에서는 연산자를 사용 하 여 `\=` 한 `Integer` 변수를 두 번째로 나누고 정수 결과를 첫 번째 변수에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="917b5-122">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="917b5-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="917b5-123">See also</span></span>

- [<span data-ttu-id="917b5-124">\ 연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="917b5-124">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="917b5-125">/= 연산자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="917b5-125">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="917b5-126">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="917b5-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="917b5-127">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="917b5-127">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="917b5-128">Visual Basic에서의 연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="917b5-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="917b5-129">기능별 연산자 목록</span><span class="sxs-lookup"><span data-stu-id="917b5-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="917b5-130">문</span><span class="sxs-lookup"><span data-stu-id="917b5-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
