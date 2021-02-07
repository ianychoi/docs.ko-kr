---
description: '자세한 정보: 예제: 동적 프로그래밍 문제 해결'
title: '예: 동적 프로그래밍 문제 해결'
ms.date: 03/30/2017
ms.assetid: 42ed860a-a022-4682-8b7f-7c9870784671
ms.openlocfilehash: 7ad3fde9c81800123abe899e2f696c3833fed5bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747857"
---
# <a name="example-troubleshooting-dynamic-programming"></a><span data-ttu-id="4d912-103">예: 동적 프로그래밍 문제 해결</span><span class="sxs-lookup"><span data-stu-id="4d912-103">Example: Troubleshooting Dynamic Programming</span></span>

> [!NOTE]
> <span data-ttu-id="4d912-104">이 항목은 시험판 소프트웨어인 .NET Native Developer Preview를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-104">This topic refers to the .NET Native Developer Preview, which is pre-release software.</span></span> <span data-ttu-id="4d912-105">이 Preview 버전은 [Microsoft Connect 웹 사이트](https://go.microsoft.com/fwlink/?LinkId=394611)에서 다운로드할 수 있습니다(등록 필요).</span><span class="sxs-lookup"><span data-stu-id="4d912-105">You can download the preview from the [Microsoft Connect website](https://go.microsoft.com/fwlink/?LinkId=394611) (requires registration).</span></span>  
  
 <span data-ttu-id="4d912-106">.NET 네이티브 도구 체인을 사용 하 여 개발 된 앱에서 일부 메타 데이터 조회 실패가 발생 하면 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-106">Not all metadata lookup failures in apps developed using the .NET Native tool chain result in an exception.</span></span>  <span data-ttu-id="4d912-107">앱에서 예기치 않은 방식으로 나타나는 오류도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-107">Some can manifest in unpredictable ways in an app.</span></span>  <span data-ttu-id="4d912-108">다음 예제에서는 null 개체를 참조하여 발생하는 액세스 위반을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-108">The following example shows an access violation caused by referencing a null object:</span></span>  
  
```output
Access violation - code c0000005 (first chance)  
App!$3_App::Core::Util::NavigationArgs.Setup  
App!$3_App::Core::Util::NavigationArgs..ctor  
App!$0_App::Gibbon::Util::DesktopNavigationArgs..ctor  
App!$0_App::ViewModels::DesktopAppVM.NavigateToPage  
App!$3_App::Core::ViewModels::AppViewModel.NavigateToFirstPage  
App!$3_App::Core::ViewModels::AppViewModel::<HandleLaunch>d__a.MoveNext  
App!$43_System::Runtime::CompilerServices::AsyncMethodBuilderCore.CallMoveNext  
App!System::Action.InvokeClosedStaticThunk  
App!System::Action.Invoke  
App!$43_System::Threading::Tasks::AwaitTaskContinuation.InvokeAction  
App!$43_System::Threading::SendOrPostCallback.InvokeOpenStaticThunk  
[snip]  
```  
  
 <span data-ttu-id="4d912-109">이제 [시작](getting-started-with-net-native.md)의 “수동으로 누락된 메타데이터 문제 해결” 섹션에서 설명하는 대로 3단계 방식을 통해 이 예외가 발생하는 문제를 해결해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-109">Let's try to troubleshoot this exception by using the three-step approach outlined in the "Manually resolve missing metadata" section of [Getting Started](getting-started-with-net-native.md).</span></span>  
  
## <a name="what-was-the-app-doing"></a><span data-ttu-id="4d912-110">앱이 어떤 작업을 수행 중이었나요?</span><span class="sxs-lookup"><span data-stu-id="4d912-110">What was the app doing?</span></span>  

 <span data-ttu-id="4d912-111">먼저 스택의 기반이 되는 `async` 키워드를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-111">The first thing to note is the `async` keyword machinery at the base of the stack.</span></span>  <span data-ttu-id="4d912-112">스택에서 원래 호출 컨텍스트가 손실되었으며 다른 스레드에 대해 `async` 코드가 실행되었기 때문에 `async` 메서드에서 앱이 실제로 수행 중이었던 작업을 확인하기가 어려울 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-112">Determining what the app was really doing in an `async` method can be problematic, because the stack has lost the context of the originating call and has run the `async` code on a different thread.</span></span> <span data-ttu-id="4d912-113">그러나 앱이 첫 페이지를 로드하고 있었다는 것은 추론할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-113">However, we can deduce that the app is trying to load its first page.</span></span>  <span data-ttu-id="4d912-114">`NavigationArgs.Setup` 구현에서는 다음 코드로 인해 액세스 위반이 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-114">In the implementation for `NavigationArgs.Setup`, the following code caused the access violation:</span></span>  
  
`AppViewModel.Current.LayoutVM.PageMap`  
  
 <span data-ttu-id="4d912-115">여기서는 `AppViewModel.Current`의 `LayoutVM` 속성이 **null** 이었습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-115">In this instance, the `LayoutVM` property on `AppViewModel.Current` was **null**.</span></span>  <span data-ttu-id="4d912-116">일부 메타데이터가 누락되어 동작이 약간 달라졌으며, 그로 인해 앱이 작동할 수 있도록 속성이 설정되는 대신 초기화되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-116">Some absence of metadata caused a subtle behavior difference and resulted in a property being uninitialized instead of set, as the app expected.</span></span>  <span data-ttu-id="4d912-117">코드에서 `LayoutVM`이 초기화되어야 하는 위치에 중단점을 설정하면 문제 해결에 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-117">Setting a breakpoint in the code where `LayoutVM` should have been initialized might throw light on the situation.</span></span>  <span data-ttu-id="4d912-118">그러나 `LayoutVM`의 형식은 `App.Core.ViewModels.Layout.LayoutApplicationVM`입니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-118">However, note that `LayoutVM`’s type is `App.Core.ViewModels.Layout.LayoutApplicationVM`.</span></span>  <span data-ttu-id="4d912-119">그러므로 rd.xml 파일에 지금까지 포함된 메타데이터 지시문은 다음 항목뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-119">The only metadata directive present so far in the rd.xml file is:</span></span>  
  
