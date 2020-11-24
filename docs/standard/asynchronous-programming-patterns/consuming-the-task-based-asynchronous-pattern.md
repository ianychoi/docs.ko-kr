---
title: 작업 기반 비동기 패턴 사용
description: 비동기 작업을 수행할 때 TAP(작업 기반 비동기 패턴)을 사용하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- .NET and TAP
- asynchronous design patterns, .NET
- TAP, .NET support for
- Task-based Asynchronous Pattern, .NET support for
- .NET, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
ms.openlocfilehash: 2a24c06e55a5f07f4831b32cf52ea2b5b389d5cc
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830547"
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a><span data-ttu-id="ac2f7-103">작업 기반 비동기 패턴 사용</span><span class="sxs-lookup"><span data-stu-id="ac2f7-103">Consuming the Task-based Asynchronous Pattern</span></span>

<span data-ttu-id="ac2f7-104">TAP(작업 기반 비동기 패턴)을 사용하여 비동기 작업을 수행할 경우 콜백을 사용하면 차단 없이 대기를 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-104">When you use the Task-based Asynchronous Pattern (TAP) to work with asynchronous operations, you can use callbacks to achieve waiting without blocking.</span></span> <span data-ttu-id="ac2f7-105">작업의 경우 이는 <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>와 같은 메서드를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-105">For tasks, this is achieved through methods such as <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ac2f7-106">언어 기반 비동기 지원은 정상적인 제어 흐름 내에서 비동기 작업이 대기할 수 있도록 함으로써 콜백 숨김을 지원하고, 컴파일러에서 생성된 코드는 이와 동일한 API 수준 지원을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-106">Language-based asynchronous support hides callbacks by allowing asynchronous operations to be awaited within normal control flow, and compiler-generated code provides this same API-level support.</span></span>

## <a name="suspending-execution-with-await"></a><span data-ttu-id="ac2f7-107">Await로 실행 일시 중지</span><span class="sxs-lookup"><span data-stu-id="ac2f7-107">Suspending Execution with Await</span></span>

<span data-ttu-id="ac2f7-108">C#의 [await](../../csharp/language-reference/operators/await.md) 키워드 및 Visual Basic의 [Await 연산자](../../visual-basic/language-reference/operators/await-operator.md)를 사용하여 <xref:System.Threading.Tasks.Task> 및 <xref:System.Threading.Tasks.Task%601> 개체를 비동기적으로 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-108">You can use the [await](../../csharp/language-reference/operators/await.md) keyword in C# and the [Await Operator](../../visual-basic/language-reference/operators/await-operator.md) in Visual Basic to asynchronously await <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects.</span></span> <span data-ttu-id="ac2f7-109"><xref:System.Threading.Tasks.Task> 개체를 대기하고 있을 때 `await` 식은 `void` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-109">When you're awaiting a <xref:System.Threading.Tasks.Task>, the `await` expression is of type `void`.</span></span> <span data-ttu-id="ac2f7-110"><xref:System.Threading.Tasks.Task%601> 개체를 대기하고 있을 때 `await` 식은 `TResult` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-110">When you're awaiting a <xref:System.Threading.Tasks.Task%601>, the `await` expression is of type `TResult`.</span></span> <span data-ttu-id="ac2f7-111">`await` 식은 비동기 메서드의 본문 내에서 발생해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-111">An `await` expression must occur inside the body of an asynchronous method.</span></span> <span data-ttu-id="ac2f7-112">관련 언어 기능은 .NET Framework 4.5에서 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-112">(These language features were introduced in .NET Framework 4.5.)</span></span>

 <span data-ttu-id="ac2f7-113">내부적으로 await 기능은 연속을 사용해서 작업에 콜백을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-113">Under the covers, the await functionality installs a callback on the task by using a continuation.</span></span>  <span data-ttu-id="ac2f7-114">이 콜백은 일시 중지 시점에서 비동기 메서드를 재개합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-114">This callback resumes the asynchronous method at the point of suspension.</span></span> <span data-ttu-id="ac2f7-115">비동기 메서드가 재개될 때 대기된 작업이 성공적으로 완료되고 <xref:System.Threading.Tasks.Task%601>인 경우 해당 `TResult`가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-115">When the asynchronous method is resumed, if the awaited operation completed successfully and was a <xref:System.Threading.Tasks.Task%601>, its `TResult` is returned.</span></span>  <span data-ttu-id="ac2f7-116">대기된 <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601> 개체가 <xref:System.Threading.Tasks.TaskStatus.Canceled> 상태에서 종료된 경우 <xref:System.OperationCanceledException> 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-116">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state, an <xref:System.OperationCanceledException> exception is thrown.</span></span>  <span data-ttu-id="ac2f7-117">대기된 <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601> 개체가 <xref:System.Threading.Tasks.TaskStatus.Faulted> 상태에서 종료된 경우 오류를 초래한 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-117">If the <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> that was awaited ended in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state, the exception that caused it to fault is thrown.</span></span> <span data-ttu-id="ac2f7-118">`Task`에서는 여러 식의 결과로 오류가 발생할 수 있지만 이러한 예외 중 하나만 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-118">A `Task` can fault as a result of multiple exceptions, but only one of these exceptions is propagated.</span></span> <span data-ttu-id="ac2f7-119">그러나 <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> 속성은 모든 오류가 포함된 <xref:System.AggregateException> 예외를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-119">However, the <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> property returns an <xref:System.AggregateException> exception that contains all the errors.</span></span>

 <span data-ttu-id="ac2f7-120">동기화 컨텍스트(<xref:System.Threading.SynchronizationContext> 개체)가 일시 중단될 때(예를 들어 <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> 속성이 `null`이 아닌 경우) 비동기 메서드를 실행하고 있던 스레드와 연결되어 있는 경우 비동기 메서드는 컨텍스트의 <xref:System.Threading.SynchronizationContext.Post%2A> 메서드를 사용하여 동일한 동기화 컨텍스트에서 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-120">If a synchronization context (<xref:System.Threading.SynchronizationContext> object) is associated with the thread that was executing the asynchronous method at the time of suspension (for example, if the <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> property is not `null`), the asynchronous method resumes on that same synchronization context by using the context's <xref:System.Threading.SynchronizationContext.Post%2A> method.</span></span> <span data-ttu-id="ac2f7-121">그러지 않으면 일시 중단될 때 최신 상태인 작업 스케줄러(<xref:System.Threading.Tasks.TaskScheduler> 개체)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-121">Otherwise, it relies on the task scheduler (<xref:System.Threading.Tasks.TaskScheduler> object) that was current at the time of suspension.</span></span> <span data-ttu-id="ac2f7-122">일반적으로 이 개체는 스레드 풀을 대상으로 하는 기본 작업 스케줄러(<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>)입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-122">Typically, this is the default task scheduler (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), which targets the thread pool.</span></span> <span data-ttu-id="ac2f7-123">이 작업 스케줄러는 대기 중이던 비동기 작업이 완료된 위치에서 다시 시작되어야 하는지 또는 재개를 예약해야 하는지를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-123">This task scheduler determines whether the awaited asynchronous operation should resume where it completed or whether the resumption should be scheduled.</span></span> <span data-ttu-id="ac2f7-124">기본 스케줄러는 일반적으로 대기 중이던 작업이 완료된 스레드에서 실행이 계속되도록 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-124">The default scheduler typically allows the continuation to run on the thread that the awaited operation completed.</span></span>

 <span data-ttu-id="ac2f7-125">비동기 메서드가 호출되면 아직 완료되지 않은 대기 가능 인스턴스에 대한 첫 번째 대기 식이 나올 때까지, 즉 호출이 호출자에게 반환될 때까지 함수 본문을 동기적으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-125">When an asynchronous method is called, it synchronously executes the body of the function up until the first await expression on an awaitable instance that has not yet completed, at which point the invocation returns to the caller.</span></span> <span data-ttu-id="ac2f7-126">비동기 메서드가 `void`를 반환하지 않으면 <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601> 개체가 반환되어 진행 중인 계산을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-126">If the asynchronous method does not return `void`, a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object is returned to represent the ongoing computation.</span></span> <span data-ttu-id="ac2f7-127">void가 아닌 비동기 메서드에서, return 문이 나오거나 메서드 본문의 끝에 도달하는 경우 작업이 <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> 최종 상태로 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-127">In a non-void asynchronous method, if a return statement is encountered or the end of the method body is reached, the task is completed in the <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> final state.</span></span> <span data-ttu-id="ac2f7-128">처리되지 않은 예외로 인해 제어 권한이 비동기 메서드의 본문을 벗어날 경우 작업이 <xref:System.Threading.Tasks.TaskStatus.Faulted> 상태로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-128">If an unhandled exception causes control to leave the body of the asynchronous method, the task ends in the <xref:System.Threading.Tasks.TaskStatus.Faulted> state.</span></span> <span data-ttu-id="ac2f7-129">해당 예외가 <xref:System.OperationCanceledException>인 경우 대신 작업이 <xref:System.Threading.Tasks.TaskStatus.Canceled> 상태로 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-129">If that exception is an <xref:System.OperationCanceledException>, the task instead ends in the <xref:System.Threading.Tasks.TaskStatus.Canceled> state.</span></span> <span data-ttu-id="ac2f7-130">이러한 방식으로 결과 또는 예외가 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-130">In this manner, the result or exception is eventually published.</span></span>

 <span data-ttu-id="ac2f7-131">이 동작은 몇 가지 중요한 형태로 변형되어 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-131">There are several important variations of this behavior.</span></span>  <span data-ttu-id="ac2f7-132">성능상의 이유로 작업이 대기될 때 이미 거의 완료되었으면 제어가 일시 중단되지 않고 함수는 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-132">For performance reasons, if a task has already completed by the time the task is awaited, control is not yielded, and the function continues to execute.</span></span>  <span data-ttu-id="ac2f7-133">또한 원래 컨텍스트로 돌아간다고 해서 항상 원하는 동작을 얻을 수 있는 것은 아니며 변경될 수 있습니다. 이 내용에 대해서는 다음 섹션에서 좀 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-133">Additionally, returning to the original context isn't always the desired behavior and can be changed; this is described in more detail in the next section.</span></span>

### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a><span data-ttu-id="ac2f7-134">Yield 및 ConfigureAwait를 사용하여 일시 중단 및 재개 구성</span><span class="sxs-lookup"><span data-stu-id="ac2f7-134">Configuring Suspension and Resumption with Yield and ConfigureAwait</span></span>
 <span data-ttu-id="ac2f7-135">몇 가지 메서드는 비동기 메서드 실행을 좀 더 강력하게 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-135">Several methods provide more control over an asynchronous method's execution.</span></span> <span data-ttu-id="ac2f7-136">예를 들어 다음과 같이 <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> 메서드를 사용하여 비동기 메서드에 양보점(yield point)을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-136">For example, you can use the <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> method to introduce a yield point into the asynchronous method:</span></span>

```csharp
public class Task : …
{
    public static YieldAwaitable Yield();
    …
}
```

 <span data-ttu-id="ac2f7-137">이 작업은 비동기적으로 원래 컨텍스트에 다시 게시하거나 원래 컨텍스트를 예약하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-137">This is equivalent to asynchronously posting or scheduling back to the current context.</span></span>

```csharp
Task.Run(async delegate
{
    for(int i=0; i<1000000; i++)
    {
        await Task.Yield(); // fork the continuation into a separate work item
        ...
    }
});
```

 <span data-ttu-id="ac2f7-138">또한 비동기 메서드에서 일시 중단 및 다시 시작에 대한 제어를 개선하기 위해 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 메서드를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-138">You can also use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method for better control over suspension and resumption in an asynchronous method.</span></span>  <span data-ttu-id="ac2f7-139">앞서 언급했듯이 기본적으로 비동기 메서드가 일시 중단되었던 당시의 현재 컨텍스트가 캡처되며 캡처된 해당 컨텍스트는 다시 시작할 때 비동기 메서드의 연속을 호출하는 데 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-139">As mentioned previously, by default, the current context is captured at the time an asynchronous  method is suspended, and that captured context is used to invoke the asynchronous  method's continuation upon resumption.</span></span>  <span data-ttu-id="ac2f7-140">대부분의 경우에서 사용자가 원하는 정확한 행동이 바로 이것일 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-140">In many cases, this is the exact behavior you want.</span></span>  <span data-ttu-id="ac2f7-141">연속 컨텍스트를 별로 중요하게 생각하지 않을 수도 있고 원래 컨텍스트로의 다시 게시를 피함으로써 더 나은 성능을 얻을 수 있는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-141">In other cases, you may not care about the continuation context, and you can achieve better performance by avoiding such posts back to the original context.</span></span>  <span data-ttu-id="ac2f7-142">이 기능을 사용하도록 설정하려면 <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> 메서드를 사용하여 대기 작업에 컨텍스트를 캡처하고 다시 시작하지 않고 대기 중인 비동기 작업이 완료될 때마다 실행을 계속하도록 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-142">To enable this, use the <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> method to inform the await operation not to capture and resume on the context, but to continue execution wherever the asynchronous operation that was being awaited completed:</span></span>

```csharp
await someTask.ConfigureAwait(continueOnCapturedContext:false);
```

## <a name="canceling-an-asynchronous-operation"></a><span data-ttu-id="ac2f7-143">비동기 작업 취소</span><span class="sxs-lookup"><span data-stu-id="ac2f7-143">Canceling an Asynchronous Operation</span></span>

<span data-ttu-id="ac2f7-144">.NET Framework 4부터는 취소를 지원하는 TAP 메서드가 취소 토큰(<xref:System.Threading.CancellationToken> 개체)을 수락하는 오버로드를 하나 이상 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-144">Starting with .NET Framework 4, TAP methods that support cancellation provide at least one overload that accepts a cancellation token (<xref:System.Threading.CancellationToken> object).</span></span>

 <span data-ttu-id="ac2f7-145">취소 토큰은 취소 토큰 소스(<xref:System.Threading.CancellationTokenSource> 개체)를 통해 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-145">A cancellation token is created through a cancellation token source (<xref:System.Threading.CancellationTokenSource> object).</span></span>  <span data-ttu-id="ac2f7-146">소스의 <xref:System.Threading.CancellationTokenSource.Token%2A> 속성은 소스의 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 메서드가 호출될 때 신호를 받을 취소 토큰을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-146">The source's <xref:System.Threading.CancellationTokenSource.Token%2A> property returns the cancellation token that will be signaled when the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method is called.</span></span>  <span data-ttu-id="ac2f7-147">예를 들어 단일 웹 페이지를 다운로드하려고 하며 작업을 취소할 수 있게 하려는 경우 <xref:System.Threading.CancellationTokenSource> 개체를 만들고, 해당 토큰을 TAP 메서드에 전달한 후 작업을 취소할 준비가 되면 소스의 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-147">For example, if you want to download a single webpage and you want to be able to cancel the operation, you create a <xref:System.Threading.CancellationTokenSource> object, pass its token to the TAP method, and then call the source's <xref:System.Threading.CancellationTokenSource.Cancel%2A> method when you're ready to cancel the operation:</span></span>

```csharp
var cts = new CancellationTokenSource();
string result = await DownloadStringAsync(url, cts.Token);
… // at some point later, potentially on another thread
cts.Cancel();
```

 <span data-ttu-id="ac2f7-148">여러 비동기 호출을 취소하려면 모든 호출에 동일한 토큰을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-148">To cancel multiple asynchronous invocations, you can pass the same token to all invocations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));
    // at some point later, potentially on another thread
    …
    cts.Cancel();
```

 <span data-ttu-id="ac2f7-149">또는 작업의 선택적 하위 집합에 동일한 토큰을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-149">Or, you can pass the same token to a selective subset of operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
    byte [] data = await DownloadDataAsync(url, cts.Token);
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);
    … // at some point later, potentially on another thread
    cts.Cancel();
```

 <span data-ttu-id="ac2f7-150">어떤 스레드에서도 취소 요청이 시작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-150">Cancellation requests may be initiated from any thread.</span></span>

 <span data-ttu-id="ac2f7-151">취소 토큰을 수락하는 모든 메서드에 <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> 값을 전달하여 취소가 절대 요청되지 않을 것을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-151">You can pass the <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> value to any method that accepts a cancellation token to indicate that cancellation will never be requested.</span></span>  <span data-ttu-id="ac2f7-152">이렇게 하면 <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> 속성이 `false`를 반환하며, 호출된 메서드가 이에 따라 최적화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-152">This causes the <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> property to return `false`, and the called method can optimize accordingly.</span></span>  <span data-ttu-id="ac2f7-153">테스트를 위해 토큰이 이미 취소된 상태 또는 취소 불가능 상태로 시작되어야 하는지를 나타내는 부울 값을 수락하는 생성자를 사용하여 인스턴스화된 미리 취소된 취소 토큰을 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-153">For testing purposes, you can also pass in a pre-canceled cancellation token that is instantiated by using the constructor that accepts a Boolean value to indicate whether the token should start in an already-canceled or not-cancelable state.</span></span>

 <span data-ttu-id="ac2f7-154">이러한 취소 방법에는 다음과 같은 여러 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-154">This approach to cancellation has several advantages:</span></span>

