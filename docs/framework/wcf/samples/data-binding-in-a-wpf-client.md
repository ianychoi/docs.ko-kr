---
description: '자세한 정보: Windows Presentation Foundation 클라이언트의 데이터 바인딩'
title: Wndows Presentation Foundation 클라이언트에서 데이터 바인딩
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 8bab24dc8f3debb75ddfd712a06f2f035707d42f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755878"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="552e1-103">Wndows Presentation Foundation 클라이언트에서 데이터 바인딩</span><span class="sxs-lookup"><span data-stu-id="552e1-103">Data Binding in a Windows Presentation Foundation Client</span></span>

<span data-ttu-id="552e1-104">이 샘플에서는 WPF(Windows Presentation Foundation) 클라이언트에서 데이터 바인딩을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-104">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="552e1-105">이 샘플에서는 클라이언트에 반환할 앨범 배열을 임의로 생성 하는 WCF (Windows Communication Foundation) 서비스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-105">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="552e1-106">각 앨범에는 이름, 가격 및 앨범 트랙 목록이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-106">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="552e1-107">앨범 트랙에는 이름과 기간이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-107">The album tracks have a name and duration.</span></span> <span data-ttu-id="552e1-108">서비스에서 반환 되는 정보는 WPF (Windows Presentation Foundation) 클라이언트에서 제공 하는 UI (사용자 인터페이스)에 자동으로 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-108">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="552e1-109">이 샘플의 설치 절차 및 빌드 지침은 이 항목의 끝부분에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="552e1-110">데이터 바인딩을 사용하면 데이터 소스를 UI에 자동으로 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-110">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="552e1-111">이렇게 하면 데이터 개체나 데이터 개체 배열의 데이터로 각 UI 요소를 프로그래밍 방식으로 업데이트할 필요가 없으므로 프로그래밍 모델이 단순화됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-111">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="552e1-112">단일 UI 요소에 개체를 바인딩하거나 `ListBox`와 같이 여러 입력을 허용하는 컨트롤에 배열을 바인딩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-112">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="552e1-113">다음 코드에서는 UI 요소의 `DataContext`에 데이터를 바인딩하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-113">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="552e1-114">위 샘플에서 `DataContext`이라는 `grid` 레이아웃 요소에 대한 `myPanel`는 `GetAlbumList` 메서드가 반환하는 데이터로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-114">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="552e1-115">`DataContext`를 사용하여 요소는 바인딩에 사용되는 데이터 소스에 대한 정보뿐만 아니라 경로와 같은 바인딩의 다른 특성을 부모 요소로부터 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-115">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="552e1-116">서버의 데이터가 업데이트될 때마다 이 코드 줄이 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-116">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="552e1-117">예를 들어, 이 코드 줄은 창이 초기화될 경우 및 새 앨범이 추가될 경우 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-117">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="552e1-118">다음 샘플 XAML 코드에서 `ListBox`는 `ItemsSource="{Binding }"`을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-118">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="552e1-119">이 샘플 코드는 최상위 UI 요소에 바인딩된 데이터가 이 컨트롤(즉, 앨범 배열)에도 바인딩되도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-119">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="552e1-120">또한 `ItemTemplate="{StaticResource AlbumStyle}"`은 `ListBox`의 각 항목에 사용될 데이터 템플릿을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-120">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="552e1-121">데이터 템플릿을 정의하여 데이터의 형식을 지정하는 방법을 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-121">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="552e1-122">이러한 데이터 템플릿을 애플리케이션의 다른 UI 요소에 다시 사용할 수 있으므로 데이터 템플릿을 한 곳에서 정의하고 유지 관리할 수 있다는 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-122">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="552e1-123">`AlbumStyle` 데이터 템플릿은 두 개의 `TextBlock`을 나란히 사용하여 그리드의 레이아웃을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-123">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="552e1-124">이러한 두 개체 중 하나는 앨범의 이름을 지정하고 다른 하나는 앨범의 트랙 수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-124">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="552e1-125">다음 XAML 코드에서는 두 번째 `ListBox`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-125">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="552e1-126">이 코드에서는 `ItemsSource`의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-126">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="552e1-127">이는 이 컨트롤에 바인딩된 데이터가 최상위 데이터가 데이터가 아니라 `Tracks`라는 최상위 데이터의 속성이라는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-127">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="552e1-128">이 속성은 앨범 내에 포함된 트랙의 배열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-128">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="552e1-129">또한 `DataTemplate`이라는 다른 `TrackStyle`이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-129">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="552e1-130">`TrackStyle` 템플릿의 레이아웃은 `AlbumStyle` 템플릿의 레이아웃과 비슷하지만 `TextBlock`이 다른 속성에 바인딩됩니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-130">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="552e1-131">이는 두 템플릿이 다른 데이터 개체와 함께 사용되기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-131">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="552e1-132">샘플을 설치, 빌드 및 실행하려면</span><span class="sxs-lookup"><span data-stu-id="552e1-132">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="552e1-133">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="552e1-134">C# 또는 Visual Basic .NET 버전의 솔루션을 빌드하려면 [Building the Windows Communication Foundation Samples](building-the-samples.md)의 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="552e1-135">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="552e1-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="552e1-136">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-136">The samples may already be installed on your machine.</span></span> <span data-ttu-id="552e1-137">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="552e1-137">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="552e1-138">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-138">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="552e1-139">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="552e1-139">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
