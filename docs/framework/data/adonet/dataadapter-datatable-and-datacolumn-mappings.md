---
title: DataAdapter DataTable 및 DataColumn 매핑
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: b979431836b55b23ac9ba6ec4535f33765dce555
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91177737"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a><span data-ttu-id="acc95-102">DataAdapter DataTable 및 DataColumn 매핑</span><span class="sxs-lookup"><span data-stu-id="acc95-102">DataAdapter DataTable and DataColumn Mappings</span></span>

<span data-ttu-id="acc95-103">**DataAdapter** 의 <xref:System.Data.Common.DataTableMapping> **TableMappings** 속성에는 0 개 이상의 개체 컬렉션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-103">A **DataAdapter** contains a collection of zero or more <xref:System.Data.Common.DataTableMapping> objects in its **TableMappings** property.</span></span> <span data-ttu-id="acc95-104">**DataTableMapping** 는 데이터 원본에 대 한 쿼리에서 반환 되는 데이터와에 대 한 마스터 매핑을 제공 <xref:System.Data.DataTable> 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-104">A **DataTableMapping** provides a master mapping between the data returned from a query against a data source, and a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="acc95-105">**DataTableMapping** 이름은 **DataTable** 이름 대신 **DataAdapter** 의 **Fill** 메서드에 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-105">The **DataTableMapping** name can be passed in place of the **DataTable** name to the **Fill** method of the **DataAdapter**.</span></span> <span data-ttu-id="acc95-106">다음 예에서는 **Authors** 테이블에 대해 **AuthorsMapping** 라는 **DataTableMapping** 를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-106">The following example creates a **DataTableMapping** named **AuthorsMapping** for the **Authors** table.</span></span>  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 <span data-ttu-id="acc95-107">**DataTableMapping** 를 사용 하면 데이터베이스와 다른 **DataTable** 에서 열 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-107">A **DataTableMapping** enables you to use column names in a **DataTable** that are different from those in the database.</span></span> <span data-ttu-id="acc95-108">**DataAdapter** 는 테이블이 업데이트 될 때 매핑을 사용 하 여 열을 일치 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-108">The **DataAdapter** uses the mapping to match the columns when the table is updated.</span></span>  
  
 <span data-ttu-id="acc95-109">**Dataadapter** 의 **Fill** 또는 **Update** 메서드를 호출할 때 **TableName** 또는 **DataTableMapping** 이름을 지정 하지 않으면 **dataadapter** 는 "Table" 이라는 **DataTableMapping** 을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-109">If you do not specify a **TableName** or a **DataTableMapping** name when calling the **Fill** or **Update** method of the **DataAdapter**, the **DataAdapter** looks for a **DataTableMapping** named "Table".</span></span> <span data-ttu-id="acc95-110">해당 **DataTableMapping** 없는 경우 **DataTable** 의 **TableName** 은 "Table"입니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-110">If that **DataTableMapping** does not exist, the **TableName** of the **DataTable** is "Table".</span></span> <span data-ttu-id="acc95-111">이름이 "Table" 인 **DataTableMapping** 를 만들어 기본 **DataTableMapping** 을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-111">You can specify a default **DataTableMapping** by creating a **DataTableMapping** with the name of "Table".</span></span>  
  
 <span data-ttu-id="acc95-112">다음 코드 예제에서는 네임 스페이스에서 **DataTableMapping** 을 만들고 <xref:System.Data.Common> 이름을 "Table"로 지정 하 여 지정 된 **DataAdapter** 의 기본 매핑으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-112">The following code example creates a **DataTableMapping** (from the <xref:System.Data.Common> namespace) and makes it the default mapping for the specified **DataAdapter** by naming it "Table".</span></span> <span data-ttu-id="acc95-113">그런 다음이 예에서는 쿼리 결과의 첫 번째 테이블 ( **northwind** 데이터베이스의 **Customers** 테이블)의 열을의 **Northwind Customers** 테이블에 있는 더 많은 사용자에 게 친숙 한 이름 집합으로 매핑합니다 <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="acc95-113">The example then maps the columns from the first table in the query result (the **Customers** table of the **Northwind** database) to a set of more user-friendly names in the **Northwind Customers** table in the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="acc95-114">매핑되지 않는 열의 경우 데이터 소스의 열 이름이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-114">For columns that are not mapped, the name of the column from the data source is used.</span></span>  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 <span data-ttu-id="acc95-115">고급 상황에서는 동일한 **DataAdapter** 를 사용 하 여 다른 매핑을 사용 하는 서로 다른 테이블의 로드를 지원 하도록 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-115">In more advanced situations, you may decide that you want the same **DataAdapter** to support loading different tables with different mappings.</span></span> <span data-ttu-id="acc95-116">이렇게 하려면 추가 **DataTableMapping** 개체를 추가 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-116">To do this, simply add additional **DataTableMapping** objects.</span></span>  
  
 <span data-ttu-id="acc95-117">**Fill** 메서드에 **데이터 집합** 의 인스턴스와 **DataTableMapping** 이름이 전달 되 면 해당 이름을 가진 매핑이 있는 경우 사용 됩니다. 그렇지 않으면 해당 이름을 가진 **DataTable** 이 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-117">When the **Fill** method is passed an instance of a **DataSet** and a **DataTableMapping** name, if a mapping with that name exists it is used; otherwise, a **DataTable** with that name is used.</span></span>  
  
 <span data-ttu-id="acc95-118">다음 예에서는 **Customers** 의 이름과 **DataTable** 이름이 **BizTalkSchema** 인 **DataTableMapping** 을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-118">The following examples create a **DataTableMapping** with a name of **Customers** and a **DataTable** name of **BizTalkSchema**.</span></span> <span data-ttu-id="acc95-119">그런 다음이 예에서는 SELECT 문에 의해 반환 된 행을 **BizTalkSchema** **DataTable** 에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-119">The example then maps the rows returned by the SELECT statement to the **BizTalkSchema** **DataTable**.</span></span>  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="acc95-120">열 매핑에 소스 열 이름을 제공하지 않거나 테이블 매핑에 소스 테이블 이름을 제공하지 않으면 기본 이름이 자동으로 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-120">If a source column name is not supplied for a column mapping or a source table name is not supplied for a table mapping, default names will be automatically generated.</span></span> <span data-ttu-id="acc95-121">열 매핑에 대해 원본 열이 제공 되지 않은 경우 열 매핑에는 **SourceColumn1** 로 시작 하는 **SourceColumn** *N* 의 증분 기본 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-121">If no source column is supplied for a column mapping, the column mapping is given an incremental default name of **SourceColumn** *N,* starting with **SourceColumn1**.</span></span> <span data-ttu-id="acc95-122">테이블 매핑에 대해 제공 된 원본 테이블 이름이 없으면 테이블 매핑에 **SourceTable1** 로 시작 하는 **SourceTable** *N* 의 증분 기본 이름이 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-122">If no source table name is supplied for a table mapping, the table mapping is given an incremental default name of **SourceTable** *N*, starting with **SourceTable1**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acc95-123">사용자가 제공 하는 이름이 **있는** 의 **ColumnMappingCollection** 또는 테이블 매핑 이름에 있는 기존 기본 열 매핑 이름과 충돌 하는 경우 열 매핑에 대 한 **SourceColumn** *n* 의 명명 규칙 또는 테이블 매핑의 **SourceTable** *n* 을 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-123">We recommend that you avoid the naming convention of **SourceColumn** *N* for a column mapping, or **SourceTable** *N* for a table mapping, because the name you supply may conflict with an existing default column mapping name in the **ColumnMappingCollection** or table mapping name in the **DataTableMappingCollection**.</span></span> <span data-ttu-id="acc95-124">이미 있는 이름을 제공하면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-124">If the supplied name already exists, an exception will be thrown.</span></span>  
  
