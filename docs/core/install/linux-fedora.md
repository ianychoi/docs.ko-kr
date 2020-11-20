---
title: Fedora에 .NET 설치 - .NET
description: Fedora에 .NET SDK 및 .NET 런타임을 설치하는 다양한 방법을 보여 줍니다.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 9e96773e30fb8ee395e37dca7a4794cd42359bb2
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594623"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-fedora"></a><span data-ttu-id="51108-103">Fedora에 .NET SDK 또는 .NET 런타임 설치</span><span class="sxs-lookup"><span data-stu-id="51108-103">Install the .NET SDK or the .NET Runtime on Fedora</span></span>

<span data-ttu-id="51108-104">.NET은 Fedora에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="51108-104">.NET is supported on Fedora.</span></span> <span data-ttu-id="51108-105">이 문서에서는 Fedora에 .NET을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="51108-105">This article describes how to install .NET on Fedora.</span></span> <span data-ttu-id="51108-106">Fedora 버전의 지원이 종료되면 해당 버전에서는 .NET도 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-106">When a Fedora version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="51108-107">그러나 이러한 지침은 지원되지 않더라도 해당 버전에서 .NET을 실행하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="51108-108">지원되는 배포</span><span class="sxs-lookup"><span data-stu-id="51108-108">Supported distributions</span></span>

<span data-ttu-id="51108-109">다음 표는 현재 지원되는 .NET 릴리스와 해당 릴리스가 지원되는 Fedora 버전의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="51108-109">The following table is a list of currently supported .NET releases and the versions of Fedora they're supported on.</span></span> <span data-ttu-id="51108-110">이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Fedora 버전이 지원 종료에 도달](https://fedoraproject.org/wiki/End_of_life)할 때까지 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="51108-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Fedora reaches end-of-life](https://fedoraproject.org/wiki/End_of_life).</span></span>

