---
title: '방법: 날짜 및 시간 값 왕복'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- round-trip date and time values
- dates [.NET], round-trip values
- time zones [.NET], round-trip date and time values
- time [.NET], round-trip values
- formatting strings [.NET], round-trip values
ms.assetid: b609b277-edc6-4c74-b03e-ea73324ecbdb
ms.openlocfilehash: 243ed98972f834c207331770f9d0202ddb60d4e6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821972"
---
# <a name="how-to-round-trip-date-and-time-values"></a><span data-ttu-id="ba0bf-102">방법: 날짜 및 시간 값 왕복</span><span class="sxs-lookup"><span data-stu-id="ba0bf-102">How to: Round-trip Date and Time Values</span></span>

<span data-ttu-id="ba0bf-103">많은 애플리케이션에서 날짜 및 시간 값은 단일 시점을 명확하게 식별하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-103">In many applications, a date and time value is intended to unambiguously identify a single point in time.</span></span> <span data-ttu-id="ba0bf-104">이 문서에서는 복원된 값이 저장된 값과 같은 시간을 식별할 수 있도록 <xref:System.DateTime> 값, <xref:System.DateTimeOffset> 값 그리고 표준 시간대 정보가 있는 날짜 및 시간 값을 저장하고 복원하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-104">This article shows how to save and restore a <xref:System.DateTime> value, a <xref:System.DateTimeOffset> value, and a date and time value with time zone information so that the restored value identifies the same time as the saved value.</span></span>

## <a name="round-trip-a-datetime-value"></a><span data-ttu-id="ba0bf-105">DateTime 값 왕복</span><span class="sxs-lookup"><span data-stu-id="ba0bf-105">Round-trip a DateTime value</span></span>

1. <span data-ttu-id="ba0bf-106">“o” 형식 지정자와 함께 <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> 메서드를 호출하여 <xref:System.DateTime> 값을 해당 문자열 표현으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-106">Convert the <xref:System.DateTime> value to its string representation by calling the <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="ba0bf-107"><xref:System.DateTime> 값의 문자열 표현을 파일에 저장하거나 프로세스, 애플리케이션 도메인 또는 컴퓨터 경계를 넘어 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-107">Save the string representation of the <xref:System.DateTime> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="ba0bf-108"><xref:System.DateTime> 값을 나타내는 문자열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-108">Retrieve the string that represents the <xref:System.DateTime> value.</span></span>

