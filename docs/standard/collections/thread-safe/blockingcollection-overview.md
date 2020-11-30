---
title: BlockingCollection 개요
description: .NET의 스레드로부터 안전한 컬렉션 클래스인 BlockingCollection<T>에 대해 알아봅니다. 이 클래스는 동시에 항목을 추가하고 여러 스레드에서 가져오기 등의 기능을 제공합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BlockingCollection, overview
ms.assetid: 987ea3d7-0ad5-4238-8b64-331ce4eb3f0b
ms.openlocfilehash: 550649ae8d5527b96e3a44edf44731c9c0586150
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733505"
---
# <a name="blockingcollection-overview"></a><span data-ttu-id="14d7a-104">BlockingCollection 개요</span><span class="sxs-lookup"><span data-stu-id="14d7a-104">BlockingCollection Overview</span></span>

<span data-ttu-id="14d7a-105"><xref:System.Collections.Concurrent.BlockingCollection%601>는 스레드로부터 안전한 컬렉션 클래스이며 제공하는 기능은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-105"><xref:System.Collections.Concurrent.BlockingCollection%601> is a thread-safe collection class that provides the following features:</span></span>  
  
- <span data-ttu-id="14d7a-106">공급자-소비자 패턴 구현</span><span class="sxs-lookup"><span data-stu-id="14d7a-106">An implementation of the Producer-Consumer pattern.</span></span>  
  
- <span data-ttu-id="14d7a-107">여러 스레드에서 동시에 항목 추가 및 가져오기</span><span class="sxs-lookup"><span data-stu-id="14d7a-107">Concurrent adding and taking of items from multiple threads.</span></span>  
  
- <span data-ttu-id="14d7a-108">선택적 최대 용량</span><span class="sxs-lookup"><span data-stu-id="14d7a-108">Optional maximum capacity.</span></span>  
  
- <span data-ttu-id="14d7a-109">컬렉션이 비어 있거나 가득 찬 경우 차단할 작업 삽입 및 제거</span><span class="sxs-lookup"><span data-stu-id="14d7a-109">Insertion and removal operations that block when collection is empty or full.</span></span>  
  
- <span data-ttu-id="14d7a-110">지정된 시간까지 차단하지 않거나 차단할 “시도” 작업 삽입 및 제거</span><span class="sxs-lookup"><span data-stu-id="14d7a-110">Insertion and removal "try" operations that do not block or that block up to a specified period of time.</span></span>  
  
- <span data-ttu-id="14d7a-111"><xref:System.Collections.Concurrent.IProducerConsumerCollection%601>를 구현하는 모든 컬렉션 형식의 캡슐화</span><span class="sxs-lookup"><span data-stu-id="14d7a-111">Encapsulates any collection type that implements <xref:System.Collections.Concurrent.IProducerConsumerCollection%601></span></span>  
  
- <span data-ttu-id="14d7a-112">취소 토큰으로 취소</span><span class="sxs-lookup"><span data-stu-id="14d7a-112">Cancellation with cancellation tokens.</span></span>  
  
- <span data-ttu-id="14d7a-113">`foreach`(Visual Basic의 `For Each`)를 사용하는 다음 두 가지 유형의 열거</span><span class="sxs-lookup"><span data-stu-id="14d7a-113">Two kinds of enumeration with `foreach` (`For Each` in Visual Basic):</span></span>  
  
    1. <span data-ttu-id="14d7a-114">읽기 전용 열거</span><span class="sxs-lookup"><span data-stu-id="14d7a-114">Read-only enumeration.</span></span>  
  
    2. <span data-ttu-id="14d7a-115">열거된 항목을 제거하는 열거</span><span class="sxs-lookup"><span data-stu-id="14d7a-115">Enumeration that removes items as they are enumerated.</span></span>  
  
