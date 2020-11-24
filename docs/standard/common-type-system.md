---
title: 공용 형식 시스템 및 공용 언어 사양
description: CTS(공용 형식 시스템) 및 CLS(공용 언어 사양)를 사용하여 .NET이 여러 언어를 지원할 수 있도록 하는 방법을 알아봅니다.
ms.date: 06/20/2016
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: e60205450e2f156407deb7be6b9c497d090b6f7b
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822882"
---
# <a name="common-type-system--common-language-specification"></a><span data-ttu-id="e13a9-103">공용 형식 시스템 및 공용 언어 사양</span><span class="sxs-lookup"><span data-stu-id="e13a9-103">Common Type System & Common Language Specification</span></span>

<span data-ttu-id="e13a9-104">두 용어는 .NET 환경에서 자유롭게 사용되지만, 실제로 .NET 구현에서 어떻게 다중 언어 개발을 사용할 수 있고 어떻게 작동하는지 이해하는 데 중요합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-104">Again, two terms that are freely used in the .NET world, they actually are crucial to understand how a .NET implementation enables multi-language development and to understand how it works.</span></span>

## <a name="common-type-system"></a><span data-ttu-id="e13a9-105">공용 형식 시스템</span><span class="sxs-lookup"><span data-stu-id="e13a9-105">Common Type System</span></span>

<span data-ttu-id="e13a9-106">먼저 .NET 구현이 _언어 독립적_ 임에 유의하세요.</span><span class="sxs-lookup"><span data-stu-id="e13a9-106">To start from the beginning, remember that a .NET implementation is _language agnostic_.</span></span> <span data-ttu-id="e13a9-107">단순히 프로그래머가 IL로 컴파일할 수 있는 모든 언어로 코드를 작성할 수 있다는 의미는 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-107">This doesn't just mean that a programmer can write their code in any language that can be compiled to IL.</span></span> <span data-ttu-id="e13a9-108">이는 프로그래머가 .NET 구현에서 사용할 수 있는 다른 언어로 작성된 코드를 조작할 수 있어야 함을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-108">It also means that they need to be able to interact with code written in other languages that are able to be used on a .NET implementation.</span></span>

<span data-ttu-id="e13a9-109">이 작업을 투명하게 수행하려면 지원되는 모든 형식을 설명하는 일반적인 방법이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-109">In order to do this transparently, there has to be a common way to describe all supported types.</span></span> <span data-ttu-id="e13a9-110">이 역할을 담당하는 것이 CTS(공용 형식 시스템)입니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-110">This is what the Common Type System (CTS) is in charge of doing.</span></span> <span data-ttu-id="e13a9-111">CTS는 다음과 같은 몇 가지 작업을 수행하도록 작성되었습니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-111">It was made to do several things:</span></span>

* <span data-ttu-id="e13a9-112">언어 간 실행을 위한 프레임워크를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-112">Establish a framework for cross-language execution.</span></span>
* <span data-ttu-id="e13a9-113">.NET 구현에서 다양한 언어 구현을 지원하는 개체 지향 모델을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-113">Provide an object-oriented model to support implementing various languages on a .NET implementation.</span></span>
* <span data-ttu-id="e13a9-114">형식으로 작업할 때 모든 언어가 따라야 하는 규칙 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-114">Define a set of rules that all languages must follow when it comes to working with types.</span></span>
* <span data-ttu-id="e13a9-115">애플리케이션 개발에 사용되는 기본 형식(즉, `Boolean`, `Byte`, `Char` 등)이 포함된 라이브러리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-115">Provide a library that contains the basic primitive types that are used in application development (such as, `Boolean`, `Byte`, `Char` etc.)</span></span>

<span data-ttu-id="e13a9-116">CTS는 지원해야 하는 두 가지 종류의 형식, 즉 참조와 값 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-116">CTS defines two main kinds of types that should be supported: reference and value types.</span></span> <span data-ttu-id="e13a9-117">해당 이름이 정의를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-117">Their names point to their definitions.</span></span>

<span data-ttu-id="e13a9-118">참조 형식의 개체는 개체의 실제 값에 대한 참조로 표시됩니다. 여기서 참조는 C/C++의 포인터와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-118">Reference types' objects are represented by a reference to the object's actual value; a reference here is similar to a pointer in C/C++.</span></span> <span data-ttu-id="e13a9-119">단순히 개체의 값이 있는 메모리 위치를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-119">It simply refers to a memory location where the objects' values are.</span></span> <span data-ttu-id="e13a9-120">이는 이러한 형식의 사용 방법에 큰 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-120">This has a profound impact on how these types are used.</span></span> <span data-ttu-id="e13a9-121">예를 들어 변수에 참조 형식을 할당한 다음 해당 변수를 메서드에 전달하는 경우 개체의 변경 내용이 주 개체에 반영됩니다. 복사 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-121">If you assign a reference type to a variable and then pass that variable into a method, for instance, any changes to the object will be reflected on the main object; there is no copying.</span></span>

<span data-ttu-id="e13a9-122">값 형식은 그 반대이며, 개체가 해당 값으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-122">Value types are the opposite, where the objects are represented by their values.</span></span> <span data-ttu-id="e13a9-123">변수에 값 형식을 할당하는 경우 기본적으로 개체의 값이 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-123">If you assign a value type to a variable, you are essentially copying a value of the object.</span></span>

