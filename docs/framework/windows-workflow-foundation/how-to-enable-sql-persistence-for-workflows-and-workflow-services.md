---
description: '방법: 워크플로 및 워크플로 서비스에 SQL 지 속성 사용에 대 한 자세한 정보'
title: '방법: 워크플로 및 워크플로 서비스에 SQL 지속성 사용'
ms.date: 03/30/2017
ms.assetid: ca7bf77f-3e5d-4b23-b17a-d0b60f46411d
ms.openlocfilehash: 5c124c4ec1d75d4b3b24468c04a4fb82236aa29a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99777725"
---
# <a name="how-to-enable-sql-persistence-for-workflows-and-workflow-services"></a><span data-ttu-id="fef13-103">방법: 워크플로 및 워크플로 서비스에 SQL 지속성 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-103">How to: Enable SQL Persistence for Workflows and Workflow Services</span></span>

<span data-ttu-id="fef13-104">이 항목에서는 프로그래밍 방식과 구성 파일을 사용하여 워크플로 및 워크플로 서비스에 지속성을 사용하도록 SQL 워크플로 인스턴스 저장소 기능을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-104">This topic describes how to configure the SQL Workflow Instance Store feature to enable persistence for your workflows and workflow services both programmatically and by using a configuration file.</span></span>

<span data-ttu-id="fef13-105">Windows Server AppFabric은 지속성의 구성 프로세스를 단순화합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-105">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="fef13-106">자세한 내용은 [App Fabric 지 속성 구성](/previous-versions/appfabric/ee790848(v=azure.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fef13-106">For more information, see [App Fabric Persistence Configuration](/previous-versions/appfabric/ee790848(v=azure.10)).</span></span>

<span data-ttu-id="fef13-107">SQL 워크플로 인스턴스 저장소 기능을 사용하기 전에 이 기능에서 워크플로 인스턴스를 유지하는 데 사용할 데이터베이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-107">Before using the SQL Workflow Instance Store feature, create a database that the feature uses to persist workflow instances.</span></span> <span data-ttu-id="fef13-108">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 설치 프로그램에서는 SQL 워크플로 인스턴스 저장소 기능과 관련된 SQL 스크립트 파일을 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN 폴더에 복사합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-108">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] set-up program copies SQL script files associated with the SQL Workflow Instance Store feature to the %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN folder.</span></span> <span data-ttu-id="fef13-109">SQL 워크플로 인스턴스 저장소에서 워크플로 인스턴스를 유지하는 데 사용할 SQL Server 2005 또는 SQL Server 2008 데이터베이스에 대해 이 스크립트 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-109">Run these script files against a SQL Server 2005 or SQL Server 2008 database that you want the SQL Workflow Instance Store to use to persist workflow instances.</span></span> <span data-ttu-id="fef13-110">SqlWorkflowInstanceStoreSchema.sql 파일을 먼저 실행한 다음 SqlWorkflowInstanceStoreLogic.sql 파일을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-110">Run the SqlWorkflowInstanceStoreSchema.sql file first and then run the SqlWorkflowInstanceStoreLogic.sql file.</span></span>

> [!NOTE]
> <span data-ttu-id="fef13-111">지속성 데이터베이스를 정리하여 새 데이터베이스 상태를 만들려면 %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN의 스크립트를 다음 순서대로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-111">To clean up the persistence database to have a fresh database, run the scripts in %WINDIR%\Microsoft.NET\Framework\v4.xxx\SQL\EN in the following order.</span></span>
>
> 1. <span data-ttu-id="fef13-112">SqlWorkflowInstanceStoreSchema.sql</span><span class="sxs-lookup"><span data-stu-id="fef13-112">SqlWorkflowInstanceStoreSchema.sql</span></span>
> 2. <span data-ttu-id="fef13-113">SqlWorkflowInstanceStoreLogic.sql</span><span class="sxs-lookup"><span data-stu-id="fef13-113">SqlWorkflowInstanceStoreLogic.sql</span></span>

