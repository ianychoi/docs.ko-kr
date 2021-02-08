---
description: '자세한 정보: 방법: WorkflowServiceHost를 사용 하 여 유휴 동작 구성'
title: '방법: WorkflowServiceHost를 사용하여 유휴 동작 구성'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1bb93652-d687-46ff-bff6-69ecdcf97437
ms.openlocfilehash: 530ab1833f3f8bb91d39b19161070bc75c45f11a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99780052"
---
# <a name="how-to-configure-idle-behavior-with-workflowservicehost"></a><span data-ttu-id="46191-103">방법: WorkflowServiceHost를 사용하여 유휴 동작 구성</span><span class="sxs-lookup"><span data-stu-id="46191-103">How to: Configure Idle Behavior with WorkflowServiceHost</span></span>

<span data-ttu-id="46191-104">워크플로 인스턴스가 <xref:System.ServiceModel.Activities.Receive> 동작을 사용하여 메시지가 전달될 때까지 기다리는 경우와 같이 워크플로는 일부 외부 자극에 의해 다시 시작되어야 하는 책갈피를 만나면 유휴 상태가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="46191-104">Workflows go idle when they encounter a bookmark that must be resumed by some external stimulus, for example when the workflow instance is waiting for a message to be delivered using a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="46191-105"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 는 서비스 인스턴스가 유휴 상태가 되는 시점과 인스턴스가 지속되거나 언로드되는 시점 사이의 기간을 지정할 수 있는 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="46191-105"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> is a behavior that allows you to specify the time between when a service instance goes idle and when the instance is persisted or unloaded.</span></span> <span data-ttu-id="46191-106">이러한 기간을 설정할 수 있는 두 가지 속성이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="46191-106">It contains two properties that enable you to set these time spans.</span></span> <span data-ttu-id="46191-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> 는 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 지속되는 때 사이의 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-107"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="46191-108"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> 는 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 언로드되는 때 사이의 시간을 지정합니다. 여기서, 언로드란 인스턴스를 인스턴스 스토어에 유지하고 메모리에서 제거하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-108"><xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> specifies the time span between when a workflow service instance goes idle and when the workflow service instance is unloaded, where unload means persisting the instance to the instance store and removing it from memory.</span></span> <span data-ttu-id="46191-109">이 항목에서는 구성 파일에서 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> 를 구성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-109">This topic explains how to configure the <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> in a configuration file.</span></span>  
  
### <a name="to-configure-workflowidlebehavior"></a><span data-ttu-id="46191-110">WorkflowIdleBehavior를 구성하려면</span><span class="sxs-lookup"><span data-stu-id="46191-110">To configure WorkflowIdleBehavior</span></span>  
  
1. <span data-ttu-id="46191-111">`workflowIdle` `behavior` 다음 예제와 같이 <> 요소 내의 <> 요소에 <> 요소를 추가 `serviceBehaviors` 합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-111">Add a <`workflowIdle`> element to the <`behavior`> element within the <`serviceBehaviors`> element as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowIdle timeToUnload="0:05:0" timeToPersist="0:04:0"/>
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     <span data-ttu-id="46191-112">`timeToUnload` 특성은 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 언로드되는 때 사이의 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-112">The `timeToUnload` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service is unloaded.</span></span> <span data-ttu-id="46191-113">`timeToPersist` 특성은 워크플로 서비스 인스턴스가 유휴 상태가 되는 때와 워크플로 서비스 인스턴스가 지속되는 때 사이의 시간을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-113">The `timeToPersist` attribute specifies the time period between when a workflow service instance goes idle and when the workflow service instance is persisted.</span></span> <span data-ttu-id="46191-114">`timeToUnload` 의 기본값은 1분입니다.</span><span class="sxs-lookup"><span data-stu-id="46191-114">The default value for `timeToUnload` is 1 minute.</span></span> <span data-ttu-id="46191-115">`timeToPersist`의 기본값은 <xref:System.TimeSpan.MaxValue>입니다.</span><span class="sxs-lookup"><span data-stu-id="46191-115">The default value for `timeToPersist` is <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="46191-116">유휴 인스턴스를 메모리에 유지하지만 견고성을 위해 지속시키려는 경우 `timeToPersist` < `timeToUnload`입니다.</span><span class="sxs-lookup"><span data-stu-id="46191-116">If you want to keep idle instances in memory but persist them for robustness, set values so that `timeToPersist` < `timeToUnload`.</span></span> <span data-ttu-id="46191-117">유휴 인스턴스가 언로드되지 않도록 하려면 `timeToUnload` 를 <xref:System.TimeSpan.MaxValue>로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-117">If you want to prevent idle instances from being unloaded, set `timeToUnload` to <xref:System.TimeSpan.MaxValue>.</span></span> <span data-ttu-id="46191-118">에 대 한 자세한 내용은 <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior> [워크플로 서비스 호스트 확장성](workflow-service-host-extensibility.md) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46191-118">For more information about <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>, see [Workflow Service Host Extensibility](workflow-service-host-extensibility.md)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="46191-119">위의 샘플에서 사용하는 구성은 단순화된 구성입니다.</span><span class="sxs-lookup"><span data-stu-id="46191-119">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="46191-120">자세한 내용은 [간소화 된 구성](../simplified-configuration.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="46191-120">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
### <a name="to-change-idle-behavior-in-code"></a><span data-ttu-id="46191-121">코드에서 유휴 동작을 변경하려면</span><span class="sxs-lookup"><span data-stu-id="46191-121">To change idle behavior in code</span></span>  
  
- <span data-ttu-id="46191-122">다음 예제에서는 프로그래밍 방식으로 지속 및 언로드 전에 대기할 시간을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="46191-122">The following example changes the time to wait before persisting and unloading programmatically.</span></span>  
  
     [!code-csharp[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/wf_svchost_idle_persist/cs/source.cs#1)]
     [!code-vb[Wf_SvcHost_Idle_persist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/wf_svchost_idle_persist/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="46191-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="46191-123">See also</span></span>

- [<span data-ttu-id="46191-124">워크플로 서비스 호스트 확장</span><span class="sxs-lookup"><span data-stu-id="46191-124">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)
- [<span data-ttu-id="46191-125">단순화된 구성</span><span class="sxs-lookup"><span data-stu-id="46191-125">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="46191-126">워크플로 서비스</span><span class="sxs-lookup"><span data-stu-id="46191-126">Workflow Services</span></span>](workflow-services.md)
