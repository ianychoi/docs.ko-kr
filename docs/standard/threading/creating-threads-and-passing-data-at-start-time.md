---
title: 스레드 만들기 및 시작할 때 데이터 전달
description: .NET에서 스레드를 만들고 운영 체제 프로세스 시작 시간에 데이터를 전달하는 방법을 이해합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET], creating
- threading [.NET], passing data to threads
- threading [.NET], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: 3f44eb9dabc9145cd0e6ec9bfd3d484c9079e803
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819931"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="2b89d-103">스레드 만들기 및 시작할 때 데이터 전달</span><span class="sxs-lookup"><span data-stu-id="2b89d-103">Creating threads and passing data at start time</span></span>

<span data-ttu-id="2b89d-104">운영 체제 프로세스가 작성될 때 운영 체제에서는 원래 애플리케이션 도메인을 포함하여 이 프로세스에서 코드를 실행하는 스레드를 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-104">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="2b89d-105">이 시점부터, 운영 체제 스레드를 꼭 만들거나 삭제하지 않고도 애플리케이션 도메인을 만들거나 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-105">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="2b89d-106">실행되는 코드가 관리 코드인 경우 현재 애플리케이션 도메인에서 실행 중인 스레드에 대한 <xref:System.Threading.Thread> 개체는 <xref:System.Threading.Thread> 형식의 정적 <xref:System.Threading.Thread.CurrentThread%2A> 속성을 검색하여 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-106">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="2b89d-107">이 항목에서는 스레드 만들기를 설명하고 스레드 프로시저에 데이터를 전달하기 위한 대체 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-107">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="2b89d-108">스레드 만들기</span><span class="sxs-lookup"><span data-stu-id="2b89d-108">Creating a thread</span></span>

 <span data-ttu-id="2b89d-109">새 <xref:System.Threading.Thread> 개체를 만들면 새 관리되는 스레드가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-109">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="2b89d-110"><xref:System.Threading.Thread> 클래스에는 <xref:System.Threading.ThreadStart> 대리자 또는 <xref:System.Threading.ParameterizedThreadStart> 대리자를 사용하는 생성자가 있습니다. 대리자는 <xref:System.Threading.Thread.Start%2A> 메서드가 호출될 때 새 스레드가 호출하는 메서드를 래핑합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-110">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="2b89d-111"><xref:System.Threading.Thread.Start%2A>를 두 번 이상 호출하면 <xref:System.Threading.ThreadStateException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-111">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="2b89d-112"><xref:System.Threading.Thread.Start%2A> 메서드는 종종 새 스레드가 실제로 시작되기 전에 즉시 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-112">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="2b89d-113"><xref:System.Threading.Thread.ThreadState%2A> 및 <xref:System.Threading.Thread.IsAlive%2A> 속성을 사용하여 특정 순간의 스레드 상태를 확인할 수 있지만 이러한 속성은 스레드의 활동을 동기화하는 데 사용되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-113">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2b89d-114">스레드가 시작되면 <xref:System.Threading.Thread> 개체에 대한 참조를 유지할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-114">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="2b89d-115">스레드 프로시저가 종료될 때까지 스레드가 계속 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-115">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="2b89d-116">다음 코드 예제에서는 또 다른 개체에서 인스턴스 및 정적 메서드를 호출하는 두 개의 새 스레드를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-116">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="2b89d-117">스레드에 데이터 전달</span><span class="sxs-lookup"><span data-stu-id="2b89d-117">Passing data to threads</span></span>

<span data-ttu-id="2b89d-118"><xref:System.Threading.ParameterizedThreadStart> 대리자는 <xref:System.Threading.Thread.Start(System.Object)?displayProperty=nameWithType>를 호출할 때 데이터를 포함하는 개체를 스레드에 전달하는 간편한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-118">The <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call <xref:System.Threading.Thread.Start(System.Object)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2b89d-119">코드 예는 <xref:System.Threading.ParameterizedThreadStart>를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="2b89d-119">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>
  
 <span data-ttu-id="2b89d-120"><xref:System.Threading.Thread.Start(System.Object)?displayProperty=nameWithType> 메서드가 모든 개체를 허용하므로 <xref:System.Threading.ParameterizedThreadStart> 대리자 사용은 형식이 안전한 데이터 전달 방법이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-120">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start(System.Object)?displayProperty=nameWithType> method accepts any object.</span></span> <span data-ttu-id="2b89d-121">대체 방법은 도우미 클래스로 스레드 프로시저 및 데이터를 캡슐화하고 <xref:System.Threading.ThreadStart> 대리자를 사용하여 스레드 프로시저를 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-121">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="2b89d-122">다음 예제에서는 이 기술을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-122">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="2b89d-123">비동기 호출에서 데이터를 반환할 위치가 없기 때문에 <xref:System.Threading.ThreadStart> 또는 <xref:System.Threading.ParameterizedThreadStart> 대리자에는 반환 값이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-123">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="2b89d-124">스레드 메서드의 결과를 검색하려면 다음 섹션에서 설명한 대로 콜백 메서드를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-124">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="2b89d-125">콜백 메서드를 사용하여 스레드에서 데이터 검색</span><span class="sxs-lookup"><span data-stu-id="2b89d-125">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="2b89d-126">다음 예제는 스레드에서 데이터를 검색하는 콜백 메서드를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-126">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="2b89d-127">데이터 및 스레드 메서드를 포함하는 클래스에 대한 생성자는 콜백 메서드를 나타내는 대리자도 허용하고, 스레드 메서드가 종료되기 전에 콜백 대리자를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2b89d-127">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2b89d-128">참조</span><span class="sxs-lookup"><span data-stu-id="2b89d-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2b89d-129">스레딩</span><span class="sxs-lookup"><span data-stu-id="2b89d-129">Threading</span></span>](index.md)
- [<span data-ttu-id="2b89d-130">스레드 및 스레딩 사용</span><span class="sxs-lookup"><span data-stu-id="2b89d-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
