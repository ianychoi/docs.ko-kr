---
title: 세계화 구성 설정
description: '.NET Core 앱의 세계화 측면(예: 일본 날짜를 구문 분석하는 방식)을 구성하는 런타임 설정에 대해 알아봅니다.'
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721917"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="4995a-103">세계화를 위한 런타임 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="4995a-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="4995a-104">고정 모드</span><span class="sxs-lookup"><span data-stu-id="4995a-104">Invariant mode</span></span>

- <span data-ttu-id="4995a-105">.NET Core 앱이 문화권별 데이터와 동작에 액세스하지 않고 세계화 고정 모드에서 실행되는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="4995a-106">이 설정을 생략하면 앱이 문화권 데이터에 액세스할 수 있는 상태로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="4995a-107">이는 값을 `false`로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="4995a-108">자세한 내용은 [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)(.NET Core 세계화 고정 모드)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4995a-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="4995a-109">설정 이름</span><span class="sxs-lookup"><span data-stu-id="4995a-109">Setting name</span></span> | <span data-ttu-id="4995a-110">값</span><span class="sxs-lookup"><span data-stu-id="4995a-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4995a-111">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="4995a-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="4995a-112">`false` - 문화권 데이터에 액세스</span><span class="sxs-lookup"><span data-stu-id="4995a-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="4995a-113">`true` - 고정 모드에서 실행</span><span class="sxs-lookup"><span data-stu-id="4995a-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="4995a-114">**MSBuild 속성**</span><span class="sxs-lookup"><span data-stu-id="4995a-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="4995a-115">`false` - 문화권 데이터에 액세스</span><span class="sxs-lookup"><span data-stu-id="4995a-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="4995a-116">`true` - 고정 모드에서 실행</span><span class="sxs-lookup"><span data-stu-id="4995a-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="4995a-117">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="4995a-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="4995a-118">`0` - 문화권 데이터에 액세스</span><span class="sxs-lookup"><span data-stu-id="4995a-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="4995a-119">`1` - 고정 모드에서 실행</span><span class="sxs-lookup"><span data-stu-id="4995a-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="4995a-120">예</span><span class="sxs-lookup"><span data-stu-id="4995a-120">Examples</span></span>

<span data-ttu-id="4995a-121">*runtimeconfig.json* 파일:</span><span class="sxs-lookup"><span data-stu-id="4995a-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="4995a-122">프로젝트 파일:</span><span class="sxs-lookup"><span data-stu-id="4995a-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="4995a-123">연대 연도 범위</span><span class="sxs-lookup"><span data-stu-id="4995a-123">Era year ranges</span></span>

