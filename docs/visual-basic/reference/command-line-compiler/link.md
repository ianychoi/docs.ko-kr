---
description: '자세한 정보: -link(Visual Basic)'
title: -link
ms.date: 03/10/2018
helpviewer_keywords:
- l compiler option [Visual Basic]
- EmbedInteropTypes
- embed interop types [COM Interop]
- -link compiler option [Visual Basic]
- /link compiler option [Visual Basic]
- link compiler option [Visual Basic]
- -l compiler option [Visual Basic]
- /l compiler option [Visual Basic]
ms.assetid: 1885f24a-86f5-486c-a064-9fb7e455ccec
ms.openlocfilehash: 31d98d2c0fb0cbd8e8baff82869501a7ff0ea270
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475138"
---
# <a name="-link-visual-basic"></a><span data-ttu-id="7b242-103">-link(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b242-103">-link (Visual Basic)</span></span>

<span data-ttu-id="7b242-104">컴파일러에서 지정된 어셈블리의 COM 형식 정보를 현재 컴파일하고 있는 프로젝트에 사용할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-104">Causes the compiler to make COM type information in the specified assemblies available to the project that you are currently compiling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b242-105">구문</span><span class="sxs-lookup"><span data-stu-id="7b242-105">Syntax</span></span>  
  
```console  
-link:fileList  
```

<span data-ttu-id="7b242-106">또는</span><span class="sxs-lookup"><span data-stu-id="7b242-106">or</span></span>  

