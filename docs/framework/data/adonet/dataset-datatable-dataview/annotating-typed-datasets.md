---
description: '자세히 알아보기: 형식화 된 데이터 집합 주석 달기'
title: 형식화된 데이터 세트에 주석 지정
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f82aaa62-321e-4c8a-b51b-9d1114700170
ms.openlocfilehash: 6f5838e94d88fd6c9b3a1991d4c8023d5892b784
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739705"
---
# <a name="annotating-typed-datasets"></a><span data-ttu-id="1b679-103">형식화된 데이터 세트에 주석 지정</span><span class="sxs-lookup"><span data-stu-id="1b679-103">Annotating Typed DataSets</span></span>

<span data-ttu-id="1b679-104">주석을 사용하면 원본으로 사용하는 스키마를 수정하지 않고 형식화된 <xref:System.Data.DataSet>의 요소 이름을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-104">Annotations enable you to modify the names of the elements in your typed <xref:System.Data.DataSet> without modifying the underlying schema.</span></span> <span data-ttu-id="1b679-105">기본 스키마의 요소 이름을 수정 하면 형식화 된 데이터 **집합이** 데이터 소스에 없는 개체를 참조 하 고 데이터 소스에 존재 하는 개체에 대 한 참조도 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-105">Modifying the names of the elements in your underlying schema would cause the typed **DataSet** to refer to objects that do not exist in the data source, as well as lose a reference to the objects that do exist in the data source.</span></span>  
  
 <span data-ttu-id="1b679-106">주석을 사용 하 여 형식화 된 **데이터 집합** 의 개체 이름을 더 의미 있는 이름으로 사용자 지정 하 여, 클라이언트에서 사용할 수 있는 코드를 더 쉽게 읽고 형식화 된 **데이터 집합** 을 쉽게 만들 수 있습니다. 기본 스키마는 그대로 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-106">Using annotations, you can customize the names of objects in your typed **DataSet** with more meaningful names, making code more readable and your typed **DataSet** easier for clients to use, while leaving underlying schema intact.</span></span> <span data-ttu-id="1b679-107">예를 들어 **Northwind** 데이터베이스의 **Customers** 테이블에 대 한 다음 스키마 요소는 **Customersrow** 및 명명 된 고객의 **DataRow** 개체 이름을 생성 <xref:System.Data.DataRowCollection> 합니다. </span><span class="sxs-lookup"><span data-stu-id="1b679-107">For example, the following schema element for the **Customers** table of the **Northwind** database would result in a **DataRow** object name of **CustomersRow** and a <xref:System.Data.DataRowCollection> named **Customers**.</span></span>  
  
```xml  
<xs:element name="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="1b679-108">**고객** 의 **DataRowCollection** 이름은 클라이언트 코드에서 의미가 있지만 **customersrow** 의 **DataRow** 이름은 단일 개체 이기 때문에 잘못 된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-108">A **DataRowCollection** name of **Customers** is meaningful in client code, but a **DataRow** name of **CustomersRow** is misleading because it is a single object.</span></span> <span data-ttu-id="1b679-109">또한 일반적인 시나리오에서 개체를 **행** 식별자 없이 참조 하 고 대신 **고객** 개체 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-109">Also, in common scenarios, the object would be referred to without the **Row** identifier and instead would be simply referred to as a **Customer** object.</span></span> <span data-ttu-id="1b679-110">이 솔루션은 스키마에 주석을 달고 **DataRow** 및 **DataRowCollection** 개체의 새 이름을 식별 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-110">The solution is to annotate the schema and identify new names for the **DataRow** and **DataRowCollection** objects.</span></span> <span data-ttu-id="1b679-111">다음 코드는 이전 스키마에 주석을 단 것입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-111">Following is the annotated version of the previous schema.</span></span>  
  
```xml  
<xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="1b679-112">**Customer** 의 **typedName** 값을 지정 하면 **DataRow** 개체 이름이 **customer** 가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-112">Specifying a **typedName** value of **Customer** will result in a **DataRow** object name of **Customer**.</span></span> <span data-ttu-id="1b679-113">**고객** 의 **typedPlural** 값을 지정 하면 **고객** 의 **DataRowCollection** 이름이 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-113">Specifying a **typedPlural** value of **Customers** preserves the **DataRowCollection** name of **Customers**.</span></span>  
  
 <span data-ttu-id="1b679-114">다음 표에서는 사용할 수 있는 주석을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-114">The following table shows the annotations available for use.</span></span>  
  
