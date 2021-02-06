---
description: '자세한 정보: DataTable 이벤트 처리'
title: DataTable 이벤트 처리
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62f404a5-13ea-4b93-a29f-55b74a16c9d3
ms.openlocfilehash: 89519345ec0c9f2348153c480366396a66d37ae0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99652356"
---
# <a name="handling-datatable-events"></a><span data-ttu-id="82b99-103">DataTable 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="82b99-103">Handling DataTable Events</span></span>

<span data-ttu-id="82b99-104"><xref:System.Data.DataTable> 개체는 애플리케이션에서 처리할 수 있는 일련의 이벤트를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-104">The <xref:System.Data.DataTable> object provides a series of events that can be processed by an application.</span></span> <span data-ttu-id="82b99-105">다음 표에서는 `DataTable` 이벤트에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-105">The following table describes `DataTable` events.</span></span>  
  
|<span data-ttu-id="82b99-106">이벤트</span><span class="sxs-lookup"><span data-stu-id="82b99-106">Event</span></span>|<span data-ttu-id="82b99-107">설명</span><span class="sxs-lookup"><span data-stu-id="82b99-107">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Data.DataTable.Initialized>|<span data-ttu-id="82b99-108"><xref:System.Data.DataTable.EndInit%2A>의 `DataTable` 메서드가 호출된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-108">Occurs after the <xref:System.Data.DataTable.EndInit%2A> method of a `DataTable` is called.</span></span> <span data-ttu-id="82b99-109">이 이벤트는 기본적으로 디자인 타임 시나리오를 지원하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-109">This event is intended primarily to support design-time scenarios.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanged>|<span data-ttu-id="82b99-110"><xref:System.Data.DataColumn>에서 값이 성공적으로 변경된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-110">Occurs after a value has been successfully changed in a <xref:System.Data.DataColumn>.</span></span>|  
|<xref:System.Data.DataTable.ColumnChanging>|<span data-ttu-id="82b99-111">`DataColumn`의 값이 제출될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-111">Occurs when a value has been submitted for a `DataColumn`.</span></span>|  
|<xref:System.Data.DataTable.RowChanged>|<span data-ttu-id="82b99-112">`DataColumn` 값 또는 <xref:System.Data.DataRow.RowState%2A>에 있는 <xref:System.Data.DataRow>의 `DataTable`가 성공적으로 변경된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-112">Occurs after a `DataColumn` value or the <xref:System.Data.DataRow.RowState%2A> of a <xref:System.Data.DataRow> in the `DataTable` has been changed successfully.</span></span>|  
|<xref:System.Data.DataTable.RowChanging>|<span data-ttu-id="82b99-113">`DataColumn` 값 또는 `RowState`에 있는 `DataRow`의 `DataTable`에 대한 변경된 값이 제출될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-113">Occurs when a change has been submitted for a `DataColumn` value or the `RowState` of a `DataRow` in the `DataTable`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleted>|<span data-ttu-id="82b99-114">`DataRow`의 `DataTable`가 `Deleted`로 표시된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-114">Occurs after a `DataRow` in the `DataTable` has been marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.RowDeleting>|<span data-ttu-id="82b99-115">`DataRow`의 `DataTable`가 `Deleted`로 표시되기 전에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-115">Occurs before a `DataRow` in the `DataTable` is marked as `Deleted`.</span></span>|  
|<xref:System.Data.DataTable.TableCleared>|<span data-ttu-id="82b99-116"><xref:System.Data.DataTable.Clear%2A>의 `DataTable` 메서드 호출을 통해 모든 `DataRow`가 성공적으로 삭제된 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-116">Occurs after a call to the <xref:System.Data.DataTable.Clear%2A> method of the `DataTable` has successfully cleared every `DataRow`.</span></span>|  
|<xref:System.Data.DataTable.TableClearing>|<span data-ttu-id="82b99-117">`Clear` 메서드가 호출된 후 `Clear` 작업이 시작되기 전에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-117">Occurs after the `Clear` method is called but before the `Clear` operation begins.</span></span>|  
|<xref:System.Data.DataTable.TableNewRow>|<span data-ttu-id="82b99-118">`DataRow`의 `NewRow` 메서드 호출을 통해 새 `DataTable`가 만들어진 후에 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-118">Occurs after a new `DataRow` is created by a call to the `NewRow` method of the `DataTable`.</span></span>|  
|<xref:System.ComponentModel.MarshalByValueComponent.Disposed>|<span data-ttu-id="82b99-119">`DataTable`이 `Disposed`가 될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-119">Occurs when the `DataTable` is `Disposed`.</span></span> <span data-ttu-id="82b99-120"><xref:System.ComponentModel.MarshalByValueComponent>에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-120">Inherited from <xref:System.ComponentModel.MarshalByValueComponent>.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="82b99-121">행을 추가하거나 삭제하는 대부분의 작업은 `ColumnChanged` 및 `ColumnChanging` 이벤트를 발생시키지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-121">Most operations that add or delete rows do not raise the `ColumnChanged` and `ColumnChanging` events.</span></span> <span data-ttu-id="82b99-122">그러나 `ReadXml` 메서드는 `ColumnChanged` 및 `ColumnChanging` 이벤트를 발생시킵니다. 단, 읽고 있는 XML 문서가 `XmlReadMode`이고 `DiffGram`가 `Auto` 또는 `DiffGram`로 설정되어 있는 경우는 예외입니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-122">However, the `ReadXml` method does raise `ColumnChanged` and `ColumnChanging` events, unless the `XmlReadMode` is set to `DiffGram` or is set to `Auto` when the XML document being read is a `DiffGram`.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="82b99-123">`DataSet` 이벤트가 발생한 `RowChanged`에서 데이터를 수정하면 데이터가 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-123">Data corruption can occur if data is modified in a `DataSet` from which the `RowChanged` event is raised.</span></span> <span data-ttu-id="82b99-124">이와 같은 데이터 손상이 발생하면 예외가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-124">No exception will be raised if such data corruption occurs.</span></span>  
  
