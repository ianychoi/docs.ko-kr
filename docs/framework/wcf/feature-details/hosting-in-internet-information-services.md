---
description: '자세한 정보: 호스트의 호스트 인터넷 정보 서비스'
title: 인터넷 정보 서비스에서의 호스팅
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 23c81bcfccba316500d333d277907d66e5d457c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743137"
---
# <a name="host-in-internet-information-services"></a><span data-ttu-id="24fa2-103">인터넷 정보 서비스 호스트</span><span class="sxs-lookup"><span data-stu-id="24fa2-103">Host in Internet Information Services</span></span>

<span data-ttu-id="24fa2-104">WCF (Windows Communication Foundation) 서비스를 호스팅하는 한 가지 옵션은 인터넷 정보 서비스 (IIS) 응용 프로그램 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-104">One option for hosting Windows Communication Foundation (WCF) services is inside of an Internet Information Services (IIS) application.</span></span> <span data-ttu-id="24fa2-105">이 호스팅 모델은 ASMX (ASP.NET and ASP.NET Web services) 웹 서비스에서 사용 하는 모델과 유사 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-105">This hosting model is similar to the model used by ASP.NET and ASP.NET Web services (ASMX) Web Services.</span></span>

## <a name="versions-of-iis"></a><span data-ttu-id="24fa2-106">IIS 버전</span><span class="sxs-lookup"><span data-stu-id="24fa2-106">Versions of IIS</span></span>

<span data-ttu-id="24fa2-107">WCF는 다음 운영 체제에 대해 다음 버전의 IIS에서 호스팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-107">WCF can be hosted on the following versions of IIS on the following operating systems:</span></span>

- <span data-ttu-id="24fa2-108">Windows XP s p 2의 IIS 5.1.</span><span class="sxs-lookup"><span data-stu-id="24fa2-108">IIS 5.1 on Windows XP SP2.</span></span> <span data-ttu-id="24fa2-109">이 환경은 나중에 Windows Server 2003와 같은 서버 운영 체제에 배포 되는 IIS에서 호스팅되는 응용 프로그램을 디자인 하 고 개발 하는 데 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-109">This environment is useful for the design and development of IIS-hosted applications that are later deployed on a server operating system such as Windows Server 2003.</span></span>

- <span data-ttu-id="24fa2-110">Windows Server 2003의 IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="24fa2-110">IIS 6.0 on Windows Server 2003.</span></span> <span data-ttu-id="24fa2-111">IIS 6.0은 향상된 확장성, 안정성 및 응용 프로그램 격리 기능을 제공하는 고급 프로세스 모델을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-111">IIS 6.0 provides an advanced process model that offers improved scalability, reliability, and application isolation.</span></span> <span data-ttu-id="24fa2-112">이 환경은 HTTP 통신을 독점적으로 사용 하는 WCF 서비스의 프로덕션 배포에 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-112">This environment is suitable for production deployment of WCF services that use HTTP communication exclusively.</span></span>