|<span data-ttu-id="1b679-115">Annotation</span><span class="sxs-lookup"><span data-stu-id="1b679-115">Annotation</span></span>|<span data-ttu-id="1b679-116">설명</span><span class="sxs-lookup"><span data-stu-id="1b679-116">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="1b679-117">**typedName**</span><span class="sxs-lookup"><span data-stu-id="1b679-117">**typedName**</span></span>|<span data-ttu-id="1b679-118">개체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-118">Name of the object.</span></span>|  
|<span data-ttu-id="1b679-119">**typedPlural**</span><span class="sxs-lookup"><span data-stu-id="1b679-119">**typedPlural**</span></span>|<span data-ttu-id="1b679-120">개체 컬렉션의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-120">Name of a collection of objects.</span></span>|  
|<span data-ttu-id="1b679-121">**typedParent**</span><span class="sxs-lookup"><span data-stu-id="1b679-121">**typedParent**</span></span>|<span data-ttu-id="1b679-122">부모 관계에서 참조될 때의 개체 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-122">Name of the object when referred to in a parent relationship.</span></span>|  
|<span data-ttu-id="1b679-123">**typedChildren**</span><span class="sxs-lookup"><span data-stu-id="1b679-123">**typedChildren**</span></span>|<span data-ttu-id="1b679-124">자식 관계에서 개체를 반환하기 위한 메서드의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-124">Name of the method to return objects from a child relationship.</span></span>|  
|<span data-ttu-id="1b679-125">**nullValue**</span><span class="sxs-lookup"><span data-stu-id="1b679-125">**nullValue**</span></span>|<span data-ttu-id="1b679-126">내부 값이 **DBNull** 인 경우 값입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-126">Value if the underlying value is **DBNull**.</span></span> <span data-ttu-id="1b679-127">**Nullvalue** 주석에 대해서는 다음 표를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b679-127">See the following table for **nullValue** annotations.</span></span> <span data-ttu-id="1b679-128">기본값은 **_throw** 입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-128">The default is **_throw**.</span></span>|  
  
 <span data-ttu-id="1b679-129">다음 표에서는 **Nullvalue** 주석에 대해 지정할 수 있는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-129">The following table shows the values that can be specified for the **nullValue** annotation.</span></span>  
  
|<span data-ttu-id="1b679-130">nullValue 값</span><span class="sxs-lookup"><span data-stu-id="1b679-130">nullValue Value</span></span>|<span data-ttu-id="1b679-131">설명</span><span class="sxs-lookup"><span data-stu-id="1b679-131">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="1b679-132">*대체 값*</span><span class="sxs-lookup"><span data-stu-id="1b679-132">*Replacement Value*</span></span>|<span data-ttu-id="1b679-133">반환될 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-133">Specify a value to be returned.</span></span> <span data-ttu-id="1b679-134">반환되는 값은 요소의 형식과 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-134">The returned value must match the type of the element.</span></span> <span data-ttu-id="1b679-135">예를 들어, `nullValue="0"`을 사용하여 null 정수 필드에 0을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-135">For example, use `nullValue="0"` to return 0 for null integer fields.</span></span>|  
|<span data-ttu-id="1b679-136">**_throw**</span><span class="sxs-lookup"><span data-stu-id="1b679-136">**_throw**</span></span>|<span data-ttu-id="1b679-137">예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-137">Throw an exception.</span></span> <span data-ttu-id="1b679-138">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-138">This is the default.</span></span>|  
|<span data-ttu-id="1b679-139">**_null**</span><span class="sxs-lookup"><span data-stu-id="1b679-139">**_null**</span></span>|<span data-ttu-id="1b679-140">기본 형식이 발견되면 null 참조를 반환하거나 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-140">Return a null reference or throw an exception if a primitive type is encountered.</span></span>|  
|<span data-ttu-id="1b679-141">**_empty**</span><span class="sxs-lookup"><span data-stu-id="1b679-141">**_empty**</span></span>|<span data-ttu-id="1b679-142">문자열의 경우 **system.string** 을 반환 하 고, 그렇지 않은 경우 빈 생성자에서 만든 개체를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-142">For strings, return **String.Empty**, otherwise return an object created from an empty constructor.</span></span> <span data-ttu-id="1b679-143">기본 형식이 발견되면 예외를 throw합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-143">If a primitive type is encountered, throw an exception.</span></span>|  
  
 <span data-ttu-id="1b679-144">다음 표에서는 형식화 된 **데이터 집합** 의 개체에 대 한 기본값과 사용 가능한 주석을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-144">The following table shows default values for objects in a typed **DataSet** and the available annotations.</span></span>  
  
