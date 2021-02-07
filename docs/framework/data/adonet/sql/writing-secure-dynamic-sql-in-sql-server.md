---
description: '자세한 정보: SQL Server에서 보안 동적 SQL 작성'
title: SQL Server에서 동적 보안 SQL 작성
ms.date: 03/30/2017
ms.assetid: df5512b0-c249-40d2-82f9-f9a2ce6665bc
ms.openlocfilehash: 35db22358bae1150a80daa72cf4a86ef8fba9620
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766948"
---
# <a name="writing-secure-dynamic-sql-in-sql-server"></a><span data-ttu-id="ff862-103">SQL Server에서 동적 보안 SQL 작성</span><span class="sxs-lookup"><span data-stu-id="ff862-103">Writing Secure Dynamic SQL in SQL Server</span></span>

<span data-ttu-id="ff862-104">SQL 삽입은 악의적인 사용자가 유효한 입력 대신 Transact-SQL 문을 입력하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-104">SQL Injection is the process by which a malicious user enters Transact-SQL statements instead of valid input.</span></span> <span data-ttu-id="ff862-105">입력이 유효성 검사를 거치지 않고 서버로 직접 전달되고 애플리케이션이 삽입된 코드를 실수로 실행하는 경우 공격으로 인해 데이터가 손상되거나 제거될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-105">If the input is passed directly to the server without being validated and if the application inadvertently executes the injected code, the attack has the potential to damage or destroy data.</span></span>  
  
 <span data-ttu-id="ff862-106">SQL Server는 구문상 유효한 모든 수신 쿼리를 실행하므로 SQL 문을 생성하는 모든 프로시저에 삽입과 관련한 취약성이 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-106">Any procedure that constructs SQL statements should be reviewed for injection vulnerabilities because SQL Server will execute all syntactically valid queries that it receives.</span></span> <span data-ttu-id="ff862-107">매개 변수가 있는 데이터도 숙련된 전문 공격자에 의해 조작될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-107">Even parameterized data can be manipulated by a skilled and determined attacker.</span></span> <span data-ttu-id="ff862-108">동적 SQL을 사용하는 경우 명령을 매개 변수화해야 하고 매개 변수 값을 쿼리 문자열에 직접 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-108">If you use dynamic SQL, be sure to parameterize your commands, and never include parameter values directly into the query string.</span></span>  
  
## <a name="anatomy-of-a-sql-injection-attack"></a><span data-ttu-id="ff862-109">SQL 삽입 공격 분석</span><span class="sxs-lookup"><span data-stu-id="ff862-109">Anatomy of a SQL Injection Attack</span></span>  

 <span data-ttu-id="ff862-110">삽입 프로세스는 텍스트 문자열을 미리 종료하고 새 명령을 덧붙이는 방법으로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-110">The injection process works by prematurely terminating a text string and appending a new command.</span></span> <span data-ttu-id="ff862-111">삽입된 명령에는 실행 전에 덧붙여진 추가 문자열이 있을 수 있으므로 공격자는 주입된 문자열을 주석 표시인 "--"으로 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-111">Because the inserted command may have additional strings appended to it before it is executed, the malefactor terminates the injected string with a comment mark "--".</span></span> <span data-ttu-id="ff862-112">실행 시 이후 텍스트는 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-112">Subsequent text is ignored at execution time.</span></span> <span data-ttu-id="ff862-113">세미콜론(;) 구분 기호를 사용하여 여러 명령을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-113">Multiple commands can be inserted using a semicolon (;) delimiter.</span></span>  
  
 <span data-ttu-id="ff862-114">삽입된 SQL 코드가 구문상 정확하기만 하면 프로그래밍 방식으로 변조를 감지할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-114">As long as injected SQL code is syntactically correct, tampering cannot be detected programmatically.</span></span> <span data-ttu-id="ff862-115">따라서 모든 사용자 입력의 유효성을 검사하고 생성된 SQL 명령을 사용 중인 서버에서 실행하는 코드를 주의 깊게 검토해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-115">Therefore, you must validate all user input and carefully review code that executes constructed SQL commands in the server that you are using.</span></span> <span data-ttu-id="ff862-116">유효성 검사를 수행하지 않은 사용자 입력을 연결하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-116">Never concatenate user input that is not validated.</span></span> <span data-ttu-id="ff862-117">문자열 연결은 스크립트 삽입이 발생하는 주요 진입점입니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-117">String concatenation is the primary point of entry for script injection.</span></span>  
  
 <span data-ttu-id="ff862-118">다음은 몇 가지 유용한 지침입니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-118">Here are some helpful guidelines:</span></span>  
  
