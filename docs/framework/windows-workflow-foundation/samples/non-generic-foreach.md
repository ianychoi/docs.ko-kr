---
title: 비제네릭 ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 9678d929375857a76d01f575e637a069b0911ae5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283577"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="2904c-102">비제네릭 ForEach</span><span class="sxs-lookup"><span data-stu-id="2904c-102">Non-Generic ForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="2904c-103">의 도구 상자에는 <xref:System.Activities.Statements.ForEach%601> 컬렉션을 반복할 수 있도록 하는 <xref:System.Collections.Generic.IEnumerable%601>을 비롯한 흐름 제어 활동이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="2904c-104"><xref:System.Activities.Statements.ForEach%601>을 사용하려면 <xref:System.Activities.Statements.ForEach%601.Values%2A> 속성이 <xref:System.Collections.Generic.IEnumerable%601> 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="2904c-105">그러면 사용자가 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스를 구현하는 데이터 구조(예: <xref:System.Collections.ArrayList>)를 반복하지 못합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="2904c-106"><xref:System.Activities.Statements.ForEach%601>의 비제네릭 버전은 컬렉션 값의 형식에 대한 호환성을 유지하기 위해 런타임 복잡성이 더 높아지지만 이러한 요구 사항의 제약을 받지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="2904c-107">이 샘플에서는 비제네릭 <xref:System.Activities.Statements.ForEach%601> 활동과 디자이너를 구현하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="2904c-108">이 활동을 사용하여 <xref:System.Collections.ArrayList>를 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="2904c-109">ForEach 활동</span><span class="sxs-lookup"><span data-stu-id="2904c-109">ForEach Activity</span></span>  

 <span data-ttu-id="2904c-110">C #/Visual Basic `foreach` 문은 컬렉션의 각 요소에 대해 포함 문을 실행 하 여 컬렉션의 요소를 열거 합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="2904c-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)]에 해당하는 `foreach` 활동은 <xref:System.Activities.Statements.ForEach%601>과 <xref:System.Activities.Statements.ParallelForEach%601>입니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="2904c-112"><xref:System.Activities.Statements.ForEach%601> 활동은 값 목록과 본문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="2904c-113">런타임에 목록이 반복되고 목록의 각 값에 대해 본문이 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="2904c-114">대부분의 경우 제네릭 버전의 활동이 기본 솔루션이어야 합니다. 제네릭 버전은 이를 사용하는 대부분의 시나리오에 적용되고 컴파일 시 형식 검사 기능을 제공하기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="2904c-115">비제네릭 <xref:System.Collections.IEnumerable> 인터페이스를 구현하는 형식을 반복하는 데는 비제네릭 버전을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="2904c-116">클래스 정의</span><span class="sxs-lookup"><span data-stu-id="2904c-116">Class Definition</span></span>  

 <span data-ttu-id="2904c-117">다음 코드 예제에서는 비제네릭 `ForEach` 활동의 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="2904c-118">Body(옵션)</span><span class="sxs-lookup"><span data-stu-id="2904c-118">Body (optional)</span></span>  
 <span data-ttu-id="2904c-119">컬렉션의 각 요소에 대해 실행되는 <xref:System.Activities.ActivityAction> 형식의 <xref:System.Object>입니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="2904c-120">각 개별 요소는 `Argument` 속성을 통해 본문에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="2904c-121">Values(옵션)</span><span class="sxs-lookup"><span data-stu-id="2904c-121">Values (optional)</span></span>  
 <span data-ttu-id="2904c-122">반복되는 요소의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="2904c-123">컬렉션의 모든 요소가 호환 가능한 형식인지 확인하는 작업은 런타임에 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="2904c-124">ForEach 사용 예제</span><span class="sxs-lookup"><span data-stu-id="2904c-124">Example of Using ForEach</span></span>  

 <span data-ttu-id="2904c-125">다음 코드에서는 애플리케이션에서 ForEach 활동을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|<span data-ttu-id="2904c-126">조건</span><span class="sxs-lookup"><span data-stu-id="2904c-126">Condition</span></span>|<span data-ttu-id="2904c-127">메시지</span><span class="sxs-lookup"><span data-stu-id="2904c-127">Message</span></span>|<span data-ttu-id="2904c-128">심각도</span><span class="sxs-lookup"><span data-stu-id="2904c-128">Severity</span></span>|<span data-ttu-id="2904c-129">예외 유형</span><span class="sxs-lookup"><span data-stu-id="2904c-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="2904c-130">값은 `null`입니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-130">Values is `null`</span></span>|<span data-ttu-id="2904c-131">필수 활동 인수 'Values'의 값이 제공되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="2904c-132">오류</span><span class="sxs-lookup"><span data-stu-id="2904c-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="2904c-133">ForEach 디자이너</span><span class="sxs-lookup"><span data-stu-id="2904c-133">ForEach Designer</span></span>  

 <span data-ttu-id="2904c-134">샘플의 활동 디자이너는 기본 제공 <xref:System.Activities.Statements.ForEach%601> 활동에 제공되는 디자이너와 모양이 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="2904c-135">디자이너는 **샘플**, **제네릭이 아닌 작업** 범주의 도구 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="2904c-136">작업은 도구 상자에서를 노출 하 고 적절 하 게 구성 된를 사용 하 여 작업을 만드는 도구 상자에서 디자이너의 이름이 **ForEachWithBodyFactory** 입니다 <xref:System.Activities.Presentation.IActivityTemplateFactory> <xref:System.Activities.ActivityAction> .</span><span class="sxs-lookup"><span data-stu-id="2904c-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="2904c-137">이 샘플을 실행하려면</span><span class="sxs-lookup"><span data-stu-id="2904c-137">To run this sample</span></span>  
  
1. <span data-ttu-id="2904c-138">선택한 프로젝트를 솔루션의 시작 프로젝트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="2904c-139">**CodeTestClient** 는 코드를 사용 하 여 작업을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="2904c-140">**Designertestclient** 는 디자이너 내에서 활동을 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="2904c-141">프로젝트를 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2904c-142">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2904c-143">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="2904c-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2904c-144">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2904c-145">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2904c-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
