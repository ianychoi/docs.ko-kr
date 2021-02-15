---
description: '자세히 알아보기: 방법: 값을 반환 하는 프로시저 만들기 (Visual Basic)'
title: '방법: 값을 반환하는 프로시저 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: fa2ea50febd1cc4e7aecf1e6f5cca671789b36fd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100467058"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a><span data-ttu-id="5f898-103">방법: 값을 반환하는 프로시저 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f898-103">How to: Create a Procedure that Returns a Value (Visual Basic)</span></span>

<span data-ttu-id="5f898-104">프로시저를 사용 하 여 `Function` 호출 코드에 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-104">You use a `Function` procedure to return a value to the calling code.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="5f898-105">값을 반환 하는 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="5f898-105">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="5f898-106">다른 프로시저 외부에서는 문을 사용 하 고 `Function` `End Function` 문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-106">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="5f898-107">`Function`문에서 `Function` 키워드를 프로시저 이름으로 따르고 매개 변수 목록을 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-107">In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="5f898-108">절을 사용 하 여 괄호를 따라 `As` 반환 된 값의 데이터 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-108">Follow the parentheses with an `As` clause to specify the data type of the returned value.</span></span>  
  
4. <span data-ttu-id="5f898-109">프로시저의 코드 문을 문과 문 사이에 `Function` 놓습니다 `End Function` .</span><span class="sxs-lookup"><span data-stu-id="5f898-109">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
5. <span data-ttu-id="5f898-110">문을 사용 `Return` 하 여 호출 코드에 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-110">Use a `Return` statement to return the value to the calling code.</span></span>  
  
     <span data-ttu-id="5f898-111">다음 `Function` 프로시저는 다른 두 변의 값을 고려 하 여 오른쪽 삼각형의 가장 긴 쪽 또는 빗변을 계산 합니다.</span><span class="sxs-lookup"><span data-stu-id="5f898-111">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     <span data-ttu-id="5f898-112">다음 예제에서는에 대 한 일반적인 호출을 보여 줍니다 `hypotenuse` .</span><span class="sxs-lookup"><span data-stu-id="5f898-112">The following example shows a typical call to `hypotenuse`.</span></span>  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="5f898-113">추가 정보</span><span class="sxs-lookup"><span data-stu-id="5f898-113">See also</span></span>

- [<span data-ttu-id="5f898-114">절차</span><span class="sxs-lookup"><span data-stu-id="5f898-114">Procedures</span></span>](./index.md)
- [<span data-ttu-id="5f898-115">하위 프로시저</span><span class="sxs-lookup"><span data-stu-id="5f898-115">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="5f898-116">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="5f898-116">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="5f898-117">연산자 프로시저</span><span class="sxs-lookup"><span data-stu-id="5f898-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="5f898-118">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="5f898-118">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="5f898-119">Function 문</span><span class="sxs-lookup"><span data-stu-id="5f898-119">Function Statement</span></span>](../../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="5f898-120">방법: 프로시저에서 값 반환</span><span class="sxs-lookup"><span data-stu-id="5f898-120">How to: Return a Value from a Procedure</span></span>](./how-to-return-a-value-from-a-procedure.md)
- [<span data-ttu-id="5f898-121">방법: 값을 반환하는 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="5f898-121">How to: Call a Procedure That Returns a Value</span></span>](./how-to-call-a-procedure-that-returns-a-value.md)
