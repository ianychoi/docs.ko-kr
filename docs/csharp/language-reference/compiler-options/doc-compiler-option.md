---
description: /doc(C# 컴파일러 옵션)
title: /doc(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- FileProperties.BuildAction
- /doc
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
ms.openlocfilehash: b1d7fbbe98aaad16454fdd71c161f2a17a2f4f2e
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173258"
---
# <a name="-doc-c-compiler-options"></a><span data-ttu-id="571a3-103">/doc(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="571a3-103">-doc (C# Compiler Options)</span></span>

<span data-ttu-id="571a3-104">**-doc** 옵션을 사용하면 XML 파일에 문서 주석을 삽입할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-104">The **-doc** option allows you to place documentation comments in an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="571a3-105">구문</span><span class="sxs-lookup"><span data-stu-id="571a3-105">Syntax</span></span>  
  
```console  
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="571a3-106">인수</span><span class="sxs-lookup"><span data-stu-id="571a3-106">Arguments</span></span>  

 `file`  
 <span data-ttu-id="571a3-107">XML에 대한 출력 파일로, 컴파일의 소스 코드 파일에 있는 주석으로 채워집니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-107">The output file for XML, which is populated with the comments in the source code files of the compilation.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="571a3-108">설명</span><span class="sxs-lookup"><span data-stu-id="571a3-108">Remarks</span></span>  

 <span data-ttu-id="571a3-109">소스 코드 파일에서 다음 항목 앞에 나오는 문서 주석을 처리하여 XML 파일에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-109">In source code files, documentation comments that precede the following can be processed and added to the XML file:</span></span>  
  
- <span data-ttu-id="571a3-110">[class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type) 또는 [interface](../keywords/interface.md) 같은 사용자 정의 형식</span><span class="sxs-lookup"><span data-stu-id="571a3-110">Such user-defined types as a [class](../keywords/class.md), [delegate](../builtin-types/reference-types.md#the-delegate-type), or [interface](../keywords/interface.md)</span></span>  
  
- <span data-ttu-id="571a3-111">필드, [이벤트](../keywords/event.md), [속성](../../programming-guide/classes-and-structs/using-properties.md) 또는 메서드 같은 멤버</span><span class="sxs-lookup"><span data-stu-id="571a3-111">Such members as a field, [event](../keywords/event.md), [property](../../programming-guide/classes-and-structs/using-properties.md), or method</span></span>  
  
 <span data-ttu-id="571a3-112">Main을 포함하는 소스 코드 파일이 먼저 XML로 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-112">The source code file that contains Main is output first into the XML.</span></span>  
  
 <span data-ttu-id="571a3-113">[IntelliSense](/visualstudio/ide/using-intellisense) 기능에서 사용하기 위해 생성된 .xml 파일을 사용하려면 .xml 파일의 이름을 지원하려는 어셈블리와 동일하게 지정한 다음 .xml 파일이 어셈블리와 동일한 디렉터리에 있도록 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-113">To use the generated .xml file for use with the [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the .xml file be the same as the assembly you want to support and then make sure the .xml file is in the same directory as the assembly.</span></span> <span data-ttu-id="571a3-114">따라서 어셈블리가 Visual Studio 프로젝트에서 참조되면 .xml 파일도 검색됩니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-114">Thus, when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="571a3-115">자세한 내용은 [코드 주석 제공](/visualstudio/ide/reference/generate-xml-documentation-comments)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="571a3-115">See [Supplying Code Comments](/visualstudio/ide/reference/generate-xml-documentation-comments) and for more information.</span></span>  
  
 <span data-ttu-id="571a3-116">[-target:module](./target-module-compiler-option.md)을 사용하여 컴파일하지 않으면 컴파일의 출력 파일에 대한 어셈블리 매니페스트를 포함하는 파일의 이름을 지정하는 \<assembly>\</assembly> 태그가 `file`에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-116">Unless you compile with [-target:module](./target-module-compiler-option.md), `file` will contain \<assembly>\</assembly> tags specifying the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="571a3-117">-doc 옵션은 모든 입력 파일에 적용됩니다. 또는 Progect Settings에서 설정한 경우 프로젝트의 모든 파일에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-117">The -doc option applies to all input files; or, if set in the Project Settings, all files in the project.</span></span> <span data-ttu-id="571a3-118">특정 파일 또는 코드 섹션에 대한 문서 주석 관련 경고를 사용하지 않으려면 [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md)을 사용하세요.</span><span class="sxs-lookup"><span data-stu-id="571a3-118">To disable warnings related to documentation comments for a specific file or section of code, use [#pragma warning](../preprocessor-directives/preprocessor-pragma-warning.md).</span></span>  
  
 <span data-ttu-id="571a3-119">코드의 주석에서 문서를 생성하는 방법은 [문서 주석에 대한 권장 태그](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="571a3-119">See [Recommended Tags for Documentation Comments](../../programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) for ways to generate documentation from comments in your code.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="571a3-120">Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="571a3-120">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="571a3-121">프로젝트 **속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-121">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="571a3-122">**빌드** 탭을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-122">Click the **Build** tab.</span></span>  
  
3. <span data-ttu-id="571a3-123">**XML 문서 파일** 속성을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="571a3-123">Modify the **XML documentation file** property.</span></span>  
  
 <span data-ttu-id="571a3-124">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="571a3-124">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="571a3-125">참고 항목</span><span class="sxs-lookup"><span data-stu-id="571a3-125">See also</span></span>

- [<span data-ttu-id="571a3-126">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="571a3-126">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="571a3-127">프로젝트 및 솔루션 속성 관리</span><span class="sxs-lookup"><span data-stu-id="571a3-127">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
