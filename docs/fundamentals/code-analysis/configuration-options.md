---
title: 코드 분석 규칙 구성
description: 분석기 구성 파일에서 코드 분석 규칙을 구성 하는 방법에 대해 알아봅니다.
ms.date: 09/24/2020
ms.topic: conceptual
no-loc:
- EditorConfig
ms.openlocfilehash: af2ebb74786f0ae884ffee4636765cae43fcb23f
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/01/2020
ms.locfileid: "96593143"
---
# <a name="configuration-options-for-code-analysis"></a><span data-ttu-id="1b8e6-103">코드 분석에 대 한 구성 옵션</span><span class="sxs-lookup"><span data-stu-id="1b8e6-103">Configuration options for code analysis</span></span>

<span data-ttu-id="1b8e6-104">코드 분석 규칙에는 다양 한 구성 옵션이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-104">Code analysis rules have various configuration options.</span></span> <span data-ttu-id="1b8e6-105">이러한 옵션은 구문을 사용 하 여 [분석기 구성 파일](configuration-files.md) 에서 키-값 쌍으로 지정 됩니다 `<option key> = <option value>` .</span><span class="sxs-lookup"><span data-stu-id="1b8e6-105">These options are specified as key-value pairs in an [analyzer configuration file](configuration-files.md) using the syntax `<option key> = <option value>`.</span></span>

<span data-ttu-id="1b8e6-106">가장 일반적으로 구성할 옵션은 규칙의 심각도입니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-106">The most common option you'll configure is a rule's severity.</span></span> <span data-ttu-id="1b8e6-107">[코드 품질 규칙](quality-rules/index.md) 및 [코드 스타일 규칙](style-rules/index.md)을 포함 하 여 모든 분석기 규칙에 대 한 심각도 수준을 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-107">You can configure severity level for all analyzer rules, including [code quality rules](quality-rules/index.md) and [code style rules](style-rules/index.md).</span></span>

<span data-ttu-id="1b8e6-108">규칙 동작을 사용자 지정 하는 추가 옵션을 구성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-108">You can also configure additional options to customize rule behavior:</span></span>

- <span data-ttu-id="1b8e6-109">코드 품질 규칙에는 규칙을 적용 해야 하는 메서드 이름과 같은 동작을 구성 하는 [추가 옵션이](code-quality-rule-options.md) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-109">Code quality rules have [additional options](code-quality-rule-options.md) to configure behavior, such as which method names a rule should apply to.</span></span>
- <span data-ttu-id="1b8e6-110">코드 스타일 규칙에는 [사용자 지정 코드 스타일 옵션이](code-style-rule-options.md)있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-110">Code style rules have [custom code style options](code-style-rule-options.md).</span></span>
- <span data-ttu-id="1b8e6-111">타사 분석기 규칙은 사용자 지정 키 이름 및 값 형식을 사용 하 여 자체 구성 옵션을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-111">Third party analyzer rules can define their own configuration options, with custom key names and value formats.</span></span>

