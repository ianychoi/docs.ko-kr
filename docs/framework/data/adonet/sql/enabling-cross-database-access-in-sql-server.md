---
description: '자세한 정보: SQL Server에서 데이터베이스 간 액세스 활성화'
title: SQL Server에서 데이터베이스간 액세스 활성화
ms.date: 03/30/2017
ms.assetid: 10663fb6-434c-4c81-8178-ec894b9cf895
ms.openlocfilehash: 4e818b4f0294fdc7edd351a1e60203357579a320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695868"
---
# <a name="enabling-cross-database-access-in-sql-server"></a><span data-ttu-id="2c0f5-103">SQL Server에서 데이터베이스간 액세스 활성화</span><span class="sxs-lookup"><span data-stu-id="2c0f5-103">Enabling Cross-Database Access in SQL Server</span></span>

<span data-ttu-id="2c0f5-104">데이터베이스 간 소유권 체인은 한 데이터베이스의 프로시저가 다른 데이터베이스의 개체에 종속되는 경우 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-104">Cross-database ownership chaining occurs when a procedure in one database depends on objects in another database.</span></span> <span data-ttu-id="2c0f5-105">끊어지지 않은 소유권 체인에서는 모든 개체 소유자가 동일한 로그인 계정에 매핑되어야 한다는 점을 제외하고 데이터베이스 간 소유권 체인은 단일 데이터베이스 내의 소유권 체인과 같은 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-105">A cross-database ownership chain works in the same way as ownership chaining within a single database, except that an unbroken ownership chain requires that all the object owners are mapped to the same login account.</span></span> <span data-ttu-id="2c0f5-106">소스 데이터베이스의 소스 개체와 대상 데이터베이스의 대상 개체를 동일한 로그인 계정에서 소유하는 경우 SQL Server는 대상 개체의 권한을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-106">If the source object in the source database and the target objects in the target databases are owned by the same login account, SQL Server does not check permissions on the target objects.</span></span>  
  
## <a name="off-by-default"></a><span data-ttu-id="2c0f5-107">기본적으로 활성화되지 않음</span><span class="sxs-lookup"><span data-stu-id="2c0f5-107">Off By Default</span></span>  

 <span data-ttu-id="2c0f5-108">데이터베이스 간 소유권 체인은 기본적으로 해제되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-108">Ownership chaining across databases is turned off by default.</span></span> <span data-ttu-id="2c0f5-109">Microsoft에서는 데이터베이스 간 소유권 체인이 다음과 같은 보안 위험에 노출되므로 데이터베이스 간 소유권 체인을 비활성화할 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-109">Microsoft recommends that you disable cross-database ownership chaining because it exposes you to the following security risks:</span></span>  
  
- <span data-ttu-id="2c0f5-110">데이터베이스 소유자 및 `db_ddladmin` 또는 `db_owners` 데이터베이스 역할의 멤버는 개체를 만들어 다른 사용자가 소유하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-110">Database owners and members of the `db_ddladmin` or the `db_owners` database roles can create objects that are owned by other users.</span></span> <span data-ttu-id="2c0f5-111">이러한 개체는 잠재적으로 다른 데이터베이스의 개체를 대상으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-111">These objects can potentially target objects in other databases.</span></span> <span data-ttu-id="2c0f5-112">이것은 데이터베이스 간 소유권 체인을 활성화할 때 모든 데이터베이스의 데이터에 대해 이러한 사용자를 완전 신뢰한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-112">This means that if you enable cross-database ownership chaining, you must fully trust these users with data in all databases.</span></span>  
  
- <span data-ttu-id="2c0f5-113">CREATE DATABASE 권한이 있는 사용자는 새 데이터베이스를 만들고 기존 데이터베이스에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-113">Users with CREATE DATABASE permission can create new databases and attach existing databases.</span></span> <span data-ttu-id="2c0f5-114">데이터베이스 간 소유권 체인이 활성화되면 이러한 사용자는 새로 만들었거나 연결한 데이터베이스를 통해 권한이 없는 다른 데이터베이스의 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-114">If cross-database ownership chaining is enabled, these users can access objects in other databases that they might not have privileges in from the newly created or attached databases that they create.</span></span>  
  
