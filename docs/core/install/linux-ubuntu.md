---
title: Ubuntu에 .NET 설치 - .NET
description: Ubuntu에 .NET SDK 및 .NET 런타임을 설치하는 다양한 방법을 보여 줍니다.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 22ce3379e028f065528e1f507a2d8c1ae598f0e8
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96031850"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-ubuntu"></a><span data-ttu-id="caf86-103">Ubuntu에 .NET SDK 또는 .NET 런타임 설치</span><span class="sxs-lookup"><span data-stu-id="caf86-103">Install the .NET SDK or the .NET Runtime on Ubuntu</span></span>

<span data-ttu-id="caf86-104">.NET은 Ubuntu에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-104">.NET is supported on Ubuntu.</span></span> <span data-ttu-id="caf86-105">이 문서에서는 Ubuntu에 .NET을 설치하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-105">This article describes how to install .NET on Ubuntu.</span></span> <span data-ttu-id="caf86-106">Ubuntu 버전의 지원이 종료되면 해당 버전에서는 .NET도 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-106">When an Ubuntu version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="caf86-107">그러나 이러한 지침은 지원되지 않더라도 해당 버전에서 .NET을 실행하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-107">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

## <a name="supported-distributions"></a><span data-ttu-id="caf86-108">지원되는 배포</span><span class="sxs-lookup"><span data-stu-id="caf86-108">Supported distributions</span></span>

