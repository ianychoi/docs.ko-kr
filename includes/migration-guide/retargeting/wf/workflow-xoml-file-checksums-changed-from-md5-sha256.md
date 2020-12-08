---
ms.openlocfilehash: b1910bf0338bccd77ad9e983990d4d193698ec1f
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96478512"
---
### <a name="workflow-xoml-file-checksums-changed-from-md5-to-sha256"></a><span data-ttu-id="69ac6-101">워크플로 XOML 파일 체크섬이 MD5에서 SHA256으로 변경됨</span><span class="sxs-lookup"><span data-stu-id="69ac6-101">Workflow XOML file checksums changed from MD5 to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="69ac6-102">설명</span><span class="sxs-lookup"><span data-stu-id="69ac6-102">Details</span></span>

<span data-ttu-id="69ac6-103">Visual Studio를 사용하여 XOML 기반 워크플로 디버깅을 지원하기 위해 XOML 파일이 포함된 워크플로 프로젝트를 빌드할 때 XOML 파일의 콘텐츠에 대한 체크섬이 <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> 값으로 생성된 코드에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-103">To support debugging XOML-based workflows with Visual Studio, when workflow projects containing XOML files build, a checksum of the contents of the XOML file is included in the code generated as a <xref:System.Workflow.ComponentModel.Compiler.WorkflowMarkupSourceAttribute.MD5Digest?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="69ac6-104">.NET Framework 4.7.2 이전 버전에서 이 체크섬 해시는 MD5 알고리즘을 사용하여 FIPS 지원 시스템에 문제가 발생했습니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-104">In the .NET Framework 4.7.2 and earlier versions, this checksum hashing used the MD5 algorithm, which caused issues on FIPS-enabled systems.</span></span> <span data-ttu-id="69ac6-105">.NET Framework 4.8부터 사용된 알고리즘은 SHA256입니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-105">Starting with the .NET Framework 4.8, the algorithm used is SHA256.</span></span> <span data-ttu-id="69ac6-106">WorkflowMarkupSourceAttribute.MD5Digest와 호환되도록 생성된 체크섬의 처음 16바이트만 사용됩니다. 이는 디버깅 중에 문제가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-106">To be compatible with the WorkflowMarkupSourceAttribute.MD5Digest, only the first 16 bytes of the generated checksum are used.This may cause problems during debugging.</span></span> <span data-ttu-id="69ac6-107">프로젝트를 다시 빌드해야 할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-107">You may need to re-build your project.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="69ac6-108">제안 해결 방법</span><span class="sxs-lookup"><span data-stu-id="69ac6-108">Suggestion</span></span>

<span data-ttu-id="69ac6-109">프로젝트를 다시 빌드해도 문제가 해결되지 않으면 다음 코드에서 `AppContext` 스위치 &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;을 true로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-109">If re-building your project does not solve the problem, try setting the `AppContext` switch &quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot; to true.In code:</span></span>

<pre><code class="lang-csharp">System.AppContext.SetSwitch(&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum&quot;, true);&#13;&#10;</code></pre>

<span data-ttu-id="69ac6-110">또는 구성 파일(사용 중인 MSBuild.exe에의 경우 MSBuild.exe.config이 있어야 함)에서 다음을 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="69ac6-110">Or in a configuration file (this needs to be in MSBuild.exe.config for the MSBuild.exe that you are using):</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Workflow.ComponentModel.UseLegacyHashForXomlFileChecksum=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="69ac6-111">이름</span><span class="sxs-lookup"><span data-stu-id="69ac6-111">Name</span></span>    | <span data-ttu-id="69ac6-112">값</span><span class="sxs-lookup"><span data-stu-id="69ac6-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="69ac6-113">Scope</span><span class="sxs-lookup"><span data-stu-id="69ac6-113">Scope</span></span>   | <span data-ttu-id="69ac6-114">부</span><span class="sxs-lookup"><span data-stu-id="69ac6-114">Minor</span></span>       |
| <span data-ttu-id="69ac6-115">버전</span><span class="sxs-lookup"><span data-stu-id="69ac6-115">Version</span></span> | <span data-ttu-id="69ac6-116">4.8</span><span class="sxs-lookup"><span data-stu-id="69ac6-116">4.8</span></span>         |
| <span data-ttu-id="69ac6-117">형식</span><span class="sxs-lookup"><span data-stu-id="69ac6-117">Type</span></span>    | <span data-ttu-id="69ac6-118">대상 변경</span><span class="sxs-lookup"><span data-stu-id="69ac6-118">Retargeting</span></span> |
