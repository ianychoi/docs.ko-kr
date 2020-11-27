---
title: WorkflowHostingEndpoint에 대한 책갈피 확인자
ms.date: 03/30/2017
ms.assetid: 97fd5816-935e-4625-ad04-e6f6befa07de
ms.openlocfilehash: 6bcf1c1ac7c0ac9e385c4259ba085ab63afd7cfa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274610"
---
# <a name="bookmark-resolver-for-workflowhostingendpoint"></a><span data-ttu-id="d17ec-102">WorkflowHostingEndpoint에 대한 책갈피 확인자</span><span class="sxs-lookup"><span data-stu-id="d17ec-102">Bookmark Resolver for WorkflowHostingEndpoint</span></span>

<span data-ttu-id="d17ec-103">이 샘플에서는 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>를 <xref:System.ServiceModel.Activities.WorkflowServiceHost>와 함께 사용하여 워크플로 인스턴스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-103">This sample demonstrates how the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> can be used with <xref:System.ServiceModel.Activities.WorkflowServiceHost> to create workflow instances.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d17ec-104">데모</span><span class="sxs-lookup"><span data-stu-id="d17ec-104">Demonstrates</span></span>  

 <span data-ttu-id="d17ec-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span><span class="sxs-lookup"><span data-stu-id="d17ec-105"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>, <xref:System.ServiceModel.Activities.WorkflowServiceHost></span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d17ec-106">토론(Discussion)</span><span class="sxs-lookup"><span data-stu-id="d17ec-106">Discussion</span></span>  

 <span data-ttu-id="d17ec-107">이 샘플에서는 <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>를 사용하여 워크플로 인스턴스를 만듭니다. 이 워크플로 인스턴스는 <xref:System.ServiceModel.Activities.WorkflowServiceHost>를 통해 호스트됩니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-107">This sample uses the <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> to create workflow instances hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="d17ec-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint>는 다음 시나리오에 사용할 수 있는 <xref:System.ServiceModel.Activities.WorkflowServiceHost>에 대한 확장성 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-108"><xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> is an extensibility point for <xref:System.ServiceModel.Activities.WorkflowServiceHost> that can be used in the following scenarios:</span></span>  
  
- <span data-ttu-id="d17ec-109">새 워크플로 인스턴스 만들기</span><span class="sxs-lookup"><span data-stu-id="d17ec-109">Creating new workflow instances.</span></span>  
  
- <span data-ttu-id="d17ec-110"><xref:System.ServiceModel.Activities.WorkflowServiceHost>에 호스트되는 워크플로 인스턴스에 대한 책갈피 다시 시작</span><span class="sxs-lookup"><span data-stu-id="d17ec-110">Resuming bookmarks on workflow instance hosted in a <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="d17ec-111">여기에 포함되어 있는 샘플 엔드포인트는 워크플로를 만들고 인스턴스 ID를 반환하거나 특정 ID의 인스턴스를 만드는 작업을 제공하는 계약을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-111">The sample endpoint that is included exposes a contract that provides operations to create a workflow and returns the instance ID or creates an instance with a specific ID.</span></span> <span data-ttu-id="d17ec-112">샘플 콘솔 애플리케이션에서는 워크플로 정의를 사용하여 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 인스턴스를 만들고 호스트에 `CreationEndpoint`를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-112">The sample console application creates a <xref:System.ServiceModel.Activities.WorkflowServiceHost> instance with a workflow definition and adds a `CreationEndpoint` to the host.</span></span> <span data-ttu-id="d17ec-113">그런 다음 엔드포인트에 대해 `Create` 작업을 호출하여 새 워크플로 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-113">It then calls the `Create` operation on the endpoint to create a new workflow instance.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d17ec-114">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="d17ec-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d17ec-115">솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-115">Build the solution.</span></span>  
  
2. <span data-ttu-id="d17ec-116">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-116">Run the application.</span></span> <span data-ttu-id="d17ec-117">워크플로 인스턴스를 만들 때 인스턴스 ID를 포함하는 메시지가 `CreationEndpoint` 콘솔에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-117">The `CreationEndpoint` console shows a message that includes the instance ID when the workflow instance is created.</span></span> <span data-ttu-id="d17ec-118">"Hello World!" 메시지</span><span class="sxs-lookup"><span data-stu-id="d17ec-118">The message "Hello World!"</span></span> <span data-ttu-id="d17ec-119">워크플로 인스턴스에 의해 인쇄 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-119">is printed by the workflow instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d17ec-120">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-120">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d17ec-121">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="d17ec-121">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d17ec-122">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d17ec-123">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d17ec-123">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreationEndpoint`
