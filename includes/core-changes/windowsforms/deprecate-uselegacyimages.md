---
ms.openlocfilehash: 07527c247e6ccd53d2a77793946ffc796c3e1cbb
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71181725"
---
### <a name="switchsystemwindowsformsuselegacyimages-compatibility-switch-not-supported"></a><span data-ttu-id="6c9bd-101">Switch.System.Windows.Forms.UseLegacyImages 호환성 스위치가 지원되지 않음</span><span class="sxs-lookup"><span data-stu-id="6c9bd-101">Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported</span></span>

<span data-ttu-id="6c9bd-102">.NET Framework 4.8에서 도입된 `Switch.System.Windows.Forms.UseLegacyImages` 호환성 스위치는 .NET Core 3.0의 Windows Forms에서 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-102">The `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch, which was introduced in .NET Framework 4.8, is not supported in Windows Forms on .NET Core 3.0.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6c9bd-103">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="6c9bd-103">Change description</span></span>

<span data-ttu-id="6c9bd-104">.NET Framework 4.8부터는 `Switch.System.Windows.Forms.UseLegacyImages` 호환성 스위치가 높은 DPI 환경의 ClickOnce 시나리오에서 가능한 이미지 크기 조정 문제를 해결했습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-104">Starting with the .NET Framework 4.8, the `Switch.System.Windows.Forms.UseLegacyImages` compatibility switch addressed possible image scaling issues in ClickOnce scenarios in high DPI environments.</span></span> <span data-ttu-id="6c9bd-105">`true`로 설정하면, 사용자가 이 스위치를 통해 배율이 100%보다 큰 값으로 설정된 높은 DPI 디스플레이에서 레거시 이미지 크기 조정을 복원할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-105">When set to `true`, the switch allows the user to restore legacy image scaling on high DPI displays whose scale is set to greater than 100%.</span></span> <span data-ttu-id="6c9bd-106">자세한 내용은 GitHub에서 [.NET Framework 4.8 릴리스 정보](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-106">For more information, see [.NET Framework 4.8 Release Notes](https://github.com/microsoft/dotnet/blob/master/releases/net48/dotnet48-changes.md#clickonce) on GitHub.</span></span>

<span data-ttu-id="6c9bd-107">.NET Core에서는 `Switch.System.Windows.Forms.UseLegacyImages` 스위치가 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-107">In .NET Core, the `Switch.System.Windows.Forms.UseLegacyImages` switch is not supported.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6c9bd-108">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="6c9bd-108">Version introduced</span></span>

<span data-ttu-id="6c9bd-109">3.0 미리 보기 9</span><span class="sxs-lookup"><span data-stu-id="6c9bd-109">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6c9bd-110">권장 작업</span><span class="sxs-lookup"><span data-stu-id="6c9bd-110">Recommended action</span></span>

<span data-ttu-id="6c9bd-111">스위치를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-111">Remove the switch.</span></span> <span data-ttu-id="6c9bd-112">이 스위치는 지원되지 않으며, 사용 가능한 대체 기능이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c9bd-112">The switch is not supported, and no alternative functionality is available.</span></span>

#### <a name="category"></a><span data-ttu-id="6c9bd-113">범주</span><span class="sxs-lookup"><span data-stu-id="6c9bd-113">Category</span></span>

<span data-ttu-id="6c9bd-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c9bd-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6c9bd-115">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="6c9bd-115">Affected APIs</span></span>

- <span data-ttu-id="6c9bd-116">없음</span><span class="sxs-lookup"><span data-stu-id="6c9bd-116">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->