---
description: '자세한 정보: Method-Based 쿼리 구문 예제: 조인 (LINQ to DataSet)'
title: '메서드 기반 쿼리 구문 예제: 조인(LINQ to DataSet)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4fd5ed2c-b03a-4054-a3ed-3ddb380d7d9d
ms.openlocfilehash: f19921ceb874d120a3b50896f3ec82159ef03aac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672701"
---
# <a name="method-based-query-syntax-examples-join-linq-to-dataset"></a>메서드 기반 쿼리 구문 예제: 조인(LINQ to DataSet)

조인은 관계형 데이터베이스 테이블과 같이 서로 탐색할 수 없는 관계를 가진 데이터 소스를 대상으로 하는 쿼리에 사용되는 중요한 작업입니다. 두 데이터 소스를 조인하는 것은 한 데이터 소스의 개체를 공통 특성을 공유하는 다른 데이터 소스의 개체와 연결하는 것입니다. 자세한 내용은 [표준 쿼리 연산자 개요 (c #)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) 또는 [표준 쿼리 연산자 개요 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)를 참조 하세요.  
  
 이 항목의 예제에서는 <xref:System.Linq.Enumerable.Join%2A> 메서드에서 메서드 쿼리 구문을 사용하여 <xref:System.Data.DataSet>을 쿼리하는 방법을 보여 줍니다.  
  
 이러한 예제에서 사용되는 `FillDataSet` 메서드는 [데이터집합에 데이터를 로드](loading-data-into-a-dataset.md)하는데 지정됩니다.  
  
 이 항목의 예제에서는 AdventureWorks 샘플 데이터베이스의 Contact, Address, Product, SalesOrderHeader 및 SalesOrderDetail 테이블을 사용합니다.  
  
 이 항목의 예제에서는 다음 문을 사용 합니다 `using` / `Imports` .  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 자세한 내용은 [방법: Visual Studio에서 LINQ to DataSet 프로젝트 만들기](how-to-create-a-linq-to-dataset-project-in-vs.md)를 참조 하세요.  
  
## <a name="join"></a>Join  
  
### <a name="example"></a>예제  

 이 예제에서는 `Contact` 및 `SalesOrderHeader` 테이블에 대한 조인을 수행합니다.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinsimple_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinSimple_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinsimple_mq)]  
  
### <a name="example"></a>예제  

 이 예제에서는 `Contact` 및 `SalesOrderHeader` 테이블에 대한 조인을 수행하고 연락처 ID별로 결과를 그룹화합니다.  
  
 [!code-csharp[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#joinwithgroupedresults_mq)]
 [!code-vb[DP LINQ to DataSet Examples#JoinWithGroupedResults_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#joinwithgroupedresults_mq)]  
  
## <a name="see-also"></a>참고 항목

- [데이터를 데이터 세트에 로드](loading-data-into-a-dataset.md)
- [LINQ to DataSet 예제](linq-to-dataset-examples.md)
- [표준 쿼리 연산자 개요(C#)](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [표준 쿼리 연산자 개요(Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
