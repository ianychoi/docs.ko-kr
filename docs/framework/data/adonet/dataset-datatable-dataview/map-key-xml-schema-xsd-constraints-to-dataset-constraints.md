---
description: '자세한 정보: 데이터 집합 제약 조건에 키 XSD (XML 스키마) 제약 조건 매핑'
title: 데이터 세트 제약 조건에 키 XSD(XML 스키마) 제약 조건 매핑
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 0c07b53e06dc6b80395764b2bdd76045ee80bffd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651992"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="c7d37-103">데이터 세트 제약 조건에 키 XSD(XML 스키마) 제약 조건 매핑</span><span class="sxs-lookup"><span data-stu-id="c7d37-103">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>

<span data-ttu-id="c7d37-104">스키마에서 **key** 요소를 사용 하 여 요소 또는 특성에 대 한 키 제약 조건을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-104">In a schema, you can specify a key constraint on an element or attribute using the **key** element.</span></span> <span data-ttu-id="c7d37-105">KEY 제약 조건이 지정된 요소 또는 특성은 모든 스키마 인스턴스에서 고유한 값을 가져야 하며 null 값을 가져서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-105">The element or attribute on which a key constraint is specified must have unique values in any schema instance, and cannot have null values.</span></span>  
  
 <span data-ttu-id="c7d37-106">KEY 제약 조건이 정의된 열이 null 값을 가질 수 없다는 것을 제외하면, key 제약 조건은 UNIQUE 제약 조건과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-106">The key constraint is similar to the unique constraint, except that the column on which a key constraint is defined cannot have null values.</span></span>  
  
 <span data-ttu-id="c7d37-107">다음 표에서는 **key** 요소에 지정할 수 있는 **msdata** 특성을 간략하게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-107">The following table outlines the **msdata** attributes that you can specify in the **key** element.</span></span>  
  
|<span data-ttu-id="c7d37-108">특성 이름</span><span class="sxs-lookup"><span data-stu-id="c7d37-108">Attribute name</span></span>|<span data-ttu-id="c7d37-109">설명</span><span class="sxs-lookup"><span data-stu-id="c7d37-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c7d37-110">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="c7d37-110">**msdata:ConstraintName**</span></span>|<span data-ttu-id="c7d37-111">이 특성을 지정하면 해당 값이 제약 조건 이름으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-111">If this attribute is specified, its value is used as the constraint name.</span></span> <span data-ttu-id="c7d37-112">그렇지 않으면 **name** 특성은 제약 조건 이름의 값을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-112">Otherwise, the **name** attribute provides the value of the constraint name.</span></span>|  
|<span data-ttu-id="c7d37-113">**msdata:PrimaryKey**</span><span class="sxs-lookup"><span data-stu-id="c7d37-113">**msdata:PrimaryKey**</span></span>|<span data-ttu-id="c7d37-114">`PrimaryKey="true"`이 있으면 **IsPrimaryKey** 제약 조건 속성이 **true** 로 설정 되어 기본 키로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-114">If `PrimaryKey="true"` is present, the **IsPrimaryKey** constraint property is set to **true**, thus making it a primary key.</span></span> <span data-ttu-id="c7d37-115">기본 키에는 null 값을 사용할 수 없으므로 **Allowdbnull** 열 속성은 **false** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-115">The **AllowDBNull** column property is set to **false**, because primary keys cannot have null values.</span></span>|  
  
 <span data-ttu-id="c7d37-116">키 제약 조건이 지정 된 스키마를 변환 하는 동안 매핑 프로세스에서는 제약 조건의 각 열에 대해 **Allowdbnull** column 속성이 **false** 로 설정 된 unique 제약 조건을 테이블에 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-116">In converting schema in which a key constraint is specified, the mapping process creates a unique constraint on the table with the **AllowDBNull** column property set to **false** for each column in the constraint.</span></span> <span data-ttu-id="c7d37-117">Key 요소에을 지정 하지 않은 경우 unique 제약 조건의 **IsPrimaryKey** 속성도 **false** 로 설정 됩니다 `msdata:PrimaryKey="true"` . </span><span class="sxs-lookup"><span data-stu-id="c7d37-117">The **IsPrimaryKey** property of the unique constraint is also set to **false** unless you have specified `msdata:PrimaryKey="true"` on the **key** element.</span></span> <span data-ttu-id="c7d37-118">이것은 `PrimaryKey="true"`인 스키마의 UNIQUE 제약 조건에도 마찬가지로 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-118">This is identical to a unique constraint in the schema in which `PrimaryKey="true"`.</span></span>  
  
 <span data-ttu-id="c7d37-119">다음 스키마 예제에서 **key** 요소는 **CustomerID** 요소에 대 한 키 제약 조건을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-119">In the following schema example, the **key** element specifies the key constraint on the **CustomerID** element.</span></span>  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>
```  
  
 <span data-ttu-id="c7d37-120">**Key** 요소는 **Customers** 요소의 **CustomerID** 자식 요소 값에 고유한 값이 있어야 하 고 null 값을 가질 수 없도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-120">The **key** element specifies that the values of the **CustomerID** child element of the **Customers** element must have unique values and cannot have null values.</span></span> <span data-ttu-id="c7d37-121">XSD(XML 스키마 정의 언어) 스키마를 변환할 때 매핑 프로세스에서는 다음 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-121">In translating the XML Schema definition language (XSD) schema, the mapping process creates the following table:</span></span>  
  
```text  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="c7d37-122">XML 스키마 매핑은 다음과 같이 **CustomerID** 열에도 **UniqueConstraint** 를 만듭니다 <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="c7d37-122">The XML Schema mapping also creates a **UniqueConstraint** on the **CustomerID** column, as shown in the following <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="c7d37-123">여기에서는 편의를 위해 관련 속성만 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-123">(For simplicity, only relevant properties are shown.)</span></span>  
  
```text  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID
      IsPrimaryKey: True  
```  
  
 <span data-ttu-id="c7d37-124">생성 된 **데이터 집합** 에서 스키마가 키 요소에를 지정 하기 때문에 **UniqueConstraint** 의 **IsPrimaryKey** 속성은 **true** 로 설정 됩니다 `msdata:PrimaryKey="true"`  .</span><span class="sxs-lookup"><span data-stu-id="c7d37-124">In the **DataSet** that is generated, the **IsPrimaryKey** property of the **UniqueConstraint** is set to **true** because the schema specifies `msdata:PrimaryKey="true"` in the **key** element.</span></span>  
  
 <span data-ttu-id="c7d37-125">**데이터 집합** 에 있는 **UniqueConstraint** 의 **ConstraintName** 속성 값은 스키마의 **키** 요소에 지정 된 **msdata: ConstraintName** 특성의 값입니다.</span><span class="sxs-lookup"><span data-stu-id="c7d37-125">The value of the **ConstraintName** property of the **UniqueConstraint** in the **DataSet** is the value of the **msdata:ConstraintName** attribute specified in the **key** element in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d37-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="c7d37-126">See also</span></span>

- [<span data-ttu-id="c7d37-127">데이터 세트 제약 조건에 XSD(XML 스키마) 제약 조건 매핑</span><span class="sxs-lookup"><span data-stu-id="c7d37-127">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="c7d37-128">XSD(XML 스키마)에서 데이터 세트 관계 생성</span><span class="sxs-lookup"><span data-stu-id="c7d37-128">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="c7d37-129">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="c7d37-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
