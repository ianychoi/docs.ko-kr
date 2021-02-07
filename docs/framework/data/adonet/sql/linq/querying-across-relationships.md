---
description: '자세히 알아보기: 관계 간 쿼리'
title: 관계 간 쿼리
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 297878d0-685b-4c01-b2e0-9d731b7322bc
ms.openlocfilehash: a29a24b21cc486f59ae7535db0e5f97831249ee0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695257"
---
# <a name="querying-across-relationships"></a><span data-ttu-id="bfb76-103">관계 간 쿼리</span><span class="sxs-lookup"><span data-stu-id="bfb76-103">Querying Across Relationships</span></span>

<span data-ttu-id="bfb76-104">클래스 정의에서 다른 개체 또는 다른 개체의 컬렉션에 대한 참조는 데이터베이스의 외래 키 관계에 직접적으로 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-104">References to other objects or collections of other objects in your class definitions directly correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="bfb76-105">점 표기법을 사용하여 쿼리할 때 이러한 관계를 사용하여 관계 속성에 액세스하고 한 개체에서 다른 개체로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-105">You can use these relationships when you query by using dot notation to access the relationship properties and navigate from one object to another.</span></span> <span data-ttu-id="bfb76-106">이러한 액세스 작업은 해당 SQL에서 더 복잡한 조인이나 연관된 하위 쿼리로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-106">These access operations translate to more complex joins or correlated subqueries in the equivalent SQL.</span></span>  
  
 <span data-ttu-id="bfb76-107">예를 들어 다음 쿼리는 런던에 있는 고객의 주문으로만 결과를 제한하기 위한 방법으로 주문에서 고객으로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-107">For example, the following query navigates from orders to customers as a way to restrict the results to only those orders for customers located in London.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#3)]
 [!code-vb[DLinqQueryConcepts#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#3)]  
  
 <span data-ttu-id="bfb76-108">관계 속성이 존재 하지 않는 경우 다음 코드와 같이 SQL 쿼리에서 수행 하는 것과 마찬가지로 *조인* 으로 수동으로 써야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-108">If relationship properties did not exist you would have to write them manually as *joins*, just as you would do in a SQL query, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#4)]
 [!code-vb[DLinqQueryConcepts#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#4)]  
  
 <span data-ttu-id="bfb76-109">*Relationship* 속성을 사용 하 여이 특정 관계를 한 번에 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-109">You can use the *relationship* property to define this particular relationship one time.</span></span> <span data-ttu-id="bfb76-110">더 편리한 점 구문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-110">You can then use the more convenient dot syntax.</span></span> <span data-ttu-id="bfb76-111">그러나 관계 속성이 존재하는 더 중요한 이유는 도메인 관련 개체 모델이 일반적으로 계층 구조나 그래프로 정의되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-111">But relationship properties exist more importantly because domain-specific object models are typically defined as hierarchies or graphs.</span></span> <span data-ttu-id="bfb76-112">사용자가 프로그래밍하는 개체는 다른 개체에 대한 참조를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-112">The objects that you program against have references to other objects.</span></span> <span data-ttu-id="bfb76-113">운이 좋다면 개체 간의 관계와 데이터베이스의 외래 키 스타일 관계가 일치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-113">It is only a happy coincidence that object-to-object relationships correspond to foreign-key-styled relationships in databases.</span></span> <span data-ttu-id="bfb76-114">그런 다음 속성 액세스를 통해 조인을 편리하게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-114">Property access then provides a convenient way to write joins.</span></span>  
  
 <span data-ttu-id="bfb76-115">이와 관련하여 관계 속성은 쿼리 자체의 일부보다는 쿼리의 결과 측면에서 더 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-115">With regard to this, relationship properties are more important on the results side of a query than as part of the query itself.</span></span> <span data-ttu-id="bfb76-116">쿼리에서 특정 고객에 대한 데이터를 검색한 후 클래스 정의에서는 고객이 주문을 갖고 있다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-116">After the query has retrieved data about a particular customer, the class definition indicates that customers have orders.</span></span> <span data-ttu-id="bfb76-117">즉, 특정 고객의 `Orders` 속성은 해당 고객의 모든 주문으로 채워지는 컬렉션으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-117">In other words, you expect the `Orders` property of a particular customer to be a collection that is populated with all the orders from that customer.</span></span> <span data-ttu-id="bfb76-118">실제로 이 방식으로 클래스를 정의하여 계약이 선언됩니다</span><span class="sxs-lookup"><span data-stu-id="bfb76-118">That is in fact the contract you declared by defining the classes in this manner.</span></span> <span data-ttu-id="bfb76-119">쿼리가 주문을 요청하지 않은 경우에도 주문을 보게 될 것입니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-119">You expect to see the orders there even if the query did not request orders.</span></span> <span data-ttu-id="bfb76-120">또한 개체 모델은 즉시 사용 가능한 관련 개체가 있는 데이터베이스의 메모리 내 확장이라는 가정을 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-120">You expect your object model to maintain an illusion that it is an in-memory extension of the database with related objects immediately available.</span></span>  
  
 <span data-ttu-id="bfb76-121">이제 관계가 존재하므로 클래스에 정의된 관계 속성을 참조하여 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-121">Now that you have relationships, you can write queries by referring to the relationship properties defined in your classes.</span></span> <span data-ttu-id="bfb76-122">이러한 관계 참조는 데이터베이스의 외래 키 관계에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-122">These relationship references correspond to foreign-key relationships in the database.</span></span> <span data-ttu-id="bfb76-123">이러한 관계를 사용하는 작업은 해당 SQL에서 더 복잡한 조인으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-123">Operations that use these relationships translate to more complex joins in the equivalent SQL.</span></span> <span data-ttu-id="bfb76-124"><xref:System.Data.Linq.Mapping.AssociationAttribute> 특성을 사용하여 관계를 정의한 경우 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 명시적 조인을 코딩할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-124">As long as you have defined a relationship (using the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute), you do not have to code an explicit join in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 <span data-ttu-id="bfb76-125">이 환상을 유지 하기 위해는 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *지연 된 로드* 라는 기법을 구현 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-125">To help maintain this illusion, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] implements a technique called *deferred loading*.</span></span> <span data-ttu-id="bfb76-126">자세한 내용은 [지연 된 로드 및 즉시 로드](deferred-versus-immediate-loading.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bfb76-126">For more information, see [Deferred versus Immediate Loading](deferred-versus-immediate-loading.md).</span></span>  
  
 <span data-ttu-id="bfb76-127">다음 SQL 쿼리를 고려 하 여 쌍 목록을 프로젝션 합니다 `CustomerID` - `OrderID` .</span><span class="sxs-lookup"><span data-stu-id="bfb76-127">Consider the following SQL query to project a list of `CustomerID`-`OrderID` pairs:</span></span>  
  
```sql
SELECT t0.CustomerID, t1.OrderID  
FROM   Customers AS t0 INNER JOIN  
          Orders AS t1 ON t0.CustomerID = t1.CustomerID  
WHERE  (t0.City = @p0)  
```  
  
 <span data-ttu-id="bfb76-128">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]을 사용하여 동일한 결과를 얻으려면 이미 `Orders` 클래스에 있는 `Customer` 속성 참조를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-128">To obtain the same results by using [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you use the `Orders` property reference already existing in the `Customer` class.</span></span> <span data-ttu-id="bfb76-129">`Orders`이 참조는 `CustomerID` - `OrderID` 다음 코드에서와 같이 쿼리를 실행 하 고 쌍을 프로젝션 하는 데 필요한 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-129">The `Orders` reference provides the necessary information to execute the query and project the `CustomerID`-`OrderID` pairs, as in the following code:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#5)]
 [!code-vb[DLinqQueryConcepts#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#5)]  
  
 <span data-ttu-id="bfb76-130">반대로 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-130">You can also do the reverse.</span></span> <span data-ttu-id="bfb76-131">즉, `Orders`를 쿼리하고 해당 `Customer` 관계 참조를 사용하여 연관된 `Customer` 개체에 대한 정보에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-131">That is, you can query `Orders` and use its `Customer` relationship reference to access information about the associated `Customer` object.</span></span> <span data-ttu-id="bfb76-132">다음 코드는 이전과 동일한 쌍을 프로젝션 `CustomerID` - `OrderID` 하지만 이번 `Orders` 에는 대신 쿼리 `Customers` 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-132">The following code projects the same `CustomerID`-`OrderID` pairs as before, but this time by querying `Orders` instead of `Customers`.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#6)]
 [!code-vb[DLinqQueryConcepts#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="bfb76-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfb76-133">See also</span></span>

- [<span data-ttu-id="bfb76-134">쿼리 개념</span><span class="sxs-lookup"><span data-stu-id="bfb76-134">Query Concepts</span></span>](query-concepts.md)
