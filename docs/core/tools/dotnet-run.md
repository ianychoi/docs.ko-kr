---
title: dotnet run 명령
description: dotnet run 명령은 소스 코드에서 애플리케이션을 실행하는 편리한 옵션을 제공합니다.
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634418"
---
# <a name="dotnet-run"></a><span data-ttu-id="7a18c-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="7a18c-103">dotnet run</span></span>

<span data-ttu-id="7a18c-104">**이 문서의 적용 대상:** ✔️ .NET Core 2.x SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="7a18c-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7a18c-105">이름</span><span class="sxs-lookup"><span data-stu-id="7a18c-105">Name</span></span>

<span data-ttu-id="7a18c-106">`dotnet run` - 명시적 컴파일이나 시작 명령을 사용하지 않고 소스 코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7a18c-107">개요</span><span class="sxs-lookup"><span data-stu-id="7a18c-107">Synopsis</span></span>

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a><span data-ttu-id="7a18c-108">설명</span><span class="sxs-lookup"><span data-stu-id="7a18c-108">Description</span></span>

<span data-ttu-id="7a18c-109">`dotnet run` 명령은 하나의 명령을 사용하여 소스 코드에서 애플리케이션을 실행하는 편리한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-109">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="7a18c-110">명령줄에서 빠른 반복 개발에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-110">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="7a18c-111">이 명령은 코드 빌드 시 [`dotnet build`](dotnet-build.md) 명령에 의존합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-111">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="7a18c-112">프로젝트를 먼저 복원해야 하는 등, 빌드에 대한 요구 사항은 `dotnet run`에도 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-112">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="7a18c-113">출력 파일은 기본 위치, 즉 `bin/<configuration>/<target>`에 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-113">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="7a18c-114">예를 들어 `netcoreapp2.1` 애플리케이션이 있고 `dotnet run`을 실행하는 경우 출력은 `bin/Debug/netcoreapp2.1`에 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-114">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="7a18c-115">필요에 따라 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-115">Files are overwritten as needed.</span></span> <span data-ttu-id="7a18c-116">임시 파일은 `obj` 디렉터리에 놓입니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-116">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="7a18c-117">프로젝트가 여러 프레임워크를 지정하는 경우 프레임워크를 지정하는 데 `-f|--framework <FRAMEWORK>` 옵션을 사용하지 않은 한, `dotnet run`을 실행하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-117">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="7a18c-118">`dotnet run` 명령은 빌드된 어셈블리가 아닌 프로젝트의 컨텍스트에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-118">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="7a18c-119">대신 프레임워크 종속 애플리케이션 DLL을 실행하려고 하는 경우 명령 없이 [dotnet](dotnet.md)을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-119">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="7a18c-120">예를 들어 `myapp.dll`을 실행하려면 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-120">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="7a18c-121">`dotnet` 드라이버에 대한 자세한 내용은 [.NET 명령줄 도구(CLI)](index.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a18c-121">For more information on the `dotnet` driver, see the [.NET Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="7a18c-122">애플리케이션을 실행하기 위해 `dotnet run` 명령은 NuGet 캐시에서 공유 런타임의 외부에 있는 애플리케이션의 종속성을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-122">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="7a18c-123">캐시된 종속성을 사용하기 때문에 프로덕션 환경에서 애플리케이션을 실행하는 데 `dotnet run`을 사용하는 것은 바람직하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-123">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="7a18c-124">대신, [`dotnet publish`](dotnet-publish.md) 명령을 사용하여 [배포를 만들고](../deploying/index.md) 게시된 출력을 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-124">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="7a18c-125">암시적 복원</span><span class="sxs-lookup"><span data-stu-id="7a18c-125">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="7a18c-126">옵션</span><span class="sxs-lookup"><span data-stu-id="7a18c-126">Options</span></span>

- **`--`**

  <span data-ttu-id="7a18c-127">실행 중인 애플리케이션에 대한 인수에서 `dotnet run`에 대한 인수를 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-127">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="7a18c-128">이 구분 기호 다음의 모든 인수가 실행 중인 애플리케이션에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-128">All arguments after this delimiter are passed to the application run.</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="7a18c-129">빌드 구성을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-129">Defines the build configuration.</span></span> <span data-ttu-id="7a18c-130">대부분의 프로젝트에 대한 기본값은 `Debug`이지만 프로젝트의 빌드 구성 설정을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-130">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="7a18c-131">지정된 [프레임워크](../../standard/frameworks.md)를 사용하여 앱을 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-131">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="7a18c-132">프레임워크는 프로젝트 파일에 지정되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-132">The framework must be specified in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="7a18c-133">마지막 복원이 성공한 경우에도 모든 종속성을 강제 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-133">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="7a18c-134">이 플래그를 지정하는 것은 *project.assets.json* 파일을 삭제하는 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-134">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7a18c-135">명령에 대한 간단한 도움말을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-135">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="7a18c-136">명령이 중지되고 사용자 입력 또는 작업을 대기할 수 있도록 허용합니다(예: 인증 완료).</span><span class="sxs-lookup"><span data-stu-id="7a18c-136">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="7a18c-137">.NET Core 3.0 SDK 이후 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-137">Available since .NET Core 3.0 SDK.</span></span>

- **`--launch-profile <NAME>`**

  <span data-ttu-id="7a18c-138">애플리케이션을 시작할 때 사용할 시작 프로필(있는 경우)의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-138">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="7a18c-139">시작 프로필은 *launchSettings.json* 파일에서 정의되고 일반적으로 `Development`, `Staging` 및 `Production`이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-139">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="7a18c-140">자세한 내용은 [여러 환경 사용](/aspnet/core/fundamentals/environments)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a18c-140">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

- **`--no-build`**

  <span data-ttu-id="7a18c-141">실행하기 전에 프로젝트를 빌드하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-141">Doesn't build the project before running.</span></span> <span data-ttu-id="7a18c-142">또한 `--no-restore` 플래그를 암시적으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-142">It also implicit sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="7a18c-143">프로젝트 간(P2P) 참조를 사용하여 프로젝트를 복원할 경우 참조가 아닌 루트 프로젝트를 복원하세요.</span><span class="sxs-lookup"><span data-stu-id="7a18c-143">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--no-launch-profile`**

  <span data-ttu-id="7a18c-144">애플리케이션을 구성하는 데 *launchSettings.json* 을 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-144">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

- **`--no-restore`**

  <span data-ttu-id="7a18c-145">명령을 실행할 때 암시적 복원을 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-145">Doesn't execute an implicit restore when running the command.</span></span>

- **`-p|--project <PATH>`**

  <span data-ttu-id="7a18c-146">실행할 프로젝트 파일의 경로를 지정합니다(폴더 이름 또는 전체 경로).</span><span class="sxs-lookup"><span data-stu-id="7a18c-146">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="7a18c-147">지정하지 않으면 현재 디렉터리로 기본 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-147">If not specified, it defaults to the current directory.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="7a18c-148">패키지를 복원할 대상 런타임을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-148">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="7a18c-149">RID(런타임 식별자) 목록은 [RID 카탈로그](../rid-catalog.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7a18c-149">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="7a18c-150">.NET Core 3.0 SDK 이후 사용할 수 있는 `-r` 짧은 옵션입니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-150">`-r` short option available since .NET Core 3.0 SDK.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7a18c-151">명령의 세부 정보 표시 수준을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7a18c-152">허용되는 값은 `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, `diag[nostic]`입니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="7a18c-153">기본값은 `m`입니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-153">The default value is `m`.</span></span> <span data-ttu-id="7a18c-154">.NET Core 2.1 SDK부터 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-154">Available since .NET Core 2.1 SDK.</span></span>

## <a name="examples"></a><span data-ttu-id="7a18c-155">예</span><span class="sxs-lookup"><span data-stu-id="7a18c-155">Examples</span></span>

- <span data-ttu-id="7a18c-156">현재 디렉터리에 있는 프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-156">Run the project in the current directory:</span></span>

  ```dotnetcli
  dotnet run
  ```

- <span data-ttu-id="7a18c-157">지정된 프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-157">Run the specified project:</span></span>

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- <span data-ttu-id="7a18c-158">현재 디렉터리에 있는 프로젝트를 실행합니다. 비어 있는 `--` 옵션을 사용하므로 이 예제의 `--help` 인수는 애플리케이션에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-158">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- <span data-ttu-id="7a18c-159">최소 출력만 표시하는 현재 디렉터리의 프로젝트에 대한 종속성 및 도구를 복원한 다음, 프로젝트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="7a18c-159">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project:</span></span>

  ```dotnetcli
  dotnet run --verbosity m
  ```
