---
title: '방법: 낮은 수준의 동기화에 SpinLock 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: 148ef5e9d5c570ef04bc6e716a884db5e688d91a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826393"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="6c241-102">방법: 낮은 수준의 동기화에 SpinLock 사용</span><span class="sxs-lookup"><span data-stu-id="6c241-102">How to: use SpinLock for low-level synchronization</span></span>

<span data-ttu-id="6c241-103">다음 예제는 <xref:System.Threading.SpinLock> 사용 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="6c241-104">이 예제에서 중요 섹션은 최소한의 작업을 수행하여 <xref:System.Threading.SpinLock>에 대해 적합한 후보를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-104">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="6c241-105">작업을 약간 늘리면 표준 잠금과 비교하여 <xref:System.Threading.SpinLock>의 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-105">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="6c241-106">그러나 SpinLock이 표준 잠금보다 비용이 드는 지점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-106">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="6c241-107">프로파일링 도구에서 동시성 프로파일링 기능을 사용하여 어떤 유형의 잠금이 프로그램에서 더 나은 성능을 제공하는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-107">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="6c241-108">자세한 내용은 [동시성 시각화 도우미](/visualstudio/profiling/concurrency-visualizer)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c241-108">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="6c241-109"><xref:System.Threading.SpinLock>은 공유 리소스에 대한 잠금을 오랫동안 유지하지 않는 경우에 유용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-109"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="6c241-110">이러한 경우에 다중 코어 컴퓨터에서 차단된 스레드를 잠금이 해제될 때까지 몇 차례 회전하는 것이 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-110">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="6c241-111">CPU를 많이 사용하는 프로세스이기 때문에 회전함으로써 스레드가 차단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-111">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="6c241-112"><xref:System.Threading.SpinLock>은 특정 조건에서 회전을 중지하여 논리 프로세서의 부족 또는 하이퍼 스레딩을 포함한 시스템에서의 우선 순위 반전을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-112"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="6c241-113">이 예제에서는 다중 스레드 액세스를 위해 사용자 동기화가 필요한 <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-113">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="6c241-114">또 다른 옵션은 사용자 잠금이 필요하지 않은 <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-114">Another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="6c241-115"><xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType> 호출에서 `false`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-115">Note the use of `false` in the call to <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6c241-116">그러면 최상의 성능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-116">This provides the best performance.</span></span> <span data-ttu-id="6c241-117">IA64 아키텍처에서 `true`를 지정하여 메모리 펜스를 사용합니다. 그러면 쓰기 버퍼를 플러시하여 시작할 다른 스레드에서 잠금을 사용할 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c241-117">Specify `true` on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to enter.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6c241-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6c241-118">See also</span></span>

- [<span data-ttu-id="6c241-119">스레딩 개체 및 기능</span><span class="sxs-lookup"><span data-stu-id="6c241-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="6c241-120">lock 문(C#)</span><span class="sxs-lookup"><span data-stu-id="6c241-120">lock statement (C#)</span></span>](../../csharp/language-reference/keywords/lock-statement.md)
- [<span data-ttu-id="6c241-121">SyncLock 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c241-121">SyncLock statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/synclock-statement.md)
