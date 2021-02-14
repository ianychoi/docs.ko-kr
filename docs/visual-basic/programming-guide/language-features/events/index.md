---
description: '다음에 대 한 자세한 정보: 이벤트 (Visual Basic)'
title: 이벤트
ms.date: 07/20/2015
helpviewer_keywords:
- events [Visual Basic], about events
- events [Visual Basic]
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
ms.openlocfilehash: 6cd4a4b997ec13b394cae38e9d66c7dd9c283aaf
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483679"
---
# <a name="events-visual-basic"></a><span data-ttu-id="b3772-103">이벤트(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3772-103">Events (Visual Basic)</span></span>

<span data-ttu-id="b3772-104">Visual Studio 프로젝트를 순서 대로 실행 되는 일련의 프로시저로 시각화할 수도 있지만 실제로 대부분의 프로그램은 이벤트 구동 방식입니다. 즉, 실행 흐름이 *이벤트* 라는 외부 발생에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-104">While you might visualize a Visual Studio project as a series of procedures that execute in a sequence, in reality, most programs are event driven—meaning the flow of execution is determined by external occurrences called *events*.</span></span>  
  
 <span data-ttu-id="b3772-105">이벤트는 중요한 문제가 발생했음을 애플리케이션에 알리는 신호입니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-105">An event is a signal that informs an application that something important has occurred.</span></span> <span data-ttu-id="b3772-106">예를 들어 사용자가 폼의 컨트롤을 클릭하면 폼이 `Click` 이벤트를 발생시키고 이벤트를 처리하는 프로시저를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-106">For example, when a user clicks a control on a form, the form can raise a `Click` event and call a procedure that handles the event.</span></span> <span data-ttu-id="b3772-107">또한 이벤트는 개별 작업이 통신할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-107">Events also allow separate tasks to communicate.</span></span> <span data-ttu-id="b3772-108">예를 들어 애플리케이션이 주 애플리케이션과는 별도로 정렬 작업을 수행한다고 가정해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-108">Say, for example, that your application performs a sort task separately from the main application.</span></span> <span data-ttu-id="b3772-109">사용자가 정렬을 취소하면 애플리케이션은 정렬 프로세스를 중지하도록 지시하는 취소 이벤트를 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-109">If a user cancels the sort, your application can send a cancel event instructing the sort process to stop.</span></span>  
  
## <a name="event-terms-and-concepts"></a><span data-ttu-id="b3772-110">이벤트 용어 및 개념</span><span class="sxs-lookup"><span data-stu-id="b3772-110">Event Terms and Concepts</span></span>  

 <span data-ttu-id="b3772-111">이 섹션에서는 Visual Basic 이벤트에 사용 되는 용어 및 개념에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-111">This section describes the terms and concepts used with events in Visual Basic.</span></span>  
  
### <a name="declaring-events"></a><span data-ttu-id="b3772-112">이벤트 선언</span><span class="sxs-lookup"><span data-stu-id="b3772-112">Declaring Events</span></span>  

 <span data-ttu-id="b3772-113">다음 예제와 같이 `Event` 키워드를 사용하여 클래스, 구조체, 모듈 및 인터페이스를 사용하여 이벤트를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-113">You declare events within classes, structures, modules, and interfaces using the `Event` keyword, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#24)]  
  
### <a name="raising-events"></a><span data-ttu-id="b3772-114">이벤트 발생</span><span class="sxs-lookup"><span data-stu-id="b3772-114">Raising Events</span></span>  

 <span data-ttu-id="b3772-115">이벤트는 중요한 문제가 발생했음을 알리는 메시지와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-115">An event is like a message announcing that something important has occurred.</span></span> <span data-ttu-id="b3772-116">메시지를 브로드캐스트하는 동작을 이벤트 *발생* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-116">The act of broadcasting the message is called *raising* the event.</span></span> <span data-ttu-id="b3772-117">Visual Basic에서 `RaiseEvent` 다음 예제와 같이 문을 사용 하 여 이벤트를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-117">In Visual Basic, you raise events with the `RaiseEvent` statement, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#25)]  
  
 <span data-ttu-id="b3772-118">선언된 클래스, 모듈 또는 구조체의 범위 내에서 이벤트가 발생되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-118">Events must be raised within the scope of the class, module, or structure where they are declared.</span></span> <span data-ttu-id="b3772-119">예를 들어 파생 클래스는 기본 클래스에서 상속된 이벤트를 발생시킬 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-119">For example, a derived class cannot raise events inherited from a base class.</span></span>  
  
