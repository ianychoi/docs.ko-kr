---
description: '자세한 정보: 방법: 타임 스탬프 또는 버전 열로 열 표현'
title: '방법: 열을 타임스탬프 또는 버전 열로 표현'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: 042e6a62c66b3f1ef522453157560e5e4c0f7de6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99712508"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>방법: 열을 타임스탬프 또는 버전 열로 표현

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 특성의 속성을 사용 <xref:System.Data.Linq.Mapping.ColumnAttribute> 하 여 필드 또는 속성을 데이터베이스 타임 스탬프 또는 버전 번호를 포함 하는 데이터베이스 열을 나타내는 것으로 지정할 수 있습니다.  
  
 코드 예는 <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>를 참조하세요.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>타임스탬프 또는 버전 열을 나타내도록 필드 또는 속성을 지정하려면  
  
1. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 특성에 <xref:System.Data.Linq.Mapping.ColumnAttribute> 속성을 추가합니다.  
  
2. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> 속성 값을 `true`로 설정합니다.  
  
## <a name="see-also"></a>참고 항목

- [LINQ to SQL 개체 모델](the-linq-to-sql-object-model.md)
- [방법: 동시성 충돌을 테스트할 멤버 지정](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [방법: 코드 편집기를 사용하여 엔터티 클래스 사용자 지정](how-to-customize-entity-classes-by-using-the-code-editor.md)
