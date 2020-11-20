---
title: 탭 완성 기능 사용
description: 이 문서에서는 PowerShell, Bash, zsh용 .NET CLI에 대해 탭 완성 기능을 사용하도록 설정하는 방법을 설명합니다.
author: adegeo
ms.author: adegeo
ms.topic: how-to
ms.date: 11/03/2019
ms.openlocfilehash: 31bf5e74644680fc30ca5b79972fbed6367363e1
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634014"
---
# <a name="how-to-enable-tab-completion-for-the-net-cli"></a><span data-ttu-id="549fe-103">.NET CLI에 대해 탭 완성 기능을 사용하도록 설정하는 방법</span><span class="sxs-lookup"><span data-stu-id="549fe-103">How to enable TAB completion for the .NET CLI</span></span>

<span data-ttu-id="549fe-104">**이 문서의 적용 대상:**  ✔️ .NET Core 2.1 SDK 이상 버전</span><span class="sxs-lookup"><span data-stu-id="549fe-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="549fe-105">이 문서에서는 세 개의 셸, PowerShell, Bash 및 zsh에 대한 탭 완성 기능을 구성하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-105">This article describes how to configure tab completion for three shells, PowerShell, Bash, and zsh.</span></span> <span data-ttu-id="549fe-106">그 밖의 셸은 해당 셸의 설명서에서 탭 완성 기능을 구현하는 방법을 확인하세요.</span><span class="sxs-lookup"><span data-stu-id="549fe-106">For other shells, refer to their documentation on how to configure tab completion.</span></span>

<span data-ttu-id="549fe-107">설정되면 셸에 `dotnet` 명령을 입력하고 Tab 키를 누르면 .NET CLI의 탭 완성 기능이 트리거됩니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-107">Once set up, tab completion for the .NET CLI is triggered by typing a `dotnet` command in the shell, and then pressing the TAB key.</span></span> <span data-ttu-id="549fe-108">현재 명령줄은 `dotnet complete` 명령으로 전송되고, 결과는 셸에 의해 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-108">The current command line is sent to the `dotnet complete` command, and the results are processed by your shell.</span></span> <span data-ttu-id="549fe-109">`dotnet complete` 명령으로 직접 전송하여 탭 완성 기능을 사용하지 않고 결과를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-109">You can test the results without enabling tab completion by sending something directly to the `dotnet complete` command.</span></span> <span data-ttu-id="549fe-110">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="549fe-110">For example:</span></span>

```console
> dotnet complete "dotnet a"
add
clean
--diagnostics
migrate
pack
```

<span data-ttu-id="549fe-111">해당 명령이 작동하지 않는 경우 .NET Core 2.0 SDK 이상이 설치되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-111">If that command doesn't work, make sure that .NET Core 2.0 SDK or above is installed.</span></span> <span data-ttu-id="549fe-112">설치되었지만 해당 명령이 여전히 작동하지 않는 경우 `dotnet` 명령이 .NET Core 2.0 SDK 이상 버전으로 확인되는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-112">If it's installed, but that command still doesn't work, make sure that the `dotnet` command resolves to a version of .NET Core 2.0 SDK and above.</span></span> <span data-ttu-id="549fe-113">`dotnet --version` 명령을 사용하여 현재 경로가 확인되는 `dotnet`의 버전을 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-113">Use the `dotnet --version` command to see what version of `dotnet` your current path is resolving to.</span></span> <span data-ttu-id="549fe-114">자세한 내용은 [사용할 .NET 버전 선택](../versions/selection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="549fe-114">For more information, see [Select the .NET version to use](../versions/selection.md).</span></span>

### <a name="examples"></a><span data-ttu-id="549fe-115">예</span><span class="sxs-lookup"><span data-stu-id="549fe-115">Examples</span></span>

<span data-ttu-id="549fe-116">탭 완성 기능에서 제공하는 몇 가지 예제는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-116">Here are some examples of what tab completion provides:</span></span>

