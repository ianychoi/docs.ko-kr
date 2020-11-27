---
title: 독립형 진단 피드 샘플
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: b4c3613656e0aec42c0d3f5cd7cde0af6540a69a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268250"
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="89cc7-102">독립형 진단 피드 샘플</span><span class="sxs-lookup"><span data-stu-id="89cc7-102">Stand-Alone Diagnostics Feed Sample</span></span>

<span data-ttu-id="89cc7-103">이 샘플에서는 Windows Communication Foundation (WCF)를 사용 하 여 배포 하기 위해 RSS/Atom 피드를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="89cc7-104">개체 모델의 기본 사항 및 Windows Communication Foundation (WCF) 서비스에서 설정 하는 방법을 보여 주는 기본적인 "Hello World" 프로그램입니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="89cc7-105">WCF는 배포 피드를 특수 데이터 형식을 반환 하는 서비스 작업으로 모델링 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> 합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="89cc7-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>의 인스턴스는 피드를 RSS 2.0 및 ATOM 1.0 형식으로 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="89cc7-107">다음 샘플 코드에서는 사용된 계약을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-107">The following sample code shows the contract used.</span></span>  
  
```csharp  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="89cc7-108">작업에는 `GetProcesses` <xref:System.ServiceModel.Web.WebGetAttribute> WCF가 서비스 작업에 HTTP GET 요청을 디스패치 하는 방법을 제어 하 고 전송 되는 메시지의 형식을 지정 하는 데 사용할 수 있는 특성으로 주석이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="89cc7-109">모든 WCF 서비스와 마찬가지로 배포 피드는 모든 관리 되는 응용 프로그램에서 자체 호스팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="89cc7-110">배포 서비스가 제대로 작동하려면 특정 바인딩(<xref:System.ServiceModel.WebHttpBinding>) 및 특정 엔드포인트 동작(<xref:System.ServiceModel.Description.WebHttpBehavior>)이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="89cc7-111">새 <xref:System.ServiceModel.Web.WebServiceHost> 클래스는 특정 구성 없이 이러한 엔드포인트를 만들기 위해 다음과 같이 편리한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```csharp  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="89cc7-112">또는 IIS에서 호스트되는 .svc 파일 내에서 <xref:System.ServiceModel.Activation.WebServiceHostFactory>를 사용하여 동일한 기능을 제공할 수 있습니다(이 방법은 샘플 코드에서 설명하지 않음).</span><span class="sxs-lookup"><span data-stu-id="89cc7-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```xml
<% @ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>
```
  
 <span data-ttu-id="89cc7-113">이 서비스는 표준 HTTP GET을 사용하여 요청을 받기 때문에 RSS 또는 ATOM 인식 클라이언트를 사용하여 서비스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="89cc7-114">예를 들어 `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` RSS 인식 브라우저에서 또는으로 이동 하 여이 서비스의 출력을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-114">For example, you can view the output of this service by navigating to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` in an RSS-aware browser.</span></span>
  
 <span data-ttu-id="89cc7-115">또한 [WCF 배포 개체 모델이 Atom 및 RSS에 매핑되는 방법을](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) 사용 하 여 배포 된 데이터를 읽고 명령적 코드를 사용 하 여 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```csharp
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",
    new XmlReaderSettings()
    {
        //MaxCharactersInDocument can be used to control the maximum amount of data
        //read from the reader and helps prevent OutOfMemoryException
        MaxCharactersInDocument = 1024 * 64
    } );

SyndicationFeed feed = SyndicationFeed.Load(reader);

foreach (SyndicationItem i in feed.Items)
{
    XmlSyndicationContent content = i.Content as XmlSyndicationContent;
    ProcessData pd = content.ReadContent<ProcessData>();

    Console.WriteLine(i.Title.Text);
    Console.WriteLine(pd.ToString());
}
```
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="89cc7-116">샘플 설정, 빌드 및 실행</span><span class="sxs-lookup"><span data-stu-id="89cc7-116">Set up, build, and run the sample</span></span>
  
1. <span data-ttu-id="89cc7-117">[Windows Communication Foundation 샘플에 대 한 일회성 설치 절차](one-time-setup-procedure-for-the-wcf-samples.md)의 지침 설정에 설명 된 대로 컴퓨터에서 HTTP 및 HTTPS에 대 한 올바른 주소 등록 권한이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="89cc7-118">솔루션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-118">Build the solution.</span></span>

3. <span data-ttu-id="89cc7-119">콘솔 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-119">Run the console application.</span></span>

4. <span data-ttu-id="89cc7-120">콘솔 응용 프로그램이 실행 되는 동안 `http://localhost:8000/diagnostics/feed/?format=atom` `http://localhost:8000/diagnostics/feed/?format=rss` RSS 인식 브라우저로 이동 하거나 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-120">While the console application is running, navigate to `http://localhost:8000/diagnostics/feed/?format=atom` or `http://localhost:8000/diagnostics/feed/?format=rss` using an RSS-aware browser.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="89cc7-121">컴퓨터에 이 샘플이 이미 설치되어 있을 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="89cc7-122">계속하기 전에 다음(기본) 디렉터리를 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="89cc7-122">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="89cc7-123">이 디렉터리가 없는 경우 [.NET Framework 4에 대 한 Windows Communication Foundation (wcf) 및 Windows Workflow Foundation (WF) 샘플](https://www.microsoft.com/download/details.aspx?id=21459) 로 이동 하 여 모든 WINDOWS COMMUNICATION FOUNDATION (wcf) 및 샘플을 다운로드 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 합니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89cc7-124">이 샘플은 다음 디렉터리에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="89cc7-124">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`

## <a name="see-also"></a><span data-ttu-id="89cc7-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="89cc7-125">See also</span></span>

- [<span data-ttu-id="89cc7-126">WCF 웹 HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="89cc7-126">WCF Web HTTP Programming Model</span></span>](../feature-details/wcf-web-http-programming-model.md)
- [<span data-ttu-id="89cc7-127">WCF 배포</span><span class="sxs-lookup"><span data-stu-id="89cc7-127">WCF Syndication</span></span>](../feature-details/wcf-syndication.md)
