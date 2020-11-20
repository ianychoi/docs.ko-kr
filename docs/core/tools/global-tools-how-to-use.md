---
title: '자습서: .NET 전역 도구 설치 및 사용'
description: .NET 도구를 전역 도구로 설치하고 사용하는 방법을 알아봅니다.
ms.topic: tutorial
ms.date: 02/12/2020
ms.openlocfilehash: 01b773516da92fb16fb0f67fc6617e0c70d17c9d
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633897"
---
# <a name="tutorial-install-and-use-a-net-global-tool-using-the-net-cli"></a><span data-ttu-id="e9ff0-103">자습서: .NET CLI를 사용하여 .NET 전역 도구 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="e9ff0-103">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>

<span data-ttu-id="e9ff0-104">**이 문서의 적용 대상:**  ✔️ .NET Core 2.1 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="e9ff0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="e9ff0-105">이 자습서에서는 전역 도구를 설치하고 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="e9ff0-106">[이 시리즈의 첫 번째 자습서](global-tools-how-to-create.md)에서 만든 도구를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9ff0-107">사전 요구 사항</span><span class="sxs-lookup"><span data-stu-id="e9ff0-107">Prerequisites</span></span>

* <span data-ttu-id="e9ff0-108">[이 시리즈의 첫 번째 자습서](global-tools-how-to-create.md)를 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="e9ff0-109">도구를 전역 도구로 사용</span><span class="sxs-lookup"><span data-stu-id="e9ff0-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="e9ff0-110">*microsoft.botsay* 프로젝트 폴더에서 [dotnet tool install](dotnet-tool-install.md) 명령을 실행하여 패키지에서 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e9ff0-111">`--global` 매개 변수는 PATH 환경 변수에 자동으로 추가되는 기본 위치에 도구 이진 파일을 설치하도록 .NET CLI에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-111">The `--global` parameter tells the .NET CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="e9ff0-112">`--add-source` 매개 변수는 NuGet 패키지의 추가 소스 피드로 *./nupkg* 디렉터리를 임시로 사용하도록 .NET CLI에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-112">The `--add-source` parameter tells the .NET CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="e9ff0-113">패키지에 고유한 이름을 지정하여 Nuget.org 사이트가 아니라 */nupkg* 디렉터리에서만 찾을 수 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="e9ff0-114">출력에서는 설치된 도구 및 버전을 호출하는 데 사용되는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="e9ff0-115">도구를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="e9ff0-116">이 명령이 실패하는 경우 PATH를 새로 고치기 위해 새 터미널을 열어야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="e9ff0-117">[dotnet tool uninstall](dotnet-tool-uninstall.md) 명령을 실행하여 도구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="e9ff0-118">사용자 지정 위치에 설치된 전역 도구로 도구 사용</span><span class="sxs-lookup"><span data-stu-id="e9ff0-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="e9ff0-119">패키지에서 도구를 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-119">Install the tool from the package.</span></span>

   <span data-ttu-id="e9ff0-120">Windows에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e9ff0-121">Linux 또는 macOS에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="e9ff0-122">`--tool-path` 매개 변수는 지정된 위치에 도구 이진 파일을 설치하도록 .NET CLI에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-122">The `--tool-path` parameter tells the .NET CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="e9ff0-123">디렉터리가 없는 경우 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="e9ff0-124">이 디렉터리는 PATH 환경 변수에 자동으로 추가되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="e9ff0-125">출력에서는 설치된 도구 및 버전을 호출하는 데 사용되는 명령을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="e9ff0-126">도구를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-126">Invoke the tool:</span></span>

   <span data-ttu-id="e9ff0-127">Windows에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="e9ff0-128">Linux 또는 macOS에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="e9ff0-129">[dotnet tool uninstall](dotnet-tool-uninstall.md) 명령을 실행하여 도구를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="e9ff0-130">Windows에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="e9ff0-131">Linux 또는 macOS에서:</span><span class="sxs-lookup"><span data-stu-id="e9ff0-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="e9ff0-132">문제 해결</span><span class="sxs-lookup"><span data-stu-id="e9ff0-132">Troubleshoot</span></span>

<span data-ttu-id="e9ff0-133">자습서를 수행하는 동안 오류 메시지가 표시되는 경우 [.NET 도구 사용 문제 해결](troubleshoot-usage-issues.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-133">If you get an error message while following the tutorial, see [Troubleshoot .NET tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e9ff0-134">다음 단계</span><span class="sxs-lookup"><span data-stu-id="e9ff0-134">Next steps</span></span>

<span data-ttu-id="e9ff0-135">이 자습서에서는 도구를 전역 도구로 설치하고 사용했습니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="e9ff0-136">로컬 도구와 동일한 도구를 설치하고 사용하려면 다음 자습서로 이동합니다.</span><span class="sxs-lookup"><span data-stu-id="e9ff0-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e9ff0-137">로컬 도구 설치 및 사용</span><span class="sxs-lookup"><span data-stu-id="e9ff0-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
