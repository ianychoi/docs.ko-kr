---
title: 스레드 제거
description: .NET에서 스레드를 제거해야 하는 경우 협조적 취소 또는 Thread.Abort 메서드 같은 옵션에 대해 알아봅니다. ThreadAbortException을 처리하는 방법을 알아봅니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- destroying threads
- threading [.NET], destroying threads
ms.assetid: df54e648-c5d1-47c9-bd29-8e4438c1db6d
ms.openlocfilehash: bdba09f5709cf99bc0d076e3875a914cc7c5a11e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723768"
---
# <a name="destroying-threads"></a><span data-ttu-id="4eb14-104">스레드 제거</span><span class="sxs-lookup"><span data-stu-id="4eb14-104">Destroying threads</span></span>

<span data-ttu-id="4eb14-105">스레드의 실행을 종료하려면 일반적으로 [협조적 취소 모델](cancellation-in-managed-threads.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-105">To terminate the execution of the thread, you usually use the [cooperative cancellation model](cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="4eb14-106">경우에 따라 스레드의 협조적 중지가 불가할 수 있는데, 이는 협조적 취소를 위해 설계되지 않은 타사 코드를 실행하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-106">Sometimes it is not possible to stop a thread cooperatively, because it runs third-party code not designed for cooperative cancellation.</span></span> <span data-ttu-id="4eb14-107">.NET Framework의 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드를 사용하여 관리되는 스레드를 강제로 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-107">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method in .NET Framework can be used to terminate a managed thread forcibly.</span></span> <span data-ttu-id="4eb14-108"><xref:System.Threading.Thread.Abort%2A>를 호출할 때 공용 언어 런타임이 대상 스레드에서 <xref:System.Threading.ThreadAbortException>을 throw하며, 대상 스레드가 이를 catch할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-108">When you call <xref:System.Threading.Thread.Abort%2A>, the Common Language Runtime throws a <xref:System.Threading.ThreadAbortException> in the target thread, which the target thread can catch.</span></span> <span data-ttu-id="4eb14-109">자세한 내용은 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4eb14-109">For more information, see <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4eb14-110"><xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드는 .NET Core를 포함하여 .Net 5 이상 버전에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-110">The <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method is not supported in .NET 5 (including .NET Core) and later versions.</span></span> <span data-ttu-id="4eb14-111">.NET 5 이상에서 강제로 타사 코드 실행을 종료해야 하는 경우 별도의 프로세스에서 실행하고 <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-111">If you need to terminate the execution of third-party code forcibly in .NET 5+, run it in the separate process and use <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="4eb14-112"><xref:System.Threading.Thread.Abort%2A> 메서드가 호출될 때 스레드가 비관리 코드를 실행하는 경우 런타임은 이를 <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-112">If a thread is executing unmanaged code when its <xref:System.Threading.Thread.Abort%2A> method is called, the runtime marks it <xref:System.Threading.ThreadState.AbortRequested?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4eb14-113">스레드가 관리 코드로 돌아오면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-113">The exception is thrown when the thread returns to managed code.</span></span>  
  
 <span data-ttu-id="4eb14-114">스레드가 중단되면 다시 시작할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-114">Once a thread is aborted, it cannot be restarted.</span></span>  
  
 <span data-ttu-id="4eb14-115">대상 스레드가 <xref:System.Threading.ThreadAbortException>를 catch하고 `finally` 블록에서 임의의 코드를 실행할 수 있으므로 <xref:System.Threading.Thread.Abort%2A> 메서드로 인해 스레드가 즉시 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-115">The <xref:System.Threading.Thread.Abort%2A> method does not cause the thread to abort immediately, because the target thread can catch the <xref:System.Threading.ThreadAbortException> and execute arbitrary amounts of code in a `finally` block.</span></span> <span data-ttu-id="4eb14-116">스레드가 종료될 때까지 기다려야 하는 경우 <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-116">You can call <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> if you need to wait until the thread has ended.</span></span> <span data-ttu-id="4eb14-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType>은 스레드가 실제로 실행을 중지했거나 선택적 시간 제한 간격이 경과할 때까지 반환하지 않는 차단 호출입니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-117"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> is a blocking call that does not return until the thread has actually stopped executing or an optional timeout interval has elapsed.</span></span> <span data-ttu-id="4eb14-118">중단된 스레드는 <xref:System.Threading.Thread.ResetAbort%2A> 메서드를 호출하거나 `finally` 블록에서 제한 없는 처리를 수행할 수 있으므로 제한 시간을 지정하지 않으면 대기가 종료되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-118">The aborted thread could call the <xref:System.Threading.Thread.ResetAbort%2A> method or perform unbounded processing in a `finally` block, so if you do not specify a timeout, the wait is not guaranteed to end.</span></span>  
  
 <span data-ttu-id="4eb14-119"><xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> 메서드 호출을 대기 중인 스레드는 <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>을 호출하는 다른 스레드에 의해 중단될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-119">Threads that are waiting on a call to the <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> method can be interrupted by other threads that call <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="handling-threadabortexception"></a><span data-ttu-id="4eb14-120">ThreadAbortException 처리</span><span class="sxs-lookup"><span data-stu-id="4eb14-120">Handling ThreadAbortException</span></span>  

 <span data-ttu-id="4eb14-121">자체 코드에서 <xref:System.Threading.Thread.Abort%2A>를 호출한 결과로 또는 스레드가 실행 중인 애플리케이션 도메인을 언로드한(<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>에서 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>를 사용하여 스레드 종료) 결과로 스레드가 중단될 것으로 예상되는 경우 스레드에서 <xref:System.Threading.ThreadAbortException>을 처리하고 다음 코드와 같이 `finally` 절에서 최종 처리를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-121">If you expect your thread to be aborted, either as a result of calling <xref:System.Threading.Thread.Abort%2A> from your own code or as a result of unloading an application domain in which the thread is running (<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uses <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> to terminate threads), your thread must handle the <xref:System.Threading.ThreadAbortException> and perform any final processing in a `finally` clause, as shown in the following code.</span></span>  
  
```vb  
Try  
    ' Code that is executing when the thread is aborted.  
Catch ex As ThreadAbortException  
    ' Clean-up code can go here.  
    ' If there is no Finally clause, ThreadAbortException is  
    ' re-thrown by the system at the end of the Catch clause.
Finally  
    ' Clean-up code can go here.  
End Try  
' Do not put clean-up code here, because the exception
' is rethrown at the end of the Finally clause.  
```  
  
```csharp  
try
{  
    // Code that is executing when the thread is aborted.  
}
catch (ThreadAbortException ex)
{  
    // Clean-up code can go here.  
    // If there is no Finally clause, ThreadAbortException is  
    // re-thrown by the system at the end of the Catch clause.
}  
// Do not put clean-up code here, because the exception
// is rethrown at the end of the Finally clause.  
```  
  
 <span data-ttu-id="4eb14-122"><xref:System.Threading.ThreadAbortException>이 `finally` 절의 끝에서 또는 `finally` 절이 없는 경우 `catch` 절의 끝에서 시스템을 통해 다시 throw되므로 정리 코드가 `catch` 절 또는 `finally` 절에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-122">Your clean-up code must be in the `catch` clause or the `finally` clause, because a <xref:System.Threading.ThreadAbortException> is rethrown by the system at the end of the `finally` clause, or at the end of the `catch` clause if there is no `finally` clause.</span></span>  
  
 <span data-ttu-id="4eb14-123"><xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> 메서드를 호출하여 시스템이 예외를 다시 throw하지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-123">You can prevent the system from rethrowing the exception by calling the <xref:System.Threading.Thread.ResetAbort%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4eb14-124">그러나 사용자의 코드가 <xref:System.Threading.ThreadAbortException>을 발생시킨 경우에만 이를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4eb14-124">However, you should do this only if your own code caused the <xref:System.Threading.ThreadAbortException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eb14-125">참조</span><span class="sxs-lookup"><span data-stu-id="4eb14-125">See also</span></span>

- <xref:System.Threading.ThreadAbortException>
- <xref:System.Threading.Thread>
- [<span data-ttu-id="4eb14-126">스레드 및 스레딩 사용</span><span class="sxs-lookup"><span data-stu-id="4eb14-126">Using Threads and Threading</span></span>](using-threads-and-threading.md)
