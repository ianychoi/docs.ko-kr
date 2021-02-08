---
description: '자세히 알아보기: Designer 재호스팅'
title: 디자이너 재호스팅
ms.date: 03/30/2017
ms.assetid: b676ad31-5f64-4d84-9a36-b4d7113a2f4d
ms.openlocfilehash: 84401ba7cfc2b5515a9dcfda36289893e55660e2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792533"
---
# <a name="designer-rehosting"></a><span data-ttu-id="cc894-103">디자이너 재호스팅</span><span class="sxs-lookup"><span data-stu-id="cc894-103">Designer Rehosting</span></span>

<span data-ttu-id="cc894-104">디자이너 재호스팅은 사용자 지정 애플리케이션 내에 워크플로 디자인 캔버스를 호스트하는 방식을 가리키는 일반적인 시나리오입니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-104">Designer rehosting is a common scenario that refers to hosting the workflow design canvas inside of a custom application.</span></span> <span data-ttu-id="cc894-105">대부분의 사람들이 가장 잘 알고 있는 호스트 애플리케이션은 Visual Studio이지만, 애플리케이션에 워크플로 디자이너를 표시하는 것이 유용할 수 있는 시나리오는 그 밖에도 여러 가지가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-105">The hosting application most people are familiar with is Visual Studio, however there are a number of scenarios where showing the workflow designer in an application may be useful:</span></span>  
  
- <span data-ttu-id="cc894-106">최종 사용자가 현재 활성 상태 등 프로세스에 대한 런타임 데이터와 프로세스를 시각화하고 실행 시간 데이터 또는 워크플로 인스턴스에 대한 기타 정보를 집계하는 데 사용할 수 있는 모니터링 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="cc894-106">Monitoring applications (allowing an end user to visualize the process, as well as runtime data about the process such as the currently active state, aggregate execution time data, or other information about an instance of the workflow).</span></span>  
  
- <span data-ttu-id="cc894-107">한정된 활동 집합으로 프로세스를 사용자 지정하는 데 사용할 수 있는 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="cc894-107">Applications that allow a user to customize the process with a limited set of activities.</span></span>  
  
 <span data-ttu-id="cc894-108">이러한 유형의 애플리케이션을 지원하기 위해 .NET Framework 내에 Workflow Designer가 함께 제공되며, 이 Workflow Designer를 WPF 애플리케이션 내에 호스트하거나 적절한 WPF 호스팅 코드를 사용하여 WinForms 애플리케이션에 호스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-108">To support these types of applications, the workflow designer ships inside the .NET Framework, and can be hosted inside a WPF application, or in a WinForms application with the appropriate WPF hosting code.</span></span> <span data-ttu-id="cc894-109">이 샘플에서 설명하는 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-109">This sample demonstrates:</span></span>  
  
- <span data-ttu-id="cc894-110">WF 디자이너 재호스팅</span><span class="sxs-lookup"><span data-stu-id="cc894-110">Rehosting the WF designer.</span></span>  
  
- <span data-ttu-id="cc894-111">재호스트된 도구 상자 및 속성 표 사용</span><span class="sxs-lookup"><span data-stu-id="cc894-111">Using the rehosted toolbox and property grid as well.</span></span>  
  
## <a name="rehosting-the-designer"></a><span data-ttu-id="cc894-112">디자이너 재호스팅</span><span class="sxs-lookup"><span data-stu-id="cc894-112">Rehosting the designer</span></span>  

 <span data-ttu-id="cc894-113">이 샘플에서는 다음과 같은 표 레이아웃에 표시되는 디자이너를 포함할 WPF 레이아웃을 만드는 방법을 보여 줍니다. (공간의 제약 때문에 도구 상자 코드는 생략했습니다.)</span><span class="sxs-lookup"><span data-stu-id="cc894-113">This sample shows how to create the WPF layout to contain the designer, seen in the following grid layout (Toolbox code omitted for space concerns).</span></span> <span data-ttu-id="cc894-114">여기에서는 디자이너와 속성 표가 포함되는 테두리의 이름에 주목할 필요가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-114">Note the naming of the borders which contain the designer and property grid.</span></span>  
  