- <span data-ttu-id="ac2f7-155">제한 없는 수의 비동기 및 동기 작업에 동일한 취소 토큰을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-155">You can pass the same cancellation token to any number of asynchronous and synchronous operations.</span></span>

- <span data-ttu-id="ac2f7-156">동일한 취소 요청을 제한 없는 수의 수신기에 확산시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-156">The same cancellation request may be proliferated to any number of listeners.</span></span>

- <span data-ttu-id="ac2f7-157">비동기 API의 개발자는 취소를 요청할 수 있는지 여부 및 적용되는 시기 등을 완전히 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-157">The developer of the asynchronous API is in complete control of whether cancellation may be requested and when it may take effect.</span></span>

- <span data-ttu-id="ac2f7-158">API를 사용하는 코드는 취소 요청이 전파되는 비동기 호출을 선택적으로 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-158">The code that consumes the API may selectively determine the asynchronous invocations that cancellation requests will be propagated to.</span></span>

## <a name="monitoring-progress"></a><span data-ttu-id="ac2f7-159">진행률 모니터링</span><span class="sxs-lookup"><span data-stu-id="ac2f7-159">Monitoring Progress</span></span>
 <span data-ttu-id="ac2f7-160">일부 비동기 메서드는 비동기 메서드에 전달된 진행률 인터페이스를 통해 진행 상황을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-160">Some asynchronous methods expose progress through a progress interface passed into the asynchronous method.</span></span>  <span data-ttu-id="ac2f7-161">예를 들어 텍스트 문자열을 비동기적으로 다운로드하고 지금까지 완료된 다운로드의 비율을 포함하는 진행률 업데이트를 야기하는 함수를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-161">For example, consider a function that asynchronously downloads a string of text, and along the way raises progress updates that include the percentage of the download that has completed thus far.</span></span>  <span data-ttu-id="ac2f7-162">이러한 메서드는 다음과 같이 WPF(Windows Presentation Foundation) 애플리케이션에서 사용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-162">Such a method could be consumed in a Windows Presentation Foundation (WPF) application as follows:</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,
            new Progress<int>(p => pbDownloadProgress.Value = p));
    }
    finally { btnDownload.IsEnabled = true; }
}
```

<a name="combinators"></a>
## <a name="using-the-built-in-task-based-combinators"></a><span data-ttu-id="ac2f7-163">기본 제공 작업 기반 조합기 사용</span><span class="sxs-lookup"><span data-stu-id="ac2f7-163">Using the Built-in Task-based Combinators</span></span>
 <span data-ttu-id="ac2f7-164"><xref:System.Threading.Tasks> 네임스페이스에는 작업을 구성하고 사용하기 위한 몇 가지 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-164">The <xref:System.Threading.Tasks> namespace includes several methods for composing and working with tasks.</span></span>

### <a name="taskrun"></a><span data-ttu-id="ac2f7-165">Task.Run</span><span class="sxs-lookup"><span data-stu-id="ac2f7-165">Task.Run</span></span>
 <span data-ttu-id="ac2f7-166"><xref:System.Threading.Tasks.Task> 클래스에는 <xref:System.Threading.Tasks.Task> 또는 <xref:System.Threading.Tasks.Task%601> 개체로 스레드 풀에 작업을 쉽게 오프로드할 수 있게 하는 몇 가지 <xref:System.Threading.Tasks.Task.Run%2A> 메서드가 포함되어 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-166">The <xref:System.Threading.Tasks.Task> class includes several <xref:System.Threading.Tasks.Task.Run%2A> methods that let you easily offload work as a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> to the thread pool, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    textBox1.Text = await Task.Run(() =>
    {
        // … do compute-bound work here
        return answer;
    });
}
```

 <span data-ttu-id="ac2f7-167"><xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> 오버로드와 같은 이러한 <xref:System.Threading.Tasks.Task.Run%2A> 메서드 중 일부는 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 메서드의 축약형으로 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-167">Some of these <xref:System.Threading.Tasks.Task.Run%2A> methods, such as the <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> overload, exist as shorthand for the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="ac2f7-168"><xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>과 같은 다른 오버로드를 사용하면 오프로드된 작업 내에서 await를 사용할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-168">Other overloads, such as <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, enable you to use await within the offloaded work, for example:</span></span>

```csharp
public async void button1_Click(object sender, EventArgs e)
{
    pictureBox1.Image = await Task.Run(async() =>
    {
        using(Bitmap bmp1 = await DownloadFirstImageAsync())
        using(Bitmap bmp2 = await DownloadSecondImageAsync())
        return Mashup(bmp1, bmp2);
    });
}
```

 <span data-ttu-id="ac2f7-169">이러한 오버로드는 <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> 메서드를 작업 병렬 라이브러리의 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 확장 메서드와 함께 사용하는 것과 논리적으로 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-169">Such overloads are logically equivalent to using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> method in conjunction with the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension method in the Task Parallel Library.</span></span>

### <a name="taskfromresult"></a><span data-ttu-id="ac2f7-170">Task.FromResult</span><span class="sxs-lookup"><span data-stu-id="ac2f7-170">Task.FromResult</span></span>
 <span data-ttu-id="ac2f7-171">데이터를 이미 사용할 수 있거나 <xref:System.Threading.Tasks.Task%601>에 리프트된 작업 반환 메서드에서 데이터를 반환하기만 하면 되는 시나리오에서는 <xref:System.Threading.Tasks.Task.FromResult%2A> 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-171">Use the <xref:System.Threading.Tasks.Task.FromResult%2A> method in scenarios where data may already be available and just needs to be returned from a task-returning method lifted into a <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public Task<int> GetValueAsync(string key)
{
    int cachedValue;
    return TryGetCachedValue(out cachedValue) ?
        Task.FromResult(cachedValue) :
        GetValueAsyncInternal();
}

private async Task<int> GetValueAsyncInternal(string key)
{
    …
}
```

### <a name="taskwhenall"></a><span data-ttu-id="ac2f7-172">Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="ac2f7-172">Task.WhenAll</span></span>
 <span data-ttu-id="ac2f7-173"><xref:System.Threading.Tasks.Task.WhenAll%2A> 메서드를 사용하여 작업(task)으로 표현되는 여러 비동기 작업을 비동기적으로 대기합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-173">Use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method to asynchronously wait on multiple asynchronous operations that are represented as tasks.</span></span>  <span data-ttu-id="ac2f7-174">이 메서드에는 비일반 작업 집합 또는 균일하지 않은 일반 작업 집합을 지원하는 오버로드(예: 여러 void 반환 작업을 비동기적으로 대기하거나 각 값이 다른 형식을 가질 수 있는 여러 값 반환 메서드를 비동기적으로 대기) 및 균일한 일반 작업 집합을 지원하는 오버로드(여러 `TResult` 반환 메서드를 비동기적으로 대기)가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-174">The method has multiple overloads that support a set of non-generic tasks or a non-uniform set of generic tasks (for example, asynchronously waiting for multiple void-returning operations, or asynchronously waiting for multiple value-returning methods where each value may have a different type) and to support a uniform set of generic tasks (such as asynchronously waiting for multiple `TResult`-returning methods).</span></span>

 <span data-ttu-id="ac2f7-175">여러 고객에게 전자 메일 메시지를 전송하려는 경우를 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-175">Let's say you want to send email messages to several customers.</span></span> <span data-ttu-id="ac2f7-176">한 메시지가 완료될 때까지 기다렸다가 다음 메시지를 전송하지 않도록 메시지 전송을 겹칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-176">You can overlap sending the messages so you're not waiting for one message to complete before sending the next.</span></span> <span data-ttu-id="ac2f7-177">또한 보내기 작업이 완료될 때와 오류가 발생했는지 여부도 확인할 수 있습니다.또</span><span class="sxs-lookup"><span data-stu-id="ac2f7-177">You can also find out when the send operations have completed and whether any errors have occurred:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
await Task.WhenAll(asyncOps);
```

 <span data-ttu-id="ac2f7-178">이 코드는 발생할 수 있는 예외를 명시적으로 처리하지 않지만 <xref:System.Threading.Tasks.Task.WhenAll%2A>의 결과 작업에 대한 `await`에서 예외가 전파되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-178">This code doesn't explicitly handle exceptions that may occur, but lets exceptions propagate out of the `await` on the resulting task from <xref:System.Threading.Tasks.Task.WhenAll%2A>.</span></span>  <span data-ttu-id="ac2f7-179">예외를 처리하려면 다음과 같은 코드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-179">To handle the exceptions, you can use code such as the following:</span></span>

