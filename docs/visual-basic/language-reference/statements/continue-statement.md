---
description: '자세히 알아보기: Continue 문 (Visual Basic)'
title: Continue 문
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: c6d67e766b2551956795803076efe639ba3c8c99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99673871"
---
# <a name="continue-statement-visual-basic"></a><span data-ttu-id="88d8d-103">Continue 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88d8d-103">Continue Statement (Visual Basic)</span></span>

<span data-ttu-id="88d8d-104">루프의 다음 반복으로 즉시 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-104">Transfers control immediately to the next iteration of a loop.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88d8d-105">구문</span><span class="sxs-lookup"><span data-stu-id="88d8d-105">Syntax</span></span>  
  
```vb  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a><span data-ttu-id="88d8d-106">설명</span><span class="sxs-lookup"><span data-stu-id="88d8d-106">Remarks</span></span>  

 <span data-ttu-id="88d8d-107">`Do`, `For` 또는 루프 내에서 `While` 해당 루프의 다음 반복으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-107">You can transfer from inside a `Do`, `For`, or `While` loop to the next iteration of that loop.</span></span> <span data-ttu-id="88d8d-108">제어는 `For` 또는 문으로 전송 하거나 `While` `Do` `Loop` 또는 절이 포함 된 또는 문으로 루프 `Until` 조건 테스트에 즉시 전달 됩니다 `While` .</span><span class="sxs-lookup"><span data-stu-id="88d8d-108">Control passes immediately to the loop condition test, which is equivalent to transferring to the `For` or `While` statement, or to the `Do` or `Loop` statement that contains the `Until` or `While` clause.</span></span>  
  
 <span data-ttu-id="88d8d-109">`Continue`전송을 허용 하는 루프의 모든 위치에서을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-109">You can use `Continue` at any location in the loop that allows transfers.</span></span> <span data-ttu-id="88d8d-110">제어를 전송할 수 있도록 허용 하는 규칙은 [GoTo 문과](goto-statement.md)동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-110">The rules allowing transfer of control are the same as with the [GoTo Statement](goto-statement.md).</span></span>  
  
 <span data-ttu-id="88d8d-111">예를 들어 루프가 블록, 블록 또는 블록 내에 완전히 포함 된 경우를 `Try` `Catch` `Finally` 사용 `Continue` 하 여 루프 밖으로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-111">For example, if a loop is totally contained within a `Try` block, a `Catch` block, or a `Finally` block, you can use `Continue` to transfer out of the loop.</span></span> <span data-ttu-id="88d8d-112">반면, `Try` ... 구조체가 루프 내에 포함 된 경우를 `End Try` 사용 하 여 제어를 블록 밖으로 전송 하 고,이를 사용 하 여 또는 블록 밖으로 전송 하는 경우에 `Continue` `Finally` `Try` `Catch` 만 또는 블록 `Try` `End Try` 외부로 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-112">If, on the other hand, the `Try`...`End Try` structure is contained within the loop, you cannot use `Continue` to transfer control out of the `Finally` block, and you can use it to transfer out of a `Try` or `Catch` block only if you transfer completely out of the `Try`...`End Try` structure.</span></span>  
  
 <span data-ttu-id="88d8d-113">다른 루프 내의 루프와 같이 동일한 형식의 루프를 중첩 하는 경우 `Do` `Do` 문은 해당 루프를 `Continue Do` `Do` 포함 하는 가장 안쪽 루프의 다음 반복으로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-113">If you have nested loops of the same type, for example a `Do` loop within another `Do` loop, a `Continue Do` statement skips to the next iteration of the innermost `Do` loop that contains it.</span></span> <span data-ttu-id="88d8d-114">를 사용 하 여 `Continue` 같은 형식의 포함 하는 루프의 다음 반복으로 건너뛸 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-114">You cannot use `Continue` to skip to the next iteration of a containing loop of the same type.</span></span>  
  
 <span data-ttu-id="88d8d-115">루프 내에서 루프와 같이 다양 한 형식의 루프를 중첩 한 경우 `Do` `For` 또는를 사용 하 여 두 루프의 다음 반복으로 건너뛸 수 있습니다 `Continue Do` `Continue For` .</span><span class="sxs-lookup"><span data-stu-id="88d8d-115">If you have nested loops of different types, for example a `Do` loop within a `For` loop, you can skip to the next iteration of either loop by using either `Continue Do` or `Continue For`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88d8d-116">예제</span><span class="sxs-lookup"><span data-stu-id="88d8d-116">Example</span></span>  

 <span data-ttu-id="88d8d-117">다음 코드 예제에서는 문을 사용 하 여 `Continue While` 제수가 0 인 경우 배열의 다음 열로 건너뜁니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-117">The following code example uses the `Continue While` statement to skip to the next column of an array if a divisor is zero.</span></span> <span data-ttu-id="88d8d-118">`Continue While`가 루프 내에 `For` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="88d8d-118">The `Continue While` is inside a `For` loop.</span></span> <span data-ttu-id="88d8d-119">`While col < lastcol`루프를 포함 하는 가장 안쪽 루프의 다음 반복 인 문으로 전송 합니다 `While` `For` .</span><span class="sxs-lookup"><span data-stu-id="88d8d-119">It transfers to the `While col < lastcol` statement, which is the next iteration of the innermost `While` loop that contains the `For` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="88d8d-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="88d8d-120">See also</span></span>

- [<span data-ttu-id="88d8d-121">Do...Loop 문</span><span class="sxs-lookup"><span data-stu-id="88d8d-121">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="88d8d-122">For...Next 문</span><span class="sxs-lookup"><span data-stu-id="88d8d-122">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="88d8d-123">While...End While 문</span><span class="sxs-lookup"><span data-stu-id="88d8d-123">While...End While Statement</span></span>](while-end-while-statement.md)
- [<span data-ttu-id="88d8d-124">Try...Catch...Finally 문</span><span class="sxs-lookup"><span data-stu-id="88d8d-124">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