> [!IMPORTANT]
> <span data-ttu-id="fef13-114">지속성 데이터베이스를 만들지 않으면 호스트가 워크플로를 유지하려고 시도할 때 SQL 워크플로 인스턴스 저장소 기능에서 다음과 유사한 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-114">If you do not create a persistence database, the SQL Workflow Instance Store feature throws an exception similar to the following one when a host tries to persist workflows.</span></span>
>
> <span data-ttu-id="fef13-115">System.Data.SqlClient.SqlException: 'System.Activities.DurableInstancing.CreateLockOwner' 저장 프로시저를 찾을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-115">System.Data.SqlClient.SqlException: Could not find stored procedure 'System.Activities.DurableInstancing.CreateLockOwner'</span></span>

<span data-ttu-id="fef13-116">다음 단원에서는 SQL 워크플로 인스턴스 저장소를 사용하여 워크플로 및 워크플로 서비스에 지속성을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-116">The following sections describe how to enable persistence for workflows and workflow services using the SQL Workflow Instance Store.</span></span> <span data-ttu-id="fef13-117">SQL 워크플로 인스턴스 저장소의 속성에 대 한 자세한 내용은 [Sql 워크플로 인스턴스 저장소의 속성](properties-of-sql-workflow-instance-store.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fef13-117">For more information about properties of the SQL Workflow Instance Store, see [Properties of SQL Workflow Instance Store](properties-of-sql-workflow-instance-store.md).</span></span>

## <a name="enabling-persistence-for-self-hosted-workflows-that-use-workflowapplication"></a><span data-ttu-id="fef13-118">WorkflowApplication을 사용하는 자체 호스팅 워크플로에 지속성 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-118">Enabling Persistence for Self-Hosted Workflows that use WorkflowApplication</span></span>

<span data-ttu-id="fef13-119"><xref:System.Activities.WorkflowApplication> 개체 모델을 사용하여 프로그래밍 방식으로 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>을 사용하는 자체 호스팅 워크플로에 지속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-119">You can enable persistence for self-hosted workflows that use <xref:System.Activities.WorkflowApplication> programmatically by using the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> object model.</span></span> <span data-ttu-id="fef13-120">다음 절차에서는 이를 수행하는 단계를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-120">The following procedure contains steps to do this.</span></span>

#### <a name="to-enable-persistence-for-self-hosted-workflows"></a><span data-ttu-id="fef13-121">자체 호스팅 워크플로에 지속성을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="fef13-121">To enable persistence for self-hosted workflows</span></span>

1. <span data-ttu-id="fef13-122">System.Activities.DurableInstancing.dll에 대 한 참조를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-122">Add a reference to System.Activities.DurableInstancing.dll.</span></span>