- <span data-ttu-id="24fa2-113">Windows Vista 및 Windows Server 2008의 IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="24fa2-113">IIS 7.0 on Windows Vista and Windows Server 2008.</span></span> <span data-ttu-id="24fa2-114">IIS 7.0는 IIS 6.0와 동일한 고급 프로세스 모델을 제공 하지만 WAS (Windows Process Activation Service)를 사용 하 여 HTTP 이외의 프로토콜을 통해 활성화 및 네트워크 통신을 허용 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-114">IIS 7.0 provides the same advanced process model as IIS 6.0, but uses the Windows Process Activation Service (WAS) to allow activation and network communication over protocols other than HTTP.</span></span> <span data-ttu-id="24fa2-115">이 환경은 WCF에서 지원 되는 모든 네트워크 프로토콜 (HTTP, net.tcp, net.pipe 및 net.pipe 포함)을 통해 통신 하는 WCF 서비스를 개발 하는 데 적합 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-115">This environment is suitable for the development of WCF services that communicate over any network protocol supported by WCF (including HTTP, net.tcp, net.pipe, and net.msmq).</span></span> <span data-ttu-id="24fa2-116">WAS에 대 한 자세한 내용은 [Windows Process Activation Service에서 호스팅](hosting-in-windows-process-activation-service.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24fa2-116">For more information about WAS, see [Hosting in Windows Process Activation Service](hosting-in-windows-process-activation-service.md).</span></span>

- <span data-ttu-id="24fa2-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) 은 IIS 7.0 및 WAS (Windows Process Activation Service)를 사용 하 여 여 net4 WCF 및 WF 서비스를 위한 풍부한 응용 프로그램 호스팅 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-117">[Windows Server AppFabric](/previous-versions/appfabric/ff384253(v=azure.10)) works with IIS 7.0 and Windows Process Activation Service (WAS) to provide a rich application hosting environment for NET4 WCF and WF services.</span></span> <span data-ttu-id="24fa2-118">이러한 기능에는 프로세스 수명 주기 관리, 프로세스 재활용, 공유 호스팅, 빠른 오류 보호, 프로세스 분리, 요청 시 활성화, 상태 모니터링 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-118">These benefits include process life-cycle management, process recycling, shared hosting, rapid failure protection, process orphaning, on-demand activation, and health monitoring.</span></span> <span data-ttu-id="24fa2-119">자세한 내용은 [Appfabric 호스팅 기능](/previous-versions/appfabric/ee677189(v=azure.10)) 및 [appfabric 호스팅 개념](/previous-versions/appfabric/ee677371(v=azure.10))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24fa2-119">For detailed information, see [AppFabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10)) and [AppFabric Hosting Concepts](/previous-versions/appfabric/ee677371(v=azure.10)).</span></span>

## <a name="benefits-of-iis-hosting"></a><span data-ttu-id="24fa2-120">IIS 호스팅의 이점</span><span class="sxs-lookup"><span data-stu-id="24fa2-120">Benefits of IIS hosting</span></span>

<span data-ttu-id="24fa2-121">IIS에서 WCF 서비스를 호스팅하면 다음과 같은 여러 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-121">Hosting WCF services in IIS has several benefits:</span></span>

- <span data-ttu-id="24fa2-122">IIS에서 호스팅되는 WCF 서비스는 ASP.NET 응용 프로그램 및 ASMX를 비롯 한 다른 유형의 IIS 응용 프로그램과 마찬가지로 배포 및 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-122">WCF services hosted in IIS are deployed and managed like any other type of IIS application, including ASP.NET applications and ASMX.</span></span>

- <span data-ttu-id="24fa2-123">IIS는 프로세스 활성화, 상태 관리 및 재활용 기능을 제공하여 호스트된 애플리케이션의 신뢰성이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-123">IIS provides process activation, health management, and recycling capabilities to increase the reliability of hosted applications.</span></span>

- <span data-ttu-id="24fa2-124">ASP.NET와 마찬가지로 ASP.NET에서 호스트 되는 WCF 서비스는 서버 밀도 및 확장성 향상을 위해 여러 응용 프로그램이 공통 작업자 프로세스에 상주 하는 ASP.NET 공유 호스팅 모델을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-124">Like ASP.NET, WCF services hosted in ASP.NET can take advantage of the ASP.NET shared hosting model where multiple applications reside in a common worker process for improved server density and scalability.</span></span>

- <span data-ttu-id="24fa2-125">IIS에서 호스팅되는 WCF 서비스는 호스트 된 서비스의 개발 및 배포를 간소화 하는 ASP.NET 2.0와 동일한 동적 컴파일 모델을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-125">WCF services hosted in IIS use the same dynamic compilation model as ASP.NET 2.0, which simplifies development and deployment of hosted services.</span></span>

<span data-ttu-id="24fa2-126">IIS에서 WCF 서비스를 호스팅하도록 결정할 때 IIS 5.1 및 IIS 6.0은 HTTP 통신 으로만 제한 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-126">When deciding to host WCF services in IIS, it is important to remember that IIS 5.1 and IIS 6.0 are limited to HTTP communication only.</span></span> <span data-ttu-id="24fa2-127">호스팅 환경을 선택 하는 방법에 대 한 자세한 내용은 [호스팅 서비스](../hosting-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24fa2-127">For more information about choosing a hosting environment, see [Hosting Services](../hosting-services.md).</span></span>

