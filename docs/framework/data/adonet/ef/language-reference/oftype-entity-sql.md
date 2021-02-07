---
description: '자세한 정보: OFTYPE (Entity SQL)'
title: OFTYPE(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 6d259ca7-bbf0-40f8-a154-181d25c0d67e
ms.openlocfilehash: d916ea4487fcc7a21f5fb62aa7e6f8a23d73fed2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739341"
---
# <a name="oftype-entity-sql"></a><span data-ttu-id="4cc8b-103">OFTYPE(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4cc8b-103">OFTYPE (Entity SQL)</span></span>

<span data-ttu-id="4cc8b-104">쿼리 식에서 특정 형식을 가진 개체 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-104">Returns a collection of objects from a query expression that is of a specific type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cc8b-105">구문</span><span class="sxs-lookup"><span data-stu-id="4cc8b-105">Syntax</span></span>  
  
```sql  
OFTYPE ( expression, [ONLY] test_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cc8b-106">인수</span><span class="sxs-lookup"><span data-stu-id="4cc8b-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4cc8b-107">개체 컬렉션을 반환하는 모든 유효한 쿼리 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-107">Any valid query expression that returns a collection of objects.</span></span>  
  
 `test_type`  
 <span data-ttu-id="4cc8b-108">`expression` 에서 반환된 각 개체를 테스트할 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-108">The type to test each object returned by `expression` against.</span></span> <span data-ttu-id="4cc8b-109">형식은 네임스페이스로 한정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-109">The type must be qualified by a namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4cc8b-110">Return Value</span><span class="sxs-lookup"><span data-stu-id="4cc8b-110">Return Value</span></span>  

 <span data-ttu-id="4cc8b-111">`test_type`형식이거나 `test_type`의 기본 형식 또는 파생 형식인 개체 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-111">A collection of objects that are of type `test_type`, or a base type or derived type of `test_type`.</span></span> <span data-ttu-id="4cc8b-112">ONLY를 지정하면 `test_type` 인스턴스나 빈 컬렉션만 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-112">If ONLY is specified, only instances of the `test_type` or an empty collection will be returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cc8b-113">설명</span><span class="sxs-lookup"><span data-stu-id="4cc8b-113">Remarks</span></span>  

 <span data-ttu-id="4cc8b-114">`OFTYPE` 식은 컬렉션의 각 요소에 대해 형식 테스트를 수행하기 위해 실행되는 형식 식을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-114">An `OFTYPE` expression specifies a type expression that is issued to perform a type test against each element of a collection.</span></span>  <span data-ttu-id="4cc8b-115">`OFTYPE` 식은 해당 형식이나 하위 형식에 해당하는 요소만 포함하는 지정된 형식의 새 컬렉션을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-115">The `OFTYPE` expression produces a new collection of the specified type containing only those elements that were either equivalent to that type or a sub-type of it.</span></span>  
  
 <span data-ttu-id="4cc8b-116">`OFTYPE` 식은 다음 쿼리 식의 단축된 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-116">An `OFTYPE` expression is an abbreviation of the following query expression:</span></span>  
  
```sql  
select value treat(t as T) from ts as t where t is of (T)  
```  
  
 <span data-ttu-id="4cc8b-117">Manager가 Employee의 하위 형식인 경우 다음 식은 직원 컬렉션에 있는 관리자만으로 구성된 컬렉션을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-117">Given that a Manager is a subtype of Employee, the following expression produces a collection of only managers from a collection of employees:</span></span>  
  
```sql  
OfType(employees, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="4cc8b-118">형식 필터를 사용하여 컬렉션을 캐스팅할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-118">It is also possible to up cast a collection using the type filter:</span></span>  
  
```sql
OfType(executives, NamespaceName.Manager)  
```  
  
 <span data-ttu-id="4cc8b-119">모든 임원은 관리자이므로 현재 컬렉션이 관리자 컬렉션으로 형식화된 경우에도 결과 컬렉션에 원래 임원이 모두 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-119">Since all executives are managers, the resulting collection still contains all the original executives, though the collection is now typed as a collection of managers.</span></span>  
  
 <span data-ttu-id="4cc8b-120">다음 표에서는 일부 패턴에 대한 `OFTYPE` 연산자의 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-120">The following table shows the behavior of the `OFTYPE` operator over some patterns.</span></span> <span data-ttu-id="4cc8b-121">공급자가 호출되기 전에 클라이언트 쪽에서 모든 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-121">All exceptions are thrown from the client side before the provider is invoked:</span></span>  
  
|<span data-ttu-id="4cc8b-122">무늬</span><span class="sxs-lookup"><span data-stu-id="4cc8b-122">Pattern</span></span>|<span data-ttu-id="4cc8b-123">동작</span><span class="sxs-lookup"><span data-stu-id="4cc8b-123">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="4cc8b-124">OFTYPE(Collection(EntityType), EntityType)</span><span class="sxs-lookup"><span data-stu-id="4cc8b-124">OFTYPE(Collection(EntityType), EntityType)</span></span>|<span data-ttu-id="4cc8b-125">Collection(EntityType)</span><span class="sxs-lookup"><span data-stu-id="4cc8b-125">Collection(EntityType)</span></span>|  
|<span data-ttu-id="4cc8b-126">OFTYPE(Collection(ComplexType), ComplexType)</span><span class="sxs-lookup"><span data-stu-id="4cc8b-126">OFTYPE(Collection(ComplexType), ComplexType)</span></span>|<span data-ttu-id="4cc8b-127">되거나</span><span class="sxs-lookup"><span data-stu-id="4cc8b-127">Throws</span></span>|  
|<span data-ttu-id="4cc8b-128">OFTYPE(Collection(RowType), RowType)</span><span class="sxs-lookup"><span data-stu-id="4cc8b-128">OFTYPE(Collection(RowType), RowType)</span></span>|<span data-ttu-id="4cc8b-129">되거나</span><span class="sxs-lookup"><span data-stu-id="4cc8b-129">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4cc8b-130">예제</span><span class="sxs-lookup"><span data-stu-id="4cc8b-130">Example</span></span>  

 <span data-ttu-id="4cc8b-131">다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 OFTYPE 연산자를 사용하여 Course 개체 컬렉션에서 OnsiteCourse 개체 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-131">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the OFTYPE operator to return a collection of OnsiteCourse objects from a collection of Course objects.</span></span> <span data-ttu-id="4cc8b-132">쿼리는 [School 모델](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100))을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4cc8b-132">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#OFTYPE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#oftype)]  
  
## <a name="see-also"></a><span data-ttu-id="4cc8b-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4cc8b-133">See also</span></span>

- [<span data-ttu-id="4cc8b-134">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="4cc8b-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
