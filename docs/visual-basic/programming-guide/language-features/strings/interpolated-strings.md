---
description: '다음에 대 한 자세한 정보: 보간된 문자열 (Visual Basic 참조)'
title: 보간된 문자열
ms.date: 10/31/2017
ms.openlocfilehash: c054401070079bdf85181619ef43c246feea5e18
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429664"
---
# <a name="interpolated-strings-visual-basic-reference"></a><span data-ttu-id="b6599-103">보간된 문자열 (Visual Basic 참조)</span><span class="sxs-lookup"><span data-stu-id="b6599-103">Interpolated Strings (Visual Basic Reference)</span></span>

<span data-ttu-id="b6599-104">문자열을 생성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-104">Used to construct strings.</span></span>  <span data-ttu-id="b6599-105">보간된 문자열은 *보간된 식* 이 포함된 템플릿 문자열과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-105">An interpolated string looks like a template string that contains *interpolated expressions*.</span></span>  <span data-ttu-id="b6599-106">보간된 문자열은 포함하는 보간된 식을 해당 문자열 표현으로 바꾸는 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-106">An interpolated string returns a string that replaces the interpolated expressions that it contains with their string representations.</span></span> <span data-ttu-id="b6599-107">이 기능은 Visual Basic 14 이상 버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-107">This feature is available in Visual Basic 14 and later versions.</span></span>

