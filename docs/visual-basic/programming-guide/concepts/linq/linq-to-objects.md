---
description: '자세한 정보: LINQ to Objects (Visual Basic)'
title: LINQ to Objects
ms.date: 07/20/2015
ms.assetid: dd4c30bc-1c9b-4781-a482-b5eada38deb2
ms.openlocfilehash: 50f04c77579595cc78ed43d04e0547eb15f91dc3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464770"
---
# <a name="linq-to-objects-visual-basic"></a><span data-ttu-id="6f355-103">LINQ to Objects(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-103">LINQ to Objects (Visual Basic)</span></span>

<span data-ttu-id="6f355-104">“LINQ to Objects”라는 용어는 중간 LINQ 공급자 또는 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md), [LINQ to XML](../../../../standard/linq/linq-xml-overview.md) 등의 API를 사용하지 않고 모든 <xref:System.Collections.IEnumerable> 또는 <xref:System.Collections.Generic.IEnumerable%601> 컬렉션에 대해 LINQ 쿼리를 직접 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-104">The term "LINQ to Objects" refers to the use of LINQ queries with any <xref:System.Collections.IEnumerable> or <xref:System.Collections.Generic.IEnumerable%601> collection directly, without the use of an intermediate LINQ provider or API such as [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md) or [LINQ to XML](../../../../standard/linq/linq-xml-overview.md).</span></span> <span data-ttu-id="6f355-105">LINQ를 사용하면 <xref:System.Collections.Generic.List%601>, <xref:System.Array>, <xref:System.Collections.Generic.Dictionary%602> 등의 모든 열거 가능 컬렉션을 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-105">You can use LINQ to query any enumerable collections such as <xref:System.Collections.Generic.List%601>, <xref:System.Array>, or <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="6f355-106">컬렉션은 사용자가 정의할 수도 있고 .NET Framework API에서 반환할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-106">The collection may be user-defined or may be returned by a .NET Framework API.</span></span>  
  
 <span data-ttu-id="6f355-107">기본적으로 LINQ to Objects는 새로운 컬렉션 방식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-107">In a basic sense, LINQ to Objects represents a new approach to collections.</span></span> <span data-ttu-id="6f355-108">이전에는 컬렉션에서 데이터를 검색하는 방법을 지정하는 복잡한 `For Each` 루프를 작성해야 했습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-108">In the old way, you had to write complex `For Each` loops that specified how to retrieve data from a collection.</span></span> <span data-ttu-id="6f355-109">그러나 LINQ 방식에서는 검색할 항목을 설명하는 선언적 코드를 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-109">In the LINQ approach, you write declarative code that describes what you want to retrieve.</span></span>  
  
 <span data-ttu-id="6f355-110">또한 LINQ 쿼리는 기존의 `For Each` 루프에 비해 세 가지 주요 이점을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-110">In addition, LINQ queries offer three main advantages over traditional `For Each` loops:</span></span>  
  
1. <span data-ttu-id="6f355-111">보다 간결하며 쉽게 읽을 수 있습니다(특히 여러 조건을 필터링하는 경우).</span><span class="sxs-lookup"><span data-stu-id="6f355-111">They are more concise and readable, especially when filtering multiple conditions.</span></span>  
  
2. <span data-ttu-id="6f355-112">최소한의 애플리케이션 코드로도 강력한 필터링, 순서 지정 및 그룹화 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-112">They provide powerful filtering, ordering, and grouping capabilities with a minimum of application code.</span></span>  
  
3. <span data-ttu-id="6f355-113">거의 또는 전혀 수정하지 않고도 다른 데이터 소스에 이식할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-113">They can be ported to other data sources with little or no modification.</span></span>  
  
 <span data-ttu-id="6f355-114">일반적으로는 데이터에 대해 수행하려는 작업이 복잡할수록 기존의 반복 기술 대신 LINQ를 사용하면 더 큰 이점을 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-114">In general, the more complex the operation you want to perform on the data, the more benefit you will realize by using LINQ instead of traditional iteration techniques.</span></span>  
  
 <span data-ttu-id="6f355-115">이 섹션에서는 몇 가지 예제를 통해 LINQ 방식에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-115">The purpose of this section is to demonstrate the LINQ approach with some select examples.</span></span> <span data-ttu-id="6f355-116">여기서 설명하는 방식 외에도 다양한 방식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-116">It is not intended to be exhaustive.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6f355-117">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="6f355-117">In This Section</span></span>  

 [<span data-ttu-id="6f355-118">LINQ 및 문자열(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-118">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)  
 <span data-ttu-id="6f355-119">LINQ를 사용하여 문자열 및 문자열 컬렉션을 쿼리하고 변환하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-119">Explains how LINQ can be used to query and transform strings and collections of strings.</span></span> <span data-ttu-id="6f355-120">또한 이러한 원칙을 설명하는 항목의 링크도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-120">Also includes links to topics that demonstrate these principles.</span></span>  
  
 [<span data-ttu-id="6f355-121">LINQ 및 리플렉션 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-121">LINQ and Reflection (Visual Basic)</span></span>](linq-and-reflection.md)  
 <span data-ttu-id="6f355-122">LINQ에서 리플렉션을 사용하는 방식을 보여 주는 샘플 링크를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-122">Links to a sample that demonstrates how LINQ uses reflection.</span></span>  
  
 [<span data-ttu-id="6f355-123">LINQ 및 파일 디렉터리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-123">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)  
 <span data-ttu-id="6f355-124">LINQ를 사용하여 파일 시스템을 조작하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-124">Explains how LINQ can be used to interact with file systems.</span></span> <span data-ttu-id="6f355-125">또한 이러한 개념을 설명하는 항목의 링크도 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-125">Also includes links to topics that demonstrate these concepts.</span></span>  
  
 [<span data-ttu-id="6f355-126">방법: LINQ를 사용 하 여 ArrayList 쿼리 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-126">How to: Query an ArrayList with LINQ (Visual Basic)</span></span>](how-to-query-an-arraylist-with-linq.md)  
 <span data-ttu-id="6f355-127">C#에서 ArrayList를 쿼리하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-127">Demonstrates how to query an ArrayList in C#.</span></span>  
  
 [<span data-ttu-id="6f355-128">방법: LINQ 쿼리에 대 한 사용자 지정 메서드 추가 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-128">How to: Add Custom Methods for LINQ Queries (Visual Basic)</span></span>](how-to-add-custom-methods-for-linq-queries.md)  
 <span data-ttu-id="6f355-129"><xref:System.Collections.Generic.IEnumerable%601> 인터페이스에 확장 메서드를 추가하여 LINQ 쿼리에 대해 사용할 수 있는 메서드 집합 확장 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-129">Explains how to extend the set of methods that you can use for LINQ queries by adding extension methods to the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span>  
  
 [<span data-ttu-id="6f355-130">LINQ(Language-Integrated Query)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f355-130">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)  
 <span data-ttu-id="6f355-131">LINQ 관련 설명과 쿼리를 수행하는 코드 예제를 제공하는 항목의 링크가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f355-131">Provides links to topics that explain LINQ and provide examples of code that perform queries.</span></span>
