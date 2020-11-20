---
title: ASP.NET Core 호환성이 손상되는 변경
titleSuffix: ''
description: ASP.NET Core의 호환성이 손상되는 변경을 나열합니다.
ms.date: 11/03/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 6e8e35d01ea7ff91c45bf1febd822e8497b608f0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440491"
---
# <a name="aspnet-core-breaking-changes"></a><span data-ttu-id="59992-103">ASP.NET Core 호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="59992-103">ASP.NET Core breaking changes</span></span>

<span data-ttu-id="59992-104">ASP.NET Core는 .NET Core에서 사용되는 웹앱 개발 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="59992-105">특정 버전의 호환성이 손상되는 변경에 해당하는 다음 링크 중 하나를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="59992-106">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="59992-106">ASP.NET Core 5.0</span></span>](#aspnet-core-50)
* [<span data-ttu-id="59992-107">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="59992-107">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="59992-108">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="59992-108">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="59992-109">이 페이지에는 ASP.NET Core 3.0, 3.1 및 5.0의 다음과 같은 호환성이 손상되는 변경이 설명되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59992-109">The following breaking changes in ASP.NET Core 3.0, 3.1, and 5.0 are documented on this page:</span></span>

- [<span data-ttu-id="59992-110">사용되지 않는 위조 방지, CORS, 진단, MVC 및 라우팅 API가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-110">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="59992-111">인증: AzureAD.UI 및 AzureADB2C.UI API와 패키지는 사용되지 않는 것으로 표시됨</span><span class="sxs-lookup"><span data-stu-id="59992-111">Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete</span></span>](#authentication-azureadui-and-azureadb2cui-apis-and-packages-marked-obsolete)
- [<span data-ttu-id="59992-112">인증: Google + 사용 중단</span><span class="sxs-lookup"><span data-stu-id="59992-112">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="59992-113">인증: HttpContext.Authentication 인증 속성이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-113">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="59992-114">인증: Newtonsoft.json 형식이 대체됨</span><span class="sxs-lookup"><span data-stu-id="59992-114">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="59992-115">인증: OAuthHandler ExchangeCodeAsync 서명이 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-115">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="59992-116">권한 부여: AddAuthorization 오버로드가 다른 어셈블리로 이동됨</span><span class="sxs-lookup"><span data-stu-id="59992-116">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="59992-117">권한 부여: AuthorizationFilterContext.Filters에서 IAllowAnonymous 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-117">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="59992-118">권한 부여: IAuthorizationPolicyProvider 구현에는 새 메서드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-118">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="59992-119">권한 부여: 엔드포인트 라우팅의 리소스가 HttpContext임</span><span class="sxs-lookup"><span data-stu-id="59992-119">Authorization: Resource in endpoint routing is HttpContext</span></span>](#authorization-resource-in-endpoint-routing-is-httpcontext)
- [<span data-ttu-id="59992-120">Azure: Microsoft 접두사가 있는 Azure 통합 패키지가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-120">Azure: Microsoft-prefixed Azure integration packages removed</span></span>](#azure-microsoft-prefixed-azure-integration-packages-removed)
- [<span data-ttu-id="59992-121">ASP.NET 앱에서 BinaryFormatter serialization 메서드가 사용되지 않고 금지됨</span><span class="sxs-lookup"><span data-stu-id="59992-121">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps)
- [<span data-ttu-id="59992-122">Blazor: 컴파일 시간에 구성 요소에서 중요하지 않은 공백을 자름</span><span class="sxs-lookup"><span data-stu-id="59992-122">Blazor: Insignificant whitespace trimmed from components at compile time</span></span>](#blazor-insignificant-whitespace-trimmed-from-components-at-compile-time)
- [<span data-ttu-id="59992-123">Blazor: JSObjectReference 및 JSInProcessObjectReference 형식을 internal로 변경함</span><span class="sxs-lookup"><span data-stu-id="59992-123">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>](#blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal)
- [<span data-ttu-id="59992-124">Blazor: ProtectedBrowserStorage 기능을 공유 프레임워크로 이동함</span><span class="sxs-lookup"><span data-stu-id="59992-124">Blazor: ProtectedBrowserStorage feature moved to shared framework</span></span>](#blazor-protectedbrowserstorage-feature-moved-to-shared-framework)
- [<span data-ttu-id="59992-125">Blazor: RenderTreeFrame 읽기 전용 퍼블릭 필드가 속성이 됨</span><span class="sxs-lookup"><span data-stu-id="59992-125">Blazor: RenderTreeFrame readonly public fields have become properties</span></span>](#blazor-rendertreeframe-readonly-public-fields-have-become-properties)
- [<span data-ttu-id="59992-126">Blazor: NuGet 패키지의 대상 프레임워크가 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-126">Blazor: Target framework of NuGet packages changed</span></span>](#blazor-target-framework-of-nuget-packages-changed)
- [<span data-ttu-id="59992-127">Blazor: 업데이트된 브라우저 지원</span><span class="sxs-lookup"><span data-stu-id="59992-127">Blazor: Updated browser support</span></span>](#blazor-updated-browser-support)
- [<span data-ttu-id="59992-128">Blazor: 정적 웹 자산에 대한 유효성 검사 논리를 업데이트함</span><span class="sxs-lookup"><span data-stu-id="59992-128">Blazor: Updated validation logic for static web assets</span></span>](#blazor-updated-validation-logic-for-static-web-assets)
- [<span data-ttu-id="59992-129">캐싱: CompactOnMemoryPressure 속성이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-129">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="59992-130">캐싱: Microsoft.Extensions.Caching.SqlServer는 새 SqlClient 패키지를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-130">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="59992-131">캐싱: ResponseCaching “pubternal” 유형이 내부로 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-131">Caching: ResponseCaching "pubternal" types changed to internal</span></span>](#caching-responsecaching-pubternal-types-changed-to-internal)
- [<span data-ttu-id="59992-132">데이터 보호: DataProtection.Blobs에서 새로운 Azure Storage API 사용</span><span class="sxs-lookup"><span data-stu-id="59992-132">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [<span data-ttu-id="59992-133">확장: 일부 NuGet 패키지에 영향을 주는 패키지 참조 변경 내용</span><span class="sxs-lookup"><span data-stu-id="59992-133">Extensions: Package reference changes affecting some NuGet packages</span></span>](#extensions-package-reference-changes-affecting-some-nuget-packages)
- [<span data-ttu-id="59992-134">호스팅: Windows Hosting Bundle에서 AspNetCoreModule V1이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-134">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="59992-135">호스팅: 제네릭 호스트는 시작 생성자 주입을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-135">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="59992-136">호스팅: IIS Out of Process 앱에 대해 HTTPS 리디렉션 사용</span><span class="sxs-lookup"><span data-stu-id="59992-136">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="59992-137">호스팅: IHostingEnvironment 및 IApplicationLifetime 형식이 바뀜</span><span class="sxs-lookup"><span data-stu-id="59992-137">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="59992-138">호스팅: WebHostBuilder 종속성에서 제거되는 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="59992-138">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="59992-139">HTTP: Kestrel 및 IIS BadHttpRequestException 형식이 사용되지 않는 것으로 표시되고 대체됨</span><span class="sxs-lookup"><span data-stu-id="59992-139">HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced</span></span>](#http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="59992-140">HTTP: 브라우저 SameSite 변경 내용이 인증에 영향</span><span class="sxs-lookup"><span data-stu-id="59992-140">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="59992-141">HTTP: DefaultHttpContext 확장성이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-141">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="59992-142">HTTP: HeaderNames 필드가 정적 읽기 전용으로 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-142">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="59992-143">HTTP: IHttpClientFactory 로그 정수 상태 코드에서 생성된 HttpClient 인스턴스</span><span class="sxs-lookup"><span data-stu-id="59992-143">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>](#http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes)
- [<span data-ttu-id="59992-144">HTTP: 응답 본문 인프라 변경</span><span class="sxs-lookup"><span data-stu-id="59992-144">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="59992-145">HTTP: 일부 쿠키 SameSite 기본값이 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-145">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="59992-146">HTTP: 기본적으로 사용하지 않도록 설정된 동기 IO</span><span class="sxs-lookup"><span data-stu-id="59992-146">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="59992-147">HttpSys: 클라이언트 인증서 재협상을 기본적으로 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="59992-147">HttpSys: Client certificate renegotiation disabled by default</span></span>](#httpsys-client-certificate-renegotiation-disabled-by-default)
- [<span data-ttu-id="59992-148">ID: AddDefaultUI 메서드 오버로드가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-148">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="59992-149">ID: UI 부트스트랩 버전 변경</span><span class="sxs-lookup"><span data-stu-id="59992-149">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="59992-150">ID: SignInAsync는 인증되지 않은 ID에 대해 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-150">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="59992-151">ID: SignInManager 생성자는 새 매개 변수를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-151">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="59992-152">ID: UI는 정적 웹 자산 기능을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="59992-152">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="59992-153">IIS: UrlRewrite 미들웨어 쿼리 문자열이 유지됨</span><span class="sxs-lookup"><span data-stu-id="59992-153">IIS: UrlRewrite middleware query strings are preserved</span></span>](#iis-urlrewrite-middleware-query-strings-are-preserved)
- [<span data-ttu-id="59992-154">Kestrel: 런타임의 구성 변경 사항이 기본적으로 검색됨</span><span class="sxs-lookup"><span data-stu-id="59992-154">Kestrel: Configuration changes at run time detected by default</span></span>](#kestrel-configuration-changes-at-run-time-detected-by-default)
- [<span data-ttu-id="59992-155">Kestrel: 연결 어댑터가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-155">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="59992-156">Kestrel: 지원되는 기본 TLS 프로토콜 버전 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-156">Kestrel: Default supported TLS protocol versions changed</span></span>](#kestrel-default-supported-tls-protocol-versions-changed)
- [<span data-ttu-id="59992-157">Kestrel: 빈 HTTPS 어셈블리가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-157">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="59992-158">Kestrel: 호환되지 않는 Windows 버전에서 TLS를 통한 HTTP/2 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="59992-158">Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions</span></span>](#kestrel-http2-disabled-over-tls-on-incompatible-windows-versions)
- [<span data-ttu-id="59992-159">Kestrel: 사용되지 않는 것으로 표시된 Libuv 전송</span><span class="sxs-lookup"><span data-stu-id="59992-159">Kestrel: Libuv transport marked as obsolete</span></span>](#kestrel-libuv-transport-marked-as-obsolete)
- [<span data-ttu-id="59992-160">Kestrel: 요청 후행부 헤더가 새 컬렉션으로 이동됨</span><span class="sxs-lookup"><span data-stu-id="59992-160">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="59992-161">Kestrel: 전송 추상화 계층 변경</span><span class="sxs-lookup"><span data-stu-id="59992-161">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="59992-162">지역화: 사용되지 않음으로 표시된 API</span><span class="sxs-lookup"><span data-stu-id="59992-162">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="59992-163">지역화: “Pubternal” API가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-163">Localization: "Pubternal" APIs removed</span></span>](#localization-pubternal-apis-removed)
- [<span data-ttu-id="59992-164">지역화: 요청 지역화 미들웨어에서 사용되지 않는 생성자가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-164">Localization: Obsolete constructor removed in request localization middleware</span></span>](#localization-obsolete-constructor-removed-in-request-localization-middleware)
- [<span data-ttu-id="59992-165">지역화: ResourceManagerWithCultureStringLocalizer 클래스 및 WithCulture 인터페이스 멤버가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-165">Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed</span></span>](#localization-resourcemanagerwithculturestringlocalizer-class-and-withculture-interface-member-removed)
- [<span data-ttu-id="59992-166">로깅: DebugLogger 클래스를 내부적으로 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="59992-166">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="59992-167">미들웨어: 사용되지 않는 것으로 표시된 데이터베이스 오류 페이지</span><span class="sxs-lookup"><span data-stu-id="59992-167">Middleware: Database error page marked as obsolete</span></span>](#middleware-database-error-page-marked-as-obsolete)
- [<span data-ttu-id="59992-168">미들웨어: 처리기를 찾을 수 없는 경우 예외 처리기 미들웨어가 원래 예외를 throw함</span><span class="sxs-lookup"><span data-stu-id="59992-168">Middleware: Exception Handler Middleware throws original exception if handler not found</span></span>](#middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found)
- [<span data-ttu-id="59992-169">MVC: 컨트롤러 작업 비동기 접미사가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-169">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="59992-170">MVC: JsonResult를 Microsoft.AspNetCore.Mvc.Core로 이동</span><span class="sxs-lookup"><span data-stu-id="59992-170">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="59992-171">MVC: ObjectModelValidator가 ValidationVisitor.Validate의 새 오버로드 호출</span><span class="sxs-lookup"><span data-stu-id="59992-171">MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate</span></span>](#mvc-objectmodelvalidator-calls-a-new-overload-of-validationvisitorvalidate)
- [<span data-ttu-id="59992-172">MVC: 미리 컴파일 도구가 사용되지 않음</span><span class="sxs-lookup"><span data-stu-id="59992-172">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="59992-173">MVC: 형식이 내부로 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-173">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="59992-174">MVC: 웹 API 호환성 shim이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-174">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="59992-175">Razor: RazorTemplateEngine API가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-175">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="59992-176">Razor: 런타임 컴파일이 패키지로 이동됨</span><span class="sxs-lookup"><span data-stu-id="59992-176">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="59992-177">보안: 쿠키 이름 인코딩이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-177">Security: Cookie name encoding removed</span></span>](#security-cookie-name-encoding-removed)
- [<span data-ttu-id="59992-178">보안: IdentityModel NuGet 패키지 버전이 업데이트됨</span><span class="sxs-lookup"><span data-stu-id="59992-178">Security: IdentityModel NuGet package versions updated</span></span>](#security-identitymodel-nuget-package-versions-updated)
- [<span data-ttu-id="59992-179">세션 상태: 사용되지 않는 API가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-179">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="59992-180">공유 프레임워크: Microsoft.AspNetCore.App에서 어셈블리 제거</span><span class="sxs-lookup"><span data-stu-id="59992-180">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="59992-181">공유 프레임워크: 제거된 Microsoft.AspNetCore.All이 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-181">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="59992-182">SignalR: HandshakeProtocol.SuccessHandshakeData가 대체됨</span><span class="sxs-lookup"><span data-stu-id="59992-182">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="59992-183">SignalR: HubConnection 메서드가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-183">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="59992-184">SignalR: HubConnectionContext 생성자가 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-184">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="59992-185">SignalR: JavaScript 클라이언트 패키지 이름 변경</span><span class="sxs-lookup"><span data-stu-id="59992-185">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="59992-186">SignalR: MessagePack 허브 프로토콜이 MessagePack 2.x 패키지로 이동됨</span><span class="sxs-lookup"><span data-stu-id="59992-186">SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package</span></span>](#signalr-messagepack-hub-protocol-moved-to-messagepack-2x-package)
- [<span data-ttu-id="59992-187">SignalR: MessagePack 허브 프로토콜 옵션 형식이 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-187">SignalR: MessagePack Hub Protocol options type changed</span></span>](#signalr-messagepack-hub-protocol-options-type-changed)
- [<span data-ttu-id="59992-188">SignalR: 사용되지 않는 API</span><span class="sxs-lookup"><span data-stu-id="59992-188">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="59992-189">SignalR: UseSignalR 및 UseConnections 메서드가 제거됨</span><span class="sxs-lookup"><span data-stu-id="59992-189">SignalR: UseSignalR and UseConnections methods removed</span></span>](#signalr-usesignalr-and-useconnections-methods-removed)
- [<span data-ttu-id="59992-190">SPA: SpaServices 및 NodeServices 콘솔 로거 대체 기본 변경</span><span class="sxs-lookup"><span data-stu-id="59992-190">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="59992-191">SPA: 사용되지 않는 것으로 표시된 SpaServices 및 NodeServices</span><span class="sxs-lookup"><span data-stu-id="59992-191">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="59992-192">정적 파일: CSV 콘텐츠 형식이 표준 규격으로 변경됨</span><span class="sxs-lookup"><span data-stu-id="59992-192">Static files: CSV content type changed to standards-compliant</span></span>](#static-files-csv-content-type-changed-to-standards-compliant)
- [<span data-ttu-id="59992-193">Blazor WebAssembly에서 지원되지 않는 System.Security.Cryptography API</span><span class="sxs-lookup"><span data-stu-id="59992-193">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly)
- [<span data-ttu-id="59992-194">대상 프레임워크: 지원되지 않는 .NET Framework</span><span class="sxs-lookup"><span data-stu-id="59992-194">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-50"></a><span data-ttu-id="59992-195">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="59992-195">ASP.NET Core 5.0</span></span>

[!INCLUDE[Authentication: AzureAD.UI and AzureADB2C.UI APIs and packages marked obsolete](~/includes/core-changes/aspnetcore/5.0/authentication-aad-packages-obsolete.md)]

***

[!INCLUDE[Authorization: Resource in endpoint routing is HttpContext](~/includes/core-changes/aspnetcore/5.0/authorization-resource-in-endpoint-routing.md)]

<span data-ttu-id="59992-196">\*\*_</span><span class="sxs-lookup"><span data-stu-id="59992-196">\*\*_</span></span>

[!INCLUDE[Azure: Microsoft-prefixed Azure integration packages removed](~/includes/core-changes/aspnetcore/5.0/azure-integration-packages-removed.md)]

_*_

[!INCLUDE[Serialization: BinaryFormatter serialization obsolete](~/includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE[Blazor: Insignificant whitespace trimmed from components at compile time](~/includes/core-changes/aspnetcore/5.0/blazor-components-trim-insignificant-whitespace.md)]

_*_

[!INCLUDE[Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal](~/includes/core-changes/aspnetcore/5.0/blazor-jsobjectreference-to-internal.md)]

_*_

[!INCLUDE[Blazor: ProtectedBrowserStorage feature moved to shared framework](~/includes/core-changes/aspnetcore/5.0/blazor-protectedbrowserstorage-moved.md)]

_*_

[!INCLUDE[Blazor: RenderTreeFrame readonly public fields have become properties](~/includes/core-changes/aspnetcore/5.0/blazor-rendertreeframe-fields-become-properties.md)]

_*_

[!INCLUDE[Blazor: Target framework of NuGet packages changed](~/includes/core-changes/aspnetcore/5.0/blazor-packages-target-framework-changed.md)]

_*_

[!INCLUDE[Blazor: Updated browser support](~/includes/core-changes/aspnetcore/5.0/blazor-browser-support-updated.md)]

_*_

[!INCLUDE[Blazor: Static web assets validation logic updated](~/includes/core-changes/aspnetcore/5.0/blazor-static-web-assets-validation-logic-updated.md)]

_*_

[!INCLUDE[Extensions: Package reference changes](~/includes/core-changes/aspnetcore/5.0/extensions-package-reference-changes.md)]

_*_

[!INCLUDE[HTTP: HttpClient instances created by IHttpClientFactory log integer status codes](~/includes/core-changes/aspnetcore/5.0/http-httpclient-instances-log-integer-status-codes.md)]

_*_

[!INCLUDE[HTTP: Kestrel and IIS BadHttpRequestException types marked obsolete and replaced](~/includes/core-changes/aspnetcore/5.0/http-badhttprequestexception-obsolete.md)]

_*_

[!INCLUDE[HttpSys: Client certificate renegotiation disabled by default](~/includes/core-changes/aspnetcore/5.0/httpsys-client-certificate-renegotiation-disabled-by-default.md)]

_*_

[!INCLUDE[IIS: UrlRewrite middleware query strings are preserved](~/includes/core-changes/aspnetcore/5.0/iis-urlrewrite-middleware-query-strings-are-preserved.md)]

_*_

[!INCLUDE[Kestrel: Configuration changes at run time detected by default](~/includes/core-changes/aspnetcore/5.0/kestrel-configuration-changes-at-run-time-detected-by-default.md)]

_*_
[!INCLUDE[Kestrel: Default supported TLS protocol versions changed](~/includes/core-changes/aspnetcore/5.0/kestrel-default-supported-tls-protocol-versions-changed.md)]

_*_

[!INCLUDE[Kestrel: HTTP/2 disabled over TLS on incompatible Windows versions](~/includes/core-changes/aspnetcore/5.0/kestrel-disables-http2-over-tls.md)]

_*_

[!INCLUDE[Kestrel: Libuv transport marked as obsolete](~/includes/core-changes/aspnetcore/5.0/kestrel-libuv-transport-obsolete.md)]

_*_

[!INCLUDE[Localization: "Pubternal" APIs removed](~/includes/core-changes/aspnetcore/5.0/localization-pubternal-apis-removed.md)]

_*_

[!INCLUDE[Localization: Obsolete constructor removed in request localization middleware](~/includes/core-changes/aspnetcore/5.0/localization-requestlocalizationmiddleware-constructor-removed.md)]

_*_

[!INCLUDE[Localization: ResourceManagerWithCultureStringLocalizer class and WithCulture interface member removed](~/includes/core-changes/aspnetcore/5.0/localization-members-removed.md)]

_*_

[!INCLUDE[Middleware: Database error page marked as obsolete](~/includes/core-changes/aspnetcore/5.0/middleware-database-error-page-obsolete.md)]

_*_

[!INCLUDE[Middleware: Exception Handler Middleware throws original exception if handler not found](~/includes/core-changes/aspnetcore/5.0/middleware-exception-handler-throws-original-exception.md)]

_*_

[!INCLUDE[MVC: ObjectModelValidator calls a new overload of ValidationVisitor.Validate](~/includes/core-changes/aspnetcore/5.0/mvc-objectmodelvalidator-calls-new-overload.md)]

_*_

[!INCLUDE[Security: Cookie name encoding removed](~/includes/core-changes/aspnetcore/5.0/security-cookie-name-encoding-removed.md)]

_*_

[!INCLUDE[Security: IdentityModel NuGet package versions updated](~/includes/core-changes/aspnetcore/5.0/security-identitymodel-nuget-package-versions-updated.md)]

_*_

[!INCLUDE[SignalR: MessagePack Hub Protocol moved to MessagePack 2.x package](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-package.md)]

_*_

[!INCLUDE[SignalR: MessagePack Hub Protocol options type changed](~/includes/core-changes/aspnetcore/5.0/signalr-messagepack-hub-protocol-options-changed.md)]

_*_

[!INCLUDE[SignalR: UseSignalR and UseConnections methods removed](~/includes/core-changes/aspnetcore/5.0/signalr-usesignalr-useconnections-removed.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE[Static files: CSV content type changed to standards-compliant](~/includes/core-changes/aspnetcore/5.0/static-files-csv-content-type-changed.md)]

_*_

## <a name="aspnet-core-31"></a><span data-ttu-id="59992-197">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="59992-197">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

_*_

## <a name="aspnet-core-30"></a><span data-ttu-id="59992-198">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="59992-198">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

_*_

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

_*_

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

_*_

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

_*_

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

_*_

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

_*_

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

_*_

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

_*_

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

_*_

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

_*_

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

_*_

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

_*_

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

_*_

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

_*_

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

_*_

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

_*_

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

_*_

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

_*_

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

_*_

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

_*_

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

_*_

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

_*_

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

_*_

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

_*_

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

_*_

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

_*_

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

_*_

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

_*_

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

_*_

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

_*_

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

_*_

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

_*_

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

_*_

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

_*_

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

_*_

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

_*_

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

_*_

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

_*_

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

_*_

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

_*_

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

_*_

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

_*_

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

_*_

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

_*_

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

_*_

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

_*_

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

_*_

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

_*_

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

<span data-ttu-id="59992-199">_\*\*</span><span class="sxs-lookup"><span data-stu-id="59992-199">_\*\*</span></span>
