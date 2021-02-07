---
description: '에 대 한 자세한 정보: 시스템 트랜잭션과 SQL Server 통합'
title: SQL Server와의 System.Transactions 통합
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 977ff18600256613dabc0212c2f7aa1bc2650408
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766779"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="13356-103">SQL Server와의 System.Transactions 통합</span><span class="sxs-lookup"><span data-stu-id="13356-103">System.Transactions Integration with SQL Server</span></span>

<span data-ttu-id="13356-104">.NET Framework 버전 2.0에는 네임 스페이스를 통해 액세스할 수 있는 트랜잭션 프레임 워크가 도입 <xref:System.Transactions> 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-104">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="13356-105">이 프레임 워크는 ADO.NET을 포함 하 여 .NET Framework에 완전히 통합 된 방식으로 트랜잭션을 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-105">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="13356-106">프로그래밍 기능 향상 외에도 <xref:System.Transactions> 및 ADO.NET은 함께 작동하여 트랜잭션을 사용할 때 최적화를 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-106">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="13356-107">승격 가능한 트랜잭션이란 필요에 따라 완전 분산 트랜잭션으로 자동 승격될 수 있는 간단한(로컬) 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="13356-107">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="13356-108">ADO.NET 2.0부터는 <xref:System.Data.SqlClient> SQL Server 작업할 때 승격 가능한 트랜잭션을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-108">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="13356-109">승격 가능한 트랜잭션은 추가 오버헤드가 필요한 경우를 제외하고 분산 트랜잭션의 추가 오버헤드를 호출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-109">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="13356-110">승격 가능한 트랜잭션은 자동으로 수행되며 개발자의 개입이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-110">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="13356-111">승격 가능한 트랜잭션은 SQL Server에서 SQL Server ()에 대 한 .NET Framework Data Provider를 사용 하는 경우에만 사용할 수 있습니다 `SqlClient` .</span><span class="sxs-lookup"><span data-stu-id="13356-111">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="13356-112">승격 가능한 트랜잭션 만들기</span><span class="sxs-lookup"><span data-stu-id="13356-112">Creating Promotable Transactions</span></span>  

 <span data-ttu-id="13356-113">SQL Server에 대 한 .NET Framework 공급자는 .NET Framework 네임 스페이스의 클래스를 통해 처리 되는 승격 가능한 트랜잭션을 지원 합니다 <xref:System.Transactions> .</span><span class="sxs-lookup"><span data-stu-id="13356-113">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="13356-114">승격 가능한 트랜잭션은 필요할 때까지 분산 트랜잭션 만들기를 연기하여 분산 트랜잭션을 최적화합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-114">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="13356-115">리소스 관리자만 필요할 경우 분산 트랜잭션은 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-115">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13356-116">부분적으로 신뢰할 수 있는 시나리오에서 트랜잭션을 분산 트랜잭션으로 승격시키려면 <xref:System.Transactions.DistributedTransactionPermission> 이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-116">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="13356-117">승격 가능한 트랜잭션 시나리오</span><span class="sxs-lookup"><span data-stu-id="13356-117">Promotable Transaction Scenarios</span></span>  

 <span data-ttu-id="13356-118">분산 트랜잭션에서는 일반적으로 MS DTC(Microsoft Distributed Transaction Coordinator)를 통해 관리되는 많은 양의 시스템 리소스를 사용합니다. MS DTC는 트랜잭션에서 액세스하는 모든 리소스 관리자를 통합합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-118">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="13356-119">승격 가능한 트랜잭션은 실제로 작업을 단순한 SQL Server 트랜잭션에 위임하는 특수한 형식의 <xref:System.Transactions> 트랜잭션입니다.</span><span class="sxs-lookup"><span data-stu-id="13356-119">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="13356-120"><xref:System.Transactions>, <xref:System.Data.SqlClient> 및 SQL Server는 트랜잭션 처리와 관련된 작업을 조정하고 필요에 따라 완전한 분산 트랜잭션으로 승격합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-120"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="13356-121">승격 가능한 트랜잭션을 사용하면 활성 <xref:System.Transactions.TransactionScope> 트랜잭션을 사용하여 연결이 열리고, 다른 연결이 열려 있지 않은 경우 완전 분산 트랜잭션의 추가 오버헤드를 발생시키는 대신 간단한 트랜잭션으로 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-121">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="13356-122">연결 문자열 키워드</span><span class="sxs-lookup"><span data-stu-id="13356-122">Connection String Keywords</span></span>  

 <span data-ttu-id="13356-123"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 속성에서는 `Enlist`에서 트랜잭션 컨텍스트를 찾은 후 분산 트랜잭션에 연결을 자동으로 인리스트먼트할지 여부를 나타내는 키워드인 <xref:System.Data.SqlClient> 를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-123">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="13356-124">`Enlist=true`인 경우 연결이 열려 있는 스레드의 현재 트랜잭션 컨텍스트에 자동으로 인리스트먼트됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-124">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="13356-125">`Enlist=false`인 경우에는 `SqlClient` 연결이 분산 트랜잭션과 상호 작용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-125">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="13356-126">`Enlist` 의 기본값은 true입니다.</span><span class="sxs-lookup"><span data-stu-id="13356-126">The default value for `Enlist` is true.</span></span> <span data-ttu-id="13356-127">연결 문자열에 `Enlist` 가 지정되지 않으면 연결이 열릴 때 감지된 연결이 분산 트랜잭션에 자동으로 인리스트먼트됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-127">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="13356-128">`Transaction Binding` 연결 문자열의 <xref:System.Data.SqlClient.SqlConnection> 키워드는 인리스트먼트된 `System.Transactions` 트랜잭션과 연결 사이의 관계를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-128">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="13356-129">이 키워드는 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> 의 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>속성을 통해서도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-129">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="13356-130">다음 표에서는 사용 가능한 값을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-130">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="13356-131">키워드</span><span class="sxs-lookup"><span data-stu-id="13356-131">Keyword</span></span>|<span data-ttu-id="13356-132">설명</span><span class="sxs-lookup"><span data-stu-id="13356-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13356-133">Implicit Unbind</span><span class="sxs-lookup"><span data-stu-id="13356-133">Implicit Unbind</span></span>|<span data-ttu-id="13356-134">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="13356-134">The default.</span></span> <span data-ttu-id="13356-135">트랜잭션이 끝나면 자동으로 연결이 끊어지고 자동 커밋 모드로 전환됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-135">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="13356-136">Explicit Unbind</span><span class="sxs-lookup"><span data-stu-id="13356-136">Explicit Unbind</span></span>|<span data-ttu-id="13356-137">트랜잭션을 닫을 때까지 트랜잭션에 대한 연결이 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-137">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="13356-138">연결된 트랜잭션이 활성 상태가 아니거나 <xref:System.Transactions.Transaction.Current%2A>와 일치하지 않으면 연결이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-138">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="13356-139">TransactionScope 사용</span><span class="sxs-lookup"><span data-stu-id="13356-139">Using TransactionScope</span></span>  

 <span data-ttu-id="13356-140"><xref:System.Transactions.TransactionScope> 클래스는 연결을 암시적으로 분산 트랜잭션에 등록함으로써 코드 블록에 트랜잭션을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-140">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="13356-141"><xref:System.Transactions.TransactionScope.Complete%2A> 메서드는 <xref:System.Transactions.TransactionScope> 블록을 벗어나기 전에 이 블록의 끝 부분에서 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-141">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="13356-142">블록을 벗어나면 <xref:System.Transactions.TransactionScope.Dispose%2A> 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-142">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="13356-143">예외가 throw되어 코드가 범위를 벗어날 경우 트랜잭션이 중단된 것으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-143">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="13356-144">`using` 블록을 사용하여 해당 블록을 종료할 때 <xref:System.Transactions.TransactionScope.Dispose%2A> 가 <xref:System.Transactions.TransactionScope> 개체에서 호출되도록 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-144">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="13356-145">보류 중인 트랜잭션을 커밋하거나 롤백하지 못하면 <xref:System.Transactions.TransactionScope> 의 기본 시간 제한이 1분이므로 성능이 크게 저하될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-145">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="13356-146">`using` 문을 사용하지 않는 경우 `Try` 블록에서 모든 작업을 수행하고 <xref:System.Transactions.TransactionScope.Dispose%2A> 블록에서 명시적으로 `Finally` 메서드를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-146">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="13356-147"><xref:System.Transactions.TransactionScope>에서 예외가 발생하면 트랜잭션이 일관성이 없는 것으로 표시되어 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-147">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="13356-148">또한 <xref:System.Transactions.TransactionScope> 가 삭제되면 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-148">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="13356-149">예외가 발생하지 않으면 참여하는 트랜잭션이 커밋됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-149">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13356-150">`TransactionScope` 클래스는 기본적으로 <xref:System.Transactions.Transaction.IsolationLevel%2A>의 `Serializable`을 사용하여 트랜잭션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="13356-150">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="13356-151">애플리케이션에 따라서는 애플리케이션에 경합이 많이 발생하지 않도록 격리 수준을 낮추는 방법을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-151">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13356-152">업데이트, 삽입 및 삭제는 데이터베이스 리소스를 많이 사용하므로 분산 트랜잭션에서는 이러한 작업만 수행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-152">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="13356-153">SELECT 문은 데이터베이스 리소스를 불필요하게 잠글 수 있으며, 경우에 따라서는 선택 시 트랜잭션을 사용해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-153">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="13356-154">다른 트랜잭트 리소스 관리자를 사용해야 하는 경우가 아니면 데이터베이스 작업이 아닌 다른 작업은 트랜잭션 범위 밖에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-154">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="13356-155">트랜잭션 범위에서 예외를 통해 트랜잭션이 커밋되는 것을 금지하고 있지만, <xref:System.Transactions.TransactionScope> 클래스에는 트랜잭션 자체 범위를 벗어난 코드 변경을 롤백할 수 있는 규정이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="13356-155">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="13356-156">트랜잭션이 롤백될 때 특별한 조치를 취해야 하는 경우에는 고유한 <xref:System.Transactions.IEnlistmentNotification> 인터페이스 구현을 작성한 후 트랜잭션에 명시적으로 인리스트먼트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-156">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13356-157">예제</span><span class="sxs-lookup"><span data-stu-id="13356-157">Example</span></span>  

 <span data-ttu-id="13356-158"><xref:System.Transactions> 를 사용하려면 System.Transactions.dll을 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-158">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="13356-159">다음 함수는 서로 다른 두 <xref:System.Data.SqlClient.SqlConnection> 개체( <xref:System.Transactions.TransactionScope> 블록에 래핑됨)로 표현되는 두 개의 서로 다른 SQL Server 인스턴스에 대해 승격 가능한 트랜잭션을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13356-159">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="13356-160">이 코드에서는 <xref:System.Transactions.TransactionScope> 문을 사용하여 `using` 블록을 만든 후 첫 번째 연결을 엽니다. 그리고 나면 이 연결은 <xref:System.Transactions.TransactionScope>에 자동으로 참여합니다.</span><span class="sxs-lookup"><span data-stu-id="13356-160">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="13356-161">트랜잭션은 처음에 전체 분산 트랜잭션이 아닌 경량 트랜잭션으로 등록됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-161">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="13356-162">두 번째 연결은 첫 번째 연결의 명령이 예외를 throw하지 않을 경우에만 <xref:System.Transactions.TransactionScope> 에 인리스트먼트됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-162">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="13356-163">두 번째 연결이 열리면 트랜잭션이 완전 분산 트랜잭션으로 자동 승격됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-163">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="13356-164">예외가 throw되지 않은 경우에만 트랜잭션을 커밋하는 <xref:System.Transactions.TransactionScope.Complete%2A> 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-164">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="13356-165"><xref:System.Transactions.TransactionScope> 블록의 한 지점에서 예외가 throw된 경우에는 `Complete` 가 호출되지 않으며 <xref:System.Transactions.TransactionScope> 블록 끝에서 `using` 가 삭제되면 분산 트랜잭션이 롤백됩니다.</span><span class="sxs-lookup"><span data-stu-id="13356-165">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2
                // only when there is a chance that the transaction can commit.
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2
                ' only when there is a chance that the transaction can commit.
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="13356-166">참조</span><span class="sxs-lookup"><span data-stu-id="13356-166">See also</span></span>

- [<span data-ttu-id="13356-167">트랜잭션 및 동시성</span><span class="sxs-lookup"><span data-stu-id="13356-167">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)
- [<span data-ttu-id="13356-168">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="13356-168">ADO.NET Overview</span></span>](ado-net-overview.md)
