---
description: '자세히 알아보기: 추적 프로필'
title: 추적 프로필
ms.date: 03/30/2017
ms.assetid: 22682566-1cd9-4672-9791-fb3523638e18
ms.openlocfilehash: 9748f0452a1699e08760372f826f2458d82f4b79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755150"
---
# <a name="tracking-profiles"></a><span data-ttu-id="6e270-103">추적 프로필</span><span class="sxs-lookup"><span data-stu-id="6e270-103">Tracking Profiles</span></span>

<span data-ttu-id="6e270-104">추적 프로필에는 추적 참가자가 런타임에 워크플로 인스턴스 상태가 변경될 때 발생하는 워크플로 이벤트를 구독할 수 있도록 허용하는 추적 쿼리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-104">Tracking profiles contain tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span>

## <a name="tracking-profiles"></a><span data-ttu-id="6e270-105">추적 프로필</span><span class="sxs-lookup"><span data-stu-id="6e270-105">Tracking Profiles</span></span>

<span data-ttu-id="6e270-106">워크플로 인스턴스에 내보낼 추적 정보를 지정하는 데 사용되는 추적 프로필입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-106">Tracking profiles are used to specify which tracking information is emitted for a workflow instance.</span></span> <span data-ttu-id="6e270-107">프로필을 지정하지 않으면 모든 추적 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-107">If no profile is specified, then all tracking events are emitted.</span></span> <span data-ttu-id="6e270-108">프로필을 지정하면 프로필에 지정된 추적 이벤트를 내보냅니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-108">If a profile is specified, then the tracking events specified in the profile will be emitted.</span></span> <span data-ttu-id="6e270-109">모니터링 요구 사항에 따라 워크플로에서 상위 수준의 상태 변경 내용 중 작은 부분만 구독하는 매우 개괄적인 프로필을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-109">Depending on your monitoring requirements, you may write a profile that is very general, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="6e270-110">이와 반대로 이후에 세부 실행 흐름을 다시 작성할 수 있을 정도로 상세한 결과 이벤트를 포함하는 아주 자세한 프로필을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-110">Conversely, you may create a very detailed profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>

