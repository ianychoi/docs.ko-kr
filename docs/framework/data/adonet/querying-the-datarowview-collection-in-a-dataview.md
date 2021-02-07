---
description: '자세한 정보: DataView에서 DataRowView Collection 쿼리'
title: DataView에서 DataRowView 컬렉션 쿼리
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 2158e1c82c530c48d7edad71f46f03cbfe566536
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99695933"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a><span data-ttu-id="e191c-103">DataView에서 DataRowView 컬렉션 쿼리</span><span class="sxs-lookup"><span data-stu-id="e191c-103">Querying the DataRowView Collection in a DataView</span></span>

<span data-ttu-id="e191c-104"><xref:System.Data.DataView>는 <xref:System.Data.DataRowView> 개체의 열거할 수 있는 컬렉션을 노출합니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-104">The <xref:System.Data.DataView> exposes an enumerable collection of <xref:System.Data.DataRowView> objects.</span></span> <span data-ttu-id="e191c-105"><xref:System.Data.DataRowView>는 <xref:System.Data.DataRow>의 사용자 지정 뷰를 나타내고 컨트롤에 해당 <xref:System.Data.DataRow>의 특정 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-105"><xref:System.Data.DataRowView> represents a customized view of a <xref:System.Data.DataRow> and displays a specific version of that <xref:System.Data.DataRow> in a control.</span></span> <span data-ttu-id="e191c-106"><xref:System.Data.DataRow>와 같은 컨트롤을 통해서는 <xref:System.Windows.Forms.DataGridView>의 한 버전만 표시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-106">Only one version of a <xref:System.Data.DataRow> can be displayed through a control, such as a <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="e191c-107"><xref:System.Data.DataRow>의 <xref:System.Data.DataRowView> 속성을 통해 <xref:System.Data.DataRowView.Row%2A>에 의해 노출되는 <xref:System.Data.DataRowView>에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-107">You can access the <xref:System.Data.DataRow> that is exposed by the <xref:System.Data.DataRowView> through the <xref:System.Data.DataRowView.Row%2A> property of the <xref:System.Data.DataRowView>.</span></span> <span data-ttu-id="e191c-108"><xref:System.Data.DataRowView>를 사용하여 값을 보는 경우 <xref:System.Data.DataView.RowStateFilter%2A> 속성에 따라 원본 <xref:System.Data.DataRow>에서 노출되는 행 버전이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-108">When you view values by using a <xref:System.Data.DataRowView>, the <xref:System.Data.DataView.RowStateFilter%2A> property determines which row version of the underlying <xref:System.Data.DataRow> is exposed.</span></span> <span data-ttu-id="e191c-109">을 사용 하 여 다른 행 버전에 액세스 하는 방법에 대 한 자세한 내용은 <xref:System.Data.DataRow> [행 상태 및 행 버전](./dataset-datatable-dataview/row-states-and-row-versions.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e191c-109">For information about accessing different row versions using a <xref:System.Data.DataRow>, see [Row States and Row Versions](./dataset-datatable-dataview/row-states-and-row-versions.md).</span></span> <span data-ttu-id="e191c-110"><xref:System.Data.DataRowView>에 의해 노출 되는 개체의 컬렉션 <xref:System.Data.DataView> 은 열거 가능 하므로 LINQ to DataSet를 사용 하 여 쿼리를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-110">Because the collection of <xref:System.Data.DataRowView> objects exposed by the <xref:System.Data.DataView> is enumerable, you can use LINQ to DataSet to query over it.</span></span>  
  
 <span data-ttu-id="e191c-111">다음 예제에서는 `Product` 테이블에서 색상이 빨강인 제품을 쿼리하고 쿼리 결과로부터 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-111">The following example queries the `Product` table for red-colored products and creates a table from that query.</span></span> <span data-ttu-id="e191c-112">이 테이블에서 <xref:System.Data.DataView>를 만들고, 삭제되고 수정된 행을 필터링하도록 <xref:System.Data.DataView.RowStateFilter%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-112">A <xref:System.Data.DataView> is created from the table and the <xref:System.Data.DataView.RowStateFilter%2A> property is set to filter on deleted and modified rows.</span></span> <span data-ttu-id="e191c-113">그런 다음 LINQ 쿼리의 소스로 <xref:System.Data.DataView>를 사용하고, 수정되고 삭제된 <xref:System.Data.DataRowView> 개체를 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-113">The <xref:System.Data.DataView> is then used as a source in a LINQ query, and the <xref:System.Data.DataRowView> objects that have been modified and deleted are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 <span data-ttu-id="e191c-114">다음 예제에서는 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩된 뷰에서 제품 테이블을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-114">The following example creates a table of products from a view that is bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e191c-115"><xref:System.Data.DataView>에서 색상이 빨강인 제품을 쿼리하고 정렬된 결과를 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="e191c-115">The <xref:System.Data.DataView> is queried for red-colored products and the ordered results are bound to a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a><span data-ttu-id="e191c-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e191c-116">See also</span></span>

- [<span data-ttu-id="e191c-117">데이터 바인딩 및 LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e191c-117">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
