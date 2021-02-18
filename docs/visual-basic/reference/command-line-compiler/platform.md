---
description: '자세한 정보: -platform(Visual Basic)'
title: -platform
ms.date: 03/13/2018
helpviewer_keywords:
- platform compiler option [Visual Basic]
- /platform compiler option [Visual Basic]
- -platform compiler option [Visual Basic]
ms.assetid: f9bc61e6-e854-4ae1-87b9-d6244de23fd1
ms.openlocfilehash: 51d7c7882c29310ef1e0c0f5790a63da3bfb91b8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432743"
---
# <a name="-platform-visual-basic"></a><span data-ttu-id="0dc9c-103">-platform(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dc9c-103">-platform (Visual Basic)</span></span>

<span data-ttu-id="0dc9c-104">출력 파일을 실행할 수 있는 CLR(공용 언어 런타임) 플랫폼 버전을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-104">Specifies which platform version of common language runtime (CLR) can run the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc9c-105">구문</span><span class="sxs-lookup"><span data-stu-id="0dc9c-105">Syntax</span></span>  
  
```console  
-platform:{ x86 | x64 | Itanium | arm | anycpu | anycpu32bitpreferred }  
```  
  
## <a name="arguments"></a><span data-ttu-id="0dc9c-106">인수</span><span class="sxs-lookup"><span data-stu-id="0dc9c-106">Arguments</span></span>  
  
|<span data-ttu-id="0dc9c-107">용어</span><span class="sxs-lookup"><span data-stu-id="0dc9c-107">Term</span></span>|<span data-ttu-id="0dc9c-108">정의</span><span class="sxs-lookup"><span data-stu-id="0dc9c-108">Definition</span></span>|  
|---|---|  
|`x86`|<span data-ttu-id="0dc9c-109">32비트, x86 호환 CLR에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-109">Compiles your assembly to be run by the 32-bit, x86-compatible CLR.</span></span>|  
|`x64`|<span data-ttu-id="0dc9c-110">AMD64 또는 EM64T 명령 집합을 지원하는 컴퓨터에서 64비트 CLR에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-110">Compiles your assembly to be run by the 64-bit CLR on a computer that supports the AMD64 or EM64T instruction set.</span></span>|  
|`Itanium`|<span data-ttu-id="0dc9c-111">Itanium 프로세서 탑재 컴퓨터에서 64비트 CLR에 의해 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-111">Compiles your assembly to be run by the 64-bit CLR on a computer with an Itanium processor.</span></span>|  
|`arm`|<span data-ttu-id="0dc9c-112">ARM(고급 RISC 컴퓨터) 프로세서를 탑재한 컴퓨터에서 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-112">Compiles your assembly to be run on a computer with an ARM (Advanced RISC Machine) processor.</span></span>|  
|`anycpu`|<span data-ttu-id="0dc9c-113">임의의 플랫폼에서 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-113">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0dc9c-114">애플리케이션은 32비트 버전 Windows에서는 32비트 애플리케이션으로, 64비트 버전 Windows에서는 64비트 애플리케이션으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-114">The application will run as a 32-bit application on 32-bit versions of Windows and as a 64-bit application on 64-bit versions of Windows.</span></span> <span data-ttu-id="0dc9c-115">이 플래그가 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-115">This flag is the default value.</span></span>|  
|`anycpu32bitpreferred`|<span data-ttu-id="0dc9c-116">임의의 플랫폼에서 실행되도록 어셈블리를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-116">Compiles your assembly to run on any platform.</span></span> <span data-ttu-id="0dc9c-117">애플리케이션은 32비트 및 64비트 버전 Windows 둘 다에서 32비트 애플리케이션으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-117">The application will run as a 32-bit application on both 32-bit and 64-bit versions of Windows.</span></span> <span data-ttu-id="0dc9c-118">이 플래그는 실행 파일(.EXE)에 대해서만 유효하며 .NET Framework 4.5가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-118">This flag is valid only for executables (.EXE) and requires .NET Framework 4.5.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dc9c-119">설명</span><span class="sxs-lookup"><span data-stu-id="0dc9c-119">Remarks</span></span>  

 <span data-ttu-id="0dc9c-120">출력 파일의 대상 프로세서 유형을 지정하려면 `-platform` 옵션을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-120">Use the `-platform` option to specify the type of processor targeted by the output file.</span></span>  
  
 <span data-ttu-id="0dc9c-121">일반적으로 Visual Basic에서 작성된 .NET Framework 어셈블리는 플랫폼에 관계없이 동일하게 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-121">In general, .NET Framework assemblies written in Visual Basic will run the same regardless of the platform.</span></span> <span data-ttu-id="0dc9c-122">그러나 플랫폼별로 동작이 다른 경우도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-122">However, there are some cases that behave differently on different platforms.</span></span> <span data-ttu-id="0dc9c-123">이러한 경우의 일반적인 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-123">These common cases are:</span></span>  
  
- <span data-ttu-id="0dc9c-124">포인터 형식과 같이 플랫폼에 따라 크기가 달라지는 멤버를 포함하는 구조체</span><span class="sxs-lookup"><span data-stu-id="0dc9c-124">Structures that contain members that change size depending on the platform, such as any pointer type.</span></span>  
  
- <span data-ttu-id="0dc9c-125">상수 크기를 포함하는 포인터 산술 연산</span><span class="sxs-lookup"><span data-stu-id="0dc9c-125">Pointer arithmetic that includes constant sizes.</span></span>  
  
