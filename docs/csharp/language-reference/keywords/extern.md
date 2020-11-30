---
description: extern 한정자 - C# 참조
title: extern 한정자 - C# 참조
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "89138971"
---
# <a name="extern-c-reference"></a><span data-ttu-id="0c6e7-103">extern(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="0c6e7-103">extern (C# Reference)</span></span>

<span data-ttu-id="0c6e7-104">`extern` 한정자는 외부에서 구현되는 메서드를 선언하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-104">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="0c6e7-105">`extern` 한정자는 일반적으로 Interop 서비스를 사용하여 비관리 코드를 호출할 때 `DllImport` 특성과 함께 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-105">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="0c6e7-106">이 경우 다음 예제에서와 같이 메서드를 `static`으로 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-106">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="0c6e7-107">`extern` 키워드는 외부 어셈블리 별칭도 정의하여 단일 어셈블리 내에서 동일한 구성 요소의 다른 버전을 참조할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-107">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="0c6e7-108">자세한 내용은 [extern alias](extern-alias.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-108">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="0c6e7-109">[abstract](abstract.md) 및 `extern` 한정자를 함께 사용하여 같은 멤버를 수정할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-109">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="0c6e7-110">`extern` 한정자는 메서드가 C# 코드 외부에서 구현됨을 나타내고 `abstract` 한정자는 해당 클래스에서 메서드가 구현되지 않음을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-110">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="0c6e7-111">extern 키워드는 C++보다 C#에서 사용이 제한적입니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-111">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="0c6e7-112">C# 키워드를 C++ 키워드와 비교하려면 extern을 사용하여 C++ 언어 참조에 링크 지정을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-112">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="0c6e7-113">예 1</span><span class="sxs-lookup"><span data-stu-id="0c6e7-113">Example 1</span></span>

<span data-ttu-id="0c6e7-114">이 예제에서는 프로그램이 사용자로부터 문자열을 수신하여 메시지 상자에 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="0c6e7-115">이 프로그램은 User32.dll 라이브러리에서 가져온 `MessageBox` 메서드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="0c6e7-116">예제 2</span><span class="sxs-lookup"><span data-stu-id="0c6e7-116">Example 2</span></span>

<span data-ttu-id="0c6e7-117">이 예제는 C 라이브러리(네이티브 DLL)로 호출되는 C# 프로그램을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-117">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="0c6e7-118">다음 C 파일을 만들고 이름을 `cmdll.c`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-118">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="0c6e7-119">Visual Studio 설치 디렉터리에서 Visual Studio x64(또는 x32) 네이티브 도구 명령 프롬프트 창을 열고 명령 프롬프트에서 **cl -LD cmdll.c** 를 입력하여 `cmdll.c` 파일을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-119">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="0c6e7-120">같은 디렉터리에서 다음 C# 파일을 만들고 이름을 `cm.cs`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-120">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="0c6e7-121">Visual Studio 설치 디렉터리에서 Visual Studio x64(또는 x32) 네이티브 도구 명령 프롬프트 창을 열고 명령 프롬프트에서 다음을 입력하여 `cm.cs` 파일을 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="0c6e7-122">**csc cm.cs**(x64 명령 프롬프트의 경우) —또는— **csc -platform:x86 cm.cs**(x32 명령 프롬프트의 경우)</span><span class="sxs-lookup"><span data-stu-id="0c6e7-122">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="0c6e7-123">이렇게 하면 실행 파일 `cm.exe`가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-123">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="0c6e7-124">`cm.exe`을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-124">Run `cm.exe`.</span></span> <span data-ttu-id="0c6e7-125">`SampleMethod` 메서드가 값 5를 DLL 파일에 전달하면 10을 곱한 값이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-125">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="0c6e7-126">프로그램에서는 다음이 출력됩니다.</span><span class="sxs-lookup"><span data-stu-id="0c6e7-126">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="0c6e7-127">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="0c6e7-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0c6e7-128">참조</span><span class="sxs-lookup"><span data-stu-id="0c6e7-128">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="0c6e7-129">C# 참조</span><span class="sxs-lookup"><span data-stu-id="0c6e7-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0c6e7-130">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="0c6e7-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0c6e7-131">C# 키워드</span><span class="sxs-lookup"><span data-stu-id="0c6e7-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0c6e7-132">한정자</span><span class="sxs-lookup"><span data-stu-id="0c6e7-132">Modifiers</span></span>](index.md)
