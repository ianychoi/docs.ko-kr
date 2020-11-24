---
title: 가비지 컬렉션 및 성능
description: 가비지 수집 및 메모리 사용량과 관련된 문제에 대해 알아봅니다. 가비지 수집이 애플리케이션에 미치는 영향을 최소화하는 방법을 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
ms.openlocfilehash: 15ca3fd06bb607a4f0257b4c5cd62f9c935c6913
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94827544"
---
# <a name="garbage-collection-and-performance"></a><span data-ttu-id="2b5fd-104">가비지 컬렉션 및 성능</span><span class="sxs-lookup"><span data-stu-id="2b5fd-104">Garbage Collection and Performance</span></span>

<span data-ttu-id="2b5fd-105">이 항목에서는 가비지 수집 및 메모리 사용과 관련된 문제를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-105">This topic describes issues related to garbage collection and memory usage.</span></span> <span data-ttu-id="2b5fd-106">관리되는 힙과 관련된 문제를 해결하고 애플리케이션에 미치는 가비지 컬렉션의 영향을 최소화하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-106">It addresses issues that pertain to the managed heap and explains how to minimize the effect of garbage collection on your applications.</span></span> <span data-ttu-id="2b5fd-107">각 문제에는 문제를 조사하는 데 사용할 수 있는 절차 링크가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-107">Each issue has links to procedures that you can use to investigate problems.</span></span>

## <a name="performance-analysis-tools"></a><span data-ttu-id="2b5fd-108">성능 분석 도구</span><span class="sxs-lookup"><span data-stu-id="2b5fd-108">Performance Analysis Tools</span></span>

