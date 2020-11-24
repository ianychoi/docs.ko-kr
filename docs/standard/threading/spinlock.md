---
title: SpinLock
ms.date: 03/30/2017
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: 071bde6e8b32d5712256e24c83d713cd63f2bffb
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819008"
---
# <a name="spinlock"></a><span data-ttu-id="1ce6b-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="1ce6b-102">SpinLock</span></span>
<span data-ttu-id="1ce6b-103"><xref:System.Threading.SpinLock> 구조는 잠금을 획득하기 위해 대기하는 동안 회전하는 하위 수준의 동기화 기본 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="1ce6b-104">멀티 코어 컴퓨터에서 대기 시간이 짧은 것으로 예상되고 경합이 최소인 경우 <xref:System.Threading.SpinLock>의 성능이 다른 종류의 잠금보다 더 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="1ce6b-105">그러나 프로파일링을 통해 <xref:System.Threading.Monitor?displayProperty=nameWithType> 메서드 또는 <xref:System.Threading.Interlocked> 메서드가 프로그램의 성능을 크게 낮추는 것을 확인하는 경우에만 <xref:System.Threading.SpinLock>을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="1ce6b-106"><xref:System.Threading.SpinLock>은 아직 잠금을 획득하지 않은 경우에도 스레드의 시간 조각을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="1ce6b-107">스레드 우선 순위가 반전되는 것을 방지하고 가비지 수집기가 진행되도록 하기 위해 이 작업을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="1ce6b-108"><xref:System.Threading.SpinLock>을 사용하면 스레드가 매우 짧은 시간 범위 이상으로 잠금을 보유할 수 없고 잠금을 보유하는 동안 스레드가 차단할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="1ce6b-109">SpinLock은 값 형식이므로 두 개의 사본이 동일한 잠금을 참조하도록 하려는 경우 참조를 통해 명시적으로 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="1ce6b-110">이 유형을 사용하는 방법에 대한 자세한 내용은 <xref:System.Threading.SpinLock?displayProperty=nameWithType>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="1ce6b-111">예를 들어 [방법: 낮은 수준의 동기화에 SpinLock 사용](how-to-use-spinlock-for-low-level-synchronization.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="1ce6b-112"><xref:System.Threading.SpinLock>은 ‘스레드 추적’ 모드를 지원합니다. 스레드 추적 모드는 특정 시간에 잠금을 보유하고 있는 스레드를 추적하기 위해 개발 단계 중에 사용할 수 있습니다.  - </span><span class="sxs-lookup"><span data-stu-id="1ce6b-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="1ce6b-113">스레드 추적 모드는 디버깅에 매우 유용하지만 성능이 저하될 수 있으므로 프로그램의 릴리스 버전에서 끄는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="1ce6b-114">자세한 내용은 [방법: 회전 잠금에서 스레드 추적 모드 사용](how-to-enable-thread-tracking-mode-in-spinlock.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1ce6b-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ce6b-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1ce6b-115">See also</span></span>

- [<span data-ttu-id="1ce6b-116">스레딩 개체 및 기능</span><span class="sxs-lookup"><span data-stu-id="1ce6b-116">Threading Objects and Features</span></span>](threading-objects-and-features.md)