## <a name="handling-multiple-result-sets"></a><span data-ttu-id="acc95-125">여러 개의 결과 집합 처리</span><span class="sxs-lookup"><span data-stu-id="acc95-125">Handling Multiple Result Sets</span></span>  

 <span data-ttu-id="acc95-126">**SelectCommand** 에서 여러 테이블을 반환 하는 경우 **채우기** 는 지정 된 테이블 이름부터 시작 하 여 **TableName1** 부터 *시작 하 여* **TableName** 형식으로 계속 하는 **데이터 집합** 의 테이블에 대 한 증분 값을 포함 하는 테이블 이름을 자동으로 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-126">If your **SelectCommand** returns multiple tables, **Fill** automatically generates table names with incremental values for the tables in the **DataSet**, starting with the specified table name and continuing on in the form **TableName** *N*, starting with **TableName1**.</span></span> <span data-ttu-id="acc95-127">테이블 매핑을 사용 하 여 자동으로 생성 된 테이블 이름을 **데이터 집합** 의 테이블에 대해 지정 하려는 이름에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-127">You can use table mappings to map the automatically generated table name to a name you want specified for the table in the **DataSet**.</span></span> <span data-ttu-id="acc95-128">예를 들어 **고객** 및 **주문의** 두 테이블을 반환 하는 **SelectCommand** 의 경우 **Fill** 에 대 한 다음 호출을 실행 합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-128">For example, for a **SelectCommand** that returns two tables, **Customers** and **Orders**, issue the following call to **Fill**.</span></span>  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 <span data-ttu-id="acc95-129">**데이터 집합** 에는 **Customers** 및 **Customers1** 라는 두 개의 테이블이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-129">Two tables are created in the **DataSet**: **Customers** and **Customers1**.</span></span> <span data-ttu-id="acc95-130">테이블 매핑을 사용 하 여 두 번째 테이블이 **Customers1** 대신 **Orders** 라는 이름으로 지정 되도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-130">You can use table mappings to ensure that the second table is named **Orders** instead of **Customers1**.</span></span> <span data-ttu-id="acc95-131">이렇게 하려면 다음 예제와 같이 **Customers1** 의 원본 테이블을 **데이터 집합** 테이블 **주문** 에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="acc95-131">To do this, map the source table of **Customers1** to the **DataSet** table **Orders**, as shown in the following example.</span></span>  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a><span data-ttu-id="acc95-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="acc95-132">See also</span></span>

- [<span data-ttu-id="acc95-133">DataAdapters 및 DataReaders</span><span class="sxs-lookup"><span data-stu-id="acc95-133">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="acc95-134">ADO.NET에서 데이터 검색 및 수정</span><span class="sxs-lookup"><span data-stu-id="acc95-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="acc95-135">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="acc95-135">ADO.NET Overview</span></span>](ado-net-overview.md)
