---
description: '자세한 정보: 방법: 서비스 작업 정의 (WCF Data Services)'
title: '방법: 서비스 작업 정의(WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 9fcad3a31ea5b439c248ba103cbf4ddd75b8109a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765622"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="04b54-103">방법: 서비스 작업 정의(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="04b54-103">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="04b54-104">WCF Data Services 서버에 서비스 작업으로 정의 된 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-104">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="04b54-105">데이터 서비스는 서비스 작업을 사용하여 URI를 통해 서버에 정의된 메서드에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-105">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="04b54-106">서비스 작업을 정의 하려면 [ `WebGet]` 또는 특성을 메서드에 적용 하십시오 `[WebInvoke]` .</span><span class="sxs-lookup"><span data-stu-id="04b54-106">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="04b54-107">쿼리 연산자를 지원 하려면 서비스 작업에서 인스턴스를 반환 해야 합니다 <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="04b54-107">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="04b54-108">서비스 작업은 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A>의 <xref:System.Data.Services.DataService%601> 속성을 통해 기본 데이터 소스에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-108">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="04b54-109">자세한 내용은 [서비스 작업](service-operations-wcf-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="04b54-109">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="04b54-110">이 항목의 예제에서는 `GetOrdersByCity`의 필터링된 <xref:System.Linq.IQueryable%601> 인스턴스 및 관련 `Orders` 개체를 반환하는 `Order_Details`라는 서비스 작업을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-110">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="04b54-111">이 예제에서는 Northwind 샘플 데이터 서비스의 데이터 소스인 <xref:System.Data.Objects.ObjectContext> 인스턴스에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-111">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="04b54-112">이 서비스는 [WCF Data Services 빠른](quickstart-wcf-data-services.md)시작을 완료 하면 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-112">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="04b54-113">Northwind 데이터 서비스에 서비스 작업을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="04b54-113">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="04b54-114">Northwind 데이터 서비스 프로젝트에서 Northwind.svc 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-114">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="04b54-115">`Northwind` 클래스에서 `GetOrdersByCity`라는 서비스 작업 메서드를 다음과 같이 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-115">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="04b54-116">`InitializeService` 클래스의 `Northwind` 메서드에서 다음 코드를 추가하여 서비스 작업에 액세스할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-116">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="04b54-117">GetOrdersByCity 서비스 작업을 쿼리하려면</span><span class="sxs-lookup"><span data-stu-id="04b54-117">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="04b54-118">웹 브라우저에서 다음 URI 중 하나를 입력하여 다음 예제에 정의된 서비스 작업을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-118">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="04b54-119">예제</span><span class="sxs-lookup"><span data-stu-id="04b54-119">Example</span></span>

<span data-ttu-id="04b54-120">다음 예제에서는 Northwind 데이터 서비스에 `GetOrderByCity`라는 서비스 작업을 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-120">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="04b54-121">이 작업은 ADO.NET Entity Framework를 사용하여 제공된 도시 이름을 기준으로 `Orders` 집합 및 관련 `Order_Details` 개체를 <xref:System.Linq.IQueryable%601> 인스턴스로 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-121">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="04b54-122">메서드에서 <xref:System.Linq.IQueryable%601> 인스턴스를 반환하기 때문에 이 서비스 작업 엔드포인트에서 쿼리 연산자가 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="04b54-122">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="04b54-123">참고 항목</span><span class="sxs-lookup"><span data-stu-id="04b54-123">See also</span></span>

- [<span data-ttu-id="04b54-124">WCF Data Services 정의</span><span class="sxs-lookup"><span data-stu-id="04b54-124">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
