---
description: '자세한 정보: WCF 웹 HTTP 프로그래밍 모델 개요'
title: WCF 웹 HTTP 프로그래밍 모델 개요
ms.date: 03/30/2017
ms.assetid: 381fdc3a-6e6c-4890-87fe-91cca6f4b476
ms.openlocfilehash: 3359b0018458256cb3436e0fb631ee5fa438521e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732880"
---
# <a name="wcf-web-http-programming-model-overview"></a><span data-ttu-id="8d6d0-103">WCF 웹 HTTP 프로그래밍 모델 개요</span><span class="sxs-lookup"><span data-stu-id="8d6d0-103">WCF Web HTTP Programming Model Overview</span></span>

<span data-ttu-id="8d6d0-104">WCF (Windows Communication Foundation) 웹 HTTP 프로그래밍 모델은 WCF를 사용 하 여 웹 HTTP 서비스를 빌드하는 데 필요한 기본 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-104">The Windows Communication Foundation (WCF) WEB HTTP programming model provides the basic elements required to build WEB HTTP services with WCF.</span></span> <span data-ttu-id="8d6d0-105">WCF 웹 HTTP 서비스는 웹 브라우저를 포함 하 여 가능한 광범위 한 클라이언트에서 액세스할 수 있도록 설계 되었으며 다음과 같은 고유한 요구 사항이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-105">WCF WEB HTTP services are designed to be accessed by the widest range of possible clients, including Web browsers and have the following unique requirements:</span></span>  
  
- <span data-ttu-id="8d6d0-106">Uri **및 Uri 처리** Uri는 웹 HTTP 서비스의 디자인에서 중앙 역할을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-106">**URIs and URI Processing** URIs play a central role in the design of WEB HTTP services.</span></span> <span data-ttu-id="8d6d0-107">WCF 웹 HTTP 프로그래밍 모델은 및 클래스를 사용 하 여 <xref:System.UriTemplate> <xref:System.UriTemplateTable> URI 처리 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-107">The WCF WEB HTTP programming model uses the <xref:System.UriTemplate> and <xref:System.UriTemplateTable> classes to provide URI processing capabilities.</span></span>  
  
- <span data-ttu-id="8d6d0-108">**GET 및 POST 작업 지원** 웹 HTTP 서비스는 데이터 수정 및 원격 호출에 대 한 다양 한 호출 동사 뿐만 아니라 데이터 검색에 GET 동사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-108">**Support for GET and POST operations** WEB HTTP services make use of the GET verb for data retrieval, in addition to various invoke verbs for data modification and remote invocation.</span></span> <span data-ttu-id="8d6d0-109">WCF 웹 HTTP 프로그래밍 모델은 및를 사용 하 여 <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> PUT, POST, DELETE 등의 GET 및 다른 HTTP 동사 둘 다에 서비스 작업을 연결 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-109">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> to associate service operations with both GET and other HTTP verbs like PUT, POST, and DELETE.</span></span>  
  
