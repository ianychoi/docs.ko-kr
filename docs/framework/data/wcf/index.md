---
title: WCF Data Services 4.5
description: REST 의미 체계를 사용 하 여 데이터를 노출 하 고 사용 하는 서비스를 지 원하는 .NET Framework 구성 요소인 WCF Data Services에 대해 알아봅니다.
ms.date: 03/30/2017
helpviewer_keywords:
- Astoria
- WCF Data Services, getting started
ms.assetid: 73d2bec3-7c92-4110-b905-11bb0462357a
ms.openlocfilehash: 2d3da2ca9cd958fc70d3b91362dde71d68dc9d8a
ms.sourcegitcommit: 8299abfbd5c49b596d61f1e4d09bc6b8ba055b36
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/27/2021
ms.locfileid: "98898760"
---
# <a name="wcf-data-services-45"></a><span data-ttu-id="4c1ad-103">WCF Data Services 4.5</span><span class="sxs-lookup"><span data-stu-id="4c1ad-103">WCF Data Services 4.5</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

## <a name="overview"></a><span data-ttu-id="4c1ad-104">개요</span><span class="sxs-lookup"><span data-stu-id="4c1ad-104">Overview</span></span>

<span data-ttu-id="4c1ad-105">WCF Data Services (이전의 "ADO.NET Data Services")는 [Representational State Transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)의 의미 체계를 사용 하 여 웹 또는 인트라넷을 통해 데이터를 노출 하 고 사용 하기 위해 Open Data Protocol (OData)를 사용 하는 서비스를 만들 수 있는 .NET Framework의 구성 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-105">WCF Data Services (formerly known as "ADO.NET Data Services") is a component of the .NET Framework that enables you to create services that use the Open Data Protocol (OData) to expose and consume data over the Web or intranet by using the semantics of [representational state transfer (REST)](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm).</span></span> <span data-ttu-id="4c1ad-106">OData는 URI로 주소를 지정할 수 있는 리소스로 데이터를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-106">OData exposes data as resources that are addressable by URIs.</span></span> <span data-ttu-id="4c1ad-107">데이터는 표준 HTTP 동사인 GET, PUT, POST 및 DELETE를 사용하여 액세스되고 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-107">Data is accessed and changed by using standard HTTP verbs of GET, PUT, POST, and DELETE.</span></span> <span data-ttu-id="4c1ad-108">OData는 [엔터티 데이터 모델](../adonet/entity-data-model.md) 의 엔터티-관계 규칙을 사용 하 여 리소스를 연결로 관련 된 엔터티 집합으로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-108">OData uses the entity-relationship conventions of the [Entity Data Model](../adonet/entity-data-model.md) to expose resources as sets of entities that are related by associations.</span></span>

<span data-ttu-id="4c1ad-109">WCF Data Services는 OData 프로토콜을 사용 하 여 리소스의 주소를 지정 하 고 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-109">WCF Data Services uses the OData protocol for addressing and updating resources.</span></span> <span data-ttu-id="4c1ad-110">이러한 방식으로 OData를 지 원하는 모든 클라이언트에서 이러한 서비스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-110">In this way, you can access these services from any client that supports OData.</span></span> <span data-ttu-id="4c1ad-111">OData를 사용 하면 데이터를 XML로 교환 및 업데이트 하기 위한 표준 집합인 Atom, AJAX 응용 프로그램에서 광범위 하 게 사용 되는 텍스트 기반 데이터 교환 형식인 JavaScript Object Notation (JSON)와 같이 잘 알려진 전송 형식을 사용 하 여 리소스를 요청 하 고 리소스에 데이터를 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-111">OData enables you to request and write data to resources by using well-known transfer formats: Atom, a set of standards for exchanging and updating data as XML, and JavaScript Object Notation (JSON), a text-based data exchange format used extensively in AJAX applications.</span></span>

<span data-ttu-id="4c1ad-112">WCF Data Services는 다양 한 원본에서 가져온 데이터를 OData 피드로 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-112">WCF Data Services can expose data that originates from various sources as OData feeds.</span></span> <span data-ttu-id="4c1ad-113">Visual Studio 도구를 사용 하면 ADO.NET Entity Framework 데이터 모델을 사용 하 여 OData 기반 서비스를 쉽게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-113">Visual Studio tools make it easier for you to create an OData-based service by using an ADO.NET Entity Framework data model.</span></span> <span data-ttu-id="4c1ad-114">CLR (공용 언어 런타임) 클래스와 런타임에 바인딩된 데이터 나 형식화 되지 않은 데이터를 기반으로 하 여 OData 피드를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-114">You can also create OData feeds based on common language runtime (CLR) classes and even late-bound or un-typed data.</span></span>

