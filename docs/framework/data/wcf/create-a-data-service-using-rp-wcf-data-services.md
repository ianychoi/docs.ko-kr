---
description: '자세히 알아보기: 방법: 리플렉션 공급자를 사용 하 여 데이터 서비스 만들기 (WCF Data Services)'
title: '방법: 리플렉션 공급자를 사용 하 여 데이터 서비스 만들기 (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 1c4d131b21c69e11dd6d8b574e4c22a6af7c5a25
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766234"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="8513f-103">방법: 리플렉션 공급자를 사용 하 여 데이터 서비스 만들기 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8513f-103">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="8513f-104">WCF Data Services를 사용 하면 해당 클래스가 인터페이스를 구현 하는 개체로 노출 되는 한 임의의 클래스를 기반으로 하는 데이터 모델을 정의할 수 있습니다 <xref:System.Linq.IQueryable%601> .</span><span class="sxs-lookup"><span data-stu-id="8513f-104">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="8513f-105">자세한 내용은 [데이터 서비스 공급자](data-services-providers-wcf-data-services.md)합니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-105">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8513f-106">예제</span><span class="sxs-lookup"><span data-stu-id="8513f-106">Example</span></span>  

 <span data-ttu-id="8513f-107">다음 예제에서는 `Orders` 및 `Items`가 포함된 데이터 모델을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-107">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="8513f-108">엔터티 컨테이너 클래스 `OrderItemData`에는 <xref:System.Linq.IQueryable%601> 인터페이스를 반환하는 두 개의 공용 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-108">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="8513f-109">이러한 인터페이스는 `Orders` 및 `Items` 엔터티 형식의 엔터티 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-109">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="8513f-110">`Order`에는 여러 `Items`가 포함될 수 있으므로 `Orders` 엔터티 형식의 `Items` 탐색 속성은 `Items` 개체의 컬렉션을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-110">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="8513f-111">`OrderItemData` 엔터티 컨테이너 클래스는 <xref:System.Data.Services.DataService%601> 데이터 서비스가 파생되는 `OrderItems` 클래스의 제네릭 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-111">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8513f-112">이 예제에서는 메모리 내 데이터 공급자를 보여 주며 변경 내용이 현재 개체 인스턴스 외부에서 유지되지 않으므로 <xref:System.Data.Services.IUpdatable> 인터페이스를 구현해도 파생되는 이점이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="8513f-112">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="8513f-113">인터페이스를 구현 하는 예제는 <xref:System.Data.Services.IUpdatable> [방법: LINQ to SQL 데이터 소스를 사용 하 여 데이터 서비스 만들기](create-a-data-service-using-linq-to-sql-wcf.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="8513f-113">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="8513f-114">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8513f-114">See also</span></span>

- [<span data-ttu-id="8513f-115">방법: LINQ to SQL 데이터 원본을 사용하여 데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8513f-115">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="8513f-116">Data Services 공급자</span><span class="sxs-lookup"><span data-stu-id="8513f-116">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="8513f-117">방법: ADO.NET Entity Framework 데이터 원본을 사용하여 데이터 서비스 만들기</span><span class="sxs-lookup"><span data-stu-id="8513f-117">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
