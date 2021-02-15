---
description: '자세히 알아보기: 특성 개요 (Visual Basic)'
title: 특성 개요
ms.date: 07/20/2015
ms.assetid: 1449f69b-c063-41de-8d89-f0bbdcf96ac6
ms.openlocfilehash: f25e69452f0af1c89af667619e673f8906704d1f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437724"
---
# <a name="attributes-overview-visual-basic"></a><span data-ttu-id="7509b-103">특성 개요(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-103">Attributes overview (Visual Basic)</span></span>

<span data-ttu-id="7509b-104">특성은 메타데이터 또는 선언적 정보를 코드(어셈블리, 형식, 메서드, 속성 등)에 연결하는 강력한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-104">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="7509b-105">특성이 프로그램 엔터티와 연결되면 *리플렉션* 이라는 기법을 사용하여 런타임에 특성이 쿼리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-105">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="7509b-106">자세한 내용은 [리플렉션(Visual Basic)](../reflection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-106">For more information, see [Reflection (Visual Basic)](../reflection.md).</span></span>

<span data-ttu-id="7509b-107">특성에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-107">Attributes have the following properties:</span></span>

- <span data-ttu-id="7509b-108">특성은 프로그램에 메타데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-108">Attributes add metadata to your program.</span></span> <span data-ttu-id="7509b-109">*메타데이터* 는 프로그램에 정의된 형식에 대한 정보를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-109">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="7509b-110">모든 .NET 어셈블리에는 어셈블리에 정의된 형식 및 형식 멤버를 설명하는 지정된 메타데이터 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-110">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="7509b-111">필요한 추가 정보를 지정하는 사용자 지정 특성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-111">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="7509b-112">자세한 내용은 [사용자 지정 특성 만들기(Visual Basic)](creating-custom-attributes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-112">For more information, see, [Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md).</span></span>

- <span data-ttu-id="7509b-113">전체 어셈블리, 모듈 또는 좀 더 작은 프로그램 요소(예: 클래스 및 속성)에 하나 이상의 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-113">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>

- <span data-ttu-id="7509b-114">메서드 및 속성의 경우와 같은 방식으로 특성은 인수를 수락할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-114">Attributes can accept arguments in the same way as methods and properties.</span></span>

- <span data-ttu-id="7509b-115">프로그램은 리플렉션을 사용하여 자체 메타데이터 또는 다른 프로그램의 메타데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-115">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="7509b-116">자세한 내용은 [리플렉션을 사용하여 특성 액세스(Visual Basic)](accessing-attributes-by-using-reflection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-116">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="7509b-117">특성 사용</span><span class="sxs-lookup"><span data-stu-id="7509b-117">Using Attributes</span></span>

<span data-ttu-id="7509b-118">특정 특성은 유효한 선언 형식이 제한적일 수 있지만 거의 모든 선언에 특성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-118">Attributes can be placed on most any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="7509b-119">Visual Basic에서 특성은 꺾쇠 괄호 ()로 묶여 \< > 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-119">In Visual Basic, an attribute is enclosed in angle brackets (\< >).</span></span> <span data-ttu-id="7509b-120">특성은 적용되는 요소 바로 앞에 표시되어야 하며 같은 줄에 위치합니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-120">It must appear immediately before the element to which it is applied, on the same line.</span></span>

<span data-ttu-id="7509b-121">이 예제에서 <xref:System.SerializableAttribute> 특성은 클래스에 특정 특성을 적용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

```vb
<System.Serializable()> Public Class SampleClass
    ' Objects of this type can be serialized.
End Class
```

 <span data-ttu-id="7509b-122"><xref:System.Runtime.InteropServices.DllImportAttribute> 특성을 사용하는 메서드는 다음과 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like this:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
<System.Runtime.InteropServices.DllImport("user32.dll")>
Sub SampleMethod()
End Sub
```

<span data-ttu-id="7509b-123">둘 이상의 특성을 하나의 선언에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-123">More than one attribute can be placed on a declaration:</span></span>

```vb
Imports System.Runtime.InteropServices
```

```vb
Sub MethodA(<[In](), Out()> ByVal x As Double)
End Sub
Sub MethodB(<Out(), [In]()> ByVal x As Double)
End Sub
```

<span data-ttu-id="7509b-124">지정된 엔터티에 대해 일부 특성을 두 번 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="7509b-125">이러한 다용도 특성의 예로 <xref:System.Diagnostics.ConditionalAttribute>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

```vb
<Conditional("DEBUG"), Conditional("TEST1")>
Sub TraceMethod()
End Sub
```

> [!NOTE]
> <span data-ttu-id="7509b-126">규칙에 따라 모든 특성 이름은 .NET Framework의 다른 항목과 구분하기 위해 단어 "Attribute"로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET Framework.</span></span> <span data-ttu-id="7509b-127">그러나 코드에서 특성을 사용하는 경우 특성 접미사를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="7509b-128">예를 들어 `[DllImport]`는 `[DllImportAttribute]`와 같지만 `DllImportAttribute`는 .NET Framework에서 특성의 실제 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Framework.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="7509b-129">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7509b-129">Attribute Parameters</span></span>

<span data-ttu-id="7509b-130">많은 특성에는 매개 변수를 위치, 명명되지 않은 또는 명명된 상태의 매개 변수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="7509b-131">모든 위치 매개 변수는 특정 순서로 지정해야 하며 생략할 수 없습니다. 명명된 매개 변수는 선택적이며 순서에 관계 없이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-131">Any positional parameters must be specified in a certain order and cannot be omitted; named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="7509b-132">위치 매개 변수가 가장 먼저 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-132">Positional parameters are specified first.</span></span> <span data-ttu-id="7509b-133">예를 들어 다음 세 가지 특성은 동급입니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-133">For example, these three attributes are equivalent:</span></span>

```vb
<DllImport("user32.dll")>
<DllImport("user32.dll", SetLastError:=False, ExactSpelling:=False)>
<DllImport("user32.dll", ExactSpelling:=False, SetLastError:=False)>
```

<span data-ttu-id="7509b-134">첫 번째 매개 변수인 DLL 이름은 위치 매개 변수이므로 항상 맨 먼저 오고 나머지 매개 변수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-134">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="7509b-135">이 경우 명명된 두 매개 변수는 기본적으로 false이므로 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-135">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="7509b-136">기본 매개 변수 값에 대한 자세한 내용은 개별 특성의 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-136">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="7509b-137">특성 대상</span><span class="sxs-lookup"><span data-stu-id="7509b-137">Attribute Targets</span></span>

<span data-ttu-id="7509b-138">특성의 *대상* 은 특성이 적용되는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-138">The *target* of an attribute is the entity to which the attribute applies.</span></span> <span data-ttu-id="7509b-139">예를 들어 특성은 클래스, 특정 메서드 또는 전체 어셈블리에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-139">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="7509b-140">기본적으로 특성은 그 앞에 오는 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-140">By default, an attribute applies to the element that it precedes.</span></span> <span data-ttu-id="7509b-141">하지만 특성이 메서드, 해당 매개 변수 또는 해당 반환 값 중 어디에 적용될지를 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-141">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="7509b-142">특성 대상을 명시적으로 식별하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-142">To explicitly identify an attribute target, use the following syntax:</span></span>

```vb
<target : attribute-list>
```

<span data-ttu-id="7509b-143">가능한 `target` 값 목록은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-143">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="7509b-144">대상 값</span><span class="sxs-lookup"><span data-stu-id="7509b-144">Target value</span></span>|<span data-ttu-id="7509b-145">적용 대상</span><span class="sxs-lookup"><span data-stu-id="7509b-145">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="7509b-146">전체 어셈블리</span><span class="sxs-lookup"><span data-stu-id="7509b-146">Entire assembly</span></span>|
|`module`|<span data-ttu-id="7509b-147">현재 어셈블리 모듈(Visual Basic 모듈과는 다름)</span><span class="sxs-lookup"><span data-stu-id="7509b-147">Current assembly module (which is different from a Visual Basic Module)</span></span>|

 <span data-ttu-id="7509b-148">다음 예제에서는 어셈블리와 모듈에 특성을 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-148">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="7509b-149">자세한 내용은 [사용자 지정 특성(Visual Basic)](common-attributes.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-149">For more information, see [Common Attributes (Visual Basic)](common-attributes.md).</span></span>

```vb
Imports System.Reflection
<Assembly: AssemblyTitleAttribute("Production assembly 4"),
Module: CLSCompliant(True)>
```

## <a name="common-uses-for-attributes"></a><span data-ttu-id="7509b-150">특성의 일반적인 용도</span><span class="sxs-lookup"><span data-stu-id="7509b-150">Common Uses for Attributes</span></span>

<span data-ttu-id="7509b-151">다음 목록에는 코드에서 특성이 사용되는 일반적인 경우가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7509b-151">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="7509b-152">SOAP 프로토콜을 통해 메서드를 호출할 수 있음을 나타내기 위해 웹 서비스에서 `WebMethod` 특성을 사용하여 메서드에 표시.</span><span class="sxs-lookup"><span data-stu-id="7509b-152">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="7509b-153">자세한 내용은 <xref:System.Web.Services.WebMethodAttribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-153">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>

- <span data-ttu-id="7509b-154">네이티브 코드와 상호 운용될 경우 메서드 매개 변수를 마샬링하는 방법 설명.</span><span class="sxs-lookup"><span data-stu-id="7509b-154">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="7509b-155">자세한 내용은 <xref:System.Runtime.InteropServices.MarshalAsAttribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-155">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

- <span data-ttu-id="7509b-156">클래스, 메서드 및 인터페이스에 대한 COM 속성 설명</span><span class="sxs-lookup"><span data-stu-id="7509b-156">Describing the COM properties for classes, methods, and interfaces.</span></span>

- <span data-ttu-id="7509b-157"><xref:System.Runtime.InteropServices.DllImportAttribute> 클래스를 사용하는 비관리 코드 호출</span><span class="sxs-lookup"><span data-stu-id="7509b-157">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>

- <span data-ttu-id="7509b-158">제목, 버전, 설명 또는 상표를 기준으로 어셈블리 설명</span><span class="sxs-lookup"><span data-stu-id="7509b-158">Describing your assembly in terms of title, version, description, or trademark.</span></span>

- <span data-ttu-id="7509b-159">지속성을 위해 serialize할 클래스의 멤버 설명</span><span class="sxs-lookup"><span data-stu-id="7509b-159">Describing which members of a class to serialize for persistence.</span></span>

- <span data-ttu-id="7509b-160">XML serialization를 위해 클래스 멤버 및 XML 노드 간을 매핑하는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="7509b-160">Describing how to map between class members and XML nodes for XML serialization.</span></span>

- <span data-ttu-id="7509b-161">메서드에 대한 보안 요구 사항 설명</span><span class="sxs-lookup"><span data-stu-id="7509b-161">Describing the security requirements for methods.</span></span>

- <span data-ttu-id="7509b-162">보안을 적용하는 데 사용되는 특징 지정</span><span class="sxs-lookup"><span data-stu-id="7509b-162">Specifying characteristics used to enforce security.</span></span>

- <span data-ttu-id="7509b-163">코드를 쉽게 디버그할 수 있도록 하기 위해 JIT(Just-In-Time) 컴파일러를 통해 최적화 제어</span><span class="sxs-lookup"><span data-stu-id="7509b-163">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>

- <span data-ttu-id="7509b-164">메서드 호출자에 대한 정보 얻기</span><span class="sxs-lookup"><span data-stu-id="7509b-164">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="7509b-165">관련 단원</span><span class="sxs-lookup"><span data-stu-id="7509b-165">Related Sections</span></span>

<span data-ttu-id="7509b-166">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7509b-166">For more information, see:</span></span>

- [<span data-ttu-id="7509b-167">사용자 지정 특성 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-167">Creating Custom Attributes (Visual Basic)</span></span>](creating-custom-attributes.md)

- [<span data-ttu-id="7509b-168">리플렉션을 사용하여 특성 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-168">Accessing Attributes by Using Reflection (Visual Basic)</span></span>](accessing-attributes-by-using-reflection.md)

- [<span data-ttu-id="7509b-169">방법: 특성을 사용하여 C/C++ 공용 구조체 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-169">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)

- [<span data-ttu-id="7509b-170">일반 특성(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-170">Common Attributes (Visual Basic)</span></span>](common-attributes.md)

- [<span data-ttu-id="7509b-171">호출자 정보(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-171">Caller Information (Visual Basic)</span></span>](../caller-information.md)

## <a name="see-also"></a><span data-ttu-id="7509b-172">추가 정보</span><span class="sxs-lookup"><span data-stu-id="7509b-172">See also</span></span>

- [<span data-ttu-id="7509b-173">Visual Basic 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="7509b-173">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="7509b-174">리플렉션(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7509b-174">Reflection (Visual Basic)</span></span>](../reflection.md)
- [<span data-ttu-id="7509b-175">특성</span><span class="sxs-lookup"><span data-stu-id="7509b-175">Attributes</span></span>](../../../../standard/attributes/index.md)
