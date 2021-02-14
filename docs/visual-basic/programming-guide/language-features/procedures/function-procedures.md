---
description: '자세한 정보: 함수 프로시저 (Visual Basic)'
title: Function 프로시저
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 4997059fc33fb5d438519356b2c9fdd9e6a27cce
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436151"
---
# <a name="function-procedures-visual-basic"></a><span data-ttu-id="2964b-103">함수 프로시저 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2964b-103">Function procedures (Visual Basic)</span></span>

<span data-ttu-id="2964b-104">`Function`프로시저는 및 문으로 묶인 일련의 Visual Basic 문입니다 `Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2964b-104">A `Function` procedure is a series of Visual Basic statements enclosed by the `Function` and `End Function` statements.</span></span> <span data-ttu-id="2964b-105">`Function`프로시저는 작업을 수행한 다음 호출 코드에 컨트롤을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-105">The `Function` procedure performs a task and then returns control to the calling code.</span></span> <span data-ttu-id="2964b-106">제어를 반환할 때 호출 코드에도 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-106">When it returns control, it also returns a value to the calling code.</span></span>

<span data-ttu-id="2964b-107">프로시저가 호출 될 때마다 문이 실행 되 고 문 뒤의 첫 번째 실행 가능 문부터 시작 `Function` 하 여 첫 번째 `End Function` , `Exit Function` 또는 문으로 끝나는 문이 실행 됩니다 `Return` .</span><span class="sxs-lookup"><span data-stu-id="2964b-107">Each time the procedure is called, its statements run, starting with the first executable statement after the `Function` statement and ending with the first `End Function`, `Exit Function`, or `Return` statement encountered.</span></span>

<span data-ttu-id="2964b-108">`Function`모듈, 클래스 또는 구조체에서 프로시저를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-108">You can define a `Function` procedure in a module, class, or structure.</span></span> <span data-ttu-id="2964b-109">이는 `Public` 기본적으로 응용 프로그램의 어디에서 나 사용자가 정의한 모듈, 클래스 또는 구조에 대 한 액세스 권한이 있는 모든 위치에서 호출할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-109">It is `Public` by default, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span>

<span data-ttu-id="2964b-110">`Function`프로시저는 호출 코드를 통해 전달 되는 상수, 변수 또는 식과 같은 인수를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-110">A `Function` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>

## <a name="declaration-syntax"></a><span data-ttu-id="2964b-111">선언 구문</span><span class="sxs-lookup"><span data-stu-id="2964b-111">Declaration syntax</span></span>

<span data-ttu-id="2964b-112">프로시저를 선언 하는 구문은 다음과 같습니다 `Function` .</span><span class="sxs-lookup"><span data-stu-id="2964b-112">The syntax for declaring a `Function` procedure is as follows:</span></span>

```vb
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType
    [Statements]
End Function
```

<span data-ttu-id="2964b-113">*한정자* 는 오버 로드, 재정의, 공유 및 숨김과 관련 된 정보 및 액세스 수준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-113">The *modifiers* can specify access level and information regarding overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="2964b-114">자세한 내용은 [Function 문](../../../language-reference/statements/function-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2964b-114">For more information, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

<span data-ttu-id="2964b-115">[하위 프로시저](./sub-procedures.md)와 동일한 방식으로 각 매개 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-115">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md).</span></span>

### <a name="data-type"></a><span data-ttu-id="2964b-116">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="2964b-116">Data type</span></span>

<span data-ttu-id="2964b-117">모든 `Function` 프로시저에는 모든 변수와 마찬가지로 데이터 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-117">Every `Function` procedure has a data type, just as every variable does.</span></span> <span data-ttu-id="2964b-118">이 데이터 형식은 문의 절에 의해 지정 `As` `Function` 되며 함수에서 호출 코드에 반환 하는 값의 데이터 형식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-118">This data type is specified by the `As` clause in the `Function` statement, and it determines the data type of the value the function returns to the calling code.</span></span> <span data-ttu-id="2964b-119">다음 샘플 선언에서는이를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-119">The following sample declarations illustrate this.</span></span>

```vb
Function Yesterday() As Date
End Function

Function FindSqrt(radicand As Single) As Single
End Function
```

<span data-ttu-id="2964b-120">자세한 내용은 [함수 문의](../../../language-reference/statements/function-statement.md)"Parts"를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2964b-120">For more information, see "Parts" in [Function Statement](../../../language-reference/statements/function-statement.md).</span></span>

### <a name="returning-values"></a><span data-ttu-id="2964b-121">값 반환</span><span class="sxs-lookup"><span data-stu-id="2964b-121">Returning values</span></span>

<span data-ttu-id="2964b-122">`Function`프로시저에서 호출 하는 코드로 다시 전송 하는 값을 해당 반환 값 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-122">The value a `Function` procedure sends back to the calling code is called its return value.</span></span> <span data-ttu-id="2964b-123">이 프로시저는 다음 두 가지 방법 중 하나로이 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-123">The procedure returns this value in one of two ways:</span></span>

- <span data-ttu-id="2964b-124">문을 사용 하 여 `Return` 반환 값을 지정 하 고 제어를 호출 프로그램에 즉시 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-124">It uses the `Return` statement to specify the return value, and returns control immediately to the calling program.</span></span> <span data-ttu-id="2964b-125">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-125">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement immediately transfers control back
      ' to the calling code and returns the value of Expression.
      Return Expression
  End Function
  ```

