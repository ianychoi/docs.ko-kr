---
title: .NET 정규식의 문자 이스케이프
description: .NET 정규식에서 특수 문자 및 이스케이프된 문자에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unescaped characters
- replacement patterns
- characters, escapes
- regular expressions, character escapes
- escape characters
- .NET regular expressions, character escapes
- constructs, character escapes
ms.assetid: f49cc9cc-db7d-4058-8b8a-422bc08b29b0
ms.openlocfilehash: 820e6cd7fa4a60fa6adfcaf0f0ff4d25fdda0f21
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734389"
---
# <a name="character-escapes-in-regular-expressions"></a><span data-ttu-id="4bb32-103">정규식의 문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="4bb32-103">Character Escapes in Regular Expressions</span></span>

<span data-ttu-id="4bb32-104">정규식의 백슬래시(\\)는 다음 중 하나를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-104">The backslash (\\) in a regular expression indicates one of the following:</span></span>  
  
- <span data-ttu-id="4bb32-105">다음 섹션의 표에 나와 있는 대로 뒤에 나오는 문자는 특수 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-105">The character that follows it is a special character, as shown in the table in the following section.</span></span> <span data-ttu-id="4bb32-106">예를 들어 `\b`는 단어 경계에서 정규식 일치가 시작되어야 함을 나타내는 앵커이고, `\t`는 탭을 나타내고, `\x020`은 공백을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-106">For example, `\b` is an anchor that indicates that a regular expression match should begin on a word boundary, `\t` represents a tab, and `\x020` represents a space.</span></span>  
  
- <span data-ttu-id="4bb32-107">이스케이프되지 않은 언어 구문으로 해석되는 문자는 문자 그대로 해석되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-107">A character that otherwise would be interpreted as an unescaped language construct should be interpreted literally.</span></span> <span data-ttu-id="4bb32-108">예를 들어 중괄호(`{`)는 수량자 정의를 시작하지만 중괄호 뒤에 백슬래시가 있으면(`\{`) 정규식 엔진이 중괄호와 일치해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-108">For example, a brace (`{`) begins the definition of a quantifier, but a backslash followed by a brace (`\{`) indicates that the regular expression engine should match the brace.</span></span> <span data-ttu-id="4bb32-109">마찬가지로 단일 백슬래시는 이스케이프된 언어 구문의 시작을 표시하지만, 이중 백슬래시(`\\`)는 정규식 엔진이 백슬래시와 일치해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-109">Similarly, a single backslash marks the beginning of an escaped language construct, but two backslashes (`\\`) indicate that the regular expression engine should match the backslash.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bb32-110">문자 이스케이프는 정규식 패턴에서는 인식되지만 대체 패턴에서 인식되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-110">Character escapes are recognized in regular expression patterns but not in replacement patterns.</span></span>  
  
## <a name="character-escapes-in-net"></a><span data-ttu-id="4bb32-111">.NET의 문자 이스케이프</span><span class="sxs-lookup"><span data-stu-id="4bb32-111">Character Escapes in .NET</span></span>  

 <span data-ttu-id="4bb32-112">다음 표에서는 .NET의 정규식에서 지원하는 문자 이스케이프를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-112">The following table lists the character escapes supported by regular expressions in .NET.</span></span>  
  
