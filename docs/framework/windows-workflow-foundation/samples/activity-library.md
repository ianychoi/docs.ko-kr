---
title: 활동 라이브러리
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: 1a0c289315d7181645573098916788f18493abb8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245708"
---
# <a name="activity-library"></a><span data-ttu-id="8b736-102">활동 라이브러리</span><span class="sxs-lookup"><span data-stu-id="8b736-102">Activity Library</span></span>

<span data-ttu-id="8b736-103">이 섹션에는 WF (Windows Workflow Foundation)의 고급 사용자 지정 작업을 보여 주는 샘플이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8b736-104">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="8b736-104">In This Section</span></span>

 [<span data-ttu-id="8b736-105">SendMail 사용자 지정 활동</span><span class="sxs-lookup"><span data-stu-id="8b736-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="8b736-106">워크플로 애플리케이션 내에서 사용하기 위해 <xref:System.Activities.AsyncCodeActivity>로부터 파생되는 사용자 지정 활동을 만들어 SMTP를 사용하여 메일을 보내는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="8b736-107">Throttled Parallel ForEach</span><span class="sxs-lookup"><span data-stu-id="8b736-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="8b736-108">`ThrottleParallelForEach` 활동이 실행할 동시 분기 수를 제한하는 동시 비율을 설정하도록 허용한다는 점만 제외하고 <xref:System.Activities.Statements.ParallelForEach%601> 활동과 어떻게 비슷한지를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="8b736-109">Database Access Activities</span><span class="sxs-lookup"><span data-stu-id="8b736-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="8b736-110">데이터베이스에 액세스 하 여 정보를 검색 하거나 수정 하 고 [ADO.NET](../../data/adonet/index.md) 를 사용 하 여 데이터베이스에 액세스할 수 있도록 하는 활동을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="8b736-111">.NET Framework 4.5의 구체화된 정책 작업</span><span class="sxs-lookup"><span data-stu-id="8b736-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="8b736-112">ExternalizedPolicy4 활동을 통해 wf <xref:System.Workflow.Activities.Rules.RuleSet> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 3.5에서 제공 되는 규칙 엔진을 사용 하 여 (wf 4.5)의 Windows Workflow Foundation에서 .NET Framework 3.5 (wf 3.5) 개체의 기존 Windows Workflow Foundation를 실행 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="8b736-113">비제네릭 ForEach</span><span class="sxs-lookup"><span data-stu-id="8b736-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="8b736-114">비제네릭 버전의 <xref:System.Activities.Statements.ForEach%601> 활동을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="8b736-115">제네릭이 아닌 ParallelForEach</span><span class="sxs-lookup"><span data-stu-id="8b736-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="8b736-116">비제네릭 버전의 <xref:System.Activities.Statements.ParallelForEach%601> 활동을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="8b736-117">WorkflowInstanceId 가져오기</span><span class="sxs-lookup"><span data-stu-id="8b736-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="8b736-118">사용자 지정 활동인 `GetWorkflowInstanceId`를 사용하여 워크플로 인스턴스 ID를 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8b736-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
