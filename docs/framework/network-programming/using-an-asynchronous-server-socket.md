---
title: 비동기 서버 소켓 사용
description: 이 예제에서는 비동기 서버 소켓을 보여 줍니다. Socket 클래스는 .NET Framework 비동기 프로그래밍을 사용하여 네트워크 서비스 요청을 처리합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- Socket class, asynchronous server sockets
- data requests, sockets
- sockets, asynchronous server sockets
- requesting data from Internet, sockets
- server sockets
- receiving data, sockets
- asynchronous server sockets
- protocols, sockets
- Internet, sockets
ms.assetid: 813489a9-3efd-41b6-a33f-371d55397676
ms.openlocfilehash: 6800a1973d9eb65bbb7520f9db7a8f431656c685
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265208"
---
# <a name="using-an-asynchronous-server-socket"></a><span data-ttu-id="b4dbb-104">비동기 서버 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="b4dbb-104">Using an Asynchronous Server Socket</span></span>

<span data-ttu-id="b4dbb-105">비동기 서버 소켓은 .NET Framework 비동기 프로그래밍 모델을 사용하여 네트워크 서비스 요청을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-105">Asynchronous server sockets use the .NET Framework asynchronous programming model to process network service requests.</span></span> <span data-ttu-id="b4dbb-106"><xref:System.Net.Sockets.Socket> 클래스는 표준 .NET Framework 비동기 명명 패턴을 따릅니다. 예를 들어 동기 <xref:System.Net.Sockets.Socket.Accept%2A> 메서드는 비동기 <xref:System.Net.Sockets.Socket.BeginAccept%2A> 및 <xref:System.Net.Sockets.Socket.EndAccept%2A> 메서드에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-106">The <xref:System.Net.Sockets.Socket> class follows the standard .NET Framework asynchronous naming pattern; for example, the synchronous <xref:System.Net.Sockets.Socket.Accept%2A> method corresponds to the asynchronous <xref:System.Net.Sockets.Socket.BeginAccept%2A> and <xref:System.Net.Sockets.Socket.EndAccept%2A> methods.</span></span>  
  
 <span data-ttu-id="b4dbb-107">비동기 서버 소켓에는 네트워크의 연결 요청 허용을 시작하는 메서드, 연결 요청을 처리하고 네트워크에서 데이터 수신을 시작하는 콜백 메서드, 데이터 수신을 종료하는 콜백 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-107">An asynchronous server socket requires a method to begin accepting connection requests from the network, a callback method to handle the connection requests and begin receiving data from the network, and a callback method to end receiving the data.</span></span> <span data-ttu-id="b4dbb-108">이 섹션에서는 이러한 모든 메서드에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-108">All these methods are discussed further in this section.</span></span>  
  
 <span data-ttu-id="b4dbb-109">다음 예제에서 네트워크의 연결 요청 허용을 시작하기 위해 `StartListening` 메서드는 **Socket** 을 초기화한 다음 **BeginAccept** 메서드를 사용하여 새 연결 허용을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-109">In the following example, to begin accepting connection requests from the network, the method `StartListening` initializes the **Socket** and then uses the **BeginAccept** method to start accepting new connections.</span></span> <span data-ttu-id="b4dbb-110">소켓에 새 연결 요청을 받으면 허용 콜백 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-110">The accept callback method is called when a new connection request is received on the socket.</span></span> <span data-ttu-id="b4dbb-111">이 메서드는 연결을 처리할 **소켓** 인스턴스를 가져온 다음 요청을 처리할 스레드에 해당 **Socket** 을 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-111">It is responsible for getting the **Socket** instance that will handle the connection and handing that **Socket** off to the thread that will process the request.</span></span> <span data-ttu-id="b4dbb-112">허용 콜백 메서드는 <xref:System.AsyncCallback> 대리자를 구현합니다. void를 반환하고 <xref:System.IAsyncResult> 형식의 단일 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-112">The accept callback method implements the <xref:System.AsyncCallback> delegate; it returns a void and takes a single parameter of type <xref:System.IAsyncResult>.</span></span> <span data-ttu-id="b4dbb-113">다음 예제는 허용 콜백 메서드의 셸입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-113">The following example is the shell of an accept callback method.</span></span>  
  
```vb  
Sub AcceptCallback(ar As IAsyncResult)  
    ' Add the callback code here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
void AcceptCallback(IAsyncResult ar)
{  
    // Add the callback code here.  
}  
```  
  
 <span data-ttu-id="b4dbb-114">**BeginAccept** 메서드는 허용 콜백 메서드를 가리키는 **AsyncCallback** 대리자와 상태 정보를 콜백 메서드에 전달하는 데 사용되는 개체 등 두 개의 매개 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-114">The **BeginAccept** method takes two parameters, an **AsyncCallback** delegate that points to the accept callback method and an object that is used to pass state information to the callback method.</span></span> <span data-ttu-id="b4dbb-115">다음 예제에서 수신 대기하는 **Socket** 은 *state* 매개 변수를 통해 콜백 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-115">In the following example, the listening **Socket** is passed to the callback method through the *state* parameter.</span></span> <span data-ttu-id="b4dbb-116">이 예제에서는 **AsyncCallback** 대리자를 만들고 네트워크 연결 허용을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-116">This example creates an **AsyncCallback** delegate and starts accepting connections from the network.</span></span>  
  
