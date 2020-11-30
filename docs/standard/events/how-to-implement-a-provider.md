---
title: '방법: 공급자 구현'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- observer design pattern [.NET], implementing providers
- providers [.NET], in observer design pattern
- observables [.NET], in observer design pattern
ms.assetid: 790b5d8b-d546-40a6-beeb-151b574e5ee5
ms.openlocfilehash: b63666a581959f7a6c6a30ca8763f9c22067f32a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734337"
---
# <a name="how-to-implement-a-provider"></a><span data-ttu-id="bfb76-102">방법: 공급자 구현</span><span class="sxs-lookup"><span data-stu-id="bfb76-102">How to: Implement a Provider</span></span>

<span data-ttu-id="bfb76-103">관찰자 디자인 패턴은 데이터를 모니터링하고 알림을 보내는 공급자와 해당 공급자로부터 알림(콜백)을 받는 하나 이상의 관찰자 간에 구분이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-103">The observer design pattern requires a division between a provider, which monitors data and sends notifications, and one or more observers, which receive notifications (callbacks) from the provider.</span></span> <span data-ttu-id="bfb76-104">이 항목에서는 공급자를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-104">This topic discusses how to create a provider.</span></span> <span data-ttu-id="bfb76-105">관련 항목인 [방법: 관찰자 구현](how-to-implement-an-observer.md)에서는 관찰자를 만드는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-105">A related topic, [How to: Implement an Observer](how-to-implement-an-observer.md), discusses how to create an observer.</span></span>  
  
### <a name="to-create-a-provider"></a><span data-ttu-id="bfb76-106">공급자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="bfb76-106">To create a provider</span></span>  
  
1. <span data-ttu-id="bfb76-107">공급자가 관찰자에게 보내야 하는 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-107">Define the data that the provider is responsible for sending to observers.</span></span> <span data-ttu-id="bfb76-108">공급자와 이 공급자가 관찰자로 보내는 데이터가 단일 형식일 수 있지만, 일반적으로 서로 다른 형식으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-108">Although the provider and the data that it sends to observers can be a single type, they are generally represented by different types.</span></span> <span data-ttu-id="bfb76-109">예를 들어 온도 모니터링 애플리케이션에서 `Temperature` 구조체는 공급자(다음 단계에 정의된 `TemperatureMonitor` 클래스로 표시됨)가 모니터링하고 관찰자가 구독하는 데이터를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-109">For example, in a temperature monitoring application, the `Temperature` structure defines the data that the provider (which is represented by the `TemperatureMonitor` class defined in the next step) monitors and to which observers subscribe.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/data.cs#1)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/data.vb#1)]  
  
2. <span data-ttu-id="bfb76-110"><xref:System.IObservable%601?displayProperty=nameWithType> 인터페이스를 구현하는 형식인 데이터 공급자를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-110">Define the data provider, which is a type that implements the <xref:System.IObservable%601?displayProperty=nameWithType> interface.</span></span> <span data-ttu-id="bfb76-111">공급자의 제네릭 형식 인수는 공급자가 관찰자로 보내는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-111">The provider's generic type argument is the type that the provider sends to observers.</span></span> <span data-ttu-id="bfb76-112">다음 예제에서는 `Temperature`의 제네릭 형식 인수를 사용하여 구성된 <xref:System.IObservable%601?displayProperty=nameWithType> 구현인 `TemperatureMonitor` 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-112">The following example defines a `TemperatureMonitor` class, which is a constructed <xref:System.IObservable%601?displayProperty=nameWithType> implementation with a generic type argument of `Temperature`.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#2)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#2)]  
  
3. <span data-ttu-id="bfb76-113">해당하는 경우 각 관찰자에게 알릴 수 있도록 공급자가 관찰자에 대한 참조를 저장할 방식을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-113">Determine how the provider will store references to observers so that each observer can be notified when appropriate.</span></span> <span data-ttu-id="bfb76-114">일반적으로 제네릭 <xref:System.Collections.Generic.List%601> 개체와 같은 컬렉션 개체가 이 용도로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-114">Most commonly, a collection object such as a generic <xref:System.Collections.Generic.List%601> object is used for this purpose.</span></span> <span data-ttu-id="bfb76-115">다음 예제에서는 `TemperatureMonitor` 클래스 생성자에서 인스턴스화되는 private <xref:System.Collections.Generic.List%601> 개체를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-115">The following example defines a private <xref:System.Collections.Generic.List%601> object that is instantiated in the `TemperatureMonitor` class constructor.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#3)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#3)]  
  
4. <span data-ttu-id="bfb76-116">구독자가 언제든지 알림 수신을 중지할 수 있도록 공급자가 해당 구독자에게 반환할 수 있는 <xref:System.IDisposable> 구현을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-116">Define an <xref:System.IDisposable> implementation that the provider can return to subscribers so that they can stop receiving notifications at any time.</span></span> <span data-ttu-id="bfb76-117">다음 예제에서는 클래스가 인스턴스화될 때 구독자 컬렉션 및 구독자에 대한 참조를 전달받는 중첩 `Unsubscriber` 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-117">The following example defines a nested `Unsubscriber` class that is passed a reference to the subscribers collection and to the subscriber when the class is instantiated.</span></span> <span data-ttu-id="bfb76-118">이 코드를 통해 구독자가 개체의 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 구현을 호출하여 구독자 컬렉션에서 자신을 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-118">This code enables the subscriber to call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to remove itself from the subscribers collection.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#4)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#4)]  
  
