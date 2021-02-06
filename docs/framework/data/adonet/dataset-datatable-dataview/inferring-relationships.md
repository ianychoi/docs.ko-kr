---
description: '자세히 알아보기: 관계 유추'
title: 관계 유추
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: a117581d512c1427c638ea862169ab3c7623d783
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652148"
---
# <a name="inferring-relationships"></a><span data-ttu-id="716e1-103">관계 유추</span><span class="sxs-lookup"><span data-stu-id="716e1-103">Inferring Relationships</span></span>

<span data-ttu-id="716e1-104">테이블로 유추되는 요소에 역시 테이블로 유추되는 자식 요소가 있으면 두 테이블 사이에 <xref:System.Data.DataRelation>이 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-104">If an element that is inferred as a table has a child element that is also inferred as a table, a <xref:System.Data.DataRelation> will be created between the two tables.</span></span> <span data-ttu-id="716e1-105">**ParentTableName_Id** 이름이 인 새 열이 부모 요소에 대해 만들어진 테이블과 자식 요소에 대해 만들어진 테이블 모두에 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-105">A new column with a name of **ParentTableName_Id** will be added to both the table created for the parent element, and the table created for the child element.</span></span> <span data-ttu-id="716e1-106">이 id 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-106">The **ColumnMapping** property of this identity column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="716e1-107">열은 부모 테이블의 자동 증분 기본 키가 되며 두 테이블 간의 **DataRelation** 에 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-107">The column will be an auto-incrementing primary key for the parent table, and will be used for the **DataRelation** between the two tables.</span></span> <span data-ttu-id="716e1-108">추가 된 id 열의 데이터 형식은 System.string 이며 다른 모든 유추 된 열의 데이터 형식 ( **system.string**)과는 **다릅니다.**</span><span class="sxs-lookup"><span data-stu-id="716e1-108">The data type of the added identity column will be **System.Int32**, unlike the data type of all other inferred columns, which is **System.String**.</span></span> <span data-ttu-id="716e1-109"><xref:System.Data.ForeignKeyConstraint>   =  부모 테이블과 자식 테이블 모두에서 새 열을 사용 하 여 DeleteRule **Cascade** 가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-109">A <xref:System.Data.ForeignKeyConstraint> with **DeleteRule** = **Cascade** will also be created using the new column in both the parent and child tables.</span></span>  
  
 <span data-ttu-id="716e1-110">예를 들어, 다음과 같은 XML을 가정해 봅시다.</span><span class="sxs-lookup"><span data-stu-id="716e1-110">For example, consider the following XML:</span></span>  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 <span data-ttu-id="716e1-111">유추 프로세스에서는 **Element1** 및 **ChildElement1** 라는 두 개의 테이블을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-111">The inference process will produce two tables: **Element1** and **ChildElement1**.</span></span>  
  
 <span data-ttu-id="716e1-112">**Element1** 테이블에는 두 개의 열 **Element1_Id** 와 **childelement2 라는** 가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-112">The **Element1** table will have two columns: **Element1_Id** and **ChildElement2**.</span></span> <span data-ttu-id="716e1-113">**Element1_Id** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-113">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span> <span data-ttu-id="716e1-114">**Childelement2 라는** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-114">The **ColumnMapping** property of the **ChildElement2** column will be set to **MappingType.Element**.</span></span> <span data-ttu-id="716e1-115">**Element1_Id** 열은 **Element1** 테이블의 기본 키로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-115">The **Element1_Id** column will be set as the primary key of the **Element1** table.</span></span>  
  
 <span data-ttu-id="716e1-116">**ChildElement1** 테이블에는 **attr1**, **attr2** 및 **Element1_Id** 라는 세 개의 열이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-116">The **ChildElement1** table will have three columns: **attr1**, **attr2** and **Element1_Id**.</span></span> <span data-ttu-id="716e1-117">**Attr1** 및 **attr2** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-117">The **ColumnMapping** property for the **attr1** and **attr2** columns will be set to **MappingType.Attribute**.</span></span> <span data-ttu-id="716e1-118">**Element1_Id** 열의 **ColumnMapping** 속성은 **mappingtype.attribute** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-118">The **ColumnMapping** property of the **Element1_Id** column will be set to **MappingType.Hidden**.</span></span>  
  
 <span data-ttu-id="716e1-119">**DataRelation** 및 **ForeignKeyConstraint** 는 두 테이블의 **Element1_Id** 열을 사용 하 여 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="716e1-119">A **DataRelation** and **ForeignKeyConstraint** will be created using the **Element1_Id** columns from both tables.</span></span>  
  
 <span data-ttu-id="716e1-120">**데이터 집합:** DocumentElement</span><span class="sxs-lookup"><span data-stu-id="716e1-120">**DataSet:** DocumentElement</span></span>  
  
 <span data-ttu-id="716e1-121">**테이블:** Element1</span><span class="sxs-lookup"><span data-stu-id="716e1-121">**Table:** Element1</span></span>  
  
