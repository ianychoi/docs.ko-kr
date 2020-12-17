---
title: ASP.NET Core MVC 앱 테스트
description: ASP.NET Core 및 Azure를 사용하여 최신 웹 애플리케이션 설계 | ASP.NET Core MVC 앱 테스트
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
ms.openlocfilehash: b253cfb90487cc462b0f3b8a7564c97ad403aa06
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851401"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="23ebc-103">ASP.NET Core MVC 앱 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="23ebc-104">*"제품 단위 테스트가 마음에 들지 않으면 대부분의 고객도 이 테스트를 좋아하지 않을 것입니다."*</span><span class="sxs-lookup"><span data-stu-id="23ebc-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="23ebc-105">\_- 익명-</span><span class="sxs-lookup"><span data-stu-id="23ebc-105">\_- Anonymous-</span></span>

<span data-ttu-id="23ebc-106">복잡한 소프트웨어는 변경에 대응하여 예기치 않은 방식으로 실패할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="23ebc-107">따라서 변경 후 테스트는 가장 사소한(또는 가장 중요하지 않은) 애플리케이션을 제외한 모든 애플리케이션에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="23ebc-108">수동 테스트는 소프트웨어를 테스트하는 데 있어 속도가 가장 느리고, 안정성이 가장 낮고, 비용이 가장 많이 드는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="23ebc-109">그러나 애플리케이션이 테스트될 수 있도록 설계되지 않은 경우 사용 가능한 유일한 방법일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="23ebc-110">[4장](architectural-principles.md)에 설명된 아키텍처 원칙을 따르도록 작성된 애플리케이션은 단위 테스트가 가능해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="23ebc-111">ASP.NET Core 애플리케이션은 자동화된 통합 및 기능 테스트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="23ebc-112">자동화된 테스트의 종류</span><span class="sxs-lookup"><span data-stu-id="23ebc-112">Kinds of automated tests</span></span>

<span data-ttu-id="23ebc-113">소프트웨어 애플리케이션에 대한 자동화된 테스트에는 여러 종류가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="23ebc-114">가장 간단하고 가장 낮은 수준의 테스트는 단위 테스트입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="23ebc-115">약간 더 높은 수준에서 통합 테스트와 기능 테스트가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="23ebc-116">UI 테스트, 부하 테스트, 스트레스 테스트 및 스모크 테스트와 같은 다른 종류의 테스트는 이 문서에서 다루지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="23ebc-117">단위 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-117">Unit tests</span></span>

<span data-ttu-id="23ebc-118">단위 테스트는 애플리케이션 논리의 단일 부분을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="23ebc-119">아닌 항목 중 일부를 나열하여 자세히 설명할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="23ebc-120">단위 테스트는 코드에서 종속성 또는 인프라와 작동하는 방식을 테스트하지 않으므로 통합 테스트가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="23ebc-121">단위 테스트는 코드가 작성된 프레임워크를 테스트하지 않습니다. 즉 이 프레임워크가 작동한다고 가정하거나, 그렇지 않으면 버그를 기록하고 해결 방법을 코딩합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="23ebc-122">단위 테스트는 메모리와 프로세스에서 전적으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="23ebc-123">파일 시스템, 네트워크 또는 데이터베이스와 통신하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="23ebc-124">단위 테스트는 코드만 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="23ebc-125">단위 테스트는 외부 종속성 없이 코드의 단일 단위만 테스트한다는 사실 때문에 매우 빠르게 실행되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely fast.</span></span> <span data-ttu-id="23ebc-126">따라서 단위 테스트의 수백 개 테스트 도구 모음을 몇 초 안에 실행할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="23ebc-127">모든 푸시를 공유 소스 제어 저장소로 수행하기 전에 빌드 서버에 있는 모든 자동화된 빌드를 사용하여 자주 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="23ebc-128">통합 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-128">Integration tests</span></span>

