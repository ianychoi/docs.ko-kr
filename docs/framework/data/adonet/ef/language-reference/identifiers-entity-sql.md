---
description: '자세한 정보: 식별자 (Entity SQL)'
title: 식별자(Entity SQL)
ms.date: 03/30/2017
ms.assetid: d58a5edd-7b5c-48e1-b5d7-a326ff426aa4
ms.openlocfilehash: 932f45e8b65b6244eada330caeb9a04b6560d427
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99748663"
---
# <a name="identifiers-entity-sql"></a><span data-ttu-id="5281f-103">식별자(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5281f-103">Identifiers (Entity SQL)</span></span>

<span data-ttu-id="5281f-104">식별자는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서 쿼리 식 별칭, 변수 참조, 개체 속성, 함수 등을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-104">Identifiers are used in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to represent query expression aliases, variable references, properties of objects, functions, and so on.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5281f-105">에서는 간단한 식별자와 따옴표 붙은 식별자의 두 가지 식별자를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-105">provides two kinds of identifiers: simple identifiers and quoted identifiers.</span></span>  
  
## <a name="simple-identifiers"></a><span data-ttu-id="5281f-106">단순 식별자</span><span class="sxs-lookup"><span data-stu-id="5281f-106">Simple Identifiers</span></span>  

 <span data-ttu-id="5281f-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 단순 식별자는 영숫자와 밑줄 문자의 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-107">A simple identifier in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is a sequence of alphanumeric and underscore characters.</span></span> <span data-ttu-id="5281f-108">식별자의 첫 문자는 영문자(a-z 또는 A-Z)여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-108">The first character of the identifier must be an alphabetical character (a-z or A-Z).</span></span>  
  
## <a name="quoted-identifiers"></a><span data-ttu-id="5281f-109">따옴표 붙은 식별자</span><span class="sxs-lookup"><span data-stu-id="5281f-109">Quoted Identifiers</span></span>  

 <span data-ttu-id="5281f-110">따옴표 붙은 식별자는 대괄호( [] )로 묶인 임의의 문자 시퀀스입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-110">A quoted identifier is any sequence of characters enclosed in square brackets ([]).</span></span> <span data-ttu-id="5281f-111">따옴표 붙은 식별자를 사용하면 식별자에 유효하지 않은 문자를 사용하여 식별자를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-111">Quoted identifiers let you specify identifiers with characters that are not valid in identifiers.</span></span> <span data-ttu-id="5281f-112">대괄호 사이의 모든 문자는 모든 공백을 포함 하 여 식별자의 일부가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-112">All characters between the square brackets become part of the identifier, including all white space.</span></span>  
  
 <span data-ttu-id="5281f-113">따옴표 붙은 식별자는 다음 문자를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-113">A quoted identifier cannot include the following characters:</span></span>  
  
- <span data-ttu-id="5281f-114">줄 바꿈 문자</span><span class="sxs-lookup"><span data-stu-id="5281f-114">Newline.</span></span>  
  
- <span data-ttu-id="5281f-115">캐리지 리턴</span><span class="sxs-lookup"><span data-stu-id="5281f-115">Carriage returns.</span></span>  
  
- <span data-ttu-id="5281f-116">탭</span><span class="sxs-lookup"><span data-stu-id="5281f-116">Tabs.</span></span>  
  
- <span data-ttu-id="5281f-117">백스페이스</span><span class="sxs-lookup"><span data-stu-id="5281f-117">Backspace.</span></span>  
  
