---
description: '자세한 정보: 날짜 데이터 형식 (Visual Basic)'
title: Date 데이터 형식
ms.date: 07/20/2015
f1_keywords:
- vb.Date
helpviewer_keywords:
- Date data type
- dates [Visual Basic], Visual Basic data types
- times [Visual Basic], Date data type
- Date literals [Visual Basic]
- data values [Visual Basic]
- times [Visual Basic], Visual Basic data types
- dates [Visual Basic], Date data type
- data types [Visual Basic], assigning
- literals [Visual Basic], Date
- '# specifier for Date literals'
ms.assetid: d9edf5b0-e85e-438b-a1cf-1f321e7c831b
ms.openlocfilehash: f6ea6aa99339d13824477bba99ecd211f826a3ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99775021"
---
# <a name="date-data-type-visual-basic"></a><span data-ttu-id="911f8-103">Date 데이터 형식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="911f8-103">Date Data Type (Visual Basic)</span></span>

<span data-ttu-id="911f8-104">0001년 1월 1일부터 9999년 12월 31일까지의 날짜와 오전 12:00:00(자정)부터 오후 11:59:59.9999999까지의 시간을 나타내는 IEEE 64비트(8비트) 값을 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-104">Holds IEEE 64-bit (8-byte) values that represent dates ranging from January 1 of the year 0001 through December 31 of the year 9999, and times from 12:00:00 AM (midnight) through 11:59:59.9999999 PM.</span></span> <span data-ttu-id="911f8-105">각 증분은 일반 달력에서 1년 1월 1일 시작 이후 경과된 시간의 100나노초를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-105">Each increment represents 100 nanoseconds of elapsed time since the beginning of January 1 of the year 1 in the Gregorian calendar.</span></span> <span data-ttu-id="911f8-106">최대값은 10000년 1월 1일 시작 이전 100나노초를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-106">The maximum value represents 100 nanoseconds before the beginning of January 1 of the year 10000.</span></span>

## <a name="remarks"></a><span data-ttu-id="911f8-107">설명</span><span class="sxs-lookup"><span data-stu-id="911f8-107">Remarks</span></span>

<span data-ttu-id="911f8-108">`Date` 데이터 형식을 사용하여 날짜 값, 시간 값 또는 날짜 및 시간 값을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-108">Use the `Date` data type to contain date values, time values, or date and time values.</span></span>

<span data-ttu-id="911f8-109">`Date`의 기본값은 0001년 1월 1일 0:00:00(자정)입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-109">The default value of `Date` is 0:00:00 (midnight) on January 1, 0001.</span></span>

<span data-ttu-id="911f8-110"><xref:Microsoft.VisualBasic.DateAndTime> 클래스에서 현재 날짜와 시간을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-110">You can get the current date and time from the <xref:Microsoft.VisualBasic.DateAndTime> class.</span></span>

## <a name="format-requirements"></a><span data-ttu-id="911f8-111">형식 요구 사항</span><span class="sxs-lookup"><span data-stu-id="911f8-111">Format Requirements</span></span>

<span data-ttu-id="911f8-112">숫자 기호(`# #`) 내의 `Date` 리터럴을 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-112">You must enclose a `Date` literal within number signs (`# #`).</span></span> <span data-ttu-id="911f8-113">M/d/yyyy(예: `#5/31/1993#`) 또는 yyyy-MM-dd(예: `#1993-5-31#`) 형식으로 날짜 값을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-113">You must specify the date value in the format M/d/yyyy, for example `#5/31/1993#`, or yyyy-MM-dd, for example `#1993-5-31#`.</span></span> <span data-ttu-id="911f8-114">연도를 먼저 지정하는 경우 슬래시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-114">You can use slashes when specifying the year first.</span></span>  <span data-ttu-id="911f8-115">이 요구 사항은 사용자 로캘과 컴퓨터의 날짜 및 시간 형식 설정에 독립적입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-115">This requirement is independent of your locale and your computer's date and time format settings.</span></span>