<span data-ttu-id="1b8e6-112">[분석기 구성 파일](configuration-files.md) 에서 특정 규칙의 심각도를 구성 하는 구문은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-112">The syntax for configuring a specific rule's severity in an [analyzer configuration file](configuration-files.md) is as follows:</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity>
```

## <a name="general-options"></a><span data-ttu-id="1b8e6-113">일반 옵션</span><span class="sxs-lookup"><span data-stu-id="1b8e6-113">General options</span></span>

<span data-ttu-id="1b8e6-114">이러한 옵션은 전체 코드 분석에 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-114">These options apply to code analysis as a whole.</span></span> <span data-ttu-id="1b8e6-115">단일 규칙 또는 규칙 집합에만 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-115">They cannot be applied only to a single rule or set of rules.</span></span>

### <a name="exclude-generated-code"></a><span data-ttu-id="1b8e6-116">생성 된 코드 제외</span><span class="sxs-lookup"><span data-stu-id="1b8e6-116">Exclude generated code</span></span>

<span data-ttu-id="1b8e6-117">`generated_code = true | false` [구성 파일](configuration-files.md)에 항목을 추가 하 여 생성 된 코드로 처리할 추가 파일 및 폴더를 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-117">You can configure additional files and folders to be treated as generated code by adding a `generated_code = true | false` entry to your [configuration file](configuration-files.md).</span></span> <span data-ttu-id="1b8e6-118">.NET 코드 분석기 경고는 디자이너에서 생성 된 파일과 같은 생성 된 코드 파일에는 유용 하지 않습니다. 이러한 파일은 사용자가 편집 하 여 위반을 수정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-118">.NET code analyzer warnings aren't useful on generated code files, such as designer-generated files, which users can't edit to fix any violations.</span></span> <span data-ttu-id="1b8e6-119">대부분의 경우 코드 분석기는 생성 된 코드 파일을 건너뛰고 이러한 파일에 대 한 위반을 보고 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-119">In most cases, code analyzers skip generated code files and don't report violations on these files.</span></span>

<span data-ttu-id="1b8e6-120">기본적으로 특정 파일 확장명 또는 자동 생성 파일 헤더를 포함 하는 파일은 생성 된 코드 파일로 처리 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-120">By default, files with certain file extensions or auto-generated file headers are treated as generated code files.</span></span> <span data-ttu-id="1b8e6-121">예를 들어 또는로 끝나는 파일 이름은 `.designer.cs` `.generated.cs` 생성 된 코드로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-121">For example, a file name ending with `.designer.cs` or `.generated.cs` is considered generated code.</span></span> <span data-ttu-id="1b8e6-122">이 구성 옵션을 사용 하 여 추가 명명 패턴을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-122">This configuration option lets you specify additional naming patterns.</span></span>

<span data-ttu-id="1b8e6-123">예를 들어 이름이 생성 된 코드로 끝나는 모든 파일을 처리 하려면 `.MyGenerated.cs` 다음 항목을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-123">For example, to treat all files whose name ends with `.MyGenerated.cs` as generated code, add the following entry:</span></span>

```ini
[*.MyGenerated.cs]
generated_code = true
```

## <a name="rule-specific-options"></a><span data-ttu-id="1b8e6-124">규칙 관련 옵션</span><span class="sxs-lookup"><span data-stu-id="1b8e6-124">Rule-specific options</span></span>

<span data-ttu-id="1b8e6-125">규칙 관련 옵션은 단일 규칙, 규칙 집합 또는 모든 규칙에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-125">Rule-specific options can be applied to a single rule, a set of rules, or all rules.</span></span> <span data-ttu-id="1b8e6-126">규칙 관련 옵션은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-126">The rule-specific options include:</span></span>

- [<span data-ttu-id="1b8e6-127">규칙 심각도 수준</span><span class="sxs-lookup"><span data-stu-id="1b8e6-127">Rule severity level</span></span>](#severity-level)
- [<span data-ttu-id="1b8e6-128">*코드 품질* 규칙과 관련 한 옵션</span><span class="sxs-lookup"><span data-stu-id="1b8e6-128">Options specific to *code-quality* rules</span></span>](code-quality-rule-options.md)

### <a name="severity-level"></a><span data-ttu-id="1b8e6-129">심각도 수준</span><span class="sxs-lookup"><span data-stu-id="1b8e6-129">Severity level</span></span>

<span data-ttu-id="1b8e6-130">다음 표에서는 [코드 품질](quality-rules/index.md) 및 [코드 스타일](style-rules/index.md) 규칙을 포함 하 여 모든 분석기 규칙에 대해 구성할 수 있는 다양 한 규칙 심각도를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-130">The following table shows the different rule severities that you can configure for all analyzer rules, including [code quality](quality-rules/index.md) and [code style](style-rules/index.md) rules.</span></span>

| <span data-ttu-id="1b8e6-131">심각도</span><span class="sxs-lookup"><span data-stu-id="1b8e6-131">Severity</span></span> | <span data-ttu-id="1b8e6-132">빌드 시간 동작</span><span class="sxs-lookup"><span data-stu-id="1b8e6-132">Build-time behavior</span></span> |
|-|-|
| `error` | <span data-ttu-id="1b8e6-133">위반은 빌드 *오류로* 표시 되 고 빌드가 실패 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-133">Violations appear as build *errors* and cause builds to fail.</span></span>|
| `warning` | <span data-ttu-id="1b8e6-134">위반은 빌드 *경고* 로 나타나지만 빌드 실패를 유발 하지 않습니다 (경고를 오류로 처리 하도록 설정 하지 않은 경우).</span><span class="sxs-lookup"><span data-stu-id="1b8e6-134">Violations appear as build *warnings* but do not cause builds to fail (unless you have an option set to treat warnings as errors).</span></span> |
| `suggestion` | <span data-ttu-id="1b8e6-135">위반은 빌드 *메시지로* 표시 되 고 VISUAL Studio IDE에서 제안 사항으로 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-135">Violations appear as build *messages* and as suggestions in the Visual Studio IDE.</span></span> |
| `silent` | <span data-ttu-id="1b8e6-136">위반은 사용자에 게 표시 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-136">Violations aren't visible to the user.</span></span> |
| `none` | <span data-ttu-id="1b8e6-137">규칙은 전혀 표시되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-137">Rule is suppressed completely.</span></span> |
| `default` | <span data-ttu-id="1b8e6-138">규칙의 기본 심각도가 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-138">The default severity of the rule is used.</span></span> |

> [!TIP]
> <span data-ttu-id="1b8e6-139">Visual Studio의 규칙 심각도 화면에 대 한 자세한 내용은 [심각도 수준](/visualstudio/ide/editorconfig-language-conventions#severity-levels)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-139">For information about how rule severities surface in Visual Studio, see [Severity levels](/visualstudio/ide/editorconfig-language-conventions#severity-levels).</span></span>

#### <a name="scope"></a><span data-ttu-id="1b8e6-140">범위</span><span class="sxs-lookup"><span data-stu-id="1b8e6-140">Scope</span></span>

<span data-ttu-id="1b8e6-141">단일 규칙에 대 한 규칙 심각도를 설정 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-141">To set the rule severity for a single rule, use the following syntax.</span></span>

```ini
dotnet_diagnostic.<rule ID>.severity = <severity value>
```

<span data-ttu-id="1b8e6-142">분석기 규칙의 범주에 대 한 기본 규칙 심각도를 설정 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-142">To set the default rule severity for a category of analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.category-<rule category>.severity = <severity value>
```

