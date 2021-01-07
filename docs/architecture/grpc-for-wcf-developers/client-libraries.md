---
title: GRPC 클라이언트 라이브러리 만들기-WCF 개발자를 위한 gRPC
description: GRPC 서비스용 공유 클라이언트 라이브러리/패키지에 대 한 설명입니다.
ms.date: 01/06/2021
ms.openlocfilehash: c55b6d1da2377af0b687e32e7776f12b96b0a2ba
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970130"
---
# <a name="create-grpc-client-libraries"></a><span data-ttu-id="c51ea-103">GRPC 클라이언트 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="c51ea-103">Create gRPC client libraries</span></span>

<span data-ttu-id="c51ea-104">GRPC 응용 프로그램에 대 한 클라이언트 라이브러리를 배포할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-104">It isn't necessary to distribute client libraries for a gRPC application.</span></span> <span data-ttu-id="c51ea-105">조직 내에서 파일의 공유 라이브러리를 만들 수 `.proto` 있으며, 다른 팀은 해당 파일을 사용 하 여 자체 프로젝트에서 클라이언트 코드를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-105">You can create a shared library of `.proto` files within your organization, and other teams can use those files to generate client code in their own projects.</span></span> <span data-ttu-id="c51ea-106">그러나 개인 NuGet 리포지토리가 있고 다른 많은 팀에서 .NET을 사용 하는 경우 서비스 프로젝트의 일부로 클라이언트 NuGet 패키지를 만들고 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-106">But if you have a private NuGet repository and many other teams are using .NET, you can create and publish client NuGet packages as part of your service project.</span></span> <span data-ttu-id="c51ea-107">이 방법은 서비스를 공유 하 고 승격 하는 좋은 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-107">This approach can be a good way of sharing and promoting your service.</span></span>

<span data-ttu-id="c51ea-108">클라이언트 라이브러리를 배포 하는 경우의 한 가지 이점은 생성 된 gRPC 및 Protobuf 클래스를 유용한 "편리한" 메서드와 속성을 사용 하 여 개선할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-108">One advantage of distributing a client library is that you can enhance the generated gRPC and Protobuf classes with helpful "convenience" methods and properties.</span></span> <span data-ttu-id="c51ea-109">서버에서와 같이 클라이언트 코드에서 모든 클래스는로 선언 `partial` 되므로 생성 된 코드를 편집 하지 않고 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-109">In the client code, as in the server, all the classes are declared as `partial`, so you can extend them without editing the generated code.</span></span> <span data-ttu-id="c51ea-110">이 동작은 생성자, 메서드 및 계산 된 속성을 기본 형식에 쉽게 추가할 수 있음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-110">This behavior means it's easy to add constructors, methods, and calculated properties to the basic types.</span></span>

> [!CAUTION]
> <span data-ttu-id="c51ea-111">사용자 지정 코드를 사용 하 여 필수 기능을 제공 해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-111">You shouldn't use custom code to provide essential functionality.</span></span> <span data-ttu-id="c51ea-112">공유 라이브러리를 사용 하는 .NET 팀에 게 중요 한 기능을 제한 하지 않고 Python 또는 Java와 같은 다른 언어나 플랫폼을 사용 하는 팀에 제공 하지 않으려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-112">You don't want to restrict that essential functionality to .NET teams that use the shared library, and not provide it to teams that use other languages or platforms, such as Python or Java.</span></span>

<span data-ttu-id="c51ea-113">가능한 한 많은 팀에서 gRPC 서비스에 액세스할 수 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-113">Ensure that as many teams as possible can access your gRPC service.</span></span> <span data-ttu-id="c51ea-114">이 기능을 수행 하는 가장 좋은 방법은 `.proto` 개발자가 자체 클라이언트를 생성할 수 있도록 파일을 공유 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-114">The best way to do this functionality is to share `.proto` files so developers can generate their own clients.</span></span> <span data-ttu-id="c51ea-115">이 방법은 여러 팀에서 다른 프로그래밍 언어 및 프레임 워크를 자주 사용 하거나 API를 외부에서 액세스할 수 있는 다중 플랫폼 환경에서 특히 그렇습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-115">This approach is particularly true in a multi-platform environment, where different teams frequently use different programming languages and frameworks, or where your API is externally accessible.</span></span>

## <a name="useful-extensions"></a><span data-ttu-id="c51ea-116">유용한 확장</span><span class="sxs-lookup"><span data-stu-id="c51ea-116">Useful extensions</span></span>

