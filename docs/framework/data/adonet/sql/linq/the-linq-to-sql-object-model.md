---
description: '자세한 정보: LINQ to SQL 개체 모델'
title: LINQ to SQL 개체 모델
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 81dd0c37-e2a4-4694-83b0-f2e49e693810
ms.openlocfilehash: be4021019d09d1479364b25268eefda50b6eaa6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681268"
---
# <a name="the-linq-to-sql-object-model"></a><span data-ttu-id="bcb77-103">LINQ to SQL 개체 모델</span><span class="sxs-lookup"><span data-stu-id="bcb77-103">The LINQ to SQL Object Model</span></span>

<span data-ttu-id="bcb77-104">에서 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 개발자의 프로그래밍 언어로 표현 된 개체 모델은 관계형 데이터베이스의 데이터 모델에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-104">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model expressed in the programming language of the developer is mapped to the data model of a relational database.</span></span> <span data-ttu-id="bcb77-105">그런 다음 개체 모델에 따라 데이터 작업이 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-105">Operations on the data are then conducted according to the object model.</span></span>  
  
 <span data-ttu-id="bcb77-106">이 시나리오에서는 데이터베이스에 대해 `INSERT`와 같은 데이터베이스 명령을 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-106">In this scenario, you do not issue database commands (for example, `INSERT`) to the database.</span></span> <span data-ttu-id="bcb77-107">대신 개체 모델 내에서 값을 변경하고 메서드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-107">Instead, you change values and execute methods within your object model.</span></span> <span data-ttu-id="bcb77-108">데이터베이스를 쿼리하거나 데이터베이스에 변경 내용을 보내려는 경우 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]은 사용자의 요청을 올바른 SQL 명령으로 변환하고 이러한 명령을 데이터베이스에 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-108">When you want to query the database or send it changes, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates your requests into the correct SQL commands and sends those commands to the database.</span></span>  
  
 ![Linq 개체 모델을 보여 주는 스크린샷](./media/the-linq-to-sql-object-model/linq-object-model-two-tier.png)  
  
 <span data-ttu-id="bcb77-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 개체 모델의 가장 기본적인 요소와 관계형 데이터 모델의 요소 간의 관계가 다음 표에 요약되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-110">The most fundamental elements in the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model and their relationship to elements in the relational data model are summarized in the following table:</span></span>  
  
|<span data-ttu-id="bcb77-111">LINQ to SQL 개체 모델</span><span class="sxs-lookup"><span data-stu-id="bcb77-111">LINQ to SQL Object Model</span></span>|<span data-ttu-id="bcb77-112">관계형 데이터 모델</span><span class="sxs-lookup"><span data-stu-id="bcb77-112">Relational Data Model</span></span>|  
|------------------------------|---------------------------|  
|<span data-ttu-id="bcb77-113">엔터티 클래스</span><span class="sxs-lookup"><span data-stu-id="bcb77-113">Entity class</span></span>|<span data-ttu-id="bcb77-114">테이블</span><span class="sxs-lookup"><span data-stu-id="bcb77-114">Table</span></span>|  
|<span data-ttu-id="bcb77-115">클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="bcb77-115">Class member</span></span>|<span data-ttu-id="bcb77-116">열</span><span class="sxs-lookup"><span data-stu-id="bcb77-116">Column</span></span>|  
|<span data-ttu-id="bcb77-117">연결</span><span class="sxs-lookup"><span data-stu-id="bcb77-117">Association</span></span>|<span data-ttu-id="bcb77-118">외래 키 관계</span><span class="sxs-lookup"><span data-stu-id="bcb77-118">Foreign-key relationship</span></span>|  
|<span data-ttu-id="bcb77-119">메서드</span><span class="sxs-lookup"><span data-stu-id="bcb77-119">Method</span></span>|<span data-ttu-id="bcb77-120">저장 프로시저 또는 함수</span><span class="sxs-lookup"><span data-stu-id="bcb77-120">Stored Procedure or Function</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="bcb77-121">지금부터는 관계형 데이터 모델과 규칙에 대해 어느 정도 지식이 있다고 가정하고 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-121">The following descriptions assume that you have a basic knowledge of the relational data model and rules.</span></span>  
  