## <a name="enabling-cross-database-ownership-chaining"></a><span data-ttu-id="2c0f5-115">데이터베이스 간 소유권 체인 활성화</span><span class="sxs-lookup"><span data-stu-id="2c0f5-115">Enabling Cross-database Ownership Chaining</span></span>  

 <span data-ttu-id="2c0f5-116">데이터베이스 간 소유권 체인은 권한이 높은 사용자를 완전 신뢰할 수 있는 환경에서만 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-116">Cross-database ownership chaining should only be enabled in environments where you can fully trust highly-privileged users.</span></span> <span data-ttu-id="2c0f5-117">모든 데이터베이스에 대해 설정하는 동안 구성하거나 Transact-SQL 명령 `sp_configure` 및 `ALTER DATABASE`을 사용하는 특정 데이터베이스에 대해 선택적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-117">It can be configured during setup for all databases, or selectively for specific databases using the Transact-SQL commands `sp_configure` and `ALTER DATABASE`.</span></span>  
  
 <span data-ttu-id="2c0f5-118">데이터베이스 간 소유권 체인을 선택적으로 구성하려면 `sp_configure`를 사용하여 서버에 대해 이를 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-118">To selectively configure cross-database ownership chaining, use `sp_configure` to turn it off for the server.</span></span> <span data-ttu-id="2c0f5-119">ALTER DATABASE 명령을 SET DB_CHAINING ON으로 사용하여 데이터베이스 간 소유권 체인을 해당 데이터베이스에 대해서만 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-119">Then use the ALTER DATABASE command with SET DB_CHAINING ON to configure cross-database ownership chaining for only the databases that require it.</span></span>  
  
 <span data-ttu-id="2c0f5-120">다음 샘플에서는 모든 데이터베이스에 대해 데이터베이스 간 소유권 체인을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-120">The following sample turns on cross-database ownership chaining for all databases:</span></span>  
  
```sql
EXECUTE sp_configure 'show advanced', 1;  
RECONFIGURE;  
EXECUTE sp_configure 'cross db ownership chaining', 1;  
RECONFIGURE;  
```  
  
 <span data-ttu-id="2c0f5-121">다음 샘플에서는 특정 데이터베이스에 대해 데이터베이스 간 소유권 체인을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-121">The following sample turns on cross-database ownership chaining for specific databases:</span></span>  
  
```sql
ALTER DATABASE Database1 SET DB_CHAINING ON;  
ALTER DATABASE Database2 SET DB_CHAINING ON;  
```  
  
### <a name="dynamic-sql"></a><span data-ttu-id="2c0f5-122">동적 SQL</span><span class="sxs-lookup"><span data-stu-id="2c0f5-122">Dynamic SQL</span></span>  

 <span data-ttu-id="2c0f5-123">데이터베이스 간 소유권 체인은 동일 사용자가 두 데이터베이스에 없는 경우 동적으로 생성된 SQL 문이 실행되는 환경에서는 동작하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-123">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed unless the same user exists in both databases.</span></span> <span data-ttu-id="2c0f5-124">SQL Server에서는 다른 데이터베이스의 데이터에 액세스하는 저장 프로시저를 만들고 두 데이터베이스 모두에 존재하는 인증서로 프로시저에 서명하여 이 문제를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-124">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="2c0f5-125">이렇게 하면 사용자에게 데이터베이스 액세스 또는 권한을 부여하지 않고 사용자가 프로시저에서 사용하는 데이터베이스 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-125">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="2c0f5-126">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="2c0f5-126">External Resources</span></span>  

 <span data-ttu-id="2c0f5-127">자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-127">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="2c0f5-128">리소스</span><span class="sxs-lookup"><span data-stu-id="2c0f5-128">Resource</span></span>|<span data-ttu-id="2c0f5-129">설명</span><span class="sxs-lookup"><span data-stu-id="2c0f5-129">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="2c0f5-130">EXECUTE AS 및 [DB 간 소유권 체인 옵션](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option)을 [사용 하 여 데이터베이스 가장을 확장](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-130">[Extending Database Impersonation by Using EXECUTE AS](/previous-versions/sql/sql-server-2008-r2/ms188304(v=sql.105)) and [Cross DB Ownership Chaining Option](/sql/database-engine/configure-windows/cross-db-ownership-chaining-server-configuration-option).</span></span>|<span data-ttu-id="2c0f5-131">문서에서는 SQL Server 인스턴스에 대 한 데이터베이스 간 소유권 체인을 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="2c0f5-131">Articles describe how to configure cross-database ownership chaining for an instance of SQL Server.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c0f5-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2c0f5-132">See also</span></span>

- [<span data-ttu-id="2c0f5-133">ADO.NET 애플리케이션 보안</span><span class="sxs-lookup"><span data-stu-id="2c0f5-133">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="2c0f5-134">SQL Server 보안 개요</span><span class="sxs-lookup"><span data-stu-id="2c0f5-134">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="2c0f5-135">SQL Server에서 저장 프로시저를 사용하여 권한 관리</span><span class="sxs-lookup"><span data-stu-id="2c0f5-135">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="2c0f5-136">SQL Server에서 보안 동적 SQL 작성</span><span class="sxs-lookup"><span data-stu-id="2c0f5-136">Writing Secure Dynamic SQL in SQL Server</span></span>](writing-secure-dynamic-sql-in-sql-server.md)
- [<span data-ttu-id="2c0f5-137">SQL Server에서 저장 프로시저에 서명</span><span class="sxs-lookup"><span data-stu-id="2c0f5-137">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="2c0f5-138">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="2c0f5-138">ADO.NET Overview</span></span>](../ado-net-overview.md)
