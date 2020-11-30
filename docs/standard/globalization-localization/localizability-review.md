---
title: 지역화 가능성 검토
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET], localization
- localizability [.NET]
- international applications [.NET], localizability
- globalization [.NET], localizability
- culture, localizability
- localization [.NET], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
ms.openlocfilehash: ecfba7b6b5908a16bb23860704a35035f58e3ed4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686022"
---
# <a name="localizability-review"></a><span data-ttu-id="453eb-102">지역화 가능성 검토</span><span class="sxs-lookup"><span data-stu-id="453eb-102">Localizability review</span></span>

<span data-ttu-id="453eb-103">지역화 가능성 검토는 지역화 대비 애플리케이션 개발의 중간 단계로,</span><span class="sxs-lookup"><span data-stu-id="453eb-103">The localizability review is an intermediate step in the development of a world-ready application.</span></span> <span data-ttu-id="453eb-104">전역화된 애플리케이션이 지역화될 준비가 되어 있는지 점검하고 특별한 처리가 필요한 사용자 인터페이스의 모든 코드 또는 측면을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-104">It verifies that a globalized application is ready for localization and identifies any code or any aspects of the user interface that require special handling.</span></span> <span data-ttu-id="453eb-105">또한 이 단계를 통해 지역화 과정 후에도 애플리케이션에 기능적 결함이 발생되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-105">This step also helps ensure that the localization process will not introduce any functional defects into your application.</span></span> <span data-ttu-id="453eb-106">지역화 가능성 검토에서 제기된 모든 문제가 해결되면 애플리케이션은 지역화될 준비가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-106">When all the issues raised by the localizability review have been addressed, your application is ready for localization.</span></span> <span data-ttu-id="453eb-107">지역화 가능성 검토가 철저할 경우 지역화 과정 중에 소스 코드를 수정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-107">If the localizability review is thorough, you should not have to modify any source code during the localization process.</span></span>

<span data-ttu-id="453eb-108">지역화 가능성 검토는 다음 세 가지 검사로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-108">The localizability review consists of the following three checks:</span></span>

