---
description: '자세한 정보: 방법: DataContext 수준에서 필터링'
title: '방법: DataContext 수준 필터링'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 15505cd7-0df2-427a-9f86-e0f96f60ee2e
ms.openlocfilehash: ffb287ac1ef8cc19044ec3d519e745f905fe213d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785980"
---
# <a name="how-to-filter-at-the-datacontext-level"></a><span data-ttu-id="8d988-103">방법: DataContext 수준 필터링</span><span class="sxs-lookup"><span data-stu-id="8d988-103">How to: Filter at the DataContext Level</span></span>

<span data-ttu-id="8d988-104">`EntitySets` 수준에서 `DataContext`를 필터링할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d988-104">You can filter `EntitySets` at the `DataContext` level.</span></span> <span data-ttu-id="8d988-105">이러한 필터는 <xref:System.Data.Linq.DataContext> 인스턴스로 수행되는 모든 쿼리에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d988-105">Such filters apply to all queries done with that <xref:System.Data.Linq.DataContext> instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d988-106">예제</span><span class="sxs-lookup"><span data-stu-id="8d988-106">Example</span></span>  

 <span data-ttu-id="8d988-107">다음 예제에서는 <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> 기준으로 고객의 미리 로드된 주문을 필터링하기 위해 `ShippedDate`가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d988-107">In the following example, <xref:System.Data.Linq.DataLoadOptions.AssociateWith%28System.Linq.Expressions.LambdaExpression%29?displayProperty=nameWithType> is used to filter the pre-loaded orders for customers by `ShippedDate`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#10](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#10)]
 [!code-vb[DLinqQueryConcepts#10](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="8d988-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d988-108">See also</span></span>

- [<span data-ttu-id="8d988-109">쿼리 개념</span><span class="sxs-lookup"><span data-stu-id="8d988-109">Query Concepts</span></span>](query-concepts.md)