- <span data-ttu-id="ff862-119">사용자 입력에서 직접 Transact-SQL 문을 작성하지 마세요. 저장 프로시저를 사용하여 사용자 입력의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-119">Never build Transact-SQL statements directly from user input; use stored procedures to validate user input.</span></span>  
  
- <span data-ttu-id="ff862-120">형식, 길이, 서식 및 범위를 테스트하여 사용자 입력의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-120">Validate user input by testing type, length, format, and range.</span></span> <span data-ttu-id="ff862-121">Transact-SQL QUOTENAME() 함수를 사용하여 시스템 이름을 이스케이프하거나 REPLACE() 함수를 사용하여 문자열의 모든 문자를 이스케이프합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-121">Use the Transact-SQL QUOTENAME() function to escape system names or the REPLACE() function to escape any character in a string.</span></span>  
  
- <span data-ttu-id="ff862-122">애플리케이션의 각 계층에서 다중 계층 유효성 검사를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-122">Implement multiple layers of validation in each tier of your application.</span></span>  
  
- <span data-ttu-id="ff862-123">입력의 크기 및 데이터 형식을 테스트하고 적합한 제한 조치를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-123">Test the size and data type of input and enforce appropriate limits.</span></span> <span data-ttu-id="ff862-124">그러면 의도적인 버퍼 오버런을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-124">This can help prevent deliberate buffer overruns.</span></span>  
  
- <span data-ttu-id="ff862-125">문자열 변수의 내용을 테스트하고 예상 값만 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-125">Test the content of string variables and accept only expected values.</span></span> <span data-ttu-id="ff862-126">이진 데이터, 이스케이프 시퀀스 및 주석 문자를 포함하는 항목은 거부합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-126">Reject entries that contain binary data, escape sequences, and comment characters.</span></span>  
  
- <span data-ttu-id="ff862-127">XML 문서 작업에서는 입력한 스키마에 대해 모든 데이터의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-127">When you are working with XML documents, validate all data against its schema as it is entered.</span></span>  
  
- <span data-ttu-id="ff862-128">다중 계층 환경에서는 신뢰할 수 있는 영역으로 들어가기 전에 모든 데이터의 유효성을 검사해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-128">In multi-tiered environments, all data should be validated before admission to the trusted zone.</span></span>  
  
- <span data-ttu-id="ff862-129">파일 이름을 생성하는 데 사용될 수 있는 필드에는 AUX, CLOCK$, COM1~COM8, CON, CONFIG$, LPT1~LPT8, NUL, PRN과 같은 문자열을 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-129">Do not accept the following strings in fields from which file names can be constructed: AUX, CLOCK$, COM1 through COM8, CON, CONFIG$, LPT1 through LPT8, NUL, and PRN.</span></span>  
  
- <span data-ttu-id="ff862-130">저장 프로시저 및 명령과 함께 <xref:System.Data.SqlClient.SqlParameter> 개체를 사용하여 형식 검사 및 길이 유효성 검사를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-130">Use <xref:System.Data.SqlClient.SqlParameter> objects with stored procedures and commands to provide type checking and length validation.</span></span>  
  
- <span data-ttu-id="ff862-131">클라이언트 코드에서 <xref:System.Text.RegularExpressions.Regex> 식을 사용하여 잘못된 문자를 필터링합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-131">Use <xref:System.Text.RegularExpressions.Regex> expressions in client code to filter invalid characters.</span></span>  
  
