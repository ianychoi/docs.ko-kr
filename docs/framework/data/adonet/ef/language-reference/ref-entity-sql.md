---
description: '자세히 알아보기: 참조 (Entity SQL)'
title: REF(Entity SQL)
ms.date: 03/30/2017
ms.assetid: c5f4cb35-69e9-44cc-b63b-ee38922bbda1
ms.openlocfilehash: 05f87ce8027e8e095722eb13d39f3f13d56f6faa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802062"
---
# <a name="ref-entity-sql"></a><span data-ttu-id="73dde-103">REF(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73dde-103">REF (Entity SQL)</span></span>

<span data-ttu-id="73dde-104">엔터티 인스턴스에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-104">Returns a reference to an entity instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73dde-105">구문</span><span class="sxs-lookup"><span data-stu-id="73dde-105">Syntax</span></span>  
  
```sql  
REF( expression )
```  
  
## <a name="arguments"></a><span data-ttu-id="73dde-106">인수</span><span class="sxs-lookup"><span data-stu-id="73dde-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="73dde-107">엔터티 형식의 인스턴스를 생성하는 모든 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-107">Any valid expression that yields an instance of an entity type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73dde-108">Return Value</span><span class="sxs-lookup"><span data-stu-id="73dde-108">Return Value</span></span>  

 <span data-ttu-id="73dde-109">지정한 엔터티 인스턴스에 대한 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-109">A reference to the specified entity instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73dde-110">설명</span><span class="sxs-lookup"><span data-stu-id="73dde-110">Remarks</span></span>  

 <span data-ttu-id="73dde-111">엔터티 참조는 엔터티 키와 엔터티 집합 이름으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-111">An entity reference consists of the entity key and an entity set name.</span></span> <span data-ttu-id="73dde-112">여러 엔터티 집합이 같은 엔터티 형식을 기반으로 할 수 있으므로 특정 엔터티 키가 여러 엔터티 집합에 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-112">Because different entity sets can be based on the same entity type, a particular entity key can appear in multiple entity sets.</span></span> <span data-ttu-id="73dde-113">하지만 엔터티 참조는 항상 고유합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-113">However, an entity reference is always unique.</span></span> <span data-ttu-id="73dde-114">입력 식이 보관된 엔터티를 나타내는 경우 이 엔터티에 대한 참조가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-114">If the input expression represents a persisted entity, a reference to this entity will be returned.</span></span> <span data-ttu-id="73dde-115">입력 식이 보관된 엔터티가 아닌 경우 Null 참조가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-115">If the input expression is not a persisted entity, a null reference will be returned.</span></span>  
  
 <span data-ttu-id="73dde-116">속성 추출 연산자(.)를 사용하여 엔터티의 속성에 액세스하면 해당 참조가 자동으로 역참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-116">If the property extraction operator (.) is used to access a property of an entity, the reference is automatically dereferenced.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73dde-117">예제</span><span class="sxs-lookup"><span data-stu-id="73dde-117">Example</span></span>  

 <span data-ttu-id="73dde-118">다음 Entity SQL 쿼리는 REF 연산자를 사용하여 입력 엔터티 인수에 대한 참조를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-118">The following Entity SQL query uses the REF operator to return the reference for an input entity argument.</span></span> <span data-ttu-id="73dde-119">속성 추출 연산자(.)를 사용하여 Product 엔터티의 속성에 액세스하고 있으므로 같은 쿼리에서 참조를 역참조합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-119">The same query dereferences the reference because we are using a property extraction operation (.) to access a property of the Product entity.</span></span> <span data-ttu-id="73dde-120">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-120">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73dde-121">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="73dde-121">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73dde-122">[방법: PrimitiveType 결과를 반환 하는 쿼리 실행](../how-to-execute-a-query-that-returns-primitivetype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-122">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="73dde-123">다음 쿼리를 `ExecutePrimitiveTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="73dde-123">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#REF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#ref)]  
  
## <a name="see-also"></a><span data-ttu-id="73dde-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="73dde-124">See also</span></span>

- [<span data-ttu-id="73dde-125">DEREF</span><span class="sxs-lookup"><span data-stu-id="73dde-125">DEREF</span></span>](deref-entity-sql.md)
- [<span data-ttu-id="73dde-126">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="73dde-126">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="73dde-127">KEY</span><span class="sxs-lookup"><span data-stu-id="73dde-127">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="73dde-128">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="73dde-128">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="73dde-129">형식 정의</span><span class="sxs-lookup"><span data-stu-id="73dde-129">Type Definitions</span></span>](type-definitions-entity-sql.md)