```csharp
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    ...
}
```

 <span data-ttu-id="ac2f7-180">이 경우 비동기 작업이 실패하면 모든 예외가 <xref:System.AggregateException> 예외에서 통합되어 <xref:System.Threading.Tasks.Task.WhenAll%2A> 메서드에서 반환되는 <xref:System.Threading.Tasks.Task>에 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-180">In this case, if any asynchronous operation fails, all the exceptions will be consolidated in an <xref:System.AggregateException> exception, which is stored in the <xref:System.Threading.Tasks.Task> that is returned from the <xref:System.Threading.Tasks.Task.WhenAll%2A> method.</span></span>  <span data-ttu-id="ac2f7-181">그러나 이러한 예외 중 하나만 `await` 키워드에 의해 전파됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-181">However, only one of those exceptions is propagated by the `await` keyword.</span></span>  <span data-ttu-id="ac2f7-182">모든 예외를 검사하려는 경우 앞의 코드를 다음과 같이 다시 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-182">If you want to examine all the exceptions, you can rewrite the previous code as follows:</span></span>

```csharp
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();
try
{
    await Task.WhenAll(asyncOps);
}
catch(Exception exc)
{
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

 <span data-ttu-id="ac2f7-183">웹에서 비동기적으로 여러 파일을 다운로드하는 예를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-183">Let's consider an example of downloading multiple files from the web asynchronously.</span></span>  <span data-ttu-id="ac2f7-184">이 경우 모든 비동기 작업이 동일한 결과 형식을 가지며 결과에 액세스하기 쉽습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-184">In this case, all the asynchronous operations have homogeneous result types, and it's easy to access the results:</span></span>

```csharp
string [] pages = await Task.WhenAll(
    from url in urls select DownloadStringAsync(url));
```

 <span data-ttu-id="ac2f7-185">이전의 void 반환 시나리오에서 설명한 것과 동일한 예외 처리 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-185">You can use the same exception-handling techniques we discussed in the previous void-returning scenario:</span></span>

```csharp
Task<string> [] asyncOps =
    (from url in urls select DownloadStringAsync(url)).ToArray();
try
{
    string [] pages = await Task.WhenAll(asyncOps);
    ...
}
catch(Exception exc)
{
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))
    {
        … // work with faulted and faulted.Exception
    }
}
```

### <a name="taskwhenany"></a><span data-ttu-id="ac2f7-186">Task.WhenAny</span><span class="sxs-lookup"><span data-stu-id="ac2f7-186">Task.WhenAny</span></span>
 <span data-ttu-id="ac2f7-187"><xref:System.Threading.Tasks.Task.WhenAny%2A> 메서드를 사용하여 작업(task)으로 표현되는 여러 비동기 작업 중 하나가 완료될 때까지만 비동기적으로 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-187">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to asynchronously wait for just one of multiple asynchronous operations represented as tasks to complete.</span></span>  <span data-ttu-id="ac2f7-188">이 메서드는 다음 네 가지 기본 사용 사례를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-188">This method serves four primary use cases:</span></span>

- <span data-ttu-id="ac2f7-189">중복성:  작업을 여러 번 수행하고 먼저 완료되는 작업을 선택합니다(예를 들어, 단일의 결과를 생성하는 여러 주식 시세 웹 서비스에 연결하고 가장 빨리 완료되는 결과를 선택).</span><span class="sxs-lookup"><span data-stu-id="ac2f7-189">Redundancy:  Performing an operation multiple times and selecting the one that completes first (for example, contacting multiple stock quote web services that will produce a single result and selecting the one that completes the fastest).</span></span>

- <span data-ttu-id="ac2f7-190">인터리브:  여러 작업을 시작하고 모두 완료해야 하지만 완료되었을 때 작업을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-190">Interleaving:  Launching multiple operations and waiting for all of them to complete, but processing them as they complete.</span></span>

- <span data-ttu-id="ac2f7-191">스로틀:  다른 작업이 완료되면 추가 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-191">Throttling:  Allowing additional operations to begin as others complete.</span></span>  <span data-ttu-id="ac2f7-192">이것은 인터리브 시나리오의 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-192">This is an extension of the interleaving scenario.</span></span>

- <span data-ttu-id="ac2f7-193">초기 재귀 한도 초과:  예를 들어, 작업 t1으로 표시되는 작업은 다른 작업 t2를 사용하여 <xref:System.Threading.Tasks.Task.WhenAny%2A> 작업에서 그룹화할 수 있으며 <xref:System.Threading.Tasks.Task.WhenAny%2A> 작업에서 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-193">Early bailout:  For example, an operation represented by task t1 can be grouped in a <xref:System.Threading.Tasks.Task.WhenAny%2A> task with another task t2, and you can wait on the <xref:System.Threading.Tasks.Task.WhenAny%2A> task.</span></span> <span data-ttu-id="ac2f7-194">작업 t2는 시간 제한 또는 취소를 나타내거나 t1이 완료되기 전에 <xref:System.Threading.Tasks.Task.WhenAny%2A> 작업이 완료되도록 하는 일부 다른 신호를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-194">Task t2 could represent a time-out, or cancellation, or some other signal that causes the <xref:System.Threading.Tasks.Task.WhenAny%2A> task to complete before t1 completes.</span></span>

#### <a name="redundancy"></a><span data-ttu-id="ac2f7-195">중복성</span><span class="sxs-lookup"><span data-stu-id="ac2f7-195">Redundancy</span></span>
 <span data-ttu-id="ac2f7-196">주식 구매 여부를 결정하려는 경우를 고려해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-196">Consider a case where you want to make a decision about whether to buy a stock.</span></span>  <span data-ttu-id="ac2f7-197">신뢰할 수 있는 일부 주식 권장 웹 서비스가 있지만 매일의 부하에 따라 각 서비스가 서로 다른 시간에 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-197">There are several stock recommendation web services that you trust, but depending on daily load, each service can end up being slow at different times.</span></span>  <span data-ttu-id="ac2f7-198">다음과 같이 <xref:System.Threading.Tasks.Task.WhenAny%2A> 메서드를 사용하면 작업이 완료될 때 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-198">You can use the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to receive a notification when any operation completes:</span></span>

```csharp
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol),
    GetBuyRecommendation2Async(symbol),
    GetBuyRecommendation3Async(symbol)
};
Task<bool> recommendation = await Task.WhenAny(recommendations);
if (await recommendation) BuyStock(symbol);
```

 <span data-ttu-id="ac2f7-199">성공적으로 완료된 모든 작업의 래핑되지 않은 결과를 반환하는 <xref:System.Threading.Tasks.Task.WhenAll%2A>과 달리, <xref:System.Threading.Tasks.Task.WhenAny%2A>는 완료된 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-199">Unlike <xref:System.Threading.Tasks.Task.WhenAll%2A>, which returns the unwrapped results of all tasks that completed successfully, <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task that completed.</span></span> <span data-ttu-id="ac2f7-200">작업이 실패하면 해당 작업이 실패했다는 사실을 알아야 하고, 작업이 성공하면 해당 반환 값과 연결된 작업이 어떤 작업인지 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-200">If a task fails, it's important to know that it failed, and if a task succeeds, it's important to know which task the return value is associated with.</span></span>  <span data-ttu-id="ac2f7-201">따라서 반환된 작업의 결과에 액세스하거나 이 예제에 나타난 대로 더 기다려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-201">Therefore, you need to access the result of the returned task, or further await it, as  this example shows.</span></span>

 <span data-ttu-id="ac2f7-202"><xref:System.Threading.Tasks.Task.WhenAll%2A>과 마찬가지로 예외를 수용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-202">As with <xref:System.Threading.Tasks.Task.WhenAll%2A>, you have to be able to accommodate exceptions.</span></span>  <span data-ttu-id="ac2f7-203">완료된 작업이 다시 수신되므로 반환된 작업이 오류를 전파하고 적절히 `try/catch`할 때까지 기다릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-203">Because you receive the completed task back, you can await the returned task to have errors propagated, and `try/catch` them appropriately; for example:</span></span>

```csharp
Task<bool> [] recommendations = …;
while(recommendations.Count > 0)
{
    Task<bool> recommendation = await Task.WhenAny(recommendations);
    try
    {
        if (await recommendation) BuyStock(symbol);
        break;
    }
    catch(WebException exc)
    {
        recommendations.Remove(recommendation);
    }
}
```

 <span data-ttu-id="ac2f7-204">또한 첫 번째 작업이 성공적으로 완료되더라도 후속 작업은 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-204">Additionally, even if a first task completes successfully, subsequent tasks may fail.</span></span>  <span data-ttu-id="ac2f7-205">이 시점에서는 예외를 처리하는 몇 가지 옵션이 있습니다.  <xref:System.Threading.Tasks.Task.WhenAll%2A> 메서드를 사용할 수 있는 경우 시작된 모든 작업이 완료될 때까지 기다릴 수도 있고 또는 모든 예외가 중요하며 로그온해야 한다고 결정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-205">At this point, you have several options for dealing with exceptions:  You can wait until all the launched tasks have completed, in which case you can use the <xref:System.Threading.Tasks.Task.WhenAll%2A> method, or you can decide that all exceptions are important and must be logged.</span></span>  <span data-ttu-id="ac2f7-206">이를 위해 연속 작업을 사용하여 작업이 비동기적으로 완료되었을 때 알림을 받을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-206">For this, you can use continuations to receive a notification when tasks have completed asynchronously:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => { if (t.IsFaulted) Log(t.Exception); });
}
```

 <span data-ttu-id="ac2f7-207">또는</span><span class="sxs-lookup"><span data-stu-id="ac2f7-207">or:</span></span>