```vb  
listener.BeginAccept( _  
    New AsyncCallback(SocketListener.AcceptCallback),_  
    listener)  
```  
  
```csharp  
listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
```  
  
 <span data-ttu-id="b4dbb-117">비동기 소켓은 시스템 스레드 풀의 스레드를 사용하여 들어오는 연결을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-117">Asynchronous sockets use threads from the system thread pool to process incoming connections.</span></span> <span data-ttu-id="b4dbb-118">한 스레드는 연결을 허용하고, 다른 스레드는 들어오는 각 연결을 처리하는 데 사용되고, 마지막 스레드는 연결에서 데이터를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-118">One thread is responsible for accepting connections, another thread is used to handle each incoming connection, and another thread is responsible for receiving data from the connection.</span></span> <span data-ttu-id="b4dbb-119">스레드 풀에서 할당된 스레드에 따라 세 스레드는 동일한 스레드일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-119">These could be the same thread, depending on which thread is assigned by the thread pool.</span></span> <span data-ttu-id="b4dbb-120">다음 예제에서 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 클래스는 주 스레드의 실행을 일시 중단하고 실행을 계속할 수 있으면 알려줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-120">In the following example, the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class suspends execution of the main thread and signals when execution can continue.</span></span>  
  
 <span data-ttu-id="b4dbb-121">다음 예제에서는 로컬 컴퓨터에 비동기 TCP/IP 소켓을 만들고 연결 허용을 시작하는 비동기 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-121">The following example shows an asynchronous method that creates an asynchronous TCP/IP socket on the local computer and begins accepting connections.</span></span> <span data-ttu-id="b4dbb-122">`allDone`이라는 전역 **ManualResetEvent** 가 있고, 메서드는 `SocketListener`라는 클래스의 멤버이고, `AcceptCallback`이라는 콜백 메서드가 정의되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-122">It assumes that there is a global **ManualResetEvent** named `allDone`, that the method is a member of a class named `SocketListener`, and that a callback method named `AcceptCallback` is defined.</span></span>  
  
```vb  
Public Sub StartListening()  
    Dim ipHostInfo As IPHostEntry = Dns.Resolve(Dns.GetHostName())  
    Dim localEP = New IPEndPoint(ipHostInfo.AddressList(0), 11000)  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}")  
  
    Dim listener As New Socket(localEP.Address.AddressFamily, _  
       SocketType.Stream, ProtocolType.Tcp)  
  
    Try  
        listener.Bind(localEP)  
        listener.Listen(10)  
  
        While True  
            allDone.Reset()  
  
            Console.WriteLine("Waiting for a connection...")  
            listener.BeginAccept(New _  
                AsyncCallback(SocketListener.AcceptCallback), _  
                listener)  
  
            allDone.WaitOne()  
        End While  
    Catch e As Exception  
        Console.WriteLine(e.ToString())  
    End Try  
    Console.WriteLine("Closing the listener...")  
End Sub 'StartListening  
```  
  
```csharp  
public void StartListening()
{  
    IPHostEntry ipHostInfo = Dns.Resolve(Dns.GetHostName());  
    IPEndPoint localEP = new IPEndPoint(ipHostInfo.AddressList[0], 11000);  
  
    Console.WriteLine($"Local address and port : {localEP.ToString()}");  
  
    Socket listener = new Socket(localEP.Address.AddressFamily, SocketType.Stream, ProtocolType.Tcp);  
  
    try
    {  
        listener.Bind(localEP);  
        listener.Listen(10);  
  
        while (true)
        {  
            allDone.Reset();  
  
            Console.WriteLine("Waiting for a connection...");  
            listener.BeginAccept(new AsyncCallback(SocketListener.AcceptCallback), listener);  
  
            allDone.WaitOne();  
        }  
    }
    catch (Exception e)
    {  
        Console.WriteLine(e.ToString());  
    }  
  
    Console.WriteLine("Closing the listener...");  
}  
```  
  
 <span data-ttu-id="b4dbb-123">허용 콜백 메서드(앞의 예제에서 `AcceptCallback`)는 주 애플리케이션 스레드에 처리를 계속하도록 알리고, 클라이언트에 연결하고, 클라이언트에서 비동기 데이터 읽기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-123">The accept callback method (`AcceptCallback` in the preceding example) is responsible for signaling the main application thread to continue processing, establishing the connection with the client, and starting the asynchronous read of data from the client.</span></span> <span data-ttu-id="b4dbb-124">다음 예제에서는 `AcceptCallback` 메서드 구현의 첫 번째 부분을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-124">The following example is the first part of an implementation of the `AcceptCallback` method.</span></span> <span data-ttu-id="b4dbb-125">이 메서드 섹션은 주 애플리케이션 스레드에 처리를 계속하도록 알리고 클라이언트에 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-125">This section of the method signals the main application thread to continue processing and establishes the connection to the client.</span></span> <span data-ttu-id="b4dbb-126">`allDone`이라는 전역 **ManualResetEvent** 를 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-126">It assumes a global **ManualResetEvent** named `allDone`.</span></span>  
  
