---
description: Visual Studio 명령줄에 필요한 환경 변수를 설정하는 방법
title: Visual Studio 명령줄에 필요한 환경 변수를 설정하는 방법
ms.date: 12/20/2019
f1_keywords:
- cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
ms.openlocfilehash: b985c85e2fddce459ed68b3d07ba7d54a8b2d0a7
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125607"
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a><span data-ttu-id="5a565-103">Visual Studio 명령줄에 필요한 환경 변수를 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="5a565-103">How to set environment variables for the Visual Studio Command Line</span></span>

<span data-ttu-id="5a565-104">VsDevCmd.bat 파일은 명령줄 빌드를 사용하도록 적절한 환경 변수를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-104">The VsDevCmd.bat file sets the appropriate environment variables to enable command-line builds.</span></span>

> [!NOTE]
> <span data-ttu-id="5a565-105">Visual Studio 2015 및 이전 버전에서는 VsDevCmd.bat가 아닌 VSVARS32.bat가 같은 용도로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-105">Visual Studio 2015 and earlier versions used VSVARS32.bat, not VsDevCmd.bat for the same purpose.</span></span> <span data-ttu-id="5a565-106">이 파일은 \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools 또는 Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools에 저장되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-106">This file was stored in \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools or Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.</span></span>

<span data-ttu-id="5a565-107">Visual Studio의 이전 버전이 설치된 컴퓨터에 Visual Studio의 최신 버전을 설치한 경우 동일한 명령 프롬프트 창에서 다른 버전의 VsDevCmd.bat 또는 VSVARS32.BAT를 실행해서는 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-107">If the current version of Visual Studio is installed on a computer that also has an earlier version of Visual Studio, you should not run VsDevCmd.bat and VSVARS32.BAT from different versions in the same Command Prompt window.</span></span> <span data-ttu-id="5a565-108">대신 별도 창에서 각 버전에 대해 명령을 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-108">Instead, you should run the command for each version in its own window.</span></span>

### <a name="to-run-vsdevcmdbat"></a><span data-ttu-id="5a565-109">VsDevCmd.BAT를 실행하려면</span><span class="sxs-lookup"><span data-stu-id="5a565-109">To run VsDevCmd.BAT</span></span>

1. <span data-ttu-id="5a565-110">**시작** 메뉴에서 **VS 2019용 개발자 명령 프롬프트** 를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-110">From the **Start** menu, open the **Developer Command Prompt for VS 2019**.</span></span>  <span data-ttu-id="5a565-111">**Visual Studio 2019** 폴더에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-111">It's in the **Visual Studio 2019** folder.</span></span>

2. <span data-ttu-id="5a565-112">설치 경로를 \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools 하위 디렉터리로 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-112">Change to the \Program Files\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools or \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offering*\Common7\Tools subdirectory of your installation.</span></span>  <span data-ttu-id="5a565-113">(*Version* 은 현재 버전용인 *2019* 입니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-113">(*Version* is *2019* for the current version.</span></span> <span data-ttu-id="5a565-114">*Offering* 은 *Enterprise*, *Professional* 또는 *Community* 중 하나입니다.)</span><span class="sxs-lookup"><span data-stu-id="5a565-114">*Offering* is one of *Enterprise*, *Professional* or *Community*.)</span></span>

3. <span data-ttu-id="5a565-115">**VsDevCmd** 를 입력하여 VsDevCmd.bat을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-115">Run VsDevCmd.bat by typing **VsDevCmd**.</span></span>

    > [!CAUTION]
    > <span data-ttu-id="5a565-116">VsDevCmd.bat는 컴퓨터마다 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5a565-116">VsDevCmd.bat can vary from computer to computer.</span></span> <span data-ttu-id="5a565-117">누락되거나 손상된 VsDevCmd.bat 파일을 다른 컴퓨터의 VsDevCmd.bat 파일로 바꾸지 마세요.</span><span class="sxs-lookup"><span data-stu-id="5a565-117">Do not replace a missing or damaged VsDevCmd.bat file with a VsDevCmd.bat from another computer.</span></span> <span data-ttu-id="5a565-118">대신 설치 프로그램을 다시 실행하여 누락된 파일을 교체하십시오.</span><span class="sxs-lookup"><span data-stu-id="5a565-118">Instead, rerun setup to replace the missing file.</span></span>

### <a name="available-options-for-vsdevcmdbat"></a><span data-ttu-id="5a565-119">VsDevCmd.BAT에 사용 가능한 옵션</span><span class="sxs-lookup"><span data-stu-id="5a565-119">Available options for VsDevCmd.BAT</span></span>

<span data-ttu-id="5a565-120">VsDevCmd.BAT에 사용 가능한 옵션을 보려면 `-help` 옵션을 사용하여 명령을 실행하세요.</span><span class="sxs-lookup"><span data-stu-id="5a565-120">To see the available options for VsDevCmd.BAT, run the command with the `-help` option:</span></span>

```console
VsDevCmd.bat -help
```

## <a name="see-also"></a><span data-ttu-id="5a565-121">참조</span><span class="sxs-lookup"><span data-stu-id="5a565-121">See also</span></span>

- [<span data-ttu-id="5a565-122">csc.exe를 사용한 명령줄 빌드</span><span class="sxs-lookup"><span data-stu-id="5a565-122">Command-line Building With csc.exe</span></span>](./command-line-building-with-csc-exe.md)
