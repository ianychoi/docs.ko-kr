---
description: '자세히 알아보기: Option Compare 문'
title: Option Compare 문
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: fba8b207c0077f95540485d79311b47f1b8c209c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741668"
---
# <a name="option-compare-statement"></a><span data-ttu-id="eeee8-103">Option Compare 문</span><span class="sxs-lookup"><span data-stu-id="eeee8-103">Option Compare Statement</span></span>

<span data-ttu-id="eeee8-104">문자열 데이터를 비교할 때 사용할 기본 비교 방법을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-104">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eeee8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eeee8-105">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="eeee8-106">부분</span><span class="sxs-lookup"><span data-stu-id="eeee8-106">Parts</span></span>  
  
|<span data-ttu-id="eeee8-107">용어</span><span class="sxs-lookup"><span data-stu-id="eeee8-107">Term</span></span>|<span data-ttu-id="eeee8-108">정의</span><span class="sxs-lookup"><span data-stu-id="eeee8-108">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="eeee8-109">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-109">Optional.</span></span> <span data-ttu-id="eeee8-110">문자의 내부 이진 표현에서 파생된 정렬 순서에 따라 문자열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-110">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="eeee8-111">이 유형의 비교는 문자열에 텍스트로 해석할 수 없는 문자가 포함될 수 있는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-111">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="eeee8-112">이 경우 대/소문자 미구분 등의 영문자 동일 여부에 따라 비교 결과가 달라지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-112">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="eeee8-113">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-113">Optional.</span></span> <span data-ttu-id="eeee8-114">시스템의 로캘에 따라 결정되는 대/소문자 미구분 텍스트 정렬 순서에 따라 문자열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-114">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="eeee8-115">문자열에 텍스트 문자만 포함되며 대/소문자 미구분, 밀접하게 관련된 문자 등의 영문자 동일 여부를 고려하여 이러한 문자를 비교하려는 경우에는 이 유형의 비교가 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-115">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="eeee8-116">예를 들어 `A`와 `a`를 같은 문자로 간주하고 `Ä` 및 `ä`가 `B` 및 `b` 앞에 온다고 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-116">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeee8-117">설명</span><span class="sxs-lookup"><span data-stu-id="eeee8-117">Remarks</span></span>  

 <span data-ttu-id="eeee8-118">`Option Compare` 문은 사용하는 경우 파일에서 다른 소스 코드 문 앞에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-118">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="eeee8-119">`Option Compare` 문은 문자열 비교 방법(`Binary` 또는 `Text`)을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-119">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="eeee8-120">기본 텍스트 비교 방법은 `Binary`입니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-120">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="eeee8-121">`Binary` 비교에서는 각 문자열 내 각 문자의 숫자 유니코드 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-121">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="eeee8-122">`Text` 비교에서는 현재 문화권의 어휘 의미에 따라 각 유니코드 문자를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-122">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="eeee8-123">Microsoft windows에서 정렬 순서는 코드 페이지에 의해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-123">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="eeee8-124">자세한 내용은 [코드 페이지](/cpp/c-runtime-library/code-pages) 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="eeee8-124">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="eeee8-125">다음 예제에서는 `Option Compare Binary`를 사용하여 영어/유럽어 코드 페이지(ANSI 1252)의 문자를 정렬합니다. 그러면 일반적인 이진 정렬 순서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-125">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="eeee8-126">`Option Compare Text`를 사용하여 같은 코드 페이지의 같은 문자를 정렬하면 다음 텍스트 정렬 순서가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-126">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="eeee8-127">Option Compare 문이 없는 경우</span><span class="sxs-lookup"><span data-stu-id="eeee8-127">When an Option Compare Statement Is Not Present</span></span>  

 <span data-ttu-id="eeee8-128">소스 코드에 문이 포함 되어 있지 않은 경우 `Option Compare` 컴파일 페이지에서 **Option Compare** 설정이 사용 됩니다 [(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="eeee8-128">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="eeee8-129">명령줄 컴파일러를 사용 하는 경우 [-옵션 비교](../../reference/command-line-compiler/optioncompare.md) 컴파일러 옵션에 지정 된 설정이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-129">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="eeee8-130">IDE에서 Option Compare를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="eeee8-130">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="eeee8-131">**솔루션 탐색기** 에서 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-131">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="eeee8-132">**프로젝트** 메뉴에서 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-132">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="eeee8-133">**컴파일** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-133">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="eeee8-134">**옵션 비교** 상자에서 값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="eeee8-135">프로젝트를 만들 때 **컴파일** 탭의 **옵션 비교** 설정이 **옵션** 대화 상자의 **옵션 비교** 설정으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="eeee8-136">이 설정을 변경 하려면 **도구** 메뉴에서 **옵션** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="eeee8-137">**옵션** 대화 상자에서 **프로젝트 및 솔루션** 을 확장하고 **VB 기본값** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="eeee8-138">**VB 기본값** 의 초기 기본 설정은 **Binary** 입니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="eeee8-139">명령줄에서 Option Compare를 설정하려면</span><span class="sxs-lookup"><span data-stu-id="eeee8-139">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="eeee8-140">**Vbc** 명령에 [-옵션 compare](../../reference/command-line-compiler/optioncompare.md) 컴파일러 옵션을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-140">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eeee8-141">예제</span><span class="sxs-lookup"><span data-stu-id="eeee8-141">Example</span></span>  

 <span data-ttu-id="eeee8-142">다음 예제에서는 `Option Compare` 문을 사용하여 이진 비교를 기본 문자열 비교 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="eeee8-143">이 코드를 사용하려면 `Option Compare Binary` 문의 주석 처리를 제거하여 소스 파일 맨 위에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="eeee8-144">예제</span><span class="sxs-lookup"><span data-stu-id="eeee8-144">Example</span></span>  

 <span data-ttu-id="eeee8-145">다음 예제에서는 `Option Compare` 문을 사용하여 대/소문자 미구분 텍스트 정렬 순서를 기본 문자열 비교 방법으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-145">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="eeee8-146">이 코드를 사용하려면 `Option Compare Text` 문의 주석 처리를 제거하여 소스 파일 맨 위에 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="eeee8-146">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="eeee8-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="eeee8-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="eeee8-148">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="eeee8-148">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="eeee8-149">비교 연산자</span><span class="sxs-lookup"><span data-stu-id="eeee8-149">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="eeee8-150">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eeee8-150">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="eeee8-151">Like 연산자</span><span class="sxs-lookup"><span data-stu-id="eeee8-151">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="eeee8-152">문자열 함수</span><span class="sxs-lookup"><span data-stu-id="eeee8-152">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="eeee8-153">Option Explicit 문</span><span class="sxs-lookup"><span data-stu-id="eeee8-153">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="eeee8-154">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="eeee8-154">Option Strict Statement</span></span>](option-strict-statement.md)