- <span data-ttu-id="51108-111">✔️는 Fedora 또는 .NET 버전이 계속 지원됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51108-111">A ✔️ indicates that the version of Fedora or .NET is still supported.</span></span>
- <span data-ttu-id="51108-112">❌는 Fedora 또는 .NET 버전이 해당 Fedora 릴리스에서 지원되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="51108-112">A ❌ indicates that the version of Fedora or .NET isn't supported on that Fedora release.</span></span>
- <span data-ttu-id="51108-113">Fedora 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="51108-113">When both a version of Fedora and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="51108-114">Fedora</span><span class="sxs-lookup"><span data-stu-id="51108-114">Fedora</span></span>               | <span data-ttu-id="51108-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-115">.NET Core 2.1</span></span> | <span data-ttu-id="51108-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-116">.NET Core 3.1</span></span> | <span data-ttu-id="51108-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-117">.NET 5.0</span></span> |
|----------------------|---------------|---------------|----------|
| <span data-ttu-id="51108-118">✔️ [33](#fedora-33-)</span><span class="sxs-lookup"><span data-stu-id="51108-118">✔️ [33](#fedora-33-)</span></span> | <span data-ttu-id="51108-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-119">✔️ 2.1</span></span>        | <span data-ttu-id="51108-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-120">✔️ 3.1</span></span>        | <span data-ttu-id="51108-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-121">✔️ 5.0</span></span> |
| <span data-ttu-id="51108-122">✔️ [32](#fedora-32-)</span><span class="sxs-lookup"><span data-stu-id="51108-122">✔️ [32](#fedora-32-)</span></span> | <span data-ttu-id="51108-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-123">✔️ 2.1</span></span>        | <span data-ttu-id="51108-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-124">✔️ 3.1</span></span>        | <span data-ttu-id="51108-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-125">✔️ 5.0</span></span> |
| <span data-ttu-id="51108-126">❌ [31](#fedora-31-)</span><span class="sxs-lookup"><span data-stu-id="51108-126">❌ [31](#fedora-31-)</span></span> | <span data-ttu-id="51108-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-127">✔️ 2.1</span></span>        | <span data-ttu-id="51108-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-128">✔️ 3.1</span></span>        | <span data-ttu-id="51108-129">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-129">❌ 5.0</span></span> |
| <span data-ttu-id="51108-130">❌ [30](#fedora-30-)</span><span class="sxs-lookup"><span data-stu-id="51108-130">❌ [30](#fedora-30-)</span></span> | <span data-ttu-id="51108-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-131">✔️ 2.1</span></span>        | <span data-ttu-id="51108-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-132">✔️ 3.1</span></span>        | <span data-ttu-id="51108-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-133">❌ 5.0</span></span> |
| <span data-ttu-id="51108-134">❌ [29](#fedora-29-)</span><span class="sxs-lookup"><span data-stu-id="51108-134">❌ [29](#fedora-29-)</span></span> | <span data-ttu-id="51108-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-135">✔️ 2.1</span></span>        | <span data-ttu-id="51108-136">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-136">✔️ 3.1</span></span>        | <span data-ttu-id="51108-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-137">❌ 5.0</span></span> |
| <span data-ttu-id="51108-138">❌ [28](#fedora-28-)</span><span class="sxs-lookup"><span data-stu-id="51108-138">❌ [28](#fedora-28-)</span></span> | <span data-ttu-id="51108-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-139">✔️ 2.1</span></span>        | <span data-ttu-id="51108-140">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-140">❌ 3.1</span></span>        | <span data-ttu-id="51108-141">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-141">❌ 5.0</span></span> |
| <span data-ttu-id="51108-142">❌ [27](#fedora-27-)</span><span class="sxs-lookup"><span data-stu-id="51108-142">❌ [27](#fedora-27-)</span></span> | <span data-ttu-id="51108-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="51108-143">✔️ 2.1</span></span>        | <span data-ttu-id="51108-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="51108-144">❌ 3.1</span></span>        | <span data-ttu-id="51108-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="51108-145">❌ 5.0</span></span> |

<span data-ttu-id="51108-146">다음 .NET 버전은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-146">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="51108-147">이러한 버전의 다운로드는 여전히 게시된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="51108-147">The downloads for these still remain published:</span></span>

- <span data-ttu-id="51108-148">3.0</span><span class="sxs-lookup"><span data-stu-id="51108-148">3.0</span></span>
- <span data-ttu-id="51108-149">2.2</span><span class="sxs-lookup"><span data-stu-id="51108-149">2.2</span></span>
- <span data-ttu-id="51108-150">2.0</span><span class="sxs-lookup"><span data-stu-id="51108-150">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="51108-151">다른 버전을 설치하는 방법</span><span class="sxs-lookup"><span data-stu-id="51108-151">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="fedora-33-"></a><span data-ttu-id="51108-152">Fedora 33 ✔️</span><span class="sxs-lookup"><span data-stu-id="51108-152">Fedora 33 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="51108-153">.NET Core 3.1은 Fedora 33의 기본 패키지 리포지토리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-153">.NET Core 3.1 is available in the default package repositories for Fedora 33.</span></span> <span data-ttu-id="51108-154">.NET Core 3.1을 설치하려면 `aspnetcore-runtime-3.1` 또는 `dotnet-sdk-3.1`과 같은 적절한 패키지에서 `dnf install` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51108-154">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="51108-155">.NET 5.0은 기본 패키지 리포지토리에서 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-155">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/33/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-32-"></a><span data-ttu-id="51108-156">Fedora 32 ✔️</span><span class="sxs-lookup"><span data-stu-id="51108-156">Fedora 32 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="51108-157">.NET Core 3.1은 Fedora 32의 기본 패키지 리포지토리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-157">.NET Core 3.1 is available in the default package repositories for Fedora 32.</span></span> <span data-ttu-id="51108-158">.NET Core 3.1을 설치하려면 `aspnetcore-runtime-3.1` 또는 `dotnet-sdk-3.1`과 같은 적절한 패키지에서 `dnf install` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="51108-158">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="51108-159">.NET 5.0은 기본 패키지 리포지토리에서 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="51108-159">.NET 5.0 isn't yet available in the default package repositories.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/32/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="fedora-31-"></a><span data-ttu-id="51108-160">Fedora 31 ❌</span><span class="sxs-lookup"><span data-stu-id="51108-160">Fedora 31 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-30-"></a><span data-ttu-id="51108-161">Fedora 30 ❌</span><span class="sxs-lookup"><span data-stu-id="51108-161">Fedora 30 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/30/prod.repo
```

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="fedora-29-"></a><span data-ttu-id="51108-162">Fedora 29 ❌</span><span class="sxs-lookup"><span data-stu-id="51108-162">Fedora 29 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

[!INCLUDE [linux-dnf-install-30](includes/linux-install-30-dnf.md)]

## <a name="fedora-28-"></a><span data-ttu-id="51108-163">Fedora 28 ❌</span><span class="sxs-lookup"><span data-stu-id="51108-163">Fedora 28 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/28/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="fedora-27-"></a><span data-ttu-id="51108-164">Fedora 27 ❌</span><span class="sxs-lookup"><span data-stu-id="51108-164">Fedora 27 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-fedora.md)]

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/27/prod.repo
```

[!INCLUDE [linux-dnf-install-20](includes/linux-install-20-dnf.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="51108-165">패키지 관리자 문제 해결</span><span class="sxs-lookup"><span data-stu-id="51108-165">Troubleshoot the package manager</span></span>

<span data-ttu-id="51108-166">이 섹션에서는 패키지 관리자를 사용하여 .NET Core를 설치할 때 발생할 수 있는 일반적인 오류에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="51108-166">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="51108-167">패키지를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="51108-167">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="failed-to-fetch"></a><span data-ttu-id="51108-168">가져오지 못함</span><span class="sxs-lookup"><span data-stu-id="51108-168">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="snap"></a><span data-ttu-id="51108-169">Snap</span><span class="sxs-lookup"><span data-stu-id="51108-169">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="51108-170">종속성</span><span class="sxs-lookup"><span data-stu-id="51108-170">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="51108-171">스크립팅된 설치</span><span class="sxs-lookup"><span data-stu-id="51108-171">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="51108-172">수동 설치</span><span class="sxs-lookup"><span data-stu-id="51108-172">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="51108-173">다음 단계</span><span class="sxs-lookup"><span data-stu-id="51108-173">Next steps</span></span>

- [<span data-ttu-id="51108-174">자습서: Visual Studio Code를 사용하여 .NET SDK에서 콘솔 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="51108-174">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
