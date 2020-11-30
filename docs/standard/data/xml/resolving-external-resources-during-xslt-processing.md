---
title: XSLT 처리 중 외부 리소스 확인
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3a59d31c-0ec5-4de6-a2a9-558531c8116e
ms.openlocfilehash: 5d50711eda266cecdb817c778f04aa845fa4c342
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686646"
---
# <a name="resolving-external-resources-during-xslt-processing"></a><span data-ttu-id="00188-102">XSLT 처리 중 외부 리소스 확인</span><span class="sxs-lookup"><span data-stu-id="00188-102">Resolving External Resources During XSLT Processing</span></span>

<span data-ttu-id="00188-103">다음과 같이 XSLT 변형 중에 외부 리소스를 확인해야 하는 몇 가지 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-103">There are several times during an XSLT transformation when you may need to resolve external resources.</span></span>  
  
## <a name="using-the-xmlresolver-class"></a><span data-ttu-id="00188-104">XmlResolver 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="00188-104">Using the XmlResolver Class</span></span>  

 <span data-ttu-id="00188-105"><xref:System.Xml.XmlResolver> 클래스를 사용하여 외부 리소스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-105">The <xref:System.Xml.XmlResolver> class is used to resolve external resources.</span></span> <span data-ttu-id="00188-106">다음 표에서는 XSLT 처리 중 <xref:System.Xml.XmlResolver>가 관련되는 경우를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-106">The following table describes when the <xref:System.Xml.XmlResolver> becomes involved during XSLT processing.</span></span>  
  
|<span data-ttu-id="00188-107">XSLT 작업</span><span class="sxs-lookup"><span data-stu-id="00188-107">XSLT task</span></span>|<span data-ttu-id="00188-108">XmlResolver를 사용하여 수행하는 작업</span><span class="sxs-lookup"><span data-stu-id="00188-108">What the XmlResolver is used for</span></span>|  
|---------------|--------------------------------------|  
|<span data-ttu-id="00188-109">스타일시트를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-109">Compile the style sheet.</span></span>|<span data-ttu-id="00188-110">스타일시트의 URI를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-110">Resolve the URI of the style sheet.</span></span><br /><br /> <span data-ttu-id="00188-111">및</span><span class="sxs-lookup"><span data-stu-id="00188-111">-and-</span></span><br /><br /> <span data-ttu-id="00188-112">`xsl:import` 또는 `xsl:include` 요소에서 URI 참조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-112">Resolve URI references in any `xsl:import` or `xsl:include` elements.</span></span>|  
|<span data-ttu-id="00188-113">스타일시트를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-113">Execute the style sheet.</span></span>|<span data-ttu-id="00188-114">컨텍스트 문서의 URI를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-114">Resolve the URI of the context document.</span></span><br /><br /> <span data-ttu-id="00188-115">및</span><span class="sxs-lookup"><span data-stu-id="00188-115">-and-</span></span><br /><br /> <span data-ttu-id="00188-116">XSLT `document()` 함수에서 URI 참조를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-116">Resolve URI references in any XSLT `document()` functions.</span></span>|  
  
 <span data-ttu-id="00188-117"><xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> 및 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> 메서드는 <xref:System.Xml.XmlResolver> 개체를 해당 인수의 하나로 사용하는 오버로드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-117">The <xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> and <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> methods include overloads that take an <xref:System.Xml.XmlResolver> object as one of its arguments.</span></span> <span data-ttu-id="00188-118"><xref:System.Xml.XmlResolver>가 지정되지 않을 경우 기본 <xref:System.Xml.XmlUrlResolver>가 자격 증명 없이 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="00188-118">If an <xref:System.Xml.XmlResolver> is not specified, a default <xref:System.Xml.XmlUrlResolver> with no credentials is used.</span></span>  
  
 <span data-ttu-id="00188-119">다음 목록에서는 <xref:System.Xml.XmlResolver> 개체를 지정하려 할 수 있는 경우에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-119">The following list describes when you may want to specify an <xref:System.Xml.XmlResolver> object:</span></span>  
  
- <span data-ttu-id="00188-120">XSLT 처리에 인증을 요구하는 네트워크 리소스에 대한 액세스 권한이 필요할 경우 <xref:System.Xml.XmlResolver>를 필요한 자격 증명과 함께 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-120">If the XSLT process needs to access a network resource that requires authentication, you can use an <xref:System.Xml.XmlResolver> with the necessary credentials.</span></span>  
  
- <span data-ttu-id="00188-121">XSLT 처리가 액세스할 수 있는 리소스를 제한하려면 <xref:System.Xml.XmlSecureResolver>를 올바른 권한 집합으로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-121">If you want to restrict the resources that the XSLT process can access, you can use an <xref:System.Xml.XmlSecureResolver> with the correct permission set.</span></span> <span data-ttu-id="00188-122">제어하지 못하거나 신뢰할 수 없는 리소스를 열어야 하는 경우 <xref:System.Xml.XmlSecureResolver> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-122">Use the <xref:System.Xml.XmlSecureResolver> class if you need to open a resource that you do not control, or that is untrusted.</span></span>  
  
- <span data-ttu-id="00188-123">동작을 사용자 지정하기 위해 사용자의 고유한 <xref:System.Xml.XmlResolver> 클래스를 구현하고 사용하여 리소스를 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-123">If you want to customize behavior, you can implement your own <xref:System.Xml.XmlResolver> class and use it to resolve resources.</span></span>  
  
- <span data-ttu-id="00188-124">외부 리소스에 액세스하지 않도록 하려면 `null` 인수에 대해 <xref:System.Xml.XmlResolver>을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="00188-124">If you want to ensure that no external resources are accessed, you can specify `null` for the <xref:System.Xml.XmlResolver> argument.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00188-125">예제</span><span class="sxs-lookup"><span data-stu-id="00188-125">Example</span></span>  

 <span data-ttu-id="00188-126">다음 예제에서는 네트워크 리소스에 저장된 스타일시트를 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-126">The following example compiles a style sheet that is stored on a network resource.</span></span> <span data-ttu-id="00188-127"><xref:System.Xml.XmlUrlResolver> 개체는 스타일시트에 액세스하는 데 필요한 자격 증명을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="00188-127">An <xref:System.Xml.XmlUrlResolver> object specifies the credentials necessary to access the style sheet.</span></span>  
  
 [!code-csharp[XslCompiledTransform.Load#11](../../../../samples/snippets/csharp/VS_Snippets_Data/XslCompiledTransform.Load/CS/Xslt_Load_v2.cs#11)]
 [!code-vb[XslCompiledTransform.Load#11](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslCompiledTransform.Load/VB/Xslt_Load_v2.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="00188-128">참조</span><span class="sxs-lookup"><span data-stu-id="00188-128">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- <xref:System.Xml.Xsl.XsltSettings>
- [<span data-ttu-id="00188-129">XSLT 변환</span><span class="sxs-lookup"><span data-stu-id="00188-129">XSLT Transformations</span></span>](xslt-transformations.md)
