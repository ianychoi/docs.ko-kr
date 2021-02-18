---
description: '자세한 정보: -keycontainer'
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: d8b83162d9404eb2ce80e5e531457360b040f27d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436814"
---
# <a name="-keycontainer"></a><span data-ttu-id="188bc-103">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="188bc-103">-keycontainer</span></span>

<span data-ttu-id="188bc-104">어셈블리에 강력한 이름을 지정하는 키 쌍의 키 컨테이너 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-104">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="188bc-105">구문</span><span class="sxs-lookup"><span data-stu-id="188bc-105">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="188bc-106">인수</span><span class="sxs-lookup"><span data-stu-id="188bc-106">Arguments</span></span>  
  
|<span data-ttu-id="188bc-107">용어</span><span class="sxs-lookup"><span data-stu-id="188bc-107">Term</span></span>|<span data-ttu-id="188bc-108">정의</span><span class="sxs-lookup"><span data-stu-id="188bc-108">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="188bc-109">필수 요소.</span><span class="sxs-lookup"><span data-stu-id="188bc-109">Required.</span></span> <span data-ttu-id="188bc-110">키를 포함하는 컨테이너 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-110">Container file that contains the key.</span></span> <span data-ttu-id="188bc-111">파일 이름에 공백이 있으면 이름을 따옴표("")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-111">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="188bc-112">설명</span><span class="sxs-lookup"><span data-stu-id="188bc-112">Remarks</span></span>  

 <span data-ttu-id="188bc-113">컴파일러는 공개 키를 어셈블리 매니페스트에 삽입하고 최종 어셈블리를 프라이빗 키로 서명하여 공유 가능한 구성 요소를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-113">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="188bc-114">키 파일을 생성하려면 명령줄에 `sn -k file`을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-114">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="188bc-115">`-i` 옵션은 컨테이너에 키 쌍을 설치합니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-115">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="188bc-116">자세한 내용은 [Sn.exe(강력한 이름 도구)](../../../framework/tools/sn-exe-strong-name-tool.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="188bc-116">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="188bc-117">`-target:module`로 컴파일하는 경우 키 파일의 이름이 모듈에 저장되고, [-addmodule](addmodule.md)을 사용하여 어셈블리를 컴파일할 때 생성되는 어셈블리에 통합됩니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-117">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="188bc-118">MSIL(Microsoft Intermediate Language) 모듈의 소스 코드에서 이 옵션을 사용자 지정 특성(<xref:System.Reflection.AssemblyKeyNameAttribute>)으로 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-118">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="188bc-119">[-keyfile](keyfile.md)을 사용하여 암호화 정보를 컴파일러에 전달할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-119">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="188bc-120">부분 서명된 어셈블리가 필요한 경우 [-delaysign](delaysign.md)을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-120">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="188bc-121">어셈블리 서명에 대한 자세한 내용은 [강력한 이름의 어셈블리 만들기 및 사용](../../../standard/assembly/create-use-strong-named.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="188bc-121">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="188bc-122">Visual Studio 개발 환경 내에서는 `-keycontainer` 옵션을 사용할 수 없습니다. 명령줄에서 컴파일하는 경우에만 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-122">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="188bc-123">예제</span><span class="sxs-lookup"><span data-stu-id="188bc-123">Example</span></span>  

 <span data-ttu-id="188bc-124">다음 코드는 소스 파일 `Input.vb`를 컴파일하고 키 컨테이너를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="188bc-124">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="188bc-125">참조</span><span class="sxs-lookup"><span data-stu-id="188bc-125">See also</span></span>

- [<span data-ttu-id="188bc-126">.NET 어셈블리</span><span class="sxs-lookup"><span data-stu-id="188bc-126">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="188bc-127">Visual Basic 명령줄 컴파일러</span><span class="sxs-lookup"><span data-stu-id="188bc-127">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="188bc-128">-keyfile</span><span class="sxs-lookup"><span data-stu-id="188bc-128">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="188bc-129">샘플 컴파일 명령줄</span><span class="sxs-lookup"><span data-stu-id="188bc-129">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
