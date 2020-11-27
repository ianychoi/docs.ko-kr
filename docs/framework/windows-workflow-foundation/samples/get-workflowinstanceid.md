---
title: WorkflowInstanceId 가져오기
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: db06b30f24a2d620406b3e6a35bba3a1fca70a9c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251544"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="13d22-102">WorkflowInstanceId 가져오기</span><span class="sxs-lookup"><span data-stu-id="13d22-102">Get WorkflowInstanceId</span></span>

<span data-ttu-id="13d22-103">이 샘플에서는 사용자 지정 활동인 `GetWorkflowInstanceId`를 사용하여 워크플로 인스턴스 ID를 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="13d22-104">데모</span><span class="sxs-lookup"><span data-stu-id="13d22-104">Demonstrates</span></span>  

 <span data-ttu-id="13d22-105">사용자 지정 활동 개발, 워크플로 인스턴스에 액세스하는 방법</span><span class="sxs-lookup"><span data-stu-id="13d22-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="13d22-106">토론(Discussion)</span><span class="sxs-lookup"><span data-stu-id="13d22-106">Discussion</span></span>  

 <span data-ttu-id="13d22-107">실행 중인 워크플로의 인스턴스 ID를 가져오려면 코드를 작성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="13d22-108">완전히 선언적인 워크플로를 작성하려면 워크플로 인스턴스 ID를 반환할 수 있는 활동이 필요합니다. 그래야만 워크플로에서 해당 활동을 참조하여 완전히 선언적인 워크플로 작성 환경을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="13d22-109">인스턴스 ID에 액세스해야 하는 시나리오에는 여러 가지가 있습니다. 예를 들어 로깅 또는 감사를 위한 시나리오도 여기에 해당하며, (가령 SendReply 활동 내에 이 활동을 사용하는 등) 나중에 연결하기 위해 인스턴스 ID를 클라이언트에 다시 제공하여 애플리케이션 수준의 상관 관계를 만드는 시나리오도 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="13d22-110">`GetWorkflowInstanceId`는 <xref:System.Activities.CodeActivity%601>로 구현됩니다. 이는 <xref:System.Guid> 형식의 값을 반환해야 하고 워크플로의 인스턴스 ID를 가져오기 위해 <xref:System.Activities.CodeActivityContext>에 액세스해야 하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="13d22-111">그 구현은 비교적 기본적입니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-111">Its implementation is fairly basic.</span></span>  
  
```csharp  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
    protected override Guid Execute(CodeActivityContext context)  
    {  
        return context.WorkflowInstanceId;  
    }  
}
```  
  
> [!IMPORTANT]
> <span data-ttu-id="13d22-112">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="13d22-113">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="13d22-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="13d22-114">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="13d22-115">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="13d22-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
