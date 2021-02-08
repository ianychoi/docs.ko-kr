---
description: '자세한 정보: SQL CLR 형식 매핑'
title: SQL-CLR 형식 매핑
ms.date: 07/23/2018
ms.assetid: 4ed76327-54a7-414b-82a9-7579bfcec04b
ms.openlocfilehash: 59d3594287ceb20f5c3887c58a0f5527df35218a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803739"
---
# <a name="sql-clr-type-mapping"></a><span data-ttu-id="f6fe8-103">SQL-CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-103">SQL-CLR Type Mapping</span></span>

<span data-ttu-id="f6fe8-104">LINQ to SQL에서 관계형 데이터베이스의 데이터 모델은 사용자가 선택한 프로그래밍 언어로 표현되는 개체 모델에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-104">In LINQ to SQL, the data model of a relational database maps to an object model that is expressed in the programming language of your choice.</span></span> <span data-ttu-id="f6fe8-105">애플리케이션을 실행하면 LINQ to SQL에서는 개체 모델의 통합 언어 쿼리를 SQL로 변환하여 실행을 위해 데이터베이스로 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-105">When the application runs, LINQ to SQL translates the language-integrated queries in the object model into SQL and sends them to the database for execution.</span></span> <span data-ttu-id="f6fe8-106">데이터베이스에서 결과가 반환되면 LINQ to SQL에서는 해당 결과를 사용자의 프로그래밍 언어로 작업할 수 있는 개체로 다시 변환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-106">When the database returns the results, LINQ to SQL translates the results back to objects that you can work with in your own programming language.</span></span>  
  
 <span data-ttu-id="f6fe8-107">개체 모델과 데이터베이스 간에 데이터를 변환 하려면 *형식 매핑을* 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-107">In order to translate data between the object model and the database, a *type mapping* must be defined.</span></span> <span data-ttu-id="f6fe8-108">LINQ to SQL에서는 형식 매핑을 사용하여 각 CLR(공용 언어 런타임) 형식을 특정 SQL Server 형식과 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-108">LINQ to SQL uses a type mapping to match each common language runtime (CLR) type with a particular SQL Server type.</span></span> <span data-ttu-id="f6fe8-109">특성 기반 매핑을 사용하여 개체 모델 내부에 형식 매핑 및 데이터베이스 구조와 테이블 관계 같은 다른 매핑 정보를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-109">You can define type mappings and other mapping information, such as database structure and table relationships, inside the object model with attribute-based mapping.</span></span> <span data-ttu-id="f6fe8-110">또는 외부 매핑 파일을 사용하여 개체 모델 외부에 매핑 정보를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-110">Alternatively, you can specify the mapping information outside the object model with an external mapping file.</span></span> <span data-ttu-id="f6fe8-111">자세한 내용은 [특성 기반 매핑](attribute-based-mapping.md) 및 [외부 매핑](external-mapping.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-111">For more information, see [Attribute-Based Mapping](attribute-based-mapping.md) and [External Mapping](external-mapping.md).</span></span>  
  
 <span data-ttu-id="f6fe8-112">이 항목에서는 다음 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-112">This topic discusses the following points:</span></span>  
  
- [<span data-ttu-id="f6fe8-113">기본 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-113">Default Type Mapping</span></span>](#DefaultTypeMapping)  
  
- [<span data-ttu-id="f6fe8-114">형식 매핑 런타임 동작 매트릭스</span><span class="sxs-lookup"><span data-stu-id="f6fe8-114">Type Mapping Run-time Behavior Matrix</span></span>](#BehaviorMatrix)  
  
- [<span data-ttu-id="f6fe8-115">CLR 및 SQL 실행 간의 동작 차이</span><span class="sxs-lookup"><span data-stu-id="f6fe8-115">Behavior Differences Between CLR and SQL Execution</span></span>](#BehaviorDiffs)  
  
- [<span data-ttu-id="f6fe8-116">Enum 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-116">Enum Mapping</span></span>](#EnumMapping)  
  
- [<span data-ttu-id="f6fe8-117">숫자 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-117">Numeric Mapping</span></span>](#NumericMapping)  
  
- [<span data-ttu-id="f6fe8-118">텍스트 및 XML 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-118">Text and XML Mapping</span></span>](#TextMapping)  
  
- [<span data-ttu-id="f6fe8-119">날짜 및 시간 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-119">Date and Time Mapping</span></span>](#DateMapping)  
  
- [<span data-ttu-id="f6fe8-120">이진 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-120">Binary Mapping</span></span>](#BinaryMapping)  
  
- [<span data-ttu-id="f6fe8-121">기타 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-121">Miscellaneous Mapping</span></span>](#MiscMapping)  
  
<a name="DefaultTypeMapping"></a>

## <a name="default-type-mapping"></a><span data-ttu-id="f6fe8-122">기본 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-122">Default Type Mapping</span></span>  

 <span data-ttu-id="f6fe8-123">개체 모델 또는 외부 매핑 파일은 O/R 디자이너(개체 관계형 디자이너) 또는 SQLMetal 명령줄 도구를 사용하여 자동으로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-123">You can create the object model or external mapping file automatically with the Object Relational Designer (O/R Designer) or the SQLMetal command-line tool.</span></span> <span data-ttu-id="f6fe8-124">이러한 도구의 기본 형식 매핑은 SQL Server 데이터베이스 내의 열에 매핑될 CLR 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-124">The default type mappings for these tools define which CLR types are chosen to map to columns inside the SQL Server database.</span></span> <span data-ttu-id="f6fe8-125">이러한 도구를 사용 하는 방법에 대 한 자세한 내용은 [개체 모델 만들기](creating-the-object-model.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-125">For more information about using these tools, see [Creating the Object Model](creating-the-object-model.md).</span></span>  
  
 <span data-ttu-id="f6fe8-126"><xref:System.Data.Linq.DataContext.CreateDatabase%2A> 메서드를 사용하여 개체 모델 또는 외부 매핑 파일의 매핑 정보를 기초로 SQL Server 데이터베이스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-126">You can also use the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method to create a SQL Server database based on the mapping information in the object model or external mapping file.</span></span> <span data-ttu-id="f6fe8-127"><xref:System.Data.Linq.DataContext.CreateDatabase%2A> 메서드의 기본 형식 매핑은 개체 모델의 CLR 형식에 매핑되도록 만들 SQL Server 열의 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-127">The default type mappings for the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method define which type of SQL Server columns are created to map to the CLR types in the object model.</span></span> <span data-ttu-id="f6fe8-128">자세한 내용은 [방법: 동적으로 데이터베이스 만들기](how-to-dynamically-create-a-database.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-128">For more information, see [How to: Dynamically Create a Database](how-to-dynamically-create-a-database.md).</span></span>  
  
<a name="BehaviorMatrix"></a>

## <a name="type-mapping-run-time-behavior-matrix"></a><span data-ttu-id="f6fe8-129">형식 매핑 런타임 동작 매트릭스</span><span class="sxs-lookup"><span data-stu-id="f6fe8-129">Type Mapping Run-time Behavior Matrix</span></span>  

 <span data-ttu-id="f6fe8-130">다음 다이어그램에서는 데이터를 데이터베이스에서 검색하거나 데이터베이스에 저장할 때 특정 형식 매핑에 대해 예상되는 런타임 동작을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-130">The following diagram shows the expected run-time behavior of specific type mappings when data is retrieved from or saved to the database.</span></span> <span data-ttu-id="f6fe8-131">serialization의 경우를 제외하고 LINQ to SQL에서는 이 매트릭스에 지정되어 있는 CLR 또는 SQL Server 데이터 형식 간 매핑만 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-131">With the exception of serialization, LINQ to SQL does not support mapping between any CLR or SQL Server data types that are not specified in this matrix.</span></span> <span data-ttu-id="f6fe8-132">Serialization 지원에 대 한 자세한 내용은 [이진 serialization](#BinarySerialization)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-132">For more information on serialization support, see [Binary Serialization](#BinarySerialization).</span></span>  

![SQL CLR 데이터 형식 매핑 테이블 SQL Server](./media/sql-clr-type-mapping.png)

> [!NOTE]
> <span data-ttu-id="f6fe8-134">일부 형식 매핑의 경우 데이터베이스 관련 변환 과정에서 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-134">Some type mappings may result in overflow or data loss exceptions while translating to or from the database.</span></span>  
  
### <a name="custom-type-mapping"></a><span data-ttu-id="f6fe8-135">사용자 지정 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-135">Custom Type Mapping</span></span>  

 <span data-ttu-id="f6fe8-136">LINQ to SQL을 사용할 경우 O/R 디자이너, SQLMetal 및 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 메서드에 사용되는 기본 형식 매핑에 제한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-136">With LINQ to SQL, you are not limited to the default type mappings used by the O/R Designer, SQLMetal, and the <xref:System.Data.Linq.DataContext.CreateDatabase%2A> method.</span></span> <span data-ttu-id="f6fe8-137">DBML 파일에 명시적으로 지정하는 방법으로 사용자 지정 형식 매핑을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-137">You can create custom type mappings by explicitly specifying them in a DBML file.</span></span> <span data-ttu-id="f6fe8-138">그런 다음 이 DBML 파일을 사용하여 개체 모델 코드 및 매핑 파일을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-138">Then you can use that DBML file to create the object model code and mapping file.</span></span> <span data-ttu-id="f6fe8-139">자세한 내용은 [SQL-CLR 사용자 지정 형식 매핑](sql-clr-custom-type-mappings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-139">For more information, see [SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).</span></span>  
  
<a name="BehaviorDiffs"></a>

## <a name="behavior-differences-between-clr-and-sql-execution"></a><span data-ttu-id="f6fe8-140">CLR 및 SQL 실행 간의 동작 차이</span><span class="sxs-lookup"><span data-stu-id="f6fe8-140">Behavior Differences Between CLR and SQL Execution</span></span>  

 <span data-ttu-id="f6fe8-141">CLR과 SQL Server는 전체 자릿수 및 실행 측면에서 차이점이 있기 때문에 어디서 계산을 수행하는지에 따라 결과나 동작이 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-141">Because of differences in precision and execution between the CLR and SQL Server, you may receive different results or experience different behavior depending on where you perform your calculations.</span></span> <span data-ttu-id="f6fe8-142">LINQ to SQL 쿼리에서 계산을 수행하면 실제로 계산은 Transact-SQL로 변환된 후 SQL Server 데이터베이스에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-142">Calculations performed in LINQ to SQL queries are actually translated to Transact-SQL and then executed on the SQL Server database.</span></span> <span data-ttu-id="f6fe8-143">LINQ to SQL 쿼리 외부에서 수행되는 계산은 CLR 컨텍스트 내에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-143">Calculations performed outside LINQ to SQL queries are executed within the context of the CLR.</span></span>  
  
 <span data-ttu-id="f6fe8-144">예를 들어 다음은 CLR과 SQL Server 사이의 몇 가지 동작 차이점입니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-144">For example, the following are some differences in behavior between the CLR and SQL Server:</span></span>  
  
- <span data-ttu-id="f6fe8-145">SQL Server에서는 일부 데이터 형식이 CLR에서 이에 해당되는 데이터 형식과 다르게 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-145">SQL Server orders some data types differently than data of equivalent type in the CLR.</span></span> <span data-ttu-id="f6fe8-146">예를 들어 SQL Server의 `UNIQUEIDENTIFIER` 데이터 형식은 CLR의 <xref:System.Guid?displayProperty=nameWithType> 데이터 형식과 다르게 정렬됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-146">For example, SQL Server data of type `UNIQUEIDENTIFIER` is ordered differently than CLR data of type <xref:System.Guid?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="f6fe8-147">SQL Server에서는 일부 문자열의 비교 연산이 CLR과 다르게 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-147">SQL Server handles some string comparison operations differently than the CLR.</span></span> <span data-ttu-id="f6fe8-148">SQL Server의 경우 문자열 비교 동작은 서버의 데이터 정렬 설정에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-148">In SQL Server, string comparison behavior depends on the collation settings on the server.</span></span> <span data-ttu-id="f6fe8-149">자세한 내용은 Microsoft SQL Server 온라인 설명서에서 [데이터 정렬 작업](/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) 을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-149">For more information, see [Working with Collations](/previous-versions/sql/sql-server-2008-r2/ms187582(v=sql.105)) in the Microsoft SQL Server Books Online.</span></span>  
  
- <span data-ttu-id="f6fe8-150">SQL Server에서는 매핑된 일부 함수에 대해 CLR과는 다른 값을 반환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-150">SQL Server may return different values for some mapped functions than the CLR.</span></span> <span data-ttu-id="f6fe8-151">예를 들어 두 문자열이 후행 공백에서만 차이가 있는 경우 SQL Server에서는 두 문자열이 동일한 것으로 간주되는 반면 CLR에서는 두 문자열이 다른 것으로 간주되기 때문에 같음 함수가 각각 다른 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-151">For example, equality functions will differ because SQL Server considers two strings to be equal if they only differ in trailing white space; whereas the CLR considers them to be not equal.</span></span>  
  
<a name="EnumMapping"></a>

## <a name="enum-mapping"></a><span data-ttu-id="f6fe8-152">Enum 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-152">Enum Mapping</span></span>  

 <span data-ttu-id="f6fe8-153">LINQ to SQL에서는 다음과 같은 두 가지 방법으로 CLR <xref:System.Enum?displayProperty=nameWithType> 형식을 SQL Server 형식에 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-153">LINQ to SQL supports mapping the CLR <xref:System.Enum?displayProperty=nameWithType> type to SQL Server types in two ways:</span></span>  
  
- <span data-ttu-id="f6fe8-154">SQL 숫자 형식에 대한 매핑(`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)</span><span class="sxs-lookup"><span data-stu-id="f6fe8-154">Mapping to SQL numeric types (`TINYINT`, `SMALLINT`, `INT`, `BIGINT`)</span></span>  
  
     <span data-ttu-id="f6fe8-155">CLR <xref:System.Enum?displayProperty=nameWithType> 형식을 SQL 숫자 형식에 매핑할 경우 CLR <xref:System.Enum?displayProperty=nameWithType>의 기본 정수 값이 SQL Server 데이터베이스 열의 값에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-155">When you map a CLR <xref:System.Enum?displayProperty=nameWithType> type to a SQL numeric type, you map the underlying integer value of the CLR <xref:System.Enum?displayProperty=nameWithType> to the value of the SQL Server database column.</span></span> <span data-ttu-id="f6fe8-156">예를 들어 <xref:System.Enum?displayProperty=nameWithType>라는 `DaysOfWeek`에 기본 정수 값이 3인 `Tue`라는 멤버가 포함된 경우 해당 멤버는 데이터베이스 값 3에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-156">For example, if a <xref:System.Enum?displayProperty=nameWithType> named `DaysOfWeek` contains a member named `Tue` with an underlying integer value of 3, that member maps to a database value of 3.</span></span>  
  
- <span data-ttu-id="f6fe8-157">SQL 텍스트 형식에 대한 매핑(`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)</span><span class="sxs-lookup"><span data-stu-id="f6fe8-157">Mapping to SQL text types (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`)</span></span>  
  
     <span data-ttu-id="f6fe8-158">CLR <xref:System.Enum?displayProperty=nameWithType> 형식을 SQL 텍스트 형식에 매핑할 경우 SQL 데이터베이스 값이 CLR <xref:System.Enum?displayProperty=nameWithType> 멤버의 이름에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-158">When you map a CLR <xref:System.Enum?displayProperty=nameWithType> type to a SQL text type, the SQL database value is mapped to the names of the CLR <xref:System.Enum?displayProperty=nameWithType> members.</span></span> <span data-ttu-id="f6fe8-159">예를 들어 <xref:System.Enum?displayProperty=nameWithType>라는 `DaysOfWeek`에 기본 정수 값이 3인 `Tue`라는 멤버가 포함된 경우 해당 멤버는 데이터베이스 값 `Tue`에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-159">For example, if a <xref:System.Enum?displayProperty=nameWithType> named `DaysOfWeek` contains a member named `Tue` with an underlying integer value of 3, that member maps to a database value of `Tue`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6fe8-160">SQL 텍스트 형식을 CLR <xref:System.Enum?displayProperty=nameWithType>에 매핑할 경우에는 매핑되는 SQL 열에 <xref:System.Enum> 멤버의 이름만 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-160">When mapping SQL text types to a CLR <xref:System.Enum?displayProperty=nameWithType>, include only the names of the <xref:System.Enum> members in the mapped SQL column.</span></span> <span data-ttu-id="f6fe8-161">다른 값은 <xref:System.Enum>에 매핑되는 SQL 열에 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-161">Other values are not supported in the <xref:System.Enum>-mapped SQL column.</span></span>  
  
 <span data-ttu-id="f6fe8-162">O/R 디자이너 및 SQLMetal 명령줄 도구는 SQL 형식을 CLR <xref:System.Enum> 클래스에 자동으로 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-162">The O/R Designer and SQLMetal command-line tool cannot automatically map a SQL type to a CLR <xref:System.Enum> class.</span></span> <span data-ttu-id="f6fe8-163">O/R 디자이너 및 SQLMetal에 사용하려면 DBML 파일을 사용자 지정하여 이 매핑을 명시적으로 구성해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-163">You must explicitly configure this mapping by customizing a DBML file for use by the O/R Designer and SQLMetal.</span></span> <span data-ttu-id="f6fe8-164">사용자 지정 형식 매핑에 대 한 자세한 내용은 [SQL-CLR 사용자 지정 형식 매핑](sql-clr-custom-type-mappings.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-164">For more information about custom type mapping, see [SQL-CLR Custom Type Mappings](sql-clr-custom-type-mappings.md).</span></span>  
  
 <span data-ttu-id="f6fe8-165">열거를 위한 SQL 열은 다른 숫자 및 텍스트 열과 형식이 동일 하기 때문에 이러한 도구는 다음 [숫자 매핑](#NumericMapping) 및 [텍스트 및 XML 매핑](#TextMapping) 섹션에 설명 된 대로 사용자의 의도를 인식 하지 못하고 기본적으로 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-165">Because a SQL column intended for enumeration will be of the same type as other numeric and text columns; these tools will not recognize your intent and default to mapping as described in the following [Numeric Mapping](#NumericMapping) and [Text and XML Mapping](#TextMapping) sections.</span></span> <span data-ttu-id="f6fe8-166">DBML 파일을 사용 하 여 코드를 생성 하는 방법에 대 한 자세한 내용은 [LINQ to SQL에서 코드 생성](code-generation-in-linq-to-sql.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-166">For more information about generating code with the DBML file, see [Code Generation in LINQ to SQL](code-generation-in-linq-to-sql.md).</span></span>  
  
 <span data-ttu-id="f6fe8-167"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드는 CLR <xref:System.Enum?displayProperty=nameWithType> 형식에 매핑되는 숫자 형식의 SQL 열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-167">The <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method creates a SQL column of numeric type to map a CLR <xref:System.Enum?displayProperty=nameWithType> type.</span></span>  
  
<a name="NumericMapping"></a>

## <a name="numeric-mapping"></a><span data-ttu-id="f6fe8-168">숫자 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-168">Numeric Mapping</span></span>  

 <span data-ttu-id="f6fe8-169">LINQ to SQL에서는 여러 CLR 및 SQL Server 숫자 형식을 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-169">LINQ to SQL lets you map many CLR and SQL Server numeric types.</span></span> <span data-ttu-id="f6fe8-170">다음 표에는 데이터베이스를 기초로 개체 모델 또는 외부 매핑 파일을 빌드할 때 O/R 디자이너와 SQLMetal에서 선택하는 CLR 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-170">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="f6fe8-171">SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-171">SQL Server Type</span></span>|<span data-ttu-id="f6fe8-172">O/R 디자이너 및 SQLMetal에서 사용하는 기본 CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-172">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`BIT`|<xref:System.Boolean?displayProperty=nameWithType>|  
|`TINYINT`|<xref:System.Int16?displayProperty=nameWithType>|  
|`INT`|<xref:System.Int32?displayProperty=nameWithType>|  
|`BIGINT`|<xref:System.Int64?displayProperty=nameWithType>|  
|`SMALLMONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`MONEY`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`DECIMAL`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`NUMERIC`|<xref:System.Decimal?displayProperty=nameWithType>|  
|`REAL/FLOAT(24)`|<xref:System.Single?displayProperty=nameWithType>|  
|`FLOAT/FLOAT(53)`|<xref:System.Double?displayProperty=nameWithType>|  
  
 <span data-ttu-id="f6fe8-173">다음 표에는 개체 모델 또는 외부 매핑 파일에 정의된 CLR 형식에 매핑되도록 만들 SQL 열의 형식을 정의하기 위해 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 사용하는 기본 형식 매핑이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-173">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="f6fe8-174">CLR 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-174">CLR Type</span></span>|<span data-ttu-id="f6fe8-175"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>에서 사용하는 기본 SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-175">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|`BIT`|  
|<xref:System.Byte?displayProperty=nameWithType>|`TINYINT`|  
|<xref:System.Int16?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.Int32?displayProperty=nameWithType>|`INT`|  
|<xref:System.Int64?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.SByte?displayProperty=nameWithType>|`SMALLINT`|  
|<xref:System.UInt16?displayProperty=nameWithType>|`INT`|  
|<xref:System.UInt32?displayProperty=nameWithType>|`BIGINT`|  
|<xref:System.UInt64?displayProperty=nameWithType>|`DECIMAL(20)`|  
|<xref:System.Decimal?displayProperty=nameWithType>|`DECIMAL(29,4)`|  
|<xref:System.Single?displayProperty=nameWithType>|`REAL`|  
|<xref:System.Double?displayProperty=nameWithType>|`FLOAT`|  
  
 <span data-ttu-id="f6fe8-176">이 외에도 여러 가지 숫자 매핑을 선택할 수 있지만 일부의 경우에는 데이터베이스 관련 변환 과정에서 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-176">There are many other numeric mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="f6fe8-177">자세한 내용은 [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-177">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="decimal-and-money-types"></a><span data-ttu-id="f6fe8-178">Decimal 및 Money 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-178">Decimal and Money Types</span></span>  

 <span data-ttu-id="f6fe8-179">SQL Server `DECIMAL` 형식의 기본 전체 자릿수(소수점을 기준으로 왼쪽과 오른쪽에 18자리)는 이 형식과 기본적으로 쌍을 이루는 CLR <xref:System.Decimal?displayProperty=nameWithType> 형식의 전체 자릿수보다 훨씬 적습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-179">The default precision of SQL Server `DECIMAL` type (18 decimal digits to the left and right of the decimal point) is much smaller than the precision of the CLR <xref:System.Decimal?displayProperty=nameWithType> type that it is paired with by default.</span></span> <span data-ttu-id="f6fe8-180">이 때문에 데이터베이스에 데이터를 저장할 때 전체 자릿수가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-180">This can result in precision loss when you save data to the database.</span></span> <span data-ttu-id="f6fe8-181">그러나 SQL Server의 `DECIMAL` 형식이 30자리 이상으로 구성된 경우에는 그 반대의 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-181">However, just the opposite can happen if the SQL Server `DECIMAL` type is configured with greater than 29 digits of precision.</span></span> <span data-ttu-id="f6fe8-182">SQL Server `DECIMAL` 형식의 전체 자릿수가 CLR <xref:System.Decimal?displayProperty=nameWithType>의 전체 자릿수보다 크게 구성된 경우 데이터베이스에서 데이터를 검색할 때 전체 자릿수가 손실될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-182">When a SQL Server `DECIMAL` type has been configured with a greater precision than the CLR <xref:System.Decimal?displayProperty=nameWithType>, precision loss can occur when retrieving data from the database.</span></span>  
  
 <span data-ttu-id="f6fe8-183">CLR `MONEY` 형식과 기본적으로 쌍을 이루는 SQL Server `SMALLMONEY` 및 <xref:System.Decimal?displayProperty=nameWithType> 형식도 전체 자릿수가 훨씬 적기 때문에 데이터베이스에 데이터를 저장할 때 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-183">The SQL Server `MONEY` and `SMALLMONEY` types, which are also paired with the CLR <xref:System.Decimal?displayProperty=nameWithType> type by default, have a much smaller precision, which can result in overflow or data loss exceptions when saving data to the database.</span></span>  
  
<a name="TextMapping"></a>

## <a name="text-and-xml-mapping"></a><span data-ttu-id="f6fe8-184">텍스트 및 XML 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-184">Text and XML Mapping</span></span>  

 <span data-ttu-id="f6fe8-185">LINQ to SQL에서는 여러 텍스트 기반 형식 및 XML 형식을 매핑할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-185">There are also many text-based and XML types that you can map with LINQ to SQL.</span></span> <span data-ttu-id="f6fe8-186">다음 표에는 데이터베이스를 기초로 개체 모델 또는 외부 매핑 파일을 빌드할 때 O/R 디자이너와 SQLMetal에서 선택하는 CLR 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-186">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="f6fe8-187">SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-187">SQL Server Type</span></span>|<span data-ttu-id="f6fe8-188">O/R 디자이너 및 SQLMetal에서 사용하는 기본 CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-188">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`CHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`VARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`NVARCHAR`|<xref:System.String?displayProperty=nameWithType>|  
|`TEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`NTEXT`|<xref:System.String?displayProperty=nameWithType>|  
|`XML`|<xref:System.Xml.Linq.XElement?displayProperty=nameWithType>|  
  
 <span data-ttu-id="f6fe8-189">다음 표에는 개체 모델 또는 외부 매핑 파일에 정의된 CLR 형식에 매핑되도록 만들 SQL 열의 형식을 정의하기 위해 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 사용하는 기본 형식 매핑이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-189">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="f6fe8-190">CLR 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-190">CLR Type</span></span>|<span data-ttu-id="f6fe8-191"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>에서 사용하는 기본 SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-191">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Char?displayProperty=nameWithType>|`NCHAR(1)`|  
|<xref:System.String?displayProperty=nameWithType>|`NVARCHAR(4000)`|  
|<span data-ttu-id="f6fe8-192"><xref:System.Char?displayProperty=nameWithType>[]</span><span class="sxs-lookup"><span data-stu-id="f6fe8-192"><xref:System.Char?displayProperty=nameWithType>[]</span></span>|`NVARCHAR(4000)`|  
|<span data-ttu-id="f6fe8-193">`Parse()` 및 `ToString()`을 구현하는 사용자 지정 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-193">Custom type implementing `Parse()` and `ToString()`</span></span>|`NVARCHAR(MAX)`|  
  
 <span data-ttu-id="f6fe8-194">이 외에도 여러 가지 텍스트 기반 및 XML 매핑을 선택할 수 있지만 일부의 경우에는 데이터베이스 관련 변환 과정에서 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-194">There are many other text-based and XML mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="f6fe8-195">자세한 내용은 [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-195">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="xml-types"></a><span data-ttu-id="f6fe8-196">XML 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-196">XML Types</span></span>  

 <span data-ttu-id="f6fe8-197">SQL Server `XML` 데이터 형식은 Microsoft SQL Server 2005부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-197">The SQL Server `XML` data type is available starting in Microsoft SQL Server 2005.</span></span> <span data-ttu-id="f6fe8-198">SQL Server `XML` 데이터 형식은 <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument> 또는 <xref:System.String>에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-198">You can map the SQL Server `XML` data type to <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XDocument>, or <xref:System.String>.</span></span> <span data-ttu-id="f6fe8-199"><xref:System.Xml.Linq.XElement>로 읽어 들일 수 없는 XML 조각이 열에 저장된 경우 런타임 오류를 방지하기 위해 해당 열을 <xref:System.String>에 매핑해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-199">If the column stores XML fragments that cannot be read into <xref:System.Xml.Linq.XElement>, the column must be mapped to <xref:System.String> to avoid run-time errors.</span></span> <span data-ttu-id="f6fe8-200"><xref:System.String>에 매핑해야 하는 XML 조각은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-200">XML fragments that must be mapped to <xref:System.String> include the following:</span></span>  
  
- <span data-ttu-id="f6fe8-201">XML 요소의 시퀀스</span><span class="sxs-lookup"><span data-stu-id="f6fe8-201">A sequence of XML elements</span></span>  
  
- <span data-ttu-id="f6fe8-202">특성</span><span class="sxs-lookup"><span data-stu-id="f6fe8-202">Attributes</span></span>  
  
- <span data-ttu-id="f6fe8-203">PI(공용 식별자)</span><span class="sxs-lookup"><span data-stu-id="f6fe8-203">Public Identifiers (PI)</span></span>  
  
- <span data-ttu-id="f6fe8-204">설명</span><span class="sxs-lookup"><span data-stu-id="f6fe8-204">Comments</span></span>  
  
 <span data-ttu-id="f6fe8-205"><xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)와 같이 및를 SQL Server에 매핑할 수 있지만 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 이 메서드에는 이러한 형식에 대 한 기본 SQL Server 형식 매핑이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-205">Although you can map <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XDocument> to SQL Server as shown in the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix), the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method has no default SQL Server type mapping for these types.</span></span>  
  
### <a name="custom-types"></a><span data-ttu-id="f6fe8-206">사용자 지정 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-206">Custom Types</span></span>  

 <span data-ttu-id="f6fe8-207">클래스가 및를 구현 하는 경우 `Parse()` `ToString()` 개체를 모든 SQL 텍스트 형식 ( `CHAR` ,,,, `NCHAR` , `VARCHAR` `NVARCHAR` `TEXT` `NTEXT` , `XML` )에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-207">If a class implements `Parse()` and `ToString()`, you can map the object to any SQL text type (`CHAR`, `NCHAR`, `VARCHAR`, `NVARCHAR`, `TEXT`, `NTEXT`, `XML`).</span></span> <span data-ttu-id="f6fe8-208">개체는 `ToString()`에서 반환하는 값을 매핑된 데이터베이스 열에 전송함으로써 데이터베이스에 저장되고,</span><span class="sxs-lookup"><span data-stu-id="f6fe8-208">The object is stored in the database by sending the value returned by `ToString()` to the mapped database column.</span></span> <span data-ttu-id="f6fe8-209">데이터베이스에서 반환하는 문자열에 대해 `Parse()`를 호출함으로써 다시 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-209">The object is reconstructed by invoking `Parse()` on the string returned by the database.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6fe8-210">LINQ to SQL에서 <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>을 사용한 serialization은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-210">LINQ to SQL does not support serialization by using <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>.</span></span>  
  
<a name="DateMapping"></a>

## <a name="date-and-time-mapping"></a><span data-ttu-id="f6fe8-211">날짜 및 시간 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-211">Date and Time Mapping</span></span>  

 <span data-ttu-id="f6fe8-212">LINQ to SQL을 사용하면 여러 SQL Server 날짜 및 시간 형식을 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-212">With LINQ to SQL, you can map many SQL Server date and time types.</span></span> <span data-ttu-id="f6fe8-213">다음 표에는 데이터베이스를 기초로 개체 모델 또는 외부 매핑 파일을 빌드할 때 O/R 디자이너와 SQLMetal에서 선택하는 CLR 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-213">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="f6fe8-214">SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-214">SQL Server Type</span></span>|<span data-ttu-id="f6fe8-215">O/R 디자이너 및 SQLMetal에서 사용하는 기본 CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-215">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`SMALLDATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIME2`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`DATETIMEOFFSET`|<xref:System.DateTimeOffset?displayProperty=nameWithType>|  
|`DATE`|<xref:System.DateTime?displayProperty=nameWithType>|  
|`TIME`|<xref:System.TimeSpan?displayProperty=nameWithType>|  
  
 <span data-ttu-id="f6fe8-216">다음 표에는 개체 모델 또는 외부 매핑 파일에 정의된 CLR 형식에 매핑되도록 만들 SQL 열의 형식을 정의하기 위해 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 사용하는 기본 형식 매핑이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-216">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="f6fe8-217">CLR 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-217">CLR Type</span></span>|<span data-ttu-id="f6fe8-218"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>에서 사용하는 기본 SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-218">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|`DATETIME`|  
|<xref:System.DateTimeOffset?displayProperty=nameWithType>|`DATETIMEOFFSET`|  
|<xref:System.TimeSpan?displayProperty=nameWithType>|`TIME`|  
  
 <span data-ttu-id="f6fe8-219">이 외에도 여러 가지 날짜 및 시간 매핑을 선택할 수 있지만 일부의 경우에는 데이터베이스 관련 변환 과정에서 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-219">There are many other date and time mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="f6fe8-220">자세한 내용은 [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-220">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6fe8-221">SQL Server 형식 `DATETIME2`, `DATETIMEOFFSET`, `DATE` 및 `TIME`은 Microsoft SQL Server 2008부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-221">The SQL Server types `DATETIME2`, `DATETIMEOFFSET`, `DATE`, and `TIME` are available starting with Microsoft SQL Server 2008.</span></span> <span data-ttu-id="f6fe8-222">LINQ to SQL에서는 .NET Framework 버전 3.5 SP1부터 이러한 새로운 형식의 매핑이 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-222">LINQ to SQL supports mapping to these new types starting with the .NET Framework version 3.5 SP1.</span></span>  
  
### <a name="systemdatetime"></a><span data-ttu-id="f6fe8-223">System.Datetime</span><span class="sxs-lookup"><span data-stu-id="f6fe8-223">System.Datetime</span></span>  

 <span data-ttu-id="f6fe8-224">CLR <xref:System.DateTime?displayProperty=nameWithType> 형식의 범위 및 전체 자릿수는 `DATETIME` 메서드의 기본 형식 매핑인 SQL Server <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 형식의 범위 및 전체 자릿수보다 큽니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-224">The range and precision of the CLR <xref:System.DateTime?displayProperty=nameWithType> type is greater than the range and precision of the SQL Server `DATETIME` type, which is the default type mapping for the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="f6fe8-225">`DATETIME`의 범위를 벗어나는 날짜와 관련된 예외가 발생하지 않도록 하려면 Microsoft SQL Server 2008부터 사용할 수 있는 `DATETIME2`를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-225">To help avoid exceptions related to dates outside the range of `DATETIME`, use `DATETIME2`, which is available starting with Microsoft SQL Server 2008.</span></span> <span data-ttu-id="f6fe8-226">`DATETIME2` 는 CLR의 범위 및 전체 자릿수와 일치할 수 있습니다 <xref:System.DateTime?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f6fe8-226">`DATETIME2` can match the range and precision of the CLR <xref:System.DateTime?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="f6fe8-227">SQL Server 날짜에는 CLR에서 지원되는 기능인 <xref:System.TimeZone> 개념이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-227">SQL Server dates have no concept of <xref:System.TimeZone>, a feature that is richly supported in the CLR.</span></span> <span data-ttu-id="f6fe8-228">원래 <xref:System.TimeZone> 정보에 관계없이 <xref:System.TimeZone> 값은 <xref:System.DateTimeKind> 변환 없이 데이터베이스에 있는 그대로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-228"><xref:System.TimeZone> values are saved as is to the database without <xref:System.TimeZone> conversion, regardless of the original <xref:System.DateTimeKind> information.</span></span> <span data-ttu-id="f6fe8-229"><xref:System.DateTime> 값이 데이터베이스에서 검색될 경우 해당 값은 <xref:System.DateTime>가 <xref:System.DateTimeKind>로 지정되어 <xref:System.DateTimeKind.Unspecified>에 있는 그대로 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-229">When <xref:System.DateTime> values are retrieved from the database, their value is loaded as is into a <xref:System.DateTime> with a <xref:System.DateTimeKind> of <xref:System.DateTimeKind.Unspecified>.</span></span> <span data-ttu-id="f6fe8-230">지원 되는 메서드에 대 한 자세한 내용은 <xref:System.DateTime?displayProperty=nameWithType> [system.web 메서드](system-datetime-methods.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-230">For more information about supported <xref:System.DateTime?displayProperty=nameWithType> methods, see [System.DateTime Methods](system-datetime-methods.md).</span></span>  
  
### <a name="systemtimespan"></a><span data-ttu-id="f6fe8-231">System.TimeSpan</span><span class="sxs-lookup"><span data-stu-id="f6fe8-231">System.TimeSpan</span></span>  

 <span data-ttu-id="f6fe8-232">Microsoft SQL Server 2008 및 .NET Framework 3.5 SP1에서는 CLR <xref:System.TimeSpan?displayProperty=nameWithType> 형식을 SQL Server `TIME` 형식에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-232">Microsoft SQL Server 2008 and the .NET Framework 3.5 SP1 let you map the CLR <xref:System.TimeSpan?displayProperty=nameWithType> type to the SQL Server `TIME` type.</span></span> <span data-ttu-id="f6fe8-233">그러나 CLR <xref:System.TimeSpan?displayProperty=nameWithType>에서 지원되는 범위와 SQL Server `TIME` 형식에서 지원되는 범위에는 상당한 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-233">However, there is a large difference between the range that the CLR <xref:System.TimeSpan?displayProperty=nameWithType> supports and what the SQL Server `TIME` type supports.</span></span> <span data-ttu-id="f6fe8-234">0보다 작거나 23:59:59.9999999시간보다 큰 값을 SQL `TIME`에 매핑하면 오버플로 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-234">Mapping values less than 0 or greater than 23:59:59.9999999 hours to the SQL `TIME` will result in overflow exceptions.</span></span> <span data-ttu-id="f6fe8-235">자세한 내용은 [Timespan.zero 메서드](system-timespan-methods.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-235">For more information, see [System.TimeSpan Methods](system-timespan-methods.md).</span></span>  
  
 <span data-ttu-id="f6fe8-236">Microsoft SQL Server 2000 및 SQL Server 2005에서는 데이터베이스 필드를 <xref:System.TimeSpan>에 매핑할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-236">In Microsoft SQL Server 2000 and SQL Server 2005, you cannot map database fields to <xref:System.TimeSpan>.</span></span> <span data-ttu-id="f6fe8-237">그러나 <xref:System.TimeSpan> 값은 <xref:System.TimeSpan> 빼기에서 반환되거나 리터럴 또는 바인딩된 변수로 식에 삽입될 수 있기 때문에 <xref:System.DateTime>에 대한 연산은 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-237">However, operations on <xref:System.TimeSpan> are supported because <xref:System.TimeSpan> values can be returned from <xref:System.DateTime> subtraction or introduced into an expression as a literal or bound variable.</span></span>  
  
<a name="BinaryMapping"></a>

## <a name="binary-mapping"></a><span data-ttu-id="f6fe8-238">이진 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-238">Binary Mapping</span></span>  

 <span data-ttu-id="f6fe8-239">여러 SQL Server 형식을 CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> 형식에 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-239">There are many SQL Server types that can map to the CLR type <xref:System.Data.Linq.Binary?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f6fe8-240">다음 표에는 데이터베이스를 기초로 개체 모델 또는 외부 매핑 파일을 빌드할 때 O/R 디자이너와 SQLMetal에서 CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> 형식을 정의하는 SQL Server 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-240">The following table shows the SQL Server types that cause O/R Designer and SQLMetal to define a CLR <xref:System.Data.Linq.Binary?displayProperty=nameWithType> type when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="f6fe8-241">SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-241">SQL Server Type</span></span>|<span data-ttu-id="f6fe8-242">O/R 디자이너 및 SQLMetal에서 사용하는 기본 CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-242">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`BINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(50)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`VARBINARY(MAX)`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|<span data-ttu-id="f6fe8-243">`VARBINARY(MAX)`특성 사용 `FILESTREAM`</span><span class="sxs-lookup"><span data-stu-id="f6fe8-243">`VARBINARY(MAX)` with the `FILESTREAM` attribute</span></span>|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`IMAGE`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
|`TIMESTAMP`|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|  
  
 <span data-ttu-id="f6fe8-244">다음 표에는 개체 모델 또는 외부 매핑 파일에 정의된 CLR 형식에 매핑되도록 만들 SQL 열의 형식을 정의하기 위해 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 사용하는 기본 형식 매핑이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-244">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="f6fe8-245">CLR 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-245">CLR Type</span></span>|<span data-ttu-id="f6fe8-246"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>에서 사용하는 기본 SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-246">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Data.Linq.Binary?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Byte?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
|<xref:System.Runtime.Serialization.ISerializable?displayProperty=nameWithType>|`VARBINARY(MAX)`|  
  
 <span data-ttu-id="f6fe8-247">이 외에도 여러 가지 이진 매핑을 선택할 수 있지만 일부의 경우에는 데이터베이스 관련 변환 과정에서 오버플로 또는 데이터 손실 예외가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-247">There are many other binary mappings you can choose, but some may result in overflow or data loss exceptions while translating to or from the database.</span></span> <span data-ttu-id="f6fe8-248">자세한 내용은 [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-248">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
### <a name="sql-server-filestream"></a><span data-ttu-id="f6fe8-249">SQL Server FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="f6fe8-249">SQL Server FILESTREAM</span></span>  

 <span data-ttu-id="f6fe8-250">`FILESTREAM` 열의 `VARBINARY(MAX)` 특성은 Microsoft SQL Server 2008부터 사용할 수 있으며 .NET Framework 버전 3.5 SP1부터 LINQ to SQL을 사용하여 매핑할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-250">The `FILESTREAM` attribute for `VARBINARY(MAX)` columns is available starting with Microsoft SQL Server 2008; you can map to it with LINQ to SQL starting with the .NET Framework version 3.5 SP1.</span></span>  
  
 <span data-ttu-id="f6fe8-251">`VARBINARY(MAX)` 개체에 `FILESTREAM` 특성이 있는 <xref:System.Data.Linq.Binary> 열을 매핑할 수는 있지만 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 `FILESTREAM` 특성이 있는 열을 자동으로 생성할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-251">Although you can map `VARBINARY(MAX)` columns with the `FILESTREAM` attribute to <xref:System.Data.Linq.Binary> objects, the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method is unable to automatically create columns with the `FILESTREAM` attribute.</span></span> <span data-ttu-id="f6fe8-252">에 대 한 자세한 내용은 `FILESTREAM` [FILESTREAM 개요](/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105))를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-252">For more information about `FILESTREAM`, see [FILESTREAM Overview](/previous-versions/sql/sql-server-2008-r2/bb933993(v=sql.105)).</span></span>  
  
<a name="BinarySerialization"></a>

### <a name="binary-serialization"></a><span data-ttu-id="f6fe8-253">이진 Serialization</span><span class="sxs-lookup"><span data-stu-id="f6fe8-253">Binary Serialization</span></span>  

 <span data-ttu-id="f6fe8-254">클래스에서 <xref:System.Runtime.Serialization.ISerializable> 인터페이스를 구현하는 경우 개체를 모든 SQL 이진 필드(`BINARY`, `VARBINARY`, `IMAGE`)로 serialize할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-254">If a class implements the <xref:System.Runtime.Serialization.ISerializable> interface, you can serialize an object to any SQL binary field (`BINARY`, `VARBINARY`, `IMAGE`).</span></span> <span data-ttu-id="f6fe8-255">개체는 <xref:System.Runtime.Serialization.ISerializable> 인터페이스가 구현되는 방법에 따라 직렬화 및 역직렬화됩니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-255">The object is serialized and deserialized according to how the <xref:System.Runtime.Serialization.ISerializable> interface is implemented.</span></span> <span data-ttu-id="f6fe8-256">자세한 내용은 [이진 Serialization](../../../../../standard/serialization/binary-serialization.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-256">For more information, see [Binary Serialization](../../../../../standard/serialization/binary-serialization.md).</span></span>
  
<a name="MiscMapping"></a>

## <a name="miscellaneous-mapping"></a><span data-ttu-id="f6fe8-257">기타 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-257">Miscellaneous Mapping</span></span>  

 <span data-ttu-id="f6fe8-258">다음 표에서는 위에서 언급하지 않은 기타 형식의 기본 형식 매핑을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-258">The following table shows the default type mappings for some miscellaneous types that have not yet been mentioned.</span></span> <span data-ttu-id="f6fe8-259">다음 표에는 데이터베이스를 기초로 개체 모델 또는 외부 매핑 파일을 빌드할 때 O/R 디자이너와 SQLMetal에서 선택하는 CLR 형식이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-259">The following table shows the CLR types that O/R Designer and SQLMetal select when building an object model or external mapping file based on your database.</span></span>  
  
|<span data-ttu-id="f6fe8-260">SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-260">SQL Server Type</span></span>|<span data-ttu-id="f6fe8-261">O/R 디자이너 및 SQLMetal에서 사용하는 기본 CLR 형식 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-261">Default CLR Type mapping used by O/R Designer and SQLMetal</span></span>|  
|---------------------|-----------------------------------------------------------------|  
|`UNIQUEIDENTIFIER`|<xref:System.Guid?displayProperty=nameWithType>|  
|`SQL_VARIANT`|<xref:System.Object?displayProperty=nameWithType>|  
  
 <span data-ttu-id="f6fe8-262">다음 표에는 개체 모델 또는 외부 매핑 파일에 정의된 CLR 형식에 매핑되도록 만들 SQL 열의 형식을 정의하기 위해 <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> 메서드에서 사용하는 기본 형식 매핑이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-262">The next table shows the default type mappings used by the <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType> method to define which type of SQL columns are created to map to the CLR types defined in your object model or external mapping file.</span></span>  
  
|<span data-ttu-id="f6fe8-263">CLR 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-263">CLR Type</span></span>|<span data-ttu-id="f6fe8-264"><xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType>에서 사용하는 기본 SQL Server 형식</span><span class="sxs-lookup"><span data-stu-id="f6fe8-264">Default SQL Server Type used by <xref:System.Data.Linq.DataContext.CreateDatabase%2A?displayProperty=nameWithType></span></span>|  
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Guid?displayProperty=nameWithType>|`UNIQUEIDENTIFIER`|  
|<xref:System.Object?displayProperty=nameWithType>|`SQL_VARIANT`|  
  
 <span data-ttu-id="f6fe8-265">LINQ to SQL에서는 이러한 기타 형식에 대해 여기에 나와 있는 것 이외의 형식 매핑은 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-265">LINQ to SQL does not support any other type mappings for these miscellaneous types.</span></span>  <span data-ttu-id="f6fe8-266">자세한 내용은 [형식 매핑 런타임 동작 매트릭스](#BehaviorMatrix)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="f6fe8-266">For more information, see the [Type Mapping Run Time Behavior Matrix](#BehaviorMatrix).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6fe8-267">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f6fe8-267">See also</span></span>

- [<span data-ttu-id="f6fe8-268">특성 기반 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-268">Attribute-Based Mapping</span></span>](attribute-based-mapping.md)
- [<span data-ttu-id="f6fe8-269">외부 매핑</span><span class="sxs-lookup"><span data-stu-id="f6fe8-269">External Mapping</span></span>](external-mapping.md)
- [<span data-ttu-id="f6fe8-270">데이터 형식 및 함수</span><span class="sxs-lookup"><span data-stu-id="f6fe8-270">Data Types and Functions</span></span>](data-types-and-functions.md)
- [<span data-ttu-id="f6fe8-271">SQL-CLR 형식 불일치</span><span class="sxs-lookup"><span data-stu-id="f6fe8-271">SQL-CLR Type Mismatches</span></span>](sql-clr-type-mismatches.md)
