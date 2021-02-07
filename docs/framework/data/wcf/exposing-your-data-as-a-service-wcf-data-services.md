---
description: '자세한 정보: 데이터를 서비스로 노출 (WCF Data Services)'
title: 서비스로 데이터 노출(WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 496cf18b264672814295916467e1bff93feebdde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765973"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a><span data-ttu-id="8346a-103">데이터를 서비스로 제공 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8346a-103">Expose Your Data as a Service (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="8346a-104">WCF Data Services는 Visual Studio와 통합 되므로 데이터를 OData (Open Data Protocol) 피드로 노출 하는 서비스를 보다 쉽게 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-104">WCF Data Services integrates with Visual Studio to enable you to more easily define services to expose your data as Open Data Protocol (OData) feeds.</span></span> <span data-ttu-id="8346a-105">OData 피드를 노출 하는 데이터 서비스를 만들려면 다음 기본 단계를 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-105">Creating a data service that exposes an OData feed involves the following basic steps:</span></span>

1. <span data-ttu-id="8346a-106">**데이터 모델을 정의 합니다.**</span><span class="sxs-lookup"><span data-stu-id="8346a-106">**Define the data model.**</span></span> <span data-ttu-id="8346a-107">WCF Data Services는 [ADO.NET Entity Framework](../adonet/ef/index.md)기반으로 하는 데이터 모델을 기본적으로 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-107">WCF Data Services natively supports data models that are based on the [ADO.NET Entity Framework](../adonet/ef/index.md).</span></span> <span data-ttu-id="8346a-108">자세한 내용은 [방법: ADO.NET Entity Framework 데이터 원본을 사용 하 여 데이터 서비스 만들기](create-a-data-service-using-an-adonet-ef-data-wcf.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8346a-108">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>

     <span data-ttu-id="8346a-109">또한 WCF Data Services는 인터페이스의 인스턴스를 반환 하는 CLR (공용 언어 런타임) 개체를 기반으로 하는 데이터 모델을 지원 <xref:System.Linq.IQueryable%601> 합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-109">WCF Data Services also supports data models that are based on common language runtime (CLR) objects that return an instance of the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="8346a-110">따라서 .NET Framework의 목록, 배열 및 컬렉션을 기반으로 하는 데이터 서비스를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-110">This enables you to deploy data services that are based on lists, arrays, and collections in the .NET Framework.</span></span> <span data-ttu-id="8346a-111">이러한 데이터 구조에 대해 만들기, 업데이트 및 삭제 작업을 수행하려면 <xref:System.Data.Services.IUpdatable> 인터페이스도 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-111">To enable create, update, and delete operations over these data structures, you must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="8346a-112">자세한 내용은 [방법: 리플렉션 공급자를 사용 하 여 데이터 서비스 만들기](create-a-data-service-using-rp-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8346a-112">For more information, see [How to: Create a Data Service Using the Reflection Provider](create-a-data-service-using-rp-wcf-data-services.md).</span></span>

     <span data-ttu-id="8346a-113">고급 시나리오를 위해 WCF Data Services에는 런타임에 바인딩된 데이터 형식을 기반으로 데이터 모델을 정의할 수 있는 공급자 집합이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-113">For more advanced scenarios, WCF Data Services includes a set of providers that enable you to define a data model based on late-bound data types.</span></span> <span data-ttu-id="8346a-114">자세한 내용은 [사용자 지정 데이터 서비스 공급자](custom-data-service-providers-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8346a-114">For more information, see [Custom Data Service Providers](custom-data-service-providers-wcf-data-services.md).</span></span>

2. <span data-ttu-id="8346a-115">**데이터 서비스를 만듭니다.**</span><span class="sxs-lookup"><span data-stu-id="8346a-115">**Create the data service.**</span></span> <span data-ttu-id="8346a-116">가장 기본적인 데이터 서비스는 <xref:System.Data.Services.DataService%601> 클래스에서 상속하는 클래스를 엔터티 컨테이너의 네임스페이스로 정규화된 이름인 `T` 형식으로 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-116">The most basic data service exposes a class that inherits from the <xref:System.Data.Services.DataService%601> class, with a type `T` that is the namespace-qualified name of the entity container.</span></span> <span data-ttu-id="8346a-117">자세한 내용은 [Defining WCF Data Services](defining-wcf-data-services.md)의 개발 및 배포에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-117">For more information, see [Defining WCF Data Services](defining-wcf-data-services.md).</span></span>

3. <span data-ttu-id="8346a-118">**데이터 서비스를 구성 합니다.**</span><span class="sxs-lookup"><span data-stu-id="8346a-118">**Configure the data service.**</span></span> <span data-ttu-id="8346a-119">기본적으로 WCF Data Services는 엔터티 컨테이너에 의해 노출 되는 리소스에 대 한 액세스를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-119">By default, WCF Data Services disables access to resources that are exposed by an entity container.</span></span> <span data-ttu-id="8346a-120"><xref:System.Data.Services.DataServiceConfiguration>인터페이스를 사용 하면 리소스 및 서비스 작업에 대 한 액세스를 구성 하 고, 지원 되는 버전의 OData를 지정 하 고, 일괄 처리 동작 또는 단일 응답에서 반환 될 수 있는 최대 엔터티 수와 같은 다른 서비스 전체 동작을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-120">The <xref:System.Data.Services.DataServiceConfiguration> interface enables you to configure access to resources and service operations, specify the supported version of OData, and to define other service-wide behaviors, such as batching behaviors or the maximum number of entities that can be returned in a single response.</span></span> <span data-ttu-id="8346a-121">자세한 내용은 [데이터 서비스 구성](configuring-the-data-service-wcf-data-services.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8346a-121">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

<span data-ttu-id="8346a-122">Northwind 샘플 데이터베이스를 기반으로 하는 간단한 데이터 서비스를 만드는 방법에 대 한 예제는 [빠른](quickstart-wcf-data-services.md)시작을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8346a-122">For an example of how to create a simple data service that is based on the Northwind sample database, see [Quickstart](quickstart-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8346a-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8346a-123">See also</span></span>

- [<span data-ttu-id="8346a-124">시작</span><span class="sxs-lookup"><span data-stu-id="8346a-124">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="8346a-125">개요</span><span class="sxs-lookup"><span data-stu-id="8346a-125">Overview</span></span>](wcf-data-services-overview.md)
