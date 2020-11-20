---
title: dotnet 명령에 대한 관리자 액세스 권한
description: 관리자 액세스 권한이 필요한 dotnet 명령에 대한 모범 사례를 알아봅니다.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: b34a4d631ec0e5ef641e1ffbc91e081d25645157
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634053"
---
# <a name="elevated-access-for-dotnet-commands"></a><span data-ttu-id="5163e-103">dotnet 명령에 대한 관리자 액세스 권한</span><span class="sxs-lookup"><span data-stu-id="5163e-103">Elevated access for dotnet commands</span></span>

<span data-ttu-id="5163e-104">소프트웨어 개발 모범 사례는 개발자에게 최소한의 권한만 요구하는 소프트웨어를 작성하도록 안내합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-104">Software development best practices guide developers to writing software that requires the least amount of privilege.</span></span> <span data-ttu-id="5163e-105">그러나 성능 모니터링 도구와 같은 일부 소프트웨어는 운영 체제 규칙 때문에 관리자 권한이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-105">However, some software, like performance monitoring tools, requires admin permission because of operating system rules.</span></span> <span data-ttu-id="5163e-106">다음 지침은 이러한 소프트웨어를 .NET Core로 작성하기 위해 지원되는 시나리오를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-106">The following guidance describes supported scenarios for writing such software with .NET Core.</span></span>

<span data-ttu-id="5163e-107">다음 명령을 관리자 권한으로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-107">The following commands can be run elevated:</span></span>

- <span data-ttu-id="5163e-108">[dotnet 도구 설치](dotnet-tool-install.md)와 같은 `dotnet tool` 명령.</span><span class="sxs-lookup"><span data-stu-id="5163e-108">`dotnet tool` commands, such as [dotnet tool install](dotnet-tool-install.md).</span></span>
- `dotnet run --no-build`
- `dotnet-core-uninstall`

<span data-ttu-id="5163e-109">상승된 다른 명령을 실행하지 않은 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-109">We don't recommend running other commands elevated.</span></span> <span data-ttu-id="5163e-110">특히 [dotnet restore](dotnet-restore.md), [dotnet 빌드](dotnet-build.md) 및 [dotnet 실행](dotnet-run.md)과 같이 MSBuild를 사용하는 명령으로 권한 상승은 권장하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-110">In particular, we don't recommend elevation with commands that use MSBuild, such as [dotnet restore](dotnet-restore.md), [dotnet build](dotnet-build.md), and [dotnet run](dotnet-run.md).</span></span> <span data-ttu-id="5163e-111">기본 문제는 사용자가 dotnet 명령을 실행한 후 루트 계정과 제한된 계정 간에 앞뒤로 전환될 때 사용 권한 관리 문제입니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-111">The primary issue is permission management problems when a user transitions back and forth between root and a restricted account after issuing dotnet commands.</span></span> <span data-ttu-id="5163e-112">제한된 사용자로 루트 사용자가 빌드한 파일에 액세스할 수 없다는 것을 알 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-112">You may find as a restricted user that you don't have access to the file built by a root user.</span></span> <span data-ttu-id="5163e-113">이 상황을 해결하는 방법이 있지만 처음부터 시작할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-113">There are ways to resolve this situation, but they're unnecessary to get into in the first place.</span></span>

<span data-ttu-id="5163e-114">루트 계정과 제한된 계정 간에 앞뒤로 전환하지 않는 한 루트로 명령을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-114">You can run commands as root as long as you don't transition back and forth between root and a restricted account.</span></span> <span data-ttu-id="5163e-115">예를 들어 Docker 컨테이너는 기본적으로 루트로 실행되므로 이러한 특성을 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-115">For example, Docker containers run as root by default, so they have this characteristic.</span></span>

## <a name="global-tool-installation"></a><span data-ttu-id="5163e-116">글로벌 도구 설치</span><span class="sxs-lookup"><span data-stu-id="5163e-116">Global tool installation</span></span>

<span data-ttu-id="5163e-117">다음 지침은 실행하려면 상승된 권한이 필요한 .NET 도구를 설치, 실행 및 제거하는 권장 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-117">The following instructions demonstrate the recommended way to install, run, and uninstall .NET tools that require elevated permissions to execute.</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="5163e-118">Windows</span><span class="sxs-lookup"><span data-stu-id="5163e-118">Windows</span></span>](#tab/windows)

### <a name="install-the-tool"></a><span data-ttu-id="5163e-119">도구 설치</span><span class="sxs-lookup"><span data-stu-id="5163e-119">Install the tool</span></span>

<span data-ttu-id="5163e-120">`%ProgramFiles%\dotnet-tools` 폴더가 이미 있는 경우 다음을 수행하여 "사용자" 그룹에 해당 디렉터리를 쓰거나 수정할 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-120">If the folder `%ProgramFiles%\dotnet-tools` already exists, do the following to check whether the "Users" group has permission to write or modify that directory:</span></span>

- <span data-ttu-id="5163e-121">`%ProgramFiles%\dotnet-tools` 폴더를 마우스 오른쪽 단추로 클릭하고 **속성** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-121">Right-click the `%ProgramFiles%\dotnet-tools` folder and select **Properties**.</span></span> <span data-ttu-id="5163e-122">**명령 속성** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-122">The **Common Properties** dialog box opens.</span></span>
- <span data-ttu-id="5163e-123">**보안** 탭을 선택합니다. **그룹 또는 사용자 이름** 에서 “사용자” 그룹에 디렉터리를 쓰거나 수정할 수 있는 권한이 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-123">Select the **Security** tab. Under **Group or user names**, check whether the "Users" group has permission to write or modify the directory.</span></span>
- <span data-ttu-id="5163e-124">"사용자" 그룹에 디렉터리를 쓰거나 수정할 수 있는 경우 *dotnet-tools* 가 아닌 도구를 설치할 때 다른 디렉터리 이름을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-124">If the "Users" group can write or modify the directory, use a different directory name when installing the tools rather than *dotnet-tools*.</span></span>

