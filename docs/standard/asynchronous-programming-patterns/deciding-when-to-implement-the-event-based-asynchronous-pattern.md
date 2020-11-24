---
title: 이벤트 기반 비동기 패턴 구현 시기 결정
ms.date: 03/30/2017
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- AsyncOperationManager class
- threading [.NET], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: 096b3e9e5732989ff5e85a5b6df4ca413e29cbcd
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830417"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a><span data-ttu-id="3b8f5-102">이벤트 기반 비동기 패턴 구현 시기 결정</span><span class="sxs-lookup"><span data-stu-id="3b8f5-102">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>

<span data-ttu-id="3b8f5-103">이벤트 기반 비동기 패턴은 클래스의 비동기 동작을 표시하기 위한 패턴을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-103">The Event-based Asynchronous Pattern provides a pattern for exposing the asynchronous behavior of a class.</span></span> <span data-ttu-id="3b8f5-104">이 패턴의 도입에 따라 .NET은 비동기 동작을 표시하기 위한 두 가지 패턴 즉, <xref:System.IAsyncResult?displayProperty=nameWithType> 인터페이스를 기반으로 하는 비동기 패턴 및 이벤트 기반 패턴을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-104">With the introduction of this pattern, .NET defines two patterns for exposing asynchronous behavior: the Asynchronous Pattern based on the <xref:System.IAsyncResult?displayProperty=nameWithType> interface, and the event-based pattern.</span></span> <span data-ttu-id="3b8f5-105">이 문서에서는 두 패턴을 모두 구현하는 것이 적절한 경우에 관해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-105">This article describes when it's appropriate for you to implement both patterns.</span></span>