<span data-ttu-id="549fe-117">입력</span><span class="sxs-lookup"><span data-stu-id="549fe-117">Input</span></span>                                | <span data-ttu-id="549fe-118">다음이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-118">becomes</span></span>                                                                     | <span data-ttu-id="549fe-119">이유</span><span class="sxs-lookup"><span data-stu-id="549fe-119">because</span></span>
:------------------------------------|:----------------------------------------------------------------------------|:--------------------------------
`dotnet a⇥`                          | `dotnet add`                                                                 | <span data-ttu-id="549fe-120">`add`는 사전순으로 첫 번째 하위 명령입니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-120">`add` is the first subcommand, alphabetically.</span></span>
`dotnet add p⇥`                      | `dotnet add --help`                                                          | <span data-ttu-id="549fe-121">탭 완성 기능은 부분 문자열과 일치하고 `--help`가 사전순으로 먼저 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-121">Tab completion matches substrings and `--help` comes first alphabetically.</span></span>
`dotnet add p⇥⇥`                    | `dotnet add package`                                                          | <span data-ttu-id="549fe-122">탭 키를 두 번째로 누르면 다음 제안이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-122">Pressing tab a second time brings up the next suggestion.</span></span>
`dotnet add package Microsoft⇥`      | `dotnet add package Microsoft.ApplicationInsights.Web`                      | <span data-ttu-id="549fe-123">결과는 사전순으로 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-123">Results are returned alphabetically.</span></span>
`dotnet remove reference ⇥`          | `dotnet remove reference ..\..\src\OmniSharp.DotNet\OmniSharp.DotNet.csproj` | <span data-ttu-id="549fe-124">탭 완성 기능은 프로젝트 파일 인식입니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-124">Tab completion is project file aware.</span></span>

## <a name="powershell"></a><span data-ttu-id="549fe-125">PowerShell</span><span class="sxs-lookup"><span data-stu-id="549fe-125">PowerShell</span></span>

<span data-ttu-id="549fe-126">.NET CLI용 **PowerShell** 에 탭 완성 기능을 추가하려면 `$PROFILE` 변수에 저장된 프로필을 만들거나 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-126">To add tab completion to **PowerShell** for the .NET CLI, create or edit the profile stored in the variable `$PROFILE`.</span></span> <span data-ttu-id="549fe-127">자세한 내용은 [프로필을 만드는 방법](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) 및 [프로필 및 실행 정책](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="549fe-127">For more information, see [How to create your profile](/powershell/module/microsoft.powershell.core/about/about_profiles#how-to-create-a-profile) and [Profiles and execution policy](/powershell/module/microsoft.powershell.core/about/about_profiles#profiles-and-execution-policy).</span></span>

<span data-ttu-id="549fe-128">프로필에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-128">Add the following code to your profile:</span></span>

```powershell
# PowerShell parameter completion shim for the dotnet CLI
Register-ArgumentCompleter -Native -CommandName dotnet -ScriptBlock {
     param($commandName, $wordToComplete, $cursorPosition)
         dotnet complete --position $cursorPosition "$wordToComplete" | ForEach-Object {
            [System.Management.Automation.CompletionResult]::new($_, $_, 'ParameterValue', $_)
         }
 }
```

## <a name="bash"></a><span data-ttu-id="549fe-129">bash</span><span class="sxs-lookup"><span data-stu-id="549fe-129">bash</span></span>

<span data-ttu-id="549fe-130">.NET CLI용 **bash** 셸에 탭 완성 기능을 추가하려면 `.bashrc` 파일에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-130">To add tab completion to your **bash** shell for the .NET CLI, add the following code to your `.bashrc` file:</span></span>

```bash
# bash parameter completion for the dotnet CLI

_dotnet_bash_complete()
{
  local word=${COMP_WORDS[COMP_CWORD]}

  local completions
  completions="$(dotnet complete --position "${COMP_POINT}" "${COMP_LINE}" 2>/dev/null)"
  if [ $? -ne 0 ]; then
    completions=""
  fi

  COMPREPLY=( $(compgen -W "$completions" -- "$word") )
}

complete -f -F _dotnet_bash_complete dotnet
```

## <a name="zsh"></a><span data-ttu-id="549fe-131">zsh</span><span class="sxs-lookup"><span data-stu-id="549fe-131">zsh</span></span>

<span data-ttu-id="549fe-132">.NET CLI용 **zsh** 셸에 탭 완성 기능을 추가하려면 `.zshrc` 파일에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="549fe-132">To add tab completion to your **zsh** shell for the .NET CLI, add the following code to your `.zshrc` file:</span></span>

```zsh
# zsh parameter completion for the dotnet CLI

_dotnet_zsh_complete()
{
  local completions=("$(dotnet complete "$words")")

  reply=( "${(ps:\n:)completions}" )
}

compctl -K _dotnet_zsh_complete dotnet
```
