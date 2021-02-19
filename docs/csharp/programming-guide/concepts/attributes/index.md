---
title: 특성(C#)
description: 특성을 사용하여 C#에서 메타데이터 또는 선언적 정보를 코드와 연결하는 방법에 대해 알아봅니다. 특성은 리플렉션을 사용하여 런타임에 쿼리할 수 있습니다.
ms.date: 04/26/2018
ms.openlocfilehash: f468b01d3f7832ed8c127f34e6d4e3c1bcf7901a
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583678"
---
# <a name="attributes-c"></a><span data-ttu-id="f8bba-104">특성(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-104">Attributes (C#)</span></span>

<span data-ttu-id="f8bba-105">특성은 메타데이터 또는 선언적 정보를 코드(어셈블리, 형식, 메서드, 속성 등)에 연결하는 강력한 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-105">Attributes provide a powerful method of associating metadata, or declarative information, with code (assemblies, types, methods, properties, and so forth).</span></span> <span data-ttu-id="f8bba-106">특성이 프로그램 엔터티와 연결되면 *리플렉션* 이라는 기법을 사용하여 런타임에 특성이 쿼리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-106">After an attribute is associated with a program entity, the attribute can be queried at run time by using a technique called *reflection*.</span></span> <span data-ttu-id="f8bba-107">자세한 내용은 [리플렉션(C#)](../reflection.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-107">For more information, see [Reflection (C#)](../reflection.md).</span></span>

<span data-ttu-id="f8bba-108">특성에는 다음과 같은 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-108">Attributes have the following properties:</span></span>

- <span data-ttu-id="f8bba-109">특성은 프로그램에 메타데이터를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-109">Attributes add metadata to your program.</span></span> <span data-ttu-id="f8bba-110">*메타데이터* 는 프로그램에 정의된 형식에 대한 정보를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-110">*Metadata* is information about the types defined in a program.</span></span> <span data-ttu-id="f8bba-111">모든 .NET 어셈블리에는 어셈블리에 정의된 형식 및 형식 멤버를 설명하는 지정된 메타데이터 집합이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-111">All .NET assemblies contain a specified set of metadata that describes the types and type members defined in the assembly.</span></span> <span data-ttu-id="f8bba-112">필요한 추가 정보를 지정하는 사용자 지정 특성을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-112">You can add custom attributes to specify any additional information that is required.</span></span> <span data-ttu-id="f8bba-113">자세한 내용은 [사용자 지정 특성 만들기(C#)](creating-custom-attributes.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-113">For more information, see, [Creating Custom Attributes (C#)](creating-custom-attributes.md).</span></span>
- <span data-ttu-id="f8bba-114">전체 어셈블리, 모듈 또는 좀 더 작은 프로그램 요소(예: 클래스 및 속성)에 하나 이상의 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-114">You can apply one or more attributes to entire assemblies, modules, or smaller program elements such as classes and properties.</span></span>
- <span data-ttu-id="f8bba-115">메서드 및 속성의 경우와 같은 방식으로 특성은 인수를 수락할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-115">Attributes can accept arguments in the same way as methods and properties.</span></span>
- <span data-ttu-id="f8bba-116">프로그램은 리플렉션을 사용하여 자체 메타데이터 또는 다른 프로그램의 메타데이터를 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-116">Your program can examine its own metadata or the metadata in other programs by using reflection.</span></span> <span data-ttu-id="f8bba-117">자세한 내용은 [리플렉션을 사용하여 특성 액세스(C#)](accessing-attributes-by-using-reflection.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-117">For more information, see [Accessing Attributes by Using Reflection (C#)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="using-attributes"></a><span data-ttu-id="f8bba-118">특성 사용</span><span class="sxs-lookup"><span data-stu-id="f8bba-118">Using attributes</span></span>

<span data-ttu-id="f8bba-119">특정 특성은 유효한 선언 형식이 제한적일 수 있지만 대부분의 선언에 특성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-119">Attributes can be placed on almost any declaration, though a specific attribute might restrict the types of declarations on which it is valid.</span></span> <span data-ttu-id="f8bba-120">C#에서는 특성 이름을 대괄호([])로 묶어 적용하고자 하는 엔터티의 선언 위에 배치하여 특성을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-120">In C#, you specify an attribute by placing the name of the attribute enclosed in square brackets ([]) above the declaration of the entity to which it applies.</span></span>

<span data-ttu-id="f8bba-121">이 예제에서 <xref:System.SerializableAttribute> 특성은 클래스에 특정 특성을 적용하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-121">In this example, the <xref:System.SerializableAttribute> attribute is used to apply a specific characteristic to a class:</span></span>

[!code-csharp[Using the serializable attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#1)]

<span data-ttu-id="f8bba-122"><xref:System.Runtime.InteropServices.DllImportAttribute> 특성을 사용하는 메서드는 다음 예제와 같이 선언됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-122">A method with the attribute <xref:System.Runtime.InteropServices.DllImportAttribute> is declared like the following example:</span></span>

[!code-csharp[Declaring a method to import from an external library](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#2)]

<span data-ttu-id="f8bba-123">다음 예제와 같이 둘 이상의 특성을 하나의 선언에 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-123">More than one attribute can be placed on a declaration as the following example shows:</span></span>

[!code-csharp[Including the interop namespace](~/samples/snippets/csharp/attributes/AttributesOverview.cs#3)]
[!code-csharp[Declaring two way marshaling for arguments](~/samples/snippets/csharp/attributes/AttributesOverview.cs#4)]

<span data-ttu-id="f8bba-124">지정된 엔터티에 대해 일부 특성을 두 번 이상 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-124">Some attributes can be specified more than once for a given entity.</span></span> <span data-ttu-id="f8bba-125">이러한 다용도 특성의 예로 <xref:System.Diagnostics.ConditionalAttribute>가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-125">An example of such a multiuse attribute is <xref:System.Diagnostics.ConditionalAttribute>:</span></span>

[!code-csharp[Using the conditional attribute](~/samples/snippets/csharp/attributes/AttributesOverview.cs#5)]

> [!NOTE]
> <span data-ttu-id="f8bba-126">규칙에 따라 모든 특성 이름은 .NET 라이브러리의 다른 항목과 구분하기 위해 "Attribute" 단어로 끝납니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-126">By convention, all attribute names end with the word "Attribute" to distinguish them from other items in the .NET libraries.</span></span> <span data-ttu-id="f8bba-127">그러나 코드에서 특성을 사용하는 경우 특성 접미사를 지정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-127">However, you do not need to specify the attribute suffix when using attributes in code.</span></span> <span data-ttu-id="f8bba-128">예를 들어 `[DllImport]`는 `[DllImportAttribute]`와 같지만, `DllImportAttribute`는 .NET 클래스 라이브러리에서 특성의 실제 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-128">For example, `[DllImport]` is equivalent to `[DllImportAttribute]`, but `DllImportAttribute` is the attribute's actual name in the .NET Class Library.</span></span>

### <a name="attribute-parameters"></a><span data-ttu-id="f8bba-129">특성 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f8bba-129">Attribute parameters</span></span>

<span data-ttu-id="f8bba-130">많은 특성에는 매개 변수를 위치, 명명되지 않은 또는 명명된 상태의 매개 변수가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-130">Many attributes have parameters, which can be positional, unnamed, or named.</span></span> <span data-ttu-id="f8bba-131">위치 매개 변수를 특정 순서로 지정해야 하며 생략할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-131">Any positional parameters must be specified in a certain order and cannot be omitted.</span></span> <span data-ttu-id="f8bba-132">명명된 매개 변수는 선택 사항이며 순서에 관계 없이 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-132">Named parameters are optional and can be specified in any order.</span></span> <span data-ttu-id="f8bba-133">위치 매개 변수가 가장 먼저 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-133">Positional parameters are specified first.</span></span> <span data-ttu-id="f8bba-134">예를 들어 다음 세 가지 특성은 동급입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-134">For example, these three attributes are equivalent:</span></span>

```csharp
[DllImport("user32.dll")]
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]
```

<span data-ttu-id="f8bba-135">첫 번째 매개 변수인 DLL 이름은 위치 매개 변수이므로 항상 맨 먼저 오고 나머지 매개 변수가 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-135">The first parameter, the DLL name, is positional and always comes first; the others are named.</span></span> <span data-ttu-id="f8bba-136">이 경우 명명된 두 매개 변수는 기본적으로 false이므로 생략할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-136">In this case, both named parameters default to false, so they can be omitted.</span></span> <span data-ttu-id="f8bba-137">위치 매개 변수는 특성 생성자의 매개 변수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-137">Positional parameters correspond to the parameters of the attribute constructor.</span></span> <span data-ttu-id="f8bba-138">명명된 또는 선택적 매개 변수는 특성의 속성 또는 필드에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-138">Named or optional parameters correspond to either properties or fields of the attribute.</span></span> <span data-ttu-id="f8bba-139">기본 매개 변수 값에 대한 자세한 내용은 개별 특성의 설명서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-139">Refer to the individual attribute's documentation for information on default parameter values.</span></span>

### <a name="attribute-targets"></a><span data-ttu-id="f8bba-140">특성 대상</span><span class="sxs-lookup"><span data-stu-id="f8bba-140">Attribute targets</span></span>

<span data-ttu-id="f8bba-141">특성의 *대상* 은 특성이 적용되는 엔터티입니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-141">The *target* of an attribute is the entity which the attribute applies to.</span></span> <span data-ttu-id="f8bba-142">예를 들어 특성은 클래스, 특정 메서드 또는 전체 어셈블리에 적용될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-142">For example, an attribute may apply to a class, a particular method, or an entire assembly.</span></span> <span data-ttu-id="f8bba-143">기본적으로 특성은 그 뒤에 오는 요소에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-143">By default, an attribute applies to the element that follows it.</span></span> <span data-ttu-id="f8bba-144">하지만 특성이 메서드, 해당 매개 변수 또는 해당 반환 값 중 어디에 적용될지를 명시적으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-144">But you can also explicitly identify, for example, whether an attribute is applied to a method, or to its parameter, or to its return value.</span></span>

<span data-ttu-id="f8bba-145">특성 대상을 명시적으로 식별하려면 다음 구문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-145">To explicitly identify an attribute target, use the following syntax:</span></span>

```csharp
[target : attribute-list]
```

<span data-ttu-id="f8bba-146">가능한 `target` 값 목록은 다음 표에 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-146">The list of possible `target` values is shown in the following table.</span></span>

|<span data-ttu-id="f8bba-147">대상 값</span><span class="sxs-lookup"><span data-stu-id="f8bba-147">Target value</span></span>|<span data-ttu-id="f8bba-148">적용 대상</span><span class="sxs-lookup"><span data-stu-id="f8bba-148">Applies to</span></span>|
|------------------|----------------|
|`assembly`|<span data-ttu-id="f8bba-149">전체 어셈블리</span><span class="sxs-lookup"><span data-stu-id="f8bba-149">Entire assembly</span></span>|
|`module`|<span data-ttu-id="f8bba-150">현재 어셈블리 모듈</span><span class="sxs-lookup"><span data-stu-id="f8bba-150">Current assembly module</span></span>|
|`field`|<span data-ttu-id="f8bba-151">클래스 또는 구조체의 필드</span><span class="sxs-lookup"><span data-stu-id="f8bba-151">Field in a class or a struct</span></span>|
|`event`|<span data-ttu-id="f8bba-152">이벤트</span><span class="sxs-lookup"><span data-stu-id="f8bba-152">Event</span></span>|
|`method`|<span data-ttu-id="f8bba-153">메서드 또는 `get` 및 `set` 속성 접근자</span><span class="sxs-lookup"><span data-stu-id="f8bba-153">Method or `get` and `set` property accessors</span></span>|
|`param`|<span data-ttu-id="f8bba-154">메서드 매개 변수 또는 `set` 속성 접근자 매개 변수</span><span class="sxs-lookup"><span data-stu-id="f8bba-154">Method parameters or `set` property accessor parameters</span></span>|
|`property`|<span data-ttu-id="f8bba-155">속성</span><span class="sxs-lookup"><span data-stu-id="f8bba-155">Property</span></span>|
|`return`|<span data-ttu-id="f8bba-156">메서드, 속성 인덱서 또는 `get` 속성 접근자의 반환 값</span><span class="sxs-lookup"><span data-stu-id="f8bba-156">Return value of a method, property indexer, or `get` property accessor</span></span>|
|`type`|<span data-ttu-id="f8bba-157">구조체, 클래스, 인터페이스, 열거형 또는 대리자</span><span class="sxs-lookup"><span data-stu-id="f8bba-157">Struct, class, interface, enum, or delegate</span></span>|

<span data-ttu-id="f8bba-158">[자동 구현 속성](../../../properties.md)에 대해 생성된 지원 필드에 특성을 적용하기 위해 `field` 대상 값을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-158">You would specify the `field` target value to apply an attribute to the backing field created for an [auto-implemented property](../../../properties.md).</span></span>

<span data-ttu-id="f8bba-159">다음 예제에서는 어셈블리와 모듈에 특성을 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-159">The following example shows how to apply attributes to assemblies and modules.</span></span> <span data-ttu-id="f8bba-160">자세한 내용은 [공통 특성(C#)](../../../language-reference/attributes/global.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-160">For more information, see [Common Attributes (C#)](../../../language-reference/attributes/global.md).</span></span>

```csharp
using System;
using System.Reflection;
[assembly: AssemblyTitleAttribute("Production assembly 4")]
[module: CLSCompliant(true)]
```

<span data-ttu-id="f8bba-161">다음 예제에서는 C#에서 메서드, 메서드 매개 변수 및 메서드 반환 값에 특성을 적용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-161">The following example shows how to apply attributes to methods, method parameters, and method return values in C#.</span></span>

[!code-csharp[Applying attributes to different code elements](../../../../../samples/snippets/csharp/attributes/AttributesOverview.cs#6)]

> [!NOTE]
> <span data-ttu-id="f8bba-162">`ValidatedContract`이 정의되는 대상이 유효한지에 상관없이, 반환 값에만 적용하도록 `ValidatedContract`이 정의된 경우에도 `return` 대상을 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-162">Regardless of the targets on which `ValidatedContract` is defined to be valid, the `return` target has to be specified, even if `ValidatedContract` were defined to apply only to return values.</span></span> <span data-ttu-id="f8bba-163">즉, 컴파일러는 모호한 특성 대상을 확인하기 위해 `AttributeUsage` 정보를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-163">In other words, the compiler will not use `AttributeUsage` information to resolve ambiguous attribute targets.</span></span> <span data-ttu-id="f8bba-164">자세한 내용은 [AttributeUsage(C#)](../../../language-reference/attributes/general.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-164">For more information, see [AttributeUsage (C#)](../../../language-reference/attributes/general.md).</span></span>

## <a name="common-uses-for-attributes"></a><span data-ttu-id="f8bba-165">특성의 일반적인 용도</span><span class="sxs-lookup"><span data-stu-id="f8bba-165">Common uses for attributes</span></span>

<span data-ttu-id="f8bba-166">다음 목록에는 코드에서 특성이 사용되는 일반적인 경우가 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f8bba-166">The following list includes a few of the common uses of attributes in code:</span></span>

- <span data-ttu-id="f8bba-167">SOAP 프로토콜을 통해 메서드를 호출할 수 있음을 나타내기 위해 웹 서비스에서 `WebMethod` 특성을 사용하여 메서드에 표시.</span><span class="sxs-lookup"><span data-stu-id="f8bba-167">Marking methods using the `WebMethod` attribute in Web services to indicate that the method should be callable over the SOAP protocol.</span></span> <span data-ttu-id="f8bba-168">자세한 내용은 <xref:System.Web.Services.WebMethodAttribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-168">For more information, see <xref:System.Web.Services.WebMethodAttribute>.</span></span>
- <span data-ttu-id="f8bba-169">네이티브 코드와 상호 운용될 경우 메서드 매개 변수를 마샬링하는 방법 설명.</span><span class="sxs-lookup"><span data-stu-id="f8bba-169">Describing how to marshal method parameters when interoperating with native code.</span></span> <span data-ttu-id="f8bba-170">자세한 내용은 <xref:System.Runtime.InteropServices.MarshalAsAttribute>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-170">For more information, see <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>
- <span data-ttu-id="f8bba-171">클래스, 메서드 및 인터페이스에 대한 COM 속성 설명</span><span class="sxs-lookup"><span data-stu-id="f8bba-171">Describing the COM properties for classes, methods, and interfaces.</span></span>
- <span data-ttu-id="f8bba-172"><xref:System.Runtime.InteropServices.DllImportAttribute> 클래스를 사용하는 비관리 코드 호출</span><span class="sxs-lookup"><span data-stu-id="f8bba-172">Calling unmanaged code using the <xref:System.Runtime.InteropServices.DllImportAttribute> class.</span></span>
- <span data-ttu-id="f8bba-173">제목, 버전, 설명 또는 상표를 기준으로 어셈블리 설명</span><span class="sxs-lookup"><span data-stu-id="f8bba-173">Describing your assembly in terms of title, version, description, or trademark.</span></span>
- <span data-ttu-id="f8bba-174">지속성을 위해 serialize할 클래스의 멤버 설명</span><span class="sxs-lookup"><span data-stu-id="f8bba-174">Describing which members of a class to serialize for persistence.</span></span>
- <span data-ttu-id="f8bba-175">XML serialization를 위해 클래스 멤버 및 XML 노드 간을 매핑하는 방법 설명</span><span class="sxs-lookup"><span data-stu-id="f8bba-175">Describing how to map between class members and XML nodes for XML serialization.</span></span>
- <span data-ttu-id="f8bba-176">메서드에 대한 보안 요구 사항 설명</span><span class="sxs-lookup"><span data-stu-id="f8bba-176">Describing the security requirements for methods.</span></span>
- <span data-ttu-id="f8bba-177">보안을 적용하는 데 사용되는 특징 지정</span><span class="sxs-lookup"><span data-stu-id="f8bba-177">Specifying characteristics used to enforce security.</span></span>
- <span data-ttu-id="f8bba-178">코드를 쉽게 디버그할 수 있도록 하기 위해 JIT(Just-In-Time) 컴파일러를 통해 최적화 제어</span><span class="sxs-lookup"><span data-stu-id="f8bba-178">Controlling optimizations by the just-in-time (JIT) compiler so the code remains easy to debug.</span></span>
- <span data-ttu-id="f8bba-179">메서드 호출자에 대한 정보 얻기</span><span class="sxs-lookup"><span data-stu-id="f8bba-179">Obtaining information about the caller to a method.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f8bba-180">관련 단원</span><span class="sxs-lookup"><span data-stu-id="f8bba-180">Related sections</span></span>

<span data-ttu-id="f8bba-181">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f8bba-181">For more information, see:</span></span>

- [<span data-ttu-id="f8bba-182">사용자 지정 특성 만들기(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-182">Creating Custom Attributes (C#)</span></span>](creating-custom-attributes.md)  
- [<span data-ttu-id="f8bba-183">리플렉션을 사용하여 특성 액세스(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-183">Accessing Attributes by Using Reflection (C#)</span></span>](accessing-attributes-by-using-reflection.md)  
- [<span data-ttu-id="f8bba-184">특성(C#)을 사용하여 C/C++ 공용 구조체를 만드는 방법</span><span class="sxs-lookup"><span data-stu-id="f8bba-184">How to create a C/C++ union by using attributes (C#)</span></span>](how-to-create-a-c-cpp-union-by-using-attributes.md)  
- [<span data-ttu-id="f8bba-185">공통 특성(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-185">Common Attributes (C#)</span></span>](../../../language-reference/attributes/global.md)  
- [<span data-ttu-id="f8bba-186">호출자 정보(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-186">Caller Information (C#)</span></span>](../../../language-reference/attributes/caller-information.md)  

## <a name="see-also"></a><span data-ttu-id="f8bba-187">참조</span><span class="sxs-lookup"><span data-stu-id="f8bba-187">See also</span></span>

- [<span data-ttu-id="f8bba-188">C# 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="f8bba-188">C# Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="f8bba-189">리플렉션(C#)</span><span class="sxs-lookup"><span data-stu-id="f8bba-189">Reflection (C#)</span></span>](../reflection.md)
- [<span data-ttu-id="f8bba-190">특성</span><span class="sxs-lookup"><span data-stu-id="f8bba-190">Attributes</span></span>](../../../../standard/attributes/index.md)
- [<span data-ttu-id="f8bba-191">C#에서 특성 사용</span><span class="sxs-lookup"><span data-stu-id="f8bba-191">Using Attributes in C#</span></span>](../../../tutorials/attributes.md)