```csharp
foreach(Task recommendation in recommendations)
{
    var ignored = recommendation.ContinueWith(
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);
}
```

 <span data-ttu-id="ac2f7-208">다음을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-208">or even:</span></span>

```csharp
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)
{
    foreach(var task in tasks)
    {
        try { await task; }
        catch(Exception exc) { Log(exc); }
    }
}
…
LogCompletionIfFailed(recommendations);
```

 <span data-ttu-id="ac2f7-209">마지막으로 남은 모든 작업을 취소하려고 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-209">Finally, you may want to cancel all the remaining operations:</span></span>

```csharp
var cts = new CancellationTokenSource();
var recommendations = new List<Task<bool>>()
{
    GetBuyRecommendation1Async(symbol, cts.Token),
    GetBuyRecommendation2Async(symbol, cts.Token),
    GetBuyRecommendation3Async(symbol, cts.Token)
};

Task<bool> recommendation = await Task.WhenAny(recommendations);
cts.Cancel();
if (await recommendation) BuyStock(symbol);
```

#### <a name="interleaving"></a><span data-ttu-id="ac2f7-210">인터리브</span><span class="sxs-lookup"><span data-stu-id="ac2f7-210">Interleaving</span></span>
 <span data-ttu-id="ac2f7-211">웹에서 이미지를 다운로드하고 각 이미지를 처리하는 것을 고려해 봅니다(예: UI 컨트롤에 이미지 추가).</span><span class="sxs-lookup"><span data-stu-id="ac2f7-211">Consider a case where you're downloading images from the web and processing each image (for example, adding the image to a UI control).</span></span> <span data-ttu-id="ac2f7-212">UI 스레드에서 이미지를 순차적으로 처리하지만 가능한 동시에 이미지를 다운로드하려고 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-212">You process the images sequentially on the UI thread, but want to download the images as concurrently as possible.</span></span> <span data-ttu-id="ac2f7-213">또한 이미지가 모두 다운로드될 때까지 UI에 이미지를 추가하는 작업을 보류하지 않고</span><span class="sxs-lookup"><span data-stu-id="ac2f7-213">Also, you don't want to hold up adding the images to the UI until they're all downloaded.</span></span> <span data-ttu-id="ac2f7-214">완료되는 대로 추가하려고 할 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-214">Instead, you want to add them as they complete.</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

 <span data-ttu-id="ac2f7-215">다운로드한 이미지의 <xref:System.Threading.ThreadPool>에 대해 계산 집약적 처리를 발생시키는 시나리오에 인터리브를 적용할 수도 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-215">You can also apply interleaving to a scenario that involves computationally intensive processing on the <xref:System.Threading.ThreadPool> of the downloaded images; for example:</span></span>

```csharp
List<Task<Bitmap>> imageTasks =
    (from imageUrl in urls select GetBitmapAsync(imageUrl)
         .ContinueWith(t => ConvertImage(t.Result)).ToList();
while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch{}
}
```

#### <a name="throttling"></a><span data-ttu-id="ac2f7-216">스로틀</span><span class="sxs-lookup"><span data-stu-id="ac2f7-216">Throttling</span></span>
 <span data-ttu-id="ac2f7-217">사용자가 너무 많은 이미지를 다운로드하여 다운로드를 조절해야 하는 경우를 제외하고, 인터리브 예제를 고려해 보세요. 예를 들어 특정 횟수의 다운로드만 동시에 발생하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-217">Consider the interleaving example, except that the user is downloading so many images that the downloads have to be throttled; for example, you want only a specific number of downloads to happen concurrently.</span></span> <span data-ttu-id="ac2f7-218">이를 위해 비동기 작업 일부를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-218">To achieve this, you can start a subset of the asynchronous operations.</span></span>  <span data-ttu-id="ac2f7-219">작업이 완료되면 추가 작업을 추가해서 시작되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-219">As operations complete, you can start additional operations to take their place:</span></span>

```csharp
const int CONCURRENCY_LEVEL = 15;
Uri [] urls = …;
int nextIndex = 0;
var imageTasks = new List<Task<Bitmap>>();
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)
{
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
    nextIndex++;
}

while(imageTasks.Count > 0)
{
    try
    {
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);
        imageTasks.Remove(imageTask);

        Bitmap image = await imageTask;
        panel.AddImage(image);
    }
    catch(Exception exc) { Log(exc); }

    if (nextIndex < urls.Length)
    {
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));
        nextIndex++;
    }
}
```

#### <a name="early-bailout"></a><span data-ttu-id="ac2f7-220">초기 재귀 한도 초과</span><span class="sxs-lookup"><span data-stu-id="ac2f7-220">Early Bailout</span></span>
 <span data-ttu-id="ac2f7-221">사용자의 취소 요청에 동시에 응답하면서 작업이 완료되기를 비동기적으로 기다리는 경우를 고려해 봅니다(예: 사용자가 취소 단추를 클릭한 경우).</span><span class="sxs-lookup"><span data-stu-id="ac2f7-221">Consider that you're waiting asynchronously for an operation to complete while simultaneously responding to a user's cancellation request (for example, the user clicked a cancel button).</span></span> <span data-ttu-id="ac2f7-222">다음 코드에서는 이 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-222">The following code illustrates this scenario:</span></span>

```csharp
private CancellationTokenSource m_cts;

public void btnCancel_Click(object sender, EventArgs e)
{
    if (m_cts != null) m_cts.Cancel();
}

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();
    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        if (imageDownload.IsCompleted)
        {
            Bitmap image = await imageDownload;
            panel.AddImage(image);
        }
        else imageDownload.ContinueWith(t => Log(t));
    }
    finally { btnRun.Enabled = true; }
}

private static async Task UntilCompletionOrCancellation(
    Task asyncOp, CancellationToken ct)
{
    var tcs = new TaskCompletionSource<bool>();
    using(ct.Register(() => tcs.TrySetResult(true)))
        await Task.WhenAny(asyncOp, tcs.Task);
    return asyncOp;
}
```

 <span data-ttu-id="ac2f7-223">이 구현은 재귀 한도가 초과되었다고 결정하는 즉시 사용자 인터페이스를 다시 사용하도록 설정하지만 기본 비동기 작업을 취소하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-223">This implementation re-enables the user interface as soon as you decide to bail out, but doesn't cancel the underlying asynchronous operations.</span></span> <span data-ttu-id="ac2f7-224">또 다른 방법은 재귀 한도가 초과하였다고 결정할 때 보류 중인 작업을 취소하지만, 취소 요청으로 인해 일찍 종료될 수 있으므로 작업이 완료될 때까지 사용자 인터페이스를 다시 설정하지 않는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-224">Another alternative would be to cancel the pending operations when you decide to bail out, but not reestablish the user interface until the operations complete, potentially due to ending early due to the cancellation request:</span></span>

