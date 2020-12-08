---
title: '호환성이 손상되는 변경: CA1831: 문자열에 대해 범위 기반 인덱서 대신 AsSpan 사용'
description: 코드 분석 규칙 CA1831 사용으로 발생하는 .NET 5.0의 호환성이 손상되는 변경에 대해 알아봅니다.
ms.date: 08/21/2020
ms.openlocfilehash: 850916b804ae29dba8d2bd05c6e4fb06fe667296
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437887"
---
# <a name="warning-ca1831-use-asspan-instead-of-range-based-indexers-for-string"></a><span data-ttu-id="d398a-103">경고 CA1831: 문자열에 대해 범위 기반 인덱서 대신 AsSpan 사용</span><span class="sxs-lookup"><span data-stu-id="d398a-103">Warning CA1831: Use AsSpan instead of Range-based indexers for string</span></span>

<span data-ttu-id="d398a-104">.Net 코드 분석기 규칙 [CA1831](/visualstudio/code-quality/ca1831)은 .NET 5.0부터 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-104">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="d398a-105"><xref:System.Range> 기반 인덱서가 문자열에서 사용되지만 복사본이 의도되지 않은 코드에 관한 빌드 경고를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-105">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

## <a name="change-description"></a><span data-ttu-id="d398a-106">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="d398a-106">Change description</span></span>

<span data-ttu-id="d398a-107">.Net 5.0부터 .Net SDK에는 [.NET 소스 코드 분석기](../../../../fundamentals/code-analysis/overview.md)가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-107">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../fundamentals/code-analysis/overview.md).</span></span> <span data-ttu-id="d398a-108">[CA1831](/visualstudio/code-quality/ca1831)을 포함하여 해당 규칙 중 여러 개가 기본적으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-108">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="d398a-109">해당 규칙을 위반하는 코드가 프로젝트에 포함되고 프로젝트가 경고를 오류로 처리하도록 구성된 경우 해당 변경으로 인해 빌드의 호환성이 손상될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-109">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="d398a-110">규칙 CA1831은 <xref:System.Range> 기반 인덱서가 문자열에서 사용되지만 복사본이 의도되지 않은 인스턴스를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-110">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="d398a-111"><xref:System.Range> 기반 인덱서가 암시적 캐스트를 생성하기 위해 문자열에서 직접 사용되는 경우에는 요청된 문자열 부분의 불필요한 복사본이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-111">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="d398a-112">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="d398a-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="d398a-113">CA1831은 대신에 문자열의 ‘범위’에서 <xref:System.Range> 기반 인덱서를 사용하도록 제안합니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-113">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="d398a-114">예를 들어:</span><span class="sxs-lookup"><span data-stu-id="d398a-114">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

## <a name="version-introduced"></a><span data-ttu-id="d398a-115">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="d398a-115">Version introduced</span></span>

<span data-ttu-id="d398a-116">5.0</span><span class="sxs-lookup"><span data-stu-id="d398a-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="d398a-117">권장 조치</span><span class="sxs-lookup"><span data-stu-id="d398a-117">Recommended action</span></span>

- <span data-ttu-id="d398a-118">코드를 수정하고 불필요한 할당을 방지하려면 <xref:System.Range> 기반 인덱서를 사용하기 전에 <xref:System.MemoryExtensions.AsSpan(System.String)> 또는 <xref:System.MemoryExtensions.AsMemory(System.String)>를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-118">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="d398a-119">예:</span><span class="sxs-lookup"><span data-stu-id="d398a-119">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="d398a-120">코드를 변경하지 않으려는 경우 심각도를 `suggestion` 또는 `none`으로 설정하여 규칙을 사용하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-120">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="d398a-121">자세한 내용은 [코드 분석 규칙 구성](../../../../fundamentals/code-analysis/configuration-options.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d398a-121">For more information, see [Configure code analysis rules](../../../../fundamentals/code-analysis/configuration-options.md).</span></span>

- <span data-ttu-id="d398a-122">코드 분석을 완전히 사용하지 않으려면 프로젝트 파일에서 `EnableNETAnalyzers`를 `false`로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="d398a-122">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="d398a-123">자세한 내용은 [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d398a-123">For more information, see [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="d398a-124">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="d398a-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Range`

### Category

Code analysis

-->
