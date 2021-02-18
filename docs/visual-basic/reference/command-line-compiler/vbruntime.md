---
description: '자세한 정보: -vbruntime'
title: -vbruntime
ms.date: 03/13/2018
f1_keywords:
- vbruntime
- -vbruntime
helpviewer_keywords:
- vbruntime compiler option [Visual Basic]
- -vbruntime compiler option [Visual Basic]
- /vbruntime compiler option [Visual Basic]
ms.assetid: 1aa0239e-511a-4c29-957d-fd72877b350a
ms.openlocfilehash: d542324e64ce31224aa75f164f121898a25f7be9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100470151"
---
# <a name="-vbruntime"></a><span data-ttu-id="0cdb5-103">-vbruntime</span><span class="sxs-lookup"><span data-stu-id="0cdb5-103">-vbruntime</span></span>

<span data-ttu-id="0cdb5-104">컴파일러에서 Visual Basic 런타임 라이브러리에 대한 참조 없이 컴파일하거나 특정 런타임 라이브러리를 참조하여 컴파일하도록 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-104">Specifies that the compiler should compile without a reference to the Visual Basic Runtime Library, or with a reference to a specific runtime library.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cdb5-105">구문</span><span class="sxs-lookup"><span data-stu-id="0cdb5-105">Syntax</span></span>  
  
```console  
-vbruntime:{ - | + | * | path }  
```  
  
## <a name="arguments"></a><span data-ttu-id="0cdb5-106">인수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-106">Arguments</span></span>  

 \-  
 <span data-ttu-id="0cdb5-107">Visual Basic 런타임 라이브러리에 대한 참조 없이 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-107">Compile without a reference to the Visual Basic Runtime Library.</span></span>  
  
 \+  
 <span data-ttu-id="0cdb5-108">기본 Visual Basic 런타임 라이브러리에 대한 참조로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-108">Compile with a reference to the default Visual Basic Runtime Library.</span></span>  
  
 \*  
 <span data-ttu-id="0cdb5-109">Visual Basic 런타임 라이브러리에 대한 참조 없이 컴파일하고 Visual Basic 런타임 라이브러리의 핵심 기능을 어셈블리에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-109">Compile without a reference to the Visual Basic Runtime Library, and embed core functionality from the Visual Basic Runtime Library into the assembly.</span></span>  
  
 `path`  
 <span data-ttu-id="0cdb5-110">지정된 라이브러리(DLL)에 대한 참조로 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-110">Compile with a reference to the specified library (DLL).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cdb5-111">설명</span><span class="sxs-lookup"><span data-stu-id="0cdb5-111">Remarks</span></span>  

 <span data-ttu-id="0cdb5-112">`-vbruntime` 컴파일러 옵션을 사용하면 컴파일러가 Visual Basic 런타임 라이브러리에 대한 참조 없이 컴파일하도록 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-112">The `-vbruntime` compiler option enables you to specify that the compiler should compile without a reference to the Visual Basic Runtime Library.</span></span> <span data-ttu-id="0cdb5-113">Visual Basic 런타임 라이브러리에 대한 참조 없이 컴파일하는 경우 Visual Basic 런타임 도우미에 대한 호출을 생성하는 코드 또는 언어 구문에 오류 또는 경고가 기록됩니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-113">If you compile without a reference to the Visual Basic Runtime Library, errors or warnings are logged on code or language constructs that generate a call to a Visual Basic runtime helper.</span></span> <span data-ttu-id="0cdb5-114">(*Visual Basic 런타임 도우미* 는 특정 언어 의미 체계를 실행하기 위해 런타임에 호출되는 Microsoft.VisualBasic.dll에 정의된 함수입니다.)</span><span class="sxs-lookup"><span data-stu-id="0cdb5-114">(A *Visual Basic runtime helper* is a function defined in Microsoft.VisualBasic.dll that is called at runtime to execute a specific language semantic.)</span></span>  
  
 <span data-ttu-id="0cdb5-115">`-vbruntime+` 옵션은 `-vbruntime` 스위치가 지정되지 않은 경우에 발생하는 것과 동일한 동작을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-115">The `-vbruntime+` option produces the same behavior that occurs if no `-vbruntime` switch is specified.</span></span> <span data-ttu-id="0cdb5-116">`-vbruntime+` 옵션을 사용하여 이전 `-vbruntime` 스위치를 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-116">You can use the `-vbruntime+` option to override previous `-vbruntime` switches.</span></span>  
  
 <span data-ttu-id="0cdb5-117">`-vbruntime-` 또는 `-vbruntime:path` 옵션을 사용하면 `My` 형식의 대부분의 개체를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-117">Most objects of the `My` type are unavailable when you use the `-vbruntime-` or `-vbruntime:path` options.</span></span>  
  
