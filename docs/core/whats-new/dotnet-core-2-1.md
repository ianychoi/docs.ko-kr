---
title: .NET Core 2.1의 새로운 기능
description: .NET Core 2.1에서 볼 수 있는 새로운 기능에 대해 알아봅니다.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 5c15b663cf69de334771e83c1a14db8d66d30458
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437918"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="aa447-103">.NET Core 2.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="aa447-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="aa447-104">.NET Core 2.1은 다음 영역에서 향상된 기능 및 새로운 기능을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="aa447-105">도구</span><span class="sxs-lookup"><span data-stu-id="aa447-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="aa447-106">롤포워드</span><span class="sxs-lookup"><span data-stu-id="aa447-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="aa447-107">배포</span><span class="sxs-lookup"><span data-stu-id="aa447-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="aa447-108">Windows 호환 기능 팩</span><span class="sxs-lookup"><span data-stu-id="aa447-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="aa447-109">JIT 컴파일 개선</span><span class="sxs-lookup"><span data-stu-id="aa447-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="aa447-110">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="aa447-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="aa447-111">도구</span><span class="sxs-lookup"><span data-stu-id="aa447-111">Tooling</span></span>

<span data-ttu-id="aa447-112">.NET Core 2.1에 포함된 도구인 .NET Core 2.1 SDK(v 2.1.300)에는 다음과 같은 변경 내용과 향상된 기능이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="aa447-113">빌드 성능 개선</span><span class="sxs-lookup"><span data-stu-id="aa447-113">Build performance improvements</span></span>

<span data-ttu-id="aa447-114">.NET Core 2.1은 특히 증분 빌드의 빌드 시간 성능을 개선하는 데 주로 초점을 맞춥니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="aa447-115">이러한 성능 개선은 `dotnet build`를 사용하는 명령줄 빌드와 Visual Studio의 빌드에 모두 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="aa447-116">개선된 일부 개별 영역은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="aa447-117">패키지 자산 해결의 경우 모든 자산이 아닌 빌드에 사용되는 자산만 해결.</span><span class="sxs-lookup"><span data-stu-id="aa447-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="aa447-118">어셈블리 참조의 캐싱.</span><span class="sxs-lookup"><span data-stu-id="aa447-118">Caching of assembly references.</span></span>

- <span data-ttu-id="aa447-119">여러 개별 `dotnet build` 호출에서 사용되는 프로세스인 장기 실행 SDK 빌드 서버의 사용.</span><span class="sxs-lookup"><span data-stu-id="aa447-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="aa447-120">`dotnet build`가 실행될 때마다 코드의 큰 블록을 JIT 컴파일할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="aa447-121">다음 명령을 사용하여 빌드 서버 프로세스를 자동으로 종료할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="aa447-122">새 CLI 명령</span><span class="sxs-lookup"><span data-stu-id="aa447-122">New CLI commands</span></span>

<span data-ttu-id="aa447-123">`DotnetCliToolReference`를 사용하여 프로젝트별로 사용할 수 있었던 많은 도구를 이제 .NET Core SDK의 일부로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="aa447-124">사용 가능한 도구는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-124">These tools include:</span></span>

