---
title: 버전 3.5의 소켓 성능 향상
description: .NET Framework 버전 3.5의 System.Net.Sockets.Socket 클래스의 성능 향상에 대해 알아봅니다.
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
ms.openlocfilehash: 5bd7c97d6a6edd5f914d6fe3118b6d81b64544e0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263141"
---
# <a name="socket-performance-enhancements-in-version-35"></a><span data-ttu-id="9fd75-103">버전 3.5의 소켓 성능 향상</span><span class="sxs-lookup"><span data-stu-id="9fd75-103">Socket Performance Enhancements in Version 3.5</span></span>

<span data-ttu-id="9fd75-104"><xref:System.Net.Sockets.Socket?displayProperty=nameWithType> 클래스는 비동기 네트워크 I/O를 통해 성능을 최적화하는 애플리케이션에서 사용하기 위해 버전 3.5에서 개선되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-104">The <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class has been enhanced in Version 3.5 for use by applications that use asynchronous network I/O to achieve the highest performance.</span></span> <span data-ttu-id="9fd75-105">특수화된 고성능 소켓 애플리케이션에서 사용할 수 있는 대체 비동기 패턴을 제공하는 <xref:System.Net.Sockets.Socket> 클래스에 대한 향상된 기능 집합의 일부로 일련의 새로운 클래스가 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-105">A series of new classes have been added as part of a set of enhancements to the <xref:System.Net.Sockets.Socket> class that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span> <span data-ttu-id="9fd75-106">이러한 개선 사항은 특히 높은 성능이 필요한 네트워크 서버 애플리케이션용으로 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-106">These enhancements were specifically designed for network server applications that require high performance.</span></span> <span data-ttu-id="9fd75-107">애플리케이션은 향상된 비동기 패턴을 단독으로 사용하거나, 애플리케이션의 대상 핫 영역에서만 사용할 수 있습니다(예: 많은 양의 데이터를 수신하는 경우).</span><span class="sxs-lookup"><span data-stu-id="9fd75-107">An application can use the enhanced asynchronous pattern exclusively, or only in targeted hot areas of their application (when receiving large amounts of data, for example).</span></span>  
  
## <a name="class-enhancements"></a><span data-ttu-id="9fd75-108">클래스 개선 사항</span><span class="sxs-lookup"><span data-stu-id="9fd75-108">Class Enhancements</span></span>  

 <span data-ttu-id="9fd75-109">이러한 개선 사항의 주요 기능은 대량 비동기 소켓 I/O 중 개체의 반복 할당 및 동기화를 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-109">The main feature of these enhancements is the avoidance of the repeated allocation and synchronization of objects during high-volume asynchronous socket I/O.</span></span> <span data-ttu-id="9fd75-110">현재 비동기 소켓 I/O에 대해 <xref:System.Net.Sockets.Socket> 클래스에서 구현되는 Begin/End 디자인 패턴에서는 각 비동기 소켓 작업에 대해 <xref:System.IAsyncResult?displayProperty=nameWithType> 개체가 할당되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-110">The Begin/End design pattern currently implemented by the <xref:System.Net.Sockets.Socket> class for asynchronous socket I/O requires a <xref:System.IAsyncResult?displayProperty=nameWithType> object be allocated for each asynchronous socket operation.</span></span>  
  
 <span data-ttu-id="9fd75-111">새 <xref:System.Net.Sockets.Socket> 클래스 개선 사항에서 비동기 소켓 작업은 애플리케이션에서 할당하고 유지 관리하는 다시 사용할 수 있는 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> 클래스 개체를 통해 설명됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-111">In the new <xref:System.Net.Sockets.Socket> class enhancements, asynchronous socket operations are described by reusable <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> class objects allocated and maintained by the application.</span></span> <span data-ttu-id="9fd75-112">고성능 소켓 애플리케이션은 유지해야 하는 겹쳐진 소켓 작업량을 가장 잘 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-112">High-performance socket applications know best the amount of overlapped socket operations that must be sustained.</span></span> <span data-ttu-id="9fd75-113">애플리케이션은 <xref:System.Net.Sockets.SocketAsyncEventArgs> 개체를 필요한 개수만큼 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-113">The application can create as many of the <xref:System.Net.Sockets.SocketAsyncEventArgs> objects that it needs.</span></span> <span data-ttu-id="9fd75-114">예를 들어 서버 애플리케이션이 들어오는 클라이언트 연결 속도를 지원하기 위해 항상 15개의 소켓 허용 작업을 처리 중이어야 하는 경우 해당 용도로 다시 사용할 수 있는 <xref:System.Net.Sockets.SocketAsyncEventArgs> 개체 15개를 미리 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-114">For example, if a server application needs to have 15 socket accept operations outstanding at all times to support incoming client connection rates, it can allocate 15 reusable <xref:System.Net.Sockets.SocketAsyncEventArgs> objects in advance for that purpose.</span></span>  
  
 <span data-ttu-id="9fd75-115">이 클래스를 사용하여 비동기 소켓 작업을 수행하기 위한 패턴은 다음 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-115">The pattern for performing an asynchronous socket operation with this class consists of the following steps:</span></span>  
  
