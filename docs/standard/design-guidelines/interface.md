---
title: 인터페이스 디자인
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 6f8cbb757ffb42f63903b212fee33cdcbba7ecb2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727681"
---
# <a name="interface-design"></a><span data-ttu-id="d6f92-102">인터페이스 디자인</span><span class="sxs-lookup"><span data-stu-id="d6f92-102">Interface Design</span></span>

<span data-ttu-id="d6f92-103">대부분의 Api는 클래스 및 구조체를 사용 하 여 모델링 하는 것이 좋지만 인터페이스가 더 적합 하거나 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="d6f92-104">CLR은 다중 상속을 지원 하지 않습니다. 즉, CLR 클래스는 둘 이상의 기본 클래스에서 상속할 수 없지만 기본 클래스에서 상속 하는 것 외에도 형식이 하나 이상의 인터페이스를 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="d6f92-105">따라서 여러 상속의 영향을 얻기 위해 인터페이스가 종종 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="d6f92-106">예를 들어 <xref:System.IDisposable> 는 형식이 참여 하려는 다른 상속 계층 구조와 독립적으로 disposability을 지원할 수 있도록 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="d6f92-107">인터페이스를 정의 하는 다른 상황은 일부 값 형식을 포함 하 여 여러 형식에서 지원할 수 있는 공용 인터페이스를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="d6f92-108">값 형식은 이외의 형식에서 상속할 수 <xref:System.ValueType> 없지만 인터페이스를 구현할 수 있으므로 공통 기본 형식을 제공 하기 위해 인터페이스를 사용 하는 것이 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="d6f92-109">값 형식을 포함 하는 형식 집합에서 몇 가지 공통 API를 지원 해야 하는 경우 인터페이스를 정의 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-109">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="d6f92-110">다른 형식에서 이미 상속 된 형식에 대해 해당 기능을 지원 해야 하는 경우 인터페이스를 정의 하는 것이 좋습니다. ✔️</span><span class="sxs-lookup"><span data-stu-id="d6f92-110">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="d6f92-111">❌ 마커 인터페이스 (멤버가 없는 인터페이스)를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="d6f92-111">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="d6f92-112">클래스를 특정 특성 (표식)으로 표시 해야 하는 경우 일반적으로 인터페이스가 아닌 사용자 지정 특성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="d6f92-113">인터페이스를 구현 하는 하나 이상의 형식을 제공 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-113">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="d6f92-114">이렇게 하면 인터페이스 디자인의 유효성을 검사 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="d6f92-115">예를 들어 <xref:System.Collections.Generic.List%601> 는 인터페이스의 구현입니다 <xref:System.Collections.Generic.IList%601> .</span><span class="sxs-lookup"><span data-stu-id="d6f92-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="d6f92-116">✔️는 정의 하는 각 인터페이스를 사용 하는 하나 이상의 API를 제공 합니다 (인터페이스를 매개 변수로 사용 하는 메서드 또는 인터페이스로 형식화 된 속성).</span><span class="sxs-lookup"><span data-stu-id="d6f92-116">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="d6f92-117">이렇게 하면 인터페이스 디자인의 유효성을 검사 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="d6f92-118">예를 들어는 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> 인터페이스를 사용 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="d6f92-119">❌ 이전에 제공 된 인터페이스에 멤버를 추가 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-119">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="d6f92-120">이렇게 하면 인터페이스의 구현이 중단 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="d6f92-121">버전 관리 문제를 방지 하기 위해 새 인터페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-121">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="d6f92-122">이러한 지침에 설명 된 상황을 제외 하 고 일반적으로 관리 코드 재사용 가능 라이브러리 디자인에서 인터페이스 대신 클래스를 선택 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6f92-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="d6f92-123">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d6f92-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d6f92-124">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="d6f92-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d6f92-125">참조</span><span class="sxs-lookup"><span data-stu-id="d6f92-125">See also</span></span>

- [<span data-ttu-id="d6f92-126">형식 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="d6f92-126">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="d6f92-127">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="d6f92-127">Framework Design Guidelines</span></span>](index.md)
