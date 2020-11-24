---
title: .NET에서 문자열 비교
description: .NET에서 문자열을 비교하는 메서드에 대해 알아봅니다. CompareOrdinal, CompareTo, StartsWith, EndsWith, Equals, IndexOf, LastIndexOf 메서드에 대해 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- value comparisons of strings
- LastIndexOf method
- CompareTo method
- IndexOf method
- Compare method
- strings [.NET], comparing
- CompareOrdinal method
- EndsWith method
- Equals method
- StartsWith method
ms.assetid: 977dc094-fe19-4955-98ec-d2294d04a4ba
ms.openlocfilehash: 08a92e314ad0900679d46cc759c80db89b43f0f0
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823149"
---
# <a name="compare-strings-in-net"></a><span data-ttu-id="b4443-104">.NET에서 문자열 비교</span><span class="sxs-lookup"><span data-stu-id="b4443-104">Compare strings in .NET</span></span>

<span data-ttu-id="b4443-105">.NET에서는 문자열의 값을 비교하는 여러 가지 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-105">.NET provides several methods to compare the values of strings.</span></span> <span data-ttu-id="b4443-106">다음 표에서는 값 비교 메서드를 나열하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-106">The following table lists and describes the value-comparison methods.</span></span>

|<span data-ttu-id="b4443-107">메서드 이름</span><span class="sxs-lookup"><span data-stu-id="b4443-107">Method name</span></span>|<span data-ttu-id="b4443-108">기능</span><span class="sxs-lookup"><span data-stu-id="b4443-108">Use</span></span>|
|-----------------|---------|
|<xref:System.String.Compare%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-109">두 문자열의 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-109">Compares the values of two strings.</span></span> <span data-ttu-id="b4443-110">정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-110">Returns an integer value.</span></span>|
|<xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-111">로컬 문화권에 관계없이 두 문자열을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-111">Compares two strings without regard to local culture.</span></span> <span data-ttu-id="b4443-112">정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-112">Returns an integer value.</span></span>|
|<xref:System.String.CompareTo%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-113">현재 문자열 개체를 다른 문자열과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-113">Compares the current string object to another string.</span></span> <span data-ttu-id="b4443-114">정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-114">Returns an integer value.</span></span>|
|<xref:System.String.StartsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-115">문자열이 전달된 문자열로 시작하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-115">Determines whether a string begins with the string passed.</span></span> <span data-ttu-id="b4443-116">부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-116">Returns a Boolean value.</span></span>|
|<xref:System.String.EndsWith%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-117">문자열이 전달된 문자열로 끝나는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-117">Determines whether a string ends with the string passed.</span></span> <span data-ttu-id="b4443-118">부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-118">Returns a Boolean value.</span></span>|
|<xref:System.String.Contains%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-119">문자 또는 문자열이 다른 문자열에 나타나는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-119">Determines whether a character or string occurs within another string.</span></span> <span data-ttu-id="b4443-120">부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-120">Returns a Boolean value.</span></span>|
|<xref:System.String.Equals%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-121">두 문자열이 같은지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-121">Determines whether two strings are the same.</span></span> <span data-ttu-id="b4443-122">부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-122">Returns a Boolean value.</span></span>|
|<xref:System.String.IndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-123">검사 중인 문자열의 처음부터 시작하여 문자 또는 문자열의 인덱스 위치를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-123">Returns the index position of a character or string, starting from the beginning of the string you are examining.</span></span> <span data-ttu-id="b4443-124">정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-124">Returns an integer value.</span></span>|
|<xref:System.String.LastIndexOf%2A?displayProperty=nameWithType>|<span data-ttu-id="b4443-125">검사 중인 문자열의 끝부터 시작하여 문자 또는 문자열의 인덱스 위치를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-125">Returns the index position of a character or string, starting from the end of the string you are examining.</span></span> <span data-ttu-id="b4443-126">정수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-126">Returns an integer value.</span></span>|

## <a name="compare-method"></a><span data-ttu-id="b4443-127">Compare 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-127">Compare method</span></span>