<span data-ttu-id="1b8e6-143">모든 분석기 규칙에 대 한 기본 규칙 심각도를 설정 하려면 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-143">To set the default rule severity for all analyzer rules, use the following syntax.</span></span>

```ini
dotnet_analyzer_diagnostic.severity = <severity value>
```

#### <a name="precedence"></a><span data-ttu-id="1b8e6-144">우선 순위</span><span class="sxs-lookup"><span data-stu-id="1b8e6-144">Precedence</span></span>

<span data-ttu-id="1b8e6-145">동일한 규칙 ID에 적용할 수 있는 여러 심각도 구성 항목이 있는 경우 우선 순위는 다음 순서로 선택 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-145">If you have multiple severity configuration entries that can be applied to the same rule ID, precedence is chosen in the following order:</span></span>

- <span data-ttu-id="1b8e6-146">ID 별로 개별 규칙의 항목은 범주에 대 한 항목 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-146">An entry for an individual rule by ID takes precedence over an entry for a category.</span></span>
- <span data-ttu-id="1b8e6-147">범주에 대 한 항목은 모든 분석기 규칙의 항목 보다 우선적으로 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-147">An entry for a category takes precedence over an entry for all analyzer rules.</span></span>

<span data-ttu-id="1b8e6-148">다음 예를 살펴보십시오. 여기서 [CA1822](/visualstudio/code-quality/ca1822) 에는 "Performance" 범주가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-148">Consider the following example, where [CA1822](/visualstudio/code-quality/ca1822) has the category "Performance":</span></span>

```ini
[*.cs]
dotnet_diagnostic.CA1822.severity = error
dotnet_analyzer_diagnostic.category-performance.severity = warning
dotnet_analyzer_diagnostic.severity = suggestion
```

<span data-ttu-id="1b8e6-149">앞의 예제에서는 세 가지 심각도 항목을 모두 CA1822에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-149">In the preceding example, all three severity entries are applicable to CA1822.</span></span> <span data-ttu-id="1b8e6-150">그러나 지정 된 선행 규칙을 사용 하 여 첫 번째 규칙 ID 기반 항목은 다음 항목에 대해 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-150">However, using the specified precedence rules, the first rule ID-based entry wins over the next entries.</span></span> <span data-ttu-id="1b8e6-151">이 예제에서 CA1822은의 유효 심각도를 갖습니다 `error` .</span><span class="sxs-lookup"><span data-stu-id="1b8e6-151">In this example, CA1822 will have an effective severity of `error`.</span></span> <span data-ttu-id="1b8e6-152">"성능" 범주 내의 다른 모든 규칙은의 심각도를 갖습니다 `warning` .</span><span class="sxs-lookup"><span data-stu-id="1b8e6-152">All other rules within the "Performance" category will have a severity of `warning`.</span></span>

<span data-ttu-id="1b8e6-153">파일 간 우선 순위를 결정 하는 방법에 대 한 자세한 내용은 [구성 파일 문서의 우선 순위 섹션](configuration-files.md#precedence)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="1b8e6-153">For information about how inter-file precedence is decided, see the [Precedence section of the Configuration files article](configuration-files.md#precedence).</span></span>
