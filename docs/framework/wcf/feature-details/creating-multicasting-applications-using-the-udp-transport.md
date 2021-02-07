---
description: '자세한 정보: UDP 전송을 사용 하 여 멀티 캐스트 응용 프로그램 만들기'
title: UDP 전송을 사용하여 멀티캐스트 애플리케이션 만들기
ms.date: 03/30/2017
ms.assetid: 7485154a-6e85-4a67-a9d4-9008e741d4df
ms.openlocfilehash: cea76bc1256d52dabebe525b0fdd8b64c08f9e7e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99705163"
---
# <a name="creating-multicasting-applications-using-the-udp-transport"></a><span data-ttu-id="41174-103">UDP 전송을 사용하여 멀티캐스트 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="41174-103">Creating Multicasting Applications using the UDP Transport</span></span>

<span data-ttu-id="41174-104">멀티캐스트 애플리케이션은 점대점 연결을 설정하지 않고도 작은 메시지를 많은 수신자에게 동시에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="41174-104">Multicasting applications send small messages to a large number of recipients at the same time without the need to establish point to point connections.</span></span> <span data-ttu-id="41174-105">그러한 애플리케이션은 신뢰성보다 속도를 강조합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-105">The emphasis of such applications is speed over reliability.</span></span> <span data-ttu-id="41174-106">달리 말해, 특정 메시지가 실제로 수신되었는지를 보장하는 것보다 데이터를 적시에 보내는 것이 더 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-106">In other words, it is more important to send timely data than to ensure any specific message is actually received.</span></span> <span data-ttu-id="41174-107">WCF는 이제 <xref:System.ServiceModel.UdpBinding>을 사용한 멀티캐스트 애플리케이션 작성을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-107">WCF now supports writing multicasting applications using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="41174-108">이 전송은 서비스에서 작은 메시지를 많은 클라이언트에 동시에 보내야 할 때 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-108">This transport is useful in scenarios where a service needs to send out small messages to a number of clients simultaneously.</span></span> <span data-ttu-id="41174-109">이러한 서비스의 예로는 주식 시세 애플리케이션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-109">A stock ticker application is an example of such a service.</span></span>  
  
## <a name="implementing-a-multicast-application"></a><span data-ttu-id="41174-110">멀티캐스트 애플리케이션 구현</span><span class="sxs-lookup"><span data-stu-id="41174-110">Implementing a Multicast Application</span></span>  

 <span data-ttu-id="41174-111">멀티캐스트 애플리케이션을 구현하려면 멀티캐스트 메시지에 응답해야 하는 각 소프트웨어 구성 요소에 대해 서비스 계약을 정의하고 서비스 계약을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-111">To implement a multicast application, define a service contract and for each software component that needs to respond to the multicast messages, implement the service contract.</span></span> <span data-ttu-id="41174-112">예를 들어 주식 시세 애플리케이션에서 서비스 계약을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-112">For example, a stock ticker application might define a service contract:</span></span>  
  
```csharp
// Shared contracts between the client and the service  
[ServiceContract]
interface IStockTicker
{
    [OperationContract(IsOneWay = true)]
    void SendStockInfo(StockInfo[] stockInfo);
}

[DataContract]
class StockInfo
{
    [DataMember]
    public string Symbol;

    [DataMember]
    public float Price;

    public StockInfo(string symbol, float price)
    {
        this.Symbol = symbol;
        this.Price = price;
    }
}
```  
  
 <span data-ttu-id="41174-113">멀티캐스트 메시지를 수신하려는 각 애플리케이션은 이 인터페이스를 노출하는 서비스를 호스팅해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-113">Each application that wants to receive multicast messages must host a service that exposes this interface.</span></span>  <span data-ttu-id="41174-114">예를 들어, 다음은 멀티캐스트 메시지를 수신하는 방법을 보여 주는 코드 샘플입니다.</span><span class="sxs-lookup"><span data-stu-id="41174-114">For example, here is a code sample that illustrates how to receive multicast messages:</span></span>  
  
