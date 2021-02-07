---
description: '자세히 알아보기: 보호 된 Friend (Visual Basic)'
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: dcc8fd2b1aa99f910f002ac05178d379532fb73d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700977"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="34a55-103">보호 된 Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34a55-103">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="34a55-104">`Protected Friend` 키워드 조합은 멤버 액세스 한정자입니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-104">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="34a55-105">선언 된 요소에 대 한 [Friend](friend.md) 액세스와 [보호 된](protected.md) 액세스를 모두 권한을 부여, 동일한 어셈블리, 자체 클래스 및 파생 클래스의 어디에서 나 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-105">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="34a55-106">클래스의 멤버만 지정할 수 있습니다. 구조체 `Protected Friend` `Protected Friend` 는 상속 될 수 없으므로 구조체의 멤버에는 적용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-106">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="34a55-107">Visual Studio에서 F1 도움말을 선택 하 여 `protected friend` [보호](protected.md) 또는 [friend](friend.md)에 대 한 도움말을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-107">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="34a55-108">IDE는 복합 단어가 아니라 커서에서 단일 토큰을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-108">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="34a55-109">규칙</span><span class="sxs-lookup"><span data-stu-id="34a55-109">Rules</span></span>

<span data-ttu-id="34a55-110">**선언 컨텍스트.**</span><span class="sxs-lookup"><span data-stu-id="34a55-110">**Declaration Context.**</span></span> <span data-ttu-id="34a55-111">`Protected Friend`는 클래스 수준 에서만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-111">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="34a55-112">즉, 요소에 대 한 선언 컨텍스트는 `Protected` 클래스 여야 하며 소스 파일, 네임 스페이스, 인터페이스, 모듈, 구조체 또는 프로시저일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="34a55-112">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="34a55-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="34a55-113">See also</span></span>

- [<span data-ttu-id="34a55-114">공용</span><span class="sxs-lookup"><span data-stu-id="34a55-114">Public</span></span>](public.md)
- [<span data-ttu-id="34a55-115">보호됨</span><span class="sxs-lookup"><span data-stu-id="34a55-115">Protected</span></span>](protected.md)
- [<span data-ttu-id="34a55-116">Friend</span><span class="sxs-lookup"><span data-stu-id="34a55-116">Friend</span></span>](friend.md)
- [<span data-ttu-id="34a55-117">개인</span><span class="sxs-lookup"><span data-stu-id="34a55-117">Private</span></span>](private.md)
- [<span data-ttu-id="34a55-118">비공개 보호</span><span class="sxs-lookup"><span data-stu-id="34a55-118">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="34a55-119">Visual Basic의 액세스 수준</span><span class="sxs-lookup"><span data-stu-id="34a55-119">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="34a55-120">절차</span><span class="sxs-lookup"><span data-stu-id="34a55-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="34a55-121">구조체</span><span class="sxs-lookup"><span data-stu-id="34a55-121">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="34a55-122">개체 및 클래스</span><span class="sxs-lookup"><span data-stu-id="34a55-122">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
