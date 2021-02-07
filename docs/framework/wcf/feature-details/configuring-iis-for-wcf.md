---
description: '자세한 정보: Windows Communication Foundation에 대 한 인터넷 정보 서비스 7.0 구성'
title: Windows Communication Foundation에 대해 Internet Information Services 7.0 구성
ms.date: 03/30/2017
ms.assetid: 1050d395-092e-44d3-b4ba-66be3b039ffb
ms.openlocfilehash: e76918d70a922cb32c9bbacd5779aa4f8e991b2c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743267"
---
# <a name="configuring-internet-information-services-70-for-windows-communication-foundation"></a><span data-ttu-id="76f0d-103">Windows Communication Foundation에 대해 Internet Information Services 7.0 구성</span><span class="sxs-lookup"><span data-stu-id="76f0d-103">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>

<span data-ttu-id="76f0d-104">IIS(인터넷 정보 서비스) 7.0은 필요한 구성 요소를 선택적으로 설치할 수 있는 모듈형 디자인입니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-104">Internet Information Services (IIS) 7.0 has a modular design that allows you to selectively install components that are required.</span></span> <span data-ttu-id="76f0d-105">이 디자인은 Windows Vista에 도입 된 새로운 매니페스트 기반 구성 요소화 기술을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-105">This design is based on the new manifest-driven componentization technology introduced in Windows Vista.</span></span> <span data-ttu-id="76f0d-106">IIS 7.0에는 독립적으로 설치할 수 있는 40 개의 독립 실행형 기능 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-106">There are more than 40 standalone feature components of IIS 7.0 that can be installed independently.</span></span> <span data-ttu-id="76f0d-107">따라서 IT 전문가는 필요에 따라 편리하게 설치를 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-107">This allows IT professionals to easily customize the installation as required.</span></span> <span data-ttu-id="76f0d-108">이 항목에서는 Windows Communication Foundation (WCF)와 함께 사용 하도록 IIS 7.0를 구성 하 고 필요한 구성 요소를 확인 하는 방법에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-108">This topic discusses how to configure IIS 7.0 for use with Windows Communication Foundation (WCF) and determine which components are required.</span></span>

