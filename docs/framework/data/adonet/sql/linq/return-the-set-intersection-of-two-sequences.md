---
description: '자세한 정보: 두 시퀀스의 교집합 반환'
title: 두 시퀀스의 교집합 반환
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d09c344e-3548-4944-a3ed-051880e3f5b8
ms.openlocfilehash: 163e138761caadb73b6dc5d672c02353a88a2c22
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662985"
---
# <a name="return-the-set-intersection-of-two-sequences"></a>두 시퀀스의 교집합 반환

<xref:System.Linq.Queryable.Intersect%2A> 연산자를 사용하여 두 시퀀스의 교집합을 반환합니다.  
  
## <a name="example"></a>예제  

 이 예에서는 <xref:System.Linq.Queryable.Intersect%2A> 를 사용 하 여와 라이브 모두에 있는 모든 국가/지역의 시퀀스를 반환 합니다 `Customers` `Employees` .  
  
 [!code-csharp[DLinqQueryExamples#42](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#42)]
 [!code-vb[DLinqQueryExamples#42](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#42)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서 <xref:System.Linq.Queryable.Intersect%2A> 작업은 집합에 대해서만 적절하게 정의되어 있습니다. 다중 집합에 대한 의미 체계는 정의되어 있지 않습니다.  
  
## <a name="see-also"></a>참고 항목

- [쿼리 예제](query-examples.md)
- [표준 쿼리 연산자 변환](standard-query-operator-translation.md)
