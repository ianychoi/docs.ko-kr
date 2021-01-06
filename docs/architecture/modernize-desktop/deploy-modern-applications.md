---
title: 최신 데스크톱 애플리케이션 배포
description: 최신 데스크톱 응용 프로그램을 배포 하는 방법에 대해 알아야 할 모든 사항입니다.
ms.date: 05/12/2020
ms.openlocfilehash: 4a4d93caf1c2f8f58d48ee3199bbe6983fa939f4
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2020
ms.locfileid: "97866559"
---
# <a name="deploying-modern-desktop-applications"></a><span data-ttu-id="eee24-103">최신 데스크톱 애플리케이션 배포</span><span class="sxs-lookup"><span data-stu-id="eee24-103">Deploying Modern Desktop Applications</span></span>

<span data-ttu-id="eee24-104">데스크톱 응용 프로그램을 개발할 때 고려해 야 할 한 가지 사항은 응용 프로그램을 패키지 하 고 사용자의 컴퓨터에 배포 하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-104">When you develop desktop applications, one thing to consider is how your application is going to be packaged and deployed to the users' machines.</span></span> <span data-ttu-id="eee24-105">패키징, 배포 및 설치와 관련 된 문제는 일반적으로 개발자와는 다른 작업을 담당 하는 IT 전문가의 포괄적인 부분에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-105">The problem with packaging, deployment, and installation is that it usually falls under the umbrella of the IT professionals, who care about different things than developers.</span></span>

<span data-ttu-id="eee24-106">이러한 일은 개발자와 IT 전문가가 응용 프로그램을 프로덕션 환경으로 이동 하는 데 긴밀 하 게 협력 하는 DevOps 개념에 대해 잘 알고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-106">These days, we're all familiar with the DevOps concept, where developers and IT Pros work closely to move applications to their production environments.</span></span> <span data-ttu-id="eee24-107">그러나 10 년 넘게 바탕 화면에 있는 경우 다음 스토리가 표시 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-107">But if you've been in the desktop battle for more than 10 years, you might have seen the following story.</span></span> <span data-ttu-id="eee24-108">개발자 팀은 프로젝트 마감일을 충족 하기 위해 작업을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-108">A team of developers works together hard to meet the project deadlines.</span></span> <span data-ttu-id="eee24-109">비즈니스 사용자는 회사를 실행 하는 데 많은 사용자의 컴퓨터에서 시스템이 작동 해야 하므로 불안해 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-109">Business people are nervous since they need the system working on many user's machines to run the company.</span></span> <span data-ttu-id="eee24-110">"D 일"에는 프로젝트 관리자가 모든 개발자가 코드를 제대로 작동 하 고 모든 것이 제대로 작동 하는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-110">On "D-Day", the project manager checks with every developer that their code is working well and that everything is fine, so they can ship.</span></span> <span data-ttu-id="eee24-111">그런 다음 패키지 팀은 앱에 대 한 설치 프로그램을 생성 하 고 모든 사용자 컴퓨터에 배포 하 고 응용 프로그램을 실행 하는 테스트 사용자 집합을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-111">Then, the package team comes in generating the setup for the app, distribute it to every user machine and a set of test users run the application.</span></span> <span data-ttu-id="eee24-112">UI를 표시 하기 전에 응용 프로그램에서 "Method ~ object ~ failed" 라는 예외를 throw 하는 경우를 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-112">Well, they try, because before showing any UI, the application throws an exception that says "Method ~ of object ~ failed".</span></span> <span data-ttu-id="eee24-113">비상은 공기를 통해 이동 하 고, 타사 컨트롤을 도입 하 여 "dev 컴퓨터에서 작동" 하는 젊은 및 지 속성이 있는 개발자에 대 한 간략 한 조사 지점도 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-113">Panic starts flowing through the air and a brief investigation points to a young and tired developer that has introduced a third-party control, that certainly "worked on the dev machine".</span></span>

<span data-ttu-id="eee24-114">데스크톱 응용 프로그램을 설치 하는 것은 일반적으로 다음과 같은 두 가지 이유 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-114">Installing desktop applications have traditionally been a nightmare for two main reasons:</span></span>

- <span data-ttu-id="eee24-115">개발 팀과 IT 팀 간의 긴밀 한 공동 작업 문화권이 부족 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-115">Lack of close collaboration culture between dev and IT teams.</span></span>
- <span data-ttu-id="eee24-116">견고한 패키징 및 배포 기술이 부족 하 여 구축할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-116">Lack of a solid packaging and deploying technology we can build upon.</span></span>

<span data-ttu-id="eee24-117">실제로 다음과 같은 이유로 앱을 설치 하는 것이 후회 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-117">In fact, we've been living with the fact that sometimes you regret that you installed an app because:</span></span>

- <span data-ttu-id="eee24-118">컴퓨터에 원치 않는 부작용이 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-118">It ends up having some undesired side effects on your machine.</span></span>
- <span data-ttu-id="eee24-119">이전에 설치 된 일부 응용 프로그램이 작동을 중지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-119">Some applications that were previously installed stop working.</span></span>

