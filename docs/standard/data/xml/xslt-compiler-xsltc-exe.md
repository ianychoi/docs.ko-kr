---
title: XSLT 컴파일러(xsltc.exe)
ms.date: 03/30/2017
ms.assetid: 672a5ac8-8305-4d28-ba10-11089c2c0924
ms.openlocfilehash: 89e2291cb4eafe9ca9e5001061b960f348fe4719
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720830"
---
# <a name="xslt-compiler-xsltcexe"></a><span data-ttu-id="d907f-102">XSLT 컴파일러(xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="d907f-102">XSLT Compiler (xsltc.exe)</span></span>

<span data-ttu-id="d907f-103">XSLT 컴파일러(xsltc.exe)에서는 XSLT 스타일시트를 컴파일하여 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="d907f-104">컴파일된 스타일시트는 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 메서드로 직접 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-104">The compiled style sheet can then be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d907f-105">서명된 어셈블리는 xsltc.exe를 사용하여 생성할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-105">You cannot generate signed assemblies with xsltc.exe.</span></span>  
  
 <span data-ttu-id="d907f-106">xsltc.exe 도구는 Visual Studio에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-106">The xsltc.exe tool is included with Visual Studio.</span></span> <span data-ttu-id="d907f-107">자세한 내용은 [Visual Studio 다운로드](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d907f-107">For more information, see the [Visual Studio Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d907f-108">구문</span><span class="sxs-lookup"><span data-stu-id="d907f-108">Syntax</span></span>  
  
```console  
xsltc [options] [/class:<name>] <sourceFile> [[/class:<name>] <sourceFile>...]  
```  
  
## <a name="argument"></a><span data-ttu-id="d907f-109">인수</span><span class="sxs-lookup"><span data-stu-id="d907f-109">Argument</span></span>  
  
|<span data-ttu-id="d907f-110">인수</span><span class="sxs-lookup"><span data-stu-id="d907f-110">Argument</span></span>|<span data-ttu-id="d907f-111">설명</span><span class="sxs-lookup"><span data-stu-id="d907f-111">Description</span></span>|  
|--------------|-----------------|  
|`sourceFile`|<span data-ttu-id="d907f-112">스타일시트 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-112">Specifies the name of the style sheet.</span></span> <span data-ttu-id="d907f-113">스타일시트는 로컬 파일이거나 인트라넷에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-113">The style sheet must be a local file or be located on the intranet.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="d907f-114">옵션</span><span class="sxs-lookup"><span data-stu-id="d907f-114">Options</span></span>  
  
|<span data-ttu-id="d907f-115">옵션</span><span class="sxs-lookup"><span data-stu-id="d907f-115">Option</span></span>|<span data-ttu-id="d907f-116">설명</span><span class="sxs-lookup"><span data-stu-id="d907f-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="d907f-117">`/c[lass]:` `name`</span><span class="sxs-lookup"><span data-stu-id="d907f-117">`/c[lass]:` `name`</span></span>|<span data-ttu-id="d907f-118">다음 스타일시트의 클래스 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-118">Specifies the name of the class for the following style sheet.</span></span> <span data-ttu-id="d907f-119">클래스 이름은 정규화된 이름일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-119">The class name can be fully qualified.</span></span><br /><br /> <span data-ttu-id="d907f-120">클래스 이름은 기본적으로 스타일시트 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-120">The class name defaults to the name of the style sheet.</span></span> <span data-ttu-id="d907f-121">예를 들어 customers.xsl 스타일시트가 컴파일되면 기본 클래스 이름은 customers입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-121">For example, if the style sheet customers.xsl is compiled, the default class name is customers.</span></span>|  
|<span data-ttu-id="d907f-122">`/debug[`+&#124;-`]`</span><span class="sxs-lookup"><span data-stu-id="d907f-122">`/debug[`+&#124;-`]`</span></span>|<span data-ttu-id="d907f-123">디버깅 정보를 생성할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-123">Specifies whether to generate debugging information.</span></span><br /><br /> <span data-ttu-id="d907f-124">`+` 또는 `/debug`를 지정하면 컴파일러에서 디버깅 정보를 생성하여 PDB(프로그램 데이터베이스) 파일에 넣습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-124">Specifying `+` or `/debug`, causes the compiler to generate debugging information and put it in a program database (PDB) file.</span></span> <span data-ttu-id="d907f-125">생성된 PDB 파일 이름은 `assemblyName`.pdb입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-125">The name of the generated PDB file is `assemblyName`.pdb.</span></span><br /><br /> <span data-ttu-id="d907f-126">`-`를 지정하면 `/debug`를 지정하지 않은 것으로 적용되어 디버그 정보가 생성되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-126">Specifying `-`, which is in effect if you do not specify `/debug`, causes no debug information to be created.</span></span> <span data-ttu-id="d907f-127">정식 버전의 어셈블리가 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-127">A retail assembly is generated.</span></span> <span data-ttu-id="d907f-128">**참고:**  디버그 모드에서 컴파일하면 XSLT 성능에 크게 영향을 미칠 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-128">**Note:**  Compiling in debug mode can affect XSLT performance significantly.</span></span>|  
|`/help`|<span data-ttu-id="d907f-129">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-129">Displays command syntax and options for the tool.</span></span>|  
|`/nologo`|<span data-ttu-id="d907f-130">컴파일러 저작권 메시지가 표시되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-130">Suppresses the compiler copyright message from displaying.</span></span>|  
|<span data-ttu-id="d907f-131">`/platform:` `string`</span><span class="sxs-lookup"><span data-stu-id="d907f-131">`/platform:` `string`</span></span>|<span data-ttu-id="d907f-132">어셈블리가 실행되는 플랫폼을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-132">Specifies the platforms that the assembly can be run on.</span></span> <span data-ttu-id="d907f-133">유효한 플랫폼 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-133">The following describes the valid platform values:</span></span><br /><br /> <span data-ttu-id="d907f-134">`x86`을 지정하면 32비트 x86 호환 공용 언어 런타임에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-134">`x86` compiles your assembly to be run by the 32-bit, x86-compatible common language runtime</span></span><br /><br /> <span data-ttu-id="d907f-135">`x64`를 지정하면 AMD64 또는 EM64T 명령 집합을 지원하는 컴퓨터에서 64비트 공용 언어 런타임에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-135">`x64` compiles your assembly to be run by the 64-bit common language runtime on a computer that supports the AMD64 or EM64T instruction set.</span></span><br /><br /> <span data-ttu-id="d907f-136">Itanium은 Itanium 프로세서가 있는 컴퓨터에서 64비트 공용 언어 런타임에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-136">Itanium compiles your assembly to be run by the 64-bit common language runtime on a computer that has an Itanium processor.</span></span><br /><br /> <span data-ttu-id="d907f-137">`anycpu`를 지정하면 임의의 플랫폼에서 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-137">`anycpu` compiles your assembly to run on any platform.</span></span> <span data-ttu-id="d907f-138">기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-138">This is the default.</span></span>|  
|<span data-ttu-id="d907f-139">`/out:` `assemblyName`</span><span class="sxs-lookup"><span data-stu-id="d907f-139">`/out:` `assemblyName`</span></span>|<span data-ttu-id="d907f-140">출력되는 어셈블리 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-140">Specifies the name of the assembly that is output.</span></span> <span data-ttu-id="d907f-141">어셈블리 이름은 기본적으로 기본 스타일시트 이름 또는 첫 번째 스타일시트 이름(스타일시트가 여러 개 있는 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-141">The assembly name defaults to the name of the main style sheet or the first style sheet if multiple style sheets are present.</span></span><br /><br /> <span data-ttu-id="d907f-142">스타일시트에 스크립트가 포함된 경우 스크립트는 별도 어셈블리로 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-142">If the style sheet contains scripts, the scripts are saved to a separate assembly.</span></span> <span data-ttu-id="d907f-143">스크립트 어셈블리 이름은 기본 어셈블리 이름에서 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-143">Script assembly names are generated from the main assembly name.</span></span> <span data-ttu-id="d907f-144">예를 들어 어셈블리 이름으로 CustOrders.dll을 지정한 경우 첫 번째 스크립트 어셈블리 이름은 CustOrders_Script1.dll입니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-144">For example, if you specified CustOrders.dll for your assembly name, the first script assembly is named CustOrders_Script1.dll.</span></span>|  
|<span data-ttu-id="d907f-145">`/settings:` `document+-, script+-, DTD+-,`</span><span class="sxs-lookup"><span data-stu-id="d907f-145">`/settings:` `document+-, script+-, DTD+-,`</span></span>|<span data-ttu-id="d907f-146">스타일시트에 `document()` 함수, XSLT 스크립트 또는 DTD(문서 종류 정의)를 허용할지 여부를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-146">Specifies whether to allow `document()` functions, XSLT script, or document type definition (DTD) in the style sheet.</span></span><br /><br /> <span data-ttu-id="d907f-147">기본 동작에서는 DTD, `document()` 함수 및 스크립트를 지원하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-147">The default behavior disables support for DTD, the `document()` function and scripting.</span></span>|  
|<span data-ttu-id="d907f-148">`@` `file`</span><span class="sxs-lookup"><span data-stu-id="d907f-148">`@` `file`</span></span>|<span data-ttu-id="d907f-149">컴파일러 옵션이 포함된 파일을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-149">Lets you specify a file that contains the compiler options.</span></span>|  
|`?`|<span data-ttu-id="d907f-150">이 도구의 명령 구문 및 옵션을 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-150">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d907f-151">설명</span><span class="sxs-lookup"><span data-stu-id="d907f-151">Remarks</span></span>  

 <span data-ttu-id="d907f-152">XSLT 솔루션은 여러 스타일시트 모듈로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-152">XSLT solutions can consist of multiple style sheet modules.</span></span> <span data-ttu-id="d907f-153">xsltc.exe 도구는 스타일시트에서 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-153">The xsltc.exe tool generates assemblies from style sheets.</span></span> <span data-ttu-id="d907f-154">그런 다음 어셈블리가 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 메서드에 전달될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-154">The assemblies can then be passed into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d907f-155">따라서 일부 XSLT 배포 시나리오에서 성능을 유지하는 데 드는 비용을 감소하는 데 도움이 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-155">This can help decrease performance costs in some XSLT deployment scenarios.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d907f-156">애플리케이션에서 컴파일된 어셈블리를 참조로 포함해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-156">You must also include the compiled assembly as a reference in your application.</span></span>  
  
 <span data-ttu-id="d907f-157">xsltc.exe 도구에서는 클래스(`/class:`*이름*) 또는 어셈블리(`/out:`*assemblyName*) 이름의 유효성을 검사하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-157">The xsltc.exe tool does not validate the class (`/class:`*name*) or assembly (`/out:`*assemblyName*) names.</span></span> <span data-ttu-id="d907f-158">이름의 유효성을 확인할 수 없으면 공용 언어 런타임에서 오류가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-158">Errors are thrown by the common language runtime if the names are not valid.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d907f-159">예</span><span class="sxs-lookup"><span data-stu-id="d907f-159">Examples</span></span>  

 <span data-ttu-id="d907f-160">다음 명령에서는 스타일시트를 컴파일하여 이름이 booksort.dll인 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-160">The following command compiles the style sheet and creates an assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl  
```  
  
 <span data-ttu-id="d907f-161">다음 명령에서는 스타일시트를 컴파일하여 이름이 각각 booksort.dll 및 booksort.pdb인 어셈블리와 PDB 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-161">The following command compiles the style sheet and creates an assembly and PDB file that are named booksort.dll and booksort.pdb respectively.</span></span>  
  
```console  
xsltc booksort.xsl /debug  
```  
  
 <span data-ttu-id="d907f-162">다음 명령에서는 msxsl:script 요소가 포함된 스타일시트를 컴파일하여 이름이 calc.dll 및 calc_Script1.dll인 두 개의 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-162">The following command compiles a style sheet that contains an msxsl:script element and creates two assemblies named calc.dll and calc_Script1.dll.</span></span>  
  
```console  
xsltc /settings:script+ calc.xsl  
```  
  
 <span data-ttu-id="d907f-163">다음 명령에서는 DTD 처리 및 스크립트 지원을 활성화하여 이름이 myTest.dll 및 myTest_Script1.dll인 두 개의 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-163">The following command enables DTD processing and script support and creates two assemblies named myTest.dll and myTest_Script1.dll.</span></span>  
  
```console  
xsltc /settings:DTD+,script+ /out:myTest calc.xsl  
```  
  
 <span data-ttu-id="d907f-164">다음 명령에서는 두 개의 스타일시트 모듈을 컴파일하여 이름이 booksort.dll인 단일 어셈블리를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d907f-164">The following command compiles two style sheet modules and creates a single assembly named booksort.dll.</span></span>  
  
```console  
xsltc booksort.xsl output.xsl  
```  
  
## <a name="see-also"></a><span data-ttu-id="d907f-165">참조</span><span class="sxs-lookup"><span data-stu-id="d907f-165">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="d907f-166">방법: 어셈블리를 사용하여 XSLT 변형 수행</span><span class="sxs-lookup"><span data-stu-id="d907f-166">How to: Perform an XSLT Transformation by Using an Assembly</span></span>](how-to-perform-an-xslt-transformation-by-using-an-assembly.md)
- [<span data-ttu-id="d907f-167">XSLT 변환</span><span class="sxs-lookup"><span data-stu-id="d907f-167">XSLT Transformations</span></span>](xslt-transformations.md)
