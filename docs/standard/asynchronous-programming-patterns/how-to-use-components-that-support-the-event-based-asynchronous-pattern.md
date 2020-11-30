---
title: '방법: 이벤트 기반 비동기 패턴을 지원하는 구성 요소 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 35e9549c-1568-4768-ad07-17cc6dff11e1
ms.openlocfilehash: 36fe8015187833e03c4cc3fc1609ec647daf7278
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678001"
---
# <a name="how-to-use-components-that-support-the-event-based-asynchronous-pattern"></a><span data-ttu-id="df187-102">방법: 이벤트 기반 비동기 패턴을 지원하는 구성 요소 사용</span><span class="sxs-lookup"><span data-stu-id="df187-102">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="df187-103">많은 구성 요소가 비동기적으로 작업을 수행하는 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-103">Many components provide you with the option of performing their work asynchronously.</span></span> <span data-ttu-id="df187-104">예를 들어 <xref:System.Media.SoundPlayer> 및 <xref:System.Windows.Forms.PictureBox> 구성 요소를 사용하면 기본 스레드가 중단 없이 계속 실행되는 동안 사운드 및 이미지를 “배경”으로 로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df187-104">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components, for example, enable you to load sounds and images "in the background" while your main thread continues running without interruption.</span></span>  
  
 <span data-ttu-id="df187-105">[이벤트 기반 비동기 패턴 개요](event-based-asynchronous-pattern-overview.md)를 지원하는 클래스에 비동기 메서드를 사용하는 작업은 다른 이벤트의 경우와 같이 구성 요소의 _MethodName_**Completed** 이벤트에 이벤트 처리기를 연결하는 것처럼 간단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df187-105">Using asynchronous methods on a class that supports the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md) can be as simple as attaching an event handler to the component's _MethodName_**Completed** event, just as you would for any other event.</span></span> <span data-ttu-id="df187-106">_MethodName_**Async** 메서드를 호출하면 애플리케이션은 _MethodName_**Completed** 이벤트가 발생할 때까지 중단 없이 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="df187-106">When you call the _MethodName_**Async** method, your application will continue running without interruption until the _MethodName_**Completed** event is raised.</span></span> <span data-ttu-id="df187-107">이벤트 처리기에서 <xref:System.ComponentModel.AsyncCompletedEventArgs> 매개 변수를 검사하여 비동기 작업이 성공적으로 완료되었는지 또는 취소되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df187-107">In your event handler, you can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the asynchronous operation successfully completed or if it was canceled.</span></span>  
  
 <span data-ttu-id="df187-108">이벤트 처리기 사용에 대한 자세한 내용은 [이벤트 처리기 개요](/dotnet/desktop/winforms/event-handlers-overview-windows-forms)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="df187-108">For more information about using event handlers, see [Event Handlers Overview](/dotnet/desktop/winforms/event-handlers-overview-windows-forms).</span></span>  
  
 <span data-ttu-id="df187-109">다음 절차는 <xref:System.Windows.Forms.PictureBox> 컨트롤의 비동기 이미지 로드 기능을 사용하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="df187-109">The following procedure shows how to use the asynchronous image-loading capability of a <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-enable-a-picturebox-control-to-asynchronously-load-an-image"></a><span data-ttu-id="df187-110">PictureBox 컨트롤을 사용하여 이미지를 비동기적으로 로드하게 하려면</span><span class="sxs-lookup"><span data-stu-id="df187-110">To enable a PictureBox control to asynchronously load an image</span></span>  
  
1. <span data-ttu-id="df187-111">폼에서 <xref:System.Windows.Forms.PictureBox> 구성 요소의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="df187-111">Create an instance of the <xref:System.Windows.Forms.PictureBox> component in your form.</span></span>  
  
2. <span data-ttu-id="df187-112">이벤트 처리기를 <xref:System.Windows.Forms.PictureBox.LoadCompleted> 이벤트에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-112">Assign an event handler to the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event.</span></span>  
  
     <span data-ttu-id="df187-113">여기에서 비동기 다운로드 중에 발생했을 수 있는 오류를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-113">Check for any errors that may have occurred during the asynchronous download here.</span></span> <span data-ttu-id="df187-114">여기에서 취소를 확인할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df187-114">This is also where you check for cancellation.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#2](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#2)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#5](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#5)]  
  
3. <span data-ttu-id="df187-115">`loadButton` 및 `cancelLoadButton`이라는 두 개의 단추를 폼에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-115">Add two buttons, called `loadButton` and `cancelLoadButton`, to your form.</span></span> <span data-ttu-id="df187-116"><xref:System.Windows.Forms.Control.Click> 이벤트 처리기를 추가하여 다운로드를 시작 및 취소합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-116">Add <xref:System.Windows.Forms.Control.Click> event handlers to start and cancel the download.</span></span>  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#3](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.PictureBox.LoadAsync#4](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/Form1.vb#4)]  
  
4. <span data-ttu-id="df187-117">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="df187-117">Run your application.</span></span>  
  
     <span data-ttu-id="df187-118">이미지 다운로드가 진행되면 폼을 자유롭게 이동하고, 최소화하고, 최대화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="df187-118">As the image download proceeds, you can move the form freely, minimize it, and maximize it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df187-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="df187-119">See also</span></span>

- [<span data-ttu-id="df187-120">방법: 백그라운드에서 작업 실행</span><span class="sxs-lookup"><span data-stu-id="df187-120">How to: Run an Operation in the Background</span></span>](/dotnet/desktop/winforms/controls/how-to-run-an-operation-in-the-background)
- [<span data-ttu-id="df187-121">이벤트 기반 비동기 패턴 개요</span><span class="sxs-lookup"><span data-stu-id="df187-121">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