|<span data-ttu-id="716e1-122">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="716e1-122">Element1_Id</span></span>|<span data-ttu-id="716e1-123">ChildElement2</span><span class="sxs-lookup"><span data-stu-id="716e1-123">ChildElement2</span></span>|  
|------------------|-------------------|  
|<span data-ttu-id="716e1-124">0</span><span class="sxs-lookup"><span data-stu-id="716e1-124">0</span></span>|<span data-ttu-id="716e1-125">Text2</span><span class="sxs-lookup"><span data-stu-id="716e1-125">Text2</span></span>|  
  
 <span data-ttu-id="716e1-126">**테이블:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="716e1-126">**Table:** ChildElement1</span></span>  
  
|<span data-ttu-id="716e1-127">attr1</span><span class="sxs-lookup"><span data-stu-id="716e1-127">attr1</span></span>|<span data-ttu-id="716e1-128">attr2</span><span class="sxs-lookup"><span data-stu-id="716e1-128">attr2</span></span>|<span data-ttu-id="716e1-129">Element1_Id</span><span class="sxs-lookup"><span data-stu-id="716e1-129">Element1_Id</span></span>|  
|-----------|-----------|------------------|  
|<span data-ttu-id="716e1-130">value1</span><span class="sxs-lookup"><span data-stu-id="716e1-130">value1</span></span>|<span data-ttu-id="716e1-131">value2</span><span class="sxs-lookup"><span data-stu-id="716e1-131">value2</span></span>|<span data-ttu-id="716e1-132">0</span><span class="sxs-lookup"><span data-stu-id="716e1-132">0</span></span>|  
  
 <span data-ttu-id="716e1-133">**DataRelation:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="716e1-133">**DataRelation:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="716e1-134">**Parenttable:** Element1</span><span class="sxs-lookup"><span data-stu-id="716e1-134">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="716e1-135">**Parentcolumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="716e1-135">**ParentColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="716e1-136">**Childtable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="716e1-136">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="716e1-137">**Childcolumn:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="716e1-137">**ChildColumn:** Element1_Id</span></span>  
  
 <span data-ttu-id="716e1-138">**중첩:** True</span><span class="sxs-lookup"><span data-stu-id="716e1-138">**Nested:** True</span></span>  
  
 <span data-ttu-id="716e1-139">**ForeignKeyConstraint:** Element1_ChildElement1</span><span class="sxs-lookup"><span data-stu-id="716e1-139">**ForeignKeyConstraint:** Element1_ChildElement1</span></span>  
  
 <span data-ttu-id="716e1-140">**열:** Element1_Id</span><span class="sxs-lookup"><span data-stu-id="716e1-140">**Column:** Element1_Id</span></span>  
  
 <span data-ttu-id="716e1-141">**Parenttable:** Element1</span><span class="sxs-lookup"><span data-stu-id="716e1-141">**ParentTable:** Element1</span></span>  
  
 <span data-ttu-id="716e1-142">**Childtable:** ChildElement1</span><span class="sxs-lookup"><span data-stu-id="716e1-142">**ChildTable:** ChildElement1</span></span>  
  
 <span data-ttu-id="716e1-143">**DeleteRule:** 캐스케이딩</span><span class="sxs-lookup"><span data-stu-id="716e1-143">**DeleteRule:** Cascade</span></span>  
  
 <span data-ttu-id="716e1-144">**AcceptRejectRule:** 없음을</span><span class="sxs-lookup"><span data-stu-id="716e1-144">**AcceptRejectRule:** None</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="716e1-145">참고 항목</span><span class="sxs-lookup"><span data-stu-id="716e1-145">See also</span></span>

- [<span data-ttu-id="716e1-146">XML에서 데이터 세트 관계형 구조 유추</span><span class="sxs-lookup"><span data-stu-id="716e1-146">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)
- [<span data-ttu-id="716e1-147">XML에서 데이터 세트 로드</span><span class="sxs-lookup"><span data-stu-id="716e1-147">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)
- [<span data-ttu-id="716e1-148">XML에서 데이터 세트 스키마 정보 로드</span><span class="sxs-lookup"><span data-stu-id="716e1-148">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)
- [<span data-ttu-id="716e1-149">DataRelation 중첩</span><span class="sxs-lookup"><span data-stu-id="716e1-149">Nesting DataRelations</span></span>](nesting-datarelations.md)
- [<span data-ttu-id="716e1-150">데이터 세트에서 XML 사용</span><span class="sxs-lookup"><span data-stu-id="716e1-150">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)
- [<span data-ttu-id="716e1-151">DataSets, DataTables 및 DataViews</span><span class="sxs-lookup"><span data-stu-id="716e1-151">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="716e1-152">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="716e1-152">ADO.NET Overview</span></span>](../ado-net-overview.md)
