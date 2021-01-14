---
title: 동적 업데이트
ms.date: 03/30/2017
ms.assetid: 8b6ef19b-9691-4b4b-824c-3c651a9db96e
ms.openlocfilehash: cb4b63a67aa6e9033b227198e2ecc2b1b80db927
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190158"
---
# <a name="dynamic-update"></a><span data-ttu-id="c4170-102">동적 업데이트</span><span class="sxs-lookup"><span data-stu-id="c4170-102">Dynamic Update</span></span>

<span data-ttu-id="c4170-103">동적 업데이트는 워크플로 애플리케이션 개발자가 지속형 워크플로 인스턴스의 워크플로 정의를 업데이트하기 위한 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="c4170-104">이를 통해 버그 수정 또는 새 요구 사항을 구현하거나 예기치 않은 변경 내용을 수용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-104">This can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="c4170-105">이 항목에서는 .NET Framework 4.5에 도입 된 동적 업데이트 기능에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-105">This topic provides an overview of the dynamic update functionality introduced in .NET Framework 4.5.</span></span>

## <a name="dynamic-update"></a><span data-ttu-id="c4170-106">동적 업데이트</span><span class="sxs-lookup"><span data-stu-id="c4170-106">Dynamic Update</span></span>

<span data-ttu-id="c4170-107">지속형 워크플로 인스턴스에 동적 업데이트를 적용하려면 지속형 워크플로 인스턴스를 수정하여 필요한 변경 내용을 반영하는 방법을 설명하는 런타임 지침이 포함된 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-107">To apply dynamic updates to a persisted workflow instance, a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> is created that contains instructions for the runtime that describe how to modify the persisted workflow instance to reflect the desired changes.</span></span> <span data-ttu-id="c4170-108">업데이트 맵을 만든 후에는 원하는 지속형 워크플로 인스턴스에 이 업데이트 맵을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-108">Once the update map is created, it is applied to the desired persisted workflow instances.</span></span> <span data-ttu-id="c4170-109">동적 업데이트를 적용한 후에는 새로 업데이트한 워크플로 정의를 사용하여 워크플로 인스턴스를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-109">Once the dynamic update is applied, the workflow instance may be resumed using the new updated workflow definition.</span></span> <span data-ttu-id="c4170-110">업데이트 맵을 만들어 적용하는 데 필요한 네 가지 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-110">There are four steps required to create and apply an update map.</span></span>