## <a name="bounding-and-blocking-support"></a><span data-ttu-id="14d7a-116">한계 지정 및 차단 지원</span><span class="sxs-lookup"><span data-stu-id="14d7a-116">Bounding and Blocking Support</span></span>  

 <span data-ttu-id="14d7a-117"><xref:System.Collections.Concurrent.BlockingCollection%601>는 한계 지정 및 차단을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-117"><xref:System.Collections.Concurrent.BlockingCollection%601> supports bounding and blocking.</span></span> <span data-ttu-id="14d7a-118">한계 지정이란 컬렉션의 최대 용량을 설정하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-118">Bounding means you can set the maximum capacity of the collection.</span></span> <span data-ttu-id="14d7a-119">메모리에서 컬렉션의 최대 크기를 제어할 수 있고 공급자 스레드가 소비자 스레드와 보조를 맞춰 실행되도록 할 수 있기 때문에 특정 시나리오에서 한계 지정은 중요한 의미를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-119">Bounding is important in certain scenarios because it enables you to control the maximum size of the collection in memory, and it prevents the producing threads from moving too far ahead of the consuming threads.</span></span>  
  
 <span data-ttu-id="14d7a-120">다중 스레드 또는 작업은 동시에 항목을 컬렉션에 추가할 수 있습니다. 컬렉션이 지정된 최대 용량에 도달하는 경우 항목 하나를 제거할 때까지 공급자 스레드를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-120">Multiple threads or tasks can add items to the collection concurrently, and if the collection reaches its specified maximum capacity, the producing threads will block until an item is removed.</span></span> <span data-ttu-id="14d7a-121">여러 소비자에서 항목을 동시에 제거할 수 있습니다. 컬렉션이 비어 있는 경우 공급자가 항목 하나를 추가할 때까지 소비자 스레드를 차단합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-121">Multiple consumers can remove items concurrently, and if the collection becomes empty, the consuming threads will block until a producer adds an item.</span></span> <span data-ttu-id="14d7a-122">공급자 스레드는 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>을 호출하여 더 이상 추가할 항목이 없음을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-122">A producing thread can call <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A> to indicate that no more items will be added.</span></span> <span data-ttu-id="14d7a-123">소비자 스레드는 컬렉션이 비어 있고 항목이 더 이상 추가되지 않는 시점을 파악하기 위해 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 속성을 모니터링합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-123">Consumers monitor the <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> property to know when the collection is empty and no more items will be added.</span></span> <span data-ttu-id="14d7a-124">다음 예제에서는 한계 용량이 100인 간단한 simple BlockingCollection을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-124">The following example shows a simple BlockingCollection with a bounded capacity of 100.</span></span> <span data-ttu-id="14d7a-125">공급자 작업에서는 일부 외부 조건이 true이면 항목을 컬렉션에 추가한 다음 <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-125">A producer task adds items to the collection as long as some external condition is true, and then calls <xref:System.Collections.Concurrent.BlockingCollection%601.CompleteAdding%2A>.</span></span> <span data-ttu-id="14d7a-126">소비자 작업에서는 <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> 속성이 true일 때까지 항목을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-126">The consumer task takes items until the <xref:System.Collections.Concurrent.BlockingCollection%601.IsCompleted%2A> property is true.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#04](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#04)]
 [!code-vb[CDS_BlockingCollection#04](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#04)]  
  
 <span data-ttu-id="14d7a-127">전체 예제는 [방법: BlockingCollection에서 개별적으로 항목 추가 및 가져오기](how-to-add-and-take-items.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-127">For a complete example, see [How to: Add and Take Items Individually from a BlockingCollection](how-to-add-and-take-items.md).</span></span>  
  
## <a name="timed-blocking-operations"></a><span data-ttu-id="14d7a-128">시간 지정된 차단 작업</span><span class="sxs-lookup"><span data-stu-id="14d7a-128">Timed Blocking Operations</span></span>  

 <span data-ttu-id="14d7a-129">한계 지정된 컬렉션의 시간 지정된 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 및 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 차단 작업에서 메서드는 항목을 추가하거나 가져오려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-129">In timed blocking <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> operations on bounded collections, the method tries to add or take an item.</span></span> <span data-ttu-id="14d7a-130">사용 가능한 항목이 있으면 이 항목은 참조로 전달된 변수에 저장되고 메서드에서 true를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-130">If an item is available it is placed into the variable that was passed in by reference, and the method returns true.</span></span> <span data-ttu-id="14d7a-131">지정된 제한 시간이 경과한 후에 검색되는 항목이 없으면 메서드에서 false를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-131">If no item is retrieved after a specified time-out period the method returns false.</span></span> <span data-ttu-id="14d7a-132">그러면 스레드에서 유용한 다른 작업을 수행한 후에 컬렉션에 대한 액세스를 다시 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-132">The thread is then free to do some other useful work before trying again to access the collection.</span></span> <span data-ttu-id="14d7a-133">시간 제한 차단 액세스의 예제는 [방법: BlockingCollection에서 개별적으로 항목 추가 및 가져오기](how-to-add-and-take-items.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-133">For an example of timed blocking access, see the second example in [How to: Add and Take Items Individually from a BlockingCollection](how-to-add-and-take-items.md).</span></span>  
  
## <a name="cancelling-add-and-take-operations"></a><span data-ttu-id="14d7a-134">추가 및 가져오기 작업 취소</span><span class="sxs-lookup"><span data-stu-id="14d7a-134">Cancelling Add and Take Operations</span></span>  

 <span data-ttu-id="14d7a-135">추가 및 가져오기 작업은 일반적으로 루프에서 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-135">Add and Take operations are typically performed in a loop.</span></span> <span data-ttu-id="14d7a-136"><xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> 또는 <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> 메서드에 <xref:System.Threading.CancellationToken>을 전달한 다음, 각 반복마다 이 토큰의 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 속성 값을 확인하여 루프를 취소할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-136">You can cancel a loop by passing in a <xref:System.Threading.CancellationToken> to the <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> or <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, and then checking the value of the token's <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property on each iteration.</span></span> <span data-ttu-id="14d7a-137">이 속성 값이 true이면 사용자가 모든 리소스를 정리하고 루프를 종료하여 취소 요청에 응답해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-137">If the value is true, then it is up to you to respond the cancellation request by cleaning up any resources and exiting the loop.</span></span> <span data-ttu-id="14d7a-138">다음 예제에서는 취소 토큰을 사용하는 <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A>의 오버로드 및 이 오버로드를 사용하는 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-138">The following example shows an overload of <xref:System.Collections.Concurrent.BlockingCollection%601.TryAdd%2A> that takes a cancellation token, and the code that uses it:</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#05](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/blockingcollection.cs#05)]
 [!code-vb[CDS_BlockingCollection#05](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/introsnippetsbc.vb#05)]  
  
 <span data-ttu-id="14d7a-139">취소 지원을 추가하는 방법에 대한 예제는 [방법: BlockingCollection에서 개별적으로 항목 추가 및 가져오기](how-to-add-and-take-items.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-139">For an example of how to add cancellation support, see the second example in [How to: Add and Take Items Individually from a BlockingCollection](how-to-add-and-take-items.md).</span></span>  
  
## <a name="specifying-the-collection-type"></a><span data-ttu-id="14d7a-140">컬렉션 형식 지정</span><span class="sxs-lookup"><span data-stu-id="14d7a-140">Specifying the Collection Type</span></span>  

 <span data-ttu-id="14d7a-141"><xref:System.Collections.Concurrent.BlockingCollection%601>를 만들 때는 한계 지정되는 용량뿐 아니라 사용할 컬렉션의 형식도 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-141">When you create a <xref:System.Collections.Concurrent.BlockingCollection%601>, you can specify not only the bounded capacity but also the type of collection to use.</span></span> <span data-ttu-id="14d7a-142">예를 들어 FIFO(선입 선출) 동작에 <xref:System.Collections.Concurrent.ConcurrentQueue%601>를 지정하거나 LIFO(후입 선출) 동작에 <xref:System.Collections.Concurrent.ConcurrentStack%601>를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-142">For example, you could specify a <xref:System.Collections.Concurrent.ConcurrentQueue%601> for first in-first out (FIFO) behavior, or a <xref:System.Collections.Concurrent.ConcurrentStack%601> for last in-first out (LIFO) behavior.</span></span> <span data-ttu-id="14d7a-143"><xref:System.Collections.Concurrent.IProducerConsumerCollection%601> 인터페이스를 구현하는 컬렉션 클래스를 모두 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-143">You can use any collection class that implements the <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> interface.</span></span> <span data-ttu-id="14d7a-144"><xref:System.Collections.Concurrent.BlockingCollection%601>의 기본 컬렉션 형식은 <xref:System.Collections.Concurrent.ConcurrentQueue%601>입니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-144">The default collection type for <xref:System.Collections.Concurrent.BlockingCollection%601> is <xref:System.Collections.Concurrent.ConcurrentQueue%601>.</span></span> <span data-ttu-id="14d7a-145">다음 코드 예제에서는 용량이 1000이고 <xref:System.Collections.Concurrent.BlockingCollection%601>를 사용하는 <xref:System.Collections.Concurrent.ConcurrentBag%601> 문자열을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-145">The following code example shows how to create a <xref:System.Collections.Concurrent.BlockingCollection%601> of strings that has a capacity of 1000 and uses a <xref:System.Collections.Concurrent.ConcurrentBag%601>:</span></span>  
  
```vb  
Dim bc = New BlockingCollection(Of String)(New ConcurrentBag(Of String()), 1000)  
```  
  
```csharp  
BlockingCollection<string> bc = new BlockingCollection<string>(new ConcurrentBag<string>(), 1000 );  
```  
  
 <span data-ttu-id="14d7a-146">자세한 내용은 [방법: 컬렉션에 한계 지정 및 차단 기능 추가](how-to-add-bounding-and-blocking.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-146">For more information, see [How to: Add Bounding and Blocking Functionality to a Collection](how-to-add-bounding-and-blocking.md).</span></span>  
  
## <a name="ienumerable-support"></a><span data-ttu-id="14d7a-147">IEnumerable 지원</span><span class="sxs-lookup"><span data-stu-id="14d7a-147">IEnumerable Support</span></span>  

 <span data-ttu-id="14d7a-148"><xref:System.Collections.Concurrent.BlockingCollection%601>에서는 컬렉션이 완료될 때까지, 즉 컬렉션이 비어 있고 항목이 더 이상 추가되지 않을 때까지 소비자가 `foreach`(Visual Basic의 `For Each`)를 사용하여 항목을 제거할 수 있도록 하는 <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-148"><xref:System.Collections.Concurrent.BlockingCollection%601> provides a <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method that enables consumers to use `foreach` (`For Each` in Visual Basic) to remove items until the collection is completed, which means it is empty and no more items will be added.</span></span> <span data-ttu-id="14d7a-149">자세한 내용은 [방법: ForEach를 사용하여 BlockingCollection의 항목 제거](how-to-use-foreach-to-remove.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-149">For more information, see [How to: Use ForEach to Remove Items in a BlockingCollection](how-to-use-foreach-to-remove.md).</span></span>  
  
## <a name="using-many-blockingcollections-as-one"></a><span data-ttu-id="14d7a-150">여러 BlockingCollection을 하나로 사용</span><span class="sxs-lookup"><span data-stu-id="14d7a-150">Using Many BlockingCollections As One</span></span>  

 <span data-ttu-id="14d7a-151">소비자에서 여러 컬렉션의 항목을 동시에 가져와야 하는 시나리오의 경우 <xref:System.Collections.Concurrent.BlockingCollection%601> 배열을 만들고, 배열 내의 컬렉션에 항목을 추가하거나 이 컬렉션으로부터 항목을 가져올 <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> 및 <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A>와 같은 정적 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-151">For scenarios in which a consumer needs to take items from multiple collections simultaneously, you can create arrays of <xref:System.Collections.Concurrent.BlockingCollection%601> and use the static methods such as <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.AddToAny%2A> that will add to or take from any of the collections in the array.</span></span> <span data-ttu-id="14d7a-152">특정 컬렉션이 차단되는 즉시 메서드에서 작업을 수행할 수 있는 컬렉션을 찾을 때까지 다른 컬렉션에 대한 액세스를 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="14d7a-152">If one collection is blocking, the method immediately tries another until it finds one that can perform the operation.</span></span> <span data-ttu-id="14d7a-153">자세한 내용은 [방법: 파이프라인에서 차단 컬렉션 배열 사용](how-to-use-arrays-of-blockingcollections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="14d7a-153">For more information, see [How to: Use Arrays of Blocking Collections in a Pipeline](how-to-use-arrays-of-blockingcollections.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14d7a-154">참조</span><span class="sxs-lookup"><span data-stu-id="14d7a-154">See also</span></span>

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [<span data-ttu-id="14d7a-155">컬렉션 및 데이터 구조</span><span class="sxs-lookup"><span data-stu-id="14d7a-155">Collections and Data Structures</span></span>](../index.md)
- [<span data-ttu-id="14d7a-156">스레드로부터 안전한 컬렉션</span><span class="sxs-lookup"><span data-stu-id="14d7a-156">Thread-Safe Collections</span></span>](index.md)
