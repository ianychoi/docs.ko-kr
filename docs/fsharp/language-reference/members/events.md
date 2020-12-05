---
title: 이벤트
description: 'F # 이벤트를 사용 하 여 함수 호출을 GUI 프로그래밍에서 중요 한 사용자 동작에 연결 하는 방법을 알아봅니다.'
ms.date: 08/15/2020
ms.openlocfilehash: 17e0cc8840053bf24d5c69694fe94d544c44510d
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740343"
---
# <a name="events"></a><span data-ttu-id="ada14-103">이벤트</span><span class="sxs-lookup"><span data-stu-id="ada14-103">Events</span></span>

<span data-ttu-id="ada14-104">이벤트를 사용하면 함수 호출을 사용자 동작에 연결할 수 있습니다. 이벤트는 GUI 프로그래밍에서 중요한 부분을 차지합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-104">Events enable you to associate function calls with user actions and are important in GUI programming.</span></span> <span data-ttu-id="ada14-105">애플리케이션이나 운영 체제에서 이벤트를 트리거할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-105">Events can also be triggered by your applications or by the operating system.</span></span>

## <a name="handling-events"></a><span data-ttu-id="ada14-106">이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="ada14-106">Handling Events</span></span>

<span data-ttu-id="ada14-107">Windows Forms 또는 WPF(Windows Presentation Foundation) 같은 GUI 라이브러리를 사용하는 경우 애플리케이션의 코드 대부분은 라이브러리에 미리 정의되어 있는 이벤트에 대한 응답으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-107">When you use a GUI library like Windows Forms or Windows Presentation Foundation (WPF), much of the code in your application runs in response to events that are predefined by the library.</span></span> <span data-ttu-id="ada14-108">이렇게 미리 정의되어 있는 이벤트는 폼과 컨트롤 같은 GUI 클래스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-108">These predefined events are members of GUI classes such as forms and controls.</span></span> <span data-ttu-id="ada14-109">다음 코드에서 볼 수 있는 것처럼 `Click` 클래스의 `Form` 이벤트 같이 명명된 특정 이벤트를 참조하고 `Add` 메서드를 호출하여 단추 클릭 같은 기존 이벤트에 사용자 지정 동작을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-109">You can add custom behavior to a preexisting event, such as a button click, by referencing the specific named event of interest (for example, the `Click` event of the `Form` class) and invoking the `Add` method, as shown in the following code.</span></span> <span data-ttu-id="ada14-110">F# Interactive에서 이를 실행할 경우에는 `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`에 대한 호출을 생략합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-110">If you run this from F# Interactive, omit the call to `System.Windows.Forms.Application.Run(System.Windows.Forms.Form)`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3601.fs)]

<span data-ttu-id="ada14-111">`Add` 메서드의 형식은 `('a -> unit) -> unit`입니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-111">The type of the `Add` method is `('a -> unit) -> unit`.</span></span> <span data-ttu-id="ada14-112">따라서 이벤트 처리기 메서드는 매개 변수 하나를 사용하고 `unit`을 반환합니다. 이 메서드에 사용되는 매개 변수는 일반적으로 이벤트 인수입니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-112">Therefore, the event handler method takes one parameter, typically the event arguments, and returns `unit`.</span></span> <span data-ttu-id="ada14-113">위 예제에서는 이벤트 처리기가 람다 식으로 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-113">The previous example shows the event handler as a lambda expression.</span></span> <span data-ttu-id="ada14-114">이벤트 처리기는 다음 코드 예제에서와 같이 함수 값일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-114">The event handler can also be a function value, as in the following code example.</span></span> <span data-ttu-id="ada14-115">다음 코드 예제에서는 이벤트 처리기 매개 변수를 사용하여 이벤트의 형식에 맞는 특정 정보를 제공하는 방법도 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-115">The following code example also shows the use of the event handler parameters, which provide information specific to the type of event.</span></span> <span data-ttu-id="ada14-116">시스템에서는 `MouseMove` 이벤트에 대해 `System.Windows.Forms.MouseEventArgs` 개체를 전달합니다. 이 개체에는 포인터의 `X` 및 `Y` 위치가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-116">For a `MouseMove` event, the system passes a `System.Windows.Forms.MouseEventArgs` object, which contains the `X` and `Y` position of the pointer.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3602.fs)]