- <span data-ttu-id="5281f-118">추가 대괄호(대괄호 내부에서 식별자를 나타내는 대괄호)</span><span class="sxs-lookup"><span data-stu-id="5281f-118">Additional square brackets (that is, square brackets within the square brackets that delineate the identifier).</span></span>  
  
 <span data-ttu-id="5281f-119">따옴표 붙은 식별자는 유니코드 문자를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-119">A quoted-identifier can include Unicode characters.</span></span>  
  
 <span data-ttu-id="5281f-120">따옴표 붙은 식별자를 사용하면 다음 예제에서 보여 주는 것처럼 식별자에서 유효하지 않은 속성 이름 문자를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-120">Quoted identifiers enable you to create property name characters that are not valid in identifiers, as illustrated in the following example:</span></span>  
  
 `SELECT c.ContactName AS [Contact Name] FROM customers AS c`  
  
 <span data-ttu-id="5281f-121">또한 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 예약된 키워드인 식별자를 지정할 때도 따옴표 붙은 식별자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-121">You can also use quoted identifiers to specify an identifier that is a reserved keyword of [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="5281f-122">예를 들어, `Email` 형식에 "From"이라는 속성이 있을 경우 다음과 같이 대괄호를 사용하면 예약된 키워드인 FROM과 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-122">For example, if the type `Email` has a property named "From", you can disambiguate it from the reserved keyword FROM by using square brackets, as follows:</span></span>  
  
 `SELECT e.[From] FROM emails AS e`  
  
 <span data-ttu-id="5281f-123">점(.) 연산자의 오른쪽에 따옴표 붙은 식별자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-123">You can use a quoted identifier on the right side of a dot (.) operator.</span></span>  
  
 `SELECT t FROM ts as t WHERE t.[property] == 2`  
  
 <span data-ttu-id="5281f-124">식별자에 대괄호를 사용하려면 대괄호를 하나 더 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-124">To use the square bracket in an identifier, add an extra square bracket.</span></span> <span data-ttu-id="5281f-125">다음 예제에서 "`abc]`"는 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-125">In the following example "`abc]`" is the identifier:</span></span>  
  
 `SELECT t from ts as t WHERE t.[abc]]] == 2`  
  
 <span data-ttu-id="5281f-126">따옴표 붙은 식별자 비교 의미 체계는 [입력 문자 집합](input-character-set-entity-sql.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="5281f-126">For quoted identifier comparison semantics, see [Input Character Set](input-character-set-entity-sql.md).</span></span>  
  
## <a name="aliasing-rules"></a><span data-ttu-id="5281f-127">별칭 지정 규칙</span><span class="sxs-lookup"><span data-stu-id="5281f-127">Aliasing Rules</span></span>  

 <span data-ttu-id="5281f-128">다음 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 구문을 비롯하여 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서 필요 시 항상 별칭을 지정하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-128">We recommend specifying aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries whenever needed, including the following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] constructs:</span></span>  
  
- <span data-ttu-id="5281f-129">행 생성자 필드</span><span class="sxs-lookup"><span data-stu-id="5281f-129">Fields of a row constructor.</span></span>  
  
- <span data-ttu-id="5281f-130">쿼리 식 FROM 절의 항목</span><span class="sxs-lookup"><span data-stu-id="5281f-130">Items in the FROM clause of a query expression.</span></span>  
  
- <span data-ttu-id="5281f-131">쿼리 식 SELECT 절의 항목</span><span class="sxs-lookup"><span data-stu-id="5281f-131">Items in the SELECT clause of a query expression.</span></span>  
  
- <span data-ttu-id="5281f-132">쿼리 식 GROUP BY 절의 항목</span><span class="sxs-lookup"><span data-stu-id="5281f-132">Items in the GROUP BY clause of a query expression.</span></span>  
  
### <a name="valid-aliases"></a><span data-ttu-id="5281f-133">유효한 별칭</span><span class="sxs-lookup"><span data-stu-id="5281f-133">Valid Aliases</span></span>  

 <span data-ttu-id="5281f-134">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서 유효한 별칭은 모든 단순 식별자 또는 따옴표 붙은 식별자입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-134">Valid aliases in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] are any simple identifier or quoted identifier.</span></span>  
  
### <a name="alias-generation"></a><span data-ttu-id="5281f-135">별칭 생성</span><span class="sxs-lookup"><span data-stu-id="5281f-135">Alias Generation</span></span>  

 <span data-ttu-id="5281f-136">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리 식에서 별칭이 지정되지 않은 경우 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 다음과 같은 간단한 규칙에 따라 별칭을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-136">If no alias is specified in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the following simple rules:</span></span>  
  
- <span data-ttu-id="5281f-137">별칭이 지정되지 않은 쿼리 식이 단순 식별자 또는 따옴표 붙은 식별자인 경우, 해당 식별자가 별칭으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-137">If the query expression (for which the alias is unspecified) is a simple or quoted identifier, that identifier is used as the alias.</span></span> <span data-ttu-id="5281f-138">예를 들어 `ROW(a, [b])`는 `ROW(a AS a, [b] AS [b])`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-138">For example, `ROW(a, [b])` becomes `ROW(a AS a, [b] AS [b])`.</span></span>  
  
- <span data-ttu-id="5281f-139">쿼리 식이 더 복잡한 식이지만 이 식의 마지막 구성 요소가 단순 식별자인 경우, 해당 식별자가 별칭으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-139">If the query expression is a more complex expression, but the last component of that query expression is a simple identifier, then that identifier is used as the alias.</span></span> <span data-ttu-id="5281f-140">예를 들어 `ROW(a.a1, b.[b1])`는 `ROW(a.a1 AS a1, b.[b1] AS [b1])`가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-140">For example, `ROW(a.a1, b.[b1])` becomes `ROW(a.a1 AS a1, b.[b1] AS [b1])`.</span></span>  
  
 <span data-ttu-id="5281f-141">나중에 별칭 이름을 사용하려는 경우 암시적 별칭을 사용하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-141">We recommend that you do not use implicit aliasing if you want to use the alias name later.</span></span> <span data-ttu-id="5281f-142">동일한 범위에서 암시적 또는 명시적 별칭이 충돌하거나 반복될 때마다 컴파일 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-142">Anytime aliases (implicit or explicit) conflict or are repeated in the same scope, there will be a compile error.</span></span> <span data-ttu-id="5281f-143">같은 이름의 명시적 또는 암시적 별칭이 있더라도 암시적 별칭은 컴파일을 거칩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-143">An implicit alias will pass compilation even if there is an explicit or implicit alias of the same name.</span></span>  
  
 <span data-ttu-id="5281f-144">암시적 별칭은 사용자 입력을 기반으로 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-144">Implicit aliases are autogenerated based on user input.</span></span> <span data-ttu-id="5281f-145">예를 들어, 다음 코드 줄에서는 두 열 모두에 대해 별칭으로 NAME을 생성하여 충돌하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-145">For example, the following line of code will generate NAME as an alias for both columns and therefore will conflict.</span></span>  
  
```sql  
SELECT product.NAME, person.NAME  
```  
  
 <span data-ttu-id="5281f-146">명시적 별칭을 사용하는 다음 코드 줄 역시 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-146">The following line of code, which uses explicit aliases, will also fail.</span></span> <span data-ttu-id="5281f-147">코드를 읽으면 실패가 더 분명해집니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-147">However, the failure will be more apparent by reading the code.</span></span>  
  
```sql  
SELECT 1 AS X, 2 AS X …  
```  
  
## <a name="scoping-rules"></a><span data-ttu-id="5281f-148">범위 지정 규칙</span><span class="sxs-lookup"><span data-stu-id="5281f-148">Scoping Rules</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="5281f-149">에서는 쿼리 언어에 특정 변수가 표시되는 시점을 결정하는 범위 지정 규칙을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-149">defines scoping rules that determine when particular variables are visible in the query language.</span></span> <span data-ttu-id="5281f-150">어떤 식이나 문에서는 새 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-150">Some expressions or statements introduce new names.</span></span> <span data-ttu-id="5281f-151">이러한 이름을 사용할 수 있는 위치 및 동일한 이름을 다른 이름으로 새로 선언하여 선행 이름을 숨길 수 있는 시점이나 위치 등을 결정하는 데 범위 지정 규칙이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-151">The scoping rules determine where those names can be used, and when or where a new declaration with the same name as another can hide its predecessor.</span></span>  
  
 <span data-ttu-id="5281f-152">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서 이름이 정의되어 있는 경우 범위 내에서 정의되어 있다고 말합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-152">When names are defined in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, they are said to be defined within a scope.</span></span> <span data-ttu-id="5281f-153">범위는 쿼리의 전체 영역을 포괄합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-153">A scope covers an entire region of the query.</span></span> <span data-ttu-id="5281f-154">특정 범위의 모든 식이나 이름 참조에서는 해당 범위에서 정의된 이름을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-154">All expressions or name references within a certain scope can see names that are defined within that scope.</span></span> <span data-ttu-id="5281f-155">범위 시작 이전과 끝난 후에는 그 범위에서 정의된 이름을 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-155">Before a scope begins and after it ends, names that are defined within the scope cannot be referenced.</span></span>  
  
 <span data-ttu-id="5281f-156">범위는 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-156">Scopes can be nested.</span></span> <span data-ttu-id="5281f-157">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 일부에서는 전체 영역을 포괄하는 새 영역을 제공하며, 이러한 영역 역시 범위를 제공하는 다른 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-157">Parts of [!INCLUDE[esql](../../../../../../includes/esql-md.md)] introduce new scopes that cover entire regions, and these regions can contain other [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expressions that also introduce scopes.</span></span> <span data-ttu-id="5281f-158">범위가 중첩될 경우, 참조를 포함하는 가장 안쪽 범위에 정의된 이름을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-158">When scopes are nested, references can be made to names that are defined in the innermost scope, which contains the reference.</span></span> <span data-ttu-id="5281f-159">또한 바깥쪽 범위에 정의된 임의의 이름을 참조할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-159">References can also be made to any names that are defined in any outer scopes.</span></span> <span data-ttu-id="5281f-160">동일한 범위에서 정의된 두 범위는 형제 범위로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-160">Any two scopes defined within the same scope are considered sibling scopes.</span></span> <span data-ttu-id="5281f-161">형제 범위에 정의된 이름은 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-161">References cannot be made to names that are defined within sibling scopes.</span></span>  
  
 <span data-ttu-id="5281f-162">안쪽 범위에서 선언된 이름이 바깥쪽 범위에서 선언된 이름과 일치하는 경우, 안쪽 범위 내 또는 그 범위에서 선언된 범위 내의 참조는 새로 선언된 이름만 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-162">If a name declared in an inner scope matches a name declared in an outer scope, references within the inner scope or within scopes declared within that scope refer only to the newly declared name.</span></span> <span data-ttu-id="5281f-163">바깥쪽 범위의 이름은 숨겨집니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-163">The name in the outer scope is hidden.</span></span>  
  
 <span data-ttu-id="5281f-164">동일한 범위 내에 있더라도 이름을 정의하기 전에는 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-164">Even within the same scope, names cannot be referenced before they are defined.</span></span>  
  
 <span data-ttu-id="5281f-165">전역 이름은 실행 환경의 일부로 존재할 수 있으며,</span><span class="sxs-lookup"><span data-stu-id="5281f-165">Global names can exist as part of the execution environment.</span></span> <span data-ttu-id="5281f-166">여기에는 영구 컬렉션 또는 환경 변수의 이름이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-166">This can include names of persistent collections or environment variables.</span></span> <span data-ttu-id="5281f-167">이름이 전역 이름이 되려면 가장 바깥쪽 범위에서 선언되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-167">For a name to be global, it must be declared in the outermost scope.</span></span>  
  
 <span data-ttu-id="5281f-168">매개 변수는 범위에 속하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-168">Parameters are not in a scope.</span></span> <span data-ttu-id="5281f-169">매개 변수에 대한 참조에는 특수 구문이 포함되므로, 매개 변수의 이름은 쿼리의 다른 이름과 충돌하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-169">Because references to parameters include special syntax, names of parameters will never collide with other names in the query.</span></span>  
  
### <a name="query-expressions"></a><span data-ttu-id="5281f-170">쿼리 식</span><span class="sxs-lookup"><span data-stu-id="5281f-170">Query Expressions</span></span>  

 <span data-ttu-id="5281f-171">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리 식에서는 새로운 범위를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-171">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query expression introduces a new scope.</span></span> <span data-ttu-id="5281f-172">FROM 절에 정의된 이름이 나타나는 순서대로 왼쪽에서 오른쪽 순으로 시작 범위에 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-172">Names that are defined in the FROM clause are introduced into the from scope in order of appearance, left to right.</span></span> <span data-ttu-id="5281f-173">조인 목록에서 식은 목록에서 앞쪽에 정의된 이름을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-173">In the join list, expressions can refer to names that were defined earlier in the list.</span></span> <span data-ttu-id="5281f-174">FROM 절에서 식별된 요소의 공용 속성(예: 필드)은 시작 범위에 추가되지 않으며</span><span class="sxs-lookup"><span data-stu-id="5281f-174">Public properties (fields and so on) of elements identified in the FROM clause are not added to the from-scope.</span></span> <span data-ttu-id="5281f-175">항상 정규화된 별칭 이름으로 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-175">They must be always referenced by the alias-qualified name.</span></span> <span data-ttu-id="5281f-176">일반적으로 SELECT 식의 모든 부분은 시작 범위 내에 있는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-176">Typically, all parts of the SELECT expression are considered within the from-scope.</span></span>  
  
 <span data-ttu-id="5281f-177">GROUP BY 절 역시 새로운 형제 범위를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-177">The GROUP BY clause also introduces a new sibling scope.</span></span> <span data-ttu-id="5281f-178">각 그룹은 그룹의 요소 컬렉션을 참조하는 그룹 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-178">Each group can have a group name that refers to the collection of elements in the group.</span></span> <span data-ttu-id="5281f-179">각 그룹화 식도 그룹 범위에 새 이름을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-179">Each grouping expression will also introduce a new name into the group-scope.</span></span> <span data-ttu-id="5281f-180">또한 중첩 집계(또는 명명된 그룹)도 범위에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-180">Additionally, the nest aggregate (or the named group) is also added to the scope.</span></span> <span data-ttu-id="5281f-181">그룹화 식 자체는 시작 범위에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-181">The grouping expressions themselves are within the from-scope.</span></span> <span data-ttu-id="5281f-182">그러나 GROUP BY 절이 사용되는 경우 선택 목록(프로젝션), HAVING 절 및 ORDER BY 절은 시작 범위가 아니라 그룹 범위에 속하는 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-182">However, when a GROUP BY clause is used, the select-list (projection), HAVING clause, and ORDER BY clause are considered to be within the group-scope, and not the from-scope.</span></span> <span data-ttu-id="5281f-183">집계는 다음 글머리 기호 목록에서 설명하는 것처럼 특별하게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-183">Aggregates receive special treatment, as described in the following bulleted list.</span></span>  
  
 <span data-ttu-id="5281f-184">다음은 범위에 대한 추가적인 참고 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-184">The following are additional notes about scopes:</span></span>  
  
- <span data-ttu-id="5281f-185">선택 목록은 새 이름을 순서대로 범위에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-185">The select-list can introduce new names into the scope, in order.</span></span> <span data-ttu-id="5281f-186">오른쪽의 프로젝션 식은 왼쪽의 프로젝션된 이름을 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-186">Projection expressions to the right might refer to names projected on the left.</span></span>  
  
- <span data-ttu-id="5281f-187">ORDER BY 절은 선택 목록에서 지정된 이름(별칭)을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-187">The ORDER BY clause can refer to names (aliases) specified in the select list.</span></span>  
  
- <span data-ttu-id="5281f-188">SELECT 식 내 절의 평가 순서에 따라 이름이 범위에 제공되는 순서가 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-188">The order of evaluation of clauses within the SELECT expression determines the order that names are introduced into the scope.</span></span> <span data-ttu-id="5281f-189">FROM 절이 가장 먼저 평가되며 그 다음에는 WHERE 절, GROUP BY 절, HAVING 절, SELECT 절 그리고 마지막으로 ORDER BY 절의 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-189">The FROM clause is evaluated first, followed by the WHERE clause, GROUP BY clause, HAVING clause, SELECT clause, and finally the ORDER BY clause.</span></span>  
  
### <a name="aggregate-handling"></a><span data-ttu-id="5281f-190">집계 처리</span><span class="sxs-lookup"><span data-stu-id="5281f-190">Aggregate Handling</span></span>  

 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="5281f-191">는 컬렉션 기반 집계와 그룹 기반 집계의 두 가지 집계 형태를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-191">supports two forms of aggregates: collection-based aggregates and group-based aggregates.</span></span> <span data-ttu-id="5281f-192">컬렉션 기반 집계는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서 선호하는 구문이며, 그룹 기반 집계는 SQL 호환성을 위해 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-192">Collection-based aggregates are the preferred construct in [!INCLUDE[esql](../../../../../../includes/esql-md.md)], and group-based aggregates are supported for SQL compatibility.</span></span>  
  
 <span data-ttu-id="5281f-193">집계를 확인할 때 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 먼저 집계를 컬렉션 기반 집계로 처리하려고 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-193">When resolving an aggregate, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] first tries to treat it as a collection-based aggregate.</span></span> <span data-ttu-id="5281f-194">이 처리에 실패하면 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 다음 예제에서 보여 주는 것처럼 집계 입력을 중첩 집계 참조로 변환하고 새 식을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5281f-194">If that fails, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] transforms the aggregate input into a reference to the nest aggregate and tries to resolve this new expression, as illustrated in the following example.</span></span>  
  
 `AVG(t.c) becomes AVG(group..(t.c))`  
  
## <a name="see-also"></a><span data-ttu-id="5281f-195">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5281f-195">See also</span></span>

- [<span data-ttu-id="5281f-196">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="5281f-196">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="5281f-197">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="5281f-197">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="5281f-198">입력 문자 세트</span><span class="sxs-lookup"><span data-stu-id="5281f-198">Input Character Set</span></span>](input-character-set-entity-sql.md)
