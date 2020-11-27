---
title: NativeActivity 기본 클래스
ms.date: 03/30/2017
ms.assetid: 254a4c50-425b-426d-a32f-0f7234925bac
ms.openlocfilehash: d875f62dacadb2baf6b5d7e93ddb2933aed9cdb0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274961"
---
# <a name="nativeactivity-base-class"></a><span data-ttu-id="40af1-102">NativeActivity 기본 클래스</span><span class="sxs-lookup"><span data-stu-id="40af1-102">NativeActivity Base Class</span></span>

<span data-ttu-id="40af1-103"><xref:System.Activities.NativeActivity>는 protected 생성자를 가진 추상 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-103"><xref:System.Activities.NativeActivity> is an abstract class with a protected constructor.</span></span> <span data-ttu-id="40af1-104"><xref:System.Activities.CodeActivity>와 마찬가지로 <xref:System.Activities.NativeActivity>는 <xref:System.Activities.NativeActivity.Execute%2A> 메서드를 구현하여 필수 동작을 작성하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-104">Like <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> is used for writing imperative behavior by implementing an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span> <span data-ttu-id="40af1-105"><xref:System.Activities.CodeActivity>와 달리 <xref:System.Activities.NativeActivity>는 <xref:System.Activities.NativeActivityContext> 메서드에 전달되는 <xref:System.Activities.NativeActivity.Execute%2A> 개체를 통해 워크플로 런타임의 모든 노출된 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-105">Unlike <xref:System.Activities.CodeActivity>, <xref:System.Activities.NativeActivity> has access to all of the exposed features of the workflow runtime through the <xref:System.Activities.NativeActivityContext> object passed to the <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

## <a name="using-nativeactivitycontext"></a><span data-ttu-id="40af1-106">NativeActivityContext 사용</span><span class="sxs-lookup"><span data-stu-id="40af1-106">Using NativeActivityContext</span></span>

 <span data-ttu-id="40af1-107"><xref:System.Activities.NativeActivity.Execute%2A> 형식의 `context` 매개 변수 멤버를 사용하여 <xref:System.Activities.NativeActivityContext> 메서드에서 워크플로 런타임 기능에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-107">Features of the workflow runtime can be accessed from within the <xref:System.Activities.NativeActivity.Execute%2A> method by using members of the `context` parameter, of type <xref:System.Activities.NativeActivityContext>.</span></span> <span data-ttu-id="40af1-108"><xref:System.Activities.NativeActivityContext>를 통해 사용할 수 있는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-108">The features available through <xref:System.Activities.NativeActivityContext> include the following:</span></span>

- <span data-ttu-id="40af1-109">인수 및 변수 가져오기 및 설정</span><span class="sxs-lookup"><span data-stu-id="40af1-109">Getting and setting of arguments and variables.</span></span>

- <span data-ttu-id="40af1-110"><xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>를 사용하여 자식 활동 예약</span><span class="sxs-lookup"><span data-stu-id="40af1-110">Scheduling child activities with <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A></span></span>

- <span data-ttu-id="40af1-111"><xref:System.Activities.NativeActivityContext.Abort%2A>를 사용하여 활동 실행 중단</span><span class="sxs-lookup"><span data-stu-id="40af1-111">Aborting activity execution using <xref:System.Activities.NativeActivityContext.Abort%2A>.</span></span>

- <span data-ttu-id="40af1-112"><xref:System.Activities.NativeActivityContext.CancelChild%2A> 및 <xref:System.Activities.NativeActivityContext.CancelChildren%2A>을 사용하여 자식 실행 취소</span><span class="sxs-lookup"><span data-stu-id="40af1-112">Canceling child execution using <xref:System.Activities.NativeActivityContext.CancelChild%2A> and <xref:System.Activities.NativeActivityContext.CancelChildren%2A>.</span></span>

- <span data-ttu-id="40af1-113"><xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A> 등과 같은 메서드를 사용하여 활동 책갈피 액세스</span><span class="sxs-lookup"><span data-stu-id="40af1-113">Access to activity bookmarks using such methods as <xref:System.Activities.NativeActivityContext.CreateBookmark%2A>, <xref:System.Activities.NativeActivityContext.RemoveBookmark%2A>, and <xref:System.Activities.NativeActivityContext.ResumeBookmark%2A>.</span></span>

- <span data-ttu-id="40af1-114"><xref:System.Activities.CodeActivityContext.Track%2A>을 사용하는 사용자 지정 추적 기능</span><span class="sxs-lookup"><span data-stu-id="40af1-114">Custom tracking features using <xref:System.Activities.CodeActivityContext.Track%2A>.</span></span>

- <span data-ttu-id="40af1-115"><xref:System.Activities.CodeActivityContext.GetProperty%2A> 및 <xref:System.Activities.NativeActivityContext.GetValue%2A>를 사용하여 활동 실행 속성 및 값 속성 액세스</span><span class="sxs-lookup"><span data-stu-id="40af1-115">Access to the activity’s execution properties and value properties using <xref:System.Activities.CodeActivityContext.GetProperty%2A> and <xref:System.Activities.NativeActivityContext.GetValue%2A>.</span></span>

