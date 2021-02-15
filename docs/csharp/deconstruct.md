---
title: 튜플 및 기타 형식 분해
description: 튜플 및 기타 형식을 분해하는 방법을 알아봅니다.
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 5aaf7157b87de4f67f6e4beba18794a6dd13b6d0
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585353"
---
# <a name="deconstructing-tuples-and-other-types"></a><span data-ttu-id="929b9-103">튜플 및 기타 형식 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-103">Deconstructing tuples and other types</span></span>

<span data-ttu-id="929b9-104">튜플은 메서드 호출에서 여러 값을 검색할 수 있는 간단한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-104">A tuple provides a lightweight way to retrieve multiple values from a method call.</span></span> <span data-ttu-id="929b9-105">하지만 튜플을 검색한 후 튜플의 개별 요소를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-105">But once you retrieve the tuple, you have to handle its individual elements.</span></span> <span data-ttu-id="929b9-106">다음 예제와 같이 요소별로 이 작업을 수행하면 번거롭습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-106">Doing this on an element-by-element basis is cumbersome, as the following example shows.</span></span> <span data-ttu-id="929b9-107">`QueryCityData` 메서드는 3 튜플을 반환하며 각 튜플 요소가 별도의 작업에서 변수에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-107">The `QueryCityData` method returns a 3-tuple, and each of its elements is assigned to a variable in a separate operation.</span></span>

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

<span data-ttu-id="929b9-108">개체에서 여러 필드 및 속성 값을 검색하는 작업도 똑같이 번거로울 수 있습니다. 멤버별로 변수에 필드 또는 속성 값을 할당해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-108">Retrieving multiple field and property values from an object can be equally cumbersome: you have to assign a field or property value to a variable on a member-by-member basis.</span></span>

<span data-ttu-id="929b9-109">C# 7.0부터는 한 번의 *분해* 작업으로 튜플에서 여러 요소를 검색하거나 개체에서 여러 필드, 속성 및 계산 값을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-109">Starting with C# 7.0, you can retrieve multiple elements from a tuple or retrieve multiple field, property, and computed values from an object in a single *deconstruct* operation.</span></span> <span data-ttu-id="929b9-110">튜플을 분해할 때는 튜플 요소를 개별 변수에 할당하고,</span><span class="sxs-lookup"><span data-stu-id="929b9-110">When you deconstruct a tuple, you assign its elements to individual variables.</span></span> <span data-ttu-id="929b9-111">개체를 분해할 때는 선택한 값을 개별 변수에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-111">When you deconstruct an object, you assign selected values to individual variables.</span></span>

## <a name="deconstructing-a-tuple"></a><span data-ttu-id="929b9-112">튜플 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-112">Deconstructing a tuple</span></span>

<span data-ttu-id="929b9-113">C#에서는 튜플 분해를 기본적으로 지원하므로 한 작업에서 튜플의 모든 항목을 패키지 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-113">C# features built-in support for deconstructing tuples, which lets you unpackage all the items in a tuple in a single operation.</span></span> <span data-ttu-id="929b9-114">튜플을 분해하는 일반 구문은 정의하는 구문과 유사합니다. 즉, 대입문 왼쪽에서 각 요소가 할당되는 변수를 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-114">The general syntax for deconstructing a tuple is similar to the syntax for defining one: you enclose the variables to which each element is to be assigned in parentheses in the left side of an assignment statement.</span></span> <span data-ttu-id="929b9-115">예를 들어 다음 문은 4 튜플의 요소를 네 개의 개별 변수에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-115">For example, the following statement assigns the elements of a 4-tuple to four separate variables:</span></span>

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

<span data-ttu-id="929b9-116">다음과 같은 세 가지 방법으로 튜플을 분해합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-116">There are three ways to deconstruct a tuple:</span></span>