```csharp
// Service Address
string serviceAddress = "soap.udp://224.0.0.1:40000";
// Binding
UdpBinding myBinding = new UdpBinding();
// Host
ServiceHost host = new ServiceHost(typeof(StockTickerService), new Uri(serviceAddress));
// Add service endpoint
host.AddServiceEndpoint(typeof(IStockTicker), myBinding, string.Empty);
// Openup the service host
host.Open();

Console.WriteLine("Start receiving stock information");
Console.ReadLine();
```  
  
 <span data-ttu-id="41174-115">이 애플리케이션은 모든 서비스를 수신 대기할 UDP 주소를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-115">The application specifies the UDP address that all services will be listening on.</span></span> <span data-ttu-id="41174-116">새로운 <xref:System.ServiceModel.ServiceHost>가 만들어지고 <xref:System.ServiceModel.UdpBinding>을 사용해서 서비스 엔드포인트가 노출됩니다.</span><span class="sxs-lookup"><span data-stu-id="41174-116">A new <xref:System.ServiceModel.ServiceHost> is created and a service endpoint is exposed using the <xref:System.ServiceModel.UdpBinding>.</span></span> <span data-ttu-id="41174-117">그런 후 <xref:System.ServiceModel.ServiceHost>가 열리고 들어오는 메시지에 대한 수신 대기를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-117">The <xref:System.ServiceModel.ServiceHost> is then opened and will start listening for incoming messages.</span></span>  
  
 <span data-ttu-id="41174-118">이러한 유형의 시나리오에서는 클라이언트가 실제로 멀티캐스트 메시지를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-118">In this type of a scenario it is the client that actually sends out multicast messages.</span></span> <span data-ttu-id="41174-119">정확한 UDP 주소에서 수신 대기하는 각 서비스가 멀티캐스트 메시지를 수신합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-119">Each service that is listening at the correct UDP address will receive the multicast messages.</span></span> <span data-ttu-id="41174-120">다음 예제는 멀티캐스트 메시지를 보내는 클라이언트입니다.</span><span class="sxs-lookup"><span data-stu-id="41174-120">Here is an example of a client that sends out multicast messages:</span></span>  
  
```csharp
// Multicast Address
string serviceAddress = "soap.udp://224.0.0.1:40000";

// Binding
UdpBinding myBinding = new UdpBinding();

// Channel factory
ChannelFactory<IStockTicker> factory
    = new ChannelFactory<IStockTicker>(myBinding,
                new EndpointAddress(serviceAddress));

// Call service
IStockTicker proxy = factory.CreateChannel();

while (true)
{
    // This will continue to mulicast stock information
    proxy.SendStockInfo(GetStockInfo());
    Console.WriteLine($"sent stock info at {DateTime.Now}");
    // Wait for one second before sending another update
    System.Threading.Thread.Sleep(new TimeSpan(0, 0, 1));
}
```  
  
 <span data-ttu-id="41174-121">이 코드는 주식 정보를 생성한 다음 IStockTicker 서비스 계약을 사용하여 정확한 UDP 주소에서 수신 대기하는 호출 서비스에 멀티캐스트 메시지를 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-121">This code generates stock information and then uses the service contract IStockTicker to send multicast messages to call services listening on the correct UDP address.</span></span>  
  
### <a name="udp-and-reliable-messaging"></a><span data-ttu-id="41174-122">UDP 및 신뢰할 수 있는 메시징</span><span class="sxs-lookup"><span data-stu-id="41174-122">UDP and Reliable Messaging</span></span>  

  <span data-ttu-id="41174-123">UDP 프로토콜은 가볍기 때문에 UDP 바인딩은 신뢰할 수 있는 메시징을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-123">The UDP binding does not support reliable messaging because of the lightweight nature of the UDP protocol.</span></span> <span data-ttu-id="41174-124">원격 엔드포인트에서 메시지를 수신했는지 확인해야 할 경우 HTTP 또는 TCP와 같이 신뢰할 수 있는 메시지를 지원하는 전송을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="41174-124">If you need to confirm that messages are received by a remote endpoint, use a transport that supports reliable messaging like  HTTP or TCP.</span></span> <span data-ttu-id="41174-125">안정적인 메시징에 대 한 자세한 내용은을 참조 하십시오 <https://go.microsoft.com/fwlink/?LinkId=231830> .</span><span class="sxs-lookup"><span data-stu-id="41174-125">For more information about reliable messaging, see <https://go.microsoft.com/fwlink/?LinkId=231830>.</span></span>  
  