<span data-ttu-id="5163e-125">도구를 설치하려면 관리자 권한 프롬프트에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-125">To install tools, run the following command in elevated prompt.</span></span> <span data-ttu-id="5163e-126">설치 중에 *dotnet-tools* 폴더를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-126">It will create the *dotnet-tools* folder during the installation.</span></span>

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a><span data-ttu-id="5163e-127">글로벌 도구 실행</span><span class="sxs-lookup"><span data-stu-id="5163e-127">Run the global tool</span></span>

<span data-ttu-id="5163e-128">**옵션 1** 관리자 권한 프롬프트를 통해 전체 경로 사용:</span><span class="sxs-lookup"><span data-stu-id="5163e-128">**Option 1** Use the full path with elevated prompt:</span></span>

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

<span data-ttu-id="5163e-129">**옵션 2** 새로 만든 폴더를 `%Path%`에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-129">**Option 2** Add the newly created folder to `%Path%`.</span></span> <span data-ttu-id="5163e-130">이 작업은 한 번만 수행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-130">You only need to do this operation once.</span></span>

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

<span data-ttu-id="5163e-131">다음 항목으로 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-131">And run with:</span></span>

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a><span data-ttu-id="5163e-132">글로벌 도구 제거</span><span class="sxs-lookup"><span data-stu-id="5163e-132">Uninstall the global tool</span></span>

<span data-ttu-id="5163e-133">관리자 권한 프롬프트에 다음 명령을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-133">In an elevated prompt, type the following command:</span></span>

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[<span data-ttu-id="5163e-134">Linux</span><span class="sxs-lookup"><span data-stu-id="5163e-134">Linux</span></span>](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[<span data-ttu-id="5163e-135">macOS</span><span class="sxs-lookup"><span data-stu-id="5163e-135">macOS</span></span>](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a><span data-ttu-id="5163e-136">로컬 도구</span><span class="sxs-lookup"><span data-stu-id="5163e-136">Local tools</span></span>

<span data-ttu-id="5163e-137">로컬 도구는 사용자당 하위 디렉터리 트리별로 범위가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-137">Local tools are scoped per subdirectory tree, per user.</span></span> <span data-ttu-id="5163e-138">관리자 권한으로 실행되면 로컬 도구는 제한된 사용자 환경을 권한이 높은 환경에 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-138">When run elevated, local tools share a restricted user environment to the elevated environment.</span></span> <span data-ttu-id="5163e-139">Linux 및 macOS에서는 이로 인해 파일이 루트 사용자 전용 액세스로 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-139">In Linux and macOS, this results in files being set with root user-only access.</span></span> <span data-ttu-id="5163e-140">사용자가 제한된 계정으로 전환하면 사용자는 더 이상 파일에 액세스하거나 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-140">If the user switches back to a restricted account, the user can no longer access or write to the files.</span></span> <span data-ttu-id="5163e-141">따라서 권한 상승이 필요한 도구를 로컬 도구로 설치하는 것은 권장되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-141">So installing tools that require elevation as local tools isn't recommended.</span></span> <span data-ttu-id="5163e-142">대신 글로벌 도구용 `--tool-path` 옵션과 이전 지침을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-142">Instead, use the `--tool-path` option and the previous guidelines for global tools.</span></span>

## <a name="elevation-during-development"></a><span data-ttu-id="5163e-143">개발 중 권한 상승</span><span class="sxs-lookup"><span data-stu-id="5163e-143">Elevation during development</span></span>

<span data-ttu-id="5163e-144">개발하는 동안 애플리케이션을 테스트하기 위해 높은 액세스 권한이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-144">During development, you may need elevated access to test your application.</span></span> <span data-ttu-id="5163e-145">예를 들어 이 시나리오는 일반적으로 IoT 앱에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-145">This scenario is common for IoT apps, for example.</span></span> <span data-ttu-id="5163e-146">권한 상승 없이 애플리케이션을 빌드한 다음, 권한 상승을 통해 실행하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-146">We recommend that you build the application without elevation and then run it with elevation.</span></span> <span data-ttu-id="5163e-147">다음과 같이 몇 가지 패턴이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5163e-147">There are a few patterns, as follows:</span></span>

- <span data-ttu-id="5163e-148">생성된 실행 파일 사용(최상의 시작 성능 제공):</span><span class="sxs-lookup"><span data-stu-id="5163e-148">Using generated executable (it provides the best startup performance):</span></span>

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- <span data-ttu-id="5163e-149">새 이진 파일을 생성하지 않으려면 `—no-build` 플래그와 함께 [dotnet 실행](dotnet-run.md) 명령 사용:</span><span class="sxs-lookup"><span data-stu-id="5163e-149">Using the [dotnet run](dotnet-run.md) command with the `—no-build` flag to avoid generating new binaries:</span></span>

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a><span data-ttu-id="5163e-150">참조</span><span class="sxs-lookup"><span data-stu-id="5163e-150">See also</span></span>

- [<span data-ttu-id="5163e-151">.NET 도구 개요</span><span class="sxs-lookup"><span data-stu-id="5163e-151">.NET tools overview</span></span>](global-tools.md)
