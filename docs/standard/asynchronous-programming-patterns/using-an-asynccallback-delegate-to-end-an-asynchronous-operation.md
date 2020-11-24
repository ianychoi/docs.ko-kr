---
title: AsyncCallback 대리자를 사용하여 비동기 작업 종료
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ending asynchronous operations
- asynchronous programming, ending operations
- AsyncCallback delegate
- stopping asynchronous operations
ms.assetid: 9d97206c-8917-406c-8961-7d0909d84eeb
ms.openlocfilehash: 55cc78bbfdda97a4d5ec8a2028fb3b0d7a9659e5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829130"
---
# <a name="using-an-asynccallback-delegate-to-end-an-asynchronous-operation"></a><span data-ttu-id="c1fb8-102">AsyncCallback 대리자를 사용하여 비동기 작업 종료</span><span class="sxs-lookup"><span data-stu-id="c1fb8-102">Using an AsyncCallback Delegate to End an Asynchronous Operation</span></span>
<span data-ttu-id="c1fb8-103">비동기 작업의 결과를 기다리는 동안 다른 작업을 수행할 수 있는 애플리케이션은 작업이 완료될 때까지 차단되면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-103">Applications that can do other work while waiting for the results of an asynchronous operation should not block waiting until the operation completes.</span></span> <span data-ttu-id="c1fb8-104">다음 옵션 중 하나를 사용하여 비동기 작업이 완료될 때까지 대기하는 동안 명령을 계속 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-104">Use one of the following options to continue executing instructions while waiting for an asynchronous operation to complete:</span></span>  
  
- <span data-ttu-id="c1fb8-105"><xref:System.AsyncCallback> 대리자를 사용하여 비동기 작업 결과를 별도의 스레드에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-105">Use an <xref:System.AsyncCallback> delegate to process the results of the asynchronous operation in a separate thread.</span></span> <span data-ttu-id="c1fb8-106">이 항목에서 이 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-106">This approach is demonstrated in this topic.</span></span>  
  
- <span data-ttu-id="c1fb8-107">비동기 작업의 **Begin**_OperationName_ 메서드에서 반환된 <xref:System.IAsyncResult>의 <xref:System.IAsyncResult.IsCompleted%2A> 속성을 사용하여 작업이 완료되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-107">Use the <xref:System.IAsyncResult.IsCompleted%2A> property of the <xref:System.IAsyncResult> returned by the asynchronous operation's **Begin**_OperationName_ method to determine whether the operation has completed.</span></span> <span data-ttu-id="c1fb8-108">이 방법을 설명하는 예제는 [비동기 작업의 상태에 대한 폴링](polling-for-the-status-of-an-asynchronous-operation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-108">For an example that demonstrates this approach, see [Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1fb8-109">예제</span><span class="sxs-lookup"><span data-stu-id="c1fb8-109">Example</span></span>  
 <span data-ttu-id="c1fb8-110">다음 코드 예제는 <xref:System.Net.Dns> 클래스에서 비동기 메서드를 사용하여 사용자가 지정한 컴퓨터의 DNS(Domain Name System) 정보를 검색하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-110">The following code example demonstrates using asynchronous methods in the <xref:System.Net.Dns> class to retrieve Domain Name System (DNS) information for user-specified computers.</span></span> <span data-ttu-id="c1fb8-111">이 예제에서는 `ProcessDnsInformation` 메서드를 참조하는 <xref:System.AsyncCallback> 대리자를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-111">This example creates an <xref:System.AsyncCallback> delegate that references the `ProcessDnsInformation` method.</span></span> <span data-ttu-id="c1fb8-112">이 메서드는 DNS 정보에 대한 각 비동기 요청에 대해 한 번 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-112">This method is called once for each asynchronous request for DNS information.</span></span>  
  
 <span data-ttu-id="c1fb8-113">사용자 지정 호스트는 <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> 매개 변수에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-113">Note that the user-specified host is passed to the <xref:System.Net.Dns.BeginGetHostByName%2A><xref:System.Object> parameter.</span></span> <span data-ttu-id="c1fb8-114">보다 복잡한 상태 개체를 정의하고 사용하는 방법을 보여주는 예제는 [AsyncCallback 대리자 및 상태 개체 사용](using-an-asynccallback-delegate-and-state-object.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1fb8-114">For an example that demonstrates defining and using a more complex state object, see [Using an AsyncCallback Delegate and State Object](using-an-asynccallback-delegate-and-state-object.md).</span></span>  
  
 [!code-csharp[AsyncDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AsyncDesignPattern/CS/AsyncDelegateNoStateObject.cs#4)]
 [!code-vb[AsyncDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AsyncDesignPattern/VB/AsyncDelegateNoState.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="c1fb8-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c1fb8-115">See also</span></span>

- [<span data-ttu-id="c1fb8-116">이벤트 기반 비동기 패턴(EAP)</span><span class="sxs-lookup"><span data-stu-id="c1fb8-116">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="c1fb8-117">이벤트 기반 비동기 패턴 개요</span><span class="sxs-lookup"><span data-stu-id="c1fb8-117">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="c1fb8-118">IAsyncResult를 사용하는 비동기 메서드 호출</span><span class="sxs-lookup"><span data-stu-id="c1fb8-118">Calling Asynchronous Methods Using IAsyncResult</span></span>](calling-asynchronous-methods-using-iasyncresult.md)
- [<span data-ttu-id="c1fb8-119">AsyncCallback 대리자 및 상태 개체 사용</span><span class="sxs-lookup"><span data-stu-id="c1fb8-119">Using an AsyncCallback Delegate and State Object</span></span>](using-an-asynccallback-delegate-and-state-object.md)
