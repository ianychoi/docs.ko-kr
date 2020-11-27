---
title: <Method> 요소 (.NET 네이티브)
ms.date: 03/30/2017
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
ms.openlocfilehash: 1d57457c90e44c70caa301eccc02c5831d283cea
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96287906"
---
# <a name="method-element-net-native"></a><span data-ttu-id="11dff-102">\<Method> 요소 (.NET 네이티브)</span><span class="sxs-lookup"><span data-stu-id="11dff-102">\<Method> Element (.NET Native)</span></span>

<span data-ttu-id="11dff-103">생성자 또는 메서드에 런타임 리플렉션 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-103">Applies runtime reflection policy to a constructor or method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11dff-104">구문</span><span class="sxs-lookup"><span data-stu-id="11dff-104">Syntax</span></span>  
  
```xml  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="11dff-105">특성 및 요소</span><span class="sxs-lookup"><span data-stu-id="11dff-105">Attributes and Elements</span></span>  

 <span data-ttu-id="11dff-106">다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="11dff-107">특성</span><span class="sxs-lookup"><span data-stu-id="11dff-107">Attributes</span></span>  
  
|<span data-ttu-id="11dff-108">attribute</span><span class="sxs-lookup"><span data-stu-id="11dff-108">Attribute</span></span>|<span data-ttu-id="11dff-109">특성 유형</span><span class="sxs-lookup"><span data-stu-id="11dff-109">Attribute type</span></span>|<span data-ttu-id="11dff-110">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-110">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="11dff-111">일반</span><span class="sxs-lookup"><span data-stu-id="11dff-111">General</span></span>|<span data-ttu-id="11dff-112">필수 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-112">Required attribute.</span></span> <span data-ttu-id="11dff-113">메서드 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-113">Specifies the method name.</span></span>|  
|`Signature`|<span data-ttu-id="11dff-114">일반</span><span class="sxs-lookup"><span data-stu-id="11dff-114">General</span></span>|<span data-ttu-id="11dff-115">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-115">Optional attribute.</span></span> <span data-ttu-id="11dff-116">메서드 시그니처를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-116">Specifies the method signature.</span></span> <span data-ttu-id="11dff-117">매개 변수가 여러 개이면 쉼표로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-117">If multiple parameters are present, they are separated by commas.</span></span> <span data-ttu-id="11dff-118">예를 들어 다음 `<Method>` 요소는 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> 메서드에 대한 정책을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-118">For example, the following `<Method>` element defines policy for the <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29> method.</span></span><br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> <span data-ttu-id="11dff-119">특성이 없으면 런타임 지시문은 메서드의 모든 오버로드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-119">If the attribute is absent, the runtime directive applies to all overloads of the method.</span></span>|  
|`Browse`|<span data-ttu-id="11dff-120">반사</span><span class="sxs-lookup"><span data-stu-id="11dff-120">Reflection</span></span>|<span data-ttu-id="11dff-121">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-121">Optional attribute.</span></span> <span data-ttu-id="11dff-122">메서드에 대한 정보 쿼리 또는 메서드 열거는 제어하지만 런타임에 동적 호출을 사용하도록 설정하지는 않습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-122">Controls querying for information about or enumerating a method but does not enable any dynamic invocation at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="11dff-123">반사</span><span class="sxs-lookup"><span data-stu-id="11dff-123">Reflection</span></span>|<span data-ttu-id="11dff-124">선택적 특성입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-124">Optional attribute.</span></span> <span data-ttu-id="11dff-125">동적 프로그래밍을 수행할 수 있도록 생성자 또는 메서드에 대한 런타임 액세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-125">Controls runtime access to a constructor or method to enable dynamic programming.</span></span> <span data-ttu-id="11dff-126">이 정책을 사용하면 런타임에 멤버를 동적으로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-126">This policy ensures that a member can be invoked dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="11dff-127">Name 특성</span><span class="sxs-lookup"><span data-stu-id="11dff-127">Name attribute</span></span>  
  
|<span data-ttu-id="11dff-128">값</span><span class="sxs-lookup"><span data-stu-id="11dff-128">Value</span></span>|<span data-ttu-id="11dff-129">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11dff-130">*method_name*</span><span class="sxs-lookup"><span data-stu-id="11dff-130">*method_name*</span></span>|<span data-ttu-id="11dff-131">메서드 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-131">The method name.</span></span> <span data-ttu-id="11dff-132">메서드의 형식은 부모 [\<Type>](type-element-net-native.md) 또는 요소로 정의 됩니다 [\<TypeInstantiation>](typeinstantiation-element-net-native.md) .</span><span class="sxs-lookup"><span data-stu-id="11dff-132">The type of the method is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="signature-attribute"></a><span data-ttu-id="11dff-133">시그니처 특성</span><span class="sxs-lookup"><span data-stu-id="11dff-133">Signature attribute</span></span>  
  
|<span data-ttu-id="11dff-134">값</span><span class="sxs-lookup"><span data-stu-id="11dff-134">Value</span></span>|<span data-ttu-id="11dff-135">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11dff-136">*method_signature*</span><span class="sxs-lookup"><span data-stu-id="11dff-136">*method_signature*</span></span>|<span data-ttu-id="11dff-137">메서드 시그니처를 구성하는 매개 변수 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-137">The parameter types that form the method signature.</span></span> <span data-ttu-id="11dff-138">매개 변수가 여러 개이면 `"System.String,System.Int32,System.Int32)"`와 같이 쉼표로 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-138">Multiple parameters are separated by commas, for example, `"System.String,System.Int32,System.Int32)"`.</span></span> <span data-ttu-id="11dff-139">매개 변수 형식 이름은 정규화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-139">Parameter type names should be fully qualified.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="11dff-140">기타 모든 특성</span><span class="sxs-lookup"><span data-stu-id="11dff-140">All other attributes</span></span>  
  
|<span data-ttu-id="11dff-141">값</span><span class="sxs-lookup"><span data-stu-id="11dff-141">Value</span></span>|<span data-ttu-id="11dff-142">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="11dff-143">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="11dff-143">*policy_setting*</span></span>|<span data-ttu-id="11dff-144">이 정책 형식에 적용할 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-144">The setting to apply to this policy type.</span></span> <span data-ttu-id="11dff-145">가능한 값은 `Auto`, `Excluded`, `Included` 및 `Required`입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-145">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="11dff-146">자세한 내용은 [런타임 지시문 정책 설정](runtime-directive-policy-settings.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="11dff-146">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="11dff-147">자식 요소</span><span class="sxs-lookup"><span data-stu-id="11dff-147">Child Elements</span></span>  
  
|<span data-ttu-id="11dff-148">요소</span><span class="sxs-lookup"><span data-stu-id="11dff-148">Element</span></span>|<span data-ttu-id="11dff-149">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-149">Description</span></span>|  
|-------------|-----------------|  
|[\<Parameter>](parameter-element-net-native.md)|<span data-ttu-id="11dff-150">메서드에 전달된 인수의 형식에 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-150">Applies policy to the type of the argument passed to a method.</span></span>|  
|[\<GenericParameter>](genericparameter-element-net-native.md)|<span data-ttu-id="11dff-151">제네릭 형식 또는 메서드의 매개 변수 형식에 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-151">Applies policy to the parameter type of a generic type or method.</span></span>|  
|[\<ImpliesType>](impliestype-element-net-native.md)|<span data-ttu-id="11dff-152">포함 `<Method>` 요소가 나타내는 메서드에 정책이 적용된 경우 형식에 해당 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-152">Applies policy to a type, if that policy has been applied to the method represented by the containing `<Method>` element.</span></span>|  
|[\<TypeParameter>](typeparameter-element-net-native.md)|<span data-ttu-id="11dff-153">메서드로 전달된 <xref:System.Type> 인수가 나타내는 형식에 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-153">Applies policy to the type represented by a <xref:System.Type> argument passed to a method.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="11dff-154">부모 요소</span><span class="sxs-lookup"><span data-stu-id="11dff-154">Parent Elements</span></span>  
  
|<span data-ttu-id="11dff-155">요소</span><span class="sxs-lookup"><span data-stu-id="11dff-155">Element</span></span>|<span data-ttu-id="11dff-156">Description</span><span class="sxs-lookup"><span data-stu-id="11dff-156">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="11dff-157">형식 및 모든 해당 멤버에 리플렉션 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-157">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="11dff-158">생성된 제네릭 형식 및 모든 해당 멤버에 리플렉션 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-158">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11dff-159">설명</span><span class="sxs-lookup"><span data-stu-id="11dff-159">Remarks</span></span>  

 <span data-ttu-id="11dff-160">제네릭 메서드의 `<Method>` 요소는 자체 정책이 없는 모든 인스턴스화에 해당 정책을 적용합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-160">A `<Method>` element of a generic method applies its policy to all instantiations that do not have their own policy.</span></span>  
  
 <span data-ttu-id="11dff-161">`Signature` 특성을 사용하여 특정 메서드 오버로드에 대한 정책을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-161">You can use the `Signature` attribute to specify policy for a particular method overload.</span></span> <span data-ttu-id="11dff-162">`Signature` 특성이 없는 경우 런타임 지시문은 메서드의 모든 오버로드에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-162">Otherwise, if the `Signature` attribute is absent, the runtime directive applies to all overloads of the method.</span></span>  
  
 <span data-ttu-id="11dff-163">`<Method>` 요소를 사용하여 생성자에 대해 런타임 리플렉션 정책을 정의할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-163">You cannot define the runtime reflection policy for a constructor by using the `<Method>` element.</span></span> <span data-ttu-id="11dff-164">대신,, `Activate` 또는 요소의 특성을  [\<Assembly>](assembly-element-net-native.md) 사용 [\<Namespace>](namespace-element-net-native.md) [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 합니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-164">Instead, use the `Activate` attribute of the  [\<Assembly>](assembly-element-net-native.md), [\<Namespace>](namespace-element-net-native.md), [\<Type>](type-element-net-native.md), or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11dff-165">예제</span><span class="sxs-lookup"><span data-stu-id="11dff-165">Example</span></span>  

 <span data-ttu-id="11dff-166">다음 예제의 `Stringify` 메서드는 리플렉션을 사용하여 개체를 문자열 표현으로 변환하는 범용 서식 지정 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-166">The `Stringify` method in the following example is a general-purpose formatting method that uses reflection to convert an object to its string representation.</span></span> <span data-ttu-id="11dff-167">이 메서드는 개체의 기본 `ToString` 메서드를 호출할 수 있을 뿐 아니라 개체의 `ToString` 메서드에 서식 문자열이나 <xref:System.IFormatProvider> 구현 중 하나 또는 둘 다를 전달하여 서식이 지정된 결과 문자열을 생성할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-167">In addition to calling the object's default `ToString` method, the method can produce a formatted result string by passing an object's `ToString` method a format string, an <xref:System.IFormatProvider> implementation, or both.</span></span> <span data-ttu-id="11dff-168">또한 숫자를 이진, 16진수 또는 8진수 표현으로 변환하는 <xref:System.Convert.ToString%2A?displayProperty=nameWithType> 오버로드 중 하나를 호출할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-168">It can also call one of the <xref:System.Convert.ToString%2A?displayProperty=nameWithType> overloads that converts a number to its binary, hexadecimal, or octal representation.</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="11dff-169">다음과 같은 코드를 통해 `Stringify` 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-169">The `Stringify` method can be called by code like the following:</span></span>  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 <span data-ttu-id="11dff-170">그러나 이 예제를 .NET 네이티브에서 컴파일하면 런타임에 <xref:System.NullReferenceException> 및 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 예외를 비롯한 여러 예외가 throw될 수 있습니다. 이러한 예외가 throw되는 이유는, `Stringify` 메서드는 기본적으로 .NET Framework 클래스 라이브러리의 기본 형식에 대한 동적 서식 지정을 지원하는 데 사용되는데</span><span class="sxs-lookup"><span data-stu-id="11dff-170">However, when compiled with .NET Native, the example can throw an number of exceptions at runtime, including <xref:System.NullReferenceException> and [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions, This occurs because the `Stringify` method is intended primarily to support dynamically formatting the primitive types in the .NET Framework Class Library.</span></span> <span data-ttu-id="11dff-171">기본 지시문 파일이 해당 메타데이터를 제공하지 않기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-171">However, their metadata is not made available by the default directives file.</span></span> <span data-ttu-id="11dff-172">그러나 메타데이터가 제공되더라도 위의 예제에서는 [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 예외가 throw됩니다. 적절한 `ToString` 구현이 네이티브 코드에 포함되지 않았기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-172">Even when their metadata is made available, however, the example throws [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) exceptions because the appropriate `ToString` implementations have not been include in the native code.</span></span>  
  
 <span data-ttu-id="11dff-173">이러한 예외는 요소를 사용 하 여 [\<Type>](type-element-net-native.md) 메타 데이터가 있어야 하는 형식을 정의 하 고, 요소를 추가 하 여 `<Method>` 동적으로 호출할 수 있는 메서드 오버 로드의 구현도 있는지 확인 하는 방법으로 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-173">These exceptions can all be eliminated by using the [\<Type>](type-element-net-native.md) element to define the types whose metadata must be present, and by adding `<Method>` elements to ensure that the implementation of method overloads that can be called dynamically is also present.</span></span> <span data-ttu-id="11dff-174">다음은 이러한 예외를 방지하고 예제가 오류 없이 실행되도록 하는 default.rd.xml 파일입니다.</span><span class="sxs-lookup"><span data-stu-id="11dff-174">The following is the default.rd.xml file that eliminates these exceptions and allows the example to execute without error.</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a><span data-ttu-id="11dff-175">참고 항목</span><span class="sxs-lookup"><span data-stu-id="11dff-175">See also</span></span>

- [<span data-ttu-id="11dff-176">런타임 지시문(rd.xml) 구성 파일 참조</span><span class="sxs-lookup"><span data-stu-id="11dff-176">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="11dff-177">런타임 지시문 요소</span><span class="sxs-lookup"><span data-stu-id="11dff-177">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="11dff-178">런타임 지시문 정책 설정</span><span class="sxs-lookup"><span data-stu-id="11dff-178">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
- [<span data-ttu-id="11dff-179">\<MethodInstantiation> 요소</span><span class="sxs-lookup"><span data-stu-id="11dff-179">\<MethodInstantiation> Element</span></span>](methodinstantiation-element-net-native.md)
