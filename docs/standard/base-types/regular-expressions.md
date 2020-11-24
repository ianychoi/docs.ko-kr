---
title: .NET 정규식
description: .NET에서 정규식을 사용하여 특정 문자 패턴을 찾고, 텍스트의 유효성을 검사하고, 텍스트 부분 문자열로 작업하고, 추출된 문자열을 컬렉션에 추가합니다.
ms.date: 06/30/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET], about regular expressions
- regular expressions [.NET]
- .NET regular expressions, about
- characters [.NET], regular expressions
- parsing text with regular expressions, overview
- .NET regular expressions
- strings [.NET], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
ms.openlocfilehash: 6fa791005aa9fa9956a3169f8f9ddecfa201bcda
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831340"
---
# <a name="net-regular-expressions"></a><span data-ttu-id="a5653-103">.NET 정규식</span><span class="sxs-lookup"><span data-stu-id="a5653-103">.NET regular expressions</span></span>

<span data-ttu-id="a5653-104">정규식은 텍스트를 처리하는 강력하고 유연하며 효율적인 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-104">Regular expressions provide a powerful, flexible, and efficient method for processing text.</span></span> <span data-ttu-id="a5653-105">정규식의 광범위한 패턴 일치 표기법을 사용하면 많은 양의 텍스트를 빠르게 구문 분석하여 다음을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-105">The extensive pattern-matching notation of regular expressions enables you to quickly parse large amounts of text to:</span></span>

- <span data-ttu-id="a5653-106">특정 문자 패턴을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-106">Find specific character patterns.</span></span>
- <span data-ttu-id="a5653-107">텍스트의 유효성을 검사하여 미리 정의된 패턴(예: 전자 메일 주소)과 일치하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-107">Validate text to ensure that it matches a predefined pattern (such as an email address).</span></span>
- <span data-ttu-id="a5653-108">텍스트 하위 문자열을 추출, 편집, 바꾸기 또는 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-108">Extract, edit, replace, or delete text substrings.</span></span>
- <span data-ttu-id="a5653-109">보고서를 생성하기 위해 추출된 문자열을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-109">Add extracted strings to a collection in order to generate a report.</span></span>

<span data-ttu-id="a5653-110">문자열을 처리하거나 텍스트의 큰 블록을 구문 분석하는 많은 애플리케이션의 경우 정규식은 필수적인 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-110">For many applications that deal with strings or that parse large blocks of text, regular expressions are an indispensable tool.</span></span>  
  
## <a name="how-regular-expressions-work"></a><span data-ttu-id="a5653-111">정규식의 작동 방식</span><span class="sxs-lookup"><span data-stu-id="a5653-111">How regular expressions work</span></span>

 <span data-ttu-id="a5653-112">정규식을 사용하여 텍스트를 처리하는 중심에는 .NET에서 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> 개체로 표현되는 정규식 엔진이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-112">The centerpiece of text processing with regular expressions is the regular expression engine, which is represented by the <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> object in .NET.</span></span> <span data-ttu-id="a5653-113">정규식을 사용하여 텍스트를 처리하려면 최소한 정규식 엔진이 다음과 같은 두 가지 정보 항목과 함께 제공되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-113">At a minimum, processing text using regular expressions requires that the regular expression engine be provided with the following two items of information:</span></span>  
  
- <span data-ttu-id="a5653-114">텍스트에서 식별할 정규식 패턴</span><span class="sxs-lookup"><span data-stu-id="a5653-114">The regular expression pattern to identify in the text.</span></span>  
  
     <span data-ttu-id="a5653-115">.NET에서 정규식 패턴은 특수 구문 또는 언어로 정의되며 Perl 5 정규식과 호환되고 오른쪽에서 왼쪽으로 일치와 같은 몇 가지 기능을 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-115">In .NET, regular expression patterns are defined by a special syntax or language, which is compatible with Perl 5 regular expressions and adds some additional features such as right-to-left matching.</span></span> <span data-ttu-id="a5653-116">자세한 내용은 [정규식 언어 - 빠른 참조](regular-expression-language-quick-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5653-116">For more information, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md).</span></span>  
  
