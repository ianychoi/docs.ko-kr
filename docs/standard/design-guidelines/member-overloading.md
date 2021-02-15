---
description: '자세한 정보: 멤버 오버로드'
title: 멤버 오버로드
ms.date: 10/22/2008
helpviewer_keywords:
- default arguments
- members [.NET Framework], overloaded
- member design guidelines [.NET Framework], overloading
- overloaded members
- signatures, members
ms.assetid: 964ba19e-8b94-4b5b-b1e3-5a0b531a0bb1
ms.openlocfilehash: d3a545bfec552686e55c9f713d58784497946819
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641956"
---
# <a name="member-overloading"></a><span data-ttu-id="22d11-103">멤버 오버로드</span><span class="sxs-lookup"><span data-stu-id="22d11-103">Member Overloading</span></span>

<span data-ttu-id="22d11-104">멤버 오버로드는 매개 변수의 개수나 형식만 다르고 이름은 같은 동일한 형식에 둘 이상의 멤버를 만든다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-104">Member overloading means creating two or more members on the same type that differ only in the number or type of parameters but have the same name.</span></span> <span data-ttu-id="22d11-105">예를 들어 다음에서는 `WriteLine` 메서드가 오버로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-105">For example, in the following, the `WriteLine` method is overloaded:</span></span>

```csharp
public static class Console {
    public void WriteLine();
    public void WriteLine(string value);
    public void WriteLine(bool value);
    ...
}
```

 <span data-ttu-id="22d11-106">메서드, 생성자, 인덱싱된 속성만 매개 변수를 가질 수 있으므로 해당 멤버만 오버로드될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-106">Because only methods, constructors, and indexed properties can have parameters, only those members can be overloaded.</span></span>

 <span data-ttu-id="22d11-107">오버로드는 재사용 가능한 라이브러리의 유용성, 생산성, 가독성을 개선할 수 있는 가장 중요한 기법의 하나입니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-107">Overloading is one of the most important techniques for improving usability, productivity, and readability of reusable libraries.</span></span> <span data-ttu-id="22d11-108">매개 변수 개수를 오버로드하면 더 간단한 버전의 생성자 및 메서드를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-108">Overloading on the number of parameters makes it possible to provide simpler versions of constructors and methods.</span></span> <span data-ttu-id="22d11-109">매개 변수 형식을 오버로드하면 선택한 다른 형식 세트에서 동일한 작업을 수행하는 멤버에 대해 동일한 멤버 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-109">Overloading on the parameter type makes it possible to use the same member name for members performing identical operations on a selected set of different types.</span></span>

 <span data-ttu-id="22d11-110">✔️ 더 짧은 오버로드에서 사용하는 기본값을 나타내려면 설명이 포함된 매개 변수 이름을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="22d11-110">✔️ DO try to use descriptive parameter names to indicate the default used by shorter overloads.</span></span>

 <span data-ttu-id="22d11-111">❌ 오버로드에서 임의로 다양한 매개 변수 이름을 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-111">❌ AVOID arbitrarily varying parameter names in overloads.</span></span> <span data-ttu-id="22d11-112">한 오버로드의 매개 변수가 다른 오버로드의 매개 변수와 동일한 입력을 나타내는 경우 매개 변수 이름은 동일해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-112">If a parameter in one overload represents the same input as a parameter in another overload, the parameters should have the same name.</span></span>

 <span data-ttu-id="22d11-113">❌ 오버로드된 멤버에서 매개 변수 순서가 일관되지 않으면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-113">❌ AVOID being inconsistent in the ordering of parameters in overloaded members.</span></span> <span data-ttu-id="22d11-114">이름이 같은 매개 변수는 모든 오버로드에서 동일한 위치에 표시되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-114">Parameters with the same name should appear in the same position in all overloads.</span></span>

 <span data-ttu-id="22d11-115">✔️ 가장 긴 오버로드만 가상으로 설정하세요(확장성이 필요한 경우).</span><span class="sxs-lookup"><span data-stu-id="22d11-115">✔️ DO make only the longest overload virtual (if extensibility is required).</span></span> <span data-ttu-id="22d11-116">더 짧은 오버로드는 더 긴 오버로드를 통해 호출하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-116">Shorter overloads should simply call through to a longer overload.</span></span>

 <span data-ttu-id="22d11-117">❌ `ref` 또는 `out` 한정자를 사용하여 멤버를 오버로드하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="22d11-117">❌ DO NOT use `ref` or `out` modifiers to overload members.</span></span>

 <span data-ttu-id="22d11-118">일부 언어에서는 이러한 오버로드에 대한 호출을 확인할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-118">Some languages cannot resolve calls to overloads like this.</span></span> <span data-ttu-id="22d11-119">또한 이러한 오버로드는 일반적으로 완전히 다른 의미 체계를 사용하며 별도의 두 메서드를 제외하면 오버로드가 되지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-119">In addition, such overloads usually have completely different semantics and probably should not be overloads but two separate methods instead.</span></span>

 <span data-ttu-id="22d11-120">❌ 유사한 형식이지만 의미 체계가 다르고 동일한 위치에 매개 변수가 있는 오버로드가 없도록 하세요.</span><span class="sxs-lookup"><span data-stu-id="22d11-120">❌ DO NOT have overloads with parameters at the same position and similar types yet with different semantics.</span></span>

 <span data-ttu-id="22d11-121">✔️ 선택적 인수에 대해 `null`을 전달하도록 허용하세요.</span><span class="sxs-lookup"><span data-stu-id="22d11-121">✔️ DO  allow `null` to be passed for optional arguments.</span></span>

 <span data-ttu-id="22d11-122">✔️ 기본 인수로 멤버를 정의하는 대신 멤버 오버로드를 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="22d11-122">✔️ DO use member overloading rather than defining members with default arguments.</span></span>

 <span data-ttu-id="22d11-123">기본 인수는 CLS 규격이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="22d11-123">Default arguments are not CLS compliant.</span></span>

 <span data-ttu-id="22d11-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="22d11-124">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="22d11-125">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="22d11-125">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="22d11-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="22d11-126">See also</span></span>

- [<span data-ttu-id="22d11-127">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="22d11-127">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="22d11-128">프레임워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="22d11-128">Framework Design Guidelines</span></span>](index.md)
