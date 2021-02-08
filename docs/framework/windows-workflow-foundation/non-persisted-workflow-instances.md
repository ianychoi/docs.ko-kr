---
description: '다음에 대 한 자세한 정보: 비지속형 워크플로 인스턴스'
title: 비지속형 워크플로 인스턴스
ms.date: 03/30/2017
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
ms.openlocfilehash: 0ee5968426a6bb800b9e70ac592c6da191c22511
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787905"
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="6524c-103">비지속형 워크플로 인스턴스</span><span class="sxs-lookup"><span data-stu-id="6524c-103">Non-Persisted Workflow Instances</span></span>

<span data-ttu-id="6524c-104"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>에 상태를 유지하는 워크플로의 새 인스턴스가 만들어지면 서비스 호스트에서는 인스턴스 저장소에 해당 서비스에 대한 항목을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-104">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="6524c-105">이후 워크플로 인스턴스가 처음으로 유지될 때 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>는 현재 인스턴스 상태를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-105">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="6524c-106">워크플로가 Windows Process Activation Service에서 호스트되는 경우에는 인스턴스가 처음으로 유지될 때 서비스 배포 데이터도 인스턴스 저장소에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-106">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>

<span data-ttu-id="6524c-107">워크플로 인스턴스가 지속 되지 않으면 **지속** 되지 않는 상태에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-107">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="6524c-108">이 상태에 있는 동안에는 애플리케이션 도메인 재활용, 호스트 오류 또는 컴퓨터 오류 후 워크플로 인스턴스를 복구할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-108">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>

## <a name="the-non-persisted-state"></a><span data-ttu-id="6524c-109">비지속형 상태</span><span class="sxs-lookup"><span data-stu-id="6524c-109">The Non-Persisted State</span></span>

<span data-ttu-id="6524c-110">유지되지 않은 영속 워크플로 인스턴스는 다음과 같은 경우에 비지속형 상태로 남아 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-110">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>

- <span data-ttu-id="6524c-111">워크플로 인스턴스가 처음으로 유지되기 전에 서비스 호스트에서 충돌이 발생한 경우.</span><span class="sxs-lookup"><span data-stu-id="6524c-111">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="6524c-112">워크플로 인스턴스가 인스턴스 저장소에 남아 있고 복구되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-112">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="6524c-113">상관 관계 메시지가 도착하면 워크플로 인스턴스가 다시 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-113">If a correlated message arrives, the workflow instance becomes active again.</span></span>

- <span data-ttu-id="6524c-114">워크플로 인스턴스가 처음으로 유지되기 전에 워크플로 인스턴스에서 예외가 발생한 경우.</span><span class="sxs-lookup"><span data-stu-id="6524c-114">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="6524c-115">반환되는 <xref:System.Activities.UnhandledExceptionAction>에 따라 다음과 같은 시나리오가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-115">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>

  - <span data-ttu-id="6524c-116"><xref:System.Activities.UnhandledExceptionAction>이 <xref:System.Activities.UnhandledExceptionAction.Abort>로 설정된 경우: 예외가 발생하면 서비스 배포 정보가 인스턴스 저장소에 기록되고 워크플로 인스턴스가 메모리에서 언로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-116"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="6524c-117">워크플로 인스턴스는 비지속형 상태로 남아 있으며 다시 로드될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-117">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>

  - <span data-ttu-id="6524c-118"><xref:System.Activities.UnhandledExceptionAction>이 <xref:System.Activities.UnhandledExceptionAction.Cancel> 또는 <xref:System.Activities.UnhandledExceptionAction.Terminate>로 설정된 경우: 예외가 발생하면 서비스 배포 정보가 인스턴스 저장소에 기록되고 활동 인스턴스 상태가 <xref:System.Activities.ActivityInstanceState.Closed>로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-118"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>

<span data-ttu-id="6524c-119">언로드된 비지속형 워크플로 인스턴스가 발생하는 위험을 최소화하려면 수명 주기의 초기에 워크플로를 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-119">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>

## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="6524c-120">비지속형 인스턴스의 검색 및 제거</span><span class="sxs-lookup"><span data-stu-id="6524c-120">Detection and Removal of Non-Persisted Instances</span></span>

<span data-ttu-id="6524c-121"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>는 비지속형 워크플로 인스턴스를 인스턴스 저장소에서 제거하지 않으며</span><span class="sxs-lookup"><span data-stu-id="6524c-121">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="6524c-122">비지속형 워크플로 인스턴스가 연결되어 있는 만료된 잠금 소유자도 제거하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-122">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>

<span data-ttu-id="6524c-123">관리자가 주기적으로 인스턴스 저장소에서 비지속형 인스턴스를 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-123">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="6524c-124">관리자는 이 워크플로가 상관 관계 메시지를 받지 않을 것임을 아는 한 해당 인스턴스를 인스턴스 저장소에서 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-124">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="6524c-125">예를 들어 인스턴스가 데이터베이스에 몇 달 동안 있었고 일반적으로 워크플로의 수명이 며칠 정도임을 알고 있는 경우 해당 인스턴스는 손상되어 초기화된 인스턴스라고 간주해도 무방합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-125">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>

<span data-ttu-id="6524c-126">SQL 워크플로 인스턴스 저장소에서 비지속형 인스턴스를 찾으려면 다음 SQL 쿼리를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-126">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>

- <span data-ttu-id="6524c-127">이 쿼리는 유지되지 않은 모든 인스턴스를 찾고 인스턴스의 ID와 만든 시간(UTC 시간으로 저장됨)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-127">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
  ```

- <span data-ttu-id="6524c-128">이 쿼리는 유지되지 않고 로드되지 않은 모든 인스턴스를 찾고 인스턴스의 ID와 만든 시간(UTC 시간으로 저장됨)을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-128">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>

  ```sql
  select InstanceId, CreationTime
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and CurrentMachine is NULL
  ```

- <span data-ttu-id="6524c-129">이 쿼리는 유지되지 않은 모든 일시 중단된 인스턴스를 찾고 인스턴스의 ID, 만든 시간(UTC 시간으로 저장됨), 일시 중단 이유 및 예외 이름을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-129">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>

  ```sql
  select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName
      from [System.Activities.DurableInstancing].[Instances]
      where IsInitialized = 0
          and IsSuspended = 1
  ```

<span data-ttu-id="6524c-130">비지속형 인스턴스를 삭제하는 경우 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-130">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="6524c-131">일반적으로 일시 중단되었거나 로드되지 않은 <xref:System.ServiceModel.Activities.WorkflowServiceHost>에서 만든 비지속형 인스턴스는 제거해도 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-131">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="6524c-132">이러한 특정 인스턴스는 다음 SQL 명령을 사용하고 올바른 인스턴스 ID로 대체하여 `[System.Activities.DurableInstancing].[Instances]` 뷰에서 삭제함으로써 저장소에서 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-132">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>

```sql
delete [System.Activities.DurableInstancing].[Instances]
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’
```

> [!WARNING]
> <span data-ttu-id="6524c-133">방금 만들어져서 아직 유지되지 않은 인스턴스가 포함되므로 비지속형 인스턴스를 모두 제거하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6524c-133">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
