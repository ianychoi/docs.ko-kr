---
title: '방법: 클라이언트에서 메시지 검사 또는 수정'
description: 적절 한 인터페이스를 구현 하 여 WCF 클라이언트 또는 서비스에서 들어오거나 나가는 메시지를 검사 하거나 수정 하는 방법에 대해 알아봅니다.
ms.date: 03/30/2017
ms.assetid: b8256335-f1c2-419f-b862-9f220ccad84c
ms.openlocfilehash: 1f8b75001754739b48d10ee577ae26a175e72860
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249048"
---
# <a name="how-to-inspect-or-modify-messages-on-the-client"></a><span data-ttu-id="58a2e-103">방법: 클라이언트에서 메시지 검사 또는 수정</span><span class="sxs-lookup"><span data-stu-id="58a2e-103">How to: Inspect or Modify Messages on the Client</span></span>

<span data-ttu-id="58a2e-104">을 구현 하 <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> 고 클라이언트 런타임에 삽입 하 여 WCF 클라이언트에서 들어오거나 나가는 메시지를 검사 하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-104">You can inspect or modify the incoming or outgoing messages across a WCF client by implementing a <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> and inserting it into the client runtime.</span></span> <span data-ttu-id="58a2e-105">자세한 내용은 [클라이언트 확장](extending-clients.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58a2e-105">For more information, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="58a2e-106">서비스의 해당 기능은 <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>입니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-106">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58a2e-107">전체 코드 예제는 [메시지 검사기](../samples/message-inspectors.md) 샘플을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58a2e-107">For a complete code example see the [Message Inspectors](../samples/message-inspectors.md) sample.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="58a2e-108">메시지를 검사하거나 수정하려면</span><span class="sxs-lookup"><span data-stu-id="58a2e-108">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="58a2e-109"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-109">Implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="58a2e-110">클라이언트 메시지 검사자를 삽입하려는 범위에 따라 <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-110">Implement a <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> depending upon the scope at which you want to insert the client message inspector.</span></span> <span data-ttu-id="58a2e-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> 끝점 수준에서 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-111"><xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> allows you to change behavior at the endpoint level.</span></span> <span data-ttu-id="58a2e-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> 계약 수준에서 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-112"><xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> allows you to change behavior at the contract level.</span></span>  
  
3. <span data-ttu-id="58a2e-113"><xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>에서 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 또는 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 메서드를 호출하여 동작을 삽입합니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-113">Insert the behavior prior to calling the <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58a2e-114">자세한 내용은 [동작을 사용 하 여 런타임 구성 및 확장](configuring-and-extending-the-runtime-with-behaviors.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="58a2e-114">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a2e-115">예제</span><span class="sxs-lookup"><span data-stu-id="58a2e-115">Example</span></span>  

 <span data-ttu-id="58a2e-116">다음 코드 예제는 아래 순서대로 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="58a2e-116">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="58a2e-117">클라이언트 검사자 구현.</span><span class="sxs-lookup"><span data-stu-id="58a2e-117">A client inspector implementation.</span></span>  
  
- <span data-ttu-id="58a2e-118">검사자를 삽입하는 엔드포인트 동작.</span><span class="sxs-lookup"><span data-stu-id="58a2e-118">An endpoint behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="58a2e-119">구성 파일에 동작을 추가하는 데 사용할 수 있는 <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 파생 클래스.</span><span class="sxs-lookup"><span data-stu-id="58a2e-119">A <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>- derived class that allows you to add the behavior in a configuration file.</span></span>  
  
- <span data-ttu-id="58a2e-120">클라이언트 메시지 검사자를 클라이언트 런타임에 삽입하는 엔드포인트 동작을 추가하는 구성 파일.</span><span class="sxs-lookup"><span data-stu-id="58a2e-120">A configuration file that adds the endpoint behavior which inserts the client message inspector into the client runtime.</span></span>  
  
```csharp  
// Client message inspector  
public class SimpleMessageInspector : IClientMessageInspector  
{  
    public void AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
    {  
        // Implement this method to inspect/modify messages after a message  
        // is received but prior to passing it back to the client
        Console.WriteLine("AfterReceiveReply called");  
    }  
  
    public object BeforeSendRequest(ref System.ServiceModel.Channels.Message request, IClientChannel channel)  
    {  
        // Implement this method to inspect/modify messages before they
        // are sent to the service  
        Console.WriteLine("BeforeSendRequest called");  
        return null;  
    }  
}  
```  
  
```csharp  
// Endpoint behavior  
public class SimpleEndpointBehavior : IEndpointBehavior  
{  
    public void AddBindingParameters(ServiceEndpoint endpoint, System.ServiceModel.Channels.BindingParameterCollection bindingParameters)  
    {  
         // No implementation necessary  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint, ClientRuntime clientRuntime)  
    {  
        clientRuntime.MessageInspectors.Add(new SimpleMessageInspector());  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint, EndpointDispatcher endpointDispatcher)  
    {  
         // No implementation necessary  
    }  
  
    public void Validate(ServiceEndpoint endpoint)  
    {  
         // No implementation necessary  
    }  
}  
```  
  
```csharp  
// Configuration element
public class SimpleBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public override Type BehaviorType  
    {  
        get { return typeof(SimpleEndpointBehavior); }  
    }  
  
    protected override object CreateBehavior()  
    {  
         // Create the  endpoint behavior that will insert the message  
         // inspector into the client runtime  
        return new SimpleEndpointBehavior();  
    }  
}  
```  
  
```xml
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <system.serviceModel>  
        <client>  
            <endpoint address="http://localhost:8080/SimpleService/"
                      binding="wsHttpBinding"
                      behaviorConfiguration="clientInspectorsAdded"
                      contract="ServiceReference1.IService1"  
                      name="WSHttpBinding_IService1"/>  
        </client>  
  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="clientInspectorsAdded">  
            <simpleBehaviorExtension />  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <extensions>  
        <behaviorExtensions>  
          <add  
            name="simpleBehaviorExtension"  
            type="SimpleServiceLib.SimpleBehaviorExtensionElement, Host, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58a2e-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="58a2e-121">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="58a2e-122">동작을 사용하여 런타임 구성 및 확장</span><span class="sxs-lookup"><span data-stu-id="58a2e-122">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
