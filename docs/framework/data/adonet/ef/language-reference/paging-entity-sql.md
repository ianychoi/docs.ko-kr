---
description: '자세한 정보: 페이징 (Entity SQL)'
title: 페이징(Entity SQL)
ms.date: 03/30/2017
ms.assetid: ba4f334d-03e5-4a7b-9d42-628f4639b9a2
ms.openlocfilehash: c32474b772be359dbf2ffd46e5489cc0b4b2abb8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791857"
---
# <a name="paging-entity-sql"></a><span data-ttu-id="a59a9-103">페이징(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a59a9-103">Paging (Entity SQL)</span></span>

<span data-ttu-id="a59a9-104">[ORDER by](order-by-entity-sql.md) 절의 [SKIP](skip-entity-sql.md) 및 [LIMIT](limit-entity-sql.md) 하위 절을 사용 하 여 물리적 페이징을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-104">Physical paging can be performed by using the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="a59a9-105">결정적인 방법으로 물리적 페이징을 수행하려면 SKIP과 LIMIT를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-105">To perform physical paging deterministically, you should use SKIP and LIMIT.</span></span> <span data-ttu-id="a59a9-106">결과의 행 수를 명확 하지 않은 방식으로 제한 하려는 경우 [TOP](top-entity-sql.md)을 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-106">If you only want to restrict the number of rows in the result in a non-deterministic way, you should use [TOP](top-entity-sql.md).</span></span> <span data-ttu-id="a59a9-107">TOP과 SKIP/LIMIT는 함께 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-107">TOP and SKIP/LIMIT are mutually exclusive.</span></span>  
  
## <a name="top-overview"></a><span data-ttu-id="a59a9-108">TOP 개요</span><span class="sxs-lookup"><span data-stu-id="a59a9-108">TOP Overview</span></span>  

 <span data-ttu-id="a59a9-109">SELECT 절에는 선택적인 TOP 하위 절과 선택적인 ALL/DISTINCT 한정자를 차례로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-109">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="a59a9-110">TOP 하위 절은 쿼리 결과에 첫 번째 행 집합만 반환되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-110">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span> <span data-ttu-id="a59a9-111">자세한 내용은 [TOP](top-entity-sql.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a59a9-111">For more information, see [TOP](top-entity-sql.md).</span></span>  
  
## <a name="skip-and-limit-overview"></a><span data-ttu-id="a59a9-112">SKIP 및 LIMIT 개요</span><span class="sxs-lookup"><span data-stu-id="a59a9-112">SKIP And LIMIT Overview</span></span>  

 <span data-ttu-id="a59a9-113">SKIP과 LIMIT는 ORDER BY 절의 일부입니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-113">SKIP and LIMIT are part of the ORDER BY clause.</span></span> <span data-ttu-id="a59a9-114">SKIP 식 하위 절이 ORDER BY 절에 있으면 결과는 정렬 기준에 따라 정렬되고 SKIP 식 바로 뒤에 있는 행에서 시작하는 행이 결과 집합에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-114">If a SKIP expression sub-clause is present in a ORDER BY clause, the results will be sorted according to the sort specification and the result set will include row(s) starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="a59a9-115">예를 들어, SKIP 5를 사용하면 처음 다섯 개의 행을 건너뛰고 여섯 번째 행부터 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-115">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span> <span data-ttu-id="a59a9-116">LIMIT 식 하위 절이 ORDER BY 절에 있으면 쿼리는 정렬 지정에 따라 정렬되고 결과 행의 수는 LIMIT 식으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-116">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="a59a9-117">예를 들어, LIMIT 5는 결과 집합을 다섯 개의 인스턴스 또는 행으로 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-117">For instance, LIMIT 5 will restrict the result set to five instances or rows.</span></span> <span data-ttu-id="a59a9-118">SKIP과 LIMIT를 반드시 함께 사용해야 하는 것은 아니므로 ORDER BY 절에 SKIP과 LIMIT 중 하나만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a59a9-118">SKIP and LIMIT do not have to be used together; you can use just SKIP or just LIMIT with ORDER BY clause.</span></span> <span data-ttu-id="a59a9-119">자세한 내용은 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a59a9-119">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="a59a9-120">킵</span><span class="sxs-lookup"><span data-stu-id="a59a9-120">SKIP</span></span>](skip-entity-sql.md)  
  
- [<span data-ttu-id="a59a9-121">제한</span><span class="sxs-lookup"><span data-stu-id="a59a9-121">LIMIT</span></span>](limit-entity-sql.md)  
  
- [<span data-ttu-id="a59a9-122">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="a59a9-122">ORDER BY</span></span>](order-by-entity-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="a59a9-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a59a9-123">See also</span></span>

- [<span data-ttu-id="a59a9-124">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="a59a9-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="a59a9-125">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="a59a9-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
- <span data-ttu-id="a59a9-126">[방법: 쿼리 결과를 통해 페이징](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a59a9-126">[How to: Page Through Query Results](/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