- <span data-ttu-id="a5653-117">정규식 패턴에 대해 구문 분석할 텍스트</span><span class="sxs-lookup"><span data-stu-id="a5653-117">The text to parse for the regular expression pattern.</span></span>  
  
<span data-ttu-id="a5653-118"><xref:System.Text.RegularExpressions.Regex> 클래스의 메서드를 사용하여 다음과 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-118">The methods of the <xref:System.Text.RegularExpressions.Regex> class let you perform the following operations:</span></span>  
  
- <span data-ttu-id="a5653-119"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> 메서드를 호출하여 입력 텍스트에서 정규식 패턴이 발생하는지를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-119">Determine whether the regular expression pattern occurs in the input text by calling the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5653-120"><xref:System.Text.RegularExpressions.Regex.IsMatch%2A> 메서드를 사용하여 텍스트의 유효성을 검사하는 예제는 [방법: 문자열이 올바른 이메일 형식인지 확인](how-to-verify-that-strings-are-in-valid-email-format.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5653-120">For an example that uses the <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> method for validating text, see [How to: Verify that Strings Are in Valid Email Format](how-to-verify-that-strings-are-in-valid-email-format.md).</span></span>  
  
- <span data-ttu-id="a5653-121"><xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> 또는 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 메서드를 호출하여 정규식 패턴과 일치하는 텍스트를 하나 또는 모두 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-121">Retrieve one or all occurrences of text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> or <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5653-122">전자 메서드는 일치하는 텍스트에 대한 정보를 제공하는 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-122">The former method returns a <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object that provides information about the matching text.</span></span> <span data-ttu-id="a5653-123">후자는 구문 분석된 텍스트에서 찾은 각 일치 항목에 대한 하나의 <xref:System.Text.RegularExpressions.MatchCollection> 개체를 포함하는 <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> 개체를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-123">The latter returns a <xref:System.Text.RegularExpressions.MatchCollection> object that contains one <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> object for each match found in the parsed text.</span></span>  
  
- <span data-ttu-id="a5653-124"><xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 메서드를 호출하여 정규식 패턴과 일치하는 텍스트를 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-124">Replace text that matches the regular expression pattern by calling the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="a5653-125"><xref:System.Text.RegularExpressions.Regex.Replace%2A> 메서드를 사용하여 날짜 형식을 변경하고 문자열에서 잘못된 문자를 제거하는 예제는 [방법: 문자열에서 유효하지 않은 문자 제거](how-to-strip-invalid-characters-from-a-string.md) 및 [예제: 날짜 형식 변경](regular-expression-example-changing-date-formats.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5653-125">For examples that use the <xref:System.Text.RegularExpressions.Regex.Replace%2A> method to change date formats and remove invalid characters from a string, see [How to: Strip Invalid Characters from a String](how-to-strip-invalid-characters-from-a-string.md) and [Example: Changing Date Formats](regular-expression-example-changing-date-formats.md).</span></span>  
  
<span data-ttu-id="a5653-126">정규식 개체 모델의 개요는 [정규식 개체 모델](the-regular-expression-object-model.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5653-126">For an overview of the regular expression object model, see [The Regular Expression Object Model](the-regular-expression-object-model.md).</span></span>  
  
<span data-ttu-id="a5653-127">정규식 언어에 대한 자세한 내용은 [정규식 언어 - 빠른 참조](regular-expression-language-quick-reference.md)를 참조하거나, 다음 브로슈어 중 하나를 다운로드하여 인쇄하세요.</span><span class="sxs-lookup"><span data-stu-id="a5653-127">For more information about the regular expression language, see [Regular Expression Language - Quick Reference](regular-expression-language-quick-reference.md) or download and print one of these brochures:</span></span>  
  
- [<span data-ttu-id="a5653-128">Word(.docx) 형식의 빠른 참조</span><span class="sxs-lookup"><span data-stu-id="a5653-128">Quick Reference in Word (.docx) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="a5653-129">PDF(.pdf) 형식의 빠른 참조</span><span class="sxs-lookup"><span data-stu-id="a5653-129">Quick Reference in PDF (.pdf) format</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a><span data-ttu-id="a5653-130">정규식 예제</span><span class="sxs-lookup"><span data-stu-id="a5653-130">Regular expression examples</span></span>

<span data-ttu-id="a5653-131"><xref:System.String> 클래스에는 큰 문자열에서 리터럴 문자열을 찾을 때 사용할 수 있는 다양한 문자열 검색 및 바꾸기 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-131">The <xref:System.String> class includes a number of string search and replacement methods that you can use when you want to locate literal strings in a larger string.</span></span> <span data-ttu-id="a5653-132">정규식은 다음 예제에서 보여 주는 것처럼 큰 문자열에서 여러 부분 문자열 중 하나를 찾거나 문자열에서 패턴을 식별할 때 가장 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-132">Regular expressions are most useful either when you want to locate one of several substrings in a larger string, or when you want to identify patterns in a string, as the following examples illustrate.</span></span>

[!INCLUDE [regex](../../../includes/regex.md)]

> [!TIP]
> <span data-ttu-id="a5653-133"><xref:System.Web.RegularExpressions> 네임스페이스에는 HTML, XML 및 ASP.NET 문서의 문자열을 구문 분석하기 위해 미리 정의된 정규식 패턴을 구현하는 여러 정규식 개체가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-133">The <xref:System.Web.RegularExpressions> namespace contains a number of regular expression objects that implement predefined regular expression patterns for parsing strings from HTML, XML, and ASP.NET documents.</span></span> <span data-ttu-id="a5653-134">예를 들어 <xref:System.Web.RegularExpressions.TagRegex> 클래스는 문자열의 시작 태그를 식별하고, <xref:System.Web.RegularExpressions.CommentRegex> 클래스는 문자열의 ASP.NET 주석을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-134">For example, the <xref:System.Web.RegularExpressions.TagRegex> class identifies start tags in a string and the <xref:System.Web.RegularExpressions.CommentRegex> class identifies ASP.NET comments in a string.</span></span>

### <a name="example-1-replace-substrings"></a><span data-ttu-id="a5653-135">예제 1: 하위 문자열 바꾸기</span><span class="sxs-lookup"><span data-stu-id="a5653-135">Example 1: Replace substrings</span></span>  

 <span data-ttu-id="a5653-136">메일 그룹에 경우에 따라 호칭(Mr., Mrs., Miss 또는 Ms.)이 이름 및 성과 함께 포함되어 있는 이름이 들어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-136">Assume that a mailing list contains names that sometimes include a title (Mr., Mrs., Miss, or Ms.) along with a first and last name.</span></span> <span data-ttu-id="a5653-137">메일 그룹에서 봉투 레이블을 생성할 때 호칭을 포함하지 않으려는 경우 다음 예제에서 보여 주는 것처럼 정규식을 사용하여 호칭을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-137">If you do not want to include the titles when you generate envelope labels from the list, you can use a regular expression to remove the titles, as the following example illustrates.</span></span>  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 <span data-ttu-id="a5653-138">정규식 패턴 `(Mr\.? |Mrs\.? |Miss |Ms\.? )`는 모든 "Mr", "Mr.", "Mrs", "Mrs.", "Miss", "Ms" 또는 "Ms."가 발생하는 것과 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-138">The regular expression pattern `(Mr\.? |Mrs\.? |Miss |Ms\.? )` matches any occurrence of "Mr ", "Mr. ", "Mrs ", "Mrs. ", "Miss ", "Ms or "Ms. ".</span></span> <span data-ttu-id="a5653-139"><xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> 메서드에 대한 호출은 일치하는 문자열을 <xref:System.String.Empty?displayProperty=nameWithType>로 바꿉니다. 즉, 원래 문자열에서 일치하는 문자열을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-139">The call to the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method replaces the matched string with <xref:System.String.Empty?displayProperty=nameWithType>; in other words, it removes it from the original string.</span></span>  
  
### <a name="example-2-identify-duplicated-words"></a><span data-ttu-id="a5653-140">예제 2: 중복된 단어 식별</span><span class="sxs-lookup"><span data-stu-id="a5653-140">Example 2: Identify duplicated words</span></span>  

 <span data-ttu-id="a5653-141">실수로 단어를 중복하는 것은 작성자가 흔히 하는 실수입니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-141">Accidentally duplicating words is a common error that writers make.</span></span> <span data-ttu-id="a5653-142">다음 예제에서 보여 주는 것처럼 정규식을 사용하여 중복된 단어를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-142">A regular expression can be used to identify duplicated words, as the following example shows.</span></span>  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 <span data-ttu-id="a5653-143">정규식 패턴 `\b(\w+?)\s\1\b`는 다음과 같이 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-143">The regular expression pattern `\b(\w+?)\s\1\b` can be interpreted as follows:</span></span>  
  
> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="a5653-144">무늬</span><span class="sxs-lookup"><span data-stu-id="a5653-144">Pattern</span></span>|<span data-ttu-id="a5653-145">해석</span><span class="sxs-lookup"><span data-stu-id="a5653-145">Interpretation</span></span>|  
> |-|-|
> |`\b`|<span data-ttu-id="a5653-146">단어 경계를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-146">Start at a word boundary.</span></span>|  
> |`(\w+?)`|<span data-ttu-id="a5653-147">하나 이상의 단어 문자(가능한 한 적은 문자)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-147">Match one or more word characters, but as few characters as possible.</span></span> <span data-ttu-id="a5653-148">이러한 단어 문자는 함께 `\1`이라고 할 수 있는 그룹을 형성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-148">Together, they form a group that can be referred to as `\1`.</span></span>|  
> |`\s`|<span data-ttu-id="a5653-149">공백 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-149">Match a white-space character.</span></span>|  
> |`\1`|<span data-ttu-id="a5653-150">`\1`이라는 그룹과 같은 부분 문자열을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-150">Match the substring that is equal to the group named `\1`.</span></span>|  
> |`\b`|<span data-ttu-id="a5653-151">단어 경계를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-151">Match a word boundary.</span></span>|  
  
 <span data-ttu-id="a5653-152"><xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> 메서드가 정규식 옵션이 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>로 설정된 상태로 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-152">The <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> method is called with regular expression options set to <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a5653-153">따라서 찾기 작업은 대/소문자를 구분하지 않으며, 이 예제에서는 부분 문자열 "This this"를 중복으로 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-153">Therefore, the match operation is case-insensitive, and the example identifies the substring "This this" as a duplication.</span></span>  
  
 <span data-ttu-id="a5653-154">입력 문자열에 하위 문자열 “this?</span><span class="sxs-lookup"><span data-stu-id="a5653-154">The input string includes the substring "this?</span></span> <span data-ttu-id="a5653-155">This"가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-155">This".</span></span> <span data-ttu-id="a5653-156">그러나 문장 부호가 중간에 있어 이는 중복으로 식별되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-156">However, because of the intervening punctuation mark, it is not identified as a duplication.</span></span>  
  
### <a name="example-3-dynamically-build-a-culture-sensitive-regular-expression"></a><span data-ttu-id="a5653-157">예제 3: 동적으로 문화권 구분 정규식 작성</span><span class="sxs-lookup"><span data-stu-id="a5653-157">Example 3: Dynamically build a culture-sensitive regular expression</span></span>  

 <span data-ttu-id="a5653-158">다음 예제에서는 정규식이 .NET의 전역화 기능에서 제공하는 유연성과 결합되었을 때의 성능을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-158">The following example illustrates the power of regular expressions combined with the flexibility offered by .NET's globalization features.</span></span> <span data-ttu-id="a5653-159">이 예제에서는 <xref:System.Globalization.NumberFormatInfo> 개체를 사용하여 시스템의 현재 문화권의 통화 값 형식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-159">It uses the <xref:System.Globalization.NumberFormatInfo> object to determine the format of currency values in the system's current culture.</span></span> <span data-ttu-id="a5653-160">그런 다음 해당 정보를 사용하여 텍스트에서 통화 값을 추출하는 정규식을 동적으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-160">It then uses that information to dynamically construct a regular expression that extracts currency values from the text.</span></span> <span data-ttu-id="a5653-161">각 일치 항목에 대해 숫자 문자열만 포함된 하위 그룹을 추출하여 <xref:System.Decimal> 값으로 변환하고 누계를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-161">For each match, it extracts the subgroup that contains the numeric string only, converts it to a <xref:System.Decimal> value, and calculates a running total.</span></span>  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 <span data-ttu-id="a5653-162">현재 문화권이 영어 - 미국(en-US)인 컴퓨터에서 이 예제를 실행할 경우 정규식 `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`가 동적으로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-162">On a computer whose current culture is English - United States (en-US), the example dynamically builds the regular expression `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`.</span></span> <span data-ttu-id="a5653-163">이 정규식 패턴은 다음과 같이 해석될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-163">This regular expression pattern can be interpreted as follows:</span></span>  

> [!div class="mx-tdCol2BreakAll"]
> |<span data-ttu-id="a5653-164">무늬</span><span class="sxs-lookup"><span data-stu-id="a5653-164">Pattern</span></span>|<span data-ttu-id="a5653-165">해석</span><span class="sxs-lookup"><span data-stu-id="a5653-165">Interpretation</span></span>|  
> |-|-|  
> |`\$`|<span data-ttu-id="a5653-166">입력 문자열에서 단일 달러 기호(`$`)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-166">Look for a single occurrence of the dollar symbol (`$`) in the input string.</span></span> <span data-ttu-id="a5653-167">정규식 패턴 문자열에는 백슬래시가 포함되어 달러 기호가 정규식 앵커로 해석되는 것이 아니라 리터럴로 해석될 것임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-167">The regular expression pattern string includes a backslash to indicate that the dollar symbol is to be interpreted literally rather than as a regular expression anchor.</span></span> <span data-ttu-id="a5653-168">(`$` 기호 단독으로는 정규식 엔진이 문자열의 끝 부분에서 찾기를 시작하려고 해야 한다는 사실을 나타냅니다.) 현재 문화권의 통화 기호가 정규식 기호로 잘못 해석되지 않도록 하기 위해 이 예제에서는 <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> 메서드를 호출하여 문자를 이스케이프합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-168">(The `$` symbol alone would indicate that the regular expression engine should try to begin its match at the end of a string.) To ensure that the current culture's currency symbol is not misinterpreted as a regular expression symbol, the example calls the <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> method to escape the character.</span></span>|  
> |`\s*`|<span data-ttu-id="a5653-169">0개 이상의 공백 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-169">Look for zero or more occurrences of a white-space character.</span></span>|  
> |`[-+]?`|<span data-ttu-id="a5653-170">0개 이상의 더하기 기호 또는 빼기 기호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-170">Look for zero or one occurrence of either a positive sign or a negative sign.</span></span>|  
> |`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|<span data-ttu-id="a5653-171">이 식을 둘러싼 바깥쪽 괄호는 이 식을 캡처링 그룹 또는 하위 식으로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-171">The outer parentheses around this expression define it as a capturing group or a subexpression.</span></span> <span data-ttu-id="a5653-172">일치 항목을 찾은 경우 일치하는 문자열의 이 부분에 대한 정보는 <xref:System.Text.RegularExpressions.Group> 속성에서 반환하는 <xref:System.Text.RegularExpressions.GroupCollection> 개체의 두 번째 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> 개체에서 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-172">If a match is found, information about this part of the matching string can be retrieved from the second <xref:System.Text.RegularExpressions.Group> object in the <xref:System.Text.RegularExpressions.GroupCollection> object returned by the <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a5653-173">(컬렉션의 첫 번째 요소는 전체 일치를 나타냅니다.)</span><span class="sxs-lookup"><span data-stu-id="a5653-173">(The first element in the collection represents the entire match.)</span></span>|  
> |`[0-9]{0,3}`|<span data-ttu-id="a5653-174">10진수 0-9를 0~3개 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-174">Look for zero to three occurrences of the decimal digits 0 through 9.</span></span>|  
> |`(,[0-9]{3})*`|<span data-ttu-id="a5653-175">그룹 구분 기호 하나 다음에 세 개의 10진수가 있는 0개 이상의 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-175">Look for zero or more occurrences of a group separator followed by three decimal digits.</span></span>|  
> |`\.`|<span data-ttu-id="a5653-176">단일 소수 구분 기호를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-176">Look for a single occurrence of the decimal separator.</span></span>|  
> |`[0-9]+`|<span data-ttu-id="a5653-177">하나 이상의 10진수를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-177">Look for one or more decimal digits.</span></span>|  
> |`(\.[0-9]+)?`|<span data-ttu-id="a5653-178">소수 구분 기호 다음에 하나 이상의 10진수가 있는 0개 이상의 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-178">Look for zero or one occurrence of the decimal separator followed by at least one decimal digit.</span></span>|  
  
 <span data-ttu-id="a5653-179">입력 문자열에서 이러한 각 하위 패턴을 찾은 경우 찾기가 성공하고 일치 항목에 대한 정보가 포함된 <xref:System.Text.RegularExpressions.Match> 개체가 <xref:System.Text.RegularExpressions.MatchCollection> 개체에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-179">If each of these subpatterns is found in the input string, the match succeeds, and a <xref:System.Text.RegularExpressions.Match> object that contains information about the match is added to the <xref:System.Text.RegularExpressions.MatchCollection> object.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="a5653-180">관련 항목</span><span class="sxs-lookup"><span data-stu-id="a5653-180">Related topics</span></span>  
  
|<span data-ttu-id="a5653-181">제목</span><span class="sxs-lookup"><span data-stu-id="a5653-181">Title</span></span>|<span data-ttu-id="a5653-182">설명</span><span class="sxs-lookup"><span data-stu-id="a5653-182">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="a5653-183">정규식 언어 - 빠른 참조</span><span class="sxs-lookup"><span data-stu-id="a5653-183">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)|<span data-ttu-id="a5653-184">정규식을 정의하는 데 사용할 수 있는 문자, 연산자 및 생성자 집합에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-184">Provides information on the set of characters, operators, and constructs that you can use to define regular expressions.</span></span>|  
|[<span data-ttu-id="a5653-185">정규식 개체 모델</span><span class="sxs-lookup"><span data-stu-id="a5653-185">The Regular Expression Object Model</span></span>](the-regular-expression-object-model.md)|<span data-ttu-id="a5653-186">정규식 클래스를 사용하는 방법을 보여 주는 코드 예제 및 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-186">Provides information and code examples that illustrate how to use the regular expression classes.</span></span>|  
|[<span data-ttu-id="a5653-187">정규식 동작 정보</span><span class="sxs-lookup"><span data-stu-id="a5653-187">Details of Regular Expression Behavior</span></span>](details-of-regular-expression-behavior.md)|<span data-ttu-id="a5653-188">.NET 정규식의 기능 및 동작에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5653-188">Provides information about the capabilities and behavior of .NET regular expressions.</span></span>|
|[<span data-ttu-id="a5653-189">Visual Studio에서 정규식 사용</span><span class="sxs-lookup"><span data-stu-id="a5653-189">Use regular expressions in Visual Studio</span></span>](/visualstudio/ide/using-regular-expressions-in-visual-studio)||
  
## <a name="reference"></a><span data-ttu-id="a5653-190">참고</span><span class="sxs-lookup"><span data-stu-id="a5653-190">Reference</span></span>  

- <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
- [<span data-ttu-id="a5653-191">정규식 - 빠른 참조(Word 형식으로 다운로드)</span><span class="sxs-lookup"><span data-stu-id="a5653-191">Regular Expressions - Quick Reference (download in Word format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
- [<span data-ttu-id="a5653-192">정규식 - 빠른 참조(PDF 형식으로 다운로드)</span><span class="sxs-lookup"><span data-stu-id="a5653-192">Regular Expressions - Quick Reference (download in PDF format)</span></span>](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
