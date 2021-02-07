---
description: '자세히 알아보기: Option 유추 문'
title: Option Infer 문
ms.date: 07/20/2015
f1_keywords:
- vb.OptionInfer
- vb.Infer
helpviewer_keywords:
- variables [Visual Basic], declaring
- Option Infer statement [Visual Basic]
- Infer keyword [Visual Basic]
- declaring variables [Visual Basic], inferred
- inferred variable declaration
ms.assetid: 4ad3e6e9-8f5b-4209-a248-de22ef6e4652
ms.openlocfilehash: d0c3de7bdafb7e9b361da7a8538046e3d76b5ce7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741590"
---
# <a name="option-infer-statement"></a><span data-ttu-id="44b2c-103">Option Infer 문</span><span class="sxs-lookup"><span data-stu-id="44b2c-103">Option Infer Statement</span></span>

<span data-ttu-id="44b2c-104">변수를 선언할 때 지역 형식 유추를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-104">Enables the use of local type inference in declaring variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="44b2c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="44b2c-105">Syntax</span></span>

```vb
Option Infer { On | Off }
```

## <a name="parts"></a><span data-ttu-id="44b2c-106">부분</span><span class="sxs-lookup"><span data-stu-id="44b2c-106">Parts</span></span>

|<span data-ttu-id="44b2c-107">용어</span><span class="sxs-lookup"><span data-stu-id="44b2c-107">Term</span></span>|<span data-ttu-id="44b2c-108">정의</span><span class="sxs-lookup"><span data-stu-id="44b2c-108">Definition</span></span>|
|---|---|
|`On`|<span data-ttu-id="44b2c-109">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-109">Optional.</span></span> <span data-ttu-id="44b2c-110">지역 형식 유추를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-110">Enables local type inference.</span></span>|
|`Off`|<span data-ttu-id="44b2c-111">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-111">Optional.</span></span> <span data-ttu-id="44b2c-112">지역 형식 유추를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-112">Disables local type inference.</span></span>|

## <a name="remarks"></a><span data-ttu-id="44b2c-113">설명</span><span class="sxs-lookup"><span data-stu-id="44b2c-113">Remarks</span></span>

<span data-ttu-id="44b2c-114">파일에서 `Option Infer`를 설정하려면 파일 맨 위(기타 모든 소스 코드 앞)에 `Option Infer On` 또는 `Option Infer Off`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-114">To set `Option Infer` in a file, type `Option Infer On` or `Option Infer Off` at the top of the file, before any other source code.</span></span> <span data-ttu-id="44b2c-115">파일에서 `Option Infer`에 대해 설정된 값이 IDE 또는 명령줄에 설정된 값과 충돌하는 경우에는 파일의 값이 우선적으로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-115">If the value set for `Option Infer` in a file conflicts with the value set in the IDE or on the command line, the value in the file has precedence.</span></span>

<span data-ttu-id="44b2c-116">`Option Infer`를 `On`으로 설정하면 데이터 형식을 명시적으로 설명하지 않고 로컬 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-116">When you set `Option Infer` to `On`, you can declare local variables without explicitly stating a data type.</span></span> <span data-ttu-id="44b2c-117">컴파일러는 초기화 식의 형식에서 변수의 데이터 형식을 유추합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-117">The compiler infers the data type of a variable from the type of its initialization expression.</span></span>

<span data-ttu-id="44b2c-118">다음 그림에서는 `Option Infer`가 설정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-118">In the following illustration, `Option Infer` is turned on.</span></span> <span data-ttu-id="44b2c-119">`Dim someVar = 2` 선언의 변수는 형식 유추에 의해 정수로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-119">The variable in the declaration `Dim someVar = 2` is declared as an integer by type inference.</span></span>

<span data-ttu-id="44b2c-120">다음 스크린샷은 추론 옵션이 설정 된 경우 IntelliSense를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-120">The following screenshot shows IntelliSense when Option Infer is on:</span></span>

![옵션 추론을 on으로 설정 하는 경우 IntelliSense 보기를 보여 주는 스크린샷](./media/option-infer-statement/option-infer-as-integer-on.png)

