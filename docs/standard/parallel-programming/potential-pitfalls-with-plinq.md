---
title: PLINQ에서 발생할 수 있는 문제
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
ms.openlocfilehash: 1e1763132cd0ee8f1135e562c36ce4adf603f5af
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822245"
---
# <a name="potential-pitfalls-with-plinq"></a><span data-ttu-id="450a8-102">PLINQ에서 발생할 수 있는 문제</span><span class="sxs-lookup"><span data-stu-id="450a8-102">Potential pitfalls with PLINQ</span></span>

<span data-ttu-id="450a8-103">대부분의 경우 PLINQ는 순차적인 LINQ to Objects 쿼리에 대해 상당한 성능 향상을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-103">In many cases, PLINQ can provide significant performance improvements over sequential LINQ to Objects queries.</span></span> <span data-ttu-id="450a8-104">그러나 쿼리 실행을 병렬 처리하는 작업에는 순차적 코드에서는 일반적이지 않거나 전혀 발생하지 않는 문제를 일으킬 수 있는 복잡성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-104">However, the work of parallelizing the query execution introduces complexity that can lead to problems that, in sequential code, are not as common or are not encountered at all.</span></span> <span data-ttu-id="450a8-105">이 항목에서는 PLINQ 쿼리를 작성할 때 주의해야 할 사항을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-105">This topic lists some practices to avoid when you write PLINQ queries.</span></span>

## <a name="dont-assume-that-parallel-is-always-faster"></a><span data-ttu-id="450a8-106">병렬이 항상 더 빠르다고 가정하지 말 것</span><span class="sxs-lookup"><span data-stu-id="450a8-106">Don't assume that parallel is always faster</span></span>

<span data-ttu-id="450a8-107">경우에 따라 병렬 처리로 인해 PLINQ 쿼리가 LINQ to Objects 쿼리보다 느리게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-107">Parallelization sometimes causes a PLINQ query to run slower than its LINQ to Objects equivalent.</span></span> <span data-ttu-id="450a8-108">소스 요소가 적고 빠른 사용자 대리자가 있는 쿼리의 속도가 훨씬 빠를 가능성이 없다는 것이 경험적인 기본 규칙입니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-108">The basic rule of thumb is that queries that have few source elements and fast user delegates are unlikely to speedup much.</span></span> <span data-ttu-id="450a8-109">그러나 많은 요소가 성능에 관련되므로 PLINQ를 사용할지 결정하기 전에 실제 결과를 측정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-109">However, because many factors are involved in performance, we recommend that you measure actual results before you decide whether to use PLINQ.</span></span> <span data-ttu-id="450a8-110">자세한 내용은 [PLINQ의 속도 향상 이해](understanding-speedup-in-plinq.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="450a8-110">For more information, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>

## <a name="avoid-writing-to-shared-memory-locations"></a><span data-ttu-id="450a8-111">공유 메모리 위치에 쓰기 방지</span><span class="sxs-lookup"><span data-stu-id="450a8-111">Avoid writing to shared memory locations</span></span>

<span data-ttu-id="450a8-112">순차적 코드에서는 정적 변수 또는 클래스 필드에서 읽거나 쓰는 것은 일반적입니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-112">In sequential code, it is not uncommon to read from or write to static variables or class fields.</span></span> <span data-ttu-id="450a8-113">그러나 여러 스레드가 해당 변수에 동시에 액세스할 때마다 경합 상태가 발생할 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-113">However, whenever multiple threads are accessing such variables concurrently, there is a big potential for race conditions.</span></span> <span data-ttu-id="450a8-114">잠금을 사용하여 변수에 대한 액세스를 동기화할 수 있지만 동기화의 비용으로 성능이 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-114">Even though you can use locks to synchronize access to the variable, the cost of synchronization can hurt performance.</span></span> <span data-ttu-id="450a8-115">따라서 가능한 한 PLINQ 쿼리에서 공유된 상태에 대한 액세스를 방지하거나 최소한의 제한으로 액세스하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-115">Therefore, we recommend that you avoid, or at least limit, access to shared state in a PLINQ query as much as possible.</span></span>

## <a name="avoid-over-parallelization"></a><span data-ttu-id="450a8-116">과도한 병렬화 방지</span><span class="sxs-lookup"><span data-stu-id="450a8-116">Avoid over-parallelization</span></span>