### <a name="event-senders"></a><span data-ttu-id="b3772-120">이벤트 전송자</span><span class="sxs-lookup"><span data-stu-id="b3772-120">Event Senders</span></span>  

 <span data-ttu-id="b3772-121">이벤트를 발생시킬 수 있는 개체는 *이벤트 소스* 라고도 하는 *이벤트 전송자* 입니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-121">Any object capable of raising an event is an *event sender*, also known as an *event source*.</span></span> <span data-ttu-id="b3772-122">폼, 컨트롤 및 사용자 정의 개체는 이벤트 전송자에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-122">Forms, controls, and user-defined objects are examples of event senders.</span></span>  
  
### <a name="event-handlers"></a><span data-ttu-id="b3772-123">이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="b3772-123">Event Handlers</span></span>  

 <span data-ttu-id="b3772-124">*이벤트 처리기* 는 해당 이벤트가 발생할 때 호출되는 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-124">*Event handlers* are procedures that are called when a corresponding event occurs.</span></span> <span data-ttu-id="b3772-125">서명이 일치하는 모든 유효한 서브루틴을 이벤트 처리기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-125">You can use any valid subroutine with a matching signature as an event handler.</span></span> <span data-ttu-id="b3772-126">그러나 함수는 이벤트 처리기로 사용할 수 없습니다. 이벤트 소스에 값을 반환할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-126">You cannot use a function as an event handler, however, because it cannot return a value to the event source.</span></span>  
  
 <span data-ttu-id="b3772-127">Visual Basic는 이벤트 보낸 사람의 이름, 밑줄 및 이벤트 이름을 결합 하는 이벤트 처리기에 표준 명명 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-127">Visual Basic uses a standard naming convention for event handlers that combines the name of the event sender, an underscore, and the name of the event.</span></span> <span data-ttu-id="b3772-128">예를 들어 `button1`이라는 단추의 `Click` 이벤트의 이름은 `Sub button1_Click`으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-128">For example, the `Click` event of a button named `button1` would be named `Sub button1_Click`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3772-129">사용자 고유의 이벤트에 대해 이벤트 처리기를 정의하는 경우 이러한 명명 규칙을 사용하는 것이 좋지만 필수는 아닙니다. 유효한 어떤 서브루틴 이름도 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-129">We recommend that you use this naming convention when defining event handlers for your own events, but it is not required; you can use any valid subroutine name.</span></span>  
  
## <a name="associating-events-with-event-handlers"></a><span data-ttu-id="b3772-130">이벤트를 이벤트 처리기에 연결</span><span class="sxs-lookup"><span data-stu-id="b3772-130">Associating Events with Event Handlers</span></span>  

 <span data-ttu-id="b3772-131">이벤트 처리기를 사용하려면 먼저 `Handles` 또는 `AddHandler` 문을 사용하여 이벤트 처리기를 이벤트에 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-131">Before an event handler becomes usable, you must first associate it with an event by using either the `Handles` or `AddHandler` statement.</span></span>  
  
### <a name="withevents-and-the-handles-clause"></a><span data-ttu-id="b3772-132">WithEvents 및 Handles 절</span><span class="sxs-lookup"><span data-stu-id="b3772-132">WithEvents and the Handles Clause</span></span>  

 <span data-ttu-id="b3772-133">`WithEvents` 문 및 `Handles` 절은 이벤트 처리기를 지정하는 선언적 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-133">The `WithEvents` statement and `Handles` clause provide a declarative way of specifying event handlers.</span></span> <span data-ttu-id="b3772-134">`WithEvents` 키워드로 선언된 개체에 의해 발생된 이벤트는 다음 그림과 같이 해당 이벤트에 대한 `Handles` 문을 사용하는 모든 프로시저에 의해 처리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-134">An event raised by an object declared with the `WithEvents` keyword can be handled by any procedure with a `Handles` statement for that event, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbalrEvents#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#1)]  
  
 <span data-ttu-id="b3772-135">`WithEvents` 문 및 `Handles` 절은 선언적 구문을 사용하여 이벤트 처리를 보다 쉽게 코딩하고 읽고 디버그할 수 있도록 하므로 이벤트 처리기에 가장 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-135">The `WithEvents` statement and the `Handles` clause are often the best choice for event handlers because the declarative syntax they use makes event handling easier to code, read and debug.</span></span> <span data-ttu-id="b3772-136">그러나 `WithEvents` 변수를 사용할 때는 다음과 같은 제한 사항이 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-136">However, be aware of the following limitations on the use of `WithEvents` variables:</span></span>  
  