<span data-ttu-id="6e270-111">추적 프로필은 표준 .NET Framework 구성 파일 내에 XML 요소로 매니페스트 되거나 코드에 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-111">Tracking profiles manifest themselves as XML elements within a standard .NET Framework configuration file or specified in code.</span></span> <span data-ttu-id="6e270-112">다음 예제에서는 추적 참가자가 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 및 `Started` 워크플로 이벤트를 구독할 수 있도록 하는 구성 파일의 `Completed` 추적 프로필을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-112">The following example is of a [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>

```xml
<system.serviceModel>
    ...
    <tracking>
     <profiles>
      <trackingProfile name="Sample Tracking Profile">
        <workflow activityDefinitionId="*">
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="Started"/>
                <state name="Completed"/>
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
    ...
</system.serviceModel>
```

<span data-ttu-id="6e270-113">다음 예제에서는 코드를 사용하여 만든 동일한 추적 프로필을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-113">The following example shows the equivalent tracking profile created using code.</span></span>

```csharp
TrackingProfile profile = new TrackingProfile()
{
    Name = "CustomTrackingProfile",
    Queries =
    {
        new WorkflowInstanceQuery()
        {
            // Limit workflow instance tracking records for started and
            // completed workflow states.
            States = { WorkflowInstanceStates.Started, WorkflowInstanceStates.Completed },
        }
    }
};
```

<span data-ttu-id="6e270-114">추적 레코드는 <xref:System.Activities.Tracking.ImplementationVisibility> 특성을 사용하여 추적 프로필의 표시 모드를 통해 필터링됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-114">Tracking records are filtered through the visibility mode within a tracking profile by using the <xref:System.Activities.Tracking.ImplementationVisibility> attribute.</span></span> <span data-ttu-id="6e270-115">복합 활동은 구현을 구성하는 다른 활동을 포함하는 최상위 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-115">A composite activity is a top-level activity that contains other activities that form its implementation.</span></span> <span data-ttu-id="6e270-116">표시 모드는 구현을 구성하는 활동을 추적할지 여부를 지정하기 위하여 워크플로 활동 내의 복합 활동에서 내보내는 추적 레코드를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-116">The visibility mode specifies the tracking records emitted from composite activities within a workflow activity, to specify if activities that form the implementation are being tracked.</span></span> <span data-ttu-id="6e270-117">표시 모드는 추적 프로필 수준에서 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-117">The visibility mode applies at the tracking profile level.</span></span> <span data-ttu-id="6e270-118">워크플로의 개별 활동에 대한 추적 레코드 필터링은 추적 프로필 내에서 쿼리에 의해 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-118">The filtering of tracking records for individual activities within a workflow is controlled by the queries within the tracking profile.</span></span> <span data-ttu-id="6e270-119">자세한 내용은이 문서의 **추적 프로필 쿼리 형식** 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6e270-119">For more information, see the **Tracking Profile Query Types** section in this document.</span></span>

<span data-ttu-id="6e270-120">추적 프로필의 `implementationVisibility` 특성은 두 가지 표시 모드(`RootScope` 및 `All`)를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-120">The two visibility modes specified by the `implementationVisibility` attribute in the tracking profile are `RootScope` and `All`.</span></span> <span data-ttu-id="6e270-121">복합 활동이 워크플로의 루트가 아닌 경우 `RootScope` 모드를 사용하면 활동의 구현을 구성하는 활동에 대한 추적 레코드가 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-121">Using the `RootScope` mode suppresses the tracking records for activities that form the implementation of an activity in the case where a composite activity is not the root of a workflow.</span></span> <span data-ttu-id="6e270-122">즉, 다른 활동을 사용하여 구현되는 활동이 워크플로에 추가되고 `implementationVisibility`가 RootScope로 설정된 경우에는 해당 복합 활동의 최상위 활동만 추적됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-122">This implies that, when an activity that is implemented using other activities is added to a workflow, and the `implementationVisibility` set to RootScope, only the top-level activity within that composite activity is tracked.</span></span> <span data-ttu-id="6e270-123">활동이 워크플로의 루트인 경우 활동 구현이 워크플로 자체이고 구현 단계를 구성하는 활동에 대한 추적 레코드가 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-123">If an activity is the root of the workflow, then the implementation of the activity is the workflow itself and tracking records are emitted for activities that form the implementation.</span></span> <span data-ttu-id="6e270-124">모두 모드에서는 루트 활동과 모든 복합 활동에 대해 모든 추적 레코드가 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-124">Using the All mode permits all tracking records to be emitted for the root activity and all its composite activities.</span></span>

<span data-ttu-id="6e270-125">예를 들어, *MyActivity* 는 *Activity1* 및 *Activity2* 라는 두 개의 작업을 포함 하는 복합 활동입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-125">For example, suppose *MyActivity* is a composite activity whose implementation contains two activities, *Activity1* and *Activity2*.</span></span> <span data-ttu-id="6e270-126">이 활동을 워크플로에 추가 하 고 추적을로 설정 하 여 추적을 사용 하도록 `implementationVisibility` 설정 하면 `RootScope` *MyActivity* 에 대해서만 추적 레코드가 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-126">When this activity is added to a workflow and tracking is enabled with a tracking profile with `implementationVisibility` set to `RootScope`, tracking records are emitted only for *MyActivity*.</span></span> <span data-ttu-id="6e270-127">그러나 활동 *Activity1* 및 *Activity2* 에 대 한 레코드는 내보내지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-127">However, no records are emitted for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="6e270-128">그러나 `implementationVisibility` 추적 프로필에 대 한 특성이로 설정 된 경우 MyActivity 뿐만 아니라 `All` 작업 *Activity1* 및 *Activity2* 에 대 한 추적 레코드가 내보내집니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-128">However, if the `implementationVisibility` attribute for the tracking profile is  set to `All`, then tracking records are emitted not only for *MyActivity*, but also for activities *Activity1* and *Activity2*.</span></span>

<span data-ttu-id="6e270-129">`implementationVisibility` 플래그가 적용되는 추적 레코드 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-129">The `implementationVisibility` flag applies to following tracking record types:</span></span>

- <span data-ttu-id="6e270-130">ActivityStateRecord</span><span class="sxs-lookup"><span data-stu-id="6e270-130">ActivityStateRecord</span></span>

- <span data-ttu-id="6e270-131">FaultPropagationRecord</span><span class="sxs-lookup"><span data-stu-id="6e270-131">FaultPropagationRecord</span></span>

- <span data-ttu-id="6e270-132">CancelRequestedRecord</span><span class="sxs-lookup"><span data-stu-id="6e270-132">CancelRequestedRecord</span></span>

- <span data-ttu-id="6e270-133">ActivityScheduledRecord</span><span class="sxs-lookup"><span data-stu-id="6e270-133">ActivityScheduledRecord</span></span>

> [!NOTE]
> <span data-ttu-id="6e270-134">활동 구현에서 내보내는 CustomTrackingRecords는 implementationVisibility 설정에 의해 필터링되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-134">CustomTrackingRecords emitted from activity implementation are not filtered out by the implementationVisibility setting.</span></span>

<span data-ttu-id="6e270-135">`implementationVisibility` 기능은 코드의 추적 프로필에서 다음과 같이 <xref:System.Activities.Tracking.ImplementationVisibility.RootScope>로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-135">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.RootScope> on the tracking profile in code as follows:</span></span>

```csharp
TrackingProfile sampleTrackingProfile = new TrackingProfile()
{
    Name = "Sample Tracking Profile",
    ImplementationVisibility = ImplementationVisibility.RootScope
};
```

<span data-ttu-id="6e270-136">`implementationVisibility` 기능은 구성 파일의 추적 프로필에서 다음과 같이 <xref:System.Activities.Tracking.ImplementationVisibility.All>로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-136">The `implementationVisibility` functionality is specified as <xref:System.Activities.Tracking.ImplementationVisibility.All> on the tracking profile in a configuration file as follows:</span></span>

```xml
<tracking>
      <profiles>
        <trackingProfile name="Shipping Monitoring" implementationVisibility="All">
          <workflow activityDefinitionId="*">
...
         </workflow>
        </trackingProfile>
      </profiles>
</tracking>
```

<span data-ttu-id="6e270-137">추적 프로필의 `ImplementationVisibility` 설정은 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-137">The `ImplementationVisibility` setting on the tracking profile is optional.</span></span> <span data-ttu-id="6e270-138">기본적으로 이 값은 `RootScope`로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-138">By default, its value is set to `RootScope`.</span></span> <span data-ttu-id="6e270-139">또한 이 특성 값은 대/소문자가 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-139">The values for this attribute are also case-sensitive.</span></span>

### <a name="tracking-profile-query-types"></a><span data-ttu-id="6e270-140">추적 프로필 쿼리 형식</span><span class="sxs-lookup"><span data-stu-id="6e270-140">Tracking Profile Query Types</span></span>

<span data-ttu-id="6e270-141">추적 프로필은 특정 추적 레코드에 대한 워크플로 런타임을 쿼리할 수 있는 추적 레코드에 대한 선언적 구독으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-141">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="6e270-142"><xref:System.Activities.Tracking.TrackingRecord> 개체의 다양한 클래스를 구독할 수 있는 여러 쿼리 형식이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-142">There are several query types that allow you subscribe to different classes of <xref:System.Activities.Tracking.TrackingRecord> objects.</span></span> <span data-ttu-id="6e270-143">추적 프로필은 구성이나 코드를 통해 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-143">Tracking profiles can be specified in configuration or through code.</span></span> <span data-ttu-id="6e270-144">가장 일반적인 쿼리 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-144">Here are the most common query types:</span></span>

- <span data-ttu-id="6e270-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - 앞에서 설명한 `Started` 및 `Completed`와 같은 워크플로 인스턴스 수명 주기 변경 내용을 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-145"><xref:System.Activities.Tracking.WorkflowInstanceQuery> - Use this to track workflow instance life cycle changes like the previously-demonstrated `Started` and `Completed`.</span></span> <span data-ttu-id="6e270-146"><xref:System.Activities.Tracking.WorkflowInstanceQuery>는 다음 <xref:System.Activities.Tracking.TrackingRecord> 개체를 구독하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-146">The <xref:System.Activities.Tracking.WorkflowInstanceQuery> is used to subscribe to the following <xref:System.Activities.Tracking.TrackingRecord> objects:</span></span>

  - <xref:System.Activities.Tracking.WorkflowInstanceRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceAbortedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceUnhandledExceptionRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceTerminatedRecord>

  - <xref:System.Activities.Tracking.WorkflowInstanceSuspendedRecord>

  <span data-ttu-id="6e270-147">구독 가능한 상태는 <xref:System.Activities.Tracking.WorkflowInstanceStates> 클래스에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-147">The states that can be subscribed to are specified in the <xref:System.Activities.Tracking.WorkflowInstanceStates> class.</span></span>

  <span data-ttu-id="6e270-148">다음 예제에서는 `Started`를 사용하여 <xref:System.Activities.Tracking.WorkflowInstanceQuery> 인스턴스에 대한 워크플로 인스턴스 수준 추적 레코드를 구독하는 데 사용되는 구성 또는 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-148">The configuration or code used to subscribe to workflow instance-level tracking records for the `Started` instance state using the <xref:System.Activities.Tracking.WorkflowInstanceQuery> is shown in the following example.</span></span>

  ```xml
  <workflowInstanceQueries>
      <workflowInstanceQuery>
        <states>
          <state name="Started"/>
        </states>
      </workflowInstanceQuery>
  </workflowInstanceQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new WorkflowInstanceQuery()
          {
              States = { WorkflowInstanceStates.Started}
          }
      }
  };
  ```

- <span data-ttu-id="6e270-149"><xref:System.Activities.Tracking.ActivityStateQuery> - 워크플로 인스턴스를 구성하는 활동에 대한 수명 주기 변경 내용을 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-149"><xref:System.Activities.Tracking.ActivityStateQuery> - Use this to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="6e270-150">예를 들어, 워크플로 인스턴스 내에서 "전자 메일 보내기" 작업이 완료 될 때마다 추적 해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-150">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="6e270-151">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.ActivityStateRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-151">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityStateRecord> objects.</span></span> <span data-ttu-id="6e270-152">구독하기 위해 사용 가능한 상태는 <xref:System.Activities.Tracking.ActivityStates>에서 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-152">The available states to subscribe to are specified in <xref:System.Activities.Tracking.ActivityStates>.</span></span>

  <span data-ttu-id="6e270-153">다음 예제에서는 <xref:System.Activities.Tracking.ActivityStateQuery> 활동에 대해 `SendEmailActivity`를 사용하는 활동 상태 추적 레코드를 구독하는 데 사용되는 구성과 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-153">The configuration and code used to subscribe activity state tracking records that use the <xref:System.Activities.Tracking.ActivityStateQuery> for the `SendEmailActivity` activity is shown in the following example.</span></span>

  ```xml
  <activityStateQueries>
    <activityStateQuery activityName="SendEmailActivity">
      <states>
        <state name="Closed"/>
      </states>
    </activityStateQuery>
  </activityStateQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityStateQuery()
          {
              ActivityName = "SendEmailActivity",
              States = { ActivityStates.Closed }
          }
      }
  };
  ```

  > [!NOTE]
  > <span data-ttu-id="6e270-154">여러 activityStateQuery 요소에 동일한 이름을 사용할 경우 마지막 요소의 상태만 추적 프로필에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-154">If multiple activityStateQuery elements have the same name, only the states in the last element are used in the tracking profile.</span></span>

- <span data-ttu-id="6e270-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - 이 쿼리를 사용하여 부모 활동에 의해 실행이 예약된 활동을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-155"><xref:System.Activities.Tracking.ActivityScheduledQuery> - This query allows you to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="6e270-156">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.ActivityScheduledRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-156">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.ActivityScheduledRecord> objects.</span></span>

  <span data-ttu-id="6e270-157">다음 예제에서는 `SendEmailActivity`를 사용하여 예약된 <xref:System.Activities.Tracking.ActivityScheduledQuery> 자식 활동 관련 레코드를 구독하는 데 사용되는 구성과 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-157">The configuration and code used to subscribe to records related to the `SendEmailActivity` child activity being scheduled using the <xref:System.Activities.Tracking.ActivityScheduledQuery> is shown in the following example.</span></span>

  ```xml
  <activityScheduledQueries>
    <activityScheduledQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </activityScheduledQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new ActivityScheduledQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="6e270-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - 활동에서 발생하는 오류 처리를 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-158"><xref:System.Activities.Tracking.FaultPropagationQuery> - Use this to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="6e270-159">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.FaultPropagationRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-159">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.FaultPropagationRecord> objects.</span></span>

  <span data-ttu-id="6e270-160">다음 예제에서는 <xref:System.Activities.Tracking.FaultPropagationQuery>를 사용하여 오류 전파 관련 레코드를 구독하는 데 사용되는 구성과 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-160">The configuration and code used to subscribe to records related to fault propagation using <xref:System.Activities.Tracking.FaultPropagationQuery> is shown in the following example.</span></span>

  ```xml
  <faultPropagationQueries>
    <faultPropagationQuery faultSourceActivityName="SendEmailActivity" faultHandlerActivityName="NotificationsFaultHandler" />
  </faultPropagationQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new FaultPropagationQuery()
          {
              FaultSourceActivityName = "SendEmailActivity",
              FaultHandlerActivityName = "NotificationsFaultHandler"
          }
      }
  };
  ```

- <span data-ttu-id="6e270-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - 부모 활동에 의한 자식 활동 취소 요청을 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-161"><xref:System.Activities.Tracking.CancelRequestedQuery> - Use this to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="6e270-162">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.CancelRequestedRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-162">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CancelRequestedRecord> objects.</span></span>

  <span data-ttu-id="6e270-163">을 사용 하 여 활동 취소와 관련 된 레코드를 구독 하는 데 사용 되는 구성 및 코드는 <xref:System.Activities.Tracking.CancelRequestedQuery> 다음 예제에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-163">The configuration and code used to subscribe to records related to activity cancellation using <xref:System.Activities.Tracking.CancelRequestedQuery> is shown in the following example.</span></span>

  ```xml
  <cancelRequestedQueries>
    <cancelRequestedQuery activityName="ProcessNotificationsActivity" childActivityName="SendEmailActivity" />
  </cancelRequestedQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CancelRequestedQuery()
          {
              ActivityName = "ProcessNotificationsActivity",
              ChildActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="6e270-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - 코드 활동에서 정의한 이벤트를 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-164"><xref:System.Activities.Tracking.CustomTrackingQuery> - Use this to track events that you define in your code activities.</span></span> <span data-ttu-id="6e270-165">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.CustomTrackingRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-165">The query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.CustomTrackingRecord> objects.</span></span>

  <span data-ttu-id="6e270-166">다음 예제에서는 <xref:System.Activities.Tracking.CustomTrackingQuery>를 사용하여 사용자 지정 추적 레코드 관련 레코드를 구독하는 데 사용되는 구성과 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-166">The configuration and code used to subscribe to records related to custom tracking records using <xref:System.Activities.Tracking.CustomTrackingQuery> is shown in the following example.</span></span>

  ```xml
  <customTrackingQueries>
    <customTrackingQuery name="EmailAddress" activityName="SendEmailActivity" />
  </customTrackingQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new CustomTrackingQuery()
          {
              Name = "EmailAddress",
              ActivityName = "SendEmailActivity"
          }
      }
  };
  ```

- <span data-ttu-id="6e270-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - 워크플로 인스턴스 내의 책갈피 다시 시작을 추적하려면 이 쿼리 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-167"><xref:System.Activities.Tracking.BookmarkResumptionQuery> - Use this to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="6e270-168">이 쿼리는 <xref:System.Activities.Tracking.TrackingParticipant>가 <xref:System.Activities.Tracking.BookmarkResumptionRecord> 개체를 구독하는 데 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-168">This query is necessary for a <xref:System.Activities.Tracking.TrackingParticipant> to subscribe to <xref:System.Activities.Tracking.BookmarkResumptionRecord> objects.</span></span>

  <span data-ttu-id="6e270-169">다음 예제에서는 <xref:System.Activities.Tracking.BookmarkResumptionQuery>를 사용하여 책갈피 다시 시작 관련 레코드를 구독하는 데 사용되는 구성과 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-169">The configuration and code used to subscribe to records related to bookmark resumption using <xref:System.Activities.Tracking.BookmarkResumptionQuery> is shown in the following example.</span></span>

  ```xml
  <bookmarkResumptionQueries>
    <bookmarkResumptionQuery name="SentEmailBookmark" />
  </bookmarkResumptionQueries>
  ```

  ```csharp
  TrackingProfile sampleTrackingProfile = new TrackingProfile()
  {
      Name = "Sample Tracking Profile",
      Queries =
      {
          new BookmarkResumptionQuery()
          {
              Name = "sentEmailBookmark"
          }
      }
  };
  ```

### <a name="annotations"></a><span data-ttu-id="6e270-170">주석</span><span class="sxs-lookup"><span data-stu-id="6e270-170">Annotations</span></span>

<span data-ttu-id="6e270-171">주석을 사용하여 빌드 시간 후에 구성될 수 있는 값으로 추적 레코드에 임의 태그를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-171">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="6e270-172">예를 들어 여러 워크플로 간에 여러 추적 레코드를 "Mail Server" = = "Mail Server1"로 태그를 지정 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-172">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="6e270-173">이렇게 하면 나중에 추적 레코드를 쿼리할 때 이 태그를 사용하여 모든 레코드를 쉽게 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-173">This makes it easy to find all records with this tag when querying tracking records later.</span></span>

<span data-ttu-id="6e270-174">이렇게 하려면 다음 예제와 같이 추적 쿼리에 주석을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-174">To accomplish this, an annotation is added to a tracking query as shown in the following example.</span></span>

```xml
<activityStateQuery activityName="SendEmailActivity">
  <states>
    <state name="Closed"/>
  </states>
  <annotations>
    <annotation name="MailServer" value="Mail Server1"/>
  </annotations>
</activityStateQuery>
```

### <a name="how-to-create-a-tracking-profile"></a><span data-ttu-id="6e270-175">추적 프로필 생성 방법</span><span class="sxs-lookup"><span data-stu-id="6e270-175">How to Create a Tracking Profile</span></span>

<span data-ttu-id="6e270-176">추적 쿼리 요소는 XML 구성 파일 또는 코드를 사용 하 여 추적 프로필을 만드는 데 사용 됩니다 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6e270-176">Tracking query elements are used to create a tracking profile using either an XML configuration file or [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] code.</span></span> <span data-ttu-id="6e270-177">다음은 구성 파일을 사용하여 만든 추적 프로필의 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-177">Here is an example of a tracking profile created using a configuration file.</span></span>

```xml
<system.serviceModel>
  <tracking>
    <profiles>
      <trackingProfile name="Sample Tracking Profile ">
        <workflow activityDefinitionId="*">
          <!--Specify the tracking profile query elements to subscribe for tracking records-->
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>
```

> [!WARNING]
> <span data-ttu-id="6e270-178">워크플로 서비스 호스트를 사용하는 WF의 경우 일반적으로 구성 파일을 사용하여 추적 프로필을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-178">For a WF using the Workflow service host, the tracking profile is typically created using a configuration file.</span></span> <span data-ttu-id="6e270-179">추적 프로필 및 추적 쿼리 API를 사용하여 코드를 통해 추적 프로필을 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-179">It is also possible to create a tracking profile with code using the tracking profile and tracking query API.</span></span>

<span data-ttu-id="6e270-180">XML 구성 파일로 구성된 프로필은 동작 확장을 사용하여 추적 참가자에게 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-180">A profile configured as an XML configuration file is applied to a tracking participant using a behavior extension.</span></span> <span data-ttu-id="6e270-181">이는 나중에 [워크플로에 대 한 추적 구성](configuring-tracking-for-a-workflow.md)섹션에 설명 된 대로 WorkflowServiceHost에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-181">This is added to a WorkflowServiceHost as described in the later section [Configuring Tracking for a Workflow](configuring-tracking-for-a-workflow.md).</span></span>

<span data-ttu-id="6e270-182">호스트에서 내보내는 추적 레코드의 자세한 정도는 추적 프로필의 구성 설정에 따라 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-182">The verbosity of the tracking records emitted by the host is determined by configuration settings within the tracking profile.</span></span> <span data-ttu-id="6e270-183">추적 참가자는 쿼리를 추적 프로필에 추가하여 추적 레코드를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-183">A tracking participant subscribes to tracking records by adding queries to a tracking profile.</span></span> <span data-ttu-id="6e270-184">모든 추적 레코드를 구독 하려면 추적 프로필에서 \* 각 쿼리의 이름 필드에 ""를 사용 하 여 모든 추적 쿼리를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-184">To subscribe to all tracking records, the tracking profile needs to specify all tracking queries using "\*" in the name fields in each of the queries.</span></span>

<span data-ttu-id="6e270-185">다음은 추적 프로필의 일반적인 몇 가지 예입니다.</span><span class="sxs-lookup"><span data-stu-id="6e270-185">Here are some of the common examples of tracking profiles.</span></span>

- <span data-ttu-id="6e270-186">워크플로 인스턴스 레코드 및 오류를 가져오는 추적 프로필</span><span class="sxs-lookup"><span data-stu-id="6e270-186">A tracking profile to obtain workflow instance records and faults.</span></span>

  ```xml
  <trackingProfile name="Instance and Fault Records">
    <workflow activityDefinitionId="*">
      <workflowInstanceQueries>
        <workflowInstanceQuery>
          <states>
            <state name="*" />
          </states>
        </workflowInstanceQuery>
      </workflowInstanceQueries>
      <activityStateQueries>
        <activityStateQuery activityName="*">
          <states>
            <state name="Faulted"/>
          </states>
        </activityStateQuery>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
  ```

- <span data-ttu-id="6e270-187">모든 사용자 지정 추적 레코드를 가져오는 추적 프로필</span><span class="sxs-lookup"><span data-stu-id="6e270-187">A tracking profile to obtain all custom tracking records.</span></span>

  ```xml
  <trackingProfile name="Instance_And_Custom_Records">
    <workflow activityDefinitionId="*">
      <customTrackingQueries>
        <customTrackingQuery name="*" activityName="*" />
      </customTrackingQueries>
    </workflow>
  </trackingProfile>
  ```

## <a name="see-also"></a><span data-ttu-id="6e270-188">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6e270-188">See also</span></span>

- [<span data-ttu-id="6e270-189">SQL 추적</span><span class="sxs-lookup"><span data-stu-id="6e270-189">SQL Tracking</span></span>](./samples/sql-tracking.md)
- <span data-ttu-id="6e270-190">[Windows Server App Fabric 모니터링](/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6e270-190">[Windows Server App Fabric Monitoring](/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="6e270-191">[App Fabric을 사용 하 여 응용 프로그램 모니터링](/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6e270-191">[Monitoring Applications with App Fabric](/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
