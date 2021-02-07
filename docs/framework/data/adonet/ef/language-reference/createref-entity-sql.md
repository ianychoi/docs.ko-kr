---
description: '자세히 알아보기: CREATEREF (Entity SQL)'
title: CREATEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 489828cf-a335-4449-9360-b0d92eec5481
ms.openlocfilehash: c4e96f97bd3587e50b34f6cbd63c5ae9ed8d94ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724780"
---
# <a name="createref-entity-sql"></a><span data-ttu-id="f79a2-103">CREATEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f79a2-103">CREATEREF (Entity SQL)</span></span>

<span data-ttu-id="f79a2-104">entityset의 엔터티에 대한 참조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-104">Fabricates references to an entity in an entityset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f79a2-105">구문</span><span class="sxs-lookup"><span data-stu-id="f79a2-105">Syntax</span></span>  
  
```sql  
CreateRef(entityset_identifier, row_typed_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f79a2-106">인수</span><span class="sxs-lookup"><span data-stu-id="f79a2-106">Arguments</span></span>  

 `entityset_identifier`  
 <span data-ttu-id="f79a2-107">문자열 리터럴이 아니라 entityset 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-107">The entityset identifier, not a string literal.</span></span>  
  
 `row_typed_expression`  
 <span data-ttu-id="f79a2-108">엔터티 형식의 키 속성에 해당하는 행 형식의 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-108">A row-typed expression that corresponds to the key properties of the entity type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f79a2-109">설명</span><span class="sxs-lookup"><span data-stu-id="f79a2-109">Remarks</span></span>  

 <span data-ttu-id="f79a2-110">`row_typed_expression` 은 엔터티의 키 유형과 구조적으로 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-110">`row_typed_expression` must be structurally equivalent to the key type for the entity.</span></span> <span data-ttu-id="f79a2-111">다시 말해서, 필드의 개수와 형식 및 배열 순서가 엔터티 키와 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-111">That is, it must have the same number and types of fields in the same order as the entity keys.</span></span>  
  
 <span data-ttu-id="f79a2-112">아래 예제에서 Order와 BadOrder는 모두 Order 형식의 entityset이며, Id는 Order의 단일 키 속성인 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-112">In the example below, Orders and BadOrders are both entitysets of type Order, and Id is assumed to be the single key property of Order.</span></span> <span data-ttu-id="f79a2-113">예제에서는 BadOrder의 엔터티에 대한 참조를 생성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-113">The example illustrates how we may produce a reference to an entity in BadOrders.</span></span> <span data-ttu-id="f79a2-114">이 참조는 현수 참조일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-114">Note that the reference may be dangling.</span></span>  <span data-ttu-id="f79a2-115">다시 말해서, 참조가 특정 엔터티를 실제로 나타내지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-115">That is, the reference may not actually identify a specific entity.</span></span> <span data-ttu-id="f79a2-116">이런 경우 해당 참조에 대해 `DEREF` 작업을 수행하면 null이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-116">In those cases, a `DEREF` operation on that reference returns a null.</span></span>  
  
```sql  
SELECT CreateRef(LOB.BadOrders, row(o.Id))
FROM LOB.Orders AS o
```  
  
## <a name="example"></a><span data-ttu-id="f79a2-117">예제</span><span class="sxs-lookup"><span data-stu-id="f79a2-117">Example</span></span>  

 <span data-ttu-id="f79a2-118">다음 Entity SQL 쿼리는 CREATEREF 연산자를 사용하여 엔터티 집합 내의 엔터티에 대한 참조를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-118">The following Entity SQL query uses the CREATEREF operator to fabricate references to an entity in an entity set.</span></span> <span data-ttu-id="f79a2-119">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-119">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f79a2-120">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="f79a2-120">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f79a2-121">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-121">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f79a2-122">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="f79a2-122">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CREATEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#createref)]  
  
## <a name="see-also"></a><span data-ttu-id="f79a2-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f79a2-123">See also</span></span>

- [<span data-ttu-id="f79a2-124">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="f79a2-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f79a2-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="f79a2-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="f79a2-126">KEY</span><span class="sxs-lookup"><span data-stu-id="f79a2-126">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="f79a2-127">행위자</span><span class="sxs-lookup"><span data-stu-id="f79a2-127">REF</span></span>](ref-entity-sql.md)