<span data-ttu-id="b4443-128">정적 <xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드는 두 문자열을 비교하는 철저한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-128">The static <xref:System.String.Compare%2A?displayProperty=nameWithType> method provides a thorough way of comparing two strings.</span></span> <span data-ttu-id="b4443-129">이 메서드는 문화권을 인식합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-129">This method is culturally aware.</span></span> <span data-ttu-id="b4443-130">이 함수를 사용하여 두 문자열 또는 두 문자열의 부분 문자열을 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-130">You can use this function to compare two strings or substrings of two strings.</span></span> <span data-ttu-id="b4443-131">또한 대/소문자와 문화권 차이를 반영하거나 무시하는 오버로드가 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-131">Additionally, overloads are provided that regard or disregard case and cultural variance.</span></span> <span data-ttu-id="b4443-132">다음 표에서는 이 메서드가 반환할 수 있는 세 가지 정수 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-132">The following table shows the three integer values that this method might return.</span></span>

|<span data-ttu-id="b4443-133">반환 값</span><span class="sxs-lookup"><span data-stu-id="b4443-133">Return value</span></span>|<span data-ttu-id="b4443-134">조건</span><span class="sxs-lookup"><span data-stu-id="b4443-134">Condition</span></span>|
|------------------|---------------|
|<span data-ttu-id="b4443-135">음의 정수</span><span class="sxs-lookup"><span data-stu-id="b4443-135">A negative integer</span></span>|<span data-ttu-id="b4443-136">정렬 순서에서 첫 번째 문자열이 두 번째 문자열 앞에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-136">The first string precedes the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="b4443-137">또는</span><span class="sxs-lookup"><span data-stu-id="b4443-137">-or-</span></span><br /><br /> <span data-ttu-id="b4443-138">첫 번째 문자열이 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-138">The first string is `null`.</span></span>|
|<span data-ttu-id="b4443-139">0</span><span class="sxs-lookup"><span data-stu-id="b4443-139">0</span></span>|<span data-ttu-id="b4443-140">첫 번째 문자열과 두 번째 문자열이 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-140">The first string and the second string are equal.</span></span><br /><br /> <span data-ttu-id="b4443-141">또는</span><span class="sxs-lookup"><span data-stu-id="b4443-141">-or-</span></span><br /><br /> <span data-ttu-id="b4443-142">두 문자열이 모두 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-142">Both strings are `null`.</span></span>|
|<span data-ttu-id="b4443-143">양의 정수</span><span class="sxs-lookup"><span data-stu-id="b4443-143">A positive integer</span></span><br /><br /> <span data-ttu-id="b4443-144">또는</span><span class="sxs-lookup"><span data-stu-id="b4443-144">-or-</span></span><br /><br /> <span data-ttu-id="b4443-145">1</span><span class="sxs-lookup"><span data-stu-id="b4443-145">1</span></span>|<span data-ttu-id="b4443-146">정렬 순서에서 첫 번째 문자열이 두 번째 문자열 뒤에 옵니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-146">The first string follows the second string in the sort order.</span></span><br /><br /> <span data-ttu-id="b4443-147">또는</span><span class="sxs-lookup"><span data-stu-id="b4443-147">-or-</span></span><br /><br /> <span data-ttu-id="b4443-148">두 번째 문자열이 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-148">The second string is `null`.</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="b4443-149"><xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드는 주로 문자열의 순서를 지정하거나 정렬할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-149">The <xref:System.String.Compare%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="b4443-150"><xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드를 통해 같은지 여부를 테스트하면 안 됩니다(즉, 한 문자열이 다른 문자열보다 작거나 큰지에 관계없이 반환 값 0을 명시적으로 찾기 위해 사용하면 안 됨).</span><span class="sxs-lookup"><span data-stu-id="b4443-150">You should not use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="b4443-151">대신, 두 문자열이 같은지 여부를 확인하려면 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-151">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="b4443-152">다음 예제에서는 <xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드를 사용하여 두 문자열의 상대 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-152">The following example uses the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to determine the relative values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#6)]
 [!code-csharp[Conceptual.String.BasicOps#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#6)]
 [!code-vb[Conceptual.String.BasicOps#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#6)]

 <span data-ttu-id="b4443-153">이 예제에서는 콘솔에 `-1` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-153">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="b4443-154">앞의 예제는 기본적으로 문화권을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-154">The preceding example is culture-sensitive by default.</span></span> <span data-ttu-id="b4443-155">문화권을 구분하지 않는 문자열 비교를 수행하려면 <xref:System.String.Compare%2A?displayProperty=nameWithType> culture *매개 변수를 제공하여 사용할 문화권을 지정할 수 있게 해주는* 메서드의 오버로드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-155">To perform a culture-insensitive string comparison, use an overload of the <xref:System.String.Compare%2A?displayProperty=nameWithType> method that allows you to specify the culture to use by supplying a *culture* parameter.</span></span> <span data-ttu-id="b4443-156"><xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드를 사용하여 문화권을 구분하지 않는 비교를 수행하는 방법을 보여 주는 예시는 [문화권을 구분하지 않는 문자열 비교](../globalization-localization/performing-culture-insensitive-string-comparisons.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4443-156">For an example that demonstrates how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> method to perform a culture-insensitive comparison, see [Culture-insensitive string comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="compareordinal-method"></a><span data-ttu-id="b4443-157">CompareOrdinal 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-157">CompareOrdinal method</span></span>

<span data-ttu-id="b4443-158"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 메서드는 로컬 문화권을 고려하지 않고 두 문자열 개체를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-158">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method compares two string objects without considering the local culture.</span></span> <span data-ttu-id="b4443-159">이 메서드의 반환 값은 앞의 표에서 `Compare` 메서드가 반환하는 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-159">The return values of this method are identical to the values returned by the `Compare` method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4443-160"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 메서드는 주로 문자열의 순서를 지정하거나 정렬할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-160">The <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="b4443-161"><xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> 메서드를 통해 같은지 여부를 테스트하면 안 됩니다(즉, 한 문자열이 다른 문자열보다 작거나 큰지에 관계없이 반환 값 0을 명시적으로 찾기 위해 사용하면 안 됨).</span><span class="sxs-lookup"><span data-stu-id="b4443-161">You should not use the <xref:System.String.CompareOrdinal%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="b4443-162">대신, 두 문자열이 같은지 여부를 확인하려면 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-162">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="b4443-163">다음 예제에서는 `CompareOrdinal` 메서드를 사용하여 두 문자열의 값을 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-163">The following example uses the `CompareOrdinal` method to compare the values of two strings.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#7)]
 [!code-csharp[Conceptual.String.BasicOps#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#7)]
 [!code-vb[Conceptual.String.BasicOps#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#7)]

 <span data-ttu-id="b4443-164">이 예제에서는 콘솔에 `-32` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-164">This example displays `-32` to the console.</span></span>

## <a name="compareto-method"></a><span data-ttu-id="b4443-165">CompareTo 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-165">CompareTo method</span></span>

<span data-ttu-id="b4443-166"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 메서드는 현재 문자열 개체가 캡슐화하는 문자열을 다른 문자열 또는 개체와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-166">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method compares the string that the current string object encapsulates to another string or object.</span></span> <span data-ttu-id="b4443-167">이 메서드의 반환 값은 앞의 표에서 <xref:System.String.Compare%2A?displayProperty=nameWithType> 메서드가 반환하는 값과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-167">The return values of this method are identical to the values returned by the <xref:System.String.Compare%2A?displayProperty=nameWithType> method in the previous table.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b4443-168"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 메서드는 주로 문자열의 순서를 지정하거나 정렬할 때 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-168">The <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method is primarily intended for use when ordering or sorting strings.</span></span> <span data-ttu-id="b4443-169"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 메서드를 통해 같은지 여부를 테스트하면 안 됩니다(즉, 한 문자열이 다른 문자열보다 작거나 큰지에 관계없이 반환 값 0을 명시적으로 찾기 위해 사용하면 안 됨).</span><span class="sxs-lookup"><span data-stu-id="b4443-169">You should not use the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to test for equality (that is, to explicitly look for a return value of 0 with no regard for whether one string is less than or greater than the other).</span></span> <span data-ttu-id="b4443-170">대신, 두 문자열이 같은지 여부를 확인하려면 <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-170">Instead, to determine whether two strings are equal, use the <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> method.</span></span>

 <span data-ttu-id="b4443-171">다음 예제에서는 <xref:System.String.CompareTo%2A?displayProperty=nameWithType> 메서드를 사용하여 `string1` 개체를 `string2` 개체와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-171">The following example uses the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method to compare the `string1` object to the `string2` object.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#8)]
 [!code-csharp[Conceptual.String.BasicOps#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#8)]
 [!code-vb[Conceptual.String.BasicOps#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#8)]

 <span data-ttu-id="b4443-172">이 예제에서는 콘솔에 `-1` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-172">This example displays `-1` to the console.</span></span>

 <span data-ttu-id="b4443-173"><xref:System.String.CompareTo%2A?displayProperty=nameWithType> 메서드의 모든 오버로드는 기본적으로 문화권 구분 및 대/소문자 구분 비교 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-173">All overloads of the <xref:System.String.CompareTo%2A?displayProperty=nameWithType> method perform culture-sensitive and case-sensitive comparisons by default.</span></span> <span data-ttu-id="b4443-174">문화권을 구분하지 않는 비교를 수행할 수 있는 이 메서드의 오버로드는 제공되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-174">No overloads of this method are provided that allow you to perform a culture-insensitive comparison.</span></span> <span data-ttu-id="b4443-175">코드를 이해하기 쉽도록 문화권 구분 작업에는 `String.Compare` 를 지정하여 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> String.Compare <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> 메서드를 대신하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-175">For code clarity, we recommend that you use the `String.Compare` method instead, specifying <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> for culture-sensitive operations or <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> for culture-insensitive operations.</span></span> <span data-ttu-id="b4443-176">`String.Compare` 메서드를 사용하여 문화권 구분 비교와 문화권을 구분하지 않는 비교를 둘 다 수행하는 방법을 보여 주는 예제는 [문화권을 구분하지 않는 문자열 비교 수행](../globalization-localization/performing-culture-insensitive-string-comparisons.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b4443-176">For examples that demonstrate how to use the `String.Compare` method to perform both culture-sensitive and culture-insensitive comparisons, see [Performing Culture-Insensitive String Comparisons](../globalization-localization/performing-culture-insensitive-string-comparisons.md).</span></span>

## <a name="equals-method"></a><span data-ttu-id="b4443-177">Equals 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-177">Equals method</span></span>

<span data-ttu-id="b4443-178"><xref:System.String.Equals%2A?displayProperty=nameWithType> 메서드는 두 문자열이 같은지 여부를 쉽게 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-178">The <xref:System.String.Equals%2A?displayProperty=nameWithType> method can easily determine if two strings are the same.</span></span> <span data-ttu-id="b4443-179">대/소문자 구분 메서드는 `true` 또는 `false` 부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-179">This case-sensitive method returns a `true` or `false` Boolean value.</span></span> <span data-ttu-id="b4443-180">다음 예제와 같이 기존 클래스에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-180">It can be used from an existing class, as illustrated in the next example.</span></span> <span data-ttu-id="b4443-181">다음 예제에서는 `Equals` 메서드를 사용하여 문자열 개체에 "Hello World"라는 구가 포함되어 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-181">The following example uses the `Equals` method to determine whether a string object contains the phrase "Hello World".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#9)]
 [!code-csharp[Conceptual.String.BasicOps#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#9)]
 [!code-vb[Conceptual.String.BasicOps#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#9)]

 <span data-ttu-id="b4443-182">이 예제에서는 콘솔에 `True` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-182">This example displays `True` to the console.</span></span>

 <span data-ttu-id="b4443-183">이 메서드는 정적 메서드로 사용될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-183">This method can also be used as a static method.</span></span> <span data-ttu-id="b4443-184">다음 예제에서는 정적 메서드를 사용하여 두 문자열 개체를 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-184">The following example compares two string objects using a static method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#10)]
 [!code-csharp[Conceptual.String.BasicOps#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#10)]
 [!code-vb[Conceptual.String.BasicOps#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#10)]

 <span data-ttu-id="b4443-185">이 예제에서는 콘솔에 `True` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-185">This example displays `True` to the console.</span></span>

## <a name="startswith-and-endswith-methods"></a><span data-ttu-id="b4443-186">StartsWith 및 EndsWith 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-186">StartsWith and EndsWith methods</span></span>

<span data-ttu-id="b4443-187"><xref:System.String.StartsWith%2A?displayProperty=nameWithType> 메서드를 사용하여 문자열 개체가 다른 문자열을 포함하는 동일한 문자로 시작하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-187">You can use the <xref:System.String.StartsWith%2A?displayProperty=nameWithType> method to determine whether a string object begins with the same characters that encompass another string.</span></span> <span data-ttu-id="b4443-188">이 대/소문자 구분 메서드는 현재 문자열 개체가 전달된 문자열로 시작하는 경우 `true`를 반환하고, 전달된 문자열로 시작하지 않는 경우 `false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-188">This case-sensitive method returns `true` if the current string object begins with the passed string and `false` if it does not.</span></span> <span data-ttu-id="b4443-189">다음 예제에서는 이 메서드를 사용하여 문자열 개체가 "Hello"로 시작하는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-189">The following example uses this method to determine if a string object begins with "Hello".</span></span>

 [!code-cpp[Conceptual.String.BasicOps#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#11)]
 [!code-csharp[Conceptual.String.BasicOps#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#11)]
 [!code-vb[Conceptual.String.BasicOps#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#11)]

 <span data-ttu-id="b4443-190">이 예제에서는 콘솔에 `True` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-190">This example displays `True` to the console.</span></span>

 <span data-ttu-id="b4443-191"><xref:System.String.EndsWith%2A?displayProperty=nameWithType> 메서드는 전달된 문자열을 현재 문자열 개체의 끝에 있는 문자와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-191">The <xref:System.String.EndsWith%2A?displayProperty=nameWithType> method compares a passed string to the characters that exist at the end of the current string object.</span></span> <span data-ttu-id="b4443-192">역시 부울 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-192">It also returns a Boolean value.</span></span> <span data-ttu-id="b4443-193">다음 예제에서는 `EndsWith` 메서드를 사용하여 문자열의 끝을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-193">The following example checks the end of a string using the `EndsWith` method.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#12)]
 [!code-csharp[Conceptual.String.BasicOps#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#12)]
 [!code-vb[Conceptual.String.BasicOps#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#12)]

 <span data-ttu-id="b4443-194">이 예제에서는 콘솔에 `False` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-194">This example displays `False` to the console.</span></span>

## <a name="indexof-and-lastindexof-methods"></a><span data-ttu-id="b4443-195">IndexOf 및 LastIndexOf 메서드</span><span class="sxs-lookup"><span data-stu-id="b4443-195">IndexOf and LastIndexOf methods</span></span>

<span data-ttu-id="b4443-196"><xref:System.String.IndexOf%2A?displayProperty=nameWithType> 메서드를 사용하여 문자열 내에서 특정 문자의 첫 번째 발생 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-196">You can use the <xref:System.String.IndexOf%2A?displayProperty=nameWithType> method to determine the position of the first occurrence of a particular character within a string.</span></span> <span data-ttu-id="b4443-197">이 대/소문자 구분 메서드는 문자열의 시작 부분에서 계산을 시작하고 0부터 시작하는 인덱스를 사용하여 전달된 문자의 위치를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-197">This case-sensitive method starts counting from the beginning of a string and returns the position of a passed character using a zero-based index.</span></span> <span data-ttu-id="b4443-198">문자를 찾을 수 없는 경우 -1 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-198">If the character cannot be found, a value of –1 is returned.</span></span>

<span data-ttu-id="b4443-199">다음 예제에서는 `IndexOf` 메서드를 사용하여 문자열에서 '`l`' 문자의 첫 번째 발생을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-199">The following example uses the `IndexOf` method to search for the first occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#13)]
 [!code-csharp[Conceptual.String.BasicOps#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#13)]
 [!code-vb[Conceptual.String.BasicOps#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#13)]

 <span data-ttu-id="b4443-200">이 예제에서는 콘솔에 `2` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-200">This example displays `2` to the console.</span></span>

 <span data-ttu-id="b4443-201"><xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> 메서드는 문자열 내에서 특정 문자가 마지막으로 나온 위치를 반환한다는 점을 제외하고 `String.IndexOf` 메서드와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-201">The <xref:System.String.LastIndexOf%2A?displayProperty=nameWithType> method is similar to the `String.IndexOf` method except that it returns the position of the last occurrence of a particular character within a string.</span></span> <span data-ttu-id="b4443-202">대/소문자를 구분하며 0부터 시작하는 인덱스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-202">It is case-sensitive and uses a zero-based index.</span></span>

 <span data-ttu-id="b4443-203">다음 예제에서는 `LastIndexOf` 메서드를 사용하여 문자열에서 '`l`' 문자의 마지막 발생을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-203">The following example uses the `LastIndexOf` method to search for the last occurrence of the '`l`' character in a string.</span></span>

 [!code-cpp[Conceptual.String.BasicOps#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/compare.cpp#14)]
 [!code-csharp[Conceptual.String.BasicOps#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/compare.cs#14)]
 [!code-vb[Conceptual.String.BasicOps#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/compare.vb#14)]

 <span data-ttu-id="b4443-204">이 예제에서는 콘솔에 `9` 를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-204">This example displays `9` to the console.</span></span>

 <span data-ttu-id="b4443-205">두 메서드는 모두 <xref:System.String.Remove%2A?displayProperty=nameWithType> 메서드와 함께 사용할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-205">Both methods are useful when used in conjunction with the <xref:System.String.Remove%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b4443-206">문자 또는 해당 문자로 시작하는 단어를 제거하기 위해 `IndexOf` 또는 `LastIndexOf` 메서드 중 하나를 사용하여 문자의 위치를 검색한 다음 해당 위치를 `Remove` 메서드에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4443-206">You can use either the `IndexOf` or `LastIndexOf` methods to retrieve the position of a character, and then supply that position to the `Remove` method in order to remove a character or a word that begins with that character.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4443-207">참조</span><span class="sxs-lookup"><span data-stu-id="b4443-207">See also</span></span>

- [<span data-ttu-id="b4443-208">.NET에서 문자열 사용에 대한 모범 사례</span><span class="sxs-lookup"><span data-stu-id="b4443-208">Best Practices for Using Strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="b4443-209">기본적인 문자열 작업</span><span class="sxs-lookup"><span data-stu-id="b4443-209">Basic String Operations</span></span>](basic-string-operations.md)
- [<span data-ttu-id="b4443-210">Culture의 영향을 받지 않는 문자열 작업 수행</span><span class="sxs-lookup"><span data-stu-id="b4443-210">Performing Culture-Insensitive String Operations</span></span>](../globalization-localization/performing-culture-insensitive-string-operations.md)
- <span data-ttu-id="b4443-211">[정렬 가중치 테이블](https://www.microsoft.com/download/details.aspx?id=10921) - Windows에서 .NET Framework 및 .NET Core 1.0~3.1에 사용됩니다</span><span class="sxs-lookup"><span data-stu-id="b4443-211">[Sorting Weight Tables](https://www.microsoft.com/download/details.aspx?id=10921) - used by .NET Framework and .NET Core 1.0-3.1 on Windows</span></span>
- <span data-ttu-id="b4443-212">[기본 유니코드 데이터 정렬 요소 테이블](https://www.unicode.org/Public/UCA/latest/allkeys.txt) - 모든 플랫폼에서 .NET 5에, Linux와 macOS에서 .NET Core에 사용됩니다</span><span class="sxs-lookup"><span data-stu-id="b4443-212">[Default Unicode Collation Element Table](https://www.unicode.org/Public/UCA/latest/allkeys.txt) - used by .NET 5 on all platforms, and by .NET Core on Linux and macOS</span></span>
