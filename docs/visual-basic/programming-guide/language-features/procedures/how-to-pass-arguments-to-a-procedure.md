---
description: '자세한 정보: 방법: 프로시저에 인수 전달 (Visual Basic)'
title: '방법: 프로시저에 인수 전달'
ms.date: 07/20/2015
helpviewer_keywords:
- arguments [Visual Basic], passing to procedures
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- procedure parameters
- procedures [Visual Basic], calling
- argument passing [Visual Basic], procedures
ms.assetid: 08723588-3890-4ddc-8249-79e049e0f241
ms.openlocfilehash: e4dcdac19699c4b4b1f88327034a9e9d4364f040
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434331"
---
# <a name="how-to-pass-arguments-to-a-procedure-visual-basic"></a><span data-ttu-id="e5dd5-103">방법: 프로시저에 인수 전달(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5dd5-103">How to: Pass Arguments to a Procedure (Visual Basic)</span></span>

<span data-ttu-id="e5dd5-104">프로시저를 호출할 때 인수 목록이 있는 프로시저 이름을 괄호 안에 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-104">When you call a procedure, you follow the procedure name with an argument list in parentheses.</span></span> <span data-ttu-id="e5dd5-105">프로시저에서 정의 하는 모든 필수 매개 변수에 해당 하는 인수를 제공 하 고 선택적으로 매개 변수에 인수를 제공할 수 있습니다 `Optional` .</span><span class="sxs-lookup"><span data-stu-id="e5dd5-105">You supply an argument corresponding to every required parameter the procedure defines, and you can optionally supply arguments to the `Optional` parameters.</span></span> <span data-ttu-id="e5dd5-106">호출에 매개 변수를 제공 하지 않는 경우 `Optional` 후속 인수를 제공 하는 경우 인수 목록에 쉼표를 포함 하 여 해당 자리를 표시 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-106">If you do not supply an `Optional` parameter in the call, you must include a comma to mark its place in the argument list if you are supplying any subsequent arguments.</span></span>  
  
 <span data-ttu-id="e5dd5-107">와 같이 해당 매개 변수와 다른 데이터 형식의 인수를 전달 하려는 경우 `Byte` `String` 형식 확인 스위치 ([Option Strict 문](../../../language-reference/statements/option-strict-statement.md))를로 설정할 수 있습니다 `Off` .</span><span class="sxs-lookup"><span data-stu-id="e5dd5-107">If you intend to pass an argument of a data type different from that of its corresponding parameter, such as `Byte` to `String`, you can set the type-checking switch ([Option Strict Statement](../../../language-reference/statements/option-strict-statement.md)) to `Off`.</span></span> <span data-ttu-id="e5dd5-108">`Option Strict`가 이면 `On` 확대 변환 또는 명시적 변환 키워드 중 하나를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-108">If `Option Strict` is `On`, you must use either widening conversions or explicit conversion keywords.</span></span> <span data-ttu-id="e5dd5-109">자세한 내용은 [확대 및 축소 변환](../data-types/widening-and-narrowing-conversions.md) 및 [형식 변환 함수](../../../language-reference/functions/type-conversion-functions.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-109">For more information, see [Widening and Narrowing Conversions](../data-types/widening-and-narrowing-conversions.md) and [Type Conversion Functions](../../../language-reference/functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="e5dd5-110">자세한 내용은 [프로시저 매개 변수 및 인수](./procedure-parameters-and-arguments.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-110">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-pass-one-or-more-arguments-to-a-procedure"></a><span data-ttu-id="e5dd5-111">프로시저에 하나 이상의 인수를 전달 하려면</span><span class="sxs-lookup"><span data-stu-id="e5dd5-111">To pass one or more arguments to a procedure</span></span>  
  
1. <span data-ttu-id="e5dd5-112">호출 문에서 괄호를 사용 하 여 프로시저 이름을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-112">In the calling statement, follow the procedure name with parentheses.</span></span>  
  
2. <span data-ttu-id="e5dd5-113">괄호 안에 인수 목록을 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-113">Inside the parentheses, put an argument list.</span></span> <span data-ttu-id="e5dd5-114">프로시저에서 정의 하는 각 필수 매개 변수에 대 한 인수를 포함 하 고 인수를 쉼표로 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-114">Include an argument for each required parameter the procedure defines, and separate the arguments with commas.</span></span>  
  
3. <span data-ttu-id="e5dd5-115">각 인수가 해당 매개 변수에 대해 프로시저에서 정의 하는 형식으로 변환할 수 있는 데이터 형식으로 계산 되는 유효한 식 인지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-115">Make sure each argument is a valid expression that evaluates to a data type convertible to the type the procedure defines for the corresponding parameter.</span></span>  
  
4. <span data-ttu-id="e5dd5-116">매개 변수가 [선택적](../../../language-reference/modifiers/optional.md)으로 정의 된 경우 인수 목록에 포함 하거나 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-116">If a parameter is defined as [Optional](../../../language-reference/modifiers/optional.md), you can either include it in the argument list or omit it.</span></span> <span data-ttu-id="e5dd5-117">생략 하면 프로시저는 해당 매개 변수에 대해 정의 된 기본값을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-117">If you omit it, the procedure uses the default value defined for that parameter.</span></span>  
  
5. <span data-ttu-id="e5dd5-118">매개 변수에 대 한 인수를 생략 하 고 매개 변수 `Optional` 목록에 다른 매개 변수가 있는 경우 인수 목록에서 생략 된 인수의 자리를 추가 쉼표로 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-118">If you omit an argument for an `Optional` parameter and there is another parameter after it in the parameter list, you can mark the place of the omitted argument by an extra comma in the argument list.</span></span>  
  
     <span data-ttu-id="e5dd5-119">다음 예에서는 Visual Basic 함수를 호출 합니다 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> .</span><span class="sxs-lookup"><span data-stu-id="e5dd5-119">The following example calls the Visual Basic <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function.</span></span>  
  
     [!code-vb[VbVbcnProcedures#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#34)]  
  
     <span data-ttu-id="e5dd5-120">앞의 예제에서는 표시 되는 메시지 문자열인 필수 첫 번째 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-120">The preceding example supplies the required first argument, which is the message string to be displayed.</span></span> <span data-ttu-id="e5dd5-121">메시지 상자에 표시할 단추를 지정 하는 선택적 두 번째 매개 변수에 대 한 인수를 생략 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-121">It omits an argument for the optional second parameter, which specifies the buttons to be displayed on the message box.</span></span> <span data-ttu-id="e5dd5-122">호출에서 값을 제공 하지 않으므로는 `MsgBox` `MsgBoxStyle.OKOnly` **확인** 단추만 표시 하는 기본값인를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-122">Because the call does not supply a value, `MsgBox` uses the default value, `MsgBoxStyle.OKOnly`, which displays only an **OK** button.</span></span>  
  
     <span data-ttu-id="e5dd5-123">인수 목록에서 두 번째 쉼표는 생략 된 두 번째 인수의 자리를 표시 하 고 마지막 문자열은 `MsgBox` 제목 표시줄에 표시 되는 텍스트인의 선택적 세 번째 매개 변수로 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e5dd5-123">The second comma in the argument list marks the place of the omitted second argument, and the last string is passed to the optional third parameter of `MsgBox`, which is the text to be displayed in the title bar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5dd5-124">추가 정보</span><span class="sxs-lookup"><span data-stu-id="e5dd5-124">See also</span></span>

- [<span data-ttu-id="e5dd5-125">하위 프로시저</span><span class="sxs-lookup"><span data-stu-id="e5dd5-125">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e5dd5-126">함수 프로시저</span><span class="sxs-lookup"><span data-stu-id="e5dd5-126">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="e5dd5-127">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="e5dd5-127">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e5dd5-128">연산자 프로시저</span><span class="sxs-lookup"><span data-stu-id="e5dd5-128">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e5dd5-129">방법: 프로시저의 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="e5dd5-129">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="e5dd5-130">값 또는 참조로 인수 전달</span><span class="sxs-lookup"><span data-stu-id="e5dd5-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e5dd5-131">재귀 프로시저</span><span class="sxs-lookup"><span data-stu-id="e5dd5-131">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="e5dd5-132">프로시저 오버로딩</span><span class="sxs-lookup"><span data-stu-id="e5dd5-132">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="e5dd5-133">개체 및 클래스</span><span class="sxs-lookup"><span data-stu-id="e5dd5-133">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="e5dd5-134">개체 지향 프로그래밍(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5dd5-134">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
