---
title: dotnet 명령
description: dotnet 명령(.NET CLI의 일반 드라이버) 및 사용법에 대해 알아봅니다.
ms.date: 11/11/2020
ms.openlocfilehash: 7a0c8f2eb7ab407bd725db56cbf31da4689970e4
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634027"
---
# <a name="dotnet-command"></a><span data-ttu-id="8026d-103">dotnet 명령</span><span class="sxs-lookup"><span data-stu-id="8026d-103">dotnet command</span></span>

<span data-ttu-id="8026d-104">**이 문서의 적용 대상:**  ✔️ .NET Core 2.1 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="8026d-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8026d-105">이름</span><span class="sxs-lookup"><span data-stu-id="8026d-105">Name</span></span>

<span data-ttu-id="8026d-106">`dotnet` - .NET CLI의 일반 드라이버입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-106">`dotnet` - The generic driver for the .NET CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8026d-107">개요</span><span class="sxs-lookup"><span data-stu-id="8026d-107">Synopsis</span></span>

<span data-ttu-id="8026d-108">사용 가능한 명령 및 환경에 대한 정보를 얻으려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="8026d-109">명령을 실행하려면(SDK를 설치해야 함) 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="8026d-110">애플리케이션을 실행하려면 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="8026d-111">`--roll-forward`는 .NET Core 3.x 이후로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="8026d-112">.NET Core 2.x의 경우 `--roll-forward-on-no-candidate-fx`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="8026d-113">Description</span><span class="sxs-lookup"><span data-stu-id="8026d-113">Description</span></span>