<span data-ttu-id="911f8-116">이러한 제한 이유는 애플리케이션을 실행하는 로캘에 따라 코드의 의미가 변경되면 안 되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-116">The reason for this restriction is that the meaning of your code should never change depending on the locale in which your application is running.</span></span> <span data-ttu-id="911f8-117">`#3/4/1998#`의 `Date` 리터럴을 하드 코딩하고 1998년 3월 4로 지정한다고 가정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="911f8-117">Suppose you hard-code a `Date` literal of `#3/4/1998#` and intend it to mean March 4, 1998.</span></span> <span data-ttu-id="911f8-118">mm/dd/yyyy를 사용하는 로캘에서는 3/4/1998이 의도한 대로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-118">In a locale that uses mm/dd/yyyy, 3/4/1998 compiles as you intend.</span></span> <span data-ttu-id="911f8-119">그러나 여러 국가/지역에 응용 프로그램을 배포 한다고 가정 합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-119">But suppose you deploy your application in many countries/regions.</span></span> <span data-ttu-id="911f8-120">dd/mm/yyyy를 사용하는 로캘에서는 하드 코딩된 리터럴이 1998년 4월 3일로 컴파일됩니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-120">In a locale that uses dd/mm/yyyy, your hard-coded literal would compile to April 3, 1998.</span></span> <span data-ttu-id="911f8-121">yyyy/mm/dd를 사용하는 로캘에서는 리터럴이 잘못 지정되며(0003년 4월 1998일) 컴파일러 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-121">In a locale that uses yyyy/mm/dd, the literal would be invalid (April 1998, 0003) and cause a compiler error.</span></span>

## <a name="workarounds"></a><span data-ttu-id="911f8-122">해결 방법</span><span class="sxs-lookup"><span data-stu-id="911f8-122">Workarounds</span></span>

<span data-ttu-id="911f8-123">`Date` 리터럴을 해당 로캘 형식이나 사용자 지정 형식으로 변환하려면 <xref:Microsoft.VisualBasic.Strings.Format%2A> 함수에 리터럴을 제공하고 미리 정의된 날짜 형식이나 사용자 정의 날짜 형식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-123">To convert a `Date` literal to the format of your locale, or to a custom format, supply the literal to the <xref:Microsoft.VisualBasic.Strings.Format%2A> function, specifying either a predefined or user-defined date format.</span></span> <span data-ttu-id="911f8-124">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-124">The following example demonstrates this.</span></span>

```vb
MsgBox("The formatted date is " & Format(#5/31/1993#, "dddd, d MMM yyyy"))
```

<span data-ttu-id="911f8-125">또는 <xref:System.DateTime> 구조체의 오버로드된 생성자 중 하나를 사용하여 날짜 및 시간 값을 어셈블할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-125">Alternatively, you can use one of the overloaded constructors of the <xref:System.DateTime> structure to assemble a date and time value.</span></span> <span data-ttu-id="911f8-126">다음 예제에서는 1993년 5월 31일 오후 12:14를 나타내는 값을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-126">The following example creates a value to represent May 31, 1993 at 12:14 in the afternoon.</span></span>

```vb
Dim dateInMay As New System.DateTime(1993, 5, 31, 12, 14, 0)
```

## <a name="hour-format"></a><span data-ttu-id="911f8-127">시간 형식</span><span class="sxs-lookup"><span data-stu-id="911f8-127">Hour Format</span></span>

<span data-ttu-id="911f8-128">12시간제 또는 24시간제 형식으로 시간 값을 지정할 수 있습니다(예: `#1:15:30 PM#` 또는 `#13:15:30#`).</span><span class="sxs-lookup"><span data-stu-id="911f8-128">You can specify the time value in either 12-hour or 24-hour format, for example `#1:15:30 PM#` or `#13:15:30#`.</span></span> <span data-ttu-id="911f8-129">그러나 분 또는 초를 지정하지 않는 경우 AM 또는 PM을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-129">However, if you do not specify either the minutes or the seconds, you must specify AM or PM.</span></span>

## <a name="date-and-time-defaults"></a><span data-ttu-id="911f8-130">날짜 및 시간 기본값</span><span class="sxs-lookup"><span data-stu-id="911f8-130">Date and Time Defaults</span></span>

<span data-ttu-id="911f8-131">날짜/시간 리터럴에 날짜를 포함하지 않으면 Visual Basic에서 값의 날짜 부분을 0001년 1월 1일로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-131">If you do not include a date in a date/time literal, Visual Basic sets the date part of the value to January 1, 0001.</span></span> <span data-ttu-id="911f8-132">날짜/시간 리터럴에 시간을 포함하지 않으면 Visual Basic에서 값의 시간 부분을 그 날의 시작, 즉 자정(0:00:00)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-132">If you do not include a time in a date/time literal, Visual Basic sets the time part of the value to the start of the day, that is, midnight (0:00:00).</span></span>

## <a name="type-conversions"></a><span data-ttu-id="911f8-133">형식 변환</span><span class="sxs-lookup"><span data-stu-id="911f8-133">Type Conversions</span></span>

