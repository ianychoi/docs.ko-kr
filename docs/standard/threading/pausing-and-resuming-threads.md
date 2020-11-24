---
title: 스레드 일시 중지 및 중단
description: .NET에서 스레드를 일시 중지 및 중단하는 방법을 알아봅니다. Thread.Sleep 및 Thread.Interrupt 같은 메서드와 ThreadInterruptedException 같은 예외를 사용하는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interrupting threads
- threading [.NET], pausing
- pausing threads
ms.assetid: 9fce4859-a19d-4506-b082-7dd0792688ca
ms.openlocfilehash: 157109ad9e9009516b107b271a59267f982c784d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826224"
---
# <a name="pausing-and-interrupting-threads"></a><span data-ttu-id="f8a7a-104">스레드 일시 중지 및 중단</span><span class="sxs-lookup"><span data-stu-id="f8a7a-104">Pausing and interrupting threads</span></span>

<span data-ttu-id="f8a7a-105">스레드 작업을 동기화하는 가장 일반적인 방법은 스레드를 차단 및 해제하거나 개체 또는 코드 영역을 잠그는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-105">The most common ways to synchronize the activities of threads are to block and release threads, or to lock objects or regions of code.</span></span> <span data-ttu-id="f8a7a-106">이러한 잠금 및 차단 메커니즘에 대한 자세한 내용은 [동기화 기본 형식 개요](overview-of-synchronization-primitives.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-106">For more information on these locking and blocking mechanisms, see [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="f8a7a-107">스레드가 자동으로 중지되도록 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-107">You can also have threads put themselves to sleep.</span></span> <span data-ttu-id="f8a7a-108">스레드가 차단 또는 중지된 경우 <xref:System.Threading.ThreadInterruptedException>을 사용하여 대기 상태에서 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-108">When threads are blocked or sleeping, you can use a <xref:System.Threading.ThreadInterruptedException> to break them out of their wait states.</span></span>  
  
## <a name="the-threadsleep-method"></a><span data-ttu-id="f8a7a-109">Thread.Sleep 메서드</span><span class="sxs-lookup"><span data-stu-id="f8a7a-109">The Thread.Sleep method</span></span>

 <span data-ttu-id="f8a7a-110"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> 메서드를 호출하면 현재 스레드가 메서드에 전달하는 시간(밀리초) 또는 시간 간격 동안 즉시 차단되고 해당 시간 조각의 나머지 부분을 다른 스레드에 양보합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-110">Calling the <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> method causes the current thread to immediately block for the number of milliseconds or the time interval you pass to the method, and yields the remainder of its time slice to another thread.</span></span> <span data-ttu-id="f8a7a-111">지정된 시간이 지나면 대기 중인 스레드가 다시 실행되기 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-111">Once that interval elapses, the sleeping thread resumes execution.</span></span>  
  
 <span data-ttu-id="f8a7a-112">한 스레드가 다른 스레드에서 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>를 호출할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-112">One thread cannot call <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> on another thread.</span></span>  <span data-ttu-id="f8a7a-113"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>은 현재 스레드를 항상 일시 중지하는 정적 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-113"><xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> is a static method that always causes the current thread to sleep.</span></span>  
  
 <span data-ttu-id="f8a7a-114"><xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> 값을 사용하여 <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>을 호출하면 일시 중지 스레드에서 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 메서드를 호출하는 다른 스레드에 의해 중단될 때까지 또는 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드 호출에 의해 종료될 때까지 스레드가 일시 중지됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-114">Calling <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> with a value of <xref:System.Threading.Timeout.Infinite?displayProperty=nameWithType> causes a thread to sleep until it is interrupted by another thread that calls the  <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the sleeping thread, or until it is terminated by a call to its <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method.</span></span>  <span data-ttu-id="f8a7a-115">다음 예제에서는 대기 중인 스레드를 중단하는 두 가지 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-115">The following example illustrates both methods of interrupting a sleeping thread.</span></span>  
  
 [!code-csharp[Conceptual.Threading.Resuming#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Threading.Resuming/cs/Sleep1.cs#1)]
 [!code-vb[Conceptual.Threading.Resuming#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Threading.Resuming/vb/Sleep1.vb#1)]  
  
## <a name="interrupting-threads"></a><span data-ttu-id="f8a7a-116">스레드 중단</span><span class="sxs-lookup"><span data-stu-id="f8a7a-116">Interrupting threads</span></span>

 <span data-ttu-id="f8a7a-117">차단된 스레드에서 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 메서드를 호출하여 <xref:System.Threading.ThreadInterruptedException>을 throw하면 스레드가 차단 호출에서 분리되어 대기 스레드를 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-117">You can interrupt a waiting thread by calling the <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> method on the blocked thread to throw a <xref:System.Threading.ThreadInterruptedException>, which breaks the thread out of the blocking call.</span></span> <span data-ttu-id="f8a7a-118">스레드는 <xref:System.Threading.ThreadInterruptedException>을 catch하고 작업을 계속하는 데 필요한 동작을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-118">The thread should catch the <xref:System.Threading.ThreadInterruptedException> and do whatever is appropriate to continue working.</span></span> <span data-ttu-id="f8a7a-119">스레드가 예외를 무시하는 경우 런타임은 예외를 catch하고 스레드를 중지합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-119">If the thread ignores the exception, the runtime catches the exception and stops the thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8a7a-120"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>를 호출할 때 대상 스레드가 차단되지 않는 경우 스레드는 차단될 때까지 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-120">If the target thread is not blocked when <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> is called, the thread is not interrupted until it blocks.</span></span> <span data-ttu-id="f8a7a-121">스레드가 차단되지 않으면 중단 없이 완료될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-121">If the thread never blocks, it could complete without ever being interrupted.</span></span>  
  
 <span data-ttu-id="f8a7a-122">대기가 관리되는 대기인 경우 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 및 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 둘 다 스레드를 즉시 깨웁니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-122">If a wait is a managed wait, then <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> and <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> both wake the thread immediately.</span></span> <span data-ttu-id="f8a7a-123">대기가 관리되지 않는 대기인 경우(예: Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) 함수에 대한 플랫폼 호출) 스레드가 관리 코드로 반환되거나 호출할 때까지 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> 및 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>는 스레드를 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-123">If a wait is an unmanaged wait (for example, a platform invoke call to the Win32 [WaitForSingleObject](/windows/desktop/api/synchapi/nf-synchapi-waitforsingleobject) function), neither <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> nor <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> can take control of the thread until it returns to or calls into managed code.</span></span> <span data-ttu-id="f8a7a-124">관리 코드에서 동작은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-124">In managed code, the behavior is as follows:</span></span>  
  
- <span data-ttu-id="f8a7a-125"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>는 대기 상태에서 스레드를 깨우고 대상 스레드에서 <xref:System.Threading.ThreadInterruptedException>이 발생하게 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-125"><xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadInterruptedException> to be thrown in the destination thread.</span></span>  
  
- <span data-ttu-id="f8a7a-126"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>는 대기 상태에서 스레드를 깨우고 스레드에서 <xref:System.Threading.ThreadAbortException>을 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-126"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> wakes a thread out of any wait it might be in and causes a <xref:System.Threading.ThreadAbortException> to be thrown on the thread.</span></span> <span data-ttu-id="f8a7a-127">자세한 내용은 [스레드 제거](destroying-threads.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8a7a-127">For details, see [Destroying Threads](destroying-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a7a-128">참조</span><span class="sxs-lookup"><span data-stu-id="f8a7a-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadInterruptedException>
- <xref:System.Threading.ThreadAbortException>
- [<span data-ttu-id="f8a7a-129">스레딩</span><span class="sxs-lookup"><span data-stu-id="f8a7a-129">Threading</span></span>](index.md)
- [<span data-ttu-id="f8a7a-130">스레드 및 스레딩 사용</span><span class="sxs-lookup"><span data-stu-id="f8a7a-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="f8a7a-131">동기화 기본 형식 개요</span><span class="sxs-lookup"><span data-stu-id="f8a7a-131">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)
