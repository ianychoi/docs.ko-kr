---
description: '다음에 대해 자세히 알아보기: ChildViews 및 관계'
title: ChildView 및 관계
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d475d356-6abb-4701-8fd1-2906fb93dfba
ms.openlocfilehash: f27526ef0ad5bee70b0c67542e2611ff85b156f8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739718"
---
# <a name="childviews-and-relations"></a><span data-ttu-id="ffce9-103">ChildView 및 관계</span><span class="sxs-lookup"><span data-stu-id="ffce9-103">ChildViews and Relations</span></span>

<span data-ttu-id="ffce9-104"><xref:System.Data.DataSet>의 테이블 사이에 관계가 존재하는 경우 부모 테이블의 행에 대한 <xref:System.Data.DataView>의 <xref:System.Data.DataRowView.CreateChildView%2A> 메서드를 사용하여 관련 자식 테이블의 행이 포함된 <xref:System.Data.DataRowView>를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ffce9-104">If a relationship exists between tables in a <xref:System.Data.DataSet>, you can create a <xref:System.Data.DataView> containing rows from the related child table by using the <xref:System.Data.DataRowView.CreateChildView%2A> method of the <xref:System.Data.DataRowView> for the rows in the parent table.</span></span> <span data-ttu-id="ffce9-105">예를 들어 다음 코드는 **범주** 와 관련 된 **제품** 을 범주 및 **ProductName** 을 기준으로 사전순으로 정렬 **하 여 표시** 합니다.</span><span class="sxs-lookup"><span data-stu-id="ffce9-105">For example, the following code displays **Categories** and their related **Products** in alphabetical order sorted by **CategoryName** and **ProductName**.</span></span>  
  
```vb  
Dim catTable As DataTable = catDS.Tables("Categories")  
Dim prodTable As DataTable = catDS.Tables("Products")  
  
' Create a relation between the Categories and Products tables.  
Dim relation As DataRelation = catDS.Relations.Add("CatProdRel", _  
  catTable.Columns("CategoryID"), _  
  prodTable.Columns("CategoryID"))  
  
' Create DataViews for the Categories and Products tables.  
Dim catView As DataView = New DataView(catTable, "", _  
  "CategoryName", DataViewRowState.CurrentRows)  
Dim prodView As DataView  
  
' Iterate through the Categories table.  
Dim catDRV, prodDRV As DataRowView  
  
For Each catDRV In catView  
  Console.WriteLine(catDRV("CategoryName"))  
  
  ' Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation)  
  prodView.Sort = "ProductName"  
  
  For Each prodDRV In prodView  
    Console.WriteLine(vbTab & prodDRV("ProductName"))  
  Next  
Next  
```  
  
```csharp  
DataTable catTable = catDS.Tables["Categories"];  
DataTable prodTable = catDS.Tables["Products"];  
  
// Create a relation between the Categories and Products tables.  
DataRelation relation = catDS.Relations.Add("CatProdRel",
  catTable.Columns["CategoryID"],  
                                                            prodTable.Columns["CategoryID"]);  
  
// Create DataViews for the Categories and Products tables.  
DataView catView = new DataView(catTable, "", "CategoryName",
  DataViewRowState.CurrentRows);  
DataView prodView;  
  
// Iterate through the Categories table.  
foreach (DataRowView catDRV in catView)  
{  
  Console.WriteLine(catDRV["CategoryName"]);  
  
  // Create a DataView of the child product records.  
  prodView = catDRV.CreateChildView(relation);  
  prodView.Sort = "ProductName";  
  
  foreach (DataRowView prodDRV in prodView)  
    Console.WriteLine("\t" + prodDRV["ProductName"]);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffce9-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ffce9-106">See also</span></span>

- <xref:System.Data.DataSet>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="ffce9-107">데이터 보기</span><span class="sxs-lookup"><span data-stu-id="ffce9-107">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="ffce9-108">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="ffce9-108">ADO.NET Overview</span></span>](../ado-net-overview.md)
