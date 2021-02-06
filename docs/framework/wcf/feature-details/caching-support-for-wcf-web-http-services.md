---
description: '자세한 정보: WCF 웹 HTTP 서비스에 대 한 캐싱 지원'
title: WCF 웹 HTTP 서비스에 대한 캐싱 지원
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: a1f7351566c06010ed70093a1cab3697ae0e9356
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99643490"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="f5607-103">WCF 웹 HTTP 서비스에 대한 캐싱 지원</span><span class="sxs-lookup"><span data-stu-id="f5607-103">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="f5607-104">WCF 웹 HTTP 서비스의 ASP.NET에서 이미 사용할 수 있는 선언적 캐싱 메커니즘을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-104">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="f5607-105">이렇게 하면 WCF 웹 HTTP 서비스 작업의 응답을 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-105">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="f5607-106">사용자가 캐시용으로 구성된 서비스에 HTTP GET을 보내면 ASP.NET이 캐시된 응답을 다시 보내고 서비스 메서드가 호출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-106">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="f5607-107">캐시가 만료되면 다음에 사용자가 HTTP GET을 보낼 때 서비스 메서드가 호출되고 응답이 다시 한 번 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-107">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="f5607-108">ASP.NET 캐싱에 대 한 자세한 내용은 [ASP.NET 캐싱 개요](/previous-versions/aspnet/ms178597(v=vs.100))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5607-108">For more information about ASP.NET caching, see [ASP.NET Caching Overview](/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="f5607-109">기본 웹 HTTP 서비스 캐싱</span><span class="sxs-lookup"><span data-stu-id="f5607-109">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="f5607-110">웹 HTTP 서비스 캐싱을 사용 하도록 설정 하려면 먼저를 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> 서비스 설정에 또는로 적용 하 여 ASP.NET 호환성을 사용 하도록 설정 해야 합니다 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required> .</span><span class="sxs-lookup"><span data-stu-id="f5607-110">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="f5607-111">.NET Framework 4에서는 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 캐시 프로필 이름을 지정할 수 있는 라는 새 특성을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-111">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="f5607-112">이 특성은 서비스 작업에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-112">This attribute is applied to a service operation.</span></span> <span data-ttu-id="f5607-113">다음 예제에서는 서비스에 <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>를 적용하여 ASP.NET 호환성을 사용하도록 설정하고 `GetCustomer` 작업을 캐시용으로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-113">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="f5607-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 특성은 사용할 캐시 설정이 들어 있는 캐시 프로필을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract]
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
<span data-ttu-id="f5607-115">또한 다음 예제와 같이 Web.config 파일에서 ASP.NET 호환 모드를 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-115">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="f5607-116">ASP.NET 호환성 모드가 사용되도록 설정되어 있지 않은 경우 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>를 사용하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-116">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="f5607-117"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>에 지정된 캐시 프로필 이름은 Web.config 구성 파일에 추가되는 캐시 프로필을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-117">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="f5607-118">캐시 프로필은 `outputCacheSetting` 다음 구성 예제에 표시 된 것 처럼 <> 요소에서로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-118">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="f5607-119">이 요소는 ASP.NET 애플리케이션에서 사용할 수 있는 구성 요소와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-119">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="f5607-120">ASP.NET cache 프로필에 대 한 자세한 내용은을 참조 하십시오 <xref:System.Web.Configuration.OutputCacheProfile> .</span><span class="sxs-lookup"><span data-stu-id="f5607-120">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="f5607-121">웹 HTTP 서비스의 경우 캐시 프로필에서 가장 중요한 특성이 `cacheDuration` 및 `varyByParam`입니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-121">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="f5607-122">두 특성 모두 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-122">Both of these attributes are required.</span></span> <span data-ttu-id="f5607-123">`cacheDuration`은 응답이 캐시되어야 하는 기간(초)을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-123">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="f5607-124">`varyByParam`에서는 응답을 캐시하는 데 사용하는 쿼리 문자열 매개 변수를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-124">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="f5607-125">여러 쿼리 문자열 매개 변수 값을 사용하여 수행한 모든 요청은 개별적으로 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-125">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="f5607-126">예를 들어,에 대 한 초기 요청이 이루어지면 `http://MyServer/MyHttpService/MyOperation?param=10` 동일한 URI를 사용 하 여 수행 된 모든 후속 요청이 캐시 된 응답을 반환 합니다 (캐시 기간이 경과 하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="f5607-126">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="f5607-127">동일하지만 쿼리 문자열 매개 변수 값이 다른 유사한 요청에 대한 응답은 개별적으로 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-127">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="f5607-128">이 개별 캐시 동작을 사용하지 않으려면 `varyByParam`을 "none"으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-128">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="f5607-129">SQL 캐시 종속성</span><span class="sxs-lookup"><span data-stu-id="f5607-129">SQL Cache Dependency</span></span>  

  <span data-ttu-id="f5607-130">웹 HTTP 서비스 응답도 SQL 캐시 종속성을 사용하여 캐시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-130">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="f5607-131">WCF 웹 HTTP 서비스에서 SQL 데이터베이스에 저장된 데이터를 사용하는 경우 이 서비스의 응답을 캐시하고 SQL 데이터베이스 테이블의 데이터가 변경되면 캐시된 응답을 무효화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-131">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="f5607-132">이 동작은 Web.config 파일에서 완전히 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-132">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="f5607-133">먼저 <> 요소에서 연결 문자열을 정의 `connectionStrings` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-133">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="f5607-134">그런 다음 `caching` `system.web` 다음 구성 예제에 표시 된 것 처럼 <> 요소 내의 <> 요소 내에서 SQL 캐시 종속성을 사용 하도록 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-134">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="f5607-135">여기서 SQL 캐시 종속성이 사용되도록 설정되었고 폴링 시간이 1000밀리초로 설정되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-135">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="f5607-136">폴링 시간이 만료될 때마다 데이터베이스 테이블이 업데이트되었는지 확인하는 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-136">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="f5607-137">변경 내용이 감지되면 캐시의 내용이 제거되고 다음에 서비스 작업이 호출될 때 새 응답이 캐시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-137">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="f5607-138"><`sqlCacheDependency`> 요소 내에서 다음 예제와 같이 데이터베이스를 추가 하 고 <> 요소 내에서 연결 문자열을 참조 `databases` 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-138">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="f5607-139">다음 예제와 같이 <> 요소 내에서 출력 캐시 설정을 구성 해야 합니다 `caching` .</span><span class="sxs-lookup"><span data-stu-id="f5607-139">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="f5607-140">여기서 캐시 기간은 60 초로 설정 되 `varyByParam` 고,는 none으로 설정 되며, `sqlDependency` 는 콜론으로 구분 된 데이터베이스 이름/테이블 쌍의 세미콜론으로 구분 된 목록으로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-140">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="f5607-141">`MyTable`의 데이터가 변경되면 서비스 작업의 캐시된 응답이 제거되고, 서비스 작업이 호출되면 새 응답이 생성 및 캐시된 후 클라이언트에 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-141">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f5607-142">ASP.NET에서 SQL database에 액세스 하려면 [ASP.NET SQL Server 등록 도구](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90))를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-142">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="f5607-143">또한 적절한 사용자 계정을 사용하여 데이터베이스와 테이블에 액세스할 수 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-143">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="f5607-144">자세한 내용은 [웹 응용 프로그램에서 SQL Server에 액세스](/previous-versions/aspnet/ht43wsex(v=vs.100))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f5607-144">For more information, see [Accessing SQL Server from a Web Application](/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="f5607-145">조건부 HTTP GET 기반 캐싱</span><span class="sxs-lookup"><span data-stu-id="f5607-145">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="f5607-146">웹 HTTP 시나리오에서 조건부 HTTP GET은 [Http 사양](https://www.w3.org/Protocols/rfc2616/rfc2616.html)에 설명 된 대로 지능형 http 캐싱을 구현 하기 위해 서비스에서 자주 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-146">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="f5607-147">이렇게 하려면 서비스가 HTTP 응답에서 ETag 헤더의 값을 설정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-147">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="f5607-148">HTTP 요청에 있는 If-None-Match 헤더를 검사하여 지정된 ETag가 현재 ETag와 일치하는지 여부도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-148">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="f5607-149">GET 및 HEAD 요청의 경우 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A>는 ETag 값을 가져와서 요청의 If-None-Match 헤더와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-149">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="f5607-150">헤더가 있고 일치 하는 경우 <xref:System.ServiceModel.Web.WebFaultException> HTTP 상태 코드 304 (수정 되지 않음)가 있는이 throw 되 고 etag 헤더가 일치 하는 etag를 사용 하 여 응답에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-150">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="f5607-151"><xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 메서드의 한 오버로드는 마지막으로 수정한 날짜를 가져와서 요청의 If-Modified-Since 헤더와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-151">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="f5607-152">이 헤더가 있고 리소스가 수정되지 않은 경우 HTTP 상태 코드 304(수정 안 됨)와 함께 <xref:System.ServiceModel.Web.WebFaultException>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-152">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="f5607-153">PUT, POST 및 DELETE 요청의 경우 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A>는 리소스의 현재 ETag 값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-153">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="f5607-154">현재 ETag 값이 null 인 경우 메서드는 비-일치 헤더에 "\*" 값이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-154">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="f5607-155">현재 ETag 값이 기본값이 아니면 이 메서드는 현재 ETag 값을 요청의 If- Match 헤더와 비교합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-155">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="f5607-156">두 경우 모두 예상 헤더가 요청에 없거나 해당 값이 조건부 검사를 충족하지 못하면 이 메서드는 HTTP 상태 코드 412(사전 조건 실패)와 함께 <xref:System.ServiceModel.Web.WebFaultException>을 throw하고 응답의 ETag 헤더를 현재 ETag 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-156">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="f5607-157">`CheckConditional` 메서드와 <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> 메서드는 모두 HTTP 사양에 따라 응답 헤더에 설정된 ETag 값이 유효한 ETag인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-157">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="f5607-158">여기에는 이러한 ETag 값이 아직 없고 내부 큰따옴표 문자로 올바로 이스케이프되지 않는 경우 큰따옴표로 이러한 값을 묶는 작업이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-158">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="f5607-159">약한 ETag 비교는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-159">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="f5607-160">다음 예제에서는 이러한 메서드를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-160">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;

        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="f5607-161">보안 고려사항</span><span class="sxs-lookup"><span data-stu-id="f5607-161">Security Considerations</span></span>  

 <span data-ttu-id="f5607-162">응답이 캐시에서 제공될 때는 권한 부여가 수행되지 않으므로 권한 부여가 필요한 요청의 경우 응답이 캐시되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-162">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="f5607-163">이러한 응답을 캐시하면 보안이 심각하게 취약해집니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-163">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="f5607-164">일반적으로 권한 부여가 필요한 요청에서는 사용자별 데이터를 제공하므로 서버 쪽 캐싱도 효과적이지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-164">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="f5607-165">이러한 경우 클라이언트 쪽 캐싱을 사용하거나 캐싱을 전혀 사용하지 않는 것이 더 적절합니다.</span><span class="sxs-lookup"><span data-stu-id="f5607-165">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