- <span data-ttu-id="929b9-117">괄호 안에 각 필드의 형식을 명시적으로 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-117">You can explicitly declare the type of each field inside parentheses.</span></span> <span data-ttu-id="929b9-118">다음 예제에서는 이 방법을 사용하여 `QueryCityData` 메서드에서 반환된 3 튜플을 분해합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-118">The following example uses this approach to deconstruct the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- <span data-ttu-id="929b9-119">C#에서 각 변수의 형식을 유추하도록 `var` 키워드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-119">You can use the `var` keyword so that C# infers the type of each variable.</span></span> <span data-ttu-id="929b9-120">`var` 키워드는 괄호 밖에 놓습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-120">You place the `var` keyword outside of the parentheses.</span></span> <span data-ttu-id="929b9-121">다음 예제에서는 `QueryCityData` 메서드에서 반환된 3 튜플을 분해할 때 형식 유추를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-121">The following example uses type inference when deconstructing the 3-tuple returned by the `QueryCityData` method.</span></span>

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    <span data-ttu-id="929b9-122">괄호 안에 일부 또는 모든 변수 선언에 `var` 키워드를 개별적으로 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-122">You can also use the `var` keyword individually with any or all of the variable declarations inside the parentheses.</span></span>

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    <span data-ttu-id="929b9-123">이 방법은 번거로우므로 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-123">This is cumbersome and is not recommended.</span></span>

- <span data-ttu-id="929b9-124">마지막으로, 튜플을 이미 선언된 변수로 분해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-124">Lastly, you may deconstruct the tuple into variables that have already been declared.</span></span>

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

<span data-ttu-id="929b9-125">튜플에 있는 모든 필드의 형식이 같은 경우에도 괄호 밖에 특정 형식을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-125">Note that you cannot specify a specific type outside the parentheses even if every field in the tuple has the same type.</span></span> <span data-ttu-id="929b9-126">이 경우 컴파일러 오류 CS8136, “Deconstruction 'var (...)' 양식에서는 'var'에 특정 형식을 사용할 수 없습니다.”가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-126">This generates compiler error CS8136, "Deconstruction 'var (...)' form disallows a specific type for 'var'.".</span></span>

<span data-ttu-id="929b9-127">튜플의 각 요소도 변수에 할당해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-127">Note that you must also assign each element of the tuple to a variable.</span></span> <span data-ttu-id="929b9-128">생략하는 요소가 있으면 컴파일러에서 CS8132 오류, “‘x’ 요소의 튜플을 ‘y’ 변수로 분해할 수 없습니다.”가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-128">If you omit any elements, the compiler generates error CS8132, "Cannot deconstruct a tuple of 'x' elements into 'y' variables."</span></span>

<span data-ttu-id="929b9-129">분해의 왼쪽에 있는 기존 변수에 할당 및 선언을 혼합할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-129">Note that you cannot mix declarations and assignments to existing variables on the left-hand side of a deconstruction.</span></span> <span data-ttu-id="929b9-130">컴파일러가 “분해는 왼쪽에 선언과 식을 혼합할 수 없습니다”라는 오류 CS8184를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-130">The compiler generates error CS8184, "a deconstruction cannot mix declarations and expressions on the left-hand-side."</span></span> <span data-ttu-id="929b9-131">구성원이 새로 선언된 변수 및 기존 변수를 포함할 경우.</span><span class="sxs-lookup"><span data-stu-id="929b9-131">when the members include newly declared and existing variables.</span></span>

## <a name="deconstructing-tuple-elements-with-discards"></a><span data-ttu-id="929b9-132">무시 항목을 사용한 튜플 요소 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-132">Deconstructing tuple elements with discards</span></span>

<span data-ttu-id="929b9-133">튜플을 분해할 때 일부 요소 값에만 관심이 있는 경우가 종종 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-133">Often when deconstructing a tuple, you're interested in the values of only some elements.</span></span> <span data-ttu-id="929b9-134">C# 7.0부터는 C#에서 지원하는 *무시 항목* 즉, 무시하도록 선택한 값을 갖는 쓰기 전용 변수를 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-134">Starting with C# 7.0, you can take advantage of C#'s support for *discards*, which are write-only variables whose values you've chosen to ignore.</span></span> <span data-ttu-id="929b9-135">무시 항목은 할당에서 밑줄 문자(“\_”)로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-135">A discard is designated by an underscore character ("\_") in an assignment.</span></span> <span data-ttu-id="929b9-136">원하는 수의 값을 모두 하나의 무시 항목 `_`로 표시하여 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-136">You can discard as many values as you like; all are represented by the single discard, `_`.</span></span>

