---
description: Datarow 및 Datarowview에 대해 자세히 알아보세요.
title: DataRow 및 DataRowView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8f5eec26-b809-4aca-8778-7e202356d856
ms.openlocfilehash: d7700922a9ae76fb9898412b6a08394059e6e494
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724949"
---
# <a name="datarows-and-datarowviews"></a>DataRow 및 DataRowView

<xref:System.Data.DataView>는 <xref:System.Data.DataRowView> 개체의 열거할 수 있는 컬렉션을 노출시킵니다. **DataRowView** 개체는 기본 테이블에 있는 열의 이름 또는 서 수 참조로 인덱싱되는 개체 배열로 값을 노출 합니다. <xref:System.Data.DataRow>DataRowView의 속성을 사용 하 여 **DataRowView** 에 의해 노출 되는에 액세스할 수 있습니다 <xref:System.Data.DataRowView.Row%2A> .   
  
 **DataRowView** 를 사용 하 여 값을 볼 때 <xref:System.Data.DataView.RowStateFilter%2A> **DataView** 의 속성은 기본 **DataRow** 가 노출 되는 행 버전을 결정 합니다. **DataRow** 를 사용 하 여 다른 행 버전에 액세스 하는 방법에 대 한 자세한 내용은 [행 상태 및 행 버전](row-states-and-row-versions.md)을 참조 하세요.  
  
 다음 코드 예제에서는 테이블의 현재 값과 원래 값을 모두 표시합니다.  
  
```vb  
Dim catView As DataView = New DataView(catDS.Tables("Categories"))  
Console.WriteLine("Current Values:")  
WriteView(catView)  
Console.WriteLine("Original Values:")  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal  
WriteView(catView)
  
Public Shared Sub WriteView(thisDataView As DataView)  
  Dim rowView As DataRowView  
  Dim i As Integer  
  
  For Each rowView In thisDataView  
    For i = 0 To thisDataView.Table.Columns.Count - 1  
      Console.Write(rowView(i) & vbTab)  
    Next  
    Console.WriteLine()  
  Next  
End Sub  
```  
  
```csharp  
DataView catView = new DataView(catDS.Tables["Categories"]);  
Console.WriteLine("Current Values:");  
WriteView(catView);  
Console.WriteLine("Original Values:");  
catView.RowStateFilter = DataViewRowState.ModifiedOriginal;  
WriteView(catView);  
  
public static void WriteView(DataView thisDataView)  
{  
  foreach (DataRowView rowView in thisDataView)  
  {  
    for (int i = 0; i < thisDataView.Table.Columns.Count; i++)  
      Console.Write(rowView[i] + "\t");  
    Console.WriteLine();  
  }  
}  
```  
  
## <a name="see-also"></a>참고 항목

- <xref:System.Data.DataRowVersion>
- <xref:System.Data.DataViewRowState>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [데이터 보기](dataviews.md)
- [ADO.NET 개요](../ado-net-overview.md)