- <span data-ttu-id="b3772-137">`WithEvents` 변수를 개체 변수로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-137">You cannot use a `WithEvents` variable as an object variable.</span></span> <span data-ttu-id="b3772-138">즉, `Object`로 선언할 수 없습니다. 따라서 변수를 선언할 때는 클래스 이름을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-138">That is, you cannot declare it as `Object`—you must specify the class name when you declare the variable.</span></span>  
  
- <span data-ttu-id="b3772-139">공유 이벤트는 클래스 인스턴스에 연결 되지 않으므로를 사용 `WithEvents` 하 여 shared 이벤트를 선언적으로 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-139">Because shared events are not tied to class instances, you cannot use `WithEvents` to declaratively handle shared events.</span></span> <span data-ttu-id="b3772-140">마찬가지로 `WithEvents` 또는 `Handles`를 사용하여 `Structure`의 이벤트를 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-140">Similarly, you cannot use `WithEvents` or `Handles` to handle events from a `Structure`.</span></span> <span data-ttu-id="b3772-141">두 경우 모두 `AddHandler` 문을 사용해서 해당 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-141">In both cases, you can use the `AddHandler` statement to handle those events.</span></span>  
  
- <span data-ttu-id="b3772-142">`WithEvents` 변수 배열을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-142">You cannot create arrays of `WithEvents` variables.</span></span>  
  
 <span data-ttu-id="b3772-143">`WithEvents` 변수는 단일 이벤트 처리기로 하나 이상의 이벤트 종류를 처리하거나, 하나 이상의 이벤트 처리기로 동일한 종류의 이벤트를 처리하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-143">`WithEvents` variables allow a single event handler to handle one or more kind of event, or one or more event handlers to handle the same kind of event.</span></span>  
  
 <span data-ttu-id="b3772-144">`Handles` 절은 이벤트를 이벤트 처리기와 연결하는 표준 방법이지만 컴파일 타임에 이벤트를 이벤트 처리기와 연결하도록 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-144">Although the `Handles` clause is the standard way of associating an event with an event handler, it is limited to associating events with event handlers at compile time.</span></span>  
  
 <span data-ttu-id="b3772-145">양식이 나 컨트롤과 연결 된 이벤트와 같은 일부 경우에는 빈 이벤트 처리기를 자동으로 스텁 하 여 이벤트에 연결 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b3772-145">In some cases, such as with events associated with forms or controls, Visual Basic automatically stubs out an empty event handler and associates it with an event.</span></span> <span data-ttu-id="b3772-146">예를 들어 디자인 모드에서 폼의 명령 단추를 두 번 클릭 하면 `WithEvents` 다음 코드와 같이 명령 단추에 대해 빈 이벤트 처리기와 변수를 Visual Basic 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-146">For example, when you double-click a command button on a form in design mode, Visual Basic creates an empty event handler and a `WithEvents` variable for the command button, as in the following code:</span></span>  
  
 [!code-vb[VbVbalrEvents#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#26)]  
  
### <a name="addhandler-and-removehandler"></a><span data-ttu-id="b3772-147">AddHandler 및 RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="b3772-147">AddHandler and RemoveHandler</span></span>  

 <span data-ttu-id="b3772-148">`AddHandler` 문은 둘 다 이벤트 처리기를 지정할 수 있다는 측면에서 `Handles` 절과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-148">The `AddHandler` statement is similar to the `Handles` clause in that both allow you to specify an event handler.</span></span> <span data-ttu-id="b3772-149">그러나 `AddHandler`를 `RemoveHandler`와 함께 사용하면 `Handles` 절보다 유연성이 높아져서 이벤트와 연결된 이벤트 처리기를 동적으로 추가, 제거 및 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-149">However, `AddHandler`, used with `RemoveHandler`, provides greater flexibility than the `Handles` clause, allowing you to dynamically add, remove, and change the event handler associated with an event.</span></span> <span data-ttu-id="b3772-150">공유 이벤트 또는 구조체의 이벤트를 처리하려는 경우 `AddHandler`를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-150">If you want to handle shared events or events from a structure, you must use `AddHandler`.</span></span>  
  
 <span data-ttu-id="b3772-151">`AddHandler`는 두 개의 인수, 즉 컨트롤과 같은 이벤트 전송자의 이벤트 이름과 대리자로 평가되는 식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-151">`AddHandler` takes two arguments: the name of an event from an event sender such as a control, and an expression that evaluates to a delegate.</span></span> <span data-ttu-id="b3772-152">`AddressOf` 문은 항상 대리자에 대한 참조를 반환하므로 `AddHandler`를 사용할 경우 대리자 클래스를 명시적으로 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-152">You do not need to explicitly specify the delegate class when using `AddHandler`, since the `AddressOf` statement always returns a reference to the delegate.</span></span> <span data-ttu-id="b3772-153">다음 예제에서는 개체에 의해 발생하는 이벤트와 이벤트 처리기를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-153">The following example associates an event handler with an event raised by an object:</span></span>  
  
 [!code-vb[VbVbalrEvents#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#28)]  
  
 <span data-ttu-id="b3772-154">이벤트 처리기에서 이벤트의 연결을 끊는 `RemoveHandler`는 `AddHandler`와 동일한 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-154">`RemoveHandler`, which disconnects an event from an event handler, uses the same syntax as `AddHandler`.</span></span> <span data-ttu-id="b3772-155">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-155">For example:</span></span>  
  
 [!code-vb[VbVbalrEvents#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#29)]  
  
 <span data-ttu-id="b3772-156">다음 예제에서 이벤트 처리기는 이벤트와 연결되고 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-156">In the following example, an event handler is associated with an event, and the event is raised.</span></span> <span data-ttu-id="b3772-157">이벤트 처리기는 이벤트를 catch하고 메시지를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-157">The event handler catches the event and displays a message.</span></span>  
  
 <span data-ttu-id="b3772-158">그런 다음 첫 번째 이벤트 처리기가 제거되고 다른 이벤트 처리기가 이벤트와 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-158">Then the first event handler is removed and a different event handler is associated with the event.</span></span> <span data-ttu-id="b3772-159">이벤트가 다시 발생하면 다른 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-159">When the event is raised again, a different message is displayed.</span></span>  
  
 <span data-ttu-id="b3772-160">마지막으로 두 번째 이벤트 처리기가 제거되고 세 번째로 해당 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-160">Finally, the second event handler is removed and the event is raised for a third time.</span></span> <span data-ttu-id="b3772-161">해당 이벤트와 연결된 이벤트 처리기가 더 이상 없으므로 아무 작업도 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-161">Because there is no longer an event handler associated with the event, no action is taken.</span></span>  
  
 [!code-vb[VbVbalrEvents#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class2.vb#38)]  
  
## <a name="handling-events-inherited-from-a-base-class"></a><span data-ttu-id="b3772-162">기본 클래스에서 상속된 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="b3772-162">Handling Events Inherited from a Base Class</span></span>  

 <span data-ttu-id="b3772-163">기본 클래스에서 특성을 상속하는 클래스인 *파생 클래스* 는 `Handles MyBase` 문을 사용하여 기본 클래스에 의해 발생된 이벤트를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-163">*Derived classes*—classes that inherit characteristics from a base class—can handle events raised by their base class using the `Handles MyBase` statement.</span></span>  
  
### <a name="to-handle-events-from-a-base-class"></a><span data-ttu-id="b3772-164">기본 클래스의 이벤트를 처리하려면</span><span class="sxs-lookup"><span data-stu-id="b3772-164">To handle events from a base class</span></span>  
  
- <span data-ttu-id="b3772-165">이벤트 처리기 프로시저의 선언 줄에 `Handles MyBase.`*eventname* 문을 추가하여 파생 클래스에서 이벤트 처리기를 선언합니다. 여기서 *eventname* 은 처리하는 기본 클래스의 이벤트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-165">Declare an event handler in the derived class by adding a `Handles MyBase.`*eventname* statement to the declaration line of your event-handler procedure, where *eventname* is the name of the event in the base class you are handling.</span></span> <span data-ttu-id="b3772-166">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-166">For example:</span></span>  
  
     [!code-vb[VbVbalrEvents#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#12)]  
  
## <a name="related-sections"></a><span data-ttu-id="b3772-167">관련 단원</span><span class="sxs-lookup"><span data-stu-id="b3772-167">Related Sections</span></span>  
  
|<span data-ttu-id="b3772-168">제목</span><span class="sxs-lookup"><span data-stu-id="b3772-168">Title</span></span>|<span data-ttu-id="b3772-169">설명</span><span class="sxs-lookup"><span data-stu-id="b3772-169">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b3772-170">연습: 이벤트 선언 및 발생</span><span class="sxs-lookup"><span data-stu-id="b3772-170">Walkthrough: Declaring and Raising Events</span></span>](walkthrough-declaring-and-raising-events.md)|<span data-ttu-id="b3772-171">클래스의 이벤트를 선언하고 발생시키는 방법에 대한 단계별 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-171">Provides a step-by-step description of how to declare and raise events for a class.</span></span>|  
|[<span data-ttu-id="b3772-172">연습: 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="b3772-172">Walkthrough: Handling Events</span></span>](walkthrough-handling-events.md)|<span data-ttu-id="b3772-173">이벤트 처리기 프로시저를 작성하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-173">Demonstrates how to write an event-handler procedure.</span></span>|  
|[<span data-ttu-id="b3772-174">방법: 차단을 방지하는 사용자 지정 이벤트 선언</span><span class="sxs-lookup"><span data-stu-id="b3772-174">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)|<span data-ttu-id="b3772-175">이벤트 처리기를 비동기적으로 호출할 수 있는 사용자 지정 이벤트를 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-175">Demonstrates how to define a custom event that allows its event handlers to be called asynchronously.</span></span>|  
|[<span data-ttu-id="b3772-176">방법: 메모리를 절약하는 사용자 지정 이벤트 선언</span><span class="sxs-lookup"><span data-stu-id="b3772-176">How to: Declare Custom Events To Conserve Memory</span></span>](how-to-declare-custom-events-to-conserve-memory.md)|<span data-ttu-id="b3772-177">이벤트가 처리될 때만 메모리를 사용하는 사용자 지정 이벤트를 정의하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-177">Demonstrates how to define a custom event that uses memory only when the event is handled.</span></span>|  
|[<span data-ttu-id="b3772-178">Visual Basic에서 상속된 이벤트 처리기 관련 문제 해결</span><span class="sxs-lookup"><span data-stu-id="b3772-178">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](troubleshooting-inherited-event-handlers.md)|<span data-ttu-id="b3772-179">상속된 구성 요소의 이벤트 처리기에서 발생하는 일반적인 문제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-179">Lists common issues that arise with event handlers in inherited components.</span></span>|  
|[<span data-ttu-id="b3772-180">이벤트</span><span class="sxs-lookup"><span data-stu-id="b3772-180">Events</span></span>](../../../../standard/events/index.md)|<span data-ttu-id="b3772-181">.NET Framework의 이벤트 모델 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-181">Provides an overview of the event model in the .NET Framework.</span></span>|  
|[<span data-ttu-id="b3772-182">Windows Forms에서 이벤트 처리기 만들기</span><span class="sxs-lookup"><span data-stu-id="b3772-182">Creating Event Handlers in Windows Forms</span></span>](/dotnet/desktop/winforms/creating-event-handlers-in-windows-forms)|<span data-ttu-id="b3772-183">Windows Forms 개체와 관련된 이벤트로 작업하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-183">Describes how to work with events associated with Windows Forms objects.</span></span>|  
|[<span data-ttu-id="b3772-184">대리자</span><span class="sxs-lookup"><span data-stu-id="b3772-184">Delegates</span></span>](../delegates/index.md)|<span data-ttu-id="b3772-185">Visual Basic의 대리자에 대해 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b3772-185">Provides an overview of delegates in Visual Basic.</span></span>|