<span data-ttu-id="e13a9-124">CTS는 각각 특정 의미 체계와 사용법이 있는 여러 형식 범주를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-124">CTS defines several categories of types, each with their specific semantics and usage:</span></span>

* <span data-ttu-id="e13a9-125">클래스</span><span class="sxs-lookup"><span data-stu-id="e13a9-125">Classes</span></span>
* <span data-ttu-id="e13a9-126">구조체</span><span class="sxs-lookup"><span data-stu-id="e13a9-126">Structures</span></span>
* <span data-ttu-id="e13a9-127">열거형</span><span class="sxs-lookup"><span data-stu-id="e13a9-127">Enums</span></span>
* <span data-ttu-id="e13a9-128">인터페이스</span><span class="sxs-lookup"><span data-stu-id="e13a9-128">Interfaces</span></span>
* <span data-ttu-id="e13a9-129">대리자</span><span class="sxs-lookup"><span data-stu-id="e13a9-129">Delegates</span></span>

<span data-ttu-id="e13a9-130">CTS는 액세스 한정자, 유효한 형식 멤버, 상속 및 오버로드 작동 방식 등 형식의 다른 모든 속성도 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-130">CTS also defines all other properties of the types, such as access modifiers, what are valid type members, how inheritance and overloading works and so on.</span></span> <span data-ttu-id="e13a9-131">이러한 내용에 대한 자세한 설명은 이 기초 문서의 범위를 벗어나지만 끝에 있는 [추가 리소스](#more-resources) 섹션에서 해당 항목을 다루는 자세한 콘텐츠의 링크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-131">Unfortunately, going deep into any of those is beyond the scope of an introductory article such as this, but you can consult [More resources](#more-resources) section at the end for links to more in-depth content that covers these topics.</span></span>

## <a name="common-language-specification"></a><span data-ttu-id="e13a9-132">공용 언어 사양</span><span class="sxs-lookup"><span data-stu-id="e13a9-132">Common Language Specification</span></span>

<span data-ttu-id="e13a9-133">완전한 상호 운용성 시나리오를 사용하려면 코드로 만든 모든 개체가 이 개체(및 해당 _호출자_)를 사용하는 언어에서 몇 가지 공통점을 가지고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-133">To enable full interoperability scenarios, all objects that are created in code must rely on some commonality in the languages that are consuming them (are their _callers_).</span></span> <span data-ttu-id="e13a9-134">다양한 언어가 있으므로 .NET 구현은 CLS(**공용 언어 사양**)에서 이러한 공통점을 지정했습니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-134">Since there are numerous different languages, .NET has specified those commonalities in something called the **Common Language Specification** (CLS).</span></span> <span data-ttu-id="e13a9-135">CLS는 일반적인 여러 애플리케이션에 필요한 기능 집합을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-135">CLS defines a set of features that are needed by many common applications.</span></span> <span data-ttu-id="e13a9-136">또한 .NET 구현을 기반으로 하여 구현된 모든 언어에서 지원해야 하는 사항에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-136">It also provides a sort of recipe for any language that is implemented on top of .NET on what it needs to support.</span></span>

<span data-ttu-id="e13a9-137">CLS는 CTS의 하위 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-137">CLS is a subset of the CTS.</span></span> <span data-ttu-id="e13a9-138">즉, CLS 규칙이 더 엄격한 경우가 아니면 CTS의 모든 규칙이 CLS에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-138">This means that all of the rules in the CTS also apply to the CLS, unless the CLS rules are more strict.</span></span> <span data-ttu-id="e13a9-139">CLS의 규칙만 사용하여 구성 요소가 빌드된 경우 해당 API에 CLS 기능만 표시되며 **CLS 규격** 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-139">If a component is built using only the rules in the CLS, that is, it exposes only the CLS features in its API, it is said to be **CLS-compliant**.</span></span> <span data-ttu-id="e13a9-140">예를 들어 `<framework-librares>`는 .NET 구현에서 지원되는 모든 언어에서 작동해야 하므로 정확히 CLS 규격입니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-140">For instance, the `<framework-librares>` are CLS-compliant precisely because they need to work across all of the languages that are supported on .NET.</span></span>

<span data-ttu-id="e13a9-141">아래 [추가 리소스](#more-resources) 섹션의 문서를 통해 CLS의 모든 기능에 대한 개요를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e13a9-141">You can consult the documents in the [More Resources](#more-resources) section below to get an overview of all the features in the CLS.</span></span>

## <a name="more-resources"></a><span data-ttu-id="e13a9-142">추가 리소스</span><span class="sxs-lookup"><span data-stu-id="e13a9-142">More resources</span></span>

* [<span data-ttu-id="e13a9-143">공용 형식 시스템</span><span class="sxs-lookup"><span data-stu-id="e13a9-143">Common Type System</span></span>](./base-types/common-type-system.md)
* [<span data-ttu-id="e13a9-144">공용 언어 사양</span><span class="sxs-lookup"><span data-stu-id="e13a9-144">Common Language Specification</span></span>](language-independence-and-language-independent-components.md)