<span data-ttu-id="caf86-109">다음 표는 현재 지원되는 .NET 릴리스와 해당 릴리스가 지원되는 Ubuntu 버전의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-109">The following table is a list of currently supported .NET releases and the versions of Ubuntu they're supported on.</span></span> <span data-ttu-id="caf86-110">이러한 버전은 [.NET 버전이 지원 종료에 도달](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)하거나 [Ubuntu 버전이 지원 종료에 도달](https://wiki.ubuntu.com/Releases)할 때까지 계속 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-110">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Ubuntu reaches end-of-life](https://wiki.ubuntu.com/Releases).</span></span>

- <span data-ttu-id="caf86-111">✔️는 Ubuntu 또는 .NET 버전이 계속 지원됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-111">A ✔️ indicates that the version of Ubuntu or .NET is still supported.</span></span>
- <span data-ttu-id="caf86-112">❌는 Ubuntu 또는 .NET 버전이 해당 Ubuntu 릴리스에서 지원되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-112">A ❌ indicates that the version of Ubuntu or .NET isn't supported on that Ubuntu release.</span></span>
- <span data-ttu-id="caf86-113">Ubuntu 버전과 .NET 버전 모두에 ✔가 있으면 해당 OS와 .NET 조합은 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-113">When both a version of Ubuntu and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="caf86-114">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="caf86-114">Ubuntu</span></span>                   | <span data-ttu-id="caf86-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-115">.NET Core 2.1</span></span> | <span data-ttu-id="caf86-116">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-116">.NET Core 3.1</span></span> | <span data-ttu-id="caf86-117">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-117">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="caf86-118">✔️ [20.10](#2010-)</span><span class="sxs-lookup"><span data-stu-id="caf86-118">✔️ [20.10](#2010-)</span></span>       | <span data-ttu-id="caf86-119">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-119">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-120">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-120">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-121">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-121">✔️ 5.0</span></span> |
| <span data-ttu-id="caf86-122">✔️ [20.04(LTS)](#2004-)</span><span class="sxs-lookup"><span data-stu-id="caf86-122">✔️ [20.04 (LTS)](#2004-)</span></span> | <span data-ttu-id="caf86-123">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-123">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-124">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-124">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-125">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-125">✔️ 5.0</span></span> |
| <span data-ttu-id="caf86-126">❌ [19.10](#1910-)</span><span class="sxs-lookup"><span data-stu-id="caf86-126">❌ [19.10](#1910-)</span></span>       | <span data-ttu-id="caf86-127">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-127">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-128">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-128">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-129">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-129">✔️ 5.0</span></span> |
| <span data-ttu-id="caf86-130">❌ [19.04](#1904-)</span><span class="sxs-lookup"><span data-stu-id="caf86-130">❌ [19.04](#1904-)</span></span>       | <span data-ttu-id="caf86-131">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-131">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-132">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-132">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-133">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-133">❌ 5.0</span></span> |
| <span data-ttu-id="caf86-134">❌ [18.10](#1810-)</span><span class="sxs-lookup"><span data-stu-id="caf86-134">❌ [18.10](#1810-)</span></span>       | <span data-ttu-id="caf86-135">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-135">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-136">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-136">❌ 3.1</span></span>        | <span data-ttu-id="caf86-137">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-137">❌ 5.0</span></span> |
| <span data-ttu-id="caf86-138">✔️ [18.04(LTS)](#1804-)</span><span class="sxs-lookup"><span data-stu-id="caf86-138">✔️ [18.04 (LTS)](#1804-)</span></span> | <span data-ttu-id="caf86-139">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-139">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-140">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-140">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-141">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-141">✔️ 5.0</span></span> |
| <span data-ttu-id="caf86-142">❌ [17.10](#1710-)</span><span class="sxs-lookup"><span data-stu-id="caf86-142">❌ [17.10](#1710-)</span></span>       | <span data-ttu-id="caf86-143">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-143">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-144">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-144">❌ 3.1</span></span>        | <span data-ttu-id="caf86-145">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-145">❌ 5.0</span></span> |
| <span data-ttu-id="caf86-146">❌ [17.04](#1704-)</span><span class="sxs-lookup"><span data-stu-id="caf86-146">❌ [17.04](#1704-)</span></span>       | <span data-ttu-id="caf86-147">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-147">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-148">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-148">❌ 3.1</span></span>        | <span data-ttu-id="caf86-149">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-149">❌ 5.0</span></span> |
| <span data-ttu-id="caf86-150">❌ [16.10](#1610-)</span><span class="sxs-lookup"><span data-stu-id="caf86-150">❌ [16.10](#1610-)</span></span>       | <span data-ttu-id="caf86-151">❌ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-151">❌ 2.1</span></span>        | <span data-ttu-id="caf86-152">❌ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-152">❌ 3.1</span></span>        | <span data-ttu-id="caf86-153">❌ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-153">❌ 5.0</span></span> |
| <span data-ttu-id="caf86-154">✔️ [16.04(LTS)](#1604-)</span><span class="sxs-lookup"><span data-stu-id="caf86-154">✔️ [16.04 (LTS)](#1604-)</span></span> | <span data-ttu-id="caf86-155">✔️ 2.1</span><span class="sxs-lookup"><span data-stu-id="caf86-155">✔️ 2.1</span></span>        | <span data-ttu-id="caf86-156">✔️ 3.1</span><span class="sxs-lookup"><span data-stu-id="caf86-156">✔️ 3.1</span></span>        | <span data-ttu-id="caf86-157">✔️ 5.0</span><span class="sxs-lookup"><span data-stu-id="caf86-157">✔️ 5.0</span></span> |

<span data-ttu-id="caf86-158">다음 .NET 버전은 더 이상 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-158">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="caf86-159">이러한 버전의 다운로드는 여전히 게시된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-159">The downloads for these still remain published:</span></span>

- <span data-ttu-id="caf86-160">3.0</span><span class="sxs-lookup"><span data-stu-id="caf86-160">3.0</span></span>
- <span data-ttu-id="caf86-161">2.2</span><span class="sxs-lookup"><span data-stu-id="caf86-161">2.2</span></span>
- <span data-ttu-id="caf86-162">2.0</span><span class="sxs-lookup"><span data-stu-id="caf86-162">2.0</span></span>

## <a name="remove-preview-versions"></a><span data-ttu-id="caf86-163">미리 보기 버전 제거</span><span class="sxs-lookup"><span data-stu-id="caf86-163">Remove preview versions</span></span>

[!INCLUDE [package-manager uninstall notice](./includes/linux-uninstall-preview-info.md)]

## <a name="how-to-install-other-versions"></a><span data-ttu-id="caf86-164">다른 버전을 설치하는 방법</span><span class="sxs-lookup"><span data-stu-id="caf86-164">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="2010-"></a><span data-ttu-id="caf86-165">20.10 ✔️</span><span class="sxs-lookup"><span data-stu-id="caf86-165">20.10 ✔️</span></span>

> [!IMPORTANT]
> <span data-ttu-id="caf86-166">.NET Core 2.1은 패키지 피드에서 아직 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-166">.NET Core 2.1 isn't yet available in the package feed.</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="2004-"></a><span data-ttu-id="caf86-167">20.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="caf86-167">20.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1910-"></a><span data-ttu-id="caf86-168">19.10 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-168">19.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1904-"></a><span data-ttu-id="caf86-169">19.04 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-169">19.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-31](includes/linux-install-31-apt.md)]

## <a name="1810-"></a><span data-ttu-id="caf86-170">18.10 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-170">18.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1804-"></a><span data-ttu-id="caf86-171">18.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="caf86-171">18.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="1710-"></a><span data-ttu-id="caf86-172">17.10 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-172">17.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1704-"></a><span data-ttu-id="caf86-173">17.04 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-173">17.04 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/17.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1610-"></a><span data-ttu-id="caf86-174">16.10 ❌</span><span class="sxs-lookup"><span data-stu-id="caf86-174">16.10 ❌</span></span>

[!INCLUDE [linux-not-supported](includes/linux-not-supported-ubuntu.md)]

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.10/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-21](includes/linux-install-21-apt.md)]

## <a name="1604-"></a><span data-ttu-id="caf86-175">16.04 ✔️</span><span class="sxs-lookup"><span data-stu-id="caf86-175">16.04 ✔️</span></span>

[!INCLUDE [linux-prep-intro-apt](includes/linux-prep-intro-apt.md)]

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

[!INCLUDE [linux-apt-install-50](includes/linux-install-50-apt.md)]

## <a name="apt-update-sdk-or-runtime"></a><span data-ttu-id="caf86-176">APT 업데이트 SDK 또는 런타임</span><span class="sxs-lookup"><span data-stu-id="caf86-176">APT update SDK or runtime</span></span>

<span data-ttu-id="caf86-177">.NET에 대한 새로운 패치 릴리스가 출시되면 다음 명령을 사용하여 APT를 통해 간단하게 업그레이드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-177">When a new patch release is available for .NET, you can simply upgrade it through APT with the following commands:</span></span>

```bash
sudo apt-get update
sudo apt-get upgrade
```

## <a name="apt-troubleshooting"></a><span data-ttu-id="caf86-178">APT 문제 해결</span><span class="sxs-lookup"><span data-stu-id="caf86-178">APT troubleshooting</span></span>

<span data-ttu-id="caf86-179">이 섹션에서는 APT를 사용하여 .NET을 설치할 때 발생할 수 있는 일반적인 오류에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-179">This section provides information on common errors you may get while using APT to install .NET.</span></span>

### <a name="unable-to-find-package"></a><span data-ttu-id="caf86-180">패키지를 찾을 수 없음</span><span class="sxs-lookup"><span data-stu-id="caf86-180">Unable to find package</span></span>

[!INCLUDE [linux-install-package-manager-x64-vs-arm](includes/linux-install-package-manager-x64-vs-arm.md)]

### <a name="unable-to-locate--some-packages-could-not-be-installed"></a><span data-ttu-id="caf86-181">찾을 수 없음 \\ 일부 패키지를 설치할 수 없음</span><span class="sxs-lookup"><span data-stu-id="caf86-181">Unable to locate \\ Some packages could not be installed</span></span>

[!INCLUDE [package-manager-failed-to-find-deb](includes/package-manager-failed-to-find-deb.md)]

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/{os-version}/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y {dotnet-package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="caf86-182">가져오지 못함</span><span class="sxs-lookup"><span data-stu-id="caf86-182">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]

## <a name="snap"></a><span data-ttu-id="caf86-183">Snap</span><span class="sxs-lookup"><span data-stu-id="caf86-183">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="caf86-184">종속성</span><span class="sxs-lookup"><span data-stu-id="caf86-184">Dependencies</span></span>

<span data-ttu-id="caf86-185">패키지 관리자를 설치할 때 이러한 라이브러리가 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-185">When you install with a package manager, these libraries are installed for you.</span></span> <span data-ttu-id="caf86-186">그러나 .NET을 수동으로 설치하거나 자체 포함 앱을 게시할 경우 이러한 라이브러리가 설치되어 있는지 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-186">But, if you manually install .NET or you publish a self-contained app, you'll need to make sure these libraries are installed:</span></span>

- <span data-ttu-id="caf86-187">libc6</span><span class="sxs-lookup"><span data-stu-id="caf86-187">libc6</span></span>
- <span data-ttu-id="caf86-188">libgcc1</span><span class="sxs-lookup"><span data-stu-id="caf86-188">libgcc1</span></span>
- <span data-ttu-id="caf86-189">libgssapi-krb5-2</span><span class="sxs-lookup"><span data-stu-id="caf86-189">libgssapi-krb5-2</span></span>
- <span data-ttu-id="caf86-190">libicu52(14.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-190">libicu52 (for 14.x)</span></span>
- <span data-ttu-id="caf86-191">libicu55(16.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-191">libicu55 (for 16.x)</span></span>
- <span data-ttu-id="caf86-192">libicu60(18.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-192">libicu60 (for 18.x)</span></span>
- <span data-ttu-id="caf86-193">libicu66(20.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-193">libicu66 (for 20.x)</span></span>
- <span data-ttu-id="caf86-194">libssl1.0.0(14.x용, 16.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-194">libssl1.0.0 (for 14.x, 16.x)</span></span>
- <span data-ttu-id="caf86-195">libssl1.1(18.x용, 20.x용)</span><span class="sxs-lookup"><span data-stu-id="caf86-195">libssl1.1 (for 18.x, 20.x)</span></span>
- <span data-ttu-id="caf86-196">libstdc++6</span><span class="sxs-lookup"><span data-stu-id="caf86-196">libstdc++6</span></span>
- <span data-ttu-id="caf86-197">zlib1g</span><span class="sxs-lookup"><span data-stu-id="caf86-197">zlib1g</span></span>

<span data-ttu-id="caf86-198">*System.Drawing.Common* 어셈블리를 사용하는 .NET 앱의 경우 다음과 같은 종속성도 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-198">For .NET apps that use the *System.Drawing.Common* assembly, you also need the following dependency:</span></span>

- <span data-ttu-id="caf86-199">libgdiplus(버전 6.0.1 이상)</span><span class="sxs-lookup"><span data-stu-id="caf86-199">libgdiplus (version 6.0.1 or later)</span></span>

  > [!WARNING]
  > <span data-ttu-id="caf86-200">시스템에 Mono 리포지토리를 추가하여 최신 버전의 *libgdiplus* 를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="caf86-200">You can install a recent version of *libgdiplus* by adding the Mono repository to your system.</span></span> <span data-ttu-id="caf86-201">자세한 내용은 <https://www.mono-project.com/download/stable/>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="caf86-201">For more information, see <https://www.mono-project.com/download/stable/>.</span></span>

## <a name="scripted-install"></a><span data-ttu-id="caf86-202">스크립팅된 설치</span><span class="sxs-lookup"><span data-stu-id="caf86-202">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="caf86-203">수동 설치</span><span class="sxs-lookup"><span data-stu-id="caf86-203">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="caf86-204">다음 단계</span><span class="sxs-lookup"><span data-stu-id="caf86-204">Next steps</span></span>

- [<span data-ttu-id="caf86-205">자습서: Visual Studio Code를 사용하여 .NET SDK에서 콘솔 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="caf86-205">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