<span data-ttu-id="eee24-120">또한 앱을 제거 하 여 시스템을 원래 상태로 복원할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-120">Additionally, you can't just restore the system to its original state by uninstalling the app.</span></span> <span data-ttu-id="eee24-121">Microsoft는 "DLL 연결 설명은" 또는 "Winrot"와 같은 용어를 사용 하 여이 상황을 실시간으로 사용 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-121">We're so used to live this situation that we've coined terms like "DLL Hell" or "Winrot".</span></span>

<span data-ttu-id="eee24-122">이 장에서는 MSIX에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-122">In this chapter, we'll talk about MSIX.</span></span> <span data-ttu-id="eee24-123">MSIX은 향후 패키징 기술에 대 한 견고한 기반을 제공 하기 위해 가장 적합 한 기술을 캡처하기 위해 Microsoft에서 제공 하는 새로운 기술입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-123">MSIX is the brand-new technology from Microsoft that tries to capture the best of previous technologies to provide a solid foundation for the packaging technology of the future.</span></span>

<span data-ttu-id="eee24-124">현대화를 사용 하 여 패키징 기술은 어떻게 해야 하나요?</span><span class="sxs-lookup"><span data-stu-id="eee24-124">What does a packaging technology have to do with modernization?</span></span> <span data-ttu-id="eee24-125">이는 많은 돈을 투자 하는 기업에 대 한 기본 패키징을 포함 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-125">Well, it turns out that packaging is fundamental for the enterprise IT with lots of money invested there.</span></span> <span data-ttu-id="eee24-126">현대화는 최신 기술을 사용 하는 것과 관련이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-126">Modernization isn't only related to using the latest technologies.</span></span> <span data-ttu-id="eee24-127">또한 회사에서 클라이언트에 기능을 제공 하기 전 까지는 비즈니스 요구 사항이 정의 된 순간 출시 시간을 단축 하는 것과 관련이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-127">It's also related to reducing time to market from the moment a business requirement is defined until your company delivers the feature to your client.</span></span>

## <a name="the-modern-application-lifecycle"></a><span data-ttu-id="eee24-128">최신 응용 프로그램 수명 주기</span><span class="sxs-lookup"><span data-stu-id="eee24-128">The modern application lifecycle</span></span>

<span data-ttu-id="eee24-129">오늘날 개발자는 앱에 대 한 코드를 작성 하 고 빌드한 다음 생성 된 자산을 IT 전문가에 게 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-129">Today, developers write and build the code for an app and then pass the generated assets to the IT Pros.</span></span> <span data-ttu-id="eee24-130">그런 다음, IT 전문가는 앱을 다시 구성 하 고 일반적으로 MSI 이상에서 App-v 패키징 형식으로 앱을 다시 패키지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-130">Then, the IT Pros reconfigure the app and repackage it, typically in an MSI or more recently in an App-V packaging format.</span></span> <span data-ttu-id="eee24-131">그러면 앱이 다른 채널 및 도구를 통해 배포 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-131">The app is then deployed through different channels and tools.</span></span> <span data-ttu-id="eee24-132">이 방법의 주요 문제 중 하나는 일반적으로 "패키징 paralysis" 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-132">One of the main problems with this approach is commonly known as "packaging paralysis".</span></span> <span data-ttu-id="eee24-133">문제는 앱 업데이트 또는 OS 업데이트가 있을 때마다이 주기가 반복 된다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-133">The problem is that this cycle repeats every time there's an app update or an OS update.</span></span>

<span data-ttu-id="eee24-134">다음 그림에 반영 된 프로세스를 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-134">You can see the process reflected on the following picture:</span></span>

![최신 IT 수명 주기를 보여 주는 다이어그램](./media/deploy-modern-applications/modern-it-application-lifecycle.png)

<span data-ttu-id="eee24-136">회사에서이 패키징 주기를 세 개의 독립 주기로 분리 하는 방법이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-136">Companies need a way to break this packaging cycle into three independent cycles:</span></span>

- <span data-ttu-id="eee24-137">OS 업데이트</span><span class="sxs-lookup"><span data-stu-id="eee24-137">OS updates</span></span>
- <span data-ttu-id="eee24-138">애플리케이션 업데이트</span><span class="sxs-lookup"><span data-stu-id="eee24-138">Application updates</span></span>
- <span data-ttu-id="eee24-139">사용자 지정</span><span class="sxs-lookup"><span data-stu-id="eee24-139">Customization</span></span>

![최신 IT 고리가 만들어집니다 주기를 보여 주는 다이어그램](./media/deploy-modern-applications/modern-it-virtuous-cycle.png)

<span data-ttu-id="eee24-141">위의 다이어그램은 다음 작업을 수행할 수 있음을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-141">The previous diagram shows that you can:</span></span>

