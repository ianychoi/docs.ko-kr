---
title: '방법: PLINQ 쿼리의 순서 제어'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: 88f19092b06e4dece202e880287bdb95e04d2f2d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817109"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="1c83b-102">방법: PLINQ 쿼리의 순서 제어</span><span class="sxs-lookup"><span data-stu-id="1c83b-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="1c83b-103">다음 예제는 <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 확장 메서드를 사용하여 PLINQ 쿼리에서 순서를 제어하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="1c83b-104">이 예제는 주로 사용법을 보여 주기 위해 제공되며 동일한 순차적 LINQ to Objects 쿼리보다 빠르게 실행되거나 실행되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c83b-105">예제</span><span class="sxs-lookup"><span data-stu-id="1c83b-105">Example</span></span>  
 <span data-ttu-id="1c83b-106">다음 예제에서는 소스 시퀀스의 순서를 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="1c83b-107">때때로 이 작업이 필요합니다. 예를 들어 일부 쿼리 연산자에는 올바른 결과를 생성하려면 순서가 지정된 소스 시퀀스가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="1c83b-108">예제</span><span class="sxs-lookup"><span data-stu-id="1c83b-108">Example</span></span>  
 <span data-ttu-id="1c83b-109">다음 예제는 소스 시퀀스의 순서가 지정되어야 할 수 있는 일부 쿼리 연산자를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="1c83b-110">이러한 연산자는 순서가 지정되지 않은 시퀀스에서 작동하지만 예기치 않은 결과를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="1c83b-111">이 메서드를 실행하려면 [PLINQ 데이터 샘플](plinq-data-sample.md) 프로젝트의 PLINQDataSample 클래스에 붙여넣고 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c83b-112">예제</span><span class="sxs-lookup"><span data-stu-id="1c83b-112">Example</span></span>  
 <span data-ttu-id="1c83b-113">다음 예제는 쿼리의 첫 번째 부분에 대한 순서를 유지하고, 순서를 제거하여 조인 절의 성능을 향상한 다음, 마지막 결과 시퀀스에 순서를 다시 적용하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="1c83b-114">이 메서드를 실행하려면 [PLINQ 데이터 샘플](plinq-data-sample.md) 프로젝트의 PLINQDataSample 클래스에 붙여넣고 F5 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c83b-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c83b-115">참조</span><span class="sxs-lookup"><span data-stu-id="1c83b-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="1c83b-116">PLINQ(병렬 LINQ)</span><span class="sxs-lookup"><span data-stu-id="1c83b-116">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
