---
title: System.Text.Json을 사용하여 오버플로 JSON을 처리하는 방법
description: .NET에서 JSON으로 직렬화하고 JSON에서 역직렬화할 때 오버플로 JSON을 처리하는 방법을 알아봅니다.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 265ce4f77d353720419122d17c36e508a377b68f
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008918"
---
# <a name="how-to-handle-overflow-json-with-no-locsystemtextjson"></a><span data-ttu-id="2bd0f-103">System.Text.Json을 사용하여 오버플로 JSON을 처리하는 방법</span><span class="sxs-lookup"><span data-stu-id="2bd0f-103">How to handle overflow JSON with System.Text.Json</span></span>

<span data-ttu-id="2bd0f-104">이 문서에서는 `System.Text.Json` 네임스페이스를 사용하여 오버플로 JSON을 처리하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-104">In this article, you will learn how to handle overflow JSON with the `System.Text.Json` namespace.</span></span>

## <a name="handle-overflow-json"></a><span data-ttu-id="2bd0f-105">오버플로 JSON 처리</span><span class="sxs-lookup"><span data-stu-id="2bd0f-105">Handle overflow JSON</span></span>

<span data-ttu-id="2bd0f-106">역직렬화할 때 대상 형식의 속성으로 표시되지 않는 데이터를 JSON에서 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-106">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="2bd0f-107">예를 들어 대상 형식이 다음과 같다고 가정하겠습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-107">For example, suppose your target type is this:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

<span data-ttu-id="2bd0f-108">그리고 역직렬화할 JSON은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-108">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="2bd0f-109">표시된 JSON을 표시된 형식으로 역직렬화하면 `DatesAvailable` 및 `SummaryWords` 속성은 이동할 곳이 없으므로 없어집니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-109">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="2bd0f-110">이러한 속성과 같은 추가 데이터를 캡처하려면 다음과 같이 [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) 특성을 `Dictionary<string,object>` 또는 `Dictionary<string,JsonElement>` 형식의 속성에 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-110">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithExtensionData":::

<span data-ttu-id="2bd0f-111">앞에서 보여드린 JSON을 이 샘플 형식으로 역직렬화하면 추가 데이터는 다음과 같이 `ExtensionData` 속성의 키-값 쌍이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-111">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

| <span data-ttu-id="2bd0f-112">속성</span><span class="sxs-lookup"><span data-stu-id="2bd0f-112">Property</span></span> | <span data-ttu-id="2bd0f-113">값</span><span class="sxs-lookup"><span data-stu-id="2bd0f-113">Value</span></span> | <span data-ttu-id="2bd0f-114">참고</span><span class="sxs-lookup"><span data-stu-id="2bd0f-114">Notes</span></span> |
|--|--|--|
| `Date` | `"8/1/2019 12:00:00 AM -07:00"` |  |
| `TemperatureCelsius` | `0` | <span data-ttu-id="2bd0f-115">대/소문자를 구분하는 불일치(JSON의 `temperatureCelsius`). 따라서 속성이 설정되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-115">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| `Summary` | `"Hot"` |  |
| `ExtensionData` | `temperatureCelsius: 25` | <span data-ttu-id="2bd0f-116">대/소문자가 일치하지 않으므로 이 JSON 속성은 추가 속성이며 사전에서 키-값 쌍이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-116">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span> |
| `DatesAvailable` | `[ "8/1/2019 12:00:00 AM -07:00", "8/2/2019 12:00:00 AM -07:00" ]` | <span data-ttu-id="2bd0f-117">JSON의 추가 속성은 키-값 쌍이 되고, 배열은 값 개체로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-117">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |
| `SummaryWords` | `[ "Cool", "Windy", "Humid" ]` | <span data-ttu-id="2bd0f-118">JSON의 추가 속성은 키-값 쌍이 되고, 배열은 값 개체로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-118">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span> |

<span data-ttu-id="2bd0f-119">대상 개체가 직렬화되면 확장 데이터 키 값 쌍은 마치 수신 JSON에 있는 것처럼 JSON 속성이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-119">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="2bd0f-120">`ExtensionData` 속성 이름은 JSON에 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-120">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="2bd0f-121">이 동작을 통해 JSON은 추가 데이터를 잃지 않고도 라운드트립을 수행할 수 있으며, 이 동작이 없으면 추가 데이터가 역직렬화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2bd0f-121">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="see-also"></a><span data-ttu-id="2bd0f-122">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2bd0f-122">See also</span></span>

* [<span data-ttu-id="2bd0f-123">System.Text.Json 개요</span><span class="sxs-lookup"><span data-stu-id="2bd0f-123">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="2bd0f-124">JSON 직렬화 및 역직렬화 방법</span><span class="sxs-lookup"><span data-stu-id="2bd0f-124">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="2bd0f-125">JsonSerializerOptions 인스턴스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="2bd0f-125">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="2bd0f-126">대/소문자를 구분하지 않는 일치를 사용하도록 설정</span><span class="sxs-lookup"><span data-stu-id="2bd0f-126">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="2bd0f-127">속성 이름 및 값 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="2bd0f-127">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="2bd0f-128">속성 무시</span><span class="sxs-lookup"><span data-stu-id="2bd0f-128">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="2bd0f-129">잘못된 JSON 허용</span><span class="sxs-lookup"><span data-stu-id="2bd0f-129">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="2bd0f-130">참조 유지</span><span class="sxs-lookup"><span data-stu-id="2bd0f-130">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="2bd0f-131">변경할 수 없는 형식 및 public이 아닌 접근자</span><span class="sxs-lookup"><span data-stu-id="2bd0f-131">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="2bd0f-132">다형 직렬화</span><span class="sxs-lookup"><span data-stu-id="2bd0f-132">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="2bd0f-133">Newtonsoft.Json에서 System.Text.Json으로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="2bd0f-133">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="2bd0f-134">문자 인코딩 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="2bd0f-134">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="2bd0f-135">사용자 지정 직렬 변환기 및 역직렬 변환기 작성</span><span class="sxs-lookup"><span data-stu-id="2bd0f-135">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="2bd0f-136">JSON serialization용 사용자 지정 변환기 작성</span><span class="sxs-lookup"><span data-stu-id="2bd0f-136">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="2bd0f-137">DateTime 및 DateTimeOffset 지원</span><span class="sxs-lookup"><span data-stu-id="2bd0f-137">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="2bd0f-138">[System.Text.Json API 참조](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2bd0f-138">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="2bd0f-139">[System.Text.Json.Serialization API 참조](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="2bd0f-139">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
