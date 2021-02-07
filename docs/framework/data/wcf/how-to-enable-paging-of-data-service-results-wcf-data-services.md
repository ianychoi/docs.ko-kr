---
description: '자세한 정보: 방법: 데이터 서비스 결과의 페이징 사용 (WCF Data Services)'
title: '방법: 데이터 서비스 결과의 페이징 사용(WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 27a2b37f432d906022d06492b2f687681d9b9ac8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765336"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="2e9f8-103">방법: 데이터 서비스 결과의 페이징 사용(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="2e9f8-103">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="2e9f8-104">WCF Data Services를 사용 하면 데이터 서비스 쿼리에서 반환 되는 엔터티 수를 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-104">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="2e9f8-105">페이지 제한은 서비스가 초기화될 때 호출되는 메서드에서 정의되며 각 엔터티 집합에 대해 별도로 설정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-105">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="2e9f8-106">페이징을 사용하도록 설정하면 피드의 최종 항목에 다음 데이터 페이지에 대한 링크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-106">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="2e9f8-107">자세한 내용은 [데이터 서비스 구성](configuring-the-data-service-wcf-data-services.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-107">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="2e9f8-108">이 항목에서는 데이터 서비스를 수정하여 반환된 `Customers` 및 `Orders` 엔터티 집합의 페이징을 사용하도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-108">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="2e9f8-109">이 항목의 예제에서는 Northwind 샘플 데이터 서비스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-109">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="2e9f8-110">이 서비스는 [WCF Data Services 빠른](quickstart-wcf-data-services.md)시작을 완료 하면 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-110">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="2e9f8-111">반환된 Customers 및 Orders 엔터티 집합의 페이징을 사용하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="2e9f8-111">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="2e9f8-112">데이터 서비스 코드에서 `InitializeService` 함수의 자리 표시자 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="2e9f8-112">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="2e9f8-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2e9f8-113">See also</span></span>

- [<span data-ttu-id="2e9f8-114">지연 콘텐츠 로드</span><span class="sxs-lookup"><span data-stu-id="2e9f8-114">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="2e9f8-115">방법: 페이징된 결과 로드</span><span class="sxs-lookup"><span data-stu-id="2e9f8-115">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