## <a name="additional-related-events"></a><span data-ttu-id="82b99-125">추가 관련 이벤트</span><span class="sxs-lookup"><span data-stu-id="82b99-125">Additional Related Events</span></span>  

 <span data-ttu-id="82b99-126"><xref:System.Data.DataTable.Constraints%2A> 속성은 <xref:System.Data.ConstraintCollection> 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-126">The <xref:System.Data.DataTable.Constraints%2A> property holds a <xref:System.Data.ConstraintCollection> instance.</span></span> <span data-ttu-id="82b99-127"><xref:System.Data.ConstraintCollection> 클래스는 <xref:System.Data.ConstraintCollection.CollectionChanged> 이벤트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-127">The <xref:System.Data.ConstraintCollection> class exposes a <xref:System.Data.ConstraintCollection.CollectionChanged> event.</span></span> <span data-ttu-id="82b99-128">이 이벤트는 `ConstraintCollection`에서 제약 조건이 추가되거나 수정되거나 제거될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-128">This event fires when a constraint is added, modified, or removed from the `ConstraintCollection`.</span></span>  
  
 <span data-ttu-id="82b99-129"><xref:System.Data.DataTable.Columns%2A> 속성은 <xref:System.Data.DataColumnCollection> 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-129">The <xref:System.Data.DataTable.Columns%2A> property holds a <xref:System.Data.DataColumnCollection> instance.</span></span> <span data-ttu-id="82b99-130">`DataColumnCollection` 클래스는 <xref:System.Data.DataColumnCollection.CollectionChanged> 이벤트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-130">The `DataColumnCollection` class exposes a <xref:System.Data.DataColumnCollection.CollectionChanged> event.</span></span> <span data-ttu-id="82b99-131">이 이벤트는 `DataColumn`에서 `DataColumnCollection`이 추가되거나 수정되거나 제거될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-131">This event fires when a `DataColumn` is added, modified, or removed from the `DataColumnCollection`.</span></span> <span data-ttu-id="82b99-132">열의 이름, 형식, 식 또는 위치 등이 변경되어 열이 수정되면 이 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-132">Modifications that cause the event to fire include changes to the name, type, expression or ordinal position of a column.</span></span>  
  
 <span data-ttu-id="82b99-133"><xref:System.Data.DataSet.Tables%2A>의 <xref:System.Data.DataSet> 속성은 <xref:System.Data.DataTableCollection> 인스턴스를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-133">The <xref:System.Data.DataSet.Tables%2A> property of a <xref:System.Data.DataSet> holds a <xref:System.Data.DataTableCollection> instance.</span></span> <span data-ttu-id="82b99-134">`DataTableCollection` 클래스는 `CollectionChanged`와 `CollectionChanging` 이벤트를 모두 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-134">The `DataTableCollection` class exposes both a `CollectionChanged` and a `CollectionChanging` event.</span></span> <span data-ttu-id="82b99-135">이 두 이벤트는 `DataTable`에서 `DataSet`이 추가되거나 제거될 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-135">These events fire when a `DataTable` is added to or removed from the `DataSet`.</span></span>  
  
 <span data-ttu-id="82b99-136">`DataRows`가 변경되는 경우에도 관련 <xref:System.Data.DataView>의 이벤트가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-136">Changes to `DataRows` can also trigger events for an associated <xref:System.Data.DataView>.</span></span> <span data-ttu-id="82b99-137">`DataView` 클래스는 <xref:System.Data.DataView.ListChanged> 값이 변경되거나 뷰의 구성 또는 정렬 순서가 변경될 때 발생하는 `DataColumn` 이벤트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-137">The `DataView` class exposes a <xref:System.Data.DataView.ListChanged> event that fires when a `DataColumn` value changes or when the composition or sort order of the view changes.</span></span> <span data-ttu-id="82b99-138"><xref:System.Data.DataRowView> 클래스는 관련 <xref:System.Data.DataRowView.PropertyChanged> 값이 변경될 때 발생하는 `DataColumn` 이벤트를 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-138">The <xref:System.Data.DataRowView> class exposes a <xref:System.Data.DataRowView.PropertyChanged> event that fires when an associated `DataColumn` value changes.</span></span>  
  