- <span data-ttu-id="8d6d0-110">**여러 데이터 형식** 웹 스타일 서비스는 SOAP 메시지 외에도 여러 종류의 데이터를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-110">**Multiple data formats** Web-style services process many kinds of data in addition to SOAP messages.</span></span> <span data-ttu-id="8d6d0-111">WCF 웹 HTTP 프로그래밍 모델은 및를 사용 하 여 <xref:System.ServiceModel.WebHttpBinding> <xref:System.ServiceModel.Description.WebHttpBehavior> XML 문서, JSON 데이터 개체 및 이미지, 비디오 파일, 일반 텍스트 등의 이진 콘텐츠 스트림을 비롯 한 다양 한 데이터 형식을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-111">The WCF WEB HTTP programming model uses the <xref:System.ServiceModel.WebHttpBinding> and <xref:System.ServiceModel.Description.WebHttpBehavior> to support many different data formats including XML documents, JSON data object, and streams of binary content such as images, video files, or plain text.</span></span>  
  
 <span data-ttu-id="8d6d0-112">WCF 웹 HTTP 프로그래밍 모델은 웹 HTTP 서비스, AJAX 및 JSON 서비스 및 배포 (ATOM/RSS) 피드가 포함 된 웹 스타일 시나리오를 포함 하도록 WCF의 범위를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-112">The WCF WEB HTTP programming model extends the reach of WCF to cover Web-style scenarios that include WEB HTTP services, AJAX and JSON services, and Syndication (ATOM/RSS) feeds.</span></span> <span data-ttu-id="8d6d0-113">AJAX 및 JSON 서비스에 대 한 자세한 내용은 [Ajax 통합 및 Json 지원](ajax-integration-and-json-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-113">For more information about AJAX and JSON services, see [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span> <span data-ttu-id="8d6d0-114">배포에 대 한 자세한 내용은 [WCF 배포 개요](wcf-syndication-overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-114">For more information about Syndication, see [WCF Syndication Overview](wcf-syndication-overview.md).</span></span>  
  
 <span data-ttu-id="8d6d0-115">WEB HTTP 서비스에서 반환될 수 있는 데이터 형식에 대한 추가 제한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-115">There are no extra restrictions on the types of data that can be returned from a WEB HTTP service.</span></span> <span data-ttu-id="8d6d0-116">모든 직렬화 가능 형식이 WEB HTTP 서비스 작업에서 반환될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-116">Any serializable type can be returned from an WEB HTTP service operation.</span></span> <span data-ttu-id="8d6d0-117">웹 브라우저가 WEB HTTP 서비스 작업을 호출할 수 있기 때문에 URL에 지정할 수 있는 데이터 형식에 대한 제한이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-117">Because WEB HTTP service operations can be invoke by a web browser there is a limitation on what data types can be specified in a URL.</span></span> <span data-ttu-id="8d6d0-118">기본적으로 지원 되는 형식에 대 한 자세한 내용은 아래의 **UriTemplate 쿼리 문자열 매개 변수 및 url** 섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-118">For more information on what types are supported by default see the **UriTemplate Query String Parameters and URLs** section below.</span></span> <span data-ttu-id="8d6d0-119">URL에 지정된 매개 변수를 실제 매개 변수 형식으로 변환하는 방법을 지정하는 고유한 T:System.ServiceModel.Dispatcher.QueryStringConverter 구현을 제공하여 기본 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-119">The default behavior can be changed by providing your own T:System.ServiceModel.Dispatcher.QueryStringConverter implementation which specifies how to convert the parameters specified in a URL to the actual parameter type.</span></span> <span data-ttu-id="8d6d0-120">자세한 내용은 <xref:System.ServiceModel.Dispatcher.QueryStringConverter>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-120">For more information, see <xref:System.ServiceModel.Dispatcher.QueryStringConverter></span></span>  
  
> [!CAUTION]
> <span data-ttu-id="8d6d0-121">WCF 웹 HTTP 프로그래밍 모델을 사용 하 여 작성 된 서비스는 SOAP 메시지를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-121">Services written with the WCF WEB HTTP programming model do not use SOAP messages.</span></span> <span data-ttu-id="8d6d0-122">SOAP는 사용 되지 않으므로 WCF에서 제공 하는 보안 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-122">Because SOAP is not used, the security features provided by WCF cannot be used.</span></span> <span data-ttu-id="8d6d0-123">그러나 HTTPS를 사용하여 서비스를 호스트하면 전송 기반 보안을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-123">You can, however use transport-based security by hosting your service with HTTPS.</span></span> <span data-ttu-id="8d6d0-124">WCF 보안에 대 한 자세한 내용은 [보안 개요](security-overview.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-124">For more information about WCF security, see [Security Overview](security-overview.md)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="8d6d0-125">IIS의 WebDAV 확장을 설치하면 WebDAV 확장에서 모든 PUT 요청을 처리하려고 하므로 WEB HTTP 서비스에서 HTTP 405 오류를 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-125">Installing the WebDAV extension for IIS can cause Web HTTP services to return an HTTP 405 error as the WebDAV extension attempts to handle all PUT requests.</span></span> <span data-ttu-id="8d6d0-126">이 문제를 해결하려면 WebDAV 확장을 제거하거나 웹 사이트에 대해 WebDAV 확장을 사용하지 않도록 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-126">To work around this issue you can uninstall the WebDAV extension or disable the WebDAV extension for your web site.</span></span> <span data-ttu-id="8d6d0-127">자세한 내용은 [IIS 및 WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-127">For more information, see [IIS and WebDav](https://learn.iis.net/page.aspx/357/webdav-for-iis-70/)</span></span>  
  
## <a name="uri-processing-with-uritemplate-and-uritemplatetable"></a><span data-ttu-id="8d6d0-128">UriTemplate 및 UriTemplateTable을 사용한 URI 처리</span><span class="sxs-lookup"><span data-stu-id="8d6d0-128">URI Processing with UriTemplate and UriTemplateTable</span></span>  

 <span data-ttu-id="8d6d0-129">URI 템플릿은 구조적으로 비슷한 아주 많은 URI 집합을 나타내기 위한 효율적인 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-129">URI templates provide an efficient syntax for expressing large sets of structurally similar URIs.</span></span> <span data-ttu-id="8d6d0-130">예를 들면 다음 템플릿은 중간 세그먼트 값에 관계없이 "a"로 시작해서 "c"로 끝나는 세 개의 세그먼트로 구성된 URI 집합(a/{segment}/c)을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-130">For example, the following template expresses the set of all three-segment URIs that begin with "a" and end with "c" without regard to the value of the intermediate segment: a/{segment}/c</span></span>  
  
 <span data-ttu-id="8d6d0-131">이 템플릿에서는 다음과 같은 URI를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-131">This template describes URIs like the following:</span></span>  
  
- <span data-ttu-id="8d6d0-132">a/x/c</span><span class="sxs-lookup"><span data-stu-id="8d6d0-132">a/x/c</span></span>  
  
- <span data-ttu-id="8d6d0-133">a/y/c</span><span class="sxs-lookup"><span data-stu-id="8d6d0-133">a/y/c</span></span>  
  
- <span data-ttu-id="8d6d0-134">a/z/c</span><span class="sxs-lookup"><span data-stu-id="8d6d0-134">a/z/c</span></span>  
  
- <span data-ttu-id="8d6d0-135">등</span><span class="sxs-lookup"><span data-stu-id="8d6d0-135">and so on.</span></span>  
  
 <span data-ttu-id="8d6d0-136">이 템플릿에서 중괄호 표기법("{segment}")은 리터럴 값 대신 변수 세그먼트를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-136">In this template, the curly brace notation ("{segment}") indicates a variable segment instead of a literal value.</span></span>  
  
 <span data-ttu-id="8d6d0-137">.NET Framework는 <xref:System.UriTemplate>이라는 URI 템플릿으로 작업하기 위한 API를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-137">.NET Framework provides an API for working with URI templates called <xref:System.UriTemplate>.</span></span> <span data-ttu-id="8d6d0-138">`UriTemplates`을 사용하여 다음 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-138">`UriTemplates` allow you to do the following:</span></span>  
  
- <span data-ttu-id="8d6d0-139">`Bind`매개 변수 집합을 사용 하 여 메서드 중 하나를 호출 하 여 템플릿과 일치 하는 *완전히 폐쇄형 URI* 를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-139">You can call one of the `Bind` methods with a set of parameters to produce a *fully-closed URI* that matches the template.</span></span> <span data-ttu-id="8d6d0-140">즉, URI 템플릿 내에 있는 변수는 모두 실제 값으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-140">This means all variables within the URI template are replaced with actual values.</span></span>  
  
- <span data-ttu-id="8d6d0-141">후보 URI로 `Match`()를 호출할 수 있으며, 후보 URI는 템플릿을 사용하여 후보 URI를 구성 부분으로 나누고 템플릿의 변수에 따라 레이블이 지정된 URI의 다른 부분이 포함된 사전을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-141">You can call `Match`() with a candidate URI, which uses a template to break up a candidate URI into its constituent parts and returns a dictionary that contains the different parts of the URI labeled according to the variables in the template.</span></span>  
  
- <span data-ttu-id="8d6d0-142">`Bind`() 및 `Match`()는 서로가 반대이므로, 사용자는 `Match`(`Bind`( x ))를 호출하고 시작한 환경으로 돌아갈 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-142">`Bind`() and `Match`() are inverses so that you can call `Match`( `Bind`( x ) ) and come back with the same environment you started with.</span></span>  
  
 <span data-ttu-id="8d6d0-143">대부분의 경우, 특히 URI를 기반으로 서비스 작업에 대한 요청을 디스패치해야 하는 서버에서는 포함된 각 템플릿을 독립적으로 처리할 수 있는 데이터 구조의 <xref:System.UriTemplate> 개체 집합을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-143">There are many times (especially on the server, where dispatching a request to a service operation based on the URI is necessary) that you want to keep track of a set of <xref:System.UriTemplate> objects in a data structure that can independently address each of the contained templates.</span></span> <span data-ttu-id="8d6d0-144"><xref:System.UriTemplateTable>은 URI 템플릿 집합을 나타내며 템플릿 집합과 후보 URI가 지정된 경우 가장 일치하는 항목을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-144"><xref:System.UriTemplateTable> represents a set of URI templates and selects the best match given a set of templates and a candidate URI.</span></span> <span data-ttu-id="8d6d0-145">이는 특정 네트워킹 스택 (WCF 포함)과 관련이 없으므로 필요할 때마다 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-145">This is not affiliated with any particular networking stack (WCF included) so you can use it wherever necessary.</span></span>  
  
 <span data-ttu-id="8d6d0-146">WCF 서비스 모델은 <xref:System.UriTemplate> 및 <xref:System.UriTemplateTable>을 사용하여, <xref:System.UriTemplate>에서 설명한 URI 집합과 서비스 작업을 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-146">The WCF Service Model makes use of <xref:System.UriTemplate> and <xref:System.UriTemplateTable> to associate service operations with a set of URIs described by a <xref:System.UriTemplate>.</span></span> <span data-ttu-id="8d6d0-147">서비스 작업은 <xref:System.UriTemplate> 또는 <xref:System.ServiceModel.Web.WebGetAttribute>를 사용하여 <xref:System.ServiceModel.Web.WebInvokeAttribute>과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-147">A service operation is associated with a <xref:System.UriTemplate>, using either the <xref:System.ServiceModel.Web.WebGetAttribute> or the <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="8d6d0-148">및에 대 한 자세한 내용은 <xref:System.UriTemplate> <xref:System.UriTemplateTable> [UriTemplate 및 UriTemplateTable](uritemplate-and-uritemplatetable.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-148">For more information about <xref:System.UriTemplate> and <xref:System.UriTemplateTable>, see [UriTemplate and UriTemplateTable](uritemplate-and-uritemplatetable.md)</span></span>  
  
## <a name="webget-and-webinvoke-attributes"></a><span data-ttu-id="8d6d0-149">WebGet 및 WebInvoke 특성</span><span class="sxs-lookup"><span data-stu-id="8d6d0-149">WebGet and WebInvoke Attributes</span></span>  

 <span data-ttu-id="8d6d0-150">WCF 웹 HTTP 서비스는 다양 한 호출 동사 (예: HTTP POST, PUT 및 DELETE) 뿐 아니라 검색 동사 (예: HTTP GET)를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-150">WCF WEB HTTP services make use of retrieval verbs (for example HTTP GET) in addition to various invoke verbs (for example HTTP POST, PUT, and DELETE).</span></span> <span data-ttu-id="8d6d0-151">WCF 웹 HTTP 프로그래밍 모델을 사용 하면 서비스 개발자가 URI 템플릿과 및를 사용 하 여 서비스 작업과 연결 된 동사를 모두 제어할 수 있습니다 <xref:System.ServiceModel.Web.WebGetAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> .</span><span class="sxs-lookup"><span data-stu-id="8d6d0-151">The WCF WEB HTTP programming model allows service developers to control the both the URI template and verb associated with their service operations with the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute>.</span></span> <span data-ttu-id="8d6d0-152"><xref:System.ServiceModel.Web.WebGetAttribute> 및 <xref:System.ServiceModel.Web.WebInvokeAttribute>를 사용하면 개별 작업이 URI 및 이러한 URI와 관련된 HTTP 메서드에 바인딩되는 방법을 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-152">The <xref:System.ServiceModel.Web.WebGetAttribute> and the <xref:System.ServiceModel.Web.WebInvokeAttribute> allow you to control how individual operations get bound to URIs and the HTTP methods associated with those URIs.</span></span> <span data-ttu-id="8d6d0-153">예를 들어 다음 코드에 <xref:System.ServiceModel.Web.WebGetAttribute> 및 <xref:System.ServiceModel.Web.WebInvokeAttribute>를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-153">For example, adding <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> in the following code.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It"  
  
  [WebGet]  
  Customer GetCustomer():  
  
  //"Do It"  
    [WebInvoke]  
  Customer UpdateCustomerName( string id,
                               string newName );  
}  
```  
  
 <span data-ttu-id="8d6d0-154">이전 코드를 통해 다음과 같은 HTTP 요청을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-154">The preceding code allows you to make the following HTTP requests.</span></span>  
  
 `GET /GetCustomer`  
  
 `POST /UpdateCustomerName`  
  
 <span data-ttu-id="8d6d0-155"><xref:System.ServiceModel.Web.WebInvokeAttribute>는 기본적으로 POST로 설정되지만 다른 동사에도 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-155"><xref:System.ServiceModel.Web.WebInvokeAttribute> defaults to POST but you can use it for other verbs too.</span></span>  
  
```csharp
[ServiceContract]  
interface ICustomer  
{  
  //"View It" -> HTTP GET  
    [WebGet( UriTemplate="customers/{id}" )]  
  Customer GetCustomer( string id ):  
  
  //"Do It" -> HTTP PUT  
  [WebInvoke( UriTemplate="customers/{id}", Method="PUT" )]  
  Customer UpdateCustomer( string id, Customer newCustomer );  
}  
```  
  
 <span data-ttu-id="8d6d0-156">WCF 웹 HTTP 프로그래밍 모델을 사용 하는 WCF 서비스의 전체 샘플을 보려면 [방법: 기본 Wcf 웹 Http 서비스 만들기](how-to-create-a-basic-wcf-web-http-service.md) 를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-156">To see a complete sample of a WCF service that uses the WCF WEB HTTP programming model, see [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md)</span></span>  
  
## <a name="uritemplate-query-string-parameters-and-urls"></a><span data-ttu-id="8d6d0-157">UriTemplate 쿼리 문자열 매개 변수 및 URL</span><span class="sxs-lookup"><span data-stu-id="8d6d0-157">UriTemplate Query String Parameters and URLs</span></span>  

 <span data-ttu-id="8d6d0-158">웹 스타일 서비스는 서비스 작업과 관련된 URL을 입력하여 웹 브라우저에서 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-158">Web-style services can be called from a Web browser by typing a URL that is associated with a service operation.</span></span> <span data-ttu-id="8d6d0-159">이러한 서비스 작업은 URL 내의 문자열 형식에 지정해야 하는 쿼리 문자열 매개 변수를 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-159">These service operations may take query string parameters that must be specified in a string form within the URL.</span></span> <span data-ttu-id="8d6d0-160">다음 표에서는 URL 내에서 전달할 수 있는 형식과 사용된 형식을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-160">The following table shows the types that can be passed within a URL and the format used.</span></span>  
  
|<span data-ttu-id="8d6d0-161">형식</span><span class="sxs-lookup"><span data-stu-id="8d6d0-161">Type</span></span>|<span data-ttu-id="8d6d0-162">서식</span><span class="sxs-lookup"><span data-stu-id="8d6d0-162">Format</span></span>|  
|----------|------------|  
|<xref:System.Byte>|<span data-ttu-id="8d6d0-163">0 ~ 255</span><span class="sxs-lookup"><span data-stu-id="8d6d0-163">0 - 255</span></span>|  
|<xref:System.SByte>|<span data-ttu-id="8d6d0-164">-128 - 127</span><span class="sxs-lookup"><span data-stu-id="8d6d0-164">-128 - 127</span></span>|  
|<xref:System.Int16>|<span data-ttu-id="8d6d0-165">-32768 - 32767</span><span class="sxs-lookup"><span data-stu-id="8d6d0-165">-32768 - 32767</span></span>|  
|<xref:System.Int32>|<span data-ttu-id="8d6d0-166">-2,147,483,648 - 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="8d6d0-166">-2,147,483,648 - 2,147,483,647</span></span>|  
|<xref:System.Int64>|<span data-ttu-id="8d6d0-167">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="8d6d0-167">-9,223,372,036,854,775,808 - 9,223,372,036,854,775,807</span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="8d6d0-168">0 - 65535</span><span class="sxs-lookup"><span data-stu-id="8d6d0-168">0 - 65535</span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="8d6d0-169">0 - 4,294,967,295</span><span class="sxs-lookup"><span data-stu-id="8d6d0-169">0 - 4,294,967,295</span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="8d6d0-170">0 - 18,446,744,073,709,551,615</span><span class="sxs-lookup"><span data-stu-id="8d6d0-170">0 - 18,446,744,073,709,551,615</span></span>|  
|<xref:System.Single>|<span data-ttu-id="8d6d0-171">-3.402823e38 - 3.402823e38(지수 표기법이 필요하지 않음)</span><span class="sxs-lookup"><span data-stu-id="8d6d0-171">-3.402823e38 - 3.402823e38 (exponent notation is not required)</span></span>|  
|<xref:System.Double>|<span data-ttu-id="8d6d0-172">-1.79769313486232e308 - 1.79769313486232e308(지수 표기법이 필요하지 않음)</span><span class="sxs-lookup"><span data-stu-id="8d6d0-172">-1.79769313486232e308 - 1.79769313486232e308 (exponent notation is not required)</span></span>|  
|<xref:System.Char>|<span data-ttu-id="8d6d0-173">임의의 단일 문자</span><span class="sxs-lookup"><span data-stu-id="8d6d0-173">Any single character</span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="8d6d0-174">표준 표기법으로 나타낸 10진수(지수 없음)</span><span class="sxs-lookup"><span data-stu-id="8d6d0-174">Any decimal in standard notation (no exponent)</span></span>|  
|<xref:System.Boolean>|<span data-ttu-id="8d6d0-175">True 또는 False(대/소문자 구분 안 함)</span><span class="sxs-lookup"><span data-stu-id="8d6d0-175">True or False (case insensitive)</span></span>|  
|<xref:System.String>|<span data-ttu-id="8d6d0-176">모든 문자열(null 문자열이 지원되지 않으며 이스케이프가 수행되지 않음)</span><span class="sxs-lookup"><span data-stu-id="8d6d0-176">Any string (null string is not supported and no escaping is done)</span></span>|  
|<xref:System.DateTime>|<span data-ttu-id="8d6d0-177">MM/DD/YYYY</span><span class="sxs-lookup"><span data-stu-id="8d6d0-177">MM/DD/YYYY</span></span><br /><br /> <span data-ttu-id="8d6d0-178">MM/DD/YYYY HH: MM: SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="8d6d0-178">MM/DD/YYYY HH:MM:SS [AM&#124;PM]</span></span><br /><br /> <span data-ttu-id="8d6d0-179">월/일/연도</span><span class="sxs-lookup"><span data-stu-id="8d6d0-179">Month Day Year</span></span><br /><br /> <span data-ttu-id="8d6d0-180">월 일 연도 HH: MM: SS [AM&#124;PM]</span><span class="sxs-lookup"><span data-stu-id="8d6d0-180">Month Day Year HH:MM:SS [AM&#124;PM]</span></span>|  
|<xref:System.TimeSpan>|<span data-ttu-id="8d6d0-181">DD.HH:MM:SS</span><span class="sxs-lookup"><span data-stu-id="8d6d0-181">DD.HH:MM:SS</span></span><br /><br /> <span data-ttu-id="8d6d0-182">여기서 DD = 일, HH = 시간, MM = 분, SS = 초입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-182">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<xref:System.Guid>|<span data-ttu-id="8d6d0-183">GUID, 예:</span><span class="sxs-lookup"><span data-stu-id="8d6d0-183">A GUID, for example:</span></span><br /><br /> <span data-ttu-id="8d6d0-184">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span><span class="sxs-lookup"><span data-stu-id="8d6d0-184">936DA01F-9ABD-4d9d-80C7-02AF85C822A8</span></span>|  
|<xref:System.DateTimeOffset>|<span data-ttu-id="8d6d0-185">MM/DD/YYYY HH:MM:SS MM:SS</span><span class="sxs-lookup"><span data-stu-id="8d6d0-185">MM/DD/YYYY HH:MM:SS MM:SS</span></span><br /><br /> <span data-ttu-id="8d6d0-186">여기서 DD = 일, HH = 시간, MM = 분, SS = 초입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-186">Where DD = Days, HH = Hours, MM = minutes, SS = Seconds</span></span>|  
|<span data-ttu-id="8d6d0-187">열거형</span><span class="sxs-lookup"><span data-stu-id="8d6d0-187">Enumerations</span></span>|<span data-ttu-id="8d6d0-188">다음 코드에서처럼 열거형을 정의하는 예제의 열거형 값입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-188">The enumeration value for example, which defines the enumeration as shown in the following code.</span></span><br /><br /> `public enum Days{ Sunday, Monday, Tuesday, Wednesday, Thursday, Friday, Saturday };`<br /><br /> <span data-ttu-id="8d6d0-189">개별 열거형 값 또는 해당 정수 값은 쿼리 문자열에 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-189">Any of the individual enumeration values (or their corresponding integer values) may be specified in the query string.</span></span>|  
|<span data-ttu-id="8d6d0-190">문자열 표현과 형식을 서로 변환할 수 있는 `TypeConverterAttribute`가 있는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-190">Types that have a `TypeConverterAttribute` that can convert the type to and from a string representation.</span></span>|<span data-ttu-id="8d6d0-191">형식 변환기에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-191">Depends on the Type Converter.</span></span>|  
  
## <a name="formats-and-the-wcf-web-http-programming-model"></a><span data-ttu-id="8d6d0-192">형식 및 WCF WEB HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="8d6d0-192">Formats and the WCF WEB HTTP Programming Model</span></span>  

 <span data-ttu-id="8d6d0-193">WCF WEB HTTP 프로그래밍 모델에는 다양 한 데이터 형식으로 작업할 수 있는 새로운 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-193">The WCF WEB HTTP programming model has new features to work with many different data formats.</span></span> <span data-ttu-id="8d6d0-194"><xref:System.ServiceModel.WebHttpBinding>은 바인딩 계층에서 다음과 같은 여러 종류의 데이터를 읽고 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-194">At the binding layer, the <xref:System.ServiceModel.WebHttpBinding> can read and write the following different kinds of data:</span></span>  
  
- <span data-ttu-id="8d6d0-195">XML</span><span class="sxs-lookup"><span data-stu-id="8d6d0-195">XML</span></span>  
  
- <span data-ttu-id="8d6d0-196">JSON</span><span class="sxs-lookup"><span data-stu-id="8d6d0-196">JSON</span></span>  
  
- <span data-ttu-id="8d6d0-197">불투명 이진 스트림</span><span class="sxs-lookup"><span data-stu-id="8d6d0-197">Opaque binary streams</span></span>  
  
 <span data-ttu-id="8d6d0-198">즉, WCF 웹 HTTP 프로그래밍 모델은 모든 형식의 데이터를 처리할 수 있지만에 대해 프로그래밍할 수 있습니다 <xref:System.IO.Stream> .</span><span class="sxs-lookup"><span data-stu-id="8d6d0-198">This means the WCF WEB HTTP programming model can handle any type of data but, you may be programming against <xref:System.IO.Stream>.</span></span>  
  
 <span data-ttu-id="8d6d0-199">.NET Framework 3.5는 JSON 데이터 (AJAX) 뿐만 아니라 배포 피드 (ATOM 및 RSS 포함)를 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-199">.NET Framework 3.5 provides support for JSON data (AJAX) as well as Syndication feeds (including ATOM and RSS).</span></span> <span data-ttu-id="8d6d0-200">이러한 기능에 대 한 자세한 내용은 [Wcf 웹 HTTP 형식 지정](wcf-web-http-formatting.md), [wcf 배포 개요](wcf-syndication-overview.md)및 [AJAX 통합 및 JSON 지원](ajax-integration-and-json-support.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-200">For more information about these features, see [WCF Web HTTP Formatting](wcf-web-http-formatting.md), [WCF Syndication Overview](wcf-syndication-overview.md), and [AJAX Integration and JSON Support](ajax-integration-and-json-support.md).</span></span>  
  
## <a name="wcf-web-http-programming-model-and-security"></a><span data-ttu-id="8d6d0-201">WCF WEB HTTP 프로그래밍 모델 및 보안</span><span class="sxs-lookup"><span data-stu-id="8d6d0-201">WCF WEB HTTP Programming Model and Security</span></span>  

<span data-ttu-id="8d6d0-202">WCF 웹 HTTP 프로그래밍 모델은 WS-\* 프로토콜을 지원 하지 않으므로 WCF 웹 HTTP 서비스를 보호 하는 유일한 방법은 SSL을 사용 하 여 HTTPS를 통해 서비스를 노출 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-202">Because the WCF WEB HTTP programming model does not support the WS-\* protocols, the only way to secure a WCF WEB HTTP service is to expose the service over HTTPS using SSL.</span></span> <span data-ttu-id="8d6d0-203">IIS 7.0를 사용 하 여 SSL을 설정 하는 방법에 대 한 자세한 내용은 [iis에서 ssl을 구현 하는 방법](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-203">For more information about setting up SSL with IIS 7.0, see [How to implement SSL in IIS](https://support.microsoft.com/help/299875/how-to-implement-ssl-in-iis).</span></span>
  
## <a name="troubleshooting-the-wcf-web-http-programming-model"></a><span data-ttu-id="8d6d0-204">WCF WEB HTTP 프로그래밍 모델 문제 해결</span><span class="sxs-lookup"><span data-stu-id="8d6d0-204">Troubleshooting the WCF WEB HTTP Programming Model</span></span>  

 <span data-ttu-id="8d6d0-205"><xref:System.ServiceModel.Channels.ChannelFactoryBase%601>을 사용하는 WCF WEB HTTP 서비스를 호출해 채널을 만들 때 <xref:System.ServiceModel.Description.WebHttpBehavior>는 다른 <xref:System.ServiceModel.EndpointAddress>가 <xref:System.ServiceModel.EndpointAddress>로 전달되어도 구성 파일에 설정된 <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8d6d0-205">When calling WCF WEB HTTP services using a <xref:System.ServiceModel.Channels.ChannelFactoryBase%601> to create a channel, the <xref:System.ServiceModel.Description.WebHttpBehavior> uses the <xref:System.ServiceModel.EndpointAddress> set in the configuration file even if a different <xref:System.ServiceModel.EndpointAddress> is passed to the <xref:System.ServiceModel.Channels.ChannelFactoryBase%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d6d0-206">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8d6d0-206">See also</span></span>

- [<span data-ttu-id="8d6d0-207">WCF 배포</span><span class="sxs-lookup"><span data-stu-id="8d6d0-207">WCF Syndication</span></span>](wcf-syndication.md)
- [<span data-ttu-id="8d6d0-208">WCF 웹 HTTP 프로그래밍 개체 모델</span><span class="sxs-lookup"><span data-stu-id="8d6d0-208">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="8d6d0-209">WCF 웹 HTTP 프로그래밍 모델</span><span class="sxs-lookup"><span data-stu-id="8d6d0-209">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
