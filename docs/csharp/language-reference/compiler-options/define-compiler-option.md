---
description: -define(C# 컴파일러 옵션)
title: -define(C# 컴파일러 옵션)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 74c9a23cd1b3a691063c2976a593c9b3a63ca618
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91173271"
---
# <a name="-define-c-compiler-options"></a><span data-ttu-id="26958-103">-define(C# 컴파일러 옵션)</span><span class="sxs-lookup"><span data-stu-id="26958-103">-define (C# Compiler Options)</span></span>

<span data-ttu-id="26958-104">**-define** 옵션은 프로그램의 모든 소스 코드 파일에서 `name`을 기호로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-104">The **-define** option defines `name` as a symbol in all source code files your program.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26958-105">구문</span><span class="sxs-lookup"><span data-stu-id="26958-105">Syntax</span></span>  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="26958-106">인수</span><span class="sxs-lookup"><span data-stu-id="26958-106">Arguments</span></span>  

 <span data-ttu-id="26958-107">`name`, `name2`</span><span class="sxs-lookup"><span data-stu-id="26958-107">`name`, `name2`</span></span>  
 <span data-ttu-id="26958-108">정의하려는 하나 이상의 기호 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="26958-108">The name of one or more symbols that you want to define.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26958-109">설명</span><span class="sxs-lookup"><span data-stu-id="26958-109">Remarks</span></span>  

 <span data-ttu-id="26958-110">**-define** 옵션은 컴파일러 옵션이 프로젝트의 모든 파일에 적용된다는 점을 제외하고는 [#define](../preprocessor-directives/preprocessor-define.md) 전처리기 지시문을 사용하는 것과 효과가 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-110">The **-define** option has the same effect as using a [#define](../preprocessor-directives/preprocessor-define.md) preprocessor directive except that the compiler option is in effect for all files in the project.</span></span> <span data-ttu-id="26958-111">소스 파일의 [#undef](../preprocessor-directives/preprocessor-undef.md) 지시문이 정의를 제거할 때까지 기호는 소스 파일에 정의된 상태로 유지됩니다.</span><span class="sxs-lookup"><span data-stu-id="26958-111">A symbol remains defined in a source file until an [#undef](../preprocessor-directives/preprocessor-undef.md) directive in the source file removes the definition.</span></span> <span data-ttu-id="26958-112">-define 옵션을 사용하는 경우 한 파일의 `#undef` 지시문이 프로젝트의 다른 소스 코드 파일에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="26958-112">When you use the -define option, an `#undef` directive in one file has no effect on other source code files in the project.</span></span>  
  
 <span data-ttu-id="26958-113">이 옵션으로 만든 기호를 [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), [#endif](../preprocessor-directives/preprocessor-endif.md)와 함께 사용하면 소스 파일을 조건부 컴파일할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26958-113">You can use symbols created by this option with [#if](../preprocessor-directives/preprocessor-if.md), [#else](../preprocessor-directives/preprocessor-else.md), [#elif](../preprocessor-directives/preprocessor-elif.md), and [#endif](../preprocessor-directives/preprocessor-endif.md) to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="26958-114">**-d** 는 **-define** 의 약식 형태입니다.</span><span class="sxs-lookup"><span data-stu-id="26958-114">**-d** is the short form of **-define**.</span></span>  
  
 <span data-ttu-id="26958-115">세미콜론 또는 쉼표를 사용해서 기호 이름을 구분하여 **-define** 으로 여러 기호를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="26958-115">You can define multiple symbols with **-define** by using a semicolon or comma to separate symbol names.</span></span> <span data-ttu-id="26958-116">예:</span><span class="sxs-lookup"><span data-stu-id="26958-116">For example:</span></span>  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 <span data-ttu-id="26958-117">C# 컴파일러 자체는 소스 코드에서 사용할 수 있는 기호 또는 매크로를 정의하지 않습니다. 모든 기호 정의는 사용자가 정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-117">The C# compiler itself defines no symbols or macros that you can use in your source code; all symbol definitions must be user-defined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26958-118">C# `#define`에서는 C++와 같은 언어에서처럼 기호에 값을 지정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26958-118">The C# `#define` does not allow a symbol to be given a value, as in languages such as C++.</span></span> <span data-ttu-id="26958-119">예를 들어 `#define`을 사용하여 매크로를 만들거나 상수를 정의할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="26958-119">For example, `#define` cannot be used to create a macro or to define a constant.</span></span> <span data-ttu-id="26958-120">상수를 정의해야 하는 경우 `enum` 변수를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-120">If you need to define a constant, use an `enum` variable.</span></span> <span data-ttu-id="26958-121">C++ 스타일 매크로를 만들려는 경우 제네릭과 같은 다른 방식을 고려해 보세요.</span><span class="sxs-lookup"><span data-stu-id="26958-121">If you want to create a C++ style macro, consider alternatives such as generics.</span></span> <span data-ttu-id="26958-122">매크로는 오류가 발생할 가능성이 크므로 C#에서는 매크로를 사용할 수 없으며 더 안전한 방식이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26958-122">Since macros are notoriously error-prone, C# disallows their use but provides safer alternatives.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="26958-123">Visual Studio 개발 환경에서 이 컴파일러 옵션을 설정하려면</span><span class="sxs-lookup"><span data-stu-id="26958-123">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="26958-124">프로젝트 **속성** 페이지를 엽니다.</span><span class="sxs-lookup"><span data-stu-id="26958-124">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="26958-125">**빌드** 탭의 **조건부 컴파일 기호** 상자에 정의할 기호를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-125">On the **Build** tab, type the symbol that is to be defined in the **Conditional compilation symbols** box.</span></span> <span data-ttu-id="26958-126">예를 들어 다음 코드 예제를 사용하는 경우 텍스트 상자에 `xx`를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="26958-126">For example, if you are using the code example that follows, just type `xx` into the text box.</span></span>  
  
 <span data-ttu-id="26958-127">이 컴파일러 옵션을 프로그래밍 방식으로 설정하는 방법에 대한 자세한 내용은 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="26958-127">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26958-128">예제</span><span class="sxs-lookup"><span data-stu-id="26958-128">Example</span></span>  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test
{  
    public static void Main()
    {  
        #if (xx)
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="26958-129">참고 항목</span><span class="sxs-lookup"><span data-stu-id="26958-129">See also</span></span>

- [<span data-ttu-id="26958-130">C# 컴파일러 옵션</span><span class="sxs-lookup"><span data-stu-id="26958-130">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="26958-131">프로젝트 및 솔루션 속성 관리</span><span class="sxs-lookup"><span data-stu-id="26958-131">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