- <span data-ttu-id="aa447-125">`dotnet watch`는 지정된 명령 집합을 실행하기 전에 파일이 변경될 때까지 대기하는 파일 시스템 감시자를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="aa447-126">예를 들어 다음 명령은 자동으로 현재 프로젝트를 다시 빌드하고 파일이 변경될 때마다 자세한 정보 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="aa447-127">`--verbose` 옵션 앞에 있는 `--` 옵션에 주목하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="aa447-128">이 옵션은 `dotnet watch` 명령으로 직접 전달되는 옵션을 자식 `dotnet` 프로세스에 전달되는 인수와 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="aa447-129">이 옵션을 사용하지 않으면 `--verbose` 옵션이 `dotnet build` 명령 대신 `dotnet watch` 명령에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="aa447-130">자세한 내용은 [dotnet watch를 사용한 ASP.NET Core 앱 개발](/aspnet/core/tutorials/dotnet-watch)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="aa447-131">`dotnet dev-certs`는 ASP.NET Core 애플리케이션에서 개발하는 동안 사용되는 인증서를 생성하고 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="aa447-132">`dotnet user-secrets`는 ASP.NET Core 애플리케이션의 사용자 비밀 저장소에서 비밀을 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="aa447-133">`dotnet sql-cache`는 분산 캐싱에 사용할 Microsoft SQL Server 데이터베이스에 테이블 및 인덱스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="aa447-134">`dotnet ef`는 Entity Framework Core 애플리케이션에서 데이터베이스, <xref:Microsoft.EntityFrameworkCore.DbContext> 개체 및 마이그레이션을 관리하기 위한 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="aa447-135">자세한 내용은 [EF Core .NET 명령줄 도구](/ef/core/miscellaneous/cli/dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="aa447-136">전역 도구</span><span class="sxs-lookup"><span data-stu-id="aa447-136">Global Tools</span></span>

<span data-ttu-id="aa447-137">.NET Core 2.1은 명령줄에서 전역으로 사용할 수 있는 사용자 지정 도구인 ‘전역 도구’를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="aa447-138">이전 버전 .NET Core의 확장성 모델은 `DotnetCliToolReference`를 사용하여 프로젝트별로만 사용 가능한 사용자 지정 도구를 만들었습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="aa447-139">전역 도구를 설치하려면 [dotnet tool install](../tools/dotnet-tool-install.md) 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="aa447-140">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="aa447-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="aa447-141">설치된 도구는 도구 이름을 지정하여 명령줄에서 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="aa447-142">자세한 내용은 [.NET Core 전역 도구 개요](../tools/global-tools.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="aa447-143">`dotnet tool` 명령을 사용한 도구 관리</span><span class="sxs-lookup"><span data-stu-id="aa447-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="aa447-144">.NET Core 2.1 SDK에서 모든 도구 작업은 `dotnet tool` 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="aa447-145">다음 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-145">The following options are available:</span></span>

- <span data-ttu-id="aa447-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) - 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="aa447-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) - 도구를 제거하고 다시 설치하여 효과적으로 업데이트합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="aa447-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) - 현재 설치된 도구를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="aa447-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) - 현재 설치된 도구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="aa447-150">롤포워드</span><span class="sxs-lookup"><span data-stu-id="aa447-150">Roll forward</span></span>

<span data-ttu-id="aa447-151">.NET Core 2.0부터 모든 .NET Core 애플리케이션은 시스템에 설치된 최신 *부 버전* 으로 자동으로 롤포워드됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="aa447-152">.NET Core 2.0부터 애플리케이션 빌드에 사용된 .NET Core 버전이 런타임에 없는 경우에는 애플리케이션이 .NET Core의 설치된 최신 ‘부 버전’에 대해 자동으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at run time, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="aa447-153">즉, 애플리케이션이 .NET Core 2.0을 사용하여 빌드되고 .NET Core 2.0이 호스트 시스템에 없지만 .NET Core 2.1이 있는 경우 애플리케이션은 .NET Core 2.1을 사용하여 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa447-154">이 롤포워드 동작은 미리 보기 릴리스에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="aa447-155">기본적으로 주요 릴리스에도 적용되지 않지만 아래 설정으로 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="aa447-156">후보 공유 프레임워크에서 롤포워드 설정을 변경하여 이 동작을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="aa447-157">사용 가능한 설정은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-157">The available settings are:</span></span>

- <span data-ttu-id="aa447-158">`0` - 부 버전 롤포워드 동작을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="aa447-159">이 설정을 사용하면 .NET Core 2.0.0용으로 빌드된 애플리케이션이 .NET Core 2.0.1 롤포워드되지만 .NET Core 2.2.0 또는 .NET Core 3.0.0에서는 롤포워드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="aa447-160">`1` - 부 버전 롤포워드 동작을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="aa447-161">이는 설정의 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-161">This is the default value for the setting.</span></span> <span data-ttu-id="aa447-162">이 설정을 사용하면 .NET Core 2.0.0용으로 빌드된 애플리케이션은 설치된 .NET Core 2.0.1 또는 .NET Core 2.2.0에 따라 하나를 롤포워드하지만 .NET Core 3.0.0으로 롤포워드되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="aa447-163">`2` - 부 버전 및 주 버전 롤포워드 동작을 활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="aa447-164">설정한 경우 다른 주 버전도 고려되므로 .NET Core 2.0.0용으로 빌드된 애플리케이션은 NET Core 3.0.0으로 롤포워드됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="aa447-165">다음 세 가지 방법 중 하나로 이 설정을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="aa447-166">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` 환경 변수를 원하는 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="aa447-167">원하는 값이 포함된 다음 줄을 *.runtimeconfig.json* 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="aa447-168">[.NET Core CLI](../tools/index.md)를 사용하는 경우 `run`과 같은 .NET Core 명령에 원하는 값을 포함하여 다음 옵션을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="aa447-169">패치 버전 롤포워드는 이 설정과는 무관하며 잠재적인 부 버전 롤포워드가 적용된 후에 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="aa447-170">배포</span><span class="sxs-lookup"><span data-stu-id="aa447-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="aa447-171">자체 포함 애플리케이션 제공</span><span class="sxs-lookup"><span data-stu-id="aa447-171">Self-contained application servicing</span></span>