### <a name="two-way-multicast-messaging"></a><span data-ttu-id="41174-126">양방향 멀티캐스트 메시징</span><span class="sxs-lookup"><span data-stu-id="41174-126">Two-way Multicast Messaging</span></span>  

 <span data-ttu-id="41174-127">멀티캐스트 메시지가 일반적으로 단방향이지만, UdpBinding은 요청/회신 메시지 교환을 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-127">While multicast messages are generally one-way, the UdpBinding does support request/reply message exchange.</span></span> <span data-ttu-id="41174-128">UDP 전송을 사용하여 보낸 메시지에는 보낸 사람 및 받는 사람 주소가 모두 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-128">Messages sent using the UDP transport contain both a From and To address.</span></span> <span data-ttu-id="41174-129">보낸 사람 주소를 사용할 때는 도중에 악의적으로 변경될 수 있으므로 주의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-129">Care must be taken when using the From address as it could be maliciously changed en-route.</span></span>  <span data-ttu-id="41174-130">이 주소는 다음 코드를 사용하여 점검할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-130">The address can be checked using the following code:</span></span>  
  
```csharp
if (address.AddressFamily == AddressFamily.InterNetwork)
{
    // IPv4
    byte[] addressBytes = address.GetAddressBytes();
    return ((addressBytes[0] & 0xE0) == 0xE0);
}
else
{
    // IPv6
    return address.IsIPv6Multicast;
}
```  
  
 <span data-ttu-id="41174-131">이 코드는 보낸 사람 주소의 첫 번째 바이트를 보고 멀티캐스트 주소인지를 나타내는 0xE0이 들어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-131">This code checks the first byte of the From address to see if it contains 0xE0 which signifies that the address is a multi-cast address.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="41174-132">보안 고려사항</span><span class="sxs-lookup"><span data-stu-id="41174-132">Security Considerations</span></span>  

 <span data-ttu-id="41174-133">멀티캐스트 메시지를 수신 대기하는 경우 ICMP 패킷을 라우터로 전송하여 멀티캐스트 주소에서 수신 대기 중임을 알립니다.</span><span class="sxs-lookup"><span data-stu-id="41174-133">When listening for multicast messages an ICMP packet is sent to the router notifying it you are listening on the multicast address.</span></span> <span data-ttu-id="41174-134">로컬 서브넷에서 권한이 있는 모든 사용자는 이러한 형식의 패킷을 수신 대기하고 수신 대기할 멀티캐스트 주소와 포트를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-134">Anyone on the local subnet who has permissions could listen for these types of packets and determine which multicast address and port you are listening on.</span></span>  
  
 <span data-ttu-id="41174-135">보안 목적을 위해 보낸 사람의 IP 주소를 사용하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="41174-135">Do not use the IP address of the sender for any security purposes.</span></span> <span data-ttu-id="41174-136">이 정보가 스푸핑되면 애플리케이션이 잘못된 컴퓨터로 응답을 보낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="41174-136">This information can be spoofed and can cause an application to send responses to the wrong machine.</span></span> <span data-ttu-id="41174-137">이 위협을 줄이는 한 가지 방법은 메시지 수준 보안을 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="41174-137">One way to mitigate this threat is to enable message level security.</span></span> <span data-ttu-id="41174-138">네트워크 수준 IPSec(Internet Protocol Security) 및/또는 NAP(Network Access Protection)에서도 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="41174-138">At the network level IPSec  (Internet Protocol Security) and/or NAP (Network Access Protection) could also be used.</span></span>
