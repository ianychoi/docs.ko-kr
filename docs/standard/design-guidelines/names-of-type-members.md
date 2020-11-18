---
title: 형식 멤버의 이름
description: 메서드, 속성, 이벤트 및 필드와 같은 .NET의 형식 멤버를 명명 하는 방법에 대 한 지침을 알아봅니다.
ms.date: 10/22/2008
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
ms.openlocfilehash: 85f3137b4a8d75de92b12d6535415743395db890
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820915"
---
# <a name="names-of-type-members"></a><span data-ttu-id="3f22d-103">형식 멤버의 이름</span><span class="sxs-lookup"><span data-stu-id="3f22d-103">Names of Type Members</span></span>
<span data-ttu-id="3f22d-104">형식은 메서드, 속성, 이벤트, 생성자 및 필드 등의 멤버로 이루어집니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-104">Types are made of members: methods, properties, events, constructors, and fields.</span></span> <span data-ttu-id="3f22d-105">다음 섹션에서는 형식 멤버 이름 지정에 대한 지침을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-105">The following sections describe guidelines for naming type members.</span></span>

## <a name="names-of-methods"></a><span data-ttu-id="3f22d-106">메서드 이름</span><span class="sxs-lookup"><span data-stu-id="3f22d-106">Names of Methods</span></span>
 <span data-ttu-id="3f22d-107">메서드가 작업을 수행하는 수단이기 때문에 디자인 지침에서는 메서드 이름이 동사 또는 동사구여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-107">Because methods are the means of taking action, the design guidelines require that method names be verbs or verb phrases.</span></span> <span data-ttu-id="3f22d-108">또한 이 지침을 따르면 명사 또는 형용사구인 속성 및 형식 이름과 메서드 이름을 구분할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-108">Following this guideline also serves to distinguish method names from property and type names, which are noun or adjective phrases.</span></span>

 <span data-ttu-id="3f22d-109">동사 또는 동사 구의 메서드 이름을 제공 하는 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-109">✔️ DO give methods names that are verbs or verb phrases.</span></span>

```csharp
public class String {
    public int CompareTo(...);
    public string[] Split(...);
    public string Trim();
}
```

## <a name="names-of-properties"></a><span data-ttu-id="3f22d-110">속성 이름</span><span class="sxs-lookup"><span data-stu-id="3f22d-110">Names of Properties</span></span>
 <span data-ttu-id="3f22d-111">다른 멤버와 달리 속성은 명사구 또는 형용사 이름이 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-111">Unlike other members, properties should be given noun phrase or adjective names.</span></span> <span data-ttu-id="3f22d-112">속성이 데이터를 나타내기 때문에 속성 이름은 이를 반영해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-112">That is because a property refers to data, and the name of the property reflects that.</span></span> <span data-ttu-id="3f22d-113">PascalCasing은 속성 이름에 항상 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-113">PascalCasing is always used for property names.</span></span>

 <span data-ttu-id="3f22d-114">명사, 명사구 또는 형용사를 사용 하 여 이름 속성을 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-114">✔️ DO name properties using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="3f22d-115">❌ 다음 예제와 같이 "Get" 메서드의 이름과 일치 하는 속성이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-115">❌ DO NOT have properties that match the name of "Get" methods as in the following example:</span></span>

 <span data-ttu-id="3f22d-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span><span class="sxs-lookup"><span data-stu-id="3f22d-116">`public string TextWriter { get {...} set {...} }` `public string GetTextWriter(int value) { ... }`</span></span>

 <span data-ttu-id="3f22d-117">이 패턴은 일반적으로 속성이 실제로 메서드임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-117">This pattern typically indicates that the property should really be a method.</span></span>

 <span data-ttu-id="3f22d-118">단일 구를 사용 하는 대신 "List" 또는 "Collection"을 사용 하는 것이 아니라 컬렉션의 항목을 설명 하는 복수 구를 사용 하 여 컬렉션 속성의 이름을 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-118">✔️ DO name collection properties with a plural phrase describing the items in the collection instead of using a singular phrase followed by "List" or "Collection".</span></span>

 <span data-ttu-id="3f22d-119">찬성 문구 (대신)를 사용 하 여 부울 속성의 이름을 ✔️ `CanSeek` `CantSeek` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-119">✔️ DO name Boolean properties with an affirmative phrase (`CanSeek` instead of `CantSeek`).</span></span> <span data-ttu-id="3f22d-120">필요에 따라 부울 속성에 "Is", "Can" 또는 "Is"를 접두사로 추가 하 고 값을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-120">Optionally, you can also prefix Boolean properties with "Is", "Can", or "Has", but only where it adds value.</span></span>

 <span data-ttu-id="3f22d-121">속성에 해당 형식과 같은 이름을 지정 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="3f22d-121">✔️ CONSIDER giving a property the same name as its type.</span></span>

 <span data-ttu-id="3f22d-122">예를 들어, 다음 속성은 현재 올바르게 `Color`라는 열거형 값을 설정하므로 속성 이름은 `Color`입니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-122">For example, the following property correctly gets and sets an enum value named `Color`, so the property is named `Color`:</span></span>

```csharp
public enum Color {...}
public class Control {
    public Color Color { get {...} set {...} }
}
```

## <a name="names-of-events"></a><span data-ttu-id="3f22d-123">이벤트 이름</span><span class="sxs-lookup"><span data-stu-id="3f22d-123">Names of Events</span></span>
 <span data-ttu-id="3f22d-124">이벤트는 발생 중인 작업 또는 발생한 작업 중 하나를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-124">Events always refer to some action, either one that is happening or one that has occurred.</span></span> <span data-ttu-id="3f22d-125">따라서 메서드와 마찬가지로 이벤트는 동사를 사용하여 명명하고 동사 시제는 이벤트가 발생할 시간을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-125">Therefore, as with methods, events are named with verbs, and verb tense is used to indicate the time when the event is raised.</span></span>

 <span data-ttu-id="3f22d-126">동사 또는 동사 구를 사용 하 여 이름 이벤트를 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-126">✔️ DO name events with a verb or a verb phrase.</span></span>

 <span data-ttu-id="3f22d-127">예를 들면 `Clicked`, `Painting`, `DroppedDown` 등입니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-127">Examples include `Clicked`, `Painting`, `DroppedDown`, and so on.</span></span>

 <span data-ttu-id="3f22d-128">✔️는 현재 및 이전 시제를 사용 하 여 전후에 이벤트 이름을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-128">✔️ DO give events names with a concept of before and after, using the present and past tenses.</span></span>

 <span data-ttu-id="3f22d-129">예를 들어 창이 닫히기 전에 발생하는 닫기 이벤트는 `Closing`이라고 하고 창이 닫힌 후에 발생하는 닫기 이벤트는 `Closed`라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-129">For example, a close event that is raised before a window is closed would be called `Closing`, and one that is raised after the window is closed would be called `Closed`.</span></span>

 <span data-ttu-id="3f22d-130">❌ 사전 및 사후 이벤트를 나타내려면 "Before" 또는 "After" 접두사 또는 postfixes를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3f22d-130">❌ DO NOT use "Before" or "After" prefixes or postfixes to indicate pre- and post-events.</span></span> <span data-ttu-id="3f22d-131">위에서 설명한 대로 현재 및 과거 시제를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-131">Use present and past tenses as just described.</span></span>

 <span data-ttu-id="3f22d-132">다음 예제에 표시 된 것 처럼 "EventHandler" 접미사를 사용 하 여 이벤트 처리기 (이벤트 유형으로 사용 되는 대리자)의 이름을 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-132">✔️ DO name event handlers (delegates used as types of events) with the "EventHandler" suffix, as shown in the following example:</span></span>

 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`

 <span data-ttu-id="3f22d-133">이벤트 처리기에서 및 라는 두 매개 변수를 사용 ✔️ `sender` `e` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-133">✔️ DO use two parameters named `sender` and `e` in event handlers.</span></span>

 <span data-ttu-id="3f22d-134">보낸 사람 매개 변수는 이벤트를 발생시킨 개체를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-134">The sender parameter represents the object that raised the event.</span></span> <span data-ttu-id="3f22d-135">보낸 사람 매개 변수는 보다 구체적인 형식을 적용할 수 있더라도 일반적으로 `object` 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-135">The sender parameter is typically of type `object`, even if it is possible to employ a more specific type.</span></span>

 <span data-ttu-id="3f22d-136">"EventArgs" 접미사를 사용 하 여 이벤트 인수 클래스의 이름을 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-136">✔️ DO name event argument classes with the "EventArgs" suffix.</span></span>

## <a name="names-of-fields"></a><span data-ttu-id="3f22d-137">필드 이름</span><span class="sxs-lookup"><span data-stu-id="3f22d-137">Names of Fields</span></span>
 <span data-ttu-id="3f22d-138">필드 명명 지침은 공용 및 보호된 고정 필드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-138">The field-naming guidelines apply to static public and protected fields.</span></span> <span data-ttu-id="3f22d-139">내부 및 개인 필드는 지침에서 다루지 않고 공용 또는 보호된 인스턴스 필드는 [멤버 디자인 지침](member.md)에서 허용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-139">Internal and private fields are not covered by guidelines, and public or protected instance fields are not allowed by the [member design guidelines](member.md).</span></span>

 <span data-ttu-id="3f22d-140">필드 이름에는 대/소문자 구분을 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-140">✔️ DO use PascalCasing in field names.</span></span>

 <span data-ttu-id="3f22d-141">명사, 명사구 또는 형용사를 사용 하 여 이름 필드를 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="3f22d-141">✔️ DO name fields using a noun, noun phrase, or adjective.</span></span>

 <span data-ttu-id="3f22d-142">❌ 필드 이름에는 접두사를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3f22d-142">❌ DO NOT use a prefix for field names.</span></span>

 <span data-ttu-id="3f22d-143">예를 들어 "g_" 또는 "s_"를 사용하여 고정 필드를 나타내지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="3f22d-143">For example, do not use "g_" or "s_" to indicate static fields.</span></span>

 <span data-ttu-id="3f22d-144">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3f22d-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="3f22d-145">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="3f22d-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="3f22d-146">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3f22d-146">See also</span></span>

- [<span data-ttu-id="3f22d-147">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="3f22d-147">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="3f22d-148">명명 지침</span><span class="sxs-lookup"><span data-stu-id="3f22d-148">Naming Guidelines</span></span>](naming-guidelines.md)
