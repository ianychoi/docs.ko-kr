---
title: WCF 서비스 게시
description: WCF 서비스 게시를 사용 하면 테스트 목적으로 응용 프로그램을 프로덕션 환경에 배포할 수 있습니다.
ms.date: 03/30/2017
ms.assetid: c806b253-cd47-4b96-b831-e73cbf08808f
ms.openlocfilehash: ac817dac15deaf35fdb8e078094dd4b9dca97d06
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293490"
---
# <a name="wcf-service-publishing"></a><span data-ttu-id="9c6b7-103">WCF 서비스 게시</span><span class="sxs-lookup"><span data-stu-id="9c6b7-103">WCF Service Publishing</span></span>

<span data-ttu-id="9c6b7-104">Wcf (Windows Communication Foundation) 서비스 게시를 사용 하면 WCF 서비스 호스트 및 WCF 테스트 클라이언트에서 제공 하는 초기 개발 환경에서 테스트를 위해 실제로 응용 프로그램을 프로덕션 환경에 배포 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-104">Windows Communication Foundation (WCF) Service Publishing assists you in progressing from the early development environment provided by WCF Service Host and WCF Test Client to actually deploying the application to a production environment for testing purposes.</span></span> <span data-ttu-id="9c6b7-105">최종 배포 계획을 커밋하기 전에 wcf (Windows Communication Foundation) 서비스 게시를 사용 하 여 WCF 서비스가 올바르게 수행 되 고 게시할 준비가 되었는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-105">Before you commit to a final deployment plan, you can use Windows Communication Foundation (WCF) Service Publishing to verify that your WCF service performs correctly and is ready to be published.</span></span> <span data-ttu-id="9c6b7-106">테스트를 위해 WCF 서비스 라이브러리를 다양 한 대상 위치에 배포 하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-106">You can also choose to deploy your WCF service libraries to various target locations for testing.</span></span>

## <a name="supported-services-and-target-locations"></a><span data-ttu-id="9c6b7-107">지원되는 서비스 및 대상 위치</span><span class="sxs-lookup"><span data-stu-id="9c6b7-107">Supported Services and Target Locations</span></span>

<span data-ttu-id="9c6b7-108">WCF 서비스 게시는 WCF 서비스 라이브러리 템플릿 집합에서 만든 WCF 서비스와 해당 항목 템플릿 (다음을 포함)을 게시할 수 있도록 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-108">WCF Service Publishing supports publishing WCF services created from the set of WCF service library templates, and their corresponding item templates, which include the following:</span></span>

- <span data-ttu-id="9c6b7-109">항목 템플릿이 있는 WCF 서비스 라이브러리 템플릿</span><span class="sxs-lookup"><span data-stu-id="9c6b7-109">WCF Service Library template with item template.</span></span>

- <span data-ttu-id="9c6b7-110">배포 서비스 라이브러리</span><span class="sxs-lookup"><span data-stu-id="9c6b7-110">Syndication Service Library.</span></span>

