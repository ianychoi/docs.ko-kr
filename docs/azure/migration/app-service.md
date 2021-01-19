---
title: .NET 웹 앱 또는 서비스를 Azure App Service로 마이그레이션
description: .NET 웹앱 또는 서비스를 온-프레미스에서 Azure App Service로 마이그레이션하는 방법에 대해 알아봅니다.
ms.topic: conceptual
ms.date: 07/08/2020
ms.openlocfilehash: 0e2aaa23aedabef007878901ec7297711f140533
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189254"
---
# <a name="migrate-your-net-web-app-or-service-to-azure-app-service"></a><span data-ttu-id="c1307-103">.NET 웹 앱 또는 서비스를 Azure App Service로 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="c1307-103">Migrate your .NET web app or service to Azure App Service</span></span>

<span data-ttu-id="c1307-104">[App Service](/azure/app-service/overview)는 확장 가능한 웹 사이트와 웹 애플리케이션 호스팅을 위해 최적화된 완전 관리형 컴퓨팅 플랫폼 서비스입니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-104">[App Service](/azure/app-service/overview) is a fully managed compute platform service that's optimized for hosting scalable websites and web applications.</span></span> <span data-ttu-id="c1307-105">이 문서에서는 기존 애플리케이션을 Azure App Service로 리프트 앤드 시프트하는 방법, 고려할 수정 사항 및 [클라우드로 이동](https://azure.microsoft.com/migration/web-applications/)하기 위한 추가 리소스에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-105">This article provides information on how to lift-and-shift an existing application to Azure App Service, modifications to consider, and additional resources for [moving to the cloud](https://azure.microsoft.com/migration/web-applications/).</span></span> <span data-ttu-id="c1307-106">대부분의 ASP.NET 웹 사이트(Webforms, MVC) 및 서비스(Web API, WCF)는 변경 없이 Azure App Service로 바로 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-106">Most ASP.NET websites (Webforms, MVC) and services (Web API, WCF) can move directly to Azure App Service with no changes.</span></span> <span data-ttu-id="c1307-107">일부는 사소한 변경이 필요할 수 있으며 약간의 리팩터링이 필요할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-107">Some may need minor changes while others may need some refactoring.</span></span>

<span data-ttu-id="c1307-108">시작할 준비가 되셨나요?</span><span class="sxs-lookup"><span data-stu-id="c1307-108">Ready to get started?</span></span> <span data-ttu-id="c1307-109">[Azure App Service에 ASP.NET + SQL 애플리케이션 게시](https://tutorials.visualstudio.com/azure-webapp-migrate/intro)</span><span class="sxs-lookup"><span data-stu-id="c1307-109">[Publish your ASP.NET + SQL application to Azure App Service](https://tutorials.visualstudio.com/azure-webapp-migrate/intro).</span></span>

## <a name="considerations"></a><span data-ttu-id="c1307-110">고려 사항</span><span class="sxs-lookup"><span data-stu-id="c1307-110">Considerations</span></span>

### <a name="on-premises-resources-including-sql-server"></a><span data-ttu-id="c1307-111">온-프레미스 리소스 (예: SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c1307-111">On-premises resources (including SQL Server)</span></span>

<span data-ttu-id="c1307-112">마이그레이션하거나 변경해야 할 수 있으므로 온-프레미스 리소스에 대한 액세스를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-112">Verify access to on-premises resources as these may need to be migrated or changed.</span></span> <span data-ttu-id="c1307-113">다음은 온-프레미스 리소스에 대한 액세스를 완화하기 위한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-113">The following are options for mitigating access to on-premises resources:</span></span>

* <span data-ttu-id="c1307-114">[Azure Virtual Network](/azure/app-service/web-sites-integrate-with-vnet)를 사용하여 App Service를 온-프레미스 리소스에 연결할 VPN을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-114">Create a VPN connecting App Service to on-premises resources using [Azure Virtual Networks](/azure/app-service/web-sites-integrate-with-vnet).</span></span>
* <span data-ttu-id="c1307-115">[Azure Relay](/azure/service-bus-relay/relay-what-is-it)를 사용하여 방화벽을 변경하지 않고 온-프레미스 서비스를 클라우드에 안전하게 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-115">Securely expose on-premises services to the cloud without firewall changes using [Azure Relay](/azure/service-bus-relay/relay-what-is-it).</span></span>
* <span data-ttu-id="c1307-116">[SQL database](./sql.md)의 Azure에 대한 종속성과 같은 종속성을 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-116">Migrate dependencies such as a [SQL database](./sql.md) to Azure.</span></span>
* <span data-ttu-id="c1307-117">클라우드의 Platform-as-a-Service 기능을 사용하여 종속성을 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-117">Use platform-as-a-service offerings in the cloud to reduce dependencies.</span></span> <span data-ttu-id="c1307-118">예를 들어, 온-프레미스 메일 서버에 연결하는 것보다 [SendGrid](/azure/sendgrid-dotnet-how-to-send-email) 사용을 고려해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-118">For example, rather than connect to an on-premises mail server, consider using [SendGrid](/azure/sendgrid-dotnet-how-to-send-email).</span></span>

### <a name="port-bindings"></a><span data-ttu-id="c1307-119">포트 바인딩</span><span class="sxs-lookup"><span data-stu-id="c1307-119">Port Bindings</span></span>

<span data-ttu-id="c1307-120">Azure App Service는 HTTP 트래픽에는 포트 80, HTTPS 트래픽에는 포트 443을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-120">Azure App Service supports port 80 for HTTP and port 443 for HTTPS traffic.</span></span>

<span data-ttu-id="c1307-121">WCF의 경우 다음 바인딩이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-121">For WCF, the following bindings are supported:</span></span>

| <span data-ttu-id="c1307-122">바인딩</span><span class="sxs-lookup"><span data-stu-id="c1307-122">Binding</span></span> | <span data-ttu-id="c1307-123">참고</span><span class="sxs-lookup"><span data-stu-id="c1307-123">Notes</span></span> |
|--|--|
| `BasicHttp` |  |
| `WSHttp` |  |
| `WSDualHttpBinding` | <span data-ttu-id="c1307-124">[웹 소켓 지원](/azure/app-service/web-sites-configure)을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-124">[Web socket support](/azure/app-service/web-sites-configure) must be enabled.</span></span> | <span data-ttu-id="c1307-125">[웹 소켓 지원](/azure/app-service/web-sites-configure)을 활성화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-125">[Web socket support](/azure/app-service/web-sites-configure) must be enabled.</span></span> |
| `NetHttpBinding` | <span data-ttu-id="c1307-126">[웹 소켓 지원](/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-126">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> | <span data-ttu-id="c1307-127">[웹 소켓 지원](/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-127">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> |
| `NetHttpsBinding` | <span data-ttu-id="c1307-128">[웹 소켓 지원](/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-128">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> | <span data-ttu-id="c1307-129">[웹 소켓 지원](/azure/app-service/web-sites-configure)이 콜백 계약에 대해 활성화되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-129">[Web socket support](/azure/app-service/web-sites-configure) must be enabled for duplex contracts.</span></span> |
| `BasicHttpContextBinding` |  |
| `WebHttpBinding` |  |
| `WSHttpContextBinding` |  |

### <a name="authentication"></a><span data-ttu-id="c1307-130">인증</span><span class="sxs-lookup"><span data-stu-id="c1307-130">Authentication</span></span>

<span data-ttu-id="c1307-131">Azure App Service는 기본적으로 익명 인증을 지원하며 의도하는 경우 폼 인증을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-131">Azure App Service supports anonymous authentication by default and Forms authentication when intended.</span></span> <span data-ttu-id="c1307-132">Windows 인증은 Azure Active Directory 및 ADFS와 통합해야만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-132">Windows authentication can be used by integrating with Azure Active Directory and ADFS only.</span></span> <span data-ttu-id="c1307-133">[온-프레미스 디렉터리와 Azure Active Directory를 통합하는 방법에 대해 알아보세요](/azure/active-directory/connect/active-directory-aadconnect).</span><span class="sxs-lookup"><span data-stu-id="c1307-133">[Learn more about how to integrate your on-premises directories with Azure Active Directory](/azure/active-directory/connect/active-directory-aadconnect).</span></span>

### <a name="assemblies-in-the-gac-global-assembly-cache"></a><span data-ttu-id="c1307-134">GAC 어셈블리(전역 어셈블리 캐시)</span><span class="sxs-lookup"><span data-stu-id="c1307-134">Assemblies in the GAC (Global Assembly Cache)</span></span>

<span data-ttu-id="c1307-135">지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-135">This isn't supported.</span></span> <span data-ttu-id="c1307-136">필요한 어셈블리를 앱의 *\bin* 폴더에 복사하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-136">Consider copying required assemblies to the app's *\bin* folder.</span></span> <span data-ttu-id="c1307-137">서버에 설치된 사용자 지정 *.msi* 파일(예: PDF 생성기)은 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-137">Custom *.msi* files installed on the server (for example, PDF generators) cannot be used.</span></span>

### <a name="iis-settings"></a><span data-ttu-id="c1307-138">IIS 설정</span><span class="sxs-lookup"><span data-stu-id="c1307-138">IIS settings</span></span>

<span data-ttu-id="c1307-139">기존에는 애플리케이션에서 applicationHost.config를 통해 구성하던 모든 것을 이제 Azure Portal을 통해 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-139">Everything traditionally configured via applicationHost.config in your application can now be configured through the Azure portal.</span></span> <span data-ttu-id="c1307-140">이는 AppPool 비트 수, WebSockets 활성화/비활성화, 관리형 파이프라인 버전, .NET Framework 버전(2.0/4.0) 등에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-140">This applies to AppPool bitness, enable/disable WebSockets, managed pipeline version, .NET Framework version (2.0/4.0), and so on.</span></span> <span data-ttu-id="c1307-141">[애플리케이션 설정](/azure/app-service/web-sites-configure)을 수정하려면 [Azure Portal](https://portal.azure.com)로 이동하고 웹앱의 블레이드를 연 다음 **애플리케이션 설정** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-141">To modify your [application settings](/azure/app-service/web-sites-configure), navigate to the [Azure portal](https://portal.azure.com), open the blade for your web app, and then select the **Application Settings** tab.</span></span>

#### <a name="iis5-compatibility-mode"></a><span data-ttu-id="c1307-142">IIS5 호환 모드</span><span class="sxs-lookup"><span data-stu-id="c1307-142">IIS5 Compatibility Mode</span></span>

<span data-ttu-id="c1307-143">IIS5 호환 모드는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-143">IIS5 Compatibility Mode is not supported.</span></span> <span data-ttu-id="c1307-144">Azure App Service에서 각 웹앱과 그 아래의 모든 애플리케이션은 특정 [애플리케이션 풀](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)) 세트로 동일한 작업자 프로세스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-144">In Azure App Service, each web app and all of the applications under it run in the same worker process with a specific set of [application pools](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc735247(v=ws.10)).</span></span>

#### <a name="iis7-schema-compliance"></a><span data-ttu-id="c1307-145">IIS7+ 스키마 준수</span><span class="sxs-lookup"><span data-stu-id="c1307-145">IIS7+ schema compliance</span></span>

<span data-ttu-id="c1307-146">Azure App Service IIS 스키마의 일부 요소와 특성이 정의되지 있지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-146">Some elements and attributes are not defined in the Azure App Service IIS schema.</span></span> <span data-ttu-id="c1307-147">문제가 발생하는 경우 [XDT 변환](/azure/app-service/configure-common) 사용을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-147">If you encounter issues, consider using [XDT transforms](/azure/app-service/configure-common).</span></span>

#### <a name="single-application-pool-per-site"></a><span data-ttu-id="c1307-148">사이트당 하나의 애플리케이션 풀</span><span class="sxs-lookup"><span data-stu-id="c1307-148">Single application pool per site</span></span>

<span data-ttu-id="c1307-149">Azure App Service에서 각 웹앱과 그 아래의 모든 애플리케이션은 동일한 애플리케이션 풀에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-149">In Azure App Service, each web app and all of the applications under it run in the same application pool.</span></span> <span data-ttu-id="c1307-150">일반적인 설정을 사용하여 단일 애플리케이션 풀을 설정하거나 각 애플리케이션에 대한 별도의 웹앱을 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-150">Consider establishing a single application pool with common settings or creating a separate web app for each application.</span></span>

### <a name="com-and-com-components"></a><span data-ttu-id="c1307-151">COM 및 COM+ 구성 요소</span><span class="sxs-lookup"><span data-stu-id="c1307-151">COM and COM+ components</span></span>

<span data-ttu-id="c1307-152">Azure App Service에서는 플랫폼에 COM 구성 요소를 등록할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-152">Azure App Service does not allow the registration of COM components on the platform.</span></span> <span data-ttu-id="c1307-153">앱이 COM 구성 요소를 사용하는 경우, 관리 코드로 다시 작성하고 사이트 또는 애플리케이션을 사용하여 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-153">If your app makes use of any COM components, these need to be rewritten in managed code and deployed with the site or application.</span></span>

### <a name="physical-directories"></a><span data-ttu-id="c1307-154">물리적 디렉터리</span><span class="sxs-lookup"><span data-stu-id="c1307-154">Physical directories</span></span>

<span data-ttu-id="c1307-155">Azure App Service는 물리적 드라이브 액세스를 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-155">Azure App Service does not allow physical drive access.</span></span> <span data-ttu-id="c1307-156">SMB를 통해 파일에 액세스하려면 [Azure Files](/azure/storage/files/storage-files-introduction)를 사용해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-156">You may need to use [Azure Files](/azure/storage/files/storage-files-introduction) to access files via SMB.</span></span> <span data-ttu-id="c1307-157">[Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction)는 HTTPS 통한 액세스를 위해 파일을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-157">[Azure Blob Storage](/azure/storage/blobs/storage-blobs-introduction) can store files for access via HTTPS.</span></span>

### <a name="isapi-filters"></a><span data-ttu-id="c1307-158">ISAPI 필터</span><span class="sxs-lookup"><span data-stu-id="c1307-158">ISAPI filters</span></span>

<span data-ttu-id="c1307-159">Azure App Service는 ISAPI 필터의 사용을 지원할 수는 있지만 ISAPI DLL은 귀하의 사이트를 사용하여 배포되어야 하며 web.config를 통해 등록되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-159">Azure App Service can support the use of ISAPI Filters, however, the ISAPI DLL must be deployed with your site and registered via web.config.</span></span>

### <a name="https-bindings-and-ssl"></a><span data-ttu-id="c1307-160">HTTPS 바인딩 및 SSL</span><span class="sxs-lookup"><span data-stu-id="c1307-160">HTTPS bindings and SSL</span></span>

<span data-ttu-id="c1307-161">HTTPS 바인딩은 마이그레이션되지 않으며, 웹 사이트와 연결된 SSL 인증서도 마이그레이션되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-161">HTTPS bindings are not migrated, nor are the SSL certificates associated with your web sites.</span></span> <span data-ttu-id="c1307-162">하지만 사이트 마이그레이션이 완료된 후 [SSL 인증서를 수동으로 업로드할 수 있습니다](/azure/app-service/app-service-web-tutorial-custom-ssl).</span><span class="sxs-lookup"><span data-stu-id="c1307-162">[SSL certificates can be manually uploaded](/azure/app-service/app-service-web-tutorial-custom-ssl) after site migration is completed, however.</span></span>

### <a name="sharepoint-and-frontpage"></a><span data-ttu-id="c1307-163">SharePoint 및 FrontPage</span><span class="sxs-lookup"><span data-stu-id="c1307-163">SharePoint and FrontPage</span></span>

<span data-ttu-id="c1307-164">SharePoint 및 FrontPage Server Extensions(FPSE)는 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-164">SharePoint and FrontPage Server Extensions (FPSE) are not supported.</span></span>

### <a name="web-site-size"></a><span data-ttu-id="c1307-165">웹 사이트 크기</span><span class="sxs-lookup"><span data-stu-id="c1307-165">Web site size</span></span>

<span data-ttu-id="c1307-166">무료 사이트는 1GB 콘텐츠로 크기가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-166">Free sites have a size limit of 1 GB of content.</span></span> <span data-ttu-id="c1307-167">귀하의 사이트가 1GB 보다 큰 경우, 유료 SKU로 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-167">If your site is greater than 1 GB, you must upgrade to a paid SKU.</span></span> <span data-ttu-id="c1307-168">[App Service 가격 책정](https://azure.microsoft.com/pricing/details/app-service/windows/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1307-168">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="database-size"></a><span data-ttu-id="c1307-169">데이터베이스 크기</span><span class="sxs-lookup"><span data-stu-id="c1307-169">Database size</span></span>

<span data-ttu-id="c1307-170">SQL Server 데이터베이스에 대한 현재의 [SQL Database 가격 책정](https://azure.microsoft.com/pricing/details/sql-database)을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-170">For SQL Server databases, please check the current [SQL Database pricing](https://azure.microsoft.com/pricing/details/sql-database).</span></span>

### <a name="azure-active-directory-aad-integration"></a><span data-ttu-id="c1307-171">Azure Active Directory(AAD) 통합</span><span class="sxs-lookup"><span data-stu-id="c1307-171">Azure Active Directory (AAD) integration</span></span>

<span data-ttu-id="c1307-172">AAD는 무료 앱으로 작동하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-172">AAD does not work with free apps.</span></span> <span data-ttu-id="c1307-173">AAD를 사용하려면 앱 SKU를 업그레이드해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-173">To use AAD, you must upgrade the app SKU.</span></span> <span data-ttu-id="c1307-174">[App Service 가격 책정](https://azure.microsoft.com/pricing/details/app-service/windows/)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c1307-174">See [App Service pricing](https://azure.microsoft.com/pricing/details/app-service/windows/).</span></span>

### <a name="monitoring-and-diagnostics"></a><span data-ttu-id="c1307-175">모니터링 및 진단</span><span class="sxs-lookup"><span data-stu-id="c1307-175">Monitoring and diagnostics</span></span>

<span data-ttu-id="c1307-176">모니터링 및 진단을 위해 현재 온-프레미스 솔루션은 클라우드에서 작동하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-176">Your current on-premises solutions for monitoring and diagnostics are unlikely to work in the cloud.</span></span> <span data-ttu-id="c1307-177">그러나 Azure는 앱의 문제를 식별하고 디버깅할 수 있도록 로깅, 모니터링 및 진단을 위한 도구를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-177">However, Azure provides tools for logging, monitoring, and diagnostics so that you can identify and debug issues with web apps.</span></span> <span data-ttu-id="c1307-178">구성에서 웹앱에 대해 쉽게 진단하고 Azure Application Insights에 기록된 로그를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-178">You can easily enable diagnostics for your web app in its configuration, and you can view the logs recorded in Azure Application Insights.</span></span> <span data-ttu-id="c1307-179">[웹앱에 대한 진단 로깅을 사용하는 방법에 대해 자세히 알아보세요](/azure/app-service/web-sites-enable-diagnostic-log).</span><span class="sxs-lookup"><span data-stu-id="c1307-179">[Learn more about enabling diagnostics logging for web apps](/azure/app-service/web-sites-enable-diagnostic-log).</span></span>

### <a name="connection-strings-and-application-settings"></a><span data-ttu-id="c1307-180">연결 문자열 및 애플리케이션 설정</span><span class="sxs-lookup"><span data-stu-id="c1307-180">Connection strings and application settings</span></span>

<span data-ttu-id="c1307-181">애플리케이션에서 사용되는 중요한 정보를 안전하게 저장하는 서비스인 [Azure KeyVault](/azure/key-vault/)를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-181">Consider using [Azure KeyVault](/azure/key-vault/), a service that securely stores sensitive information used in your application.</span></span> <span data-ttu-id="c1307-182">또는 이 데이터를 App Service 설정으로 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-182">Alternatively, you can store this data as an App Service setting.</span></span>

### <a name="dns"></a><span data-ttu-id="c1307-183">DNS</span><span class="sxs-lookup"><span data-stu-id="c1307-183">DNS</span></span>

<span data-ttu-id="c1307-184">애플리케이션의 요구 사항에 따라 DNS 구성을 업데이트해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-184">You may need to update DNS configurations based on the requirements of your application.</span></span> <span data-ttu-id="c1307-185">이러한 DNS 설정은 App Service [사용자 지정 도메인 설정](/azure/app-service/app-service-web-tutorial-custom-domain)에서 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-185">These DNS settings can be configured in the App Service [custom domain settings](/azure/app-service/app-service-web-tutorial-custom-domain).</span></span>

## <a name="azure-app-service-with-windows-containers"></a><span data-ttu-id="c1307-186">Windows 컨테이너를 사용하는 Azure App Service</span><span class="sxs-lookup"><span data-stu-id="c1307-186">Azure App Service with Windows Containers</span></span>

<span data-ttu-id="c1307-187">앱을 App Service로 직접 마이그레이션할 수 없는 경우 GAC, COM 구성 요소, MSI, .NET FX API, DirectX 등의 사용을 활성화하는 Windows 컨테이너를 사용하는 App Service를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="c1307-187">If your app cannot be migrated directly to App Service, consider App Service using Windows Containers, which enables usage of the GAC, COM components, MSIs, full access to .NET FX APIs, DirectX, and more.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1307-188">참조</span><span class="sxs-lookup"><span data-stu-id="c1307-188">See also</span></span>

* [<span data-ttu-id="c1307-189">앱이 App Service에 적합한지 판단하는 방법</span><span class="sxs-lookup"><span data-stu-id="c1307-189">How to determine if your app qualifies for App Service</span></span>](https://appmigration.microsoft.com/)
* [<span data-ttu-id="c1307-190">클라우드로 데이터베이스 이동</span><span class="sxs-lookup"><span data-stu-id="c1307-190">Moving your database to the cloud</span></span>](sql.md)
* [<span data-ttu-id="c1307-191">Azure 웹앱 샌드박스 세부 정보 및 제한 사항</span><span class="sxs-lookup"><span data-stu-id="c1307-191">Azure web app sandbox details and restrictions</span></span>](https://github.com/projectkudu/kudu/wiki/Azure-Web-App-sandbox)
