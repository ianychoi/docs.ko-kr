---
description: '자세한 정보: 방법: 여러 결과 도형에 매핑된 저장 프로시저 사용'
title: '방법: 여러 결과 도형에 매핑된 저장 프로시저 사용'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2b84dfe-7fec-489a-92de-45215cec4518
ms.openlocfilehash: 9faf80e565656120a2601b30424df80ca10913e8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785824"
---
# <a name="how-to-use-stored-procedures-mapped-for-multiple-result-shapes"></a><span data-ttu-id="08c87-103">방법: 여러 결과 도형에 매핑된 저장 프로시저 사용</span><span class="sxs-lookup"><span data-stu-id="08c87-103">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>

<span data-ttu-id="08c87-104">저장 프로시저에서 여러 결과 도형을 반환할 수 있는 경우 반환 형식은 단일 프로젝션 도형에 대해 강력하게 형식화될 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-104">When a stored procedure can return multiple result shapes, the return type cannot be strongly typed to a single projection shape.</span></span> <span data-ttu-id="08c87-105">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]에서는 모든 가능한 프로젝션 형식을 생성할 수 있더라도 해당 형식들이 반환되는 순서는 알 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-105">Although [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can generate all possible projection types, it cannot know the order in which they will be returned.</span></span>  
  
 <span data-ttu-id="08c87-106">이 시나리오와 달리 순차적으로 여러 결과 도형을 생성하는 저장 프로시저에 대한</span><span class="sxs-lookup"><span data-stu-id="08c87-106">Contrast this scenario with stored procedures that produce multiple result shapes sequentially.</span></span> <span data-ttu-id="08c87-107">자세한 내용은 [방법: 순차적 결과 도형에 매핑된 저장 프로시저 사용](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08c87-107">For more information, see [How to: Use Stored Procedures Mapped for Sequential Result Shapes](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md).</span></span>  
  
 <span data-ttu-id="08c87-108"><xref:System.Data.Linq.Mapping.ResultTypeAttribute> 특성을 여러 결과 형식을 반환하는 저장 프로시저에 적용하여 프로시저에서 반환할 수 있는 형식 집합을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-108">The <xref:System.Data.Linq.Mapping.ResultTypeAttribute> attribute is applied to stored procedures that return multiple result types to specify the set of types the procedure can return.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08c87-109">예제</span><span class="sxs-lookup"><span data-stu-id="08c87-109">Example</span></span>  

 <span data-ttu-id="08c87-110">다음 SQL 코드 예제에서 결과 도형은 입력(`shape =1` 또는 `shape = 2`)에 따라 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-110">In the following SQL code example, the result shape depends on the input (`shape =1` or `shape = 2`).</span></span> <span data-ttu-id="08c87-111">따라서 사용자는 처음 반환되는 프로젝션을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-111">You do not know which projection will be returned first.</span></span>  
  
``` sql
CREATE PROCEDURE VariableResultShapes(@shape int)  
AS  
if(@shape = 1)  
    select CustomerID, ContactTitle, CompanyName from customers  
else if(@shape = 2)  
    select OrderID, ShipName from orders  
```  
  
 [!code-csharp[DLinqSprox#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#4)]
 [!code-vb[DLinqSprox#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="08c87-112">예제</span><span class="sxs-lookup"><span data-stu-id="08c87-112">Example</span></span>  

 <span data-ttu-id="08c87-113">다음과 유사한 코드를 사용하여 이 저장 프로시저를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-113">You would use code similar to the following to execute this stored procedure.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08c87-114">저장 프로시저에 대한 정보에 따라 <xref:System.Data.Linq.IMultipleResults.GetResult%2A> 패턴을 사용하여 올바른 형식의 열거자를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08c87-114">You must use the <xref:System.Data.Linq.IMultipleResults.GetResult%2A> pattern to obtain an enumerator of the correct type, based on your knowledge of the stored procedure.</span></span>  
  
 [!code-csharp[DLinqSprox#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#5)]
 [!code-vb[DLinqSprox#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="08c87-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08c87-115">See also</span></span>

- [<span data-ttu-id="08c87-116">저장 프로시저</span><span class="sxs-lookup"><span data-stu-id="08c87-116">Stored Procedures</span></span>](stored-procedures.md)
