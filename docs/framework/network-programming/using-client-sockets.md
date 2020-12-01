---
title: 클라이언트 소켓 사용
description: 이 예제에서는 .NET Framework에서 소켓을 사용하여 원격 서비스에 대한 TCP/IP 연결을 만드는 방법을 보여 줍니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- receiving data, sockets
- Socket class, client sockets
- protocols, sockets
- Internet, sockets
- sockets, client sockets
- client sockets
ms.assetid: 81de9f59-8177-4d98-b25d-43fc32a98383
ms.openlocfilehash: 6982d09c20cd0d7e9d27fc63880b39e0982c86ef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96265195"
---
# <a name="using-client-sockets"></a><span data-ttu-id="d0a36-103">클라이언트 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="d0a36-103">Using Client Sockets</span></span>

<span data-ttu-id="d0a36-104"><xref:System.Net.Sockets.Socket>을 통해 대화를 시작하려면 먼저 애플리케이션과 원격 디바이스 간에 데이터 파이프를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-104">Before you can initiate a conversation through a <xref:System.Net.Sockets.Socket>, you must create a data pipe between your application and the remote device.</span></span> <span data-ttu-id="d0a36-105">다른 네트워크 주소 패밀리 및 프로토콜이 있어도 이 예제에서는 원격 서비스에 대한 TCP/IP 연결을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-105">Although other network address families and protocols exist, this example shows how to create a TCP/IP connection to a remote service.</span></span>  
  
 <span data-ttu-id="d0a36-106">TCP/IP는 네트워크 주소와 서비스 포트 번호를 사용하여 서비스를 고유하게 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-106">TCP/IP uses a network address and a service port number to uniquely identify a service.</span></span> <span data-ttu-id="d0a36-107">네트워크 주소는 네트워크에서 특정 디바이스를 식별하고, 포트 번호는 연결할 해당 디바이스의 특정 서비스를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-107">The network address identifies a specific device on the network; the port number identifies the specific service on that device to connect to.</span></span> <span data-ttu-id="d0a36-108">네트워크 주소와 서비스 포트의 조합을 엔드포인트가라고 하며, .NET Framework에서는 <xref:System.Net.EndPoint> 클래스로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-108">The combination of network address and service port is called an endpoint, which is represented in the .NET Framework by the <xref:System.Net.EndPoint> class.</span></span> <span data-ttu-id="d0a36-109">**EndPoint** 의 하위 항목이 지원되는 각 주소 패밀리에 대해 정의되고, IP 주소 패밀리에 대한 클래스는 <xref:System.Net.IPEndPoint>입니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-109">A descendant of **EndPoint** is defined for each supported address family; for the IP address family, the class is <xref:System.Net.IPEndPoint>.</span></span>  
  
 <span data-ttu-id="d0a36-110"><xref:System.Net.Dns> 클래스는 TCP/IP 인터넷 서비스를 사용하는 애플리케이션에 도메인 이름 서비스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-110">The <xref:System.Net.Dns> class provides domain-name services to applications that use TCP/IP Internet services.</span></span> <span data-ttu-id="d0a36-111"><xref:System.Net.Dns.Resolve%2A> 메서드는 DNS 서버를 쿼리하여 친숙한 도메인 이름(예: “host.contoso.com”)을 숫자 인터넷 주소(예: 192.168.1.1)에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-111">The <xref:System.Net.Dns.Resolve%2A> method queries a DNS server to map a user-friendly domain name (such as "host.contoso.com") to a numeric Internet address (such as 192.168.1.1).</span></span> <span data-ttu-id="d0a36-112">**Resolve** 는 요청된 이름에 대한 주소 및 별칭 목록이 들어 있는 <xref:System.Net.IPHostEntry>를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-112">**Resolve** returns an <xref:System.Net.IPHostEntry> that contains a list of addresses and aliases for the requested name.</span></span> <span data-ttu-id="d0a36-113">대부분의 경우 <xref:System.Net.IPHostEntry.AddressList%2A> 배열에 반환된 첫 번째 주소를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-113">In most cases, you can use the first address returned in the <xref:System.Net.IPHostEntry.AddressList%2A> array.</span></span> <span data-ttu-id="d0a36-114">다음 코드에서는 host.contoso.com 서버의 IP 주소가 포함된 <xref:System.Net.IPAddress>를 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-114">The following code gets an <xref:System.Net.IPAddress> containing the IP address for the server host.contoso.com.</span></span>  
  
