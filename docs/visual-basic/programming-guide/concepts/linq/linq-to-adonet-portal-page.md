---
description: '자세한 정보: LINQ to ADO.NET (포털 페이지)'
title: LINQ to ADO.NET(포털 페이지)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 5fe670be0bb87fb9a18ee73b3c3ea341d787b13e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100426753"
---
# <a name="linq-to-adonet-portal-page"></a><span data-ttu-id="21a38-103">LINQ to ADO.NET(포털 페이지)</span><span class="sxs-lookup"><span data-stu-id="21a38-103">LINQ to ADO.NET (Portal Page)</span></span>

<span data-ttu-id="21a38-104">LINQ to ADO.NET을 사용하면 LINQ(Language-Integrated Query) 프로그래밍 모델을 통해 ADO.NET의 열거 가능한 개체를 쿼리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-104">LINQ to ADO.NET enables you to query over any enumerable object in ADO.NET by using the Language-Integrated Query (LINQ) programming model.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21a38-105">LINQ to ADO.NET 설명서는 .NET Framework SDK의 ADO.NET 섹션에 있습니다. [LINQ 및 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="21a38-105">The LINQ to ADO.NET documentation is located in the ADO.NET section of the .NET Framework SDK: [LINQ and ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).</span></span>
  
 <span data-ttu-id="21a38-106">ADO.NET LINQ(Language-Integrated Query) 기술에는 LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 및 LINQ to Entities의 세 가지 독립적인 기술이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-106">There are three separate ADO.NET Language-Integrated Query (LINQ) technologies: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], and LINQ to Entities.</span></span> <span data-ttu-id="21a38-107">LINQ to DataSet은 다양한 기능을 사용하여 <xref:System.Data.DataSet>에 대해 최적화된 쿼리를 제공하고, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]는 SQL Server 데이터베이스 스키마를 직접 쿼리하는 데 사용되며, LINQ to Entities는 엔터티 데이터 모델을 쿼리하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-107">LINQ to DataSet provides richer, optimized querying over the <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] enables you to directly query SQL Server database schemas, and LINQ to Entities allows you to query an Entity Data Model.</span></span>  
  
## <a name="linq-to-dataset"></a><span data-ttu-id="21a38-108">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="21a38-108">LINQ to DataSet</span></span>  

 <span data-ttu-id="21a38-109"><xref:System.Data.DataSet>는 ADO.NET에서 가장 널리 사용되는 구성 요소 중 하나이며, ADO.NET의 기반이 되는 연결되지 않은 프로그래밍 모델의 핵심 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-109">The <xref:System.Data.DataSet> is one of the most widely used components in ADO.NET, and is a key element of the disconnected programming model that ADO.NET is built on.</span></span> <span data-ttu-id="21a38-110">그러나 이러한 탁월함에도 불구하고 <xref:System.Data.DataSet>의 쿼리 기능에는 한계가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-110">Despite this prominence, however, the <xref:System.Data.DataSet> has limited query capabilities.</span></span>  
  
 <span data-ttu-id="21a38-111">LINQ to DataSet을 사용하면 다른 많은 데이터 원본에 사용되는 것과 같은 쿼리 기능을 사용하여 더 다양한 쿼리 기능을 <xref:System.Data.DataSet>에 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-111">LINQ to DataSet enables you to build richer query capabilities into <xref:System.Data.DataSet> by using the same query functionality that is available for many other data sources.</span></span>  
  
 <span data-ttu-id="21a38-112">자세한 내용은 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a38-112">For more information, see [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).</span></span>  
  
## <a name="linq-to-sql"></a><span data-ttu-id="21a38-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="21a38-113">LINQ to SQL</span></span>  

 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]<span data-ttu-id="21a38-114">은 관계형 데이터를 개체로 관리하는 데 필요한 런타임 인프라를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-114">provides a run-time infrastructure for managing relational data as objects.</span></span> <span data-ttu-id="21a38-115">[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 관계형 데이터베이스의 데이터 모델은 개발자의 프로그래밍 언어로 표현되는 개체 모델에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-115">In [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)], the data model of a relational database is mapped to an object model expressed in the programming language of the developer.</span></span> <span data-ttu-id="21a38-116">애플리케이션을 실행하면 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 개체 모델의 언어 통합 쿼리를 SQL로 변환하여 실행을 위해 데이터베이스로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-116">When you execute the application, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="21a38-117">데이터베이스가 결과를 반환하면 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 조작할 수 있는 개체로 다시 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-117">When the database returns the results, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] translates them back into objects that you can manipulate.</span></span>  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]<span data-ttu-id="21a38-118">에는 데이터베이스의 저장 프로시저 및 사용자 정의 함수와 개체 모델의 상속을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-118">includes support for stored procedures and user-defined functions in the database, and for inheritance in the object model.</span></span>  
  
 <span data-ttu-id="21a38-119">자세한 내용은 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a38-119">For more information, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).</span></span>  
  
## <a name="linq-to-entities"></a><span data-ttu-id="21a38-120">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="21a38-120">LINQ to Entities</span></span>  

 <span data-ttu-id="21a38-121">엔터티 데이터 모델을 통해 관계형 데이터는 .NET 환경에서 개체로 공개됩니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-121">Through the Entity Data Model, relational data is exposed as objects in the .NET environment.</span></span> <span data-ttu-id="21a38-122">이를 통해 개체 계층은 LINQ 지원을 위한 이상적인 대상이 되므로 개발자는 비즈니스 논리를 개발할 때 사용한 언어로 데이터베이스에 대한 쿼리를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-122">This makes the object layer an ideal target for LINQ support, allowing developers to formulate queries against the database from the language used to build the business logic.</span></span> <span data-ttu-id="21a38-123">이 기능은 LINQ to Entities로 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="21a38-123">This capability is known as LINQ to Entities.</span></span> <span data-ttu-id="21a38-124">자세한 내용은 [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="21a38-124">See [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md) for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a38-125">참조</span><span class="sxs-lookup"><span data-stu-id="21a38-125">See also</span></span>

- [<span data-ttu-id="21a38-126">LINQ 및 ADO.NET</span><span class="sxs-lookup"><span data-stu-id="21a38-126">LINQ and ADO.NET</span></span>](../../../../framework/data/adonet/linq-and-ado-net.md)
- [<span data-ttu-id="21a38-127">LINQ(Language-Integrated Query)(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a38-127">Language-Integrated Query (LINQ) (Visual Basic)</span></span>](index.md)