2. <span data-ttu-id="fef13-123">소스 파일 맨 위의 기존 "using" 문 뒤에 다음 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-123">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.Activities.DurableInstancing;
    ```

3. <span data-ttu-id="fef13-124"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>를 구성하고 다음 코드 예제에서와 같이 <xref:System.Activities.WorkflowApplication.InstanceStore%2A>의 <xref:System.Activities.WorkflowApplication> 에 이를 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-124">Construct a <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> and assign it to the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> of the <xref:System.Activities.WorkflowApplication> as shown in the following code example.</span></span>

    ```csharp
    SqlWorkflowInstanceStore store =
        new SqlWorkflowInstanceStore("Server=.\\SQLEXPRESS;Initial Catalog=Persistence;Integrated Security=SSPI");

    WorkflowApplication wfApp =
        new WorkflowApplication(new Workflow1());

    wfApp.InstanceStore = store;
    ```

   > [!NOTE]
   > <span data-ttu-id="fef13-125">SQL Server 에디션에 따라 연결 문자열 서버 이름이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-125">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

4. <span data-ttu-id="fef13-126"><xref:System.Activities.WorkflowApplication.Persist%2A> 개체에 대해 <xref:System.Activities.WorkflowApplication> 메서드를 호출하여 워크플로를 유지하거나 <xref:System.Activities.WorkflowApplication.Unload%2A> 메서드를 호출하여 워크플로를 유지하고 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-126">Invoke the <xref:System.Activities.WorkflowApplication.Persist%2A> method on the <xref:System.Activities.WorkflowApplication> object to persist a workflow, or <xref:System.Activities.WorkflowApplication.Unload%2A> method to persist and unload a workflow.</span></span> <span data-ttu-id="fef13-127"><xref:System.Activities.WorkflowApplication.PersistableIdle%2A> 개체를 통해 발생한 <xref:System.Activities.WorkflowApplication> 이벤트를 처리하고 <xref:System.Activities.PersistableIdleAction.Persist>의 적절한 멤버(<xref:System.Activities.PersistableIdleAction.Unload> 또는 <xref:System.Activities.PersistableIdleAction>)를 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-127">You can also handle the <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> event raised by the <xref:System.Activities.WorkflowApplication> object and return appropriate (<xref:System.Activities.PersistableIdleAction.Persist> or <xref:System.Activities.PersistableIdleAction.Unload>) member of <xref:System.Activities.PersistableIdleAction>.</span></span>

   ```csharp
   wfApp.PersistableIdle = delegate(WorkflowApplicationIdleEventArgs e)
   {
       return PersistableIdleAction.Persist;
   };
   ```

> [!NOTE]
> <span data-ttu-id="fef13-128">단계별 지침은 방법: [시작 자습서](getting-started-tutorial.md) 의 [장기 실행 워크플로 만들기 및 실행](how-to-create-and-run-a-long-running-workflow.md) 단계를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fef13-128">See the [How to: Create and Run a Long Running Workflow](how-to-create-and-run-a-long-running-workflow.md) step of the [Getting Started Tutorial](getting-started-tutorial.md) for step by step instructions.</span></span>

## <a name="enabling-persistence-for-self-hosted-workflow-services-that-use-the-workflowservicehost"></a><span data-ttu-id="fef13-129">WorkflowServiceHost를 사용하는 자체 호스팅 워크플로 서비스에 지속성 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-129">Enabling Persistence for Self-Hosted Workflow Services that use the WorkflowServiceHost</span></span>

<span data-ttu-id="fef13-130"><xref:System.ServiceModel.WorkflowServiceHost> 클래스 또는 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 클래스를 사용하여 프로그래밍 방식으로 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A>를 사용하는 자체 호스팅 워크플로 서비스에 지속성을 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-130">You can enable persistence for self-hosted workflow services that use <xref:System.ServiceModel.WorkflowServiceHost> programmatically by using the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class or the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> class.</span></span>

### <a name="using-the-sqlworkflowinstancestorebehavior-class"></a><span data-ttu-id="fef13-131">SqlWorkflowInstanceStoreBehavior 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-131">Using the SqlWorkflowInstanceStoreBehavior Class</span></span>

<span data-ttu-id="fef13-132">다음 절차에서는 <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> 클래스를 사용하여 자체 호스팅 워크플로 서비스에 지속성을 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-132">The following procedure contains steps to use the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> class to enable persistence for self-hosted workflow services.</span></span>

#### <a name="to-enable-persistence-using-sqlworkflowinstancestorebehavior"></a><span data-ttu-id="fef13-133">SqlWorkflowInstanceStoreBehavior를 통해 지속성을 사용하려면</span><span class="sxs-lookup"><span data-stu-id="fef13-133">To enable persistence using SqlWorkflowInstanceStoreBehavior</span></span>

1. <span data-ttu-id="fef13-134">System.ServiceModel.dll에 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-134">Add a reference to the System.ServiceModel.dll.</span></span>

2. <span data-ttu-id="fef13-135">소스 파일 맨 위의 기존 "using" 문 뒤에 다음 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-135">Add the following statement at the top of the source file after the existing "using" statements.</span></span>

    ```csharp
    using System.ServiceModel.Activities.Description;
    ```

3. <span data-ttu-id="fef13-136">ph x="1" /&gt; 인스턴스를 만들고 워크플로 서비스에 대한 엔드포인트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-136">Create an instance of the `WorkflowServiceHost` and add endpoints for the workflow service.</span></span>

    ```csharp
    WorkflowServiceHost host = new WorkflowServiceHost(new CountingWorkflow(), new Uri(hostBaseAddress));
    host.AddServiceEndpoint("ICountingWorkflow", new BasicHttpBinding(), "");
    ```

4. <span data-ttu-id="fef13-137">`SqlWorkflowInstanceStoreBehavior` 개체를 구성하고 동작 개체의 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-137">Construct a `SqlWorkflowInstanceStoreBehavior` object and to set properties of the behavior object.</span></span>

    ```csharp
    SqlWorkflowInstanceStoreBehavior instanceStoreBehavior = new SqlWorkflowInstanceStoreBehavior(connectionString);
    instanceStoreBehavior.HostLockRenewalPeriod = new TimeSpan(0, 0, 5);
    instanceStoreBehavior.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;
    instanceStoreBehavior.InstanceLockedExceptionAction = InstanceLockedExceptionAction.AggressiveRetry;
    instanceStoreBehavior.InstanceEncodingOption = InstanceEncodingOption.GZip;
    instanceStoreBehavior.RunnableInstancesDetectionPeriod = new TimeSpan("00:00:02");
    host.Description.Behaviors.Add(instanceStoreBehavior);
    ```

5. <span data-ttu-id="fef13-138">워크플로 서비스 호스트를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-138">Open the workflow service host.</span></span>

    ```csharp
    host.Open();
    ```

### <a name="using-the-durableinstancingoptions-property"></a><span data-ttu-id="fef13-139">DurableInstancingOptions 속성 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-139">Using the DurableInstancingOptions Property</span></span>

<span data-ttu-id="fef13-140">`SqlWorkflowInstanceStoreBehavior`가 적용되면 `DurableInstancingOptions.InstanceStore`의 `WorkflowServiceHost`는 구성 값을 사용하여 만든 `SqlWorkflowInstanceStore` 개체로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-140">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="fef13-141">다음 코드 예제에서와 같이 <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> 클래스를 사용하지 않고 프로그래밍 방식으로 `WorkflowServiceHost`의 `SqlWorkflowInstanceStoreBehavior` 속성을 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-141">You can do the same programmatically to set the <xref:System.ServiceModel.Activities.WorkflowServiceHost.DurableInstancingOptions%2A> property of the `WorkflowServiceHost` without using the `SqlWorkflowInstanceStoreBehavior` class as shown in the following code example.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

## <a name="enabling-persistence-for-was-hosted-workflow-services-that-use-the-workflowservicehost-using-a-configuration-file"></a><span data-ttu-id="fef13-142">구성 파일을 통해 WorkflowServiceHost를 사용하는 WAS 호스팅 워크플로 서비스에 지속성 사용</span><span class="sxs-lookup"><span data-stu-id="fef13-142">Enabling Persistence for WAS-Hosted Workflow Services that use the WorkflowServiceHost using a Configuration File</span></span>

<span data-ttu-id="fef13-143">구성 파일을 통해 자체 호스팅 또는 WAS(Windows Process Activation Service) 호스팅 워크플로 서비스에 지속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-143">You can enable persistence for self-hosted or Windows Process Activation Service (WAS)-hosted workflow services by using a configuration file.</span></span> <span data-ttu-id="fef13-144">WAS 호스팅 워크플로 서비스는 자체 호스팅 워크플로 서비스와 마찬가지로 WorkflowServiceHost를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-144">A WAS-hosted workflow service uses the WorkflowServiceHost as the self-hosted workflow services do.</span></span>

<span data-ttu-id="fef13-145">`SqlWorkflowInstanceStoreBehavior`XML 구성을 통해 [SQL 워크플로 인스턴스 저장소](sql-workflow-instance-store.md) 속성을 편리 하 게 변경할 수 있도록 하는 서비스 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-145">The `SqlWorkflowInstanceStoreBehavior`, a service behavior that allows you to conveniently change the [SQL Workflow Instance Store](sql-workflow-instance-store.md) properties through XML configuration.</span></span> <span data-ttu-id="fef13-146">WAS 호스팅 워크플로 서비스에는 Web.config 파일을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-146">For WAS-hosted workflow services, use the Web.config file.</span></span> <span data-ttu-id="fef13-147">다음 구성 예제에서는 구성 파일에서 `sqlWorkflowInstanceStore` 동작 요소를 사용하여 SQL 워크플로 인스턴스 저장소를 구성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-147">The following configuration example shows how to configure the SQL Workflow Instance Store by using the `sqlWorkflowInstanceStore` behavior element in a configuration file.</span></span>

```xml
<serviceBehaviors>
    <behavior name="">
        <sqlWorkflowInstanceStore
                    connectionString="Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"
                    instanceEncodingOption="GZip | None"
                    instanceCompletionAction="DeleteAll | DeleteNothing"
                    instanceLockedExceptionAction="NoRetry | BasicRetry |AggressiveRetry"
                    hostLockRenewalPeriod="00:00:30"
                    runnableInstancesDetectionPeriod="00:00:05" />

    </behavior>
