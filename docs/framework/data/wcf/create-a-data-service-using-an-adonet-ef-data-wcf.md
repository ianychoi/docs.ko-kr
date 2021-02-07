---
description: '자세한 정보: 방법: ADO.NET Entity Framework 데이터 소스를 사용 하 여 데이터 서비스 만들기 (WCF Data Services)'
title: '방법: ADO.NET Entity Framework 데이터 원본을 사용하여 데이터 서비스 만들기(WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: aea96c3953ec990b5f70a9702961512332330c6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766209"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="f0647-103">방법: ADO.NET Entity Framework 데이터 원본을 사용하여 데이터 서비스 만들기(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="f0647-103">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="f0647-104">WCF Data Services 엔터티 데이터를 데이터 서비스로 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-104">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="f0647-105">이 엔터티 데이터는 데이터 원본이 관계형 데이터베이스인 경우에 ADO. NETEntity Framework에서 제공 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-105">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="f0647-106">이 항목에서는 기존 데이터베이스를 기반으로 하는 Visual Studio 웹 애플리케이션에서 Entity Framework 기반 데이터 모델을 만들고 이 데이터 모델을 사용하여 새 데이터 서비스를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-106">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="f0647-107">Entity Framework는 Visual Studio 프로젝트 외부에서 Entity Framework 모델을 생성할 수 있는 명령줄 도구도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-107">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="f0647-108">자세한 내용은 [방법: EdmGen.exe를 사용 하 여 모델 및 매핑 파일 생성](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0647-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="f0647-109">기존 웹 애플리케이션에 기존 데이터베이스를 기반으로 하는 Entity Framework 모델을 추가하려면</span><span class="sxs-lookup"><span data-stu-id="f0647-109">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="f0647-110">**프로젝트** 메뉴에서   >  **새 항목** 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-110">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f0647-111">**템플릿** 창에서 **데이터** 범주를 클릭 한 다음 **ADO.NET 엔터티 데이터 모델** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-111">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="f0647-112">모델 이름을 입력 한 다음 **추가** 를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-112">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="f0647-113">엔터티 데이터 모델 마법사 시작 페이지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-113">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="f0647-114">**Model 콘텐츠 선택** 대화 상자에서 **데이터베이스에서 생성** 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-114">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="f0647-115">그런 후 **Next** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-115">Then click **Next**.</span></span>

5. <span data-ttu-id="f0647-116">**새 연결** 단추를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-116">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="f0647-117">**연결 속성** 대화 상자에서 서버 이름을 입력 하 고 인증 방법을 선택한 다음 데이터베이스 이름을 입력 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-117">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="f0647-118">**데이터 연결 선택** 대화 상자가 데이터베이스 연결 설정으로 업데이트 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-118">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="f0647-119">**App.Config에서 엔터티 연결 설정 저장:** 확인란을 선택 했는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-119">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="f0647-120">그런 후 **Next** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-120">Then click **Next**.</span></span>

8. <span data-ttu-id="f0647-121">**데이터베이스 개체 선택** 대화 상자에서 데이터 서비스에 노출할 데이터베이스 개체를 모두 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-121">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f0647-122">데이터 모델에 포함된 개체는 데이터 서비스에 의해 자동으로 노출되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-122">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="f0647-123">서비스 자체에서 해당 개체를 명시적으로 노출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-123">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="f0647-124">자세한 내용은 [데이터 서비스 구성](configuring-the-data-service-wcf-data-services.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-124">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="f0647-125">**마침** 을 클릭하여 마법사를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-125">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="f0647-126">특정 데이터베이스를 기반으로 하는 기본 데이터 모델이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-126">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="f0647-127">Entity Framework에서 데이터 모델을 사용하도록 설정하여 사용자 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-127">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="f0647-128">자세한 내용은 [엔터티 데이터 모델 도구 작업](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0647-128">For more information, see [Entity Data Model Tools Tasks](/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="f0647-129">새 데이터 모델을 사용하여 데이터 서비스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="f0647-129">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="f0647-130">Visual Studio에서 데이터 모델을 나타내는 .edmx 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-130">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="f0647-131">**모델 브라우저** 에서 모델을 마우스 오른쪽 단추로 클릭 하 고 **속성** 을 클릭 한 다음 엔터티 컨테이너의 이름을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-131">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="f0647-132">**솔루션 탐색기** 에서 ASP.NET 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 한 다음   >  **새 항목** 추가를 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-132">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="f0647-133">**새 항목 추가** 대화 상자의 **웹** 범주에서 **WCF 데이터 서비스** 템플릿을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-133">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Visual Studio 2015의 WCF 데이터 서비스 항목 템플릿](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="f0647-135">**WCF 데이터 서비스** 템플릿은 visual studio 2015 이상에서 사용할 수 있지만 visual studio 2017 이상에서는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

5. <span data-ttu-id="f0647-136">서비스의 이름을 입력 하 고 **확인** 을 클릭 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-136">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="f0647-137">Visual Studio에서 새 서비스의 XML 태그 및 코드 파일이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="f0647-138">기본적으로 코드 편집기 창이 열립니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-138">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="f0647-139">데이터 서비스 코드에서 데이터 서비스를 정의하는 클래스 정의의 `/* TODO: put your data source class name here */` 주석을 <xref:System.Data.Objects.ObjectContext> 클래스에서 상속되고 2단계에서 적어 둔 데이터 모델의 엔터티 컨테이너인 형식으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-139">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="f0647-140">데이터 서비스 코드에서 권한 있는 클라이언트가 데이터 서비스에서 노출하는 엔터티 집합에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0647-140">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="f0647-141">자세한 내용은 [데이터 서비스 만들기](creating-the-data-service.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f0647-141">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="f0647-142">웹 브라우저를 사용 하 여 Northwind 데이터 서비스를 테스트 하려면 [웹 브라우저에서 서비스 액세스](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)항목의 지침을 따르세요.</span><span class="sxs-lookup"><span data-stu-id="f0647-142">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f0647-143">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0647-143">See also</span></span>

- [<span data-ttu-id="f0647-144">WCF Data Services 정의</span><span class="sxs-lookup"><span data-stu-id="f0647-144">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
- [<span data-ttu-id="f0647-145">Data Services 공급자</span><span class="sxs-lookup"><span data-stu-id="f0647-145">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="f0647-146">방법: 리플렉션 공급자를 사용하여 데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="f0647-146">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="f0647-147">방법: LINQ to SQL 데이터 원본을 사용하여 데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="f0647-147">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
