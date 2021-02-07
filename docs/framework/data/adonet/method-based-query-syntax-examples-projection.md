---
description: '자세한 정보: Method-Based 쿼리 구문 예제: 프로젝션 (LINQ to DataSet)'
title: '메서드 기반 쿼리 구문 예제: 프로젝션(LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0fc2c8f0-1967-4f30-8b20-39b8dccfb82f
ms.openlocfilehash: 380c35962ed122f5d4bbe85ba3fbd87cf7d7a3bf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754383"
---
# <a name="method-based-query-syntax-examples-projection-linq-to-dataset"></a><span data-ttu-id="d187a-103">메서드 기반 쿼리 구문 예제: 프로젝션(LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d187a-103">Method-Based Query Syntax Examples: Projection (LINQ to DataSet)</span></span>

<span data-ttu-id="d187a-104">이 항목의 예제에서는 <xref:System.Linq.Enumerable.Select%2A> 및 <xref:System.Linq.Enumerable.SelectMany%2A> 메서드에서 메서드 기반 쿼리 구문을 사용하여 <xref:System.Data.DataSet>을 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-104">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the method-based query syntax.</span></span>  
  
 <span data-ttu-id="d187a-105">이러한 예제에서 사용되는 `FillDataSet` 메서드는 [데이터집합에 데이터를 로드](loading-data-into-a-dataset.md)하는데 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-105">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="d187a-106">이 항목의 예제에서는 AdventureWorks 샘플 데이터베이스의 Contact, Address, Product, SalesOrderHeader 및 SalesOrderDetail 테이블을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-106">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="d187a-107">이 항목의 예제에서는 다음 문을 사용 합니다 `using` / `Imports` .</span><span class="sxs-lookup"><span data-stu-id="d187a-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="d187a-108">자세한 내용은 [방법: Visual Studio에서 LINQ to DataSet 프로젝트 만들기](how-to-create-a-linq-to-dataset-project-in-vs.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d187a-108">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="d187a-109">선택</span><span class="sxs-lookup"><span data-stu-id="d187a-109">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="d187a-110">예제</span><span class="sxs-lookup"><span data-stu-id="d187a-110">Example</span></span>  

 <span data-ttu-id="d187a-111">이 예제에서는 <xref:System.Linq.Enumerable.Select%2A> 메서드를 사용하여 `Name`, `ProductNumber` 및 `ListPrice` 속성을 익명 형식 시퀀스로 프로젝션합니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-111">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to project the `Name`, `ProductNumber`, and `ListPrice` properties to a sequence of anonymous types.</span></span>  <span data-ttu-id="d187a-112">`ListPrice` 속성 이름도 결과 형식에서 `Price`로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-112">The `ListPrice` property is also renamed to `Price` in the resulting type.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="selectmany"></a><span data-ttu-id="d187a-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="d187a-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="d187a-114">예제</span><span class="sxs-lookup"><span data-stu-id="d187a-114">Example</span></span>  

 <span data-ttu-id="d187a-115">이 예제에서는 <xref:System.Linq.Enumerable.SelectMany%2A> 메서드를 사용하여 `TotalDue`가 500.00보다 작은 모든 주문을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-115">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom_mq)]  
  
### <a name="example"></a><span data-ttu-id="d187a-116">예제</span><span class="sxs-lookup"><span data-stu-id="d187a-116">Example</span></span>  

 <span data-ttu-id="d187a-117">이 예제에서는 <xref:System.Linq.Enumerable.SelectMany%2A> 메서드를 사용하여 2002년 10월 1일 이후에 작성된 모든 주문을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d187a-117">This example uses the <xref:System.Linq.Enumerable.SelectMany%2A> method to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="d187a-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d187a-118">See also</span></span>

- [<span data-ttu-id="d187a-119">데이터를 데이터 세트에 로드</span><span class="sxs-lookup"><span data-stu-id="d187a-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="d187a-120">LINQ to DataSet 예제</span><span class="sxs-lookup"><span data-stu-id="d187a-120">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="d187a-121">표준 쿼리 연산자 개요(C#)</span><span class="sxs-lookup"><span data-stu-id="d187a-121">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="d187a-122">표준 쿼리 연산자 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d187a-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
