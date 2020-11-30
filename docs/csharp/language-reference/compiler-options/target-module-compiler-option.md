---
description: -target:module(C# 컴파일러 옵션)
title: -target:module(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- /target:module
helpviewer_keywords:
- -target compiler options [C#], /target:module
- target compiler options [C#], /target:module
- /target compiler options [C#], /target:module
ms.assetid: 9af1e4fa-c749-44e7-ae58-90a3d05d4e72
ms.openlocfilehash: d8691e5e4477dbbe989344469b44382d5e0e7c8b
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91193610"
---
# <a name="-targetmodule-c-compiler-options"></a><span data-ttu-id="beff6-103">-target:module(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="beff6-103">-target:module (C# Compiler Options)</span></span>

<span data-ttu-id="beff6-104">이 옵션은 컴파일러에서 어셈블리 매니페스트를 생성하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-104">This option causes the compiler to not generate an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beff6-105">구문</span><span class="sxs-lookup"><span data-stu-id="beff6-105">Syntax</span></span>  
  
```console  
-target:module  
```  
  
## <a name="remarks"></a><span data-ttu-id="beff6-106">설명</span><span class="sxs-lookup"><span data-stu-id="beff6-106">Remarks</span></span>  

 <span data-ttu-id="beff6-107">기본적으로 이 옵션으로 컴파일하여 생성되는 출력 파일의 확장명은 .netmodule입니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-107">By default, the output file created by compiling with this option will have an extension of .netmodule.</span></span>  
  
 <span data-ttu-id="beff6-108">어셈블리 매니페스트가 없는 파일은 .NET 런타임에서 로드할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-108">A file that does not have an assembly manifest cannot be loaded by the .NET runtime.</span></span> <span data-ttu-id="beff6-109">그러나 이러한 파일은 [-addmodule](./addmodule-compiler-option.md)을 통해 어셈블리의 어셈블리 매니페스트에 통합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-109">However, such a file can be incorporated into the assembly manifest of an assembly by means of [-addmodule](./addmodule-compiler-option.md).</span></span>  
  
 <span data-ttu-id="beff6-110">둘 이상의 모듈이 단일 컴파일에서 생성될 경우 한 모듈의 [내부](../keywords/internal.md) 형식을 컴파일에 포함된 다른 모듈에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-110">If more than one module is created in a single compilation, [internal](../keywords/internal.md) types in one module will be available to other modules in the compilation.</span></span> <span data-ttu-id="beff6-111">한 모듈의 코드가 다른 모듈의 `internal` 형식을 참조하는 경우 **-addmodule** 을 통해 두 모듈을 모두 어셈블리 매니페스트에 통합해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-111">When code in one module references `internal` types in another module, then both modules must be incorporated into an assembly manifest, by means of **-addmodule**.</span></span>  
  
 <span data-ttu-id="beff6-112">Visual Studio 개발 환경에서는 모듈을 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-112">Creating a module is not supported in the Visual Studio development environment.</span></span>  
  
 <span data-ttu-id="beff6-113">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.ProjectProperties3.OutputType%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="beff6-113">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beff6-114">예제</span><span class="sxs-lookup"><span data-stu-id="beff6-114">Example</span></span>  

 <span data-ttu-id="beff6-115">`in.cs`를 컴파일하고 `in.netmodule`을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="beff6-115">Compile `in.cs`, creating `in.netmodule`:</span></span>  
  
```console  
csc -target:module in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="beff6-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="beff6-116">See also</span></span>

- [<span data-ttu-id="beff6-117">-target(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="beff6-117">-target (C# Compiler Options)</span></span>](./target-compiler-option.md)
- [<span data-ttu-id="beff6-118">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="beff6-118">C# Compiler Options</span></span>](./index.md)
