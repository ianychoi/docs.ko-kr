---
description: '자세한 정보: 이벤트 디자인'
title: 이벤트 디자인
ms.date: 10/22/2008
helpviewer_keywords:
- pre-events
- events [.NET Framework], design guidelines
- member design guidelines, events
- event handlers [.NET Framework], event design guidelines
- post-events
- signatures, event handling
ms.assetid: 67b3c6e2-6a8f-480d-a78f-ebeeaca1b95a
ms.openlocfilehash: d64bfb13792aa9d646560de844acddd9b7e188c0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642203"
---
# <a name="event-design"></a><span data-ttu-id="5052f-103">이벤트 디자인</span><span class="sxs-lookup"><span data-stu-id="5052f-103">Event Design</span></span>

<span data-ttu-id="5052f-104">이벤트는 가장 일반적으로 사용되는 형식의 콜백(프레임워크에서 사용자 코드를 호출할 수 있도록 하는 구문)입니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-104">Events are the most commonly used form of callbacks (constructs that allow the framework to call into user code).</span></span> <span data-ttu-id="5052f-105">다른 콜백 메커니즘으로는 대리자를 사용하는 멤버, 가상 멤버, 인터페이스 기반 플러그 인이 있습니다. 유용성 연구의 데이터에 따르면 대다수 개발자가 다른 콜백 메커니즘을 사용할 때보다 이벤트를 사용할 때 더 편안하다고 합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-105">Other callback mechanisms include members taking delegates, virtual members, and interface-based plug-ins. Data from usability studies indicate that the majority of developers are more comfortable using events than they are using the other callback mechanisms.</span></span> <span data-ttu-id="5052f-106">이벤트는 Visual Studio 및 많은 언어와 적절히 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-106">Events are nicely integrated with Visual Studio and many languages.</span></span>

 <span data-ttu-id="5052f-107">이벤트에는 시스템 상태 변경 이전에 발생한 이벤트(사전 이벤트)와 상태 변경 후 발생한 이벤트(사후 이벤트)의 두 그룹이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-107">It is important to note that there are two groups of events: events raised before a state of the system changes, called pre-events, and events raised after a state changes, called post-events.</span></span> <span data-ttu-id="5052f-108">사전 이벤트의 예로는 `Form.Closing`이 있으며, 양식을 닫기 전에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-108">An example of a pre-event would be `Form.Closing`, which is raised before a form is closed.</span></span> <span data-ttu-id="5052f-109">사후 이벤트의 예로는 `Form.Closed`가 있으며, 양식을 닫은 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-109">An example of a post-event would be `Form.Closed`, which is raised after a form is closed.</span></span>

 <span data-ttu-id="5052f-110">✔️ 이벤트에는 “fire(발생)” 또는 “trigger(트리거)”가 아닌 “raise(발생)”라는 용어를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-110">✔️ DO use the term "raise" for events rather than "fire" or "trigger."</span></span>

 <span data-ttu-id="5052f-111">✔️ 이벤트 처리기로 사용할 새 대리자를 수동으로 만드는 대신 <xref:System.EventHandler%601?displayProperty=nameWithType>를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-111">✔️ DO use <xref:System.EventHandler%601?displayProperty=nameWithType> instead of manually creating new delegates to be used as event handlers.</span></span>

 <span data-ttu-id="5052f-112">✔️ 이벤트가 이벤트 처리 메서드에 데이터를 전달할 필요가 없다고 확신할 수 없다면 <xref:System.EventArgs>의 서브클래스를 이벤트 인수로 사용하는 것이 좋습니다. 이 경우 `EventArgs` 형식을 직접 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-112">✔️ CONSIDER using a subclass of <xref:System.EventArgs> as the event argument, unless you are absolutely sure the event will never need to carry any data to the event handling method, in which case you can use the `EventArgs` type directly.</span></span>

 <span data-ttu-id="5052f-113">`EventArgs`를 직접 사용하는 API를 제공하는 경우 호환성을 손상하지 않고 이벤트와 함께 전달할 데이터를 추가할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-113">If you ship an API using `EventArgs` directly, you will never be able to add any data to be carried with the event without breaking compatibility.</span></span> <span data-ttu-id="5052f-114">서브클래스를 사용하면 처음에는 완전히 비어 있지만 필요할 때 서브클래스에 속성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-114">If you use a subclass, even if initially completely empty, you will be able to add properties to the subclass when needed.</span></span>

 <span data-ttu-id="5052f-115">✔️ 각 이벤트를 발생시키려면 보호된 가상 메서드를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-115">✔️ DO use a protected virtual method to raise each event.</span></span> <span data-ttu-id="5052f-116">이 지침은 구조체, 봉인된 클래스 또는 정적 이벤트가 아니라 봉인되지 않은 클래스의 비정적 이벤트에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-116">This is only applicable to nonstatic events on unsealed classes, not to structs, sealed classes, or static events.</span></span>

 <span data-ttu-id="5052f-117">메서드의 용도는 파생 클래스가 재정의를 사용하여 이벤트를 처리하는 방법을 제공하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-117">The purpose of the method is to provide a way for a derived class to handle the event using an override.</span></span> <span data-ttu-id="5052f-118">재정의는 파생 클래스에서 기본 클래스 이벤트를 처리하는, 더 유연하고 신속하며 자연스러운 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-118">Overriding is a more flexible, faster, and more natural way to handle base class events in derived classes.</span></span> <span data-ttu-id="5052f-119">규칙에 따라 메서드의 이름은 “On”으로 시작하고 이벤트의 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-119">By convention, the name of the method should start with "On" and be followed with the name of the event.</span></span>

 <span data-ttu-id="5052f-120">파생 클래스는 재정의에서 메서드의 기본 구현을 호출하지 않도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-120">The derived class can choose not to call the base implementation of the method in its override.</span></span> <span data-ttu-id="5052f-121">이렇게 준비하려면 기본 클래스가 제대로 작동하는 데 필요한 메서드에 처리를 포함하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-121">Be prepared for this by not including any processing in the method that is required for the base class to work correctly.</span></span>

 <span data-ttu-id="5052f-122">✔️ 이벤트를 발생시키는 보호된 메서드에 하나의 매개 변수를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-122">✔️ DO take one parameter to the protected method that raises an event.</span></span>

 <span data-ttu-id="5052f-123">매개 변수는 `e`로 이름을 지정하고 이벤트 인수 클래스로 형식화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-123">The parameter should be named `e` and should be typed as the event argument class.</span></span>

 <span data-ttu-id="5052f-124">❌ 비정적 이벤트를 발생시킬 때 보낸 사람으로 null을 전달하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-124">❌ DO NOT pass null as the sender when raising a nonstatic event.</span></span>

 <span data-ttu-id="5052f-125">✔️ 정적 이벤트를 발생시킬 때 보낸 사람으로 null을 전달하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-125">✔️ DO pass null as the sender when raising a static event.</span></span>

 <span data-ttu-id="5052f-126">❌ 이벤트를 발생시킬 때 이벤트 데이터 매개 변수로 null을 전달하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-126">❌ DO NOT pass null as the event data parameter when raising an event.</span></span>

 <span data-ttu-id="5052f-127">이벤트 처리 메서드에 데이터를 전달하지 않으려는 경우 `EventArgs.Empty`를 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-127">You should pass `EventArgs.Empty` if you don’t want to pass any data to the event handling method.</span></span> <span data-ttu-id="5052f-128">개발자는 이 매개 변수가 null이 아닌 것으로 예상합니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-128">Developers expect this parameter not to be null.</span></span>

 <span data-ttu-id="5052f-129">✔️ 최종 사용자가 취소할 수 있는 이벤트를 발생시키는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-129">✔️ CONSIDER raising events that the end user can cancel.</span></span> <span data-ttu-id="5052f-130">이 지침은 사전 이벤트에만 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-130">This only applies to pre-events.</span></span>

 <span data-ttu-id="5052f-131">최종 사용자가 이벤트를 취소할 수 있도록 하려면 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> 또는 서브클래스를 이벤트 인수로 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-131">Use <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType> or its subclass as the event argument to allow the end user to cancel events.</span></span>