<span data-ttu-id="3b8f5-106"><xref:System.IAsyncResult> 인터페이스를 사용한 비동기 프로그래밍에 대한 자세한 내용은 [APM(비동기 프로그래밍 모델)](asynchronous-programming-model-apm.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-106">For more information about asynchronous programming with the <xref:System.IAsyncResult> interface, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>

## <a name="general-principles"></a><span data-ttu-id="3b8f5-107">일반 원칙</span><span class="sxs-lookup"><span data-stu-id="3b8f5-107">General Principles</span></span>

<span data-ttu-id="3b8f5-108">일반적으로 가능한 경우 언제든 이벤트 기반 비동기 패턴을 사용하여 비동기 기능을 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-108">In general, you should expose asynchronous features using the Event-based Asynchronous Pattern whenever possible.</span></span> <span data-ttu-id="3b8f5-109">그러나 이벤트 기반 패턴이 충족할 수 없는 몇 가지 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-109">However, there are some requirements that the event-based pattern cannot meet.</span></span> <span data-ttu-id="3b8f5-110">이러한 경우 이벤트 기반 패턴 외에도 <xref:System.IAsyncResult> 패턴을 구현해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-110">In those cases, you may need to implement the <xref:System.IAsyncResult> pattern in addition to the event-based pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="3b8f5-111">이벤트 기반 패턴을 구현하지 않고 <xref:System.IAsyncResult> 패턴을 구현하는 경우는 거의 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-111">It is rare for the <xref:System.IAsyncResult> pattern to be implemented without the event-based pattern also being implemented.</span></span>

## <a name="guidelines"></a><span data-ttu-id="3b8f5-112">지침</span><span class="sxs-lookup"><span data-stu-id="3b8f5-112">Guidelines</span></span>

<span data-ttu-id="3b8f5-113">다음 목록은 이벤트 기반 비동기 패턴을 구현해야 하는 경우에 대한 지침을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-113">The following list describes the guidelines for when you should implement Event-based Asynchronous Pattern:</span></span>

- <span data-ttu-id="3b8f5-114">이벤트 기반 패턴을 기본 API로 사용하여 클래스의 비동기 동작을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-114">Use the event-based pattern as the default API to expose asynchronous behavior for your class.</span></span>

- <span data-ttu-id="3b8f5-115">클래스가 Windows Forms와 같은 클라이언트 애플리케이션에서 주로 사용되는 경우 <xref:System.IAsyncResult> 패턴을 표시하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-115">Do not expose the <xref:System.IAsyncResult> pattern when your class is primarily used in a client application, for example Windows Forms.</span></span>

- <span data-ttu-id="3b8f5-116">요구 사항을 충족하는 데 필요한 경우에만 <xref:System.IAsyncResult> 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-116">Only expose the <xref:System.IAsyncResult> pattern when it is necessary for meeting your requirements.</span></span> <span data-ttu-id="3b8f5-117">예를 들어 기존 API와의 호환성을 위해 <xref:System.IAsyncResult> 패턴을 표시해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-117">For example, compatibility with an existing API may require you to expose the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="3b8f5-118">이벤트 기반 패턴을 표시하지 않고 <xref:System.IAsyncResult> 패턴을 표시해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-118">Do not expose the <xref:System.IAsyncResult> pattern without also exposing the event-based pattern.</span></span>

- <span data-ttu-id="3b8f5-119"><xref:System.IAsyncResult> 패턴을 표시해야 하는 경우 고급 옵션으로 그렇게 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-119">If you must expose the <xref:System.IAsyncResult> pattern, do so as an advanced option.</span></span> <span data-ttu-id="3b8f5-120">예를 들어 프록시 개체를 생성하는 경우 기본적으로 <xref:System.IAsyncResult> 패턴을 생성하는 옵션을 사용하여 이벤트 기반 패턴을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-120">For example, if you generate a proxy object, generate the event-based pattern by default, with an option to generate the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="3b8f5-121"><xref:System.IAsyncResult> 패턴 구현 시 이벤트 기반 패턴 구현을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-121">Build your event-based pattern implementation on your <xref:System.IAsyncResult> pattern implementation.</span></span>

- <span data-ttu-id="3b8f5-122">이벤트 기반 패턴과 <xref:System.IAsyncResult> 패턴이 모두 동일한 클래스에 표시되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-122">Avoid exposing both the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class.</span></span> <span data-ttu-id="3b8f5-123">“상위 수준” 클래스에 이벤트 기반 패턴을 표시하고 “하위 수준” 클래스에 <xref:System.IAsyncResult> 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-123">Expose the event-based pattern on "higher level" classes and the <xref:System.IAsyncResult> pattern on "lower level" classes.</span></span> <span data-ttu-id="3b8f5-124">예를 들어 <xref:System.Net.WebClient> 구성 요소의 이벤트 기반 패턴을 <xref:System.Web.HttpRequest> 클래스의 <xref:System.IAsyncResult> 패턴과 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-124">For example, compare the event-based pattern on the <xref:System.Net.WebClient> component with the <xref:System.IAsyncResult> pattern on the <xref:System.Web.HttpRequest> class.</span></span>

  - <span data-ttu-id="3b8f5-125">호환성을 위해 필요한 경우 이벤트 기반 패턴 및 <xref:System.IAsyncResult> 패턴을 동일한 클래스에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-125">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class when compatibility requires it.</span></span> <span data-ttu-id="3b8f5-126">예를 들어 <xref:System.IAsyncResult> 패턴을 사용하는 API를 이미 릴리스한 경우 이전 버전과의 호환성을 위해 <xref:System.IAsyncResult> 패턴을 유지해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-126">For example, if you have already released an API that uses the <xref:System.IAsyncResult> pattern, you would need to retain the <xref:System.IAsyncResult> pattern for backward compatibility.</span></span>

  - <span data-ttu-id="3b8f5-127">결과 개체 모델의 복잡성이 구현을 분리하는 이점보다 더 큰 경우 이벤트 기반 패턴 및 <xref:System.IAsyncResult> 패턴을 동일한 클래스에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-127">Expose the event-based pattern and the <xref:System.IAsyncResult> pattern on the same class if the resulting object model complexity outweighs the benefit of separating the implementations.</span></span> <span data-ttu-id="3b8f5-128">이벤트 기반 패턴 표시를 피하는 것보다 단일 클래스에 두 패턴을 모두 표시하는 것이 더 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-128">It is better to expose both patterns on a single class than to avoid exposing the event-based pattern.</span></span>

  - <span data-ttu-id="3b8f5-129">이벤트 기반 패턴과 <xref:System.IAsyncResult> 패턴을 모두 단일 클래스에 표시해야 하는 경우 <xref:System.ComponentModel.EditorBrowsableState.Advanced>로 설정된 <xref:System.ComponentModel.EditorBrowsableAttribute>를 사용하여 <xref:System.IAsyncResult> 패턴 구현을 고급 기능으로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-129">If you must expose both the event-based pattern and <xref:System.IAsyncResult> pattern on a single class, use <xref:System.ComponentModel.EditorBrowsableAttribute> set to <xref:System.ComponentModel.EditorBrowsableState.Advanced> to mark the <xref:System.IAsyncResult> pattern implementation as an advanced feature.</span></span> <span data-ttu-id="3b8f5-130">이는 Visual Studio IntelliSense와 같은 환경에서 <xref:System.IAsyncResult> 속성 및 메서드를 표시하지 않도록 설계한다는 것을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-130">This indicates to design environments, such as Visual Studio IntelliSense, not to display the <xref:System.IAsyncResult> properties and methods.</span></span> <span data-ttu-id="3b8f5-131">이러한 속성 및 메서드는 여전히 완벽하게 사용할 수 있지만, IntelliSense를 통해 작업하는 개발자는 API를 더욱 명확하게 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-131">These properties and methods are still fully usable, but the developer working through IntelliSense has a clearer view of the API.</span></span>

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a><span data-ttu-id="3b8f5-132">이벤트 기반 패턴 외에도 IAsyncResult 패턴을 표시하기 위한 조건</span><span class="sxs-lookup"><span data-stu-id="3b8f5-132">Criteria for Exposing the IAsyncResult Pattern in Addition to the Event-based Pattern</span></span>

<span data-ttu-id="3b8f5-133">이벤트 기반 비동기 패턴은 앞서 언급한 시나리오에 따른 많은 이점이 있지만, 성능이 가장 중요한 요구 사항인 경우 알고 있어야 하는 몇 가지 단점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-133">While the Event-based Asynchronous Pattern has many benefits under the previously mentioned scenarios, it does have some drawbacks, which you should be aware of if performance is your most important requirement.</span></span>

<span data-ttu-id="3b8f5-134"><xref:System.IAsyncResult> 패턴뿐만 아니라 이벤트 기반 패턴이 다루지 않는 세 가지 시나리오가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-134">There are three scenarios that the event-based pattern does not address as well as the <xref:System.IAsyncResult> pattern:</span></span>

- <span data-ttu-id="3b8f5-135">하나의 <xref:System.IAsyncResult>에서 차단 대기</span><span class="sxs-lookup"><span data-stu-id="3b8f5-135">Blocking wait on one <xref:System.IAsyncResult></span></span>

- <span data-ttu-id="3b8f5-136">여러 <xref:System.IAsyncResult> 개체에서 차단 대기</span><span class="sxs-lookup"><span data-stu-id="3b8f5-136">Blocking wait on many <xref:System.IAsyncResult> objects</span></span>

- <span data-ttu-id="3b8f5-137"><xref:System.IAsyncResult>에서 완료를 위한 폴링</span><span class="sxs-lookup"><span data-stu-id="3b8f5-137">Polling for completion on the <xref:System.IAsyncResult></span></span>

<span data-ttu-id="3b8f5-138">이벤트 기반 패턴을 사용하여 이러한 시나리오를 다룰 수 ​​있지만, 그렇게 하면 <xref:System.IAsyncResult> 패턴을 사용하는 것보다 더 복잡하고 번거롭습니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-138">You can address these scenarios by using the event-based pattern, but doing so is more cumbersome than using the <xref:System.IAsyncResult> pattern.</span></span>

<span data-ttu-id="3b8f5-139">개발자는 일반적으로 성능 요구 사항이 매우 높은 서비스에 대해 <xref:System.IAsyncResult> 패턴을 흔히 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-139">Developers often use the <xref:System.IAsyncResult> pattern for services that typically have very high performance requirements.</span></span> <span data-ttu-id="3b8f5-140">예를 들어 완료를 위한 폴링 시나리오는 고성능 서버 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-140">For example, the polling for completion scenario is a high-performance server technique.</span></span>

<span data-ttu-id="3b8f5-141">또한 이벤트 기반 패턴은 더 많은 개체 특히, <xref:System.EventArgs>를 생성하고 스레드 간에 동기화되므로 <xref:System.IAsyncResult> 패턴보다 덜 효율적입니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-141">Additionally, the event-based pattern is less efficient than the <xref:System.IAsyncResult> pattern because it creates more objects, especially <xref:System.EventArgs>, and because it synchronizes across threads.</span></span>

<span data-ttu-id="3b8f5-142">다음 목록은 <xref:System.IAsyncResult> 패턴을 사용하기로 한 경우 따라야 할 몇 가지 권장 사항을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-142">The following list shows some recommendations to follow if you decide to use the <xref:System.IAsyncResult> pattern:</span></span>

- <span data-ttu-id="3b8f5-143">특히 <xref:System.Threading.WaitHandle> 또는 <xref:System.IAsyncResult> 개체에 대한 지원이 필요한 경우에만 <xref:System.IAsyncResult> 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-143">Only expose the <xref:System.IAsyncResult> pattern when you specifically require support for <xref:System.Threading.WaitHandle> or <xref:System.IAsyncResult> objects.</span></span>

- <span data-ttu-id="3b8f5-144"><xref:System.IAsyncResult> 패턴을 사용하는 기존 API가 있는 경우에만 <xref:System.IAsyncResult> 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-144">Only expose the <xref:System.IAsyncResult> pattern when you have an existing API that uses the <xref:System.IAsyncResult> pattern.</span></span>

- <span data-ttu-id="3b8f5-145"><xref:System.IAsyncResult> 패턴을 기반으로 하는 기존 API가 있는 경우 다음 릴리스에서 이벤트 기반 패턴을 표시하는 것도 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-145">If you have an existing API based on the <xref:System.IAsyncResult> pattern, consider also exposing the event-based pattern in your next release.</span></span>

- <span data-ttu-id="3b8f5-146">확인한 고성능 요구 사항을 이벤트 기반 패턴으로 충족할 수 없지만 <xref:System.IAsyncResult> 패턴으로 충족할 수 있는 경우에만 <xref:System.IAsyncResult> 패턴을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="3b8f5-146">Only expose <xref:System.IAsyncResult> pattern if you have high performance requirements which you have verified cannot be met by the event-based pattern but can be met by the <xref:System.IAsyncResult> pattern.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b8f5-147">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3b8f5-147">See also</span></span>

- [<span data-ttu-id="3b8f5-148">방법: 이벤트 기반 비동기 패턴을 지원하는 구성 요소 구현</span><span class="sxs-lookup"><span data-stu-id="3b8f5-148">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="3b8f5-149">이벤트 기반 비동기 패턴(EAP)</span><span class="sxs-lookup"><span data-stu-id="3b8f5-149">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="3b8f5-150">이벤트 기반 비동기 패턴 구현</span><span class="sxs-lookup"><span data-stu-id="3b8f5-150">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="3b8f5-151">최선의 이벤트 기반 비동기 패턴 구현 방법</span><span class="sxs-lookup"><span data-stu-id="3b8f5-151">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="3b8f5-152">이벤트 기반 비동기 패턴 개요</span><span class="sxs-lookup"><span data-stu-id="3b8f5-152">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