- <span data-ttu-id="40af1-116"><xref:System.Activities.NativeActivityContext.ScheduleAction%2A> 및 <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>을 사용하여 활동 동작 및 기능 예약</span><span class="sxs-lookup"><span data-stu-id="40af1-116">Scheduling activity actions and functions using <xref:System.Activities.NativeActivityContext.ScheduleAction%2A> and <xref:System.Activities.NativeActivityContext.ScheduleFunc%2A>.</span></span>

### <a name="to-create-a-custom-activity-that-inherits-from-nativeactivity"></a><span data-ttu-id="40af1-117">NativeActivity에서 상속되는 사용자 지정 활동을 만들려면</span><span class="sxs-lookup"><span data-stu-id="40af1-117">To create a custom activity that inherits from NativeActivity</span></span>

1. <span data-ttu-id="40af1-118">OpenVisual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="40af1-118">OpenVisual Studio 2010.</span></span>

2. <span data-ttu-id="40af1-119">**파일**, **새로 만들기**, **프로젝트** 를 차례로 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-119">Select **File**, **New**, and then **Project**.</span></span> <span data-ttu-id="40af1-120">**프로젝트 형식** 창에서 **Visual c #** 아래에 있는 **Workflow 4.0** 을 선택 하 고 **v2010** 노드를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-120">Select **Workflow 4.0** under **Visual C#** in the **Project Types** window, and select the **v2010** node.</span></span> <span data-ttu-id="40af1-121">**템플릿** 창에서 **활동 라이브러리** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-121">Select **Activity Library** in the **Templates** window.</span></span> <span data-ttu-id="40af1-122">새 프로젝트의 이름을 HelloActivity로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-122">Name the new project HelloActivity.</span></span>

3. <span data-ttu-id="40af1-123">HelloActivity 프로젝트에서 Activity1를 마우스 오른쪽 단추로 클릭 하 고 **삭제** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-123">Right-click Activity1.xaml in the HelloActivity project and select **Delete**.</span></span>

4. <span data-ttu-id="40af1-124">HelloActivity 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **추가** 를 선택한 다음 **클래스** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-124">Right-click the HelloActivity project and select **Add**, and then **Class**.</span></span> <span data-ttu-id="40af1-125">새 프로젝트의 이름을 HelloActivity.cs로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-125">Name the new class HelloActivity.cs.</span></span>

5. <span data-ttu-id="40af1-126">HelloActivity.cs 파일에서 다음 `using` 지시문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-126">In the HelloActivity.cs file, add the following `using` directives.</span></span>

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    ```

6. <span data-ttu-id="40af1-127">기본 클래스를 클래스 선언에 추가하여 새 클래스를 <xref:System.Activities.NativeActivity>에서 상속하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-127">Make the new class inherit from <xref:System.Activities.NativeActivity> by adding a base class to the class declaration.</span></span>

    ```csharp
    class HelloActivity : NativeActivity
    ```

7. <span data-ttu-id="40af1-128"><xref:System.Activities.NativeActivity.Execute%2A> 메서드를 추가하여 클래스에 기능을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-128">Add functionality to the class by adding an <xref:System.Activities.NativeActivity.Execute%2A> method.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
    {
        Console.WriteLine("Hello World!");
    }
    ```

8. <span data-ttu-id="40af1-129"><xref:System.Activities.NativeActivity.CacheMetadata%2A> 메서드를 재정의하고 적합한 Add 메서드를 호출하여 워크플로 런타임에서 사용자 지정 활동의 변수, 인수, 자식 및 대리자를 알 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-129">Override the <xref:System.Activities.NativeActivity.CacheMetadata%2A> method and call the appropriate Add method to let the workflow runtime know about the custom activity’s variables, arguments, children, and delegates.</span></span> <span data-ttu-id="40af1-130">자세한 내용은 <xref:System.Activities.NativeActivityMetadata> 클래스를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40af1-130">For more information see the <xref:System.Activities.NativeActivityMetadata> class.</span></span>

9. <span data-ttu-id="40af1-131"><xref:System.Activities.NativeActivityContext> 개체를 사용하여 책갈피를 예약합니다.</span><span class="sxs-lookup"><span data-stu-id="40af1-131">Use the <xref:System.Activities.NativeActivityContext> object to schedule a bookmark.</span></span> <span data-ttu-id="40af1-132">책갈피를 만들고 예약하고 다시 시작하는 방법은 <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="40af1-132">See <xref:System.Activities.WorkflowApplicationIdleEventArgs.Bookmarks%2A> for details on how to create, schedule, and resume a bookmark.</span></span>

    ```csharp
    protected override void Execute(NativeActivityContext context)
        {
            // Create a Bookmark and wait for it to be resumed.
            context.CreateBookmark(BookmarkName.Get(context),
                new BookmarkCallback(OnResumeBookmark));
        }
    ```