## <a name="creating-custom-events"></a><span data-ttu-id="ada14-117">사용자 지정 이벤트 만들기</span><span class="sxs-lookup"><span data-stu-id="ada14-117">Creating Custom Events</span></span>

<span data-ttu-id="ada14-118">F # 이벤트는 [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) 인터페이스를 구현 하는 f # [이벤트](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) 형식으로 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-118">F# events are represented by the F# [Event](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html) type, which implements the [IEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-ievent-1.html) interface.</span></span> <span data-ttu-id="ada14-119">`IEvent`자체는 다른 두 인터페이스 및 IDelegateEvent의 기능을 결합 하는 인터페이스입니다 `System.IObservable<'T>` . [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html)</span><span class="sxs-lookup"><span data-stu-id="ada14-119">`IEvent` is itself an interface that combines the functionality of two other interfaces, `System.IObservable<'T>` and [IDelegateEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-idelegateevent-1.html).</span></span> <span data-ttu-id="ada14-120">따라서 `Event`에는 다른 언어의 대리자와 동등한 기능에 더해 `IObservable`의 기능이 추가로 포함됩니다. 즉, F# 이벤트는 이벤트 필터링을 지원하며 F# 고급 함수와 람다 식을 이벤트 처리기로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-120">Therefore, `Event`s have the equivalent functionality of delegates in other languages, plus the additional functionality from `IObservable`, which means that F# events support event filtering and using F# first-class functions and lambda expressions as event handlers.</span></span> <span data-ttu-id="ada14-121">이 기능은 [이벤트 모듈](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html)에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-121">This functionality is provided in the [Event module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html).</span></span>

<span data-ttu-id="ada14-122">클래스에 대해 다른 .NET Framework 이벤트와 같은 방식으로 작동하는 이벤트를 만들려면 클래스의 필드로 `let` 를 정의하는 `Event` 바인딩을 클래스에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-122">To create an event on a class that acts just like any other .NET Framework event, add to the class a `let` binding that defines an `Event` as a field in a class.</span></span> <span data-ttu-id="ada14-123">원하는 이벤트 인수 형식을 형식 인수로 지정하거나, 인수 형식을 비워 두고 컴파일러가 적합한 형식을 유추하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-123">You can specify the desired event argument type as the type argument, or leave it blank and have the compiler infer the appropriate type.</span></span> <span data-ttu-id="ada14-124">또한 이벤트를 노출하는 이벤트 멤버를 CLI이벤트로 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-124">You also must define an event member that exposes the event as a CLI event.</span></span> <span data-ttu-id="ada14-125">이 멤버에는 [Clievent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) 특성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-125">This member should have the [CLIEvent](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-clieventattribute.html) attribute.</span></span> <span data-ttu-id="ada14-126">이 클래스는 속성으로 선언 되며, 해당 구현은 이벤트의 [게시](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) 속성에 대 한 호출 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-126">It is declared like a property and its implementation is just a call to the [Publish](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-fsharpevent-1.html#Publish) property of the event.</span></span> <span data-ttu-id="ada14-127">클래스 사용자는 게시된 이벤트의 `Add` 메서드를 사용하여 처리기를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-127">Users of your class can use the `Add` method of the published event to add a handler.</span></span> <span data-ttu-id="ada14-128">`Add` 메서드에 대한 인수는 람다 식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-128">The argument for the `Add` method can be a lambda expression.</span></span> <span data-ttu-id="ada14-129">이벤트의 `Trigger` 속성을 사용하여 이벤트를 발생시키고 인수를 처리기 함수에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-129">You can use the `Trigger` property of the event to raise the event, passing the arguments to the handler function.</span></span> <span data-ttu-id="ada14-130">다음 코드 예제에서는 그 구체적인 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-130">The following code example illustrates this.</span></span> <span data-ttu-id="ada14-131">이 예에서 이벤트에 대해 유추된 형식 인수는 람다 식의 인수를 나타내는 튜플입니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-131">In this example, the inferred type argument for the event is a tuple, which represents the arguments for the lambda expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3605.fs)]

