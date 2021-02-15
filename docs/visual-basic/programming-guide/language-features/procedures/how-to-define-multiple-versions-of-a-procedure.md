---
description: '자세히 알아보기: 방법: 여러 버전의 프로시저 정의 (Visual Basic)'
title: '방법: 여러 버전의 프로시저 정의'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 4b470e478c22c3a827f71b9b28056e16d6d9b7cd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456031"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a><span data-ttu-id="52782-103">방법: 여러 버전의 프로시저 정의(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="52782-103">How to: Define Multiple Versions of a Procedure (Visual Basic)</span></span>

<span data-ttu-id="52782-104">각 버전에 대해 동일한 이름을 사용 하 고 다른 매개 변수 목록을 사용 *하 여 프로시저* 를 여러 버전으로 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52782-104">You can define a procedure in multiple versions by *overloading* it, using the same name but a different parameter list for each version.</span></span> <span data-ttu-id="52782-105">오버 로드의 목적은 프로시저를 이름으로 구분 하지 않고도 긴밀 하 게 관련 된 여러 버전을 정의 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="52782-105">The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name.</span></span>  
  
 <span data-ttu-id="52782-106">자세한 내용은 [Procedure Overloading](./procedure-overloading.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="52782-106">For more information, see [Procedure Overloading](./procedure-overloading.md).</span></span>  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a><span data-ttu-id="52782-107">프로시저의 여러 버전을 정의 하려면</span><span class="sxs-lookup"><span data-stu-id="52782-107">To define multiple versions of a procedure</span></span>  
  
1. <span data-ttu-id="52782-108">정의 하려는 `Sub` `Function` 프로시저의 각 버전에 대 한 또는 선언문을 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-108">Write a `Sub` or `Function` declaration statement for each version of the procedure you want to define.</span></span> <span data-ttu-id="52782-109">모든 선언에 동일한 프로시저 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-109">Use the same procedure name in every declaration.</span></span>  
  
2. <span data-ttu-id="52782-110">`Sub` `Function` 각 선언의 또는 키워드 앞에 [Overloads](../../../language-reference/modifiers/overloads.md) 키워드를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-110">Precede the `Sub` or `Function` keyword in each declaration with the [Overloads](../../../language-reference/modifiers/overloads.md) keyword.</span></span> <span data-ttu-id="52782-111">필요에 따라 선언에서 생략할 수 있지만 선언에 `Overloads` 포함 하는 경우 모든 선언에 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-111">You can optionally omit `Overloads` in the declarations, but if you include it in any of the declarations, you must include it in every declaration.</span></span>  
  
3. <span data-ttu-id="52782-112">각 선언 문 다음에 호출 코드가 해당 버전의 매개 변수 목록과 일치 하는 인수를 제공 하는 특정 사례를 처리 하는 프로시저 코드를 작성 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-112">Following each declaration statement, write procedure code to handle the specific case where the calling code supplies arguments matching that version's parameter list.</span></span> <span data-ttu-id="52782-113">호출 코드에서 제공 하는 매개 변수를 테스트할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="52782-113">You do not have to test for which parameters the calling code has supplied.</span></span> <span data-ttu-id="52782-114">Visual Basic는 프로시저의 일치 하는 버전으로 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-114">Visual Basic passes control to the matching version of your procedure.</span></span>  
  
4. <span data-ttu-id="52782-115">또는 문을 사용 하 여 프로시저의 각 버전을 적절 하 게 종료 `End Sub` `End Function` 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-115">Terminate each version of the procedure with the `End Sub` or `End Function` statement as appropriate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52782-116">예</span><span class="sxs-lookup"><span data-stu-id="52782-116">Example</span></span>  

 <span data-ttu-id="52782-117">다음 예에서는 `Sub` 고객의 잔액에 대해 트랜잭션을 게시 하는 프로시저를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-117">The following example defines a `Sub` procedure to post a transaction against a customer's balance.</span></span> <span data-ttu-id="52782-118">키워드를 사용 하 여 `Overloads` 두 가지 버전의 프로시저를 정의 합니다. 하나는 이름으로 고객을 수락 하 고 다른 하나는 계정 번호로 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-118">It uses the `Overloads` keyword to define two versions of the procedure, one that accepts the customer by name and the other by account number.</span></span>  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 <span data-ttu-id="52782-119">호출 하는 코드는 또는로 고객 id를 가져온 `String` `Integer` 다음 두 경우 모두 동일한 호출 문을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="52782-119">The calling code can obtain the customer identification as either a `String` or an `Integer`, and then use the same calling statement in either case.</span></span>  
  
 <span data-ttu-id="52782-120">이러한 버전의 프로시저를 호출 하는 방법에 대 한 자세한 내용은 `post` [방법: 오버 로드 된 프로시저 호출](./how-to-call-an-overloaded-procedure.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="52782-120">For information on how to call these versions of the `post` procedure, see [How to: Call an Overloaded Procedure](./how-to-call-an-overloaded-procedure.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="52782-121">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="52782-121">Compile the code</span></span>  

 <span data-ttu-id="52782-122">오버 로드 된 각 버전에 동일한 프로시저 이름이 있지만 다른 매개 변수 목록이 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="52782-122">Make sure each of your overloaded versions has the same procedure name but a different parameter list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52782-123">추가 정보</span><span class="sxs-lookup"><span data-stu-id="52782-123">See also</span></span>

- [<span data-ttu-id="52782-124">절차</span><span class="sxs-lookup"><span data-stu-id="52782-124">Procedures</span></span>](./index.md)
- [<span data-ttu-id="52782-125">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="52782-125">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="52782-126">프로시저 문제 해결</span><span class="sxs-lookup"><span data-stu-id="52782-126">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="52782-127">방법: 선택적 매개 변수를 사용하는 프로시저 오버로드</span><span class="sxs-lookup"><span data-stu-id="52782-127">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="52782-128">방법: 매개 변수를 무제한으로 사용하는 프로시저 오버로드</span><span class="sxs-lookup"><span data-stu-id="52782-128">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="52782-129">프로시저 오버로드에서 고려해야 할 사항</span><span class="sxs-lookup"><span data-stu-id="52782-129">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="52782-130">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="52782-130">Overload Resolution</span></span>](./overload-resolution.md)
