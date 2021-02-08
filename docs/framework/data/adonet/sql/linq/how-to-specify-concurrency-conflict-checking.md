---
description: '자세히 알아보기: 방법: Concurrency-Conflict 확인 지정'
title: '방법: 동시성 충돌 확인 지정'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2547fcb-58eb-4377-9948-1b8d76a0f3d7
ms.openlocfilehash: a1c1c771dba95e558d86764d023625a63e9e53bc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785928"
---
# <a name="how-to-specify-concurrency-conflict-checking"></a><span data-ttu-id="200be-103">방법: 동시성 충돌 확인 지정</span><span class="sxs-lookup"><span data-stu-id="200be-103">How to: Specify Concurrency-Conflict Checking</span></span>

<span data-ttu-id="200be-104"><xref:System.Data.Linq.DataContext.SubmitChanges%2A>를 호출하는 경우 동시성 충돌을 검사할 데이터베이스의 열을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="200be-104">You can specify which columns of the database are to be checked for concurrency conflicts when you call <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.</span></span> <span data-ttu-id="200be-105">자세한 내용은 [방법: 동시성 충돌에 대해 테스트할 멤버 지정](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="200be-105">For more information, see [How to: Specify Which Members are Tested for Concurrency Conflicts](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="200be-106">예제</span><span class="sxs-lookup"><span data-stu-id="200be-106">Example</span></span>  

 <span data-ttu-id="200be-107">다음 코드에서는 업데이트를 확인하는 동안 `HomePage` 멤버를 테스트하지 말아야 함을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="200be-107">The following code specifies that the `HomePage` member should never be tested during update checks.</span></span> <span data-ttu-id="200be-108">자세한 내용은 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="200be-108">For more information, see <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.</span></span>  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="200be-109">참조</span><span class="sxs-lookup"><span data-stu-id="200be-109">See also</span></span>

- [<span data-ttu-id="200be-110">LINQ to SQL 개체 모델</span><span class="sxs-lookup"><span data-stu-id="200be-110">The LINQ to SQL Object Model</span></span>](the-linq-to-sql-object-model.md)
- [<span data-ttu-id="200be-111">방법: 코드 편집기를 사용하여 엔터티 클래스 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="200be-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](how-to-customize-entity-classes-by-using-the-code-editor.md)