```xaml  
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition Width="2*"/>  
        <ColumnDefinition Width="7*"/>  
        <ColumnDefinition Width="3*"/>  
    </Grid.ColumnDefinitions>  
    <Border Grid.Column="0">  
        <sapt:ToolboxControl>...</sapt:ToolboxControl>  
    </Border>  
    <Border Grid.Column="1" Name="DesignerBorder"/>  
    <Border Grid.Column="2" Name="PropertyBorder"/>  
</Grid>  
```  
  
 <span data-ttu-id="cc894-115">다음으로 이 샘플에서는 디자이너를 만들고 해당 기본 <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> 및 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A>를 사용자 인터페이스의 적절한 컨테이너와 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-115">Next the sample creates the designer, and associates its primary <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> with the appropriate container in the user interface.</span></span> <span data-ttu-id="cc894-116">아래에 추가로 나와 있는 몇몇 코드 줄에 대해서는 약간의 설명이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-116">There are a few additional lines of code in the following example that merit some explanation.</span></span> <span data-ttu-id="cc894-117"><xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A>.NET Framework와 함께 제공 되는 작업에 대 한 기본 활동 디자이너를 연결 하려면 호출이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-117">The <xref:System.Activities.Core.Presentation.DesignerMetadata.Register%2A> call is required to associate the default activity designers for the activities shipped with .NET Framework.</span></span> <span data-ttu-id="cc894-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A>는 편집할 WF 항목을 전달하기 위해 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-118"><xref:System.Activities.Presentation.WorkflowDesigner.Load%2A> is called to pass in the WF item to be edited.</span></span> <span data-ttu-id="cc894-119">마지막으로, <xref:System.Activities.Presentation.WorkflowDesigner.View%2A>(기본 캔버스) 및 <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A>(속성 표)가 사용자 인터페이스 화면에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-119">Finally, the <xref:System.Activities.Presentation.WorkflowDesigner.View%2A> (primary canvas) and <xref:System.Activities.Presentation.WorkflowDesigner.PropertyInspectorView%2A> (property grid) are placed onto the user interface surface.</span></span>  
  
```csharp  
protected override void OnInitialized(EventArgs e)  
{  
   base.OnInitialized(e);  
   // register metadata  
   (new DesignerMetadata()).Register();  
  
   // create the workflow designer  
   WorkflowDesigner wd = new WorkflowDesigner();  
   wd.Load(new Sequence());  
   DesignerBorder.Child = wd.View;  
   PropertyBorder.Child = wd.PropertyInspectorView;  
}  
```  
  
## <a name="using-the-rehosted-toolbox"></a><span data-ttu-id="cc894-120">재호스트된 도구 상자 사용</span><span class="sxs-lookup"><span data-stu-id="cc894-120">Using the rehosted toolbox</span></span>  

 <span data-ttu-id="cc894-121">이 샘플에서는 재호스트된 도구 상자 컨트롤을 XAML에 선언적으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-121">This sample uses the rehosted toolbox control declaratively in XAML.</span></span> <span data-ttu-id="cc894-122">코드에서 <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> 생성자에 형식을 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-122">Note that in code, one can pass a type to the <xref:System.Activities.Presentation.Toolbox.ToolboxItemWrapper> constructor.</span></span>  
  
```xaml  
<!-- Copyright (c) Microsoft Corporation. All rights reserved-->  
<Window x:Class="Microsoft.Samples.DesignerRehosting.RehostingWfDesigner"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"  
        xmlns:sys="clr-namespace:System;assembly=mscorlib"  
        Title="Window1" Height="600" Width="900">  
    <Window.Resources>  
        <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>  
    </Window.Resources>  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="2*"/>  
            <ColumnDefinition Width="7*"/>  
            <ColumnDefinition Width="3*"/>  
        </Grid.ColumnDefinitions>  
        <Border Grid.Column="0">  
            <sapt:ToolboxControl>  
                <sapt:ToolboxCategory CategoryName="Basic">  
                    <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.Sequence  
                        </sapt:ToolboxItemWrapper.ToolName>  
                       </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.WriteLine  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.If  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                    <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">  
                        <sapt:ToolboxItemWrapper.ToolName>  
                            System.Activities.Statements.While  
                        </sapt:ToolboxItemWrapper.ToolName>  
  
                    </sapt:ToolboxItemWrapper>  
                </sapt:ToolboxCategory>  
            </sapt:ToolboxControl>  
        </Border>  
        <Border Grid.Column="1" Name="DesignerBorder"/>  
        <Border Grid.Column="2" Name="PropertyBorder"/>  
    </Grid>  
</Window>  
```  
  
#### <a name="using-the-sample"></a><span data-ttu-id="cc894-123">샘플 사용</span><span class="sxs-lookup"><span data-stu-id="cc894-123">Using the sample</span></span>  
  
1. <span data-ttu-id="cc894-124">Visual Studio 2010에서 DesignerRehosting 솔루션을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-124">Open the DesignerRehosting.sln solution in Visual Studio 2010.</span></span>  
  
2. <span data-ttu-id="cc894-125">F5 키를 눌러 애플리케이션을 컴파일하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-125">Press F5 to compile and run the application.</span></span>  
  
3. <span data-ttu-id="cc894-126">재호스트된 디자이너와 함께 WPF 애플리케이션이 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-126">A WPF application starts with a rehosted designer.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="cc894-127">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-127">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc894-128">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="cc894-128">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cc894-129">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-129">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc894-130">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cc894-130">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\DesignerRehosting\Basic`