## <a name="minimal-installation-installing-was"></a><span data-ttu-id="76f0d-109">최소 설치: WAS 설치</span><span class="sxs-lookup"><span data-stu-id="76f0d-109">Minimal Installation: Installing WAS</span></span>

 <span data-ttu-id="76f0d-110">전체 IIS 7.0 패키지의 최소 설치는 WAS (Windows Process Activation Service)를 설치 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-110">The minimal installation of the whole IIS 7.0 package is to install the Windows Process Activation Service (WAS).</span></span> <span data-ttu-id="76f0d-111">WAS는 독립 실행형 기능이 며, 모든 Windows Vista 운영 체제 (Home Basic, Home Premium, Business, Ultimate 및 Enterprise)에서 사용할 수 있는 IIS 7.0의 유일한 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-111">WAS is a standalone feature and it is the only feature from the IIS 7.0 that is available for all Windows Vista operating systems (Home Basic, Home Premium, Business, and Ultimate and Enterprise).</span></span>

 <span data-ttu-id="76f0d-112">제어판에서 **프로그램** 을 클릭 한 다음 **프로그램 및 기능** 아래에 나열 된 **Windows 기능 사용/사용 안 함** 을 클릭 합니다. 다음 그림과 같이 WAS 구성 요소가 목록에 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-112">From the Control Panel, click **Programs** and then click **Turn Windows features on or off** which is listed under **Programs and Features**, the WAS component is shown in the list as in the following illustration.</span></span>

 <span data-ttu-id="76f0d-113">![Windows 기능 사용/사용 안 함 대화 상자](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span><span class="sxs-lookup"><span data-stu-id="76f0d-113">![Turn Features On or Off Dialog](media/wcfc-turnfeaturesonoroffs.gif "wcfc_TurnFeaturesOnOrOffs")</span></span>

 <span data-ttu-id="76f0d-114">이 기능에는 다음과 같은 하위 구성 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-114">This feature has the following sub-components:</span></span>

- <span data-ttu-id="76f0d-115">.NET 환경</span><span class="sxs-lookup"><span data-stu-id="76f0d-115">.NET Environment</span></span>

- <span data-ttu-id="76f0d-116">구성 API</span><span class="sxs-lookup"><span data-stu-id="76f0d-116">Configuration APIs</span></span>

- <span data-ttu-id="76f0d-117">프로세스 모델</span><span class="sxs-lookup"><span data-stu-id="76f0d-117">Process Model</span></span>

 <span data-ttu-id="76f0d-118">WAS의 루트 노드를 선택 하면 **프로세스 모델** 하위 노드만 기본적으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-118">If you select the root node of WAS, only the **Process Model** sub-node is checked by default.</span></span> <span data-ttu-id="76f0d-119">이 설치에서는 웹 서버에 대한 지원이 없으므로 WAS만 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-119">Please note that with this installation you are only installing WAS, because there is no support for a Web server.</span></span>

 <span data-ttu-id="76f0d-120">WCF 또는 ASP.NET 응용 프로그램을 작동 시키려면 **.Net 환경** 확인란을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-120">To make WCF or any ASP.NET application work, check the **.NET Environment** checkbox.</span></span> <span data-ttu-id="76f0d-121">즉, WCF 및 ASP.NET가 제대로 작동 하도록 하기 위해서는 모든 WAS 구성 요소가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-121">This means that all of WAS components are required to make WCF and ASP.NET to work well.</span></span> <span data-ttu-id="76f0d-122">이러한 구성 요소는 일단 설치되면 자동으로 선택됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-122">These are automatically checked once you install any of those components.</span></span>

## <a name="iis-70-default-installation"></a><span data-ttu-id="76f0d-123">IIS 7.0: 기본 설치</span><span class="sxs-lookup"><span data-stu-id="76f0d-123">IIS 7.0: Default Installation</span></span>

 <span data-ttu-id="76f0d-124">**인터넷 정보 서비스** 기능을 확인 하면 다음 그림과 같이 일부 하위 노드가 자동으로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-124">By checking the **Internet Information Services** feature, some of the sub-nodes are automatically checked as shown in the following illustration.</span></span>

 <span data-ttu-id="76f0d-125">![IIS 7.0 기능에 대한 기본 설정](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span><span class="sxs-lookup"><span data-stu-id="76f0d-125">![Default settings for IIS 7.0 features](media/wcfc-turningfeaturesonoroff2.gif "wcfc_TurningFeaturesOnOrOff2")</span></span>

 <span data-ttu-id="76f0d-126">이는 IIS 7.0의 기본 설치입니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-126">This is the default installation of IIS 7.0.</span></span> <span data-ttu-id="76f0d-127">이 설치에서는 IIS 7.0를 사용 하 여 정적 콘텐츠 (예: HTML 페이지 및 기타 콘텐츠)를 서비스 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-127">With this installation, you can use IIS 7.0 to service static content (such as HTML pages and other content).</span></span> <span data-ttu-id="76f0d-128">그러나 ASP.NET 또는 CGI 응용 프로그램을 실행 하거나 WCF 서비스를 호스트할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-128">However, you cannot run ASP.NET or CGI applications or host WCF services.</span></span>

## <a name="iis-70-installation-with-aspnet-support"></a><span data-ttu-id="76f0d-129">IIS 7.0: ASP.NET 지원과 함께 설치</span><span class="sxs-lookup"><span data-stu-id="76f0d-129">IIS 7.0: Installation with ASP.NET Support</span></span>

 <span data-ttu-id="76f0d-130">IIS 7.0에서 ASP.NET 작업을 수행 하려면 ASP.NET를 설치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-130">You must install ASP.NET to make ASP.NET work on IIS 7.0.</span></span> <span data-ttu-id="76f0d-131">**ASP.NET** 를 확인 한 후 화면은 다음 그림과 같이 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-131">After checking **ASP.NET**, your screen should look like the following illustration.</span></span>

 <span data-ttu-id="76f0d-132">![ASP.NET 필수 설정](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span><span class="sxs-lookup"><span data-stu-id="76f0d-132">![Asp.NET required settings](media/wcfc-trunfeaturesonoroff3s.gif "wcfc_TrunFeaturesOnOrOFf3s")</span></span>

 <span data-ttu-id="76f0d-133">이는 IIS 7.0에서 WCF 및 ASP.NET 응용 프로그램이 작동 하는 최소 환경입니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-133">This is the minimal environment for both WCF and ASP.NET applications to work in IIS 7.0.</span></span>

## <a name="iis-70-installation-with-iis-60-compatibility-components"></a><span data-ttu-id="76f0d-134">IIS 7.0: IIS 6.0 호환성 구성 요소와 함께 설치</span><span class="sxs-lookup"><span data-stu-id="76f0d-134">IIS 7.0: Installation with IIS 6.0 Compatibility Components</span></span>

 <span data-ttu-id="76f0d-135">Visual Studio 2005를 사용 하는 시스템 또는 iis 6.0 메타 베이스 API를 사용 하는 가상 응용 프로그램을 구성 하는 기타 자동화 스크립트나 도구 (예: Adsutil.vbs)에 IIS 7.0를 설치할 경우 IIS 6.0 **스크립팅 도구** 를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-135">When installing IIS 7.0 on a system with Visual Studio 2005 or some other automation scripts or tools (such as Adsutil.vbs) that configure virtual applications that use IIS 6.0 Metabase API, ensure that you check the IIS 6.0 **Scripting Tools**.</span></span> <span data-ttu-id="76f0d-136">그러면 IIS 6.0 **관리 호환성** 의 다른 하위 노드가 자동으로 확인 됩니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-136">This automatically checks the other sub-nodes of IIS 6.0 **Management Compatibility**.</span></span> <span data-ttu-id="76f0d-137">다음 그림에서는이 작업을 수행한 후의 화면을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-137">The following illustration shows the screen after this is done:</span></span>

 <span data-ttu-id="76f0d-138">![IIS 6.0 관리 호환성 설정](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span><span class="sxs-lookup"><span data-stu-id="76f0d-138">![IIS 6.0 Management Compatibility Settings](media/scfc-turnfeaturesonoroff5s.gif "scfc_TurnFeaturesOnOrOff5s")</span></span>

 <span data-ttu-id="76f0d-139">이 설치에서는 웹에서 사용할 수 있는 IIS 7.0, ASP.NET 및 WCF 기능과 샘플을 사용 하는 데 필요한 모든 것이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-139">With this installation, you have everything required to use IIS 7.0, ASP.NET and WCF features and samples available on the Web.</span></span>

## <a name="request-limits"></a><span data-ttu-id="76f0d-140">요청 제한</span><span class="sxs-lookup"><span data-stu-id="76f0d-140">Request Limits</span></span>

 <span data-ttu-id="76f0d-141">Windows Vista with IIS 7에서는 `maxUri` 및 설정의 기본값이 `maxQueryStringSize` 변경 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-141">On Windows Vista with IIS 7 the default value of the `maxUri` and `maxQueryStringSize` settings have been changed.</span></span> <span data-ttu-id="76f0d-142">기본적으로 IIS 7.0의 요청 필터링은 URL 길이로 4096자를 허용하며 쿼리 문자열 길이로 2048자를 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-142">By default, request filtering in IIS 7.0 allows a URL length of 4096 characters and a query string length of 2048 characters.</span></span> <span data-ttu-id="76f0d-143">이러한 기본값을 변경하려면 다음 XML을 App.config 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="76f0d-143">To change these defaults add the following XML to your App.config file.</span></span>

```xml
 <system.webServer>
    <security>
        <requestFiltering>
            <requestLimits maxUrl="8192" maxQueryString="8192" />
        </requestFiltering>
    </security>
 </system.webServer>
 ```

## <a name="see-also"></a><span data-ttu-id="76f0d-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="76f0d-144">See also</span></span>

- [<span data-ttu-id="76f0d-145">WAS Activation 아키텍처</span><span class="sxs-lookup"><span data-stu-id="76f0d-145">WAS Activation Architecture</span></span>](was-activation-architecture.md)
- [<span data-ttu-id="76f0d-146">WCF에서 사용하도록 WAS 구성</span><span class="sxs-lookup"><span data-stu-id="76f0d-146">Configuring WAS for Use with WCF</span></span>](configuring-the-wpa--service-for-use-with-wcf.md)
- [<span data-ttu-id="76f0d-147">방법: WCF 활성화 구성 요소 설치 및 구성</span><span class="sxs-lookup"><span data-stu-id="76f0d-147">How to: Install and Configure WCF Activation Components</span></span>](how-to-install-and-configure-wcf-activation-components.md)
- <span data-ttu-id="76f0d-148">[Windows Server App Fabric 호스팅 기능](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="76f0d-148">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