## <a name="embedding-visual-basic-runtime-core-functionality"></a><span data-ttu-id="0cdb5-118">Visual Basic 런타임 핵심 기능 포함</span><span class="sxs-lookup"><span data-stu-id="0cdb5-118">Embedding Visual Basic Runtime core functionality</span></span>  

 <span data-ttu-id="0cdb5-119">`-vbruntime*` 옵션을 사용하면 런타임 라이브러리에 대한 참조 없이 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-119">The `-vbruntime*` option enables you to compile without a reference to a runtime library.</span></span> <span data-ttu-id="0cdb5-120">대신 Visual Basic 런타임 라이브러리의 핵심 기능이 사용자 어셈블리에 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-120">Instead, core functionality from the Visual Basic Runtime Library is embedded in the user assembly.</span></span> <span data-ttu-id="0cdb5-121">Visual Basic 런타임을 포함하지 않는 플랫폼에서 애플리케이션을 실행하는 경우 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-121">You can use this option if your application runs on platforms that do not contain the Visual Basic runtime.</span></span>  
  
 <span data-ttu-id="0cdb5-122">다음 런타임 멤버가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-122">The following runtime members are embedded:</span></span>  
  
- <span data-ttu-id="0cdb5-123"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> 클래스</span><span class="sxs-lookup"><span data-stu-id="0cdb5-123"><xref:Microsoft.VisualBasic.CompilerServices.Conversions> class</span></span>  
  
- <span data-ttu-id="0cdb5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> 메서드</span><span class="sxs-lookup"><span data-stu-id="0cdb5-124"><xref:Microsoft.VisualBasic.Strings.AscW%28System.Char%29> method</span></span>  
  
- <span data-ttu-id="0cdb5-125"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> 메서드</span><span class="sxs-lookup"><span data-stu-id="0cdb5-125"><xref:Microsoft.VisualBasic.Strings.AscW%28System.String%29> method</span></span>  
  
- <span data-ttu-id="0cdb5-126"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> 메서드</span><span class="sxs-lookup"><span data-stu-id="0cdb5-126"><xref:Microsoft.VisualBasic.Strings.ChrW%28System.Int32%29> method</span></span>  
  
- <span data-ttu-id="0cdb5-127"><xref:Microsoft.VisualBasic.Constants.vbBack> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-127"><xref:Microsoft.VisualBasic.Constants.vbBack> constant</span></span>  
  
- <span data-ttu-id="0cdb5-128"><xref:Microsoft.VisualBasic.Constants.vbCr> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-128"><xref:Microsoft.VisualBasic.Constants.vbCr> constant</span></span>  
  
- <span data-ttu-id="0cdb5-129"><xref:Microsoft.VisualBasic.Constants.vbCrLf> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-129"><xref:Microsoft.VisualBasic.Constants.vbCrLf> constant</span></span>  
  
- <span data-ttu-id="0cdb5-130"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-130"><xref:Microsoft.VisualBasic.Constants.vbFormFeed> constant</span></span>  
  
- <span data-ttu-id="0cdb5-131"><xref:Microsoft.VisualBasic.Constants.vbLf> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-131"><xref:Microsoft.VisualBasic.Constants.vbLf> constant</span></span>  
  
- <span data-ttu-id="0cdb5-132"><xref:Microsoft.VisualBasic.Constants.vbNewLine> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-132"><xref:Microsoft.VisualBasic.Constants.vbNewLine> constant</span></span>  
  
- <span data-ttu-id="0cdb5-133"><xref:Microsoft.VisualBasic.Constants.vbNullChar> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-133"><xref:Microsoft.VisualBasic.Constants.vbNullChar> constant</span></span>  
  
- <span data-ttu-id="0cdb5-134"><xref:Microsoft.VisualBasic.Constants.vbNullString> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-134"><xref:Microsoft.VisualBasic.Constants.vbNullString> constant</span></span>  
  
- <span data-ttu-id="0cdb5-135"><xref:Microsoft.VisualBasic.Constants.vbTab> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-135"><xref:Microsoft.VisualBasic.Constants.vbTab> constant</span></span>  
  