<span data-ttu-id="aa447-172">`dotnet publish`는 이제 서비스 런타임 버전이 포함된 자체 포함 애플리케이션을 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="aa447-173">.NET Core 2.1 SDK(v 2.1.300)를 사용하여 자체 포함 애플리케이션을 게시하면 애플리케이션에는 해당 SDK가 인식하는 최신 서비스 런타임 버전이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="aa447-174">최신 SDK로 업그레이드하면 최신 .NET Core 런타임 버전으로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="aa447-175">이는 .NET Core 1.0 런타임 이상에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="aa447-176">자체 포함 게시에는 NuGet.org의 런타임 버전을 사용합니다. 컴퓨터에 서비스 런타임이 있어야 할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="aa447-177">.NET Core 2.0 SDK를 사용하면 `RuntimeFrameworkVersion` 속성을 통해 다른 버전이 지정되지 않는 한 자체 포함 애플리케이션은 .NET Core 2.0.0 런타임으로 게시됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="aa447-178">이 새 동작을 사용하면 더 이상 자체 포함 애플리케이션의 상위 런타임 버전을 선택하기 위해 이 속성을 설정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="aa447-179">앞으로 가장 쉬운 방법은 항상 .NET Core 2.1 SDK(v 2.1.300)로 게시하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="aa447-180">자세한 내용은 [자체 포함 배포 런타임 롤포워드](../deploying/runtime-patch-selection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="aa447-181">Windows 호환 기능 팩</span><span class="sxs-lookup"><span data-stu-id="aa447-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="aa447-182">.NET Framework에서 .NET Core로 기존 코드를 포팅할 경우 [Windows 호환 기능 팩](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="aa447-183">.NET Core에서 사용할 수 있는 것보다 20,000개 많은 API에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="aa447-184">이러한 API에는 <xref:System.Drawing?displayProperty=nameWithType> 네임스페이스, <xref:System.Diagnostics.EventLog> 클래스, WMI, 성능 카운터, Windows 서비스 및 Windows 레지스트리 형식/멤버의 형식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="aa447-185">JIT 컴파일러 개선</span><span class="sxs-lookup"><span data-stu-id="aa447-185">JIT compiler improvements</span></span>

<span data-ttu-id="aa447-186">.NET Core는 성능을 상당히 개선할 수 있는 ‘계층화된 컴파일’(‘적응형 최적화’라고도 함)이라는 새로운 JIT 컴파일러 기술을 통합합니다. </span><span class="sxs-lookup"><span data-stu-id="aa447-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="aa447-187">계층화된 컴파일은 옵트인 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="aa447-188">JIT 컴파일러가 수행하는 중요한 작업 중 하나는 코드 실행을 최적화하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="aa447-189">그러나 자주 사용되지 않는 코드 경로의 경우 컴파일러가 코드 최적화에 사용하는 시간이 런타임이 최적화되지 않은 코드 실행에 사용하는 시간보다 길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="aa447-190">계층화된 컴파일은 JIT 컴파일에 다음과 같은 두 단계를 도입합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="aa447-191">가능한 한 빨리 코드를 생성하는 **첫 번째 계층**.</span><span class="sxs-lookup"><span data-stu-id="aa447-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="aa447-192">자주 실행되는 메서드에 대한 최적화된 코드를 생성하는 **두 번째 계층**.</span><span class="sxs-lookup"><span data-stu-id="aa447-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="aa447-193">컴파일의 두 번째 계층은 성능 향상을 위해 병렬로 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="aa447-194">두 가지 방법 중 하나로 계층화된 컴파일을 옵트인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="aa447-195">.NET Core 2.1 SDK를 사용하는 모든 프로젝트에서 계층화된 컴파일을 사용하려면 다음 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="aa447-196">프로젝트별로 계층화된 컴파일을 사용하려면 다음 예제처럼 MSBuild 프로젝트 파일의 `<PropertyGroup>` 섹션에 `<TieredCompilation>` 속성을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="aa447-197">API 변경 내용</span><span class="sxs-lookup"><span data-stu-id="aa447-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="aa447-198">`Span<T>` 및 `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="aa447-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="aa447-199">.NET Core 2.1에는 배열 및 다른 유형의 메모리 관련 작업을 훨씬 더 효율적으로 만드는 몇 가지 새로운 형식이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="aa447-200">새 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-200">The new types include:</span></span>

- <span data-ttu-id="aa447-201"><xref:System.Span%601?displayProperty=nameWithType>와 <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="aa447-202"><xref:System.Memory%601?displayProperty=nameWithType>와 <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="aa447-203">이러한 형식이 없다면 배열의 일부 또는 메모리 버퍼의 섹션과 같은 항목을 전달할 경우 데이터의 일부를 복사한 다음, 메서드에 전달해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="aa447-204">이러한 형식은 추가 메모리 할당 및 복사 작업이 없어도 해당 데이터의 가상 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="aa447-205">다음 예제에서는 <xref:System.Span%601> 및 <xref:System.Memory%601> 인스턴스를 사용하여 배열의 10개 요소에 대한 가상 보기를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](./snippets/dotnet-core-2-1/csharp/program.cs)]

[!code-vb[Memory\<T>](./snippets/dotnet-core-2-1/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="aa447-206">Brotli 압축</span><span class="sxs-lookup"><span data-stu-id="aa447-206">Brotli compression</span></span>

<span data-ttu-id="aa447-207">.NET Core 2.1은 Brotli 압축 및 압축 풀기에 대한 지원을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="aa447-208">Brotli는 [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt)에 정의되어 있고 대부분의 웹 브라우저와 주요 웹 서버에서 지원되는 범용 무손실 압축 알고리즘입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="aa447-209">스트림 기반 <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> 클래스 또는 고성능 범위 기반 <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> 및 <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> 클래스를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="aa447-210">다음 예제는 <xref:System.IO.Compression.BrotliStream> 클래스를 사용한 압축을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](./snippets/dotnet-core-2-1/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](./snippets/dotnet-core-2-1/vb/brotli.vb#1)]

<span data-ttu-id="aa447-211"><xref:System.IO.Compression.BrotliStream> 동작은 <xref:System.IO.Compression.DeflateStream> 및 <xref:System.IO.Compression.GZipStream>과 동일하므로, 이러한 API를 호출하는 코드를 <xref:System.IO.Compression.BrotliStream>으로 쉽게 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="aa447-212">새 암호화 API 및 암호화 개선</span><span class="sxs-lookup"><span data-stu-id="aa447-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="aa447-213">.NET Core 2.1에는 암호화 API에 대한 다양한 개선 사항이 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="aa447-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>는 System.Security.Cryptography.Pkcs 패키지에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="aa447-215">구현은 .NET Framework의 <xref:System.Security.Cryptography.Pkcs.SignedCms> 클래스와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="aa447-216"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> 및 <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> 메서드의 새 오버로드는 해시 알고리즘 식별자를 허용하므로 호출자가 SHA-1 이외의 알고리즘을 사용하여 인증서 지문 값을 가져올 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="aa447-217">새 <xref:System.Span%601> 기반 암호화 API는 해시, HMAC, 암호화 난수 생성, 비대칭 시그니처 생성, 비대칭 시그니처 처리 및 RSA 암호화에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="aa447-218"><xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> 성능은 <xref:System.Span%601> 기반 구현을 사용함으로써 15% 정도 향상되었습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="aa447-219">새 <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> 클래스에는 다음 두 가지 새 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="aa447-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>는 동일한 길이의 두 입력에 대해 반환하는 데 고정된 시간을 사용하므로, 타이밍 부채널 정보에 영향을 주지 않기 위해 암호화 확인에 사용하기에 적합합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="aa447-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>는 최적화할 수 없는 메모리 정리 루틴입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="aa447-222"><xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> 정적 메서드는 <xref:System.Span%601>를 임의 값으로 채웁니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="aa447-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType>는 이제 Linux 및 macOS에서 지원됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="aa447-224">ECDH(타원 곡선 Diffie-Hellman)는 이제 <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> 클래스 제품군에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="aa447-225">노출 영역은 .NET Framework의 것과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="aa447-226"><xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType>에서 반환된 인스턴스는 SHA-2 다이제스트를 사용하여 OAEP에서 암호화 또는 암호 해독되고 RSA-PSS를 사용하여 시그니처를 생성하거나 유효성 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="aa447-227">소켓 개선</span><span class="sxs-lookup"><span data-stu-id="aa447-227">Sockets improvements</span></span>

<span data-ttu-id="aa447-228">.NET Core에는 더 높은 수준의 네트워킹 API 기반을 형성하는 새 형식 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 및 다시 작성된 <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="aa447-229">예를 들어 <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>는 <xref:System.Net.Http.HttpClient> 구현의 기반입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="aa447-230">이전 버전의 .NET Core에서 더 높은 수준의 API는 기본 네트워킹 구현을 기반으로 했습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="aa447-231">.NET Core 2.1에 도입된 소켓 구현에는 다음과 같은 여러 가지 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="aa447-232">이전 구현보다 월등히 향상된 성능.</span><span class="sxs-lookup"><span data-stu-id="aa447-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="aa447-233">배포 및 서비스를 단순화하는 플랫폼 종속성 제거.</span><span class="sxs-lookup"><span data-stu-id="aa447-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="aa447-234">모든 .NET Core 플랫폼에서 일관된 동작.</span><span class="sxs-lookup"><span data-stu-id="aa447-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="aa447-235"><xref:System.Net.Http.SocketsHttpHandler>는 .NET Core 2.1의 기본 구현입니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="aa447-236">그러나 <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> 메서드를 호출하여 이전 <xref:System.Net.Http.HttpClientHandler> 클래스를 사용하도록 애플리케이션을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="aa447-237">환경 변수를 사용하여 <xref:System.Net.Http.SocketsHttpHandler>를 기반으로 한 소켓 구현 사용을 옵트아웃할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="aa447-238">이를 수행하려면 `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER`를 `false` 또는 0으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="aa447-239">Windows에서는 네이티브 구현을 사용하는 <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>을 사용하거나 클래스의 인스턴스를 <xref:System.Net.Http.HttpClient> 생성자에 전달하여 <xref:System.Net.Http.SocketsHttpHandler> 클래스를 사용하도록 선택할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="aa447-240">Linux 및 macOS에서는 프로세스별로 <xref:System.Net.Http.HttpClient>만 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="aa447-241">Linux에서 이전 <xref:System.Net.Http.HttpClient> 구현을 사용하려면 [libcurl](https://curl.haxx.se/libcurl/)을 배포해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="aa447-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="aa447-242">(.NET Core 2.0과 함께 설치됩니다.)</span><span class="sxs-lookup"><span data-stu-id="aa447-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="aa447-243">호환성이 손상되는 변경</span><span class="sxs-lookup"><span data-stu-id="aa447-243">Breaking changes</span></span>

<span data-ttu-id="aa447-244">호환성이 손상되는 변경에 대한 자세한 내용은 [버전 2.0에서 2.1로 마이그레이션 시 호환성이 손상되는 변경](../compatibility/2.1.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="aa447-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa447-245">참조</span><span class="sxs-lookup"><span data-stu-id="aa447-245">See also</span></span>

- [<span data-ttu-id="aa447-246">.NET Core 3.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="aa447-246">What's new in .NET Core 3.1</span></span>](dotnet-core-3-1.md)
- [<span data-ttu-id="aa447-247">EF Core 2.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="aa447-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="aa447-248">ASP.NET Core 2.1의 새로운 기능</span><span class="sxs-lookup"><span data-stu-id="aa447-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
