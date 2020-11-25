---
title: 매개 변수 이름 지정
description: 매개 변수의 이름을 지정 하는 방법에 대 한 지침을 알아봅니다. 예를 들어 카멜식 대/소문자 & 설명 매개 변수 이름을 사용 하 & 형식 대신 의미에 따라 이름을 지정 하는 것이 좋습니다.
ms.date: 10/22/2008
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
ms.openlocfilehash: 9f03eda511c2ef0c9565d270c52fd72bf54692d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698353"
---
# <a name="naming-parameters"></a><span data-ttu-id="b53d4-104">매개 변수 이름 지정</span><span class="sxs-lookup"><span data-stu-id="b53d4-104">Naming Parameters</span></span>

<span data-ttu-id="b53d4-105">시각적 디자인 도구에서 Intellisense 및 클래스 검색 기능을 제공 하는 경우 매개 변수가 설명서 및 디자이너에 표시 되기 때문에 가독성을 명확 하 게 이해 하는 것은 매개 변수 이름에 대 한 지침을 따르는 것이 중요 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-105">Beyond the obvious reason of readability, it is important to follow the guidelines for parameter names because parameters are displayed in documentation and in the designer when visual design tools provide Intellisense and class browsing functionality.</span></span>

 <span data-ttu-id="b53d4-106">✔️ 매개 변수 이름에 camelCasing를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-106">✔️ DO use camelCasing in parameter names.</span></span>

 <span data-ttu-id="b53d4-107">✔️ 설명 매개 변수 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-107">✔️ DO use descriptive parameter names.</span></span>

 <span data-ttu-id="b53d4-108">매개 변수의 형식이 아닌 매개 변수의 의미에 따라 이름을 사용 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="b53d4-108">✔️ CONSIDER using names based on a parameter’s meaning rather than the parameter’s type.</span></span>

### <a name="naming-operator-overload-parameters"></a><span data-ttu-id="b53d4-109">명명 연산자 오버 로드 매개 변수</span><span class="sxs-lookup"><span data-stu-id="b53d4-109">Naming Operator Overload Parameters</span></span>

 <span data-ttu-id="b53d4-110">`left` `right` 매개 변수에 의미가 없으면 이항 연산자 오버 로드 매개 변수 이름에 및를 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-110">✔️ DO use `left` and `right` for binary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="b53d4-111">`value`매개 변수에 의미가 없는 경우 단항 연산자 오버 로드 매개 변수 이름을 사용 하 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-111">✔️ DO use `value` for unary operator overload parameter names if there is no meaning to the parameters.</span></span>

 <span data-ttu-id="b53d4-112">연산자 오버 로드 매개 변수에 대 한 의미 있는 이름을 고려 ✔️ 합니다. 이렇게 하면 중요 한 값이 추가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b53d4-112">✔️ CONSIDER meaningful names for operator overload parameters if doing so adds significant value.</span></span>

 <span data-ttu-id="b53d4-113">❌ 연산자 오버 로드 매개 변수 이름에 약어 또는 숫자 인덱스를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="b53d4-113">❌ DO NOT use abbreviations or numeric indices for operator overload parameter names.</span></span>

 <span data-ttu-id="b53d4-114">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b53d4-114">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b53d4-115">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="b53d4-115">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b53d4-116">참조</span><span class="sxs-lookup"><span data-stu-id="b53d4-116">See also</span></span>

- [<span data-ttu-id="b53d4-117">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="b53d4-117">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="b53d4-118">명명 지침</span><span class="sxs-lookup"><span data-stu-id="b53d4-118">Naming Guidelines</span></span>](naming-guidelines.md)
