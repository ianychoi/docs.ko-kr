---
description: '다음에 대 한 자세한 정보: + = 연산자 (Visual Basic)'
title: += 연산자
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: e5a6b8fcc75e44c00ee18fec9cd57e68b1218de7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640474"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="ae9ca-103">+= 연산자(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae9ca-103">+= Operator (Visual Basic)</span></span>

<span data-ttu-id="ae9ca-104">숫자 식의 값을 숫자 변수나 속성의 값에 추가 하 고 결과를 변수 또는 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-104">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="ae9ca-105">를 사용 하 여 `String` 변수 또는 속성에 식을 연결 하 `String` 고 결과를 변수 또는 속성에 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-105">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae9ca-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae9ca-106">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ae9ca-107">부분</span><span class="sxs-lookup"><span data-stu-id="ae9ca-107">Parts</span></span>  

 `variableorproperty`  
 <span data-ttu-id="ae9ca-108">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-108">Required.</span></span> <span data-ttu-id="ae9ca-109">임의의 숫자 또는 `String` 변수 또는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-109">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="ae9ca-110">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-110">Required.</span></span> <span data-ttu-id="ae9ca-111">임의의 숫자 또는 `String` 식입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-111">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae9ca-112">설명</span><span class="sxs-lookup"><span data-stu-id="ae9ca-112">Remarks</span></span>  

 <span data-ttu-id="ae9ca-113">연산자의 좌 변에 있는 요소는 `+=` 간단한 스칼라 변수, 속성 또는 배열의 요소일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-113">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ae9ca-114">변수 또는 속성은 [ReadOnly](../modifiers/readonly.md)일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-114">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ae9ca-115">`+=`연산자는 오른쪽의 값을 왼쪽에 있는 변수나 속성에 추가 하 고 결과를 왼쪽에 있는 변수나 속성에 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-115">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="ae9ca-116">`+=`연산자를 사용 하 여 `String` 오른쪽에 있는 식을 `String` 왼쪽에 있는 변수나 속성에 연결 하 고 그 왼쪽에 있는 변수나 속성에 결과를 할당할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-116">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ae9ca-117">연산자를 사용 하는 경우 `+=` 더하기 또는 문자열 연결의 발생 여부를 확인 하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-117">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="ae9ca-118">모호성을 `&=` 없애고 자체 문서화 코드를 제공 하려면 연산자를 연결에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-118">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="ae9ca-119">이 할당 연산자는 컴파일 환경에서 엄격한 의미 체계를 적용 하는 경우 암시적으로 확대를 수행 하지만 축소 변환을 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-119">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="ae9ca-120">이러한 변환에 대 한 자세한 내용은 [확대 및 축소 변환](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-120">For more information on these conversions, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="ae9ca-121">Strict 및 관대 한 의미 체계에 대 한 자세한 내용은 [Option Strict 문](../statements/option-strict-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-121">For more information on strict and permissive semantics, see [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="ae9ca-122">관대 한 의미 체계가 허용 되는 경우 `+=` 연산자는 연산자가 수행 하는 것과 같은 다양 한 문자열 및 숫자 변환을 암시적으로 수행 합니다 `+` .</span><span class="sxs-lookup"><span data-stu-id="ae9ca-122">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="ae9ca-123">이러한 변환에 대 한 자세한 내용은 [+ 연산자](addition-operator.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-123">For details on these conversions, see [+ Operator](addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ae9ca-124">오버로딩</span><span class="sxs-lookup"><span data-stu-id="ae9ca-124">Overloading</span></span>  

 <span data-ttu-id="ae9ca-125">`+`연산자를 *오버 로드할* 수 있습니다. 즉, 피연산자가 해당 클래스 또는 구조체의 형식일 때 클래스 또는 구조체의 동작을 다시 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-125">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ae9ca-126">연산자를 오버 로드 하면 `+` 연산자의 동작에 영향을 줍니다 `+=` .</span><span class="sxs-lookup"><span data-stu-id="ae9ca-126">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="ae9ca-127">`+=`오버 로드 하는 클래스 또는 구조체에서 코드를 사용 하는 경우 다시 `+` 정의 된 동작을 이해 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-127">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ae9ca-128">자세한 내용은 [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-128">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae9ca-129">예제</span><span class="sxs-lookup"><span data-stu-id="ae9ca-129">Example</span></span>  

 <span data-ttu-id="ae9ca-130">다음 예에서는 연산자를 사용 `+=` 하 여 한 변수의 값을 다른 변수의 값과 결합 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-130">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="ae9ca-131">첫 번째 부분은 숫자 변수와 함께를 사용 하 여 `+=` 한 값을 다른 값에 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-131">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="ae9ca-132">두 번째 부분은 변수와 함께를 사용 하 여 `+=` `String` 한 값을 다른 값과 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-132">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="ae9ca-133">두 경우 모두 결과는 첫 번째 변수에 할당 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-133">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="ae9ca-134">값은 `num1` 이제 13 이며 값은 `str1` 이제 "103"입니다.</span><span class="sxs-lookup"><span data-stu-id="ae9ca-134">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae9ca-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ae9ca-135">See also</span></span>

- [<span data-ttu-id="ae9ca-136">+ 연산자</span><span class="sxs-lookup"><span data-stu-id="ae9ca-136">+ Operator</span></span>](addition-operator.md)
- [<span data-ttu-id="ae9ca-137">할당 연산자</span><span class="sxs-lookup"><span data-stu-id="ae9ca-137">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="ae9ca-138">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="ae9ca-138">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="ae9ca-139">연결 연산자</span><span class="sxs-lookup"><span data-stu-id="ae9ca-139">Concatenation Operators</span></span>](concatenation-operators.md)
- [<span data-ttu-id="ae9ca-140">Visual Basic에서의 연산자 우선 순위</span><span class="sxs-lookup"><span data-stu-id="ae9ca-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="ae9ca-141">기능별 연산자 목록</span><span class="sxs-lookup"><span data-stu-id="ae9ca-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="ae9ca-142">문</span><span class="sxs-lookup"><span data-stu-id="ae9ca-142">Statements</span></span>](../../programming-guide/language-features/statements.md)