<span data-ttu-id="911f8-134">`Date` 값을 `String` 형식으로 변환하는 경우 Visual Basic에서 런타임 로캘에 지정된 약식 날짜 형식에 따라 날짜를 렌더링하고 런타임 로캘에 지정된 시간 형식(12시간제 또는 24시간제)에 따라 시간을 렌더링합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-134">If you convert a `Date` value to the `String` type, Visual Basic renders the date according to the short date format specified by the run-time locale, and it renders the time according to the time format (either 12-hour or 24-hour) specified by the run-time locale.</span></span>

## <a name="programming-tips"></a><span data-ttu-id="911f8-135">프로그래밍 팁</span><span class="sxs-lookup"><span data-stu-id="911f8-135">Programming Tips</span></span>

- <span data-ttu-id="911f8-136">**Interop 고려 사항.**</span><span class="sxs-lookup"><span data-stu-id="911f8-136">**Interop Considerations.**</span></span> <span data-ttu-id="911f8-137">자동화 개체나 COM 개체와 같이 .NET Framework용으로 작성되지 않은 구성 요소를 조작하는 경우 다른 환경의 날짜/시간 형식이 Visual Basic `Date` 형식과 호환되지 않는 것에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="911f8-137">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that date/time types in other environments are not compatible with the Visual Basic `Date` type.</span></span> <span data-ttu-id="911f8-138">이러한 구성 요소에 날짜/시간 인수를 전달하는 경우 새로운 Visual Basic 코드에서 이 인수를 `Date` 대신 `Double`로 선언하고 변환 메서드 <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> 및 <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-138">If you are passing a date/time argument to such a component, declare it as `Double` instead of `Date` in your new Visual Basic code, and use the conversion methods <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> and <xref:System.DateTime.ToOADate%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="911f8-139">**문자를 입력 합니다.**</span><span class="sxs-lookup"><span data-stu-id="911f8-139">**Type Characters.**</span></span> <span data-ttu-id="911f8-140">`Date` 에는 리터럴 형식 문자 또는 식별자 형식 문자가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-140">`Date` has no literal type character or identifier type character.</span></span> <span data-ttu-id="911f8-141">그러나 컴파일러가 숫자 기호(`# #`)로 묶인 리터럴을 `Date`로 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-141">However, the compiler treats literals enclosed within number signs (`# #`) as `Date`.</span></span>

- <span data-ttu-id="911f8-142">**Framework 형식.**</span><span class="sxs-lookup"><span data-stu-id="911f8-142">**Framework Type.**</span></span> <span data-ttu-id="911f8-143">.NET Framework에서 해당하는 형식은 <xref:System.DateTime?displayProperty=nameWithType> 구조체입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-143">The corresponding type in the .NET Framework is the <xref:System.DateTime?displayProperty=nameWithType> structure.</span></span>

## <a name="example"></a><span data-ttu-id="911f8-144">예제</span><span class="sxs-lookup"><span data-stu-id="911f8-144">Example</span></span>

<span data-ttu-id="911f8-145">`Date` 데이터 형식의 변수 또는 상수는 날짜와 시간을 모두 보유합니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-145">A variable or constant of the `Date` data type holds both the date and the time.</span></span> <span data-ttu-id="911f8-146">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="911f8-146">The following example illustrates this.</span></span>

```vb
Dim someDateAndTime As Date = #8/13/2002 12:14 PM#
```

## <a name="see-also"></a><span data-ttu-id="911f8-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="911f8-147">See also</span></span>

- <xref:System.DateTime?displayProperty=nameWithType>
- [<span data-ttu-id="911f8-148">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="911f8-148">Data Types</span></span>](index.md)
- [<span data-ttu-id="911f8-149">표준 날짜 및 시간 형식 문자열</span><span class="sxs-lookup"><span data-stu-id="911f8-149">Standard Date and Time Format Strings</span></span>](../../../standard/base-types/standard-date-and-time-format-strings.md)
- [<span data-ttu-id="911f8-150">사용자 지정 날짜 및 시간 형식 문자열</span><span class="sxs-lookup"><span data-stu-id="911f8-150">Custom Date and Time Format Strings</span></span>](../../../standard/base-types/custom-date-and-time-format-strings.md)
- [<span data-ttu-id="911f8-151">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="911f8-151">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="911f8-152">변환 요약</span><span class="sxs-lookup"><span data-stu-id="911f8-152">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="911f8-153">데이터 형식의 효율적 사용</span><span class="sxs-lookup"><span data-stu-id="911f8-153">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