<span data-ttu-id="ada14-132">출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-132">The output is as follows.</span></span>

```console
Event1 occurred! Object data: Hello World!
```

<span data-ttu-id="ada14-133">여기서는 `Event` 모듈을 통해 추가로 제공되는 기능을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-133">The additional functionality provided by the `Event` module is illustrated here.</span></span> <span data-ttu-id="ada14-134">다음 코드 예제에서는 `Event.create`를 사용하여 이벤트와 트리거 메서드를 만들고 이벤트 처리기 두 개를 람다 식 형태로 추가한 다음 이벤트를 트리거하여 두 람다 식을 실행하는 기본적인 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-134">The following code example illustrates the basic use of `Event.create` to create an event and a trigger method, add two event handlers in the form of lambda expressions, and then trigger the event to execute both lambda expressions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3603.fs)]

<span data-ttu-id="ada14-135">위 코드는 다음과 같이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-135">The output of the previous code is as follows.</span></span>

```console
Event occurred.
Given a value: Event occurred.
```

## <a name="processing-event-streams"></a><span data-ttu-id="ada14-136">이벤트 스트림 처리</span><span class="sxs-lookup"><span data-stu-id="ada14-136">Processing Event Streams</span></span>

<span data-ttu-id="ada14-137">Event [. add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) 함수를 사용 하 여 이벤트에 대 한 이벤트 처리기를 추가 하는 대신 모듈의 함수를 사용 `Event` 하 여 고도로 사용자 지정 된 방식으로 이벤트 스트림을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-137">Instead of just adding an event handler for an event by using the [Event.add](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-eventmodule.html#add) function, you can use the functions in the `Event` module to process streams of events in highly customized ways.</span></span> <span data-ttu-id="ada14-138">이를 위해서는 일련의 함수 호출에서 첫째 값으로 이벤트를 사용하고 이후의 함수 호출로는 `|>` 모듈 함수를 사용하면서 전달 파이프(`Event`)를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-138">To do this, you use the forward pipe (`|>`) together with the event as the first value in a series of function calls, and the `Event` module functions as subsequent function calls.</span></span>

<span data-ttu-id="ada14-139">다음 코드 예제에서는 특정 조건이 충족될 때만 처리기가 호출되는 이벤트를 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-139">The following code example shows how to set up an event for which the handler is only called under certain conditions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3604.fs)]

<span data-ttu-id="ada14-140">[관찰 가능한 모듈](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) 은 관찰 가능한 개체에서 작동 하는 유사한 함수를 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-140">The [Observable module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-control-observablemodule.html) contains similar functions that operate on observable objects.</span></span> <span data-ttu-id="ada14-141">관찰 가능한 개체는 이벤트와 비슷하지만 개체 자체가 구독 대상인 경우에만 능동적으로 이벤트를 구독합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-141">Observable objects are similar to events but only actively subscribe to events if they themselves are being subscribed to.</span></span>

## <a name="implementing-an-interface-event"></a><span data-ttu-id="ada14-142">인터페이스 이벤트 구현</span><span class="sxs-lookup"><span data-stu-id="ada14-142">Implementing an Interface Event</span></span>

<span data-ttu-id="ada14-143">UI 구성 요소를 개발할 때 종종 기존 폼 또는 컨트롤에서 상속하는 새 컨트롤 또는 새 폼을 만들어 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-143">As you develop UI components, you often start by creating a new form or a new control that inherits from an existing form or control.</span></span> <span data-ttu-id="ada14-144">이벤트는 인터페이스에서 자주 정의되며, 그럴 경우 이벤트를 구현하려면 인터페이스를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-144">Events are frequently defined on an interface, and, in that case, you must implement the interface to implement the event.</span></span> <span data-ttu-id="ada14-145">`System.ComponentModel.INotifyPropertyChanged` 인터페이스는 단일 `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` 이벤트를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-145">The `System.ComponentModel.INotifyPropertyChanged` interface defines a single `System.ComponentModel.INotifyPropertyChanged.PropertyChanged` event.</span></span> <span data-ttu-id="ada14-146">다음 코드에서는 이 상속된 인터페이스가 정의한 이벤트를 구현하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-146">The following code illustrates how to implement the event that this inherited interface defined:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

type AppForm() as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property-changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property-changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    // Expose the PropertyChanged event as a first class .NET event.
    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = propertyChanged.Publish.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = propertyChanged.Publish.RemoveHandler(handler)

    // This is the event-handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
let inpc = appForm :> INotifyPropertyChanged
inpc.PropertyChanged.Add(appForm.OnPropertyChanged)
Application.Run(appForm)
```

<span data-ttu-id="ada14-147">생성자에서 이벤트를 후크하려는 경우 다음 예제에서처럼 이벤트 연결이 추가 생성자의 `then` 블록에 있어야 하기 때문에 코드가 조금 더 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="ada14-147">If you want to hook up the event in the constructor, the code is a bit more complicated because the event hookup must be in a `then` block in an additional constructor, as in the following example:</span></span>

```fsharp
module CustomForm

open System.Windows.Forms
open System.ComponentModel

// Create a private constructor with a dummy argument so that the public
// constructor can have no arguments.
type AppForm private (dummy) as this =
    inherit Form()

    // Define the propertyChanged event.
    let propertyChanged = Event<PropertyChangedEventHandler, PropertyChangedEventArgs>()
    let mutable underlyingValue = "text0"

    // Set up a click event to change the properties.
    do
        this.Click |> Event.add(fun evArgs ->
            this.Property1 <- "text2"
            this.Property2 <- "text3")

    // This property does not have the property changed event set.
    member val Property1 : string = "text" with get, set

    // This property has the property changed event set.
    member this.Property2
        with get() = underlyingValue
        and set(newValue) =
            underlyingValue <- newValue
            propertyChanged.Trigger(this, new PropertyChangedEventArgs("Property2"))

    [<CLIEvent>]
    member this.PropertyChanged = propertyChanged.Publish

    // Define the add and remove methods to implement this interface.
    interface INotifyPropertyChanged with
        member this.add_PropertyChanged(handler) = this.PropertyChanged.AddHandler(handler)
        member this.remove_PropertyChanged(handler) = this.PropertyChanged.RemoveHandler(handler)

    // This is the event handler method.
    member this.OnPropertyChanged(args : PropertyChangedEventArgs) =
        let newProperty = this.GetType().GetProperty(args.PropertyName)
        let newValue = newProperty.GetValue(this :> obj) :?> string
        printfn "Property {args.PropertyName} changed its value to {newValue}"

    new() as this =
        new AppForm(0)
        then
            let inpc = this :> INotifyPropertyChanged
            inpc.PropertyChanged.Add(this.OnPropertyChanged)

// Create a form, hook up the event handler, and start the application.
let appForm = new AppForm()
Application.Run(appForm)
```

## <a name="see-also"></a><span data-ttu-id="ada14-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ada14-148">See also</span></span>

- [<span data-ttu-id="ada14-149">멤버</span><span class="sxs-lookup"><span data-stu-id="ada14-149">Members</span></span>](index.md)
- [<span data-ttu-id="ada14-150">이벤트 처리 및 발생</span><span class="sxs-lookup"><span data-stu-id="ada14-150">Handling and Raising Events</span></span>](../../../standard/events/index.md)
- [<span data-ttu-id="ada14-151">람다 식: `fun` 키워드</span><span class="sxs-lookup"><span data-stu-id="ada14-151">Lambda Expressions: The `fun` Keyword</span></span>](../functions/lambda-expressions-the-fun-keyword.md)