## <a name="dynamic-sql-strategies"></a><span data-ttu-id="ff862-132">동적 SQL 전략</span><span class="sxs-lookup"><span data-stu-id="ff862-132">Dynamic SQL Strategies</span></span>  

 <span data-ttu-id="ff862-133">프로시저 코드에서 동적으로 생성된 SQL 문을 실행하면 소유권 체인이 중단되고 이로 인해 SQL Server가 동적 SQL에서 액세스하는 개체에 대해 호출자의 권한을 확인하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-133">Executing dynamically created SQL statements in your procedural code breaks the ownership chain, causing SQL Server to check the permissions of the caller against the objects being accessed by the dynamic SQL.</span></span>  
  
 <span data-ttu-id="ff862-134">SQL Server에는 동적 SQL을 실행하는 사용자 정의 함수 및 저장 프로시저를 사용하여 데이터에 액세스할 수 있는 권한을 사용자에게 부여하는 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-134">SQL Server has methods for granting users access to data using stored procedures and user-defined functions that execute dynamic SQL.</span></span>  
  
- <span data-ttu-id="ff862-135">[SQL Server에서 가장으로 권한 사용자 지정](customizing-permissions-with-impersonation-in-sql-server.md)에 설명된 대로 Transact-SQL EXECUTE AS 절과 함께 가장을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-135">Using impersonation with the Transact-SQL EXECUTE AS clause, as described in [Customizing Permissions with Impersonation in SQL Server](customizing-permissions-with-impersonation-in-sql-server.md).</span></span>  
  
- <span data-ttu-id="ff862-136">[SQL Server에서 저장 프로시저에 서명](signing-stored-procedures-in-sql-server.md)에 설명된 대로 인증서로 저장 프로시저를 서명합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-136">Signing stored procedures with certificates, as described in [Signing Stored Procedures in SQL Server](signing-stored-procedures-in-sql-server.md).</span></span>  
  
### <a name="execute-as"></a><span data-ttu-id="ff862-137">EXECUTE AS</span><span class="sxs-lookup"><span data-stu-id="ff862-137">EXECUTE AS</span></span>  

 <span data-ttu-id="ff862-138">EXECUTE AS 절은 호출자의 권한을 EXECUTE AS 절에 지정된 사용자의 권한으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-138">The EXECUTE AS clause replaces the permissions of the caller with that of the user specified in the EXECUTE AS clause.</span></span> <span data-ttu-id="ff862-139">중첩된 저장 프로시저 또는 트리거는 프록시 사용자의 보안 컨텍스트에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-139">Nested stored procedures or triggers execute under the security context of the proxy user.</span></span> <span data-ttu-id="ff862-140">이는 행 수준 보안을 사용하거나 감사를 요구하는 애플리케이션을 중단시킬 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-140">This can break applications that rely on row-level security or require auditing.</span></span> <span data-ttu-id="ff862-141">사용자의 ID를 반환하는 일부 함수는 원래 호출자가 아니라 EXECUTE AS 절에 지정된 사용자를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-141">Some functions that return the identity of the user return the user specified in the EXECUTE AS clause, not the original caller.</span></span> <span data-ttu-id="ff862-142">실행 컨텍스트는 프로시저 실행 후 또는 REVERT 문이 실행된 후에만 원래 호출자로 되돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-142">Execution context is reverted to the original caller only after execution of the procedure or when a REVERT statement is issued.</span></span>  
  
### <a name="certificate-signing"></a><span data-ttu-id="ff862-143">인증서 서명</span><span class="sxs-lookup"><span data-stu-id="ff862-143">Certificate Signing</span></span>  

 <span data-ttu-id="ff862-144">인증서로 서명된 저장 프로시저를 실행하면 인증서 사용자에게 부여된 권한이 해당 호출자의 권한과 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-144">When a stored procedure that has been signed with a certificate executes, the permissions granted to the certificate user are merged with those of the caller.</span></span> <span data-ttu-id="ff862-145">실행 컨텍스트는 동일하게 유지됩니다. 인증서 사용자는 호출자를 가장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-145">The execution context remains the same; the certificate user does not impersonate the caller.</span></span> <span data-ttu-id="ff862-146">저장 프로시저에 서명하려면 여러 단계를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-146">Signing stored procedures requires several steps to implement.</span></span> <span data-ttu-id="ff862-147">프로시저를 수정할 때마다 다시 서명해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-147">Each time the procedure is modified, it must be re-signed.</span></span>  
  
