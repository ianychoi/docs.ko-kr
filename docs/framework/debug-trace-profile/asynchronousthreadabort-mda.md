---
title: asynchronousThreadAbort MDA
description: 스레드가 비동기 abort를 다른 스레드에 삽입 하려고 할 때 asynchronousThreadAbort MDA (관리 디버깅 도우미)가 어떻게 활성화 되는지 검토 합니다.
ms.date: 03/30/2017
helpviewer_keywords:
- asynchronous thread aborts
- AsynchronousThreadAbort MDA
- managed debugging assistants (MDAs), asynchronous thread aborts
- threading [.NET Framework], managed debugging assistants
- MDAs (managed debugging assistants), asynchronous thread aborts
ms.assetid: 9ebe40b2-d703-421e-8660-984acc42bfe0
ms.openlocfilehash: 216c4bbe570fe34b59513bb338f0f2c5da0fc3e2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265247"
---
# <a name="asynchronousthreadabort-mda"></a><span data-ttu-id="f3164-103">asynchronousThreadAbort MDA</span><span class="sxs-lookup"><span data-stu-id="f3164-103">asynchronousThreadAbort MDA</span></span>

<span data-ttu-id="f3164-104">`asynchronousThreadAbort` MDA(관리 디버깅 도우미)는 스레드가 비동기 중단을 다른 스레드에 도입하려고 할 때 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-104">The `asynchronousThreadAbort` managed debugging assistant (MDA) is activated when a thread attempts to introduce an asynchronous abort into another thread.</span></span> <span data-ttu-id="f3164-105">동기 스레드 중단은 `asynchronousThreadAbort` MDA를 활성화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-105">Synchronous thread aborts do not activate the `asynchronousThreadAbort` MDA.</span></span>

## <a name="symptoms"></a><span data-ttu-id="f3164-106">증상</span><span class="sxs-lookup"><span data-stu-id="f3164-106">Symptoms</span></span>

 <span data-ttu-id="f3164-107">주 애플리케이션 스레드가 중단되는 경우 애플리케이션이 처리되지 않은 <xref:System.Threading.ThreadAbortException>과 충돌합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-107">An application crashes with an unhandled <xref:System.Threading.ThreadAbortException> when the main application thread is aborted.</span></span> <span data-ttu-id="f3164-108">애플리케이션을 계속 실행하면 결과가 애플리케이션 충돌보다 더욱 악화되어 추가 데이터 손상이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-108">If the application were to continue to execute, the consequences might be worse than the application crashing, possibly resulting in further data corruption.</span></span>

 <span data-ttu-id="f3164-109">원자성으로 의도된 작업이 부분 완료 후 중단되어 애플리케이션 데이터가 예측할 수 없는 상태로 남겨졌을 가능성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-109">Operations meant to be atomic have likely been interrupted after partial completion, leaving application data in an unpredictable state.</span></span> <span data-ttu-id="f3164-110">코드 실행의 임의 지점에서 <xref:System.Threading.ThreadAbortException>이 생성될 수 있으며, 예외가 발생할 것으로 예상되지 않는 지점에서 생성되는 경우도 많습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-110">A <xref:System.Threading.ThreadAbortException> can be generated from seemingly random points in the execution of code, often in places from which an exception is not expected to arise.</span></span> <span data-ttu-id="f3164-111">코드에서 이러한 예외를 처리하지 못해 손상된 상태가 발생할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-111">The code might not be capable of handling such an exception, resulting in a corrupt state.</span></span>

 <span data-ttu-id="f3164-112">문제에 상속되는 임의성으로 인해 증상이 크게 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-112">Symptoms can vary widely due to the randomness inherent to the problem.</span></span>

## <a name="cause"></a><span data-ttu-id="f3164-113">원인</span><span class="sxs-lookup"><span data-stu-id="f3164-113">Cause</span></span>

 <span data-ttu-id="f3164-114">한 스레드의 코드에서 대상 스레드에 대해 <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> 메서드를 호출하여 비동기 스레드 중단을 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-114">Code in one thread called the <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> method on a target thread to introduce an asynchronous thread abort.</span></span> <span data-ttu-id="f3164-115"><xref:System.Threading.Thread.Abort%2A>를 호출하는 코드가 중단 작업의 대상이 아닌 다른 스레드에서 실행되고 있으므로 스레드 중단은 비동기입니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-115">The thread abort is asynchronous because the code that makes the call to <xref:System.Threading.Thread.Abort%2A> is running on a different thread than the target of the abort operation.</span></span> <span data-ttu-id="f3164-116"><xref:System.Threading.Thread.Abort%2A>를 수행하는 스레드는 애플리케이션 상태가 일치하는 안전한 검사점에서만 작업했기 때문에 동기 스레드 중단으로 인한 문제가 발생하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-116">Synchronous thread aborts should not cause a problem because the thread performing the <xref:System.Threading.Thread.Abort%2A> should have done so only at a safe checkpoint where application state is consistent.</span></span>

 <span data-ttu-id="f3164-117">비동기 스레드 중단은 대상 스레드 실행 중 예기치 않은 지점에서 처리되므로 문제를 일으킵니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-117">Asynchronous thread aborts present a problem because they are processed at unpredictable points in the target thread's execution.</span></span> <span data-ttu-id="f3164-118">이를 방지하려면 이런 방식으로 중단될 수 있는 스레드에서 실행되도록 작성된 코드는 거의 모든 코드 줄에서 <xref:System.Threading.ThreadAbortException>을 처리하고 애플리케이션 데이터를 다시 일치 상태로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-118">To avoid this, code written to run on a thread that might be aborted in this manner would need to handle a <xref:System.Threading.ThreadAbortException> at almost every line of code, taking care to put application data back into a consistent state.</span></span> <span data-ttu-id="f3164-119">이 문제를 염두에 두고 코드가 작성되기를 기대하거나 가능한 모든 상황으로부터 보호하는 코드를 작성하는 것은 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-119">It is not realistic to expect code to be written with this problem in mind or to write code that protects against all possible circumstances.</span></span>

 <span data-ttu-id="f3164-120">비관리 코드와 `finally` 블록 호출은 비동기적으로 중단되지 않고 이러한 범주 중 하나에서 종료 시 즉시 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-120">Calls into unmanaged code and `finally` blocks will not be aborted asynchronously but immediately upon exit from one of these categories.</span></span>

 <span data-ttu-id="f3164-121">문제에 내재된 임의성 때문에 원인을 확인하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-121">The cause might be difficult to determine due to the randomness inherent to the problem.</span></span>