## <a name="deploy-an-iis-hosted-wcf-service"></a><span data-ttu-id="24fa2-128">IIS에서 호스트 되는 WCF 서비스 배포</span><span class="sxs-lookup"><span data-stu-id="24fa2-128">Deploy an IIS-hosted WCF service</span></span>

<span data-ttu-id="24fa2-129">IIS에서 호스트 하는 WCF 서비스의 개발 및 배포는 다음과 같은 작업으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-129">Developing and deploying an IIS-hosted WCF service consists of the following tasks:</span></span>

- <span data-ttu-id="24fa2-130">IIS, ASP.NET, WCF 및 WCF HTTP 활성화 구성 요소가 제대로 설치 되 고 등록 되었는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-130">Ensure that IIS, ASP.NET, WCF, and the WCF HTTP activation component are correctly installed and registered.</span></span>

- <span data-ttu-id="24fa2-131">새 IIS 응용 프로그램을 만들거나 기존 ASP.NET 응용 프로그램을 다시 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-131">Create a new IIS application, or reuse an existing ASP.NET application.</span></span>

- <span data-ttu-id="24fa2-132">WCF 서비스에 대 한 .svc 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-132">Create a .svc file for the WCF service.</span></span>

- <span data-ttu-id="24fa2-133">IIS 애플리케이션에 서비스 구현을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-133">Deploy the service implementation to the IIS application.</span></span>

- <span data-ttu-id="24fa2-134">WCF 서비스를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-134">Configure the WCF service.</span></span>

<span data-ttu-id="24fa2-135">이러한 각 작업에 대 한 설명은 [WCF 서비스 Services-Hosted 인터넷 정보 배포](deploying-an-internet-information-services-hosted-wcf-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24fa2-135">For a discussion of each of these tasks, see [Deploying an Internet Information Services-Hosted WCF Service](deploying-an-internet-information-services-hosted-wcf-service.md).</span></span>

## <a name="wcf-services-and-aspnet"></a><span data-ttu-id="24fa2-136">WCF 서비스 및 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="24fa2-136">WCF services and ASP.NET</span></span>

<span data-ttu-id="24fa2-137">WCF 서비스는 서비스에서 ASP.NET 웹 응용 프로그램 플랫폼에서 제공 하는 기능을 모두 활용할 수 있는 ASP.NET 또는 ASP.NET 호환성 모드에서 함께 호스팅될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="24fa2-137">WCF services can be hosted either side-by-side with ASP.NET or in ASP.NET Compatibility Mode in which services can take full advantage of features provided by the ASP.NET Web application platform.</span></span> <span data-ttu-id="24fa2-138">이러한 기능에 대 한 설명은 [WCF 서비스 및 ASP.NET](wcf-services-and-aspnet.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="24fa2-138">For a discussion of these features, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="24fa2-139">참고 항목</span><span class="sxs-lookup"><span data-stu-id="24fa2-139">See also</span></span>

- [<span data-ttu-id="24fa2-140">ServiceHostFactory를 사용하여 호스팅 확장명</span><span class="sxs-lookup"><span data-stu-id="24fa2-140">Extending Hosting Using ServiceHostFactory</span></span>](../extending/extending-hosting-using-servicehostfactory.md)
- [<span data-ttu-id="24fa2-141">인터넷 정보 서비스에서 호스트하는 WCF 서비스 배포</span><span class="sxs-lookup"><span data-stu-id="24fa2-141">Deploying an Internet Information Services-Hosted WCF Service</span></span>](deploying-an-internet-information-services-hosted-wcf-service.md)
- [<span data-ttu-id="24fa2-142">WCF 서비스 및 ASP.NET</span><span class="sxs-lookup"><span data-stu-id="24fa2-142">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="24fa2-143">인터넷 정보 서비스 호스팅을 위한 최선의 방법</span><span class="sxs-lookup"><span data-stu-id="24fa2-143">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="24fa2-144">Windows Communication Foundation에 대해 Internet Information Services 7.0 구성</span><span class="sxs-lookup"><span data-stu-id="24fa2-144">Configuring Internet Information Services 7.0 for Windows Communication Foundation</span></span>](configuring-iis-for-wcf.md)
- <span data-ttu-id="24fa2-145">[Windows Server App Fabric 호스팅 기능](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="24fa2-145">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
