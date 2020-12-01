---
title: '방법: 소켓 만들기'
description: 원격 디바이스와 통신하도록 소켓을 초기화하는 방법을 알아봅니다. Socket 클래스를 사용하여 주소 패밀리, 소켓 형식, 프로토콜 유형을 지정합니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: 9746b814188a4dc92463399542a6044501d0da12
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287399"
---
# <a name="how-to-create-a-socket"></a><span data-ttu-id="d434e-104">방법: 소켓 만들기</span><span class="sxs-lookup"><span data-stu-id="d434e-104">How to: Create a Socket</span></span>

<span data-ttu-id="d434e-105">소켓을 사용하여 원격 디바이스와 통신하려면 먼저 프로토콜 및 네트워크 주소 정보를 사용하여 소켓을 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-105">Before you can use a socket to communicate with remote devices, the socket must be initialized with protocol and network address information.</span></span> <span data-ttu-id="d434e-106"><xref:System.Net.Sockets.Socket> 클래스에 대한 생성자에는 소켓이 연결을 만드는 데 사용하는 주소 패밀리, 소켓 형식 및 프로토콜 형식을 지정하는 매개 변수가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-106">The constructor for the <xref:System.Net.Sockets.Socket> class has parameters that specify the address family, socket type, and protocol type that the socket uses to make connections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d434e-107">예제</span><span class="sxs-lookup"><span data-stu-id="d434e-107">Example</span></span>  

 <span data-ttu-id="d434e-108">다음 예제에서는 인터넷 같은 TCP/IP 기반 네트워크에서 통신하는 데 사용될 수 있는 소켓을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-108">The following example creates a Socket that can be used to communicate on a TCP/IP-based network, such as the Internet.</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 <span data-ttu-id="d434e-109">TCP 대신 UDP를 사용하려면 다음 예제와 같이 프로토콜 형식을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-109">To use UDP instead of TCP, change the protocol type, as in the following example:</span></span>  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <span data-ttu-id="d434e-110"><xref:System.Net.Sockets.AddressFamily> 열거형은 **Socket** 클래스에서 네트워크 주소를 확인하는 데 사용되는 표준 주소 패밀리를 지정합니다. 예를 들어 **AddressFamily.InterNetwork** 멤버는 IP 버전 4 주소 패밀리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-110">The <xref:System.Net.Sockets.AddressFamily> enumeration specifies the standard address families used by the **Socket** class to resolve network addresses (for example, the **AddressFamily.InterNetwork** member specifies the IP version 4 address family).</span></span>  
  
 <span data-ttu-id="d434e-111"><xref:System.Net.Sockets.SocketType> 열거형은 소켓 형식을 지정합니다. 예를 들어 **SocketType.Stream** 멤버는 흐름 컨트롤을 통해 데이터를 보내고 받기 위한 표준 소켓을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-111">The <xref:System.Net.Sockets.SocketType> enumeration specifies the type of socket (for example, the **SocketType.Stream** member indicates a standard socket for sending and receiving data with flow control).</span></span>  
  
 <span data-ttu-id="d434e-112"><xref:System.Net.Sockets.ProtocolType> 열거형은 **소켓** 에서 통신할 때 사용할 네트워크 프로토콜을 지정합니다. 예를 들어 **ProtocolType.Tcp** 는 소켓이 TCP를 사용함을 나타내고 **ProtocolType.Udp** 는 소켓이 UDP를 사용함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-112">The <xref:System.Net.Sockets.ProtocolType> enumeration specifies the network protocol to use when communicating on the **Socket** (for example, **ProtocolType.Tcp** indicates that the socket uses TCP; **ProtocolType.Udp** indicates that the socket uses UDP).</span></span>  
  
 <span data-ttu-id="d434e-113">**소켓** 이 만들어진 후 원격 엔드포인트에 대한 연결을 시작하거나 원격 디바이스에서 연결을 수신할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d434e-113">After a **Socket** is created, it can either initiate a connection to a remote endpoint or receive connections from remote devices.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d434e-114">참조</span><span class="sxs-lookup"><span data-stu-id="d434e-114">See also</span></span>

- [<span data-ttu-id="d434e-115">클라이언트 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="d434e-115">Using Client Sockets</span></span>](using-client-sockets.md)
- [<span data-ttu-id="d434e-116">소켓으로 수신</span><span class="sxs-lookup"><span data-stu-id="d434e-116">Listening with Sockets</span></span>](listening-with-sockets.md)