- <span data-ttu-id="2964b-126">프로시저의 하나 이상의 문에서 고유한 함수 이름에 값을 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-126">It assigns a value to its own function name in one or more statements of the procedure.</span></span> <span data-ttu-id="2964b-127">컨트롤은 `Exit Function` 또는 문이 실행 될 때까지 호출 프로그램에 반환 되지 않습니다 `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2964b-127">Control does not return to the calling program until an `Exit Function` or `End Function` statement is executed.</span></span> <span data-ttu-id="2964b-128">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-128">The following example illustrates this.</span></span>

  ```vb
  Function FunctionName [(ParameterList)] As ReturnType
      ' The following statement does not transfer control back to the calling code.
      FunctionName = Expression
      ' When control returns to the calling code, Expression is the return value.
  End Function
  ```

<span data-ttu-id="2964b-129">함수 이름에 반환 값을 할당 하는 장점은 컨트롤이 또는 문을 발견할 때까지 프로시저에서 반환 되지 않는다는 것입니다 `Exit Function` `End Function` .</span><span class="sxs-lookup"><span data-stu-id="2964b-129">The advantage of assigning the return value to the function name is that control does not return from the procedure until it encounters an `Exit Function` or `End Function` statement.</span></span> <span data-ttu-id="2964b-130">이렇게 하면 예비 값을 할당 하 고 필요한 경우 나중에 해당 값을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-130">This allows you to assign a preliminary value and adjust it later if necessary.</span></span>

<span data-ttu-id="2964b-131">값 반환에 대 한 자세한 내용은 [Function 문](../../../language-reference/statements/function-statement.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="2964b-131">For more information about returning values, see [Function Statement](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="2964b-132">배열을 반환 하는 방법에 대 한 자세한 내용은 [배열](../arrays/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="2964b-132">For information about returning arrays, see [Arrays](../arrays/index.md).</span></span>

## <a name="calling-syntax"></a><span data-ttu-id="2964b-133">호출 구문</span><span class="sxs-lookup"><span data-stu-id="2964b-133">Calling syntax</span></span>

<span data-ttu-id="2964b-134">`Function`프로시저는 대입문의 오른쪽에 있는 이름 및 인수를 포함 하 여 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-134">You invoke a `Function` procedure by including its name and arguments either on the right side of an assignment statement or in an expression.</span></span> <span data-ttu-id="2964b-135">선택 사항이 아닌 모든 인수에 대 한 값을 제공 해야 하며 인수 목록을 괄호로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-135">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="2964b-136">인수를 제공 하지 않으면 필요에 따라 괄호를 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-136">If no arguments are supplied, you can optionally omit the parentheses.</span></span>

<span data-ttu-id="2964b-137">프로시저에 대 한 호출 구문은 `Function` 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-137">The syntax for a call to a `Function` procedure is as follows.</span></span>

<span data-ttu-id="2964b-138">*lvalue* `=` *functionname* `[(` *argumentlist*    `)]`</span><span class="sxs-lookup"><span data-stu-id="2964b-138">*lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`</span></span>

<span data-ttu-id="2964b-139">`If ((`*functionname* `[(` *argumentlist* `)] / 3) <=` *식*  `) Then`</span><span class="sxs-lookup"><span data-stu-id="2964b-139">`If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`</span></span>

<span data-ttu-id="2964b-140">프로시저를 호출할 때는 `Function` 해당 반환 값을 사용 하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-140">When you call a `Function` procedure, you do not have to use its return value.</span></span> <span data-ttu-id="2964b-141">그렇지 않으면 함수의 모든 동작이 수행 되지만 반환 값은 무시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-141">If you do not, all the actions of the function are performed, but the return value is ignored.</span></span> <span data-ttu-id="2964b-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> 는 이러한 방식으로 호출 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-142"><xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> is often called in this manner.</span></span>

### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="2964b-143">선언 및 호출에 대 한 그림</span><span class="sxs-lookup"><span data-stu-id="2964b-143">Illustration of declaration and call</span></span>

<span data-ttu-id="2964b-144">다음 `Function` 프로시저는 다른 두 변의 값을 고려 하 여 오른쪽 삼각형의 가장 긴 쪽 또는 빗변을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="2964b-144">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>

[!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

<span data-ttu-id="2964b-145">다음 예제에서는에 대 한 일반적인 호출을 보여 줍니다 `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="2964b-145">The following example shows a typical call to `hypotenuse`.</span></span>

[!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]

## <a name="see-also"></a><span data-ttu-id="2964b-146">추가 정보</span><span class="sxs-lookup"><span data-stu-id="2964b-146">See also</span></span>

- [<span data-ttu-id="2964b-147">절차</span><span class="sxs-lookup"><span data-stu-id="2964b-147">Procedures</span></span>](./index.md)
- [<span data-ttu-id="2964b-148">하위 프로시저</span><span class="sxs-lookup"><span data-stu-id="2964b-148">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="2964b-149">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="2964b-149">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="2964b-150">연산자 프로시저</span><span class="sxs-lookup"><span data-stu-id="2964b-150">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="2964b-151">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="2964b-151">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="2964b-152">Function 문</span><span class="sxs-lookup"><span data-stu-id="2964b-152">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="2964b-153">방법: 값을 반환하는 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="2964b-153">How to: Create a Procedure that Returns a Value</span></span>](./how-to-create-a-procedure-that-returns-a-value.md)
- [<span data-ttu-id="2964b-154">방법: 프로시저에서 값 반환</span><span class="sxs-lookup"><span data-stu-id="2964b-154">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="2964b-155">방법: 값을 반환하는 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="2964b-155">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