|<span data-ttu-id="1b679-145">개체/메서드/이벤트</span><span class="sxs-lookup"><span data-stu-id="1b679-145">Object/Method/Event</span></span>|<span data-ttu-id="1b679-146">기본값</span><span class="sxs-lookup"><span data-stu-id="1b679-146">Default</span></span>|<span data-ttu-id="1b679-147">Annotation</span><span class="sxs-lookup"><span data-stu-id="1b679-147">Annotation</span></span>|  
|---------------------------|-------------|----------------|  
|<span data-ttu-id="1b679-148">**DataTable**</span><span class="sxs-lookup"><span data-stu-id="1b679-148">**DataTable**</span></span>|<span data-ttu-id="1b679-149">TableNameDataTable</span><span class="sxs-lookup"><span data-stu-id="1b679-149">TableNameDataTable</span></span>|<span data-ttu-id="1b679-150">typedPlural</span><span class="sxs-lookup"><span data-stu-id="1b679-150">typedPlural</span></span>|  
|<span data-ttu-id="1b679-151">**DataTable** 메서드</span><span class="sxs-lookup"><span data-stu-id="1b679-151">**DataTable** Methods</span></span>|<span data-ttu-id="1b679-152">NewTableNameRow</span><span class="sxs-lookup"><span data-stu-id="1b679-152">NewTableNameRow</span></span><br /><br /> <span data-ttu-id="1b679-153">AddTableNameRow</span><span class="sxs-lookup"><span data-stu-id="1b679-153">AddTableNameRow</span></span><br /><br /> <span data-ttu-id="1b679-154">DeleteTableNameRow</span><span class="sxs-lookup"><span data-stu-id="1b679-154">DeleteTableNameRow</span></span>|<span data-ttu-id="1b679-155">typedName</span><span class="sxs-lookup"><span data-stu-id="1b679-155">typedName</span></span>|  
|<span data-ttu-id="1b679-156">**DataRowCollection**</span><span class="sxs-lookup"><span data-stu-id="1b679-156">**DataRowCollection**</span></span>|<span data-ttu-id="1b679-157">TableName</span><span class="sxs-lookup"><span data-stu-id="1b679-157">TableName</span></span>|<span data-ttu-id="1b679-158">typedPlural</span><span class="sxs-lookup"><span data-stu-id="1b679-158">typedPlural</span></span>|  
|<span data-ttu-id="1b679-159">**DataRow**</span><span class="sxs-lookup"><span data-stu-id="1b679-159">**DataRow**</span></span>|<span data-ttu-id="1b679-160">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="1b679-160">TableNameRow</span></span>|<span data-ttu-id="1b679-161">typedName</span><span class="sxs-lookup"><span data-stu-id="1b679-161">typedName</span></span>|  
|<span data-ttu-id="1b679-162">**DataColumn**</span><span class="sxs-lookup"><span data-stu-id="1b679-162">**DataColumn**</span></span>|<span data-ttu-id="1b679-163">DataTable.ColumnNameColumn</span><span class="sxs-lookup"><span data-stu-id="1b679-163">DataTable.ColumnNameColumn</span></span><br /><br /> <span data-ttu-id="1b679-164">DataRow.ColumnName</span><span class="sxs-lookup"><span data-stu-id="1b679-164">DataRow.ColumnName</span></span>|<span data-ttu-id="1b679-165">typedName</span><span class="sxs-lookup"><span data-stu-id="1b679-165">typedName</span></span>|  
|<span data-ttu-id="1b679-166">**속성**</span><span class="sxs-lookup"><span data-stu-id="1b679-166">**Property**</span></span>|<span data-ttu-id="1b679-167">PropertyName</span><span class="sxs-lookup"><span data-stu-id="1b679-167">PropertyName</span></span>|<span data-ttu-id="1b679-168">typedName</span><span class="sxs-lookup"><span data-stu-id="1b679-168">typedName</span></span>|  
|<span data-ttu-id="1b679-169">**자식** 접근자</span><span class="sxs-lookup"><span data-stu-id="1b679-169">**Child** Accessor</span></span>|<span data-ttu-id="1b679-170">GetChildTableNameRows</span><span class="sxs-lookup"><span data-stu-id="1b679-170">GetChildTableNameRows</span></span>|<span data-ttu-id="1b679-171">typedChildren</span><span class="sxs-lookup"><span data-stu-id="1b679-171">typedChildren</span></span>|  
|<span data-ttu-id="1b679-172">**부모** 접근자</span><span class="sxs-lookup"><span data-stu-id="1b679-172">**Parent** Accessor</span></span>|<span data-ttu-id="1b679-173">TableNameRow</span><span class="sxs-lookup"><span data-stu-id="1b679-173">TableNameRow</span></span>|<span data-ttu-id="1b679-174">typedParent</span><span class="sxs-lookup"><span data-stu-id="1b679-174">typedParent</span></span>|  
|<span data-ttu-id="1b679-175">**데이터 집합** 이벤트</span><span class="sxs-lookup"><span data-stu-id="1b679-175">**DataSet** Events</span></span>|<span data-ttu-id="1b679-176">TableNameRowChangeEvent</span><span class="sxs-lookup"><span data-stu-id="1b679-176">TableNameRowChangeEvent</span></span><br /><br /> <span data-ttu-id="1b679-177">TableNameRowChangeEventHandler</span><span class="sxs-lookup"><span data-stu-id="1b679-177">TableNameRowChangeEventHandler</span></span>|<span data-ttu-id="1b679-178">typedName</span><span class="sxs-lookup"><span data-stu-id="1b679-178">typedName</span></span>|  
  
 <span data-ttu-id="1b679-179">형식화 된 **데이터 집합** 주석을 사용 하려면 XSD (XML 스키마 정의 언어) 스키마에 다음 **xmlns** 참조를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-179">To use typed **DataSet** annotations, you must include the following **xmlns** reference in your XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="1b679-180">데이터베이스 테이블에서 xsd를 만들려면 <xref:System.Data.DataSet.WriteXmlSchema%2A> 또는 [Visual Studio에서 데이터 집합 작업](/visualstudio/data-tools/dataset-tools-in-visual-studio)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b679-180">To create an xsd from database tables, see <xref:System.Data.DataSet.WriteXmlSchema%2A> or [Working with Datasets in Visual Studio](/visualstudio/data-tools/dataset-tools-in-visual-studio).</span></span>  
  
