---
description: '자세히 알아보기: 방법: 중첩 된 컬렉션을 반환 하는 쿼리 실행'
title: '방법: 중첩 컬렉션을 반환하는 쿼리 실행'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f7f385f3-ffcf-4f3b-af35-de8818938e5f
ms.openlocfilehash: 941b7471820c09224e6828fac6e17b92f70ff57e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650627"
---
# <a name="how-to-execute-a-query-that-returns-nested-collections"></a><span data-ttu-id="9c1e8-103">방법: 중첩 컬렉션을 반환하는 쿼리 실행</span><span class="sxs-lookup"><span data-stu-id="9c1e8-103">How to: Execute a Query that Returns Nested Collections</span></span>

<span data-ttu-id="9c1e8-104">여기에서는 <xref:System.Data.EntityClient.EntityCommand> 개체를 사용하여 개념적 모델에 대해 명령을 실행하는 방법 및 <xref:System.Data.EntityClient.EntityDataReader>를 사용하여 중첩 컬렉션 결과를 검색하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-104">This shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the nested collection results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="9c1e8-105">이 예제의 코드를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="9c1e8-105">To run the code in this example</span></span>  
  
1. <span data-ttu-id="9c1e8-106">프로젝트에 [AdventureWorks Sales 모델](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) 을 추가 하 고 Entity Framework를 사용 하도록 프로젝트를 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-106">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="9c1e8-107">자세한 내용은 [방법: 엔터티 데이터 모델 마법사 사용](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-107">For more information, see [How to: Use the Entity Data Model Wizard](/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="9c1e8-108">애플리케이션의 코드 페이지에서 다음 `using` 문(Visual Basic에서는 `Imports`)을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-108">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="9c1e8-109">예제</span><span class="sxs-lookup"><span data-stu-id="9c1e8-109">Example</span></span>  

 <span data-ttu-id="9c1e8-110">*중첩 컬렉션* 은 다른 컬렉션 내에 있는 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-110">A *nested collection* is a collection that is inside another collection.</span></span> <span data-ttu-id="9c1e8-111">다음 코드에서는 `Contacts` 컬렉션과 각 `SalesOrderHeaders`에 연결된 `Contact`의 중첩 컬렉션을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="9c1e8-111">The following code retrieves a collection of `Contacts` and the nested collections of `SalesOrderHeaders` that are associated with each `Contact`.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#returnnestedcollectionwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ReturnNestedCollectionWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#returnnestedcollectionwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="9c1e8-112">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9c1e8-112">See also</span></span>

- [<span data-ttu-id="9c1e8-113">Entity Framework용 EntityClient 공급자</span><span class="sxs-lookup"><span data-stu-id="9c1e8-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