- <span data-ttu-id="eee24-142">앱을 다시 패키지 하지 않고도 기본 OS를 업데이트 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-142">Update the underlying OS without having to repackage your apps.</span></span>
- <span data-ttu-id="eee24-143">원래 개발자 패키지를 다시 패키징할 필요 없이 사용자 지정 항목을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-143">Enable customizations from IT without the need to repackage the original developer package.</span></span>

<span data-ttu-id="eee24-144">이러한 변화는 다음 그림과 같이 새로운 최신 IT 수명 주기를 초래 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-144">This radical change leads us to the new and modern IT lifecycle as shown in the following picture:</span></span>

![Microsoft 도구를 사용 하 여 응용 프로그램 수명 주기를 보여 주는 다이어그램](./media/deploy-modern-applications/microsoft-it-tools.png)

<span data-ttu-id="eee24-146">개발자는 앱을 만들고 IT 전문가가 다시 패키지 필요 없이 사용 하 고 구성할 수 있는 MSIX 패키지를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-146">Developers create the app and generate an MSIX package that IT Pros can consume and configure without the need of repackaging.</span></span> <span data-ttu-id="eee24-147">Microsoft는 MSIX 기술과 함께 다시 패키지 없이 패키지를 사용자 지정 하 고 구성할 수 있도록 하는 도구를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-147">Along with the MSIX technology, Microsoft has created tools to allow IT to customize and configure packages without repackaging.</span></span>

## <a name="msix-the-next-generation-of-deployment"></a><span data-ttu-id="eee24-148">MSIX: 차세대 배포</span><span class="sxs-lookup"><span data-stu-id="eee24-148">MSIX: The next generation of deployment</span></span>

<span data-ttu-id="eee24-149">MSIX 이전에는 설치 마법사, MSI, ClickOnce, App-v 및 스크립팅과 같은 몇 가지 패키징 기술을 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-149">Before MSIX, there were several packaging technologies available like setup wizards, MSI, ClickOnce, App-V, and scripting.</span></span> <span data-ttu-id="eee24-150">이러한 각 기술에는 고유한 장단점이 있으며 Microsoft는 MSIX 빌드에 가장 적합 한 것을 선택 하기로 결정 했습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-150">Each of these technologies has their own strengths and Microsoft has decided to pick the best of all to build MSIX.</span></span> <span data-ttu-id="eee24-151">MSIX은 이러한 기존 기술의 기초를 기반으로 하 여 가장 적합 한 기술을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-151">MSIX is built on the foundations of these existing technologies picking the best of each:</span></span>

- <span data-ttu-id="eee24-152">App-v = \> 컨테이너 화</span><span class="sxs-lookup"><span data-stu-id="eee24-152">App-V =\> Containerization</span></span>
- <span data-ttu-id="eee24-153">ClickOnce = \> 자동 업데이트</span><span class="sxs-lookup"><span data-stu-id="eee24-153">ClickOnce =\> Auto updating</span></span>
- <span data-ttu-id="eee24-154">MSI = \> 쉽게 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-154">MSI =\> Easy to distribute</span></span>

<span data-ttu-id="eee24-155">MSIX을 사용 하면 모든 기능을 갖춘 하나의 설치 관리자 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-155">With MSIX, you get one installer technology with all these features.</span></span>

![MSIX 빌드에 영향을 미치는 다양 한 기술을 보여 주는 다이어그램](./media/deploy-modern-applications/msix.png)

### <a name="benefits-of-msix"></a><span data-ttu-id="eee24-157">MSIX의 이점</span><span class="sxs-lookup"><span data-stu-id="eee24-157">Benefits of MSIX</span></span>

#### <a name="never-regret-installing-an-app"></a><span data-ttu-id="eee24-158">앱 설치를 후회 하지 않음</span><span class="sxs-lookup"><span data-stu-id="eee24-158">Never regret installing an app</span></span>

<span data-ttu-id="eee24-159">MSIX은 예측 가능 하 고 안정적 이며 안전한 배포를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-159">MSIX provides a predictable, reliable, and safe deployment.</span></span> <span data-ttu-id="eee24-160">패키지 매니페스트에 포함 된 선언적 메서드를 통해 OS는 응용 프로그램에 필요한 모든 자산을 추적할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-160">The declarative method contained in the package manifest lets the OS keep track of every asset your application needs.</span></span> <span data-ttu-id="eee24-161">또한 부작용 없이 진정한 정리 제거를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-161">It also provides a true clean uninstall with no side effects.</span></span>

#### <a name="disk-space-optimization"></a><span data-ttu-id="eee24-162">디스크 공간 최적화</span><span class="sxs-lookup"><span data-stu-id="eee24-162">Disk space optimization</span></span>

<span data-ttu-id="eee24-163">MSIX은 사용자의 컴퓨터 디스크 공간에 대 한 응용 프로그램의 공간을 줄이기 위해 최적화 되었습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-163">MSIX is optimized to reduce the footprint that an application has on the user's machine disk space.</span></span> <span data-ttu-id="eee24-164">파일의 단일 인스턴스 저장소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-164">It creates a single instance storage of your files.</span></span> <span data-ttu-id="eee24-165">즉, DLL이 같은 두 개의 다른 패키지가 있는 경우 DLL은 두 번 설치 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-165">That is, if you have two different packages with the same DLL, the DLL isn't installed twice.</span></span> <span data-ttu-id="eee24-166">플랫폼은 특정 앱이 설치 된 모든 파일을 선언적 특성에 대해 알고 있으므로 해당 문제를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-166">The platform takes care of that problem because it knows all the files that a particular app installed thanks to its declarative nature.</span></span> <span data-ttu-id="eee24-167">또한 다른 버전의 DLL을 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-167">It also allows you to have different versions of a DLL working side by side.</span></span>

<span data-ttu-id="eee24-168">리소스 패키지를 사용 하면 다국어 앱을 쉽게 만들 수 있으며, OS는 사용 되는 앱을 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-168">With the use of resource packages, you can easily create multilingual apps and the OS takes care of installing the ones that are used.</span></span>

#### <a name="network-optimization"></a><span data-ttu-id="eee24-169">네트워크 최적화</span><span class="sxs-lookup"><span data-stu-id="eee24-169">Network optimization</span></span>

<span data-ttu-id="eee24-170">MSIX은 차등 업데이트 라는 기능을 사용 하도록 설정 하는 바이트 블록 수준에서 파일의 차이점을 감지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-170">MSIX detects the differences on the files at the byte block level enabling a feature called differential updates.</span></span> <span data-ttu-id="eee24-171">즉, 업데이트 된 바이트 블록만 응용 프로그램 업데이트에서 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-171">What this means is that only the updated byte blocks are downloaded on application updates.</span></span>

![MSIX에서 차등 업데이트를 관리 하는 방법을 보여 주는 다이어그램](./media/deploy-modern-applications/msix-managing-updates.png)

<span data-ttu-id="eee24-173">스트리밍 설치를 사용 하면 앱의 다른 부분이 백그라운드에서 다운로드 되는 동안 사용자가 신속 하 게 응용 프로그램에 대 한 작업을 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-173">With streaming installation, the user can quickly start working on your application while other parts of the app are downloaded on the background.</span></span> <span data-ttu-id="eee24-174">이 기능은 사용자에 게 매력적인 경험을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-174">This feature contributes to an engaging experience for your users.</span></span>

<span data-ttu-id="eee24-175">선택적 패키지 기능을 사용 하면 앱 배포에 대 한 구성 요소화를 달성할 수 있으므로 필요할 때 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-175">With the optional packages feature, you achieve componentization on your app deployment, so you can download them when needed.</span></span>

#### <a name="simple-packaging-and-deployment"></a><span data-ttu-id="eee24-176">간단한 패키징 및 배포</span><span class="sxs-lookup"><span data-stu-id="eee24-176">Simple packaging and deployment</span></span>

<span data-ttu-id="eee24-177">AppManifest는 모든 응용 프로그램에 대 한 표준 방식으로 버전 관리, 장치 대상 지정 및 식별을 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-177">The AppManifest declares the versioning, device targeting and identify in a standard way for every application.</span></span> <span data-ttu-id="eee24-178">또한 견고한 보안 기반을 제공 하는 자산에 서명 하는 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-178">It also provides a way to sign your assets providing a solid security foundation.</span></span>

#### <a name="os-managed"></a><span data-ttu-id="eee24-179">운영 체제 관리</span><span class="sxs-lookup"><span data-stu-id="eee24-179">OS managed</span></span>

<span data-ttu-id="eee24-180">OS는 응용 프로그램을 설치, 업데이트 및 제거 하는 모든 프로세스를 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-180">The OS handles all the processes for installing, updating, and removing an application.</span></span> <span data-ttu-id="eee24-181">응용 프로그램은 사용자별로 설치 되지만 디스크 공간을 최소화 하 여 한 번만 다운로드 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-181">Applications are installed per user but downloaded only once, minimizing the disk footprint.</span></span> <span data-ttu-id="eee24-182">Microsoft는 Windows 7 에서도 MSIX 환경을 제공 하기 위해 노력 하 고 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-182">Microsoft is working on providing the MSIX experience also on Windows 7.</span></span>

#### <a name="windows-provides-integrity-for-the-app"></a><span data-ttu-id="eee24-183">Windows에서 앱의 무결성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-183">Windows provides integrity for the app</span></span>

<span data-ttu-id="eee24-184">디지털 서명을 사용 하 여 신뢰할 수 없는 소스에서 응용 프로그램을 설치 하지 않도록 보장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-184">With the use of digital signatures, you can guarantee that you don't install an application from untrusted sources.</span></span> <span data-ttu-id="eee24-185">MSIX은 다음과 같은 경우에도 변조를 방지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-185">MSIX also prevents tampering because:</span></span>

- <span data-ttu-id="eee24-186">파일 해시에 대 한 레코드를 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-186">It keeps a record of file hashes.</span></span>
- <span data-ttu-id="eee24-187">설치 후 파일이 수정 되었는지 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-187">It detects if a file has been modified after installation.</span></span>