```xml  
xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
```  
  
 <span data-ttu-id="1b679-181">다음은 포함 된 **Orders** 테이블과 관련 된 **Northwind** 데이터베이스의 **Customers** 테이블을 표시 하는 주석이 추가 된 샘플 스키마입니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-181">The following is a sample annotated schema that exposes the **Customers** table of the **Northwind** database with a relation to the **Orders** table included.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet"
      xmlns:codegen="urn:schemas-microsoft-com:xml-msprop"  
      xmlns=""
      xmlns:xs="http://www.w3.org/2001/XMLSchema"
      xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers" codegen:typedName="Customer" codegen:typedPlural="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID" type="xs:string" minOccurs="0" />  
              <xs:element name="CompanyName"  
codegen:typedName="CompanyName" type="xs:string" minOccurs="0" />  
              <xs:element name="Phone" codegen:typedName="Phone" codegen:nullValue="" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
        <xs:element name="Orders" codegen:typedName="Order" codegen:typedPlural="Orders">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="OrderID" codegen:typedName="OrderID"  
type="xs:int" minOccurs="0" />  
              <xs:element name="CustomerID"  
codegen:typedName="CustomerID"                  codegen:nullValue="" type="xs:string" minOccurs="0" />  
              <xs:element name="EmployeeID"  
codegen:typedName="EmployeeID" codegen:nullValue="0"
type="xs:int" minOccurs="0" />  
              <xs:element name="OrderAdapter"  
codegen:typedName="OrderAdapter" codegen:nullValue="1980-01-01T00:00:00"
type="xs:dateTime" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
    <xs:unique name="Constraint1">  
      <xs:selector xpath=".//Customers" />  
      <xs:field xpath="CustomerID" />  
    </xs:unique>  
    <xs:keyref name="CustOrders" refer="Constraint1"  
