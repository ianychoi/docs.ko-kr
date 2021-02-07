---
description: '자세한 정보: 사용자 지정 서비스 호스트'
title: 사용자 지정 서비스 호스트
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: a18c3ec10eef5fc2c436a2fc2665ea73ed963384
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99752446"
---
# <a name="custom-service-host"></a><span data-ttu-id="33275-103">사용자 지정 서비스 호스트</span><span class="sxs-lookup"><span data-stu-id="33275-103">Custom Service Host</span></span>

<span data-ttu-id="33275-104">이 샘플에서는 <xref:System.ServiceModel.ServiceHost> 클래스의 사용자 지정 파생 항목을 사용하여 서비스의 런타임 동작을 변경하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33275-104">This sample demonstrates how to use a custom derivative of the <xref:System.ServiceModel.ServiceHost> class to alter the run-time behavior of a service.</span></span> <span data-ttu-id="33275-105">이 접근 방식을 사용하면 일반적인 방법으로 여러 서비스를 구성하는 대신 재사용 가능한 대체 방법이 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="33275-105">This approach provides a reusable alternative to configuring a large number of services in a common way.</span></span> <span data-ttu-id="33275-106">또한 샘플에서는 <xref:System.ServiceModel.Activation.ServiceHostFactory> 클래스를 사용하여 IIS(인터넷 정보 서비스) 또는 WAS(Windows Process Activation Service) 호스팅 환경에서 사용자 지정 ServiceHost를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33275-106">The sample also demonstrates how to use the <xref:System.ServiceModel.Activation.ServiceHostFactory> class to use a custom ServiceHost in the Internet Information Services (IIS) or Windows Process Activation Service (WAS) hosting environment.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33275-107">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="33275-108">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="33275-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="33275-109">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="33275-110">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a><span data-ttu-id="33275-111">시나리오 정보</span><span class="sxs-lookup"><span data-stu-id="33275-111">About the scenario</span></span>

 <span data-ttu-id="33275-112">잠재적으로 중요 한 서비스 메타 데이터가 실수로 공개 되지 않도록 하기 위해 WCF (Windows Communication Foundation) 서비스의 기본 구성에서는 메타 데이터 게시를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-112">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="33275-113">이 동작은 기본적으로 안전 하지만, 구성에서 서비스의 메타 데이터 게시 동작을 명시적으로 사용 하도록 설정 하지 않은 경우 Svcutil.exe와 같은 메타 데이터 가져오기 도구를 사용 하 여 서비스를 호출 하는 데 필요한 클라이언트 코드를 생성할 수 없음을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-113">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service's metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
 <span data-ttu-id="33275-114">여러 서비스에 메타데이터 게시를 사용하도록 설정하면 각각의 개별 서비스에 동일한 구성 요소가 추가되어 기본적으로 동일한 구성 정보가 많이 생성될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-114">Enabling metadata publishing for a large number of services involves adding the same configuration elements to each individual service, which results in a large amount of configuration information that is essentially the same.</span></span> <span data-ttu-id="33275-115">각 서비스를 개별적으로 구성하는 대신 메타데이터 게시를 한 번 사용한 다음 여러 가지 다른 서비스에서 해당 코드를 다시 사용하도록 하는 명령 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-115">As an alternative to configuring each service individually, it is possible to write the imperative code that enables metadata publishing once and then reuse that code across several different services.</span></span> <span data-ttu-id="33275-116">이 작업은 새 클래스를 만들어 수행합니다. 새 클래스는 <xref:System.ServiceModel.ServiceHost>에서 파생되며 `ApplyConfiguration`() 메서드를 재정의하여 메타데이터 게시 동작을 명령적으로 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-116">This is accomplished by creating a new class that derives from <xref:System.ServiceModel.ServiceHost> and overrides the `ApplyConfiguration`() method to imperatively add the metadata publishing behavior.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="33275-117">쉽게 구별할 수 있도록 이 샘플에서는 보안이 설정되지 않은 메타데이터 게시 엔드포인트를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33275-117">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="33275-118">이러한 끝점은 인증 되지 않은 익명의 소비자가 사용할 수 있으므로 이러한 끝점을 배포 하기 전에 서비스의 메타 데이터를 공개적으로 노출 하는 것이 적절 한지 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-118">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service's metadata is appropriate.</span></span>  
  