<span data-ttu-id="b6599-108">보간된 문자열의 인수는 [복합 형식 문자열](../../../../standard/base-types/composite-formatting.md#composite-format-string)보다 더 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-108">The arguments of an interpolated string are easier to understand than a [composite format string](../../../../standard/base-types/composite-formatting.md#composite-format-string).</span></span>  <span data-ttu-id="b6599-109">예를 들어 보간된 문자열</span><span class="sxs-lookup"><span data-stu-id="b6599-109">For example, the interpolated string</span></span>

```vb
Console.WriteLine($"Name = {name}, hours = {hours:hh}")
```

<span data-ttu-id="b6599-110">에는 두 개의 보간된 식 '{name}' 및 '{hours:hh}'가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-110">contains two interpolated expressions, '{name}' and '{hours:hh}'.</span></span> <span data-ttu-id="b6599-111">동등한 복합 형식 문자열은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-111">The equivalent composite format string is:</span></span>

```vb
Console.WriteLine("Name = {0}, hours = {1:hh}", name, hours)
```

<span data-ttu-id="b6599-112">보간된 문자열의 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-112">The structure of an interpolated string is:</span></span>

```vb
$"<text> {<interpolated-expression> [,<field-width>] [:<format-string>] } <text> ..."
```

<span data-ttu-id="b6599-113">여기서</span><span class="sxs-lookup"><span data-stu-id="b6599-113">where:</span></span>

- <span data-ttu-id="b6599-114">*필드 너비* 는 필드의 문자 수를 나타내는 부호 있는 정수입니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-114">*field-width* is a signed integer that indicates the number of characters in the field.</span></span> <span data-ttu-id="b6599-115">양수이면 필드가 오른쪽에 맞춰지고, 음수이면 왼쪽에 맞춰집니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-115">If it is positive, the field is right-aligned; if negative, left-aligned.</span></span>

- <span data-ttu-id="b6599-116">*형식 문자열* 은 형식을 지정할 개체 형식에 적합한 형식 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-116">*format-string* is a format string appropriate for the type of object being formatted.</span></span> <span data-ttu-id="b6599-117">예를 들어 값의 경우 <xref:System.DateTime> "d" 또는 "d"와 같은 [표준 날짜 및 시간 형식 문자열일](../../../../standard/base-types/standard-date-and-time-format-strings.md) 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-117">For example, for a <xref:System.DateTime> value, it could be a [standard date and time format string](../../../../standard/base-types/standard-date-and-time-format-strings.md) such as "D" or "d".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b6599-118">문자열을 시작하는 `$` 및 `"` 사이에 공백이 없어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-118">You cannot have any white space between the `$` and the `"` that starts the string.</span></span> <span data-ttu-id="b6599-119">이렇게 하면 컴파일러 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-119">Doing so causes a compiler error.</span></span>

<span data-ttu-id="b6599-120">문자열 리터럴을 사용할 수 있는 곳이면 어디든지 보간된 문자열을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-120">You can use an interpolated string anywhere you can use a string literal.</span></span>  <span data-ttu-id="b6599-121">보간된 문자열을 포함하는 코드가 실행될 때마다 보간된 문자열이 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-121">The interpolated string is evaluated each time the code with the interpolated string executes.</span></span> <span data-ttu-id="b6599-122">이렇게 하면 보간된 문자열의 정의 및 평가를 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-122">This allows you to separate the definition and evaluation of an interpolated string.</span></span>

<span data-ttu-id="b6599-123">보간된 문자열에 중괄호("{" 또는 "}")를 포함하려면 두 개의 중괄호 "{{" 또는 "}}"를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-123">To include a curly brace ("{" or "}") in an interpolated string, use two curly braces, "{{" or "}}".</span></span>  <span data-ttu-id="b6599-124">자세한 내용은 암시적 변환 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b6599-124">See the Implicit Conversions section for more details.</span></span>

<span data-ttu-id="b6599-125">큰따옴표("), 콜론(:), 쉼표(,) 등 특별한 의미를 가진 다른 문자가 보간된 문자열에 포함된 경우 리터럴 텍스트에 발생하면 이스케이프해야 하거나, 보간된 식에 포함된 언어 요소이면 괄호로 구분된 식에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-125">If the interpolated string contains other characters with special meaning in an interpolated string, such as the quotation mark ("), colon (:), or comma (,), they should be escaped if they occur in literal text, or they should be included in an expression delimited by parentheses if they are language elements included in an interpolated expression.</span></span> <span data-ttu-id="b6599-126">다음 예에서는 따옴표를 이스케이프 하 여 결과 문자열에 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-126">The following example escapes quotation marks to include them in the result string:</span></span>

[!code-vb[interpolated-strings](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings4.vb)]

## <a name="implicit-conversions"></a><span data-ttu-id="b6599-127">암시적 변환</span><span class="sxs-lookup"><span data-stu-id="b6599-127">Implicit Conversions</span></span>

<span data-ttu-id="b6599-128">보간된 문자열에서 다음과 같은 세 가지 암시적 형식 변환을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-128">There are three implicit type conversions from an interpolated string:</span></span>

1. <span data-ttu-id="b6599-129">보간된 문자열을 <xref:System.String>으로 변환.</span><span class="sxs-lookup"><span data-stu-id="b6599-129">Conversion of an interpolated string to a <xref:System.String>.</span></span> <span data-ttu-id="b6599-130">다음 예제에서는 보간된 문자열 식이 해당 문자열 표현으로 바뀐 문자열을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-130">The following example returns a string whose interpolated string expressions have been replaced with their string representations.</span></span> <span data-ttu-id="b6599-131">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-131">For example:</span></span>

   [!code-vb[interpolated-strings1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings1.vb)]

   <span data-ttu-id="b6599-132">이는 문자열 해석의 최종 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-132">This is the final result of a string interpretation.</span></span> <span data-ttu-id="b6599-133">나타나는 모든 이중 중괄호("{{" 및 "}}")가 단일 중괄호로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-133">All occurrences of double curly braces ("{{" and "}}") are converted to a single curly brace.</span></span>

2. <span data-ttu-id="b6599-134">보간된 문자열을 <xref:System.IFormattable> 변수로 변환. 이 변수를 사용하면 단일 <xref:System.IFormattable> 인스턴스의 문화권별 콘텐츠로 여러 결과 문자열을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-134">Conversion of an interpolated string to an <xref:System.IFormattable> variable that allows you create multiple result strings with culture-specific content from a single <xref:System.IFormattable> instance.</span></span> <span data-ttu-id="b6599-135">이 옵션은 개별 문화권의 올바른 숫자 및 날짜 형식 등을 포함하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-135">This is useful for including such things as the correct numeric and date formats for individual cultures.</span></span>  <span data-ttu-id="b6599-136">모든 이중 중괄호("{{" 및 "}}")는 <xref:System.Object.ToString> 메서드를 명시적 또는 암시적으로 호출하여 문자열을 형식을 지정할 때까지 이중 중괄호로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-136">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format the string by explicitly or implicitly calling the <xref:System.Object.ToString> method.</span></span>  <span data-ttu-id="b6599-137">포함 된 보간 식은 모두, 등으로 변환 됩니다 {0} {1} .</span><span class="sxs-lookup"><span data-stu-id="b6599-137">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   <span data-ttu-id="b6599-138">다음 예제에서는 리플렉션을 사용하여 보간된 문자열에서 생성된 <xref:System.IFormattable> 변수의 필드 및 속성 값뿐 아니라 멤버를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-138">The following example uses reflection to display the members as well as the field and property values of an <xref:System.IFormattable> variable that is created from an interpolated string.</span></span> <span data-ttu-id="b6599-139">또한 <xref:System.IFormattable> 변수를 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 메서드에 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-139">It also passes the <xref:System.IFormattable> variable to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method.</span></span>

   [!code-vb[interpolated-strings2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings2.vb)]

   <span data-ttu-id="b6599-140">보간된 문자열은 리플렉션을 통해서만 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-140">Note that the interpolated string can be inspected only by using reflection.</span></span> <span data-ttu-id="b6599-141"><xref:System.Console.WriteLine(System.String)> 등의 문자열 형식 지정 메서드에 전달되는 경우 해당 형식 항목이 확인되고 결과 문자열이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-141">If it is passed to a string formatting method, such as <xref:System.Console.WriteLine(System.String)>, its format items are resolved and the result string returned.</span></span>

3. <span data-ttu-id="b6599-142">보간된 문자열을 <xref:System.FormattableString> 복합 서식 문자열을 나타내는 변수로 변환</span><span class="sxs-lookup"><span data-stu-id="b6599-142">Conversion of an interpolated string to a <xref:System.FormattableString> variable that represents a composite format string.</span></span> <span data-ttu-id="b6599-143">예를 들어 복합 형식 문자열 및 복합 형식 문자열이 결과 문자열로 렌더링되는 방식을 검사하면 쿼리를 빌드하는 경우 삽입 공격으로부터 보호하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-143">Inspecting the composite format string and how it renders as a result string might, for example, help you protect against an injection attack if you were building a query.</span></span> <span data-ttu-id="b6599-144">에는 <xref:System.FormattableString> 다음도 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-144">A <xref:System.FormattableString> also includes:</span></span>

      - <span data-ttu-id="b6599-145"><xref:System.Globalization.CultureInfo.CurrentCulture>에 대한 결과 문자열을 생성하는 <xref:System.FormattableString.ToString> 오버로드.</span><span class="sxs-lookup"><span data-stu-id="b6599-145">A <xref:System.FormattableString.ToString> overload that produces a result string for the <xref:System.Globalization.CultureInfo.CurrentCulture>.</span></span>

      - <span data-ttu-id="b6599-146"><xref:System.FormattableString.Invariant%2A>에 대 한 문자열을 생성 하는 메서드입니다 <xref:System.Globalization.CultureInfo.InvariantCulture> .</span><span class="sxs-lookup"><span data-stu-id="b6599-146">A <xref:System.FormattableString.Invariant%2A> method that produces a string for the <xref:System.Globalization.CultureInfo.InvariantCulture>.</span></span>

      - <span data-ttu-id="b6599-147">지정된 문화에 대한 결과 문자열을 생성하는 <xref:System.FormattableString.ToString(System.IFormatProvider)> 메서드.</span><span class="sxs-lookup"><span data-stu-id="b6599-147">A <xref:System.FormattableString.ToString(System.IFormatProvider)> method that produces a result string for a specified culture.</span></span>

    <span data-ttu-id="b6599-148">모든 이중 중괄호 ("{{" 및 "}}")는 형식을 지정할 때까지 이중 중괄호로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b6599-148">All occurrences of double curly braces ("{{" and "}}") remain as double curly braces until you format.</span></span>  <span data-ttu-id="b6599-149">포함 된 보간 식은 모두, 등으로 변환 됩니다 {0} {1} .</span><span class="sxs-lookup"><span data-stu-id="b6599-149">All contained interpolation expressions are converted to {0}, {1}, and so on.</span></span>

   [!code-vb[interpolated-strings3](../../../../../samples/snippets/visualbasic/programming-guide/language-features/strings/interpolated-strings3.vb)]

## <a name="see-also"></a><span data-ttu-id="b6599-150">참조</span><span class="sxs-lookup"><span data-stu-id="b6599-150">See also</span></span>

- <xref:System.IFormattable?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- [<span data-ttu-id="b6599-151">Visual Basic 언어 참조</span><span class="sxs-lookup"><span data-stu-id="b6599-151">Visual Basic Language Reference</span></span>](index.md)