```csharp
private CancellationTokenSource m_cts;

public async void btnRun_Click(object sender, EventArgs e)
{
    m_cts = new CancellationTokenSource();

    btnRun.Enabled = false;
    try
    {
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);
        Bitmap image = await imageDownload;
        panel.AddImage(image);
    }
    catch(OperationCanceledException) {}
    finally { btnRun.Enabled = true; }
}
```

 <span data-ttu-id="ac2f7-225">조기 종료의 또 다른 예제에는 <xref:System.Threading.Tasks.Task.WhenAny%2A> 메서드를 <xref:System.Threading.Tasks.Task.Delay%2A> 메서드와 함께 사용하는 방법(다음 섹션에서 논의함)이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-225">Another example of early bailout involves using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method in conjunction with the <xref:System.Threading.Tasks.Task.Delay%2A> method, as discussed in the next section.</span></span>

### <a name="taskdelay"></a><span data-ttu-id="ac2f7-226">Task.Delay</span><span class="sxs-lookup"><span data-stu-id="ac2f7-226">Task.Delay</span></span>
 <span data-ttu-id="ac2f7-227"><xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 메서드를 사용하여 비동기 메서드 실행에 일시 중지를 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-227">You can use the <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method to introduce pauses into an asynchronous method's execution.</span></span>  <span data-ttu-id="ac2f7-228">이것은 폴링 루프 작성 및 미리 결정된 기간 동안 사용자 입력 처리 지연 등의 다양한 기능에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-228">This is useful for many kinds of functionality, including building polling loops and delaying the handling of user input for a predetermined period of time.</span></span>  <span data-ttu-id="ac2f7-229">또한 <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 메서드를 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>와 함께 사용하면 대기 시간 제한을 구현하는 데 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-229">The <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> method can also be useful in combination with <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> for implementing time-outs on awaits.</span></span>

 <span data-ttu-id="ac2f7-230">더 큰 비동기 작업(예: ASP.NET 웹 서비스)에 속하는 작업(task)이 완료하는 데 너무 오래 걸리는 경우 전체 작업에 문제가 발생하며, 완료가 실패하는 경우에는 더 큰 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-230">If a task that's part of a larger asynchronous operation (for example, an ASP.NET web service) takes too long to complete, the overall operation could suffer, especially if it fails to ever complete.</span></span>  <span data-ttu-id="ac2f7-231">이러한 이유로 비동기 작업을 대기하는 경우 시간이 초과하도록 할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-231">For this reason, it's important to be able to time out when waiting on an asynchronous operation.</span></span>  <span data-ttu-id="ac2f7-232">동기 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType> 및 <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> 메서드는 시간 제한 값을 허용하지만, 해당 <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 및 앞에서 언급한 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> 메서드는 시간 제한 값을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-232">The synchronous <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> methods accept time-out values, but the corresponding <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> and the previously mentioned <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>/<xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> methods do not.</span></span>  <span data-ttu-id="ac2f7-233">대신, <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> 및 <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>를 함께 사용하여 시간 제한을 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-233">Instead, you can use <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> in combination to implement a time-out.</span></span>

 <span data-ttu-id="ac2f7-234">예를 들어 UI 애플리케이션에서 이미지를 다운로드하려고 하며 이미지를 다운로드하는 동안에 UI를 사용하지 않도록 설정하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-234">For example, in your UI application, let's say that you want to download an image and disable the UI while the image is downloading.</span></span> <span data-ttu-id="ac2f7-235">그러나 다운로드가 너무 오래 걸리는 경우 UI를 다시 사용하도록 설정하고 다운로드를 취소하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-235">However, if the download takes too long, you want to re-enable the UI and discard the download:</span></span>

```csharp
public async void btnDownload_Click(object sender, EventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap> download = GetBitmapAsync(url);
        if (download == await Task.WhenAny(download, Task.Delay(3000)))
        {
            Bitmap bmp = await download;
            pictureBox.Image = bmp;
            status.Text = "Downloaded";
        }
        else
        {
            pictureBox.Image = null;
            status.Text = "Timed out";
            var ignored = download.ContinueWith(
                t => Trace("Task finally completed"));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

 <span data-ttu-id="ac2f7-236"><xref:System.Threading.Tasks.Task.WhenAll%2A>이 작업을 반환하므로 동일한 사항이 여러 다운로드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-236">The same applies to multiple downloads, because <xref:System.Threading.Tasks.Task.WhenAll%2A> returns a task:</span></span>

```csharp
public async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.Enabled = false;
    try
    {
        Task<Bitmap[]> downloads =
            Task.WhenAll(from url in urls select GetBitmapAsync(url));
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))
        {
            foreach(var bmp in downloads.Result) panel.AddImage(bmp);
            status.Text = "Downloaded";
        }
        else
        {
            status.Text = "Timed out";
            downloads.ContinueWith(t => Log(t));
        }
    }
    finally { btnDownload.Enabled = true; }
}
```

## <a name="building-task-based-combinators"></a><span data-ttu-id="ac2f7-237">작업 기반 조합기 구축</span><span class="sxs-lookup"><span data-stu-id="ac2f7-237">Building Task-based Combinators</span></span>
 <span data-ttu-id="ac2f7-238">작업(task)이 완전히 비동기 작업을 나타내고 작업에 조인, 결과 가져오기 등을 위한 동기 및 비동기 기능을 제공할 수 있으므로 작업을 구성하여 더 큰 패턴을 구축하는 유용한 조합기 라이브러리를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-238">Because a task is able to completely represent an asynchronous operation and provide synchronous and asynchronous capabilities for joining with the operation, retrieving its results, and so on, you can build useful libraries of combinators that compose tasks to build larger patterns.</span></span> <span data-ttu-id="ac2f7-239">이전 섹션에서 설명한 것처럼 .NET에는 몇 가지 기본 제공 조합기가 포함되어 있으나 직접 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-239">As discussed in the previous section, .NET includes several built-in combinators, but you can also build your own.</span></span> <span data-ttu-id="ac2f7-240">다음 섹션에서는 잠재적인 조합기 메서드 및 형식의 몇 가지 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-240">The following sections provide several examples of potential combinator methods and types.</span></span>

### <a name="retryonfault"></a><span data-ttu-id="ac2f7-241">RetryOnFault</span><span class="sxs-lookup"><span data-stu-id="ac2f7-241">RetryOnFault</span></span>
 <span data-ttu-id="ac2f7-242">대부분의 경우 이전 시도가 실패하면 작업을 다시 시도하려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-242">In many situations, you may want to retry an operation if a previous attempt fails.</span></span>  <span data-ttu-id="ac2f7-243">동기 코드의 경우 이를 위해 다음 예제의 `RetryOnFault`와 같은 도우미 메서드를 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-243">For synchronous code, you might build a helper method such as `RetryOnFault` in the following example to accomplish this:</span></span>

```csharp
public static T RetryOnFault<T>(
    Func<T> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return function(); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="ac2f7-244">TAP으로 구현되므로 작업(task)을 반환하는 비동기 작업에 대해서도 거의 동일한 도우미 메서드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-244">You can build an almost identical helper method for asynchronous operations that are implemented with TAP and thus return tasks:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
    }
    return default(T);
}
```

 <span data-ttu-id="ac2f7-245">이 조합기를 사용하여 애플리케이션의 논리에 다시 시도를 인코딩할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-245">You can then use this combinator to encode retries into the application's logic; for example:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3);
```

 <span data-ttu-id="ac2f7-246">`RetryOnFault` 함수를 추가로 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-246">You could extend the `RetryOnFault` function further.</span></span> <span data-ttu-id="ac2f7-247">예를 들어 이 함수는 다시 시도 중간에 호출되는 다른 `Func<Task>`를 수락하여 작업을 다시 시도해야 하는 시기를 결정할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-247">For example, the function could accept another `Func<Task>` that will be invoked between retries to determine when to try the operation again; for example:</span></span>

```csharp
public static async Task<T> RetryOnFault<T>(
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)
{
    for(int i=0; i<maxTries; i++)
    {
        try { return await function().ConfigureAwait(false); }
        catch { if (i == maxTries-1) throw; }
        await retryWhen().ConfigureAwait(false);
    }
    return default(T);
}
```

 <span data-ttu-id="ac2f7-248">그런 후 다음과 같은 함수를 사용하여 작업을 다시 시도하기 전에 잠시 대기할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-248">You could then use the function as follows to wait for a second before retrying the operation:</span></span>

```csharp
// Download the URL, trying up to three times in case of failure,
// and delaying for a second between retries
string pageContents = await RetryOnFault(
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));
```

