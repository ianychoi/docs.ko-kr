---
title: 프레임워크 디자인 지침
description: API 일관성과 사용 편의성을 보장 하기 위해 .NET을 확장 하 고 상호 작용 하는 라이브러리를 디자인 하기 위한 프레임 워크 디자인 지침을 참조 하세요.
titleSuffix: ''
ms.date: 10/22/2008
helpviewer_keywords:
- libraries, .NET Framework class library
- class library design guidelines [.NET Framework], about
- class library design guidelines [.NET Framework]
ms.assetid: 5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b
ms.openlocfilehash: 03fa44c1fed219b50cf1a8d22b2c9f79947f4976
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706660"
---
# <a name="framework-design-guidelines"></a><span data-ttu-id="f4372-103">프레임워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-103">Framework Design Guidelines</span></span>

<span data-ttu-id="f4372-104">이 섹션에서는 .NET Framework를 확장 하 고 상호 작용 하는 라이브러리를 디자인 하기 위한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-104">This section provides guidelines for designing libraries that extend and interact with the .NET Framework.</span></span> <span data-ttu-id="f4372-105">개발에 사용 되는 프로그래밍 언어와 독립적인 통합 프로그래밍 모델을 제공 하 여 라이브러리 디자이너가 API 일관성과 사용 편의성을 보장할 수 있도록 돕는 것이 목표입니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-105">The goal is to help library designers ensure API consistency and ease of use by providing a unified programming model that is independent of the programming language used for development.</span></span> <span data-ttu-id="f4372-106">.NET Framework를 확장 하는 클래스 및 구성 요소를 개발 하는 경우 이러한 디자인 지침을 따르는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-106">We recommend that you follow these design guidelines when developing classes and components that extend the .NET Framework.</span></span> <span data-ttu-id="f4372-107">일관 되지 않은 라이브러리 디자인은 개발자 생산성에 영향을 주지 않고 채택을 유지 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-107">Inconsistent library design adversely affects developer productivity and discourages adoption.</span></span>  
  
 <span data-ttu-id="f4372-108">지침은,, 및 라는 용어가 접두사로 추가 된 간단한 권장 사항으로 구성 됩니다 `Do` `Consider` `Avoid` `Do not` .</span><span class="sxs-lookup"><span data-stu-id="f4372-108">The guidelines are organized as simple recommendations prefixed with the terms `Do`, `Consider`, `Avoid`, and `Do not`.</span></span> <span data-ttu-id="f4372-109">이러한 지침은 클래스 라이브러리 디자이너가 서로 다른 솔루션 간의 장단점을 이해 하는 데 도움을 주기 위해 작성 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-109">These guidelines are intended to help class library designers understand the trade-offs between different solutions.</span></span> <span data-ttu-id="f4372-110">적절 한 라이브러리 디자인에서 이러한 디자인 지침을 위반 해야 하는 경우가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-110">There might be situations where good library design requires that you violate these design guidelines.</span></span> <span data-ttu-id="f4372-111">이러한 경우는 드물게 발생 하 고 결정에 대 한 분명 하 고 매력적인 이유가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-111">Such cases should be rare, and it is important that you have a clear and compelling reason for your decision.</span></span>  
  
 <span data-ttu-id="f4372-112">이러한 지침은 설명서 *프레임 워크 디자인 지침에서 발췌 한 것. 다시 사용할 수 있는 .Net 라이브러리에 대 한 규칙, 관용구, 패턴*, Krzysztof Cwalina 및 Brad abrams 성, 두 번째 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-112">These guidelines are excerpted from the book *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition*, by Krzysztof Cwalina and Brad Abrams.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4372-113">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="f4372-113">In This Section</span></span>  

 [<span data-ttu-id="f4372-114">명명 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-114">Naming Guidelines</span></span>](naming-guidelines.md)  
 <span data-ttu-id="f4372-115">클래스 라이브러리에서 어셈블리, 네임 스페이스, 형식 및 멤버의 이름을 지정 하는 방법에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-115">Provides guidelines for naming assemblies, namespaces, types, and members in class libraries.</span></span>  
  
 [<span data-ttu-id="f4372-116">형식 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-116">Type Design Guidelines</span></span>](type.md)  
 <span data-ttu-id="f4372-117">정적 클래스, 추상 클래스, 인터페이스, 열거형, 구조체 및 기타 형식을 사용 하는 방법에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-117">Provides guidelines for using static and abstract classes, interfaces, enumerations, structures, and other types.</span></span>  
  
 [<span data-ttu-id="f4372-118">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-118">Member Design Guidelines</span></span>](member.md)  
 <span data-ttu-id="f4372-119">속성, 메서드, 생성자, 필드, 이벤트, 연산자 및 매개 변수를 디자인 하 고 사용 하는 방법에 대 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-119">Provides guidelines for designing and using properties, methods, constructors, fields, events, operators, and parameters.</span></span>  
  
 [<span data-ttu-id="f4372-120">확장성을 위한 디자인</span><span class="sxs-lookup"><span data-stu-id="f4372-120">Designing for Extensibility</span></span>](designing-for-extensibility.md)  
 <span data-ttu-id="f4372-121">서브클래싱, 이벤트, 가상 멤버 및 콜백과 같은 확장성 메커니즘에 대해 설명 하 고 프레임 워크의 요구 사항을 가장 잘 충족 하는 메커니즘을 선택 하는 방법을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-121">Discusses extensibility mechanisms such as subclassing, using events, virtual members, and callbacks, and explains how to choose the mechanisms that best meet your framework's requirements.</span></span>  
  
 [<span data-ttu-id="f4372-122">예외 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-122">Design Guidelines for Exceptions</span></span>](exceptions.md)  
 <span data-ttu-id="f4372-123">예외를 디자인, throw 및 catch 하기 위한 디자인 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-123">Describes design guidelines for designing, throwing, and catching exceptions.</span></span>  
  
 [<span data-ttu-id="f4372-124">사용 지침</span><span class="sxs-lookup"><span data-stu-id="f4372-124">Usage Guidelines</span></span>](usage-guidelines.md)  
 <span data-ttu-id="f4372-125">배열, 특성 및 컬렉션과 같은 공용 형식을 사용 하 고 serialization을 지원 하며 같음 연산자를 오버 로드 하는 방법에 대 한 지침을 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-125">Describes guidelines for using common types such as arrays, attributes, and collections, supporting serialization, and overloading equality operators.</span></span>  
  
 [<span data-ttu-id="f4372-126">일반적인 디자인 패턴</span><span class="sxs-lookup"><span data-stu-id="f4372-126">Common Design Patterns</span></span>](common-design-patterns.md)  
 <span data-ttu-id="f4372-127">종속성 속성을 선택 하 고 구현 하기 위한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="f4372-127">Provides guidelines for choosing and implementing dependency properties.</span></span>  
  
 <span data-ttu-id="f4372-128">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="f4372-128">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="f4372-129">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="f4372-129">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4372-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="f4372-130">See also</span></span>

- [<span data-ttu-id="f4372-131">개요</span><span class="sxs-lookup"><span data-stu-id="f4372-131">Overview</span></span>](../../framework/get-started/overview.md)
- [<span data-ttu-id="f4372-132">개발 가이드</span><span class="sxs-lookup"><span data-stu-id="f4372-132">Development Guide</span></span>](../../framework/development-guide.md)
