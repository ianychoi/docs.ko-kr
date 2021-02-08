---
description: '자세한 정보: 쿼리 프로젝션 (WCF Data Services)'
title: 쿼리 프로젝션(WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: a09f4985-9f0d-48c8-b183-83d67a3dfe5f
ms.openlocfilehash: 35427a4bc74691f366711c30cfa7af23de1caa35
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794964"
---
# <a name="query-projections-wcf-data-services"></a><span data-ttu-id="c195d-103">쿼리 프로젝션(WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="c195d-103">Query Projections (WCF Data Services)</span></span>

[!INCLUDE [wcf-deprecated](~/includes/wcf-deprecated.md)]

<span data-ttu-id="c195d-104">프로젝션은 엔터티의 특정 속성만 응답에서 반환 되도록 지정 하 여 쿼리에서 반환 되는 피드의 데이터 양을 줄이도록 OData (Open Data Protocol)의 메커니즘을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-104">Projection provides a mechanism in the Open Data Protocol (OData) to reduce the amount of data in the feed returned by a query by specifying that only certain properties of an entity are returned in the response.</span></span> <span data-ttu-id="c195d-105">자세한 내용은 섹션 4.8을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c195d-105">For more information, see section 4.8.</span></span> <span data-ttu-id="c195d-106">[URI 규칙 (OData 버전 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/)에서 시스템 쿼리 옵션 ($select)을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-106">Select System Query Option ($select) in [URI Conventions (OData Version 2.0)](https://www.odata.org/documentation/odata-version-2-0/uri-conventions/).</span></span>

<span data-ttu-id="c195d-107">이 항목에서는 쿼리 프로젝션을 정의하는 방법, 엔터티 및 비 엔터티 형식에 대한 요구 사항, 프로젝션된 결과 업데이트 및 프로젝션된 형식 만들기에 대해 설명하고 몇 가지 프로젝션 고려 사항을 제시합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-107">This topic describes how to define a query projection, what the requirements are for entity and non-entity types, making updates to projected results, creating projected types, and lists some projection considerations.</span></span>

## <a name="defining-a-query-projection"></a><span data-ttu-id="c195d-108">쿼리 프로젝션 정의</span><span class="sxs-lookup"><span data-stu-id="c195d-108">Defining a Query Projection</span></span>

<span data-ttu-id="c195d-109">`$select`URI에서 쿼리 옵션을 사용 하거나 LINQ 쿼리에서 [select](../../../csharp/language-reference/keywords/select-clause.md) 절 (Visual Basic에서[선택](../../../visual-basic/language-reference/queries/select-clause.md) )을 사용 하 여 쿼리에 프로젝션 절을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-109">You can add a projection clause to a query either by using the `$select` query option in a URI or by using the [select](../../../csharp/language-reference/keywords/select-clause.md) clause ([Select](../../../visual-basic/language-reference/queries/select-clause.md) in Visual Basic) in a LINQ query.</span></span> <span data-ttu-id="c195d-110">반환된 엔터티 데이터는 클라이언트에서 엔터티 형식이나 비 엔터티 형식으로 프로젝션될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-110">Returned entity data can be projected into either entity types or non-entity types on the client.</span></span> <span data-ttu-id="c195d-111">이 항목의 예제에서는 LINQ 쿼리에서 `select` 절을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-111">Examples in this topic demonstrate how to use the `select` clause in a LINQ query.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c195d-112">프로젝션된 형식을 업데이트한 내용을 저장할 때 데이터 서비스에서 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-112">Data loss might occur in the data service when you save updates that were made to projected types.</span></span> <span data-ttu-id="c195d-113">자세한 내용은 [프로젝션 고려 사항](#considerations)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c195d-113">For more information, see [Projection Considerations](#considerations).</span></span>

## <a name="requirements-for-entity-and-non-entity-types"></a><span data-ttu-id="c195d-114">엔터티 및 비 엔터티 형식에 대한 요구 사항</span><span class="sxs-lookup"><span data-stu-id="c195d-114">Requirements for Entity and Non-Entity Types</span></span>

<span data-ttu-id="c195d-115">엔터티 형식에는 엔터티 키를 구성하는 하나 이상의 ID 속성이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-115">Entity types must have one or more identity properties that make up the entity key.</span></span> <span data-ttu-id="c195d-116">엔터티 형식은 클라이언트에서 다음 중 한 가지 방법으로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-116">Entity types are defined on clients in one of the following ways:</span></span>

- <span data-ttu-id="c195d-117"><xref:System.Data.Services.Common.DataServiceKeyAttribute> 또는 <xref:System.Data.Services.Common.DataServiceEntityAttribute>를 형식에 적용하여</span><span class="sxs-lookup"><span data-stu-id="c195d-117">By applying the <xref:System.Data.Services.Common.DataServiceKeyAttribute> or <xref:System.Data.Services.Common.DataServiceEntityAttribute> to the type.</span></span>

- <span data-ttu-id="c195d-118">형식에 `ID`라는 속성이 있는 경우</span><span class="sxs-lookup"><span data-stu-id="c195d-118">When the type has a property named `ID`.</span></span>

- <span data-ttu-id="c195d-119">형식에 형식이 인 속성이 있는 경우  `ID` . 여기서 *type* 은 형식의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-119">When the type has a property named *type*`ID`, where *type* is the name of the type.</span></span>

<span data-ttu-id="c195d-120">기본적으로 쿼리 결과를 클라이언트에서 정의된 형식으로 프로젝션하는 경우 프로젝션에서 요청된 속성이 클라이언트 형식에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-120">By default, when you project query results into a type defined at the client, the properties requested in the projection must exist in the client type.</span></span> <span data-ttu-id="c195d-121">그러나 `true`의 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 속성에 <xref:System.Data.Services.Client.DataServiceContext> 값을 지정하는 경우에는 프로젝션에 지정된 속성이 클라이언트 형식에 있을 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-121">However, when you specify a value of `true` for the <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> property of the <xref:System.Data.Services.Client.DataServiceContext>, properties specified in the projection are not required to occur in the client type.</span></span>

### <a name="making-updates-to-projected-results"></a><span data-ttu-id="c195d-122">프로젝션된 결과 업데이트</span><span class="sxs-lookup"><span data-stu-id="c195d-122">Making Updates to Projected Results</span></span>

<span data-ttu-id="c195d-123">쿼리 결과를 클라이언트에서 엔터티 형식으로 프로젝션하는 경우 <xref:System.Data.Services.Client.DataServiceContext>는 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 메서드를 호출할 때 데이터 서비스로 다시 전송되는 업데이트를 통해 이러한 개체를 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-123">When you project query results into entity types on the client, the <xref:System.Data.Services.Client.DataServiceContext> can track those objects with updates to be sent back to the data service when the <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> method is called.</span></span> <span data-ttu-id="c195d-124">그러나 클라이언트에서 비 엔터티 형식으로 프로젝션된 데이터를 업데이트한 내용은 데이터 서비스로 다시 전송될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-124">However, updates that are made to data projected into non-entity types on the client cannot be sent back to the data service.</span></span> <span data-ttu-id="c195d-125">이는 엔터티 인스턴스를 식별하는 키가 없는 경우 데이터 서비스가 데이터 소스에서 올바른 엔터티를 업데이트할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-125">This is because without a key to identify the entity instance, the data service cannot update the correct entity in the data source.</span></span> <span data-ttu-id="c195d-126">비 엔터티 형식은 <xref:System.Data.Services.Client.DataServiceContext>에 연결되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-126">Non-entity types are not attached to the <xref:System.Data.Services.Client.DataServiceContext>.</span></span>

<span data-ttu-id="c195d-127">데이터 서비스에 정의된 엔터티 형식의 속성 중 하나 이상이 엔터티가 프로젝션되는 클라이언트 형식에 없는 경우 새 엔터티를 삽입할 때 이러한 없는 속성이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-127">When one or more properties of an entity type defined in the data service do not occur in the client type into which the entity is projected, inserts of new entities will not contain these missing properties.</span></span> <span data-ttu-id="c195d-128">이 경우 기존 엔터티에 대 한 업데이트에 **도** 이러한 누락 된 속성이 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-128">In this case, updates that are made to existing entities will **also** not include these missing properties.</span></span> <span data-ttu-id="c195d-129">이러한 속성의 값이 있는 경우 업데이트를 수행하면 속성의 값이 데이터 소스에 정의된 속성의 기본값으로 다시 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-129">When a value exists for such a property, the update resets it to the default value for the property, as defined in the data source.</span></span>

### <a name="creating-projected-types"></a><span data-ttu-id="c195d-130">프로젝션된 형식 만들기</span><span class="sxs-lookup"><span data-stu-id="c195d-130">Creating Projected Types</span></span>

<span data-ttu-id="c195d-131">다음 예제에서는 `Customers` 형식의 주소 관련 속성을 새 `CustomerAddress` 형식으로 프로젝션하는 익명 LINQ 쿼리를 사용합니다. 새 형식은 클라이언트에서 정의되며 엔터티 형식으로 특성이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-131">The following example uses an anonymous LINQ query that projects the address-related properties of the `Customers` type into a new `CustomerAddress` type, which is defined on the client and is attributed as an entity type:</span></span>

[!code-csharp[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressspecific)]
[!code-vb[Astoria Northwind Client#SelectCustomerAddressSpecific](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressspecific)]

<span data-ttu-id="c195d-132">이 예제에서 개체 이니셜라이저 패턴은 생성자를 호출하는 대신 `CustomerAddress` 형식의 새 인스턴스를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-132">In this example, the object initializer pattern is used to create a new instance of the `CustomerAddress` type instead of calling a constructor.</span></span> <span data-ttu-id="c195d-133">생성자는 엔터티 형식으로 프로젝션할 때 지원되지 않지만 비 엔터티 및 익명 형식으로 프로젝션할 때 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-133">Constructors are not supported when projecting into entity types, but they can be used when projecting into non-entity and anonymous types.</span></span> <span data-ttu-id="c195d-134">`CustomerAddress`가 엔터티 형식이기 때문에 변경 후 데이터 서비스로 다시 전송될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-134">Because `CustomerAddress` is an entity type, changes can be made and sent back to the data service.</span></span>

<span data-ttu-id="c195d-135">또한 `Customer` 형식의 데이터가 익명 형식 대신 `CustomerAddress` 엔터티 형식의 인스턴스로 프로젝션됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-135">Also, the data from the `Customer` type is projected into an instance of the `CustomerAddress` entity type instead of an anonymous type.</span></span> <span data-ttu-id="c195d-136">익명 형식으로 프로젝션할 수 있지만 익명 형식이 비 엔터티 형식으로 처리되기 때문에 데이터가 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-136">Projection into anonymous types is supported, but the data is read-only because anonymous types are treated as non-entity types.</span></span>

<span data-ttu-id="c195d-137"><xref:System.Data.Services.Client.MergeOption>의 <xref:System.Data.Services.Client.DataServiceContext> 설정은 쿼리 프로젝션 중에 ID 확인에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-137">The <xref:System.Data.Services.Client.MergeOption> settings of the <xref:System.Data.Services.Client.DataServiceContext> are used for identity resolution during query projection.</span></span> <span data-ttu-id="c195d-138">이는 `Customer` 형식의 인스턴스가 이미 <xref:System.Data.Services.Client.DataServiceContext>에 있는 경우 ID가 동일한 `CustomerAddress`의 인스턴스가 <xref:System.Data.Services.Client.MergeOption>에 의해 설정된 ID 확인 규칙을 따름을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-138">This means that if an instance of the `Customer` type already exists in the <xref:System.Data.Services.Client.DataServiceContext>, an instance of `CustomerAddress` with the same identity will follow the identity resolution rules set by the <xref:System.Data.Services.Client.MergeOption></span></span>

<span data-ttu-id="c195d-139">다음에서는 결과를 엔터티 및 비 엔터티 형식으로 프로젝션 하는 경우의 동작에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-139">The following describes the behaviors when projecting results into entity and non-entity types:</span></span>

<span data-ttu-id="c195d-140">**이니셜라이저를 사용 하 여 새 프로젝션 인스턴스 만들기**</span><span class="sxs-lookup"><span data-stu-id="c195d-140">**Creating a new projected instance by using initializers**</span></span>

- <span data-ttu-id="c195d-141">예제:</span><span class="sxs-lookup"><span data-stu-id="c195d-141">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithinitializer)]
   [!code-vb[Astoria Northwind Client#ProjectWithInitializer](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithinitializer)]

- <span data-ttu-id="c195d-142">엔터티 형식: 지원 됨</span><span class="sxs-lookup"><span data-stu-id="c195d-142">Entity type: Supported</span></span>

- <span data-ttu-id="c195d-143">비 엔터티 형식: 지원 됨</span><span class="sxs-lookup"><span data-stu-id="c195d-143">Non-entity type: Supported</span></span>

<span data-ttu-id="c195d-144">**생성자를 사용 하 여 새 프로젝션 인스턴스 만들기**</span><span class="sxs-lookup"><span data-stu-id="c195d-144">**Creating a new projected instance by using constructors**</span></span>

- <span data-ttu-id="c195d-145">예제:</span><span class="sxs-lookup"><span data-stu-id="c195d-145">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithconstructor)]
   [!code-vb[Astoria Northwind Client#ProjectWithConstructor](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithconstructor)]

- <span data-ttu-id="c195d-146">엔터티 형식: <xref:System.NotSupportedException> 이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-146">Entity type: A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="c195d-147">비 엔터티 형식: 지원 됨</span><span class="sxs-lookup"><span data-stu-id="c195d-147">Non-entity type: Supported</span></span>

<span data-ttu-id="c195d-148">**프로젝션을 사용 하 여 속성 값 변환**</span><span class="sxs-lookup"><span data-stu-id="c195d-148">**Using projection to transform a property value**</span></span>

- <span data-ttu-id="c195d-149">예제:</span><span class="sxs-lookup"><span data-stu-id="c195d-149">Example:</span></span>

   [!code-csharp[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#projectwithtransform)]
   [!code-vb[Astoria Northwind Client#ProjectWithTransform](~/samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#projectwithtransform)]

- <span data-ttu-id="c195d-150">엔터티 형식: 혼동을 야기 하 고 잠재적으로 다른 엔터티에 속한 데이터 소스의 데이터를 덮어쓸 수 있기 때문에이 변환은 엔터티 형식에 대해 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-150">Entity type: This transformation is not supported for entity types because it can lead to confusion and potentially overwriting the data in the data source that belongs to another entity.</span></span> <span data-ttu-id="c195d-151"><xref:System.NotSupportedException>이 발생함</span><span class="sxs-lookup"><span data-stu-id="c195d-151">A <xref:System.NotSupportedException> is raised.</span></span>

- <span data-ttu-id="c195d-152">비 엔터티 형식: 지원 됨</span><span class="sxs-lookup"><span data-stu-id="c195d-152">Non-entity type: Supported</span></span>

<a name="considerations"></a>

## <a name="projection-considerations"></a><span data-ttu-id="c195d-153">프로젝션 고려 사항</span><span class="sxs-lookup"><span data-stu-id="c195d-153">Projection Considerations</span></span>

<span data-ttu-id="c195d-154">쿼리 프로젝션을 정의할 때 다음 사항을 추가로 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-154">The following additional considerations apply when defining a query projection.</span></span>

- <span data-ttu-id="c195d-155">Atom 형식에 대한 사용자 지정 피드를 정의하는 경우 사용자 지정 매핑이 정의되어 있는 모든 엔터티 속성이 프로젝션에 포함되도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-155">When you define custom feeds for the Atom format, you must make sure that all entity properties that have custom mappings defined are included in the projection.</span></span> <span data-ttu-id="c195d-156">매핑된 엔터티 속성이 프로젝션에 포함되지 않는 경우 데이터가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-156">When a mapped entity property is not included in the projection, data loss might occur.</span></span> <span data-ttu-id="c195d-157">자세한 내용은 [피드 사용자 지정](feed-customization-wcf-data-services.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c195d-157">For more information, see [Feed Customization](feed-customization-wcf-data-services.md).</span></span>

- <span data-ttu-id="c195d-158">데이터 서비스의 데이터 모델에서 엔터티의 모든 속성을 포함하지 않는 프로젝션된 형식에 삽입이 수행되는 경우 클라이언트에서 프로젝션에 포함되지 않은 속성이 기본값으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-158">When inserts are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, the properties not included in the projection at the client are set to their default values.</span></span>

- <span data-ttu-id="c195d-159">데이터 서비스의 데이터 모델에서 엔터티의 모든 속성을 포함하지 않는 프로젝션된 형식을 업데이트하는 경우 클라이언트에서 프로젝션에 포함되지 않은 기존 값이 초기화되지 않은 기본값으로 덮어쓰입니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-159">When updates are made to a projected type that does not contain all of the properties of the entity in the data model of the data service, existing values not included in the projection on the client will be overwritten with uninitialized default values.</span></span>

- <span data-ttu-id="c195d-160">프로젝션에 복합 속성이 포함된 경우 전체 복합 개체가 반환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-160">When a projection includes a complex property, the entire complex object must be returned.</span></span>

- <span data-ttu-id="c195d-161">프로젝션에 탐색 속성이 포함된 경우 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드를 호출하지 않고도 관련 개체가 암시적으로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-161">When a projection includes a navigation property, the related objects are loaded implicitly without having to call the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method.</span></span> <span data-ttu-id="c195d-162"><xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 메서드는 프로젝션된 쿼리에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-162">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is not supported for use in a projected query.</span></span>

- <span data-ttu-id="c195d-163">클라이언트의 쿼리 프로젝션 쿼리는 요청 URI에서 `$select` 쿼리 옵션을 사용하도록 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-163">Query projections queries on the client are translated to use the `$select` query option in the request URI.</span></span> <span data-ttu-id="c195d-164">프로젝션을 포함 하는 쿼리가 쿼리 옵션을 지원 하지 않는 이전 버전의 WCF Data Services에 대해 실행 되는 경우 `$select` 오류가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-164">When a query with projection is executed against a previous version of WCF Data Services that does not support the `$select` query option, an error is returned.</span></span> <span data-ttu-id="c195d-165">이러한 문제는 데이터 서비스에 대한 <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A>의 <xref:System.Data.Services.DataServiceBehavior>이 <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1> 값으로 설정된 경우에도 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c195d-165">This can also happen when the <xref:System.Data.Services.DataServiceBehavior.MaxProtocolVersion%2A> of the <xref:System.Data.Services.DataServiceBehavior> for the data service is set to a value of <xref:System.Data.Services.Common.DataServiceProtocolVersion.V1>.</span></span> <span data-ttu-id="c195d-166">자세한 내용은 [데이터 서비스 버전 관리](data-service-versioning-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c195d-166">For more information, see [Data Service Versioning](data-service-versioning-wcf-data-services.md).</span></span>

<span data-ttu-id="c195d-167">자세한 내용은 [방법: 쿼리 결과 프로젝트](how-to-project-query-results-wcf-data-services.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="c195d-167">For more information, see [How to: Project Query Results](how-to-project-query-results-wcf-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c195d-168">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c195d-168">See also</span></span>

- [<span data-ttu-id="c195d-169">데이터 서비스 쿼리</span><span class="sxs-lookup"><span data-stu-id="c195d-169">Querying the Data Service</span></span>](querying-the-data-service-wcf-data-services.md)
