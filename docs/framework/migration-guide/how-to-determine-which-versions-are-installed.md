---
title: 설치된 .NET Framework 버전 확인
description: 코드, regedit.exe 또는 PowerShell을 사용하여 Windows 레지스트리를 쿼리하는 방법으로 컴퓨터에 설치된 .NET Framework 버전을 검색합니다.
ms.date: 02/03/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
ms.openlocfilehash: f4cb85e346e0043a3f28c48845f574afa89548db
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673360"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a><span data-ttu-id="ccd41-103">방법: 설치된 .NET Framework 버전 확인</span><span class="sxs-lookup"><span data-stu-id="ccd41-103">How to: Determine which .NET Framework versions are installed</span></span>

<span data-ttu-id="ccd41-104">사용자는 컴퓨터에 여러 버전의 .NET Framework를 [설치](../install/index.md)하여 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-104">Users can [install](../install/index.md) and run multiple versions of .NET Framework on their computers.</span></span> <span data-ttu-id="ccd41-105">따라서 앱을 개발하거나 배포할 때 사용자 컴퓨터에 설치된 .NET Framework 버전을 알아야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-105">When you develop or deploy your app, you might need to know which .NET Framework versions are installed on the user's computer.</span></span> <span data-ttu-id="ccd41-106">레지스트리에는 컴퓨터에 설치된 .NET Framework 버전 목록이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-106">The registry contains a list of the versions of .NET Framework installed on the computer.</span></span>

<span data-ttu-id="ccd41-107">.NET Framework는 버전이 별도로 관리되는 다음 두 가지 주요 구성 요소로 이루어져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-107">.NET Framework consists of two main components, which are versioned separately:</span></span>

- <span data-ttu-id="ccd41-108">앱의 기능을 제공하는 형식 및 리소스 컬렉션에 해당하는 어셈블리 집합.</span><span class="sxs-lookup"><span data-stu-id="ccd41-108">A set of assemblies, which are collections of types and resources that provide the functionality for your apps.</span></span> <span data-ttu-id="ccd41-109">.NET Framework와 어셈블리는 동일한 버전 번호를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-109">.NET Framework and the assemblies share the same version number.</span></span> <span data-ttu-id="ccd41-110">예를 들어, .NET Framework 버전에는 4.5, 4.6.1, 4.7.2가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-110">For example, .NET Framework versions include 4.5, 4.6.1, and 4.7.2.</span></span>

- <span data-ttu-id="ccd41-111">앱 코드를 관리하고 실행하는 CLR(공용 언어 런타임).</span><span class="sxs-lookup"><span data-stu-id="ccd41-111">The common language runtime (CLR), which manages and executes your app's code.</span></span> <span data-ttu-id="ccd41-112">하나의 CLR 버전이 여러 개의.NET Framework 버전을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-112">A single CLR version typically supports multiple .NET Framework versions.</span></span> <span data-ttu-id="ccd41-113">예를 들어 CLR 버전이 4.0.30319.‘xxxxx’이고 ‘xxxxx’가 42000보다 작은 경우 .NET Framework 버전 4~4.5.2를 지원합니다. </span><span class="sxs-lookup"><span data-stu-id="ccd41-113">For example, CLR version 4.0.30319.*xxxxx* where *xxxxx* is less than 42000, supports .NET Framework versions 4 through 4.5.2.</span></span> <span data-ttu-id="ccd41-114">CLR 버전이 4.0.30319.42000보다 크거나 같으면 .NET Framework 4.6 이상 버전의 .NET Framework를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-114">CLR version greater than or equal to 4.0.30319.42000 supports .NET Framework versions starting with .NET Framework 4.6.</span></span>

<span data-ttu-id="ccd41-115">커뮤니티에서 유지 관리되는 도구를 사용하여 설치된 .NET Framework 버전을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-115">Community-maintained tools are available to help detect which .NET Framework versions are installed:</span></span>

