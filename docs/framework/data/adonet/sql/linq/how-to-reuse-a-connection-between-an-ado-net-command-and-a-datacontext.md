---
description: '자세한 정보: 방법: ADO.NET 명령 및 DataContext 간 연결 다시 사용'
title: '방법: ADO.NET 명령 및 DataContext 간의 연결 다시 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7e26c7eb-c18a-43b5-a8f0-28fd8b04b0f0
ms.openlocfilehash: d5bf45dfd705ed6e9b9d4ed9659e01bfcb539df2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785954"
---
# <a name="how-to-reuse-a-connection-between-an-adonet-command-and-a-datacontext"></a>방법: ADO.NET 명령 및 DataContext 간의 연결 다시 사용

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]는 ADO.NET 기술 제품군의 일부이 고 ADO.NET에서 제공 하는 서비스를 기반으로 하기 때문에 ADO.NET 명령과 간의 연결을 다시 사용할 수 있습니다 <xref:System.Data.Linq.DataContext> .  
  
## <a name="example"></a>예제  

 다음 예제에서는 ADO.NET 명령과 사이에 동일한 연결을 다시 사용 하는 방법을 보여 줍니다 <xref:System.Data.Linq.DataContext> .  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>참고 항목

- [배경 정보](background-information.md)
- [ADO.NET 및 LINQ to SQL](ado-net-and-linq-to-sql.md)
- [데이터베이스와 통신](communicating-with-the-database.md)