</serviceBehaviors>
```

<span data-ttu-id="fef13-148">`connectionString` 또는 `connectionStringName` 속성의 값을 설정하지 않으면 SQL 워크플로 인스턴스 저장소에서는 기본 명명된 연결 문자열 `DefaultSqlWorkflowInstanceStoreConnectionString`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-148">If you do not set values for the `connectionString` or the `connectionStringName` property, the SQL Workflow Instance Store uses the default named connection string `DefaultSqlWorkflowInstanceStoreConnectionString`.</span></span>

<span data-ttu-id="fef13-149">`SqlWorkflowInstanceStoreBehavior`가 적용되면 `DurableInstancingOptions.InstanceStore`의 `WorkflowServiceHost`는 구성 값을 사용하여 만든 `SqlWorkflowInstanceStore` 개체로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-149">When the `SqlWorkflowInstanceStoreBehavior` is applied, the `DurableInstancingOptions.InstanceStore` on the `WorkflowServiceHost` is set to the `SqlWorkflowInstanceStore` object created using the configuration values.</span></span> <span data-ttu-id="fef13-150">서비스 동작 요소를 사용하지 않고 프로그래밍 방식으로 같은 작업을 수행하여 `SqlWorkflowInstanceStore`와 함께 `WorkflowServiceHost`를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-150">You can do the same programmatically to use the `SqlWorkflowInstanceStore` with `WorkflowServiceHost` without using the service behavior element.</span></span>

```csharp
workflowServiceHost.DurableInstancingOptions.InstanceStore = sqlInstanceStoreObject;
```

> [!IMPORTANT]
> <span data-ttu-id="fef13-151">Web.config 파일에는 사용자 이름 및 암호와 같은 중요한 정보를 저장하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-151">It is recommended that you do not store sensitive information such as user names and passwords in the Web.config file.</span></span> <span data-ttu-id="fef13-152">Web.config 파일에 중요한 정보를 저장하는 경우 파일 시스템 ACL(액세스 제어 목록)을 사용하여 Web.config 파일에 대한 액세스를 보호해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-152">If you do store sensitive information in the Web.config file, you should secure access to the Web.config file by using file system Access Control Lists (ACLs).</span></span> <span data-ttu-id="fef13-153">또한 [보호 된 구성을 사용 하 여 구성 정보 암호화](/previous-versions/aspnet/53tyfkaw(v=vs.100))에 설명 된 대로 구성 파일 내에서 구성 값을 보호할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-153">In addition, you can also secure the configuration values within a configuration file as mentioned in [Encrypting Configuration Information Using Protected Configuration](/previous-versions/aspnet/53tyfkaw(v=vs.100)).</span></span>

### <a name="machineconfig-elements-related-to-the-sql-workflow-instance-store-feature"></a><span data-ttu-id="fef13-154">SQL 워크플로 인스턴스 저장소 기능과 관련된 Machine.config 요소</span><span class="sxs-lookup"><span data-stu-id="fef13-154">Machine.config Elements Related to the SQL Workflow Instance Store Feature</span></span>

<span data-ttu-id="fef13-155">[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]를 설치하면 SQL 워크플로 인스턴스 저장소 기능과 관련된 다음 요소가 Machine.config 파일에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-155">The [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] installation adds the following elements related to the SQL Workflow Instance Store feature to the Machine.config file:</span></span>

- <span data-ttu-id="fef13-156">\<sqlWorkflowInstanceStore>구성 파일의 서비스 동작 요소를 사용 하 여 서비스에 대 한 지 속성을 구성할 수 있도록 Machine.config 파일에 다음 동작 확장 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fef13-156">Adds the following behavior extension element to the Machine.config file so that you can use the \<sqlWorkflowInstanceStore> service behavior element in the configuration file to configure persistence for your services.</span></span>

    ```xml
    <configuration>
        <system.serviceModel>
            <extensions>
                <behaviorExtensions>
                    <add name="sqlWorkflowInstanceStore" type="System.Activities.DurableInstancing.SqlWorkflowInstanceStoreElement, System.Activities.DurableInstancing, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
                </behaviorExtensions>
            </extensions>
        </system.serviceModel>
    </configuration>
    ```