## <a name="sequence-of-operations"></a><span data-ttu-id="82b99-139">작업 순서</span><span class="sxs-lookup"><span data-stu-id="82b99-139">Sequence of Operations</span></span>  

 <span data-ttu-id="82b99-140">다음은 `DataRow`가 추가, 수정 또는 삭제되는 경우의 작업 순서입니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-140">Here is the sequence of operations that occur when a `DataRow` is added, modified, or deleted:</span></span>  
  
1. <span data-ttu-id="82b99-141">제안된 레코드를 만들고 변경 내용을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-141">Create the proposed record and apply any changes.</span></span>  
  
2. <span data-ttu-id="82b99-142">식이 아닌 열의 제약 조건을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-142">Check constraints for non-expression columns.</span></span>  
  
3. <span data-ttu-id="82b99-143">가능한 경우 `RowChanging` 또는 `RowDeleting` 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-143">Raise the `RowChanging` or `RowDeleting` events as applicable.</span></span>  
  
4. <span data-ttu-id="82b99-144">제안된 레코드를 현재 레코드로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-144">Set the proposed record to be the current record.</span></span>  
  
5. <span data-ttu-id="82b99-145">관련된 인덱스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-145">Update any associated indexes.</span></span>  
  
6. <span data-ttu-id="82b99-146">관련 `ListChanged` 개체에 대해 `DataView` 이벤트를 발생시키고, 관련 `PropertyChanged` 개체에 대해 `DataRowView` 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-146">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects.</span></span>  
  
7. <span data-ttu-id="82b99-147">모든 식 열을 계산합니다. 단, 열의 제약 조건 검사는 지금 수행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-147">Evaluate all expression columns, but delay checking any constraints on these columns.</span></span>  
  
8. <span data-ttu-id="82b99-148">식 열 계산 결과에 영향을 받은 관련 `ListChanged` 개체에 대해 `DataView` 이벤트를 발생시키고, 관련 `PropertyChanged` 개체에 대해 `DataRowView` 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-148">Raise `ListChanged` events for associated `DataView` objects and `PropertyChanged` events for associated `DataRowView` objects affected by the expression column evaluations.</span></span>  
  