#### <a name="works-for-the-entire-app-catalog"></a><span data-ttu-id="eee24-188">전체 앱 카탈로그에 대해 작동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-188">Works for the entire App Catalog</span></span>

<span data-ttu-id="eee24-189">가장 멋진에 대 한 정보 중 하나는 전체 응용 프로그램 카탈로그, Windows Forms, WPF, MFC/ATL, Delphi에 대해 작동 한다는 것입니다. xCopy 배포를 수행 하거나 스토어로 이동 하려는 경우에도 동일한 MSIX 패키지를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-189">One of the coolest things about MSIX is that it works for the entire application catalog, Windows Forms, WPF, MFC/ATL, Delphi, even if you want to do xCopy deployment, ClickOnce, or going to the Store, you can use the same MSIX package.</span></span>

### <a name="tools"></a><span data-ttu-id="eee24-190">도구</span><span class="sxs-lookup"><span data-stu-id="eee24-190">Tools</span></span>

#### <a name="windows-application-packaging-project"></a><span data-ttu-id="eee24-191">Windows 애플리케이션 패키징 프로젝트</span><span class="sxs-lookup"><span data-stu-id="eee24-191">Windows Application Packaging Project</span></span>

<span data-ttu-id="eee24-192">Visual Studio에서 **Windows 응용 프로그램 패키징 프로젝트**   프로젝트를 사용 하 여 데스크톱 앱에 대 한 패키지를 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-192">You can use the **Windows Application Packaging Project** project in Visual Studio to generate a package for your desktop app.</span></span> <span data-ttu-id="eee24-193">그런 다음 해당 패키지를 Microsoft Store에 게시 하거나 하나 이상의 Pc로 테스트용으로 로드 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-193">Then, you can publish that package to the Microsoft Store or sideload it onto one or more PCs.</span></span>

#### <a name="msix-packaging-tool"></a><span data-ttu-id="eee24-194">MSIX Packaging Tool</span><span class="sxs-lookup"><span data-stu-id="eee24-194">MSIX Packaging Tool</span></span>

<span data-ttu-id="eee24-195">MSIX 패키징 도구를 사용하면 기존 Win32 애플리케이션을 MSIX 형식으로 다시 패키지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-195">The MSIX Packaging Tool enables you to repackage your existing Win32 applications to the MSIX format.</span></span> <span data-ttu-id="eee24-196">이 메서드는 변환을 위해 대화형 UI와 명령줄을 모두 제공 하며 소스 코드 없이 응용 프로그램을 변환 하는 기능을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-196">It offers both an interactive UI and a command line for conversions and gives you the ability to convert an application without having the source code.</span></span>

![MSIX Packaging Tool](./media/deploy-modern-applications/msix-packaging-tool.png)

#### <a name="package-support-framework"></a><span data-ttu-id="eee24-198">패키지 지원 프레임워크</span><span class="sxs-lookup"><span data-stu-id="eee24-198">Package Support Framework</span></span>

<span data-ttu-id="eee24-199">패키지 지원 프레임 워크는 MSIX 컨테이너에서 실행 될 수 있도록 원본 코드에 대 한 액세스 권한이 없는 경우 기존 Win32 응용 프로그램에 수정 사항을 적용 하는 데 도움이 되는 오픈 소스 키트입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-199">The Package Support Framework is an open-source kit that helps you apply fixes to your existing Win32 application when you don't have access to the source code, so that it can run in an MSIX container.</span></span> <span data-ttu-id="eee24-200">패키지 지원 프레임워크는 애플리케이션이 최신 런타임 환경의 모범 사례를 수행하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-200">The Package Support Framework helps your application follow the best practices of the modern runtime environment.</span></span>

#### <a name="app-installer"></a><span data-ttu-id="eee24-201">앱 설치 관리자</span><span class="sxs-lookup"><span data-stu-id="eee24-201">App Installer</span></span>

<span data-ttu-id="eee24-202">앱 설치 관리자를 사용 하면 앱 패키지를 두 번 클릭 하 여 Windows 10 앱을 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-202">App Installer allows Windows 10 apps to be installed by double-clicking the app package.</span></span> <span data-ttu-id="eee24-203">즉, 사용자가 PowerShell 또는 다른 개발자 도구를 사용 하 여 Windows 10 앱을 배포할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-203">This means that users don't need to use PowerShell or other developer tools to deploy Windows 10 apps.</span></span> <span data-ttu-id="eee24-204">앱 설치 관리자는 웹, 선택적 패키지 및 관련 집합에서 앱을 설치할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-204">The App Installer can also install an app from the web, optional packages, and related sets.</span></span>

## <a name="how-to-create-an-msix-package-from-an-existing-win32-desktop-application"></a><span data-ttu-id="eee24-205">기존 Win32 데스크톱 응용 프로그램에서 MSIX 패키지를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="eee24-205">How to create an MSIX package from an existing Win32 desktop application</span></span>