```vb  
Public Sub AcceptCallback(ar As IAsyncResult)  
    allDone.Set()  
  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Additional code to read data goes here.  
End Sub 'AcceptCallback  
```  
  
```csharp  
public void AcceptCallback(IAsyncResult ar)
{  
    allDone.Set();  
  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Additional code to read data goes here.
}  
```  
  
 <span data-ttu-id="b4dbb-127">클라이언트 소켓에서 데이터를 읽으려면 비동기 호출 간에 값을 전달하는 상태 개체가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-127">Reading data from a client socket requires a state object that passes values between asynchronous calls.</span></span> <span data-ttu-id="b4dbb-128">다음 예제에서는 원격 클라이언트에서 문자열을 수신하는 상태 개체를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-128">The following example implements a state object for receiving a string from the remote client.</span></span> <span data-ttu-id="b4dbb-129">클라이언트 소켓에 대한 필드, 데이터 수신을 위한 데이터 버퍼, 클라이언트에서 보낸 데이터 문자열을 수신하기 위한 <xref:System.Text.StringBuilder>가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-129">It contains fields for the client socket, a data buffer for receiving data, and a <xref:System.Text.StringBuilder> for creating the data string sent by the client.</span></span> <span data-ttu-id="b4dbb-130">이러한 필드를 상태 개체에 배치하면 여러 호출 간에 개체 값을 보존하여 클라이언트 소켓에서 데이터를 읽을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-130">Placing these fields in the state object allows their values to be preserved across multiple calls to read data from the client socket.</span></span>  
  
```vb  
Public Class StateObject  
    Public workSocket As Socket = Nothing  
    Public BufferSize As Integer = 1024  
    Public buffer(BufferSize) As Byte  
    Public sb As New StringBuilder()  
End Class 'StateObject  
```  
  
```csharp  
public class StateObject
{  
    public Socket workSocket = null;  
    public const int BufferSize = 1024;  
    public byte[] buffer = new byte[BufferSize];  
    public StringBuilder sb = new StringBuilder();  
}  
```  
  
 <span data-ttu-id="b4dbb-131">클라이언트 소켓에서 데이터 수신을 시작하는 `AcceptCallback` 메서드 섹션은 먼저 `StateObject` 클래스의 인스턴스를 초기화한 다음 <xref:System.Net.Sockets.Socket.BeginReceive%2A> 메서드를 호출하여 클라이언트 소켓에서 비동기적으로 데이터 읽기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-131">The section of the `AcceptCallback` method that starts receiving the data from the client socket first initializes an instance of the `StateObject` class and then calls the <xref:System.Net.Sockets.Socket.BeginReceive%2A> method to start reading the data from the client socket asynchronously.</span></span>  
  
 <span data-ttu-id="b4dbb-132">다음 예제에서는 전체 `AcceptCallback` 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-132">The following example shows the complete `AcceptCallback` method.</span></span> <span data-ttu-id="b4dbb-133">`allDone,`이라는 전역 **ManualResetEvent** 가 있고, `StateObject`가 정의되어 있고, `ReadCallback` 메서드가 `SocketListener`라는 클래스에 정의되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-133">It assumes that there is a global **ManualResetEvent** named `allDone,` that the `StateObject` class is defined, and that the `ReadCallback` method is defined in a class named `SocketListener`.</span></span>  
  
```vb  
Public Shared Sub AcceptCallback(ar As IAsyncResult)  
    ' Get the socket that handles the client request.  
    Dim listener As Socket = CType(ar.AsyncState, Socket)  
    Dim handler As Socket = listener.EndAccept(ar)  
  
    ' Signal the main thread to continue.  
    allDone.Set()  
  
    ' Create the state object.  
    Dim state As New StateObject()  
    state.workSocket = handler  
    handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
        AddressOf AsynchronousSocketListener.ReadCallback, state)  
End Sub 'AcceptCallback  
```  
  
