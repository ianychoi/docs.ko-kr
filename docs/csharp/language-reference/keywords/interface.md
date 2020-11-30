---
description: :::no-loc text=interface:::(C# 참조)
title: interface - C# 참조
ms.date: 01/17/2020
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 24f95e828522f467c519c0c8a7ba9410aa97af4e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89134590"
---
# <a name="no-loc-textinterface-c-reference"></a><span data-ttu-id="f0085-103">:::no-loc text="interface":::(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="f0085-103">:::no-loc text="interface"::: (C# Reference)</span></span>

<span data-ttu-id="f0085-104">인터페이스는 계약을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-104">An interface defines a contract.</span></span> <span data-ttu-id="f0085-105">해당 계약을 구현 하는 [`class`](class.md) 또는 [`struct`](../builtin-types/struct.md)는 인터페이스에 정의된 구성원의 구현을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-105">Any [`class`](class.md) or [`struct`](../builtin-types/struct.md) that implements that contract must provide an implementation of the members defined in the interface.</span></span> <span data-ttu-id="f0085-106">C# 8.0부터 인터페이스는 구성원에 대한 기본 구현을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-106">Beginning with C# 8.0, an interface may define a default implementation for members.</span></span> <span data-ttu-id="f0085-107">공통적인 기능에 대해 단일 구현을 제공하기 위해 [`static`](static.md) 구성원을 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-107">It may also define [`static`](static.md) members in order to provide a single implementation for common functionality.</span></span>

<span data-ttu-id="f0085-108">다음 예제에서 `ImplementationClass` 클래스는 매개 변수가 없고 `void`를 반환하는 `SampleMethod`라는 메서드를 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-108">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="f0085-109">자세한 내용과 예제는 [인터페이스](../../programming-guide/interfaces/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0085-109">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="f0085-110">예제</span><span class="sxs-lookup"><span data-stu-id="f0085-110">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="f0085-111">인터페이스는 네임스페이스 또는 클래스의 구성원일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-111">An interface can be a member of a namespace or a class.</span></span> <span data-ttu-id="f0085-112">인터페이스 선언에는 다음 구성원의 선언(구현이 없는 서명)을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-112">An interface declaration can contain declarations (signatures without any implementation) of the following members:</span></span>

- [<span data-ttu-id="f0085-113">메서드</span><span class="sxs-lookup"><span data-stu-id="f0085-113">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="f0085-114">속성</span><span class="sxs-lookup"><span data-stu-id="f0085-114">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="f0085-115">인덱서</span><span class="sxs-lookup"><span data-stu-id="f0085-115">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="f0085-116">이벤트</span><span class="sxs-lookup"><span data-stu-id="f0085-116">Events</span></span>](event.md)

<span data-ttu-id="f0085-117">이러한 앞의 구성원 선언에는 일반적으로 본문이 포함되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-117">These preceding member declarations typically do not contain a body.</span></span> <span data-ttu-id="f0085-118">C# 8.0부터는 인터페이스 구성원이 본문을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-118">Beginning with C# 8.0, an interface member may declare a body.</span></span> <span data-ttu-id="f0085-119">이를 *기본 구현* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-119">This is called a *default implementation*.</span></span> <span data-ttu-id="f0085-120">본문이 있는 구성원은 인터페이스가 재정의 구현을 제공하지 않는 클래스 및 구조체에 대해 "기본" 구현을 제공하도록 허용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-120">Members with bodies permit the interface to provide a "default" implementation for classes and structs that don't provide an overriding implementation.</span></span> <span data-ttu-id="f0085-121">또한 C# 8.0부터 인터페이스에는 다음이 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-121">In addition, beginning with C# 8.0, an interface may include:</span></span>

- [<span data-ttu-id="f0085-122">상수</span><span class="sxs-lookup"><span data-stu-id="f0085-122">Constants</span></span>](const.md)
- [<span data-ttu-id="f0085-123">연산자</span><span class="sxs-lookup"><span data-stu-id="f0085-123">Operators</span></span>](../operators/operator-overloading.md)
- <span data-ttu-id="f0085-124">[정적 생성자](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span><span class="sxs-lookup"><span data-stu-id="f0085-124">[Static constructor](../../programming-guide/classes-and-structs/constructors.md#static-constructors).</span></span>
- [<span data-ttu-id="f0085-125">중첩 형식</span><span class="sxs-lookup"><span data-stu-id="f0085-125">Nested types</span></span>](../../programming-guide/classes-and-structs/nested-types.md)
- [<span data-ttu-id="f0085-126">정적 필드, 메서드, 속성, 인덱서 및 이벤트</span><span class="sxs-lookup"><span data-stu-id="f0085-126">Static fields, methods, properties, indexers, and events</span></span>](static.md)
- <span data-ttu-id="f0085-127">명시적 인터페이스 구현 구문을 사용한 구성원 선언</span><span class="sxs-lookup"><span data-stu-id="f0085-127">Member declarations using the explicit interface implementation syntax.</span></span>
- <span data-ttu-id="f0085-128">명시적 액세스 한정자(기본 액세스는 [`public`](access-modifiers.md))</span><span class="sxs-lookup"><span data-stu-id="f0085-128">Explicit access modifiers (the default access is [`public`](access-modifiers.md)).</span></span>

<span data-ttu-id="f0085-129">인터페이스에는 인스턴스 상태를 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-129">Interfaces may not contain instance state.</span></span> <span data-ttu-id="f0085-130">이제 정적 필드가 허용되지만 인터페이스에서는 인스턴스 필드가 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-130">While static fields are now permitted, instance fields are not permitted in interfaces.</span></span> <span data-ttu-id="f0085-131">[인스턴스 자동 속성](../../programming-guide/classes-and-structs/auto-implemented-properties.md)은 숨겨진 필드를 암시적으로 선언하므로 인터페이스에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-131">[Instance auto-properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) are not supported in interfaces, as they would implicitly declare a hidden field.</span></span> <span data-ttu-id="f0085-132">이 규칙은 속성 선언에 미묘한 영향을 미칩니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-132">This rule has a subtle effect on property declarations.</span></span> <span data-ttu-id="f0085-133">인터페이스 선언에서 다음 코드는 `class` 또는 `struct`에서와 같이 자동으로 구현된 속성을 선언하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-133">In an interface declaration, the following code does not declare an auto-implemented property as it does in a `class` or `struct`.</span></span> <span data-ttu-id="f0085-134">대신, 기본 구현은 없지만 인터페이스를 구현하는 형식에서 구현되어야 하는 속성을 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-134">Instead, it declares a property that doesn't have a default implementation but must be implemented in any type that implements the interface:</span></span>

```csharp
public interface INamed
{
  public string Name {get; set;}
}
```

<span data-ttu-id="f0085-135">인터페이스는 하나 이상의 기본 인터페이스에서 상속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-135">An interface can inherit from one or more base interfaces.</span></span> <span data-ttu-id="f0085-136">인터페이스가 기본 인터페이스에 구현된 [메서드를 재정의](override.md)하는 경우 [명시적 인터페이스 구현](../../programming-guide/interfaces/explicit-interface-implementation.md) 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-136">When an interface [overrides a method](override.md) implemented in a base interface, it must use the [explicit interface implementation](../../programming-guide/interfaces/explicit-interface-implementation.md) syntax.</span></span>

<span data-ttu-id="f0085-137">기본 형식 목록에 기본 클래스 및 인터페이스가 포함된 경우 기본 클래스가 목록의 첫 번째 항목이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-137">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="f0085-138">인터페이스를 구현하는 클래스는 해당 인터페이스의 멤버를 명시적으로 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-138">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="f0085-139">명시적으로 구현된 멤버는 클래스 인스턴스를 통해 액세스할 수 없고 인터페이스 인스턴스를 통해서만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-139">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span> <span data-ttu-id="f0085-140">또한 기본 인터페이스 구성원은 인터페이스의 인스턴스를 통해서만 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-140">In addition, default interface members can only be accessed through an instance of the interface.</span></span>

<span data-ttu-id="f0085-141">명시적 인터페이스 구현에 대한 자세한 내용은 [명시적 인터페이스 구현](../../programming-guide/interfaces/explicit-interface-implementation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0085-141">For more information about explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="f0085-142">예제</span><span class="sxs-lookup"><span data-stu-id="f0085-142">Example</span></span>

<span data-ttu-id="f0085-143">다음 예제에서는 인터페이스의 구현 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-143">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="f0085-144">이 예제에서 인터페이스에는 속성 선언이 포함되어 있고, 클래스에는 구현이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-144">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="f0085-145">`IPoint`를 구현하는 클래스의 모든 인스턴스에는 정수 속성 `x` 및 `y`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f0085-145">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="f0085-146">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="f0085-146">C# language specification</span></span>

<span data-ttu-id="f0085-147">자세한 내용은 [C# 언어 사양](~/_csharplang/spec/introduction.md)의 [인터페이스](~/_csharplang/spec/interfaces.md) 섹션 및 [기본 인터페이스 구성원 - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)의 기능 사양을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f0085-147">For more information, see the [Interfaces](~/_csharplang/spec/interfaces.md) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the feature specification for [Default interface members - C# 8.0](~/_csharplang/proposals/csharp-8.0/default-interface-methods.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="f0085-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f0085-148">See also</span></span>

- [<span data-ttu-id="f0085-149">C# 참조</span><span class="sxs-lookup"><span data-stu-id="f0085-149">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f0085-150">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="f0085-150">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f0085-151">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="f0085-151">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f0085-152">참조 형식</span><span class="sxs-lookup"><span data-stu-id="f0085-152">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="f0085-153">인터페이스</span><span class="sxs-lookup"><span data-stu-id="f0085-153">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="f0085-154">속성 사용</span><span class="sxs-lookup"><span data-stu-id="f0085-154">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="f0085-155">인덱서 사용</span><span class="sxs-lookup"><span data-stu-id="f0085-155">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
