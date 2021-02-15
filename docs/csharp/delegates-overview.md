---
title: 대리자 소개
description: 기본 개념을 소개하고 대리자에 대한 언어 디자인 목표를 설명하는 이 개요 문서에서 대리자에 대해 알아봅니다.
ms.date: 02/02/2021
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 72086301a6dd0552ab25baf732978802ad62669b
ms.sourcegitcommit: 4df8e005c074ceb1f978f007b222fe253be2baf3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99548346"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="7cc6a-103">대리자 소개</span><span class="sxs-lookup"><span data-stu-id="7cc6a-103">Introduction to Delegates</span></span>

<span data-ttu-id="7cc6a-104">대리자는 .NET에서 *런타임에 바인딩* 메커니즘을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="7cc6a-105">런타임에 바인딩은 호출자가 알고리즘의 일부를 구현하는 하나 이상의 메서드도 제공하는 알고리즘을 만든다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="7cc6a-106">예를 들어 천문학 애플리케이션에서 별 목록을 정렬한다는 가정해 보세요.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="7cc6a-107">이러한 별은 지구로부터의 거리, 별의 크기, 인식된 밝기 등에 따라 정렬할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="7cc6a-108">모든 경우에 Sort() 메서드는 기본적으로 동일한 작업을 수행합니다. 즉, 몇 가지 비교를 통해 목록의 항목을 정렬합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="7cc6a-109">별 두 개를 비교하는 코드는 각 정렬 순서마다 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="7cc6a-110">이러한 종류의 솔루션이 반세기 동안 소프트웨어에서 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="7cc6a-111">C# 언어 대리자 개념은 최고 수준의 언어 지원 및 해당 개념 관련 형식 안정성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="7cc6a-112">이 시리즈의 뒷부분에서 살펴보겠지만 이러한 알고리즘에 대해 작성하는 C# 코드는 형식이 안전하며 언어 규칙 및 컴파일러를 사용하여 형식이 인수 및 반환 형식과 일치하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and uses the language rules and the compiler to ensure that the types match for arguments and return types.</span></span>

<span data-ttu-id="7cc6a-113">[함수 포인터](~/_csharplang/proposals/csharp-9.0/function-pointers.md)는 호출 규칙을 더욱 세부적으로 제어해야 하는 유사한 시나리오용으로 C# 9에 추가되었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-113">[Function pointers](~/_csharplang/proposals/csharp-9.0/function-pointers.md) were added to C# 9 for similar scenarios, where you need more control over the calling convention.</span></span> <span data-ttu-id="7cc6a-114">대리자와 연결된 코드는 대리자 형식에 추가된 가상 메서드를 사용하여 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-114">The code associated with a delegate is invoked using a virtual method added to a delegate type.</span></span> <span data-ttu-id="7cc6a-115">함수 포인터를 사용하여 다른 규칙을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-115">Using function pointers, you can specify different conventions.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="7cc6a-116">대리자의 언어 디자인 목표</span><span class="sxs-lookup"><span data-stu-id="7cc6a-116">Language Design Goals for Delegates</span></span>

<span data-ttu-id="7cc6a-117">언어 디자이너는 결국 대리자가 된 기능에 대해 여러 가지 목표를 열거했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-117">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="7cc6a-118">팀은 런타임에 바인딩 알고리즘에 사용할 수 있는 공용 언어 구문을 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-118">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="7cc6a-119">대리자를 통해 개발자는 하나의 개념을 익히고 여러 가지 다양한 소프트웨어 문제에서 동일한 개념을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-119">Delegates enable developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="7cc6a-120">두 번째로 팀은 단일 및 멀티캐스트 메서드 호출을 모두 지원하기를 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-120">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="7cc6a-121">(멀티캐스트 대리자는 여러 메서드 호출을 함께 연결하는 대리자입니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-121">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="7cc6a-122">예제는 [이 시리즈의 뒷부분](delegate-class.md)에서 확인할 수 있습니다.)</span><span class="sxs-lookup"><span data-stu-id="7cc6a-122">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="7cc6a-123">팀은 개발자가 모든 C# 구문에서 기대하는 동일한 형식 안전성을 대리자가 지원하기를 원했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-123">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="7cc6a-124">마지막으로 팀은 이벤트 패턴이 대리자나 지연 바인딩 알고리즘이 매우 유용한 하나의 특정 패턴임을 인식했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-124">Finally, the team recognized an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="7cc6a-125">팀은 대리자에 대한 코드가 .NET 이벤트 패턴의 기반을 제공할 수 있도록 하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-125">The team wanted to ensure the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="7cc6a-126">이러한 모든 작업의 결과가 C# 및 .NET의 대리자와 이벤트 지원이었습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-126">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="7cc6a-127">이 섹션의 나머지 문서에서는 대리자를 사용하여 작업할 때 사용되는 언어 기능, 라이브러리 지원 및 관용구에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-127">The remaining articles in this section will cover language features, library support, and common idioms used when you work with delegates.</span></span>

<span data-ttu-id="7cc6a-128">`delegate` 키워드와 이 키워드에서 생성하는 코드에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-128">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="7cc6a-129">`System.Delegate` 클래스의 기능 및 해당 기능을 사용하는 방법에 대해서도 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-129">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="7cc6a-130">형식이 안전한 대리자를 만드는 방법 및 대리자를 통해 호출할 수 있는 메서드를 만드는 방법에 대해 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-130">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="7cc6a-131">또한 람다 식을 사용하여 대리자 및 이벤트로 작업하는 방법을 알아봅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-131">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="7cc6a-132">대리자가 LINQ 구성 요소 중 하나가 되는 위치를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-132">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="7cc6a-133">어떻게 대리자가 .NET 이벤트 패턴의 기반이 되는지와 어떻게 다른지도 살펴봅니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-133">You'll learn how delegates are the basis for the .NET event pattern, and how they're different.</span></span>

<span data-ttu-id="7cc6a-134">이제 시작해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7cc6a-134">Let's get started.</span></span>

[<span data-ttu-id="7cc6a-135">다음</span><span class="sxs-lookup"><span data-stu-id="7cc6a-135">Next</span></span>](delegate-class.md)
