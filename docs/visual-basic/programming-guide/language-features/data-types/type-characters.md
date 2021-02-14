---
description: '자세한 정보: 문자 형식 (Visual Basic)'
title: 형식 문자
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: d1afccb821d2ffb4dfabe3c38e0db4a7f902c164
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454549"
---
# <a name="type-characters-visual-basic"></a><span data-ttu-id="06de8-103">형식 문자 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06de8-103">Type characters (Visual Basic)</span></span>

<span data-ttu-id="06de8-104">선언문에서 데이터 형식을 지정 하는 것 외에도 *형식 문자* 를 사용 하 여 일부 프로그래밍 요소의 데이터 형식을 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-104">In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*.</span></span> <span data-ttu-id="06de8-105">형식 문자는 요소 바로 뒤에와 야 하며 모든 종류의 중간 문자는 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-105">The type character must immediately follow the element, with no intervening characters of any kind.</span></span>

<span data-ttu-id="06de8-106">형식 문자는 요소 이름의 일부가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-106">The type character is not part of the name of the element.</span></span> <span data-ttu-id="06de8-107">형식 문자를 사용 하 여 정의 된 요소는 형식 문자 없이 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-107">An element defined with a type character can be referenced without the type character.</span></span>

## <a name="identifier-type-characters"></a><span data-ttu-id="06de8-108">식별자 형식 문자</span><span class="sxs-lookup"><span data-stu-id="06de8-108">Identifier type characters</span></span>

<span data-ttu-id="06de8-109">Visual Basic는 선언에서 변수나 상수의 데이터 형식을 지정 하는 데 사용할 수 있는 *식별자 형식 문자* 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-109">Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant.</span></span> <span data-ttu-id="06de8-110">다음 표에서는 사용 가능한 식별자 형식 문자를 사용 예제와 함께 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-110">The following table shows the available identifier type characters with examples of usage.</span></span>
  
|<span data-ttu-id="06de8-111">식별자 형식 문자</span><span class="sxs-lookup"><span data-stu-id="06de8-111">Identifier type character</span></span>|<span data-ttu-id="06de8-112">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-112">Data type</span></span>|<span data-ttu-id="06de8-113">예</span><span class="sxs-lookup"><span data-stu-id="06de8-113">Example</span></span>|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 <span data-ttu-id="06de8-114">,,,,,,,, 또는 데이터 형식에 대 한 식별자 형식 문자 `Boolean` `Byte` `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` `UShort` 또는 배열이 나 구조체와 같은 복합 데이터 형식에 대 한 식별자 형식 문자는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-114">No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="06de8-115">경우에 따라 `$` `Left$` 형식의 반환 된 값을 얻기 위해 문자를 대신 Visual Basic 함수에 추가할 수 있습니다 `Left` `String` .</span><span class="sxs-lookup"><span data-stu-id="06de8-115">In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.</span></span>

<span data-ttu-id="06de8-116">모든 경우에서 식별자 형식 문자는 식별자 이름 바로 뒤에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-116">In all cases, the identifier type character must immediately follow the identifier name.</span></span>

## <a name="literal-type-characters"></a><span data-ttu-id="06de8-117">리터럴 형식 문자</span><span class="sxs-lookup"><span data-stu-id="06de8-117">Literal type characters</span></span>

<span data-ttu-id="06de8-118">*리터럴은* 데이터 형식의 특정 값에 대 한 텍스트 표현입니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-118">A *literal* is a textual representation of a particular value of a data type.</span></span>  

### <a name="default-literal-types"></a><span data-ttu-id="06de8-119">기본 리터럴 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-119">Default literal types</span></span>

<span data-ttu-id="06de8-120">코드에 표시 되는 리터럴의 형식은 일반적으로 해당 데이터 형식을 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-120">The form of a literal as it appears in your code ordinarily determines its data type.</span></span> <span data-ttu-id="06de8-121">다음 표에서는 이러한 기본 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-121">The following table shows these default types.</span></span>  
  