```console
-l:fileList  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b242-107">인수</span><span class="sxs-lookup"><span data-stu-id="7b242-107">Arguments</span></span>  
  
|<span data-ttu-id="7b242-108">용어</span><span class="sxs-lookup"><span data-stu-id="7b242-108">Term</span></span>|<span data-ttu-id="7b242-109">정의</span><span class="sxs-lookup"><span data-stu-id="7b242-109">Definition</span></span>|  
|---|---|  
|`fileList`|<span data-ttu-id="7b242-110">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="7b242-110">Required.</span></span> <span data-ttu-id="7b242-111">쉼표로 구분된 어셈블리 파일 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-111">Comma-delimited list of assembly file names.</span></span> <span data-ttu-id="7b242-112">파일 이름에 공백이 있으면 이름을 따옴표로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-112">If the file name contains a space, enclose the name in quotation marks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b242-113">설명</span><span class="sxs-lookup"><span data-stu-id="7b242-113">Remarks</span></span>  

 <span data-ttu-id="7b242-114">`-link` 옵션을 사용하면 포함된 형식 정보가 있는 애플리케이션을 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-114">The `-link` option enables you to deploy an application that has embedded type information.</span></span> <span data-ttu-id="7b242-115">그러면 애플리케이션은 런타임 어셈블리에 대한 참조를 요구하지 않고 포함된 형식 정보를 구현하는 형식을 런타임 어셈블리에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-115">The application can then use types in a runtime assembly that implement the embedded type information without requiring a reference to the runtime assembly.</span></span> <span data-ttu-id="7b242-116">다양한 버전의 런타임 어셈블리가 게시된 경우 포함된 형식 정보를 포함하는 애플리케이션은 다시 컴파일하지 않아도 다양한 버전에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-116">If various versions of the runtime assembly are published, the application that contains the embedded type information can work with the various versions without having to be recompiled.</span></span> <span data-ttu-id="7b242-117">예제를 보려면 [연습: 관리되는 어셈블리의 형식 포함](../../../standard/assembly/embed-types-visual-studio.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7b242-117">For an example, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>  
  
 <span data-ttu-id="7b242-118">`-link` 옵션을 사용하면 COM interop를 사용하여 작업할 때 특히 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-118">Using the `-link` option is especially useful when you are working with COM interop.</span></span> <span data-ttu-id="7b242-119">애플리케이션에 대상 컴퓨터의 PIA(주 interop 어셈블리)가 더 이상 필요하지 않도록 COM 형식을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-119">You can embed COM types so that your application no longer requires a primary interop assembly (PIA) on the target computer.</span></span> <span data-ttu-id="7b242-120">`-link` 옵션은 참조된 interop 어셈블리의 COM 형식 정보를 컴파일된 결과 코드에 포함하도록 컴파일러에 지시합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-120">The `-link` option instructs the compiler to embed the COM type information from the referenced interop assembly into the resulting compiled code.</span></span> <span data-ttu-id="7b242-121">COM 형식은 CLSID(GUID) 값으로 식별됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-121">The COM type is identified by the CLSID (GUID) value.</span></span> <span data-ttu-id="7b242-122">따라서 동일한 CLSID 값을 갖는 동일한 COM 형식이 설치된 대상 컴퓨터에서 애플리케이션을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-122">As a result, your application can run on a target computer that has installed the same COM types with the same CLSID values.</span></span> <span data-ttu-id="7b242-123">Microsoft Office를 자동화하는 애플리케이션이 좋은 예입니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-123">Applications that automate Microsoft Office are a good example.</span></span> <span data-ttu-id="7b242-124">Office와 같은 애플리케이션은 일반적으로 여러 버전에서 동일한 CLSID 값을 유지하지 때문에 .NET Framework 4 이상이 대상 컴퓨터에 설치되어 있고 애플리케이션이 참조된 COM 형식에 포함된 메서드, 속성 또는 이벤트를 사용하는 한 애플리케이션에서 참조된 COM 형식을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-124">Because applications like Office usually keep the same CLSID value across different versions, your application can use the referenced COM types as long as .NET Framework 4 or later is installed on the target computer and your application uses methods, properties, or events that are included in the referenced COM types.</span></span>  
  
 <span data-ttu-id="7b242-125">`-link` 옵션은 인터페이스, 구조체 및 대리자만 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-125">The `-link` option embeds only interfaces, structures, and delegates.</span></span> <span data-ttu-id="7b242-126">COM 클래스는 포함할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-126">Embedding COM classes is not supported.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b242-127">코드에서 포함된 COM 형식의 인스턴스를 만드는 경우 적절한 인터페이스를 사용하여 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-127">When you create an instance of an embedded COM type in your code, you must create the instance by using the appropriate interface.</span></span> <span data-ttu-id="7b242-128">CoClass를 사용하여 포함된 COM 형식의 인스턴스를 만들려고 하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-128">Attempting to create an instance of an embedded COM type by using the CoClass causes an error.</span></span>  
  
 <span data-ttu-id="7b242-129">Visual Studio에서 `-link` 옵션을 설정하려면 어셈블리 참조를 추가하고 `Embed Interop Types` 속성을 **true** 로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-129">To set the `-link` option in Visual Studio, add an assembly reference and set the `Embed Interop Types` property to **true**.</span></span> <span data-ttu-id="7b242-130">`Embed Interop Types` 속성의 기본값은 **false** 입니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-130">The default for the `Embed Interop Types` property is **false**.</span></span>  
  
 <span data-ttu-id="7b242-131">COM 어셈블리 자체가 또 다른 COM 어셈블리(어셈블리 B)를 참조하는 COM 어셈블리(어셈블리 A)에 연결하는 경우 다음 중 하나에 해당되면 어셈블리 B에도 연결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-131">If you link to a COM assembly (Assembly A) which itself references another COM assembly (Assembly B), you also have to link to Assembly B if either of the following is true:</span></span>  
  
- <span data-ttu-id="7b242-132">어셈블리 A의 형식은 형식에서 상속되거나 어셈블리 B의 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-132">A type from Assembly A inherits from a type or implements an interface from Assembly B.</span></span>  
  
- <span data-ttu-id="7b242-133">어셈블리 B의 반환 형식이나 매개 변수 형식을 사용하는 필드, 속성, 이벤트 또는 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-133">A field, property, event, or method that has a return type or parameter type from Assembly B is invoked.</span></span>  
  
 <span data-ttu-id="7b242-134">[-libpath](libpath.md)를 사용하여 하나 이상의 어셈블리 참조가 있는 디렉터리를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-134">Use [-libpath](libpath.md) to specify the directory in which one or more of your assembly references is located.</span></span>  
  
 <span data-ttu-id="7b242-135">[-reference](reference.md) 컴파일러 옵션과 마찬가지로 `-link` 컴파일러 옵션은 Vbc.rsp 지시 파일을 사용하며, 자주 사용되는 .NET Framework 어셈블리를 참조합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-135">Like the [-reference](reference.md) compiler option, the `-link` compiler option uses the Vbc.rsp response file, which references frequently used .NET Framework assemblies.</span></span> <span data-ttu-id="7b242-136">컴파일러에서 Vbc.rsp 파일을 사용하지 않도록 하려면 [-noconfig](noconfig.md) 컴파일러 옵션을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="7b242-136">Use the [-noconfig](noconfig.md) compiler option if you do not want the compiler to use the Vbc.rsp file.</span></span>  
  
 <span data-ttu-id="7b242-137">`-link`의 약식은 `-l`입니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-137">The short form of `-link` is `-l`.</span></span>  
  
## <a name="generics-and-embedded-types"></a><span data-ttu-id="7b242-138">제네릭 및 포함된 형식</span><span class="sxs-lookup"><span data-stu-id="7b242-138">Generics and Embedded Types</span></span>  

 <span data-ttu-id="7b242-139">다음 섹션에서는 interop 형식을 포함하는 애플리케이션에서 제네릭 형식을 사용할 경우의 제한 사항에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-139">The following sections describe the limitations on using generic types in applications that embed interop types.</span></span>  
  
### <a name="generic-interfaces"></a><span data-ttu-id="7b242-140">제네릭 인터페이스</span><span class="sxs-lookup"><span data-stu-id="7b242-140">Generic Interfaces</span></span>  

 <span data-ttu-id="7b242-141">interop 어셈블리에서 포함되는 제네릭 인터페이스는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-141">Generic interfaces that are embedded from an interop assembly cannot be used.</span></span> <span data-ttu-id="7b242-142">다음 예제에서 이를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-142">This is shown in the following example.</span></span>  
  
 [!code-vb[VbLinkCompiler#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#1)]  
  
### <a name="types-that-have-generic-parameters"></a><span data-ttu-id="7b242-143">제네릭 매개 변수가 있는 형식</span><span class="sxs-lookup"><span data-stu-id="7b242-143">Types That Have Generic Parameters</span></span>  

 <span data-ttu-id="7b242-144">형식이 interop 어셈블리에서 포함된 제네릭 매개 변수가 있는 형식은 해당 형식이 외부 어셈블리에서 제공된 경우 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-144">Types that have a generic parameter whose type is embedded from an interop assembly cannot be used if that type is from an external assembly.</span></span> <span data-ttu-id="7b242-145">인터페이스에는 이 제한이 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-145">This restriction does not apply to interfaces.</span></span> <span data-ttu-id="7b242-146">예를 들어 <xref:Microsoft.Office.Interop.Excel> 어셈블리에 정의된 <xref:Microsoft.Office.Interop.Excel.Range> 인터페이스를 살펴보세요.</span><span class="sxs-lookup"><span data-stu-id="7b242-146">For example, consider the <xref:Microsoft.Office.Interop.Excel.Range> interface that is defined in the <xref:Microsoft.Office.Interop.Excel> assembly.</span></span> <span data-ttu-id="7b242-147">다음 코드 예제와 같이 라이브러리가 <xref:Microsoft.Office.Interop.Excel> 어셈블리의 interop 형식을 포함하고 형식이 <xref:Microsoft.Office.Interop.Excel.Range> 인터페이스인 매개 변수가 있는 제네릭 형식을 반환하는 메서드를 노출하는 경우 해당 메서드는 제네릭 인터페이스를 반환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-147">If a library embeds interop types from the <xref:Microsoft.Office.Interop.Excel> assembly and exposes a method that returns a generic type that has a parameter whose type is the <xref:Microsoft.Office.Interop.Excel.Range> interface, that method must return a generic interface, as shown in the following code example.</span></span>  
  
 [!code-vb[VbLinkCompiler#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#2)]  
[!code-vb[VbLinkCompiler#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#3)]  
[!code-vb[VbLinkCompiler#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/utility.vb#4)]  
  
 <span data-ttu-id="7b242-148">다음 예제에서 클라이언트 코드는 <xref:System.Collections.IList> 제네릭 인터페이스를 반환하는 메서드를 오류 없이 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-148">In the following example, client code can call the method that returns the <xref:System.Collections.IList> generic interface without error.</span></span>  
  
 [!code-vb[VbLinkCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vblinkcompiler/vb/module1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="7b242-149">예제</span><span class="sxs-lookup"><span data-stu-id="7b242-149">Example</span></span>  

 <span data-ttu-id="7b242-150">다음 명령줄은 원본 파일 `OfficeApp.vb`와 `COMData1.dll` 및 `COMData2.dll`의 참조 어셈블리를 컴파일하여 `OfficeApp.exe`를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="7b242-150">The following command line compiles source file `OfficeApp.vb` and reference assemblies from `COMData1.dll` and `COMData2.dll` to produce `OfficeApp.exe`.</span></span>  
  
```console  
vbc -link:COMData1.dll,COMData2.dll -out:OfficeApp.exe OfficeApp.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b242-151">참조</span><span class="sxs-lookup"><span data-stu-id="7b242-151">See also</span></span>

- [<span data-ttu-id="7b242-152">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="7b242-152">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="7b242-153">연습: 관리되는 어셈블리의 형식 포함</span><span class="sxs-lookup"><span data-stu-id="7b242-153">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../standard/assembly/embed-types-visual-studio.md)
- [<span data-ttu-id="7b242-154">-reference(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7b242-154">-reference (Visual Basic)</span></span>](reference.md)
- [<span data-ttu-id="7b242-155">-noconfig</span><span class="sxs-lookup"><span data-stu-id="7b242-155">-noconfig</span></span>](noconfig.md)
- [<span data-ttu-id="7b242-156">-libpath</span><span class="sxs-lookup"><span data-stu-id="7b242-156">-libpath</span></span>](libpath.md)
- [<span data-ttu-id="7b242-157">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="7b242-157">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- [<span data-ttu-id="7b242-158">COM Interop 소개</span><span class="sxs-lookup"><span data-stu-id="7b242-158">Introduction to COM Interop</span></span>](../../programming-guide/com-interop/introduction-to-com-interop.md)