<span data-ttu-id="9c6b7-111">**파일**  >  **새로 만들기 프로젝트** > [**Visual Basic** 또는 **Visual c #**] > **WCF** 를 선택 하 여 이러한 서비스 템플릿을 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-111">You can find these service templates by choosing **File** > **New Project** > [**Visual Basic** or **Visual C#**] > **WCF**.</span></span> <span data-ttu-id="9c6b7-112">WCF Workflow Service 응용 프로그램 및 WCF 서비스 응용 프로그램을 포함 하 여이 위치에 있는 다른 WCF 템플릿의 경우, [웹 응용 프로그램에 대해 한 번 클릭 게시](/previous-versions/aspnet/dd465337(v=vs.110))를 사용 하 여 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-112">For other WCF templates in this location (including WCF Workflow Service Application and WCF Service Application), you can publish using [One-Click publishing for web applications](/previous-versions/aspnet/dd465337(v=vs.110)).</span></span>

<span data-ttu-id="9c6b7-113">다음과 같은 대상 위치에 서비스를 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-113">The service can be published to the following target locations.</span></span>

- <span data-ttu-id="9c6b7-114">로컬 IIS</span><span class="sxs-lookup"><span data-stu-id="9c6b7-114">Local IIS.</span></span>

- <span data-ttu-id="9c6b7-115">파일 시스템</span><span class="sxs-lookup"><span data-stu-id="9c6b7-115">File System.</span></span>

- <span data-ttu-id="9c6b7-116">FTP 사이트</span><span class="sxs-lookup"><span data-stu-id="9c6b7-116">FTP Site.</span></span>

## <a name="using-wcf-service-publishing"></a><span data-ttu-id="9c6b7-117">WCF 서비스 게시 사용</span><span class="sxs-lookup"><span data-stu-id="9c6b7-117">Using WCF Service Publishing</span></span>

<span data-ttu-id="9c6b7-118">서비스 구현을 배포하려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-118">Perform the following steps to deploy a service implementation:</span></span>

1. <span data-ttu-id="9c6b7-119">높은 권한으로 Visual Studio를 엽니다 (실행 파일을 마우스 오른쪽 단추로 클릭 하 고 **관리자 권한으로 실행** 을 선택 하 여 엽니다).</span><span class="sxs-lookup"><span data-stu-id="9c6b7-119">Open Visual Studio with elevated privileges (right-click the executable and choose **Run as administrator** to open it).</span></span>  <span data-ttu-id="9c6b7-120">IIS 7.0 이상 버전을 사용 하는 경우 제어판의 "Windows 기능 사용/사용 안 함"을 사용 하 여 "IIS 메타 베이스 및 IIS6 구성 호환성" 구성 요소를 설치 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-120">If you are using IIS 7.0 or later, ensure that you have installed the "IIS Metabase and IIS6 Configuration Compatibility" component using "Turn Windows features on or off" in Control Panel.</span></span>

2. <span data-ttu-id="9c6b7-121">서비스 프로젝트를 열고 **Build**  >  주 메뉴에서 빌드 **\<Project Name> 게시** 를 선택 하거나 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **게시** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-121">Open a service project, select **Build** > **Publish \<Project Name>** from the main menu, or right-click the project in **Solution Explorer** and click **Publish**.</span></span>

3. <span data-ttu-id="9c6b7-122">**게시** 창이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-122">The **Publish** window appears.</span></span> <span data-ttu-id="9c6b7-123">**...를 클릭** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-123">Click the **…**.</span></span> <span data-ttu-id="9c6b7-124">단추를 클릭하여 서비스를 배포할 대상 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-124">button to specify the target location that the service should be deployed to.</span></span> <span data-ttu-id="9c6b7-125">로컬 IIS, 파일 시스템 또는 FTP 사이트에 응용 프로그램을 배포 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-125">You can select to deploy the application to local IIS, File System, or FTP Site.</span></span> <span data-ttu-id="9c6b7-126">로컬 IIS에 응용 프로그램을 배포 하는 경우 오른쪽 위 모서리에서 **새 웹 응용 프로그램 만들기** 아이콘을 클릭 하 여 웹 사이트를 선택 하 고 그 아래에서 웹 응용 프로그램을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-126">If deploying the application to local IIS, you can select your website and create your web application under it, by clicking the **Create New Web Application** icon at the top right corner.</span></span>

4. <span data-ttu-id="9c6b7-127">주 창에서 **게시** 를 클릭 한 후 Visual Studio는 지정 된 대상 위치에 응용 프로그램을 배포 하 고 Web.config, .svc 및 어셈블리 파일을 대상 디렉터리에 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-127">After you click **Publish** in the main window, Visual Studio deploys the application to the specified target location and copies the Web.config, .svc, and assembly files to the target directory.</span></span> <span data-ttu-id="9c6b7-128">.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-128">.</span></span> <span data-ttu-id="9c6b7-129">.Svc의 이름은 "ProjectName. ServiceName"이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-129">The name of .svc will be "ProjectName.ServiceName.svc".</span></span> <span data-ttu-id="9c6b7-130">서비스를 성공적으로 게시 한 후 Visual Studio 출력 창에서 hotlink를 찾을 수 있습니다 .이 창에는 "연결 중"과 유사한 것으로 `http://localhost/WebApplicationFolderName...` 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-130">After the service is published successfully, you can find a hotlink in the Visual Studio Output window, which looks similar to "Connecting to `http://localhost/WebApplicationFolderName...`".</span></span> <span data-ttu-id="9c6b7-131">Ctrl 키를 누르고 링크를 클릭하여 Visual Studio 내에서 브라우저 페이지를 열고 서비스 디렉터리 구조를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-131">You can press CTRL and click the link to open a browser page inside Visual Studio to view the service directory structure.</span></span>

     <span data-ttu-id="9c6b7-132">사이트를 찾을 수 없으면 IIS에서 디렉터리 브라우저를 사용하도록 설정되지 않았을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-132">If you cannot browse to the site, it may because directory browser is not enabled in IIS.</span></span> <span data-ttu-id="9c6b7-133">"시도해 볼 수 있는 항목" 섹션의 팁을 따라 사용 하도록 설정 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-133">Please follow the tips in the "Things you can try" section to enable it.</span></span> <span data-ttu-id="9c6b7-134">또는를 직접 입력 하 여 `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` 서비스 페이지를 볼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-134">Alternatively, you can directly type `http://localhost/WebApplicationFolderName/ProjectName.ServiceName.svc` to view your service page.</span></span>

<span data-ttu-id="9c6b7-135">**게시** 를 사용 하 여 프로젝트에 정의 된 모든 서비스에 대 한 어셈블리, 구성 및 .svc 파일을 대상 위치에 복사할지 여부를 지정 하 고 대상에서 기존 파일을 덮어쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-135">You can use **Publish** to specify if you want to copy the assembly, configuration, and .svc file for all services defined in the project to the target location, and overwrite existing files at the destination.</span></span>

<span data-ttu-id="9c6b7-136">애플리케이션을 로컬 IIS에 배포하도록 선택하면 IIS 설치와 관련된 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-136">If you choose to deploy your application to local IIS, you may encounter errors related to IIS setup.</span></span> <span data-ttu-id="9c6b7-137">IIS가 제대로 설치되었는지 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-137">Please ensure that IIS is installed properly.</span></span> <span data-ttu-id="9c6b7-138">`http://localhost`브라우저의 주소 표시줄에를 입력 하 고 IIS 기본 페이지가 표시 되는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-138">You can enter `http://localhost` in your browser's address bar and check whether the IIS default page displays.</span></span> <span data-ttu-id="9c6b7-139">일부 경우에는 IIS에서 ASP.NET 또는 WCF를 잘못 등록 하는 경우에도 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-139">In some cases, the issues may also be caused by improper registration of ASP.NET or WCF in IIS.</span></span> <span data-ttu-id="9c6b7-140">Visual Studio에 대 한 개발자 명령 프롬프트를 열고 명령을 실행 하 여 `aspnet_regiis.exe -ir` ASP.NET 등록 문제를 해결 하거나, 명령을 실행 하 여 `ServiceModelReg.exe –ia` WCF 등록 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-140">You can open the Developer Command Prompt for Visual Studio and run the command `aspnet_regiis.exe -ir` to fix ASP.NET registration issues, or run command `ServiceModelReg.exe –ia` to fix WCF registration issues.</span></span>

## <a name="files-generated-for-publishing"></a><span data-ttu-id="9c6b7-141">게시를 위해 생성되는 파일</span><span class="sxs-lookup"><span data-stu-id="9c6b7-141">Files Generated for Publishing</span></span>

 <span data-ttu-id="9c6b7-142">WCF 서비스 라이브러리를 웹 호스트로 만들려면 도구에서 어셈블리 파일, Web.config 파일, .svc 파일 등의 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-142">Before a WCF service library can be Web-hosted, the following files are generated by the tool: assembly files, Web.config file, and .svc file.</span></span> <span data-ttu-id="9c6b7-143">이러한 파일이 모두 대상 위치에 복사된 후에</span><span class="sxs-lookup"><span data-stu-id="9c6b7-143">All the files are copied to the target location.</span></span> <span data-ttu-id="9c6b7-144">서비스가 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-144">The service is then published.</span></span>

### <a name="assembly-files"></a><span data-ttu-id="9c6b7-145">어셈블리 파일</span><span class="sxs-lookup"><span data-stu-id="9c6b7-145">Assembly files</span></span>

 <span data-ttu-id="9c6b7-146">이 도구를 사용 하 여 WCF 서비스를 게시 하면 서비스가 먼저 자동으로 빌드되고 빌드 후에 서비스 프로젝트에 어셈블리 파일이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-146">When you publish a WCF service using this tool, the service is automatically built first and the assembly files are generated in the service project after building.</span></span>

### <a name="svc-file"></a><span data-ttu-id="9c6b7-147">.SVC 파일</span><span class="sxs-lookup"><span data-stu-id="9c6b7-147">.SVC File</span></span>

 <span data-ttu-id="9c6b7-148">게시 작업은 버전 유효성을 확인 하기 위해 각 WCF 서비스에 대해 파일이 있는지 여부에 관계 없이 \* .svc 파일을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-148">The publishing operation generates a \*.svc file for each WCF service, whether the file exists or not, to ensure version validity.</span></span> <span data-ttu-id="9c6b7-149">두 가지 svc 파일, 즉 WCF 서비스 라이브러리 및 배포 서비스 라이브러리와 순차 및 상태 시스템 워크플로 서비스 라이브러리에 대 한 두 가지 다른 종류의 svc 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-149">There are two different kinds of svc files: one for WCF Service Library and Syndication Service Library, and another one for Sequential and State Machine Workflow Service Library.</span></span> <span data-ttu-id="9c6b7-150">생성 된 \* .svc 파일은 대상 위치의 루트 폴더에 복사 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-150">The generated \*.svc file is copied to the root folder in the target location.</span></span>

### <a name="webconfig-file"></a><span data-ttu-id="9c6b7-151">Web.config 파일</span><span class="sxs-lookup"><span data-stu-id="9c6b7-151">Web.config File</span></span>

 <span data-ttu-id="9c6b7-152">서비스 프로젝트를 특정 대상 위치에 게시할 때마다 Web.config 파일이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-152">Each time a service project is published to a specific target location, a Web.config file is created.</span></span>

 <span data-ttu-id="9c6b7-153">생성 된 Web.config 파일에는 웹 호스팅에 유용한 웹 섹션과 다음과 같이 변경 된 WCF 서비스 라이브러리의 App.config 내용이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-153">The generated Web.config file includes Web sections that are useful for Web hosting, and the content of App.config for the WCF service library with the following changes:</span></span>

- <span data-ttu-id="9c6b7-154">기본 주소는 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-154">The base address is excluded.</span></span>

- <span data-ttu-id="9c6b7-155">`<diagnostics>` 요소의 설정은 대상 플랫폼의 추적 설정을 유지하기 위해 제외됩니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-155">Settings in the `<diagnostics>` element are excluded to preserve the tracing settings of the target platform.</span></span>

## <a name="publishing-wcf-services-with-non-http-bindings-to-iis"></a><span data-ttu-id="9c6b7-156">HTTP가 아닌 바인딩을 사용하여 WCF 서비스를 IIS에 게시</span><span class="sxs-lookup"><span data-stu-id="9c6b7-156">Publishing WCF services with non-HTTP Bindings to IIS</span></span>

 <span data-ttu-id="9c6b7-157">IIS 7.0 이상을 사용 하는 경우 HTTP가 아닌 바인딩을 사용 하 여 WCF 서비스를 IIS에 게시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-157">If you are using IIS7.0 or later, you can publish WCF services with non-HTTP bindings to IIS.</span></span> <span data-ttu-id="9c6b7-158">몇 가지 사전 구성 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-158">You need to do some pre-configurations.</span></span> <span data-ttu-id="9c6b7-159">자세한 내용은  [Windows Process Activation Service에서 호스팅](./feature-details/hosting-in-windows-process-activation-service.md)항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-159">For more information, please see the topics at  [Hosting in Windows Process Activation Service](./feature-details/hosting-in-windows-process-activation-service.md).</span></span>

## <a name="security"></a><span data-ttu-id="9c6b7-160">보안</span><span class="sxs-lookup"><span data-stu-id="9c6b7-160">Security</span></span>

 <span data-ttu-id="9c6b7-161">IIS는 관리자 계정으로 실행해야 하므로 로컬 IIS에 게시하려면 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-161">Publishing to local IIS requires administrator privilege, because IIS requires running in Administrator account.</span></span> <span data-ttu-id="9c6b7-162">관리자 권한이 없는 사용자가 WCF 서비스 게시를 열면 IIS를 대상 위치로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-162">If a user without administrator privilege opens WCF Service Publishing, IIS is not available as a target location.</span></span> <span data-ttu-id="9c6b7-163">파일 시스템 또는 FTP 사이트에 대 한 게시는 관리자 권한 없이 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c6b7-163">Publishing to File System, or FTP Site works without administrator privilege.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c6b7-164">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c6b7-164">See also</span></span>

- [<span data-ttu-id="9c6b7-165">WCF Visual Studio 템플릿</span><span class="sxs-lookup"><span data-stu-id="9c6b7-165">WCF Visual Studio Templates</span></span>](wcf-vs-templates.md)
- [<span data-ttu-id="9c6b7-166">WCF 서비스 호스트(WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9c6b7-166">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
- [<span data-ttu-id="9c6b7-167">WCF 테스트 클라이언트(WcfTestClient.exe)</span><span class="sxs-lookup"><span data-stu-id="9c6b7-167">WCF Test Client (WcfTestClient.exe)</span></span>](wcf-test-client-wcftestclient-exe.md)