|<span data-ttu-id="4bb32-113">문자 또는 시퀀스</span><span class="sxs-lookup"><span data-stu-id="4bb32-113">Character or sequence</span></span>|<span data-ttu-id="4bb32-114">설명</span><span class="sxs-lookup"><span data-stu-id="4bb32-114">Description</span></span>|  
|---------------------------|-----------------|  
|<span data-ttu-id="4bb32-115">다음을 제외한 모든 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-115">All characters except for the following:</span></span><br /><br /> <span data-ttu-id="4bb32-116">을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-116">.</span></span> <span data-ttu-id="4bb32-117">$ ^ { [ ( &#124; ) \* + ?</span><span class="sxs-lookup"><span data-stu-id="4bb32-117">$ ^ { [ ( &#124; ) \* + ?</span></span> \ |<span data-ttu-id="4bb32-118">**문자 또는 시퀀스** 열에 나열된 문자 이외의 문자는 정규식에서 특별한 의미를 가지지 않습니다. 문자 그대로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-118">Characters other than those listed in the **Character or sequence** column have no special meaning in regular expressions; they match themselves.</span></span><br /><br /> <span data-ttu-id="4bb32-119">**문자 또는 시퀀스** 열에 포함된 문자는 특수 정규식 언어 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-119">The characters included in the **Character or sequence** column are special regular expression language elements.</span></span> <span data-ttu-id="4bb32-120">정규식에서 이들 문자를 찾으려면 문자를 이스케이프하거나 [긍정 문자 그룹](character-classes-in-regular-expressions.md)에 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-120">To match them in a regular expression, they must be escaped or included in a [positive character group](character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="4bb32-121">예를 들어 정규식 `\$\d+` 또는 `[$]\d+`는 "$1200"을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-121">For example, the regular expression `\$\d+` or `[$]\d+` matches "$1200".</span></span>|  
|`\a`|<span data-ttu-id="4bb32-122">벨 문자인 `\u0007`을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-122">Matches a bell (alarm) character, `\u0007`.</span></span>|  
|`\b`|<span data-ttu-id="4bb32-123">`[`*character_group*`]` 문자 클래스에서 백스페이스 문자인 `\u0008`을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-123">In a `[`*character_group*`]` character class, matches a backspace, `\u0008`.</span></span>  <span data-ttu-id="4bb32-124">[문자 클래스](character-classes-in-regular-expressions.md)를 참조하세요. 문자 클래스 이외에 `\b`는 단어 경계와 일치하는 앵커입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-124">(See [Character Classes](character-classes-in-regular-expressions.md).) Outside a character class, `\b` is an anchor that matches a word boundary.</span></span> <span data-ttu-id="4bb32-125">[앵커](anchors-in-regular-expressions.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bb32-125">(See [Anchors](anchors-in-regular-expressions.md).)</span></span>|  
|`\t`|<span data-ttu-id="4bb32-126">탭 문자인 `\u0009`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-126">Matches a tab, `\u0009`.</span></span>|  
|`\r`|<span data-ttu-id="4bb32-127">캐리지 리턴 문자인 `\u000D`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-127">Matches a carriage return, `\u000D`.</span></span> <span data-ttu-id="4bb32-128">`\r`은 줄 바꿈 문자인 `\n`과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-128">Note that `\r` is not equivalent to the newline character, `\n`.</span></span>|  
|`\v`|<span data-ttu-id="4bb32-129">세로 탭 문자인 `\u000B`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-129">Matches a vertical tab, `\u000B`.</span></span>|  
|`\f`|<span data-ttu-id="4bb32-130">용지 공급 문자인 `\u000C`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-130">Matches a form feed, `\u000C`.</span></span>|  
|`\n`|<span data-ttu-id="4bb32-131">줄 바꿈 문자인 `\u000A`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-131">Matches a new line, `\u000A`.</span></span>|  
|`\e`|<span data-ttu-id="4bb32-132">이스케이프 문자인 `\u001B`를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-132">Matches an escape, `\u001B`.</span></span>|  
|<span data-ttu-id="4bb32-133">`\` *nnn*</span><span class="sxs-lookup"><span data-stu-id="4bb32-133">`\` *nnn*</span></span>|<span data-ttu-id="4bb32-134">ASCII 문자를 찾습니다. 여기서 *nnn* 은 8진수 문자 코드를 나타내는 두 자리 또는 세 자리 숫자로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-134">Matches an ASCII character, where *nnn* consists of two or three digits that represent the octal character code.</span></span> <span data-ttu-id="4bb32-135">예를 들어 `\040`은 공백 문자를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-135">For example, `\040` represents a space character.</span></span> <span data-ttu-id="4bb32-136">이 생성자가 한 개의 숫자만 포함하거나(예: `\2`) 캡처링 그룹의 수와 일치하는 경우에는 역참조로 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-136">This construct is interpreted as a backreference if it has only one digit (for example, `\2`) or if it corresponds to the number of a capturing group.</span></span> <span data-ttu-id="4bb32-137">[역참조 구문](backreference-constructs-in-regular-expressions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4bb32-137">(See [Backreference Constructs](backreference-constructs-in-regular-expressions.md).)</span></span>|  
|<span data-ttu-id="4bb32-138">`\x` *nn*</span><span class="sxs-lookup"><span data-stu-id="4bb32-138">`\x` *nn*</span></span>|<span data-ttu-id="4bb32-139">ASCII 문자를 찾습니다. 여기서 *nn* 은 두 자리 16진수 문자 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-139">Matches an ASCII character, where *nn* is a two-digit hexadecimal character code.</span></span>|  
|<span data-ttu-id="4bb32-140">`\c` *X*</span><span class="sxs-lookup"><span data-stu-id="4bb32-140">`\c` *X*</span></span>|<span data-ttu-id="4bb32-141">ASCII 제어 문자를 찾습니다. 여기서 X는 제어 문자를 나타내는 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-141">Matches an ASCII control character, where X is the letter of the control character.</span></span> <span data-ttu-id="4bb32-142">예를 들어, `\cC`는 CTRL-C입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-142">For example, `\cC` is CTRL-C.</span></span>|  
|<span data-ttu-id="4bb32-143">`\u` *nnnn*</span><span class="sxs-lookup"><span data-stu-id="4bb32-143">`\u` *nnnn*</span></span>|<span data-ttu-id="4bb32-144">단위 값이 *nnnn* 16진수인 UTF-16 코드 단위를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-144">Matches a UTF-16 code unit whose value is *nnnn* hexadecimal.</span></span> <span data-ttu-id="4bb32-145">**참고:**  유니코드를 지정하는 데 사용되는 Perl 5 문자 이스케이프는 .NET에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-145">**Note:**  The Perl 5 character escape that is used to specify Unicode is not supported by .NET.</span></span> <span data-ttu-id="4bb32-146">Perl 5 문자 이스케이프는 `\x{` *####* `…}` 형식입니다. 여기서 *####* `…`는 일련의 16진수입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-146">The Perl 5 character escape has the form `\x{`*####*`…}`, where *####*`…` is a series of hexadecimal digits.</span></span> <span data-ttu-id="4bb32-147">대신에 `\u`*nnnn* 을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-147">Instead, use `\u`*nnnn*.</span></span>|  
|`\`|<span data-ttu-id="4bb32-148">이스케이프된 문자로 인식되지 않는 문자가 뒤에 나올 경우 이 문자를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-148">When followed by a character that is not recognized as an escaped character, matches that character.</span></span> <span data-ttu-id="4bb32-149">예를 들어 `\*`는 별표(\*)와 일치하고 `\x2A`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-149">For example, `\*` matches an asterisk (\*) and is the same as `\x2A`.</span></span>|  
  
## <a name="an-example"></a><span data-ttu-id="4bb32-150">예제</span><span class="sxs-lookup"><span data-stu-id="4bb32-150">An Example</span></span>  

 <span data-ttu-id="4bb32-151">다음 예제에서는 정규식에서 문자 이스케이프를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-151">The following example illustrates the use of character escapes in a regular expression.</span></span> <span data-ttu-id="4bb32-152">세계 최대 도시의 이름과 2009년 인구가 포함된 문자열을 구문 분석합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-152">It parses a string that contains the names of the world's largest cities and their populations in 2009.</span></span> <span data-ttu-id="4bb32-153">각 도시 이름과 해당 인구는 탭(`\t`) 또는 세로 막대(&#124; 또는 `\u007c`)로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-153">Each city name is separated from its population by a tab (`\t`) or a vertical bar (&#124; or `\u007c`).</span></span> <span data-ttu-id="4bb32-154">개별 도시 및 해당 인구는 캐리지 리턴 및 줄 바꿈으로 서로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-154">Individual cities and their populations are separated from each other by a carriage return and line feed.</span></span>  
  
 [!code-csharp[RegularExpressions.Language.Escapes#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.language.escapes/cs/escape1.cs#1)]
 [!code-vb[RegularExpressions.Language.Escapes#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.language.escapes/vb/escape1.vb#1)]  
  
 <span data-ttu-id="4bb32-155">정규식 `\G(.+)[\t\u007c](.+)\r?\n` 는 다음 테이블과 같이 해석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-155">The regular expression `\G(.+)[\t\u007c](.+)\r?\n` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="4bb32-156">무늬</span><span class="sxs-lookup"><span data-stu-id="4bb32-156">Pattern</span></span>|<span data-ttu-id="4bb32-157">설명</span><span class="sxs-lookup"><span data-stu-id="4bb32-157">Description</span></span>|  
|-------------|-----------------|  
|`\G`|<span data-ttu-id="4bb32-158">마지막 일치가 종료되면 일치를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-158">Begin the match where the last match ended.</span></span>|  
|`(.+)`|<span data-ttu-id="4bb32-159">임의 문자를 한 번 이상 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-159">Match any character one or more times.</span></span> <span data-ttu-id="4bb32-160">이 그룹은 첫 번째 캡처링 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-160">This is the first capturing group.</span></span>|  
|`[\t\u007c]`|<span data-ttu-id="4bb32-161">탭 문자(`\t`) 또는 세로 막대(&#124;)를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-161">Match a tab (`\t`) or a vertical bar (&#124;).</span></span>|  
|`(.+)`|<span data-ttu-id="4bb32-162">임의 문자를 한 번 이상 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-162">Match any character one or more times.</span></span> <span data-ttu-id="4bb32-163">이 그룹은 두 번째 캡처링 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-163">This is the second capturing group.</span></span>|  
|`\r?\n`|<span data-ttu-id="4bb32-164">캐리지 리턴, 줄 바꿈이 차례로 나타나는 발생 0개 또는 1개를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="4bb32-164">Match zero or one occurrence of a carriage return followed by a new line.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bb32-165">참조</span><span class="sxs-lookup"><span data-stu-id="4bb32-165">See also</span></span>

- [<span data-ttu-id="4bb32-166">정규식 언어 - 빠른 참조</span><span class="sxs-lookup"><span data-stu-id="4bb32-166">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