9. <span data-ttu-id="82b99-149">가능한 경우 `RowChanged` 또는 `RowDeleted` 이벤트를 발생시킵니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-149">Raise `RowChanged` or `RowDeleted` events as applicable.</span></span>  
  
10. <span data-ttu-id="82b99-150">식 열의 제약 조건을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-150">Check constraints on expression columns.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="82b99-151">식 열이 변경되는 경우에는 `DataTable` 이벤트가 발생하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-151">Changes to expression columns never raise `DataTable` events.</span></span> <span data-ttu-id="82b99-152">식 열이 변경되면 `DataView` 및 `DataRowView` 이벤트만 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-152">Changes to expression columns only raise `DataView` and `DataRowView` events.</span></span> <span data-ttu-id="82b99-153">식 열은 다른 여러 열에 종속될 수 있으므로 단일 `DataRow` 작업 중 여러 번 계산될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-153">Expression columns can have dependencies on multiple other columns, and can be evaluated multiple times during a single `DataRow` operation.</span></span> <span data-ttu-id="82b99-154">식을 계산할 때마다 이벤트가 발생합니다. 또한 식 열이 변경되는 경우 동일한 식 열에 대한 여러 이벤트를 포함하여 단일 `DataRow` 작업에서 여러 `ListChanged` 및 `PropertyChanged` 이벤트가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-154">Each expression evaluation raises events, and a single `DataRow` operation can raise multiple `ListChanged` and `PropertyChanged` events when expression columns are affected, possibly including multiple events for the same expression column.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="82b99-155"><xref:System.NullReferenceException> 이벤트 처리기 내에서 `RowChanged`을 throw하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="82b99-155">Do not throw a <xref:System.NullReferenceException> within the `RowChanged` event handler.</span></span> <span data-ttu-id="82b99-156"><xref:System.NullReferenceException>이 `RowChanged`의 `DataTable` 이벤트 내에서 throw되면 `DataTable`이 손상됩니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-156">If a <xref:System.NullReferenceException> is thrown within the `RowChanged` event of a `DataTable`, then the `DataTable` will be corrupted.</span></span>  
  
### <a name="example"></a><span data-ttu-id="82b99-157">예제</span><span class="sxs-lookup"><span data-stu-id="82b99-157">Example</span></span>  

 <span data-ttu-id="82b99-158">다음 예제에서는 `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared` 및 `TableClearing` 이벤트에 대한 이벤트 처리기를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-158">The following example demonstrates how to create event handlers for the `RowChanged`, `RowChanging`, `RowDeleted`, `RowDeleting`, `ColumnChanged`, `ColumnChanging`, `TableNewRow`, `TableCleared`, and `TableClearing` events.</span></span> <span data-ttu-id="82b99-159">각 이벤트 처리기는 이벤트가 발생하면 콘솔 창에 해당 출력을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="82b99-159">Each event handler displays output in the console window when it is fired.</span></span>  
  
 [!code-csharp[DataWorks DataTable.Events#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DataTable.Events/CS/source.cs#1)]
 [!code-vb[DataWorks DataTable.Events#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DataTable.Events/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="82b99-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="82b99-160">See also</span></span>

- [<span data-ttu-id="82b99-161">DataTable에서 데이터 조작</span><span class="sxs-lookup"><span data-stu-id="82b99-161">Manipulating Data in a DataTable</span></span>](manipulating-data-in-a-datatable.md)
- [<span data-ttu-id="82b99-162">DataAdapter 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="82b99-162">Handling DataAdapter Events</span></span>](../handling-dataadapter-events.md)
- [<span data-ttu-id="82b99-163">데이터 세트 이벤트 처리</span><span class="sxs-lookup"><span data-stu-id="82b99-163">Handling DataSet Events</span></span>](handling-dataset-events.md)
- [<span data-ttu-id="82b99-164">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="82b99-164">ADO.NET Overview</span></span>](../ado-net-overview.md)