- [<span data-ttu-id="453eb-109">전역화 권장 사항이 구현되었습니까?</span><span class="sxs-lookup"><span data-stu-id="453eb-109">Are the globalization recommendations implemented?</span></span>](#global)

- [<span data-ttu-id="453eb-110">문화권 구분 기능이 올바르게 처리되었습니까?</span><span class="sxs-lookup"><span data-stu-id="453eb-110">Are culture-sensitive features handled correctly?</span></span>](#culture)

- [<span data-ttu-id="453eb-111">국가별 데이터를 사용하여 애플리케이션을 테스트했습니까?</span><span class="sxs-lookup"><span data-stu-id="453eb-111">Have you tested your application with international data?</span></span>](#test)

<a name="global"></a>

## <a name="implement-globalization-recommendations"></a><span data-ttu-id="453eb-112">세계화 권장 사항 구현</span><span class="sxs-lookup"><span data-stu-id="453eb-112">Implement globalization recommendations</span></span>

<span data-ttu-id="453eb-113">지역화를 염두에 두고 애플리케이션을 설계 및 개발했고 [세계화](globalization.md) 문서에 설명된 권장 사항을 따른 경우 지역화 가능성 검토는 대개 품질 보증 단계에서 통과하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-113">If you have designed and developed your application with localization in mind, and if you have followed the recommendations discussed in the [Globalization](globalization.md) article, the localizability review will largely be a quality assurance pass.</span></span> <span data-ttu-id="453eb-114">그러지 않으면 이 단계에서 [세계화](globalization.md)를 위한 권장 사항을 검토 및 구현하고 지역화를 방해하는 소스 코드의 오류를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-114">Otherwise, during this stage you should review and implement the recommendations for [globalization](globalization.md) and fix the errors in source code that prevent localization.</span></span>

<a name="culture"></a>

## <a name="handle-culture-sensitive-features"></a><span data-ttu-id="453eb-115">문화권 구분 기능 처리</span><span class="sxs-lookup"><span data-stu-id="453eb-115">Handle culture-sensitive features</span></span>

<span data-ttu-id="453eb-116">.NET에서는 다양한 영역에서 문화권마다 다른 프로그래밍 방식 지원을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-116">.NET does not provide programmatic support in a number of areas that vary widely by culture.</span></span> <span data-ttu-id="453eb-117">대부분의 경우 사용자 지정 코드를 작성하여 다음과 같은 기능 영역을 처리해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-117">In most cases, you have to write custom code to handle feature areas like the following:</span></span>

- <span data-ttu-id="453eb-118">주소</span><span class="sxs-lookup"><span data-stu-id="453eb-118">Addresses</span></span>

- <span data-ttu-id="453eb-119">전화 번호</span><span class="sxs-lookup"><span data-stu-id="453eb-119">Telephone numbers</span></span>

- <span data-ttu-id="453eb-120">용지 크기</span><span class="sxs-lookup"><span data-stu-id="453eb-120">Paper sizes</span></span>

- <span data-ttu-id="453eb-121">길이, 무게, 영역, 볼륨 및 온도에 사용되는 측정 단위</span><span class="sxs-lookup"><span data-stu-id="453eb-121">Units of measure used for lengths, weights, area, volume, and temperatures</span></span>

   <span data-ttu-id="453eb-122">.NET에서 측정 단위 간의 변환에 대한 기본 지원을 제공하지 않지만, 다음 예제와 같이 <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> 속성을 사용하여 특정 국가 또는 지역이 미터법을 사용하는지 여부를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-122">Although .NET does not offer built-in support for converting between units of measure, you can use the <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> property to determine whether a particular country or region uses the metric system, as the following example illustrates.</span></span>

   [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
   [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]

<a name="test"></a>

## <a name="test-your-application"></a><span data-ttu-id="453eb-123">애플리케이션 테스트</span><span class="sxs-lookup"><span data-stu-id="453eb-123">Test your application</span></span>

<span data-ttu-id="453eb-124">애플리케이션을 지역화하기 전에 운영 체제의 국가별 버전에서 국가별 데이터를 사용하여 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-124">Before you localize your application, you should test it by using international data on international versions of the operating system.</span></span> <span data-ttu-id="453eb-125">대부분의 사용자 인터페이스는 이 시점에서 지역화되지 않지만, 다음과 같은 문제를 발견할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-125">Although most of the user interface will not be localized at this point, you will be able to detect problems such as the following:</span></span>

- <span data-ttu-id="453eb-126">운영 체제 버전마다 제대로 역직렬화하지 않는 직렬화된 데이터.</span><span class="sxs-lookup"><span data-stu-id="453eb-126">Serialized data that does not deserialize correctly across operating system versions.</span></span>

- <span data-ttu-id="453eb-127">현재 문화권의 규칙을 반영하지 않는 숫자 데이터.</span><span class="sxs-lookup"><span data-stu-id="453eb-127">Numeric data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="453eb-128">예를 들어, 숫자가 정확하지 않은 그룹 구분 기호, 소수 구분 기호 또는 통화 기호를 사용하여 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-128">For example, numbers may be displayed with inaccurate group separators, decimal separators, or currency symbols.</span></span>

- <span data-ttu-id="453eb-129">현재 문화권의 규칙을 반영하지 않는 날짜 및 시간 데이터.</span><span class="sxs-lookup"><span data-stu-id="453eb-129">Date and time data that does not reflect the conventions of the current culture.</span></span> <span data-ttu-id="453eb-130">예를 들어, 월 및 일을 나타내는 숫자가 잘못된 순서로 나타나고, 날짜 구분 기호가 올바르지 않거나 표준 시간대 정보가 잘못될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-130">For example, numbers that represent the month and day may appear in the wrong order, date separators may be incorrect, or time zone information may be incorrect.</span></span>

- <span data-ttu-id="453eb-131">애플리케이션에 대한 기본 문화권을 확인하지 않았으므로 찾을 수 없는 리소스.</span><span class="sxs-lookup"><span data-stu-id="453eb-131">Resources that cannot be found because you have not identified a default culture for your application.</span></span>

- <span data-ttu-id="453eb-132">특정 문화권에 대해 비정상적인 순서로 표시되는 문자열.</span><span class="sxs-lookup"><span data-stu-id="453eb-132">Strings that are displayed in an unusual order for the specific culture.</span></span>

- <span data-ttu-id="453eb-133">예기치 않은 결과를 반환하는 같음 비교 또는 문자열 비교.</span><span class="sxs-lookup"><span data-stu-id="453eb-133">String comparisons or comparisons for equality that return unexpected results.</span></span>

<span data-ttu-id="453eb-134">애플리케이션을 개발할 때 세계화 권장 사항을 따르고 문화권 구분 기능을 올바르게 처리하고 테스트 중 발생한 지역화 문제를 해결했다면 다음 단계인 [지역화](localization.md)로 진행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="453eb-134">If you've followed the globalization recommendations when developing your application, handled culture-sensitive features correctly, and identified and addressed the localization issues that arose during testing, you can proceed to the next step, [Localization](localization.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="453eb-135">참고 항목</span><span class="sxs-lookup"><span data-stu-id="453eb-135">See also</span></span>

- [<span data-ttu-id="453eb-136">전역화 및 지역화</span><span class="sxs-lookup"><span data-stu-id="453eb-136">Globalization and Localization</span></span>](index.md)
- [<span data-ttu-id="453eb-137">지역화</span><span class="sxs-lookup"><span data-stu-id="453eb-137">Localization</span></span>](localization.md)
- [<span data-ttu-id="453eb-138">전역화</span><span class="sxs-lookup"><span data-stu-id="453eb-138">Globalization</span></span>](globalization.md)
- [<span data-ttu-id="453eb-139">데스크톱 앱의 리소스</span><span class="sxs-lookup"><span data-stu-id="453eb-139">Resources in Desktop Apps</span></span>](../../framework/resources/index.md)
