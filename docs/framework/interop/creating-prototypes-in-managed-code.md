---
title: 관리 코드에서 프로토타입 만들기
description: .NET 관리 코드에서 프로토타입을 만듭니다. 그러면 관리되지 않는 함수에 액세스하고 관리 코드의 메서드 정의에 주석을 추가하는 특성 필드를 사용할 수 있습니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
ms.openlocfilehash: 4260bc8b3f9a2550faa28dd4d35842327b4e5935
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244108"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="b49d2-103">관리 코드에서 프로토타입 만들기</span><span class="sxs-lookup"><span data-stu-id="b49d2-103">Creating Prototypes in Managed Code</span></span>

<span data-ttu-id="b49d2-104">이 항목에서는 관리되지 않는 함수에 액세스하는 방법을 설명하고 관리 코드에서 메서드 정의에 주석을 다는 여러 특성 필드를 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-104">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="b49d2-105">플랫폼 호출에서 사용되는 .NET 기반 선언을 생성하는 방법을 보여 주는 예제는 [플랫폼 호출을 사용하여 데이터 마샬링](marshaling-data-with-platform-invoke.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b49d2-105">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="b49d2-106">관리 코드에서 관리되지 않는 DLL 함수에 액세스하기 전에 함수 이름과 함수를 내보내는 DLL 이름을 알아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-106">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="b49d2-107">이 정보를 사용하여 DLL에서 구현되는 관리되지 않는 함수에 대한 관리되는 정의를 쓰기 시작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-107">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="b49d2-108">또한 플랫폼 호출이 함수를 만들고 데이터를 함수로 또는 반대로 마샬링하는 방법을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-108">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b49d2-109">문자열을 할당하는 Windows API 함수를 통해 `LocalFree`와 같은 메서드를 사용하여 문자열을 해제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-109">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="b49d2-110">플랫폼 호출은 매개 변수를 다르게 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-110">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="b49d2-111">플랫폼 호출의 경우 매개 변수를 `String` 형식 대신 `IntPtr` 형식으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-111">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="b49d2-112"><xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> 클래스에서 제공된 메서드를 사용하여 형식을 문자열로 수동으로 변환하고 해제합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-112">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="b49d2-113">선언 기본 사항</span><span class="sxs-lookup"><span data-stu-id="b49d2-113">Declaration Basics</span></span>  

 <span data-ttu-id="b49d2-114">관리되지 않는 함수에 대한 관리되는 정의는 다음 예제와 같이 언어 종속적입니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-114">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="b49d2-115">전체 코드 예제를 보려면 [플랫폼 호출 예제](platform-invoke-examples.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b49d2-115">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="b49d2-116"><xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> 또는 <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> 필드를 Visual Basic 선언에 적용하려면 `Declare` 문 대신 <xref:System.Runtime.InteropServices.DllImportAttribute> 특성을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-116">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="b49d2-117">정의 조정</span><span class="sxs-lookup"><span data-stu-id="b49d2-117">Adjusting the Definition</span></span>  

 <span data-ttu-id="b49d2-118">명시적으로 설정하는지와 관계없이 특성 필드는 관리 코드 동작을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-118">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="b49d2-119">플랫폼 호출은 어셈블리에서 메타데이터로 있는 다양한 필드에 설정된 기본값에 따라 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-119">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="b49d2-120">필드 하나 이상의 값을 조정하여 이 기본 동작을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-120">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="b49d2-121">대부분 <xref:System.Runtime.InteropServices.DllImportAttribute>를 사용하여 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-121">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="b49d2-122">다음 표에는 플랫폼 호출과 관련된 전체 특성 필드 집합이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-122">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="b49d2-123">표에는 각 필드에 대한 기본값과 이들 필드를 사용하여 관리되지 않는 DLL 함수를 정의하는 방법에 대한 정보 링크가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-123">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="b49d2-124">필드</span><span class="sxs-lookup"><span data-stu-id="b49d2-124">Field</span></span>|<span data-ttu-id="b49d2-125">설명</span><span class="sxs-lookup"><span data-stu-id="b49d2-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="b49d2-126">최적 매핑을 사용하거나 사용하지 않도록 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-126">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="b49d2-127">메서드 인수 전달 시 사용할 호출 규칙을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-127">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="b49d2-128">기본값은 `WinAPI`로, 32비트 Intel 기반 플랫폼의 `__stdcall`에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-128">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="b49d2-129">이름 손상 및 문자열 인수가 함수로 마샬링되는 방법을 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-129">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="b49d2-130">기본값은 `CharSet.Ansi`입니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-130">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="b49d2-131">호출할 DLL 진입점을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-131">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="b49d2-132">문자 집합과 일치하도록 진입점을 수정해야 하는지를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-132">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="b49d2-133">기본값은 프로프래밍 언어에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-133">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="b49d2-134">HRESULT를 반환하고 반환 값에 대한 추가 [out, retval] 인수가 포함된 관리되지 않는 서명으로 관리되는 메서드 서명을 변환할지를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-134">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="b49d2-135">기본값은 `true`입니다(서명을 변형하지 않아야 함).</span><span class="sxs-lookup"><span data-stu-id="b49d2-135">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="b49d2-136">호출자가 `Marshal.GetLastWin32Error` API 함수를 사용하여 메서드를 실행하는 동안 오류가 발생했는지를 확인할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-136">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="b49d2-137">Visual Basic에서 기본값은 `true`이고, C# 및 C++에서 기본값은 `false`입니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-137">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="b49d2-138">ANSI "?" 문자로 변환되는 매핑할 수 없는 유니코드 문자에 대한 예외 throw를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-138">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="b49d2-139">자세한 참조 정보는 <xref:System.Runtime.InteropServices.DllImportAttribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b49d2-139">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="b49d2-140">플랫폼 호출 보안 고려 사항</span><span class="sxs-lookup"><span data-stu-id="b49d2-140">Platform invoke security considerations</span></span>  

 <span data-ttu-id="b49d2-141"><xref:System.Security.Permissions.SecurityAction> 열거형의 `Assert`, `Deny` 및 `PermitOnly` 멤버를 *스택 워크 한정자* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-141">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="b49d2-142">이들 멤버는 플랫폼 호출 선언 및 COM IDL(Interface Definition Language) 문에서 선언 특성으로 사용될 경우 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-142">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="b49d2-143">플랫폼 호출 예제</span><span class="sxs-lookup"><span data-stu-id="b49d2-143">Platform Invoke Examples</span></span>  

 <span data-ttu-id="b49d2-144">이 섹션의 플랫폼 호출 샘플에서는 스택 워크 한정자와 함께 `RegistryPermission` 특성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-144">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="b49d2-145">다음 예제에서는 <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny` 및 `PermitOnly` 한정자가 무시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-145">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="b49d2-146">그러나 다음 예제에서 `Demand` 한정자는 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-146">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="b49d2-147"><xref:System.Security.Permissions.SecurityAction> 한정자는 플랫폼 호출을 포함(래핑)하는 클래스에 배치될 경우 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-147"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="b49d2-148"><xref:System.Security.Permissions.SecurityAction> 한정자는 플랫폼 호출의 호출자에 배치되는 중첩된 시나리오에서도 제대로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-148"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="b49d2-149">COM Interop 예제</span><span class="sxs-lookup"><span data-stu-id="b49d2-149">COM Interop Examples</span></span>  

 <span data-ttu-id="b49d2-150">이 섹션의 COM Interop 샘플에서는 스택 워크 한정자와 함께 `RegistryPermission` 특성을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-150">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="b49d2-151">이전 섹션의 플랫폼 호출 예제와 비슷하게 다음 COM interop 인터페이스 선언은 `Assert`, `Deny` 및 `PermitOnly` 한정자를 무시합니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-151">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="b49d2-152">또한 다음 예제와 같이 `Demand` 한정자는 COM interop 인터페이스 선언 시나리오에서 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b49d2-152">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="b49d2-153">참조</span><span class="sxs-lookup"><span data-stu-id="b49d2-153">See also</span></span>

- [<span data-ttu-id="b49d2-154">관리되지 않는 DLL 함수 사용</span><span class="sxs-lookup"><span data-stu-id="b49d2-154">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="b49d2-155">진입점 지정</span><span class="sxs-lookup"><span data-stu-id="b49d2-155">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="b49d2-156">문자 집합 지정</span><span class="sxs-lookup"><span data-stu-id="b49d2-156">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="b49d2-157">플랫폼 호출 예제</span><span class="sxs-lookup"><span data-stu-id="b49d2-157">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="b49d2-158">[플랫폼 호출 보안 고려 사항](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b49d2-158">[Platform Invoke Security Considerations](/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="b49d2-159">DLL 함수 식별</span><span class="sxs-lookup"><span data-stu-id="b49d2-159">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="b49d2-160">DLL 함수가 포함된 클래스 만들기</span><span class="sxs-lookup"><span data-stu-id="b49d2-160">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="b49d2-161">DLL 함수 호출</span><span class="sxs-lookup"><span data-stu-id="b49d2-161">Calling a DLL Function</span></span>](calling-a-dll-function.md)
