---
description: '자세한 정보: LINQ 소개 (Visual Basic)'
title: LINQ 소개
ms.date: 07/20/2015
ms.assetid: c6339c12-9b2d-433e-961c-0d2b7f0091c2
ms.openlocfilehash: b6be93bbf9b458ca19068961617ee08f67601edc
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426792"
---
# <a name="introduction-to-linq-visual-basic"></a><span data-ttu-id="d6c0a-103">LINQ 소개(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-103">Introduction to LINQ (Visual Basic)</span></span>

<span data-ttu-id="d6c0a-104">LINQ(Language-Integrated Query)는 개체 환경과 데이터 환경 간의 간격을 연결하는 .NET Framework 버전 3.5에서 도입된 혁신입니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-104">Language-Integrated Query (LINQ) is an innovation introduced in the .NET Framework version 3.5 that bridges the gap between the world of objects and the world of data.</span></span>  
  
 <span data-ttu-id="d6c0a-105">일반적으로 데이터에 대한 쿼리는 컴파일 시간의 형식 검사나 IntelliSense 지원 없이 간단한 문자열로 표현됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-105">Traditionally, queries against data are expressed as simple strings without type checking at compile time or IntelliSense support.</span></span> <span data-ttu-id="d6c0a-106">또한 데이터 원본의 각 유형에 대해 다른 쿼리 언어를 배워야 합니다. SQL 데이터베이스, XML 문서, 다양한 웹 서비스 등.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-106">Furthermore, you have to learn a different query language for each type of data source: SQL databases, XML documents, various Web services, and so on.</span></span> <span data-ttu-id="d6c0a-107">LINQ는 Visual Basic에서 *쿼리* 를 최고 수준의 언어 구문으로 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-107">LINQ makes a *query* a first-class language construct in Visual Basic.</span></span> <span data-ttu-id="d6c0a-108">언어 키워드 및 친숙한 연산자를 사용하여 강력한 형식의 개체 컬렉션에 대해 쿼리를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-108">You write queries against strongly typed collections of objects by using language keywords and familiar operators.</span></span>  
  
 <span data-ttu-id="d6c0a-109">SQL Server 데이터베이스, XML 문서, ADO.NET 데이터 집합 및 또는 제네릭 인터페이스를 지 원하는 개체의 컬렉션에 대 한 Visual Basic에 LINQ 쿼리를 작성할 수 있습니다 <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="d6c0a-109">You can write LINQ queries in Visual Basic for SQL Server databases, XML documents, ADO.NET Datasets, and any collection of objects that supports <xref:System.Collections.IEnumerable> or the generic <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="d6c0a-110">LINQ는 많은 웹 서비스 및 기타 데이터베이스 구현을 위해 타사에서도 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-110">LINQ support is also provided by third parties for many Web services and other database implementations.</span></span>  
  
 <span data-ttu-id="d6c0a-111">LINQ 쿼리는 새 프로젝트에서 사용하거나 기존 프로젝트에서 LINQ가 아닌 쿼리와 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-111">You can use LINQ queries in new projects, or alongside non-LINQ queries in existing projects.</span></span> <span data-ttu-id="d6c0a-112">프로젝트가 .NET Framework 3.5 이상을 대상으로 하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-112">The only requirement is that the project target .NET Framework 3.5 or later.</span></span>  
  
 <span data-ttu-id="d6c0a-113">다음 그림에서는 Visual Studio에서 전체 형식 검사 및 IntelliSense를 지원하는 C#과 Visual Basic을 사용하여 SQL Server 데이터베이스에 대해 부분적으로 완성된 LINQ 쿼리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-113">The following illustration from Visual Studio shows a partially-completed LINQ query against a SQL Server database in both C# and Visual Basic with full type checking and IntelliSense support.</span></span>  
  
 ![Intellisense를 사용하는 LINQ 쿼리를 보여주는 다이어그램](./media/introduction-to-linq/linq-query-intellisense.png)  
  
## <a name="next-steps"></a><span data-ttu-id="d6c0a-115">다음 단계</span><span class="sxs-lookup"><span data-stu-id="d6c0a-115">Next Steps</span></span>  

 <span data-ttu-id="d6c0a-116">LINQ에 대 한 자세한 내용을 보려면 시작 섹션의 [Linq 시작 Visual Basic](getting-started-with-linq.md)에서 몇 가지 기본 개념을 숙지 한 다음 관심 있는 linq 기술에 대 한 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d6c0a-116">To learn more details about LINQ, start by becoming familiar with some basic concepts in the Getting Started section [Getting Started with LINQ in Visual Basic](getting-started-with-linq.md), and then read the documentation for the LINQ technology in which you are interested:</span></span>  
  
- <span data-ttu-id="d6c0a-117">SQL Server 데이터베이스: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-117">SQL Server databases: [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)</span></span>  
  
- <span data-ttu-id="d6c0a-118">XML 문서: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-118">XML documents: [LINQ to XML (Visual Basic)](../../../../standard/linq/linq-xml-overview.md)</span></span>  
  
- <span data-ttu-id="d6c0a-119">ADO.NET 데이터 세트: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-119">ADO.NET Datasets: [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)</span></span>  
  
- <span data-ttu-id="d6c0a-120">.NET 컬렉션, 파일, 문자열 등: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-120">.NET collections, files, strings and so on: [LINQ to Objects (Visual Basic)](linq-to-objects.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6c0a-121">추가 정보</span><span class="sxs-lookup"><span data-stu-id="d6c0a-121">See also</span></span>

- [<span data-ttu-id="d6c0a-122">LINQ(Language-Integrated Query)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6c0a-122">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