<span data-ttu-id="c51ea-117">.NET에서는 개체의 스트림 처리를 위해 일반적으로 사용 되는 두 개의 인터페이스인 및가 있습니다. <xref:System.Collections.Generic.IEnumerable%601> <xref:System.IObservable%601></span><span class="sxs-lookup"><span data-stu-id="c51ea-117">There are two commonly used interfaces in .NET for dealing with streams of objects: <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IObservable%601>.</span></span> <span data-ttu-id="c51ea-118">.NET Core 3.0 및 c # 8.0부터 <xref:System.Collections.Generic.IAsyncEnumerable%601> 스트림을 비동기적으로 처리 하기 위한 인터페이스와 `await foreach` 인터페이스를 사용 하기 위한 구문이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-118">Starting with .NET Core 3.0 and C# 8.0, there's an <xref:System.Collections.Generic.IAsyncEnumerable%601> interface for processing streams asynchronously, and an `await foreach` syntax for using the interface.</span></span> <span data-ttu-id="c51ea-119">이 섹션에서는 이러한 인터페이스를 gRPC 스트림에 적용 하기 위한 재사용 가능한 코드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-119">This section presents reusable code for applying these interfaces to gRPC streams.</span></span>

<span data-ttu-id="c51ea-120">.NET gRPC 클라이언트 라이브러리에는 `ReadAllAsync` 인터페이스를 만드는에 대 한 확장 메서드가 있습니다 `IAsyncStreamReader<T>` `IAsyncEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="c51ea-120">With the .NET gRPC client libraries, there's a `ReadAllAsync` extension method for `IAsyncStreamReader<T>` that creates an `IAsyncEnumerable<T>` interface.</span></span> <span data-ttu-id="c51ea-121">사후 프로그래밍을 사용 하는 개발자를 위해 인터페이스를 만드는 동일한 확장 메서드는 `IObservable<T>` 다음 섹션의 예제와 같이 보일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-121">For developers using reactive programming, an equivalent extension method to create an `IObservable<T>` interface might look like the example in the following section.</span></span>

### <a name="iobservable"></a><span data-ttu-id="c51ea-122">IObservable</span><span class="sxs-lookup"><span data-stu-id="c51ea-122">IObservable</span></span>

<span data-ttu-id="c51ea-123">`IObservable<T>`인터페이스는의 "사후" 역입니다 `IEnumerable<T>` .</span><span class="sxs-lookup"><span data-stu-id="c51ea-123">The `IObservable<T>` interface is the "reactive" inverse of `IEnumerable<T>`.</span></span> <span data-ttu-id="c51ea-124">스트림에서 항목을 풀링 하는 대신 반응 방식을 사용 하면 스트림이 구독자에 항목을 푸시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-124">Rather than pulling items from a stream, the reactive approach lets the stream push items to a subscriber.</span></span> <span data-ttu-id="c51ea-125">이 동작은 gRPC 스트림과 매우 비슷하며 인터페이스 주위에 인터페이스를 쉽게 래핑할 수 `IObservable<T>` `IAsyncStreamReader<T>` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-125">This behavior is very similar to gRPC streams, and it's easy to wrap an `IObservable<T>` interface around an `IAsyncStreamReader<T>` interface.</span></span>

<span data-ttu-id="c51ea-126">`IAsyncEnumerable<T>`C #에서는 관찰 가능 개체 작업을 기본적으로 지원 하지 않기 때문에이 코드는 코드 보다 더 깁니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-126">This code is longer than the `IAsyncEnumerable<T>` code, because C# doesn't have built-in support for working with observables.</span></span> <span data-ttu-id="c51ea-127">구현 클래스를 수동으로 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-127">You have to create the implementation class manually.</span></span> <span data-ttu-id="c51ea-128">그러나 제네릭 클래스 이지만 단일 구현은 모든 형식에서 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-128">It's a generic class, though, so a single implementation works across all types.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public class GrpcStreamObservable<T> : IObservable<T>
    {
        private readonly IAsyncStreamReader<T> _reader;
        private readonly CancellationToken _token;
        private int _used;

        public GrpcStreamObservable(IAsyncStreamReader<T> reader, CancellationToken token = default)
        {
            _reader = reader;
            _token = token;
            _used = 0;
        }

        public IDisposable Subscribe(IObserver<T> observer) =>
            Interlocked.Exchange(ref _used, 1) == 0
                ? new GrpcStreamSubscription(_reader, observer, _token)
                : throw new InvalidOperationException("Subscribe can only be called once.");

    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="c51ea-129">이러한 관찰 가능한 구현을 통해 `Subscribe` 여러 구독자가 스트림에서 읽으려고 하면 비정상 상황이 발생 하므로 메서드를 한 번만 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-129">This observable implementation allows the `Subscribe` method to be called only once, because having multiple subscribers trying to read from the stream would result in chaos.</span></span> <span data-ttu-id="c51ea-130">`Replay`관찰 가능 개체의 버퍼링 및 반복 가능한 공유를 사용 하도록 설정 하는와 같은 연산자가 [있습니다.](https://www.nuget.org/packages/System.Reactive.Linq)이러한 연산자는이 구현과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-130">There are operators, such as `Replay` in the [System.Reactive.Linq](https://www.nuget.org/packages/System.Reactive.Linq), that enable buffering and repeatable sharing of observables, which can be used with this implementation.</span></span>

<span data-ttu-id="c51ea-131">`GrpcStreamSubscription`클래스는의 열거를 처리 합니다 `IAsyncStreamReader` .</span><span class="sxs-lookup"><span data-stu-id="c51ea-131">The `GrpcStreamSubscription` class handles the enumeration of the `IAsyncStreamReader`:</span></span>

```csharp
public class GrpcStreamSubscription : IDisposable
{
    private readonly Task _task;
    private readonly CancellationTokenSource _tokenSource;
    private bool _completed;