### <a name="cross-database-access"></a><span data-ttu-id="ff862-148">데이터베이스 간 액세스</span><span class="sxs-lookup"><span data-stu-id="ff862-148">Cross Database Access</span></span>  

 <span data-ttu-id="ff862-149">동적으로 생성된 SQL 문을 실행하는 경우에는 데이터베이스 간 소유권 체인이 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-149">Cross-database ownership chaining does not work in cases where dynamically created SQL statements are executed.</span></span> <span data-ttu-id="ff862-150">SQL Server에서는 다른 데이터베이스의 데이터에 액세스하는 저장 프로시저를 만들고 두 데이터베이스 모두에 존재하는 인증서로 프로시저에 서명하여 이 문제를 피할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-150">You can work around this in SQL Server by creating a stored procedure that accesses data in another database and signing the procedure with a certificate that exists in both databases.</span></span> <span data-ttu-id="ff862-151">이렇게 하면 사용자에게 데이터베이스 액세스 또는 권한을 부여하지 않고 사용자가 프로시저에서 사용하는 데이터베이스 리소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-151">This gives users access to the database resources used by the procedure without granting them database access or permissions.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="ff862-152">외부 리소스</span><span class="sxs-lookup"><span data-stu-id="ff862-152">External Resources</span></span>  

 <span data-ttu-id="ff862-153">자세한 내용은 다음 리소스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ff862-153">For more information, see the following resources.</span></span>  
  
|<span data-ttu-id="ff862-154">리소스</span><span class="sxs-lookup"><span data-stu-id="ff862-154">Resource</span></span>|<span data-ttu-id="ff862-155">설명</span><span class="sxs-lookup"><span data-stu-id="ff862-155">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="ff862-156">[저장 프로시저](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) 및 [SQL 삽입](/sql/relational-databases/security/sql-injection)(SQL Server 온라인 설명서)</span><span class="sxs-lookup"><span data-stu-id="ff862-156">[Stored Procedures](/sql/relational-databases/stored-procedures/stored-procedures-database-engine) and [SQL Injection](/sql/relational-databases/security/sql-injection) in SQL Server Books Online</span></span>|<span data-ttu-id="ff862-157">이들 항목에서는 저장 프로시저를 만드는 방법과 SQL 삽입이 작동하는 방식을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="ff862-157">Topics describe how to create stored procedures and how SQL Injection works.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ff862-158">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ff862-158">See also</span></span>

- [<span data-ttu-id="ff862-159">ADO.NET 애플리케이션 보안</span><span class="sxs-lookup"><span data-stu-id="ff862-159">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="ff862-160">SQL Server 보안 개요</span><span class="sxs-lookup"><span data-stu-id="ff862-160">Overview of SQL Server Security</span></span>](overview-of-sql-server-security.md)
- [<span data-ttu-id="ff862-161">SQL Server의 애플리케이션 보안 시나리오</span><span class="sxs-lookup"><span data-stu-id="ff862-161">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="ff862-162">SQL Server에서 저장 프로시저를 사용하여 권한 관리</span><span class="sxs-lookup"><span data-stu-id="ff862-162">Managing Permissions with Stored Procedures in SQL Server</span></span>](managing-permissions-with-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="ff862-163">SQL Server에서 저장 프로시저에 서명</span><span class="sxs-lookup"><span data-stu-id="ff862-163">Signing Stored Procedures in SQL Server</span></span>](signing-stored-procedures-in-sql-server.md)
- [<span data-ttu-id="ff862-164">SQL Server에서 가장으로 권한 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="ff862-164">Customizing Permissions with Impersonation in SQL Server</span></span>](customizing-permissions-with-impersonation-in-sql-server.md)
- [<span data-ttu-id="ff862-165">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="ff862-165">ADO.NET Overview</span></span>](../ado-net-overview.md)
