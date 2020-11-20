---
ms.openlocfilehash: bd0953697ee3a9e928d09c1f270a4af5606ee0d9
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507075"
---

### <a name="install-the-sdk"></a><span data-ttu-id="59237-101">SDK 설치</span><span class="sxs-lookup"><span data-stu-id="59237-101">Install the SDK</span></span>

<span data-ttu-id="59237-102">.NET Core SDK를 사용하면 .NET Core로 앱을 개발할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59237-102">The .NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="59237-103">.NET Core SDK를 설치하면 해당 런타임을 설치할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="59237-103">If you install the .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="59237-104">.NET Core SDK를 설치하려면 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="59237-104">To install the .NET Core SDK, run the following commands:</span></span>

```bash
sudo dnf install dotnet-sdk-2.0
```

### <a name="install-the-runtime"></a><span data-ttu-id="59237-105">런타임 설치</span><span class="sxs-lookup"><span data-stu-id="59237-105">Install the runtime</span></span>

<span data-ttu-id="59237-106">.NET Core 런타임을 사용하면 런타임을 포함하지 않았던 .NET Core로 만든 앱을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="59237-106">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="59237-107">다음 명령을 실행하면 .NET Core에 대해 가장 호환성이 높은 ASP.NET Core 런타임이 설치됩니다.</span><span class="sxs-lookup"><span data-stu-id="59237-107">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="59237-108">터미널에서 다음 명령을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="59237-108">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install aspnetcore-runtime-2.0
```

<span data-ttu-id="59237-109">ASP.NET Core 런타임 대신 ASP.NET Core 지원이 포함되지 않은 .NET Core 런타임을 설치할 수 있습니다. 이전 명령에서 `aspnetcore-runtime-2.0`을 `dotnet-runtime-2.0`으로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="59237-109">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime, which doesn't include ASP.NET Core support: replace `aspnetcore-runtime-2.0` in the previous command with `dotnet-runtime-2.0`.</span></span>

```bash
sudo dnf install dotnet-runtime-2.0
```