- <span data-ttu-id="0cdb5-136"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> 상수</span><span class="sxs-lookup"><span data-stu-id="0cdb5-136"><xref:Microsoft.VisualBasic.Constants.vbVerticalTab> constant</span></span>  
  
- <span data-ttu-id="0cdb5-137">`My` 형식의 일부 개체</span><span class="sxs-lookup"><span data-stu-id="0cdb5-137">Some objects of the `My` type</span></span>  
  
 <span data-ttu-id="0cdb5-138">`-vbruntime*` 옵션을 사용하여 컴파일하고 코드가 핵심 기능에 포함되지 않은 Visual Basic 런타임 라이브러리의 멤버를 참조하는 경우 컴파일러에서 해당 멤버를 사용할 수 없음을 나타내는 오류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-138">If you compile using the `-vbruntime*` option and your code references a member from the Visual Basic Runtime Library that is not embedded with the core functionality, the compiler returns an error that indicates that the member is not available.</span></span>  
  
## <a name="referencing-a-specified-library"></a><span data-ttu-id="0cdb5-139">지정된 라이브러리 참조</span><span class="sxs-lookup"><span data-stu-id="0cdb5-139">Referencing a specified library</span></span>  

 <span data-ttu-id="0cdb5-140">`path` 인수를 사용하여 기본 Visual Basic 런타임 라이브러리 대신 사용자 지정 런타임 라이브러리에 대한 참조로 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-140">You can use the `path` argument to compile with a reference to a custom runtime library instead of the default Visual Basic Runtime Library.</span></span>  
  
 <span data-ttu-id="0cdb5-141">`path` 인수의 값이 DLL에 대해 정규화된 경로인 경우 컴파일러는 해당 파일을 런타임 라이브러리로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-141">If the value for the `path` argument is a fully qualified path to a DLL, the compiler will use that file as the runtime library.</span></span> <span data-ttu-id="0cdb5-142">`path` 인수의 값이 DLL에 대해 정규화된 경로가 아닌 경우 Visual Basic 컴파일러는 먼저 현재 폴더에서 식별된 DLL을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-142">If the value for the `path` argument is not a fully qualified path to a DLL, the Visual Basic compiler will search for the identified DLL in the current folder first.</span></span> <span data-ttu-id="0cdb5-143">그런 다음, [-sdkpath](sdkpath.md) 컴파일러 옵션을 사용하여 지정한 경로를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-143">It will then search in the path that you have specified by using the [-sdkpath](sdkpath.md) compiler option.</span></span> <span data-ttu-id="0cdb5-144">`-sdkpath` 컴파일러 옵션을 사용하지 않으면 컴파일러는 .NET Framework 폴더(`%systemroot%\Microsoft.NET\Framework\versionNumber`)에서 식별된 DLL을 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-144">If the `-sdkpath` compiler option is not used, the compiler will search for the identified DLL in the .NET Framework folder (`%systemroot%\Microsoft.NET\Framework\versionNumber`).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cdb5-145">예제</span><span class="sxs-lookup"><span data-stu-id="0cdb5-145">Example</span></span>  

 <span data-ttu-id="0cdb5-146">다음 예제에서는 `-vbruntime` 옵션을 사용하여 사용자 지정 라이브러리에 대한 참조로 컴파일하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="0cdb5-146">The following example shows how to use the `-vbruntime` option to compile with a reference to a custom library.</span></span>  
  
```console
vbc -vbruntime:C:\VBLibraries\CustomVBLibrary.dll  
```  
  
## <a name="see-also"></a><span data-ttu-id="0cdb5-147">참조</span><span class="sxs-lookup"><span data-stu-id="0cdb5-147">See also</span></span>

- [<span data-ttu-id="0cdb5-148">Visual Basic Core – Visual Studio 2010 SP1의 새로운 컴파일 모드</span><span class="sxs-lookup"><span data-stu-id="0cdb5-148">Visual Basic Core – New compilation mode in Visual Studio 2010 SP1</span></span>](https://devblogs.microsoft.com/vbteam/vb-core-new-compilation-mode-in-visual-studio-2010-sp1/)
- [<span data-ttu-id="0cdb5-149">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="0cdb5-149">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="0cdb5-150">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="0cdb5-150">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="0cdb5-151">-sdkpath</span><span class="sxs-lookup"><span data-stu-id="0cdb5-151">-sdkpath</span></span>](sdkpath.md)
