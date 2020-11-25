---
title: 확장 메서드
ms.date: 10/22/2008
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
ms.openlocfilehash: 02a421c9a4b73c779474a392e77104d4ccfbb109
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734714"
---
# <a name="extension-methods"></a><span data-ttu-id="fd74f-102">확장 메서드</span><span class="sxs-lookup"><span data-stu-id="fd74f-102">Extension Methods</span></span>

<span data-ttu-id="fd74f-103">확장 메서드는 인스턴스 메서드 호출 구문을 사용 하 여 정적 메서드를 호출할 수 있도록 하는 언어 기능입니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="fd74f-104">이러한 메서드는 메서드가 작동 하는 인스턴스를 나타내는 매개 변수를 하나 이상 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>

 <span data-ttu-id="fd74f-105">이러한 확장 메서드를 정의 하는 클래스를 "스폰서" 클래스 라고 하며 정적으로 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="fd74f-106">확장 메서드를 사용 하려면 스폰서 클래스를 정의 하는 네임 스페이스를 가져와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>

 <span data-ttu-id="fd74f-107">❌ 특히 소유 하지 않는 형식에 대 한 확장 메서드를 정의 하는 frivolously을 피합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-107">❌ AVOID frivolously defining extension methods, especially on types you don't own.</span></span>

 <span data-ttu-id="fd74f-108">형식의 소스 코드를 소유 하는 경우 대신 일반 인스턴스 메서드를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="fd74f-109">소유 하 고 있지 않은 경우에는 메서드를 추가 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-109">If you don't own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="fd74f-110">확장 메서드를 자유롭게 사용 하면 이러한 메서드를 사용 하도록 설계 되지 않은 복잡 한 형식의 Api가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>

 <span data-ttu-id="fd74f-111">다음 시나리오에서는 확장 메서드를 사용 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="fd74f-111">✔️ CONSIDER using extension methods in any of the following scenarios:</span></span>

- <span data-ttu-id="fd74f-112">인터페이스의 모든 구현과 관련 된 도우미 기능을 제공 하려는 경우 핵심 인터페이스를 기준으로 기능을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="fd74f-113">구체적 구현은 인터페이스에 할당할 수 없기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="fd74f-114">예를 들어 `LINQ to Objects` 연산자는 모든 형식에 대해 확장 메서드로 구현 됩니다 <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="fd74f-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="fd74f-115">따라서 모든 `IEnumerable<>` 구현은 자동으로 LINQ를 사용 하도록 설정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>

- <span data-ttu-id="fd74f-116">인스턴스 메서드가 일부 형식에 대 한 종속성을 도입할 때 이러한 종속성은 종속성 관리 규칙을 중단 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="fd74f-117">예를 들어에서로의 <xref:System.String> 종속성 <xref:System.Uri?displayProperty=nameWithType> 이 바람직하지 않을 수 있으므로,이를 반환 하는 `String.ToUri()` 인스턴스 메서드는 `System.Uri` 종속성 관리 관점에서 잘못 된 디자인입니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="fd74f-118">을 반환 하는 정적 확장 메서드는 `Uri.ToUri(this string str)` `System.Uri` 훨씬 더 나은 디자인입니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>

 <span data-ttu-id="fd74f-119">❌ 에 확장 메서드를 정의 하지 마십시오 <xref:System.Object?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fd74f-119">❌ AVOID defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="fd74f-120">VB 사용자는 확장 메서드 구문을 사용 하 여 개체 참조에서 이러한 메서드를 호출할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="fd74f-121">VB에서 참조를 개체로 선언 하면 런타임에 바인딩된 (실제 멤버는 런타임에 결정 됨), 확장명 메서드에 대 한 바인딩은 컴파일 시간 (초기 바인딩)에서 결정 되기 때문에 이러한 메서드 호출은 지원 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>

 <span data-ttu-id="fd74f-122">이 지침은 동일한 바인딩 동작이 있는 다른 언어나 확장 메서드가 지원 되지 않는 경우에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>

 <span data-ttu-id="fd74f-123">❌ 인터페이스에 메서드를 추가 하거나 종속성을 관리 하는 경우를 제외 하 고 확장 형식과 동일한 네임 스페이스에 확장 메서드를 배치 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fd74f-123">❌ DO NOT put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>

 <span data-ttu-id="fd74f-124">❌ 서로 다른 네임 스페이스에 있는 경우에도 동일한 서명으로 두 개 이상의 확장 메서드를 정의 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fd74f-124">❌ AVOID defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>

 <span data-ttu-id="fd74f-125">형식이 인터페이스인 경우 확장 형식과 동일한 네임 스페이스에 확장 메서드를 정의 하는 것이 좋습니다. 대부분의 경우 또는 모든 경우에 확장 메서드를 사용 하려는 경우에 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-125">✔️ CONSIDER defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>

 <span data-ttu-id="fd74f-126">❌ 일반적으로 다른 기능과 연결 된 네임 스페이스의 기능을 구현 하는 확장 메서드를 정의 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="fd74f-126">❌ DO NOT define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="fd74f-127">대신 자신이 속한 기능과 연결 된 네임 스페이스에서 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>

 <span data-ttu-id="fd74f-128">❌ 확장 메서드 (예: "확장")에 전용으로 사용 되는 네임 스페이스의 일반적인 이름을 지정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="fd74f-128">❌ AVOID generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="fd74f-129">대신 설명이 포함 된 이름 (예: "라우팅")을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="fd74f-129">Use a descriptive name (e.g., "Routing") instead.</span></span>

 <span data-ttu-id="fd74f-130">*&copy;2005 부분, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="fd74f-130">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="fd74f-131">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="fd74f-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="fd74f-132">참조</span><span class="sxs-lookup"><span data-stu-id="fd74f-132">See also</span></span>

- [<span data-ttu-id="fd74f-133">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="fd74f-133">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="fd74f-134">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="fd74f-134">Framework Design Guidelines</span></span>](index.md)
