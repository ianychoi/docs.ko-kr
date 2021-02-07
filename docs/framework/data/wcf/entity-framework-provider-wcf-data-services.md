---
description: '자세한 정보: Entity Framework 공급자 (WCF Data Services)'
title: Entity Framework 공급자(WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 0c321ca49520c9b2957a807c01175bea8ee7ae3b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766051"
---
# <a name="entity-framework-provider-wcf-data-services"></a><span data-ttu-id="6651c-103">Entity Framework 공급자(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="6651c-103">Entity Framework Provider (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="6651c-104">WCF Data Services와 마찬가지로 ADO.NET Entity Framework는 엔터티-관계 모델의 유형인 엔터티 데이터 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-104">Like WCF Data Services, the ADO.NET Entity Framework is based on the Entity Data Model, which is a type of entity-relationship model.</span></span> <span data-ttu-id="6651c-105">Entity Framework은 *개념적 모델* 이라고 하는 엔터티 데이터 모델의 구현에 대해 작업을 데이터 소스에 대 한 동등한 작업으로 변환 합니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-105">The Entity Framework translates operations against its implementation of the Entity Data Model, which is called the *conceptual model*, into equivalent operations against a data source.</span></span> <span data-ttu-id="6651c-106">이를 통해 Entity Framework는 관계형 데이터를 기반으로 하는 데이터 서비스에 적합 한 공급자 이며 Entity Framework를 지 원하는 데이터 공급자가 있는 모든 데이터베이스를 WCF Data Services와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-106">This makes the Entity Framework an ideal provider for data services that are based on relational data, and any database that has a data provider that supports the Entity Framework can be used with WCF Data Services.</span></span> <span data-ttu-id="6651c-107">현재 Entity Framework을 지 원하는 데이터 원본 목록은 [Entity Framework 공급자](/ef/ef6/fundamentals/providers/)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6651c-107">For a list of the data sources that currently support the Entity Framework, see [Entity Framework Providers](/ef/ef6/fundamentals/providers/).</span></span>
  
 <span data-ttu-id="6651c-108">개념적 모델에서 엔터티 컨테이너는 서비스 루트입니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-108">In a conceptual model, the entity container is the root of the service.</span></span> <span data-ttu-id="6651c-109">먼저 Entity Framework에서 개념적 모델을 정의해야 데이터 서비스가 데이터를 노출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-109">You must define a conceptual model in the Entity Framework before the data can be exposed by a data service.</span></span> <span data-ttu-id="6651c-110">자세한 내용은 [방법: ADO.NET Entity Framework 데이터 원본을 사용 하 여 데이터 서비스 만들기](create-a-data-service-using-an-adonet-ef-data-wcf.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6651c-110">For more information, see [How to: Create a Data Service Using an ADO.NET Entity Framework Data Source](create-a-data-service-using-an-adonet-ef-data-wcf.md).</span></span>  
  
 <span data-ttu-id="6651c-111">WCF Data Services은 엔터티에 대 한 동시성 토큰을 정의할 수 있도록 하 여 낙관적 동시성 모델을 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-111">WCF Data Services supports the optimistic concurrency model by enabling you to define a concurrency token for an entity.</span></span> <span data-ttu-id="6651c-112">엔터티의 속성을 하나 이상 포함하는 이 동시성 토큰은 요청되거나 업데이트 또는 삭제되고 있는 데이터가 변경되었는지 여부를 데이터 서비스에서 확인하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-112">This concurrency token, which includes one or more properties of the entity, is used by the data service to determine whether a change has occurred in the data that is being requested, updated, or deleted.</span></span> <span data-ttu-id="6651c-113">요청의 eTag에서 가져온 토큰 값이 엔터티의 현재 값과 다르면 데이터 서비스에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-113">When token values obtained from the eTag in the request differ from the current values of the entity, an exception is raised by the data service.</span></span> <span data-ttu-id="6651c-114">속성이 동시성 토큰의 일부임을 나타내려면 `ConcurrencyMode="Fixed"` Entity Framework 공급자가 정의한 데이터 모델에 특성을 적용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-114">To indicate that a property is part of the concurrency token, you must apply the attribute `ConcurrencyMode="Fixed"` in the data model defined by the Entity Framework provider.</span></span> <span data-ttu-id="6651c-115">동시성 토큰에는 키 속성이나 탐색 속성이 포함될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6651c-115">The concurrency token cannot include a key property or a navigation property.</span></span> <span data-ttu-id="6651c-116">자세한 내용은 [데이터 서비스 업데이트](updating-the-data-service-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6651c-116">For more information, see [Updating the Data Service](updating-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="6651c-117">Entity Framework에 대해 자세히 알아보려면 [Entity Framework 개요](../adonet/ef/overview.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6651c-117">To learn more about the Entity Framework, see [Entity Framework Overview](../adonet/ef/overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6651c-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6651c-118">See also</span></span>

- [<span data-ttu-id="6651c-119">Data Services 공급자</span><span class="sxs-lookup"><span data-stu-id="6651c-119">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="6651c-120">리플렉션 공급자</span><span class="sxs-lookup"><span data-stu-id="6651c-120">Reflection Provider</span></span>](reflection-provider-wcf-data-services.md)
- [<span data-ttu-id="6651c-121">엔터티 데이터 모델</span><span class="sxs-lookup"><span data-stu-id="6651c-121">Entity Data Model</span></span>](../adonet/entity-data-model.md)
