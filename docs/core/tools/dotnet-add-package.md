---
title: dotnet add package 명령
description: ‘dotnet add package’ 명령은 NuGet 패키지 참조를 프로젝트에 추가하는 편리한 옵션을 제공합니다.
ms.date: 11/11/2020
ms.openlocfilehash: 10373b3b69c669323674b192d54cd277a5828f24
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94556877"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="bf129-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="bf129-103">dotnet add package</span></span>

<span data-ttu-id="bf129-104">**이 문서의 적용 대상:** ✔️ .NET Core 2.x SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="bf129-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bf129-105">이름</span><span class="sxs-lookup"><span data-stu-id="bf129-105">Name</span></span>

<span data-ttu-id="bf129-106">`dotnet add package` - 패키지 참조를 프로젝트 파일에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf129-107">개요</span><span class="sxs-lookup"><span data-stu-id="bf129-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [--prerelease] [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="bf129-108">설명</span><span class="sxs-lookup"><span data-stu-id="bf129-108">Description</span></span>

<span data-ttu-id="bf129-109">`dotnet add package` 명령은 패키지 참조를 프로젝트 파일에 추가하는 편리한 옵션을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="bf129-110">명령을 실행한 후 패키지가 프로젝트의 프레임워크와 호환되는지 확인하는 호환성 검사가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="bf129-111">검사를 통과하면 `<PackageReference>` 요소가 프로젝트 파일에 추가되고 [dotnet restore](dotnet-restore.md)가 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="bf129-112">예를 들어 `Newtonsoft.Json`를 *ToDo.csproj* 에 추가하면 다음 예제와 유사한 출력이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="bf129-113">이제 *ToDo.csproj* 파일에 참조되는 패키지에 대한 [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="bf129-114">암시적 복원</span><span class="sxs-lookup"><span data-stu-id="bf129-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="bf129-115">인수</span><span class="sxs-lookup"><span data-stu-id="bf129-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="bf129-116">프로젝트 파일을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-116">Specifies the project file.</span></span> <span data-ttu-id="bf129-117">지정하지 않으면 이 명령은 현재 디렉터리에서 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="bf129-118">추가할 패키지 참조입니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="bf129-119">옵션</span><span class="sxs-lookup"><span data-stu-id="bf129-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bf129-120">특정 [프레임워크](../../standard/frameworks.md)를 대상으로 하는 경우에만 패키지 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="bf129-121">명령에 대한 간단한 도움말을 출력합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="bf129-122">명령이 중지되고 사용자 입력 또는 작업을 대기할 수 있도록 허용합니다(예: 인증 완료).</span><span class="sxs-lookup"><span data-stu-id="bf129-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="bf129-123">.NET Core 2.1 SDK 버전 2.1.400 이상에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="bf129-124">복원 미리 보기 및 호환성 검사를 수행하지 않고 패키지 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="bf129-125">패키지를 복원할 디렉터리입니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-125">The directory where to restore the packages.</span></span> <span data-ttu-id="bf129-126">기본 패키지 복원 위치는 Windows에서는 `%userprofile%\.nuget\packages`이고, macOS 및 Linux에서는 `~/.nuget/packages`입니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="bf129-127">자세한 내용은 [NuGet에서 글로벌 패키지, 캐시 및 임시 폴더 관리](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf129-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`--prerelease`**

  <span data-ttu-id="bf129-128">시험판 패키지를 설치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-128">Allows prerelease packages to be installed.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="bf129-129">복원 작업 중에 사용할 NuGet 패키지 소스의 URI입니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-129">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="bf129-130">패키지의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-130">Version of the package.</span></span> <span data-ttu-id="bf129-131">[NuGet 패키지 버전 관리](/nuget/reference/package-versioning)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bf129-131">See [NuGet package versioning](/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="bf129-132">예</span><span class="sxs-lookup"><span data-stu-id="bf129-132">Examples</span></span>

- <span data-ttu-id="bf129-133">`Newtonsoft.Json` NuGet 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-133">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="bf129-134">특정 버전의 패키지를 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-134">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="bf129-135">특정 NuGet 소스를 사용하여 패키지를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="bf129-135">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="bf129-136">참조</span><span class="sxs-lookup"><span data-stu-id="bf129-136">See also</span></span>

- [<span data-ttu-id="bf129-137">NuGet에서 글로벌 패키지, 캐시 및 임시 폴더 관리</span><span class="sxs-lookup"><span data-stu-id="bf129-137">Managing the global packages, cache, and temp folders in NuGet</span></span>](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="bf129-138">NuGet 패키지 버전 관리</span><span class="sxs-lookup"><span data-stu-id="bf129-138">NuGet package versioning</span></span>](/nuget/reference/package-versioning)
