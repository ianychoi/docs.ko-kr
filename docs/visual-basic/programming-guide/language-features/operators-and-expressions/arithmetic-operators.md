---
description: '자세한 정보: 산술 연산자 Visual Basic'
title: 산술 연산자
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: 3a7005b0a44f9b0358e393d8580a2a19a9a19881
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100465329"
---
# <a name="arithmetic-operators-in-visual-basic"></a><span data-ttu-id="c87e2-103">Visual Basic의 산술 연산자</span><span class="sxs-lookup"><span data-stu-id="c87e2-103">Arithmetic Operators in Visual Basic</span></span>

<span data-ttu-id="c87e2-104">산술 연산자는 리터럴, 변수, 기타 식, 함수 및 속성 호출, 상수로 표시 되는 숫자 값의 계산과 관련 된 많은 익숙한 산술 연산을 수행 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-104">Arithmetic operators are used to perform many of the familiar arithmetic operations that involve the calculation of numeric values represented by literals, variables, other expressions, function and property calls, and constants.</span></span> <span data-ttu-id="c87e2-105">또한 산술 연산자를 사용 하 여 분류 하는 비트 시프트 연산자는 피연산자의 개별 비트 수준에서 작동 하 고 비트 패턴을 왼쪽 또는 오른쪽으로 이동 하는 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-105">Also classified with arithmetic operators are the bit-shift operators, which act at the level of the individual bits of the operands and shift their bit patterns to the left or right.</span></span>  
  
