---
description: 자세한 정보:-(음수) (Entity SQL)
title: '- 양수 (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: f3d30ce36b95e44755d148dc06279f67f15b0664
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712885"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="24fdf-103">- (부정)(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="24fdf-103">- (Negative) (Entity SQL)</span></span>

<span data-ttu-id="24fdf-104">숫자 식의 음수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-104">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24fdf-105">구문</span><span class="sxs-lookup"><span data-stu-id="24fdf-105">Syntax</span></span>  
  
```sql  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="24fdf-106">인수</span><span class="sxs-lookup"><span data-stu-id="24fdf-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="24fdf-107">숫자 데이터 형식의 유효한 식입니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-107">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="24fdf-108">결과 형식</span><span class="sxs-lookup"><span data-stu-id="24fdf-108">Result Types</span></span>  

 <span data-ttu-id="24fdf-109">`expression`의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-109">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24fdf-110">설명</span><span class="sxs-lookup"><span data-stu-id="24fdf-110">Remarks</span></span>  

 <span data-ttu-id="24fdf-111">`expression` 이 부호 없는 형식이면 결과 형식은 `expression`의 형식과 가장 밀접하게 관련된 부호 있는 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-111">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="24fdf-112">`expression` 이 Byte 형식이면 Int16 형식의 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-112">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24fdf-113">예제</span><span class="sxs-lookup"><span data-stu-id="24fdf-113">Example</span></span>  

 <span data-ttu-id="24fdf-114">다음 Entity SQL 쿼리에서는 - 산술 연산자를 사용하여 숫자 식의 음수 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-114">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="24fdf-115">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="24fdf-116">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="24fdf-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="24fdf-117">[How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="24fdf-118">다음 쿼리를 `ExecuteStructuralTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="24fdf-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#NEGATIVE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="24fdf-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24fdf-119">See also</span></span>

- [<span data-ttu-id="24fdf-120">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="24fdf-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
