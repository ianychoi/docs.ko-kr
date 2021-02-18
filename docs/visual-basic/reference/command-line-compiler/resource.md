---
description: '자세한 정보: -resource(Visual Basic)'
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: 830d89ab4f4063aa12d12a5206b76e49c5355708
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474111"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="136bd-103">-resource(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136bd-103">-resource (Visual Basic)</span></span>

<span data-ttu-id="136bd-104">관리되는 리소스를 어셈블리에 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-104">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="136bd-105">구문</span><span class="sxs-lookup"><span data-stu-id="136bd-105">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="136bd-106">또는</span><span class="sxs-lookup"><span data-stu-id="136bd-106">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="136bd-107">인수</span><span class="sxs-lookup"><span data-stu-id="136bd-107">Arguments</span></span>  
  
|<span data-ttu-id="136bd-108">용어</span><span class="sxs-lookup"><span data-stu-id="136bd-108">Term</span></span>|<span data-ttu-id="136bd-109">정의</span><span class="sxs-lookup"><span data-stu-id="136bd-109">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="136bd-110">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="136bd-110">Required.</span></span> <span data-ttu-id="136bd-111">출력 파일에 포함할 리소스 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-111">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="136bd-112">기본적으로 `filename`은 어셈블리에서 공용입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-112">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="136bd-113">공백이 있으면 파일 이름을 따옴표(" ")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-113">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="136bd-114">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-114">Optional.</span></span> <span data-ttu-id="136bd-115">리소스의 논리적 이름, 즉 리소스를 로드하는 데 사용되는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-115">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="136bd-116">기본값은 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-116">The default is the name of the file.</span></span> <span data-ttu-id="136bd-117">필요에 따라 다음과 같이 리소스를 어셈블리 매니페스트에서 공용 또는 전용으로 지정할 수 있습니다. `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="136bd-117">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="136bd-118">설명</span><span class="sxs-lookup"><span data-stu-id="136bd-118">Remarks</span></span>  

 <span data-ttu-id="136bd-119">리소스 파일을 출력 파일에 배치하지 않고 어셈블리에 리소스를 연결하려면 `-linkresource`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-119">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="136bd-120">예를 들어, `filename`이 [Resgen.exe(리소스 파일 생성기)](../../../framework/tools/resgen-exe-resource-file-generator.md)에 의해 또는 개발 환경에서 만들어진 .NET Framework 리소스 파일인 경우에는 <xref:System.Resources> 네임스페이스의 멤버를 사용하여 해당 파일에 액세스할 수 있습니다(자세한 내용은 <xref:System.Resources.ResourceManager> 참조).</span><span class="sxs-lookup"><span data-stu-id="136bd-120">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="136bd-121">런타임에 다른 모든 리소스에 액세스하려면 다음 메서드 중 하나를 사용합니다. <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> 또는 <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="136bd-121">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="136bd-122">`-resource`의 약식은 `-res`입니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-122">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="136bd-123">Visual Studio IDE에서 `-resource`를 설정하는 방법에 대한 자세한 내용은 [애플리케이션 리소스 관리(.NET)](/visualstudio/ide/managing-application-resources-dotnet)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="136bd-123">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="136bd-124">예제</span><span class="sxs-lookup"><span data-stu-id="136bd-124">Example</span></span>  

 <span data-ttu-id="136bd-125">다음 코드에서는 `In.vb`를 컴파일하고 리소스 파일 `Rf.resource`를 연결합니다.</span><span class="sxs-lookup"><span data-stu-id="136bd-125">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="136bd-126">참조</span><span class="sxs-lookup"><span data-stu-id="136bd-126">See also</span></span>

- [<span data-ttu-id="136bd-127">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="136bd-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="136bd-128">-win32resource</span><span class="sxs-lookup"><span data-stu-id="136bd-128">-win32resource</span></span>](win32resource.md)
- [<span data-ttu-id="136bd-129">-linkresource(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136bd-129">-linkresource (Visual Basic)</span></span>](linkresource.md)
- [<span data-ttu-id="136bd-130">-target(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="136bd-130">-target (Visual Basic)</span></span>](target.md)
- [<span data-ttu-id="136bd-131">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="136bd-131">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
