---
title: .NET Core의 EventCounters
description: 이 문서에서는 EventCounters의 정의, 구현 방법 및 사용 방법에 대해 알아봅니다.
ms.date: 08/07/2020
ms.openlocfilehash: 843f1ec645bf7f52fd4f85e30d183e6e21fee5c6
ms.sourcegitcommit: 78eb25647b0c750cd80354ebd6ce83a60668e22c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2021
ms.locfileid: "99065066"
---
# <a name="eventcounters-in-net-core"></a><span data-ttu-id="bce8e-103">.NET Core의 EventCounters</span><span class="sxs-lookup"><span data-stu-id="bce8e-103">EventCounters in .NET Core</span></span>

<span data-ttu-id="bce8e-104">**이 문서의 적용 대상:** ✔️ .NET Core 3.0 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="bce8e-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="bce8e-105">EventCounters는 경량, 플랫폼 간 및 근 실시간 성능 메트릭 컬렉션에 사용되는 .NET Core API입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-105">EventCounters are .NET Core APIs used for lightweight, cross-platform, and near real-time performance metric collection.</span></span> <span data-ttu-id="bce8e-106">EventCounters는 Windows에서 .NET Framework의 “성능 카운터”에 대한 교차 플랫폼 대체 항목으로 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-106">EventCounters were added as a cross-platform alternative to the "performance counters" of the .NET Framework on Windows.</span></span> <span data-ttu-id="bce8e-107">이 문서에서는 EventCounters의 정의, 구현 방법 및 사용 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-107">In this article you'll learn what EventCounters are, how to implement them, and how to consume them.</span></span>

<span data-ttu-id="bce8e-108">.Net Core 런타임 및 일부 .NET 라이브러리는 .NET Core 3.0부터 EventCounters를 사용하여 기본 진단 정보를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-108">The .NET Core runtime and a few .NET libraries publish basic diagnostics information using EventCounters starting in .NET Core 3.0.</span></span> <span data-ttu-id="bce8e-109">.NET 런타임에서 제공하는 EventCounters 외에도 고유한 EventCounters를 구현하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-109">Apart from the EventCounters that are provided by the .NET runtime, you may choose to implement your own EventCounters.</span></span> <span data-ttu-id="bce8e-110">EventCounters를 사용하여 다양한 메트릭을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-110">EventCounters can be used to track various metrics.</span></span> <span data-ttu-id="bce8e-111">[.NET의 잘 알려진 EventCounters](available-counters.md)에서 자세히 알아보세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-111">Learn more about them in the [well-known EventCounters in .NET](available-counters.md)</span></span>