1. <span data-ttu-id="9fd75-116">새 <xref:System.Net.Sockets.SocketAsyncEventArgs> 컨텍스트 개체를 할당하거나 애플리케이션 풀에서 무료 개체를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-116">Allocate a new <xref:System.Net.Sockets.SocketAsyncEventArgs> context object, or get a free one from an application pool.</span></span>  
  
2. <span data-ttu-id="9fd75-117">컨텍스트 개체의 속성을 수행할 작업으로 설정합니다(예: 콜백 대리자 메서드 및 데이터 버퍼).</span><span class="sxs-lookup"><span data-stu-id="9fd75-117">Set properties on the context object to the operation about to be performed (the callback delegate method and data buffer, for example).</span></span>  
  
3. <span data-ttu-id="9fd75-118">적절한 소켓 메서드(xxxAsync)를 호출하여 비동기 작업을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-118">Call the appropriate socket method (xxxAsync) to initiate the asynchronous operation.</span></span>  
  
4. <span data-ttu-id="9fd75-119">비동기 소켓 메서드(xxxAsync)가 콜백에서 true를 반환하는 경우 컨텍스트 속성에서 완료 상태를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-119">If the asynchronous socket method (xxxAsync) returns true in the callback, query the context properties for completion status.</span></span>  
  
5. <span data-ttu-id="9fd75-120">비동기 소켓 메서드(xxxAsync)가 콜백에서 false를 반환하는 경우 작업이 동기적으로 완료됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-120">If the asynchronous socket method (xxxAsync) returns false in the callback, the operation completed synchronously.</span></span> <span data-ttu-id="9fd75-121">컨텍스트 속성에서 작업 결과를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-121">The context properties may be queried for the operation result.</span></span>  
  
6. <span data-ttu-id="9fd75-122">컨텍스트를 다른 작업에 다시 사용하거나, 풀에 다시 넣거나, 삭제합니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-122">Reuse the context for another operation, put it back in the pool, or discard it.</span></span>  
  
 <span data-ttu-id="9fd75-123">새 비동기 소켓 작업 컨텍스트 개체의 수명은 애플리케이션 코드와 비동기 I/O 참조에서 참조를 통해 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-123">The lifetime of the new asynchronous socket operation context object is determined by references in the application code and asynchronous I/O references.</span></span> <span data-ttu-id="9fd75-124">비동기 소켓 작업 방법 중 하나에 매개 변수로 제출된 후 애플리케이션이 비동기 소켓 작업 컨텍스트 개체에 대한 참조를 유지할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-124">It is not necessary for the application to retain a reference to an asynchronous socket operation context object after it is submitted as a parameter to one of the asynchronous socket operation methods.</span></span> <span data-ttu-id="9fd75-125">완료 콜백이 반환될 때까지 참조된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-125">It will remain referenced until the completion callback returns.</span></span> <span data-ttu-id="9fd75-126">그러나 이후 비동기 소켓 작업에 다시 사용할 수 있도록 애플리케이션에서 컨텍스트 개체에 대한 참조를 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9fd75-126">However it is advantageous for the application to retain the reference to the context object so that it can be reused for a future asynchronous socket operation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fd75-127">참조</span><span class="sxs-lookup"><span data-stu-id="9fd75-127">See also</span></span>

- <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>
- [<span data-ttu-id="9fd75-128">네트워크 프로그래밍 샘플</span><span class="sxs-lookup"><span data-stu-id="9fd75-128">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="9fd75-129">소켓 코드 예제</span><span class="sxs-lookup"><span data-stu-id="9fd75-129">Socket Code Examples</span></span>](socket-code-examples.md)
