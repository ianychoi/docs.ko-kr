---
description: '자세한 정보: 네임 스페이스 (Entity SQL)'
title: 네임스페이스(Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 70ef0021c3015fd661b42becb5371dcfd958f20f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99696557"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="638c7-103">네임스페이스(Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="638c7-103">Namespaces (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="638c7-104">에서는 형식 이름, 엔터티 집합, 함수 등의 전역 식별자에 대한 이름 충돌을 피하기 위해 네임스페이스가 도입되었습니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-104">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="638c7-105">의 네임 스페이스 지원은 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .NET Framework의 네임 스페이스 지원과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-105">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="638c7-106">은 다음 예제와 같이 정규화된 네임스페이스(네임스페이스에 대해 짧은 별칭이 제공됨)와 비정규화된 네임스페이스라는 두 가지 형태의 USING 절을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-106">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="638c7-107">이름 확인 규칙</span><span class="sxs-lookup"><span data-stu-id="638c7-107">Name Resolution Rules</span></span>  

 <span data-ttu-id="638c7-108">로컬 범위에서 식별자를 확인할 수 없는 경우에서는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 전역 범위 (네임 스페이스)에서 이름을 찾으려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-108">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="638c7-109">에서는 먼저 식별자(접두사)와 일치하는 정규화된 네임스페이스가 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-109">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="638c7-110">일치하는 것이 있으면 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 해당 네임스페이스에서 나머지 식별자를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-110">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="638c7-111">일치하는 것이 없으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-111">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="638c7-112">다음으로 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 모든 비정규화된 네임스페이스(프롤로그에 지정됨)에서 식별자를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-112">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="638c7-113">식별자를 정확하게 하나의 네임스페이스에서 찾을 수 있으면 해당 위치가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-113">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="638c7-114">해당 식별자와 일치하는 네임스페이스가 둘 이상이면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-114">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="638c7-115">식별자의 네임스페이스를 확인할 수 없는 경우 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 다음 예제와 같이 이름을 다음 바깥쪽 범위(<xref:System.Data.Common.DbCommand> 또는 <xref:System.Data.Common.DbConnection> 개체)로 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-115">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="638c7-116">.NET Framework와의 차이점</span><span class="sxs-lookup"><span data-stu-id="638c7-116">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="638c7-117">.NET Framework에서 부분적으로 정규화 된 네임 스페이스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-117">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="638c7-118">에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-118">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="638c7-119">ADO.NET 사용</span><span class="sxs-lookup"><span data-stu-id="638c7-119">ADO.NET Usage</span></span>  

 <span data-ttu-id="638c7-120">쿼리는 ADO.NET <xref:System.Data.Common.DbCommand> 개체를 통해 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-120">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="638c7-121"><xref:System.Data.Common.DbCommand> 개체를 통해 <xref:System.Data.Common.DbConnection> 개체를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-121"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="638c7-122">네임스페이스는 <xref:System.Data.Common.DbCommand> 및 <xref:System.Data.Common.DbConnection> 개체의 일부로 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="638c7-122">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="638c7-123">[!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서는 쿼리 자체 내에서 식별자를 확인할 수 없는 경우 외부 네임스페이스를 검색합니다(비슷한 규칙이 사용됨).</span><span class="sxs-lookup"><span data-stu-id="638c7-123">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="638c7-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="638c7-124">See also</span></span>

- [<span data-ttu-id="638c7-125">엔터티 SQL 참조</span><span class="sxs-lookup"><span data-stu-id="638c7-125">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="638c7-126">Entity SQL 개요</span><span class="sxs-lookup"><span data-stu-id="638c7-126">Entity SQL Overview</span></span>](entity-sql-overview.md)
