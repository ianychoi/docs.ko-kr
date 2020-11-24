---
title: '방법: PLINQ 쿼리 성능 측정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 43f83a34531b853d108785052f637d9568c45280
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826881"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="4d4d9-102">방법: PLINQ 쿼리 성능 측정</span><span class="sxs-lookup"><span data-stu-id="4d4d9-102">How to: Measure PLINQ Query Performance</span></span>

<span data-ttu-id="4d4d9-103">다음 예제에서는 <xref:System.Diagnostics.Stopwatch> 클래스를 사용하여 PLINQ 쿼리를 실행하는 데 걸리는 시간을 측정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-103">This example shows how to use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d4d9-104">예제</span><span class="sxs-lookup"><span data-stu-id="4d4d9-104">Example</span></span>  
 <span data-ttu-id="4d4d9-105">이 예제에서는 빈 `foreach` 루프(Visual Basic에서 `For Each`)를 사용하여 쿼리를 실행하는 데 걸리는 시간을 측정합니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="4d4d9-106">실제 코드에서 루프는 일반적으로 전체 쿼리 실행 시간에 추가되는 추가 처리 단계를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="4d4d9-107">루프 바로 전까지 스톱워치를 시작하지 않습니다. 루프 바로 전은 쿼리 실행을 시작하는 시점이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-107">Notice that the stopwatch is not started until just before the loop, because that's when the query execution begins.</span></span> <span data-ttu-id="4d4d9-108">보다 세밀한 측정이 필요한 경우 `ElapsedMilliseconds` 대신 `ElapsedTicks` 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="4d4d9-109">쿼리 구현을 실험하는 경우 총 실행 시간은 유용한 메트릭이지만 항상 전체적인 내용을 알려주지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-109">The total execution time is a useful metric when you are experimenting with query implementations, but it doesn't always tell the whole story.</span></span> <span data-ttu-id="4d4d9-110">쿼리 스레드 간의 상호 작용 또는 다른 실행 중인 프로세스와 쿼리 스레드의 상호 작용을 자세히 보려면 [동시성 시각화 도우미](/visualstudio/profiling/concurrency-visualizer)를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="4d4d9-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d4d9-111">참조</span><span class="sxs-lookup"><span data-stu-id="4d4d9-111">See also</span></span>

- [<span data-ttu-id="4d4d9-112">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="4d4d9-112">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
