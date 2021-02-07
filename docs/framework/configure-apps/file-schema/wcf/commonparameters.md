---
description: 다음에 대해 자세히 알아보세요. <commonParameters>
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: a9d230fb0f205315dc52357119e6b35752abc96d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698377"
---
# \<commonParameters>

<span data-ttu-id="baf5b-102">여러 서비스에서 전역적으로 사용되는 매개 변수의 컬렉션을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="baf5b-103">일반적으로 이 컬렉션에는 영속 서비스에서 공유할 수 있는 데이터베이스 연결 문자열이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="baf5b-104">구문</span><span class="sxs-lookup"><span data-stu-id="baf5b-104">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="baf5b-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="baf5b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="baf5b-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="baf5b-107">특성</span><span class="sxs-lookup"><span data-stu-id="baf5b-107">Attributes</span></span>  

 <span data-ttu-id="baf5b-108">없음</span><span class="sxs-lookup"><span data-stu-id="baf5b-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="baf5b-109">자식 요소</span><span class="sxs-lookup"><span data-stu-id="baf5b-109">Child Elements</span></span>  
  
|<span data-ttu-id="baf5b-110">요소</span><span class="sxs-lookup"><span data-stu-id="baf5b-110">Element</span></span>|<span data-ttu-id="baf5b-111">설명</span><span class="sxs-lookup"><span data-stu-id="baf5b-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="baf5b-112">서비스에서 사용되는 일반 매개 변수의 이름-값 쌍을 컬렉션에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-112">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="baf5b-113">부모 요소</span><span class="sxs-lookup"><span data-stu-id="baf5b-113">Parent Elements</span></span>  
  
|<span data-ttu-id="baf5b-114">요소</span><span class="sxs-lookup"><span data-stu-id="baf5b-114">Element</span></span>|<span data-ttu-id="baf5b-115">설명</span><span class="sxs-lookup"><span data-stu-id="baf5b-115">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="baf5b-116"><xref:System.Workflow.Runtime.WorkflowRuntime>WCF (워크플로 기반 Windows Communication Foundation) 서비스를 호스팅하기 위한의 인스턴스에 대 한 설정을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-116">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="baf5b-117">설명</span><span class="sxs-lookup"><span data-stu-id="baf5b-117">Remarks</span></span>  

 <span data-ttu-id="baf5b-118">`<commonParameters>` 요소는 여러 서비스에서 전역적으로 사용되는 모든 매개 변수를 정의합니다. 예를 들어 `ConnectionString`를 사용하는 경우 <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-118">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="baf5b-119">SQL 추적 서비스에서는 `ConnectionString` 값이 `<commonParameters>` 섹션에 지정된 경우 해당 값을 일관성 있게 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-119">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="baf5b-120">`StateMachineWorkflowInstance.StateHistory` 속성을 검색하는 것과 같은 일부 작업이 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-120">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="baf5b-121">이 문제를 해결하려면 다음 예제와 같이 추적 공급자에 대한 구성 섹션에 `ConnectionString` 특성을 지정하세요.</span><span class="sxs-lookup"><span data-stu-id="baf5b-121">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="baf5b-122">작업 일괄 처리를 지속성 저장소에 커밋하는 서비스(예: <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> 및 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>)의 경우 다음 예제와 같이 `EnableRetries` 매개 변수를 사용하여 트랜잭션을 다시 시도하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-122">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="baf5b-123">`EnableRetries`매개 변수는 전역 수준에서 설정 하거나 ( *CommonParameters* 섹션에서 볼 수 있음)를 지 원하는 개별 서비스 `EnableRetries` ( *서비스* 섹션에서 볼 수 있음)로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-123">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="baf5b-124">다음 샘플 코드는 일반 매개 변수를 프로그래밍 방식으로 변경 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="baf5b-124">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="baf5b-125">구성 파일을 사용 하 여 Windows Workflow Foundation 호스트 응용 프로그램 개체의 동작을 제어 하는 방법에 대 한 자세한 내용은 <xref:System.Workflow.Runtime.WorkflowRuntime> [워크플로 구성 파일](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="baf5b-125">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baf5b-126">예제</span><span class="sxs-lookup"><span data-stu-id="baf5b-126">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="baf5b-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="baf5b-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="baf5b-128">[워크플로 구성 파일](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="baf5b-128">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
