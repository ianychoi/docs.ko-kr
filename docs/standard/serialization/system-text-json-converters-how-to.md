---
title: JSON serialization용 사용자 지정 변환기를 작성하는 방법 - .NET
description: System.Text.Json 네임스페이스에 제공된 JSON 직렬화 클래스의 사용자 지정 변환기를 만드는 방법을 알아봅니다.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 33334ccd8bad4ac5a9f5dccde79ff3ae09ca8f89
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008866"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="81b03-103">.NET에서 JSON serialization(마샬링)용 사용자 지정 변환기를 작성하는 방법</span><span class="sxs-lookup"><span data-stu-id="81b03-103">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="81b03-104">이 문서에서는 <xref:System.Text.Json> 네임스페이스에 제공된 JSON serialization 클래스에 대한 사용자 지정 변환기를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-104">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="81b03-105">`System.Text.Json`에 대한 소개는 [.NET에서 JSON을 직렬화 및 역직렬화하는 방법](system-text-json-how-to.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-105">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="81b03-106">*변환기* 는 개체 또는 값을 JSON으로 변환하는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-106">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="81b03-107">`System.Text.Json` 네임스페이스에는 JavaScript 기본 형식에 매핑되는 기본 형식 대부분에 대한 기본 제공 변환기가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-107">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="81b03-108">다음과 같은 용도로 사용자 지정 변환기를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-108">You can write custom converters:</span></span>

* <span data-ttu-id="81b03-109">기본 제공 변환기의 기본 동작을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-109">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="81b03-110">예를 들어 `DateTime` 값을 mm/dd/yyyy 형식으로 표시하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-110">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format.</span></span> <span data-ttu-id="81b03-111">기본적으로 RFC 3339 프로필을 포함하여 ISO 8601-1:2019가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-111">By default, ISO 8601-1:2019 is supported, including the RFC 3339 profile.</span></span> <span data-ttu-id="81b03-112">자세한 내용은 [System.Text.Json의 DateTime 및 DateTimeOffset 지원](../datetime/system-text-json-support.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-112">For more information, see [DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md).</span></span>
* <span data-ttu-id="81b03-113">사용자 지정 값 형식을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-113">To support a custom value type.</span></span> <span data-ttu-id="81b03-114">예를 들어 `PhoneNumber` 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-114">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="81b03-115">현재 릴리스에 포함되지 않은 기능을 사용하여 `System.Text.Json`를 사용자 지정하거나 확장하는 사용자 지정 변환기를 작성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-115">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="81b03-116">이 문서의 뒷부분에서 다음과 같은 시나리오에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-116">The following scenarios are covered later in this article:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="81b03-117">[유추된 형식을 개체 속성으로 역직렬화](#deserialize-inferred-types-to-object-properties)</span><span class="sxs-lookup"><span data-stu-id="81b03-117">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="81b03-118">[다형 deserialization 지원](#support-polymorphic-deserialization)</span><span class="sxs-lookup"><span data-stu-id="81b03-118">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="81b03-119">[Stack\<T>에 대한 왕복 지원](#support-round-trip-for-stackt)</span><span class="sxs-lookup"><span data-stu-id="81b03-119">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="81b03-120">[유추된 형식을 개체 속성으로 역직렬화](#deserialize-inferred-types-to-object-properties)</span><span class="sxs-lookup"><span data-stu-id="81b03-120">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="81b03-121">[문자열이 아닌 키를 사용하는 사전 지원](#support-dictionary-with-non-string-key)</span><span class="sxs-lookup"><span data-stu-id="81b03-121">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="81b03-122">[다형 deserialization 지원](#support-polymorphic-deserialization)</span><span class="sxs-lookup"><span data-stu-id="81b03-122">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="81b03-123">[Stack\<T>에 대한 왕복 지원](#support-round-trip-for-stackt)</span><span class="sxs-lookup"><span data-stu-id="81b03-123">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

<span data-ttu-id="81b03-124">사용자 지정 변환기에 대해 작성하는 코드에서는 새 <xref:System.Text.Json.JsonSerializerOptions> 인스턴스를 사용하는 경우 성능 저하에 대해 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-124">In the code you write for a custom converter, be aware of the substantial performance penalty for using new <xref:System.Text.Json.JsonSerializerOptions> instances.</span></span> <span data-ttu-id="81b03-125">자세한 내용은 [JsonSerializerOptions 인스턴스 다시 사용](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-125">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="81b03-126">사용자 지정 변환기 패턴</span><span class="sxs-lookup"><span data-stu-id="81b03-126">Custom converter patterns</span></span>

<span data-ttu-id="81b03-127">사용자 지정 변환기를 만드는 데는 기본 패턴과 팩터리 패턴의 두 가지 패턴이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-127">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="81b03-128">팩터리 패턴은 `Enum` 형식 또는 개방형 제네릭을 처리하는 변환기를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-128">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="81b03-129">기본 패턴은 제네릭이 아닌 형식과 폐쇄형 제네릭 형식을 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-129">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="81b03-130">예를 들어 다음 형식의 변환기에는 팩터리 패턴이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-130">For example, converters for the following types require the factory pattern:</span></span>

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

<span data-ttu-id="81b03-131">기본 패턴으로 처리할 수 있는 형식의 몇 가지 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-131">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

<span data-ttu-id="81b03-132">기본 패턴은 한 형식을 처리할 수 있는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-132">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="81b03-133">팩터리 패턴은 런타임에 특정 형식이 필요한지 여부를 결정하는 클래스를 만들고 적절한 변환기를 동적으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-133">The factory pattern creates a class that determines, at run time, which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="81b03-134">샘플 기본 변환기</span><span class="sxs-lookup"><span data-stu-id="81b03-134">Sample basic converter</span></span>

<span data-ttu-id="81b03-135">다음 샘플은 기존 데이터 형식에 대한 기본 serialization을 재정의하는 변환기입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-135">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="81b03-136">변환기는 `DateTimeOffset` 속성에 mm/dd/yyyy 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-136">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="81b03-137">샘플 팩터리 패턴 변환기</span><span class="sxs-lookup"><span data-stu-id="81b03-137">Sample factory pattern converter</span></span>

<span data-ttu-id="81b03-138">다음 코드에서는 `Dictionary<Enum,TValue>`와 함께 작동하는 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-138">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="81b03-139">첫 번째 제네릭 형식 매개 변수가 `Enum`이고 두 번째는 개방형이기 때문에 이 코드는 팩터리 패턴을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-139">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="81b03-140">`CanConvert` 메서드는 두 개의 제네릭 매개 변수(이 중 첫 번째는 `Enum` 형식)가 있는 `Dictionary`에 대해서만 `true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-140">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="81b03-141">내부 변환기는 런타임에 `TValue`에 제공되는 형식을 처리하기 위해 기존 변환기를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-141">The inner converter gets an existing converter to handle whichever type is provided at run time for `TValue`.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="81b03-142">위의 코드는 이 문서의 뒷부분에 나오는 [문자열이 아닌 키를 사용하는 사전 지원](#support-dictionary-with-non-string-key)에서 보여 주는 것과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-142">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="81b03-143">기본 패턴을 따르기 위한 단계</span><span class="sxs-lookup"><span data-stu-id="81b03-143">Steps to follow the basic pattern</span></span>

<span data-ttu-id="81b03-144">다음 단계에서는 기본 패턴을 따라 변환기를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-144">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="81b03-145"><xref:System.Text.Json.Serialization.JsonConverter%601>에서 파생되는 클래스를 만듭니다. 여기서 `T`는 직렬화 및 역직렬화할 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-145">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="81b03-146">들어오는 JSON을 역직렬화하고 `T` 형식으로 변환하도록 `Read` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-146">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="81b03-147">메서드에 전달된 <xref:System.Text.Json.Utf8JsonReader>를 사용하여 JSON을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-147">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="81b03-148">들어오는 `T` 형식의 개체를 직렬화하도록 `Write` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-148">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="81b03-149">메서드에 전달된 <xref:System.Text.Json.Utf8JsonWriter>를 사용하여 JSON을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-149">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="81b03-150">필요한 경우에만 `CanConvert` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-150">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="81b03-151">기본 구현은 변환할 형식이 `T` 형식일 때 `true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-151">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="81b03-152">따라서 `T` 형식만 지원하는 변환기는 이 메서드를 재정의할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-152">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="81b03-153">이 메서드를 재정의해야 하는 변환기의 예제는 이 문서의 뒷부분에 나오는 [다형 deserialization](#support-polymorphic-deserialization) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-153">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="81b03-154">사용자 지정 변환기 작성을 위한 참조 구현으로 [기본 제공 변환기 소스 코드](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/)를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-154">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="81b03-155">팩터리 패턴을 따르기 위한 단계</span><span class="sxs-lookup"><span data-stu-id="81b03-155">Steps to follow the factory pattern</span></span>

<span data-ttu-id="81b03-156">다음 단계에서는 팩터리 패턴을 따라 변환기를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-156">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="81b03-157"><xref:System.Text.Json.Serialization.JsonConverterFactory>에서 파생되는 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-157">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="81b03-158">변환할 형식이 변환기에서 처리할 수 있는 형식인 경우 true를 반환하도록 `CanConvert` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-158">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="81b03-159">예를 들어 `List<T>`에 대한 변환기인 경우 `List<int>`, `List<string>` 및 `List<DateTime>`만 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-159">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="81b03-160">런타임에 제공되는 변환할 형식을 처리할 변환기 클래스 인스턴스를 반환하도록 `CreateConverter` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-160">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at run time.</span></span>
* <span data-ttu-id="81b03-161">`CreateConverter` 메서드가 인스턴스화하는 변환기 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-161">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="81b03-162">개체와 문자열 간에 변환하는 코드가 모든 형식에 대해 동일하지 않기 때문에 개방형 제네릭에는 팩터리 패턴이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-162">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="81b03-163">개방형 제네릭 형식(예: `List<T>`)에 대한 변환기는 백그라운드에서 폐쇄형 제네릭 형식(예: `List<DateTime>`)에 대한 변환기를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-163">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="81b03-164">변환기가 처리할 수 있는 각 폐쇄형 제네릭 형식을 처리하기 위해 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-164">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="81b03-165">`Enum` 형식은 개방형 제네릭 형식과 유사합니다. `Enum`에 대한 변환기는 내부적으로 특정 `Enum`(예: `WeekdaysEnum`)에 대한 변환기를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-165">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="81b03-166">오류 처리</span><span class="sxs-lookup"><span data-stu-id="81b03-166">Error handling</span></span>

<span data-ttu-id="81b03-167">직렬 변환기는 <xref:System.Text.Json.JsonException> 및 <xref:System.NotSupportedException> 예외 형식을 특별히 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-167">The serializer provides special handling for exception types <xref:System.Text.Json.JsonException> and <xref:System.NotSupportedException>.</span></span>

### <a name="jsonexception"></a><span data-ttu-id="81b03-168">JsonException</span><span class="sxs-lookup"><span data-stu-id="81b03-168">JsonException</span></span>

<span data-ttu-id="81b03-169">메시지 없이 `JsonException`을 throw하는 경우 직렬 변환기는 JSON에서 오류를 발생시킨 부분의 경로를 포함하는 메시지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-169">If you throw a `JsonException` without a message, the serializer creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="81b03-170">예를 들어 `throw new JsonException()` 문은 다음 예제와 같은 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-170">For example, the statement `throw new JsonException()` produces an error message like the following example:</span></span>

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="81b03-171">메시지를 제공하는 경우(예: `throw new JsonException("Error occurred")`) 직렬 변환기는 <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, 및 <xref:System.Text.Json.JsonException.BytePositionInLine> 속성을 계속 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-171">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the serializer still sets the <xref:System.Text.Json.JsonException.Path>, <xref:System.Text.Json.JsonException.LineNumber>, and <xref:System.Text.Json.JsonException.BytePositionInLine> properties.</span></span>

### <a name="notsupportedexception"></a><span data-ttu-id="81b03-172">NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="81b03-172">NotSupportedException</span></span>

<span data-ttu-id="81b03-173">`NotSupportedException`을 throw하는 경우 메시지에 항상 경로 정보를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-173">If you throw a `NotSupportedException`, you always get the path information in the message.</span></span> <span data-ttu-id="81b03-174">메시지를 제공하는 경우 경로 정보가 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-174">If you provide a message, the path information is appended to it.</span></span> <span data-ttu-id="81b03-175">예를 들어 `throw new NotSupportedException("Error occurred.")` 문은 다음 예제와 같은 오류 메시지를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-175">For example, the statement `throw new NotSupportedException("Error occurred.")` produces an error message like the following example:</span></span>

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a><span data-ttu-id="81b03-176">예외 형식을 throw하는 경우</span><span class="sxs-lookup"><span data-stu-id="81b03-176">When to throw which exception type</span></span>

<span data-ttu-id="81b03-177">JSON 페이로드에 역직렬화되는 형식에 유효하지 않은 토큰이 포함된 경우 `JsonException`을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-177">When the JSON payload contains tokens that are not valid for the type being deserialized, throw a `JsonException`.</span></span>

<span data-ttu-id="81b03-178">특정 형식을 허용하지 않으려면 `NotSupportedException`을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-178">When you want to disallow certain types, throw a `NotSupportedException`.</span></span> <span data-ttu-id="81b03-179">이 예외는 직렬 변환기가 지원되지 않는 형식에 대해 자동으로 throw하는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-179">This exception is what the serializer automatically throws for types that are not supported.</span></span> <span data-ttu-id="81b03-180">예를 들어 `System.Type`은 보안상의 이유로 지원되지 않으므로, 역직렬화하려고 하면 `NotSupportedException`이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-180">For example, `System.Type` is not supported for security reasons, so an attempt to deserialize it results in a `NotSupportedException`.</span></span>

<span data-ttu-id="81b03-181">필요에 따라 다른 예외를 throw할 수 있지만, JSON 경로 정보는 자동으로 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-181">You can throw other exceptions as needed, but they don't automatically include JSON path information.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="81b03-182">사용자 지정 변환기 등록</span><span class="sxs-lookup"><span data-stu-id="81b03-182">Register a custom converter</span></span>

<span data-ttu-id="81b03-183">`Serialize` 및 `Deserialize` 메서드가 사용할 수 있도록 사용자 지정 변환기를 *등록* 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-183">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="81b03-184">다음 방법 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-184">Choose one of the following approaches:</span></span>

* <span data-ttu-id="81b03-185"><xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> 컬렉션에 변환기 클래스의 인스턴스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-185">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="81b03-186">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 특성을 사용자 지정 변환기가 필요한 속성에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-186">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="81b03-187">[[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) 특성을 사용자 지정 값 형식을 나타내는 클래스 또는 구조체에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-187">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="81b03-188">등록 샘플 - 변환기 컬렉션</span><span class="sxs-lookup"><span data-stu-id="81b03-188">Registration sample - Converters collection</span></span>

<span data-ttu-id="81b03-189">다음은 <xref:System.ComponentModel.DateTimeOffsetConverter>를 <xref:System.DateTimeOffset> 형식의 속성에 대한 기본값으로 지정하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-189">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

<span data-ttu-id="81b03-190">다음 형식의 인스턴스를 직렬화한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-190">Suppose you serialize an instance of the following type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="81b03-191">다음은 사용자 지정 변환기가 사용되었음을 보여 주는 JSON 출력의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-191">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="81b03-192">다음 코드에서는 사용자 지정 `DateTimeOffset` 변환기를 사용하여 역직렬화하기 위해 동일한 방법을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-192">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="81b03-193">등록 샘플 - 속성에 적용되는 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="81b03-193">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="81b03-194">다음 코드에서는 `Date` 속성에 대한 사용자 지정 변환기를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-194">The following code selects a custom converter for the `Date` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

<span data-ttu-id="81b03-195">`WeatherForecastWithConverterAttribute`를 직렬화하는 코드는 `JsonSerializeOptions.Converters`를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-195">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

<span data-ttu-id="81b03-196">역직렬화하는 코드도 `Converters`를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-196">The code to deserialize also doesn't require the use of `Converters`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="81b03-197">등록 샘플 - 형식에 적용되는 [JsonConverter]</span><span class="sxs-lookup"><span data-stu-id="81b03-197">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="81b03-198">다음은 구조체를 만들고 `[JsonConverter]` 특성을 적용하는 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-198">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

<span data-ttu-id="81b03-199">앞의 구조체에 대한 사용자 지정 변환기는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-199">Here's the custom converter for the preceding struct:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

<span data-ttu-id="81b03-200">구조체의 `[JsonConvert]` 특성은 사용자 지정 변환기를 `Temperature` 형식의 속성에 대한 기본값으로 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-200">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="81b03-201">이 변환기는 다음 형식의 `TemperatureCelsius` 속성을 직렬화 또는 역직렬화할 때 자동으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-201">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a><span data-ttu-id="81b03-202">변환기 등록 우선 순위</span><span class="sxs-lookup"><span data-stu-id="81b03-202">Converter registration precedence</span></span>

<span data-ttu-id="81b03-203">serialization 또는 deserialization 동안 각 JSON 요소에 대해 가장 높은 우선 순위에서 가장 낮은 순서로 변환기가 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-203">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="81b03-204">속성에 적용된 `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="81b03-204">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="81b03-205">`Converters` 컬렉션에 추가된 변환기.</span><span class="sxs-lookup"><span data-stu-id="81b03-205">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="81b03-206">사용자 지정 값 형식 또는 POCO에 적용된 `[JsonConverter]`.</span><span class="sxs-lookup"><span data-stu-id="81b03-206">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="81b03-207">`Converters` 컬렉션에 특정 형식에 대한 여러 사용자 지정 변환기가 등록된 경우 `CanConvert`에 true를 반환하는 첫 번째 변환기가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-207">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="81b03-208">기본 제공 변환기는 해당하는 사용자 지정 변환기가 등록되지 않은 경우에만 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-208">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="81b03-209">일반 시나리오용 변환기 샘플</span><span class="sxs-lookup"><span data-stu-id="81b03-209">Converter samples for common scenarios</span></span>

<span data-ttu-id="81b03-210">다음 섹션에서는 기본 제공 기능이 처리하지 않는 몇 가지 일반적인 시나리오를 해결하는 변환기 샘플을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-210">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="81b03-211">[유추된 형식을 개체 속성으로 역직렬화](#deserialize-inferred-types-to-object-properties)</span><span class="sxs-lookup"><span data-stu-id="81b03-211">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="81b03-212">[다형 deserialization 지원](#support-polymorphic-deserialization)</span><span class="sxs-lookup"><span data-stu-id="81b03-212">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="81b03-213">[Stack\<T>에 대한 왕복 지원](#support-round-trip-for-stackt)</span><span class="sxs-lookup"><span data-stu-id="81b03-213">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="81b03-214">[유추된 형식을 개체 속성으로 역직렬화](#deserialize-inferred-types-to-object-properties)</span><span class="sxs-lookup"><span data-stu-id="81b03-214">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="81b03-215">[문자열이 아닌 키를 사용하는 사전 지원](#support-dictionary-with-non-string-key)</span><span class="sxs-lookup"><span data-stu-id="81b03-215">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="81b03-216">[다형 deserialization 지원](#support-polymorphic-deserialization)</span><span class="sxs-lookup"><span data-stu-id="81b03-216">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="81b03-217">[Stack\<T>에 대한 왕복 지원](#support-round-trip-for-stackt)</span><span class="sxs-lookup"><span data-stu-id="81b03-217">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="81b03-218">유추된 형식을 개체 속성으로 역직렬화</span><span class="sxs-lookup"><span data-stu-id="81b03-218">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="81b03-219">`object` 형식의 속성으로 역직렬화할 때 `JsonElement` 개체가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-219">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="81b03-220">그 이유는 역직렬 변환기가 만들 CLR 형식을 알지 못하고 추측하려고 하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-220">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="81b03-221">예를 들어 JSON 속성에 "true"가 있는 경우 역직렬 변환기는 값이 `Boolean`임을 유추하지 않으며 요소에 "01/01/2019"가 있는 경우 역직렬 변환기가 `DateTime`를 유추하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-221">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="81b03-222">형식 유추는 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-222">Type inference can be inaccurate.</span></span> <span data-ttu-id="81b03-223">역직렬 변환기가 소수점이 없는 JSON 번호를 `long`으로 구문 분석하는 경우 값이 원래 `ulong` 또는 `BigInteger`로 직렬화되었다면 범위를 벗어남 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-223">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="81b03-224">소수점이 있는 숫자를 `double`로 구문 분석하면 해당 숫자가 원래 `decimal`로 직렬화된 경우에는 전체 자릿수가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-224">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="81b03-225">형식 유추가 필요한 시나리오의 경우 다음 코드는 `object` 속성에 대한 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-225">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="81b03-226">이 코드는 다음과 같이 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-226">The code converts:</span></span>

* <span data-ttu-id="81b03-227">`true` 및 `false`를 `Boolean`으로</span><span class="sxs-lookup"><span data-stu-id="81b03-227">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="81b03-228">소수점이 없는 숫자를 `long`으로</span><span class="sxs-lookup"><span data-stu-id="81b03-228">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="81b03-229">소수점이 있는 숫자를 `double`로</span><span class="sxs-lookup"><span data-stu-id="81b03-229">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="81b03-230">날짜를 `DateTime`으로</span><span class="sxs-lookup"><span data-stu-id="81b03-230">Dates to `DateTime`</span></span>
* <span data-ttu-id="81b03-231">문자열을 `string`으로</span><span class="sxs-lookup"><span data-stu-id="81b03-231">Strings to `string`</span></span>
* <span data-ttu-id="81b03-232">그 밖의 모든 항목으로 `JsonElement`로</span><span class="sxs-lookup"><span data-stu-id="81b03-232">Everything else to `JsonElement`</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

<span data-ttu-id="81b03-233">다음 코드는 변환기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-233">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

<span data-ttu-id="81b03-234">다음은 `object` 속성을 사용하는 예제 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-234">Here's an example type with `object` properties:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

<span data-ttu-id="81b03-235">다음의 역직렬화 JSON 예제에는 `DateTime`, `long` 및 `string`으로 역직렬화될 값이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-235">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="81b03-236">사용자 지정 변환기가 없으면 deserialization은 각 속성에 `JsonElement`를 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-236">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="81b03-237">`System.Text.Json.Serialization` 네임스페이스의 [unit tests 폴더](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)에는 `object` 속성에 대한 deserialization을 처리하는 사용자 지정 변환기의 더 많은 예제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-237">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="81b03-238">문자열이 아닌 키를 사용하는 사전 지원</span><span class="sxs-lookup"><span data-stu-id="81b03-238">Support Dictionary with non-string key</span></span>

<span data-ttu-id="81b03-239">사전 컬렉션에 대한 기본 제공 지원은 `Dictionary<string, TValue>`입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-239">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="81b03-240">즉, 키가 문자열이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-240">That is, the key must be a string.</span></span> <span data-ttu-id="81b03-241">정수 또는 다른 형식을 키로 사용하는 사전을 지원하려면 사용자 지정 변환기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-241">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="81b03-242">다음 코드에서는 `Dictionary<Enum,TValue>`와 함께 작동하는 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-242">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

<span data-ttu-id="81b03-243">다음 코드는 변환기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-243">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

<span data-ttu-id="81b03-244">이 변환기는 다음 `Enum`을 사용하는 다음 클래스의 `TemperatureRanges` 속성을 직렬화 및 역직렬화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-244">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

<span data-ttu-id="81b03-245">Serialization의 JSON 출력은 다음 예제와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-245">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="81b03-246">`System.Text.Json.Serialization` 네임스페이스의 [unit tests 폴더](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)에는 비 문자열 키 사전을 처리하는 사용자 지정 변환기의 더 많은 예제가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-246">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>
::: zone-end

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="81b03-247">다형 deserialization 지원</span><span class="sxs-lookup"><span data-stu-id="81b03-247">Support polymorphic deserialization</span></span>

<span data-ttu-id="81b03-248">기본 제공 기능을 통해 제한적으로 [다형 serialization](system-text-json-polymorphism.md)을 제공할 수 있지만 deserialization은 전혀 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-248">Built-in features provide a limited range of [polymorphic serialization](system-text-json-polymorphism.md) but no support for deserialization at all.</span></span> <span data-ttu-id="81b03-249">deserialization을 수행하려면 사용자 지정 변환기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-249">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="81b03-250">예를 들어 `Employee` 및 `Customer` 파생 클래스를 사용하는 `Person` 추상 기본 클래스가 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-250">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="81b03-251">다형성 deserialization은 디자인 타임에 `Person`을 deserialization 대상으로 지정할 수 있고 런타임에 JSON의 `Customer` 및 `Employee` 개체가 올바르게 역직렬화됨을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-251">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at run time.</span></span> <span data-ttu-id="81b03-252">deserialization 동안 JSON에서 필요한 형식을 식별하는 단서를 찾아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-252">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="81b03-253">사용 가능한 단서의 종류는 각 시나리오마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-253">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="81b03-254">예를 들어 판별자 속성을 사용할 수 있거나 특정 속성이 존재하는지 여부에 의존해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-254">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="81b03-255">현재 릴리스의 `System.Text.Json`에서는 다형 deserialization 시나리오를 처리하는 방법을 지정하는 특성을 제공하지 않으므로 사용자 지정 변환기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-255">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="81b03-256">다음 코드에서는 기본 클래스, 두 개의 파생 클래스 및 해당 클래스에 대한 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-256">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="81b03-257">이 변환기는 판별자 속성을 사용하여 다형 deserialization을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-257">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="81b03-258">형식 판별자는 클래스 정의에 없지만 serialization 동안 만들어지고 deserialization 동안 읽힙니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-258">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

<span data-ttu-id="81b03-259">다음 코드는 변환기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-259">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

<span data-ttu-id="81b03-260">변환기는 동일한 직렬화 변환기를 사용하여 만든 JSON을 역직렬화할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-260">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="81b03-261">이전 예제의 변환기 코드는 각 속성을 수동으로 읽고 씁니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-261">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="81b03-262">대신 `Deserialize` 또는 `Serialize`를 호출하여 일부 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-262">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="81b03-263">예제는 [이 StackOverflow 게시물](https://stackoverflow.com/a/59744873/12509023)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-263">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="81b03-264">Stack\<T>에 대한 왕복 지원</span><span class="sxs-lookup"><span data-stu-id="81b03-264">Support round trip for Stack\<T></span></span>

<span data-ttu-id="81b03-265">JSON 문자열을 <xref:System.Collections.Generic.Stack%601> 개체로 역직렬화한 다음 해당 개체를 직렬화하는 경우 스택의 내용이 역순으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-265">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="81b03-266">이 동작은 다음 형식 및 인터페이스, 그리고 이러한 형식에서 파생되는 사용자 정의 형식에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-266">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="81b03-267">스택에서 원래 순서를 유지하는 serialization 및 deserialization을 지원하려면 사용자 지정 변환기가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-267">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="81b03-268">다음 코드는 `Stack<T>` 개체에 대한 라운드트립을 가능하게 하는 사용자 지정 변환기를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-268">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

<span data-ttu-id="81b03-269">다음 코드는 변환기를 등록합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-269">The following code registers the converter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a><span data-ttu-id="81b03-270">Null 값 처리</span><span class="sxs-lookup"><span data-stu-id="81b03-270">Handle null values</span></span>

<span data-ttu-id="81b03-271">기본적으로 직렬 변환기는 null 값을 다음과 같이 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-271">By default, the serializer handles null values as follows:</span></span>

* <span data-ttu-id="81b03-272">참조 형식 및 <xref:System.Nullable%601> 형식:</span><span class="sxs-lookup"><span data-stu-id="81b03-272">For reference types and <xref:System.Nullable%601> types:</span></span>

  * <span data-ttu-id="81b03-273">직렬화 시 사용자 지정 변환기에 `null`을 전달하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-273">It does not pass `null` to custom converters on serialization.</span></span>
  * <span data-ttu-id="81b03-274">역직렬화 시 사용자 지정 변환기에 `JsonTokenType.Null`을 전달하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-274">It does not pass `JsonTokenType.Null` to custom converters on deserialization.</span></span>
  * <span data-ttu-id="81b03-275">역직렬화 시 `null` 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-275">It returns a `null` instance on deserialization.</span></span>
  * <span data-ttu-id="81b03-276">직렬화 시 기록기로 직접 `null`을 씁니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-276">It writes `null` directly with the writer on serialization.</span></span>

* <span data-ttu-id="81b03-277">null을 허용하지 않는 값 형식:</span><span class="sxs-lookup"><span data-stu-id="81b03-277">For non-nullable value types:</span></span>

  * <span data-ttu-id="81b03-278">역직렬화 시 사용자 지정 변환기에 `JsonTokenType.Null`을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-278">It passes `JsonTokenType.Null` to custom converters on deserialization.</span></span> <span data-ttu-id="81b03-279">(사용자 지정 변환기를 사용할 수 없는 경우 형식의 내부 변환기에서 `JsonException` 예외가 throw됩니다.)</span><span class="sxs-lookup"><span data-stu-id="81b03-279">(If no custom converter is available, a `JsonException` exception is thrown by the internal converter for the type.)</span></span>

<span data-ttu-id="81b03-280">이 null 처리 동작은 주로 변환기에 대한 추가 호출을 건너뛰어 성능을 최적화하기 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-280">This null-handling behavior is primarily to optimize performance by skipping an extra call to the converter.</span></span> <span data-ttu-id="81b03-281">또한 nullable 형식의 변환기가 모든 `Read` 및 `Write` 메서드 재정의가 시작될 때 강제로 `null`을 확인하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-281">In addition, it avoids forcing converters for nullable types to check for `null` at the start of every `Read` and `Write` method override.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="81b03-282">사용자 지정 변환기가 참조 또는 값 형식의 `null`을 처리할 수 있게 하려면 다음 예제와 같이 `true`를 반환하도록 <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType>을 재정의하세요.</span><span class="sxs-lookup"><span data-stu-id="81b03-282">To enable a custom converter to handle `null` for a reference or value type, override <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> to return `true`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="19":::
::: zone-end

## <a name="other-custom-converter-samples"></a><span data-ttu-id="81b03-283">기타 사용자 지정 변환기 샘플</span><span class="sxs-lookup"><span data-stu-id="81b03-283">Other custom converter samples</span></span>

<span data-ttu-id="81b03-284">[Newtonsoft.Json에서 System.Text.Json로 마이그레이션](system-text-json-migrate-from-newtonsoft-how-to.md) 문서에는 사용자 지정 변환기의 추가 샘플이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-284">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="81b03-285">`System.Text.Json.Serialization` 소스 코드의 [unit tests 폴더](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/)에는 다음과 같은 다른 사용자 지정 변환기 샘플이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-285">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="81b03-286">[역직렬화할 때 null을 0으로 변환하는 Int32 변환기](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="81b03-286">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="81b03-287">[역직렬화할 때 문자열 및 숫자 값을 모두 허용하는 Int32 변환기](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="81b03-287">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="81b03-288">[Enum 변환기](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="81b03-288">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="81b03-289">외부 데이터를 허용하는 [List\<T> 변환기](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="81b03-289">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="81b03-290">[쉼표로 구분된 숫자 목록과 함께 작동하는 Long[] 변환기](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="81b03-290">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="81b03-291">기존 기본 제공 변환기의 동작을 수정하는 변환기를 만들어야 하는 경우 [기존 변환기의 소스 코드](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)를 가져와 사용자 지정을 위한 시작 지점으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="81b03-291">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="81b03-292">추가 자료</span><span class="sxs-lookup"><span data-stu-id="81b03-292">Additional resources</span></span>

* <span data-ttu-id="81b03-293">[기본 제공 변환기 소스 코드](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="81b03-293">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* [<span data-ttu-id="81b03-294">System.Text.Json 개요</span><span class="sxs-lookup"><span data-stu-id="81b03-294">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="81b03-295">JSON 직렬화 및 역직렬화 방법</span><span class="sxs-lookup"><span data-stu-id="81b03-295">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="81b03-296">JsonSerializerOptions 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="81b03-296">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="81b03-297">대/소문자를 구분하지 않는 일치를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="81b03-297">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="81b03-298">속성 이름 및 값 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="81b03-298">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="81b03-299">속성 무시</span><span class="sxs-lookup"><span data-stu-id="81b03-299">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="81b03-300">잘못된 JSON 허용</span><span class="sxs-lookup"><span data-stu-id="81b03-300">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="81b03-301">오버플로 JSON 처리</span><span class="sxs-lookup"><span data-stu-id="81b03-301">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="81b03-302">참조 유지</span><span class="sxs-lookup"><span data-stu-id="81b03-302">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="81b03-303">변경할 수 없는 형식 및 public이 아닌 접근자</span><span class="sxs-lookup"><span data-stu-id="81b03-303">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="81b03-304">다형 직렬화</span><span class="sxs-lookup"><span data-stu-id="81b03-304">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="81b03-305">Newtonsoft.Json에서 System.Text.Json으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="81b03-305">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="81b03-306">문자 인코딩 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="81b03-306">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="81b03-307">사용자 지정 직렬 변환기 및 역직렬 변환기 작성</span><span class="sxs-lookup"><span data-stu-id="81b03-307">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="81b03-308">DateTime 및 DateTimeOffset 지원</span><span class="sxs-lookup"><span data-stu-id="81b03-308">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="81b03-309">[System.Text.Json API 참조](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="81b03-309">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="81b03-310">[System.Text.Json.Serialization API 참조](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="81b03-310">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