5. <span data-ttu-id="bfb76-119"><xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-119">Implement the <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bfb76-120">이 메서드는 <xref:System.IObserver%601?displayProperty=nameWithType> 인터페이스에 대한 참조를 전달받으며, 3단계에서 해당 용도로 디자인한 개체에 저장되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-120">The method is passed a reference to the <xref:System.IObserver%601?displayProperty=nameWithType> interface and should be stored in the object designed for that purpose in step 3.</span></span> <span data-ttu-id="bfb76-121">그런 다음, 이 메서드는 4단계에서 개발한 <xref:System.IDisposable> 구현을 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-121">The method should then return the <xref:System.IDisposable> implementation developed in step 4.</span></span> <span data-ttu-id="bfb76-122">다음 예제는 `TemperatureMonitor` 클래스의 <xref:System.IObservable%601.Subscribe%2A> 메서드 구현을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-122">The following example shows the implementation of the <xref:System.IObservable%601.Subscribe%2A> method in the `TemperatureMonitor` class.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#5)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#5)]  
  
6. <span data-ttu-id="bfb76-123">해당 <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType> 및 <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> 구현을 호출하여 적절하게 관찰자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-123">Notify observers as appropriate by calling their <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, and <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> implementations.</span></span> <span data-ttu-id="bfb76-124">일부 경우에 오류가 발생하면 공급자가 <xref:System.IObserver%601.OnError%2A> 메서드를 호출하지 못할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-124">In some cases, a provider may not call the <xref:System.IObserver%601.OnError%2A> method when an error occurs.</span></span> <span data-ttu-id="bfb76-125">예를 들어 다음 `GetTemperature` 메서드는 5초마다 온도 데이터를 읽는 모니터를 시뮬레이트하고 온도가 이전 값보다 .1도 이상 변경된 경우 관찰자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-125">For example, the following `GetTemperature` method simulates a monitor that reads temperature data every five seconds and notifies observers if the temperature has changed by at least .1 degree since the previous reading.</span></span> <span data-ttu-id="bfb76-126">디바이스에서 온도를 보고하지 않으면(즉, 값이 null인 경우) 공급자는 전송이 완료되었음을 관찰자에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-126">If the device does not report a temperature (that is, if its value is null), the provider notifies observers that the transmission is complete.</span></span> <span data-ttu-id="bfb76-127">각 관찰자의 <xref:System.IObserver%601.OnCompleted%2A> 메서드를 호출할 뿐만 아니라 `GetTemperature` 메서드는 <xref:System.Collections.Generic.List%601> 컬렉션을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-127">Note that, in addition to calling each observer's <xref:System.IObserver%601.OnCompleted%2A> method, the `GetTemperature` method clears the <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="bfb76-128">이 경우 공급자는 해당 관찰자의 <xref:System.IObserver%601.OnError%2A> 메서드를 호출하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-128">In this case, the provider makes no calls to the <xref:System.IObserver%601.OnError%2A> method of its observers.</span></span>  
  
     [!code-csharp[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#6)]
     [!code-vb[Conceptual.ObserverDesign.HowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="bfb76-129">예제</span><span class="sxs-lookup"><span data-stu-id="bfb76-129">Example</span></span>  

 <span data-ttu-id="bfb76-130">다음 예제에는 온도 모니터링 애플리케이션에 대한 <xref:System.IObservable%601> 구현을 정의하기 위한 전체 소스 코드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-130">The following example contains the complete source code for defining an <xref:System.IObservable%601> implementation for a temperature monitoring application.</span></span> <span data-ttu-id="bfb76-131">여기에는 관찰자로 전송된 데이터인 `Temperature` 구조체 및 <xref:System.IObservable%601> 구현인 `TemperatureMonitor` 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bfb76-131">It includes the `Temperature` structure, which is the data sent to observers, and the `TemperatureMonitor` class, which is the <xref:System.IObservable%601> implementation.</span></span>  
  
 [!code-csharp[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesign.howto/cs/provider.cs#7)]
 [!code-vb[Conceptual.ObserverDesign.HowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesign.howto/vb/provider.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="bfb76-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bfb76-132">See also</span></span>

- <xref:System.IObservable%601>
- [<span data-ttu-id="bfb76-133">관찰자 디자인 패턴</span><span class="sxs-lookup"><span data-stu-id="bfb76-133">Observer Design Pattern</span></span>](observer-design-pattern.md)
- [<span data-ttu-id="bfb76-134">방법: 관찰자 구현</span><span class="sxs-lookup"><span data-stu-id="bfb76-134">How to: Implement an Observer</span></span>](how-to-implement-an-observer.md)
- [<span data-ttu-id="bfb76-135">관찰자 디자인 패턴 유용한 정보</span><span class="sxs-lookup"><span data-stu-id="bfb76-135">Observer Design Pattern Best Practices</span></span>](observer-design-pattern-best-practices.md)
