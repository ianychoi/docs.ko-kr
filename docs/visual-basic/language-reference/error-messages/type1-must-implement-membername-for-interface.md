---
description: "자세한 내용은 BC30154: ' '에서 ' ' <type1> <typename> <membername> 인터페이스에 대해 ' '을 (를) 구현 해야 합니다. <interfacename>"
title: <type1>'<typename>'은 '<interfacename>' 인터페이스에 대한 '<membername>'을 구현해야 합니다.
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: fc0cf8544984ddf41f1f91cb0bca90b630d9614d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100473565"
---
# <a name="bc30154-type1typename-must-implement-membername-for-interface-interfacename"></a><span data-ttu-id="a206a-103">BC30154: \<type1> ' ' \<typename> 은 ' ' \<membername> 인터페이스에 대해 ' '을 (를) 구현 해야 합니다. \<interfacename></span><span class="sxs-lookup"><span data-stu-id="a206a-103">BC30154: \<type1>'\<typename>' must implement '\<membername>' for interface '\<interfacename>'</span></span>

<span data-ttu-id="a206a-104">' ' \<typename> 은 ' ' \<membername> 인터페이스에 대해 ' '을 (를) 구현 해야 합니다 \<interfacename> .</span><span class="sxs-lookup"><span data-stu-id="a206a-104">'\<typename>' must implement '\<membername>' for interface '\<interfacename>'.</span></span> <span data-ttu-id="a206a-105">구현 속성에 일치 하는 ' ReadOnly '/' WriteOnly ' 지정 자가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-105">Implementing property must have matching 'ReadOnly'/'WriteOnly' specifiers.</span></span>

 <span data-ttu-id="a206a-106">클래스 또는 구조체는 인터페이스를 구현 하지만 인터페이스에 의해 정의 된 프로시저, 속성 또는 이벤트를 구현 하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-106">A class or structure claims to implement an interface but does not implement a procedure, property, or event defined by the interface.</span></span> <span data-ttu-id="a206a-107">인터페이스의 모든 멤버를 구현 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-107">Every member of the interface must be implemented.</span></span>

 <span data-ttu-id="a206a-108">**오류 ID:** BC30154</span><span class="sxs-lookup"><span data-stu-id="a206a-108">**Error ID:** BC30154</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a206a-109">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="a206a-109">To correct this error</span></span>

1. <span data-ttu-id="a206a-110">인터페이스에 정의 된 것과 동일한 이름 및 서명을 사용 하 여 멤버를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-110">Declare a member with the same name and signature as defined in the interface.</span></span> <span data-ttu-id="a206a-111">적어도, `End Function` `End Sub` 또는 문을 포함 해야 `End Property` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-111">Be sure to include at least the `End Function`, `End Sub`, or `End Property` statement.</span></span>

2. <span data-ttu-id="a206a-112">,, `Implements` 또는 문의 끝에 절을 `Function` 추가 `Sub` `Property` `Event` 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-112">Add an `Implements` clause to the end of the `Function`, `Sub`, `Property`, or `Event` statement.</span></span> <span data-ttu-id="a206a-113">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-113">For example:</span></span>

    ```vb
    Public Event ItHappened() Implements IBaseInterface.ItHappened
    ```

3. <span data-ttu-id="a206a-114">속성을 구현할 때 `ReadOnly` 또는 `WriteOnly` 가 인터페이스 정의에서와 동일한 방식으로 사용 되는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-114">When implementing a property, make sure that `ReadOnly` or `WriteOnly` is used in the same way as in the interface definition.</span></span>

4. <span data-ttu-id="a206a-115">속성을 구현 하는 경우 `Get` 및 `Set` 프로시저를 적절 하 게 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="a206a-115">When implementing a property, declare `Get` and `Set` procedures, as appropriate.</span></span>

## <a name="see-also"></a><span data-ttu-id="a206a-116">추가 정보</span><span class="sxs-lookup"><span data-stu-id="a206a-116">See also</span></span>

- [<span data-ttu-id="a206a-117">Implements 문</span><span class="sxs-lookup"><span data-stu-id="a206a-117">Implements Statement</span></span>](../statements/implements-statement.md)
- [<span data-ttu-id="a206a-118">인터페이스</span><span class="sxs-lookup"><span data-stu-id="a206a-118">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