### <a name="needonlyone"></a><span data-ttu-id="ac2f7-249">NeedOnlyOne</span><span class="sxs-lookup"><span data-stu-id="ac2f7-249">NeedOnlyOne</span></span>
 <span data-ttu-id="ac2f7-250">경우에 따라 작업의 대기 시간 및 성공 가능성을 개선하기 위해 중복성을 이용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-250">Sometimes, you can take advantage of redundancy to improve an operation's latency and chances for success.</span></span>  <span data-ttu-id="ac2f7-251">주식 시세를 제공하는 여러 웹 서비스가 있으나 각 서비스는 하루 중 다른 시간에 다른 수준의 품질 및 응답 시간을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-251">Consider multiple web services that provide stock quotes, but at various times of the day, each service may provide different levels of quality and response times.</span></span>  <span data-ttu-id="ac2f7-252">이러한 변동을 처리하려면 모든 웹 서비스로 요청을 보내고 응답을 받는 즉시 나머지 요청을 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-252">To deal with these fluctuations, you may issue requests to all the web services, and as soon as you get a response from one, cancel the remaining requests.</span></span>  <span data-ttu-id="ac2f7-253">도우미 함수를 구현하면 여러 작업을 시작하고, 하나가 완료되기를 기다린 후 나머지는 취소하는 이러한 일반적인 패턴을 보다 쉽게 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-253">You can implement a helper function to make it easier to implement this common pattern of launching multiple operations, waiting for any, and then canceling the rest.</span></span> <span data-ttu-id="ac2f7-254">다음 예제의 `NeedOnlyOne` 함수는 이 시나리오를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-254">The `NeedOnlyOne` function in the following example illustrates this scenario:</span></span>

```csharp
public static async Task<T> NeedOnlyOne(
    params Func<CancellationToken,Task<T>> [] functions)
{
    var cts = new CancellationTokenSource();
    var tasks = (from function in functions
                 select function(cts.Token)).ToArray();
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);
    cts.Cancel();
    foreach(var task in tasks)
    {
        var ignored = task.ContinueWith(
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);
    }
    return completed;
}
```

 <span data-ttu-id="ac2f7-255">그런 후 이 함수를 다음과 같이 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-255">You can then use this function as follows:</span></span>

```csharp
double currentPrice = await NeedOnlyOne(
    ct => GetCurrentPriceFromServer1Async("msft", ct),
    ct => GetCurrentPriceFromServer2Async("msft", ct),
    ct => GetCurrentPriceFromServer3Async("msft", ct));
```

### <a name="interleaved-operations"></a><span data-ttu-id="ac2f7-256">인터리브 작업</span><span class="sxs-lookup"><span data-stu-id="ac2f7-256">Interleaved Operations</span></span>
 <span data-ttu-id="ac2f7-257">큰 작업 세트를 사용할 때 <xref:System.Threading.Tasks.Task.WhenAny%2A> 메서드를 사용하여 인터리브 시나리오를 지원할 경우 성능 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-257">There is a potential performance problem with using the <xref:System.Threading.Tasks.Task.WhenAny%2A> method to support an interleaving scenario when you're working with large sets of tasks.</span></span> <span data-ttu-id="ac2f7-258"><xref:System.Threading.Tasks.Task.WhenAny%2A>에 대한 모든 호출로 각 작업에 연속이 등록되게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-258">Every call to <xref:System.Threading.Tasks.Task.WhenAny%2A> results in a continuation being registered with each task.</span></span> <span data-ttu-id="ac2f7-259">작업 수가 N이면 인터리브 작업의 수명 동안 O(N<sup>2</sup>) 연속이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-259">For N number of tasks, this results in O(N<sup>2</sup>) continuations created over the lifetime of the interleaving operation.</span></span> <span data-ttu-id="ac2f7-260">큰 작업을 하는 경우에는 성능 문제를 해결하기 위해 (다음 예의 `Interleaved`와 같은) 조합기를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-260">If you're working with a large set of tasks, you can use a combinator (`Interleaved` in the following example) to address the performance issue:</span></span>

```csharp
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)
{
    var inputTasks = tasks.ToList();
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)
                   select new TaskCompletionSource<T>()).ToList();
    int nextTaskIndex = -1;
    foreach (var inputTask in inputTasks)
    {
        inputTask.ContinueWith(completed =>
        {
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];
            if (completed.IsFaulted)
                source.TrySetException(completed.Exception.InnerExceptions);
            else if (completed.IsCanceled)
                source.TrySetCanceled();
            else
                source.TrySetResult(completed.Result);
        }, CancellationToken.None,
           TaskContinuationOptions.ExecuteSynchronously,
           TaskScheduler.Default);
    }
    return from source in sources
           select source.Task;
}
```

 <span data-ttu-id="ac2f7-261">그런 다음 조합기를 사용하여 완료된 작업의 결과를 처리할 수 있습니다. 예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-261">You can then use the combinator to process the results of tasks as they complete; for example:</span></span>

```csharp
IEnumerable<Task<int>> tasks = ...;
foreach(var task in Interleaved(tasks))
{
    int result = await task;
    …
}
```

### <a name="whenallorfirstexception"></a><span data-ttu-id="ac2f7-262">WhenAllOrFirstException</span><span class="sxs-lookup"><span data-stu-id="ac2f7-262">WhenAllOrFirstException</span></span>
 <span data-ttu-id="ac2f7-263">특정 분산/수집 시나리오에서 집합의 작업 하나가 실패하지 않는 한, 모든 작업이 완료되기를 기다리며, 실패하는 작업이 있으면 예외가 발생하는 즉시 대기를 중지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-263">In certain scatter/gather scenarios, you might want to wait for all tasks in a set, unless one of them faults, in which case you want to stop waiting as soon as the exception occurs.</span></span>  <span data-ttu-id="ac2f7-264">다음 예제의 `WhenAllOrFirstException`과 같은 조합기 메서드로 이러한 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-264">You can accomplish that with a combinator method such as `WhenAllOrFirstException` in the following example:</span></span>

```csharp
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)
{
    var inputs = tasks.ToList();
    var ce = new CountdownEvent(inputs.Count);
    var tcs = new TaskCompletionSource<T[]>();

    Action<Task> onCompleted = (Task completed) =>
    {
        if (completed.IsFaulted)
            tcs.TrySetException(completed.Exception.InnerExceptions);
        if (ce.Signal() && !tcs.Task.IsCompleted)
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());
    };

    foreach (var t in inputs) t.ContinueWith(onCompleted);
    return tcs.Task;
}
```

## <a name="building-task-based-data-structures"></a><span data-ttu-id="ac2f7-265">작업 기반 데이터 구조 구축</span><span class="sxs-lookup"><span data-stu-id="ac2f7-265">Building Task-based Data Structures</span></span>
 <span data-ttu-id="ac2f7-266">사용자 지정 작업 기반 조합기를 구축하는 기능 외에도, <xref:System.Threading.Tasks.Task> 및 <xref:System.Threading.Tasks.Task%601>에서 비동기 작업의 결과와 조인을 위해 필요한 동기화를 모두 나타내는 데이터 구조를 유지하면 비동기 시나리오에서 사용할 사용자 지정 데이터 구조를 빌드할 수 있는 강력한 형식이 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-266">In addition to the ability to build custom task-based combinators, having a data structure in <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> that represents both the results of an asynchronous operation and the necessary synchronization to join with it makes it a powerful type on which to build custom data structures to be used in asynchronous scenarios.</span></span>

### <a name="asynccache"></a><span data-ttu-id="ac2f7-267">AsyncCache</span><span class="sxs-lookup"><span data-stu-id="ac2f7-267">AsyncCache</span></span>
 <span data-ttu-id="ac2f7-268">작업의 한 가지 중요한 측면은 작업이 여러 소비자에게 전달될 수 있으며, 이들 모두가 작업을 대기하고, 작업에 연속을 등록하고, 해당 결과 또는 예외를 가져올(<xref:System.Threading.Tasks.Task%601>의 경우) 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-268">One important aspect of a task is that it may be handed out to multiple consumers, all of whom may await it, register continuations with it, get its result or exceptions (in the case of <xref:System.Threading.Tasks.Task%601>), and so on.</span></span>  <span data-ttu-id="ac2f7-269">이로 인해 <xref:System.Threading.Tasks.Task> 및 <xref:System.Threading.Tasks.Task%601> 개체가 비동기 캐싱 인프라에서 사용되는 데 완전히 적합하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-269">This makes <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> perfectly suited to be used in an asynchronous caching infrastructure.</span></span>  <span data-ttu-id="ac2f7-270">다음은 <xref:System.Threading.Tasks.Task%601> 개체를 기반으로 빌드한 작지만 강력한 비동기 캐시의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-270">Here's an example of a small but powerful asynchronous cache built on top of <xref:System.Threading.Tasks.Task%601>:</span></span>

