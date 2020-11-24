---
title: '방법: 정적 분할을 위한 파티셔너 구현'
ms.date: 03/30/2017
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 1593f1bc3c17f162b20f8bd9f645d51393f2198c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817135"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="17b89-102">방법: 정적 분할을 위한 파티셔너 구현</span><span class="sxs-lookup"><span data-stu-id="17b89-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="17b89-103">다음 예제에서는 정적 파티셔닝을 수행하는 PLINQ에 대해 단순한 사용자 지정 파티셔너를 구현하는 한 가지 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="17b89-104">파티셔너는 동적 파티션을 지원하지 않으므로 <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="17b89-105">이 특정 파티셔너는 각 요소로 인해 처리 시간이 늘어나는 데이터 소스의 기본 범위 파티셔너에 대해 가속을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17b89-106">예제</span><span class="sxs-lookup"><span data-stu-id="17b89-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="17b89-107">이 예제의 파티션은 각 요소의 처리 시간이 선형으로 증가할 것이라는 가정을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="17b89-108">실제로는 처리 시간을 이 방법으로 예측하기 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="17b89-109">특정 데이터 소스와 함께 정적 파티셔너를 사용하는 경우 소스에 대한 파티셔닝 수식을 최적화하거나 로드 밸런싱 논리를 추가하거나 [방법: 동적 파티션 구현](how-to-implement-dynamic-partitions.md)에 설명된 청크 파티셔닝 접근 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="17b89-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17b89-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="17b89-110">See also</span></span>

- [<span data-ttu-id="17b89-111">PLINQ 및 TPL에 대한 사용자 지정 파티셔너</span><span class="sxs-lookup"><span data-stu-id="17b89-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