## <a name="arithmetic-operations"></a><span data-ttu-id="c87e2-106">산술 연산</span><span class="sxs-lookup"><span data-stu-id="c87e2-106">Arithmetic Operations</span></span>  

 <span data-ttu-id="c87e2-107">다음 예제가 보여 주는 것 처럼 [+ 연산자](../../../language-reference/operators/addition-operator.md)를 사용 하 여 식에 두 값을 추가 하거나 [-연산자 (Visual Basic)](../../../language-reference/operators/subtraction-operator.md)를 사용 하 여 다른 값에서 1을 뺄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-107">You can add two values in an expression together with the [+ Operator](../../../language-reference/operators/addition-operator.md), or subtract one from another with the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 <span data-ttu-id="c87e2-108">또한 부정 [연산자 (Visual Basic)](../../../language-reference/operators/subtraction-operator.md)를 사용 하지만 다음 예제와 같이 피연산자를 하나만 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-108">Negation also uses the [- Operator (Visual Basic)](../../../language-reference/operators/subtraction-operator.md), but with only one operand, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 <span data-ttu-id="c87e2-109">곱하기와 나누기는 다음 예제에서 보여 주는 것 처럼 각각 [\* 연산자](../../../language-reference/operators/multiplication-operator.md) 및 [/연산자 (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-109">Multiplication and division use the [\* Operator](../../../language-reference/operators/multiplication-operator.md) and [/ Operator (Visual Basic)](../../../language-reference/operators/floating-point-division-operator.md), respectively, as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 <span data-ttu-id="c87e2-110">다음 예제와 같이 지 한가 [^ 연산자](../../../language-reference/operators/exponentiation-operator.md)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-110">Exponentiation uses the [^ Operator](../../../language-reference/operators/exponentiation-operator.md), as the following example demonstrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 <span data-ttu-id="c87e2-111">정수 나누기는 [\ 연산자 (Visual Basic)](../../../language-reference/operators/integer-division-operator.md)를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-111">Integer division is carried out using the [\ Operator (Visual Basic)](../../../language-reference/operators/integer-division-operator.md).</span></span> <span data-ttu-id="c87e2-112">정수 나누기는 몫을 반환 합니다. 즉, 나머지는 고려 하지 않고 나누는 수를 피제수로 나눌 수 있는 횟수를 나타내는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-112">Integer division returns the quotient, that is, the integer that represents the number of times the divisor can divide into the dividend without consideration of any remainder.</span></span> <span data-ttu-id="c87e2-113">`SByte` `Byte` `Short` `UShort` `Integer` `UInteger` `Long` `ULong` 이 연산자에 대 한 제 수와 피제수는 모두 정수 계열 형식 (,,,,,, 및) 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-113">Both the divisor and the dividend must be integral types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, and `ULong`) for this operator.</span></span> <span data-ttu-id="c87e2-114">다른 모든 형식은 먼저 정수 계열 형식으로 변환 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-114">All other types must be converted to an integral type first.</span></span> <span data-ttu-id="c87e2-115">다음 예제에서는 정수 나누기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-115">The following example demonstrates integer division.</span></span>  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 <span data-ttu-id="c87e2-116">모듈러스 연산은 [Mod 연산자](../../../language-reference/operators/mod-operator.md)를 사용 하 여 수행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-116">Modulus arithmetic is performed using the [Mod Operator](../../../language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="c87e2-117">이 연산자는 제 수를 피제수로 나눈 후 나머지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-117">This operator returns the remainder after dividing the divisor into the dividend an integral number of times.</span></span> <span data-ttu-id="c87e2-118">제 수와 피제수 모두 정수 계열 형식인 경우 반환 되는 값은 정수 계열입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-118">If both divisor and dividend are integral types, the returned value is integral.</span></span> <span data-ttu-id="c87e2-119">제 수와 피제수가 부동 소수점 형식인 경우 반환 되는 값도 부동 소수점입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-119">If divisor and dividend are floating-point types, the returned value is also floating-point.</span></span> <span data-ttu-id="c87e2-120">다음 예에서는 이러한 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-120">The following example demonstrates this behavior.</span></span>  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a><span data-ttu-id="c87e2-121">0으로 나누기 시도</span><span class="sxs-lookup"><span data-stu-id="c87e2-121">Attempted Division by Zero</span></span>  

 <span data-ttu-id="c87e2-122">0으로 나누기는 관련 데이터 형식에 따라 다른 결과를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-122">Division by zero has different results depending on the data types involved.</span></span> <span data-ttu-id="c87e2-123">정수 부분 ( `SByte` ,,,,,, `Byte` `Short` `UShort` `Integer` `UInteger` `Long` ,)에서 `ULong` .NET Framework는 예외를 throw <xref:System.DivideByZeroException> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-123">In integral divisions (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`), the .NET Framework throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="c87e2-124">또는 데이터 형식에 대 한 나누기 작업에서 `Decimal` `Single` .NET Framework도 예외를 throw <xref:System.DivideByZeroException> 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-124">In division operations on the `Decimal` or `Single` data type, the .NET Framework also throws a <xref:System.DivideByZeroException> exception.</span></span>  
  
 <span data-ttu-id="c87e2-125">데이터 형식을 포함 하는 부동 소수점 분할에서는 예외가 throw 되지 않으며, `Double` <xref:System.Double.NaN> <xref:System.Double.PositiveInfinity> 피제수에 따라, 또는를 나타내는 클래스 멤버가 생성 됩니다 <xref:System.Double.NegativeInfinity> .</span><span class="sxs-lookup"><span data-stu-id="c87e2-125">In floating-point divisions involving the `Double` data type, no exception is thrown, and the result is the class member representing <xref:System.Double.NaN>, <xref:System.Double.PositiveInfinity>, or <xref:System.Double.NegativeInfinity>, depending on the dividend.</span></span> <span data-ttu-id="c87e2-126">다음 표에서는 값을 0으로 나누려고 시도 하는 다양 한 결과를 요약 하 여 보여 줍니다 `Double` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-126">The following table summarizes the various results of attempting to divide a `Double` value by zero.</span></span>  
  
|<span data-ttu-id="c87e2-127">피제수 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c87e2-127">Dividend data type</span></span>|<span data-ttu-id="c87e2-128">제 들 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="c87e2-128">Divisor data type</span></span>|<span data-ttu-id="c87e2-129">피제수 값</span><span class="sxs-lookup"><span data-stu-id="c87e2-129">Dividend value</span></span>|<span data-ttu-id="c87e2-130">결과</span><span class="sxs-lookup"><span data-stu-id="c87e2-130">Result</span></span>|  
|---|---|---|---|  
|`Double`|`Double`|<span data-ttu-id="c87e2-131">0</span><span class="sxs-lookup"><span data-stu-id="c87e2-131">0</span></span>|<span data-ttu-id="c87e2-132"><xref:System.Double.NaN> (수학적으로 정의 된 숫자 아님)</span><span class="sxs-lookup"><span data-stu-id="c87e2-132"><xref:System.Double.NaN> (not a mathematically defined number)</span></span>|  
|`Double`|`Double`|<span data-ttu-id="c87e2-133">> 0</span><span class="sxs-lookup"><span data-stu-id="c87e2-133">> 0</span></span>|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|<span data-ttu-id="c87e2-134">\< 0</span><span class="sxs-lookup"><span data-stu-id="c87e2-134">\< 0</span></span>|<xref:System.Double.NegativeInfinity>|  
  
 <span data-ttu-id="c87e2-135">예외를 catch 하는 경우 <xref:System.DivideByZeroException> 해당 멤버를 사용 하 여 처리를 지원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-135">When you catch a <xref:System.DivideByZeroException> exception, you can use its members to help you handle it.</span></span> <span data-ttu-id="c87e2-136">예를 들어 <xref:System.Exception.Message%2A> 속성은 예외에 대 한 메시지 텍스트를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-136">For example, the <xref:System.Exception.Message%2A> property holds the message text for the exception.</span></span> <span data-ttu-id="c87e2-137">자세한 내용은 [Try...Catch...Finally 문](../../../language-reference/statements/try-catch-finally-statement.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e2-137">For more information, see [Try...Catch...Finally Statement](../../../language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="bit-shift-operations"></a><span data-ttu-id="c87e2-138">Bit-Shift 작업</span><span class="sxs-lookup"><span data-stu-id="c87e2-138">Bit-Shift Operations</span></span>  

 <span data-ttu-id="c87e2-139">비트 시프트 연산은 비트 패턴에서 산술 시프트를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-139">A bit-shift operation performs an arithmetic shift on a bit pattern.</span></span> <span data-ttu-id="c87e2-140">패턴은 왼쪽에 있는 피연산자에 포함 되 고 오른쪽의 피연산자는 패턴을 이동할 위치 수를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-140">The pattern is contained in the operand on the left, while the operand on the right specifies the number of positions to shift the pattern.</span></span> <span data-ttu-id="c87e2-141">[>> 연산자](../../../language-reference/operators/right-shift-operator.md) 를 사용 하 여 패턴을 오른쪽으로 이동 하거나 [<< 연산자](../../../language-reference/operators/left-shift-operator.md)를 사용 하 여 왼쪽으로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-141">You can shift the pattern to the right with the [>> Operator](../../../language-reference/operators/right-shift-operator.md) or to the left with the [<< Operator](../../../language-reference/operators/left-shift-operator.md).</span></span>  
  
 <span data-ttu-id="c87e2-142">패턴 피연산자의 데이터 형식은 `SByte` ,, `Byte` `Short` ,,,, 또는 여야 합니다 `UShort` `Integer` `UInteger` `Long` `ULong` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-142">The data type of the pattern operand must be `SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`.</span></span> <span data-ttu-id="c87e2-143">시프트 금액 피연산자의 데이터 형식은 `Integer` 로 확대 되거나 확장 되어야 합니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-143">The data type of the shift amount operand must be `Integer` or must widen to `Integer`.</span></span>  
  
 <span data-ttu-id="c87e2-144">산술 시프트는 순환 하지 않습니다. 즉, 결과의 한쪽 끝에서 이동 하는 비트가 다른 쪽 끝에서는 다시 계산 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-144">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="c87e2-145">시프트에 의해 비워진 비트 위치는 다음과 같이 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-145">The bit positions vacated by a shift are set as follows:</span></span>  
  
- <span data-ttu-id="c87e2-146">산술 왼쪽 시프트의 경우 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-146">0 for an arithmetic left shift</span></span>  
  
- <span data-ttu-id="c87e2-147">양수의 산술 오른쪽 시프트 인 경우 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-147">0 for an arithmetic right shift of a positive number</span></span>  
  
- <span data-ttu-id="c87e2-148">부호 없는 데이터 형식 ( `Byte` , `UShort` , `UInteger` , `ULong` )의 산술 오른쪽 시프트의 경우 0입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-148">0 for an arithmetic right shift of an unsigned data type (`Byte`, `UShort`, `UInteger`, `ULong`)</span></span>  
  
- <span data-ttu-id="c87e2-149">음수 ( `SByte` ,, `Short` `Integer` 또는 `Long` )의 산술 오른쪽 시프트 인 경우 1입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-149">1 for an arithmetic right shift of a negative number (`SByte`, `Short`, `Integer`, or `Long`)</span></span>  
  
 <span data-ttu-id="c87e2-150">다음 예에서는 `Integer` 왼쪽 및 오른쪽 모두에 값을 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-150">The following example shifts an `Integer` value both left and right.</span></span>  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 <span data-ttu-id="c87e2-151">산술 시프트는 오버플로 예외를 생성 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-151">Arithmetic shifts never generate overflow exceptions.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="c87e2-152">비트 연산</span><span class="sxs-lookup"><span data-stu-id="c87e2-152">Bitwise Operations</span></span>  

 <span data-ttu-id="c87e2-153">논리 연산자 외에도,, `Not` `Or` `And` 및 `Xor` 는 숫자 값에 사용 될 때 비트 산술 연산을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-153">In addition to being logical operators, `Not`, `Or`, `And`, and `Xor` also perform bitwise arithmetic when used on numeric values.</span></span> <span data-ttu-id="c87e2-154">자세한 내용은 [Visual Basic 논리 및 비트 연산자](logical-and-bitwise-operators.md)의 "비트 연산"을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e2-154">For more information, see "Bitwise Operations" in [Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md).</span></span>  
  
## <a name="type-safety"></a><span data-ttu-id="c87e2-155">형식 안전성</span><span class="sxs-lookup"><span data-stu-id="c87e2-155">Type Safety</span></span>  

 <span data-ttu-id="c87e2-156">일반적으로 피연산자는 동일한 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-156">Operands should normally be of the same type.</span></span> <span data-ttu-id="c87e2-157">예를 들어 변수를 추가 하는 경우 `Integer` 다른 변수에 추가 하 `Integer` 고 결과를 형식의 변수에도 할당 해야 합니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-157">For example, if you are doing addition with an `Integer` variable, you should add it to another `Integer` variable, and you should assign the result to a variable of type `Integer` as well.</span></span>  
  
 <span data-ttu-id="c87e2-158">적절 한 형식 안전 코딩 방법을 보장 하는 한 가지 방법은 [Option Strict 문을](../../../language-reference/statements/option-strict-statement.md)사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-158">One way to ensure good type-safe coding practice is to use the [Option Strict Statement](../../../language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="c87e2-159">를 설정 하 `Option Strict On` 는 경우 Visual Basic에서 *형식 안전* 변환을 자동으로 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-159">If you set `Option Strict On`, Visual Basic automatically performs *type-safe* conversions.</span></span> <span data-ttu-id="c87e2-160">예를 들어 변수에 변수를 추가 하 여 변수에 값을 할당 하려고 하면 `Integer` `Double` 값이 `Double` `Integer` `Double` 데이터 손실 없이로 변환 될 수 있으므로 작업은 정상적으로 진행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-160">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to a `Double` variable, the operation proceeds normally, because an `Integer` value can be converted to `Double` without loss of data.</span></span> <span data-ttu-id="c87e2-161">반면 형식이 안전 하지 않은 변환은에서 컴파일러 오류가 발생 `Option Strict On` 합니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-161">Type-unsafe conversions, on the other hand, cause a compiler error with `Option Strict On`.</span></span> <span data-ttu-id="c87e2-162">예를 들어 변수에 변수를 추가 하 고 변수에 값을 할당 하려고 하면 `Integer` 변수를 암시적으로 형식으로 `Double` `Integer` 변환할 수 없기 때문에 컴파일러 오류가 발생 합니다 `Double` `Integer` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-162">For example, if you try to add an `Integer` variable to a `Double` variable and assign the value to an `Integer` variable, a compiler error results, because a `Double` variable cannot be implicitly converted to type `Integer`.</span></span>  
  
 <span data-ttu-id="c87e2-163">그러나를 설정 하는 경우에는 `Option Strict Off` Visual Basic에서 암시적 축소 변환을 수행할 수 있지만 예기치 않은 데이터 손실 또는 전체 자릿수가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c87e2-163">If you set `Option Strict Off`, however, Visual Basic allows implicit narrowing conversions to take place, although they can result in the unexpected loss of data or precision.</span></span> <span data-ttu-id="c87e2-164">따라서 프로덕션 코드를 작성할 때를 사용 하는 것이 좋습니다 `Option Strict On` .</span><span class="sxs-lookup"><span data-stu-id="c87e2-164">For this reason, we recommend that you use `Option Strict On` when writing production code.</span></span> <span data-ttu-id="c87e2-165">자세한 내용은 [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c87e2-165">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c87e2-166">추가 정보</span><span class="sxs-lookup"><span data-stu-id="c87e2-166">See also</span></span>

- [<span data-ttu-id="c87e2-167">산술 연산자</span><span class="sxs-lookup"><span data-stu-id="c87e2-167">Arithmetic Operators</span></span>](../../../language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="c87e2-168">비트 시프트 연산자</span><span class="sxs-lookup"><span data-stu-id="c87e2-168">Bit Shift Operators</span></span>](../../../language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="c87e2-169">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c87e2-169">Comparison Operators in Visual Basic</span></span>](comparison-operators.md)
- [<span data-ttu-id="c87e2-170">Visual Basic의 연결 연산자</span><span class="sxs-lookup"><span data-stu-id="c87e2-170">Concatenation Operators in Visual Basic</span></span>](concatenation-operators.md)
- [<span data-ttu-id="c87e2-171">Visual Basic의 논리 및 비트 연산자</span><span class="sxs-lookup"><span data-stu-id="c87e2-171">Logical and Bitwise Operators in Visual Basic</span></span>](logical-and-bitwise-operators.md)
- [<span data-ttu-id="c87e2-172">연산자의 효율적 결합</span><span class="sxs-lookup"><span data-stu-id="c87e2-172">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