## <a name="linq-to-sql-entity-classes-and-database-tables"></a><span data-ttu-id="bcb77-122">LINQ to SQL 엔터티 클래스 및 데이터베이스 테이블</span><span class="sxs-lookup"><span data-stu-id="bcb77-122">LINQ to SQL Entity Classes and Database Tables</span></span>  

 <span data-ttu-id="bcb77-123">에서 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 데이터베이스 테이블은 *엔터티 클래스로* 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-123">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], a database table is represented by an *entity class*.</span></span> <span data-ttu-id="bcb77-124">엔터티 클래스는 클래스를 데이터베이스 테이블과 연결하는 특수한 정보를 사용하여 클래스에 주석을 단다는 점을 제외하고 사용자가 만들 수 있는 다른 클래스와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-124">An entity class is like any other class you might create except that you annotate the class by using special information that associates the class with a database table.</span></span> <span data-ttu-id="bcb77-125">다음 예제와 같이 사용자 지정 특성(<xref:System.Data.Linq.Mapping.TableAttribute>)을 클래스 선언에 추가하여 이 주석을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-125">You make this annotation by adding a custom attribute (<xref:System.Data.Linq.Mapping.TableAttribute>) to your class declaration, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="bcb77-126">예제</span><span class="sxs-lookup"><span data-stu-id="bcb77-126">Example</span></span>  

 [!code-csharp[DLinqObjectModel#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#1)]
 [!code-vb[DLinqObjectModel#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#1)]  
  
 <span data-ttu-id="bcb77-127">테이블로 선언된 클래스의 인스턴스(즉, 엔터티 클래스)만 데이터베이스에 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-127">Only instances of classes declared as tables (that is, entity classes) can be saved to the database.</span></span>  
  
 <span data-ttu-id="bcb77-128">자세한 내용은 [특성 기반 매핑의](attribute-based-mapping.md)테이블 특성 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bcb77-128">For more information, see the Table Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-class-members-and-database-columns"></a><span data-ttu-id="bcb77-129">LINQ to SQL 클래스 멤버 및 데이터베이스 열</span><span class="sxs-lookup"><span data-stu-id="bcb77-129">LINQ to SQL Class Members and Database Columns</span></span>  

 <span data-ttu-id="bcb77-130">클래스를 테이블과 연결하는 것 외에도 데이터베이스 열을 나타내는 필드나 속성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-130">In addition to associating classes with tables, you designate fields or properties to represent database columns.</span></span> <span data-ttu-id="bcb77-131">이 작업을 위해 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 다음 예제와 같이 <xref:System.Data.Linq.Mapping.ColumnAttribute> 특성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-131">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] defines the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute, as in the following example:</span></span>  
  
### <a name="example"></a><span data-ttu-id="bcb77-132">예제</span><span class="sxs-lookup"><span data-stu-id="bcb77-132">Example</span></span>  

 [!code-csharp[DLinqObjectModel#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/Program.cs#2)]
 [!code-vb[DLinqObjectModel#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/Module1.vb#2)]  
  
 <span data-ttu-id="bcb77-133">열에 매핑된 필드와 속성만 데이터베이스에서 유지되거나 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-133">Only fields and properties mapped to columns are persisted to or retrieved from the database.</span></span> <span data-ttu-id="bcb77-134">열로 선언되지 않은 필드와 속성은 애플리케이션 논리의 임시 부분으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-134">Those not declared as columns are considered as transient parts of your application logic.</span></span>  
  
 <span data-ttu-id="bcb77-135"><xref:System.Data.Linq.Mapping.ColumnAttribute> 특성에는 열을 나타내는 이러한 멤버를 사용자 지정(예: 기본 키 열을 나타내도록 멤버 지정)하는 데 사용할 수 있는 다양한 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-135">The <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute has a variety of properties that you can use to customize these members that represent columns (for example, designating a member as representing a primary key column).</span></span> <span data-ttu-id="bcb77-136">자세한 내용은 [특성 기반 매핑의](attribute-based-mapping.md)열 특성 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bcb77-136">For more information, see the Column Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-associations-and-database-foreign-key-relationships"></a><span data-ttu-id="bcb77-137">LINQ to SQL 연결 및 데이터베이스 외래 키 관계</span><span class="sxs-lookup"><span data-stu-id="bcb77-137">LINQ to SQL Associations and Database Foreign-key Relationships</span></span>  

 <span data-ttu-id="bcb77-138">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 <xref:System.Data.Linq.Mapping.AssociationAttribute> 특성을 적용하여 외래 키와 기본 키 사이의 관계와 같은 데이터베이스 연결을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-138">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you represent database associations (such as foreign-key to primary-key relationships) by applying the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="bcb77-139">다음 코드 세그먼트에서 `Order` 클래스는 `Customer` 특성이 있는 <xref:System.Data.Linq.Mapping.AssociationAttribute> 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-139">In the following segment of code, the `Order` class contains a `Customer` property that has an <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="bcb77-140">이 속성과 해당 특성은 `Order` 클래스에 `Customer` 클래스와의 관계를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-140">This property and its attribute provide the `Order` class with a relationship to the `Customer` class.</span></span>  
  
 <span data-ttu-id="bcb77-141">다음 코드 예제에서는 `Customer` 클래스의 `Order` 속성을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-141">The following code example shows the `Customer` property from the `Order` class.</span></span>  
  
### <a name="example"></a><span data-ttu-id="bcb77-142">예제</span><span class="sxs-lookup"><span data-stu-id="bcb77-142">Example</span></span>  

 [!code-csharp[DLinqObjectModel#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#3)]
 [!code-vb[DLinqObjectModel#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#3)]  
  
 <span data-ttu-id="bcb77-143">자세한 내용은 [특성 기반 매핑의](attribute-based-mapping.md)Association 특성 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bcb77-143">For more information, see the Association Attribute section of [Attribute-Based Mapping](attribute-based-mapping.md).</span></span>  
  
## <a name="linq-to-sql-methods-and-database-stored-procedures"></a><span data-ttu-id="bcb77-144">LINQ to SQL 메서드 및 데이터베이스 저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="bcb77-144">LINQ to SQL Methods and Database Stored Procedures</span></span>  

 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bcb77-145">은 저장 프로시저와 사용자 정의 함수를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-145">supports stored procedures and user-defined functions.</span></span> <span data-ttu-id="bcb77-146">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 이러한 데이터베이스 정의 추상화를 클라이언트 개체에 매핑하면 클라이언트 코드에서 강력한 형식으로 해당 개체에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-146">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], you map these database-defined abstractions to client objects so that you can access them in a strongly typed manner from client code.</span></span> <span data-ttu-id="bcb77-147">메서드 시그니처는 데이터베이스에 정의된 프로시저 및 함수의 시그니처와 매우 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-147">The method signatures resemble as closely as possible the signatures of the procedures and functions defined in the database.</span></span> <span data-ttu-id="bcb77-148">IntelliSense를 사용하여 이러한 메서드를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-148">You can use IntelliSense to discover these methods.</span></span>  
  
 <span data-ttu-id="bcb77-149">매핑된 프로시저에 대한 호출에서 반환되는 결과 집합은 강력한 형식의 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-149">A result set that is returned by a call to a mapped procedure is a strongly typed collection.</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="bcb77-150">은 <xref:System.Data.Linq.Mapping.FunctionAttribute> 및 <xref:System.Data.Linq.Mapping.ParameterAttribute> 특성을 사용하여 저장 프로시저와 함수를 메서드에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-150">maps stored procedures and functions to methods by using the <xref:System.Data.Linq.Mapping.FunctionAttribute> and <xref:System.Data.Linq.Mapping.ParameterAttribute> attributes.</span></span> <span data-ttu-id="bcb77-151">저장 프로시저를 나타내는 메서드와 사용자 정의 함수를 나타내는 메서드는 <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> 속성에 의해 구별됩니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-151">Methods representing stored procedures are distinguished from those representing user-defined functions by the <xref:System.Data.Linq.Mapping.FunctionAttribute.IsComposable%2A> property.</span></span> <span data-ttu-id="bcb77-152">이 속성이 `false`(기본값)로 설정된 경우 메서드는 저장 프로시저를 나타내고</span><span class="sxs-lookup"><span data-stu-id="bcb77-152">If this property is set to `false` (the default), the method represents a stored procedure.</span></span> <span data-ttu-id="bcb77-153">`true`로 설정된 경우 메서드는 데이터베이스 함수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-153">If it is set to `true`, the method represents a database function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcb77-154">Visual Studio를 사용 하는 경우 개체 관계형 디자이너를 사용 하 여 저장 프로시저 및 사용자 정의 함수에 매핑된 메서드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bcb77-154">If you are using Visual Studio, you can use the Object Relational Designer to create methods mapped to stored procedures and user-defined functions.</span></span>  
  
### <a name="example"></a><span data-ttu-id="bcb77-155">예제</span><span class="sxs-lookup"><span data-stu-id="bcb77-155">Example</span></span>  

 [!code-csharp[DLinqObjectModel#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqObjectModel/cs/northwind.cs#4)]
 [!code-vb[DLinqObjectModel#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqObjectModel/vb/northwind.vb#4)]  
  
 <span data-ttu-id="bcb77-156">자세한 내용은 [특성 기반 매핑](attribute-based-mapping.md) 및 [저장 프로시저](stored-procedures.md)의 함수 특성, 저장 프로시저 특성 및 매개 변수 특성 섹션을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="bcb77-156">For more information, see the Function Attribute, Stored Procedure Attribute, and Parameter Attribute sections of [Attribute-Based Mapping](attribute-based-mapping.md) and [Stored Procedures](stored-procedures.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcb77-157">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bcb77-157">See also</span></span>

- [<span data-ttu-id="bcb77-158">특성 기반 매핑</span><span class="sxs-lookup"><span data-stu-id="bcb77-158">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="bcb77-159">배경 정보</span><span class="sxs-lookup"><span data-stu-id="bcb77-159">Background Information</span></span>](background-information.md)
