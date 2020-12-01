---
title: 진입점 지정
description: DLL에서 함수의 위치를 식별하는 진입점을 지정하는 방법을 알아봅니다. 진입점을 다른 이름에 매핑하여 함수 이름을 바꿀 수 있습니다.
ms.date: 03/30/2017
helpviewer_keywords:
- EntryPoint field
- platform invoke, attribute fields
- attribute fields in platform invoke, EntryPoint
ms.assetid: d1247f08-0965-416a-b978-e0b50652dfe3
ms.openlocfilehash: d5c6b651b3b5f19eea8e61bc17da92158be87957
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266365"
---
# <a name="specifying-an-entry-point"></a><span data-ttu-id="31a9c-104">진입점 지정</span><span class="sxs-lookup"><span data-stu-id="31a9c-104">Specifying an Entry Point</span></span>

<span data-ttu-id="31a9c-105">진입점은 DLL에서 함수의 위치를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-105">An entry point identifies the location of a function in a DLL.</span></span> <span data-ttu-id="31a9c-106">관리되는 프로젝트 내에서 대상 함수의 원래 이름이나 서수 진입점은 상호 운용 경계 간에 해당 함수를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-106">Within a managed project, the original name or ordinal entry point of a target function identifies that function across the interoperation boundary.</span></span> <span data-ttu-id="31a9c-107">또한 진입점을 다른 이름에 매핑하여 효과적으로 함수 이름을 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-107">Further, you can map the entry point to a different name, effectively renaming the function.</span></span>  
  
 <span data-ttu-id="31a9c-108">다음은 DLL 함수 이름을 바꿀 수 있는 이유 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-108">The following is a list of possible reasons to rename a DLL function:</span></span>  
  
- <span data-ttu-id="31a9c-109">대/소문자를 구분하는 API 함수 이름을 사용하지 않도록 하기 위해</span><span class="sxs-lookup"><span data-stu-id="31a9c-109">To avoid using case-sensitive API function names</span></span>  
  
- <span data-ttu-id="31a9c-110">기존 명명 표준을 준수하기 위해</span><span class="sxs-lookup"><span data-stu-id="31a9c-110">To comply with existing naming standards</span></span>  
  
- <span data-ttu-id="31a9c-111">동일한 DLL 함수의 여러 버전을 선언하여 다른 데이터 형식을 사용하는 함수를 수용하기 위해</span><span class="sxs-lookup"><span data-stu-id="31a9c-111">To accommodate functions that take different data types (by declaring multiple versions of the same DLL function)</span></span>  
  
- <span data-ttu-id="31a9c-112">ANSI 및 유니코드 버전을 포함하는 API 사용을 간소화하기 위해</span><span class="sxs-lookup"><span data-stu-id="31a9c-112">To simplify using APIs that contain ANSI and Unicode versions</span></span>  
  
 <span data-ttu-id="31a9c-113">이 항목에는 관리 코드에서 DLL 함수 이름을 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-113">This topic demonstrates how to rename a DLL function in managed code.</span></span>  
  
## <a name="renaming-a-function-in-visual-basic"></a><span data-ttu-id="31a9c-114">Visual Basic에서 함수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="31a9c-114">Renaming a Function in Visual Basic</span></span>  

<span data-ttu-id="31a9c-115">Visual Basic에서는 **Declare** 문에 **Function** 키워드를 사용하여 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 필드를 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-115">Visual Basic uses the **Function** keyword in the **Declare** statement to set the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field.</span></span> <span data-ttu-id="31a9c-116">다음 예제에서는 기본 선언을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-116">The following example shows a basic declaration.</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
<span data-ttu-id="31a9c-117">다음 예제와 같이 정의에 **Alias** 키워드를 포함하여 **MessageBox** 진입점을 **MsgBox** 로 바꿀 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-117">You can replace the **MessageBox** entry point with **MsgBox** by including the **Alias** keyword in your definition, as shown in the following example.</span></span> <span data-ttu-id="31a9c-118">두 예제에서 모두 **Auto** 키워드를 사용하면 진입점의 문자 집합 버전을 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-118">In both examples the **Auto** keyword eliminates the need to specify the character-set version of the entry point.</span></span> <span data-ttu-id="31a9c-119">문자 집합을 선택하는 방법에 대한 자세한 내용은 [문자 집합 지정](specifying-a-character-set.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="31a9c-119">For more information about selecting a character set, see [Specifying a Character Set](specifying-a-character-set.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MsgBox _
        Lib "user32.dll" Alias "MessageBox" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
## <a name="renaming-a-function-in-c-and-c"></a><span data-ttu-id="31a9c-120">C# 및 C++에서 함수 이름 바꾸기</span><span class="sxs-lookup"><span data-stu-id="31a9c-120">Renaming a Function in C# and C++</span></span>  

 <span data-ttu-id="31a9c-121"><xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> 필드를 사용하여 DLL 함수를 이름 또는 서수로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-121">You can use the <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint?displayProperty=nameWithType> field to specify a DLL function by name or ordinal.</span></span> <span data-ttu-id="31a9c-122">메서드 정의의 함수 이름이 DLL의 진입점과 같으면 **EntryPoint** 필드를 사용하여 함수를 명시적으로 식별할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-122">If the name of the function in your method definition is the same as the entry point in the DLL, you do not have to explicitly identify the function with the **EntryPoint** field.</span></span> <span data-ttu-id="31a9c-123">그러지 않으면 다음 특성 형식 중 하나를 사용하여 이름 또는 서수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-123">Otherwise, use one of the following attribute forms to indicate a name or ordinal:</span></span>  
  
```csharp
[DllImport("DllName", EntryPoint = "Functionname")]
[DllImport("DllName", EntryPoint = "#123")]
```
  
 <span data-ttu-id="31a9c-124">서수 앞에 파운드 기호(#)를 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-124">Notice that you must prefix an ordinal with the pound sign (#).</span></span>  
  
 <span data-ttu-id="31a9c-125">다음 예제에서는 **EntryPoint** 필드를 사용하여 코드에서 **MessageBoxA** 를 **MsgBox** 로 바꾸는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="31a9c-125">The following example demonstrates how to replace **MessageBoxA** with **MsgBox** in your code by using the **EntryPoint** field.</span></span>  
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll", EntryPoint = "MessageBoxA")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

typedef void* HWND;
[DllImport("user32", EntryPoint = "MessageBoxA")]
extern "C" int MsgBox(
    HWND hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="see-also"></a><span data-ttu-id="31a9c-126">참조</span><span class="sxs-lookup"><span data-stu-id="31a9c-126">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="31a9c-127">관리 코드에서 프로토타입 만들기</span><span class="sxs-lookup"><span data-stu-id="31a9c-127">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="31a9c-128">플랫폼 호출 예제</span><span class="sxs-lookup"><span data-stu-id="31a9c-128">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- [<span data-ttu-id="31a9c-129">플랫폼 호출을 사용하여 데이터 마샬링</span><span class="sxs-lookup"><span data-stu-id="31a9c-129">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)
