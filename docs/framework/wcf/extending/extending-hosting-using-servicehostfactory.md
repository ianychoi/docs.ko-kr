---
description: '자세히 알아보기: ServiceHostFactory를 사용 하 여 호스팅 확장'
title: ServiceHostFactory를 사용하여 호스팅 확장명
ms.date: 03/30/2017
ms.assetid: bcc5ae1b-21ce-4e0e-a184-17fad74a441e
ms.openlocfilehash: cd7749a153f23586bbf570eaf97f5ae849fc522d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99735142"
---
# <a name="extending-hosting-using-servicehostfactory"></a><span data-ttu-id="b8a7a-103">ServiceHostFactory를 사용하여 호스팅 확장명</span><span class="sxs-lookup"><span data-stu-id="b8a7a-103">Extending Hosting Using ServiceHostFactory</span></span>

<span data-ttu-id="b8a7a-104"><xref:System.ServiceModel.ServiceHost>Wcf (Windows Communication Foundation)에서 서비스를 호스팅하기 위한 표준 API는 wcf 아키텍처의 확장성 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-104">The standard <xref:System.ServiceModel.ServiceHost> API for hosting services in Windows Communication Foundation (WCF) is an extensibility point in the WCF architecture.</span></span> <span data-ttu-id="b8a7a-105">사용자는 일반적으로 <xref:System.ServiceModel.ServiceHost>을 사용하여 서비스를 열기 전에 기본 엔드포인트를 명령적으로 추가하거나 동작을 수정하도록 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening>을 재지정하기 위해 <xref:System.ServiceModel.Description.ServiceDescription>에서 호스트 클래스를 파생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-105">Users can derive their own host classes from <xref:System.ServiceModel.ServiceHost>, usually to override <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening> to use <xref:System.ServiceModel.Description.ServiceDescription> to add default endpoints imperatively or modify behaviors, prior to opening the service.</span></span>  
  
 <span data-ttu-id="b8a7a-106">자체 호스팅 환경에서는 호스트를 인스턴스화하는 코드를 쓴 다음 해당 코드를 인스턴스화한 후에 그 코드에서 <xref:System.ServiceModel.ServiceHost>을 호출하기 때문에 사용자 지정 <xref:System.ServiceModel.ICommunicationObject.Open>를 만들 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-106">In the self-host environment, you do not have to create a custom <xref:System.ServiceModel.ServiceHost> because you write the code that instantiates the host and then call <xref:System.ServiceModel.ICommunicationObject.Open> on it after you instantiate it.</span></span> <span data-ttu-id="b8a7a-107">이러한 두 단계 사이에서 원하는 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-107">Between those two steps you can do whatever you want.</span></span> <span data-ttu-id="b8a7a-108">예를 들어 다음과 같이 새 <xref:System.ServiceModel.Description.IServiceBehavior>를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-108">You could, for example, add a new <xref:System.ServiceModel.Description.IServiceBehavior>:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new ServiceHost( typeof( MyService ) );  
   host.Description.Add( new MyServiceBehavior() );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="b8a7a-109">이 접근 방법은 다시 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-109">This approach is not reusable.</span></span> <span data-ttu-id="b8a7a-110">설명을 조작하는 코드는 호스트 프로그램에 코딩되기 때문에(이 경우 Main() 함수) 다른 컨텍스트에서 해당 논리를 다시 사용하기 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-110">The code that manipulates the description is coded into the host program (in this case, the Main() function), so it is difficult to reuse that logic in other contexts.</span></span> <span data-ttu-id="b8a7a-111">또한 명령적 코드가 필요 없는 <xref:System.ServiceModel.Description.IServiceBehavior>를 추가하는 다른 방법이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-111">There are also other ways of adding an <xref:System.ServiceModel.Description.IServiceBehavior> that do not require imperative code.</span></span> <span data-ttu-id="b8a7a-112"><xref:System.ServiceModel.ServiceBehaviorAttribute>에서 특성을 파생시켜 서비스 구현 형식에 적용하거나 구성 가능한 사용자 지정 동작을 만들고 구성을 사용하여 이 동작을 동적으로 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-112">You can derive an attribute from <xref:System.ServiceModel.ServiceBehaviorAttribute> and put that on your service implementation type or you can make a custom behavior configurable and compose it dynamically using configuration.</span></span>  
  
 <span data-ttu-id="b8a7a-113">그러나 이 문제를 해결하기 위해 약간 변형된 예제를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-113">However, a slight variation of the example can also be used to solve this problem.</span></span> <span data-ttu-id="b8a7a-114">한 가지 방법은 `Main()` 외부의 ServiceBehavior를 추가하는 코드를 <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A>의 사용자 지정 파생 항목에 포함되는 <xref:System.ServiceModel.ServiceHost> 메서드로 이동하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-114">One approach is to move the code that adds the ServiceBehavior out of `Main()` and into the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> method of a custom derivative of <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedHost : ServiceHost  
{  
   public DerivedHost( Type t, params Uri baseAddresses ) :  
      base( t, baseAddresses ) {}  
  
   public override void OnOpening()  
   {  
  this.Description.Add( new MyServiceBehavior() );  
   }  
}  
```  
  
 <span data-ttu-id="b8a7a-115">그런 다음 `Main()` 대신 다음을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-115">Then, inside of `Main()` you can use:</span></span>  
  
```csharp
public static void Main()  
{  
   ServiceHost host = new DerivedHost( typeof( MyService ) );  
   host.Open();  
  
   ...  
}  
```  
  
 <span data-ttu-id="b8a7a-116">이제 사용자 지정 논리를 다양한 호스트 실행 파일에 쉽게 다시 사용할 수 있는 명확하고 추상적인 개념으로 캡슐화했습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-116">Now you have encapsulated the custom logic into a clean abstraction that can be easily reused across many different host executables.</span></span>  
  
 <span data-ttu-id="b8a7a-117">IIS(인터넷 정보 서비스) 또는 WAS(Windows Process Activation Service) 내부에서 이 사용자 지정 <xref:System.ServiceModel.ServiceHost>를 사용하는 방법이 확실하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-117">It is not immediately obvious how to use this custom <xref:System.ServiceModel.ServiceHost> from inside of Internet Information Services (IIS) or Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="b8a7a-118">호스팅 환경은 애플리케이션 대신 <xref:System.ServiceModel.ServiceHost>를 인스턴스화하는 환경이기 때문에 이러한 환경은 자체 호스팅 환경과는 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-118">Those environments are different than the self-host environment, because the hosting environment is the one instantiating the <xref:System.ServiceModel.ServiceHost> on behalf of the application.</span></span> <span data-ttu-id="b8a7a-119">IIS 및 WAS 호스팅 인프라에서는 사용자 지정 <xref:System.ServiceModel.ServiceHost> 지시문에 대한 어떠한 정보도 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-119">The IIS and WAS hosting infrastructure does not know anything about your custom <xref:System.ServiceModel.ServiceHost> derivative.</span></span>  
  
 <span data-ttu-id="b8a7a-120"><xref:System.ServiceModel.Activation.ServiceHostFactory>는 IIS 또는 WAS 내에서 사용자 지정 <xref:System.ServiceModel.ServiceHost>에 액세스할 때의 문제를 해결하도록 설계되었습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-120">The <xref:System.ServiceModel.Activation.ServiceHostFactory> was designed to solve this problem of accessing your custom <xref:System.ServiceModel.ServiceHost> from within IIS or WAS.</span></span> <span data-ttu-id="b8a7a-121"><xref:System.ServiceModel.ServiceHost>에서 파생되는 사용자 지정 호스트는 동적으로 구성되고 잠재적으로 다양한 형식이기 때문에 호스팅 환경은 이러한 호스트를 직접 인스턴스화하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-121">Because a custom host that is derived from <xref:System.ServiceModel.ServiceHost> is dynamically configured and potentially of various types, the hosting environment never instantiates it directly.</span></span> <span data-ttu-id="b8a7a-122">대신 WCF는 팩터리 패턴을 사용 하 여 호스팅 환경 및 서비스의 구체적인 형식 간에 간접 참조 계층을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-122">Instead, WCF uses a factory pattern to provide a layer of indirection between the hosting environment and the concrete type of the service.</span></span> <span data-ttu-id="b8a7a-123">이러한 경우가 아닌 한 <xref:System.ServiceModel.Activation.ServiceHostFactory>의 인스턴스를 반환하는 <xref:System.ServiceModel.ServiceHost>의 기본 구현을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-123">Unless you tell it otherwise, it uses a default implementation of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="b8a7a-124">그러나 지시문에 팩터리 구현의 CLR 형식 이름을 지정 하 여 파생 호스트를 반환 하는 고유한 팩터리를 제공할 수도 있습니다 @ServiceHost .</span><span class="sxs-lookup"><span data-stu-id="b8a7a-124">But you can also provide your own factory that returns your derived host by specifying the CLR type name of your factory implementation in the @ServiceHost directive.</span></span>  
  
 <span data-ttu-id="b8a7a-125">일반적인 경우 팩터리를 구현하는 작업은 단순해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-125">The intent is that for basic cases, implementing your own factory should be a straight forward exercise.</span></span> <span data-ttu-id="b8a7a-126">예를 들어 다음은 파생된 <xref:System.ServiceModel.Activation.ServiceHostFactory>를 반환하는 사용자 지정 <xref:System.ServiceModel.ServiceHost>입니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-126">For example, here is a custom <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns a derived <xref:System.ServiceModel.ServiceHost>:</span></span>  
  
```csharp
public class DerivedFactory : ServiceHostFactory  
{  
   public override ServiceHost CreateServiceHost( Type t, Uri[] baseAddresses )  
   {  
      return new DerivedHost( t, baseAddresses )  
   }  
}  
```  
  
 <span data-ttu-id="b8a7a-127">기본 팩터리 대신이 팩터리를 사용 하려면 다음과 같이 지시문에 형식 이름을 제공 합니다 @ServiceHost .</span><span class="sxs-lookup"><span data-stu-id="b8a7a-127">To use this factory instead of the default factory, provide the type name in the @ServiceHost directive as follows:</span></span>  
  
`<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>`  
  
 <span data-ttu-id="b8a7a-128"><xref:System.ServiceModel.ServiceHost>에서 반환하는 <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>에 대해 원하는 작업을 수행하는 데 기술적 제한은 없지만 가능한 간단하게 팩터리 구현을 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-128">While there is no technical limit on doing what you want to the <xref:System.ServiceModel.ServiceHost> you return from <xref:System.ServiceModel.Activation.ServiceHostFactory.CreateServiceHost%2A>, we suggest that you keep your factory implementations as simple as possible.</span></span> <span data-ttu-id="b8a7a-129">사용자 지정 논리가 많은 경우 다시 사용할 수 있도록 팩터리 내부 대신 호스트 내부에 해당 논리를 배치 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-129">If you have lots of custom logic, it is better to put that logic inside of your host instead of inside the factory so that it can be reusable.</span></span>  
  
 <span data-ttu-id="b8a7a-130">여기에서는 호스팅 API에 대한 하나 이상의 레이어를 언급해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-130">There is one more layer to the hosting API that should be mentioned here.</span></span> <span data-ttu-id="b8a7a-131">WCF에 <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.Activation.ServiceHostFactoryBase> 는와가 각각 파생 되는 및도 있습니다 <xref:System.ServiceModel.ServiceHost> <xref:System.ServiceModel.Activation.ServiceHostFactory> .</span><span class="sxs-lookup"><span data-stu-id="b8a7a-131">WCF also has <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>, from which <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.Activation.ServiceHostFactory> respectively derive.</span></span> <span data-ttu-id="b8a7a-132">이러한 경우는 상당한 부분의 메타데이터 시스템을 사용자 지정된 생성 항목과 스왑해야 하는 고급 시나리오에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="b8a7a-132">Those exist for more advanced scenarios where you must swap out large parts of the metadata system with your own customized creations.</span></span>