<span data-ttu-id="23ebc-129">데이터베이스 및 파일 시스템과 같은 인프라와 상호 작용하는 코드를 캡슐화하는 것이 좋지만, 여전히 해당 코드 중 일부를 사용할 수 있고 이를 테스트하려고 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="23ebc-130">또한 애플리케이션의 종속성이 완전히 해결되면 코드 계층이 예상대로 상호 작용하는지도 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="23ebc-131">이 기능은 통합 테스트에서 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-131">This functionality is the responsibility of integration tests.</span></span> <span data-ttu-id="23ebc-132">통합 테스트는 종종 외부 종속성 및 인프라를 사용하므로 단위 테스트에 비해 속도가 더 느리고 설정하기도 더 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="23ebc-133">따라서 통합 테스트에서 단위 테스트로 테스트할 수 있는 항목은 테스트하지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="23ebc-134">지정된 시나리오를 단위 테스트에서 테스트할 수 있으면 단위 테스트를 사용하여 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="23ebc-135">그렇게 할 수 없으면 통합 테스트를 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="23ebc-136">통합 테스트에는 단위 테스트보다 더 복잡한 설정 및 해체 절차가 포함되는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="23ebc-137">예를 들어 실제 데이터베이스에 대한 통합 테스트에는 각 테스트를 실행하기 전에 데이터베이스를 알려진 상태로 되돌릴 방법이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="23ebc-138">새 테스트가 추가되고 프로덕션 데이터베이스 스키마가 진화함에 따라 이러한 테스트 스크립트의 크기와 복잡성이 증가하는 경향이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="23ebc-139">많은 대형 시스템에서 공유 소스 제어에 대한 변경 내용을 체크 인하기 전에 개발자 워크스테이션에 대한 통합 테스트의 전체 제품군을 실행하는 것은 비현실적입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="23ebc-140">이러한 경우 통합 테스트는 빌드 서버에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="23ebc-141">기능 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-141">Functional tests</span></span>

<span data-ttu-id="23ebc-142">통합 테스트는 개발자의 관점에서 작성되어 시스템의 일부 구성 요소가 모두 제대로 작동하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="23ebc-143">기능 테스트는 사용자의 관점에서 작성되며, 요구 사항에 따라 시스템의 정확성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="23ebc-144">다음 인용문은 단위 테스트와 비교하여 기능 테스트를 생각하는 방법에 대한 유용한 유사성을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="23ebc-145">"시스템 개발은 집의 건축에 비유되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="23ebc-146">이 비유가 그다지 정확한 것은 아니지만 단위 테스트와 기능 테스트의 차이점을 이해하기 위해 확장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="23ebc-147">단위 테스트는 집의 건축 현장을 방문하는 건물 감독관과 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="23ebc-148">그는 집의 다양한 내부 시스템, 기초, 골조, 전기, 배관 등에 초점을 맞추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="23ebc-149">그는 집의 구성 부분이 안전하게 제대로 작동하는지, 즉, 건축 법규를 충족하는지 확인(테스트)합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="23ebc-150">이 시나리오의 기능 테스트는 이 건축 현장을 방문하는 주택 소유자와 유사합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="23ebc-151">그는 내부 시스템이 적절히 작동하고 건물 감독관이 자신의 임무를 수행하고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="23ebc-152">주택 소유자는 이 집에서 사는 것이 어떤 것일지에 초점을 맞추고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="23ebc-153">그는 집이 어떻게 보이는지, 여러 방이 편안한 크기인지, 집이 가족의 요구에 부응하는지, 아침 햇살이 드는 좋은 장소에 창문이 있는지 등에 관심이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="23ebc-154">주택 소유자는 사용자의 관점에서 집에 대한 기능 테스트를</span><span class="sxs-lookup"><span data-stu-id="23ebc-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="23ebc-155">수행하고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-155">He has the user's perspective.</span></span> <span data-ttu-id="23ebc-156">한편 건물 감독관은 건축가의 관점에서 집에 대한 단위 테스트를</span><span class="sxs-lookup"><span data-stu-id="23ebc-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="23ebc-157">수행하고 있습니다."</span><span class="sxs-lookup"><span data-stu-id="23ebc-157">He has the builder's perspective."</span></span>