|<span data-ttu-id="06de8-122">리터럴의 텍스트 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-122">Textual form of literal</span></span>|<span data-ttu-id="06de8-123">기본 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-123">Default data type</span></span>|<span data-ttu-id="06de8-124">예</span><span class="sxs-lookup"><span data-stu-id="06de8-124">Example</span></span>|  
|-----------------------------|-----------------------|-------------|  
|<span data-ttu-id="06de8-125">숫자, 소수 부분 없음</span><span class="sxs-lookup"><span data-stu-id="06de8-125">Numeric, no fractional part</span></span>|`Integer`|`2147483647`|  
|<span data-ttu-id="06de8-126">숫자, 소수 부분 없음,에 대해 너무 큼 `Integer`</span><span class="sxs-lookup"><span data-stu-id="06de8-126">Numeric, no fractional part, too large for `Integer`</span></span>|`Long`|`2147483648`|  
|<span data-ttu-id="06de8-127">숫자, 소수 부분</span><span class="sxs-lookup"><span data-stu-id="06de8-127">Numeric, fractional part</span></span>|`Double`|`1.2`|  
|<span data-ttu-id="06de8-128">큰따옴표로 묶어서</span><span class="sxs-lookup"><span data-stu-id="06de8-128">Enclosed in double quotation marks</span></span>|`String`|`"A"`|  
|<span data-ttu-id="06de8-129">숫자 기호로 묶여 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-129">Enclosed within number signs</span></span>|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a><span data-ttu-id="06de8-130">강제 리터럴 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-130">Forced literal types</span></span>

<span data-ttu-id="06de8-131">Visual Basic 리터럴 *형식 문자* 집합을 제공 합니다 .이 문자를 사용 하 여 리터럴은 폼이 나타내는 데이터 형식이 아닌 다른 데이터 형식을 사용 하는 것을 강제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-131">Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates.</span></span> <span data-ttu-id="06de8-132">리터럴 끝에 문자를 추가 하 여이 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-132">You do this by appending the character to the end of the literal.</span></span> <span data-ttu-id="06de8-133">다음 표에서는 사용 가능한 리터럴 형식 문자를 사용 예제와 함께 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-133">The following table shows the available literal type characters with examples of usage.</span></span>
  
|<span data-ttu-id="06de8-134">리터럴 형식 문자</span><span class="sxs-lookup"><span data-stu-id="06de8-134">Literal type character</span></span>|<span data-ttu-id="06de8-135">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-135">Data type</span></span>|<span data-ttu-id="06de8-136">예</span><span class="sxs-lookup"><span data-stu-id="06de8-136">Example</span></span>|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

<span data-ttu-id="06de8-137">`Boolean`, `Byte` , `Date` ,, `Object` `SByte` 또는 `String` 데이터 형식 또는 배열 또는 구조체와 같은 복합 데이터 형식에 대 한 리터럴 형식 문자는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-137">No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.</span></span>

<span data-ttu-id="06de8-138">리터럴은 `%` `&` `@` `!` `#` `$` 변수, 상수 및 식으로 식별자 형식 문자 (,,,,,)를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-138">Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions.</span></span> <span data-ttu-id="06de8-139">그러나 리터럴 형식 문자 ( `S` , `I` , `L` ,,, `D` `F` `R` ,)는 `C` 리터럴에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-139">However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.</span></span>

<span data-ttu-id="06de8-140">모든 경우에서 리터럴 형식 문자는 리터럴 값 바로 뒤에와 야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-140">In all cases, the literal type character must immediately follow the literal value.</span></span>

## <a name="hexadecimal-binary-and-octal-literals"></a><span data-ttu-id="06de8-141">16 진수, 이진 및 8 진수 리터럴</span><span class="sxs-lookup"><span data-stu-id="06de8-141">Hexadecimal, binary, and octal literals</span></span>

<span data-ttu-id="06de8-142">컴파일러는 일반적으로 정수 리터럴을 10 진수 (밑수 10) 숫자 시스템에 있는 것으로 해석 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-142">The compiler normally interprets an integer literal to be in the decimal (base 10) number system.</span></span> <span data-ttu-id="06de8-143">접두사를 사용 하 여 접두사를 포함 하는 16 진수 (기 수)로 정수 리터럴을 정의 하 고 접두사를 사용 하 여 `&H` `&B` 8 진수 (밑수 8)로 지정할 수도 있습니다 `&O` .</span><span class="sxs-lookup"><span data-stu-id="06de8-143">You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix.</span></span> <span data-ttu-id="06de8-144">접두사 뒤의 숫자는 숫자 시스템에 적합 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-144">The digits that follow the prefix must be appropriate for the number system.</span></span> <span data-ttu-id="06de8-145">다음 표에서는이에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-145">The following table illustrates this.</span></span>  
  