<span data-ttu-id="eee24-206">기존 Win32 응용 프로그램에서 MSIX 패키지를 만드는 프로세스를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-206">Let's go through the process to create an MSIX package from an existing Win32 application.</span></span> <span data-ttu-id="eee24-207">이 예제에서는 Windows Forms 앱을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-207">In this example, we'll use a Windows Forms app.</span></span>

<span data-ttu-id="eee24-208">시작 하려면 솔루션에 새 프로젝트를 추가 하 고 Windows 응용 프로그램 패키징 프로젝트를 선택한 다음 이름을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-208">To start, add a new project to your solution, select the Windows Application Packaging Project, and give it a name.</span></span>

![새 Windows 응용 프로그램 패키징 프로젝트 추가](./media/deploy-modern-applications/add-packaging-project.png)

<span data-ttu-id="eee24-210">패키징 프로젝트의 구조가 표시 되 고 *응용 프로그램* 이라는 특수 폴더가 기록 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-210">You'll see the structure of the packaging project and note a special folder called *Applications*.</span></span> <span data-ttu-id="eee24-211">이 폴더 내에서 패키지에 포함 하려는 응용 프로그램을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-211">Inside this folder, you can specify which applications you want to include in the package.</span></span> <span data-ttu-id="eee24-212">둘 이상이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-212">It can be more than one.</span></span>

![패키징 프로젝트의 구조](./media/deploy-modern-applications/packaging-project.png)

<span data-ttu-id="eee24-214">*응용 프로그램* 폴더를 마우스 오른쪽 단추로 클릭 하 고 Visual Studio 솔루션에서 패키지할 Windows Forms 프로젝트를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-214">Right-click on the *Applications* folder and select the Windows Forms project you want to package from the Visual Studio solution.</span></span>

![패키징 프로젝트에 Windows Forms 프로젝트 추가](./media/deploy-modern-applications/add-winforms-project.png)

<span data-ttu-id="eee24-216">이 시점에서 패키지를 컴파일 및 생성할 수 있지만 몇 가지를 살펴보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-216">At this point, you can compile and generate the package but let's examine a couple of things.</span></span> <span data-ttu-id="eee24-217">사용자 환경을 개선 하기 위해 Visual Studio는 최신 응용 프로그램이 타일 표시줄과 시작 메뉴의 아이콘 및 타일 자산을 처리 하는 데 필요한 모든 시각적 자산을 자동으로 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-217">To have a better user experience, Visual Studio can autogenerate all the visual assets a modern application needs to handle icons and tile assets for the tile bar and start menu.</span></span> <span data-ttu-id="eee24-218">*Appxmanifest.xml* 파일을 열어 매니페스트 디자이너에 액세스 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-218">Open the *Package.appxmanifest* file to access the Manifest Designer.</span></span> <span data-ttu-id="eee24-219">그런 다음 **만들기** 를 클릭 하 여 프로젝트에 있는 지정 된 이미지에서 모든 시각적 자산을 생성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-219">You can then generate all the visual assets from a given image present on your project just by clicking **Create**.</span></span>

![Visual Studio의 매니페스트 디자이너 스크린샷](./media/deploy-modern-applications/manifest-designer.png)

<span data-ttu-id="eee24-221">*Appxmanifest.xml* 파일에 대 한 코드를 열면 몇 가지 흥미로운 작업을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-221">If you open the code for the *Package.appxmanifest* file, you can see a couple of interesting things.</span></span>

<span data-ttu-id="eee24-222">오른쪽 `<Package>` 에는 `<Identity>` 노드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-222">Right under `<Package>`, there's an `<Identity>` node.</span></span> <span data-ttu-id="eee24-223">패키지 응용 프로그램에서 해당 id를 가져오는 위치입니다 .이 위치는 OS에서 관리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-223">This is where your packaged application is going to get its identity, which will be managed by the OS.</span></span>

![Id 노드](./media/deploy-modern-applications/identity-node.png)

<span data-ttu-id="eee24-225">`<Capabilities>`노드에서는 응용 프로그램에 필요한 모든 요구 사항을 찾을 수 있습니다 .이는 `<rescap:Capability Name="runFullTrust" \>` Win32 응용 프로그램 이므로 완전 신뢰 모드로 앱을 실행 하도록 OS에 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-225">In the `<Capabilities>` node, you can find all the requirements the application needs, paying special attention to the `<rescap:Capability Name="runFullTrust" \>`, which tells the OS to run the app in full trust mode since it's a Win32 application.</span></span>

![기능 노드](./media/deploy-modern-applications/capabilities-node.png)

<span data-ttu-id="eee24-227">패키징 프로젝트를 솔루션의 시작 프로젝트로 설정 하 고 *실행* 을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-227">Set the packaging project as the startup project for the solution and select *Run*.</span></span> <span data-ttu-id="eee24-228">다음으로 이동 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-228">This is going to:</span></span>

