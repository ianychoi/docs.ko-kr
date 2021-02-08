---
description: '자세한 정보: 빠른 시작 (WCF Data Services)'
title: 빠른 시작(WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, quick-start example
- WCF Data Services, Entity Data Model (EDM) service
ms.assetid: 7b18ca1e-d4d6-4c7a-afb9-ce3cebb98a8d
ms.openlocfilehash: 92a1b8882f6a7db2ed33f032ad434efd06400421
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794951"
---
# <a name="quickstart-wcf-data-services"></a><span data-ttu-id="d9593-103">빠른 시작(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d9593-103">Quickstart (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="d9593-104">이 빠른 시작을 사용 하면 [시작](getting-started-with-wcf-data-services.md)의 항목을 지 원하는 일련의 작업을 통해 WCF Data Services 및 Open Data Protocol (OData)에 익숙해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-104">This quickstart helps you become familiar with WCF Data Services and the Open Data Protocol (OData) through a series of tasks that support the topics in [Getting Started](getting-started-with-wcf-data-services.md).</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="d9593-105">학습할 내용</span><span class="sxs-lookup"><span data-stu-id="d9593-105">What you'll learn</span></span>

<span data-ttu-id="d9593-106">이 빠른 시작의 첫 번째 작업에서는 Northwind 샘플 데이터베이스에서 OData 피드를 노출 하는 데이터 서비스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-106">The first task in this quickstart shows how to create a data service to expose an OData feed from the Northwind sample database.</span></span> <span data-ttu-id="d9593-107">이후 항목에서는 웹 브라우저를 사용 하 여 OData 피드에 액세스 하 고 클라이언트 라이브러리를 사용 하 여 OData 피드를 사용 하는 Windows Presentation Foundation (WPF) 클라이언트 응용 프로그램도 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-107">In later topics, you will access the OData feed by using a Web browser, and also create a Windows Presentation Foundation (WPF) client application that consumes the OData feed by using client libraries.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d9593-108">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="d9593-108">Prerequisites</span></span>

<span data-ttu-id="d9593-109">이 빠른 시작을 완료 하려면 다음 구성 요소를 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-109">To complete this quickstart, install the following components:</span></span>

- <span data-ttu-id="d9593-110">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d9593-110">Visual Studio</span></span>

- <span data-ttu-id="d9593-111">SQL Server 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-111">An instance of SQL Server.</span></span> <span data-ttu-id="d9593-112">여기에는 visual studio 2015의 기본 설치에 포함 되거나 Visual Studio 2017 이상에서 **데이터 저장소 및 처리** 워크 로드의 일부로 포함 되는 SQL Server Express 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-112">This includes SQL Server Express, which is included in a default installation of Visual Studio 2015, or as part of the **Data storage and processing** workload in Visual Studio 2017 or later.</span></span>

- <span data-ttu-id="d9593-113">Northwind 샘플 데이터베이스</span><span class="sxs-lookup"><span data-stu-id="d9593-113">The Northwind sample database.</span></span> <span data-ttu-id="d9593-114">데이터베이스를 설치 하려면 [Northwind 및 pubs 예제 데이터베이스에서 Microsoft SQL Server에 대 한](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)transact-sql 스크립트를 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-114">To install the database, run the Transact-SQL script from [Northwind and pubs sample databases for Microsoft SQL Server](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs).</span></span>

## <a name="wcf-data-services-quickstart-tasks"></a><span data-ttu-id="d9593-115">WCF data services 빠른 시작 작업</span><span class="sxs-lookup"><span data-stu-id="d9593-115">WCF data services quickstart tasks</span></span>

 [<span data-ttu-id="d9593-116">데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="d9593-116">Create the Data Service</span></span>](creating-the-data-service.md)

 <span data-ttu-id="d9593-117">ASP.NET 애플리케이션과 데이터 모델을 정의하고, 데이터 서비스를 만들고, 리소스에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-117">Define the ASP.NET application, define the data model, create the data service, and enable access to resources.</span></span>

 [<span data-ttu-id="d9593-118">웹 브라우저에서 서비스 액세스</span><span class="sxs-lookup"><span data-stu-id="d9593-118">Access the Service from a Web Browser</span></span>](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

 <span data-ttu-id="d9593-119">Visual Studio에서 서비스를 시작하고 웹 브라우저를 통해 HTTP GET 요청을 노출된 피드로 전송하여 서비스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-119">Start the service from Visual Studio and access the service by submitting HTTP GET requests through a Web browser to the exposed feed.</span></span>

 [<span data-ttu-id="d9593-120">.NET Framework 클라이언트 응용 프로그램 만들기</span><span class="sxs-lookup"><span data-stu-id="d9593-120">Create the .NET Framework Client Application</span></span>](creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

 <span data-ttu-id="d9593-121">OData 피드를 사용 하 고, 데이터를 Windows 컨트롤에 바인딩하고, 바인딩된 컨트롤의 데이터를 변경 하 고, 변경 내용을 데이터 서비스로 다시 전송 하는 WPF 앱을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-121">Create a WPF app to consume the OData feed, bind data to Windows controls, change data in the bound controls, and then send the changes back to the data service.</span></span>

> [!NOTE]
> <span data-ttu-id="d9593-122">완료 된 빠른 시작 버전의 프로젝트 파일은 [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client))에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d9593-122">Project files from a completed version of the quickstart can be downloaded from [GitHub](https://github.com/microsoftarchive/msdn-code-gallery-community-s-z/tree/master/WCF%20Data%20Services%20Quickstart%20(OData%20Service%20and%20WPF%20Client)).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d9593-123">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d9593-123">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d9593-124">빠른 시작 시작</span><span class="sxs-lookup"><span data-stu-id="d9593-124">Start the quickstart</span></span>](creating-the-data-service.md)

## <a name="see-also"></a><span data-ttu-id="d9593-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d9593-125">See also</span></span>

- [<span data-ttu-id="d9593-126">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d9593-126">ADO.NET Entity Framework</span></span>](../adonet/ef/index.md)