- <span data-ttu-id="0dc9c-126">핸들에 대해 `Integer` 대신 <xref:System.IntPtr>를 사용하는 잘못된 플랫폼 호출 또는 COM 선언</span><span class="sxs-lookup"><span data-stu-id="0dc9c-126">Incorrect platform invoke or COM declarations that use `Integer` for handles instead of <xref:System.IntPtr>.</span></span>  
  
- <span data-ttu-id="0dc9c-127"><xref:System.IntPtr>을 `Integer`로 캐스팅</span><span class="sxs-lookup"><span data-stu-id="0dc9c-127">Casting <xref:System.IntPtr> to `Integer`.</span></span>  
  
- <span data-ttu-id="0dc9c-128">일부 플랫폼에만 있는 구성 요소를 통한 플랫폼 호출 또는 COM interop 사용</span><span class="sxs-lookup"><span data-stu-id="0dc9c-128">Using platform invoke or COM interop with components that do not exist on all platforms.</span></span>  
  
 <span data-ttu-id="0dc9c-129">코드를 실행할 아키텍처에 대한 가정 내용을 알고 있는 경우 **-platform** 옵션을 사용하면 일부 문제가 완화될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-129">The **-platform** option will mitigate some issues if you know you have made assumptions about the architecture your code will run on.</span></span> <span data-ttu-id="0dc9c-130">구체적으로는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-130">Specifically:</span></span>  
  
- <span data-ttu-id="0dc9c-131">애플리케이션이 32비트 컴퓨터에서 실행되는데 64비트 플랫폼을 대상으로 지정하는 경우에는 오류 메시지가 훨씬 더 일찍 표시되며, 이 스위치를 사용하지 않아 발생하는 오류보다는 문제 자체에 대한 내용이 중점적으로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-131">If you decide to target a 64-bit platform, and the application is run on a 32-bit machine, the error message comes much earlier and is more targeted at the problem than the error that occurs without using this switch.</span></span>  
  
- <span data-ttu-id="0dc9c-132">옵션에 대해 `x86` 플래그를 설정한 후 애플리케이션을 64비트 컴퓨터에서 실행하면 애플리케이션이 기본적으로 실행되지 않고 WOW 하위 시스템에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-132">If you set the `x86` flag on the option and the application is subsequently run on a 64-bit machine, the application will run in the WOW subsystem instead of running natively.</span></span>  
  
 <span data-ttu-id="0dc9c-133">64비트 Windows 운영 체제:</span><span class="sxs-lookup"><span data-stu-id="0dc9c-133">On a 64-bit Windows operating system:</span></span>  
  
- <span data-ttu-id="0dc9c-134">`-platform:x86`으로 컴파일된 어셈블리는 WOW64에서 실행되는 32비트 CLR에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-134">Assemblies compiled with `-platform:x86` will execute on the 32-bit CLR running under WOW64.</span></span>  
  
- <span data-ttu-id="0dc9c-135">`-platform:anycpu`로 컴파일된 실행 파일은 64비트 CLR에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-135">Executables compiled with the `-platform:anycpu` will execute on the 64-bit CLR.</span></span>  
  
- <span data-ttu-id="0dc9c-136">`-platform:anycpu`로 컴파일된 DLL은 이 DLL이 로드된 프로세스와 동일한 CLR에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-136">A DLL compiled with the `-platform:anycpu` will execute on the same CLR as the process into which it loaded.</span></span>  
  
- <span data-ttu-id="0dc9c-137">`-platform:anycpu32bitpreferred`로 컴파일된 실행 파일은 32비트 CLR에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-137">Executables that are compiled with `-platform:anycpu32bitpreferred` will execute on the 32-bit CLR.</span></span>  
  
 <span data-ttu-id="0dc9c-138">64비트 버전의 Windows에서 실행되도록 애플리케이션을 개발하는 방법에 대한 자세한 내용은 [64비트 애플리케이션](../../../framework/64-bit-apps.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-138">For more information about how to develop an application to run on a 64-bit version of Windows, see [64-bit Applications](../../../framework/64-bit-apps.md).</span></span>  
  
### <a name="to-set--platform-in-the-visual-studio-ide"></a><span data-ttu-id="0dc9c-139">Visual Studio IDE에서 -platform을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="0dc9c-139">To set -platform in the Visual Studio IDE</span></span>  
  
1. <span data-ttu-id="0dc9c-140">**솔루션 탐색기** 에서 프로젝트를 선택하고 **프로젝트** 메뉴를 연 다음 **속성** 을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-140">In **Solution Explorer**, choose the project, open the **Project** menu, and then click **Properties**.</span></span>  
  
2. <span data-ttu-id="0dc9c-141">**컴파일** 탭에서 **32비트 선호** 확인란을 선택하거나 선택을 취소합니다. 또는 **대상 CPU** 목록에서 값을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-141">On the **Compile** tab, select or clear the **Prefer 32-bit** check box, or, in the **Target CPU** list, choose a value.</span></span>  
  
     <span data-ttu-id="0dc9c-142">자세한 내용은 [컴파일 페이지, 프로젝트 디자이너(Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-142">For more information, see [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dc9c-143">예제</span><span class="sxs-lookup"><span data-stu-id="0dc9c-143">Example</span></span>  

 <span data-ttu-id="0dc9c-144">다음 예제에서는 `-platform` 컴파일러 옵션을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0dc9c-144">The following example illustrates how to use the `-platform` compiler option.</span></span>  
  
```console
vbc -platform:x86 myFile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dc9c-145">참조</span><span class="sxs-lookup"><span data-stu-id="0dc9c-145">See also</span></span>

- [<span data-ttu-id="0dc9c-146">-target(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0dc9c-146">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="0dc9c-147">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="0dc9c-147">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0dc9c-148">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="0dc9c-148">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
