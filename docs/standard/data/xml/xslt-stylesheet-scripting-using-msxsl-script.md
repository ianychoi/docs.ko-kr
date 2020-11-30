---
title: <msxsl:script>를 사용한 XSLT 스타일시트 스크립팅
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 60e2541b-0cea-4b2e-a4fa-85f4c50f1bef
ms.openlocfilehash: 206a659656f1019af1540b9b2476ae7fe9ba93eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685112"
---
# <a name="xslt-stylesheet-scripting-using-msxslscript"></a><span data-ttu-id="55d9a-102">\<msxsl:script>를 사용한 XSLT 스타일시트 스크립팅</span><span class="sxs-lookup"><span data-stu-id="55d9a-102">XSLT Stylesheet Scripting Using \<msxsl:script></span></span>

<span data-ttu-id="55d9a-103"><xref:System.Xml.Xsl.XslTransform> 클래스는 `script` 요소를 사용하여 포함 스크립트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-103">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55d9a-104"><xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 2.0에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-104">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="55d9a-105"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT(Extensible Stylesheet Language for Transformations) 변환을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-105">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="55d9a-106">자세한 내용은 [XslCompiledTransform 클래스 사용](using-the-xslcompiledtransform-class.md) 및 [XslTransform 클래스에서 마이그레이션](migrating-from-the-xsltransform-class.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55d9a-106">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="55d9a-107"><xref:System.Xml.Xsl.XslTransform> 클래스는 `script` 요소를 사용하여 포함 스크립트를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-107">The <xref:System.Xml.Xsl.XslTransform> class supports embedded scripting using the `script` element.</span></span> <span data-ttu-id="55d9a-108">스타일시트가 로드될 때 정의된 모든 함수는 클래스 정의에서 래핑되어 MSIL(Microsoft Intermediate Language)로 컴파일되므로 성능이 저하되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-108">When the style sheet is loaded, any defined functions are compiled to Microsoft intermediate language (MSIL) by being wrapped in a class definition and have no performance loss as a result.</span></span>  
  
 <span data-ttu-id="55d9a-109">`<msxsl:script>` 요소는 다음에 정의되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-109">The `<msxsl:script>` element is defined below:</span></span>  
  
```xml  
<msxsl:script language = "language-name" implements-prefix = "prefix of user namespace"> </msxsl:script>  
```  
  
 <span data-ttu-id="55d9a-110">여기서 `msxsl`은 네임스페이스 `urn:schemas-microsoft-com:xslt`에 바인딩되는 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-110">where `msxsl` is a prefix bound to the namespace `urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="55d9a-111">`language` 특성은 필수 항목은 아니지만, 지정할 경우 값은 `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic` 또는 `CSharp` 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-111">The `language` attribute is not mandatory, but if specified, its value must be one of the following: `C#`, `VB`, `JScript`, `JavaScript`, `VisualBasic`, or `CSharp`.</span></span> <span data-ttu-id="55d9a-112">지정하지 않을 경우 언어 기본값은 JScript입니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-112">If not specified, the language defaults to JScript.</span></span> <span data-ttu-id="55d9a-113">`language-name`은 대/소문자를 구분하지 않으므로 'JavaScript'와 'javascript'는 같습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-113">The `language-name` is not case-sensitive, so 'JavaScript' and 'javascript' are equivalent.</span></span>  
  
 <span data-ttu-id="55d9a-114">`implements-prefix` 특성은 필수 항목입니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-114">The `implements-prefix` attribute is mandatory.</span></span> <span data-ttu-id="55d9a-115">이 특성은 네임스페이스를 선언하고 스크립트 블록에 연결하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-115">This attribute is used to declare a namespace and associate it with the script block.</span></span> <span data-ttu-id="55d9a-116">이 특성 값은 네임스페이스를 나타내는 접두사입니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-116">The value of this attribute is the prefix that represents the namespace.</span></span> <span data-ttu-id="55d9a-117">이 네임스페이스는 스타일시트에서 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-117">This namespace can be defined somewhere in a style sheet.</span></span>  
  
 <span data-ttu-id="55d9a-118">`msxsl:script` 요소가 네임스페이스 `urn:schemas-microsoft-com:xslt`에 속하기 때문에 스타일시트에는 네임스페이스 선언 `xmlns:msxsl=urn:schemas-microsoft-com:xslt`가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-118">Because the `msxsl:script` element belongs to the namespace `urn:schemas-microsoft-com:xslt`, the style sheet must include the namespace declaration `xmlns:msxsl=urn:schemas-microsoft-com:xslt`.</span></span>  
  
 <span data-ttu-id="55d9a-119">스크립트의 호출자에게 <xref:System.Security.Permissions.SecurityPermissionFlag> 액세스 권한이 없으면 스타일시트의 스크립트는 컴파일되지 않으며 <xref:System.Xml.Xsl.XslTransform.Load%2A>에 대한 호출도 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-119">If the caller of the script does not have <xref:System.Security.Permissions.SecurityPermissionFlag> access permission, then the script in a style sheet will never compile and the call to <xref:System.Xml.Xsl.XslTransform.Load%2A> will fail.</span></span>  
  
 <span data-ttu-id="55d9a-120">호출자에게 `UnmanagedCode` 권한이 없는 경우에는 스크립트가 컴파일되지만 로드할 때 제공된 증명 정보에 따라 허용되는 작업이 결정됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-120">If the caller has `UnmanagedCode` permission, the script compiles, but the operations that are allowed are dependent on the evidence that is supplied at load time.</span></span>  
  
 <span data-ttu-id="55d9a-121"><xref:System.Xml.Xsl.XslTransform.Load%2A> 또는 <xref:System.Xml.XmlReader>를 사용하는 <xref:System.Xml.XPath.XPathNavigator> 메서드 중 하나를 사용하여 스타일시트를 로드하는 경우 <xref:System.Xml.Xsl.XslTransform.Load%2A> 매개 변수를 인수 중 하나로 사용하는 <xref:System.Security.Policy.Evidence> 오버로드를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-121">If you are using one of the <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlReader> or <xref:System.Xml.XPath.XPathNavigator> to load the style sheet, you need to use the <xref:System.Xml.Xsl.XslTransform.Load%2A> overload that takes an <xref:System.Security.Policy.Evidence> parameter as one of its arguments.</span></span> <span data-ttu-id="55d9a-122">증명 정보를 제공하려는 경우 호출자는 <xref:System.Security.Permissions.SecurityPermissionFlag> 권한이 있어야 스크립트 어셈블리에 대한 `Evidence`를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-122">To provide evidence, the caller must have <xref:System.Security.Permissions.SecurityPermissionFlag> permission to supply `Evidence` for the script assembly.</span></span> <span data-ttu-id="55d9a-123">호출자에게 이 권한이 없으면 `Evidence` 매개 변수를 `null`로 설정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-123">If the caller does not have this permission, then they can set the `Evidence` parameter to `null`.</span></span> <span data-ttu-id="55d9a-124">그러면 <xref:System.Xml.Xsl.XslTransform.Load%2A> 함수는 스크립트를 찾는 데 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-124">This causes the <xref:System.Xml.Xsl.XslTransform.Load%2A> function to fail if it finds script.</span></span> <span data-ttu-id="55d9a-125">`ControlEvidence` 권한은 충분히 신뢰할 수 있는 코드에만 부여되는 매우 강력한 권한으로 간주됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-125">The `ControlEvidence` permission is considered a very powerful permission that should only be granted to highly trusted code.</span></span>  
  
 <span data-ttu-id="55d9a-126">어셈블리에서 증명 정보를 가져오려면 `this.GetType().Assembly.Evidence`를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-126">To get the evidence from your assembly, use `this.GetType().Assembly.Evidence`.</span></span> <span data-ttu-id="55d9a-127">URI(Uniform Resource Identifier)에서 증명 정보를 가져오려면 `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-127">To get the evidence from a Uniform Resource Identifier (URI), use `Evidence e = XmlSecureResolver.CreateEvidenceForUrl(stylesheetURI)`.</span></span>  
  
 <span data-ttu-id="55d9a-128"><xref:System.Xml.Xsl.XslTransform.Load%2A>가 아닌 <xref:System.Xml.XmlResolver>를 사용하는 `Evidence` 메서드를 사용하는 경우 어셈블리의 보안 영역은 기본적으로 Full Trust가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-128">If you use <xref:System.Xml.Xsl.XslTransform.Load%2A> methods that take an <xref:System.Xml.XmlResolver> but no `Evidence`, the security zone for the assembly defaults to Full Trust.</span></span> <span data-ttu-id="55d9a-129">자세한 내용은 <xref:System.Security.SecurityZone> 및 [명명된 권한 집합](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100))을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="55d9a-129">For more information, see <xref:System.Security.SecurityZone> and [Named Permission Sets](/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).</span></span>  
  
 <span data-ttu-id="55d9a-130">함수는 `msxsl:script` 요소 내에서 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-130">Functions can be declared within the `msxsl:script` element.</span></span> <span data-ttu-id="55d9a-131">다음 표에서는 기본적으로 지원되는 네임스페이스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-131">The following table shows the namespaces that are supported by default.</span></span> <span data-ttu-id="55d9a-132">나열된 네임스페이스 외부에 있는 클래스는 사용할 수 있지만,</span><span class="sxs-lookup"><span data-stu-id="55d9a-132">You can use classes outside the listed namespaces.</span></span> <span data-ttu-id="55d9a-133">정규화되어야만 사용 가능합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-133">However, these classes must be fully qualified.</span></span>  
  
|<span data-ttu-id="55d9a-134">기본 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="55d9a-134">Default Namespaces</span></span>|<span data-ttu-id="55d9a-135">설명</span><span class="sxs-lookup"><span data-stu-id="55d9a-135">Description</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="55d9a-136">시스템</span><span class="sxs-lookup"><span data-stu-id="55d9a-136">System</span></span>|<span data-ttu-id="55d9a-137">System 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-137">System class.</span></span>|  
|<span data-ttu-id="55d9a-138">System.Collection</span><span class="sxs-lookup"><span data-stu-id="55d9a-138">System.Collection</span></span>|<span data-ttu-id="55d9a-139">Collection 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-139">Collection classes.</span></span>|  
|<span data-ttu-id="55d9a-140">System.Text</span><span class="sxs-lookup"><span data-stu-id="55d9a-140">System.Text</span></span>|<span data-ttu-id="55d9a-141">Text 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-141">Text classes.</span></span>|  
|<span data-ttu-id="55d9a-142">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="55d9a-142">System.Text.RegularExpressions</span></span>|<span data-ttu-id="55d9a-143">정규식 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-143">Regular expression classes.</span></span>|  
|<span data-ttu-id="55d9a-144">System.Xml</span><span class="sxs-lookup"><span data-stu-id="55d9a-144">System.Xml</span></span>|<span data-ttu-id="55d9a-145">핵심 XML 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-145">Core XML classes.</span></span>|  
|<span data-ttu-id="55d9a-146">System.Xml.Xsl</span><span class="sxs-lookup"><span data-stu-id="55d9a-146">System.Xml.Xsl</span></span>|<span data-ttu-id="55d9a-147">XSLT 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-147">XSLT classes.</span></span>|  
|<span data-ttu-id="55d9a-148">System.Xml.XPath</span><span class="sxs-lookup"><span data-stu-id="55d9a-148">System.Xml.XPath</span></span>|<span data-ttu-id="55d9a-149">XPath(XML Path Language) 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-149">XML Path Language (XPath) classes.</span></span>|  
|<span data-ttu-id="55d9a-150">Microsoft.VisualBasic</span><span class="sxs-lookup"><span data-stu-id="55d9a-150">Microsoft.VisualBasic</span></span>|<span data-ttu-id="55d9a-151">Microsoft Visual Basic 스크립트용 클래스</span><span class="sxs-lookup"><span data-stu-id="55d9a-151">Classes for Microsoft Visual Basic scripts.</span></span>|  
  
 <span data-ttu-id="55d9a-152">함수를 선언하면 해당 함수는 스크립트 블록 내에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-152">When a function is declared, it is contained in a script block.</span></span> <span data-ttu-id="55d9a-153">스타일시트에는 여러 스크립트 블록이 포함될 수 있으며 각 블록은 서로 독립적으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-153">Style sheets can contain multiple script blocks, each operating independent of the other.</span></span> <span data-ttu-id="55d9a-154">즉, 스크립트 블록 내부에서 실행할 경우 같은 네임스페이스와 같은 스크립트 언어를 사용하도록 선언된 경우에만 다른 스크립트 블록에 정의된 함수를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-154">That means that if you are executing inside a script block, you cannot call a function that you defined in another script block unless it is declared to have the same namespace and the same scripting language.</span></span> <span data-ttu-id="55d9a-155">각 스크립트 블록에서는 서로 다른 언어를 사용할 수 있고, 블록은 해당 언어 파서의 문법 규칙에 따라 구문 분석되기 때문에 사용하는 언어의 올바른 구문을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-155">Because each script block can be in its own language, and the block is parsed according to the grammar rules of that language parser, you must use the correct syntax for the language in use.</span></span> <span data-ttu-id="55d9a-156">예를 들어, C# 스크립트 블록에서 XML comment 노드 `<!-- an XML comment -->`를 사용하면 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-156">For example, if you are in a C# script block, then it is an error to use an XML comment node `<!-- an XML comment -->` in the block.</span></span>  
  
 <span data-ttu-id="55d9a-157">스크립트 함수에 정의된 인수와 반환 값은 W3C(World Wide Web 컨소시엄) XPath 또는 XSLT 형식 중 하나여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-157">The supplied arguments and return values defined by the script functions must be one of the World Wide Web Consortium (W3C) XPath or XSLT types.</span></span> <span data-ttu-id="55d9a-158">다음 표에서는 해당하는 W3C 형식과 해당 .NET Framework 클래스(형식), W3C 형식이 XPath 형식인지 아니면 XSLT 형식인지를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-158">The following table shows the corresponding W3C types, the equivalent .NET Framework classes (Type), and whether the W3C type is an XPath type or XSLT type.</span></span>  
  
|<span data-ttu-id="55d9a-159">형식</span><span class="sxs-lookup"><span data-stu-id="55d9a-159">Type</span></span>|<span data-ttu-id="55d9a-160">해당 .NET Framework 클래스(형식)</span><span class="sxs-lookup"><span data-stu-id="55d9a-160">Equivalent .NET Framework Class (Type)</span></span>|<span data-ttu-id="55d9a-161">XPath 형식 또는 XSLT 형식</span><span class="sxs-lookup"><span data-stu-id="55d9a-161">XPath type or XSLT type</span></span>|  
|----------|----------------------------------------------|-----------------------------|  
|<span data-ttu-id="55d9a-162">String</span><span class="sxs-lookup"><span data-stu-id="55d9a-162">String</span></span>|<span data-ttu-id="55d9a-163">System.String</span><span class="sxs-lookup"><span data-stu-id="55d9a-163">System.String</span></span>|<span data-ttu-id="55d9a-164">XPath</span><span class="sxs-lookup"><span data-stu-id="55d9a-164">XPath</span></span>|  
|<span data-ttu-id="55d9a-165">부울</span><span class="sxs-lookup"><span data-stu-id="55d9a-165">Boolean</span></span>|<span data-ttu-id="55d9a-166">System.Boolean</span><span class="sxs-lookup"><span data-stu-id="55d9a-166">System.Boolean</span></span>|<span data-ttu-id="55d9a-167">XPath</span><span class="sxs-lookup"><span data-stu-id="55d9a-167">XPath</span></span>|  
|<span data-ttu-id="55d9a-168">수</span><span class="sxs-lookup"><span data-stu-id="55d9a-168">Number</span></span>|<span data-ttu-id="55d9a-169">System.Double</span><span class="sxs-lookup"><span data-stu-id="55d9a-169">System.Double</span></span>|<span data-ttu-id="55d9a-170">XPath</span><span class="sxs-lookup"><span data-stu-id="55d9a-170">XPath</span></span>|  
|<span data-ttu-id="55d9a-171">결과 트리 조각</span><span class="sxs-lookup"><span data-stu-id="55d9a-171">Result Tree Fragment</span></span>|<span data-ttu-id="55d9a-172">System.Xml.XPath.XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="55d9a-172">System.Xml.XPath.XPathNavigator</span></span>|<span data-ttu-id="55d9a-173">XSLT</span><span class="sxs-lookup"><span data-stu-id="55d9a-173">XSLT</span></span>|  
|<span data-ttu-id="55d9a-174">노드 집합</span><span class="sxs-lookup"><span data-stu-id="55d9a-174">Node Set</span></span>|<span data-ttu-id="55d9a-175">System.Xml.XPath.XPathNodeIterator</span><span class="sxs-lookup"><span data-stu-id="55d9a-175">System.Xml.XPath.XPathNodeIterator</span></span>|<span data-ttu-id="55d9a-176">XPath</span><span class="sxs-lookup"><span data-stu-id="55d9a-176">XPath</span></span>|  
  
 <span data-ttu-id="55d9a-177">스크립트 함수가 다음 숫자 유형 중 하나를 사용하는 경우: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single 또는 Decimal의 경우 W3C XPath 형식 숫자에 매핑되는 Double이 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-177">If the script function utilizes one of the following numeric types: Int16, UInt16, Int32, UInt32, Int64, UInt64, Single, or Decimal, they are forced to Double, which maps to the W3C XPath type number.</span></span> <span data-ttu-id="55d9a-178">기타 모든 형식은 `ToString` 메서드 호출을 통해 문자열 형식이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-178">All other types are forced to a string by calling the `ToString` method.</span></span>  
  
 <span data-ttu-id="55d9a-179">스크립트 함수에서 위에 설명되어 있지 않은 형식을 사용하거나 스타일시트를 <xref:System.Xml.Xsl.XslTransform> 개체에 로드할 때 함수가 컴파일되지 않으면 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-179">If the script function utilizes a type other than the ones mentioned above, or if the function does not compile when the style sheet is loaded into the <xref:System.Xml.Xsl.XslTransform> object, an exception is thrown.</span></span>  
  
 <span data-ttu-id="55d9a-180">`msxsl:script` 요소를 사용하는 경우에는 언어에 관계없이 스크립트를 CDATA 섹션에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-180">When using the `msxsl:script` element, it is highly recommended that the script, regardless of language, be placed inside a CDATA section.</span></span> <span data-ttu-id="55d9a-181">예를 들어, 다음 XML에서는 코드를 배치할 CDATA 섹션 템플릿을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-181">For example, the following XML shows the template of the CDATA section where your code is placed.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    <![CDATA[  
    ... your code here ...  
    ]]>  
</msxsl:script>  
```  
  
 <span data-ttu-id="55d9a-182">지정된 언어의 연산자, 식별자 또는 구분자가 XML로 잘못 해석될 위험이 있으므로 스크립트 내용을 CDATA 섹션에 배치하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-182">It is highly recommended that all script content be placed in a CDATA section, because operators, identifiers, or delimiters for a given language have the potential of being misinterpreted as XML.</span></span> <span data-ttu-id="55d9a-183">다음 예제에서는 스크립트에서 논리곱 연산자를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-183">The following example shows the use of the logical AND operator in script.</span></span>  
  
```xml  
<msxsl:script implements-prefix='yourprefix' language='CSharp'>  
    public string book(string abc, string xyz)  
    {  
        if ((abc == bar) && (abc == xyz)) return bar + xyz;  
        else return null;  
    }  
</msxsl:script>  
```  
  
 <span data-ttu-id="55d9a-184">이 경우 앰퍼샌드가 이스케이프되지 않기 때문에 예외가 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-184">This throws an exception because the ampersands are not escaped.</span></span> <span data-ttu-id="55d9a-185">문서는 XML로 로드되고 `msxsl:script` 요소 태그 사이의 텍스트에는 특별한 작업이 수행되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-185">The document is loaded as XML, and no special treatment is applied to the text between the `msxsl:script` element tags.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55d9a-186">예제</span><span class="sxs-lookup"><span data-stu-id="55d9a-186">Example</span></span>  

 <span data-ttu-id="55d9a-187">다음 예제에서는 포함 스크립트를 사용하여 주어진 반지름으로 원의 원주를 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="55d9a-187">The following example uses an embedded script to calculate the circumference of a circle given its radius.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.XPath  
Imports System.Xml.Xsl  
  
Public Class Sample  
  
   Private Const filename As String = "number.xml"  
   Private Const stylesheet As String = "calc.xsl"  
  
   Public Shared Sub Main()  
  
    'Create the XslTransform and load the style sheet.  
    Dim xslt As XslTransform = New XslTransform  
    xslt.Load(stylesheet)  
  
    'Load the XML data file.  
    Dim doc As XPathDocument = New XPathDocument(filename)  
  
    'Create an XmlTextWriter to output to the console.
    Dim writer As XmlTextWriter = New XmlTextWriter(Console.Out)  
    writer.Formatting = Formatting.Indented  
  
    'Transform the file.  
    xslt.Transform(doc, Nothing, writer, Nothing)  
    writer.Close()  
  End Sub
End Class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
  
public class Sample  
{  
   private const String filename = "number.xml";  
   private const String stylesheet = "calc.xsl";  
  
   public static void Main()  
   {  
    //Create the XslTransform and load the style sheet.  
    XslTransform xslt = new XslTransform();  
    xslt.Load(stylesheet);  
  
    //Load the XML data file.  
    XPathDocument doc = new XPathDocument(filename);  
  
    //Create an XmlTextWriter to output to the console.
    XmlTextWriter writer = new XmlTextWriter(Console.Out);  
    writer.Formatting = Formatting.Indented;  
  
    //Transform the file.  
    xslt.Transform(doc, null, writer, null);  
    writer.Close();  
  }  
}  
```  
  
## <a name="input"></a><span data-ttu-id="55d9a-188">입력</span><span class="sxs-lookup"><span data-stu-id="55d9a-188">Input</span></span>  

 <span data-ttu-id="55d9a-189">number.xml</span><span class="sxs-lookup"><span data-stu-id="55d9a-189">number.xml</span></span>  
  
```xml  
<?xml version='1.0'?>  
<data>  
  <circle>  
    <radius>12</radius>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
  </circle>  
</data>  
```  
  
 <span data-ttu-id="55d9a-190">calc.xsl</span><span class="sxs-lookup"><span data-stu-id="55d9a-190">calc.xsl</span></span>  
  
```xml  
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
    xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
    xmlns:user="urn:my-scripts">  
  
  <msxsl:script language="C#" implements-prefix="user">  
     <![CDATA[  
     public double circumference(double radius)  
     {  
       double pi = 3.14;  
       double circ = pi*radius*2;  
       return circ;  
     }  
      ]]>  
   </msxsl:script>  
  
  <xsl:template match="data">
  <circles>  
  
  <xsl:for-each select="circle">  
    <circle>  
    <xsl:copy-of select="node()"/>  
       <circumference>  
          <xsl:value-of select="user:circumference(radius)"/>
       </circumference>  
    </circle>  
  </xsl:for-each>  
  </circles>  
  </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="55d9a-191">출력</span><span class="sxs-lookup"><span data-stu-id="55d9a-191">Output</span></span>  
  
```xml  
<circles xmlns:msxsl="urn:schemas-microsoft-com:xslt" xmlns:user="urn:my-scripts">  
  <circle>  
    <radius>12</radius>  
    <circumference>75.36</circumference>  
  </circle>  
  <circle>  
    <radius>37.5</radius>  
    <circumference>235.5</circumference>  
  </circle>  
</circles>
```  
  
## <a name="see-also"></a><span data-ttu-id="55d9a-192">참조</span><span class="sxs-lookup"><span data-stu-id="55d9a-192">See also</span></span>

- [<span data-ttu-id="55d9a-193">XslTransform 클래스의 XSLT 프로세서 구현</span><span class="sxs-lookup"><span data-stu-id="55d9a-193">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