<span data-ttu-id="4c1ad-115">또한 WCF Data Services에는 클라이언트 라이브러리 집합, 일반 .NET Framework 클라이언트 응용 프로그램 및 Silverlight 기반 응용 프로그램용 기타 기능이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-115">WCF Data Services also includes a set of client libraries, one for general .NET Framework client applications and another specifically for Silverlight-based applications.</span></span> <span data-ttu-id="4c1ad-116">이러한 클라이언트 라이브러리는 .NET Framework 및 Silverlight와 같은 환경에서 OData 피드에 액세스할 때 개체 기반 프로그래밍 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-116">These client libraries provide an object-based programming model when you access an OData feed from environments such as the .NET Framework and Silverlight.</span></span>

## <a name="where-should-i-start"></a><span data-ttu-id="4c1ad-117">시작 지점</span><span class="sxs-lookup"><span data-stu-id="4c1ad-117">Where Should I Start?</span></span>

<span data-ttu-id="4c1ad-118">관심 사항에 따라 다음 항목 중 하나를 사용 하 여 WCF Data Services 시작 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-118">Depending on your interests, consider getting started with WCF Data Services in one of the following topics.</span></span>

<span data-ttu-id="4c1ad-119">바로 시작...</span><span class="sxs-lookup"><span data-stu-id="4c1ad-119">I want to jump right in...</span></span>

