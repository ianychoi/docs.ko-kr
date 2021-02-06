---
description: '자세히 알아보기: DbConnection, DbCommand 및 Dbcommand'
title: DbConnection, DbCommand 및 DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: b5cb748a8dd5fb06f2f5dc5ab0479a679b2cc07d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651277"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a><span data-ttu-id="9adf9-103">DbConnection, DbCommand 및 DbException</span><span class="sxs-lookup"><span data-stu-id="9adf9-103">DbConnection, DbCommand and DbException</span></span>

<span data-ttu-id="9adf9-104"><xref:System.Data.Common.DbProviderFactory>와 <xref:System.Data.Common.DbConnection>을 만든 다음 명령과 데이터 판독기를 사용하여 데이터 소스에서 데이터를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-104">Once you have created a <xref:System.Data.Common.DbProviderFactory> and a <xref:System.Data.Common.DbConnection>, you can then work with commands and data readers to retrieve data from the data source.</span></span>  
  
## <a name="retrieving-data-example"></a><span data-ttu-id="9adf9-105">데이터 검색 예제</span><span class="sxs-lookup"><span data-stu-id="9adf9-105">Retrieving Data Example</span></span>  

 <span data-ttu-id="9adf9-106">다음 예제에서는 `DbConnection` 개체를 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-106">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9adf9-107"><xref:System.Data.Common.DbCommand>를 SQL SELECT 문으로 설정하여 Categories 테이블에서 데이터를 선택하기 위해 <xref:System.Data.Common.DbCommand.CommandText%2A>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-107">A <xref:System.Data.Common.DbCommand> is created to select data from the Categories table by setting the <xref:System.Data.Common.DbCommand.CommandText%2A> to a SQL SELECT statement.</span></span> <span data-ttu-id="9adf9-108">이 코드에서는 Categories 테이블이 데이터 소스에 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-108">The code assumes that the Categories table exists at the data source.</span></span> <span data-ttu-id="9adf9-109">연결이 열리고 <xref:System.Data.Common.DbDataReader>를 통해 데이터가 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-109">The connection is opened and the data is retrieved using a <xref:System.Data.Common.DbDataReader>.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a><span data-ttu-id="9adf9-110">명령 실행 예제</span><span class="sxs-lookup"><span data-stu-id="9adf9-110">Executing a Command Example</span></span>  

 <span data-ttu-id="9adf9-111">다음 예제에서는 `DbConnection` 개체를 인수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-111">This example takes a `DbConnection` object as an argument.</span></span> <span data-ttu-id="9adf9-112">`DbConnection`이 유효하면 연결이 열리고 <xref:System.Data.Common.DbCommand>가 만들어져 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-112">If the `DbConnection` is valid, the connection is opened and a <xref:System.Data.Common.DbCommand> is created and executed.</span></span> <span data-ttu-id="9adf9-113"><xref:System.Data.Common.DbCommand.CommandText%2A>는 Northwind 데이터베이스의 Categories 테이블에 대해 삽입 작업을 수행하는 SQL INSERT 문으로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-113">The <xref:System.Data.Common.DbCommand.CommandText%2A> is set to a SQL INSERT statement that performs an insert to the Categories table in the Northwind database.</span></span> <span data-ttu-id="9adf9-114">이 코드에서는 Northwind 데이터베이스가 데이터 소스에 있고 INSERT 문에 사용된 SQL 구문이 지정된 공급자에 대해 유효하다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-114">The code assumes that the Northwind database exists at the data source, and that the SQL syntax used in the INSERT statement is valid for the specified provider.</span></span> <span data-ttu-id="9adf9-115">데이터 소스에서 발생하는 오류는 <xref:System.Data.Common.DbException> 코드 블록에서 처리되고 다른 모든 예외는 <xref:System.Exception> 블록에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-115">Errors occurring at the data source are handled by the <xref:System.Data.Common.DbException> code block, and all other exceptions are handled in the <xref:System.Exception> block.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a><span data-ttu-id="9adf9-116">DbException을 사용하여 데이터 오류 처리</span><span class="sxs-lookup"><span data-stu-id="9adf9-116">Handling Data Errors with DbException</span></span>  

 <span data-ttu-id="9adf9-117"><xref:System.Data.Common.DbException> 클래스는 데이터 소스와 관련하여 throw되는 모든 예외에 대한 기본 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-117">The <xref:System.Data.Common.DbException> class is the base class for all exceptions thrown on behalf of a data source.</span></span> <span data-ttu-id="9adf9-118">예외 처리 코드에서 이 클래스를 사용하면 특정 예외 클래스를 참조하지 않고도 다양한 공급자에 의해 throw되는 예외를 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-118">You can use it in your exception handling code to handle exceptions thrown by different providers without having to reference a specific exception class.</span></span> <span data-ttu-id="9adf9-119">다음 코드 조각에서는 <xref:System.Data.Common.DbException>에 <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> 및 <xref:System.Exception.Message%2A> 속성을 사용하여 데이터 소스에서 반환한 오류 정보를 표시하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-119">The following code fragment demonstrates how to use <xref:System.Data.Common.DbException> to display error information returned by the data source using <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, and <xref:System.Exception.Message%2A> properties.</span></span> <span data-ttu-id="9adf9-120">오류 형식, 공급자 이름을 나타내는 소스, 오류 코드, 오류와 관련된 메시지 등이 출력에 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9adf9-120">The output will display the type of error, the source indicating the provider name, an error code, and the message associated with the error.</span></span>  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9adf9-121">추가 정보</span><span class="sxs-lookup"><span data-stu-id="9adf9-121">See also</span></span>

- [<span data-ttu-id="9adf9-122">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="9adf9-122">DbProviderFactories</span></span>](dbproviderfactories.md)
- [<span data-ttu-id="9adf9-123">DbProviderFactory 가져오기</span><span class="sxs-lookup"><span data-stu-id="9adf9-123">Obtaining a DbProviderFactory</span></span>](obtaining-a-dbproviderfactory.md)
- [<span data-ttu-id="9adf9-124">DbDataAdapter로 데이터 수정</span><span class="sxs-lookup"><span data-stu-id="9adf9-124">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="9adf9-125">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="9adf9-125">ADO.NET Overview</span></span>](ado-net-overview.md)
