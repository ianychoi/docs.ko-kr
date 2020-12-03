---
title: '호환성이 손상되는 변경: Pubternal API가 제거됨'
description: 일부 pubternal 지역화 API가 제거된 ASP.NET Core 5.0의 호환성이 손상되는 변경에 대해 알아봅니다.
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: ae647d66b716175536edb3c978b027ebb7d3ddac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759659"
---
# <a name="localization-pubternal-apis-removed"></a><span data-ttu-id="dd391-103">지역화: "Pubternal" API가 제거됨</span><span class="sxs-lookup"><span data-stu-id="dd391-103">Localization: "Pubternal" APIs removed</span></span>

<span data-ttu-id="dd391-104">ASP.NET Core의 공용 API 노출 영역을 보다 효율적으로 유지 관리하기 위해 일부 :::no-loc text="\"pubternal\""::: 지역화 API가 제거되었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-104">To better maintain the public API surface of ASP.NET Core, some :::no-loc text="\"pubternal\""::: localization APIs were removed.</span></span> <span data-ttu-id="dd391-105">:::no-loc text="\"pubternal\""::: API는 `public` 액세스 한정자를 포함하고 있으며 [internal](../../../../csharp/language-reference/keywords/internal.md) 의도를 암시하는 네임스페이스에서 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-105">A :::no-loc text="\"pubternal\""::: API has a `public` access modifier and is defined in a namespace that implies an [internal](../../../../csharp/language-reference/keywords/internal.md) intent.</span></span>

<span data-ttu-id="dd391-106">자세한 내용은 [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd391-106">For discussion, see [dotnet/aspnetcore#22291](https://github.com/dotnet/aspnetcore/issues/22291).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="dd391-107">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="dd391-107">Version introduced</span></span>

<span data-ttu-id="dd391-108">5.0 미리 보기 6</span><span class="sxs-lookup"><span data-stu-id="dd391-108">5.0 Preview 6</span></span>

## <a name="old-behavior"></a><span data-ttu-id="dd391-109">이전 동작</span><span class="sxs-lookup"><span data-stu-id="dd391-109">Old behavior</span></span>

<span data-ttu-id="dd391-110">다음 API는 `public`이었습니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-110">The following APIs were `public`:</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <span data-ttu-id="dd391-111">다음 매개 변수 형식 중 하나를 허용하는 `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 생성자 오버로드:</span><span class="sxs-lookup"><span data-stu-id="dd391-111">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="new-behavior"></a><span data-ttu-id="dd391-112">새 동작</span><span class="sxs-lookup"><span data-stu-id="dd391-112">New behavior</span></span>

<span data-ttu-id="dd391-113">다음 목록에서는 변경 내용을 간략하게 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-113">The following list outlines the changes:</span></span>

- <span data-ttu-id="dd391-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper`가 `Microsoft.Extensions.Localization.AssemblyWrapper`가 되었으며 이제 `internal`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-114">`Microsoft.Extensions.Localization.Internal.AssemblyWrapper` became `Microsoft.Extensions.Localization.AssemblyWrapper` and is now `internal`.</span></span>
- <span data-ttu-id="dd391-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider`가 `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`가 되었으며 이제 `internal`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-115">`Microsoft.Extensions.Localization.Internal.IResourceStringProvider` became `Microsoft.Extensions.Localization.Internal.IResourceStringProvider` and is now `internal`.</span></span>
- <span data-ttu-id="dd391-116">다음 매개 변수 형식 중 하나를 허용하는 `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` 생성자 오버로드가 이제 `internal`입니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-116">`Microsoft.Extensions.Localization.ResourceManagerStringLocalizer` constructor overloads accepting either of the following parameter types are now `internal`:</span></span>
  - `AssemblyWrapper`
  - `IResourceStringProvider`

## <a name="reason-for-change"></a><span data-ttu-id="dd391-117">변경 이유</span><span class="sxs-lookup"><span data-stu-id="dd391-117">Reason for change</span></span>

<span data-ttu-id="dd391-118">`public` API 노출 영역에서 :::no-loc text="\"pubternal\""::: 형식이 제거되었습니다([aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)에서 더 자세히 설명).</span><span class="sxs-lookup"><span data-stu-id="dd391-118">Explained more thoroughly at [aspnet/Announcements#377](https://github.com/aspnet/Announcements/issues/377#issue-473651882), :::no-loc text="\"pubternal\""::: types were removed from the `public` API surface.</span></span> <span data-ttu-id="dd391-119">이러한 변경은 해당 디자인 결정에 따라 더 많은 클래스를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-119">These changes adapt more classes to that design decision.</span></span> <span data-ttu-id="dd391-120">해당 클래스는 팀의 내부 테스트를 위한 확장 지점으로 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-120">The classes in question were intended as extension points for the team's internal testing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="dd391-121">권장 조치</span><span class="sxs-lookup"><span data-stu-id="dd391-121">Recommended action</span></span>

<span data-ttu-id="dd391-122">발생할 가능성은 거의 없지만 일부 앱은 의도적으로 또는 실수로 :::no-loc text="\"pubternal\""::: 형식에 의존할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="dd391-122">Although it's unlikely, some apps may intentionally or accidentally depend upon the :::no-loc text="\"pubternal\""::: types.</span></span> <span data-ttu-id="dd391-123">형식에서 마이그레이션하는 방법을 확인하려면 [새 동작](#new-behavior) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="dd391-123">See the [New behavior](#new-behavior) sections to determine how to migrate away from the types.</span></span>

<span data-ttu-id="dd391-124">이 변경 전에 공용 API에서 허용되었지만 지금은 허용되지 않는 시나리오를 확인했다면 [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)에서 이슈를 제출하세요.</span><span class="sxs-lookup"><span data-stu-id="dd391-124">If you've identified a scenario which the public API allowed before this change but doesn't now, file an issue at [dotnet/aspnetcore](https://github.com/dotnet/aspnetcore/issues).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="dd391-125">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="dd391-125">Affected APIs</span></span>

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