## <a name="resolution"></a><span data-ttu-id="f3164-122">해결 방법</span><span class="sxs-lookup"><span data-stu-id="f3164-122">Resolution</span></span>

 <span data-ttu-id="f3164-123">비동기 스레드 중단을 사용해야 하는 코드 디자인을 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f3164-123">Avoid code design that requires the use of asynchronous thread aborts.</span></span> <span data-ttu-id="f3164-124"><xref:System.Threading.Thread.Abort%2A> 호출이 필요 없고 대상 스레드 중단에 더 적합한 여러 가지 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-124">There are several approaches more appropriate for interruption of a target thread that do not require a call to <xref:System.Threading.Thread.Abort%2A>.</span></span> <span data-ttu-id="f3164-125">가장 안전한 방법은 대상 스레드에 중단을 요청하도록 알리는 일반 속성 등의 메커니즘을 도입하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-125">The safest is to introduce a mechanism, such as a common property, that signals the target thread to request an interrupt.</span></span> <span data-ttu-id="f3164-126">대상 스레드는 안전한 특정 검사점에서 신호를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-126">The target thread checks the signal at certain safe checkpoints.</span></span> <span data-ttu-id="f3164-127">인터럽트가 요청된 것을 발견하면 정상적으로 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-127">If it notices that an interrupt has been requested, it can shut down gracefully.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="f3164-128">런타임에 대한 영향</span><span class="sxs-lookup"><span data-stu-id="f3164-128">Effect on the Runtime</span></span>

 <span data-ttu-id="f3164-129">이 MDA는 CLR에 아무런 영향을 미치지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-129">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="f3164-130">비동기 스레드 중단에 대한 데이터를 보고만 합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-130">It only reports data about asynchronous thread aborts.</span></span>

## <a name="output"></a><span data-ttu-id="f3164-131">출력</span><span class="sxs-lookup"><span data-stu-id="f3164-131">Output</span></span>

 <span data-ttu-id="f3164-132">MDA는 중단을 수행하는 스레드의 ID 및 중단의 대상이 되는 스레드의 ID를 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-132">The MDA reports the ID of the thread performing the abort and the ID of the thread that is the target of the abort.</span></span> <span data-ttu-id="f3164-133">비동기 중단으로 제한되므로 두 ID는 동일하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-133">These will never be the same because this is limited to asynchronous aborts.</span></span>

## <a name="configuration"></a><span data-ttu-id="f3164-134">구성</span><span class="sxs-lookup"><span data-stu-id="f3164-134">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <asynchronousThreadAbort />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="f3164-135">예제</span><span class="sxs-lookup"><span data-stu-id="f3164-135">Example</span></span>

 <span data-ttu-id="f3164-136">`asynchronousThreadAbort` MDA를 활성화하려는 경우 실행 중인 별도 스레드에서 <xref:System.Threading.Thread.Abort%2A>를 호출하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f3164-136">Activating the `asynchronousThreadAbort` MDA requires only a call to <xref:System.Threading.Thread.Abort%2A> on a separate running thread.</span></span> <span data-ttu-id="f3164-137">스레드 시작 함수의 내용이 임의 지점에서 중단에 의해 인터럽트될 수 있는 보다 복잡한 작업 집합인 경우의 결과를 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="f3164-137">Consider the consequences if the contents of the thread start function were a set of more complex operations which might be interrupted at any arbitrary point by the abort.</span></span>

```csharp
using System.Threading;
void FireMda()
{
    Thread t = new Thread(delegate() { Thread.Sleep(1000); });
    t.Start();
    // The following line activates the MDA.
    t.Abort();
    t.Join();
}
```

## <a name="see-also"></a><span data-ttu-id="f3164-138">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f3164-138">See also</span></span>

- <xref:System.Threading.Thread>
- [<span data-ttu-id="f3164-139">관리 디버깅 도우미를 사용하여 오류 진단</span><span class="sxs-lookup"><span data-stu-id="f3164-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