```csharp  
public static void AcceptCallback(IAsyncResult ar)
{  
    // Get the socket that handles the client request.  
    Socket listener = (Socket) ar.AsyncState;  
    Socket handler = listener.EndAccept(ar);  
  
    // Signal the main thread to continue.  
    allDone.Set();  
  
    // Create the state object.  
    StateObject state = new StateObject();  
    state.workSocket = handler;  
    handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
        new AsyncCallback(AsynchronousSocketListener.ReadCallback), state);  
}  
```  
  
 <span data-ttu-id="b4dbb-134">비동기 소켓 서버에 대해 구현해야 하는 최종 메서드는 클라이언트에서 보낸 데이터를 반환하는 읽기 콜백 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-134">The final method that needs to be implemented for the asynchronous socket server is the read callback method that returns the data sent by the client.</span></span> <span data-ttu-id="b4dbb-135">허용 콜백 메서드와 마찬가지로 읽기 콜백 메서드는 **AsyncCallback** 대리자입니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-135">Like the accept callback method, the read callback method is an **AsyncCallback** delegate.</span></span> <span data-ttu-id="b4dbb-136">이 메서드는 클라이언트 소켓에서 1바이트 이상을 데이터 버퍼로 읽어온 다음 클라이언트에서 보낸 데이터가 완료될 때까지 **BeginReceive** 메서드를 다시 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-136">This method reads one or more bytes from the client socket into the data buffer and then calls the **BeginReceive** method again until the data sent by the client is complete.</span></span> <span data-ttu-id="b4dbb-137">클라이언트에서 전체 메시지를 읽은 후 문자열이 콘솔에 표시되고 클라이언트에 대한 연결을 처리하는 서버 소켓이 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-137">Once the entire message has been read from the client, the string is displayed on the console and the server socket handling the connection to the client is closed.</span></span>  
  
 <span data-ttu-id="b4dbb-138">다음 샘플에서는 `ReadCallback` 메서드를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-138">The following sample implements the `ReadCallback` method.</span></span> <span data-ttu-id="b4dbb-139">`StateObject` 클래스가 정의되어 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="b4dbb-139">It assumes that the `StateObject` class is defined.</span></span>  
  
```vb  
Public Shared Sub ReadCallback(ar As IAsyncResult)  
    Dim state As StateObject = CType(ar.AsyncState, StateObject)  
    Dim handler As Socket = state.workSocket  
  
    ' Read data from the client socket.
    Dim read As Integer = handler.EndReceive(ar)  
  
    ' Data was read from the client socket.  
    If read > 0 Then  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer, 0, read))  
        handler.BeginReceive(state.buffer, 0, state.BufferSize, 0, _  
            AddressOf ReadCallback, state)  
    Else  
        If state.sb.Length > 1 Then  
            ' All the data has been read from the client;  
            ' display it on the console.  
            Dim content As String = state.sb.ToString()  
            Console.WriteLine($"Read {content.Length} bytes from socket. {ControlChars.Cr} Data : {content}")  
        End If  
    End If  
End Sub 'ReadCallback  
```  
  
```csharp  
public static void ReadCallback(IAsyncResult ar)
{  
    StateObject state = (StateObject) ar.AsyncState;  
    Socket handler = state.WorkSocket;  
  
    // Read data from the client socket.  
    int read = handler.EndReceive(ar);  
  
    // Data was read from the client socket.  
    if (read > 0)
    {  
        state.sb.Append(Encoding.ASCII.GetString(state.buffer,0,read));  
        handler.BeginReceive(state.buffer, 0, StateObject.BufferSize, 0,  
            new AsyncCallback(ReadCallback), state);  
    }
    else
    {  
        if (state.sb.Length > 1)
        {  
            // All the data has been read from the client;  
            // display it on the console.  
            string content = state.sb.ToString();  
            Console.WriteLine($"Read {content.Length} bytes from socket.\n Data : {content}");
        }  
        handler.Close();  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4dbb-140">참조</span><span class="sxs-lookup"><span data-stu-id="b4dbb-140">See also</span></span>

- [<span data-ttu-id="b4dbb-141">동기 서버 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="b4dbb-141">Using a Synchronous Server Socket</span></span>](using-a-synchronous-server-socket.md)
- [<span data-ttu-id="b4dbb-142">비동기 서버 소켓 예제</span><span class="sxs-lookup"><span data-stu-id="b4dbb-142">Asynchronous Server Socket Example</span></span>](asynchronous-server-socket-example.md)
- [<span data-ttu-id="b4dbb-143">스레딩</span><span class="sxs-lookup"><span data-stu-id="b4dbb-143">Threading</span></span>](../../standard/threading/index.md)
- [<span data-ttu-id="b4dbb-144">소켓으로 수신</span><span class="sxs-lookup"><span data-stu-id="b4dbb-144">Listening with Sockets</span></span>](listening-with-sockets.md)
