---
title: dotnet-gcdump 진단 도구 - .NET CLI
description: .NET EventPipe를 사용하여 라이브 .NET 프로세스의 GC(가비지 수집기) 덤프를 수집하기 위해 dotnet-gcdump CLI 도구를 설치하고 사용하는 방법을 알아봅니다.
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826042"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="2cf82-103">힙 분석 도구(dotnet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="2cf82-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="2cf82-104">**이 문서의 적용 대상:** ✔️ .NET Core 3.1 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="2cf82-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="2cf82-105">설치</span><span class="sxs-lookup"><span data-stu-id="2cf82-105">Install</span></span>

<span data-ttu-id="2cf82-106">다음 두 가지 방법으로 `dotnet-gcdump`를 다운로드하고 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="2cf82-107">**dotnet 전역 도구:**</span><span class="sxs-lookup"><span data-stu-id="2cf82-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="2cf82-108">`dotnet-gcdump` [NuGet 패키지](https://www.nuget.org/packages/dotnet-gcdump)의 최신 릴리스 버전을 설치하려면 [dotnet tool install](../tools/dotnet-tool-install.md) 명령을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="2cf82-109">**직접 다운로드:**</span><span class="sxs-lookup"><span data-stu-id="2cf82-109">**Direct download:**</span></span>

  <span data-ttu-id="2cf82-110">플랫폼에 맞는 도구 실행 파일을 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="2cf82-111">OS</span><span class="sxs-lookup"><span data-stu-id="2cf82-111">OS</span></span>  | <span data-ttu-id="2cf82-112">플랫폼</span><span class="sxs-lookup"><span data-stu-id="2cf82-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="2cf82-113">Windows</span><span class="sxs-lookup"><span data-stu-id="2cf82-113">Windows</span></span> | <span data-ttu-id="2cf82-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="2cf82-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="2cf82-115">macOS</span><span class="sxs-lookup"><span data-stu-id="2cf82-115">macOS</span></span>   | [<span data-ttu-id="2cf82-116">x64</span><span class="sxs-lookup"><span data-stu-id="2cf82-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="2cf82-117">Linux</span><span class="sxs-lookup"><span data-stu-id="2cf82-117">Linux</span></span>   | <span data-ttu-id="2cf82-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="2cf82-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="2cf82-119">개요</span><span class="sxs-lookup"><span data-stu-id="2cf82-119">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="2cf82-120">설명</span><span class="sxs-lookup"><span data-stu-id="2cf82-120">Description</span></span>

<span data-ttu-id="2cf82-121">`dotnet-gcdump` 전역 도구는 [EventPipe](./eventpipe.md)를 사용하여 라이브 .NET 프로세스의 GC(가비지 수집기) 덤프를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-121">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="2cf82-122">GC 덤프는 대상 프로세스에서 GC를 트리거하고 특수 이벤트를 켠 후 이벤트 스트림에서 개체 루트의 그래프를 다시 생성하여 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-122">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="2cf82-123">이 프로세스를 통해 프로세스가 실행되는 동안 최소한의 오버헤드로 GC 덤프를 수집할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-123">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="2cf82-124">해당 덤프는 다음을 비롯한 여러 시나리오에서 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-124">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="2cf82-125">여러 시점에 힙의 개체 수 비교</span><span class="sxs-lookup"><span data-stu-id="2cf82-125">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="2cf82-126">개체 루트 분석(“이 형식에 대한 참조를 여전히 포함하는 것은 무엇인가요?” 등의 질문에 답변)</span><span class="sxs-lookup"><span data-stu-id="2cf82-126">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="2cf82-127">힙의 개체 수에 대한 일반 통계 수집</span><span class="sxs-lookup"><span data-stu-id="2cf82-127">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="2cf82-128">dotnet-gcdump에서 캡처된 GC 덤프 보기</span><span class="sxs-lookup"><span data-stu-id="2cf82-128">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="2cf82-129">Windows의 `.gcdump` 파일은 분석을 위해 [PerfView](https://github.com/microsoft/perfview)에서 보거나 Visual Studio에서 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-129">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="2cf82-130">Windows 이외의 플랫폼에서는 현재 `.gcdump`를 열 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-130">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="2cf82-131">`.gcdump`를 여러 개 수집하고 Visual Studio에서 동시에 열어 비교할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-131">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="2cf82-132">옵션</span><span class="sxs-lookup"><span data-stu-id="2cf82-132">Options</span></span>

- **`--version`**

  <span data-ttu-id="2cf82-133">`dotnet-gcdump` 유틸리티의 버전을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-133">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2cf82-134">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-134">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="2cf82-135">현재 실행 중인 프로세스에서 GC 덤프를 수집합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-135">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2cf82-136">개요</span><span class="sxs-lookup"><span data-stu-id="2cf82-136">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="2cf82-137">옵션</span><span class="sxs-lookup"><span data-stu-id="2cf82-137">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2cf82-138">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-138">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="2cf82-139">GC 덤프를 수집할 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-139">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="2cf82-140">수집된 GC 덤프를 작성해야 하는 경로입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-140">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="2cf82-141">기본값은 *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump* 입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-141">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="2cf82-142">GC 덤프를 수집하는 동안 로그를 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-142">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="2cf82-143">이 시간(초)보다 오래 걸릴 경우 GC 덤프 수집을 포기합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-143">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="2cf82-144">기본값은 30입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-144">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="2cf82-145">GC 덤프를 수집할 프로세스의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-145">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="2cf82-146">GC 덤프를 수집할 수 있는 dotnet 프로세스를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-146">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2cf82-147">개요</span><span class="sxs-lookup"><span data-stu-id="2cf82-147">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="2cf82-148">이전에 생성된 GC 덤프 또는 실행 중인 프로세스에서 보고서를 생성하고 `stdout`에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-148">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2cf82-149">개요</span><span class="sxs-lookup"><span data-stu-id="2cf82-149">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="2cf82-150">옵션</span><span class="sxs-lookup"><span data-stu-id="2cf82-150">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2cf82-151">명령줄 도움말을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-151">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="2cf82-152">GC 덤프를 수집할 프로세스 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-152">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="2cf82-153">생성할 보고서의 유형입니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-153">The type of report to generate.</span></span> <span data-ttu-id="2cf82-154">사용 가능한 옵션: heapstat(기본값)</span><span class="sxs-lookup"><span data-stu-id="2cf82-154">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="2cf82-155">문제 해결</span><span class="sxs-lookup"><span data-stu-id="2cf82-155">Troubleshoot</span></span>

- <span data-ttu-id="2cf82-156">gcdump에 형식 정보가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-156">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="2cf82-157">.NET Core 3.1 이전에는 EventPipe를 사용하여 호출된 gcdumps 사이에 형식 캐시가 지워지지 않는 문제가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-157">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="2cf82-158">이 때문에 두 번째 및 후속 gcdumps에서는 형식 정보를 확인하는 데 필요한 이벤트가 전송되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-158">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="2cf82-159">이 문제는 .NET Core 3.1-preview2에서 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-159">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="2cf82-160">GC 덤프에 COM 및 정적 형식이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-160">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="2cf82-161">.NET Core 3.1-preview2 이전에는 EventPipe를 통해 GC 덤프를 호출할 경우 정적 및 COM 형식이 전송되지 않는 문제가 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-161">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="2cf82-162">이 문제는 .NET Core 3.1-preview2에서 해결되었습니다.</span><span class="sxs-lookup"><span data-stu-id="2cf82-162">This has been fixed in .NET Core 3.1-preview2.</span></span>