- [https://github.com/jmalarcon/DotNetVersions](https://github.com/jmalarcon/DotNetVersions)

  <span data-ttu-id="ccd41-116">.NET Framework 2.0 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-116">A .NET Framework 2.0 command-line tool.</span></span>

- [https://github.com/EliteLoser/DotNetVersionLister](https://github.com/EliteLoser/DotNetVersionLister)

  <span data-ttu-id="ccd41-117">PowerShell 2.0 모듈</span><span class="sxs-lookup"><span data-stu-id="ccd41-117">A PowerShell 2.0 module.</span></span>

<span data-ttu-id="ccd41-118">.NET Framework 버전별로 설치된 업데이트를 검색하는 방법에 대한 자세한 내용은 [방법: 설치된 .NET Framework 업데이트 확인](how-to-determine-which-net-framework-updates-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="ccd41-118">For information about detecting the installed updates for each version of .NET Framework, see [How to: Determine which .NET Framework updates are installed](how-to-determine-which-net-framework-updates-are-installed.md).</span></span>

## <a name="detect-net-framework-45-and-later-versions"></a><span data-ttu-id="ccd41-119">.NET Framework 4.5 이상 버전 검색</span><span class="sxs-lookup"><span data-stu-id="ccd41-119">Detect .NET Framework 4.5 and later versions</span></span>

<span data-ttu-id="ccd41-120">컴퓨터에 설치된 .NET Framework 버전(4.5 이상)은 레지스트리에서 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** 에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-120">The version of .NET Framework (4.5 and later) installed on a machine is listed in the registry at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="ccd41-121">**Full** 하위 키가 없으면 .NET Framework 4.5 이상이 설치되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-121">If the **Full** subkey is missing, then .NET Framework 4.5 or above isn't installed.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd41-122">레지스트리 경로에서 **NET Framework Setup** 하위 키는 마침표로 시작되지 ‘않습니다’.</span><span class="sxs-lookup"><span data-stu-id="ccd41-122">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

<span data-ttu-id="ccd41-123">레지스트리의 **Release** REG_DWORD 값은 설치된 .NET Framework 버전을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-123">The **Release** REG_DWORD value in the registry represents the version of .NET Framework installed.</span></span>

<a name="version_table"></a>

| <span data-ttu-id="ccd41-124">.NET Framework 버전</span><span class="sxs-lookup"><span data-stu-id="ccd41-124">.NET Framework version</span></span> | <span data-ttu-id="ccd41-125">**Release** 값</span><span class="sxs-lookup"><span data-stu-id="ccd41-125">Value of **Release**</span></span> |
| ---------------------- | -------------------------- |
| <span data-ttu-id="ccd41-126">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ccd41-126">.NET Framework 4.5</span></span>     | <span data-ttu-id="ccd41-127">모든 Windows 운영 체제: 378389</span><span class="sxs-lookup"><span data-stu-id="ccd41-127">All Windows operating systems: 378389</span></span> |
| <span data-ttu-id="ccd41-128">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-128">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="ccd41-129">Windows 8.1 및 Windows Server 2012 R2: 378675</span><span class="sxs-lookup"><span data-stu-id="ccd41-129">On Windows 8.1 and Windows Server 2012 R2: 378675</span></span><br /><span data-ttu-id="ccd41-130">다른 모든 Windows 운영 체제: 378758</span><span class="sxs-lookup"><span data-stu-id="ccd41-130">On all other Windows operating systems: 378758</span></span> |
| <span data-ttu-id="ccd41-131">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-131">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="ccd41-132">모든 Windows 운영 체제: 379893</span><span class="sxs-lookup"><span data-stu-id="ccd41-132">All Windows operating systems: 379893</span></span> |
| <span data-ttu-id="ccd41-133">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ccd41-133">.NET Framework 4.6</span></span>     | <span data-ttu-id="ccd41-134">Windows 10: 393295</span><span class="sxs-lookup"><span data-stu-id="ccd41-134">On Windows 10: 393295</span></span><br /><span data-ttu-id="ccd41-135">다른 모든 Windows 운영 체제: 393297</span><span class="sxs-lookup"><span data-stu-id="ccd41-135">On all other Windows operating systems: 393297</span></span> |
| <span data-ttu-id="ccd41-136">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-136">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="ccd41-137">Windows 10 11월 업데이트 운영 체제: 394254</span><span class="sxs-lookup"><span data-stu-id="ccd41-137">On Windows 10 November Update systems: 394254</span></span><br /><span data-ttu-id="ccd41-138">다른 모든 Windows 운영 체제(Windows 10 포함): 394271</span><span class="sxs-lookup"><span data-stu-id="ccd41-138">On all other Windows operating systems (including Windows 10): 394271</span></span> |
| <span data-ttu-id="ccd41-139">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-139">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="ccd41-140">Windows 10 1주년 업데이트 및 Windows Server 2016: 394802</span><span class="sxs-lookup"><span data-stu-id="ccd41-140">On Windows 10 Anniversary Update and Windows Server 2016: 394802</span></span><br /><span data-ttu-id="ccd41-141">다른 모든 Windows 운영 체제(다른 Windows 10 운영 체제 포함): 394806</span><span class="sxs-lookup"><span data-stu-id="ccd41-141">On all other Windows operating systems (including other Windows 10 operating systems): 394806</span></span> |
| <span data-ttu-id="ccd41-142">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ccd41-142">.NET Framework 4.7</span></span>     | <span data-ttu-id="ccd41-143">Windows 10 Creators Update: 460798</span><span class="sxs-lookup"><span data-stu-id="ccd41-143">On Windows 10 Creators Update: 460798</span></span><br /><span data-ttu-id="ccd41-144">다른 모든 Windows 운영 체제(다른 Windows 10 운영 체제 포함): 460805</span><span class="sxs-lookup"><span data-stu-id="ccd41-144">On all other Windows operating systems (including other Windows 10 operating systems): 460805</span></span> |
| <span data-ttu-id="ccd41-145">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-145">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="ccd41-146">Windows 10 Fall Creators Update 및 Windows Server, 버전 1709: 461308</span><span class="sxs-lookup"><span data-stu-id="ccd41-146">On Windows 10 Fall Creators Update and Windows Server, version 1709: 461308</span></span><br/><span data-ttu-id="ccd41-147">다른 모든 Windows 운영 체제(다른 Windows 10 운영 체제 포함): 461310</span><span class="sxs-lookup"><span data-stu-id="ccd41-147">On all other Windows operating systems (including other Windows 10 operating systems): 461310</span></span> |
| <span data-ttu-id="ccd41-148">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-148">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="ccd41-149">Windows 10 2018년 4월 업데이트 및 Windows Server, 버전 1803: 461808</span><span class="sxs-lookup"><span data-stu-id="ccd41-149">On Windows 10 April 2018 Update and Windows Server, version 1803: 461808</span></span><br/><span data-ttu-id="ccd41-150">Windows 10 2018년 4월 업데이트 및 Windows Server, 버전 1803 이외의 모든 Windows 운영 체제: 461814</span><span class="sxs-lookup"><span data-stu-id="ccd41-150">On all Windows operating systems other than Windows 10 April 2018 Update and Windows Server, version 1803: 461814</span></span> |
| <span data-ttu-id="ccd41-151">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="ccd41-151">.NET Framework 4.8</span></span>     | <span data-ttu-id="ccd41-152">Windows 10 2019년 5월 업데이트 및 Windows 10 2019년 11월 업데이트: 528040</span><span class="sxs-lookup"><span data-stu-id="ccd41-152">On Windows 10 May 2019 Update and Windows 10 November 2019 Update: 528040</span></span><br/><span data-ttu-id="ccd41-153">Windows 10 2020년 5월 업데이트 및 Windows 10 2020년 10월 업데이트: 528372</span><span class="sxs-lookup"><span data-stu-id="ccd41-153">On Windows 10 May 2020 Update and Windows 10 October 2020 Update: 528372</span></span><br/><span data-ttu-id="ccd41-154">다른 모든 Windows 운영 체제(다른 Windows 10 운영 체제 포함): 528049</span><span class="sxs-lookup"><span data-stu-id="ccd41-154">On all other Windows operating systems (including other Windows 10 operating systems): 528049</span></span> |

### <a name="minimum-version"></a><span data-ttu-id="ccd41-155">최소 버전</span><span class="sxs-lookup"><span data-stu-id="ccd41-155">Minimum version</span></span>

<span data-ttu-id="ccd41-156">.NET Framework의 ‘최소’ 버전이 있는지 확인하려면 다음 표에 나열된 해당 값보다 크거나 같은 **Release** REG_DWORD 값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-156">To determine whether a *minimum* version of .NET Framework is present, check for a **Release** REG_DWORD value that's greater than or equal to the corresponding value listed in the following table.</span></span> <span data-ttu-id="ccd41-157">예를 들어 애플리케이션이 .NET Framework 4.8 이상 버전에서 실행되는 경우 528040보다 ‘크거나 같은’ **Release** REG_DWORD 값을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-157">For example, if your application runs under .NET Framework 4.8 or a later version, test for a **Release** REG_DWORD value that's *greater than or equal to* 528040.</span></span>

| <span data-ttu-id="ccd41-158">.NET Framework 버전</span><span class="sxs-lookup"><span data-stu-id="ccd41-158">.NET Framework version</span></span> | <span data-ttu-id="ccd41-159">최소값</span><span class="sxs-lookup"><span data-stu-id="ccd41-159">Minimum value</span></span> |
| ---------------------- | ------------- |
| <span data-ttu-id="ccd41-160">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="ccd41-160">.NET Framework 4.5</span></span>     | <span data-ttu-id="ccd41-161">378389</span><span class="sxs-lookup"><span data-stu-id="ccd41-161">378389</span></span> |
| <span data-ttu-id="ccd41-162">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-162">.NET Framework 4.5.1</span></span>   | <span data-ttu-id="ccd41-163">378675</span><span class="sxs-lookup"><span data-stu-id="ccd41-163">378675</span></span> |
| <span data-ttu-id="ccd41-164">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-164">.NET Framework 4.5.2</span></span>   | <span data-ttu-id="ccd41-165">379893</span><span class="sxs-lookup"><span data-stu-id="ccd41-165">379893</span></span> |
| <span data-ttu-id="ccd41-166">.NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="ccd41-166">.NET Framework 4.6</span></span>     | <span data-ttu-id="ccd41-167">393295</span><span class="sxs-lookup"><span data-stu-id="ccd41-167">393295</span></span> |
| <span data-ttu-id="ccd41-168">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-168">.NET Framework 4.6.1</span></span>   | <span data-ttu-id="ccd41-169">394254</span><span class="sxs-lookup"><span data-stu-id="ccd41-169">394254</span></span> |
| <span data-ttu-id="ccd41-170">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-170">.NET Framework 4.6.2</span></span>   | <span data-ttu-id="ccd41-171">394802</span><span class="sxs-lookup"><span data-stu-id="ccd41-171">394802</span></span> |
| <span data-ttu-id="ccd41-172">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="ccd41-172">.NET Framework 4.7</span></span>     | <span data-ttu-id="ccd41-173">460798</span><span class="sxs-lookup"><span data-stu-id="ccd41-173">460798</span></span> |
| <span data-ttu-id="ccd41-174">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-174">.NET Framework 4.7.1</span></span>   | <span data-ttu-id="ccd41-175">461308</span><span class="sxs-lookup"><span data-stu-id="ccd41-175">461308</span></span> |
| <span data-ttu-id="ccd41-176">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ccd41-176">.NET Framework 4.7.2</span></span>   | <span data-ttu-id="ccd41-177">461808</span><span class="sxs-lookup"><span data-stu-id="ccd41-177">461808</span></span> |
| <span data-ttu-id="ccd41-178">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="ccd41-178">.NET Framework 4.8</span></span>     | <span data-ttu-id="ccd41-179">528040</span><span class="sxs-lookup"><span data-stu-id="ccd41-179">528040</span></span> |

### <a name="use-registry-editor"></a><span data-ttu-id="ccd41-180">레지스트리 편집기 사용</span><span class="sxs-lookup"><span data-stu-id="ccd41-180">Use Registry Editor</span></span>

01. <span data-ttu-id="ccd41-181">**시작** 메뉴에서 **실행** 을 선택하고 *regedit* 을 입력한 다음, **OK** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-181">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

   <span data-ttu-id="ccd41-182">(regedit를 실행하려면 관리자 자격 증명이 있어야 합니다.)</span><span class="sxs-lookup"><span data-stu-id="ccd41-182">(You must have administrative credentials to run regedit.)</span></span>

01. <span data-ttu-id="ccd41-183">레지스트리 편집기에서 다음 하위 키를 엽니다. **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span><span class="sxs-lookup"><span data-stu-id="ccd41-183">In the Registry Editor, open the following subkey: **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span> <span data-ttu-id="ccd41-184">**Full** 하위 키가 없으면 .NET Framework 4.5 이상이 설치되지 않은 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-184">If the **Full** subkey isn't present, then you don't have .NET Framework 4.5 or later installed.</span></span>

01. <span data-ttu-id="ccd41-185">**Release** 라는 REG_DWORD 항목을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-185">Check for a REG_DWORD entry named **Release**.</span></span> <span data-ttu-id="ccd41-186">릴리스 DWORD가 있으면 컴퓨터에 .NET Framework 4.5 이상이 설치된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-186">If it exists, then you have .NET Framework 4.5 or later installed.</span></span> <span data-ttu-id="ccd41-187">항목 값은 특정 .NET Framework 버전에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-187">Its value corresponds to a particular version of .NET Framework.</span></span> <span data-ttu-id="ccd41-188">예를 들어 다음 그림에서 **Release** 항목의 값은 528040으로, 이것은 .NET Framework 4.8의 릴리스 키입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-188">In the following figure, for example, the value of the **Release** entry is 528040, which is the release key for .NET Framework 4.8.</span></span>

   ![.NET Framework 4.5의 레지스트리 항목](./media/clr-installdir.png )

### <a name="use-powershell-to-check-for-a-minimum-version"></a><span data-ttu-id="ccd41-190">PowerShell을 사용하여 최소 버전 확인</span><span class="sxs-lookup"><span data-stu-id="ccd41-190">Use PowerShell to check for a minimum version</span></span>

<span data-ttu-id="ccd41-191">PowerShell 명령을 사용하여 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** 하위 키의 **Release** 항목값을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-191">Use PowerShell commands to check the value of the **Release** entry of the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey.</span></span>

<span data-ttu-id="ccd41-192">다음 예제에서는 **Release** 항목 값을 검사하여 .NET Framework 4.6.2 이상이 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-192">The following examples check the value of the **Release** entry to determine whether .NET Framework 4.6.2 or later is installed.</span></span> <span data-ttu-id="ccd41-193">설치된 경우 `True` 코드 반환, 설치되지 않은 경우 `False` 코드 반환.</span><span class="sxs-lookup"><span data-stu-id="ccd41-193">This code returns `True` if it's installed and `False` otherwise.</span></span>

```powershell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

### <a name="query-the-registry-using-code"></a><span data-ttu-id="ccd41-194">코드를 사용하여 레지스트리를 쿼리</span><span class="sxs-lookup"><span data-stu-id="ccd41-194">Query the registry using code</span></span>

01. <span data-ttu-id="ccd41-195"><xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> 및 <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> 메서드를 사용하여 Windows 레지스트리의 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** 하위 키에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-195">Use the <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> and <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> methods to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** subkey in the Windows registry.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="ccd41-196">실행 중인 앱이 32비트이고 64비트 Windows에서 실행되는 경우 레지스트리 경로는 이전에 나열된 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-196">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="ccd41-197">64비트 레지스트리는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 하위 키에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-197">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="ccd41-198">예를 들어 .NET Framework 4.5의 레지스트리 하위 키는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-198">For example, the registry subkey for .NET Framework 4.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**.</span></span>

01. <span data-ttu-id="ccd41-199">**Release** REG_DWORD 값을 확인하여 설치된 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-199">Check the **Release** REG_DWORD value to determine the installed version.</span></span> <span data-ttu-id="ccd41-200">이후 버전과의 호환성을 유지하려는 경우 버전의 값이 [.NET Framework 버전 표](#version_table)에 나와 있는 값 이상인지를 확인하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-200">To be forward-compatible, check for a value greater than or equal to the value listed in the [.NET Framework version table](#version_table).</span></span>

<span data-ttu-id="ccd41-201">다음 예제에서는 레지스트리의 **Release** 항목 값을 검사하여 .NET Framework 4.5~4.8 버전이 설치되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-201">The following example checks the value of the **Release** entry in the registry to find the versions of .NET Framework 4.5-4.8 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="2":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="2":::

<span data-ttu-id="ccd41-202">예제 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-202">The example displays output like the following:</span></span>

```output
.NET Framework Version: 4.6.1
```

<span data-ttu-id="ccd41-203">이 예제에서는 버전을 확인하기 위한 권장된 방법을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-203">This example follows the recommended practice for version checking:</span></span>

- <span data-ttu-id="ccd41-204">**릴리스** 항목의 값이 알려진 릴리스 키의 값보다 *크거나 같은지* 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-204">It checks whether the value of the **Release** entry is *greater than or equal to* the value of the known release keys.</span></span>
- <span data-ttu-id="ccd41-205">최신 버전에서 가장 오래된 버전 순서대로 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-205">It checks in order from most recent version to earliest version.</span></span>

## <a name="detect-net-framework-10-through-40"></a><span data-ttu-id="ccd41-206">.NET Framework 1.0~4.0 검색</span><span class="sxs-lookup"><span data-stu-id="ccd41-206">Detect .NET Framework 1.0 through 4.0</span></span>

<span data-ttu-id="ccd41-207">1\.1에서 4.0까지의 각 .NET Framework 버전은 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** 의 하위 키로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-207">Each version of .NET Framework from 1.1 to 4.0 is listed as a subkey at **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP**.</span></span> <span data-ttu-id="ccd41-208">다음 표에서는 각 .NET Framework 버전의 경로를 에 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-208">The following table lists the path to each .NET Framework version.</span></span> <span data-ttu-id="ccd41-209">대부분의 버전에서 **Install** REG_DWORD 값은 `1`로 설정되어 해당 버전이 설치되었음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-209">For most versions, there's an **Install** REG_DWORD value of `1` to indicate this version is installed.</span></span> <span data-ttu-id="ccd41-210">이러한 하위 키에는 버전 문자열을 포함하는 **Version** REG_SZ 값도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-210">In these subkeys, there's also a **Version** REG_SZ value that contains a version string.</span></span>

> [!NOTE]
> <span data-ttu-id="ccd41-211">레지스트리 경로에서 **NET Framework Setup** 하위 키는 마침표로 시작되지 ‘않습니다’.</span><span class="sxs-lookup"><span data-stu-id="ccd41-211">The **NET Framework Setup** subkey in the registry path does *not* begin with a period.</span></span>

| <span data-ttu-id="ccd41-212">프레임워크 버전</span><span class="sxs-lookup"><span data-stu-id="ccd41-212">Framework Version</span></span>  | <span data-ttu-id="ccd41-213">레지스트리 하위 키</span><span class="sxs-lookup"><span data-stu-id="ccd41-213">Registry Subkey</span></span> | <span data-ttu-id="ccd41-214">값</span><span class="sxs-lookup"><span data-stu-id="ccd41-214">Value</span></span> |
| ------------------ | --------------- | ----- |
| <span data-ttu-id="ccd41-215">1.0</span><span class="sxs-lookup"><span data-stu-id="ccd41-215">1.0</span></span>                | <span data-ttu-id="ccd41-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span><span class="sxs-lookup"><span data-stu-id="ccd41-216">**HKLM\\Software\\Microsoft\\.NETFramework\\Policy\\v1.0\\3705**</span></span>     | <span data-ttu-id="ccd41-217">**Install** REG_SZ가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-217">**Install** REG_SZ equals `1`</span></span> |
| <span data-ttu-id="ccd41-218">1.1</span><span class="sxs-lookup"><span data-stu-id="ccd41-218">1.1</span></span>                | <span data-ttu-id="ccd41-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span><span class="sxs-lookup"><span data-stu-id="ccd41-219">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v1.1.4322**</span></span>   | <span data-ttu-id="ccd41-220">**Install** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-220">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="ccd41-221">2.0</span><span class="sxs-lookup"><span data-stu-id="ccd41-221">2.0</span></span>                | <span data-ttu-id="ccd41-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span><span class="sxs-lookup"><span data-stu-id="ccd41-222">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v2.0.50727**</span></span>  | <span data-ttu-id="ccd41-223">**Install** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-223">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="ccd41-224">3.0</span><span class="sxs-lookup"><span data-stu-id="ccd41-224">3.0</span></span>                | <span data-ttu-id="ccd41-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span><span class="sxs-lookup"><span data-stu-id="ccd41-225">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.0\\Setup**</span></span> | <span data-ttu-id="ccd41-226">**InstallSuccess** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-226">**InstallSuccess** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="ccd41-227">3.5</span><span class="sxs-lookup"><span data-stu-id="ccd41-227">3.5</span></span>                | <span data-ttu-id="ccd41-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span><span class="sxs-lookup"><span data-stu-id="ccd41-228">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v3.5**</span></span>        | <span data-ttu-id="ccd41-229">**Install** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-229">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="ccd41-230">4.0 클라이언트 프로필</span><span class="sxs-lookup"><span data-stu-id="ccd41-230">4.0 Client Profile</span></span> | <span data-ttu-id="ccd41-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span><span class="sxs-lookup"><span data-stu-id="ccd41-231">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Client**</span></span>  | <span data-ttu-id="ccd41-232">**Install** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-232">**Install** REG_DWORD equals `1`</span></span> |
| <span data-ttu-id="ccd41-233">4.0 전체 프로필</span><span class="sxs-lookup"><span data-stu-id="ccd41-233">4.0 Full Profile</span></span>   | <span data-ttu-id="ccd41-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span><span class="sxs-lookup"><span data-stu-id="ccd41-234">**HKLM\\Software\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full**</span></span>    | <span data-ttu-id="ccd41-235">**Install** REG_DWORD가 `1`과 같음</span><span class="sxs-lookup"><span data-stu-id="ccd41-235">**Install** REG_DWORD equals `1`</span></span> |

> [!IMPORTANT]
> <span data-ttu-id="ccd41-236">실행 중인 앱이 32비트이고 64비트 Windows에서 실행되는 경우 레지스트리 경로는 이전에 나열된 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-236">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="ccd41-237">64비트 레지스트리는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 하위 키에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-237">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="ccd41-238">예를 들어 .NET Framework 3.5의 레지스트리 하위 키는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-238">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="ccd41-239">.NET Framework 1.0 하위 키의 레지스트리 경로는 다른 하위 키와 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-239">Notice that the registry path to the .NET Framework 1.0 subkey is different from the others.</span></span>

### <a name="use-registry-editor-older-framework-versions"></a><span data-ttu-id="ccd41-240">레지스트리 편집기 사용(이전 프레임워크 버전)</span><span class="sxs-lookup"><span data-stu-id="ccd41-240">Use Registry Editor (older framework versions)</span></span>

01. <span data-ttu-id="ccd41-241">**시작** 메뉴에서 **실행** 을 선택하고 *regedit* 을 입력한 다음, **OK** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-241">From the **Start** menu, choose **Run**, enter *regedit*, and then select **OK**.</span></span>

    <span data-ttu-id="ccd41-242">regedit을 실행하려면 관리자 자격 증명이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-242">You must have administrative credentials to run regedit.</span></span>

01. <span data-ttu-id="ccd41-243">확인하려는 버전과 일치하는 하위 키를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-243">Open the subkey that matches the version you want to check.</span></span> <span data-ttu-id="ccd41-244">[.NET Framework 1.0~4.0 검색](#detect-net-framework-10-through-40) 섹션의 표를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-244">Use the table in the [Detect .NET Framework 1.0 through 4.0](#detect-net-framework-10-through-40) section.</span></span>

    <span data-ttu-id="ccd41-245">다음 그림은 .NET Framework 3.5의 하위 키와 **Version** 값을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-245">The following figure shows the subkey and its **Version** value for .NET Framework 3.5.</span></span>

    <span data-ttu-id="ccd41-246">![.NET Framework 3.5의 레지스트리 항목](./media/net-4-and-earlier.png ".NET Framework 3.5 및 이전 버전")</span><span class="sxs-lookup"><span data-stu-id="ccd41-246">![The registry entry for .NET Framework 3.5.](./media/net-4-and-earlier.png ".NET Framework 3.5 and earlier versions")</span></span>

### <a name="query-the-registry-using-code-older-framework-versions"></a><span data-ttu-id="ccd41-247">코드를 사용한 레지스트리 쿼리(이전 프레임워크 버전)</span><span class="sxs-lookup"><span data-stu-id="ccd41-247">Query the registry using code (older framework versions)</span></span>

<span data-ttu-id="ccd41-248"><xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> 클래스를 사용하여 Windows 레지스트리의 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** 하위 키에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-248">Use the <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> class to access the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\NET Framework Setup\\NDP** subkey in the Windows registry.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccd41-249">실행 중인 앱이 32비트이고 64비트 Windows에서 실행되는 경우 레지스트리 경로는 이전에 나열된 것과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-249">If the app you're running is 32-bit and running in 64-bit Windows, the registry paths will be different than previously listed.</span></span> <span data-ttu-id="ccd41-250">64비트 레지스트리는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** 하위 키에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-250">The 64-bit registry is available in the **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\** subkey.</span></span> <span data-ttu-id="ccd41-251">예를 들어 .NET Framework 3.5의 레지스트리 하위 키는 **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5** 입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-251">For example, the registry subkey for .NET Framework 3.5 is **HKEY_LOCAL_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\NET Framework Setup\\NDP\\v3.5**.</span></span>

<span data-ttu-id="ccd41-252">다음 예제에서는 설치된 .NET Framework 1-4 버전을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-252">The following example finds the versions of .NET Framework 1-4 that are installed:</span></span>

:::code language="csharp" source="snippets/csharp/versions-installed.cs" id="1":::

:::code language="vb" source="snippets/visual-basic/versions-installed.vb" id="1":::

<span data-ttu-id="ccd41-253">예제 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-253">The example displays output similar to the following:</span></span>

```output
v2.0.50727  2.0.50727.4927  SP2
v3.0  3.0.30729.4926  SP2
v3.5  3.5.30729.4926  SP1
v4.0
  Client  4.0.0.0
```

## <a name="find-clr-versions"></a><span data-ttu-id="ccd41-254">CLR 버전 찾기</span><span class="sxs-lookup"><span data-stu-id="ccd41-254">Find CLR versions</span></span>

<span data-ttu-id="ccd41-255">.NET Framework와 함께 설치된 .NET Framework CLR은 별도로 버전이 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-255">The .NET Framework CLR installed with .NET Framework is versioned separately.</span></span> <span data-ttu-id="ccd41-256">.NET Framework CLR의 버전을 검색하는 두 가지 방법은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-256">There are two ways to detect the version of the .NET Framework CLR:</span></span>

- <span data-ttu-id="ccd41-257">**Clrver.exe 도구**</span><span class="sxs-lookup"><span data-stu-id="ccd41-257">**The Clrver.exe tool**</span></span>

  <span data-ttu-id="ccd41-258">[CLR 버전 도구(Clrver.exe)](../tools/clrver-exe-clr-version-tool.md)를 사용하여 컴퓨터에 설치된 CRL의 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-258">Use the [CLR Version tool (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) to determine which versions of the CLR are installed on a computer.</span></span> <span data-ttu-id="ccd41-259">[Visual Studio용 개발자 명령 프롬프트](../tools/developer-command-prompt-for-vs.md)를 열고 `clrver`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-259">Open the [Developer Command Prompt for Visual Studio](../tools/developer-command-prompt-for-vs.md) and enter `clrver`.</span></span>

  <span data-ttu-id="ccd41-260">샘플 출력:</span><span class="sxs-lookup"><span data-stu-id="ccd41-260">Sample output:</span></span>

  ```console
  Versions installed on the machine:
  v2.0.50727
  v4.0.30319
  ```

- <span data-ttu-id="ccd41-261">**`Environment` 클래스**</span><span class="sxs-lookup"><span data-stu-id="ccd41-261">**The `Environment` class**</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="ccd41-262">.NET Framework 4.5 이상 버전의 경우 <xref:System.Environment.Version%2A?displayProperty=nameWithType> 속성을 사용하여 CLR의 버전을 확인하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-262">For .NET Framework 4.5 and later versions, don't use the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to detect the version of the CLR.</span></span> <span data-ttu-id="ccd41-263">대신 [.NET Framework 4.5 이상 버전 검색](#detect-net-framework-45-and-later-versions)에 설명된 대로 레지스트리를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-263">Instead, query the registry as described in [Detect .NET Framework 4.5 and later versions](#detect-net-framework-45-and-later-versions).</span></span>

  1. <span data-ttu-id="ccd41-264"><xref:System.Version>개체를 검색하기 위해 <xref:System.Environment.Version?displayProperty=nameWithType>속성을 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-264">Query the <xref:System.Environment.Version?displayProperty=nameWithType> property to retrieve a <xref:System.Version> object.</span></span>

     <span data-ttu-id="ccd41-265">반환된 `System.Version`개체는 현재 코드를 실행하는 런타임 버전을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-265">The returned `System.Version` object identifies the version of the runtime that's currently executing the code.</span></span> <span data-ttu-id="ccd41-266">컴퓨터에 설치된 어셈블리 버전이나 다른 런타임 버전은 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-266">It doesn't return assembly versions or other versions of the runtime that may have been installed on the computer.</span></span>

     <span data-ttu-id="ccd41-267">.NET Framework 버전 4, 4.5, 4.5.1 및 4.5.2의 경우 반환된 <xref:System.Version> 개체 문자열 표현은 4.0.30319.‘xxxxx’ 형식이며, ‘xxxxx’는 42000보다 작습니다. </span><span class="sxs-lookup"><span data-stu-id="ccd41-267">For .NET Framework versions 4, 4.5, 4.5.1, and 4.5.2, the string representation of the returned <xref:System.Version> object has the form 4.0.30319.*xxxxx*, where *xxxxx* is less than 42000.</span></span> <span data-ttu-id="ccd41-268">.NET Framework 4.6 및 이후 버전의 경우 형식은 4.0.30319.42000입니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-268">For .NET Framework 4.6 and later versions, it has the form 4.0.30319.42000.</span></span>

  1. <span data-ttu-id="ccd41-269">**Version** 개체를 가져온 후, 다음과 같이 개체를 쿼리합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-269">After you have the **Version** object, query it as follows:</span></span>

     - <span data-ttu-id="ccd41-270">주 릴리스 식별자(예:버전 4.0의 경우 *4*)는 <xref:System.Version.Major%2A?displayProperty=nameWithType>속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-270">For the major release identifier (for example, *4* for version 4.0), use the <xref:System.Version.Major%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="ccd41-271">부 릴리스 식별자(예:버전 4.0의 경우 *0*)는 <xref:System.Version.Minor%2A?displayProperty=nameWithType>속성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-271">For the minor release identifier (for example, *0* for version 4.0), use the <xref:System.Version.Minor%2A?displayProperty=nameWithType> property.</span></span>

     - <span data-ttu-id="ccd41-272">전체 버전 문자열(예를 들어 *4.0.30319.18010*)에는 <xref:System.Version.ToString%2A?displayProperty=nameWithType>메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-272">For the entire version string (for example, *4.0.30319.18010*), use the <xref:System.Version.ToString%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ccd41-273">메서드는 코드를 실행 하는 런타임 버전을 반영하는 단일 값을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-273">This method returns a single value that reflects the version of the runtime that's executing the code.</span></span> <span data-ttu-id="ccd41-274">이는 컴퓨터에 설치된 어셈블리 버전이나 다른 런타임 버전은 반환하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-274">It doesn't return assembly versions or other runtime versions that may be installed on the computer.</span></span>

  <span data-ttu-id="ccd41-275">다음 예제에서는 <xref:System.Environment.Version%2A?displayProperty=nameWithType>속성을 사용하여 CLR 버전 정보를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-275">The following example uses the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property to retrieve CLR version information:</span></span>

  ```csharp
  Console.WriteLine($"Version: {Environment.Version}");
  ```

  ```vb
  Console.WriteLine($"Version: {Environment.Version}")
  ```

  <span data-ttu-id="ccd41-276">예제 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ccd41-276">The example displays output similar to the following:</span></span>

  ```output
  Version: 4.0.30319.18010
  ```

## <a name="see-also"></a><span data-ttu-id="ccd41-277">참조</span><span class="sxs-lookup"><span data-stu-id="ccd41-277">See also</span></span>

- [<span data-ttu-id="ccd41-278">방법: 설치된 .NET Framework 업데이트 확인</span><span class="sxs-lookup"><span data-stu-id="ccd41-278">How to: Determine which .NET Framework updates are installed</span></span>](how-to-determine-which-net-framework-updates-are-installed.md)
- [<span data-ttu-id="ccd41-279">개발자용 .NET Framework 설치</span><span class="sxs-lookup"><span data-stu-id="ccd41-279">Install .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="ccd41-280">.NET Framework 버전 및 종속성</span><span class="sxs-lookup"><span data-stu-id="ccd41-280">.NET Framework versions and dependencies</span></span>](versions-and-dependencies.md)