    public GrpcStreamSubscription(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        Debug.Assert(reader != null);
        Debug.Assert(observer != null);
        _tokenSource = new CancellationTokenSource();
        token.Register(_tokenSource.Cancel);
        _task = Run(reader, observer, _tokenSource.Token);
    }

    private async Task Run(IAsyncStreamReader<T> reader, IObserver<T> observer, CancellationToken token)
    {
        while (!token.IsCancellationRequested)
        {
            try
            {
                if (!await reader.MoveNext(token)) break;
            }
            catch (RpcException e) when (e.StatusCode == Grpc.Core.StatusCode.NotFound)
            {
                break;
            }
            catch (OperationCanceledException)
            {
                break;
            }
            catch (Exception e)
            {
                observer.OnError(e);
                _completed = true;
                return;
            }

            observer.OnNext(reader.Current);
        }

        _completed = true;
        observer.OnCompleted();
    }

    public void Dispose()
    {
        if (!_completed && !_tokenSource.IsCancellationRequested)
        {
            _tokenSource.Cancel();
        }

        _tokenSource.Dispose();
        _task.Dispose();
    }

}
```

<span data-ttu-id="c51ea-132">이제 필요한 모든 항목은 스트림 판독기에서 관찰 가능 개체를 만드는 간단한 확장 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-132">All that is required now is a simple extension method to create the observable from the stream reader.</span></span>

```csharp
using System;
using System.Diagnostics;
using System.Threading;
using System.Threading.Tasks;

namespace Grpc.Core
{
    public static class AsyncStreamReaderObservableExtensions
    {
        public static IObservable<T> AsObservable<T>(this IAsyncStreamReader<T> reader) =>
            new GrpcStreamObservable<T>(reader);
    }
}
```

## <a name="summary"></a><span data-ttu-id="c51ea-133">요약</span><span class="sxs-lookup"><span data-stu-id="c51ea-133">Summary</span></span>

<span data-ttu-id="c51ea-134"><xref:System.Collections.Generic.IAsyncEnumerable%601>및 <xref:System.IObservable%601> 모델은 .net의 비동기 데이터 스트림을 처리 하는 잘 지원 되 고 잘 문서화 된 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-134">The <xref:System.Collections.Generic.IAsyncEnumerable%601> and <xref:System.IObservable%601> models are both well-supported and well-documented ways of dealing with asynchronous streams of data in .NET.</span></span> <span data-ttu-id="c51ea-135">gRPC 스트림은 .NET과의 긴밀 한 통합을 제공 하 고 사후 및 비동기 프로그래밍 스타일을 제공 하 여 두 패러다임 모두에 잘 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c51ea-135">gRPC streams map well to both paradigms, offering close integration with .NET, and reactive and asynchronous programming styles.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c51ea-136">[이전](streaming-versus-repeated.md)
>[다음](security.md)</span><span class="sxs-lookup"><span data-stu-id="c51ea-136">[Previous](streaming-versus-repeated.md)
[Next](security.md)</span></span>