1. [<span data-ttu-id="c4170-111">워크플로 정의를 동적 업데이트할 수 있도록 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-111">Prepare the workflow definition for dynamic update</span></span>](dynamic-update.md#Prepare)

2. [<span data-ttu-id="c4170-112">워크플로 정의를 업데이트하여 원하는 변경 내용을 반영합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-112">Update the workflow definition to reflect the desired changes</span></span>](dynamic-update.md#Update)

3. [<span data-ttu-id="c4170-113">업데이트 맵을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-113">Create the update map</span></span>](dynamic-update.md#Create)

4. [<span data-ttu-id="c4170-114">원하는 지속형 워크플로 인스턴스에 업데이트 맵을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-114">Apply the update map to the desired persisted workflow instances</span></span>](dynamic-update.md#Apply)

> [!NOTE]
> <span data-ttu-id="c4170-115">업데이트 맵을 만드는 1~3단계와 업데이트를 적용하는 단계는 서로 독립적으로 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-115">Note that steps 1 through 3, which cover the creation of the update map, may be performed independently of applying the update.</span></span> <span data-ttu-id="c4170-116">워크플로 개발자가 업데이트 맵을 오프 라인으로 만들고 관리자가 나중에 업데이트를 적용 하는 일반적인 시나리오를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-116">A common scenario that the workflow developer will create the update map offline, and then an administrator will apply the update at a later time.</span></span>

<span data-ttu-id="c4170-117">이 항목에서는 컴파일된 XAML 워크플로의 지속형 인스턴스에 새 활동을 추가하는 동적 업데이트 프로세스에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-117">This topic provides an overview of the dynamic update process of adding a new activity to a persisted instance of a compiled Xaml workflow.</span></span>

### <a name="prepare-the-workflow-definition-for-dynamic-update"></a><a name="Prepare"></a> <span data-ttu-id="c4170-118">워크플로 정의에서 동적 업데이트 준비</span><span class="sxs-lookup"><span data-stu-id="c4170-118">Prepare the workflow definition for dynamic update</span></span>

<span data-ttu-id="c4170-119">동적 업데이트 프로세스의 첫 번째 단계는 원하는 워크플로 정의를 업데이트할 수 있도록 준비하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-119">The first step in the dynamic update process is to prepare the desired workflow definition for update.</span></span> <span data-ttu-id="c4170-120">이를 위해서는 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> 메서드를 호출하고 수정할 워크플로 정의를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-120">This is done by calling the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method and passing in the workflow definition to modify.</span></span> <span data-ttu-id="c4170-121">이 메서드는 유효성을 검사한 다음 나중에 수정된 워크플로 정의와 비교할 수 있도록 워크플로 트리에서 태그가 지정되어야 하는 공용 활동 및 변수와 같은 모든 개체를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-121">This method validates and then walks the workflow tree to identify all of the objects such as public activities and variables that need to be tagged so they can be compared later with the modified workflow definition.</span></span> <span data-ttu-id="c4170-122">이 작업이 완료되면 워크플로 트리가 복제되어 원래 워크플로 정의에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-122">When this is complete, the workflow tree is cloned and attached to the original workflow definition.</span></span> <span data-ttu-id="c4170-123">업데이트 맵을 만들 때는 워크플로 정의의 업데이트 버전과 원래 워크플로 정의를 비교하여 그 차이에 따라 업데이트 맵이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-123">When the update map is created, the updated version of the workflow definition is compared with the original workflow definition and the update map is generated based on the differences.</span></span>

<span data-ttu-id="c4170-124">XAML 워크플로를 동적으로 업데이트할 수 있도록 준비하려면 해당 워크플로를 <xref:System.Activities.ActivityBuilder>에 로드한 후 <xref:System.Activities.ActivityBuilder>에 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-124">To prepare a Xaml workflow for dynamic update it may be loaded into an <xref:System.Activities.ActivityBuilder>, and then the <xref:System.Activities.ActivityBuilder> is passed into <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>.</span></span>

> [!NOTE]
> <span data-ttu-id="c4170-125">Serialize 된 워크플로 및 작업에 대 한 자세한 내용은 <xref:System.Activities.ActivityBuilder> [XAML로 워크플로 및 활동 직렬화](serializing-workflows-and-activities-to-and-from-xaml.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4170-125">For more information about working with serialized workflows and <xref:System.Activities.ActivityBuilder>, see [Serializing Workflows and Activities to and from XAML](serializing-workflows-and-activities-to-and-from-xaml.md).</span></span>

<span data-ttu-id="c4170-126">다음 예제에서는 여러 자식 활동과 `MortgageWorkflow`로 구성된 <xref:System.Activities.Statements.Sequence> 정의를 <xref:System.Activities.ActivityBuilder>에 로드한 후 동적 업데이트를 준비합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-126">In the following example, a `MortgageWorkflow` definition (that consists of a <xref:System.Activities.Statements.Sequence> with several child activities) is loaded into an <xref:System.Activities.ActivityBuilder>, and then prepared for dynamic update.</span></span> <span data-ttu-id="c4170-127">메서드가 반환한 후 <xref:System.Activities.ActivityBuilder>는 원래 워크플로 정의와 복사본이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-127">After the method returns, the <xref:System.Activities.ActivityBuilder> contains the original workflow definition as well as a copy.</span></span>

```csharp
// Load the MortgageWorkflow definition from Xaml into
// an ActivityBuilder.
XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
{
    LocalAssembly = Assembly.GetExecutingAssembly()
};

XamlXmlReader xamlReader = new XamlXmlReader(@"C:\WorkflowDefinitions\MortgageWorkflow.xaml",
    readerSettings);

ActivityBuilder ab = XamlServices.Load(
    ActivityXamlServices.CreateBuilderReader(xamlReader)) as ActivityBuilder;

// Prepare the workflow definition for dynamic update.
DynamicUpdateServices.PrepareForUpdate(ab);
```

### <a name="update-the-workflow-definition-to-reflect-the-desired-changes"></a><a name="Update"></a> <span data-ttu-id="c4170-128">워크플로 정의를 업데이트 하 여 원하는 변경 내용을 반영 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-128">Update the workflow definition to reflect the desired changes</span></span>

<span data-ttu-id="c4170-129">워크플로 정의를 업데이트할 준비가 되면 원하는 변경 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-129">Once the workflow definition has been prepared for updating, the desired changes can be made.</span></span> <span data-ttu-id="c4170-130">활동 추가 또는 제거, 공용 변수 추가, 이동 또는 삭제, 인수 추가 또는 제거, 활동 대리자의 시그니처 변경 같은 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-130">You can add or remove activities, add, move or delete public variables, add or remove arguments, and make changes to the signature of activity delegates.</span></span> <span data-ttu-id="c4170-131">실행 중인 활동을 제거하거나 실행 중인 대리자의 시그니처를 변경할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-131">You cannot remove a running activity or change the signature of a running delegate.</span></span> <span data-ttu-id="c4170-132">이러한 변경 작업은 코드를 사용하거나 재호스트된 워크플로 디자이너를 사용하여 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-132">These changes may be made using code, or in a re-hosted workflow designer.</span></span> <span data-ttu-id="c4170-133">다음 예제에서는 이전 예제에서 사용한 `VerifyAppraisal`의 본문을 구성하는 Sequence에 사용자 지정 `MortgageWorkflow` 활동을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-133">In the following example, a custom `VerifyAppraisal` activity is added to the Sequence that makes up the body of the `MortgageWorkflow` from the previous example.</span></span>

```csharp
// Make desired changes to the definition. In this example, we are
// inserting a new VerifyAppraisal activity as the 3rd child of the root Sequence.
VerifyAppraisal va = new VerifyAppraisal
{
    Result = new VisualBasicReference<bool>("LoanCriteria")
};

// Get the Sequence that makes up the body of the workflow.
Sequence s = ab.Implementation as Sequence;

// Insert the new activity into the Sequence.
s.Activities.Insert(2, va);
```

### <a name="create-the-update-map"></a><a name="Create"></a> <span data-ttu-id="c4170-134">업데이트 맵 만들기</span><span class="sxs-lookup"><span data-stu-id="c4170-134">Create the update map</span></span>

<span data-ttu-id="c4170-135">업데이트할 준비가 된 워크플로 정의를 수정한 후에는 업데이트 맵을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-135">Once the workflow definition that was prepared for update has been modified, the update map can be created.</span></span> <span data-ttu-id="c4170-136">동적 업데이트 맵을 만들려면 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-136">To create a dynamic update map, the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> method is invoked.</span></span> <span data-ttu-id="c4170-137">이 메서드는 런타임에 새 워크플로 정의를 사용하여 지속형 워크플로 인스턴스를 로드하고 다시 시작할 수 있도록 런타임에 해당 인스턴스를 수정하는 데 필요한 정보가 포함된 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-137">This returns a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> that contains the information the runtime needs to modify a persisted workflow instance so that it may be loaded and resumed with the new workflow definition.</span></span> <span data-ttu-id="c4170-138">다음 예제에서는 이전 예제에서 수정된 `MortgageWorkflow` 정의에 대해 동적 맵을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-138">In the following example, a dynamic map is created for the modified `MortgageWorkflow` definition from the previous example.</span></span>

```csharp
// Create the update map.
DynamicUpdateMap map = DynamicUpdateServices.CreateUpdateMap(ab);
```

<span data-ttu-id="c4170-139">이 업데이트 맵은 지속형 워크플로 인스턴스를 수정하는 데 즉시 사용할 수 있으며, 보다 일반적인 방법으로는 이를 저장했다가 나중에 업데이트를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-139">This update map can immediately be used to modify persisted workflow instances, or more typically it can be saved and the updates applied later.</span></span> <span data-ttu-id="c4170-140">업데이트 맵을 저장하는 한 가지 방법은 다음 예제와 같이 파일에 serialize하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-140">One way to save the update map is to serialize it to a file, as shown in the following example.</span></span>

```csharp
// Serialize the update map to a file.
DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
using (FileStream fs = System.IO.File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Create))
{
    serializer.WriteObject(fs, map);
}
```

<span data-ttu-id="c4170-141"><xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>이 결과를 반환하면 복제된 워크플로 정의와 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType>에 대한 호출에 추가된 기타 동적 업데이트 정보는 제거되고, 수정된 워크플로 정의는 나중에 업데이트된 워크플로 인스턴스를 다시 시작할 때 사용할 수 있도록 저장될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-141">When <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> returns, the cloned workflow definition and other dynamic update information that was added in the call to <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> is removed, and the modified workflow definition is ready to be saved so that it can be used later when resuming updated workflow instances.</span></span> <span data-ttu-id="c4170-142">다음 예제에서는 수정된 워크플로 정의를 `MortgageWorkflow_v1.1.xaml`에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-142">In the following example, the modified workflow definition is saved to `MortgageWorkflow_v1.1.xaml`.</span></span>

```csharp
// Save the modified workflow definition.
StreamWriter sw = File.CreateText(@"C:\WorkflowDefinitions\MortgageWorkflow_v1.1.xaml");
XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(new XamlXmlWriter(sw, new XamlSchemaContext()));
XamlServices.Save(xw, ab);
sw.Close();
```

### <a name="apply-the-update-map-to-the-desired-persisted-workflow-instances"></a><a name="Apply"></a> <span data-ttu-id="c4170-143">원하는 지속형 워크플로 인스턴스에 업데이트 맵을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-143">Apply the update map to the desired persisted workflow instances</span></span>

<span data-ttu-id="c4170-144">업데이트 맵을 만든 후 언제든지 업데이트 맵을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-144">Applying the update map can be done at any time after creating it.</span></span> <span data-ttu-id="c4170-145">이 작업은 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>에서 반환된 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType> 인스턴스를 사용하여 바로 수행하거나, 저장된 업데이트 맵 복사본을 사용하여 나중에 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-145">It can be done right away using the <xref:System.Activities.DynamicUpdate.DynamicUpdateMap> instance that was returned by <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.CreateUpdateMap%2A?displayProperty=nameWithType>, or it can be done later using a saved copy of the update map.</span></span> <span data-ttu-id="c4170-146">워크플로 인스턴스를 업데이트하려면 <xref:System.Activities.WorkflowApplicationInstance>를 사용하여 해당 인스턴스를 <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-146">To update a workflow instance, load it into a <xref:System.Activities.WorkflowApplicationInstance> using <xref:System.Activities.WorkflowApplication.GetInstance%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4170-147">다음으로 업데이트된 워크플로 정의 및 원하는 <xref:System.Activities.WorkflowApplication>를 사용하여 <xref:System.Activities.WorkflowIdentity>을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-147">Next, create a <xref:System.Activities.WorkflowApplication> using the updated workflow definition, and the desired <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="c4170-148">이 <xref:System.Activities.WorkflowIdentity>는 원래 워크플로를 유지하는 데 사용된 것과 다를 수 있으며, 일반적으로 지속형 인스턴스가 수정되었음을 반영하기 위해 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-148">This <xref:System.Activities.WorkflowIdentity> may be different than the one that was used to persist the original workflow, and typically is in order to reflect that the persisted instance has been modified.</span></span> <span data-ttu-id="c4170-149"><xref:System.Activities.WorkflowApplication>을 만든 후에는 <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType>을 사용하는 <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>의 오버로드를 사용하여 이를 로드한 다음 <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>를 호출하여 언로드합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-149">Once the <xref:System.Activities.WorkflowApplication> is created, it is loaded using the overload of <xref:System.Activities.WorkflowApplication.Load%2A?displayProperty=nameWithType> that takes a <xref:System.Activities.DynamicUpdate.DynamicUpdateMap>, and then unloaded with a call to <xref:System.Activities.WorkflowApplication.Unload%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4170-150">그러면 동적 업데이트가 적용되고 업데이트된 워크플로 인스턴스가 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-150">This applies the dynamic update and persists the updated workflow instance.</span></span>

```csharp
// Load the serialized update map.
DynamicUpdateMap map;
using (FileStream fs = File.Open(@"C:\WorkflowDefinitions\MortgageWorkflow.map", FileMode.Open))
{
    DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
    object updateMap = serializer.ReadObject(fs);
    if (updateMap == null)
    {
        throw new ApplicationException("DynamicUpdateMap is null.");
    }

    map = (DynamicUpdateMap)updateMap;
}

// Retrieve a list of workflow instance ids that corresponds to the
// workflow instances to update. This step is the responsibility of
// the application developer.
List<Guid> ids = GetPersistedWorkflowIds();
foreach (Guid id in ids)
{
    // Get a proxy to the persisted workflow instance.
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(id, store);

    // If desired, you can inspect the WorkflowIdentity of the instance
    // using the DefinitionIdentity property to determine whether to apply
    // the update.
    Console.WriteLine(instance.DefinitionIdentity);

    // Create a workflow application. You must specify the updated workflow definition, and
    // you may provide an updated WorkflowIdentity if desired to reflect the update.
    WorkflowIdentity identity = new WorkflowIdentity
    {
        Name = "MortgageWorkflow v1.1",
        Version = new Version(1, 1, 0, 0)
    };

    // Load the persisted workflow instance using the updated workflow definition
    // and with an updated WorkflowIdentity. In this example the MortgageWorkflow class
    // contains the updated definition.
    WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

    // Apply the dynamic update on the loaded instance.
    wfApp.Load(instance, map);

    // Unload the updated instance.
    wfApp.Unload();
}
```

### <a name="resuming-an-updated-workflow-instance"></a><span data-ttu-id="c4170-151">업데이트된 워크플로 인스턴스 다시 시작</span><span class="sxs-lookup"><span data-stu-id="c4170-151">Resuming an Updated Workflow Instance</span></span>

<span data-ttu-id="c4170-152">동적 업데이트를 적용한 후에는 워크플로 인스턴스를 다시 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-152">Once dynamic update has been applied, the workflow instance may be resumed.</span></span> <span data-ttu-id="c4170-153">이때 새로 업데이트된 정의와 <xref:System.Activities.WorkflowIdentity>를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-153">Note that the new updated definition and <xref:System.Activities.WorkflowIdentity> must be used.</span></span>

> [!NOTE]
> <span data-ttu-id="c4170-154">및 작업에 대 한 자세한 <xref:System.Activities.WorkflowApplication> 내용은 <xref:System.Activities.WorkflowIdentity> [WorkflowIdentity 및 버전 관리 사용](using-workflowidentity-and-versioning.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c4170-154">For more information about working with <xref:System.Activities.WorkflowApplication> and <xref:System.Activities.WorkflowIdentity>, see [Using WorkflowIdentity and Versioning](using-workflowidentity-and-versioning.md).</span></span>

<span data-ttu-id="c4170-155">다음 예제에서는 이전 예제에서 컴파일된 `MortgageWorkflow_v1.1.xaml` 워크플로를 업데이트된 워크플로 정의를 사용하여 로드하고 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="c4170-155">In the following example, the `MortgageWorkflow_v1.1.xaml` workflow from the previous example has been compiled, and is loaded and resumed using the updated workflow definition.</span></span>

```csharp
// Load the persisted workflow instance using the updated workflow definition
// and updated WorkflowIdentity.
WorkflowIdentity identity = new WorkflowIdentity
{
    Name = "MortgageWorkflow v1.1",
    Version = new Version(1, 1, 0, 0)
};

WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);

// Configure persistence and desired workflow event handlers.
// (Omitted for brevity.)
ConfigureWorkflowApplication(wfApp);

// Load the persisted workflow instance.
wfApp.Load(InstanceId);

// Resume the workflow.
// wfApp.ResumeBookmark(...);
```
