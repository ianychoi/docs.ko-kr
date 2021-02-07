---
description: '자세한 정보: 정식 함수'
title: 정식 함수
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 6e84c4b5199d38e2efac44cf7e69c72abb1663f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739510"
---
# <a name="canonical-functions"></a><span data-ttu-id="20f6a-103">정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-103">Canonical Functions</span></span>

<span data-ttu-id="20f6a-104">이 단원에서는 모든 데이터 공급자에서 지원되며 모든 쿼리 기술에 사용될 수 있는 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-104">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="20f6a-105">정식 함수는 공급자에서 확장할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-105">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="20f6a-106">이러한 정식 함수는 공급자에 해당하는 데이터 소스 기능으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-106">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="20f6a-107">그러면 다양한 데이터 소스에서 일반적인 형태로 함수 호출을 표현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-107">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="20f6a-108">이러한 정식 함수는 데이터 소스에 대해 독립적이므로, 정식 함수의 인수와 반환 형식은 개념적 모델의 형식으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-108">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="20f6a-109">하지만 일부 데이터 소스에서는 개념적 모델의 모든 형식이 지원되지 않을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-109">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="20f6a-110">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] 쿼리에서 정식 함수를 사용하면 데이터 소스에서 적절한 함수가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-110">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="20f6a-111">모든 정규 함수에는 null 입력 동작과 오류 조건이 모두 명시적으로 지정되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-111">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="20f6a-112">저장소 공급자는 해당 동작을 따라야 하지만 Entity Framework이 동작을 적용 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-112">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="20f6a-113">LINQ 시나리오의 경우 Entity Framework에 대 한 쿼리에서 CLR 메서드를 기본 데이터 소스의 메서드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-113">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="20f6a-114">CLR 메서드는 특정 메서드 집합이 데이터 소스에 관계없이 올바르게 매핑되도록 정식 함수에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-114">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="20f6a-115">정식 함수 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="20f6a-115">Canonical Functions Namespace</span></span>  

 <span data-ttu-id="20f6a-116">정식 함수의 네임스페이스는 <xref:System.Data.Metadata.Edm>입니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-116">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="20f6a-117"><xref:System.Data.Metadata.Edm> 네임스페이스는 모든 쿼리에 자동으로 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-117">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="20f6a-118">하지만, 정식 함수와 이름이 같은 함수가 포함된(<xref:System.Data.Metadata.Edm> 네임스페이스) 다른 네임스페이스를 가져온 경우 네임스페이스를 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-118">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20f6a-119">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="20f6a-119">In This Section</span></span>  

 [<span data-ttu-id="20f6a-120">집계 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-120">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="20f6a-121">집계 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-121">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-122">수학 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-122">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="20f6a-123">수식 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-123">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-124">문자열 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-124">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="20f6a-125">문자열 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-125">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-126">날짜 및 시간 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-126">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="20f6a-127">날짜 및 시간 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-127">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-128">비트 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-128">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="20f6a-129">비트 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-129">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-130">공간 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-130">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="20f6a-131">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]의 공간 정식 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-131">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="20f6a-132">기타 정식 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-132">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="20f6a-133">비트, 날짜/시간, 문자열, 수식, 집계 등으로 분류되지 않는 함수에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="20f6a-133">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f6a-134">참고 항목</span><span class="sxs-lookup"><span data-stu-id="20f6a-134">See also</span></span>

- [<span data-ttu-id="20f6a-135">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="20f6a-135">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="20f6a-136">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="20f6a-136">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="20f6a-137">개념적 모델 정식 함수와 SQL Server 함수 매핑</span><span class="sxs-lookup"><span data-stu-id="20f6a-137">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="20f6a-138">사용자 정의 함수</span><span class="sxs-lookup"><span data-stu-id="20f6a-138">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
