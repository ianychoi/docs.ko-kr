---
description: '자세히 알아보기: 중첩 된 Entity SQL 쿼리 작성'
title: 중첩 Entity SQL 쿼리 작성
ms.date: 03/30/2017
ms.assetid: 685d4cd3-2c1f-419f-bb46-c9d97a351eeb
ms.openlocfilehash: 971625f0b1e82068192d4f8f74e2f1c55043d900
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99724897"
---
# <a name="composing-nested-entity-sql-queries"></a>중첩 Entity SQL 쿼리 작성

[!INCLUDE[esql](../../../../../../includes/esql-md.md)]은 다양한 기능을 가진 언어입니다. 의 빌딩 블록은 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 식입니다. 기존 SQL과 달리 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 은 테이블 형식 결과 집합으로 제한 되지 않습니다 .는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 리터럴, 매개 변수 또는 중첩 된 식을 포함할 수 있는 복잡 한 식을 작성할 수 있도록 지원 합니다. 식의 값은 매개 변수화할 수 있으며 다른 식으로 구성될 수도 있습니다.  
  
## <a name="nested-expressions"></a>중첩된 식  

 중첩된 식은 자신이 반환한 형식의 값이 허용되는 임의의 위치에 놓일 수 있습니다. 다음은 그 예입니다.   
  
```sql  
-- Returns a hierarchical collection of three elements at top-level.
-- x must be passed in the parameter collection.  
ROW(@x, {@x}, {@x, 4, 5}, {@x, 7, 8, 9})  
  
-- Returns a hierarchical collection of one element at top-level.  
-- x must be passed in the parameter collection.  
{{{@x}}};  
```  
  
 중첩 쿼리는 프로젝션 절에 위치할 수 있습니다. 다음은 그 예입니다.   
  
```sql  
-- Returns a collection of rows where each row contains an Address entity.  
-- and a collection of references to its corresponding SalesOrderHeader entities.  
SELECT address, (SELECT DEREF(soh)
                    FROM NAVIGATE(address, AdventureWorksModel.FK_SalesOrderHeader_Address_BillToAddressID) AS soh)
                    AS salesOrderHeader FROM AdventureWorksEntities.Address AS address  
```  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]에서 중첩 쿼리는 반드시 괄호로 묶어야 합니다.  
  
```sql  
-- Pseudo-Entity SQL  
( SELECT …  
FROM … )  
UNION ALL  
( SELECT …  
FROM … );  
```  
  
 다음 예제에서는 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] [방법: 두 쿼리의 합집합 순서를 정렬](/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))하는 방법을 보여 줍니다.  
  
## <a name="nested-queries-in-projection"></a>프로젝션의 중첩 쿼리  

 프로젝션 절의 중첩 쿼리는 서버의 Cartesian 제품 쿼리로 변환될 수 있습니다. SQL Server를 포함 한 일부 백엔드 서버에서는 TempDB 테이블이 매우 커질 수 있으므로 서버 성능에 부정적인 영향을 줄 수 있습니다.  
  
 다음은 이러한 쿼리의 예제입니다.  
  
```sql  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="ordering-nested-queries"></a>중첩 쿼리 순서  

 Entity Framework에서 중첩된 식은 쿼리 내 임의의 위치에 올 수 있습니다. Entity SQL을 사용하면 보다 유연성 있게 쿼리를 작성할 수 있으므로 중첩 쿼리의 순서가 포함된 쿼리를 작성할 수 있습니다. 하지만 중첩 쿼리의 순서는 유지되지 않습니다.  
  
```sql  
-- The following query will order the results by last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```sql  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorksModel.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="see-also"></a>참고 항목

- [Entity SQL 개요](entity-sql-overview.md)