```xml  
<Namespace Name="App.ViewModels" Browse="Required Public" Dynamic="Required Public" />  
```  
  
 <span data-ttu-id="4d912-120">`App.Core.ViewModels.Layout.LayoutApplicationVM`이 다른 네임스페이스에 있어서 메타데이터가 누락되었기 때문에 오류가 발생했을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-120">A likely candidate for the failure is that `App.Core.ViewModels.Layout.LayoutApplicationVM` is missing metadata because it's in a different namespace.</span></span>  
  
 <span data-ttu-id="4d912-121">이 경우 `App.Core.ViewModels`에 대해 런타임 지시문을 추가하면 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-121">In this case, adding a runtime directive for `App.Core.ViewModels` resolved the issue.</span></span> <span data-ttu-id="4d912-122">근본 원인은 <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> 메서드에 대한 API 호출에서 **null** 이 반환된 것이며, 앱은 충돌이 해결될 때까지 문제를 자동으로 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-122">The root cause was an API call to the <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> method that returned **null**, and the app silently ignored the problem until a crash occurred.</span></span>  
  
 <span data-ttu-id="4d912-123">동적 프로그래밍에서 .NET 네이티브에서 리플렉션 Api를 사용할 때는 <xref:System.Type.GetType%2A?displayProperty=nameWithType> 오류 발생 시 예외를 throw 하는 오버 로드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-123">In dynamic programming, a good practice when using reflection APIs under .NET Native is to use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> overloads that throw an exception on failure.</span></span>  
  
## <a name="is-this-an-isolated-case"></a><span data-ttu-id="4d912-124">사례의 격리 여부 확인</span><span class="sxs-lookup"><span data-stu-id="4d912-124">Is this an isolated case?</span></span>  

 <span data-ttu-id="4d912-125">`App.Core.ViewModels` 사용 시에는 다른 문제도 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-125">Other issues might also arise when using `App.Core.ViewModels`.</span></span>  <span data-ttu-id="4d912-126">따라서 각 메타데이터 누락 예외를 파악하여 수정할지 아니면 시간 절약을 위해 대형 형식 클래스에 대한 지시문을 추가할지를 결정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-126">You must decide whether it’s worth identifying and fixing each missing metadata exception, or saving time and adding directives for a larger class of types.</span></span>  <span data-ttu-id="4d912-127">여기서는 생성되는 출력 바이너리의 크기가 증가해도 문제가 없다면 `dynamic`에 대해 `App.Core.ViewModels` 메타데이터를 추가하는 것이 가장 효율적인 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-127">Here, adding `dynamic` metadata for `App.Core.ViewModels` might be the best approach if the resulting size increase of the output binary isn’t an issue.</span></span>  
  
## <a name="could-the-code-be-rewritten"></a><span data-ttu-id="4d912-128">코드 다시 작성 가능 여부 확인</span><span class="sxs-lookup"><span data-stu-id="4d912-128">Could the code be rewritten?</span></span>  

 <span data-ttu-id="4d912-129">앱에서 `typeof(LayoutApplicationVM)` 대신 `Type.GetType("LayoutApplicationVM")`를 사용했다면 도구 체인이 `browse` 메타데이터를 보존했을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-129">If the app had used `typeof(LayoutApplicationVM)` instead of `Type.GetType("LayoutApplicationVM")`, the tool chain could have preserved `browse` metadata.</span></span>  <span data-ttu-id="4d912-130">그러나 `invoke` 메타데이터는 작성되지 않았으므로 형식을 인스턴스화할 때 [MissingMetadataException](missingmetadataexception-class-net-native.md) 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-130">However, it still wouldn't have created `invoke` metadata, which would have led to a [MissingMetadataException](missingmetadataexception-class-net-native.md) exception when instantiating the type.</span></span> <span data-ttu-id="4d912-131">이 예외를 방지하려면 `dynamic` 정책을 지정하는 형식 또는 네임스페이스에 대해 런타임 지시문을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4d912-131">To prevent the exception, you'd still have to add a runtime directive for the namespace or the type that specifies the `dynamic` policy.</span></span> <span data-ttu-id="4d912-132">런타임 지시문에 대한 자세한 내용은 [런타임 지시문(rd.xml) 구성 파일 참조](runtime-directives-rd-xml-configuration-file-reference.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="4d912-132">For information on runtime directives, see the [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d912-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="4d912-133">See also</span></span>

- [<span data-ttu-id="4d912-134">시작</span><span class="sxs-lookup"><span data-stu-id="4d912-134">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="4d912-135">예: 데이터를 바인딩하는 경우 예외 처리</span><span class="sxs-lookup"><span data-stu-id="4d912-135">Example: Handling Exceptions When Binding Data</span></span>](example-handling-exceptions-when-binding-data.md)