### <a name="custom-event-handler-design"></a><span data-ttu-id="5052f-132">사용자 지정 이벤트 처리기 디자인</span><span class="sxs-lookup"><span data-stu-id="5052f-132">Custom Event Handler Design</span></span>

 <span data-ttu-id="5052f-133">제네릭을 지원하지 않는 이전 버전의 CLR에서 프레임워크를 사용해야 하는 경우처럼 `EventHandler<T>`를 사용할 수 없는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-133">There are cases in which `EventHandler<T>` cannot be used, such as when the framework needs to work with earlier versions of the CLR, which did not support Generics.</span></span> <span data-ttu-id="5052f-134">이런 경우 사용자 지정 이벤트 처리기 대리자를 디자인하고 개발해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-134">In such cases, you might need to design and develop a custom event handler delegate.</span></span>

 <span data-ttu-id="5052f-135">✔️ 이벤트 처리기에 void의 반환 형식을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-135">✔️ DO use a return type of void for event handlers.</span></span>

 <span data-ttu-id="5052f-136">이벤트 처리기는 여러 개체에서 여러 이벤트 처리 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-136">An event handler can invoke multiple event handling methods, possibly on multiple objects.</span></span> <span data-ttu-id="5052f-137">이벤트 처리 메서드에서 값을 반환할 수 있는 경우 각 이벤트 호출에 대해 여러 개의 반환 값이 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5052f-137">If event handling methods were allowed to return a value, there would be multiple return values for each event invocation.</span></span>

 <span data-ttu-id="5052f-138">✔️ `object`를 이벤트 처리기의 첫 번째 매개 변수 형식으로 사용하고 `sender`라고 하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-138">✔️ DO use `object` as the type of the first parameter of the event handler, and call it `sender`.</span></span>

 <span data-ttu-id="5052f-139">✔️ <xref:System.EventArgs?displayProperty=nameWithType> 또는 서브클래스를 이벤트 처리기의 두 번째 매개 변수 형식으로 사용하고 `e`라고 하세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-139">✔️ DO use <xref:System.EventArgs?displayProperty=nameWithType> or its subclass as the type of the second parameter of the event handler, and call it `e`.</span></span>

 <span data-ttu-id="5052f-140">❌ 이벤트 처리기에서 세 개 이상의 매개 변수를 사용하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5052f-140">❌ DO NOT have more than two parameters on event handlers.</span></span>

 <span data-ttu-id="5052f-141">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="5052f-141">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5052f-142">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="5052f-142">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5052f-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="5052f-143">See also</span></span>

- [<span data-ttu-id="5052f-144">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="5052f-144">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="5052f-145">프레임워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="5052f-145">Framework Design Guidelines</span></span>](index.md)
