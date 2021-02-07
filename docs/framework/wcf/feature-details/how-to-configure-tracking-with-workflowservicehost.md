---
description: '자세히 알아보기: 방법: WorkflowServiceHost를 사용 하 여 추적 구성'
title: '방법: WorkflowServiceHost를 사용하여 추적 구성'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 11c48c3989ab9b788c1e6834d8cbfe53e2b8a53e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99734830"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="fa85d-103">방법: WorkflowServiceHost를 사용하여 추적 구성</span><span class="sxs-lookup"><span data-stu-id="fa85d-103">How to: Configure Tracking with WorkflowServiceHost</span></span>

<span data-ttu-id="fa85d-104">이 항목에서는 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]에서 호스트되는 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 워크플로에 대해 추적을 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-104">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="fa85d-105">이러한 추적 기능은 Web.config 파일에서 서비스 동작을 지정하여 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-105">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="fa85d-106">구성에서 추적 구성</span><span class="sxs-lookup"><span data-stu-id="fa85d-106">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="fa85d-107"><xref:System.Activities.Tracking.EtwTrackingParticipant> `behavior` 다음 예제와 같이 구성 파일에 <> 요소를 사용 하 여를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-107">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="fa85d-108">위의 샘플에서 사용하는 구성은 단순화된 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-108">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="fa85d-109">자세한 내용은 [간소화 된 구성](../simplified-configuration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-109">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="fa85d-110">위의 구성 샘플에서는 <xref:System.Activities.Tracking.EtwTrackingParticipant>를 추가하고 추적 프로필 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-110">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="fa85d-111">추적 프로필은 `trackingProfile` <> 요소 내의 <> 요소에 생성 됩니다 `tracking` .</span><span class="sxs-lookup"><span data-stu-id="fa85d-111">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="fa85d-112">추적 프로필에는 추적 참가자가 런타임에 워크플로 인스턴스 상태가 변경될 때 발생하는 워크플로 이벤트를 구독할 수 있도록 허용하는 추적 쿼리가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-112">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="fa85d-113">다음 예제에서는 추적 프로필을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-113">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <tracking>
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
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="fa85d-114">추적 프로필에 대 한 자세한 내용은 [추적 프로필](../../windows-workflow-foundation/tracking-profiles.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-114">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="fa85d-115">일반적으로 추적 하는 방법에 대 한 자세한 내용은 [워크플로 추적 및 추적](../../windows-workflow-foundation/workflow-tracking-and-tracing.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-115">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="fa85d-116">코드에서 추적 구성</span><span class="sxs-lookup"><span data-stu-id="fa85d-116">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="fa85d-117">다음 예제와 같이 코드에서 <xref:System.Activities.Tracking.EtwTrackingParticipant> 동작을 사용하여 <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-117">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="fa85d-118">위의 코드 샘플에서는 <xref:System.Activities.Tracking.EtwTrackingParticipant>를 추가하고 추적 프로필 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-118">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="fa85d-119">추적 프로필은 `trackingProfile` `tracking` 이전 단원에 표시 된 것 처럼 <> 요소 내의 <> 요소에 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fa85d-119">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="fa85d-120">추적 프로필에 대 한 자세한 내용은 [추적 프로필](../../windows-workflow-foundation/tracking-profiles.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-120">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="fa85d-121">일반적으로 추적 하는 방법에 대 한 자세한 내용은 [워크플로 추적 및 추적](../../windows-workflow-foundation/workflow-tracking-and-tracing.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-121">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="fa85d-122">프로그래밍 방식으로 추적을 구성 하는 예제는 [워크플로에 대 한 추적 구성](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fa85d-122">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa85d-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fa85d-123">See also</span></span>

- [<span data-ttu-id="fa85d-124">WCF 서비스를 위한 단순화된 구성</span><span class="sxs-lookup"><span data-stu-id="fa85d-124">Simplified Configuration for WCF Services</span></span>](../samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="fa85d-125">워크플로 서비스</span><span class="sxs-lookup"><span data-stu-id="fa85d-125">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="fa85d-126">추적 프로필</span><span class="sxs-lookup"><span data-stu-id="fa85d-126">Tracking Profiles</span></span>](../../windows-workflow-foundation/tracking-profiles.md)