<span data-ttu-id="23ebc-158">소스: [단위 테스트 및 기능 테스트](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="23ebc-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="23ebc-159">"개발자로서 우리는 두 가지 방법에서 실패합니다. 즉 작업을 잘못 빌드하거나 잘못된 작업을 빌드합니다."라고 말하고 싶습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="23ebc-160">단위 테스트를 통해 작업을 올바르게 빌드할 수 있으며, 기능 테스트를 통해 올바른 작업을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="23ebc-161">기능 테스트는 시스템 수준에서 작동하므로 어느 정도의 UI 자동화가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="23ebc-162">일반적으로 기능 테스트는 통합 테스트와 마찬가지로 일종의 테스트 인프라에서도 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="23ebc-163">이 작업 때문에 단위 테스트와 통합 테스트보다 더 느리고 더 불안정합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-163">This activity makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="23ebc-164">사용자가 예상하는 대로 시스템이 제대로 작동하는지 확신할 수 있을 만큼 많은 기능 테스트만 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="23ebc-165">피라미드형 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-165">Testing Pyramid</span></span>

<span data-ttu-id="23ebc-166">Martin Fowler는 피라미드형 테스트에 대해 글을 썼으며. 그 예는 그림 9-1에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![피라미드형 테스트](./media/image9-1.png)

<span data-ttu-id="23ebc-168">**그림 9-1**.</span><span class="sxs-lookup"><span data-stu-id="23ebc-168">**Figure 9-1**.</span></span> <span data-ttu-id="23ebc-169">피라미드형 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-169">Testing Pyramid</span></span>

<span data-ttu-id="23ebc-170">피라미드의 서로 다른 계층과 상대적인 크기는 여러 종류의 테스트와 애플리케이션에 대해 작성해야 하는 횟수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="23ebc-171">여기서 볼 수 있듯이, 더 작은 계층의 기능 테스트와 함께 작은 계층의 통합 테스트 계층에서 지원하는 큰 기반의 단위 테스트를 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="23ebc-172">각 계층에는 이상적으로 하위 계층에서 적절하게 수행할 수 없는 테스트만 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="23ebc-173">특정 시나리오에 필요한 테스트 종류를 결정할 때에는 피라미드형 테스트를 명심하세요.</span><span class="sxs-lookup"><span data-stu-id="23ebc-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="23ebc-174">테스트 항목</span><span class="sxs-lookup"><span data-stu-id="23ebc-174">What to test</span></span>

<span data-ttu-id="23ebc-175">자동화된 테스트를 작성하는 데 익숙하지 않은 개발자에게 발생하는 일반적인 문제는 테스트 항목에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="23ebc-176">좋은 출발점은 조건부 논리를 테스트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="23ebc-177">조건문(if-else, switch 등)에 따라 동작이 바뀌는 메서드가 있는 경우 특정 조건에 대한 올바른 동작을 확인하기 위해 최소한 두 가지 테스트를 고안할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="23ebc-178">코드에 오류 조건이 있는 경우 코드를 통해 "정상 경로"에 대한 테스트(오류 없음)를 하나 이상 작성하고, "비정상 경로"에 대한 테스트(오류 또는 비정상 결과 있음)를 하나 이상 작성하여 오류 발생 시 애플리케이션이 예상대로 작동하는지 확인하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="23ebc-179">마지막으로, 코드 검사와 같은 메트릭에 집중하는 것이 아니라 실패할 수 있는 작업을 테스트하는 데 집중하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="23ebc-180">일반적으로 코드 검사가 더 많을수록 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="23ebc-181">그러나 복잡하고 업무상 중요한 메서드에 대한 몇 가지 테스트를 작성하는 경우, 테스트 코드 검사 메트릭을 향상시키기 위해 일반적으로 자동 속성 테스트를 작성하는 것보다 더 효과적으로 시간을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="23ebc-182">테스트 프로젝트 구성</span><span class="sxs-lookup"><span data-stu-id="23ebc-182">Organizing test projects</span></span>

<span data-ttu-id="23ebc-183">테스트 프로젝트는 구성할 수 있지만 가장 효과적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="23ebc-184">테스트를 유형별(단위 테스트, 통합 테스트) 및 테스트 기능별(프로젝트별, 네임스페이스별)로 구분하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="23ebc-185">이 분리가 단일 테스트 프로젝트 또는 여러 테스트 프로젝트 내의 폴더로 구성되는지는 디자인상의 결정입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="23ebc-186">하나의 프로젝트가 가장 간단하지만, 여러 테스트가 포함된 대규모 프로젝트의 경우 또는 다른 테스트 집합을 더 쉽게 실행하기 위해 몇 가지 여러 테스트 프로젝트를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="23ebc-187">많은 팀에서 테스트 중인 프로젝트를 기반으로 하여 테스트 프로젝트를 구성하며, 프로젝트가 여러 개 있는 애플리케이션의 경우, 특히 각 프로젝트의 테스트 종류에 따라 해당 프로젝트를 여전히 분석하는 경우 많은 테스트 프로젝트를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="23ebc-188">절충 방법으로, 테스트 프로젝트 내에 테스트할 프로젝트(및 클래스)를 나타내는 폴더를 포함하여 애플리케이션마다 테스트 종류별로 하나의 프로젝트를 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="23ebc-189">일반적인 방법은 애플리케이션 프로젝트를 'src' 폴더 아래에 구성하고, 애플리케이션의 테스트 프로젝트를 병렬 'tests' 폴더 아래에 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="23ebc-190">이 구성이 유용할 경우 Visual Studio에서 일치하는 솔루션 폴더를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![솔루션의 테스트 구성](./media/image9-2.png)

<span data-ttu-id="23ebc-192">**그림9-2**</span><span class="sxs-lookup"><span data-stu-id="23ebc-192">**Figure 9-2**.</span></span> <span data-ttu-id="23ebc-193">솔루션의 테스트 구성</span><span class="sxs-lookup"><span data-stu-id="23ebc-193">Test organization in your solution</span></span>

<span data-ttu-id="23ebc-194">원하는 테스트 프레임워크를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="23ebc-195">xUnit 프레임워크는 제대로 작동하며 모든 ASP.NET Core 및 EF Core 테스트가 작성된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="23ebc-196">그림 9-3에 표시된 템플릿을 사용하여 Visual Studio에서 또는 `dotnet new xunit`을 사용하여 CLI에서 xUnit 테스트 프로젝트를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![Visual Studio에서 xUnit 테스트 프로젝트 추가](./media/image9-3.png)

<span data-ttu-id="23ebc-198">**그림 9-3**</span><span class="sxs-lookup"><span data-stu-id="23ebc-198">**Figure 9-3**.</span></span> <span data-ttu-id="23ebc-199">Visual Studio에서 xUnit 테스트 프로젝트 추가</span><span class="sxs-lookup"><span data-stu-id="23ebc-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="23ebc-200">테스트 이름 지정</span><span class="sxs-lookup"><span data-stu-id="23ebc-200">Test naming</span></span>

<span data-ttu-id="23ebc-201">테스트 이름은 일관된 방식으로 각 테스트의 기능을 나타내는 이름으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="23ebc-202">크게 성공한 한 가지 방법은 테스트할 클래스와 메서드에 따라 테스트 클래스의 이름을 지정하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="23ebc-203">이 방법에서는 많은 소규모 테스트 클래스가 만들어지지만 각 테스트에서 수행하는 역할이 매우 명확하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-203">This approach results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="23ebc-204">테스트할 클래스와 메서드를 식별하도록 테스트 클래스 이름을 설정하면 테스트 메서드 이름을 사용하여 테스트할 동작을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-204">With the test class name set up, to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="23ebc-205">이 이름에는 예상되는 동작과 해당 동작을 생성해야 하는 모든 입력이나 가정이 포함되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-205">This name should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="23ebc-206">몇 가지 테스트 이름 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="23ebc-207">이 방법의 변형은 다음과 같이 각 테스트 클래스 이름을 "Should"로 끝내고 시제를 약간 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="23ebc-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="23ebc-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="23ebc-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="23ebc-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="23ebc-210">일부 팀에서는 두 번째 명명 방법이 다소 장황하지만 더 명확하다고 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="23ebc-211">어떤 경우이든 테스트 동작에 대한 통찰력을 제공하는 명명 규칙을 사용하여 하나 이상의 테스트가 실패하는 경우 해당 이름에서 실패한 사례에 대해 분명하게 파악할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="23ebc-212">테스트 결과에서 볼 때 값이 제공되지 않으므로 테스트 이름은 ControllerTests.Test1과 같이 모호하게 지정하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="23ebc-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these names offer no value when you see them in test results.</span></span>

<span data-ttu-id="23ebc-213">많은 소규모 테스트 클래스를 생성하는 위와 같은 명명 규칙을 따르는 경우 폴더와 네임스페이스를 사용하여 테스트를 자세히 구성하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="23ebc-214">그림 9-4에서는 여러 테스트 프로젝트 내에서 폴더별로 테스트를 구성하는 방법 중 하나를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![테스트할 클래스에 따라 폴더별로 테스트 클래스 구성](./media/image9-4.png)

<span data-ttu-id="23ebc-216">**그림 9-4**</span><span class="sxs-lookup"><span data-stu-id="23ebc-216">**Figure 9-4.**</span></span> <span data-ttu-id="23ebc-217">테스트할 클래스에 따라 폴더별로 테스트 클래스 구성</span><span class="sxs-lookup"><span data-stu-id="23ebc-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="23ebc-218">특정 애플리케이션 클래스에 많은 메서드(이에 따라 많은 테스트 클래스)가 있는 경우 애플리케이션 클래스에 해당하는 폴더에 해당 클래스를 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these classes in a folder corresponding to the application class.</span></span> <span data-ttu-id="23ebc-219">이 구성은 다른 위치의 폴더에 파일을 구성하는 방법과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="23ebc-220">다른 파일이 많이 포함된 폴더에 3-4개보다 많은 관련 파일이 있는 경우 해당 파일을 자체의 하위 폴더로 이동하는 것이 도움이 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="23ebc-221">ASP.NET Core 앱 단위 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="23ebc-222">잘 디자인된 ASP.NET Core 애플리케이션에서 대부분의 복잡성과 비즈니스 논리는 비즈니스 엔터티 및 다양한 서비스에 캡슐화됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="23ebc-223">컨트롤러, 필터, viewmodel 및 뷰와 함께 ASP.NET Core MVC 앱 자체에는 단위 테스트가 거의 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require few unit tests.</span></span> <span data-ttu-id="23ebc-224">지정된 작업의 기능 대부분은 작업 메서드 자체의 외부에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="23ebc-225">단위 테스트로는 라우팅 또는 전역 오류 처리가 올바르게 작동하는지 여부를 효과적으로 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-225">Testing whether routing or global error handling work correctly cannot be done effectively with a unit test.</span></span> <span data-ttu-id="23ebc-226">마찬가지로 모델 유효성 검사, 인증 및 권한 부여 필터를 비롯한 모든 필터는 컨트롤러의 동작 메서드를 대상으로 하는 테스트를 사용하여 단위 테스트할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="23ebc-227">이러한 동작 소스가 없는 경우 대부분의 작업 메서드는 사소하게 작아야 하며, 이러한 메서드를 사용하는 컨트롤러와 관계없이 테스트할 수 있는 서비스에 대량의 작업을 위임해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="23ebc-228">단위 테스트를 위해 코드를 리팩터링해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="23ebc-229">이 작업에는 인프라에 대해 직접 코딩하는 대신 테스트하려는 코드의 추상화에 액세스하기 위해 추상화 식별과 종속성 주입 사용이 자주 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-229">Frequently this activity involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="23ebc-230">예를 들어 이미지를 표시하는 다음과 같은 간단한 작업 메서드를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-230">For example, consider this easy action method for displaying images:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

<span data-ttu-id="23ebc-231">이 메서드를 단위 테스트하는 것은 파일 시스템에서 읽는 데 사용하는 `System.IO.File`에 직접 종속되기 때문에 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="23ebc-232">이 동작을 테스트하여 예상대로 작동하는지 확인할 수 있지만, 실제 파일을 사용하여 수행하는 경우 통합 테스트가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="23ebc-233">이 메서드의 경로는 단위 테스트가 불가능하다는 점에 유의해야 합니다. 잠시 후에 기능 테스트를 통해 이 테스트를 수행하는 방법을 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-233">It's worth noting you can't unit test this method's route&mdash;you'll see how to do this testing with a functional test shortly.</span></span>

<span data-ttu-id="23ebc-234">파일 시스템 동작을 직접 단위 테스트할 수 없고 경로를 테스트할 수 없는 경우 테스트할 대상은 무엇일까요?</span><span class="sxs-lookup"><span data-stu-id="23ebc-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="23ebc-235">단위 테스트를 가능하게 하기 위해 리팩터링한 후에 오류 처리와 같은 일부 테스트 사례와 누락된 동작을 발견할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="23ebc-236">파일을 찾을 수 없는 경우 메서드에서 어떻게 할까요?</span><span class="sxs-lookup"><span data-stu-id="23ebc-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="23ebc-237">어떻게 해야 할까요?</span><span class="sxs-lookup"><span data-stu-id="23ebc-237">What should it do?</span></span> <span data-ttu-id="23ebc-238">이 예제에서 리팩터링된 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

<span data-ttu-id="23ebc-239">`_logger`와 `_imageService`는 모두 종속성으로 삽입됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="23ebc-240">이제 작업 메서드에 전달된 동일한 ID가 `_imageService`에 전달되고 결과 바이트가 FileResult의 일부로 반환되는지 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="23ebc-241">또한 오류 로깅이 예상대로 수행되는지, 그리고 이미지가 누락된 경우 중요한 애플리케이션 동작이라고 가정하고(즉, 개발자가 문제를 진단하기 위해 추가한 임시 코드가 아님) `NotFound` 결과가 반환되는지도 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this behavior is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="23ebc-242">실제 파일 논리는 별도의 구현 서비스로 이동되었으며, 누락된 파일의 경우 애플리케이션별 예외를 반환하도록 보강되었습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="23ebc-243">통합 테스트를 사용하여 이 구현을 독립적으로 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="23ebc-244">대부분의 경우에는 컨트롤러에서 글로벌 예외 처리기를 사용합니다. 따라서 논리의 양은 최소화되어야 하고 단위 테스트할 가치가 없을 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="23ebc-245">아래에 설명된 기능 테스트 및 `TestServer` 클래스를 사용하여 컨트롤러 작업의 테스트를 대부분 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="23ebc-246">ASP.NET Core 앱 통합 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="23ebc-247">ASP.NET Core 앱의 통합 테스트는 대부분 인프라 프로젝트에 정의된 서비스 및 다른 구현 형식을 테스트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="23ebc-248">예를 들어 인프라 프로젝트에 상주하는 데이터 액세스 클래스에서 [EF Core가 예상되는 데이터를 성공적으로 업데이트하고 검색했는지 테스트](/ef/core/miscellaneous/testing/)할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="23ebc-249">ASP.NET Core MVC 프로젝트가 올바르게 작동하고 있는지를 테스트하는 가장 좋은 방법은 테스트 호스트에서 실행 중인 앱에서 실행되는 기능 테스트를 사용하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="23ebc-250">ASP.NET Core 앱 기능 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="23ebc-251">ASP.NET Core 애플리케이션의 경우 `TestServer` 클래스를 사용하면 기능 테스트를 매우 쉽게 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="23ebc-252">일반적으로 애플리케이션에서 수행하는 대로 `WebHostBuilder`(또는 `HostBuilder`)를 직접 사용하거나 버전 2.1부터 사용할 수 있는 `WebApplicationFactory` 형식을 사용하여 `TestServer`를 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="23ebc-253">프로덕션 호스트에 테스트 호스트를 최대한 일치시켜야 테스트가 앱이 프로덕션 환경에서 수행하는 것과 유사한 동작을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="23ebc-254">`WebApplicationFactory` 클래스는 ASP.NET Core에서 보기와 같은 정적 리소스를 찾는 데 사용되는 TestServer의 ContentRoot를 구성하는 데 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="23ebc-255">`TEntry`가 웹 애플리케이션의 `Startup` 클래스인 `IClassFixture\<WebApplicationFactory\<TEntry>>`를 구현하는 테스트 클래스를 만들면 간단한 기능 테스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-255">You can create simple functional tests by creating a test class that implements `IClassFixture\<WebApplicationFactory\<TEntry>>`, where `TEntry` is your web application's `Startup` class.</span></span> <span data-ttu-id="23ebc-256">이 인터페이스가 구현되면 테스트 픽스쳐에서 팩터리의 `CreateClient` 메서드를 사용하여 클라이언트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-256">With this interface in place, your test fixture can create a client using the factory's `CreateClient` method:</span></span>

```csharp
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="23ebc-257">각 테스트를 실행하기 전에 메모리 내 데이터 저장소에서 사용할 애플리케이션을 구성한 다음, 테스트 데이터로 애플리케이션을 시드하는 것과 같은 추가적인 사이트 구성을 일부 수행하고자 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in-memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="23ebc-258">이 기능을 구현하려면 `WebApplicationFactory\<TEntry>`의 고유한 서브클래스를 만들고 해당 `ConfigureWebHost` 메서드를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-258">To achieve this functionality, create your own subclass of `WebApplicationFactory\<TEntry>` and override its `ConfigureWebHost` method.</span></span> <span data-ttu-id="23ebc-259">아래 예제에서는 eShopOnWeb FunctionalTests 프로젝트에서 가져온 것으로, 기본 웹 애플리케이션에서 테스트의 일부로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

<span data-ttu-id="23ebc-260">테스트는 이 사용자 지정 WebApplicationFactory를 사용할 수 있습니다. 이를 사용하여 클라이언트를 만든 다음, 이 클라이언트 인스턴스를 사용하는 애플리케이션에 요청을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="23ebc-261">애플리케이션에는 테스트의 어설션의 일부로 사용할 수 있는 시드된 데이터가 생깁니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="23ebc-262">다음 테스트는 eShopOnWeb 애플리케이션의 홈페이지가 올바르게 로드되고 시드 데이터의 일부로 애플리케이션에 추가된 제품 목록이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```csharp
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="23ebc-263">이 기능 테스트는 미리 제공될 수 있는 모든 미들웨어, 필터, 바인더를 포함하여 ASP.NET Core MVC / Razor Pages 애플리케이션 스택 전체를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, and binders that may be in place.</span></span> <span data-ttu-id="23ebc-264">지정된 경로(“/”)가 예상된 성공 상태 코드 및 HTML 출력을 반환하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="23ebc-265">실제 웹 서버를 설정하지 않아도 확인 작업이 수행되므로, 테스트를 위해 실제 웹 서버를 사용할 때 발생할 수 있는 취약성(예: 방화벽 설정 문제)을 대부분 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-265">It does so without setting up a real web server, and avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="23ebc-266">TestServer에 대해 실행되는 기능 테스트는 일반적으로 통합 및 단위 테스트보다 느리지만 네트워크를 통해 테스트 웹 서버에 실행되는 테스트보다 훨씬 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="23ebc-267">애플리케이션의 프런트 엔드 스택이 예상대로 작동되도록 기능 테스트를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="23ebc-268">이러한 테스트는 컨트롤러 또는 페이지에서 중복을 찾거나 필터를 추가하여 중복을 해결하는 경우 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="23ebc-269">이상적으로 이 리팩터링은 애플리케이션의 동작을 변경하지 않으며, 기능 테스트 도구 모음은 이 경우에 해당하는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="23ebc-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="23ebc-270">참조 - ASP.NET Core MVC 앱 테스트</span><span class="sxs-lookup"><span data-stu-id="23ebc-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="23ebc-271">**ASP.NET Core에서 테스트** </span><span class="sxs-lookup"><span data-stu-id="23ebc-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="23ebc-272">**단위 테스트 명명 규칙** </span><span class="sxs-lookup"><span data-stu-id="23ebc-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="23ebc-273">**EF Core 테스트** </span><span class="sxs-lookup"><span data-stu-id="23ebc-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="23ebc-274">**ASP.NET Core의 통합 테스트** </span><span class="sxs-lookup"><span data-stu-id="23ebc-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="23ebc-275">[이전](work-with-data-in-asp-net-core-apps.md)
>[다음](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="23ebc-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