## <a name="implementing-a-custom-servicehost"></a><span data-ttu-id="33275-119">사용자 지정 ServiceHost 구현</span><span class="sxs-lookup"><span data-stu-id="33275-119">Implementing a custom ServiceHost</span></span>

 <span data-ttu-id="33275-120"><xref:System.ServiceModel.ServiceHost> 클래스는 상속자가 서비스의 런타임 동작을 변경하기 위해 재정의할 수 있는 여러 가지 유용한 가상 메서드를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-120">The <xref:System.ServiceModel.ServiceHost> class exposes several useful virtual methods that inheritors can override to alter the run-time behavior of a service.</span></span> <span data-ttu-id="33275-121">예를 들어, `ApplyConfiguration`() 메서드는 구성 저장소에서 서비스 구성 정보를 읽고 그에 따라 호스트의 <xref:System.ServiceModel.Description.ServiceDescription>을 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-121">For example, the `ApplyConfiguration`() method reads service configuration information from the configuration store and alters the host's <xref:System.ServiceModel.Description.ServiceDescription> accordingly.</span></span> <span data-ttu-id="33275-122">기본 구현은 응용 프로그램의 구성 파일에서 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-122">The default implementation reads configuration from the application's configuration file.</span></span> <span data-ttu-id="33275-123">사용자 지정 구현에서는 명령 코드를 사용하여 `ApplyConfiguration`을 추가로 변경하거나 기본 구성 저장소를 완전히 바꾸도록 <xref:System.ServiceModel.Description.ServiceDescription>()을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-123">Custom implementations can override `ApplyConfiguration`() to further alter the <xref:System.ServiceModel.Description.ServiceDescription> using imperative code or even replace the default configuration store entirely.</span></span> <span data-ttu-id="33275-124">예를 들어 응용 프로그램의 구성 파일 대신 데이터베이스에서 서비스의 끝점 구성을 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-124">For example, to read a service's endpoint configuration from a database instead of the application's configuration file.</span></span>  
  
 <span data-ttu-id="33275-125">이 샘플에서는이 동작이 서비스의 구성 파일에 명시적으로 추가 되지 않은 경우에도 ServiceMetadataBehavior (메타 데이터 게시를 사용 하도록 설정)를 추가 하는 사용자 지정 ServiceHost를 빌드하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-125">In this sample, we want to build a custom ServiceHost that adds the ServiceMetadataBehavior (which enables metadata publishing) even if this behavior is not explicitly added in the service's configuration file.</span></span> <span data-ttu-id="33275-126">이를 수행 하려면에서 상속 하는 새 클래스를 만들고 <xref:System.ServiceModel.ServiceHost> `ApplyConfiguration` ()을 재정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-126">To accomplish this, create a new class that inherits from <xref:System.ServiceModel.ServiceHost> and overrides `ApplyConfiguration`().</span></span>  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 <span data-ttu-id="33275-127">응용 프로그램의 구성 파일에 제공 된 구성을 무시 하지 않기 때문에 ()를 재정의 하는 첫 번째 작업은 `ApplyConfiguration` 기본 구현을 호출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="33275-127">Because we do not want to ignore any configuration that has been provided in the application's configuration file, the first thing our override of `ApplyConfiguration`() does is call the base implementation.</span></span> <span data-ttu-id="33275-128">이 메서드가 완료되면 다음 명령 코드를 사용하여 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>를 명령적으로 설명에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-128">Once this method completes, we can imperatively add the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> to the description using the following imperative code.</span></span>  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 <span data-ttu-id="33275-129">마지막으로 `ApplyConfiguration`()을 재정의하기 위해 기본 메타데이터 엔드포인트를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-129">The last thing our `ApplyConfiguration`() override must do is add the default metadata endpoint.</span></span> <span data-ttu-id="33275-130">규칙에 따라 서비스 호스트의 BaseAddresses 컬렉션에서 각 URI에 대해 하나의 메타 데이터 끝점이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33275-130">By convention, one metadata endpoint is created for each URI in the service host's BaseAddresses collection.</span></span>  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a><span data-ttu-id="33275-131">자체 호스팅 환경에서 사용자 지정 ServiceHost 사용</span><span class="sxs-lookup"><span data-stu-id="33275-131">Using a custom ServiceHost in self-host</span></span>  

 <span data-ttu-id="33275-132">이제 사용자 지정 ServiceHost 구현을 완료했으므로 `SelfDescribingServiceHost`의 인스턴스 내부에 해당 서비스를 호스트하여 모든 서비스에 메타데이터 게시 동작을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-132">Now that we have completed our custom ServiceHost implementation, we can use it to add metadata publishing behavior to any service by hosting that service inside of an instance of our `SelfDescribingServiceHost`.</span></span> <span data-ttu-id="33275-133">다음 코드에서는 자체 호스팅 시나리오에서 해당 서비스를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33275-133">The following code shows how to use it in the self-host scenario.</span></span>  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 <span data-ttu-id="33275-134">사용자 지정 호스트는 기본 클래스를 사용 하 여 서비스를 호스트 하는 것 처럼 응용 프로그램의 구성 파일에서 서비스의 끝점 구성을 계속 읽습니다 <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="33275-134">Our custom host still reads the service's endpoint configuration from the application's configuration file, as if we had used the default <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="33275-135">그러나 사용자 지정 호스트의 내부에서 메타데이터 게시를 사용하도록 설정하는 논리를 추가했으므로 구성에서 메타데이터 게시 동작을 더 이상 명시적으로 사용하도록 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-135">However, because we added the logic to enable metadata publishing inside of our custom host, we no longer must explicitly enable the metadata publishing behavior in configuration.</span></span> <span data-ttu-id="33275-136">이 접근 방식을 사용하면 여러 서비스가 포함된 애플리케이션을 빌드할 때 같은 구성 요소를 반복해서 작성하지 않고도 각 서비스에서 메타데이터 게시를 사용하도록 설정할 수 있다는 장점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-136">This approach has a distinct advantage when you are building an application that contains several services and you want to enable metadata publishing on each of them without writing the same configuration elements over and over.</span></span>  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a><span data-ttu-id="33275-137">IIS 또는 WAS 환경에서 사용자 지정 ServiceHost 사용</span><span class="sxs-lookup"><span data-stu-id="33275-137">Using a custom ServiceHost in IIS or WAS</span></span>  

 <span data-ttu-id="33275-138">자체 호스팅 시나리오에서는 결국 애플리케이션 코드를 통해 서비스 호스트 인스턴스를 만들고 여는 작업을 수행하므로 사용자 지정 서비스 호스트 사용이 간단합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-138">Using a custom service host in self-host scenarios is straightforward, because it is your application code that is ultimately responsible for creating and opening the service host instance.</span></span> <span data-ttu-id="33275-139">그러나 IIS 또는 WAS 호스팅 환경에서 WCF 인프라는 들어오는 메시지에 응답 하 여 서비스의 호스트를 동적으로 인스턴스화합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-139">In the IIS or WAS hosting environment, however, the WCF infrastructure is dynamically instantiating your service's host in response to incoming messages.</span></span> <span data-ttu-id="33275-140">이 호스팅 환경에서 사용자 지정 서비스 호스트를 사용할 수도 있지만 ServiceHostFactory 형식의 추가 코드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-140">Custom service hosts can also be used in this hosting environment, but they require some additional code in the form of a ServiceHostFactory.</span></span> <span data-ttu-id="33275-141">다음 코드에서는 사용자 지정 <xref:System.ServiceModel.Activation.ServiceHostFactory>의 인스턴스를 반환하는 `SelfDescribingServiceHost`의 파생 항목을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="33275-141">The following code shows a derivative of <xref:System.ServiceModel.Activation.ServiceHostFactory> that returns instances of our custom `SelfDescribingServiceHost`.</span></span>  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 <span data-ttu-id="33275-142">여기에서 볼 수 있듯이 사용자 지정 ServiceHostFactory을 구현 하는 것은 간단 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-142">As you can see, implementing a custom ServiceHostFactory is straightforward.</span></span> <span data-ttu-id="33275-143">모든 사용자 지정 논리는 ServiceHost 구현 내에 있고 팩터리는 파생 클래스의 인스턴스를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-143">All of the custom logic resides inside of the ServiceHost implementation; the factory returns an instance of the derived class.</span></span>  
  
 <span data-ttu-id="33275-144">서비스 구현과 함께 사용자 지정 팩터리를 사용 하려면 서비스의 .svc 파일에 추가 메타 데이터를 추가 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-144">To use a custom factory with a service implementation, we must add some additional metadata to the service's .svc file.</span></span>  
  
