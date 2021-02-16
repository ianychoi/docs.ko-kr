---
description: '자세한 정보: 인터페이스 디자인'
title: 인터페이스 디자인
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
ms.openlocfilehash: 387f921f8bdbe6c6d398aa31dcc8a22c7da455f7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641982"
---
# <a name="interface-design"></a><span data-ttu-id="db530-103">인터페이스 디자인</span><span class="sxs-lookup"><span data-stu-id="db530-103">Interface Design</span></span>

<span data-ttu-id="db530-104">대부분의 API는 클래스 및 구조체를 사용하여 모델링하는 것이 가장 좋지만 인터페이스가 더 적합하거나 유일한 옵션인 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="db530-104">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>

 <span data-ttu-id="db530-105">CLR은 다중 상속을 지원하지 않지만(즉, CLR 클래스는 둘 이상의 기본 클래스에서 상속할 수 없음) 기본 클래스에서 상속할 뿐만 아니라 하나 이상의 인터페이스를 구현하는 형식을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="db530-105">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="db530-106">따라서 인터페이스는 대개 다중 상속의 효과를 얻는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="db530-106">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="db530-107">예를 들어 <xref:System.IDisposable>은 참여하려는 다른 모든 상속 계층 구조와 별도로 형식이 삭제 가능성을 지원할 수 있도록 하는 인터페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="db530-107">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>

 <span data-ttu-id="db530-108">인터페이스 정의가 적합한 다른 상황은 일부 값 형식을 포함하여 여러 형식에서 지원할 수 있는 공용 인터페이스를 만드는 경우입니다.</span><span class="sxs-lookup"><span data-stu-id="db530-108">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="db530-109">값 형식은 <xref:System.ValueType> 이외의 다른 형식에서 상속할 수 없지만 인터페이스를 구현할 수 있으므로 공통 기본 형식을 제공하려면 인터페이스 사용이 유일한 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="db530-109">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>

 <span data-ttu-id="db530-110">✔️ 값 형식을 포함하는 형식 세트에서 몇 가지 공용 API를 지원해야 하는 경우 인터페이스를 정의하세요.</span><span class="sxs-lookup"><span data-stu-id="db530-110">✔️ DO define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>

 <span data-ttu-id="db530-111">✔️ 몇 가지 다른 형식에서 이미 상속된 형식에서 해당 기능을 지원해야 하는 경우 인터페이스를 정의하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="db530-111">✔️ CONSIDER defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>

 <span data-ttu-id="db530-112">❌ 마커 인터페이스(멤버가 없는 인터페이스)를 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db530-112">❌ AVOID using marker interfaces (interfaces with no members).</span></span>

 <span data-ttu-id="db530-113">클래스를 특정 특성(마커)이 있는 것으로 표시해야 하는 경우 일반적으로 인터페이스가 아닌 사용자 지정 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db530-113">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>

 <span data-ttu-id="db530-114">✔️ 인터페이스의 구현인 형식을 하나 이상 제공하세요.</span><span class="sxs-lookup"><span data-stu-id="db530-114">✔️ DO provide at least one type that is an implementation of an interface.</span></span>

 <span data-ttu-id="db530-115">그러면 인터페이스 디자인의 유효성을 검사하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db530-115">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="db530-116">예를 들어 <xref:System.Collections.Generic.List%601>는 <xref:System.Collections.Generic.IList%601> 인터페이스의 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="db530-116">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>

 <span data-ttu-id="db530-117">✔️ 정의하는 각 인터페이스를 사용하는 하나 이상의 API를 제공하세요(인터페이스를 매개 변수로 사용하는 메서드 또는 인터페이스로 형식화된 속성).</span><span class="sxs-lookup"><span data-stu-id="db530-117">✔️ DO provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>

 <span data-ttu-id="db530-118">그러면 인터페이스 디자인의 유효성을 검사하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="db530-118">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="db530-119">예를 들어 <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>는 <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> 인터페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="db530-119">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>

 <span data-ttu-id="db530-120">❌ 이전에 제공된 인터페이스에 멤버를 추가하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="db530-120">❌ DO NOT add members to an interface that has previously shipped.</span></span>

 <span data-ttu-id="db530-121">그러면 인터페이스의 구현이 중단됩니다.</span><span class="sxs-lookup"><span data-stu-id="db530-121">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="db530-122">버전 관리 문제를 방지하려면 새 인터페이스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db530-122">You should create a new interface in order to avoid versioning problems.</span></span>

 <span data-ttu-id="db530-123">이러한 지침에 설명된 경우를 제외하고 관리 코드 재사용 가능 라이브러리를 디자인할 때는 일반적으로 인터페이스가 아닌 클래스를 선택해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="db530-123">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>

 <span data-ttu-id="db530-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="db530-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="db530-125">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="db530-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="db530-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="db530-126">See also</span></span>

- [<span data-ttu-id="db530-127">형식 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="db530-127">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="db530-128">프레임워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="db530-128">Framework Design Guidelines</span></span>](index.md)