- <span data-ttu-id="eee24-229">Windows Forms 응용 프로그램을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-229">Compile the Windows Forms application.</span></span>
- <span data-ttu-id="eee24-230">빌드 결과에서 MSIX 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-230">Create an MSIX package out of the build results.</span></span>
- <span data-ttu-id="eee24-231">패키지를 배포 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-231">Deploy the packages.</span></span>
- <span data-ttu-id="eee24-232">개발 컴퓨터에 로컬로 설치 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-232">Install it locally on the development machine.</span></span>
- <span data-ttu-id="eee24-233">앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-233">Launch the app.</span></span>

![설치 된 응용 프로그램](./media/deploy-modern-applications/our-installed-application.png)

<span data-ttu-id="eee24-235">이를 통해 MSIX에서 Windows 10에 완전히 통합 된 기능을 새로 설치 하 고 제거 하는 환경을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-235">With this, you have the clean install and uninstall experience that MSIX provides fully integrated into Windows 10.</span></span>

<span data-ttu-id="eee24-236">최종 단계는 MSIX 패키지를 다른 컴퓨터에 배포 하는 방법에 대 한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-236">The final stage is about how you deploy the MSIX package to another machine.</span></span>

<span data-ttu-id="eee24-237">패키징 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **스토어** 메뉴를 선택한 다음 **앱 패키지 만들기** 옵션을 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-237">Right-click on the packaging project, select the **Store** menu, and then select the **Create App Packages** option.</span></span>

<span data-ttu-id="eee24-238">그런 다음 패키지를 만들어 저장소에 업로드 하거나 테스트용 로드에 대 한 패키지를 만들 때 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-238">Then, you can choose between creating a package to upload to the store or creating packages for sideloading.</span></span> <span data-ttu-id="eee24-239">대부분의 현대화 시나리오에서 **테스트용 로드에 대 한 패키지를 만들려는** 경우를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-239">In most modernization scenarios, you'll choose **I want to create packages for sideloading**.</span></span>

![패키지 구성](./media/deploy-modern-applications/configuring-packages.png)

<span data-ttu-id="eee24-241">여기서 원하는 수 만큼 동일한 MSIX 패키지에 포함할 수 있으므로 대상으로 지정할 아키텍처를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-241">There you can select the different architectures you want to target as you can include as many as you want into the same MSIX package.</span></span>

<span data-ttu-id="eee24-242">마지막 단계는 최종 설치 자산을 배포할 위치를 선언 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-242">The final step is to declare where you want to deploy the final installation assets.</span></span>

![업데이트 설정 구성](./media/deploy-modern-applications/configure-update-settings.png)

<span data-ttu-id="eee24-244">엔터프라이즈 파일 서버에서 공유 UNC 경로의 웹 서버를 사용 하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-244">You can choose to use a web server of a shared UNC path on your enterprise file servers.</span></span> <span data-ttu-id="eee24-245">응용 프로그램을 업데이트 하는 방법을 지정 하려면 설정에 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-245">Pay attention to the settings to specify how you want to update your application.</span></span> <span data-ttu-id="eee24-246">응용 프로그램 업데이트에 대해서는 다음 섹션에서 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-246">We'll cover application updates in the next section.</span></span>