```aspx-csharp
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 <span data-ttu-id="33275-145">여기서는 `Factory` 지시문에 추가 특성을 추가 `@ServiceHost` 하 고 사용자 지정 팩터리의 CLR 형식 이름을 특성의 값으로 전달 했습니다.</span><span class="sxs-lookup"><span data-stu-id="33275-145">Here we have added an additional `Factory` attribute to the `@ServiceHost` directive, and passed the CLR type name of our custom factory as the attribute's value.</span></span> <span data-ttu-id="33275-146">IIS 또는 WAS가이 서비스에 대 한 메시지를 받으면 WCF 호스팅 인프라는 먼저 ServiceHostFactory의 인스턴스를 만든 다음를 호출 하 여 서비스 호스트 자체를 인스턴스화합니다 `ServiceHostFactory.CreateServiceHost()` .</span><span class="sxs-lookup"><span data-stu-id="33275-146">When IIS or WAS receives a message for this service, the WCF hosting infrastructure first creates an instance of the ServiceHostFactory and then instantiates the service host itself by calling `ServiceHostFactory.CreateServiceHost()`.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="33275-147">샘플 실행</span><span class="sxs-lookup"><span data-stu-id="33275-147">Running the sample</span></span>  

 <span data-ttu-id="33275-148">이 샘플에서는 완벽 하 게 작동 하는 클라이언트 및 서비스 구현을 제공 하지만이 샘플에서는 사용자 지정 호스트를 사용 하 여 서비스의 런타임 동작을 변경 하는 방법을 보여 줍니다 .를 사용 하 여 다음 단계를 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-148">Although this sample does provide a fully functional client and service implementation, the point of the sample is to illustrate how to alter a service's run-time behavior by means of a custom host., do the following steps:</span></span>  
  
### <a name="observe-the-effect-of-the-custom-host"></a><span data-ttu-id="33275-149">사용자 지정 호스트의 효과를 관찰 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-149">Observe the effect of the custom host</span></span>
  
1. <span data-ttu-id="33275-150">서비스의 Web.config 파일을 열고 서비스에 대 한 메타 데이터를 명시적으로 사용 하도록 설정 하는 구성이 없는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-150">Open the service's Web.config file and observe that there is no configuration explicitly enabling metadata for the service.</span></span>  
  
2. <span data-ttu-id="33275-151">서비스의 .svc 파일을 열고 해당 @ServiceHost 지시문에 사용자 지정 ServiceHostFactory의 이름을 지정 하는 팩터리 특성이 포함 되어 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-151">Open the service's .svc file and observe that its @ServiceHost directive contains a Factory attribute that specifies the name of a custom ServiceHostFactory.</span></span>  
  
### <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="33275-152">샘플 설정, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="33275-152">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="33275-153">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)를 수행 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-153">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="33275-154">솔루션을 빌드하려면 [Windows Communication Foundation 샘플 빌드](building-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="33275-154">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="33275-155">솔루션이 빌드된 후 Setup.bat를 실행 하 여 IIS 7.0에서 ServiceModelSamples 응용 프로그램을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-155">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS 7.0.</span></span> <span data-ttu-id="33275-156">이제 ServiceModelSamples 디렉터리가 IIS 7.0 응용 프로그램으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="33275-156">The ServiceModelSamples directory should now appear as an IIS 7.0 Application.</span></span>

4. <span data-ttu-id="33275-157">단일 컴퓨터 또는 다중 컴퓨터 구성에서 샘플을 실행 하려면 [Windows Communication Foundation 샘플 실행](running-the-samples.md)의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="33275-157">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

5. <span data-ttu-id="33275-158">IIS 7.0 응용 프로그램을 제거 하려면 *Cleanup.bat* 를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="33275-158">To remove the IIS 7.0 application, run *Cleanup.bat*.</span></span>

## <a name="see-also"></a><span data-ttu-id="33275-159">참고 항목</span><span class="sxs-lookup"><span data-stu-id="33275-159">See also</span></span>

- [<span data-ttu-id="33275-160">방법: IIS에서 WCF 서비스 호스팅</span><span class="sxs-lookup"><span data-stu-id="33275-160">How to: Host a WCF Service in IIS</span></span>](../feature-details/how-to-host-a-wcf-service-in-iis.md)
