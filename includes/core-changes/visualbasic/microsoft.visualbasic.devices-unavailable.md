---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237409"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a><span data-ttu-id="c31f2-101">Microsoft.VisualBasic.Devices 네임스페이스의 형식을 사용할 수 없음</span><span class="sxs-lookup"><span data-stu-id="c31f2-101">Types in Microsoft.VisualBasic.Devices namespace not available</span></span>

<span data-ttu-id="c31f2-102"><xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 네임스페이스의 형식을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-102">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace are not available.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c31f2-103">도입된 버전</span><span class="sxs-lookup"><span data-stu-id="c31f2-103">Version introduced</span></span>

<span data-ttu-id="c31f2-104">.NET Core 3.0 미리 보기 8</span><span class="sxs-lookup"><span data-stu-id="c31f2-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="c31f2-105">변경 내용 설명</span><span class="sxs-lookup"><span data-stu-id="c31f2-105">Change description</span></span>

<span data-ttu-id="c31f2-106">일부 .NET Core 3.0 미리 보기 릴리스에서는 <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> 네임스페이스의 형식을 사용할 수 있었습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-106">The types in the <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> namespace were available in some .NET Core 3.0 Preview releases,.</span></span> <span data-ttu-id="c31f2-107">.NET Core 3.0 미리 보기 9부터는 해당 형식을 더 이상 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-107">They are no longer available starting with .NET Core 3.0 Preview 9.</span></span>

<span data-ttu-id="c31f2-108">후속 릴리스에서 불필요한 어셈블리 종속성이나 호환성이 손상되는 변경을 방지하기 위해 형식을 제거했습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-108">The types were removed to avoid unnecessary assembly dependencies or breaking changes in subsequent releases.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="c31f2-109">권장 작업</span><span class="sxs-lookup"><span data-stu-id="c31f2-109">Recommended action</span></span>

<span data-ttu-id="c31f2-110">코드에서 <xref:Microsoft.VisualBasic.Devices> 형식과 해당 멤버를 사용해야 하는 경우, .NET 클래스 라이브러리의 해당 형식이나 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-110">If your code depends on the use of <xref:Microsoft.VisualBasic.Devices> types and their members, you may be able to use a corresponding type or member in the .NET class library.</span></span> <span data-ttu-id="c31f2-111">예를 들어 <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> 클래스와 동등한 기능은 <xref:System.DateTime?displayProperty=nameWithType> 및 <xref:System.Environment?displayProperty=nameWithType> 형식에서 제공되고, <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> 클래스와 동등한 기능은 <xref:System.IO.Ports?displayProperty=nameWithType> 네임스페이스의 형식에서 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="c31f2-111">For example, equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> class is provided by the <xref:System.DateTime?displayProperty=nameWithType> and <xref:System.Environment?displayProperty=nameWithType> types, and equivalent functionality to the <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> class is provided by types in the <xref:System.IO.Ports?displayProperty=nameWithType> namespace.</span></span>

#### <a name="category"></a><span data-ttu-id="c31f2-112">범주</span><span class="sxs-lookup"><span data-stu-id="c31f2-112">Category</span></span>

<span data-ttu-id="c31f2-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c31f2-113">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c31f2-114">영향을 받는 API</span><span class="sxs-lookup"><span data-stu-id="c31f2-114">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >
