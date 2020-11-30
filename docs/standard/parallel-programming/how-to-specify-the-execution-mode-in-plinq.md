---
title: '방법: PLINQ에 실행 모드 지정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: 725f232337952449cd8569b12f65da75569996df
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722405"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a><span data-ttu-id="5bfc3-102">방법: PLINQ에 실행 모드 지정</span><span class="sxs-lookup"><span data-stu-id="5bfc3-102">How to: Specify the Execution Mode in PLINQ</span></span>

<span data-ttu-id="5bfc3-103">이 예제에서는 PLINQ가 해당 기본 추론을 강제로 바이패스하게 하여 쿼리 모양에 관계없이 쿼리를 병렬 처리하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-103">This example shows how to force PLINQ to bypass its default heuristics and parallelize a query regardless of the query's shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5bfc3-104">이 예제는 사용법을 보여 주기 위한 것이며, 동일한 순차 LINQ to Objects 쿼리보다 빠르게 실행되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-104">This example is intended to demonstrate usage and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="5bfc3-105">속도 향상에 대한 자세한 내용은 [PLINQ의 속도 향상 이해](understanding-speedup-in-plinq.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-105">For more information about speedup, see [Understanding Speedup in PLINQ](understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5bfc3-106">예제</span><span class="sxs-lookup"><span data-stu-id="5bfc3-106">Example</span></span>  

 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 <span data-ttu-id="5bfc3-107">PLINQ는 병렬 처리 기회를 활용하도록 설계됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-107">PLINQ is designed to exploit opportunities for parallelization.</span></span> <span data-ttu-id="5bfc3-108">그러나 일부 쿼리는 병렬 실행을 활용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-108">However, not all queries benefit from parallel execution.</span></span> <span data-ttu-id="5bfc3-109">예를 들어 작업이 거의 없는 단일 사용자 대리자가 쿼리에 포함될 경우 해당 쿼리는 대개 더 빠르게 순차적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-109">For example, when a query contains a single user delegate that does little work, the query will usually run faster sequentially.</span></span> <span data-ttu-id="5bfc3-110">병렬 실행을 구현하는 것과 관련된 오버헤드는 확보된 속도 향상보다 비용이 더 크기 때문에 순차적 실행이 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-110">Sequential execution is faster because the overhead involved in enabling parallelizing execution is more expensive than the speedup that's obtained.</span></span> <span data-ttu-id="5bfc3-111">따라서 PLINQ가 모든 쿼리를 자동으로 병렬 처리하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-111">Therefore, PLINQ does not automatically parallelize every query.</span></span> <span data-ttu-id="5bfc3-112">먼저 쿼리 모양을 확인하고 쿼리를 구성하는 다양한 연산자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-112">It first examines the shape of the query and the various operators that comprise it.</span></span> <span data-ttu-id="5bfc3-113">이 분석에 따라 기본 실행 모드의 PLINQ는 쿼리의 일부 또는 전체를 순차적으로 실행하도록 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-113">Based on this analysis, PLINQ in the default execution mode may decide to execute some or all of the query sequentially.</span></span> <span data-ttu-id="5bfc3-114">그러나 일부 경우에는 PLINQ가 분석에서 확인할 수 있는 것보다 더 많은 쿼리 정보를 사용자가 알고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-114">However, in some cases you may know more about your query than PLINQ is able to determine from its analysis.</span></span> <span data-ttu-id="5bfc3-115">예를 들어 대리자의 비용이 많이 들고 쿼리가 분명히 병렬 처리를 활용할 것이라는 점을 알고 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-115">For example, you may know that a delegate is expensive and that the query will definitely benefit from parallelization.</span></span> <span data-ttu-id="5bfc3-116">이러한 경우에는 <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> 메서드를 사용하고 <xref:System.Linq.ParallelExecutionMode.ForceParallelism>을 지정하여 PLINQ가 항상 쿼리를 병렬로 실행하도록 지시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-116">In such cases, you can use the <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> method and specify the <xref:System.Linq.ParallelExecutionMode.ForceParallelism> value to instruct PLINQ to always run the query as parallel.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5bfc3-117">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="5bfc3-117">Compiling the Code</span></span>  

 <span data-ttu-id="5bfc3-118">이 코드를 잘라내어 [PLINQ 데이터 샘플](plinq-data-sample.md)에 붙여넣고 `Main`에서 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="5bfc3-118">Cut and paste this code into the [PLINQ Data Sample](plinq-data-sample.md) and call the method from `Main`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bfc3-119">참조</span><span class="sxs-lookup"><span data-stu-id="5bfc3-119">See also</span></span>

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [<span data-ttu-id="5bfc3-120">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="5bfc3-120">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
