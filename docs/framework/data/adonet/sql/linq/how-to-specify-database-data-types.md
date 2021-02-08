---
description: '자세한 정보: 방법: 데이터베이스 데이터 형식 지정'
title: '방법: 데이터베이스 데이터 형식 지정'
ms.date: 03/30/2017
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
ms.openlocfilehash: 004a16fe9dd0cda608485b13b03ce922d6a9f671
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785915"
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="7f4d2-103">방법: 데이터베이스 데이터 형식 지정</span><span class="sxs-lookup"><span data-stu-id="7f4d2-103">How to: Specify Database Data Types</span></span>

<span data-ttu-id="7f4d2-104">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 특성의 속성을 사용 <xref:System.Data.Linq.Mapping.ColumnAttribute> 하 여 t-sql 테이블 선언에서 열을 정의 하는 정확한 텍스트를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d2-104">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="7f4d2-105"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>를 사용하여 데이터베이스 인스턴스를 만들려고 계획한 경우에만 <xref:System.Data.Linq.DataContext.CreateDatabase%2A> 속성을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d2-105">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="7f4d2-106">코드 예는 <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f4d2-106">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="7f4d2-107">T-SQL 테이블에서 데이터 형식을 정의하기 위한 텍스트를 지정하려면</span><span class="sxs-lookup"><span data-stu-id="7f4d2-107">To specify text to define a data type in a T-SQL table</span></span>  
  
1. <span data-ttu-id="7f4d2-108"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 특성에 <xref:System.Data.Linq.Mapping.ColumnAttribute> 속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d2-108">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2. <span data-ttu-id="7f4d2-109"><xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> 속성 값을 T-SQL에서 사용되는 정확한 텍스트로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7f4d2-109">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f4d2-110">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f4d2-110">See also</span></span>

- [<span data-ttu-id="7f4d2-111">LINQ to SQL 개체 모델</span><span class="sxs-lookup"><span data-stu-id="7f4d2-111">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="7f4d2-112">방법: 코드 편집기를 사용하여 엔터티 클래스 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="7f4d2-112">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