codegen:typedParent="Customer" codegen:typedChildren="GetOrders">  
      <xs:selector xpath=".//Orders" />  
      <xs:field xpath="CustomerID" />  
    </xs:keyref>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="1b679-182">다음 코드 예제에서는 샘플 스키마에서 만든 강력한 형식의 **데이터 집합** 을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-182">The following code example uses a strongly typed **DataSet** created from the sample schema.</span></span> <span data-ttu-id="1b679-183">하나를 사용 하 여 <xref:System.Data.SqlClient.SqlDataAdapter> **Customers** 테이블을 채우고 <xref:System.Data.SqlClient.SqlDataAdapter> **Orders** 테이블을 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-183">It uses one <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Customers** table and another <xref:System.Data.SqlClient.SqlDataAdapter> to populate the **Orders** table.</span></span> <span data-ttu-id="1b679-184">강력한 형식의 **데이터 집합** 은 **datarelations** 을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b679-184">The strongly typed **DataSet** defines the **DataRelations**.</span></span>  
  
```vb  
' Assumes a valid SqlConnection object named connection.  
Dim customerAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT CustomerID, CompanyName, Phone FROM Customers", &  
    connection)  
Dim orderAdapter As SqlDataAdapter = New SqlDataAdapter( _  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders", &  
    connection)  
  
' Populate a strongly typed DataSet.  
connection.Open()  
Dim customers As CustomerDataSet = New CustomerDataSet()  
customerAdapter.Fill(customers, "Customers")  
orderAdapter.Fill(customers, "Orders")  
connection.Close()  
  
' Add a strongly typed event.  
AddHandler customers.Customers.CustomerChanged, &  
    New CustomerDataSet.CustomerChangeEventHandler( _  
    AddressOf OnCustomerChanged)  
  
' Add a strongly typed DataRow.  
Dim newCustomer As CustomerDataSet.Customer = _  
    customers.Customers.NewCustomer()  
newCustomer.CustomerID = "NEW01"  
newCustomer.CompanyName = "My New Company"  
customers.Customers.AddCustomer(newCustomer)  
  
' Navigate the child relation.  
Dim customer As CustomerDataSet.Customer  
Dim order As CustomerDataSet.Order  
  
For Each customer In customers.Customers  
  Console.WriteLine(customer.CustomerID)  
  For Each order In customer.GetOrders()  
    Console.WriteLine(vbTab & order.OrderID)  
  Next  
Next  
  
Private Shared Sub OnCustomerChanged( _  
    sender As Object, e As CustomerDataSet.CustomerChangeEvent)  
  
End Sub  
```  
  
```csharp  
// Assumes a valid SqlConnection object named connection.  
SqlDataAdapter customerAdapter = new SqlDataAdapter(  
    "SELECT CustomerID, CompanyName, Phone FROM Customers",  
    connection);  
SqlDataAdapter orderAdapter = new SqlDataAdapter(  
    "SELECT OrderID, CustomerID, EmployeeID, OrderAdapter FROM Orders",
    connection);  
  
// Populate a strongly typed DataSet.  
connection.Open();  
CustomerDataSet customers = new CustomerDataSet();  
customerAdapter.Fill(customers, "Customers");  
orderAdapter.Fill(customers, "Orders");  
connection.Close();  
  
// Add a strongly typed event.  
customers.Customers.CustomerChanged += new
  CustomerDataSet.CustomerChangeEventHandler(OnCustomerChanged);  
  
// Add a strongly typed DataRow.  
CustomerDataSet.Customer newCustomer =
    customers.Customers.NewCustomer();  
newCustomer.CustomerID = "NEW01";  
newCustomer.CompanyName = "My New Company";  
customers.Customers.AddCustomer(newCustomer);  
  
// Navigate the child relation.  
foreach(CustomerDataSet.Customer customer in customers.Customers)  
{  
  Console.WriteLine(customer.CustomerID);  
  foreach(CustomerDataSet.Order order in customer.GetOrders())  
    Console.WriteLine("\t" + order.OrderID);  
}  
  
protected static void OnCustomerChanged(object sender, CustomerDataSet.CustomerChangeEvent e)  
    {  
  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b679-185">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1b679-185">See also</span></span>

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [<span data-ttu-id="1b679-186">형식화된 데이터 세트</span><span class="sxs-lookup"><span data-stu-id="1b679-186">Typed DataSets</span></span>](typed-datasets.md)
- [<span data-ttu-id="1b679-187">DataSets, DataTables 및 DataViews</span><span class="sxs-lookup"><span data-stu-id="1b679-187">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="1b679-188">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="1b679-188">ADO.NET Overview</span></span>](../ado-net-overview.md)
