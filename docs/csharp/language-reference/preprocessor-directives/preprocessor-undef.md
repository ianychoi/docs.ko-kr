---
description: '#undef - C# 참조'
title: '#undef - C# 참조'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "91150559"
---
# <a name="undef-c-reference"></a><span data-ttu-id="6345d-103">#undef(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="6345d-103">#undef (C# Reference)</span></span>

<span data-ttu-id="6345d-104">`#undef`를 사용하면 기호의 정의를 해제할 수 있습니다. 그러면 [#if](./preprocessor-if.md) 지시문에서 해당 기호를 식으로 사용하여 식이 `false`로 평가됩니다.</span><span class="sxs-lookup"><span data-stu-id="6345d-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="6345d-105">[#define](./preprocessor-define.md) 지시문 또는 [-define](../compiler-options/define-compiler-option.md) 컴파일러 옵션을 사용하여 기호를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6345d-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="6345d-106">`#undef` 지시문은 지시문이 아닌 문을 사용하기 전에 파일에 나와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6345d-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6345d-107">예제</span><span class="sxs-lookup"><span data-stu-id="6345d-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="6345d-108">**디버그가 정의되어 있지 않습니다.**</span><span class="sxs-lookup"><span data-stu-id="6345d-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="6345d-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6345d-109">See also</span></span>

- [<span data-ttu-id="6345d-110">C# 참조</span><span class="sxs-lookup"><span data-stu-id="6345d-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6345d-111">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="6345d-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6345d-112">C# 전처리기 지시문</span><span class="sxs-lookup"><span data-stu-id="6345d-112">C# Preprocessor Directives</span></span>](./index.md)
