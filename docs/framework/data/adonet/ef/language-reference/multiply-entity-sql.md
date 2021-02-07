---
description: '다음에 대 한 자세한 정보: * (곱하기) (Entity SQL)'
title: '* 곱하기 (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 92606e5f9e4646ab651d0e07095e6f419401188f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696622"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="4bbed-103">\* (곱하기) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4bbed-103">\* (Multiply) (Entity SQL)</span></span>

<span data-ttu-id="4bbed-104">두 식을 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-104">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bbed-105">구문</span><span class="sxs-lookup"><span data-stu-id="4bbed-105">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4bbed-106">인수</span><span class="sxs-lookup"><span data-stu-id="4bbed-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="4bbed-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4bbed-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="4bbed-108">Result Types</span></span>  

 <span data-ttu-id="4bbed-109">두 인수에 대해 암시적 형식 승격을 수행한 결과 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-109">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="4bbed-110">암시적 형식 승격에 대 한 자세한 내용은 [형식 시스템](type-system-entity-sql.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="4bbed-110">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bbed-111">예제</span><span class="sxs-lookup"><span data-stu-id="4bbed-111">Example</span></span>  

 <span data-ttu-id="4bbed-112">다음 Entity SQL 쿼리에서는 \* 산술 연산자를 사용하여 두 숫자를 곱합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-112">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="4bbed-113">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-113">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4bbed-114">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="4bbed-114">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4bbed-115">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-115">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4bbed-116">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="4bbed-116">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="4bbed-117">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4bbed-117">See also</span></span>

- [<span data-ttu-id="4bbed-118">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="4bbed-118">Entity SQL Reference</span></span>](entity-sql-reference.md)