4. <span data-ttu-id="ba0bf-109"><xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> 메서드를 호출하고 `styles` 매개 변수의 값으로 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-109">Call the <xref:System.DateTime.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="ba0bf-110">다음 예제는 <xref:System.DateTime> 값을 왕복하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-110">The following example illustrates how to round-trip a <xref:System.DateTime> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#1)]
[!code-vb[Formatting.HowTo.RoundTrip#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#1)]

<span data-ttu-id="ba0bf-111"><xref:System.DateTime> 값을 왕복할 경우 이 기술은 모든 현지 시간 및 세계시에 대한 시간을 성공적으로 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-111">When round-tripping a <xref:System.DateTime> value, this technique successfully preserves the time for all local and universal times.</span></span> <span data-ttu-id="ba0bf-112">예를 들어 로컬 <xref:System.DateTime> 값이 미국에 있는 시스템에 저장되는 경우입니다. 태평양 표준 시간대는 미국에 있는 시스템에서 복원됩니다. 중앙 표준 시간대인 복원된 날짜 및 시간은 원래 시간보다 2시간이 늦어지며 이것은 두 표준 시간대 사이의 시간 차이를 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-112">For example, if a local <xref:System.DateTime> value is saved on a system in the U.S. Pacific Standard Time zone and is restored on a system in the U.S. Central Standard Time zone, the restored date and time will be two hours later than the original time, which reflects the time difference between the two time zones.</span></span> <span data-ttu-id="ba0bf-113">그러나 이 기술은 지정되지 않은 시간에 대해 반드시 정확하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-113">However, this technique is not necessarily accurate for unspecified times.</span></span> <span data-ttu-id="ba0bf-114"><xref:System.DateTime.Kind%2A> 속성이 <xref:System.DateTimeKind.Unspecified>인 모든 <xref:System.DateTime> 값은 로컬 시간인 것처럼 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-114">All <xref:System.DateTime> values whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Unspecified> are treated as if they are local times.</span></span> <span data-ttu-id="ba0bf-115">로컬 시간이 아닌 경우 <xref:System.DateTime>은 올바른 시점을 성공적으로 식별하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-115">If it's not a local time, the <xref:System.DateTime> doesn't successfully identify the correct point in time.</span></span> <span data-ttu-id="ba0bf-116">이 제한에 대한 해결책은 저장 및 복원 작업의 표준 시간대와 날짜 및 시간 값을 밀접하게 연결하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-116">The workaround for this limitation is to tightly couple a date and time value with its time zone for the save and restore operation.</span></span>

## <a name="round-trip-a-datetimeoffset-value"></a><span data-ttu-id="ba0bf-117">DateTimeOffset 값 왕복</span><span class="sxs-lookup"><span data-stu-id="ba0bf-117">Round-trip a DateTimeOffset value</span></span>

1. <span data-ttu-id="ba0bf-118">“o” 형식 지정자와 함께 <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> 메서드를 호출하여 <xref:System.DateTimeOffset> 값을 해당 문자열 표현으로 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-118">Convert the <xref:System.DateTimeOffset> value to its string representation by calling the <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType> method with the "o" format specifier.</span></span>

2. <span data-ttu-id="ba0bf-119"><xref:System.DateTimeOffset> 값의 문자열 표현을 파일에 저장하거나 프로세스, 애플리케이션 도메인 또는 컴퓨터 경계를 넘어 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-119">Save the string representation of the <xref:System.DateTimeOffset> value to a file, or pass it across a process, application domain, or machine boundary.</span></span>

3. <span data-ttu-id="ba0bf-120"><xref:System.DateTimeOffset> 값을 나타내는 문자열을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-120">Retrieve the string that represents the <xref:System.DateTimeOffset> value.</span></span>

4. <span data-ttu-id="ba0bf-121"><xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> 메서드를 호출하고 `styles` 매개 변수의 값으로 <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType>를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-121">Call the <xref:System.DateTimeOffset.Parse%28System.String%2CSystem.IFormatProvider%2CSystem.Globalization.DateTimeStyles%29?displayProperty=nameWithType> method, and pass <xref:System.Globalization.DateTimeStyles.RoundtripKind?displayProperty=nameWithType> as the value of the `styles` parameter.</span></span>

<span data-ttu-id="ba0bf-122">다음 예제는 <xref:System.DateTimeOffset> 값을 왕복하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-122">The following example illustrates how to round-trip a <xref:System.DateTimeOffset> value.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#2)]
[!code-vb[Formatting.HowTo.RoundTrip#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#2)]

<span data-ttu-id="ba0bf-123">이 기술은 <xref:System.DateTimeOffset> 값을 항상 단일 시점으로 명확하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-123">This technique always unambiguously identifies a <xref:System.DateTimeOffset> value as a single point in time.</span></span> <span data-ttu-id="ba0bf-124">그런 다음, <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> 메서드를 호출하여 값을 UTC(협정 세계시)로 변환하거나 <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> 또는 <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> 메서드를 호출하여 값을 특정 표준 시간대의 시간으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-124">The value can then be converted to Coordinated Universal Time (UTC) by calling the <xref:System.DateTimeOffset.ToUniversalTime%2A?displayProperty=nameWithType> method, or it can be converted to the time in a particular time zone by calling the <xref:System.DateTimeOffset.ToOffset%2A?displayProperty=nameWithType> or <xref:System.TimeZoneInfo.ConvertTime%28System.DateTimeOffset%2CSystem.TimeZoneInfo%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ba0bf-125">이 기술의 주요 제한은 특정 표준 시간대의 시간을 나타내는 <xref:System.DateTimeOffset> 값에 대해 날짜 및 시간 연산을 수행하면 해당 표준 시간대에 대해 정확한 결과를 얻을 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-125">The major limitation of this technique is that date and time arithmetic, when performed on a <xref:System.DateTimeOffset> value that represents the time in a particular time zone, may not produce accurate results for that time zone.</span></span> <span data-ttu-id="ba0bf-126">이는 <xref:System.DateTimeOffset> 값이 인스턴스화될 때 해당 표준 시간대에서 분리되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-126">This is because when a <xref:System.DateTimeOffset> value is instantiated, it is disassociated from its time zone.</span></span> <span data-ttu-id="ba0bf-127">따라서 날짜 및 시간 계산을 수행할 경우에 해당 표준 시간대의 조정 규칙은 더 이상 적용될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-127">Therefore, that time zone's adjustment rules can no longer be applied when you perform date and time calculations.</span></span> <span data-ttu-id="ba0bf-128">날짜 및 시간 값과 동반되는 표준 시간대를 포함하는 사용자 지정 형식을 정의하여 이 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-128">You can work around this problem by defining a custom type that includes both a date and time value and its accompanying time zone.</span></span>

## <a name="round-trip-a-date-and-time-value-with-its-time-zone"></a><span data-ttu-id="ba0bf-129">표준 시간대를 사용하여 날짜 및 시간 값 왕복</span><span class="sxs-lookup"><span data-stu-id="ba0bf-129">Round-trip a date and time value with its time zone</span></span>

1. <span data-ttu-id="ba0bf-130">두 필드가 있는 클래스 또는 구조체를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-130">Define a class or a structure with two fields.</span></span> <span data-ttu-id="ba0bf-131">첫 번째 필드는 <xref:System.DateTime> 또는 <xref:System.DateTimeOffset> 개체이며, 두 번째 필드는 <xref:System.TimeZoneInfo> 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-131">The first field is either a <xref:System.DateTime> or a <xref:System.DateTimeOffset> object, and the second is a <xref:System.TimeZoneInfo> object.</span></span> <span data-ttu-id="ba0bf-132">다음 예제는 이러한 형식의 단순 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-132">The following example is a simple version of such a type.</span></span>

    [!code-csharp[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#3)]
    [!code-vb[Formatting.HowTo.RoundTrip#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#3)]

2. <span data-ttu-id="ba0bf-133"><xref:System.SerializableAttribute> 특성을 사용하여 클래스를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-133">Mark the class with the <xref:System.SerializableAttribute> attribute.</span></span>

3. <span data-ttu-id="ba0bf-134"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> 메서드를 사용하여 개체를 직렬화합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-134">Serialize the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType> method.</span></span>

4. <span data-ttu-id="ba0bf-135"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> 메서드를 사용하여 개체를 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-135">Restore the object using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A> method.</span></span>

5. <span data-ttu-id="ba0bf-136">역직렬화된 개체를 적절한 형식의 개체로 캐스트(C#에서)하거나 변환(Visual Basic에서)합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-136">Cast (in C#) or convert (in Visual Basic) the deserialized object to an object of the appropriate type.</span></span>

<span data-ttu-id="ba0bf-137">다음 예제에서는 날짜 및 시간 정보와 표준 시간대 정보를 모두 저장하는 개체를 왕복하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-137">The following example illustrates how to round-trip an object that stores both time zone and date and time information.</span></span>

[!code-csharp[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/cs/RoundTrip.cs#4)]
[!code-vb[Formatting.HowTo.RoundTrip#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.RoundTrip/vb/RoundTrip.vb#4)]

<span data-ttu-id="ba0bf-138">날짜 및 시간과 표준 시간대 개체 결합의 구현으로 인해 날짜 값이 표준 시간대 값과 동기화되지 않게 된 경우 이 기술은 저장 및 복원 이전과 이후에 모두 올바른 시점을 항상 명확하게 반영해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-138">This technique should always unambiguously reflect the correct point of time both before and after it is saved and restored, provided that the implementation of the combined date and time and time zone object does not allow the date value to become out of sync with the time zone value.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="ba0bf-139">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="ba0bf-139">Compile the code</span></span>

<span data-ttu-id="ba0bf-140">관련 예제에서는 다음이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-140">These examples require that:</span></span>

- <span data-ttu-id="ba0bf-141">C# `using` 지시문 또는 Visual Basic `Imports` 문을 사용하여 다음 네임스페이스를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-141">The following namespaces be imported with C# `using` directives or Visual Basic `Imports` statements:</span></span>

  - <span data-ttu-id="ba0bf-142"><xref:System>(C#만 해당)</span><span class="sxs-lookup"><span data-stu-id="ba0bf-142"><xref:System> (C# only)</span></span>

  - <xref:System.Globalization?displayProperty=nameWithType>

  - <xref:System.IO?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Formatters.Binary?displayProperty=nameWithType>

- <span data-ttu-id="ba0bf-143">`DateInTimeZone` 클래스 이외의 각 코드 예제가 클래스 또는 Visual Basic 모듈에 포함되어야 하며, 메서드에 래핑되고, `Main` 메서드에서 호출되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ba0bf-143">Each code example, other than the `DateInTimeZone` class, be included in a class or Visual Basic module, wrapped in methods, and called from the `Main` method.</span></span>

## <a name="see-also"></a><span data-ttu-id="ba0bf-144">참조</span><span class="sxs-lookup"><span data-stu-id="ba0bf-144">See also</span></span>

- [<span data-ttu-id="ba0bf-145">DateTime, DateTimeOffset, TimeSpan 및 TimeZoneInfo 중 선택</span><span class="sxs-lookup"><span data-stu-id="ba0bf-145">Choosing Between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo</span></span>](../datetime/choosing-between-datetime.md)
- [<span data-ttu-id="ba0bf-146">표준 날짜 및 시간 형식 문자열</span><span class="sxs-lookup"><span data-stu-id="ba0bf-146">Standard Date and Time Format Strings</span></span>](standard-date-and-time-format-strings.md)
