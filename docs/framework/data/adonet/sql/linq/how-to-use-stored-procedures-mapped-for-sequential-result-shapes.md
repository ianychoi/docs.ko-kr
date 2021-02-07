---
description: '자세한 정보: 방법: 순차적 결과 도형에 매핑된 저장 프로시저 사용'
title: '방법: 순차적 결과 도형에 매핑된 저장 프로시저 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a73530de-5a4e-4d9c-8d66-abb19c225b11
ms.openlocfilehash: 3b5791875a7beb5a0c702e787e775cd528ab2517
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738769"
---
# <a name="how-to-use-stored-procedures-mapped-for-sequential-result-shapes"></a><span data-ttu-id="60e1c-103">방법: 순차적 결과 도형에 매핑된 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="60e1c-103">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>

<span data-ttu-id="60e1c-104">이러한 종류의 저장 프로시저에서는 두 개 이상의 결과 도형을 만들지만 결과가 반환되는 순서를 사용자가 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e1c-104">This kind of stored procedure can generate more than one result shape, but you know in what order the results are returned.</span></span> <span data-ttu-id="60e1c-105">이러한 시나리오와 반대로 사용자가 반환 순서를 모르는 시나리오에 대한</span><span class="sxs-lookup"><span data-stu-id="60e1c-105">Contrast this scenario with the scenario where you do not know the sequence of the returns.</span></span> <span data-ttu-id="60e1c-106">자세한 내용은 [방법: 여러 결과 도형에 매핑된 저장 프로시저 사용](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="60e1c-106">For more information, see [How to: Use Stored Procedures Mapped for Multiple Result Shapes](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60e1c-107">예제</span><span class="sxs-lookup"><span data-stu-id="60e1c-107">Example</span></span>  

 <span data-ttu-id="60e1c-108">다음은 순차적으로 여러 결과 도형을 반환하는 T-SQL 저장 프로시저입니다.</span><span class="sxs-lookup"><span data-stu-id="60e1c-108">Here is the T-SQL of a stored procedure that returns multiple result shapes sequentially:</span></span>  
  
```sql
CREATE PROCEDURE MultipleResultTypesSequentially  
AS  
select * from products  
select * from customers  
```  
  
 [!code-csharp[DLinqSprox#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#6)]
 [!code-vb[DLinqSprox#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="60e1c-109">예제</span><span class="sxs-lookup"><span data-stu-id="60e1c-109">Example</span></span>  

 <span data-ttu-id="60e1c-110">다음과 유사한 코드를 사용하여 이 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="60e1c-110">You would use code similar to the following to execute this stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#7)]
 [!code-vb[DLinqSprox#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="60e1c-111">참고 항목</span><span class="sxs-lookup"><span data-stu-id="60e1c-111">See also</span></span>

- [<span data-ttu-id="60e1c-112">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="60e1c-112">Stored Procedures</span></span>](stored-procedures.md)
