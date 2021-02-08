---
description: '자세한 정보: 쿼리 결과'
title: 쿼리 결과
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bcd7b699-4e50-4523-8c33-2f54a103d94e
ms.openlocfilehash: ebdc7929afffc0218ddef7429c53be1decf94772
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802075"
---
# <a name="query-results"></a><span data-ttu-id="4e992-103">쿼리 결과</span><span class="sxs-lookup"><span data-stu-id="4e992-103">Query Results</span></span>

<span data-ttu-id="4e992-104">LINQ to Entities 쿼리가 명령 트리로 변환 되 고 실행 되 면 일반적으로 쿼리 결과가 다음 중 하나로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-104">After a LINQ to Entities query is converted to command trees and executed, the query results are usually returned as one of the following:</span></span>  
  
- <span data-ttu-id="4e992-105">개념적 모델에 있는 0개 이상의 형식화된 엔터티 개체 컬렉션 또는 복합 형식의 프로젝션</span><span class="sxs-lookup"><span data-stu-id="4e992-105">A collection of zero or more typed entity objects or a projection of complex types in the conceptual model.</span></span>  
  
- <span data-ttu-id="4e992-106">개념적 모델에서 지원되는 CLR 형식</span><span class="sxs-lookup"><span data-stu-id="4e992-106">CLR types supported by the conceptual model.</span></span>  
  
- <span data-ttu-id="4e992-107">인라인 컬렉션</span><span class="sxs-lookup"><span data-stu-id="4e992-107">Inline collections.</span></span>  
  
- <span data-ttu-id="4e992-108">익명 형식</span><span class="sxs-lookup"><span data-stu-id="4e992-108">Anonymous types.</span></span>  
  
 <span data-ttu-id="4e992-109">쿼리가 데이터 소스에 대해 실행된 경우 그 결과는 CLR 형식으로 구체화되어 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-109">When the query has executed against the data source, the results are materialized into CLR types and returned to the client.</span></span> <span data-ttu-id="4e992-110">모든 개체 구체화는 Entity Framework에 의해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-110">All object materialization is performed by the Entity Framework.</span></span> <span data-ttu-id="4e992-111">Entity Framework와 CLR 간의 매핑 실패로 인해 오류가 발생하면 개체 구체화 동안 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-111">Any errors that result from an inability to map between the Entity Framework and the CLR will cause exceptions to be thrown during object materialization.</span></span>
  
 <span data-ttu-id="4e992-112">쿼리 실행에서 기본 개념적 모델 유형을 반환 하는 경우 결과는 독립 실행형 이며 Entity Framework에서 분리 된 CLR 형식으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-112">If the query execution returns primitive conceptual model types, the results consist of CLR types that are stand-alone and disconnected from the Entity Framework.</span></span> <span data-ttu-id="4e992-113">이와 달리 쿼리가 형식화된 엔터티 개체 컬렉션을 반환하는 경우(<xref:System.Data.Objects.ObjectQuery%601>로 표현됨), 이러한 형식은 개체 컨텍스트에서 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-113">However, if the query returns a collection of typed entity objects, represented by <xref:System.Data.Objects.ObjectQuery%601>, those types are tracked by the object context.</span></span> <span data-ttu-id="4e992-114">모든 개체 동작 (예: 자식/부모 컬렉션, 변경 내용 추적, 다형성 등)은 Entity Framework에 정의 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-114">All object behavior (such as child/parent collections, change tracking, polymorphism, and so on) are as defined in the Entity Framework.</span></span> <span data-ttu-id="4e992-115">Entity Framework에 정의 된 대로이 기능을 용량에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-115">This functionality can be used in its capacity, as defined in the Entity Framework.</span></span> <span data-ttu-id="4e992-116">자세한 내용은 [개체 작업](../working-with-objects.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4e992-116">For more information, see [Working with Objects](../working-with-objects.md).</span></span>
  
 <span data-ttu-id="4e992-117">쿼리에서 반환된 구조 형식(예: 익명 형식 및 null 허용 복합 형식)의 값은 `null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-117">Struct types returned from queries (such as anonymous types and nullable complex types) can be of `null` value.</span></span> <span data-ttu-id="4e992-118">반환된 엔터티의 <xref:System.Data.Objects.DataClasses.EntityCollection%601> 속성 값 또한 `null`일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-118">An <xref:System.Data.Objects.DataClasses.EntityCollection%601> property of a returned entity can also be of `null` value.</span></span> <span data-ttu-id="4e992-119">이것은 값이 `null`인 엔터티 컬렉션 속성을 프로젝션했기 때문일 수 있습니다. 예를 들면, 요소가 없는 <xref:System.Linq.Queryable.FirstOrDefault%2A>에 대해 <xref:System.Data.Objects.ObjectQuery%601>를 호출하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-119">This can result from projecting the collection property of an entity that is of `null` value, such as calling <xref:System.Linq.Queryable.FirstOrDefault%2A> on an <xref:System.Data.Objects.ObjectQuery%601> that has no elements.</span></span>  
  
 <span data-ttu-id="4e992-120">특정 상황에서는 쿼리가 실행 과정에서 구체화된 결과를 생성하는 것처럼 보일 수도 있지만, 쿼리는 서버에서 실행되며 엔터티 개체가 CLR에서 구체화되는 일은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-120">In certain situations, a query might appear to generate a materialized result during its execution, but the query will be executed on the server and the entity object will never be materialized in the CLR.</span></span> <span data-ttu-id="4e992-121">이런 특징은 개체 구체화의 부작용에 좌우되는 경우 문제가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-121">This can cause problems if you are depending on side effects of object materialization.</span></span>  
  
 <span data-ttu-id="4e992-122">다음 예제에서는 `MyContact` 속성을 가진 사용자 지정 클래스 `LastName`를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-122">The following example contains a custom class, `MyContact`, with a `LastName` property.</span></span> <span data-ttu-id="4e992-123">`LastName` 속성이 설정되면 `count` 변수가 증가합니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-123">When the `LastName` property is set, a `count` variable is incremented.</span></span> <span data-ttu-id="4e992-124">다음 쿼리를 실행하면, 첫 번째 쿼리에서는 `count`가 증가하는 반면, 두 번째 쿼리에서는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-124">If you execute the two following queries, the first query will increment `count` while the second query will not.</span></span> <span data-ttu-id="4e992-125">이것은 두 번째 쿼리의 `LastName` 속성이 결과에서 프로젝션되고 `MyContact` 클래스가 저장소에 대한 쿼리 실행에 필요가 없어서 생성되지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="4e992-125">This is because in the second query the `LastName` property is projected from the results and the `MyContact` class is never created, because it is not required to execute the query on the store.</span></span>  
  
 [!code-csharp[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#materializationsideeffects)]
 [!code-vb[DP L2E Materialization Example#MaterializationSideEffects](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#materializationsideeffects)]  
  
 [!code-csharp[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Materialization Example/CS/Program.cs#mycontactclass)]
 [!code-vb[DP L2E Materialization Example#MyContactClass](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Materialization Example/VB/Module1.vb#mycontactclass)]
