---
title: 클래스, 구조체 및 인터페이스의 이름
description: .NET 라이브러리를 확장 하 고 상호 작용 하는 라이브러리를 디자인 하기 위한 지침의 일부로 클래스, 구조체 및 인터페이스의 이름을 지정 하는 데 이러한 지침을 사용 합니다.
ms.date: 10/22/2008
helpviewer_keywords:
- type names, guidelines
- classes [.NET Framework], names
- enumerations [.NET Framework], names
- names [.NET Framework], interfaces
- common type names
- names [.NET Framework], type names
- names [.NET Framework], classes
- interfaces [.NET Framework], names
- generic type parameters
ms.assetid: 87a4b0da-ed64-43b1-ac43-968576c444ce
ms.openlocfilehash: 49bafda0d5c362fa02313c5304436069d054cfd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706517"
---
# <a name="names-of-classes-structs-and-interfaces"></a><span data-ttu-id="03fcf-103">클래스, 구조체 및 인터페이스의 이름</span><span class="sxs-lookup"><span data-stu-id="03fcf-103">Names of Classes, Structs, and Interfaces</span></span>

<span data-ttu-id="03fcf-104">다음 명명 지침은 일반적인 형식 이름 지정에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-104">The naming guidelines that follow apply to general type naming.</span></span>

 <span data-ttu-id="03fcf-105">✔️는 명사 또는 명사구를 사용 하 여 클래스와 구조체의 이름을 지정할 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-105">✔️ DO name classes and structs with nouns or noun phrases, using PascalCasing.</span></span>

 <span data-ttu-id="03fcf-106">이는 동사 구와 이름이 지정 된 메서드의 형식 이름을 구분 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-106">This distinguishes type names from methods, which are named with verb phrases.</span></span>

 <span data-ttu-id="03fcf-107">✔️는 형용사 구를 사용 하 여 인터페이스를 만들거나 명사 또는 명사구를 사용 하는 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-107">✔️ DO name interfaces with adjective phrases, or occasionally with nouns or noun phrases.</span></span>

 <span data-ttu-id="03fcf-108">명사 및 명사구는 거의 사용 되지 않으며 형식이 인터페이스가 아닌 추상 클래스 여야 함을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-108">Nouns and noun phrases should be used rarely and they might indicate that the type should be an abstract class, and not an interface.</span></span>

 <span data-ttu-id="03fcf-109">❌ 클래스 이름을 접두사로 지정 하지 마십시오 (예: "C").</span><span class="sxs-lookup"><span data-stu-id="03fcf-109">❌ DO NOT give class names a prefix (e.g., "C").</span></span>

 <span data-ttu-id="03fcf-110">기본 클래스의 이름을 사용 하 여 파생 클래스의 이름을 종료 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="03fcf-110">✔️ CONSIDER ending the name of derived classes with the name of the base class.</span></span>

 <span data-ttu-id="03fcf-111">이는 매우 읽기 쉬우며 관계를 명확 하 게 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-111">This is very readable and explains the relationship clearly.</span></span> <span data-ttu-id="03fcf-112">코드에서이에 대 한 몇 가지 예는 이며 일종의, `ArgumentOutOfRangeException` `Exception` 및 `SerializableAttribute` 입니다. `Attribute`</span><span class="sxs-lookup"><span data-stu-id="03fcf-112">Some examples of this in code are: `ArgumentOutOfRangeException`, which is a kind of `Exception`, and `SerializableAttribute`, which is a kind of `Attribute`.</span></span> <span data-ttu-id="03fcf-113">그러나이 지침을 적용할 때 적절 한 판단을 사용 하는 것이 중요 합니다. 예를 들어 `Button` 클래스는 일종의 이벤트 이지만 `Control` `Control` 이름에는 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-113">However, it is important to use reasonable judgment in applying this guideline; for example, the `Button` class is a kind of `Control` event, although `Control` doesn’t appear in its name.</span></span>

 <span data-ttu-id="03fcf-114">인터페이스 이름 앞에 문자 I를 사용 하 여 형식이 인터페이스 임을 나타내려면 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-114">✔️ DO prefix interface names with the letter I, to indicate that the type is an interface.</span></span>

 <span data-ttu-id="03fcf-115">예를 들어 `IComponent` (설명 명사), `ICustomAttributeProvider` (명사 구) 및 `IPersistable` (형용사)는 적절 한 인터페이스 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-115">For example, `IComponent` (descriptive noun), `ICustomAttributeProvider` (noun phrase), and `IPersistable` (adjective) are appropriate interface names.</span></span> <span data-ttu-id="03fcf-116">다른 형식 이름과 마찬가지로 약어를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="03fcf-116">As with other type names, avoid abbreviations.</span></span>

 <span data-ttu-id="03fcf-117">클래스가 인터페이스의 표준 구현인 클래스-인터페이스 쌍을 정의 하는 경우 인터페이스 이름에서 "I" 접두사에 의해서만 이름이 다른 지 확인 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-117">✔️ DO ensure that the names differ only by the "I" prefix on the interface name when you are defining a class–interface pair where the class is a standard implementation of the interface.</span></span>

## <a name="names-of-generic-type-parameters"></a><span data-ttu-id="03fcf-118">제네릭 형식 매개 변수의 이름</span><span class="sxs-lookup"><span data-stu-id="03fcf-118">Names of Generic Type Parameters</span></span>

 <span data-ttu-id="03fcf-119">제네릭을 .NET Framework 2.0에 추가 했습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-119">Generics were added to .NET Framework 2.0.</span></span> <span data-ttu-id="03fcf-120">이 기능에는 *형식 매개 변수* 라는 새로운 종류의 식별자가 도입 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-120">The feature introduced a new kind of identifier called *type parameter*.</span></span>

 <span data-ttu-id="03fcf-121">단일 문자 이름이 완전히 설명이 없는 경우 설명이 포함 된 이름을 사용 하 여 제네릭 형식 매개 변수 이름을 지정 하 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-121">✔️ DO name generic type parameters with descriptive names unless a single-letter name is completely self-explanatory and a descriptive name would not add value.</span></span>

 <span data-ttu-id="03fcf-122">✔️ 하나의 `T` 단일 문자 형식 매개 변수를 사용 하는 형식에 대 한 형식 매개 변수 이름으로를 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-122">✔️ CONSIDER using `T` as the type parameter name for types with one single-letter type parameter.</span></span>

```csharp
public int IComparer<T> { ... }
public delegate bool Predicate<T>(T item);
public struct Nullable<T> where T:struct { ... }
```

 <span data-ttu-id="03fcf-123">을 사용 하 여 설명 형식 매개 변수 이름에 접두사를 ✔️ `T` 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-123">✔️ DO prefix descriptive type parameter names with `T`.</span></span>

```csharp
public interface ISessionChannel<TSession> where TSession : ISession {
    TSession Session { get; }
}
```

 <span data-ttu-id="03fcf-124">매개 변수 이름에서 형식 매개 변수에 적용 되는 제약 조건을 표시 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="03fcf-124">✔️ CONSIDER indicating constraints placed on a type parameter in the name of the parameter.</span></span>

 <span data-ttu-id="03fcf-125">예를 들어로 제한 된 매개 변수를 `ISession` 호출할 수 있습니다 `TSession` .</span><span class="sxs-lookup"><span data-stu-id="03fcf-125">For example, a parameter constrained to `ISession` might be called `TSession`.</span></span>

## <a name="names-of-common-types"></a><span data-ttu-id="03fcf-126">공용 형식의 이름</span><span class="sxs-lookup"><span data-stu-id="03fcf-126">Names of Common Types</span></span>

 <span data-ttu-id="03fcf-127">✔️에서 파생 된 형식을 명명 하거나 특정 .NET Framework 형식을 구현할 때 다음 표에 설명 된 지침을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-127">✔️ DO follow the guidelines described in the following table when naming types derived from or implementing certain .NET Framework types.</span></span>

|<span data-ttu-id="03fcf-128">Base Type</span><span class="sxs-lookup"><span data-stu-id="03fcf-128">Base Type</span></span>|<span data-ttu-id="03fcf-129">파생/구현 형식 지침</span><span class="sxs-lookup"><span data-stu-id="03fcf-129">Derived/Implementing Type Guideline</span></span>|
|---------------|------------------------------------------|
|`System.Attribute`|<span data-ttu-id="03fcf-130">✔️ 사용자 지정 특성 클래스의 이름에 "Attribute" 접미사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-130">✔️ DO add the suffix "Attribute" to names of custom attribute classes.</span></span>|
|`System.Delegate`|<span data-ttu-id="03fcf-131">✔️ 이벤트에 사용 되는 대리자 이름에 "EventHandler" 접미사를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-131">✔️ DO add the suffix "EventHandler" to names of delegates that are used in events.</span></span><br /><br /> <span data-ttu-id="03fcf-132">이벤트 처리기로 사용 된 대리자 이외의 이름에 "Callback" 접미사를 추가 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-132">✔️ DO add the suffix "Callback" to names of delegates other than those used as event handlers.</span></span><br /><br /> <span data-ttu-id="03fcf-133">❌ "Delegate" 접미사를 대리자에 추가 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="03fcf-133">❌ DO NOT add the suffix "Delegate" to a delegate.</span></span>|
|`System.EventArgs`|<span data-ttu-id="03fcf-134">"EventArgs" 접미사를 추가 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-134">✔️ DO add the suffix "EventArgs."</span></span>|
|`System.Enum`|<span data-ttu-id="03fcf-135">❌ 이 클래스에서 파생 되지 않습니다. 대신 해당 언어로 지원 되는 키워드를 사용 합니다. 예를 들어 c #에서는 키워드를 사용 `enum` 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-135">❌ DO NOT derive from this class; use the keyword supported by your language instead; for example, in C#, use the `enum` keyword.</span></span><br /><br /> <span data-ttu-id="03fcf-136">❌ "Enum" 또는 "Flag" 접미사는 추가 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="03fcf-136">❌ DO NOT add the suffix "Enum" or "Flag."</span></span>|
|`System.Exception`|<span data-ttu-id="03fcf-137">✔️ 접미사 "Exception"을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-137">✔️ DO add the suffix "Exception."</span></span>|
|`IDictionary` <br /> `IDictionary<TKey,TValue>`|<span data-ttu-id="03fcf-138">✔️ 접미사 "Dictionary"를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-138">✔️ DO add the suffix "Dictionary."</span></span> <span data-ttu-id="03fcf-139">는 `IDictionary` 특정 유형의 컬렉션 이지만이 지침은 다음과 같은 보다 일반적인 컬렉션 지침 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-139">Note that `IDictionary` is a specific type of collection, but this guideline takes precedence over the more general collections guideline that follows.</span></span>|
|`IEnumerable` <br /> `ICollection` <br /> `IList` <br /> `IEnumerable<T>` <br /> `ICollection<T>` <br /> `IList<T>`|<span data-ttu-id="03fcf-140">"Collection" 접미사를 추가 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-140">✔️ DO add the suffix "Collection."</span></span>|
|`System.IO.Stream`|<span data-ttu-id="03fcf-141">접미사 "Stream"을 추가 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-141">✔️ DO add the suffix "Stream."</span></span>|
|`CodeAccessPermission IPermission`|<span data-ttu-id="03fcf-142">✔️ 접미사 "Permission"을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-142">✔️ DO add the suffix "Permission."</span></span>|

## <a name="naming-enumerations"></a><span data-ttu-id="03fcf-143">열거형 이름 지정</span><span class="sxs-lookup"><span data-stu-id="03fcf-143">Naming Enumerations</span></span>

 <span data-ttu-id="03fcf-144">일반적으로 열거형 형식 (열거형이 라고도 함)의 이름은 표준 형식 명명 규칙을 따라야 합니다 (예를 들어).</span><span class="sxs-lookup"><span data-stu-id="03fcf-144">Names of enumeration types (also called enums) in general should follow the standard type-naming rules (PascalCasing, etc.).</span></span> <span data-ttu-id="03fcf-145">그러나 열거형에는 특별히 적용 되는 추가 지침이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-145">However, there are additional guidelines that apply specifically to enums.</span></span>

 <span data-ttu-id="03fcf-146">값이 비트 필드인 경우를 제외 하 고는 열거형에 대해 단 수 형식 이름을 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-146">✔️ DO use a singular type name for an enumeration unless its values are bit fields.</span></span>

 <span data-ttu-id="03fcf-147">비트 필드를 값으로 사용 하는 열거형 (플래그 열거형이 라고도 함)에는 복수형 형식 이름을 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="03fcf-147">✔️ DO use a plural type name for an enumeration with bit fields as values, also called flags enum.</span></span>

 <span data-ttu-id="03fcf-148">❌ 열거형 형식 이름에 "Enum" 접미사를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="03fcf-148">❌ DO NOT use an "Enum" suffix in enum type names.</span></span>

 <span data-ttu-id="03fcf-149">❌ 열거형 형식 이름에는 "Flag" 또는 "Flags" 접미사를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="03fcf-149">❌ DO NOT use "Flag" or "Flags" suffixes in enum type names.</span></span>

 <span data-ttu-id="03fcf-150">❌ 열거형 값 이름에 접두사를 사용 하지 마십시오 (예: ADO 열거형의 경우 "ad", 서식 있는 텍스트 열거형의 경우 "rtf").</span><span class="sxs-lookup"><span data-stu-id="03fcf-150">❌ DO NOT use a prefix on enumeration value names (e.g., "ad" for ADO enums, "rtf" for rich text enums, etc.).</span></span>

 <span data-ttu-id="03fcf-151">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="03fcf-151">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="03fcf-152">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="03fcf-152">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="03fcf-153">참조</span><span class="sxs-lookup"><span data-stu-id="03fcf-153">See also</span></span>

- [<span data-ttu-id="03fcf-154">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="03fcf-154">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="03fcf-155">명명 지침</span><span class="sxs-lookup"><span data-stu-id="03fcf-155">Naming Guidelines</span></span>](naming-guidelines.md)