```vb  
Dim ipHostInfo As IPHostEntry = Dns.Resolve("host.contoso.com")  
Dim ipAddress As IPAddress = ipHostInfo.AddressList(0)  
```  
  
```csharp  
IPHostEntry ipHostInfo = Dns.Resolve("host.contoso.com");  
IPAddress ipAddress = ipHostInfo.AddressList[0];  
```  
  
 <span data-ttu-id="d0a36-115">IANA(Internet Assigned Numbers Authority)는 공통 서비스의 포트 번호를 정의합니다. 자세한 내용은 [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)(서비스 이름 및 전송 프로토콜 포트 번호 레지스트리)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d0a36-115">The Internet Assigned Numbers Authority (Iana) defines port numbers for common services (for more information, see [Service Name and Transport Protocol Port Number Registry](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.xhtml)).</span></span> <span data-ttu-id="d0a36-116">다른 서비스에는 1,024 ~ 65,535 범위의 등록된 포트 번호가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-116">Other services can have registered port numbers in the range 1,024 to 65,535.</span></span> <span data-ttu-id="d0a36-117">다음 코드에서는 host.contoso.com의 IP 주소를 포트 번호와 결합하여 연결에 대한 원격 엔드포인트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-117">The following code combines the IP address for host.contoso.com with a port number to create a remote endpoint for a connection.</span></span>  
  
```vb  
Dim ipe As New IPEndPoint(ipAddress, 11000)  
```  
  
```csharp  
IPEndPoint ipe = new IPEndPoint(ipAddress,11000);  
```  
  
 <span data-ttu-id="d0a36-118">원격 디바이스의 주소를 결정하고 연결에 사용할 포트를 선택하면 애플리케이션이 원격 디바이스에 대한 연결을 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-118">After determining the address of the remote device and choosing a port to use for the connection, the application can attempt to establish a connection with the remote device.</span></span> <span data-ttu-id="d0a36-119">다음 예제에서는 기존 **IPEndPoint** 를 사용하여 원격 디바이스에 연결하고 throw되는 예외를 catch합니다.</span><span class="sxs-lookup"><span data-stu-id="d0a36-119">The following example uses an existing **IPEndPoint** to connect to a remote device and catches any exceptions that are thrown.</span></span>  
  
```vb  
Try  
    s.Connect(ipe)  
Catch ae As ArgumentNullException  
    Console.WriteLine("ArgumentNullException : {0}", _  
        ae.ToString())  
Catch se As SocketException  
    Console.WriteLine("SocketException : {0}", se.ToString())  
Catch e As Exception  
    Console.WriteLine("Unexpected exception : {0}", e.ToString())  
End Try  
```  
  
```csharp  
try {  
    s.Connect(ipe);  
} catch(ArgumentNullException ae) {  
    Console.WriteLine("ArgumentNullException : {0}", ae.ToString());  
} catch(SocketException se) {  
    Console.WriteLine("SocketException : {0}", se.ToString());  
} catch(Exception e) {  
    Console.WriteLine("Unexpected exception : {0}", e.ToString());  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0a36-120">참조</span><span class="sxs-lookup"><span data-stu-id="d0a36-120">See also</span></span>

- [<span data-ttu-id="d0a36-121">동기 클라이언트 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="d0a36-121">Using a Synchronous Client Socket</span></span>](using-a-synchronous-client-socket.md)
- [<span data-ttu-id="d0a36-122">비동기 클라이언트 소켓 사용</span><span class="sxs-lookup"><span data-stu-id="d0a36-122">Using an Asynchronous Client Socket</span></span>](using-an-asynchronous-client-socket.md)
- [<span data-ttu-id="d0a36-123">방법: 소켓 만들기</span><span class="sxs-lookup"><span data-stu-id="d0a36-123">How to: Create a Socket</span></span>](how-to-create-a-socket.md)
- [<span data-ttu-id="d0a36-124">소켓</span><span class="sxs-lookup"><span data-stu-id="d0a36-124">Sockets</span></span>](sockets.md)