<span data-ttu-id="eee24-247">자세한 단계별 가이드는 [Visual Studio를 사용 하 여 소스 코드에서 데스크톱 앱 패키지](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="eee24-247">For a detailed step-by-step guide, see [Package a desktop app from source code using Visual Studio](/windows/msix/desktop/desktop-to-uwp-packaging-dot-net).</span></span>

## <a name="auto-updates-in-msix"></a><span data-ttu-id="eee24-248">MSIX의 자동 업데이트</span><span class="sxs-lookup"><span data-stu-id="eee24-248">Auto Updates in MSIX</span></span>

<span data-ttu-id="eee24-249">Windows 스토어에는 Windows 업데이트를 사용 하는 뛰어난 업데이트 메커니즘이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-249">The Windows Store has a great updating mechanism using Windows Update.</span></span> <span data-ttu-id="eee24-250">대부분의 엔터프라이즈 시나리오에서는 저장소를 사용 하 여 데스크톱 앱을 배포 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-250">In most enterprise scenarios, you don't use the Store to distribute your desktop apps.</span></span> <span data-ttu-id="eee24-251">따라서 응용 프로그램에 대 한 업데이트를 구성 하 고 사용자에 게 풀 하는 비슷한 방법이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-251">So, you need a similar way to configure updates for your application and pull them to your users.</span></span>

<span data-ttu-id="eee24-252">Windows 10 기능 및 MSIX 패키지의 조합을 사용 하 여 사용자에 게 뛰어난 업데이트 환경을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-252">Using a combination of Windows 10 features and MSIX packages, you can provide a great updating experience for your users.</span></span> <span data-ttu-id="eee24-253">실제로 사용자는 기술적으로는 필요 하지 않지만 원활한 응용 프로그램 업데이트 환경을 활용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-253">In fact, the user doesn't need to be technical at all but still benefit from a seamless application update experience.</span></span>

<span data-ttu-id="eee24-254">두 가지 방법으로 사용자와 상호 작용 하도록 업데이트를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-254">You can configure your updates to interact with the user in two different ways:</span></span>

- <span data-ttu-id="eee24-255">사용자에 게 메시지를 표시 합니다.: OS는 응용 프로그램의 설치 여부를 사용자에 게 알리기 위해 자동 생성 된 유용한 UI를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-255">User prompted updates: The OS shows some autogenerated nice UI to notify the user about the application is about to install.</span></span> <span data-ttu-id="eee24-256">설치 파일에 지정 하는 속성을 기반으로이 UI를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-256">It builds this UI based on the properties you specify on your installation files.</span></span>

- <span data-ttu-id="eee24-257">백그라운드에서 자동 업데이트.</span><span class="sxs-lookup"><span data-stu-id="eee24-257">Silent updates in the background.</span></span> <span data-ttu-id="eee24-258">이 옵션을 사용 하면 사용자가 업데이트를 인식할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-258">With this option, your users don't need to be aware of the updates.</span></span>

<span data-ttu-id="eee24-259">응용 프로그램이 시작 되거나 정기적으로 업데이트를 수행 하려는 시기를 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-259">You can also configure when you want to perform updates, when the application launches or on a regular basis.</span></span> <span data-ttu-id="eee24-260">테스트용 로드 기능 덕분에 응용 프로그램이 실행 되는 동안에도 이러한 업데이트를 얻을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-260">Thanks to the side-loading features, you can even get these updates while the application is running.</span></span>

<span data-ttu-id="eee24-261">이러한 유형의 배포를 사용 하는 경우 특수 파일을 *appinstaller 라고 합니다.*</span><span class="sxs-lookup"><span data-stu-id="eee24-261">When you use this type of deployment, a special file is created called *.appinstaller*.</span></span> <span data-ttu-id="eee24-262">이 간단한 파일에는 다음과 같은 섹션이 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-262">This simple file contains the following sections:</span></span>

- <span data-ttu-id="eee24-263">Appinstaller 파일의 위치입니다 *.*</span><span class="sxs-lookup"><span data-stu-id="eee24-263">The location of the *.appinstaller* file</span></span>
- <span data-ttu-id="eee24-264">응용 프로그램의 기본 MSIX 패키지 속성</span><span class="sxs-lookup"><span data-stu-id="eee24-264">The application's main MSIX package properties</span></span>
- <span data-ttu-id="eee24-265">업데이트 동작</span><span class="sxs-lookup"><span data-stu-id="eee24-265">The update behavior</span></span>

![. appinstaller 파일](./media/deploy-modern-applications/appinstaller-file.png)

<span data-ttu-id="eee24-267">이 파일과 함께 Microsoft는 특정 URL 프로토콜을 설계 하 여 링크에서 설치 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-267">In combination with this file, Microsoft has designed a special URL protocol to launch the installation process from a link:</span></span>

```xml
<a href="ms-appinstaller:?source=http://mywebservice.azureedge.net/MyApp.msix">Install app package </a>
```

<span data-ttu-id="eee24-268">이 프로토콜은 모든 브라우저에서 작동 하 고 Windows 10에서 뛰어난 사용자 환경을 사용 하 여 설치 프로세스를 시작 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-268">This protocol works on all browsers and launches the installation process with a great user experience on Windows 10.</span></span> <span data-ttu-id="eee24-269">OS는 설치 프로세스를 관리 하므로이 응용 프로그램이 설치 된 위치를 인식 하 고 프로세스의 영향을 받는 모든 파일을 추적 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-269">Since the OS manages the installation process, it's aware of the location this application was installed from and tracks all the files affected by the process.</span></span>

<span data-ttu-id="eee24-270">MSIX은 설치를 위한 사용자 인터페이스를 만들어 패키지의 일부 속성을 자동으로 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-270">MSIX creates a user interface for installation automatically showing some properties of the package.</span></span> <span data-ttu-id="eee24-271">이를 통해 모든 앱에 대해 공통적인 설치 환경을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-271">This allows for a common installation experience for every app.</span></span>

<span data-ttu-id="eee24-272">새 MSIX 패키지를 생성 하 고 배포 서버로 옮긴 후에는 *appinstaller* 파일을 편집 하 여 이러한 변경 내용을 반영 해야 합니다 .이는 주로 새 msix 파일의 버전과 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-272">Once you've generated the new MSIX package and moved it to the deployment server, you just have to edit the *.appinstaller* file to reflect these changes, mainly the version and the path to the new MSIX file.</span></span> <span data-ttu-id="eee24-273">다음에 사용자가 응용 프로그램을 시작할 때 시스템은 변경 내용을 검색 하 고 새 버전에 대 한 파일을 백그라운드에서 다운로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-273">The next time the user launches the application, the system is going to detect the change and download the files for the new version in the background.</span></span> <span data-ttu-id="eee24-274">이 작업이 완료 되 면 새 응용 프로그램이 사용자에 대해 투명 하 게 실행 될 때 설치가 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eee24-274">When this is done, installation will execute on new application launch transparently for your user.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="eee24-275">이전</span><span class="sxs-lookup"><span data-stu-id="eee24-275">Previous</span></span>](example-migration-core.md)