```csharp
public class AsyncCache<TKey, TValue>
{
    private readonly Func<TKey, Task<TValue>> _valueFactory;
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;

    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)
    {
        if (valueFactory == null) throw new ArgumentNullException("loader");
        _valueFactory = valueFactory;
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();
    }

    public Task<TValue> this[TKey key]
    {
        get
        {
            if (key == null) throw new ArgumentNullException("key");
            return _map.GetOrAdd(key, toAdd =>
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;
        }
    }
}
```

 <span data-ttu-id="ac2f7-271">[AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) 클래스는 `TKey`를 받고 <xref:System.Threading.Tasks.Task%601> 개체를 반환하는 함수를 해당 생성자에 대한 대리자로 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-271">The [AsyncCache\<TKey,TValue>](https://devblogs.microsoft.com/pfxteam/parallelextensionsextras-tour-12-asynccache/) class accepts as a delegate to its constructor a function that takes a `TKey` and returns a <xref:System.Threading.Tasks.Task%601>.</span></span>  <span data-ttu-id="ac2f7-272">캐시에서 이전에 액세스했던 값은 내부 사전에 저장되며, 캐시에 동시에 액세스하더라도 `AsyncCache`는 키당 하나의 작업만 생성되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-272">Any previously accessed values from the cache are stored in the internal dictionary, and the `AsyncCache` ensures that only one task is generated per key, even if the cache is accessed concurrently.</span></span>

 <span data-ttu-id="ac2f7-273">예를 들어 다운로드한 웹 페이지에 대한 캐시를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-273">For example, you can build a cache for downloaded web pages:</span></span>

```csharp
private AsyncCache<string,string> m_webPages =
    new AsyncCache<string,string>(DownloadStringAsync);
```

 <span data-ttu-id="ac2f7-274">그런 다음 웹 페이지의 콘텐츠가 필요할 때마다 비동기 메서드에서 이 캐시를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-274">You can then use this cache in asynchronous methods whenever you need the contents of a web page.</span></span> <span data-ttu-id="ac2f7-275">`AsyncCache` 클래스는 가능한 작은 수의 페이지를 다운로드하도록 하고 결과를 캐시합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-275">The `AsyncCache` class ensures that you're downloading as few pages as possible, and caches the results.</span></span>

```csharp
private async void btnDownload_Click(object sender, RoutedEventArgs e)
{
    btnDownload.IsEnabled = false;
    try
    {
        txtContents.Text = await m_webPages["https://www.microsoft.com"];
    }
    finally { btnDownload.IsEnabled = true; }
}
```

### <a name="asyncproducerconsumercollection"></a><span data-ttu-id="ac2f7-276">AsyncProducerConsumerCollection</span><span class="sxs-lookup"><span data-stu-id="ac2f7-276">AsyncProducerConsumerCollection</span></span>
 <span data-ttu-id="ac2f7-277">또한 작업을 사용하여 비동기 활동을 조정하기 위한 데이터 구조를 구축할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-277">You can also use tasks to build data structures for coordinating asynchronous activities.</span></span>  <span data-ttu-id="ac2f7-278">클래식 병렬 디자인인 생산자/소비자 중 하나를 고려하세요.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-278">Consider one of the classic parallel design patterns: producer/consumer.</span></span>  <span data-ttu-id="ac2f7-279">이 패턴에서 생산자는 소비자가 사용하는 데이터를 생성하고, 생산자와 소비자가 동시에 실행될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-279">In this pattern, producers generate data that is consumed by consumers, and the producers and consumers may run in parallel.</span></span> <span data-ttu-id="ac2f7-280">예를 들어, 소비자는 항목 2를 생성하고 있는 생산자가 이전에 생성한 항목 1을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-280">For example, the consumer processes item 1, which was previously generated by a producer who is now producing item 2.</span></span>  <span data-ttu-id="ac2f7-281">생산자/소비자 패턴의 경우 항상 소비자가 새 데이터에 대한 알림을 수신하고 사용 가능할 때 찾을 수 있도록 생산자가 만든 작업을 저장할 일부 데이터 구조가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-281">For the producer/consumer pattern, you invariably need some data structure to store the work created by producers so that the consumers may be notified of new data and find it when available.</span></span>

 <span data-ttu-id="ac2f7-282">비동기 메서드가 생산자 및 소비자로 사용할 수 있게 해 주는 작업 기반의 간단한 데이터 구조는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-282">Here's a simple data structure, built on top of tasks, that enables asynchronous methods to be used as producers and consumers:</span></span>

```csharp
public class AsyncProducerConsumerCollection<T>
{
    private readonly Queue<T> m_collection = new Queue<T>();
    private readonly Queue<TaskCompletionSource<T>> m_waiting =
        new Queue<TaskCompletionSource<T>>();

    public void Add(T item)
    {
        TaskCompletionSource<T> tcs = null;
        lock (m_collection)
        {
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();
            else m_collection.Enqueue(item);
        }
        if (tcs != null) tcs.TrySetResult(item);
    }

    public Task<T> Take()
    {
        lock (m_collection)
        {
            if (m_collection.Count > 0)
            {
                return Task.FromResult(m_collection.Dequeue());
            }
            else
            {
                var tcs = new TaskCompletionSource<T>();
                m_waiting.Enqueue(tcs);
                return tcs.Task;
            }
        }
    }
}
```

 <span data-ttu-id="ac2f7-283">해당 데이터 구조가 준비되면 다음과 같이 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-283">With that data structure in place, you can write code such as the following:</span></span>

```csharp
private static AsyncProducerConsumerCollection<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.Take();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Add(data);
}
```

<span data-ttu-id="ac2f7-284"><xref:System.Threading.Tasks.Dataflow> 네임스페이스에는 <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> 형식이 포함됩니다. 이 형식을 다음과 유사한 방식으로 사용할 수 있지만, 사용자 지정 컬렉션 형식을 빌드하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-284">The <xref:System.Threading.Tasks.Dataflow> namespace includes the <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> type, which you can use in a similar manner, but without having to build a custom collection type:</span></span>

```csharp
private static BufferBlock<int> m_data = …;
…
private static async Task ConsumerAsync()
{
    while(true)
    {
        int nextItem = await m_data.ReceiveAsync();
        ProcessNextItem(nextItem);
    }
}
…
private static void Produce(int data)
{
    m_data.Post(data);
}
```

> [!NOTE]
> <span data-ttu-id="ac2f7-285"><xref:System.Threading.Tasks.Dataflow> 네임스페이스는 NuGet 패키지로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-285">The <xref:System.Threading.Tasks.Dataflow> namespace is available as a NuGet package.</span></span> <span data-ttu-id="ac2f7-286"><xref:System.Threading.Tasks.Dataflow> 네임스페이스가 포함된 어셈블리를 설치하려면 Visual Studio에서 프로젝트를 열고 프로젝트 메뉴에서 **NuGet 패키지 관리** 를 선택한 후 온라인으로 `System.Threading.Tasks.Dataflow` 패키지를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ac2f7-286">To install the assembly that contains the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in Visual Studio, choose **Manage NuGet Packages** from the Project menu, and search online for the `System.Threading.Tasks.Dataflow` package.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac2f7-287">참조</span><span class="sxs-lookup"><span data-stu-id="ac2f7-287">See also</span></span>

- [<span data-ttu-id="ac2f7-288">TAP(작업 기반 비동기 패턴)</span><span class="sxs-lookup"><span data-stu-id="ac2f7-288">Task-based Asynchronous Pattern (TAP)</span></span>](task-based-asynchronous-pattern-tap.md)
- [<span data-ttu-id="ac2f7-289">작업 기반 비동기 패턴 구현</span><span class="sxs-lookup"><span data-stu-id="ac2f7-289">Implementing the Task-based Asynchronous Pattern</span></span>](implementing-the-task-based-asynchronous-pattern.md)
- [<span data-ttu-id="ac2f7-290">다른 비동기 패턴 및 형식과의 Interop</span><span class="sxs-lookup"><span data-stu-id="ac2f7-290">Interop with Other Asynchronous Patterns and Types</span></span>](interop-with-other-asynchronous-patterns-and-types.md)