<span data-ttu-id="450a8-117">`AsParallel` 메서드를 사용하면 소스 컬렉션을 분할하고 작업자 스레드를 동기화하는 오버헤드 비용이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-117">By using the `AsParallel` method, you incur the overhead costs of partitioning the source collection and synchronizing the worker threads.</span></span> <span data-ttu-id="450a8-118">병렬화의 이점은 컴퓨터의 프로세서 수로 더 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-118">The benefits of parallelization are further limited by the number of processors on the computer.</span></span> <span data-ttu-id="450a8-119">하나의 프로세서에서 여러 컴퓨팅 바인딩된 스레드를 실행하여 얻을 수 있는 속도 향상이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-119">There is no speedup to be gained by running multiple compute-bound threads on just one processor.</span></span> <span data-ttu-id="450a8-120">따라서 쿼리를 과도하게 병렬 처리하지 않도록 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-120">Therefore, you must be careful not to over-parallelize a query.</span></span>

<span data-ttu-id="450a8-121">과도한 병렬 처리가 발생할 수 있는 가장 일반적인 시나리오는 다음 코드 조각에 표시된 대로 중첩된 루프에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-121">The most common scenario in which over-parallelization can occur is in nested queries, as shown in the following snippet.</span></span>

[!code-csharp[PLINQ#20](~/samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
[!code-vb[PLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]

<span data-ttu-id="450a8-122">이 경우에서 다음 조건 중 하나 이상이 적용되지 않는 한 외부 데이터 소스(고객)만을 병렬 처리하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-122">In this case, it is best to parallelize only the outer data source (customers) unless one or more of the following conditions apply:</span></span>

- <span data-ttu-id="450a8-123">내부 데이터 소스(cust.Orders)가 매우 긴 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-123">The inner data source (cust.Orders) is known to be very long.</span></span>

- <span data-ttu-id="450a8-124">각 순서에서 비용이 많이 드는 계산을 수행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-124">You are performing an expensive computation on each order.</span></span> <span data-ttu-id="450a8-125">(이 예제에 나와 있는 작업은 비용이 많이 들지 않습니다.)</span><span class="sxs-lookup"><span data-stu-id="450a8-125">(The operation shown in the example is not expensive.)</span></span>

- <span data-ttu-id="450a8-126">대상 시스템은 `cust.Orders`에서 쿼리를 병렬화하여 생성될 스레드의 수를 처리할 충분한 프로세서를 가진 것으로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-126">The target system is known to have enough processors to handle the number of threads that will be produced by parallelizing the query on `cust.Orders`.</span></span>

<span data-ttu-id="450a8-127">모든 경우에서 최적의 쿼리 형태를 결정하는 가장 좋은 방법은 테스트하고 측정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-127">In all cases, the best way to determine the optimum query shape is to test and measure.</span></span> <span data-ttu-id="450a8-128">자세한 내용은 [방법: PLINQ 쿼리 성능 측정](how-to-measure-plinq-query-performance.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="450a8-128">For more information, see [How to: Measure PLINQ Query Performance](how-to-measure-plinq-query-performance.md).</span></span>

## <a name="avoid-calls-to-non-thread-safe-methods"></a><span data-ttu-id="450a8-129">스레드로부터 안전하지 않은 메서드에 대한 호출 방지</span><span class="sxs-lookup"><span data-stu-id="450a8-129">Avoid calls to non-thread-safe methods</span></span>

<span data-ttu-id="450a8-130">PLINQ 쿼리에서 스레드로부터 안전하지 않은 인스턴스 메서드를 작성하면 프로그램에서 감지하거나 감지하지 않을 수도 있는 데이터 손상이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-130">Writing to non-thread-safe instance methods from a PLINQ query can lead to data corruption which may or may not go undetected in your program.</span></span> <span data-ttu-id="450a8-131">예외가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-131">It can also lead to exceptions.</span></span> <span data-ttu-id="450a8-132">다음 예제에서는 여러 스레드가 `FileStream.Write` 메서드를 동시에 호출하려고 합니다. 이는 클래스에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-132">In the following example, multiple threads would be attempting to call the `FileStream.Write` method simultaneously, which is not supported by the class.</span></span>

```vb
Dim fs As FileStream = File.OpenWrite(…)
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))
```

```csharp
FileStream fs = File.OpenWrite(...);
a.AsParallel().Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));
```

## <a name="limit-calls-to-thread-safe-methods"></a><span data-ttu-id="450a8-133">스레드로부터 안전한 메서드에 대한 호출 제한</span><span class="sxs-lookup"><span data-stu-id="450a8-133">Limit calls to thread-safe methods</span></span>

<span data-ttu-id="450a8-134">.NET에서 대부분의 정적 메서드는 스레드로부터 안전하고 여러 스레드에서 동시에 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-134">Most static methods in .NET are thread-safe and can be called from multiple threads concurrently.</span></span> <span data-ttu-id="450a8-135">그러나 이러한 경우에도 관련된 동기화로 인해 쿼리 속도가 상당히 느려질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-135">However, even in these cases, the synchronization involved can lead to significant slowdown in the query.</span></span>

> [!NOTE]
> <span data-ttu-id="450a8-136">쿼리에서 <xref:System.Console.WriteLine%2A>에 일부 호출을 삽입하여 이를 직접 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-136">You can test for this yourself by inserting some calls to <xref:System.Console.WriteLine%2A> in your queries.</span></span> <span data-ttu-id="450a8-137">이 메서드는 설명 목적으로 설명서 예제에서 사용되지만 PLINQ 쿼리에서 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="450a8-137">Although this method is used in the documentation examples for demonstration purposes, do not use it in PLINQ queries.</span></span>

## <a name="avoid-unnecessary-ordering-operations"></a><span data-ttu-id="450a8-138">불필요한 순서 지정 작업 방지</span><span class="sxs-lookup"><span data-stu-id="450a8-138">Avoid unnecessary ordering operations</span></span>

<span data-ttu-id="450a8-139">PLINQ는 쿼리를 병렬로 실행할 때 소스 시퀀스를 여러 스레드에서 동시에 작동할 수 있는 파티션으로 나눕니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-139">When PLINQ executes a query in parallel, it divides the source sequence into partitions that can be operated on concurrently on multiple threads.</span></span> <span data-ttu-id="450a8-140">기본적으로 파티션이 처리되고 결과가 전달되는 순서는 예측할 수 없습니다(`OrderBy` 같은 연산자 제외).</span><span class="sxs-lookup"><span data-stu-id="450a8-140">By default, the order in which the partitions are processed and the results are delivered is not predictable (except for operators such as `OrderBy`).</span></span> <span data-ttu-id="450a8-141">소스 시퀀스의 순서를 유지하도록 PLINQ에 지시할 수 있지만 이 지시는 성능에 부정적인 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-141">You can instruct PLINQ to preserve the ordering of any source sequence, but this has a negative impact on performance.</span></span> <span data-ttu-id="450a8-142">가능한 한 순서 유지에 의존하지 않도록 쿼리를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-142">The best practice, whenever possible, is to structure queries so that they do not rely on order preservation.</span></span> <span data-ttu-id="450a8-143">자세한 내용은 [PLINQ에서 순서 유지](order-preservation-in-plinq.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="450a8-143">For more information, see [Order Preservation in PLINQ](order-preservation-in-plinq.md).</span></span>

## <a name="prefer-forall-to-foreach-when-it-is-possible"></a><span data-ttu-id="450a8-144">가능한 경우 ForEach보다 ForAll 사용</span><span class="sxs-lookup"><span data-stu-id="450a8-144">Prefer ForAll to ForEach when it is possible</span></span>

<span data-ttu-id="450a8-145">PLINQ는 여러 스레드에서 쿼리를 실행하지만 `foreach` 루프(Visual Basic의 `For Each`)의 결과를 사용하는 경우 쿼리 결과는 한 스레드로 다시 병합되고 열거자에 의해 직렬로 액세스되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-145">Although PLINQ executes a query on multiple threads, if you consume the results in a `foreach` loop (`For Each` in Visual Basic), then the query results must be merged back into one thread and accessed serially by the enumerator.</span></span> <span data-ttu-id="450a8-146">경우에 따라 이 상황은 피할 수 없지만, 가능한 한 `ForAll` 메서드를 사용하여 <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> 같은 스레드로부터 안전한 컬렉션을 작성하는 등의 방법으로 스레드가 고유한 결과를 출력하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-146">In some cases, this is unavoidable; however, whenever possible, use the `ForAll` method to enable each thread to output its own results, for example, by writing to a thread-safe collection such as <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="450a8-147"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>에도 같은 문제가 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-147">The same issue applies to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="450a8-148">즉, `Parallel.ForEach(source.AsParallel().Where(), ...)`보다 `source.AsParallel().Where().ForAll(...)`을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-148">In other words, `source.AsParallel().Where().ForAll(...)` should be strongly preferred to `Parallel.ForEach(source.AsParallel().Where(), ...)`.</span></span>

## <a name="be-aware-of-thread-affinity-issues"></a><span data-ttu-id="450a8-149">스레드 선호도 문제 인식</span><span class="sxs-lookup"><span data-stu-id="450a8-149">Be aware of thread affinity issues</span></span>

<span data-ttu-id="450a8-150">STA(단일 스레드 아파트) 구성 요소에 대한 COM 상호 운용성, Windows Forms 및 WPF(Windows Presentation Foundation)와 같은 일부 기술은 특정 스레드에서 실행하는 코드를 필요로 하는 스레드 선호도 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-150">Some technologies, for example, COM interoperability for Single-Threaded Apartment (STA) components, Windows Forms, and Windows Presentation Foundation (WPF), impose thread affinity restrictions that require code to run on a specific thread.</span></span> <span data-ttu-id="450a8-151">예를 들어 Windows Forms 및 WPF에서 컨트롤은 작성된 스레드에서만 액세스될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-151">For example, in both Windows Forms and WPF, a control can only be accessed on the thread on which it was created.</span></span> <span data-ttu-id="450a8-152">PLINQ 쿼리에서 Windows Forms 컨트롤의 공유 상태에 액세스하려고 하면 디버거에서 실행 중인 경우 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-152">If you try to access the shared state of a Windows Forms control in a PLINQ query, an exception is raised if you are running in the debugger.</span></span> <span data-ttu-id="450a8-153">(이 설정은 해제할 수 있습니다.) 그러나 쿼리를 UI 스레드에서 사용하는 경우 해당 코드가 한 스레드에서만 실행되므로 쿼리 결과를 열거하는 `foreach` 루프에서 이 컨트롤에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-153">(This setting can be turned off.) However, if your query is consumed on the UI thread, then you can access the control from the `foreach` loop that enumerates the query results because that code executes on just one thread.</span></span>

## <a name="dont-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a><span data-ttu-id="450a8-154">ForEach, For 및 ForAll의 반복이 항상 병렬로 실행된다고 가정하지 말 것</span><span class="sxs-lookup"><span data-stu-id="450a8-154">Don't assume that iterations of ForEach, For, and ForAll always execute in parallel</span></span>

<span data-ttu-id="450a8-155"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> 또는 <xref:System.Linq.ParallelEnumerable.ForAll%2A> 루프의 개별 반복이 병렬로 실행될 수 있지만, 반드시 병렬로 실행될 필요는 없다는 사실을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-155">It is important to keep in mind that individual iterations in a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>, or <xref:System.Linq.ParallelEnumerable.ForAll%2A> loop may but do not have to execute in parallel.</span></span> <span data-ttu-id="450a8-156">따라서 반복의 병렬 실행 또는 특정 순서로 반복 실행의 정확성에 의존하는 코드를 작성하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="450a8-156">Therefore, you should avoid writing any code that depends for correctness on parallel execution of iterations or on the execution of iterations in any particular order.</span></span>

<span data-ttu-id="450a8-157">예를 들어 다음 코드는 교착 상태의 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-157">For example, this code is likely to deadlock:</span></span>

```vb
Dim mre = New ManualResetEventSlim()
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll(Sub(j)
   If j = Environment.ProcessorCount Then
       Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Set()
   Else
       Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)
       mre.Wait()
   End If
End Sub) ' deadlocks
```

```csharp
ManualResetEventSlim mre = new ManualResetEventSlim();
Enumerable.Range(0, Environment.ProcessorCount * 100).AsParallel().ForAll((j) =>
{
    if (j == Environment.ProcessorCount)
    {
        Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Set();
    }
    else
    {
        Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);
        mre.Wait();
    }
}); //deadlocks
```

<span data-ttu-id="450a8-158">이 예제에서는 하나의 반복이 이벤트를 설정하고 다른 모든 반복은 이벤트를 기다립니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-158">In this example, one iteration sets an event, and all other iterations wait on the event.</span></span> <span data-ttu-id="450a8-159">대기 중인 반복은 이벤트 설정 반복이 완료될 때까지 완료할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-159">None of the waiting iterations can complete until the event-setting iteration has completed.</span></span> <span data-ttu-id="450a8-160">그러나 대기 중인 반복은 이벤트 설정 반복이 실행될 기회를 갖기 전에 병렬 루프를 실행하는 데 사용되는 모든 스레드를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-160">However, it is possible that the waiting iterations block all threads that are used to execute the parallel loop, before the event-setting iteration has had a chance to execute.</span></span> <span data-ttu-id="450a8-161">이로 인해 교착 상태가 발생하고 이벤트 설정 반복은 실행되지 않으며 대기 중인 반복은 시작되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-161">This results in a deadlock – the event-setting iteration will never execute, and the waiting iterations will never wake up.</span></span>

<span data-ttu-id="450a8-162">특히 병렬 루프의 하나의 반복은 다른 루프의 반복이 진행되기를 기다리면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-162">In particular, one iteration of a parallel loop should never wait on another iteration of the loop to make progress.</span></span> <span data-ttu-id="450a8-163">병렬 루프가 반대 순서로 순차적으로 반복되도록 결정하는 경우 교착 상태가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="450a8-163">If the parallel loop decides to schedule the iterations sequentially but in the opposite order, a deadlock will occur.</span></span>

## <a name="see-also"></a><span data-ttu-id="450a8-164">참조</span><span class="sxs-lookup"><span data-stu-id="450a8-164">See also</span></span>

- [<span data-ttu-id="450a8-165">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="450a8-165">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
