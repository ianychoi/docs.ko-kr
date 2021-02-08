---
description: '자세히 알아보기: System.web. 라우팅 통합'
title: System.Web.Routing 통합
ms.date: 03/30/2017
ms.assetid: 31fe2a4f-5c47-4e5d-8ee1-84c524609d41
ms.openlocfilehash: 8f396d5a3cad30f5cc67cb0cf44fad76a0bb54c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99793339"
---
# <a name="systemwebrouting-integration"></a><span data-ttu-id="cdecd-103">System.Web.Routing 통합</span><span class="sxs-lookup"><span data-stu-id="cdecd-103">System.Web.Routing Integration</span></span>

<span data-ttu-id="cdecd-104">IIS (인터넷 정보 서비스)에서 WCF (Windows Communication Foundation) 서비스를 호스트 하는 경우 가상 디렉터리에 .svc 파일을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-104">When hosting a Windows Communication Foundation (WCF) service in Internet Information Service (IIS) you place a .svc file in the virtual directory.</span></span> <span data-ttu-id="cdecd-105">이 .svc 파일은 사용할 서비스 호스트 팩터리와 함께 서비스를 구현하는 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-105">This .svc file specifies the service host factory to use as well as the class that implements the service.</span></span> <span data-ttu-id="cdecd-106">서비스에 대 한 요청을 만들 때 URI에 .svc 파일을 `http://contoso.com/EmployeeServce.svc` 지정 합니다 (예:).</span><span class="sxs-lookup"><span data-stu-id="cdecd-106">When making requests to the service you specify the .svc file in the URI, for example: `http://contoso.com/EmployeeServce.svc`.</span></span> <span data-ttu-id="cdecd-107">REST 서비스를 작성하는 프로그래머에게는 이러한 유형의 URI가 적합하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-107">For programmers writing REST services, this type of URI is not optimal.</span></span> <span data-ttu-id="cdecd-108">REST 서비스의 URI는 특정 리소스를 지정하며 일반적으로 확장명을 포함하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-108">URIs for REST services specify a specific resource and normally do not have any extensions.</span></span> <span data-ttu-id="cdecd-109"><xref:System.Web.Routing>통합 기능을 사용 하면 확장이 없는 uri에 응답 하는 WCF REST 서비스를 호스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-109">The <xref:System.Web.Routing> integration feature allows you to host a WCF REST service that responds to URIs without an extension.</span></span> <span data-ttu-id="cdecd-110">라우팅에 대 한 자세한 내용은 [ASP.NET 라우팅](/previous-versions/aspnet/cc668201(v=vs.100))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="cdecd-110">For more information about routing see [ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100)).</span></span>  
  
## <a name="using-systemwebrouting-integration"></a><span data-ttu-id="cdecd-111">System.Web.Routing 통합 사용</span><span class="sxs-lookup"><span data-stu-id="cdecd-111">Using System.Web.Routing Integration</span></span>  

 <span data-ttu-id="cdecd-112"><xref:System.Web.Routing> 통합 기능을 사용하려면 <xref:System.ServiceModel.Activation.ServiceRoute> 클래스를 사용하여 하나 이상의 경로를 만들어 Global.asax 파일의 <xref:System.Web.Routing.RouteTable>에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-112">To use the <xref:System.Web.Routing> integration feature, you use the <xref:System.ServiceModel.Activation.ServiceRoute> class to create one or more routes and add them to the <xref:System.Web.Routing.RouteTable> in a Global.asax file.</span></span> <span data-ttu-id="cdecd-113">이러한 경로는 서비스가 응답하는 상대 URI를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-113">These routes specify the relative URIs that the service responds to.</span></span> <span data-ttu-id="cdecd-114">다음 예제에 이 작업을 수행하는 방법이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-114">The following example shows how to do this.</span></span>  
  
```aspx-csharp  
<%@ Application Language="C#" %>  
<%@ Import Namespace="System.Web.Routing" %>  
<%@ Import Namespace="System.ServiceModel.Activation" %>  
<%@ Import Namespace="System.ServiceModel.Web " %>  
  
<script RunAt="server">  
    void Application_Start(object sender, EventArgs e)  
    {  
        RegisterRoutes(RouteTable.Routes);  
    }  
  
    private void RegisterRoutes(RouteCollection routes)  
    {  
        routes.Add(new ServiceRoute("Customers", new WebServiceHostFactory(), typeof(Service)));
   }  
</script>  
```  
  
 <span data-ttu-id="cdecd-115">그러면 Customers로 시작하는 상대 URI가 있는 모든 요청이 `Service` 서비스에 라우트됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-115">This routes all requests with a relative URI that begins with Customers to the `Service` service.</span></span>  
  
 <span data-ttu-id="cdecd-116">Web.config 파일에서는 다음 예제와 같이 `System.Web.Routing.UrlRoutingModule` 모듈을 설정하고, `runAllManagedModulesForAllRequests` 특성을 `true`로 설정하고, `UrlRoutingHandler` 요소에 `<system.webServer>` 처리기를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-116">In your Web.config file you must add the `System.Web.Routing.UrlRoutingModule` module, set the `runAllManagedModulesForAllRequests` attribute to `true`, and add the `UrlRoutingHandler` handler to the `<system.webServer>` element as shown in the following example.</span></span>  
  
```xml  
<system.webServer>  
      <modules runAllManagedModulesForAllRequests="true">  
        <add name="UrlRoutingModule" type="System.Web.Routing.UrlRoutingModule, System.Web, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a" />  
      </modules>  
      <handlers>  
        <add name="UrlRoutingHandler" preCondition="integratedMode" verb="*" path="UrlRouting.axd"/>  
      </handlers>  
    </system.webServer>  
```  
  
 <span data-ttu-id="cdecd-117">그러면 라우팅에 필요한 모듈과 처리기가 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-117">This loads a module and handler required for routing.</span></span> <span data-ttu-id="cdecd-118">자세한 내용은 [라우팅](routing.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="cdecd-118">For more information, see [Routing](routing.md).</span></span> <span data-ttu-id="cdecd-119">또한 다음 예제와 같이 `aspNetCompatibilityEnabled` 요소의 `true` 특성도 `<serviceHostingEnvironment>`로 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-119">You must also set the `aspNetCompatibilityEnabled` attribute to `true` in the `<serviceHostingEnvironment>` element as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
    <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        <!-- ... -->  
    </system.serviceModel>  
```  
  
 <span data-ttu-id="cdecd-120">서비스를 구현하는 클래스에서는 다음 예제와 같이 ASP.NET 호환성 요구 사항을 사용하도록 설정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="cdecd-120">The class that implements the service must enable ASP.NET compatibility requirements as shown in the following example.</span></span>  
  
```csharp
[ServiceContract]  
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]  
    public class Service  
    {  
        // ...  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="cdecd-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cdecd-121">See also</span></span>

- [<span data-ttu-id="cdecd-122">WCF 웹 HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="cdecd-122">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- <span data-ttu-id="cdecd-123">[ASP.NET 라우팅](/previous-versions/aspnet/cc668201(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="cdecd-123">[ASP.NET Routing](/previous-versions/aspnet/cc668201(v=vs.100))</span></span>
