---
description: "BC31103: ' ' 속성의 ' Get ' 접근자에 <propertyname> 액세스할 수 없음에 대해 자세히 알아보세요."
title: "'<propertyname>' 속성의 'Get' 접근자에 액세스할 수 없습니다."
ms.date: 07/20/2015
f1_keywords:
- vbc31103
- bc31103
helpviewer_keywords:
- BC31103
ms.assetid: 3c346c32-7669-4b04-841d-7a9df9cb703e
ms.openlocfilehash: 3517bc7ec512ec99909539eb4d7cf3fafe9016fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796134"
---
# <a name="bc31103-get-accessor-of-property-propertyname-is-not-accessible"></a><span data-ttu-id="9e1be-103">BC31103: ' ' 속성의 ' Get ' 접근자 \<propertyname> 에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-103">BC31103: 'Get' accessor of property '\<propertyname>' is not accessible</span></span>

<span data-ttu-id="9e1be-104">문이 속성의 프로시저에 대 한 액세스 권한이 없는 경우 속성의 값을 검색 하려고 시도 합니다 `Get` .</span><span class="sxs-lookup"><span data-stu-id="9e1be-104">A statement attempts to retrieve the value of a property when it does not have access to the property's `Get` procedure.</span></span>

 <span data-ttu-id="9e1be-105">[Get 문이](../statements/get-statement.md) [property 문](../statements/property-statement.md)보다 더 제한적인 액세스 수준으로 표시 되 면 다음과 같은 경우에 속성 값을 읽으려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-105">If the [Get Statement](../statements/get-statement.md) is marked with a more restrictive access level than its [Property Statement](../statements/property-statement.md), an attempt to read the property value could fail in the following cases:</span></span>

- <span data-ttu-id="9e1be-106">`Get`문이 [Private](../modifiers/private.md) 으로 표시 되 고 호출 코드가 속성이 정의 된 클래스 또는 구조체 외부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-106">The `Get` statement is marked [Private](../modifiers/private.md) and the calling code is outside the class or structure in which the property is defined.</span></span>

- <span data-ttu-id="9e1be-107">`Get`문이 [Protected](../modifiers/protected.md) 로 표시 되어 있고 호출 코드가 속성이 정의 된 클래스 또는 구조체에 없거나 파생 클래스에 없는 경우</span><span class="sxs-lookup"><span data-stu-id="9e1be-107">The `Get` statement is marked [Protected](../modifiers/protected.md) and the calling code is not in the class or structure in which the property is defined, nor in a derived class.</span></span>

- <span data-ttu-id="9e1be-108">`Get`문이 [Friend](../modifiers/friend.md) 로 표시 되어 있고 호출 코드가 속성이 정의 된 어셈블리와 동일 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-108">The `Get` statement is marked [Friend](../modifiers/friend.md) and the calling code is not in the same assembly in which the property is defined.</span></span>

 <span data-ttu-id="9e1be-109">**오류 ID:** BC31103</span><span class="sxs-lookup"><span data-stu-id="9e1be-109">**Error ID:** BC31103</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9e1be-110">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="9e1be-110">To correct this error</span></span>

- <span data-ttu-id="9e1be-111">속성을 정의 하는 소스 코드를 제어할 수 있는 경우 `Get` 속성 자체와 동일한 액세스 수준을 사용 하 여 프로시저를 선언 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-111">If you have control of the source code defining the property, consider declaring the `Get` procedure with the same access level as the property itself.</span></span>

- <span data-ttu-id="9e1be-112">속성을 정의 하는 소스 코드를 제어할 수 없거나 `Get` 프로시저 액세스 수준을 속성 자체 보다 더 제한 해야 하는 경우 속성 값을 읽는 문을 속성에 대 한 액세스를 향상 하는 코드 영역으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="9e1be-112">If you do not have control of the source code defining the property, or you must restrict the `Get` procedure access level more than the property itself, try to move the statement that reads the property value to a region of code that has better access to the property.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e1be-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9e1be-113">See also</span></span>

- [<span data-ttu-id="9e1be-114">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="9e1be-114">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="9e1be-115">방법: 액세스 수준이 혼합된 속성 선언</span><span class="sxs-lookup"><span data-stu-id="9e1be-115">How to: Declare a Property with Mixed Access Levels</span></span>](../../programming-guide/language-features/procedures/how-to-declare-a-property-with-mixed-access-levels.md)
