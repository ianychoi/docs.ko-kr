---
title: 부동 소수점 숫자 형식 - C# 참조
description: 기본 제공 C# 부동 소수점 형식인 float, double 및 decimal에 대해 알아보기
ms.date: 02/04/2021
f1_keywords:
- float
- float_CSharpKeyword
- double
- double_CSharpKeyword
- decimal_CSharpKeyword
- decimal
helpviewer_keywords:
- floating-point numbers [C#]
- ranges of floating-point types [C#]
- size of floating-point types [C#]
- types [C#], floating-point types
- float keyword [C#]
- floating-point numbers [C#], float keyword
- double data type [C#]
- decimal keyword [C#]
ms.openlocfilehash: a086e8de60bbb63408c3f2cd557feb36c4baa0f8
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585756"
---
# <a name="floating-point-numeric-types-c-reference"></a><span data-ttu-id="f7bdc-103">부동 소수점 숫자 형식(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="f7bdc-103">Floating-point numeric types (C# reference)</span></span>

<span data-ttu-id="f7bdc-104">*부동 소수점 숫자 형식* 은 실수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-104">The *floating-point numeric types* represent real numbers.</span></span> <span data-ttu-id="f7bdc-105">모든 부동 소수점 숫자 형식은 [값 형식](value-types.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-105">All floating-point numeric types are [value types](value-types.md).</span></span> <span data-ttu-id="f7bdc-106">이것은 [기본 형식](value-types.md#built-in-value-types)이기도 하며, [리터럴](#real-literals)로 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-106">They are also [simple types](value-types.md#built-in-value-types) and can be initialized with [literals](#real-literals).</span></span> <span data-ttu-id="f7bdc-107">모든 부동 소수점 숫자 형식은 [산술](../operators/arithmetic-operators.md), [비교](../operators/comparison-operators.md) 및 [같음](../operators/equality-operators.md) 연산자를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-107">All floating-point numeric types support [arithmetic](../operators/arithmetic-operators.md), [comparison](../operators/comparison-operators.md), and [equality](../operators/equality-operators.md) operators.</span></span>

## <a name="characteristics-of-the-floating-point-types"></a><span data-ttu-id="f7bdc-108">부동 소수점 형식의 특성</span><span class="sxs-lookup"><span data-stu-id="f7bdc-108">Characteristics of the floating-point types</span></span>

<span data-ttu-id="f7bdc-109">C#은 다음과 같은 미리 정의된 부동 소수점 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-109">C# supports the following predefined floating-point types:</span></span>
  
|<span data-ttu-id="f7bdc-110">C# 형식/키워드</span><span class="sxs-lookup"><span data-stu-id="f7bdc-110">C# type/keyword</span></span>|<span data-ttu-id="f7bdc-111">근사 범위</span><span class="sxs-lookup"><span data-stu-id="f7bdc-111">Approximate range</span></span>|<span data-ttu-id="f7bdc-112">전체 자릿수</span><span class="sxs-lookup"><span data-stu-id="f7bdc-112">Precision</span></span>|<span data-ttu-id="f7bdc-113">Size</span><span class="sxs-lookup"><span data-stu-id="f7bdc-113">Size</span></span>|<span data-ttu-id="f7bdc-114">.NET 형식</span><span class="sxs-lookup"><span data-stu-id="f7bdc-114">.NET type</span></span>|
|----------|-----------------------|---------------|--------------|--------------|
|`float`|<span data-ttu-id="f7bdc-115">±1.5 x 10<sup>−45</sup> ~ ±3.4 x 10<sup>38</sup></span><span class="sxs-lookup"><span data-stu-id="f7bdc-115">±1.5 x 10<sup>−45</sup> to ±3.4 x 10<sup>38</sup></span></span>|<span data-ttu-id="f7bdc-116">~6-9개 자릿수</span><span class="sxs-lookup"><span data-stu-id="f7bdc-116">~6-9 digits</span></span>|<span data-ttu-id="f7bdc-117">4바이트</span><span class="sxs-lookup"><span data-stu-id="f7bdc-117">4 bytes</span></span>|<xref:System.Single?displayProperty=nameWithType>|
|`double`|<span data-ttu-id="f7bdc-118">±5.0 × 10<sup>−324</sup> ~ ±1.7 × 10<sup>308</sup></span><span class="sxs-lookup"><span data-stu-id="f7bdc-118">±5.0 × 10<sup>−324</sup> to ±1.7 × 10<sup>308</sup></span></span>|<span data-ttu-id="f7bdc-119">~15-17개 자릿수</span><span class="sxs-lookup"><span data-stu-id="f7bdc-119">~15-17 digits</span></span>|<span data-ttu-id="f7bdc-120">8바이트</span><span class="sxs-lookup"><span data-stu-id="f7bdc-120">8 bytes</span></span>|<xref:System.Double?displayProperty=nameWithType>|
|`decimal`|<span data-ttu-id="f7bdc-121">±1.0 x 10<sup>-28</sup> ~ ±7.9228 x 10<sup>28</sup></span><span class="sxs-lookup"><span data-stu-id="f7bdc-121">±1.0 x 10<sup>-28</sup> to ±7.9228 x 10<sup>28</sup></span></span>|<span data-ttu-id="f7bdc-122">28-29개의 자릿수</span><span class="sxs-lookup"><span data-stu-id="f7bdc-122">28-29 digits</span></span>|<span data-ttu-id="f7bdc-123">16바이트</span><span class="sxs-lookup"><span data-stu-id="f7bdc-123">16 bytes</span></span>|<xref:System.Decimal?displayProperty=nameWithType>|

<span data-ttu-id="f7bdc-124">이전 표에서 맨 왼쪽 열의 각 C# 형식 키워드는 해당하는 .NET 형식의 별칭입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-124">In the preceding table, each C# type keyword from the leftmost column is an alias for the corresponding .NET type.</span></span> <span data-ttu-id="f7bdc-125">서로 교환하여 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-125">They are interchangeable.</span></span> <span data-ttu-id="f7bdc-126">예를 들어 다음 선언은 동일한 형식의 변수를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-126">For example, the following declarations declare variables of the same type:</span></span>

```csharp
double a = 12.3;
System.Double b = 12.3;
```

<span data-ttu-id="f7bdc-127">각 부동 소수점 형식의 기본값은 `0`입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-127">The default value of each floating-point type is zero, `0`.</span></span> <span data-ttu-id="f7bdc-128">각 부동 소수점 형식에는 해당 형식의 최소 및 최대 유한값을 제공하는 `MinValue` 및 `MaxValue` 상수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-128">Each of the floating-point types has the `MinValue` and `MaxValue` constants that provide the minimum and maximum finite value of that type.</span></span> <span data-ttu-id="f7bdc-129">또한 `float` 및 `double` 형식은 숫자가 아닌 무한 값을 나타내는 상수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-129">The `float` and `double` types also provide constants that represent not-a-number and infinity values.</span></span> <span data-ttu-id="f7bdc-130">예를 들어 `double` 형식은 <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> 및 <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>와 같은 상수를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-130">For example, the `double` type provides the following constants: <xref:System.Double.NaN?displayProperty=nameWithType>, <xref:System.Double.NegativeInfinity?displayProperty=nameWithType>, and <xref:System.Double.PositiveInfinity?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f7bdc-131">필요한 전체 자릿수를 소수점 이하 자릿수에 따라 결정하는 경우에는 `decimal` 형식이 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-131">The `decimal` type is appropriate when the required degree of precision is determined by the number of digits to the right of the decimal point.</span></span> <span data-ttu-id="f7bdc-132">이러한 숫자는 일반적으로 재무 애플리케이션에서 통화 금액(예: $1.00), 이자율(예: 2.625%) 등에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-132">Such numbers are commonly used in financial applications, for currency amounts (for example, $1.00), interest rates (for example, 2.625%), and so forth.</span></span> <span data-ttu-id="f7bdc-133">소수점 한 자리 숫자인 경우에도 `decimal` 형식에서 더 정확하게 처리됩니다. 예를 들어 0.1은 `decimal` 인스턴스로 정확하게 표현될 수 있지만 0.1을 정확히 표현하는 `double` 또는 `float` 인스턴스는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-133">Even numbers that are precise to only one decimal digit are handled more accurately by the `decimal` type: 0.1, for example, can be exactly represented by a `decimal` instance, while there's no `double` or `float` instance that exactly represents 0.1.</span></span> <span data-ttu-id="f7bdc-134">10진 데이터에 `double` 또는 `float`를 사용하는 경우 숫자 형식의 차이로 인해 산술 계산에서 예기치 않은 반올림 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-134">Because of this difference in numeric types, unexpected rounding errors can occur in arithmetic calculations when you use `double` or `float` for decimal data.</span></span> <span data-ttu-id="f7bdc-135">성능 최적화가 정확성을 보장하는 것보다 중요한 경우 `decimal` 대신 `double`을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-135">You can use `double` instead of `decimal` when optimizing performance is more important than ensuring accuracy.</span></span> <span data-ttu-id="f7bdc-136">그러나 성능 차이는 계산 집약적인 애플리케이션을 제외한 모든 애플리케이션에서 알지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-136">However, any difference in performance would go unnoticed by all but the most calculation-intensive applications.</span></span> <span data-ttu-id="f7bdc-137">`decimal`을 사용하지 않는 또 다른 가능한 이유는 스토리지 요구 사항을 최소화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-137">Another possible reason to avoid `decimal` is to minimize storage requirements.</span></span> <span data-ttu-id="f7bdc-138">예를 들어 [ML.NET](../../../machine-learning/how-does-mldotnet-work.md)은 `float`를 사용합니다. 규모가 매우 큰 데이터 세트에서는 4바이트와 16바이트의 차이가 증폭되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-138">For example, [ML.NET](../../../machine-learning/how-does-mldotnet-work.md) uses `float` because the difference between 4 bytes and 16 bytes adds up for very large data sets.</span></span> <span data-ttu-id="f7bdc-139">자세한 내용은 <xref:System.Decimal?displayProperty=nameWithType>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-139">For more information, see <xref:System.Decimal?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f7bdc-140">식에서 [정수](integral-numeric-types.md) 형식과 `float` 및 `double` 형식을 혼합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-140">You can mix [integral](integral-numeric-types.md) types and the `float` and `double` types in an expression.</span></span> <span data-ttu-id="f7bdc-141">이 경우 정수 형식이 암시적으로 부동 소수점 형식 중 하나로 변환되며, 필요한 경우 `float` 형식이 암시적으로 `double`로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-141">In this case, integral types are implicitly converted to one of the floating-point types and, if necessary, the `float` type is implicitly converted to `double`.</span></span> <span data-ttu-id="f7bdc-142">이 식은 다음과 같이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-142">The expression is evaluated as follows:</span></span>

- <span data-ttu-id="f7bdc-143">식에 `double` 형식이 있는 경우 식은 관계형 및 같음 비교에서 `double` 또는 [`bool`](bool.md)로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-143">If there is `double` type in the expression, the expression evaluates to `double`, or to [`bool`](bool.md) in relational and equality comparisons.</span></span>
- <span data-ttu-id="f7bdc-144">식에 `double` 형식이 없는 경우 식은 관계형 및 같음 비교에서 `float` 또는 `bool`로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-144">If there is no `double` type in the expression, the expression evaluates to `float`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="f7bdc-145">식에서 정수 형식과 `decimal` 형식을 혼합할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-145">You can also mix integral types and the `decimal` type in an expression.</span></span> <span data-ttu-id="f7bdc-146">이 경우 정수 형식은 암시적으로 `decimal` 형식으로 변환되고 식은 관계형 및 같음 비교에서 `decimal` 또는 `bool`로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-146">In this case, integral types are implicitly converted to the `decimal` type and the expression evaluates to `decimal`, or to `bool` in relational and equality comparisons.</span></span>

<span data-ttu-id="f7bdc-147">식에서 `decimal` 형식을 `float` 및 `double` 형식과 혼합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-147">You cannot mix the `decimal` type with the `float` and `double` types in an expression.</span></span> <span data-ttu-id="f7bdc-148">이 경우 산술, 비교 또는 같음 연산을 수행하려면 다음 예제와 같이 명시적으로 피연산자를 `decimal` 형식으로 변환하거나 반대로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-148">In this case, if you want to perform arithmetic, comparison, or equality operations, you must explicitly convert the operands either from or to the `decimal` type, as the following example shows:</span></span>

```csharp-interactive
double a = 1.0;
decimal b = 2.1m;
Console.WriteLine(a + (double)b);
Console.WriteLine((decimal)a + b);
```

<span data-ttu-id="f7bdc-149">[표준 숫자 서식 문자열](../../../standard/base-types/standard-numeric-format-strings.md) 또는 [사용자 지정 숫자 서식 문자열](../../../standard/base-types/custom-numeric-format-strings.md)을 사용하여 부동 소수점 값의 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-149">You can use either [standard numeric format strings](../../../standard/base-types/standard-numeric-format-strings.md) or [custom numeric format strings](../../../standard/base-types/custom-numeric-format-strings.md) to format a floating-point value.</span></span>

## <a name="real-literals"></a><span data-ttu-id="f7bdc-150">real 리터럴</span><span class="sxs-lookup"><span data-stu-id="f7bdc-150">Real literals</span></span>

<span data-ttu-id="f7bdc-151">real 리터럴의 형식은 접미사로 다음과 같이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-151">The type of a real literal is determined by its suffix as follows:</span></span>

- <span data-ttu-id="f7bdc-152">접미사가 없거나 `d` 또는 `D` 접미사가 있는 리터럴은 `double` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-152">The literal without suffix or with the `d` or `D` suffix is of type `double`</span></span>
- <span data-ttu-id="f7bdc-153">`f` 또는 `F` 접미사가 있는 리터럴은 `float` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-153">The literal with the `f` or `F` suffix is of type `float`</span></span>
- <span data-ttu-id="f7bdc-154">`m` 또는 `M` 접미사가 있는 리터럴은 `decimal` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-154">The literal with the `m` or `M` suffix is of type `decimal`</span></span>

<span data-ttu-id="f7bdc-155">다음 코드에서는 각 예제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-155">The following code demonstrates an example of each:</span></span>

```csharp
double d = 3D;
d = 4d;
d = 3.934_001;

float f = 3_000.5F;
f = 5.4f;

decimal myMoney = 3_000.5m;
myMoney = 400.75M;
```

<span data-ttu-id="f7bdc-156">앞의 예제에서는 C# 7.0부터 지원되는 *숫자 구분 기호* 인 `_`를 사용하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-156">The preceding example also shows the use of `_` as a *digit separator*, which is supported starting with C# 7.0.</span></span> <span data-ttu-id="f7bdc-157">모든 종류의 숫자 리터럴에서 숫자 구분 기호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-157">You can use the digit separator with all kinds of numeric literals.</span></span>

<span data-ttu-id="f7bdc-158">또한 다음 예제와 같이 과학적 표기법을 사용하여 real 리터럴의 지수 부분을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-158">You can also use scientific notation, that is, specify an exponent part of a real literal, as the following example shows:</span></span>

```csharp-interactive
double d = 0.42e2;
Console.WriteLine(d);  // output 42

float f = 134.45E-2f;
Console.WriteLine(f);  // output: 1.3445

decimal m = 1.5E6m;
Console.WriteLine(m);  // output: 1500000
```

## <a name="conversions"></a><span data-ttu-id="f7bdc-159">변환</span><span class="sxs-lookup"><span data-stu-id="f7bdc-159">Conversions</span></span>

<span data-ttu-id="f7bdc-160">부동 소수점 숫자 형식 간의 암시적 변환은 `float`에서 `double`로의 암시적 변환 하나뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-160">There is only one implicit conversion between floating-point numeric types: from `float` to `double`.</span></span> <span data-ttu-id="f7bdc-161">그러나 [명시적 캐스트](../operators/type-testing-and-cast.md#cast-expression)를 사용하여 부동 소수점 형식을 다른 부동 소수점 형식으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-161">However, you can convert any floating-point type to any other floating-point type with the [explicit cast](../operators/type-testing-and-cast.md#cast-expression).</span></span> <span data-ttu-id="f7bdc-162">자세한 내용은 [기본 제공 숫자 변환](numeric-conversions.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-162">For more information, see [Built-in numeric conversions](numeric-conversions.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f7bdc-163">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="f7bdc-163">C# language specification</span></span>

<span data-ttu-id="f7bdc-164">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 다음 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f7bdc-164">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f7bdc-165">부동 소수점 형식</span><span class="sxs-lookup"><span data-stu-id="f7bdc-165">Floating-point types</span></span>](~/_csharplang/spec/types.md#floating-point-types)
- [<span data-ttu-id="f7bdc-166">10진 형식</span><span class="sxs-lookup"><span data-stu-id="f7bdc-166">The decimal type</span></span>](~/_csharplang/spec/types.md#the-decimal-type)
- [<span data-ttu-id="f7bdc-167">real 리터럴</span><span class="sxs-lookup"><span data-stu-id="f7bdc-167">Real literals</span></span>](~/_csharplang/spec/lexical-structure.md#real-literals)

## <a name="see-also"></a><span data-ttu-id="f7bdc-168">참조</span><span class="sxs-lookup"><span data-stu-id="f7bdc-168">See also</span></span>

- [<span data-ttu-id="f7bdc-169">C# 참조</span><span class="sxs-lookup"><span data-stu-id="f7bdc-169">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f7bdc-170">값 형식</span><span class="sxs-lookup"><span data-stu-id="f7bdc-170">Value types</span></span>](value-types.md)
- [<span data-ttu-id="f7bdc-171">정수 형식</span><span class="sxs-lookup"><span data-stu-id="f7bdc-171">Integral types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f7bdc-172">표준 숫자 형식 문자열</span><span class="sxs-lookup"><span data-stu-id="f7bdc-172">Standard numeric format strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="f7bdc-173">.NET의 숫자</span><span class="sxs-lookup"><span data-stu-id="f7bdc-173">Numerics in .NET</span></span>](../../../standard/numerics.md)
- <xref:System.Numerics.Complex?displayProperty=nameWithType>
