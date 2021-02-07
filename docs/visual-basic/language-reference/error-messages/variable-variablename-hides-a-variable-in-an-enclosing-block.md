---
description: "자세히 알아보기: BC30616: ' ' 변수 <variablename> 는 바깥쪽 블록의 변수를 숨깁니다."
title: "'<variablename>' 변수는 바깥쪽 블록에 있는 변수를 숨깁니다."
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: a0b2a4d024ff0409b5617354b5e671ca6dc0305b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666123"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="b0091-103">BC30616: ' \<variablename> ' 변수는 바깥쪽 블록의 변수를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="b0091-103">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="b0091-104">블록에 포함 된 변수는 다른 지역 변수와 동일한 이름을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="b0091-104">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="b0091-105">**오류 ID:** BC30616</span><span class="sxs-lookup"><span data-stu-id="b0091-105">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b0091-106">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="b0091-106">To correct this error</span></span>

- <span data-ttu-id="b0091-107">다른 지역 변수와 동일 하지 않도록 포함 된 블록의 변수 이름을 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b0091-107">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="b0091-108">다음은 그 예입니다. </span><span class="sxs-lookup"><span data-stu-id="b0091-108">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="b0091-109">이 오류의 일반적인 원인은 이벤트 처리기 내에서를 사용 하는 것입니다 `Catch e As Exception` .</span><span class="sxs-lookup"><span data-stu-id="b0091-109">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="b0091-110">이 경우에는 `Catch` 대신 블록 변수의 이름을로 `ex` `e` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b0091-110">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="b0091-111">이 오류의 또 다른 일반적인 소스는 블록 내에서 선언 된 지역 변수를 별도의 블록에 액세스 하려고 시도 하는 것입니다 `Try` `Catch` .</span><span class="sxs-lookup"><span data-stu-id="b0091-111">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="b0091-112">이를 해결 하려면 구조체 외부에서 변수를 선언 합니다 `Try...Catch...Finally` .</span><span class="sxs-lookup"><span data-stu-id="b0091-112">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="b0091-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="b0091-113">See also</span></span>

- [<span data-ttu-id="b0091-114">Try...Catch...Finally 문</span><span class="sxs-lookup"><span data-stu-id="b0091-114">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b0091-115">변수 선언</span><span class="sxs-lookup"><span data-stu-id="b0091-115">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