<span data-ttu-id="8026d-114">`dotnet` 명령에는 두 가지 기능이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="8026d-115">.NET 프로젝트 작업을 위한 명령을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-115">It provides commands for working with .NET projects.</span></span>

  <span data-ttu-id="8026d-116">예를 들어 [`dotnet build`](dotnet-build.md)는 프로젝트를 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="8026d-117">각 명령은 자체 옵션과 인수를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="8026d-118">모든 명령은 명령을 사용하는 방법에 대해 간략한 설명서를 출력하는 `--help` 옵션을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="8026d-119">.NET 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-119">It runs .NET applications.</span></span>

  <span data-ttu-id="8026d-120">애플리케이션을 실행할 애플리케이션 `.dll` 파일의 경로를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="8026d-121">애플리케이션을 실행하는 것은 진입점을 찾아서 실행하는 것이며 콘솔 앱의 경우에는 `Main` 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="8026d-122">예를 들어 `dotnet myapp.dll`은 `myapp` 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="8026d-123">배포 옵션에 대해 자세히 알아보려면 [.NET 애플리케이션 배포](../deploying/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-123">See [.NET application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="8026d-124">옵션</span><span class="sxs-lookup"><span data-stu-id="8026d-124">Options</span></span>

<span data-ttu-id="8026d-125">명령 실행, 애플리케이션 실행을 위해 `dotnet` 자체에 사용할 수 있는 다양한 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="8026d-126">dotnet 자체에 대한 옵션</span><span class="sxs-lookup"><span data-stu-id="8026d-126">Options for dotnet by itself</span></span>

<span data-ttu-id="8026d-127">`dotnet` 자체에 대한 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="8026d-128">예: `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="8026d-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="8026d-129">환경에 대한 정보를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="8026d-130">.NET 설치 및 머신 환경(예: 현재 운영 체제)에 대한 자세한 정보를 출력하고 .NET 버전의 SHA를 커밋합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-130">Prints out detailed information about a .NET installation and the machine environment, such as the current operating system, and commit SHA of the .NET version.</span></span>

- **`--version`**

  <span data-ttu-id="8026d-131">사용 중인 .NET SDK 버전을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-131">Prints out the version of the .NET SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="8026d-132">설치된 .NET 런타임의 목록을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-132">Prints out a list of the installed .NET runtimes.</span></span> <span data-ttu-id="8026d-133">x86 버전 SDK는 x86 런타임만 나열하며 x64 버전 SDK는 x64 런타임만 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="8026d-134">설치된 .NET SDK의 목록을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-134">Prints out a list of the installed .NET SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8026d-135">사용 가능한 명령 목록을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="8026d-136">명령을 실행하기 위한 SDK 옵션</span><span class="sxs-lookup"><span data-stu-id="8026d-136">SDK options for running a command</span></span>

<span data-ttu-id="8026d-137">명령과 함께 사용하는 `dotnet`의 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="8026d-138">예: `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="8026d-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="8026d-139">진단 출력을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="8026d-140">명령의 세부 정보 표시 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="8026d-141">허용되는 값은 `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, `diag[nostic]`입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="8026d-142">모든 명령에서 지원되지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-142">Not supported in every command.</span></span> <span data-ttu-id="8026d-143">이 옵션을 사용할 수 있는지 확인하려면 특정 명령 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="8026d-144">`dotnet build --help`와 같은 지정된 명령에 대한 설명서를 인쇄합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="8026d-145">각 명령은 해당 명령과 관련된 옵션을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="8026d-146">사용 가능한 옵션 목록은 특정 명령 페이지를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="8026d-147">런타임 옵션</span><span class="sxs-lookup"><span data-stu-id="8026d-147">Runtime options</span></span>

<span data-ttu-id="8026d-148">`dotnet`이 애플리케이션을 실행할 때 사용할 수 있는 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="8026d-149">예: `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="8026d-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="8026d-150">검색 정책 및 검색할 어셈블리를 포함하는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="8026d-151">추가적인 *.deps.json* 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="8026d-152">*deps.json* 파일에는 어셈블리 충돌을 해결하는 데 사용되는 종속성, 컴파일 종속성 및 버전 정보 목록이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="8026d-153">자세한 내용은 GitHub에서 [런타임 구성 파일](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="8026d-154">*deps.json* 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="8026d-155">*deps.json* 파일은 애플리케이션을 실행하는 데 필요한 종속성에 대한 정보를 포함하는 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="8026d-156">이 파일은 .NET SDK에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-156">This file is generated by the .NET SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="8026d-157">*runtimeconfig.json* 파일의 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="8026d-158">*runtimeconfig.json* 파일은 런타임 설정을 포함하는 구성 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="8026d-159">자세한 내용은 [.NET 런타임 구성 설정](../run-time-config/index.md#runtimeconfigjson)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-159">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="8026d-160">**`--roll-forward <SETTING>`** **.NET Core SDK 3.0부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="8026d-161">앱에 롤포워드가 적용되는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="8026d-162">`SETTING`은 다음 값 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="8026d-163">지정하지 않으면 `Minor`이 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="8026d-164">`LatestPatch` - 가장 높은 패치 버전으로 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="8026d-165">부 버전 롤포워드를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="8026d-166">`Minor` - 요청된 부 버전이 없을 경우 가장 낮은 높은 부 버전으로 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="8026d-167">요청된 부 버전이 있다면 LatestPatch 정책이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="8026d-168">`Major` - 요청된 주 버전이 없을 경우 가장 낮은 높은 주 버전으로 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="8026d-169">요청된 주 버전이 있다면 Minor 정책이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="8026d-170">`LatestMinor` - 요청된 부 버전이 있는 경우에도 가장 높은 부 버전으로 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="8026d-171">구성 요소 호스팅 시나리오를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="8026d-172">`LatestMajor` - 요청된 주 버전이 있는 경우에도 가장 높은 주 버전, 가장 높은 부 버전으로 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="8026d-173">구성 요소 호스팅 시나리오를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="8026d-174">`Disable` - 롤포워드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="8026d-175">지정된 버전에만 바인딩합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-175">Only bind to specified version.</span></span> <span data-ttu-id="8026d-176">이 정책은 최신 패치를 롤포워드할 수 있는 기능을 사용하지 않도록 설정하므로 일반 용도에는 좋지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="8026d-177">이 값은 테스트용으로만 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="8026d-178">`Disable`을 제외하고, 모든 설정에서 사용 가능한 가장 높은 패치 버전을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="8026d-179">롤포워드 동작은 프로젝트 파일 속성, 런타임 구성 파일 속성 및 환경 변수에서도 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="8026d-180">자세한 내용은 [주 버전 런타임 롤포워드](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="8026d-181">**`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2.x SDK에서 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="8026d-182">필요한 공유 프레임워크를 사용할 수 없을 때 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="8026d-183">`N`는 다음이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-183">`N` can be:</span></span>

  - <span data-ttu-id="8026d-184">`0` - 부 버전 롤포워드도 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="8026d-185">`1` - 부 버전에서는 롤포워드하지만 주 버전에서는 롤포워드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="8026d-186">이것은 기본적인 동작입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-186">This is the default behavior.</span></span>
  - <span data-ttu-id="8026d-187">`2` - 부 버전과 주 버전에서 롤포워드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="8026d-188">자세한 내용은 [롤포워드](../whats-new/dotnet-core-2-1.md#roll-forward)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="8026d-189">.NET Core 3.0부터 이 옵션은 `--roll-forward`로 대체되었으므로 이 옵션을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="8026d-190">애플리케이션 실행에 사용할 .NET 런타임의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-190">Version of the .NET runtime to use to run the application.</span></span>

  <span data-ttu-id="8026d-191">이 옵션은 애플리케이션의 `.runtimeconfig.json` 파일에 있는 첫 번째 프레임워크 참조의 버전을 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="8026d-192">그러므로 프레임워크 참조가 하나만 있는 경우에만 예상대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="8026d-193">애플리케이션에 둘 이상의 프레임워크 참조가 있는 경우 이 옵션을 사용하면 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="8026d-194">dotnet 명령</span><span class="sxs-lookup"><span data-stu-id="8026d-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="8026d-195">일반</span><span class="sxs-lookup"><span data-stu-id="8026d-195">General</span></span>

| <span data-ttu-id="8026d-196">명령</span><span class="sxs-lookup"><span data-stu-id="8026d-196">Command</span></span>                                       | <span data-ttu-id="8026d-197">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="8026d-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="8026d-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="8026d-199">.NET 애플리케이션을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-199">Builds a .NET application.</span></span>                                     |
| [<span data-ttu-id="8026d-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="8026d-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="8026d-201">빌드에서 시작된 서버와 상호 작용합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="8026d-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="8026d-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="8026d-203">빌드 출력을 정리합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="8026d-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="8026d-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="8026d-205">명령에 대한 자세한 온라인 설명서를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="8026d-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="8026d-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="8026d-207">유효한 Preview 2 프로젝트를 .NET Core SDK 1.0 프로젝트로 마이그레이션합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="8026d-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="8026d-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="8026d-209">MSBuild 명령줄에 대한 액세스 권한을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="8026d-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="8026d-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="8026d-211">지정한 템플릿에 대해 C# 또는 F# 프로젝트를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="8026d-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="8026d-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="8026d-213">코드의 NuGet 패키지를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="8026d-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="8026d-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="8026d-215">.NET Framework 종속형 또는 자체 포함 애플리케이션을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="8026d-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="8026d-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="8026d-217">지정된 애플리케이션에 대한 종속성을 복원합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="8026d-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="8026d-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="8026d-219">소스에서 애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="8026d-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="8026d-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="8026d-221">솔루션 파일에 프로젝트를 추가, 제거 및 나열하는 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="8026d-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="8026d-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="8026d-223">어셈블리를 런타임 패키지 저장소에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="8026d-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="8026d-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="8026d-225">Test Runner를 사용하여 테스트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="8026d-226">프로젝트 참조</span><span class="sxs-lookup"><span data-stu-id="8026d-226">Project references</span></span>

<span data-ttu-id="8026d-227">명령</span><span class="sxs-lookup"><span data-stu-id="8026d-227">Command</span></span> | <span data-ttu-id="8026d-228">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-228">Function</span></span>
--- | ---
[<span data-ttu-id="8026d-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="8026d-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="8026d-230">프로젝트 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-230">Adds a project reference.</span></span>
[<span data-ttu-id="8026d-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="8026d-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="8026d-232">프로젝트 참조를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-232">Lists project references.</span></span>
[<span data-ttu-id="8026d-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="8026d-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="8026d-234">프로젝트 참조를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="8026d-235">NuGet 패키지</span><span class="sxs-lookup"><span data-stu-id="8026d-235">NuGet packages</span></span>

<span data-ttu-id="8026d-236">명령</span><span class="sxs-lookup"><span data-stu-id="8026d-236">Command</span></span> | <span data-ttu-id="8026d-237">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-237">Function</span></span>
--- | ---
[<span data-ttu-id="8026d-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="8026d-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="8026d-239">NuGet 패키지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="8026d-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="8026d-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="8026d-241">NuGet 패키지를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="8026d-242">NuGet 명령</span><span class="sxs-lookup"><span data-stu-id="8026d-242">NuGet commands</span></span>

<span data-ttu-id="8026d-243">명령</span><span class="sxs-lookup"><span data-stu-id="8026d-243">Command</span></span> | <span data-ttu-id="8026d-244">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-244">Function</span></span>
--- | ---
[<span data-ttu-id="8026d-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="8026d-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="8026d-246">서버에서 패키지를 삭제하거나 목록에서 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="8026d-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="8026d-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="8026d-248">서버에 패키지를 푸시하고 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="8026d-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="8026d-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="8026d-250">http-request 캐시, 임시 캐시 또는 시스템 전체의 글로벌 패키지 폴더와 같은 로컬 NuGet 리소스를 지우거나 목록에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="8026d-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="8026d-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="8026d-252">NuGet 소스를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="8026d-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="8026d-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="8026d-254">NuGet 소스를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="8026d-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="8026d-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="8026d-256">NuGet 소스를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="8026d-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="8026d-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="8026d-258">구성된 NuGet 소스를 모두 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="8026d-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="8026d-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="8026d-260">NuGet 소스를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="8026d-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="8026d-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="8026d-262">NuGet 소스를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="8026d-263">전역, 도구 경로 및 로컬 도구 명령</span><span class="sxs-lookup"><span data-stu-id="8026d-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="8026d-264">도구는 NuGet 패키지에서 설치되고 명령 프롬프트에서 호출되는 콘솔 애플리케이션입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="8026d-265">도구를 직접 작성하거나 타사에서 작성한 도구를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="8026d-266">도구를 전역 도구, 도구 경로 도구 및 로컬 도구라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="8026d-267">자세한 내용은 [.NET 도구 개요](global-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-267">For more information, see [.NET tools overview](global-tools.md).</span></span> <span data-ttu-id="8026d-268">전역 및 도구 경로 도구는 .NET Core SDK 2.1부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="8026d-269">로컬 도구는 .NET Core SDK 3.0부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="8026d-270">명령</span><span class="sxs-lookup"><span data-stu-id="8026d-270">Command</span></span> | <span data-ttu-id="8026d-271">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-271">Function</span></span>
--- | ---
[<span data-ttu-id="8026d-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="8026d-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="8026d-273">컴퓨터에 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="8026d-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="8026d-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="8026d-275">컴퓨터에 현재 설치되어 있는 모든 전역, 도구 경로 또는 로컬 도구를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="8026d-276">dotnet tool search</span><span class="sxs-lookup"><span data-stu-id="8026d-276">dotnet tool search</span></span>](dotnet-tool-list.md) | <span data-ttu-id="8026d-277">NuGet.org에서 지정된 검색 용어가 이름 또는 메타데이터에 포함된 도구를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-277">Searches NuGet.org for tools that have the specified search term in their name or metadata.</span></span>
[<span data-ttu-id="8026d-278">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="8026d-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="8026d-279">컴퓨터에서 도구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-279">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="8026d-280">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="8026d-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="8026d-281">컴퓨터에 설치된 도구를 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-281">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="8026d-282">추가 도구</span><span class="sxs-lookup"><span data-stu-id="8026d-282">Additional tools</span></span>

<span data-ttu-id="8026d-283">.NET Core SDK 2.1.300부터는 `DotnetCliToolReference`를 사용하여 프로젝트별로만 사용할 수 있었던 여러 도구를 .NET SDK의 일부로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET SDK.</span></span> <span data-ttu-id="8026d-284">이러한 도구는 다음 표에 나열되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-284">These tools are listed in the following table:</span></span>

| <span data-ttu-id="8026d-285">도구</span><span class="sxs-lookup"><span data-stu-id="8026d-285">Tool</span></span>                                              | <span data-ttu-id="8026d-286">기능</span><span class="sxs-lookup"><span data-stu-id="8026d-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="8026d-287">dev-certs</span><span class="sxs-lookup"><span data-stu-id="8026d-287">dev-certs</span></span>                                         | <span data-ttu-id="8026d-288">개발 인증서를 만들고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="8026d-289">ef</span><span class="sxs-lookup"><span data-stu-id="8026d-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="8026d-290">Entity Framework Core 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="8026d-291">sql-cache</span><span class="sxs-lookup"><span data-stu-id="8026d-291">sql-cache</span></span>                                         | <span data-ttu-id="8026d-292">SQL Server 캐시 명령줄 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="8026d-293">user-secrets</span><span class="sxs-lookup"><span data-stu-id="8026d-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="8026d-294">개발 사용자 비밀을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="8026d-295">watch</span><span class="sxs-lookup"><span data-stu-id="8026d-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="8026d-296">파일이 변경될 때 명령을 실행하는 파일 감시자를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="8026d-297">각 도구에 대한 자세한 내용을 보려면 `dotnet <tool-name> --help`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-297">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="8026d-298">예</span><span class="sxs-lookup"><span data-stu-id="8026d-298">Examples</span></span>

<span data-ttu-id="8026d-299">새 .NET 콘솔 애플리케이션 만들기</span><span class="sxs-lookup"><span data-stu-id="8026d-299">Create a new .NET console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="8026d-300">지정된 디렉터리에서 프로젝트 및 해당 종속성을 빌드합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-300">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="8026d-301">애플리케이션을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-301">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="8026d-302">환경 변수</span><span class="sxs-lookup"><span data-stu-id="8026d-302">Environment variables</span></span>

- <span data-ttu-id="8026d-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="8026d-303">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="8026d-304">기본 위치에 설치되지 않은 경우 .NET 런타임의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-304">Specifies the location of the .NET runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="8026d-305">Windows에서 기본 위치는 `C:\Program Files\dotnet`입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-305">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="8026d-306">Linux 및 macOS에서 기본 위치는 `/usr/share/dotnet`입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-306">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="8026d-307">이 환경 변수는 생성된 실행 파일(apphost)을 통해 앱을 실행할 때만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-307">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="8026d-308">64비트 OS에서 32비트 실행 파일을 실행할 때는 대신 `DOTNET_ROOT(x86)`가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-308">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `NUGET_PACKAGES`

  <span data-ttu-id="8026d-309">글로벌 패키지 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-309">The global packages folder.</span></span> <span data-ttu-id="8026d-310">설정하지 않으면 기본적으로 Unix에서는 `~/.nuget/packages`, Windows에서는 `%userprofile%\.nuget\packages`로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-310">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="8026d-311">런타임을 로드할 때 공유 호스트에서 사용할 서비스 인덱스의 위치를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-311">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="8026d-312">처음 실행할 때 .NET 시작 및 원격 분석 메시지를 표시할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-312">Specifies whether .NET welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="8026d-313">이러한 메시지를 음소거하려면 `true`로 설정하고(`true`, `1` 또는 `yes` 값 사용) 허용하려면 `false`로 설정합니다(`false`, `0` 또는 `no` 값 사용).</span><span class="sxs-lookup"><span data-stu-id="8026d-313">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8026d-314">설정되지 않은 경우 기본값은 `false`이고 처음 실행될 때 메시지가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-314">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="8026d-315">이 플래그는 원격 분석에는 영향을 주지 않습니다(원격 분석 보내기를 옵트아웃하는 경우 `DOTNET_CLI_TELEMETRY_OPTOUT` 참조).</span><span class="sxs-lookup"><span data-stu-id="8026d-315">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="8026d-316">.NET 도구 사용에 대한 데이터를 수집하여 Microsoft에 전송할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-316">Specifies whether data about the .NET tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="8026d-317">원격 분석 기능을 옵트아웃하려면 `true`로 설정합니다(값 `true`, `1` 또는 `yes`가 허용됨).</span><span class="sxs-lookup"><span data-stu-id="8026d-317">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="8026d-318">이외의 경우 원격 분석 기능을 옵트인하려면 `false`로 설정합니다(`false`, `0` 또는 `no`가 허용됨).</span><span class="sxs-lookup"><span data-stu-id="8026d-318">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="8026d-319">설정하지 않으면 기본적으로 `false`이고 원격 분석 기능은 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-319">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="8026d-320">전역 위치에서 .NET 런타임, 공유 프레임워크 또는 SDK가 확인되는지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-320">Specifies whether .NET runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="8026d-321">설정하지 않은 경우 기본값은 1(논리적 `true`)입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-321">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="8026d-322">전역 위치에서 확인하지 않고 격리된 .NET 설치를 사용하려면 0(논리적 `false`)으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-322">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET installations.</span></span> <span data-ttu-id="8026d-323">다중 수준의 조회에 대한 자세한 내용은 [다중 수준 SharedFX 조회](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-323">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="8026d-324">`DOTNET_ROLL_FORWARD` **.NET Core 3.x부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-324">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="8026d-325">롤포워드 동작을 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-325">Determines roll forward behavior.</span></span> <span data-ttu-id="8026d-326">자세한 내용은 이 문서 앞부분에서 `--roll-forward` 옵션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-326">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="8026d-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **.NET Core 3.x부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-327">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="8026d-328">`1`(사용)로 설정된 경우 릴리스 버전에서 시험판 버전으로 롤포워드를 사용하도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-328">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="8026d-329">기본적으로(`0` - 사용 안 함) .NET 런타임의 릴리스 버전이 요청되면 롤포워드는 설치된 릴리스 버전만 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-329">By default (`0` - disabled), when a release version of .NET runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="8026d-330">자세한 내용은 [롤포워드](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-330">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="8026d-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2.x에서 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-331">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="8026d-332">`0`으로 설정된 경우 부 버전 롤포워드를 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-332">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="8026d-333">자세한 내용은 [롤포워드](../whats-new/dotnet-core-2-1.md#roll-forward)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-333">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="8026d-334">이 설정은 .NET Core 3.0에서 `DOTNET_ROLL_FORWARD`로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-334">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="8026d-335">새 설정을 대신 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-335">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="8026d-336">`en-us`와 같은 로캘 값을 사용하여 CLI UI의 언어를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-336">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="8026d-337">지원되는 값은 Visual Studio의 경우와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-337">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="8026d-338">자세한 내용은 [Visual Studio 설치 설명서](/visualstudio/install/install-visual-studio)에서 설치 프로그램 언어 변경에 대한 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-338">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="8026d-339">.NET 리소스 관리자 규칙이 적용되므로, 정확한 일치를 선택할 필요가 없습니다. `CultureInfo` 트리에서 하위 항목을 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-339">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="8026d-340">예를 들어 `fr-CA`로 설정하면 CLI에서 `fr` 번역을 찾아 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-340">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="8026d-341">지원되지 않는 언어로 설정하면 CLI는 영어로 대체됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-341">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="8026d-342">GUI 지원 생성된 실행 파일의 경우 일반적으로 특정 오류 클래스에 대해 표시하는 대화 상자 팝업을 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-342">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="8026d-343">`stderr`에만 쓰고 이러한 경우에는 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-343">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="8026d-344">CLI 옵션 `--additional-deps`와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-344">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="8026d-345">검색된 RID를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-345">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="8026d-346">일부 경우에는 어셈블리 확인이 대체되는 "공유 저장소"의 위치입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-346">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="8026d-347">시작 후크를 로드하고 실행하는 어셈블리의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-347">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="8026d-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **.NET Core 3.x부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-348">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="8026d-349">단일 파일 애플리케이션이 실행되기 전에 추출되는 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-349">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="8026d-350">자세한 내용은 [단일 파일 실행 파일](../whats-new/dotnet-core-3-0.md#single-file-executables)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="8026d-350">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="8026d-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="8026d-351">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="8026d-352">호스팅 구성 요소(예: `dotnet.exe`, `hostfxr`, `hostpolicy`)에서 진단 추적을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-352">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="8026d-353">`COREHOST_TRACE=[0/1]` -기본값은 `0`(추적 사용 안 함)입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-353">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="8026d-354">`1`로 설정된 경우 진단 추적이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-354">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="8026d-355">`COREHOST_TRACEFILE=<file path>` - `COREHOST_TRACE=1`을 통해 추적을 사용하도록 설정한 경우에만 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-355">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="8026d-356">설정되면 추적 정보가 지정된 파일에 기록되고, 그렇지 않으면 추적 정보가 `stderr`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-356">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="8026d-357">**.NET Core 3.x부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-357">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="8026d-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - 기본값은 `4`입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-358">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="8026d-359">이 설정은 `COREHOST_TRACE=1`을 통해 추적을 사용하도록 설정한 경우에만 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-359">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="8026d-360">**.NET Core 3.x부터 사용할 수 있습니다.**</span><span class="sxs-lookup"><span data-stu-id="8026d-360">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="8026d-361">`4` - 모든 추적 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-361">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="8026d-362">`3` - 정보, 경고 및 오류 메시지만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-362">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="8026d-363">`2` - 경고 및 오류 메시지만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-363">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="8026d-364">`1` - 오류 메시지만 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-364">`1` - only error messages are written</span></span>

  <span data-ttu-id="8026d-365">애플리케이션 시작에 대한 자세한 추적 정보를 얻는 일반적인 방법은 `COREHOST_TRACE=1` 및 `COREHOST_TRACEFILE=host_trace.txt`를 설정하고 애플리케이션을 실행하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-365">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="8026d-366">현재 디렉터리에 새 파일 `host_trace.txt`가 생성되어 자세한 정보가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="8026d-366">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="8026d-367">참조</span><span class="sxs-lookup"><span data-stu-id="8026d-367">See also</span></span>

- [<span data-ttu-id="8026d-368">런타임 구성 파일</span><span class="sxs-lookup"><span data-stu-id="8026d-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="8026d-369">.NET 런타임 구성 설정</span><span class="sxs-lookup"><span data-stu-id="8026d-369">.NET run-time configuration settings</span></span>](../run-time-config/index.md)
