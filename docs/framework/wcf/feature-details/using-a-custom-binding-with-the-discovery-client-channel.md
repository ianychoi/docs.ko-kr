---
title: Discovery 클라이언트 채널을 통해 사용자 지정 바인딩 사용
ms.date: 03/30/2017
ms.assetid: 36f95e75-04f7-44f3-a995-a0d623624d7f
ms.openlocfilehash: d84739a0021262826c541ab3ff9df663adabf44a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289661"
---
# <a name="using-a-custom-binding-with-the-discovery-client-channel"></a><span data-ttu-id="fc43b-102">Discovery 클라이언트 채널을 통해 사용자 지정 바인딩 사용</span><span class="sxs-lookup"><span data-stu-id="fc43b-102">Using a Custom Binding with the Discovery Client Channel</span></span>

<span data-ttu-id="fc43b-103"><xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>와 함께 사용자 지정 바인딩을 사용하는 경우 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> 인스턴스를 만드는 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>를 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fc43b-103">When using a custom binding with the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, you must define a <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> that creates <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances.</span></span>  
  
## <a name="creating-a-discoveryendpointprovider"></a><span data-ttu-id="fc43b-104">DiscoveryEndpointProvider 만들기</span><span class="sxs-lookup"><span data-stu-id="fc43b-104">Creating a DiscoveryEndpointProvider</span></span>  

 <span data-ttu-id="fc43b-105">는 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 요청 시 인스턴스를 만들 책임이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc43b-105">The <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> is responsible for creating <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instances on demand.</span></span> <span data-ttu-id="fc43b-106">검색 엔드포인트 공급자를 정의하려면 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider>에서 클래스를 파생시키고 <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> 메서드를 재정의한 다음 새 검색 엔드포인트를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="fc43b-106">To define a discovery endpoint provider, derive a class from <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider> and override the <xref:System.ServiceModel.Discovery.DiscoveryEndpointProvider.GetDiscoveryEndpoint%2A> method and return a new discovery endpoint.</span></span> <span data-ttu-id="fc43b-107">다음 예제에서는 검색 엔드포인트 공급자를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="fc43b-107">The following example shows how to create a discovery endpoint provider.</span></span>  
  
```csharp
// Extend DiscoveryEndpointProvider class to change the default DiscoveryEndpoint  
// to the DiscoveryClientBindingElement. The Discovery ClientChannel
// uses this endpoint to send Probe message.  
public class UdpDiscoveryEndpointProvider : DiscoveryEndpointProvider  
{  
   public override DiscoveryEndpoint GetDiscoveryEndpoint()  
   {  
      return new UdpDiscoveryEndpoint(DiscoveryVersion.WSDiscoveryApril2005);  
   }  
}  
```  
  
 <span data-ttu-id="fc43b-108">검색 엔드포인트 공급자를 정의한 후에는 다음 예제와 같이 사용자 지정 바인딩을 만들고 검색 엔드포인트 공급자를 참조하는 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fc43b-108">Once you have defined the discovery endpoint provider you can create a custom binding and add the <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>, which references the discovery endpoint provider as shown in the following example.</span></span>  
  
```csharp
DiscoveryClientBindingElement discoveryBindingElement = new DiscoveryClientBindingElement();  
  
// Provide the search criteria and the endpoint over which the probe is sent.  
discoveryBindingElement.FindCriteria = new FindCriteria(typeof(ICalculatorService));  
discoveryBindingElement.DiscoveryEndpointProvider = new UdpDiscoveryEndpointProvider();  
  
CustomBinding customBinding = new CustomBinding(new NetTcpBinding());  
// Insert DiscoveryClientBindingElement at the top of the BindingElement stack.  
// An exception is thrown if this binding element is not at the top.  
customBinding.Elements.Insert(0, discoveryBindingElement);  
```  
  
 <span data-ttu-id="fc43b-109">검색 클라이언트 채널을 사용 하는 방법에 대 한 자세한 내용은 [검색 클라이언트 채널 사용](using-the-discovery-client-channel.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="fc43b-109">For more information about using the discovery client channel, see [Using the Discovery Client Channel](using-the-discovery-client-channel.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fc43b-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="fc43b-110">See also</span></span>

- [<span data-ttu-id="fc43b-111">WCF Discovery 개요</span><span class="sxs-lookup"><span data-stu-id="fc43b-111">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)
- [<span data-ttu-id="fc43b-112">Discovery 클라이언트 채널 사용</span><span class="sxs-lookup"><span data-stu-id="fc43b-112">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)