|<span data-ttu-id="06de8-146">숫자 기준</span><span class="sxs-lookup"><span data-stu-id="06de8-146">Number base</span></span>|<span data-ttu-id="06de8-147">접두사</span><span class="sxs-lookup"><span data-stu-id="06de8-147">Prefix</span></span>|<span data-ttu-id="06de8-148">유효한 숫자 값</span><span class="sxs-lookup"><span data-stu-id="06de8-148">Valid digit values</span></span>|<span data-ttu-id="06de8-149">예</span><span class="sxs-lookup"><span data-stu-id="06de8-149">Example</span></span>|
|-----------------|------------|------------------------|-------------|
|<span data-ttu-id="06de8-150">16진수</span><span class="sxs-lookup"><span data-stu-id="06de8-150">Hexadecimal (base 16)</span></span>|`&H`|<span data-ttu-id="06de8-151">0-9 및 A-f</span><span class="sxs-lookup"><span data-stu-id="06de8-151">0-9 and A-F</span></span>|`&HFFFF`|
|<span data-ttu-id="06de8-152">Binary (밑 2)</span><span class="sxs-lookup"><span data-stu-id="06de8-152">Binary (base 2)</span></span>|`&B`|<span data-ttu-id="06de8-153">0-1</span><span class="sxs-lookup"><span data-stu-id="06de8-153">0-1</span></span>|`&B01111100`|
|<span data-ttu-id="06de8-154">8진수</span><span class="sxs-lookup"><span data-stu-id="06de8-154">Octal (base 8)</span></span>|`&O`|<span data-ttu-id="06de8-155">0-7</span><span class="sxs-lookup"><span data-stu-id="06de8-155">0-7</span></span>|`&O77`|

<span data-ttu-id="06de8-156">Visual Basic 2017부터 밑줄 문자 ( `_` )를 그룹 구분 기호로 사용 하 여 정수 리터럴의 가독성을 향상 시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-156">Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal.</span></span> <span data-ttu-id="06de8-157">다음 예제에서는 문자를 사용 하 여 `_` 이진 리터럴을 8 비트 그룹으로 그룹화 합니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-157">The following example uses the `_` character to group a binary literal into 8-bit groups:</span></span>

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

<span data-ttu-id="06de8-158">리터럴 형식 문자를 사용 하 여 접두 리터럴을 따라갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-158">You can follow a prefixed literal with a literal type character.</span></span> <span data-ttu-id="06de8-159">다음 예에서는 이러한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-159">The following example shows this.</span></span>

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

<span data-ttu-id="06de8-160">앞의 예제에서의 `counter` 10 진수 값은-32768이 고 `flags` 10 진수 값은 + 32768입니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-160">In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.</span></span>

<span data-ttu-id="06de8-161">Visual Basic 15.5부터 `_` 접두사와 16 진수, 이진 또는 8 진수 숫자 사이의 선행 구분 기호로 밑줄 문자 ()를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-161">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="06de8-162">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="06de8-162">For example:</span></span>

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a><span data-ttu-id="06de8-163">참조</span><span class="sxs-lookup"><span data-stu-id="06de8-163">See also</span></span>

- [<span data-ttu-id="06de8-164">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-164">Data Types</span></span>](index.md)
- [<span data-ttu-id="06de8-165">기본 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-165">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="06de8-166">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="06de8-166">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="06de8-167">Visual Basic의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="06de8-167">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="06de8-168">데이터 형식 문제 해결</span><span class="sxs-lookup"><span data-stu-id="06de8-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="06de8-169">변수 선언</span><span class="sxs-lookup"><span data-stu-id="06de8-169">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="06de8-170">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="06de8-170">Data Types</span></span>](../../../language-reference/data-types/index.md)
