---
description: '자세한 정보: Visual Basic의 문자열 기본 사항'
title: 문자열 기본 사항
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 25d76ee177e5b3eaaa8aa6b2b1b1787dc29095a1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424361"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="3938f-103">Visual Basic의 문자열 기본</span><span class="sxs-lookup"><span data-stu-id="3938f-103">String Basics in Visual Basic</span></span>

<span data-ttu-id="3938f-104">`String` 데이터 형식은 일련의 문자를 나타내며, 각각은 차례로 `Char` 데이터 형식의 인스턴스를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-104">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="3938f-105">이 항목에서는 Visual Basic에 있는 문자열의 기본 개념을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-105">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="3938f-106">문자열 변수</span><span class="sxs-lookup"><span data-stu-id="3938f-106">String Variables</span></span>  

 <span data-ttu-id="3938f-107">문자열의 인스턴스에 일련의 문자를 나타내는 리터럴 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-107">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="3938f-108">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-108">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="3938f-109">또한 `String` 변수는 문자열로 계산되는 모든 식을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-109">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="3938f-110">예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-110">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="3938f-111">`String` 변수에 할당되는 모든 리터럴은 큰따옴표("")로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-111">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="3938f-112">즉, 문자열 내의 큰따옴표는 큰따옴표로 나타낼 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-112">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="3938f-113">예를 들어 다음 코드는 컴파일러 오류를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-113">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="3938f-114">이 코드에서는 컴파일러가 두번째 큰따옴표 다음 문자열을 종료하고 문자열의 나머지 부분이 코드로 해석되기 때문에 오류가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-114">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="3938f-115">이 문제를 해결 하기 위해 Visual Basic 문자열 리터럴의 두 따옴표를 문자열에서 하나의 따옴표로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-115">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="3938f-116">다음 예제에서는 문자열에 큰따옴표를 포함하는 올바른 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-116">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="3938f-117">이전 예제에서 `Look`이라는 단어 앞에 오는 두 개의 큰따옴표가 문자열에서 하나의 큰따옴표가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-117">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="3938f-118">줄의 끝에 있는 큰따옴표 세 개는 문자열의 큰따옴표 한 개와 문자열 종료 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-118">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="3938f-119">문자열 리터럴에 여러 줄이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-119">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="3938f-120">결과 문자열에는 문자열 리터럴(vbcr, vbcrlf 등)에서 사용한 줄 바꿈 시퀀스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-120">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="3938f-121">이전 해결 방법은 더 이상 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-121">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="3938f-122">문자열의 문자</span><span class="sxs-lookup"><span data-stu-id="3938f-122">Characters in Strings</span></span>  

 <span data-ttu-id="3938f-123">문자열은 일련은 `Char` 값으로 간주되며 `String` 형식에는 배열에서 허용하는 조작과 유사한 많은 조작을 문자열에서 수행할 수 있는 기본 제공 함수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-123">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="3938f-124">.NET Framework의 모든 배열과 마찬가지로 0부터 시작 하는 배열입니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-124">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="3938f-125">문자열에서 나타나는 위치를 기준으로 문자에 액세스하는 방법을 제공하는 `Chars` 속성을 통해 문자열의 특정 문자를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-125">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="3938f-126">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-126">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="3938f-127">위 예제에서 문자열의 `Chars` 속성은 문자열에서 네 번째 문자인 `D`를 반환하고 `myChar`에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-127">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="3938f-128">`Length` 속성을 통해 특정 문자열의 길이를 가져올 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-128">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="3938f-129">문자열에서 여러 배열 형식 조작을 수행해야 하는 경우 문자열의 `ToCharArray` 함수를 사용하여 `Char` 인스턴스의 배열로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-129">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="3938f-130">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-130">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="3938f-131">이제 변수 `myArray`에 `Char` 값의 배열이 포함되며, 각각은 `myString`의 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-131">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="3938f-132">문자열의 불변성</span><span class="sxs-lookup"><span data-stu-id="3938f-132">The Immutability of Strings</span></span>  

 <span data-ttu-id="3938f-133">문자열은 *변경할* 수 없습니다. 즉, 생성 된 후에는 해당 값을 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-133">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="3938f-134">그러나 둘 이상의 값을 문자열 변수에 할당할 수는 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-134">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="3938f-135">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3938f-135">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="3938f-136">여기에서는 문자열 변수를 만들고 값을 지정한 다음 해당 값을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-136">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="3938f-137">좀더 구체적으로 첫 번째 줄에서는 `String` 형식의 인스턴스를 만들고 `This string is immutable`값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-137">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="3938f-138">예제의 두 번째 줄에서는 새 인스턴스를 만들고 `Or is it?` 값을 지정합니다. 문자열 변수는 첫 번째 인스턴스에 대한 참조를 삭제하고 새 인스턴스에 대한 참조를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-138">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="3938f-139">다른 내장 데이터 형식과 달리 `String`은 참조 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-139">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="3938f-140">참조 형식의 변수가 인수로 함수 또는 서브루틴에 전달되면 데이터가 저장되는 메모리 주소에 대한 참조가 문자열의 실제 값 대신 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-140">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="3938f-141">따라서 이전 예제에서 변수의 이름은 동일하게 유지되지만 새 값을 보유하는 `String` 클래스의 다른 새 인스턴스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3938f-141">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3938f-142">추가 정보</span><span class="sxs-lookup"><span data-stu-id="3938f-142">See also</span></span>

- [<span data-ttu-id="3938f-143">Visual Basic의 문자열 소개</span><span class="sxs-lookup"><span data-stu-id="3938f-143">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
- [<span data-ttu-id="3938f-144">문자열 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3938f-144">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="3938f-145">Char 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3938f-145">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="3938f-146">기본적인 문자열 작업</span><span class="sxs-lookup"><span data-stu-id="3938f-146">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
