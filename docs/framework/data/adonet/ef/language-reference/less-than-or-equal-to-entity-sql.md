---
description: '다음에 대 한 자세한 정보: <= (작거나 같음) (Entity SQL)'
title: <= (작거나 같음) (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 7c46da5c-fa09-4d90-adcc-c7e1b769d8e6
ms.openlocfilehash: f720c4ef87cdd0cceea175b1ea70caf5ac6e1deb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748260"
---
# <a name="-less-than-or-equal-to-entity-sql"></a><span data-ttu-id="abe87-103">\<=(보다 작거나 같음)(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="abe87-103">\<= (Less Than or Equal To) (Entity SQL)</span></span>

<span data-ttu-id="abe87-104">두 식을 비교하여 왼쪽 식의 값이 오른쪽 식의 값보다 작거나 같은지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-104">Compares two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe87-105">구문</span><span class="sxs-lookup"><span data-stu-id="abe87-105">Syntax</span></span>  
  
```sql  
expression <= expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="abe87-106">인수</span><span class="sxs-lookup"><span data-stu-id="abe87-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="abe87-107">유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-107">Any valid expression.</span></span> <span data-ttu-id="abe87-108">두 식은 모두 암시적으로 변환 가능한 데이터 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-108">Both expressions must have implicitly convertible data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="abe87-109">결과 형식</span><span class="sxs-lookup"><span data-stu-id="abe87-109">Result Types</span></span>  

 <span data-ttu-id="abe87-110">왼쪽 식의 값이 오른쪽 식의 값보다 작거나 같으면`true` 이고, 그렇지 않으면 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-110">`true` if the left expression has a value less than or equal to the right expression; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abe87-111">예제</span><span class="sxs-lookup"><span data-stu-id="abe87-111">Example</span></span>  

 <span data-ttu-id="abe87-112">다음 Entity SQL 쿼리는 <= 비교 연산자를 통해 두 식을 비교하여 왼쪽 식의 값이 오른쪽 식의 값보다 작거나 같은지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-112">The following Entity SQL query uses <= comparison operator to compare two expressions to determine whether the left expression has a value less than or equal to the right expression.</span></span> <span data-ttu-id="abe87-113">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="abe87-114">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="abe87-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="abe87-115">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="abe87-116">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="abe87-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LESS_OR_EQUALS](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#less_or_equals)]  
  
## <a name="see-also"></a><span data-ttu-id="abe87-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="abe87-117">See also</span></span>

- [<span data-ttu-id="abe87-118">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="abe87-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
