---
description: '자세한 정보: DataViews 수정'
title: 데이터 보기 수정
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: e0f62c0b8553cd4b83c28da99b8bdec316c8a91d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651836"
---
# <a name="modifying-dataviews"></a><span data-ttu-id="3a8fd-103">데이터 보기 수정</span><span class="sxs-lookup"><span data-stu-id="3a8fd-103">Modifying DataViews</span></span>

<span data-ttu-id="3a8fd-104"><xref:System.Data.DataView>를 사용하여 원본 테이블의 데이터 행을 추가, 삭제 또는 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-104">You can use the <xref:System.Data.DataView> to add, delete, or modify rows of data in the underlying table.</span></span> <span data-ttu-id="3a8fd-105">**Dataview를** 사용 하 여 기본 테이블의 데이터를 수정 하는 기능은 **dataview** 의 세 가지 부울 속성 중 하나를 설정 하 여 제어 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-105">The ability to use the **DataView** to modify data in the underlying table is controlled by setting one of three Boolean properties of the **DataView**.</span></span> <span data-ttu-id="3a8fd-106">이러한 속성에는 <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A> 및 <xref:System.Data.DataView.AllowDelete%2A>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-106">These properties are <xref:System.Data.DataView.AllowNew%2A>, <xref:System.Data.DataView.AllowEdit%2A>, and <xref:System.Data.DataView.AllowDelete%2A>.</span></span> <span data-ttu-id="3a8fd-107">기본적으로 **true** 로 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-107">They are set to **true** by default.</span></span>  
  
 <span data-ttu-id="3a8fd-108">**AllowNew** 가 **True** 인 경우 <xref:System.Data.DataView.AddNew%2A> **DataView** 의 메서드를 사용 하 여 새를 만들 수 있습니다 <xref:System.Data.DataRowView> .</span><span class="sxs-lookup"><span data-stu-id="3a8fd-108">If **AllowNew** is **true**, you can use the <xref:System.Data.DataView.AddNew%2A> method of the **DataView** to create a new <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="3a8fd-109"><xref:System.Data.DataTable> <xref:System.Data.DataRowView.EndEdit%2A> **DataRowView** 의 메서드가 호출 될 때까지 새 행은 실제로 내부에 추가 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-109">Note that a new row is not actually added to the underlying <xref:System.Data.DataTable> until the <xref:System.Data.DataRowView.EndEdit%2A> method of the **DataRowView** is called.</span></span> <span data-ttu-id="3a8fd-110"><xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView** 의 메서드를 호출 하면 새 행이 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-110">If the <xref:System.Data.DataRowView.CancelEdit%2A> method of the **DataRowView** is called, the new row is discarded.</span></span> <span data-ttu-id="3a8fd-111">또한 한 번에 하나의 **DataRowView** 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-111">Note also that you can edit only one **DataRowView** at a time.</span></span> <span data-ttu-id="3a8fd-112">보류 중인 행이 있는 동안 **DataRowView** 의 **AddNew** 또는 **BeginEdit** 메서드를 호출 하면 보류 중인 행에서 **EndEdit** 가 암시적으로 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-112">If you call the **AddNew** or **BeginEdit** method of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3a8fd-113">**EndEdit** 가 호출 되 면 변경 내용이 기본 **datatable** 에 적용 되며, 나중에 **DataTable**, **DataSet** 또는 **DataRow** 개체의 **AcceptChanges** 또는 **RejectChanges** 메서드를 사용 하 여 커밋하거나 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-113">When **EndEdit** is called, the changes are applied to the underlying **DataTable** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3a8fd-114">**AllowNew** 가 **false** 이면 **DataRowView** 의 **AddNew** 메서드를 호출 하면 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-114">If **AllowNew** is **false**, an exception is thrown if you call the **AddNew** method of the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3a8fd-115">**Allowedit** 이 **True** 인 경우 **DataRowView** 을 통해 **DataRow** 의 내용을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-115">If **AllowEdit** is **true**, you can modify the contents of a **DataRow** via the **DataRowView**.</span></span> <span data-ttu-id="3a8fd-116">EndEdit를 사용 하 여 기본 행의 변경 내용을 확인 하거나 **DataRowView** 를 사용 하 여 변경 내용을 **DataRowView** 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-116">You can confirm changes to the underlying row using **DataRowView.EndEdit** or reject the changes using **DataRowView.CancelEdit**.</span></span> <span data-ttu-id="3a8fd-117">행은 한 번에 하나씩만 편집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-117">Note that only one row can be edited at a time.</span></span> <span data-ttu-id="3a8fd-118">보류 중인 행이 있는 동안 **DataRowView** 의 **AddNew** 또는 **BeginEdit** 메서드를 호출 하는 경우 **EndEdit** 는 보류 중인 행에서 암시적으로 호출 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-118">If you call the **AddNew** or **BeginEdit** methods of the **DataRowView** while a pending row exists, **EndEdit** is implicitly called on the pending row.</span></span> <span data-ttu-id="3a8fd-119">**EndEdit** 를 호출 하면 제안 된 변경 내용이 기본 **DataRow** 의 **현재** 행 버전에 배치 되 고 나중에 **DataTable**, **DataSet** 또는 **DataRow** 개체의 **AcceptChanges** 또는 **RejectChanges** 메서드를 사용 하 여 커밋하거나 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-119">When **EndEdit** is called, proposed changes are placed in the **Current** row version of the underlying **DataRow** and can later be committed or rejected using the **AcceptChanges** or **RejectChanges** methods of the **DataTable**, **DataSet**, or **DataRow** object.</span></span> <span data-ttu-id="3a8fd-120">**Allowedit** 이 **False** 인 경우 **DataView** 에서 값을 수정 하려고 하면 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-120">If **AllowEdit** is **false**, an exception is thrown if you attempt to modify a value in the **DataView**.</span></span>  
  
 <span data-ttu-id="3a8fd-121">기존 **DataRowView** 을 편집 하는 경우 기본 **DataTable** 의 이벤트는 제안 된 변경 내용으로 계속 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-121">When an existing **DataRowView** is being edited, events of the underlying **DataTable** will still be raised with the proposed changes.</span></span> <span data-ttu-id="3a8fd-122">기본 **DataRow** 에서 **EndEdit** 또는 **CancelEdit** 를 호출 하면 **DataRowView** 에서 **EndEdit** 또는 **CancelEdit** 가 호출 되었는지 여부에 관계 없이 보류 중인 변경 내용이 적용 되거나 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-122">Note that if you call **EndEdit** or **CancelEdit** on the underlying **DataRow**, pending changes will be applied or canceled regardless of whether **EndEdit** or **CancelEdit** is called on the **DataRowView**.</span></span>  
  
 <span data-ttu-id="3a8fd-123">**Allowdelete** 가 **True** 인 경우 **Dataview** 또는 **DataRowView** 개체의 **delete** 메서드를 사용 하 여 **dataview** 에서 행을 삭제할 수 있으며 행은 기본 **DataTable** 에서 삭제 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-123">If **AllowDelete** is **true**, you can delete rows from the **DataView** by using the **Delete** method of the **DataView** or **DataRowView** object, and the rows are deleted from the underlying **DataTable**.</span></span> <span data-ttu-id="3a8fd-124">나중에 **AcceptChanges** 또는 **RejectChanges** 를 사용 하 여 삭제를 커밋하거나 거부할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-124">You can later commit or reject the deletes using **AcceptChanges** or **RejectChanges** respectively.</span></span> <span data-ttu-id="3a8fd-125">**Allowdelete** 가 **False** 인 경우 **DataView** 또는 **DataRowView** 의 **Delete** 메서드를 호출 하면 예외가 throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-125">If **AllowDelete** is **false**, an exception is thrown if you call the **Delete** method of the **DataView** or **DataRowView**.</span></span>  
  
 <span data-ttu-id="3a8fd-126">다음 코드 예제 **에서는 dataview를** 사용 하 여 행을 삭제 하 고 **dataview** 를 사용 하 여 기본 테이블에 새 행을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3a8fd-126">The following code example disables using the **DataView** to delete rows  and adds a new row to the underlying table using the **DataView**.</span></span>  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a8fd-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3a8fd-127">See also</span></span>

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [<span data-ttu-id="3a8fd-128">데이터 보기</span><span class="sxs-lookup"><span data-stu-id="3a8fd-128">DataViews</span></span>](dataviews.md)
- [<span data-ttu-id="3a8fd-129">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="3a8fd-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
