---
description: '자세한 정보: LIKE (Entity SQL)'
title: LIKE(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: 932ddfcf8a8ab8b32f6a097f92ff2979e32239da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748273"
---
# <a name="like-entity-sql"></a><span data-ttu-id="f112c-103">LIKE(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f112c-103">LIKE (Entity SQL)</span></span>

<span data-ttu-id="f112c-104">특정 문자 `String`이 지정된 패턴과 일치하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-104">Determines whether a specific character `String` matches a specified pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f112c-105">구문</span><span class="sxs-lookup"><span data-stu-id="f112c-105">Syntax</span></span>  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a><span data-ttu-id="f112c-106">인수</span><span class="sxs-lookup"><span data-stu-id="f112c-106">Arguments</span></span>  

 `match`  
 <span data-ttu-id="f112c-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 값을 반환하는 `String` 식입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-107">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression that evaluates to a `String`.</span></span>  
  
 `pattern`  
 <span data-ttu-id="f112c-108">지정된 `String`과 일치하는 패턴입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-108">A pattern to match to the specified `String`.</span></span>  
  
 `escape`  
 <span data-ttu-id="f112c-109">이스케이프 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-109">An escape character.</span></span>  
  
 <span data-ttu-id="f112c-110">NOT</span><span class="sxs-lookup"><span data-stu-id="f112c-110">NOT</span></span>  
 <span data-ttu-id="f112c-111">LIKE의 결과를 부정하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-111">Specifies that the result of LIKE be negated.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f112c-112">Return Value</span><span class="sxs-lookup"><span data-stu-id="f112c-112">Return Value</span></span>  

 <span data-ttu-id="f112c-113">`true`이 패턴과 일치하면 `string`이고, 그렇지 않으면 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-113">`true` if the `string` matches the pattern; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f112c-114">설명</span><span class="sxs-lookup"><span data-stu-id="f112c-114">Remarks</span></span>  

 <span data-ttu-id="f112c-115">LIKE 연산자를 사용하는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 식의 계산은 같음을 필터 조건으로 사용하는 식과 동일한 방법으로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-115">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator are evaluated in much the same way as expressions that use equality as the filter criteria.</span></span> <span data-ttu-id="f112c-116">하지만, LIKE 연산자를 사용하는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 식에는 리터럴과 와일드카드 문자 모두가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-116">However, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that use the LIKE operator can include both literals and wildcard characters.</span></span>  
  
 <span data-ttu-id="f112c-117">다음 표에서는 패턴 `string`의 구문을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-117">The following table describes the syntax of the pattern `string`.</span></span>  
  
|<span data-ttu-id="f112c-118">와일드카드 문자</span><span class="sxs-lookup"><span data-stu-id="f112c-118">Wildcard Character</span></span>|<span data-ttu-id="f112c-119">설명</span><span class="sxs-lookup"><span data-stu-id="f112c-119">Description</span></span>|<span data-ttu-id="f112c-120">예제</span><span class="sxs-lookup"><span data-stu-id="f112c-120">Example</span></span>|  
|------------------------|-----------------|-------------|  
|%|<span data-ttu-id="f112c-121">문자 0개 이상으로 이루어진 임의의 `string`입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-121">Any `string` of zero or more characters.</span></span>|<span data-ttu-id="f112c-122">`title like '%computer%'` 제목의 임의의 위치에 단어가 있는 모든 제목을 찾습니다 `"computer"` .</span><span class="sxs-lookup"><span data-stu-id="f112c-122">`title like '%computer%'` finds all titles with the word `"computer"` anywhere in the title.</span></span>|  
|<span data-ttu-id="f112c-123">_ (밑줄)</span><span class="sxs-lookup"><span data-stu-id="f112c-123">_ (underscore)</span></span>|<span data-ttu-id="f112c-124">단일 문자</span><span class="sxs-lookup"><span data-stu-id="f112c-124">Any single character.</span></span>|<span data-ttu-id="f112c-125">`firstname like '_ean'`은 Dean이나 Sean처럼 `"ean`"으로 끝나면서 4문자로 이루어진 이름을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-125">`firstname like '_ean'` finds all four-letter first names that end with `"ean`," such as Dean or Sean.</span></span>|  
|<span data-ttu-id="f112c-126">[ ]</span><span class="sxs-lookup"><span data-stu-id="f112c-126">[ ]</span></span>|<span data-ttu-id="f112c-127">지정된 범위([a-f]) 또는 집합([abcdef]) 내의 임의의 단일 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-127">Any single character in the specified range ([a-f]) or set ([abcdef]).</span></span>|<span data-ttu-id="f112c-128">`lastname like '[C-P]arsen'`은 Carsen이나 Larsen처럼 C와 P 사이의 단일 문자로 시작되고 "arsen"으로 끝나는 성을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-128">`lastname like '[C-P]arsen'` finds last names ending with "arsen" and beginning with any single character between C and P, such as Carsen or Larsen.</span></span>|  
|<span data-ttu-id="f112c-129">[^]</span><span class="sxs-lookup"><span data-stu-id="f112c-129">[^]</span></span>|<span data-ttu-id="f112c-130">지정된 범위([^a-f]) 또는 집합([^abcdef])에 속하지 않는 임의의 단일 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-130">Any single character not in the specified range ([^a-f]) or set ([^abcdef]).</span></span>|<span data-ttu-id="f112c-131">`lastname like 'de[^l]%'` 는 "de"로 시작 하 고 "l"을 다음 문자로 포함 하지 않는 성을 모두 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-131">`lastname like 'de[^l]%'` finds all last names that begin with "de" and do not include "l" as the following letter.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="f112c-132">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE 연산자와 ESCAPE 절은 `System.DateTime` 또는 `System.Guid` 값에 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-132">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] LIKE operator and ESCAPE clause cannot be applied to `System.DateTime` or `System.Guid` values.</span></span>  
  
 <span data-ttu-id="f112c-133">LIKE는 ASCII 패턴 일치와 유니코드 패턴 일치를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-133">LIKE supports ASCII pattern matching and Unicode pattern matching.</span></span> <span data-ttu-id="f112c-134">모든 매개 변수가 ASCII 문자인 경우 ASCII 패턴 일치가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-134">When all parameters are ASCII characters, ASCII pattern matching is performed.</span></span> <span data-ttu-id="f112c-135">인수 하나 이상이 유니코드인 경우 모든 인수가 유니코드로 변환되고 유니코드 패턴 일치가 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-135">If one or more of the arguments are Unicode, all arguments are converted to Unicode and Unicode pattern matching is performed.</span></span> <span data-ttu-id="f112c-136">LIKE로 유니코드를 사용할 경우에는 후행 공백이 중요하지만 비유니코드의 경우에는 후행 공백이 중요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-136">When you use Unicode with LIKE, trailing blanks are significant; however, for non-Unicode, trailing blanks are not significant.</span></span> <span data-ttu-id="f112c-137">의 패턴 문자열 구문은 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transact-sql의 구문과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-137">The pattern string syntax of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is the same as that of Transact-SQL.</span></span>  
  
 <span data-ttu-id="f112c-138">패턴은 일반 문자와 와일드카드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-138">A pattern can include regular characters and wildcard characters.</span></span> <span data-ttu-id="f112c-139">패턴 일치 과정에서 정규 문자는 문자 `string`에 지정된 문자와 정확히 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-139">During pattern matching, regular characters must exactly match the characters specified in the character `string`.</span></span> <span data-ttu-id="f112c-140">그러나 와일드카드 문자는 문자열에서 어느 한 부분만 일치하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-140">However, wildcard characters can be matched with arbitrary fragments of the character string.</span></span> <span data-ttu-id="f112c-141">와일드카드 문자와 함께 사용할 때 LIKE 연산자는 = 및 != 문자열 비교 연산자보다 융통성이 뛰어납니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-141">When it is used with wildcard characters, the LIKE operator is more flexible than the = and != string comparison operators.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f112c-142">특정 공급자를 대상으로 하는 경우 공급자 특정 확장을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-142">You may use provider-specific extensions if you target a specific provider.</span></span> <span data-ttu-id="f112c-143">하지만 그렇게 하면 다른 공급자에서 다르게 취급할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-143">However, such constructs may be treated differently by other providers, for example.</span></span> <span data-ttu-id="f112c-144">SqlServer에서는 [first-last] 및 [^first-last] 패턴이 지원되며, 여기서 첫 번째는 first와 last 사이의 한 문자와 정확히 일치하고 두 번째는 first와 last 사이에 존재하지 않는 한 문자와 정확히 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-144">SqlServer supports [first-last] and [^first-last] patterns where the former matches exactly one character between first and last, and the latter matches exactly one character that is not between first and last.</span></span>  
  
### <a name="escape"></a><span data-ttu-id="f112c-145">이스케이프</span><span class="sxs-lookup"><span data-stu-id="f112c-145">Escape</span></span>  

 <span data-ttu-id="f112c-146">ESCAPE 절을 사용하면 이전 단원의 표에서 설명한 특수 와일드카드 문자가 한 개 이상 포함된 문자열을 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-146">By using the ESCAPE clause, you can search for character strings that include one or more of the special wildcard characters described in the table in the previous section.</span></span> <span data-ttu-id="f112c-147">예를 들어, 여러 문서의 제목에 "100%"라는 리터럴이 포함되어 있고 해당 문서 전체에서 검색하려는 경우를 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-147">For example, assume several documents include the literal "100%" in the title and you want to search for all of those documents.</span></span> <span data-ttu-id="f112c-148">백분율(%) 문자는 와일드카드 문자이므로, 검색을 성공적으로 실행하려면 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE 절을 사용하여 이 문자를 이스케이프 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-148">Because the percent (%) character is a wildcard character, you must escape it using the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ESCAPE clause to successfully execute the search.</span></span> <span data-ttu-id="f112c-149">다음은 이러한 필터의 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-149">The following is an example of this filter.</span></span>  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 <span data-ttu-id="f112c-150">이 검색 식에서 느낌표(!) 문자 바로 다음에 나오는 백분율(%) 와일드카드 문자는 와일드카드 문자가 아니라 리터럴로 취급됩니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-150">In this search expression, the percent wildcard character (%) immediately following the exclamation point character (!) is treated as a literal, instead of as a wildcard character.</span></span> <span data-ttu-id="f112c-151">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 와일드카드 문자 및 대괄호(`[ ]`) 문자를 제외한 모든 문자를 이스케이프 문자로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-151">You can use any character as an escape character except for the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] wildcard characters and the square bracket (`[ ]`) characters.</span></span> <span data-ttu-id="f112c-152">이전의 예제에서 느낌표(!) 문자가 이스케이프 문자입니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-152">In the previous example, the exclamation point (!) character is the escape character.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f112c-153">예제</span><span class="sxs-lookup"><span data-stu-id="f112c-153">Example</span></span>  

 <span data-ttu-id="f112c-154">다음 두 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서는 LIKE 및 ESCAPE 연산자를 사용하여 특정 문자열이 지정된 패턴과 일치하는지 여부를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-154">The following two [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries use the LIKE and ESCAPE operators to determine whether a specific character string matches a specified pattern.</span></span> <span data-ttu-id="f112c-155">첫 번째 쿼리는 `Name`이라는 문자로 시작되는 `Down_`을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-155">The first query searches for the `Name` that starts with the characters `Down_`.</span></span> <span data-ttu-id="f112c-156">이 쿼리에서는 밑줄(`_`)이 와일드카드 문자이므로 ESCAPE 옵션이 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-156">This query uses the ESCAPE option because the underscore (`_`) is a wildcard character.</span></span> <span data-ttu-id="f112c-157">이스케이프 옵션을 지정 하지 않으면 쿼리는 `Name` 단어 `Down` 다음에 밑줄 문자 이외의 단일 문자로 시작 하는 값을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-157">Without specifying the ESCAPE option, the query would search for any `Name` values that start with the word `Down` followed by any single character other than the underscore character.</span></span> <span data-ttu-id="f112c-158">쿼리는 AdventureWorks Sales 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-158">The queries are based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f112c-159">이 쿼리를 컴파일하고 실행하려면 다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="f112c-159">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f112c-160">[방법: PrimitiveType 결과를 반환 하는 쿼리 실행](../how-to-execute-a-query-that-returns-primitivetype-results.md)의 절차를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-160">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="f112c-161">다음 쿼리를 `ExecutePrimitiveTypeQuery` 메서드에 인수로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="f112c-161">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a><span data-ttu-id="f112c-162">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f112c-162">See also</span></span>

- [<span data-ttu-id="f112c-163">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="f112c-163">Entity SQL Reference</span></span>](entity-sql-reference.md)