- <span data-ttu-id="4995a-124">여러 연대를 지원하는 달력의 범위 검사가 완화적인지 아니면 특정 연대의 날짜 범위를 오버플로하는 날짜는 <xref:System.ArgumentOutOfRangeException>을 throw하는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="4995a-125">이 설정을 생략하면 범위 검사가 완화됩니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="4995a-126">이는 값을 `false`로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="4995a-127">자세한 내용은 [달력, 연대 및 날짜 범위: 완화 범위 검사](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4995a-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="4995a-128">설정 이름</span><span class="sxs-lookup"><span data-stu-id="4995a-128">Setting name</span></span> | <span data-ttu-id="4995a-129">값</span><span class="sxs-lookup"><span data-stu-id="4995a-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4995a-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="4995a-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="4995a-131">`false` - 완화 범위 검사</span><span class="sxs-lookup"><span data-stu-id="4995a-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="4995a-132">`true` - 오버플로 시 예외 발생</span><span class="sxs-lookup"><span data-stu-id="4995a-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="4995a-133">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="4995a-133">**Environment variable**</span></span> | <span data-ttu-id="4995a-134">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-134">N/A</span></span> | <span data-ttu-id="4995a-135">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="4995a-136">일본 날짜 구문 분석</span><span class="sxs-lookup"><span data-stu-id="4995a-136">Japanese date parsing</span></span>

- <span data-ttu-id="4995a-137">연도로 “1” 또는 “Gannen”을 포함하는 문자열이 성공적으로 구문 분석되는지 아니면 “1”만 지원되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="4995a-138">이 설정을 생략하면 "1" 또는 "Gannen"를 연도로 포함하는 문자열이 성공적으로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="4995a-139">이는 값을 `false`로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="4995a-140">자세한 내용은 [달력의 날짜를 여러 연대로 표현](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4995a-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="4995a-141">설정 이름</span><span class="sxs-lookup"><span data-stu-id="4995a-141">Setting name</span></span> | <span data-ttu-id="4995a-142">값</span><span class="sxs-lookup"><span data-stu-id="4995a-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4995a-143">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="4995a-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="4995a-144">`false` - “Gannen” 또는 “1”이 지원됨</span><span class="sxs-lookup"><span data-stu-id="4995a-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="4995a-145">`true` - “1”만 지원됨</span><span class="sxs-lookup"><span data-stu-id="4995a-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="4995a-146">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="4995a-146">**Environment variable**</span></span> | <span data-ttu-id="4995a-147">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-147">N/A</span></span> | <span data-ttu-id="4995a-148">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="4995a-149">일본 연도 형식</span><span class="sxs-lookup"><span data-stu-id="4995a-149">Japanese year format</span></span>

- <span data-ttu-id="4995a-150">일본 달력 연대의 첫해의 형식이 “Gannen”으로 지정되는지 아니면 숫자로 지정되는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="4995a-151">이 설정을 생략하면 첫 번째 연도가 "Gannen"으로 서식 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="4995a-152">이는 값을 `false`로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="4995a-153">자세한 내용은 [달력의 날짜를 여러 연대로 표현](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4995a-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="4995a-154">설정 이름</span><span class="sxs-lookup"><span data-stu-id="4995a-154">Setting name</span></span> | <span data-ttu-id="4995a-155">값</span><span class="sxs-lookup"><span data-stu-id="4995a-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="4995a-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="4995a-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="4995a-157">`false` - “Gannen”으로 형식 지정</span><span class="sxs-lookup"><span data-stu-id="4995a-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="4995a-158">`true` - 숫자로 형식 지정</span><span class="sxs-lookup"><span data-stu-id="4995a-158">`true` - format as number</span></span> |
| <span data-ttu-id="4995a-159">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="4995a-159">**Environment variable**</span></span> | <span data-ttu-id="4995a-160">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-160">N/A</span></span> | <span data-ttu-id="4995a-161">N/A</span><span class="sxs-lookup"><span data-stu-id="4995a-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="4995a-162">NLS</span><span class="sxs-lookup"><span data-stu-id="4995a-162">NLS</span></span>

- <span data-ttu-id="4995a-163">.NET에서 Windows 앱에 NLS(국가별 언어 지원) 또는 ICU(International Components for Unicode) 세계화 API를 사용하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="4995a-164">.NET 5.0 이상 버전에서는 기본적으로 Windows 10 2019년 5월 업데이트 이상 버전에 ICU 세계화 API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="4995a-165">이 설정을 생략하면 .NET는 기본적으로 ICU 세계화 API를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="4995a-166">이는 값을 `false`로 설정하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="4995a-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="4995a-167">자세한 내용은 [Windows에서 세계화 API가 ICU 라이브러리를 사용](../compatibility/globalization/5.0/icu-globalization-api.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4995a-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

| | <span data-ttu-id="4995a-168">설정 이름</span><span class="sxs-lookup"><span data-stu-id="4995a-168">Setting name</span></span> | <span data-ttu-id="4995a-169">값</span><span class="sxs-lookup"><span data-stu-id="4995a-169">Values</span></span> | <span data-ttu-id="4995a-170">도입</span><span class="sxs-lookup"><span data-stu-id="4995a-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="4995a-171">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="4995a-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="4995a-172">`false` - ICU 세계화 API를 사용</span><span class="sxs-lookup"><span data-stu-id="4995a-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="4995a-173">`true` - NLS 세계화 API를 사용</span><span class="sxs-lookup"><span data-stu-id="4995a-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="4995a-174">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4995a-174">.NET 5.0</span></span> |
| <span data-ttu-id="4995a-175">**환경 변수**</span><span class="sxs-lookup"><span data-stu-id="4995a-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="4995a-176">`false` - ICU 세계화 API를 사용</span><span class="sxs-lookup"><span data-stu-id="4995a-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="4995a-177">`true` - NLS 세계화 API를 사용</span><span class="sxs-lookup"><span data-stu-id="4995a-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="4995a-178">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="4995a-178">.NET 5.0</span></span> |