<span data-ttu-id="929b9-137">다음 예제에서는 무시 항목과 함께 튜플을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-137">The following example illustrates the use of tuples with discards.</span></span> <span data-ttu-id="929b9-138">`QueryCityDataForYears` 메서드는 도시의 이름, 도시의 면적, 연도, 해당 연도의 도시 인구, 두 번째 연도, 해당 두 번째 연도의 도구 인구를 포함하는 6 튜플을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-138">The `QueryCityDataForYears` method returns a 6-tuple with the name of a city, its area, a year, the city's population for that year, a second year, and the city's population for that second year.</span></span> <span data-ttu-id="929b9-139">이 예제는 이러한 두 연도 사이의 인구 변화를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-139">The example shows the change in population between those two years.</span></span> <span data-ttu-id="929b9-140">튜플에서 사용 가능한 데이터 중 도시 면적에는 관심이 없고 디자인 타임에 도시 이름과 두 날짜를 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-140">Of the data available from the tuple, we're unconcerned with the city area, and we know the city name and the two dates at design-time.</span></span> <span data-ttu-id="929b9-141">따라서 튜플에 저장된 두 가지 인구 값에만 관심이 있고 나머지 값은 무시 항목으로 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-141">As a result, we're only interested in the two population values stored in the tuple, and can handle its remaining values as discards.</span></span>  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a><span data-ttu-id="929b9-142">사용자 정의 형식 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-142">Deconstructing user-defined types</span></span>

<span data-ttu-id="929b9-143">C#은 튜플이 아닌 형식의 분해에 대해 기본 제공 지원을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-143">C# does not offer built-in support for deconstructing non-tuple types.</span></span> <span data-ttu-id="929b9-144">그러나 클래스, 구조체 또는 인터페이스의 만든 이는 하나 이상의 `Deconstruct` 메서드를 구현하여 형식의 인스턴스를 분해하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-144">However, as the author of a class, a struct, or an interface, you can allow instances of the type to be deconstructed by implementing one or more `Deconstruct` methods.</span></span> <span data-ttu-id="929b9-145">이 메서드는 void를 반환하며 분해할 각 값은 메서드 시그니처에서 [out](language-reference/keywords/out-parameter-modifier.md) 매개 변수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-145">The method returns void, and each value to be deconstructed is indicated by an [out](language-reference/keywords/out-parameter-modifier.md) parameter in the method signature.</span></span> <span data-ttu-id="929b9-146">예를 들어 다음 `Person` 클래스의 `Deconstruct` 메서드는 이름, 중간 이름 및 성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-146">For example, the following `Deconstruct` method of a `Person` class returns the first, middle, and last name:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

<span data-ttu-id="929b9-147">그러면 다음과 같은 할당을 사용하여 `p`라는 `Person` 클래스의 인스턴스를 분해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-147">You can then deconstruct an instance of the `Person` class named `p` with an assignment like the following:</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

<span data-ttu-id="929b9-148">다음 예제에서는 `Deconstruct` 메서드를 오버로드하여 `Person` 개체의 속성을 다양한 조합으로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-148">The following example overloads the `Deconstruct` method to return various combinations of properties of a `Person` object.</span></span> <span data-ttu-id="929b9-149">개별 오버로드는 다음을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-149">Individual overloads return:</span></span>

- <span data-ttu-id="929b9-150">이름 및 성</span><span class="sxs-lookup"><span data-stu-id="929b9-150">A first and last name.</span></span>
- <span data-ttu-id="929b9-151">성, 중간 이름, 성</span><span class="sxs-lookup"><span data-stu-id="929b9-151">A first, middle, and last name.</span></span>
- <span data-ttu-id="929b9-152">이름, 성, 도시 이름 및 주 이름</span><span class="sxs-lookup"><span data-stu-id="929b9-152">A first name, a last name, a city name, and a state name.</span></span>

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

<span data-ttu-id="929b9-153">매개 변수 수가 같은 여러 `Deconstruct` 메서드는 모호합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-153">Multiple `Deconstruct` methods having the same number of parameters are ambiguous.</span></span> <span data-ttu-id="929b9-154">매개 변수 수, 즉 "인자"가 다른 `Deconstruct` 메서드를 정의하도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-154">You must be careful to define `Deconstruct` methods with different numbers of parameters, or "arity".</span></span> <span data-ttu-id="929b9-155">오버로드 확인 중에 동일한 수의 매개 변수를 가진 `Deconstruct` 메서드를 구분할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-155">`Deconstruct` methods with the same number of parameters cannot be distinguished during overload resolution.</span></span>

