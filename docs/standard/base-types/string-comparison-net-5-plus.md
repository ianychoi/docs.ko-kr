---
title: .NET 5+에서 문자열 비교 시 동작 변경
description: Windows에서 .NET 5 이상 버전의 문자열 비교 동작 변경에 대해 알아봅니다.
ms.date: 12/07/2020
ms.openlocfilehash: a53c36b31785fb43c0aa5f5040042abb6d40031a
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851753"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="d5ae7-103">.NET 5+에서 문자열 비교 시 동작 변경</span><span class="sxs-lookup"><span data-stu-id="d5ae7-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="d5ae7-104">.NET 5.0에, 세계화 API가 [이제 기본적으로 ICU를 사용](../../core/compatibility/globalization/5.0/icu-globalization-api.md)하는 런타임 동작 변경이 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="d5ae7-105">이것은 Windows에서 실행할 때 운영 체제의 NLS(국가별 언어 지원) 기능을 활용하는 이전 .NET Core 및 .NET Framework과 달라진 점입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="d5ae7-106">이와 같이 동작 변경을 되돌릴 수 있는 호환성 스위치를 비롯한 변경에 대한 자세한 내용은 [.NET 세계화 및 ICU](../globalization-localization/globalization-icu.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="d5ae7-107">변경 이유</span><span class="sxs-lookup"><span data-stu-id="d5ae7-107">Reason for change</span></span>

<span data-ttu-id="d5ae7-108">이 변경은 지원되는 모든 운영 체제에서 .NET의 세계화 동작을 통일하기 위해 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="d5ae7-109">또한 애플리케이션이 OS의 기본 제공 라이브러리에 의존하지 않고 자체 세계화 라이브러리를 묶을 수 있는 기능도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="d5ae7-110">자세한 내용은 [호환성이 손상되는 변경 알림](../../core/compatibility/globalization/5.0/icu-globalization-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="d5ae7-111">동작의 차이</span><span class="sxs-lookup"><span data-stu-id="d5ae7-111">Behavioral differences</span></span>

<span data-ttu-id="d5ae7-112"><xref:System.StringComparison> 인수를 사용하는 오버로드를 호출하지 않고 `string.IndexOf(string)`와 같은 함수를 사용하는 경우 서수 검색을 수행하려 할 때 뜻하지 않게 문화권별 동작에 대한 종속성을 대신 사용하게 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="d5ae7-113">NLS와 ICU는 언어 비교자에서 구현하는 논리가 다르므로 `string.IndexOf(string)`와 같은 메서드의 결과가 예기치 않은 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="d5ae7-114">이는 세계화 기능이 항상 활성 상태일 것으로 예상하지 않는 곳에서도 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="d5ae7-115">예를 들어 다음 코드는 현재 런타임에 따라 다른 답을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="d5ae7-116">예기치 않은 동작 방지</span><span class="sxs-lookup"><span data-stu-id="d5ae7-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="d5ae7-117">이 섹션에서는 .NET 5.0의 예기치 않은 동작 변경을 처리하는 두 가지 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="d5ae7-118">코드 분석기 사용</span><span class="sxs-lookup"><span data-stu-id="d5ae7-118">Enable code analyzers</span></span>

<span data-ttu-id="d5ae7-119">[코드 분석기](../../fundamentals/code-analysis/overview.md)는 버그가 있을 수 있는 호출 사이트를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="d5ae7-120">의외의 동작을 방지하려면 프로젝트에서 .NET 컴파일러 플랫폼(Roslyn) 분석기를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-120">To help guard against any surprising behaviors, we recommend enabling .NET compiler platform (Roslyn) analyzers in your project.</span></span> <span data-ttu-id="d5ae7-121">분석기는 서수 비교자를 사용하려 할 때 뜻하지 않게 언어 비교자를 사용할 수 있는 코드에 플래그를 지정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-121">The analyzers help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span> <span data-ttu-id="d5ae7-122">다음 규칙은 이러한 문제에 플래그를 지정하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-122">The following rules should help flag these issues:</span></span>

- [<span data-ttu-id="d5ae7-123">CA1307: 명확성을 위해 StringComparison 지정</span><span class="sxs-lookup"><span data-stu-id="d5ae7-123">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [<span data-ttu-id="d5ae7-124">CA1309: 서수 StringComparison을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-124">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [<span data-ttu-id="d5ae7-125">CA1310: 정확성을 위해 StringComparison 지정</span><span class="sxs-lookup"><span data-stu-id="d5ae7-125">CA1310: Specify StringComparison for correctness</span></span>](../../fundamentals/code-analysis/quality-rules/ca1310.md)

<span data-ttu-id="d5ae7-126">이러한 특정 규칙은 기본적으로 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-126">These specific rules aren't enabled by default.</span></span> <span data-ttu-id="d5ae7-127">해당 규칙을 사용하도록 설정하고 위반을 빌드 오류로 표시하려면 프로젝트 파일에 다음 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-127">To enable them and show any violations as build errors, set the following properties in your project file:</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="d5ae7-128">다음 코드 조각은 관련 코드 분석기 경고 또는 오류를 생성하는 코드 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-128">The following snippet shows examples of code that produces the relevant code analyzer warnings or errors.</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="d5ae7-129">마찬가지로 정렬된 문자열 컬렉션을 인스턴스화하거나 기존 문자열 기반 컬렉션을 정렬하는 경우 명시적 비교자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-129">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="d5ae7-130">NLS 동작으로 되돌리기</span><span class="sxs-lookup"><span data-stu-id="d5ae7-130">Revert back to NLS behaviors</span></span>

<span data-ttu-id="d5ae7-131">Windows에서 실행할 때 .NET 5 애플리케이션을 이전 NLS 동작으로 되돌리려면 [.NET 세계화 및 ICU](../globalization-localization/globalization-icu.md)의 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-131">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="d5ae7-132">이 애플리케이션 전체 호환성 스위치는 애플리케이션 수준에서 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-132">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="d5ae7-133">개별 라이브러리는 이 동작을 옵트인하거나 옵트아웃할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-133">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="d5ae7-134">코드 상태를 개선하고 숨어 있는 기존 버그를 발견하려면 [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) 및 [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) 코드 분석 규칙을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-134">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), and [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="d5ae7-135">자세한 내용은 [코드 분석기 사용](#enable-code-analyzers)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-135">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d5ae7-136">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="d5ae7-136">Affected APIs</span></span>

<span data-ttu-id="d5ae7-137">대부분의 .NET 애플리케이션에서는 .NET 5.0의 변경으로 인한 예기치 않은 동작이 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-137">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="d5ae7-138">그러나 영향을 받는 API 수가 많고 이러한 API는 .NET 에코시스템의 기본 요소이기 때문에, .NET 5.0에서 원치 않는 동작이 도입되거나 애플리케이션에 이미 존재하던 숨어 있는 버그가 드러날 가능성에 유의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-138">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="d5ae7-139">영향을 받는 API는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-139">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="d5ae7-140"><xref:System.Globalization.TextInfo?displayProperty=fullName>(대부분의 멤버)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="d5ae7-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName>(대부분의 멤버)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="d5ae7-142"><xref:System.Array.Sort%2A?displayProperty=fullName>(문자열 배열을 정렬하는 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="d5ae7-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName>(목록 요소가 문자열인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="d5ae7-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName>(키가 문자열인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="d5ae7-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName>(키가 문자열인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="d5ae7-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName>(집합에 문자열이 포함된 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="d5ae7-147">이 목록은 영향을 받는 API의 전체 목록이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-147">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="d5ae7-148">위의 모든 API는 기본적으로 스레드의 [현재 문화권](xref:System.Threading.Thread.CurrentCulture)을 사용하여 언어 문자열 검색 및 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-148">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="d5ae7-149">언어 검색 및 비교와 서수 검색 및 비교의 차이점은 [서수 검색 및 비교 대 언어 검색 및 비교](#ordinal-vs-linguistic-search-and-comparison)에 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-149">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="d5ae7-150">ICU가 구현하는 언어 문자열 비교는 NLS와 다르기 때문에, 이전 버전의 .NET Core나 .NET Framework에서 .NET 5.0으로 업그레이드하고 영향을 받는 API 중 하나를 호출하는 Windows 기반 애플리케이션은 API가 다른 동작을 보이기 시작하는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-150">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="d5ae7-151">예외</span><span class="sxs-lookup"><span data-stu-id="d5ae7-151">Exceptions</span></span>

* <span data-ttu-id="d5ae7-152">API가 명시적인 `StringComparison` 또는 `CultureInfo` 매개 변수를 허용하는 경우 이 매개 변수는 API의 기본 동작을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-152">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="d5ae7-153">`CurrentCulture[IgnoreCase]` 또는 `InvariantCulture[IgnoreCase]`를 지정하는 명시적 `StringComparison` 인수를 호출자가 전달하지 않으면 첫 번째 매개 변수가 `char` 형식(예를 들어 <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>)인 `System.String` 멤버는 서수 검색을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-153">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="d5ae7-154">각 <xref:System.String> API의 기본 동작에 대한 자세한 분석은 [기본 검색 및 비교 형식](#default-search-and-comparison-types) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-154">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="d5ae7-155">서수 검색 및 비교 대 언어 검색 및 비교</span><span class="sxs-lookup"><span data-stu-id="d5ae7-155">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="d5ae7-156">서수(비언어라고도 함) 검색 및 비교는 문자열을 개별 `char` 요소로 분해하여 문자 대응 검색 또는 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-156">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="d5ae7-157">예를 들어 `"dog"` 문자열과 `"dog"` 문자열은 `Ordinal` 비교자에서 같음으로 비교됩니다. 두 문자열이 정확히 동일한 문자 순서로 구성되어 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-157">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="d5ae7-158">하지만 `"dog"`와 `"Dog"`는 `Ordinal` 비교자에서 같지 않음으로 비교되는데, 정확히 동일한 문자 순서로 구성되지 않았기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-158">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="d5ae7-159">즉, 대문자 `'D'`의 코드 포인트 `U+0044`가 소문자 `'d'`의 코드 포인트 `U+0064` 전에 나오므로 `"Dog"` 전에 `"dog"`이 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-159">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="d5ae7-160">`OrdinalIgnoreCase` 비교자는 계속 문자 대응 방식으로 작동하지만 작업을 수행하는 동안 대/소문자 차이를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-160">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="d5ae7-161">`OrdinalIgnoreCase` 비교자에서는 문자 쌍 `'d'`와 `'D'`는 문자 쌍 `'á'`와 `'Á'`처럼 같음으로 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-161">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="d5ae7-162">하지만 악센트가 없는 문자 `'a'`는 악센트가 있는 문자 `'á'`와 같지 않음으로 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-162">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="d5ae7-163">다음 표에는 몇 가지 예가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-163">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="d5ae7-164">String 1</span><span class="sxs-lookup"><span data-stu-id="d5ae7-164">String 1</span></span> | <span data-ttu-id="d5ae7-165">String 2</span><span class="sxs-lookup"><span data-stu-id="d5ae7-165">String 2</span></span> | <span data-ttu-id="d5ae7-166">`Ordinal` 비교</span><span class="sxs-lookup"><span data-stu-id="d5ae7-166">`Ordinal` comparison</span></span> | <span data-ttu-id="d5ae7-167">`OrdinalIgnoreCase` 비교</span><span class="sxs-lookup"><span data-stu-id="d5ae7-167">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="d5ae7-168">equal</span><span class="sxs-lookup"><span data-stu-id="d5ae7-168">equal</span></span> | <span data-ttu-id="d5ae7-169">equal</span><span class="sxs-lookup"><span data-stu-id="d5ae7-169">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="d5ae7-170">같지 않음</span><span class="sxs-lookup"><span data-stu-id="d5ae7-170">not equal</span></span> | <span data-ttu-id="d5ae7-171">equal</span><span class="sxs-lookup"><span data-stu-id="d5ae7-171">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="d5ae7-172">같지 않음</span><span class="sxs-lookup"><span data-stu-id="d5ae7-172">not equal</span></span> | <span data-ttu-id="d5ae7-173">equal</span><span class="sxs-lookup"><span data-stu-id="d5ae7-173">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="d5ae7-174">같지 않음</span><span class="sxs-lookup"><span data-stu-id="d5ae7-174">not equal</span></span> | <span data-ttu-id="d5ae7-175">같지 않음</span><span class="sxs-lookup"><span data-stu-id="d5ae7-175">not equal</span></span> |

<span data-ttu-id="d5ae7-176">유니코드에서도 문자열은 여러 가지 메모리 내 표현을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-176">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="d5ae7-177">예를 들어 e 양음 부호(é)는 다음과 같은 두 가지 방법으로 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-177">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="d5ae7-178">단일 리터럴 `'é'` 문자(`'\u00E9'`로도 씀).</span><span class="sxs-lookup"><span data-stu-id="d5ae7-178">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="d5ae7-179">결합 악센트 한정자 문자 `'\u0301'`이 뒤에 오는 악센트 없는 리터럴 `'e'` 문자.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-179">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="d5ae7-180">즉, 다음 네 개의 문자열은 구성 요소가 서로 다르더라도 모두 `"résumé"`로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-180">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="d5ae7-181">이 문자열들은 리터럴 `'é'` 문자 또는 악센트가 없는 리터럴 `'e'` 문자와 결합 악센트 한정자 `'\u0301'`의 조합을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-181">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="d5ae7-182">서수 비교자에서는 이러한 문자열 중 어느 것도 서로 같음으로 비교되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-182">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="d5ae7-183">그 이유는 화면에 렌더링될 때 모두 똑같이 보이더라도 서로 다른 기본 문자 시퀀스를 포함하고 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-183">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="d5ae7-184">`string.IndexOf(..., StringComparison.Ordinal)` 작업을 수행할 때 런타임은 정확한 부분 문자열 일치 항목을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-184">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="d5ae7-185">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-185">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="d5ae7-186">서수 검색 및 비교 루틴은 현재 스레드의 문화권 설정에 영향을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-186">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="d5ae7-187">언어 검색 및 비교 루틴은 문자열을 데이터 정렬 요소로 분해하고 이러한 요소에 대해 검색 또는 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-187">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="d5ae7-188">문자열의 문자와 해당 구성 요소 데이터 정렬 요소 사이에 1:1 매핑이 반드시 필요하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-188">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="d5ae7-189">예를 들어 길이가 2인 문자열은 단일 데이터 정렬 요소로만 구성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-189">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="d5ae7-190">두 문자열이 언어적으로 인식되는 방식으로 비교되는 경우, 비교자는 문자열의 리터럴 문자가 서로 다른 경우에도 두 문자열의 데이터 정렬 요소에 동일한 의미상 의미가 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-190">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="d5ae7-191">문자열 `"résumé"`와 네 가지 다른 표현을 다시 생각해 보세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-191">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="d5ae7-192">다음 표는 각 표현을 데이터 정렬 요소로 분할하여 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-192">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="d5ae7-193">String</span><span class="sxs-lookup"><span data-stu-id="d5ae7-193">String</span></span> | <span data-ttu-id="d5ae7-194">데이터 정렬 요소</span><span class="sxs-lookup"><span data-stu-id="d5ae7-194">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="d5ae7-195">데이터 정렬 요소는 판독기가 단일 문자 또는 문자 클러스터로 인식하는 항목과 대체로 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-195">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="d5ae7-196">개념적으로는 [문자소 클러스터](character-encoding-introduction.md#grapheme-clusters)와 유사하지만 포함하는 범위가 약간 더 큽니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-196">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="d5ae7-197">언어 비교자에서는 정확한 일치가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-197">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="d5ae7-198">대신 데이터 정렬 요소가 해당 의미상 의미에 따라 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-198">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="d5ae7-199">예를 들어 언어 비교자는 `"\u00E9"` 부분 문자열과 `"e\u0301"` 부분 문자열을 같음으로 처리하는데, 둘 다 의미상 “양음 부호 악센트 한정자가 있는 소문자 e”를 뜻하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-199">For example, a linguistic comparer treats the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="d5ae7-200">이를 통해 `IndexOf` 메서드는 다음 코드 샘플에 나온 것처럼 의미상 동등한 부분 문자열 `"\u00E9"`가 포함된 더 큰 문자열 내에서 `"e\u0301"` 부분 문자열을 일치시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-200">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="d5ae7-201">그 결과, 언어 비교가 사용되는 경우 길이가 다른 두 문자열이 같음으로 비교될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-201">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="d5ae7-202">호출자는 이러한 시나리오에서 문자열 길이를 처리하는 특수한 사례 논리를 적용하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-202">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="d5ae7-203">문화권 인식 검색 및 비교 루틴은 언어 검색 및 비교 루틴의 특수한 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-203">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="d5ae7-204">문화권 인식 비교자에서 데이터 정렬 요소의 개념은 지정된 문화권과 관련된 정보를 포함하도록 확장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-204">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="d5ae7-205">예를 들어 [헝가리어 알파벳에서](https://en.wikipedia.org/wiki/Hungarian_alphabet) 연속으로 나타나는 두 문자 \<dz\>는 \<d\> 또는 \<z\>와 구별되는 고유한 자체 문자로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-205">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="d5ae7-206">즉, 문자열에 \<dz\>가 보이는 경우 헝가리어 문화권 인식 비교자는 이를 단일 데이터 정렬 요소로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-206">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="d5ae7-207">String</span><span class="sxs-lookup"><span data-stu-id="d5ae7-207">String</span></span> | <span data-ttu-id="d5ae7-208">데이터 정렬 요소</span><span class="sxs-lookup"><span data-stu-id="d5ae7-208">As collation elements</span></span> | <span data-ttu-id="d5ae7-209">설명</span><span class="sxs-lookup"><span data-stu-id="d5ae7-209">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="d5ae7-210">(표준 언어 비교자 사용)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-210">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="d5ae7-211">(헝가리어 문화권 인식 비교자 사용)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-211">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="d5ae7-212">헝가리어 문화권 인식 비교자를 사용하는 경우 이는 문자열 `"endz"`가 부분 문자열 `"z"`로 끝나지 않음을 뜻합니다. <\dz\>와 <\z\>가 의미상 의미가 서로 다른 데이터 정렬 요소로 간주되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-212">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="d5ae7-213">동작: 언어 비교자와 문화권 인식 비교자의 동작은 수시로 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-213">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="d5ae7-214">ICU와 이전 Windows NLS 기능 모두 세계 언어의 변화를 반영하여 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-214">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="d5ae7-215">자세한 내용은 블로그 게시물 [Local (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-215">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="d5ae7-216">서수 비교자의 동작은 정확한 비트 검색 및 비교를 수행하므로 변경되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-216">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="d5ae7-217">하지만 유니코드가 더 많은 문자 집합을 포함하도록 확장되고 기존 대/소문자 데이터의 누락을 수정함에 따라 *OrdinalIgnoreCase* 비교자의 동작이 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-217">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="d5ae7-218">사용: `StringComparison.InvariantCulture` 비교자와 `StringComparison.InvariantCultureIgnoreCase` 비교자는 문화권을 인식하지 않는 언어 비교자입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-218">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="d5ae7-219">즉, 이러한 비교자는 악센트가 있는 문자 é에 가능한 기본 표현이 여러 개 있을 수 있다는 개념과 이러한 모든 표현을 같음으로 처리해야 한다는 것을 이해합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-219">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="d5ae7-220">그러나 문화권을 인식하지 않는 언어 비교자에는 위에 나온 것처럼 \<d\> 또는 \<z\>와는 다른 \<dz\>의 특별한 처리가 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-220">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="d5ae7-221">또한 독일어 Eszett(ß)와 같은 문자도 특별히 처리하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-221">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="d5ae7-222">.NET은 고정 전역화 모드도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-222">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="d5ae7-223">이 옵트인 모드는 언어 검색 및 비교 루틴을 처리하는 코드 경로를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-223">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="d5ae7-224">이 모드에서 모든 작업은 호출자가 어떤 `CultureInfo` 또는 `StringComparison` 인수를 제공하든 관계 없이 서수 또는 *OrdinalIgnoreCase* 동작을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-224">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="d5ae7-225">자세한 내용은 [세계화를 위한 런타임 구성 옵션](../../core/run-time-config/globalization.md)과 [.NET Core 세계화 고정 모드](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-225">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="d5ae7-226">자세한 내용은 [.NET에서의 문자열 비교 모범 사례](best-practices-strings.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-226">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="d5ae7-227">보안 의미</span><span class="sxs-lookup"><span data-stu-id="d5ae7-227">Security implications</span></span>

<span data-ttu-id="d5ae7-228">앱에서 영향을 받는 API가 필터링에 사용되는 경우 CA1307 및 CA1309 코드 분석 규칙을 사용하도록 설정하여 실수로 언어 검색이 서수 검색 대신 사용되었을 수 있는 위치를 찾는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-228">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="d5ae7-229">다음과 같은 코드 패턴은 보안 악용에 취약할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-229">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="d5ae7-230">`string.IndexOf(string)` 메서드는 기본적으로 언어 검색을 사용하기 때문에 문자열에 리터럴 `'<'` 또는 `'&'` 문자가 포함되고 `string.IndexOf(string)` 루틴에서 검색 부분 문자열을 찾을 수 없다는 `-1`가 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-230">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="d5ae7-231">코드 분석 규칙 CA1307과 CA1309는 이러한 호출 사이트에 플래그를 지정하고, 잠재적 문제가 있음을 개발자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-231">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="d5ae7-232">기본 검색 및 비교 형식</span><span class="sxs-lookup"><span data-stu-id="d5ae7-232">Default search and comparison types</span></span>

<span data-ttu-id="d5ae7-233">다음 표에는 다양한 문자열 및 문자열 형식 API의 기본 검색 및 비교 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-233">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="d5ae7-234">호출자가 명시적인 `CultureInfo` 또는 `StringComparison` 매개 변수를 제공하는 경우 이 매개 변수는 모든 기본값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-234">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="d5ae7-235">API</span><span class="sxs-lookup"><span data-stu-id="d5ae7-235">API</span></span> | <span data-ttu-id="d5ae7-236">기본 동작</span><span class="sxs-lookup"><span data-stu-id="d5ae7-236">Default behavior</span></span> | <span data-ttu-id="d5ae7-237">설명</span><span class="sxs-lookup"><span data-stu-id="d5ae7-237">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="d5ae7-238">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-238">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="d5ae7-239">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-239">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="d5ae7-240">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-240">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="d5ae7-241">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-241">Ordinal</span></span> | <span data-ttu-id="d5ae7-242">(첫 번째 매개 변수가 `char`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-242">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="d5ae7-243">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-243">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-244">(첫 번째 매개 변수가 `string`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-244">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="d5ae7-245">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-245">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="d5ae7-246">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-246">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="d5ae7-247">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-247">Ordinal</span></span> | <span data-ttu-id="d5ae7-248">(첫 번째 매개 변수가 `char`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-248">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="d5ae7-249">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-249">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-250">(첫 번째 매개 변수가 `string`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-250">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="d5ae7-251">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-251">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="d5ae7-252">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-252">Ordinal</span></span> | <span data-ttu-id="d5ae7-253">(첫 번째 매개 변수가 `char`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-253">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="d5ae7-254">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-254">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-255">(첫 번째 매개 변수가 `string`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-255">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="d5ae7-256">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-256">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="d5ae7-257">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-257">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="d5ae7-258">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-258">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="d5ae7-259">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-259">Ordinal</span></span> | <span data-ttu-id="d5ae7-260">(첫 번째 매개 변수가 `char`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-260">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="d5ae7-261">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-261">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-262">(첫 번째 매개 변수가 `string`인 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-262">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="d5ae7-263">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-263">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="d5ae7-264">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-264">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="d5ae7-265">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-265">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="d5ae7-266">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-266">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="d5ae7-267">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-267">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="d5ae7-268">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-268">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="d5ae7-269">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-269">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="d5ae7-270">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-270">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="d5ae7-271">서수</span><span class="sxs-lookup"><span data-stu-id="d5ae7-271">Ordinal</span></span> | |

<span data-ttu-id="d5ae7-272">`string` API와 달리 모든 `MemoryExtensions` API는 다음을 제외하고 기본적으로 서수 검색 및 비교를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-272">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="d5ae7-273">API</span><span class="sxs-lookup"><span data-stu-id="d5ae7-273">API</span></span> | <span data-ttu-id="d5ae7-274">기본 동작</span><span class="sxs-lookup"><span data-stu-id="d5ae7-274">Default behavior</span></span> | <span data-ttu-id="d5ae7-275">설명</span><span class="sxs-lookup"><span data-stu-id="d5ae7-275">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="d5ae7-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-276">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-277">(null `CultureInfo` 인수를 전달한 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="d5ae7-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-278">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="d5ae7-279">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-279">CurrentCulture</span></span> | <span data-ttu-id="d5ae7-280">(null `CultureInfo` 인수를 전달한 경우)</span><span class="sxs-lookup"><span data-stu-id="d5ae7-280">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="d5ae7-281">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="d5ae7-281">InvariantCulture</span></span> | |

<span data-ttu-id="d5ae7-282">결과적으로 `string` 사용에서 `ReadOnlySpan<char>` 사용으로 코드를 변환하면 의도하지 않은 동작 변경이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-282">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="d5ae7-283">그 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-283">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="d5ae7-284">이를 해결하는 데 권장되는 방법은 명시적 `StringComparison` 매개 변수를 이러한 API에 전달하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-284">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="d5ae7-285">코드 분석 규칙 CA1307와 CA1309가 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d5ae7-285">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="d5ae7-286">참조</span><span class="sxs-lookup"><span data-stu-id="d5ae7-286">See also</span></span>

- [<span data-ttu-id="d5ae7-287">세계화 관련 호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="d5ae7-287">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="d5ae7-288">.NET에서의 문자열 비교 모범 사례</span><span class="sxs-lookup"><span data-stu-id="d5ae7-288">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="d5ae7-289">C#에서 문자열을 비교하는 방법</span><span class="sxs-lookup"><span data-stu-id="d5ae7-289">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="d5ae7-290">.NET 세계화 및 ICU</span><span class="sxs-lookup"><span data-stu-id="d5ae7-290">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="d5ae7-291">서수 문자열 작업과 문화권 구분 문자열 작업 비교</span><span class="sxs-lookup"><span data-stu-id="d5ae7-291">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="d5ae7-292">.NET 소스 코드 분석 개요</span><span class="sxs-lookup"><span data-stu-id="d5ae7-292">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