<span data-ttu-id="2b5fd-109">다음 섹션에서는 메모리 사용 및 가비지 컬렉션 문제를 조사하는 데 사용할 수 있는 도구를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-109">The following sections describe the tools that are available for investigating memory usage and garbage collection issues.</span></span> <span data-ttu-id="2b5fd-110">이 항목의 뒷부분에 제공된 [절차](#performance-check-procedures)에서는 이러한 도구를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-110">The [procedures](#performance-check-procedures) provided later in this topic refer to these tools.</span></span>

### <a name="memory-performance-counters"></a><span data-ttu-id="2b5fd-111">메모리 성능 카운터</span><span class="sxs-lookup"><span data-stu-id="2b5fd-111">Memory Performance Counters</span></span>

<span data-ttu-id="2b5fd-112">성능 카운터를 사용하여 성능 데이터를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-112">You can use performance counters to gather performance data.</span></span> <span data-ttu-id="2b5fd-113">자세한 내용은 [런타임 프로파일링](../../framework/debug-trace-profile/runtime-profiling.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-113">For instructions, see [Runtime Profiling](../../framework/debug-trace-profile/runtime-profiling.md).</span></span> <span data-ttu-id="2b5fd-114">[.NET의 성능 카운터](../../framework/debug-trace-profile/performance-counters.md)에 설명된 대로 성능 카운터의 .NET CLR 메모리 범주는 가비지 수집기에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-114">The .NET CLR Memory category of performance counters, as described in [Performance Counters in .NET](../../framework/debug-trace-profile/performance-counters.md), provides information about the garbage collector.</span></span>

### <a name="debugging-with-sos"></a><span data-ttu-id="2b5fd-115">SOS를 사용한 디버깅</span><span class="sxs-lookup"><span data-stu-id="2b5fd-115">Debugging with SOS</span></span>

<span data-ttu-id="2b5fd-116">[Windows 디버거(WinDbg)](/windows-hardware/drivers/debugger/index)를 사용하여 관리되는 힙의 개체를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-116">You can use the [Windows Debugger (WinDbg)](/windows-hardware/drivers/debugger/index) to inspect objects on the managed heap.</span></span>

<span data-ttu-id="2b5fd-117">WinDbg를 설치하려면 [Debugging Tools for Windows 다운로드](/windows-hardware/drivers/debugger/debugger-download-tools) 페이지에서 Debugging Tools for Windows를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-117">To install WinDbg, install Debugging Tools for Windows from the [Download Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) page.</span></span>

### <a name="garbage-collection-etw-events"></a><span data-ttu-id="2b5fd-118">가비지 컬렉션 ETW 이벤트</span><span class="sxs-lookup"><span data-stu-id="2b5fd-118">Garbage Collection ETW Events</span></span>

<span data-ttu-id="2b5fd-119">ETW(Windows용 이벤트 추적)는 .NET에서 제공하는 프로파일링 및 디버깅 지원을 보완하는 추적 시스템입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-119">Event tracing for Windows (ETW) is a tracing system that supplements the profiling and debugging support provided by .NET.</span></span> <span data-ttu-id="2b5fd-120">.NET Framework 4부터 [가비지 수집 ETW 이벤트](../../framework/performance/garbage-collection-etw-events.md)는 통계 관점에서 관리되는 힙을 분석하는 데 유용한 정보를 캡처합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-120">Starting with .NET Framework 4, [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md) capture useful information for analyzing the managed heap from a statistical point of view.</span></span> <span data-ttu-id="2b5fd-121">예를 들어 가비지 수집이 수행되려고 할 때 발생하는 `GCStart_V1` 이벤트는 다음과 같은 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-121">For example, the `GCStart_V1` event, which is raised when a garbage collection is about to occur, provides the following information:</span></span>

- <span data-ttu-id="2b5fd-122">수집되는 개체 세대</span><span class="sxs-lookup"><span data-stu-id="2b5fd-122">Which generation of objects is being collected.</span></span>

- <span data-ttu-id="2b5fd-123">가비지 수집 트리거</span><span class="sxs-lookup"><span data-stu-id="2b5fd-123">What triggered the garbage collection.</span></span>

- <span data-ttu-id="2b5fd-124">가비지 수집 유형(동시 수집 또는 비동시 수집)</span><span class="sxs-lookup"><span data-stu-id="2b5fd-124">Type of garbage collection (concurrent or not concurrent).</span></span>

<span data-ttu-id="2b5fd-125">ETW 이벤트 로깅은 효율적이며 가비지 수집과 관련된 성능 문제를 숨기지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-125">ETW event logging is efficient and will not mask any performance problems associated with garbage collection.</span></span> <span data-ttu-id="2b5fd-126">프로세스에서 ETW 이벤트와 함께 고유한 이벤트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-126">A process can provide its own events in conjunction with ETW events.</span></span> <span data-ttu-id="2b5fd-127">기록된 경우 애플리케이션 이벤트와 가비지 수집 이벤트를 서로 연결하여 힙 문제가 발생하는 방법 및 시기를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-127">When logged, both the application's events and the garbage collection events can be correlated to determine how and when heap problems occur.</span></span> <span data-ttu-id="2b5fd-128">예를 들어 서버 애플리케이션은 클라이언트 요청이 시작되고 끝날 때 이벤트를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-128">For example, a server application could provide events at the start and end of a client request.</span></span>

### <a name="the-profiling-api"></a><span data-ttu-id="2b5fd-129">프로파일링 API</span><span class="sxs-lookup"><span data-stu-id="2b5fd-129">The Profiling API</span></span>

<span data-ttu-id="2b5fd-130">CLR(공용 언어 런타임) 프로파일링 인터페이스는 가비지 수집 중에 영향을 받은 개체에 대한 자세한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-130">The common language runtime (CLR) profiling interfaces provide detailed information about the objects that were affected during garbage collection.</span></span> <span data-ttu-id="2b5fd-131">가비지 수집이 시작되고 끝날 때 프로파일러에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-131">A profiler can be notified when a garbage collection starts and ends.</span></span> <span data-ttu-id="2b5fd-132">각 세대의 개체 ID를 포함하여 관리되는 힙의 개체에 대한 보고서를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-132">It can provide reports about the objects on the managed heap, including an identification of objects in each generation.</span></span> <span data-ttu-id="2b5fd-133">자세한 내용은 [프로파일링 개요](../../framework/unmanaged-api/profiling/profiling-overview.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-133">For more information, see [Profiling Overview](../../framework/unmanaged-api/profiling/profiling-overview.md).</span></span>

<span data-ttu-id="2b5fd-134">프로파일러는 포괄적인 정보를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-134">Profilers can provide comprehensive information.</span></span> <span data-ttu-id="2b5fd-135">그러나 복잡한 프로파일러는 애플리케이션의 동작을 수정할 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-135">However, complex profilers can potentially modify an application's behavior.</span></span>

### <a name="application-domain-resource-monitoring"></a><span data-ttu-id="2b5fd-136">애플리케이션 도메인 리소스 모니터링</span><span class="sxs-lookup"><span data-stu-id="2b5fd-136">Application Domain Resource Monitoring</span></span>

<span data-ttu-id="2b5fd-137">.NET Framework 4부터 ARM(애플리케이션 도메인 리소스 모니터링)을 통해 호스트가 애플리케이션 도메인별로 CPU 및 메모리 사용량을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-137">Starting with .NET Framework 4, Application domain resource monitoring (ARM) enables hosts to monitor CPU and memory usage by application domain.</span></span> <span data-ttu-id="2b5fd-138">자세한 내용은 [애플리케이션 도메인 리소스 모니터링](app-domain-resource-monitoring.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-138">For more information, see [Application Domain Resource Monitoring](app-domain-resource-monitoring.md).</span></span>

## <a name="troubleshooting-performance-issues"></a><span data-ttu-id="2b5fd-139">성능 문제 해결</span><span class="sxs-lookup"><span data-stu-id="2b5fd-139">Troubleshooting Performance Issues</span></span>

<span data-ttu-id="2b5fd-140">첫 번째 단계에서는 [문제가 실제로 가비지 컬렉션인지 여부를 확인](#IsGC)합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-140">The first step is to [determine whether the issue is actually garbage collection](#IsGC).</span></span> <span data-ttu-id="2b5fd-141">확인되었으면 다음 목록에서 선택하여 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-141">If you determine that it is, select from the following list to troubleshoot the problem.</span></span>

- [<span data-ttu-id="2b5fd-142">메모리 부족 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-142">An out-of-memory exception is thrown</span></span>](#Issue_OOM)

- [<span data-ttu-id="2b5fd-143">프로세스에서 메모리를 너무 많이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-143">The process uses too much memory</span></span>](#Issue_TooMuchMemory)

- [<span data-ttu-id="2b5fd-144">가비지 수집기가 개체를 충분히 빠르게 회수하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-144">The garbage collector does not reclaim objects fast enough</span></span>](#Issue_NotFastEnough)

- [<span data-ttu-id="2b5fd-145">관리되는 힙이 너무 조각화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-145">The managed heap is too fragmented</span></span>](#Issue_Fragmentation)

- [<span data-ttu-id="2b5fd-146">가비지 컬렉션 일시 중지가 너무 깁니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-146">Garbage collection pauses are too long</span></span>](#Issue_LongPauses)

- [<span data-ttu-id="2b5fd-147">0세대가 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-147">Generation 0 is too big</span></span>](#Issue_Gen0)

- [<span data-ttu-id="2b5fd-148">가비지 컬렉션 중 CPU 사용량이 너무 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-148">CPU usage during a garbage collection is too high</span></span>](#Issue_HighCPU)

<a name="Issue_OOM"></a>

### <a name="issue-an-out-of-memory-exception-is-thrown"></a><span data-ttu-id="2b5fd-149">문제: 메모리 부족 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-149">Issue: An Out-of-Memory Exception Is Thrown</span></span>

<span data-ttu-id="2b5fd-150">관리되는 <xref:System.OutOfMemoryException>이 발생하는 다음 두 가지 정당한 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-150">There are two legitimate cases for a managed <xref:System.OutOfMemoryException> to be thrown:</span></span>

- <span data-ttu-id="2b5fd-151">가상 메모리 부족.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-151">Running out of virtual memory.</span></span>

  <span data-ttu-id="2b5fd-152">가비지 수집기는 미리 결정된 크기의 세그먼트로 시스템의 메모리를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-152">The garbage collector allocates memory from the system in segments of a pre-determined size.</span></span> <span data-ttu-id="2b5fd-153">할당에 추가 세그먼트가 필요하지만 프로세스의 가상 메모리 공간에 연속된 여유 블록이 남지 않은 경우 관리되는 힙에 대한 할당이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-153">If an allocation requires an additional segment, but there is no contiguous free block left in the process's virtual memory space, the allocation for the managed heap will fail.</span></span>

- <span data-ttu-id="2b5fd-154">할당할 실제 메모리 부족</span><span class="sxs-lookup"><span data-stu-id="2b5fd-154">Not having enough physical memory to allocate.</span></span>

|<span data-ttu-id="2b5fd-155">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-155">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-156">메모리 부족 예외가 관리되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-156">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)<br /><br /> [<span data-ttu-id="2b5fd-157">예약할 수 있는 가상 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-157">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="2b5fd-158">실제 메모리가 충분한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-158">Determine whether there is enough physical memory.</span></span>](#Physical)|

<span data-ttu-id="2b5fd-159">예외가 정당하지 않다고 확인되면 다음 정보와 함께 Microsoft 고객 지원 담당자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-159">If you determine that the exception is not legitimate, contact Microsoft Customer Service and Support with the following information:</span></span>

- <span data-ttu-id="2b5fd-160">관리되는 메모리 부족 예외가 발생한 스택</span><span class="sxs-lookup"><span data-stu-id="2b5fd-160">The stack with the managed out-of-memory exception.</span></span>

- <span data-ttu-id="2b5fd-161">전체 메모리 덤프</span><span class="sxs-lookup"><span data-stu-id="2b5fd-161">Full memory dump.</span></span>

- <span data-ttu-id="2b5fd-162">가상 메모리 또는 실제 메모리가 문제가 아님을 보여 주는 데이터를 포함하여 정당한 메모리 부족 예외가 아님을 입증하는 데이터</span><span class="sxs-lookup"><span data-stu-id="2b5fd-162">Data that proves that it is not a legitimate out-of-memory exception, including data that shows that virtual or physical memory is not an issue.</span></span>

<a name="Issue_TooMuchMemory"></a>

### <a name="issue-the-process-uses-too-much-memory"></a><span data-ttu-id="2b5fd-163">문제: 프로세스에서 메모리를 너무 많이 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-163">Issue: The Process Uses Too Much Memory</span></span>

<span data-ttu-id="2b5fd-164">일반적인 가정은 Windows 작업 관리자 **성능** 탭의 메모리 사용량 표시에서 메모리가 너무 많이 사용되는 경우를 나타낼 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-164">A common assumption is that the memory usage display on the **Performance** tab of Windows Task Manager can indicate when too much memory is being used.</span></span> <span data-ttu-id="2b5fd-165">그러나 해당 표시는 작업 집합과 관련이 있고 가상 메모리 사용량에 대한 정보는 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-165">However, that display pertains to the working set; it does not provide information about virtual memory usage.</span></span>

<span data-ttu-id="2b5fd-166">문제가 관리되는 힙에서 발생한 것이면 시간별로 관리되는 힙을 측정하여 패턴을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-166">If you determine that the issue is caused by the managed heap, you must measure the managed heap over time to determine any patterns.</span></span>

<span data-ttu-id="2b5fd-167">문제가 관리되는 힙에서 발생한 것이 아니면 네이티브 디버깅을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-167">If you determine that the problem is not caused by the managed heap, you must use native debugging.</span></span>

|<span data-ttu-id="2b5fd-168">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-168">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-169">예약할 수 있는 가상 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-169">Determine how much virtual memory can be reserved.</span></span>](#GetVM)<br /><br /> [<span data-ttu-id="2b5fd-170">관리되는 힙이 커밋 중인 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-170">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)<br /><br /> [<span data-ttu-id="2b5fd-171">관리되는 힙이 예약하는 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-171">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)<br /><br /> [<span data-ttu-id="2b5fd-172">2세대의 대형 개체를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-172">Determine large objects in generation 2.</span></span>](#ExamineGen2)<br /><br /> [<span data-ttu-id="2b5fd-173">개체에 대한 참조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-173">Determine references to objects.</span></span>](#ObjRef)|

<a name="Issue_NotFastEnough"></a>

### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a><span data-ttu-id="2b5fd-174">문제: 가비지 수집기가 개체를 충분히 빠르게 회수하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-174">Issue: The Garbage Collector Does Not Reclaim Objects Fast Enough</span></span>

<span data-ttu-id="2b5fd-175">개체가 가비지 수집에 예상되는 대로 회수되지 않는 것처럼 보이면 해당 개체에 대한 강력한 참조가 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-175">When it appears as if objects are not being reclaimed as expected for garbage collection, you must determine if there are any strong references to those objects.</span></span>

<span data-ttu-id="2b5fd-176">비활성 개체를 포함하는 세대에 대한 가비지 수집이 없어 비활성 개체에 대한 종료자가 실행되지 않았음을 나타내는 경우 이 문제가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-176">You may also encounter this issue if there has been no garbage collection for the generation that contains a dead object, which indicates that the finalizer for the dead object has not been run.</span></span> <span data-ttu-id="2b5fd-177">예를 들어 STA(단일 스레드 아파트) 애플리케이션을 실행 중이며 종료자 큐를 서비스하는 스레드가 큐를 호출할 수 없는 경우에 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-177">For example, this is possible when you are running a single-threaded apartment (STA) application and the thread that services the finalizer queue cannot call into it.</span></span>

|<span data-ttu-id="2b5fd-178">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-178">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-179">개체에 대한 참조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-179">Check references to objects.</span></span>](#ObjRef)<br /><br /> [<span data-ttu-id="2b5fd-180">종료자가 실행되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-180">Determine whether a finalizer has been run.</span></span>](#Induce)<br /><br /> [<span data-ttu-id="2b5fd-181">종료 대기 중인 개체가 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-181">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)|

<a name="Issue_Fragmentation"></a>

### <a name="issue-the-managed-heap-is-too-fragmented"></a><span data-ttu-id="2b5fd-182">문제: 관리되는 힙이 너무 조각화되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-182">Issue: The Managed Heap Is Too fragmented</span></span>

<span data-ttu-id="2b5fd-183">조각화 수준은 세대에 할당된 총 메모리에 대한 여유 공간의 비율로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-183">The fragmentation level is calculated as the ratio of free space over the total allocated memory for the generation.</span></span> <span data-ttu-id="2b5fd-184">2세대에 적절한 조각화 수준은 20% 이하입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-184">For generation 2, an acceptable level of fragmentation is no more than 20%.</span></span> <span data-ttu-id="2b5fd-185">2세대는 매우 커질 수 있으므로 절대값보다 조각화 비율이 더 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-185">Because generation 2 can get very big, the ratio of fragmentation is more important than the absolute value.</span></span>

<span data-ttu-id="2b5fd-186">새 개체가 할당되는 세대이므로 0세대에 여유 공간이 많은 것은 문제가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-186">Having lots of free space in generation 0 is not a problem because this is the generation where new objects are allocated.</span></span>

<span data-ttu-id="2b5fd-187">조각화는 항상 대형 개체 힙이 압축되지 않아서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-187">Fragmentation always occurs in the large object heap because it is not compacted.</span></span> <span data-ttu-id="2b5fd-188">대형 개체 할당 요청을 충족하기 위해 인접한 여유 개체가 자연스럽게 단일 공간으로 축소됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-188">Free objects that are adjacent are naturally collapsed into a single space to satisfy large object allocation requests.</span></span>

<span data-ttu-id="2b5fd-189">조각화는 1세대와 2세대에서 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-189">Fragmentation can become a problem in generation 1 and generation 2.</span></span> <span data-ttu-id="2b5fd-190">가비지 수집 후에 이러한 세대에 대량의 여유 공간이 있을 경우 애플리케이션의 개체 사용을 수정해야 할 수 있으며 장기 개체의 수명을 다시 평가하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-190">If these generations have a large amount of free space after a garbage collection, an application's object usage may need modification, and you should consider re-evaluating the lifetime of long-term objects.</span></span>

<span data-ttu-id="2b5fd-191">개체를 과도하게 고정하면 조각화가 증가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-191">Excessive pinning of objects can increase fragmentation.</span></span> <span data-ttu-id="2b5fd-192">조각화가 높을 경우 너무 많은 개체가 고정된 것일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-192">If fragmentation is high, too many objects could have been pinned.</span></span>

<span data-ttu-id="2b5fd-193">가상 메모리의 조각화로 인해 가비지 수집기에서 세그먼트를 추가할 수 없는 경우 원인은 다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-193">If fragmentation of virtual memory is preventing the garbage collector from adding segments, the causes could be one of the following:</span></span>

- <span data-ttu-id="2b5fd-194">다수의 작은 어셈블리를 자주 로드 및 언로드</span><span class="sxs-lookup"><span data-stu-id="2b5fd-194">Frequent loading and unloading of many small assemblies.</span></span>

- <span data-ttu-id="2b5fd-195">비관리 코드와 상호 운용할 때 COM 개체에 대한 참조를 너무 많이 보유</span><span class="sxs-lookup"><span data-stu-id="2b5fd-195">Holding too many references to COM objects when interoperating with unmanaged code.</span></span>

- <span data-ttu-id="2b5fd-196">대형 임시 개체를 만들어 대형 개체 힙이 힙 세그먼트를 자주 할당 및 해제</span><span class="sxs-lookup"><span data-stu-id="2b5fd-196">Creation of large transient objects, which causes the large object heap to allocate and free heap segments frequently.</span></span>

  <span data-ttu-id="2b5fd-197">CLR을 호스트하는 경우 애플리케이션에서 가비지 수집기가 해당 세그먼트를 유지하도록 요청할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-197">When hosting the CLR, an application can request that the garbage collector retain its segments.</span></span> <span data-ttu-id="2b5fd-198">이 경우 세그먼트 할당 빈도가 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-198">This reduces the frequency of segment allocations.</span></span> <span data-ttu-id="2b5fd-199">이 작업을 수행하려면 [STARTUP_FLAGS 열거형](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md)의 STARTUP_HOARD_GC_VM 플래그를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-199">This is accomplished by using the STARTUP_HOARD_GC_VM flag in the [STARTUP_FLAGS Enumeration](../../framework/unmanaged-api/hosting/startup-flags-enumeration.md).</span></span>

|<span data-ttu-id="2b5fd-200">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-200">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-201">관리되는 힙의 여유 공간 크기를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-201">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)<br /><br /> [<span data-ttu-id="2b5fd-202">고정된 개체 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-202">Determine the number of pinned objects.</span></span>](#Pinned)|

<span data-ttu-id="2b5fd-203">조각화에 대한 정당한 원인이 없다고 생각하는 경우 Microsoft 고객 지원 담당자에게 문의하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-203">If you think that there is no legitimate cause for the fragmentation, contact Microsoft Customer Service and Support.</span></span>

<a name="Issue_LongPauses"></a>

### <a name="issue-garbage-collection-pauses-are-too-long"></a><span data-ttu-id="2b5fd-204">문제: 가비지 수집 일시 중지가 너무 깁니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-204">Issue: Garbage Collection Pauses Are Too Long</span></span>

<span data-ttu-id="2b5fd-205">가비지 수집은 소프트 실시간으로 작동하므로 애플리케이션에서 약간의 일시 중지를 허용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-205">Garbage collection operates in soft real time, so an application must be able to tolerate some pauses.</span></span> <span data-ttu-id="2b5fd-206">소프트 실시간의 기준은 작업의 95%가 시간 내에 완료되어야 한다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-206">A criterion for soft real time is that 95% of the operations must finish on time.</span></span>

<span data-ttu-id="2b5fd-207">동시 가비지 수집에서는 수집 중에 관리되는 스레드를 실행할 수 있으므로 일시 중지가 최소화됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-207">In concurrent garbage collection, managed threads are allowed to run during a collection, which means that pauses are very minimal.</span></span>

<span data-ttu-id="2b5fd-208">단기 가비지 수집(0세대 및 1세대)은 몇 밀리초 동안만 지속되므로 일시 중지를 줄이는 것이 일반적으로 불가능합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-208">Ephemeral garbage collections (generations 0 and 1) last only a few milliseconds, so decreasing pauses is usually not feasible.</span></span> <span data-ttu-id="2b5fd-209">그러나 애플리케이션에 의한 할당 요청 패턴을 변경하면 2세대 컬렉션의 일시 중지를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-209">However, you can decrease the pauses in generation 2 collections by changing the pattern of allocation requests by an application.</span></span>

<span data-ttu-id="2b5fd-210">보다 정확한 다른 방법은 [가비지 컬렉션 ETW 이벤트](../../framework/performance/garbage-collection-etw-events.md)를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-210">Another, more accurate, method is to use [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md).</span></span> <span data-ttu-id="2b5fd-211">이벤트 시퀀스에 대한 타임스탬프 차이를 추가하여 컬렉션 타이밍을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-211">You can find the timings for collections by adding the time stamp differences for a sequence of events.</span></span> <span data-ttu-id="2b5fd-212">전체 컬렉션 시퀀스에는 실행 엔진 일시 중단, 가비지 컬렉션 자체 및 실행 엔진 다시 시작이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-212">The whole collection sequence includes suspension of the execution engine, the garbage collection itself, and the resumption of the execution engine.</span></span>

<span data-ttu-id="2b5fd-213">[가비지 컬렉션 알림](notifications.md)을 사용하여 서버가 2세대 컬렉션을 수행할지 여부 및 요청을 다른 서버로 다시 라우팅할 경우 일시 중지 문제를 줄일 수 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-213">You can use [Garbage Collection Notifications](notifications.md) to determine whether a server is about to have a generation 2 collection, and whether rerouting requests to another server could ease any problems with pauses.</span></span>

|<span data-ttu-id="2b5fd-214">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-214">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-215">가비지 컬렉션 기간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-215">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)<br /><br /> [<span data-ttu-id="2b5fd-216">가비지 컬렉션이 발생한 이유를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-216">Determine what caused a garbage collection.</span></span>](#Triggered)|

<a name="Issue_Gen0"></a>

### <a name="issue-generation-0-is-too-big"></a><span data-ttu-id="2b5fd-217">문제: 0세대가 너무 큽니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-217">Issue: Generation 0 Is Too Big</span></span>

<span data-ttu-id="2b5fd-218">0세대는 워크스테이션 가비지 수집 대신 서버 가비지 수집을 사용하는 경우 특히 64비트 시스템에서 다수의 개체를 포함할 가능성이 큽니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-218">Generation 0 is likely to have a larger number of objects on a 64-bit system, especially when you use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="2b5fd-219">이러한 환경에서는 0세대 가비지 수집을 트리거하는 임계값이 더 높으며 0세대 수집이 훨씬 더 커질 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-219">This is because the threshold to trigger a generation 0 garbage collection is higher in these environments, and generation 0 collections can get much bigger.</span></span> <span data-ttu-id="2b5fd-220">가비지 수집이 트리거되기 전에 애플리케이션이 더 많은 메모리를 할당하면 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-220">Performance is improved when an application allocates more memory before a garbage collection is triggered.</span></span>

<a name="Issue_HighCPU"></a>

### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a><span data-ttu-id="2b5fd-221">문제: 가비지 수집 중 CPU 사용량이 너무 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-221">Issue: CPU Usage During a Garbage Collection Is Too High</span></span>

<span data-ttu-id="2b5fd-222">가비지 수집 중 CPU 사용량이 너무 많습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-222">CPU usage will be high during a garbage collection.</span></span> <span data-ttu-id="2b5fd-223">상당한 양의 처리 시간이 가비지 수집에 소요되는 경우 수집 횟수가 너무 빈번하거나 수집이 너무 오래 지속되는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-223">If a significant amount of process time is spent in a garbage collection, the number of collections is too frequent or the collection is lasting too long.</span></span> <span data-ttu-id="2b5fd-224">관리되는 힙에서 개체의 할당 비율이 증가하면 가비지 수집이 더 자주 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-224">An increased allocation rate of objects on the managed heap causes garbage collection to occur more frequently.</span></span> <span data-ttu-id="2b5fd-225">할당 비율을 낮추면 가비지 수집 빈도가 감소합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-225">Decreasing the allocation rate reduces the frequency of garbage collections.</span></span>

<span data-ttu-id="2b5fd-226">`Allocated Bytes/second` 성능 카운터를 사용하여 할당 비율을 모니터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-226">You can monitor allocation rates by using the `Allocated Bytes/second` performance counter.</span></span> <span data-ttu-id="2b5fd-227">자세한 내용은 [.NET의 성능 카운터](../../framework/debug-trace-profile/performance-counters.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-227">For more information, see [Performance Counters in .NET](../../framework/debug-trace-profile/performance-counters.md).</span></span>

<span data-ttu-id="2b5fd-228">컬렉션 기간은 주로 할당 후 남아 있는 개체 수의 비율입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-228">The duration of a collection is primarily a factor of the number of objects that survive after allocation.</span></span> <span data-ttu-id="2b5fd-229">수집할 많은 개체가 남아 있으면 가비지 수집기가 많은 양의 메모리를 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-229">The garbage collector must go through a large amount of memory if many objects remain to be collected.</span></span> <span data-ttu-id="2b5fd-230">남은 개체를 압축하는 작업은 오랜 시간이 소요됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-230">The work to compact the survivors is time-consuming.</span></span> <span data-ttu-id="2b5fd-231">수집 중 처리된 개체 수를 확인하려면 디버거에서 지정된 세대에 대한 가비지 수집의 끝에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-231">To determine how many objects were handled during a collection, set a breakpoint in the debugger at the end of a garbage collection for a specified generation.</span></span>

|<span data-ttu-id="2b5fd-232">성능 검사</span><span class="sxs-lookup"><span data-stu-id="2b5fd-232">Performance checks</span></span>|
|------------------------|
|[<span data-ttu-id="2b5fd-233">높은 CPU 사용량이 가비지 컬렉션에 의해 발생한 것인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-233">Determine if high CPU usage is caused by garbage collection.</span></span>](#HighCPU)<br /><br /> [<span data-ttu-id="2b5fd-234">가비지 컬렉션의 끝에 중단점을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-234">Set a breakpoint at the end of garbage collection.</span></span>](#GenBreak)|

## <a name="troubleshooting-guidelines"></a><span data-ttu-id="2b5fd-235">문제 해결 지침</span><span class="sxs-lookup"><span data-stu-id="2b5fd-235">Troubleshooting Guidelines</span></span>

<span data-ttu-id="2b5fd-236">이 섹션에서는 조사를 시작할 때 고려해야 할 지침을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-236">This section describes guidelines that you should consider as you begin your investigations.</span></span>

### <a name="workstation-or-server-garbage-collection"></a><span data-ttu-id="2b5fd-237">워크스테이션 또는 서버 가비지 수집</span><span class="sxs-lookup"><span data-stu-id="2b5fd-237">Workstation or Server Garbage Collection</span></span>

<span data-ttu-id="2b5fd-238">올바른 유형의 가비지 수집을 사용 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-238">Determine if you are using the correct type of garbage collection.</span></span> <span data-ttu-id="2b5fd-239">애플리케이션에서 여러 스레드 및 개체 인스턴스를 사용하는 경우 워크스테이션 가비지 수집 대신 서버 가비지 수집을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-239">If your application uses multiple threads and object instances, use server garbage collection instead of workstation garbage collection.</span></span> <span data-ttu-id="2b5fd-240">서버 가비지 수집은 여러 스레드에서 작동하는 반면, 워크스테이션 가비지 수집에서는 애플리케이션의 여러 인스턴스가 고유한 가비지 수집 스레드를 실행하고 CPU 시간을 경합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-240">Server garbage collection operates on multiple threads, whereas workstation garbage collection requires multiple instances of an application to run their own garbage collection threads and compete for CPU time.</span></span>

<span data-ttu-id="2b5fd-241">부하가 낮고 백그라운드에서 자주 작업을 수행하지 않는 서비스와 같은 애플리케이션은 동시 가비지 수집을 사용하지 않도록 설정하여 워크스테이션 가비지 수집을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-241">An application that has a low load and that performs tasks infrequently in the background, such as a service, could use workstation garbage collection with concurrent garbage collection disabled.</span></span>

### <a name="when-to-measure-the-managed-heap-size"></a><span data-ttu-id="2b5fd-242">관리되는 힙 크기를 측정하는 시기</span><span class="sxs-lookup"><span data-stu-id="2b5fd-242">When to Measure the Managed Heap Size</span></span>

<span data-ttu-id="2b5fd-243">프로파일러를 사용하지 않는 한 효과적으로 성능 문제를 진단하려면 일관된 측정 패턴을 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-243">Unless you are using a profiler, you will have to establish a consistent measuring pattern to effectively diagnose performance issues.</span></span> <span data-ttu-id="2b5fd-244">일정을 설정하려면 다음 사항을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-244">Consider the following points to establish a schedule:</span></span>

- <span data-ttu-id="2b5fd-245">2세대 가비지 수집 후에 측정하는 경우 전체 관리되는 힙의 가비지(비활성 개체)가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-245">If you measure after a generation 2 garbage collection, the entire managed heap will be free of garbage (dead objects).</span></span>

- <span data-ttu-id="2b5fd-246">0세대 가비지 수집 직후에 측정하는 경우 1세대 및 2세대의 개체는 아직 수집되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-246">If you measure immediately after a generation 0 garbage collection, the objects in generations 1 and 2 will not be collected yet.</span></span>

- <span data-ttu-id="2b5fd-247">가비지 수집 직전에 측정하는 경우 가비지 수집이 시작되기 전에 가능한 한 많은 할당을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-247">If you measure immediately before a garbage collection, you will measure as much allocation as possible before the garbage collection starts.</span></span>

- <span data-ttu-id="2b5fd-248">가비지 수집기 데이터 구조는 순회에 유효한 상태가 아니며 완전한 결과를 제공할 수 없으므로 가비지 수집 중에 측정하는 것은 문제가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-248">Measuring during a garbage collection is problematic, because the garbage collector data structures are not in a valid state for traversal and may not be able to give you the complete results.</span></span> <span data-ttu-id="2b5fd-249">이것은 의도적인 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-249">This is by design.</span></span>

- <span data-ttu-id="2b5fd-250">동시 가비지 수집과 함께 워크스테이션 가비지 수집을 사용하는 경우 회수된 개체가 압축되지 않으므로 힙 크기가 동일하거나 더 클 수 있습니다(조각화로 인해 더 크게 보일 수 있음).</span><span class="sxs-lookup"><span data-stu-id="2b5fd-250">When you are using workstation garbage collection with concurrent garbage collection, the reclaimed objects are not compacted, so the heap size can be the same or larger (fragmentation can make it appear to be larger).</span></span>

- <span data-ttu-id="2b5fd-251">실제 메모리 부하가 너무 높으면 2세대의 동시 가비지 수집이 지연됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-251">Concurrent garbage collection on generation 2 is delayed when the physical memory load is too high.</span></span>

<span data-ttu-id="2b5fd-252">다음 절차에서는 관리되는 힙을 측정할 수 있도록 중단점을 설정하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-252">The following procedure describes how to set a breakpoint so that you can measure the managed heap.</span></span>

<a name="GenBreak"></a>

#### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a><span data-ttu-id="2b5fd-253">가비지 수집의 끝에 중단점을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-253">To set a breakpoint at the end of garbage collection</span></span>

- <span data-ttu-id="2b5fd-254">SOS 디버거 확장이 로드된 WinDbg에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-254">In WinDbg with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="2b5fd-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-255">**bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**</span></span>

  <span data-ttu-id="2b5fd-256">여기서 **GcCondemnedGeneration** 은 원하는 세대로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-256">where **GcCondemnedGeneration** is set to the desired generation.</span></span> <span data-ttu-id="2b5fd-257">이 명령에는 전용 기호가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-257">This command requires private symbols.</span></span>

  <span data-ttu-id="2b5fd-258">이 명령은 가비지 컬렉션을 위해 2세대 개체가 회수된 후 **RestartEE** 가 실행되는 경우 강제로 중단합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-258">This command forces a break if **RestartEE** is executed after generation 2 objects have been reclaimed for garbage collection.</span></span>

  <span data-ttu-id="2b5fd-259">서버 가비지 컬렉션에서는 하나의 스레드만 **RestartEE** 를 호출하므로 2세대 가비지 컬렉션 중 한 번만 중단점이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-259">In server garbage collection, only one thread calls **RestartEE**, so the breakpoint will occur only once during a generation 2 garbage collection.</span></span>

## <a name="performance-check-procedures"></a><span data-ttu-id="2b5fd-260">성능 검사 절차</span><span class="sxs-lookup"><span data-stu-id="2b5fd-260">Performance Check Procedures</span></span>

<span data-ttu-id="2b5fd-261">이 섹션에서는 성능 문제의 원인을 격리시키는 다음 절차를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-261">This section describes the following procedures to isolate the cause of your performance issue:</span></span>

- [<span data-ttu-id="2b5fd-262">문제가 가비지 컬렉션에 의해 발생한 것인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-262">Determine whether the problem is caused by garbage collection.</span></span>](#IsGC)

- [<span data-ttu-id="2b5fd-263">메모리 부족 예외가 관리되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-263">Determine whether the out-of-memory exception is managed.</span></span>](#OOMIsManaged)

- [<span data-ttu-id="2b5fd-264">예약할 수 있는 가상 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-264">Determine how much virtual memory can be reserved.</span></span>](#GetVM)

- [<span data-ttu-id="2b5fd-265">실제 메모리가 충분한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-265">Determine whether there is enough physical memory.</span></span>](#Physical)

- [<span data-ttu-id="2b5fd-266">관리되는 힙이 커밋 중인 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-266">Determine how much memory the managed heap is committing.</span></span>](#ManagedHeapCommit)

- [<span data-ttu-id="2b5fd-267">관리되는 힙이 예약하는 메모리 양을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-267">Determine how much memory the managed heap reserves.</span></span>](#ManagedHeapReserve)

- [<span data-ttu-id="2b5fd-268">2세대의 대형 개체를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-268">Determine large objects in generation 2.</span></span>](#ExamineGen2)

- [<span data-ttu-id="2b5fd-269">개체에 대한 참조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-269">Determine references to objects.</span></span>](#ObjRef)

- [<span data-ttu-id="2b5fd-270">종료자가 실행되었는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-270">Determine whether a finalizer has been run.</span></span>](#Induce)

- [<span data-ttu-id="2b5fd-271">종료 대기 중인 개체가 있는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-271">Determine whether there are objects waiting to be finalized.</span></span>](#Finalize)

- [<span data-ttu-id="2b5fd-272">관리되는 힙의 여유 공간 크기를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-272">Determine the amount of free space in the managed heap.</span></span>](#Fragmented)

- [<span data-ttu-id="2b5fd-273">고정된 개체 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-273">Determine the number of pinned objects.</span></span>](#Pinned)

- [<span data-ttu-id="2b5fd-274">가비지 컬렉션 기간을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-274">Determine the length of time in a garbage collection.</span></span>](#TimeInGC)

- [<span data-ttu-id="2b5fd-275">가비지 컬렉션 트리거를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-275">Determine what triggered a garbage collection.</span></span>](#Triggered)

- [<span data-ttu-id="2b5fd-276">높은 CPU 사용량이 가비지 컬렉션에 의해 발생한 것인지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-276">Determine whether high CPU usage is caused by garbage collection.</span></span>](#HighCPU)

<a name="IsGC"></a>

### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a><span data-ttu-id="2b5fd-277">문제가 가비지 컬렉션에 의해 발생한 것인지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-277">To determine whether the problem is caused by garbage collection</span></span>

- <span data-ttu-id="2b5fd-278">다음 두 개의 메모리 성능 카운터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-278">Examine the following two memory performance counters:</span></span>

  - <span data-ttu-id="2b5fd-279">**% Time in GC**.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-279">**% Time in GC**.</span></span> <span data-ttu-id="2b5fd-280">마지막 가비지 컬렉션 주기 이후 가비지 컬렉션을 수행하는 데 소요된 경과 시간의 백분율을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-280">Displays the percentage of elapsed time that was spent performing a garbage collection after the last garbage collection cycle.</span></span> <span data-ttu-id="2b5fd-281">이 카운터를 사용하여 가비지 수집기가 관리되는 힙 공간을 사용할 수 있도록 하는 데 너무 많은 시간을 소비하고 있는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-281">Use this counter to determine whether the garbage collector is spending too much time to make managed heap space available.</span></span> <span data-ttu-id="2b5fd-282">가비지 수집에 소요된 시간이 비교적 적은 경우 관리되는 힙 외부의 리소스 문제를 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-282">If the time spent in garbage collection is relatively low, that could indicate a resource problem outside the managed heap.</span></span> <span data-ttu-id="2b5fd-283">이 카운터는 동시 또는 백그라운드 가비지 컬렉션이 관련된 경우 정확하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-283">This counter may not be accurate when concurrent or background garbage collection is involved.</span></span>

  - <span data-ttu-id="2b5fd-284">**# Total committed Bytes**.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-284">**# Total committed Bytes**.</span></span> <span data-ttu-id="2b5fd-285">가비지 컬렉션기에서 현재 커밋한 가상 메모리 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-285">Displays the amount of virtual memory currently committed by the garbage collector.</span></span> <span data-ttu-id="2b5fd-286">이 카운터를 사용하여 가비지 수집기에서 사용되는 메모리가 애플리케이션에서 사용되는 메모리에 비해 과도하게 많은지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-286">Use this counter to determine whether the memory consumed by the garbage collector is an excessive portion of the memory that your application uses.</span></span>

  <span data-ttu-id="2b5fd-287">대부분의 메모리 성능 카운터는 각 가비지 수집이 끝날 때 업데이트됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-287">Most of the memory performance counters are updated at the end of each garbage collection.</span></span> <span data-ttu-id="2b5fd-288">따라서 정보를 확인하려는 현재 상태가 반영되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-288">Therefore, they may not reflect the current conditions that you want information about.</span></span>

<a name="OOMIsManaged"></a>

### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a><span data-ttu-id="2b5fd-289">메모리 부족 예외가 관리되는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-289">To determine whether the out-of-memory exception is managed</span></span>

1. <span data-ttu-id="2b5fd-290">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 예외 인쇄(**pe**) 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-290">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the print exception (**pe**) command:</span></span>

    <span data-ttu-id="2b5fd-291">**!pe**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-291">**!pe**</span></span>

    <span data-ttu-id="2b5fd-292">예외가 관리되는 경우 다음 예제와 같이 <xref:System.OutOfMemoryException>이 예외 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-292">If the exception is managed, <xref:System.OutOfMemoryException> is displayed as the exception type, as shown in the following example.</span></span>

    ```console
    Exception object: 39594518
    Exception type: System.OutOfMemoryException
    Message: <none>
    InnerException: <none>
    StackTrace (generated):
    ```

2. <span data-ttu-id="2b5fd-293">출력에서 예외를 지정하지 않는 경우 메모리 부족 예외가 발생한 스레드를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-293">If the output does not specify an exception, you have to determine which thread the out-of-memory exception is from.</span></span> <span data-ttu-id="2b5fd-294">디버거에서 다음 명령을 입력하여 호출 스택과 함께 모든 스레드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-294">Type the following command in the debugger to show all the threads with their call stacks:</span></span>

    <span data-ttu-id="2b5fd-295">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-295">**~\*kb**</span></span>

    <span data-ttu-id="2b5fd-296">예외 호출이 포함된 스택이 있는 스레드는 `RaiseTheException` 인수로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-296">The thread with the stack that has exception calls is indicated by the `RaiseTheException` argument.</span></span> <span data-ttu-id="2b5fd-297">이는 관리되는 예외 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-297">This is the managed exception object.</span></span>

    ```console
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0
    ```

3. <span data-ttu-id="2b5fd-298">다음 명령을 사용하여 중첩된 예외를 덤프할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-298">You can use the following command to dump nested exceptions.</span></span>

    <span data-ttu-id="2b5fd-299">**!pe -nested**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-299">**!pe -nested**</span></span>

    <span data-ttu-id="2b5fd-300">예외를 찾을 수 없는 경우 메모리 부족 예외가 비관리 코드에서 발생한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-300">If you do not find any exceptions, the out-of-memory exception originated from unmanaged code.</span></span>

<a name="GetVM"></a>

### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a><span data-ttu-id="2b5fd-301">예약할 수 있는 가상 메모리 양을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-301">To determine how much virtual memory can be reserved</span></span>

- <span data-ttu-id="2b5fd-302">SOS 디버거 확장이 로드된 WinDbg에서 다음 명령을 입력하여 최대 여유 영역을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-302">In WinDbg with the SOS debugger extension loaded, type the following command to get the largest free region:</span></span>

  <span data-ttu-id="2b5fd-303">**!address -summary**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-303">**!address -summary**</span></span>

  <span data-ttu-id="2b5fd-304">다음 출력과 같이 최대 여유 영역이 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-304">The largest free region is displayed as shown in the following output.</span></span>

  ```console
  Largest free region: Base 54000000 - Size 0003A980
  ```

  <span data-ttu-id="2b5fd-305">이 예제에서 최대 여유 영역의 크기는 약 24000KB(16진수로 3A980)입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-305">In this example, the size of the largest free region is approximately 24000 KB (3A980 in hexadecimal).</span></span> <span data-ttu-id="2b5fd-306">이 영역은 가비지 수집기에서 세그먼트에 필요한 크기보다 훨씬 작습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-306">This region is much smaller than what the garbage collector needs for a segment.</span></span>

  <span data-ttu-id="2b5fd-307">또는</span><span class="sxs-lookup"><span data-stu-id="2b5fd-307">-or-</span></span>

- <span data-ttu-id="2b5fd-308">다음 **vmstat** 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-308">Use the **vmstat** command:</span></span>

  <span data-ttu-id="2b5fd-309">**!vmstat**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-309">**!vmstat**</span></span>

  <span data-ttu-id="2b5fd-310">다음 출력과 같이 최대 여유 영역은 MAXIMUM 열에서 가장 큰 값입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-310">The largest free region is the largest value in the MAXIMUM column, as shown in the following output.</span></span>

  ```console
  TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL
  ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~
  Free:
  Small       8K        64K         46K       36          1,671K
  Medium      80K       864K        349K      3           1,047K
  Large       1,384K    1,278,848K  151,834K  12          1,822,015K
  Summary     8K        1,278,848K  35,779K   51          1,824,735K
  ```

<a name="Physical"></a>

### <a name="to-determine-whether-there-is-enough-physical-memory"></a><span data-ttu-id="2b5fd-311">실제 메모리가 충분한지 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-311">To determine whether there is enough physical memory</span></span>

1. <span data-ttu-id="2b5fd-312">Windows 작업 관리자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-312">Start Windows Task Manager.</span></span>

2. <span data-ttu-id="2b5fd-313">**성능** 탭에서 커밋된 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-313">On the **Performance** tab, look at the committed value.</span></span> <span data-ttu-id="2b5fd-314">Windows 7에서는 **시스템 그룹** 의 **커밋(KB)** 을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-314">(In Windows 7, look at **Commit (KB)** in the **System group**.)</span></span>

    <span data-ttu-id="2b5fd-315">**합계** 가 **제한** 에 가까우면 실제 메모리가 부족한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-315">If the **Total** is close to the **Limit**, you are running low on physical memory.</span></span>

<a name="ManagedHeapCommit"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a><span data-ttu-id="2b5fd-316">관리되는 힙이 커밋 중인 메모리 양을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-316">To determine how much memory the managed heap is committing</span></span>

- <span data-ttu-id="2b5fd-317">`# Total committed bytes` 메모리 성능 카운터를 사용하여 관리되는 힙에서 커밋 중인 바이트 수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-317">Use the `# Total committed bytes` memory performance counter to get the number of bytes that the managed heap is committing.</span></span> <span data-ttu-id="2b5fd-318">가비지 수집기는 동시에 모두 커밋하지 않고 필요에 따라 세그먼트의 청크를 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-318">The garbage collector commits chunks on a segment as needed, not all at the same time.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2b5fd-319">`# Bytes in all Heaps` 성능 카운터는 관리되는 힙의 실제 메모리 사용량을 나타내지 않으므로 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-319">Do not use the `# Bytes in all Heaps` performance counter, because it does not represent actual memory usage by the managed heap.</span></span> <span data-ttu-id="2b5fd-320">세대 크기가 이 값에 포함되며 실제로 해당 임계값 크기, 즉 세대가 개체로 채워진 경우 가비지 수집을 실행하는 크기입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-320">The size of a generation is included in this value and is actually its threshold size, that is, the size that induces a garbage collection if the generation is filled with objects.</span></span> <span data-ttu-id="2b5fd-321">따라서 이 값은 일반적으로 0입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-321">Therefore, this value is usually zero.</span></span>

<a name="ManagedHeapReserve"></a>

### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a><span data-ttu-id="2b5fd-322">관리되는 힙이 예약하는 메모리 양을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-322">To determine how much memory the managed heap reserves</span></span>

- <span data-ttu-id="2b5fd-323">`# Total reserved bytes` 메모리 성능 카운터를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-323">Use the `# Total reserved bytes` memory performance counter.</span></span>

  <span data-ttu-id="2b5fd-324">가비지 수집기는 세그먼트의 메모리를 예약하고, **eeheap** 명령을 사용하여 세그먼트가 시작되는 위치를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-324">The garbage collector reserves memory in segments, and you can determine where a segment starts by using the **eeheap** command.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="2b5fd-325">가비지 수집기가 각 세그먼트에 대해 할당하는 메모리 양은 확인할 수 있지만 세그먼트 크기는 구현마다 다르며 정기 업데이트를 포함하여 언제든지 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-325">Although you can determine the amount of memory the garbage collector allocates for each segment, segment size is implementation-specific and is subject to change at any time, including in periodic updates.</span></span> <span data-ttu-id="2b5fd-326">앱에서 특정 세그먼트 크기를 가정하거나 의존해서는 안 되며, 세그먼트 할당에 사용할 수 있는 메모리 크기를 구성하려고 해서도 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-326">Your app should never make assumptions about or depend on a particular segment size, nor should it attempt to configure the amount of memory available for segment allocations.</span></span>

- <span data-ttu-id="2b5fd-327">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-327">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="2b5fd-328">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-328">**!eeheap -gc**</span></span>

  <span data-ttu-id="2b5fd-329">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-329">The result is as follows.</span></span>

  ```console
  Number of GC Heaps: 2
  ------------------------------
  Heap 0 (002db550)
  generation 0 starts at 0x02abe29c
  generation 1 starts at 0x02abdd08
  generation 2 starts at 0x02ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  02ab0000 02ab0038  02aceff4 0x0001efbc(126908)
  Large object heap starts at 0x0aab0038
    segment    begin allocated     size
  0aab0000 0aab0038  0aab2278 0x00002240(8768)
  Heap Size   0x211fc(135676)
  ------------------------------
  Heap 1 (002dc958)
  generation 0 starts at 0x06ab1bd8
  generation 1 starts at 0x06ab1bcc
  generation 2 starts at 0x06ab0038
  ephemeral segment allocation context: none
    segment    begin allocated     size
  06ab0000 06ab0038  06ab3be4 0x00003bac(15276)
  Large object heap starts at 0x0cab0038
    segment    begin allocated     size
  0cab0000 0cab0038  0cab0048 0x00000010(16)
  Heap Size    0x3bbc(15292)
  ------------------------------
  GC Heap Size   0x24db8(150968)
  ```

  <span data-ttu-id="2b5fd-330">"segment"로 표시된 주소는 세그먼트의 시작 주소입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-330">The addresses indicated by "segment" are the starting addresses of the segments.</span></span>

<a name="ExamineGen2"></a>

### <a name="to-determine-large-objects-in-generation-2"></a><span data-ttu-id="2b5fd-331">2세대의 대형 개체를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-331">To determine large objects in generation 2</span></span>

- <span data-ttu-id="2b5fd-332">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-332">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="2b5fd-333">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-333">**!dumpheap –stat**</span></span>

  <span data-ttu-id="2b5fd-334">관리되는 힙이 크면 **dumpheap** 을 완료하는 데 오랜 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-334">If the managed heap is big, **dumpheap** may take a while to finish.</span></span>

  <span data-ttu-id="2b5fd-335">가장 많은 공간을 사용하는 개체를 나열하는 출력의 마지막 몇 줄에서 분석을 시작하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-335">You can start analyzing from the last few lines of the output, because they list the objects that use the most space.</span></span> <span data-ttu-id="2b5fd-336">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="2b5fd-336">For example:</span></span>

  ```console
  2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo
  00155f80      533     15216804      Free
  7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary
  2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo
  79124228   121143     29064120 System.Object[]
  035f0ee4    81626     35588936 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    40182     90664128 System.Collections.Hashtable+bucket[]
  790fa3e0  3154024    137881448 System.String
  Total 8454945 objects
  ```

  <span data-ttu-id="2b5fd-337">마지막에 나열된 개체는 문자열이며 가장 많은 공간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-337">The last object listed is a string and occupies the most space.</span></span> <span data-ttu-id="2b5fd-338">애플리케이션을 검사하여 문자열 개체를 최적화할 수 있는 방법을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-338">You can examine your application to see how your string objects can be optimized.</span></span> <span data-ttu-id="2b5fd-339">150바이트에서 200바이트 사이의 문자열을 확인하려면 다음을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-339">To see strings that are between 150 and 200 bytes, type the following:</span></span>

  <span data-ttu-id="2b5fd-340">**!dumpheap -type System.String -min 150 -max 200**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-340">**!dumpheap -type System.String -min 150 -max 200**</span></span>

  <span data-ttu-id="2b5fd-341">결과의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-341">An example of the results is as follows.</span></span>

  ```console
  Address  MT           Size  Gen
  1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11
  …
  ```

  <span data-ttu-id="2b5fd-342">ID 문자열 대신 정수를 사용하면 더 효율적일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-342">Using an integer instead of a string for an ID can be more efficient.</span></span> <span data-ttu-id="2b5fd-343">같은 문자열이 수천 번 반복되는 경우 문자열 인터닝을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-343">If the same string is being repeated thousands of times, consider string interning.</span></span> <span data-ttu-id="2b5fd-344">문자열 인터닝에 대한 자세한 내용은 <xref:System.String.Intern%2A?displayProperty=nameWithType> 메서드에 대한 참조 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-344">For more information about string interning, see the reference topic for the <xref:System.String.Intern%2A?displayProperty=nameWithType> method.</span></span>

<a name="ObjRef"></a>

### <a name="to-determine-references-to-objects"></a><span data-ttu-id="2b5fd-345">개체에 대한 참조를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-345">To determine references to objects</span></span>

- <span data-ttu-id="2b5fd-346">SOS 디버거 확장이 로드된 WinDbg에서 다음 명령을 입력하여 개체에 대한 참조를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-346">In WinDbg with the SOS debugger extension loaded, type the following command to list references to objects:</span></span>

  <span data-ttu-id="2b5fd-347">**!gcroot**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-347">**!gcroot**</span></span>

  `-or-`

- <span data-ttu-id="2b5fd-348">특정 개체에 대한 참조를 확인하려면 다음과 같이 주소를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-348">To determine the references for a specific object, include the address:</span></span>

  <span data-ttu-id="2b5fd-349">**!gcroot 1c37b2ac**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-349">**!gcroot 1c37b2ac**</span></span>

  <span data-ttu-id="2b5fd-350">스택에서 발견된 루트는 가양성(false positive)일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-350">Roots found on stacks may be false positives.</span></span> <span data-ttu-id="2b5fd-351">자세한 내용을 보려면 `!help gcroot` 명령을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-351">For more information, use the command `!help gcroot`.</span></span>

  ```console
  ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->
  19010b78(DemoApp.FormDemoApp)->
  19011158(System.Windows.Forms.PropertyStore)->
  … [omitted]
  1c3745ec(System.Data.DataTable)->
  1c3747a8(System.Data.DataColumnCollection)->
  1c3747f8(System.Collections.Hashtable)->
  1c376590(System.Collections.Hashtable+bucket[])->
  1c376c98(System.Data.DataColumn)->
  1c37b270(System.Data.Common.DoubleStorage)->
  1c37b2ac(System.Double[])
  Scan Thread 0 OSTHread 99c
  Scan Thread 6 OSTHread 484
  ```

  <span data-ttu-id="2b5fd-352">**gcroot** 명령을 완료하는 데 오랜 시간이 걸릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-352">The **gcroot** command can take a long time to finish.</span></span> <span data-ttu-id="2b5fd-353">가비지 컬렉션에 의해 회수되지 않은 개체는 모두 라이브 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-353">Any object that is not reclaimed by garbage collection is a live object.</span></span> <span data-ttu-id="2b5fd-354">이는 일부 루트가 직접 또는 간접적으로 개체에 연결되어 있으므로 **gcroot** 에서 개체의 경로 정보가 반환되어야 함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-354">This means that some root is directly or indirectly holding onto the object, so **gcroot** should return path information to the object.</span></span> <span data-ttu-id="2b5fd-355">반환된 그래프를 검사하고 이러한 개체가 여전히 참조되는 이유를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-355">You should examine the graphs returned and see why these objects are still referenced.</span></span>

<a name="Induce"></a>

### <a name="to-determine-whether-a-finalizer-has-been-run"></a><span data-ttu-id="2b5fd-356">종료자가 실행되었는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-356">To determine whether a finalizer has been run</span></span>

- <span data-ttu-id="2b5fd-357">다음 코드가 포함된 테스트 프로그램을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-357">Run a test program that contains the following code:</span></span>

  ```csharp
  GC.Collect();
  GC.WaitForPendingFinalizers();
  GC.Collect();
  ```

  <span data-ttu-id="2b5fd-358">테스트에서 문제가 해결되는 경우 이는 해당 개체에 대한 종료자가 일시 중단되어 가비지 수집기가 개체를 회수하지 못했음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-358">If the test resolves the problem, this means that the garbage collector was not reclaiming objects, because the finalizers for those objects had been suspended.</span></span> <span data-ttu-id="2b5fd-359"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> 메서드는 종료자가 해당 작업을 완료할 수 있도록 하며 문제를 해결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-359">The <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method enables the finalizers to complete their tasks, and fixes the problem.</span></span>

<a name="Finalize"></a>

### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a><span data-ttu-id="2b5fd-360">종료 대기 중인 개체가 있는지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-360">To determine whether there are objects waiting to be finalized</span></span>

1. <span data-ttu-id="2b5fd-361">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-361">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

    <span data-ttu-id="2b5fd-362">**!finalizequeue**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-362">**!finalizequeue**</span></span>

    <span data-ttu-id="2b5fd-363">종료 준비가 된 개체 수를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-363">Look at the number of objects that are ready for finalization.</span></span> <span data-ttu-id="2b5fd-364">개수가 많을 경우 이러한 종료자가 전혀 처리할 수 없거나 충분히 빨리 처리할 수 없는 이유를 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-364">If the number is high, you must examine why these finalizers cannot progress at all or cannot progress fast enough.</span></span>

2. <span data-ttu-id="2b5fd-365">스레드의 출력을 가져오려면 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-365">To get an output of threads, type the following command:</span></span>

    <span data-ttu-id="2b5fd-366">**threads -special**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-366">**threads -special**</span></span>

    <span data-ttu-id="2b5fd-367">이 명령은 다음과 같은 출력을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-367">This command provides output such as the following.</span></span>

    ```console
       OSID     Special thread type
    2    cd0    DbgHelper
    3    c18    Finalizer
    4    df0    GC SuspendEE
    ```

    <span data-ttu-id="2b5fd-368">종료자 스레드는 현재 실행 중인 종료자(있는 경우)를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-368">The finalizer thread indicates which finalizer, if any, is currently being run.</span></span> <span data-ttu-id="2b5fd-369">종료자 스레드가 종료자를 실행하지 않는 경우 해당 작업을 수행하도록 지시할 이벤트를 기다리고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-369">When a finalizer thread is not running any finalizers, it is waiting for an event to tell it to do its work.</span></span> <span data-ttu-id="2b5fd-370">종료자 스레드는 THREAD_HIGHEST_PRIORITY에서 실행되고 종료자(있는 경우) 실행을 매우 빠르게 완료하기 때문에 대부분의 경우 이 상태의 종료자 스레드가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-370">Most of the time you will see the finalizer thread in this state because it runs at THREAD_HIGHEST_PRIORITY and is supposed to finish running finalizers, if any, very quickly.</span></span>

<a name="Fragmented"></a>

### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a><span data-ttu-id="2b5fd-371">관리되는 힙의 여유 공간 크기를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-371">To determine the amount of free space in the managed heap</span></span>

- <span data-ttu-id="2b5fd-372">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-372">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="2b5fd-373">**!dumpheap -type Free -stat**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-373">**!dumpheap -type Free -stat**</span></span>

  <span data-ttu-id="2b5fd-374">이 명령은 다음 예제와 같이 관리되는 힙에서 사용 가능한 모든 개체의 전체 크기를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-374">This command displays the total size of all the free objects on the managed heap, as shown in the following example.</span></span>

  ```console
  total 230 objects
  Statistics:
        MT    Count    TotalSize Class Name
  00152b18      230     40958584      Free
  Total 230 objects
  ```

- <span data-ttu-id="2b5fd-375">0세대의 여유 공간을 확인하려면 세대별 메모리 소비 정보를 위해 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-375">To determine the free space in generation 0, type the following command for memory consumption information by generation:</span></span>

  <span data-ttu-id="2b5fd-376">**!eeheap -gc**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-376">**!eeheap -gc**</span></span>

  <span data-ttu-id="2b5fd-377">이 명령은 다음과 유사한 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-377">This command displays output similar to the following.</span></span> <span data-ttu-id="2b5fd-378">마지막 줄은 단기 세그먼트를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-378">The last line shows the ephemeral segment.</span></span>

  ```console
  Heap 0 (0015ad08)
  generation 0 starts at 0x49521f8c
  generation 1 starts at 0x494d7f64
  generation 2 starts at 0x007f0038
  ephemeral segment allocation context: none
  segment  begin     allocated  size
  00178250 7a80d84c  7a82f1cc   0x00021980(137600)
  00161918 78c50e40  78c7056c   0x0001f72c(128812)
  007f0000 007f0038  047eed28   0x03ffecf0(67103984)
  3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)
  46120000 46120038  49e05d04   0x03ce5ccc(63855820)
  ```

- <span data-ttu-id="2b5fd-379">0세대에서 사용되는 공간을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-379">Calculate the space used by generation 0:</span></span>

  <span data-ttu-id="2b5fd-380">**? 49e05d04-0x49521f8c**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-380">**? 49e05d04-0x49521f8c**</span></span>

  <span data-ttu-id="2b5fd-381">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-381">The result is as follows.</span></span> <span data-ttu-id="2b5fd-382">0세대는 약 9MB입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-382">Generation 0 is approximately 9 MB.</span></span>

  ```console
  Evaluate expression: 9321848 = 008e3d78
  ```

- <span data-ttu-id="2b5fd-383">다음 명령은 0세대 범위 내의 여유 공간을 덤프합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-383">The following command dumps the free space within the generation 0 range:</span></span>

  <span data-ttu-id="2b5fd-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-384">**!dumpheap -type Free -stat 0x49521f8c 49e05d04**</span></span>

  <span data-ttu-id="2b5fd-385">결과는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-385">The result is as follows.</span></span>

  ```console
  ------------------------------
  Heap 0
  total 409 objects
  ------------------------------
  Heap 1
  total 0 objects
  ------------------------------
  Heap 2
  total 0 objects
  ------------------------------
  Heap 3
  total 0 objects
  ------------------------------
  total 409 objects
  Statistics:
        MT    Count TotalSize Class Name
  0015a498      409   7296540      Free
  Total 409 objects
  ```

  <span data-ttu-id="2b5fd-386">이 출력은 힙의 0세대 부분에서 개체에 9MB 공간을 사용하고 있으며 여유 공간이 7MB임을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-386">This output shows that the generation 0 portion of the heap is using 9 MB of space for objects and has 7 MB free.</span></span> <span data-ttu-id="2b5fd-387">이 분석은 0세대가 조각화에 기여하는 정도를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-387">This analysis shows the extent to which generation 0 contributes to fragmentation.</span></span> <span data-ttu-id="2b5fd-388">장기 개체에 의한 조각화의 원인으로 계산된 전체 크기에서 이 힙 사용량을 차감해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-388">This amount of heap usage should be discounted from the total amount as the cause of fragmentation by long-term objects.</span></span>

<a name="Pinned"></a>

### <a name="to-determine-the-number-of-pinned-objects"></a><span data-ttu-id="2b5fd-389">고정된 개체 수를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-389">To determine the number of pinned objects</span></span>

- <span data-ttu-id="2b5fd-390">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-390">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command:</span></span>

  <span data-ttu-id="2b5fd-391">**!gchandles**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-391">**!gchandles**</span></span>

  <span data-ttu-id="2b5fd-392">다음 예제와 같이 표시된 통계는 고정된 핸들 수를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-392">The statistics displayed includes the number of pinned handles, as the following example shows.</span></span>

  ```console
  GC Handle Statistics:
  Strong Handles:      29
  Pinned Handles:      10
  ```

<a name="TimeInGC"></a>

### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a><span data-ttu-id="2b5fd-393">가비지 수집 기간을 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-393">To determine the length of time in a garbage collection</span></span>

- <span data-ttu-id="2b5fd-394">`% Time in GC` 메모리 성능 카운터를 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-394">Examine the `% Time in GC` memory performance counter.</span></span>

  <span data-ttu-id="2b5fd-395">값은 샘플 간격 시간을 사용하여 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-395">The value is calculated by using a sample interval time.</span></span> <span data-ttu-id="2b5fd-396">각 가비지 수집이 끝날 때 카운터가 업데이트되므로 간격 중에 수집이 발생하지 않은 경우 현재 샘플은 이전 샘플과 동일한 값을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-396">Because the counters are updated at the end of each garbage collection, the current sample will have the same value as the previous sample if no collections occurred during the interval.</span></span>

  <span data-ttu-id="2b5fd-397">수집 시간은 샘플 간격 시간에 백분율 값을 곱하여 구합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-397">Collection time is obtained by multiplying the sample interval time with the percentage value.</span></span>

  <span data-ttu-id="2b5fd-398">다음 데이터는 8초 연구를 위해 2초 샘플링 간격 4개를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-398">The following data shows four sampling intervals of two seconds, for an 8-second study.</span></span> <span data-ttu-id="2b5fd-399">`Gen0`, `Gen1` 및 `Gen2` 열은 해당 세대에 대해 해당 간격 중에 발생한 가비지 수집 횟수를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-399">The `Gen0`, `Gen1`, and `Gen2` columns show the number of garbage collections that occurred during that interval for that generation.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2    % Time in GC
          1       9       3       1              10
          2      10       3       1               1
          3      11       3       1               3
          4      11       3       1               3
  ```

  <span data-ttu-id="2b5fd-400">이 정보는 가비지 수집이 발생한 시간을 표시하지 않지만 시간 간격에서 발생한 가비지 수집 횟수를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-400">This information does not show when the garbage collection occurred, but you can determine the number of garbage collections that occurred in an interval of time.</span></span> <span data-ttu-id="2b5fd-401">최악의 경우를 가정하여 2번째 간격이 시작될 때 10번째 0세대 가비지 수집이 완료되었으며 5번째 간격이 끝날 때 11번째 0세대 가비지 수집이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-401">Assuming the worst case, the tenth generation 0 garbage collection finished at the start of the second interval, and the eleventh generation 0 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="2b5fd-402">10번째 가비지 수집의 끝과 11번째 가비지 수집의 끝 사이의 시간은 약 2초이며, 성능 카운터에 3%가 표시되므로 11번째 0세대 가비지 수집 기간은 (2초 \* 3% = 60ms)입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-402">The time between the end of the tenth and the end of the eleventh garbage collection is about 2 seconds, and the performance counter shows 3%, so the duration of the eleventh generation 0 garbage collection was (2 seconds \* 3% = 60ms).</span></span>

  <span data-ttu-id="2b5fd-403">이 예제에서는 5개 기간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-403">In this example, there are 5 periods.</span></span>

  ```console
  Interval    Gen0    Gen1    Gen2     % Time in GC
          1       9       3       1                3
          2      10       3       1                1
          3      11       4       2                1
          4      11       4       2                1
          5      11       4       2               20
  ```

  <span data-ttu-id="2b5fd-404">2번째 2세대 가비지 수집은 3번째 간격 중에 시작되고 5번째 간격에 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-404">The second generation 2 garbage collection started during the third interval and finished at the fifth interval.</span></span> <span data-ttu-id="2b5fd-405">최악의 경우를 가정하여 0세대에 대한 마지막 수집은 2번째 간격이 시작될 때 완료된 수집이었으며 5번째 간격이 끝날 때 2세대 가비지 수집이 완료되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-405">Assuming the worst case, the last garbage collection was for a generation 0 collection that finished at the start of the second interval, and the generation 2 garbage collection finished at the end of the fifth interval.</span></span> <span data-ttu-id="2b5fd-406">따라서 0세대 가비지 수집의 끝과 2세대 가비지 수집의 끝 사이의 시간은 4초입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-406">Therefore, the time between the end of the generation 0 garbage collection and the end of the generation 2 garbage collection is 4 seconds.</span></span> <span data-ttu-id="2b5fd-407">`% Time in GC` 카운터는 20%이므로 2세대 가비지 수집에 소요되었을 수 있는 최대 시간은 (4초 \* 20% = 800ms)입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-407">Because the `% Time in GC` counter is 20%, the maximum amount of time the generation 2 garbage collection could have taken is (4 seconds \* 20% = 800ms).</span></span>

- <span data-ttu-id="2b5fd-408">또는 [가비지 컬렉션 ETW 이벤트](../../framework/performance/garbage-collection-etw-events.md)를 사용하여 가비지 컬렉션 길이를 결정하고 정보를 분석하여 가비지 컬렉션 기간을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-408">Alternatively, you can determine the length of a garbage collection by using [garbage collection ETW events](../../framework/performance/garbage-collection-etw-events.md), and analyze the information to determine the duration of garbage collection.</span></span>

  <span data-ttu-id="2b5fd-409">예를 들어 다음 데이터는 비 동시 가비지 컬렉션 중에 발생한 이벤트 시퀀스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-409">For example, the following data shows an event sequence that occurred during a non-concurrent garbage collection.</span></span>

  ```console
  Timestamp    Event name
  513052        GCSuspendEEBegin_V1
  513078        GCSuspendEEEnd
  513090        GCStart_V1
  517890        GCEnd_V1
  517894        GCHeapStats
  517897        GCRestartEEBegin
  517918        GCRestartEEEnd
  ```

  <span data-ttu-id="2b5fd-410">관리되는 스레드를 일시 중단하는 데 26us(`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`) 걸렸습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-410">Suspending the managed thread took 26us (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`).</span></span>

  <span data-ttu-id="2b5fd-411">실제 가비지 수집에 4.8ms(`GCEnd_V1` – `GCStart_V1`) 걸렸습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-411">The actual garbage collection took 4.8ms (`GCEnd_V1` – `GCStart_V1`).</span></span>

  <span data-ttu-id="2b5fd-412">관리되는 스레드를 다시 시작하는 데 21us(`GCRestartEEEnd` – `GCRestartEEBegin`) 걸렸습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-412">Resuming the managed threads took 21us (`GCRestartEEEnd` – `GCRestartEEBegin`).</span></span>

  <span data-ttu-id="2b5fd-413">다음 출력은 백그라운드 가비지 수집에 대한 예제를 제공하며 프로세스, 스레드 및 이벤트 필드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-413">The following output provides an example for background garbage collection, and includes the process, thread, and event fields.</span></span> <span data-ttu-id="2b5fd-414">일부 데이터만 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-414">(Not all data is shown.)</span></span>

  ```console
  timestamp(us)    event name            process    thread    event field
  42504385        GCSuspendEEBegin_V1    Test.exe    4372             1
  42504648        GCSuspendEEEnd         Test.exe    4372
  42504816        GCStart_V1             Test.exe    4372        102019
  42504907        GCStart_V1             Test.exe    4372        102020
  42514170        GCEnd_V1               Test.exe    4372
  42514204        GCHeapStats            Test.exe    4372        102020
  42832052        GCRestartEEBegin       Test.exe    4372
  42832136        GCRestartEEEnd         Test.exe    4372
  63685394        GCSuspendEEBegin_V1    Test.exe    4744             6
  63686347        GCSuspendEEEnd         Test.exe    4744
  63784294        GCRestartEEBegin       Test.exe    4744
  63784407        GCRestartEEEnd         Test.exe    4744
  89931423        GCEnd_V1               Test.exe    4372        102019
  89931464        GCHeapStats            Test.exe    4372
  ```

  <span data-ttu-id="2b5fd-415">42504816의 `GCStart_V1` 이벤트는 마지막 필드가 `1`이므로 백그라운드 가비지 수집임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-415">The `GCStart_V1` event at 42504816 indicates that this is a background garbage collection, because the last field is `1`.</span></span> <span data-ttu-id="2b5fd-416">가비지 수집 번호</span><span class="sxs-lookup"><span data-stu-id="2b5fd-416">This becomes garbage collection No.</span></span> <span data-ttu-id="2b5fd-417">102019가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-417">102019.</span></span>

  <span data-ttu-id="2b5fd-418">`GCStart` 이벤트는 백그라운드 가비지 수집을 시작하기 전에 단기 가비지 수집이 필요한 경우에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-418">The `GCStart` event occurs because there is a need for an ephemeral garbage collection before you start a background garbage collection.</span></span> <span data-ttu-id="2b5fd-419">가비지 수집 번호</span><span class="sxs-lookup"><span data-stu-id="2b5fd-419">This becomes garbage collection No.</span></span> <span data-ttu-id="2b5fd-420">102020이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-420">102020.</span></span>

  <span data-ttu-id="2b5fd-421">42514170에서 가비지 수집 번호</span><span class="sxs-lookup"><span data-stu-id="2b5fd-421">At 42514170, garbage collection No.</span></span> <span data-ttu-id="2b5fd-422">102020이 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-422">102020 finishes.</span></span> <span data-ttu-id="2b5fd-423">이 지점에서 관리되는 스레드가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-423">The managed threads are restarted at this point.</span></span> <span data-ttu-id="2b5fd-424">이 수집은 이 백그라운드 가비지 수집을 트리거한 스레드 4372에서 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-424">This is completed on thread 4372, which triggered this background garbage collection.</span></span>

  <span data-ttu-id="2b5fd-425">스레드 4744에서 일시 중단이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-425">On thread 4744, a suspension occurs.</span></span> <span data-ttu-id="2b5fd-426">백그라운드 가비지 수집이 관리되는 스레드를 일시 중단해야 하는 경우는 이때뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-426">This is the only time at which the background garbage collection has to suspend managed threads.</span></span> <span data-ttu-id="2b5fd-427">이 기간은 약 99ms((63784407-63685394)/1000)입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-427">This duration is approximately 99ms ((63784407-63685394)/1000).</span></span>

  <span data-ttu-id="2b5fd-428">백그라운드 가비지 수집에 대한 `GCEnd` 이벤트는 89931423에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-428">The `GCEnd` event for the background garbage collection is at 89931423.</span></span> <span data-ttu-id="2b5fd-429">이는 백그라운드 가비지 수집이 약 47초((89931423-42504816)/1000) 동안 지속되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-429">This means that the background garbage collection lasted for about 47seconds ((89931423-42504816)/1000).</span></span>

  <span data-ttu-id="2b5fd-430">관리되는 스레드가 실행되는 동안 개수에 관계없이 발생하는 단기 가비지 수집을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-430">While the managed threads are running, you can see any number of ephemeral garbage collections occurring.</span></span>

<a name="Triggered"></a>

### <a name="to-determine-what-triggered-a-garbage-collection"></a><span data-ttu-id="2b5fd-431">가비지 수집 트리거를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-431">To determine what triggered a garbage collection</span></span>

- <span data-ttu-id="2b5fd-432">SOS 디버거 확장이 로드된 WinDbg 또는 Visual Studio 디버거에서 다음 명령을 입력하여 호출 스택과 함께 모든 스레드를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-432">In the WinDbg or Visual Studio debugger with the SOS debugger extension loaded, type the following command to show all the threads with their call stacks:</span></span>

  <span data-ttu-id="2b5fd-433">**~\*kb**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-433">**~\*kb**</span></span>

  <span data-ttu-id="2b5fd-434">이 명령은 다음과 유사한 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-434">This command displays output similar to the following.</span></span>

  ```console
  0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect
  0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4
  0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48
  ```

  <span data-ttu-id="2b5fd-435">가비지 수집이 운영 체제의 메모리 부족 알림으로 인해 발생한 경우 스레드가 종료자 스레드라는 것을 제외하면 호출 스택이 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-435">If the garbage collection was caused by a low memory notification from the operating system, the call stack is similar, except that the thread is the finalizer thread.</span></span> <span data-ttu-id="2b5fd-436">종료자 스레드는 비동기 메모리 부족 알림을 가져오고 가비지 수집을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-436">The finalizer thread gets an asynchronous low memory notification and induces the garbage collection.</span></span>

  <span data-ttu-id="2b5fd-437">가비지 수집이 메모리 할당에 의해 발생한 경우 스택이 다음과 같이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-437">If the garbage collection was caused by memory allocation, the stack appears as follows:</span></span>

  ```console
  0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration
  0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1
  0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18
  0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b
  0012f310 7a02ae4c mscorwks!Alloc+0x60
  0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd
  0012f424 300027f4 mscorwks!JIT_NewArr1+0x148
  000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c
  0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153
  ```

  <span data-ttu-id="2b5fd-438">결국 Just-In-Time 도우미(`JIT_New*`)가 `GCHeap::GarbageCollectGeneration`을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-438">A just-in-time helper (`JIT_New*`) eventually calls `GCHeap::GarbageCollectGeneration`.</span></span> <span data-ttu-id="2b5fd-439">2세대 가비지 수집이 할당에 의해 발생한 경우 2세대 가비지 수집에서 수집된 개체와 이를 방지하는 방법을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-439">If you determine that generation 2 garbage collections are caused by allocations, you must determine which objects are collected by a generation 2 garbage collection and how to avoid them.</span></span> <span data-ttu-id="2b5fd-440">즉, 2세대 가비지 수집의 시작과 끝 사이의 차이 및 2세대 수집을 발생시킨 개체를 확인하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-440">That is, you want to determine the difference between the start and the end of a generation 2 garbage collection, and the objects that caused the generation 2 collection.</span></span>

  <span data-ttu-id="2b5fd-441">예를 들어 디버거에서 다음 명령을 입력하여 2세대 컬렉션의 시작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-441">For example, type the following command in the debugger to show the beginning of a generation 2 collection:</span></span>

  <span data-ttu-id="2b5fd-442">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-442">**!dumpheap –stat**</span></span>

  <span data-ttu-id="2b5fd-443">예제 출력(가장 많은 공간을 사용하는 개체를 표시하기 위해 요약됨):</span><span class="sxs-lookup"><span data-stu-id="2b5fd-443">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    31857      9862328 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  00155f80    21248     12256296      Free
  79103b6c   297003     13068132 System.Threading.ReaderWriterLock
  7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary
  7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  035f0ee4    89192     38887712 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  7912c444    91616     71887080 System.Double[]
  791242ec    32451     82462728 System.Collections.Hashtable+bucket[]
  790fa3e0  2459154    112128436 System.String
  Total 6471774 objects
  ```

  <span data-ttu-id="2b5fd-444">2세대의 끝에서 명령을 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-444">Repeat the command at the end of generation 2:</span></span>

  <span data-ttu-id="2b5fd-445">**!dumpheap –stat**</span><span class="sxs-lookup"><span data-stu-id="2b5fd-445">**!dumpheap –stat**</span></span>

  <span data-ttu-id="2b5fd-446">예제 출력(가장 많은 공간을 사용하는 개체를 표시하기 위해 요약됨):</span><span class="sxs-lookup"><span data-stu-id="2b5fd-446">Example output (abridged to show the objects that use the most space):</span></span>

  ```console
  79124228    26648      9314256 System.Object[]
  035f0384    25668     11601936 Toolkit.TlkPosition
  79103b6c   296770     13057880 System.Threading.ReaderWriterLock
  7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary
  7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode
  7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary
  00155f80    13806     34007212      Free
  035f0ee4    89187     38885532 Toolkit.TlkOrder
  00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]
  791242ec    32370     82359768 System.Collections.Hashtable+bucket[]
  790fa3e0  2440020    111341808 System.String
  Total 6417525 objects
  ```

  <span data-ttu-id="2b5fd-447">`double[]` 개체가 출력의 끝에서 사라졌으며, 이는 수집되었음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-447">The `double[]` objects disappeared from the end of the output, which means that they were collected.</span></span> <span data-ttu-id="2b5fd-448">이러한 개체가 약 70MB를 차지합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-448">These objects account for approximately 70 MB.</span></span> <span data-ttu-id="2b5fd-449">나머지 개체는 많이 변경되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-449">The remaining objects did not change much.</span></span> <span data-ttu-id="2b5fd-450">따라서 이러한 `double[]` 개체가 이 2세대 가비지 수집이 발생한 이유입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-450">Therefore, these `double[]` objects were the reason why this generation 2 garbage collection occurred.</span></span> <span data-ttu-id="2b5fd-451">다음 단계에서는 `double[]` 개체가 있는 이유 및 작동하지 않는 이유를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-451">Your next step is to determine why the `double[]` objects are there and why they died.</span></span> <span data-ttu-id="2b5fd-452">이러한 개체가 어디서 온 것인지 코드 개발자에게 묻거나 **gcroot** 명령을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-452">You can ask the code developer where these objects came from, or you can use the **gcroot** command.</span></span>

<a name="HighCPU"></a>

### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a><span data-ttu-id="2b5fd-453">높은 CPU 사용량이 가비지 컬렉션에 의해 발생한 것인지 여부를 확인하려면</span><span class="sxs-lookup"><span data-stu-id="2b5fd-453">To determine whether high CPU usage is caused by garbage collection</span></span>

- <span data-ttu-id="2b5fd-454">`% Time in GC` 메모리 성능 카운터 값을 프로세스 시간과 상호 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-454">Correlate the `% Time in GC` memory performance counter value with the process time.</span></span>

  <span data-ttu-id="2b5fd-455">`% Time in GC` 값이 프로세스 시간과 동시에 급증하는 경우 가비지 수집으로 인해 CPU 사용량이 증가한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-455">If the `% Time in GC` value spikes at the same time as process time, garbage collection is causing a high CPU usage.</span></span> <span data-ttu-id="2b5fd-456">그러지 않으면 애플리케이션을 프로파일링하여 높은 사용량이 발생하는 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="2b5fd-456">Otherwise, profile the application to find where the high usage is occurring.</span></span>

## <a name="see-also"></a><span data-ttu-id="2b5fd-457">참조</span><span class="sxs-lookup"><span data-stu-id="2b5fd-457">See also</span></span>

- [<span data-ttu-id="2b5fd-458">가비지 수집</span><span class="sxs-lookup"><span data-stu-id="2b5fd-458">Garbage Collection</span></span>](index.md)