## <a name="deconstructing-a-user-defined-type-with-discards"></a><span data-ttu-id="929b9-156">무시 항목을 사용한 사용자 정의 형식 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-156">Deconstructing a user-defined type with discards</span></span>

<span data-ttu-id="929b9-157">[튜플](#deconstructing-tuple-elements-with-discards)에서와 마찬가지로 무시 항목을 사용하여 `Deconstruct` 메서드에서 반환된 항목 중 선택한 항목을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-157">Just as you do with [tuples](#deconstructing-tuple-elements-with-discards), you can use discards to ignore selected items returned by a `Deconstruct` method.</span></span> <span data-ttu-id="929b9-158">각 무시 항목은 “\_”이라는 변수로 정의하며 단일 분해 작업에 여러 무시 항목을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-158">Each discard is defined by a variable named "\_", and a single deconstruction operation can include multiple discards.</span></span>

<span data-ttu-id="929b9-159">다음 예제에서는 `Person` 개체를 4개의 문자열(이름, 성, 도시 및 주)로 분해하지만 성과 주는 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-159">The following example deconstructs a `Person` object into four strings (the first and last names, the city, and the state) but discards the last name and the state.</span></span>

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a><span data-ttu-id="929b9-160">확장 메서드를 사용한 사용자 정의 형식 분해</span><span class="sxs-lookup"><span data-stu-id="929b9-160">Deconstructing a user-defined type with an extension method</span></span>

<span data-ttu-id="929b9-161">클래스, 구조체 또는 인터페이스의 만든 이가 아니더라도 하나 이상의 `Deconstruct` [확장 메서드](programming-guide/classes-and-structs/extension-methods.md) 구현을 통해 해당 형식의 개체를 분해하여 관심 있는 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-161">If you didn't author a class, struct, or interface, you can still deconstruct objects of that type by implementing one or more `Deconstruct` [extension methods](programming-guide/classes-and-structs/extension-methods.md) to return the values in which you're interested.</span></span>

<span data-ttu-id="929b9-162">다음 예제에서는 <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> 클래스에 대한 두 개의 `Deconstruct` 확장 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-162">The following example defines two `Deconstruct` extension methods for the <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="929b9-163">첫 번째 메서드는 속성의 형식, 정적 속성인지 인스턴스 속성인지 여부, 읽기 전용인지 여부, 인덱싱되었는지 여부 등 속성의 특성을 나타내는 값 집합을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-163">The first returns a set of values that indicate the characteristics of the property, including its type, whether it's static or instance, whether it's read-only, and whether it's indexed.</span></span> <span data-ttu-id="929b9-164">두 번째 메서드는 속성의 접근성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-164">The second indicates the property's accessibility.</span></span> <span data-ttu-id="929b9-165">get 및 set 접근자의 접근성이 다를 수 있으므로 부울 값은 속성에 별도의 get 및 set 접근자가 있는지 여부와 있는 경우 접근성이 동일한지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-165">Because the accessibility of get and set accessors can differ, Boolean values indicate whether the property has separate get and set accessors and, if it does, whether they have the same accessibility.</span></span> <span data-ttu-id="929b9-166">접근자가 하나만 있거나 get 및 set 접근자 모두 접근성이 동일한 경우 `access` 변수는 속성 전체의 접근성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-166">If there is only one accessor or both the get and the set accessor have the same accessibility, the `access` variable indicates the accessibility of the property as a whole.</span></span> <span data-ttu-id="929b9-167">그러지 않으면 get 및 set 접근자의 접근성이 `getAccess` 및 `setAccess` 변수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="929b9-167">Otherwise, the accessibility of the get and set accessors are indicated by the `getAccess` and `setAccess` variables.</span></span>

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a><span data-ttu-id="929b9-168">참조</span><span class="sxs-lookup"><span data-stu-id="929b9-168">See also</span></span>

- [<span data-ttu-id="929b9-169">삭제</span><span class="sxs-lookup"><span data-stu-id="929b9-169">Discards</span></span>](discards.md)
- [<span data-ttu-id="929b9-170">튜플 형식</span><span class="sxs-lookup"><span data-stu-id="929b9-170">Tuple types</span></span>](language-reference/builtin-types/value-tuples.md)