- [<span data-ttu-id="4c1ad-120">빠른 시작</span><span class="sxs-lookup"><span data-stu-id="4c1ad-120">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-121">시작</span><span class="sxs-lookup"><span data-stu-id="4c1ad-121">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="4c1ad-122">코드를 표시 하기만 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-122">Just show me some code...</span></span>

- [<span data-ttu-id="4c1ad-123">빠른 시작</span><span class="sxs-lookup"><span data-stu-id="4c1ad-123">Quickstart</span></span>](quickstart-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-124">방법: 데이터 서비스 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="4c1ad-124">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-125">방법: Windows Presentation Foundation 요소에 데이터 바인딩</span><span class="sxs-lookup"><span data-stu-id="4c1ad-125">How to: Bind Data to Windows Presentation Foundation Elements</span></span>](bind-data-to-wpf-elements-wcf-data-services.md)

<span data-ttu-id="4c1ad-126">OData에 대 한 자세한 내용을 확인 하려면 ...</span><span class="sxs-lookup"><span data-stu-id="4c1ad-126">I want to know more about OData...</span></span>

- [<span data-ttu-id="4c1ad-127">백서: OData 소개</span><span class="sxs-lookup"><span data-stu-id="4c1ad-127">White paper: Introducing OData</span></span>](https://download.microsoft.com/download/E/5/A/E5A59052-EE48-4D64-897B-5F7C608165B8/IntroducingOData.pdf)
- [<span data-ttu-id="4c1ad-128">웹 사이트 Open Data Protocol</span><span class="sxs-lookup"><span data-stu-id="4c1ad-128">Open Data Protocol website</span></span>](https://www.odata.org/)
- [<span data-ttu-id="4c1ad-129">OData: SDK</span><span class="sxs-lookup"><span data-stu-id="4c1ad-129">OData: SDK</span></span>](https://www.odata.org/ecosystem/)

<span data-ttu-id="4c1ad-130">종단 간 샘플을 확인 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-130">I want to see end-to-end samples...</span></span>

- <span data-ttu-id="4c1ad-131">[WCF Data Services 빠른 시작](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span><span class="sxs-lookup"><span data-stu-id="4c1ad-131">[WCF Data Services Quickstart](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))</span></span>
- [<span data-ttu-id="4c1ad-132">OData SDK-샘플 코드</span><span class="sxs-lookup"><span data-stu-id="4c1ad-132">OData SDK - Sample Code</span></span>](https://www.odata.org/ecosystem/#sdk)

<span data-ttu-id="4c1ad-133">Visual Studio와의 통합 방식</span><span class="sxs-lookup"><span data-stu-id="4c1ad-133">How does it integrate with Visual Studio?</span></span>

- [<span data-ttu-id="4c1ad-134">데이터 서비스 클라이언트 라이브러리 생성</span><span class="sxs-lookup"><span data-stu-id="4c1ad-134">Generating the Data Service Client Library</span></span>](generating-the-data-service-client-library-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-135">데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="4c1ad-135">Creating the Data Service</span></span>](creating-the-data-service.md)

- [<span data-ttu-id="4c1ad-136">Entity Framework 공급자</span><span class="sxs-lookup"><span data-stu-id="4c1ad-136">Entity Framework Provider</span></span>](entity-framework-provider-wcf-data-services.md)

<span data-ttu-id="4c1ad-137">Privileged Identity Management로 무엇을 할 수 있나요?</span><span class="sxs-lookup"><span data-stu-id="4c1ad-137">What can I do with it?</span></span>

- [<span data-ttu-id="4c1ad-138">개요</span><span class="sxs-lookup"><span data-stu-id="4c1ad-138">Overview</span></span>](wcf-data-services-overview.md)

- [<span data-ttu-id="4c1ad-139">응용 프로그램 시나리오</span><span class="sxs-lookup"><span data-stu-id="4c1ad-139">Application Scenarios</span></span>](application-scenarios-wcf-data-services.md)

<span data-ttu-id="4c1ad-140">LINQ를 사용 하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-140">I want to use LINQ...</span></span>

- [<span data-ttu-id="4c1ad-141">데이터 서비스 쿼리</span><span class="sxs-lookup"><span data-stu-id="4c1ad-141">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-142">LINQ 고려 사항</span><span class="sxs-lookup"><span data-stu-id="4c1ad-142">LINQ Considerations</span></span>](linq-considerations-wcf-data-services.md)

- [<span data-ttu-id="4c1ad-143">방법: 데이터 서비스 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="4c1ad-143">How to: Execute Data Service Queries</span></span>](how-to-execute-data-service-queries-wcf-data-services.md)

<span data-ttu-id="4c1ad-144">추가 정보가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-144">I still need some more information...</span></span>

- [<span data-ttu-id="4c1ad-145">WCF Data Services 팀 블로그</span><span class="sxs-lookup"><span data-stu-id="4c1ad-145">WCF Data Services Team Blog</span></span>](/archive/blogs/astoriateam/)

- [<span data-ttu-id="4c1ad-146">리소스</span><span class="sxs-lookup"><span data-stu-id="4c1ad-146">Resources</span></span>](wcf-data-services-resources.md)

## <a name="in-this-section"></a><span data-ttu-id="4c1ad-147">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="4c1ad-147">In This Section</span></span>

[<span data-ttu-id="4c1ad-148">개요</span><span class="sxs-lookup"><span data-stu-id="4c1ad-148">Overview</span></span>](wcf-data-services-overview.md)

<span data-ttu-id="4c1ad-149">WCF Data Services에서 사용 가능한 기능에 대 한 개요를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-149">Provides an overview of the features and functionality available in WCF Data Services.</span></span>

<span data-ttu-id="4c1ad-150">[WCF Data Services 5.0의 새로운 기능](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span><span class="sxs-lookup"><span data-stu-id="4c1ad-150">[What's New in WCF Data Services 5.0](/previous-versions/dotnet/wcf-data-services/ee373845(v=vs.103))</span></span>

<span data-ttu-id="4c1ad-151">WCF Data Services의 새로운 기능 및 새로운 OData 기능에 대 한 지원을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-151">Describes new functionality in WCF Data Services and support for new OData features.</span></span>

[<span data-ttu-id="4c1ad-152">시작</span><span class="sxs-lookup"><span data-stu-id="4c1ad-152">Getting Started</span></span>](getting-started-with-wcf-data-services.md)

<span data-ttu-id="4c1ad-153">WCF Data Services를 사용 하 여 OData 피드를 노출 하 고 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-153">Describes how to expose and consume OData feeds by using WCF Data Services.</span></span>

[<span data-ttu-id="4c1ad-154">WCF Data Services 정의</span><span class="sxs-lookup"><span data-stu-id="4c1ad-154">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)

<span data-ttu-id="4c1ad-155">OData 피드를 노출 하는 데이터 서비스를 만들고 구성 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-155">Describes how to create and configure a data service that exposes OData feeds.</span></span>

[<span data-ttu-id="4c1ad-156">WCF Data Services 클라이언트 라이브러리</span><span class="sxs-lookup"><span data-stu-id="4c1ad-156">WCF Data Services Client Library</span></span>](wcf-data-services-client-library.md)

<span data-ttu-id="4c1ad-157">클라이언트 라이브러리를 사용 하 여 .NET Framework 클라이언트 응용 프로그램에서 OData 피드를 사용 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="4c1ad-157">Describes how to use client libraries to consume OData feeds from a .NET Framework client application.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c1ad-158">추가 정보</span><span class="sxs-lookup"><span data-stu-id="4c1ad-158">See also</span></span>

- [<span data-ttu-id="4c1ad-159">REST(Representational State Transfer)</span><span class="sxs-lookup"><span data-stu-id="4c1ad-159">Representational State Transfer (REST)</span></span>](https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm)
