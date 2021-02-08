---
description: '자세한 정보: 방법: 검색 되는 관련 데이터의 양 제어'
title: '방법: 관련 데이터의 검색 양 제어'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: becf1282d18d5c630da3e3be27c62ebae404d940
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786045"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="dfaf0-103">방법: 관련 데이터의 검색 양 제어</span><span class="sxs-lookup"><span data-stu-id="dfaf0-103">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="dfaf0-104"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> 메서드를 사용하여 동시에 검색되어야 하는 주 대상과 관련된 데이터를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-104">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="dfaf0-105">예를 들어 고객 주문에 대한 정보가 필요한 경우 <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A>를 사용하여 주문 정보와 고객 정보가 검색되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-105">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="dfaf0-106">이 접근 방법은 두 가지 정보에 대한 데이터베이스에서 원트립만의 결과입니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-106">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfaf0-107">고객을 대상으로 할 경우 주문을 검색하는 것과 같이 외적을 하나의 큰 프로젝션처럼 검색하여 쿼리의 주 대상과 관련된 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-107">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="dfaf0-108">그러나 이러한 방법에는 종종 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-108">But this approach often has disadvantages.</span></span> <span data-ttu-id="dfaf0-109">예를 들어 결과는 엔터티가 아니라 프로젝션이기에 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 변경되고 유지될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-109">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="dfaf0-110">원하지 않는 많은 데이터가 검색될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-110">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfaf0-111">예제</span><span class="sxs-lookup"><span data-stu-id="dfaf0-111">Example</span></span>  

 <span data-ttu-id="dfaf0-112">다음 예제에서는 `Orders` `Customers` 쿼리가 실행 될 때 런던에 있는 모든에 대 한 모든가 검색 됩니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-112">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="dfaf0-113">따라서 개체의 속성에 대 한 연속 액세스는 `Orders` `Customer` 새 데이터베이스 쿼리를 트리거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfaf0-113">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="dfaf0-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="dfaf0-114">See also</span></span>

- [<span data-ttu-id="dfaf0-115">데이터베이스 쿼리</span><span class="sxs-lookup"><span data-stu-id="dfaf0-115">Querying the Database</span></span>](querying-the-database.md)
