---
description: '자세히 알아보기: 위쪽 (Entity SQL)'
title: TOP(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 51e4ce53cff4b47f6f57b6b856ccb09b38e639cf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673442"
---
# <a name="top-entity-sql"></a><span data-ttu-id="2a4e2-103">TOP(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2a4e2-103">TOP (Entity SQL)</span></span>

<span data-ttu-id="2a4e2-104">SELECT 절에는 선택적인 TOP 하위 절과 선택적인 ALL/DISTINCT 한정자를 차례로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-104">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="2a4e2-105">TOP 하위 절은 쿼리 결과에 첫 번째 행 집합만 반환되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-105">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a4e2-106">구문</span><span class="sxs-lookup"><span data-stu-id="2a4e2-106">Syntax</span></span>

```sql
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="2a4e2-107">인수</span><span class="sxs-lookup"><span data-stu-id="2a4e2-107">Arguments</span></span>

<span data-ttu-id="2a4e2-108">`n` 반환할 행 수를 지정 하는 숫자 식입니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-108">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="2a4e2-109">`n` 은 단일 숫자 리터럴 또는 단일 매개 변수일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-109">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a4e2-110">설명</span><span class="sxs-lookup"><span data-stu-id="2a4e2-110">Remarks</span></span>

<span data-ttu-id="2a4e2-111">TOP 식은 단일 숫자 리터럴이거나 단일 매개 변수여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-111">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="2a4e2-112">상수 리터럴이 사용되는 경우, 리터럴 형식은 Edm.Int64(바이트. int16, int32, int64이거나 Edm.Int64로 확장 가능한 형식으로 매핑되는 모든 공급자 형식)로의 암시적 확장이 가능해야 하며 그 값이 0이거나 0보다 커야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-112">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="2a4e2-113">그렇지 않으면 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-113">Otherwise an exception will be raised.</span></span> <span data-ttu-id="2a4e2-114">매개 변수가 식으로 사용되는 경우에는 매개 변수 형식도 역시 암시적으로 Edm.Int64로 확장할 수 있어야 합니다. 하지만 매개 변수 값은 런타임에 바인딩되므로 컴파일 과정에서 실제 매개 변수 값에 대한 확인은 이루어지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-114">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="2a4e2-115">다음은 상수 TOP 식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-115">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="2a4e2-116">다음은 매개 변수가 있는 TOP 식의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-116">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="2a4e2-117">쿼리가 정렬되지 않는 한 TOP은 결정적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-117">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="2a4e2-118">결정적인 결과가 필요한 경우에는 [ORDER BY](skip-entity-sql.md) 절의 [SKIP](limit-entity-sql.md) 및 [LIMIT](order-by-entity-sql.md) 하위 절을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-118">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="2a4e2-119">TOP과 SKIP/LIMIT는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-119">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="2a4e2-120">예제</span><span class="sxs-lookup"><span data-stu-id="2a4e2-120">Example</span></span>

<span data-ttu-id="2a4e2-121">다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 TOP을 사용하여 쿼리 결과에서 반환할 상위 행 하나를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-121">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="2a4e2-122">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-122">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2a4e2-123">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-123">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="2a4e2-124">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-124">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="2a4e2-125">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="2a4e2-125">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-sql[DP EntityServices Concepts#TOP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#top)]

## <a name="see-also"></a><span data-ttu-id="2a4e2-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2a4e2-126">See also</span></span>

- [<span data-ttu-id="2a4e2-127">SELECT</span><span class="sxs-lookup"><span data-stu-id="2a4e2-127">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="2a4e2-128">킵</span><span class="sxs-lookup"><span data-stu-id="2a4e2-128">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="2a4e2-129">제한</span><span class="sxs-lookup"><span data-stu-id="2a4e2-129">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="2a4e2-130">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="2a4e2-130">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="2a4e2-131">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="2a4e2-131">Entity SQL Reference</span></span>](entity-sql-reference.md)
