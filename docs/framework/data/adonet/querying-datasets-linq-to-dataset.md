---
description: '자세한 정보: 데이터 집합 쿼리 (LINQ to DataSet)'
title: 데이터 집합 쿼리(LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: 609de99069d39317d8d372cb2a7f43ea301ada2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99663458"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="10d25-103">데이터 집합 쿼리(LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="10d25-103">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="10d25-104"><xref:System.Data.DataSet> 개체에 데이터가 채워지면 개체에 대한 쿼리를 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-104">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="10d25-105">LINQ to DataSet 사용 하 여 쿼리를 작성 하는 것은 다른 LINQ 사용 데이터 소스에 대해 LINQ (Language-Integrated Query)를 사용 하는 것과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-105">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="10d25-106">그러나 개체에 대해 LINQ 쿼리를 사용 하는 경우 <xref:System.Data.DataSet> <xref:System.Data.DataRow> 사용자 지정 형식의 열거형 대신 개체의 열거형을 쿼리 하 게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-106">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="10d25-107">즉, LINQ 쿼리에서 클래스의 멤버 중 하나를 사용할 수 있습니다 <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="10d25-107">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="10d25-108">이렇게 하면 다양 한 복잡 한 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-108">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="10d25-109">LINQ의 다른 구현과 마찬가지로 쿼리 식 구문과 메서드 기반 쿼리 구문 이라는 두 가지 형식으로 LINQ to DataSet 쿼리를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-109">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="10d25-110">쿼리 식 구문 또는 메서드 기반 쿼리 구문을 사용하여 <xref:System.Data.DataSet>의 단일 테이블, <xref:System.Data.DataSet>의 여러 테이블 또는 형식화된 <xref:System.Data.DataSet>의 테이블에 대해 쿼리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-110">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="10d25-111">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="10d25-111">In This Section</span></span>  

 [<span data-ttu-id="10d25-112">단일 테이블 쿼리</span><span class="sxs-lookup"><span data-stu-id="10d25-112">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="10d25-113">단일 테이블 쿼리를 수행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-113">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="10d25-114">크로스 테이블 쿼리</span><span class="sxs-lookup"><span data-stu-id="10d25-114">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="10d25-115">크로스 테이블 쿼리를 수행하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-115">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="10d25-116">형식화된 데이터 세트 쿼리</span><span class="sxs-lookup"><span data-stu-id="10d25-116">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="10d25-117">형식화된 <xref:System.Data.DataSet> 개체를 쿼리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="10d25-117">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10d25-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="10d25-118">See also</span></span>

- [<span data-ttu-id="10d25-119">LINQ to DataSet 예제</span><span class="sxs-lookup"><span data-stu-id="10d25-119">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="10d25-120">데이터를 데이터 세트에 로드</span><span class="sxs-lookup"><span data-stu-id="10d25-120">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