<span data-ttu-id="44b2c-122">다음 그림에서는 `Option Infer`가 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-122">In the following illustration, `Option Infer` is turned off.</span></span> <span data-ttu-id="44b2c-123">`Dim someVar = 2` 선언의 변수는 형식 유추에 의해 `Object`로 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-123">The variable in the declaration `Dim someVar = 2` is declared as an `Object` by type inference.</span></span> <span data-ttu-id="44b2c-124">이 예제에서 **Option Strict** 설정은 [컴파일 페이지, 프로젝트 디자이너 (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)에서 **Off** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-124">In this example, the **Option Strict** setting is set to **Off** on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>

<span data-ttu-id="44b2c-125">다음 스크린샷은 추론 옵션이 해제 된 경우 IntelliSense를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-125">The following screenshot shows IntelliSense when Option Infer is off:</span></span>

![옵션 추론을 해제 한 경우 IntelliSense 보기를 보여 주는 스크린샷](./media/option-infer-statement/option-infer-as-object-off.png)

> [!NOTE]
> <span data-ttu-id="44b2c-127">변수가 `Object`로 선언되면 프로그램을 실행하는 동안 런타임 형식이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-127">When a variable is declared as an `Object`, the run-time type can change while the program is running.</span></span> <span data-ttu-id="44b2c-128">Visual Basic는 *boxing* 및 *unboxing* 작업을 수행 하 여와 값 형식 간에 변환 하는 작업을 수행 하므로 `Object` 실행 속도가 느려집니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-128">Visual Basic performs operations called *boxing* and *unboxing* to convert between an `Object` and a value type, which makes execution slower.</span></span> <span data-ttu-id="44b2c-129">Boxing 및 unboxing에 대 한 자세한 내용은 [Visual Basic 언어 사양](~/_vblang/spec/conversions.md#value-type-conversions)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44b2c-129">For information about boxing and unboxing, see the [Visual Basic Language Specification](~/_vblang/spec/conversions.md#value-type-conversions).</span></span>

<span data-ttu-id="44b2c-130">형식 유추는 프로시저 수준에서 적용되며 클래스, 구조체, 모듈 또는 인터페이스의 프로시저 외부에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-130">Type inference applies at the procedure level, and does not apply outside a procedure in a class, structure, module, or interface.</span></span>

<span data-ttu-id="44b2c-131">자세한 내용은 [지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44b2c-131">For additional information, see [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

## <a name="when-an-option-infer-statement-is-not-present"></a><span data-ttu-id="44b2c-132">Option Infer 문이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="44b2c-132">When an Option Infer Statement Is Not Present</span></span>

<span data-ttu-id="44b2c-133">소스 코드에 문이 포함 되어 있지 않으면 `Option Infer` 컴파일 페이지에서 설정 **유추 옵션이** 사용 됩니다 [(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="44b2c-133">If the source code does not contain an `Option Infer` statement, the **Option Infer** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="44b2c-134">명령줄 컴파일러를 사용 하는 경우 [-옵션 추론](../../reference/command-line-compiler/optioninfer.md) 컴파일러 옵션이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-134">If the command-line compiler is used, the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option is used.</span></span>

#### <a name="to-set-option-infer-in-the-ide"></a><span data-ttu-id="44b2c-135">IDE에서 Option Infer를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="44b2c-135">To set Option Infer in the IDE</span></span>

1. <span data-ttu-id="44b2c-136">**솔루션 탐색기** 에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-136">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="44b2c-137">**프로젝트** 메뉴에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-137">On the **Project** menu, click **Properties**.</span></span>

2. <span data-ttu-id="44b2c-138">**컴파일** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-138">Click the **Compile** tab.</span></span>

3. <span data-ttu-id="44b2c-139">**유추 옵션** 상자에서 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-139">Set the value in the **Option infer** box.</span></span>

<span data-ttu-id="44b2c-140">새 프로젝트를 만들 때 **컴파일** 탭의 **유추 설정 옵션이** **VB 기본값** 대화 상자의 **유추 옵션** 으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-140">When you create a new project, the **Option Infer** setting on the **Compile** tab is set to the **Option Infer** setting in the **VB Defaults** dialog box.</span></span> <span data-ttu-id="44b2c-141">**VB 기본값** 대화 상자에 액세스 하려면 **도구** 메뉴에서 **옵션** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-141">To access the **VB Defaults** dialog box, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="44b2c-142">**옵션** 대화 상자에서 **프로젝트 및 솔루션** 을 확장하고 **VB 기본값** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-142">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="44b2c-143">**VB 기본값** 의 초기 기본 설정은 `On` 입니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-143">The initial default setting in **VB Defaults** is `On`.</span></span>

#### <a name="to-set-option-infer-on-the-command-line"></a><span data-ttu-id="44b2c-144">명령줄에서 Option Infer를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="44b2c-144">To set Option Infer on the command line</span></span>

<span data-ttu-id="44b2c-145">**Vbc** 명령에 [-옵션 추론](../../reference/command-line-compiler/optioninfer.md) 컴파일러 옵션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-145">Include the [-optioninfer](../../reference/command-line-compiler/optioninfer.md) compiler option in the **vbc** command.</span></span>

## <a name="default-data-types-and-values"></a><span data-ttu-id="44b2c-146">기본 데이터 형식 및 값</span><span class="sxs-lookup"><span data-stu-id="44b2c-146">Default Data Types and Values</span></span>

<span data-ttu-id="44b2c-147">다음 테이블에는 `Dim` 문에서 데이터 형식과 이니셜라이저를 지정하는 다양한 조합의 결과에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-147">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="44b2c-148">데이터 형식 지정 여부</span><span class="sxs-lookup"><span data-stu-id="44b2c-148">Data type specified?</span></span>|<span data-ttu-id="44b2c-149">이니셜라이저 지정 여부</span><span class="sxs-lookup"><span data-stu-id="44b2c-149">Initializer specified?</span></span>|<span data-ttu-id="44b2c-150">예제</span><span class="sxs-lookup"><span data-stu-id="44b2c-150">Example</span></span>|<span data-ttu-id="44b2c-151">결과</span><span class="sxs-lookup"><span data-stu-id="44b2c-151">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="44b2c-152">아니요</span><span class="sxs-lookup"><span data-stu-id="44b2c-152">No</span></span>|<span data-ttu-id="44b2c-153">아니요</span><span class="sxs-lookup"><span data-stu-id="44b2c-153">No</span></span>|`Dim qty`|<span data-ttu-id="44b2c-154">`Option Strict`가 off(기본값)이면 변수는 `Nothing`으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-154">If `Option Strict` is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="44b2c-155">`Option Strict`가 on이면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-155">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="44b2c-156">아니요</span><span class="sxs-lookup"><span data-stu-id="44b2c-156">No</span></span>|<span data-ttu-id="44b2c-157">예</span><span class="sxs-lookup"><span data-stu-id="44b2c-157">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="44b2c-158">`Option Infer`가 on(기본값)이면 변수가 이니셜라이저의 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-158">If `Option Infer` is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="44b2c-159">[지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44b2c-159">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="44b2c-160">`Option Infer`가 off이고 `Option Strict`고 off이면 변수가 `Object`의 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-160">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="44b2c-161">`Option Infer`가 off이고 `Option Strict`는 on이면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-161">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="44b2c-162">예</span><span class="sxs-lookup"><span data-stu-id="44b2c-162">Yes</span></span>|<span data-ttu-id="44b2c-163">아니요</span><span class="sxs-lookup"><span data-stu-id="44b2c-163">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="44b2c-164">변수는 데이터 형식의 기본값으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-164">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="44b2c-165">자세한 내용은 [Dim 문](dim-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="44b2c-165">For more information, see [Dim Statement](dim-statement.md).</span></span>|
|<span data-ttu-id="44b2c-166">예</span><span class="sxs-lookup"><span data-stu-id="44b2c-166">Yes</span></span>|<span data-ttu-id="44b2c-167">예</span><span class="sxs-lookup"><span data-stu-id="44b2c-167">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="44b2c-168">이니셜라이저의 데이터 형식을 지정한 데이터 형식으로 변환할 수 없으면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-168">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

## <a name="example"></a><span data-ttu-id="44b2c-169">예제</span><span class="sxs-lookup"><span data-stu-id="44b2c-169">Example</span></span>

<span data-ttu-id="44b2c-170">다음 예제에서는 `Option Infer` 문이 지역 형식 유추를 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-170">The following examples demonstrate how the `Option Infer` statement enables local type inference.</span></span>

[!code-vb[VbVbalrTypeInference#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#6)]

## <a name="example"></a><span data-ttu-id="44b2c-171">예제</span><span class="sxs-lookup"><span data-stu-id="44b2c-171">Example</span></span>

<span data-ttu-id="44b2c-172">다음 예제에서는 변수가 `Object`로 식별되는 경우 런타임 형식이 달라질 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="44b2c-172">The following example demonstrates that the run-time type can differ when a variable is identified as an `Object`.</span></span>

[!code-vb[VbVbalrTypeInference#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#11)]

## <a name="see-also"></a><span data-ttu-id="44b2c-173">참고 항목</span><span class="sxs-lookup"><span data-stu-id="44b2c-173">See also</span></span>

- [<span data-ttu-id="44b2c-174">Dim 문</span><span class="sxs-lookup"><span data-stu-id="44b2c-174">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="44b2c-175">지역 형식 유추</span><span class="sxs-lookup"><span data-stu-id="44b2c-175">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="44b2c-176">Option Compare 문</span><span class="sxs-lookup"><span data-stu-id="44b2c-176">Option Compare Statement</span></span>](option-compare-statement.md)
- [<span data-ttu-id="44b2c-177">Option Explicit 문</span><span class="sxs-lookup"><span data-stu-id="44b2c-177">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="44b2c-178">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="44b2c-178">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="44b2c-179">옵션 대화 상자, 프로젝트, Visual Basic 기본값</span><span class="sxs-lookup"><span data-stu-id="44b2c-179">Visual Basic Defaults, Projects, Options Dialog Box</span></span>](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
- [<span data-ttu-id="44b2c-180">-optioninfer</span><span class="sxs-lookup"><span data-stu-id="44b2c-180">-optioninfer</span></span>](../../reference/command-line-compiler/optioninfer.md)
- [<span data-ttu-id="44b2c-181">boxing 및 unboxing</span><span class="sxs-lookup"><span data-stu-id="44b2c-181">Boxing and Unboxing</span></span>](../../../csharp/programming-guide/types/boxing-and-unboxing.md)