<span data-ttu-id="bce8e-112">EventCounters는 <xref:System.Diagnostics.Tracing.EventSource>의 일부로 사용되며, 주기적으로 수신기 도구에 자동으로 푸시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-112">EventCounters live as a part of an <xref:System.Diagnostics.Tracing.EventSource>, and are automatically pushed to listener tools on a regular basis.</span></span> <span data-ttu-id="bce8e-113"><xref:System.Diagnostics.Tracing.EventSource>의 다른 모든 이벤트와 마찬가지로 <xref:System.Diagnostics.Tracing.EventListener> 및 [EventPipe](./eventpipe.md)를 통해 in-proc 및 out-of-proc에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-113">Like all other events on an <xref:System.Diagnostics.Tracing.EventSource>, they can be consumed both in-proc and out-of-proc via <xref:System.Diagnostics.Tracing.EventListener> and [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="bce8e-114">이 문서에서는 EventCounters의 교차 플랫폼 기능을 중점적으로 설명하며, PerfView 및 ETW(Windows용 이벤트 추적)를 둘 다 EventCounters와 함께 사용할 수 있지만 여기서는 의도적으로 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-114">This article focuses on the cross-platform capabilities of EventCounters, and intentionally excludes PerfView and ETW (Event Tracing for Windows) - although both can be used with EventCounters.</span></span>

![EventCounters in-proc 및 out-of-proc 다이어그램 이미지](media/event-counters.svg)

## <a name="eventcounter-api-overview"></a><span data-ttu-id="bce8e-116">EventCounter API 개요</span><span class="sxs-lookup"><span data-stu-id="bce8e-116">EventCounter API overview</span></span>

<span data-ttu-id="bce8e-117">카운터에는 두 가지 기본 범주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-117">There are two primary categories of counters.</span></span> <span data-ttu-id="bce8e-118">일부는 총 예외 수, 총 GC 수, 총 요청 수 등의 “비율” 값에 대한 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-118">Some counters are for "rate" values, such as total number of exceptions, total number of GCs, and total number of requests.</span></span> <span data-ttu-id="bce8e-119">힙 사용량, CPU 사용량, 작업 세트 크기 등의 “스냅샷” 값에 대한 카운터도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-119">Other counters are "snapshot" values, such as heap usage, CPU usage, and working set size.</span></span> <span data-ttu-id="bce8e-120">이러한 각 카운터 범주 내에는 값을 가져오는 방법에 따라 두 가지 유형의 카운터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-120">Within each of these categories of counters, there are two types of counters that vary by how they get their value.</span></span> <span data-ttu-id="bce8e-121">폴링 카운터는 콜백을 통해 해당 값을 검색하고 비폴링 카운터는 카운터 인스턴스에서 직접 해당 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-121">Polling counters retrieve their value via a callback, and non-polling counters have their values directly set on the counter instance.</span></span>

<span data-ttu-id="bce8e-122">카운터는 다음 구현으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-122">The counters are represented by the following implementations:</span></span>

* <xref:System.Diagnostics.Tracing.EventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingEventCounter>
* <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>
* <xref:System.Diagnostics.Tracing.PollingCounter>

<span data-ttu-id="bce8e-123">이벤트 수신기는 측정 간격의 길이를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-123">An event listener specifies how long measurement intervals are.</span></span> <span data-ttu-id="bce8e-124">각 간격의 끝에서 각 카운터에 대한 수신기로 값이 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-124">At the end of each interval a value is transmitted to the listener for each counter.</span></span> <span data-ttu-id="bce8e-125">카운터의 구현에 따라 각 간격 값을 생성하는 데 사용되는 API 및 계산이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-125">The implementations of a counter determine what APIs and calculations are used to produce the value each interval.</span></span>

1. <span data-ttu-id="bce8e-126"><xref:System.Diagnostics.Tracing.EventCounter>는 값 세트를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-126">The <xref:System.Diagnostics.Tracing.EventCounter> records a set of values.</span></span> <span data-ttu-id="bce8e-127"><xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> 메서드는 세트에 새 값을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-127">The <xref:System.Diagnostics.Tracing.EventCounter.WriteMetric%2A?displayProperty=nameWithType> method adds a new value to the set.</span></span> <span data-ttu-id="bce8e-128">간격마다 min, max 및 mean과 같은 세트에 대한 통계 요약이 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-128">With each interval, a statistical summary for the set is computed, such as the min, max, and mean.</span></span> <span data-ttu-id="bce8e-129">[dotnet-counters](dotnet-counters.md) 도구는 항상 평균 값을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-129">The [dotnet-counters](dotnet-counters.md) tool will always display the mean value.</span></span> <span data-ttu-id="bce8e-130"><xref:System.Diagnostics.Tracing.EventCounter>는 불연속 작업 세트를 설명하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-130">The <xref:System.Diagnostics.Tracing.EventCounter> is useful to describe a discrete set of operations.</span></span> <span data-ttu-id="bce8e-131">일반적인 사용에는 최근 IO 작업의 평균 크기(바이트) 또는 재무 트랜잭션 세트의 평균 통화 값 모니터링이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-131">Common usage may include monitoring the average size in bytes of recent IO operations, or the average monetary value of a set of financial transactions.</span></span>

1. <span data-ttu-id="bce8e-132"><xref:System.Diagnostics.Tracing.IncrementingEventCounter>는 각 시간 간격의 누계를 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-132">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> records a running total for each time interval.</span></span> <span data-ttu-id="bce8e-133"><xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> 메서드는 더하여 합계를 구합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-133">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter.Increment%2A?displayProperty=nameWithType> method adds to the total.</span></span> <span data-ttu-id="bce8e-134">예를 들어 값 `1`, `2` 및 `5`를 사용하여 하나의 간격 동안 `Increment()`를 세 번 호출하는 경우 `8`의 누계는 이 간격의 카운터 값으로 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-134">For example, if `Increment()` is called three times during one interval with values `1`, `2`, and `5`, then the running total of `8` will be reported as the counter value for this interval.</span></span> <span data-ttu-id="bce8e-135">[dotnet-counters](dotnet-counters.md) 도구는 이 비율을 기록된 합계/시간으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-135">The [dotnet-counters](dotnet-counters.md) tool will display the rate as the recorded total / time.</span></span> <span data-ttu-id="bce8e-136"><xref:System.Diagnostics.Tracing.IncrementingEventCounter>는 초당 처리된 요청 수와 같이 작업이 발생하는 빈도를 측정하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-136">The <xref:System.Diagnostics.Tracing.IncrementingEventCounter> is useful to measure how frequently an action is occurring, such as the number of requests processed per second.</span></span>

1. <span data-ttu-id="bce8e-137"><xref:System.Diagnostics.Tracing.PollingCounter>는 콜백을 사용하여 보고되는 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-137">The <xref:System.Diagnostics.Tracing.PollingCounter> uses a callback to determine the value that is reported.</span></span> <span data-ttu-id="bce8e-138">시간 간격마다 사용자가 제공한 콜백 함수가 호출되고 반환 값이 카운터 값으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-138">With each time interval, the user provided callback function is invoked and the return value is used as the counter value.</span></span> <span data-ttu-id="bce8e-139"><xref:System.Diagnostics.Tracing.PollingCounter>를 사용하여 외부 소스에서 메트릭을 쿼리할 수 있습니다. 예를 들어 디스크의 현재 사용 가능한 바이트를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-139">A <xref:System.Diagnostics.Tracing.PollingCounter> can be used to query a metric from an external source, for example getting the current free bytes on a disk.</span></span> <span data-ttu-id="bce8e-140">애플리케이션에서 요청 시에 계산될 수 있는 사용자 지정 통계를 보고하는 데도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-140">It can also be used to report custom statistics that can be computed on demand by an application.</span></span> <span data-ttu-id="bce8e-141">최근 요청 대기 시간의 95번째 백분위 수, 캐시의 현재 적중 또는 누락 비율을 보고하는 경우를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-141">Examples include reporting the 95th percentile of recent request latencies, or the current hit or miss ratio of a cache.</span></span>

1. <span data-ttu-id="bce8e-142"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter>는 콜백을 사용하여 보고된 증분 값을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-142">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses a callback to determine the reported increment value.</span></span> <span data-ttu-id="bce8e-143">시간 간격마다 콜백이 호출된 다음, 현재 호출과 마지막 호출 간의 차이가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-143">With each time interval, the callback is invoked, and then the difference between the current invocation, and the last invocation is the reported value.</span></span> <span data-ttu-id="bce8e-144">[dotnet-counters](dotnet-counters.md) 도구는 항상 차이를 보고된 값/시간 비율로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-144">The [dotnet-counters](dotnet-counters.md) tool will always display the difference as a rate, the reported value / time.</span></span> <span data-ttu-id="bce8e-145">이 카운터는 발생할 때마다 API를 호출하는 것이 불가능하지만 총 발생 횟수를 쿼리할 수 있는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-145">This counter is useful when it isn't feasible to call an API on each occurrence, but it's possible to query the total number of occurrences.</span></span> <span data-ttu-id="bce8e-146">예를 들어 바이트를 쓸 때마다 알림이 표시되지 않더라도 초당 파일에 쓴 바이트 수를 보고할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-146">For example, you could report the number of bytes written to a file per second, even without a notification each time a byte is written.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="bce8e-147">EventSource 구현</span><span class="sxs-lookup"><span data-stu-id="bce8e-147">Implement an EventSource</span></span>

<span data-ttu-id="bce8e-148">다음 코드에서는 명명된 `"Sample.EventCounter.Minimal"` 공급자로 노출되는 샘플 <xref:System.Diagnostics.Tracing.EventSource>를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-148">The following code implements a sample <xref:System.Diagnostics.Tracing.EventSource> exposed as the named `"Sample.EventCounter.Minimal"` provider.</span></span> <span data-ttu-id="bce8e-149">이 소스에는 요청 처리 시간을 나타내는 <xref:System.Diagnostics.Tracing.EventCounter>가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-149">This source contains an <xref:System.Diagnostics.Tracing.EventCounter> representing request processing time.</span></span> <span data-ttu-id="bce8e-150">이러한 카운터에는 이름(즉, 소스의 고유 ID)과 표시 이름이 있으며 둘 다 [dotnet-counter](dotnet-counters.md)와 같은 수신기 도구에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-150">Such a counter has a name (that is, its unique ID in the source) and a display name, both used by listener tools such as [dotnet-counter](dotnet-counters.md).</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="bce8e-151">`dotnet-counters ps`를 사용하여 모니터링할 수 있는 .NET 프로세스의 목록을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-151">You use `dotnet-counters ps` to display a list of .NET processes that can be monitored:</span></span>

```console
dotnet-counters ps
   1398652 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399072 dotnet     C:\Program Files\dotnet\dotnet.exe
   1399112 dotnet     C:\Program Files\dotnet\dotnet.exe
   1401880 dotnet     C:\Program Files\dotnet\dotnet.exe
   1400180 sample-counters C:\sample-counters\bin\Debug\netcoreapp3.1\sample-counters.exe
```

<span data-ttu-id="bce8e-152"><xref:System.Diagnostics.Tracing.EventSource> 이름을 `--counters` 옵션에 전달하여 카운터 모니터링을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-152">Pass the <xref:System.Diagnostics.Tracing.EventSource> name to the `--counters` option to start monitoring your counter:</span></span>

```console
dotnet-counters monitor --process-id 1400180 --counters Sample.EventCounter.Minimal
```

<span data-ttu-id="bce8e-153">다음 예제에서는 모니터 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-153">The following example shows monitor output:</span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Samples-EventCounterDemos-Minimal]
    Request Processing Time (ms)                            0.445
```

<span data-ttu-id="bce8e-154"><kbd>q</kbd>를 눌러 모니터링 명령을 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-154">Press <kbd>q</kbd> to stop the monitoring command.</span></span>

#### <a name="conditional-counters"></a><span data-ttu-id="bce8e-155">조건부 카운터</span><span class="sxs-lookup"><span data-stu-id="bce8e-155">Conditional counters</span></span>

<span data-ttu-id="bce8e-156"><xref:System.Diagnostics.Tracing.EventSource>를 구현할 때 `EventCommand.Enable`의 <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> 값을 사용하여 <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> 메서드가 호출되는 경우 포함하는 카운터를 조건부로 인스턴스화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-156">When implementing an <xref:System.Diagnostics.Tracing.EventSource>, the containing counters can be conditionally instantiated when the <xref:System.Diagnostics.Tracing.EventSource.OnEventCommand%2A?displayProperty=nameWithType> method is called with a <xref:System.Diagnostics.Tracing.EventCommandEventArgs.Command> value of `EventCommand.Enable`.</span></span> <span data-ttu-id="bce8e-157">`null`인 경우에만 카운터 인스턴스를 안전하게 인스턴스화하려면 [null 병합 대입 연산자](../../csharp/language-reference/operators/null-coalescing-operator.md)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-157">To safely instantiate a counter instance only if it is `null`, use the [null-coalescing assignment operator](../../csharp/language-reference/operators/null-coalescing-operator.md).</span></span> <span data-ttu-id="bce8e-158">또한 사용자 지정 메서드는 <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> 메서드를 평가하여 현재 이벤트 소스를 사용할 수 있는지를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-158">Additionally, custom methods can evaluate the <xref:System.Diagnostics.DiagnosticSource.IsEnabled%2A> method to determine whether or not the current event source is enabled.</span></span>

:::code language="csharp" source="snippets/EventCounters/ConditionalEventCounterSource.cs":::

> [!TIP]
> <span data-ttu-id="bce8e-159">조건부 카운터는 조건부로 인스턴스화되는 마이크로 최적화에 해당하는 카운터입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-159">Conditional counters are counters that are conditionally instantiated, a micro-optimization.</span></span> <span data-ttu-id="bce8e-160">런타임에서는 카운터가 일반적으로 사용되지 않는 시나리오에 대해 이 패턴을 사용하여 시간(밀리초)을 절약합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-160">The runtime adopts this pattern for scenarios where counters are normally not used, to save a fraction of a millisecond.</span></span>

### <a name="net-core-runtime-example-counters"></a><span data-ttu-id="bce8e-161">.NET Core 런타임 예제 카운터</span><span class="sxs-lookup"><span data-stu-id="bce8e-161">.NET Core runtime example counters</span></span>

<span data-ttu-id="bce8e-162">.NET Core 런타임에는 많은 유용한 예제 구현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-162">There are many great example implementations in the .NET Core runtime.</span></span> <span data-ttu-id="bce8e-163">다음은 애플리케이션의 작업 세트 크기를 추적하는 카운터에 대한 런타임 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-163">Here is the runtime implementation for the counter that tracks the working set size of the application.</span></span>

```csharp
var workingSetCounter = new PollingCounter(
    "working-set",
    this,
    () => (double)(Environment.WorkingSet / 1_000_000))
{
    DisplayName = "Working Set",
    DisplayUnits = "MB"
};
```

<span data-ttu-id="bce8e-164"><xref:System.Diagnostics.Tracing.PollingCounter>는 특정 시점에 메트릭을 캡처하기 때문에 앱의 프로세스(작업 세트)에 매핑되는 실제 메모리의 현재 크기를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-164">The <xref:System.Diagnostics.Tracing.PollingCounter> reports the current amount of physical memory mapped to the process (working set) of the app, since it captures a metric at a moment in time.</span></span> <span data-ttu-id="bce8e-165">값 폴링에 대한 콜백은 제공된 람다 식으로, <xref:System.Environment.WorkingSet?displayProperty=fullName> API에 대한 호출에 불과합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-165">The callback for polling a value is the provided lambda expression, which is just a call to the <xref:System.Environment.WorkingSet?displayProperty=fullName> API.</span></span> <span data-ttu-id="bce8e-166"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> 및 <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits>는 카운터의 소비자 쪽에서 값을 보다 명확하게 표시하는 데 도움이 되도록 설정할 수 있는 선택적 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-166"><xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayName> and <xref:System.Diagnostics.Tracing.DiagnosticCounter.DisplayUnits> are optional properties that can be set to help the consumer side of the counter to display the value more clearly.</span></span> <span data-ttu-id="bce8e-167">예를 들어 [dotnet-counters](dotnet-counters.md)는 이러한 속성을 사용하여 좀 더 친숙한 카운터 이름 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-167">For example, [dotnet-counters](dotnet-counters.md) uses these properties to display the more display-friendly version of the counter names.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bce8e-168">`DisplayName` 속성은 지역화되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-168">The `DisplayName` properties are not localized.</span></span>

<span data-ttu-id="bce8e-169"><xref:System.Diagnostics.Tracing.PollingCounter> 및 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>의 경우 다른 작업을 수행할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-169">For the <xref:System.Diagnostics.Tracing.PollingCounter>, and the <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>, nothing else needs to be done.</span></span> <span data-ttu-id="bce8e-170">소비자가 요청한 간격으로 값 자체를 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-170">They both poll the values themselves at an interval requested by the consumer.</span></span>

<span data-ttu-id="bce8e-171"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter>를 사용하여 구현된 런타임 카운터의 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-171">Here is an example of a runtime counter implemented using <xref:System.Diagnostics.Tracing.IncrementingPollingCounter>.</span></span>

```csharp
var monitorContentionCounter = new IncrementingPollingCounter(
    "monitor-lock-contention-count",
    this,
    () => Monitor.LockContentionCount
)
{
    DisplayName = "Monitor Lock Contention Count",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

<span data-ttu-id="bce8e-172"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter>는 <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API를 사용하여 총 잠금 경합 수의 증분을 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-172">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> uses the <xref:System.Threading.Monitor.LockContentionCount?displayProperty=nameWithType> API to report the increment of the total lock contention count.</span></span> <span data-ttu-id="bce8e-173"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> 속성은 선택 사항이지만 이 속성을 사용하면 카운터가 가장 잘 표시되는 시간 간격에 대한 힌트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-173">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> property is optional, but when used it can provide a hint for what time interval the counter is best displayed at.</span></span> <span data-ttu-id="bce8e-174">예를 들어 잠금 경합 횟수는 ‘초당 횟수’로 가장 잘 표시되므로 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>은 1초로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-174">For example, the lock contention count is best displayed as _count per second_, so its <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is set to one second.</span></span> <span data-ttu-id="bce8e-175">표시 비율은 다른 유형의 비율 카운터에 맞게 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-175">The display rate can be adjusted for different types of rate counters.</span></span>

> [!NOTE]
> <span data-ttu-id="bce8e-176"><xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale>은 [dotnet-counters](dotnet-counters.md)에서 사용되지 ‘않으며’ 이를 사용하는 데 이벤트 수신기가 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-176">The <xref:System.Diagnostics.Tracing.IncrementingPollingCounter.DisplayRateTimeScale> is _not_ used by [dotnet-counters](dotnet-counters.md), and event listeners are not required to use it.</span></span>

<span data-ttu-id="bce8e-177">[.NET 런타임](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) 리포지토리에 참조로 사용할 수 있는 더 많은 카운터 구현이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-177">There are more counter implementations to use as a reference in the [.NET runtime](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/Diagnostics/Tracing/RuntimeEventSource.cs) repo.</span></span>

## <a name="concurrency"></a><span data-ttu-id="bce8e-178">동시성</span><span class="sxs-lookup"><span data-stu-id="bce8e-178">Concurrency</span></span>

> [!TIP]
> <span data-ttu-id="bce8e-179">EventCounters API는 스레드 보안을 보장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-179">The EventCounters API does not guarantee thread safety.</span></span> <span data-ttu-id="bce8e-180"><xref:System.Diagnostics.Tracing.PollingCounter> 또는 <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> 인스턴스에 전달된 대리자가 여러 스레드에서 호출되는 경우 대리자가 스레드로부터 안전한지 보장하는 것은 사용자의 책임입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-180">When the delegates passed to <xref:System.Diagnostics.Tracing.PollingCounter> or <xref:System.Diagnostics.Tracing.IncrementingPollingCounter> instances are called by multiple threads, it's your responsibility to guarantee the delegates' thread-safety.</span></span>

<span data-ttu-id="bce8e-181">예를 들어 다음 <xref:System.Diagnostics.Tracing.EventSource>를 사용하여 요청을 추적하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-181">For example, consider the following <xref:System.Diagnostics.Tracing.EventSource> to keep track of requests.</span></span>

:::code language="csharp" source="snippets/EventCounters/RequestEventSource.cs":::

<span data-ttu-id="bce8e-182">`AddRequest()` 메서드는 요청 처리기에서 호출될 수 있으며, `RequestRateCounter`는 카운터 소비자가 지정한 간격에 따라 값을 폴링합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-182">The `AddRequest()` method can be called from a request handler, and the `RequestRateCounter` polls the value at the interval specified by the consumer of the counter.</span></span> <span data-ttu-id="bce8e-183">그러나 한 번에 여러 스레드에서 `AddRequest()` 메서드를 호출하여 `_requestCount`가 경합 상태가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-183">However, the `AddRequest()` method can be called by multiple threads at once, putting a race condition on `_requestCount`.</span></span> <span data-ttu-id="bce8e-184">스레드로부터 안전하게 `_requestCount`를 증분하는 방법은 <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-184">A thread-safe alternative way to increment the `_requestCount` is to use <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>.</span></span>

```csharp
public void AddRequest() => Interlocked.Increment(ref _requestCount);
```

<span data-ttu-id="bce8e-185">`long` 필드 `_requestCount`의 읽기 중단(32비트 아키텍처)을 방지하려면 <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-185">To prevent torn reads (on 32-bit architectures) of the `long`-field `_requestCount` use <xref:System.Threading.Interlocked.Read%2A?displayProperty=nameWithType>.</span></span>

```csharp
_requestRateCounter = new IncrementingPollingCounter("request-rate", this, () => Interlocked.Read(ref _requestCount))
{
    DisplayName = "Request Rate",
    DisplayRateTimeScale = TimeSpan.FromSeconds(1)
};
```

## <a name="consume-eventcounters"></a><span data-ttu-id="bce8e-186">EventCounters 사용</span><span class="sxs-lookup"><span data-stu-id="bce8e-186">Consume EventCounters</span></span>

<span data-ttu-id="bce8e-187">EventCounters를 사용하는 두 가지 기본 방법은 in-proc 또는 out-of-proc입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-187">There are two primary ways of consuming EventCounters, either in-proc, or out-of-proc.</span></span> <span data-ttu-id="bce8e-188">EventCounters의 사용은 세 가지 계층의 다양한 사용 기술로 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-188">The consumption of EventCounters can be distinguished into three layers of various consuming technologies.</span></span>

- <span data-ttu-id="bce8e-189">ETW 또는 EventPipe를 통해 원시 스트림에서 이벤트 전송:</span><span class="sxs-lookup"><span data-stu-id="bce8e-189">Transporting events in a raw stream via ETW or EventPipe:</span></span>
  - <span data-ttu-id="bce8e-190">ETW API는 Windows OS와 함께 제공되며 EventPipe는 [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console) 또는 진단 [IPC 프로토콜](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md)로서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-190">ETW APIs come with the Windows OS, and EventPipe is accessible as a [.NET API](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/diagnostics-client-library.md#1-attaching-to-a-process-and-dumping-out-all-the-runtime-gc-events-in-real-time-to-the-console), or the diagnostic [IPC protocol](https://github.com/dotnet/diagnostics/blob/master/documentation/design-docs/ipc-protocol.md).</span></span>
- <span data-ttu-id="bce8e-191">이진 이벤트 스트림을 이벤트로 디코드:</span><span class="sxs-lookup"><span data-stu-id="bce8e-191">Decoding the binary event stream into events:</span></span>
  - <span data-ttu-id="bce8e-192">[TraceEvent 라이브러리](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent)는 ETW 및 EventPipe 스트림 형식을 둘 다 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-192">The [TraceEvent library](https://www.nuget.org/packages/Microsoft.Diagnostics.Tracing.TraceEvent) handles both ETW and EventPipe stream formats.</span></span>
- <span data-ttu-id="bce8e-193">명령줄 및 GUI 도구:</span><span class="sxs-lookup"><span data-stu-id="bce8e-193">Command-line and GUI tools:</span></span>
  - <span data-ttu-id="bce8e-194">PerfView(ETW 또는 EventPipe), dotnet-counters(EventPipe 전용) 및 dotnet-monitor(EventPipe 전용)와 같은 도구</span><span class="sxs-lookup"><span data-stu-id="bce8e-194">Tools like PerfView (ETW or EventPipe), dotnet-counters (EventPipe only), and dotnet-monitor (EventPipe only).</span></span>

### <a name="consume-out-of-proc"></a><span data-ttu-id="bce8e-195">out-of-proc 사용</span><span class="sxs-lookup"><span data-stu-id="bce8e-195">Consume out-of-proc</span></span>

<span data-ttu-id="bce8e-196">out-of-proc에서 EventCounters를 사용하는 것은 매우 일반적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-196">Consuming EventCounters out-of-proc is a very common approach.</span></span> <span data-ttu-id="bce8e-197">[dotnet-counters](dotnet-counters.md)를 사용하여 EventPipe를 통해 플랫폼 간 방식으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-197">You can use [dotnet-counters](dotnet-counters.md) to consume them in a cross-platform manner via an EventPipe.</span></span> <span data-ttu-id="bce8e-198">`dotnet-counters` 도구는 카운터 값을 모니터링하는 데 사용할 수 있는 플랫폼 간 dotnet CLI 전역 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-198">The `dotnet-counters` tool is a cross-platform dotnet CLI global tool that can be used to monitor the counter values.</span></span> <span data-ttu-id="bce8e-199">`dotnet-counters`를 사용하여 카운터를 모니터링하는 방법을 알아보려면 [dotnet-counters](dotnet-counters.md)를 참조하거나 [EventCounters를 사용하여 성능 측정](event-counter-perf.md) 자습서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-199">To find out how to use `dotnet-counters` to monitor your counters, see [dotnet-counters](dotnet-counters.md), or work through the [Measure performance using EventCounters](event-counter-perf.md) tutorial.</span></span>

#### <a name="dotnet-trace"></a><span data-ttu-id="bce8e-200">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bce8e-200">dotnet-trace</span></span>

<span data-ttu-id="bce8e-201">`dotnet-trace` 도구는 EventPipe를 통해 카운터 데이터를 사용하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-201">The `dotnet-trace` tool can be used to consume the counter data through an EventPipe.</span></span> <span data-ttu-id="bce8e-202">다음은 `dotnet-trace`를 사용하여 카운터 데이터를 수집 하는 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-202">Here is an example using `dotnet-trace` to collect counter data.</span></span>

```console
dotnet-trace collect --process-id <pid> Sample.EventCounter.Minimal:0:0:EventCounterIntervalSec=1
```

<span data-ttu-id="bce8e-203">시간 경과에 따른 카운터 값 수집 방법에 대한 자세한 내용은 [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-203">For more information on how to collect counter values over time, see the [dotnet-trace](dotnet-trace.md#use-dotnet-trace-to-collect-counter-values-over-time) documentation.</span></span>

#### <a name="azure-application-insights"></a><span data-ttu-id="bce8e-204">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="bce8e-204">Azure Application Insights</span></span>

<span data-ttu-id="bce8e-205">EventCounters는 Azure Monitor에서, 특히 Azure Application Insights에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-205">EventCounters can be consumed by Azure Monitor, specifically Azure Application Insights.</span></span> <span data-ttu-id="bce8e-206">카운터를 추가 및 제거할 수 있으며 사용자 지정 카운터 또는 잘 알려진 카운터를 자유롭게 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-206">Counters can be added and removed, and you're free to specify custom counters, or well-known counters.</span></span> <span data-ttu-id="bce8e-207">자세한 내용은 [수집할 카운터 사용자 지정](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-207">For more information, see [Customizing counters to be collected](/azure/azure-monitor/app/eventcounters#customizing-counters-to-be-collected).</span></span>

#### <a name="dotnet-monitor"></a><span data-ttu-id="bce8e-208">dotnet-monitor</span><span class="sxs-lookup"><span data-stu-id="bce8e-208">dotnet-monitor</span></span>

<span data-ttu-id="bce8e-209">`dotnet-monitor` 도구는 .NET 프로세스의 진단 정보에 쉽게 액세스할 수 있게 해 주는 실험적 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-209">The `dotnet-monitor` tool is an experimental tool that makes it easier to get access to diagnostics information in a .NET process.</span></span> <span data-ttu-id="bce8e-210">이 도구는 모든 진단 도구의 상위 집합으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-210">The tool serves as a superset of all diagnostics tools.</span></span> <span data-ttu-id="bce8e-211">추적 외에도, 메트릭을 모니터링하고 메모리 덤프를 수집하고 GC 덤프를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-211">In addition to traces, it can monitor metrics, collect memory dumps, and collect GC dumps.</span></span> <span data-ttu-id="bce8e-212">CLI 도구와 Docker 이미지 둘 다로 배포됩니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-212">It's distributed as both a CLI tool and a docker image.</span></span> <span data-ttu-id="bce8e-213">해당 도구가 REST API를 노출하면 진단 아티팩트의 컬렉션이 REST 호출을 통해 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-213">It exposes a REST API, and the collection of diagnostic artifacts occurs through REST calls.</span></span>

<span data-ttu-id="bce8e-214">자세한 내용은 [실험적 도구 dotnet-monitor 소개](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-214">For more information, see [Introducing dotnet-monitor, an experimental tool](https://devblogs.microsoft.com/dotnet/introducing-dotnet-monitor).</span></span>

### <a name="consume-in-proc"></a><span data-ttu-id="bce8e-215">In-proc에서 사용</span><span class="sxs-lookup"><span data-stu-id="bce8e-215">Consume in-proc</span></span>

<span data-ttu-id="bce8e-216"><xref:System.Diagnostics.Tracing.EventListener> API를 통해 카운터 값을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-216">You can consume the counter values via the <xref:System.Diagnostics.Tracing.EventListener> API.</span></span> <span data-ttu-id="bce8e-217"><xref:System.Diagnostics.Tracing.EventListener>는 애플리케이션의 모든 <xref:System.Diagnostics.Tracing.EventSource> 인스턴스에서 작성된 모든 이벤트를 사용하는 in-proc 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-217">An <xref:System.Diagnostics.Tracing.EventListener> is an in-proc way of consuming any events written by all instances of an <xref:System.Diagnostics.Tracing.EventSource> in your application.</span></span> <span data-ttu-id="bce8e-218">`EventListener` API를 사용하는 방법에 대한 자세한 내용은 <xref:System.Diagnostics.Tracing.EventListener>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bce8e-218">For more information on how to use the `EventListener` API, see <xref:System.Diagnostics.Tracing.EventListener>.</span></span>

<span data-ttu-id="bce8e-219">먼저 카운터 값을 생성하는 <xref:System.Diagnostics.Tracing.EventSource>를 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-219">First, the <xref:System.Diagnostics.Tracing.EventSource> that produces the counter value needs to be enabled.</span></span> <span data-ttu-id="bce8e-220"><xref:System.Diagnostics.Tracing.EventSource>가 생성될 때 알림을 받을 수 있도록 <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> 메서드를 재정의합니다. 이것이 EventCounters에서 올바른 <xref:System.Diagnostics.Tracing.EventSource>인 경우 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType>을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-220">Override the <xref:System.Diagnostics.Tracing.EventListener.OnEventSourceCreated%2A?displayProperty=nameWithType> method to get a notification when an <xref:System.Diagnostics.Tracing.EventSource> is created, and if this is the correct <xref:System.Diagnostics.Tracing.EventSource> with your EventCounters, then you can call <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A?displayProperty=nameWithType> on it.</span></span> <span data-ttu-id="bce8e-221">다음은 재정의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-221">Here is an example override:</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs" range="11-22":::

#### <a name="sample-code"></a><span data-ttu-id="bce8e-222">예제 코드</span><span class="sxs-lookup"><span data-stu-id="bce8e-222">Sample code</span></span>

<span data-ttu-id="bce8e-223">다음은 매초마다 내부 카운터(`System.Runtime`)를 게시하기 위해 .NET 런타임의 <xref:System.Diagnostics.Tracing.EventSource>에서 모든 카운터 이름 및 값을 출력하는 샘플 <xref:System.Diagnostics.Tracing.EventListener> 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-223">Here is a sample <xref:System.Diagnostics.Tracing.EventListener> class that prints out all the counter names and values from the .NET runtime's <xref:System.Diagnostics.Tracing.EventSource>, for publishing its internal counters (`System.Runtime`) every second.</span></span>

:::code language="csharp" source="snippets/EventCounters/SimpleEventListener.cs":::

<span data-ttu-id="bce8e-224">위와 같이 <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>를 호출할 때 `filterPayload` 인수에 `"EventCounterIntervalSec"` 인수가 설정되어 있는지 ‘반드시’ 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-224">As shown above, you _must_ make sure the `"EventCounterIntervalSec"` argument is set in the `filterPayload` argument when calling <xref:System.Diagnostics.Tracing.EventListener.EnableEvents%2A>.</span></span> <span data-ttu-id="bce8e-225">그러지 않으면 카운터는 플러시 간격을 알 수 없으므로 값을 플러시할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bce8e-225">Otherwise the counters will not be able to flush out values since it doesn't know at which interval it should be getting flushed out.</span></span>

## <a name="see-also"></a><span data-ttu-id="bce8e-226">참조</span><span class="sxs-lookup"><span data-stu-id="bce8e-226">See also</span></span>

- [<span data-ttu-id="bce8e-227">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="bce8e-227">dotnet-counters</span></span>](dotnet-counters.md)
- [<span data-ttu-id="bce8e-228">dotnet-trace</span><span class="sxs-lookup"><span data-stu-id="bce8e-228">dotnet-trace</span></span>](dotnet-trace.md)
- <xref:System.Diagnostics.Tracing.EventCounter>
- <xref:System.Diagnostics.Tracing.EventListener>
- <xref:System.Diagnostics.Tracing.EventSource>
