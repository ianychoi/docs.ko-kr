---
title: XPath 네임스페이스 탐색
ms.date: 03/30/2017
ms.assetid: 06cc7abb-7416-415c-9dd6-67751b8cabd5
ms.openlocfilehash: d5350f0c8f73c5efb0f7d9e4c492a841b4978c36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720895"
---
# <a name="xpath-namespace-navigation"></a><span data-ttu-id="a5c92-102">XPath 네임스페이스 탐색</span><span class="sxs-lookup"><span data-stu-id="a5c92-102">XPath Namespace Navigation</span></span>

<span data-ttu-id="a5c92-103">XML 문서가 있는 XPath 쿼리를 사용하려면 네임스페이스에 포함된 XML 네임스페이스 및 요소를 올바르게 지정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-103">To use XPath queries with XML documents, you have to correctly address XML namespaces and the elements contained by namespaces.</span></span> <span data-ttu-id="a5c92-104">네임스페이스를 사용하면 이름이 둘 이상의 컨텍스트에 사용되는 경우 발생할 수 있는 모호성을 방지할 수 있습니다. 예를 들어 이름 `ID`는 XML 문서의 여러 다른 요소와 연결된 둘 이상의 ID를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-104">Namespaces prevent ambiguities that can occur when names are used in more than one context; for example, the name `ID` may refer to more than one identifier associated with different elements of an XML document.</span></span> <span data-ttu-id="a5c92-105">네임스페이스 구문은 URI, 이름 및 XML 문서의 요소를 구분하는 접두사를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-105">Namespace syntax specifies URIs, names, and prefixes that distinguish the elements of an XML document.</span></span>  
  
 <span data-ttu-id="a5c92-106">이 항목의 예제는 <xref:System.Xml.XPath.XPathNavigator>로 XML 문서를 탐색하는 데 접두사를 사용하는 경우를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-106">The example in this topic demonstrates the use of prefixes in navigating an XML document with <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a5c92-107">네임스페이스 및 구문에 대한 자세한 내용은 [XML 파일: XML 네임스페이스 이해](/previous-versions/dotnet/articles/bb986013(v=msdn.10))를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a5c92-107">For more information about namespaces and syntax, see [XML Files: Understanding XML Namespaces](/previous-versions/dotnet/articles/bb986013(v=msdn.10)).</span></span>  
  
## <a name="namespace-declarations"></a><span data-ttu-id="a5c92-108">네임스페이스 선언</span><span class="sxs-lookup"><span data-stu-id="a5c92-108">Namespace Declarations</span></span>  

 <span data-ttu-id="a5c92-109">네임스페이스 선언은 <xref:System.Xml.XPath.XPathNavigator> 인스턴스를 사용하는 경우 XML 문서의 요소를 구분하고 지정할 수 있게 해 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-109">Namespace declarations make the elements of an XML document distinguishable and addressable when using an instance of <xref:System.Xml.XPath.XPathNavigator>.</span></span> <span data-ttu-id="a5c92-110">네임스페이스 접두사는 네임스페이스 지정에 사용되는 간단한 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-110">Namespace prefixes provide a brief syntax for addressing namespaces.</span></span>  
  
 <span data-ttu-id="a5c92-111">접두사는 다음 양식으로 정의됩니다. `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` 이 구문에서 "`e`" 접두사는 네임스페이스의 정식 URI에 대한 약어입니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-111">Prefixes are defined by the form: `<e:Envelope xmlns:e=http://schemas.xmlsoap.org/soap/envelope/>.` In this syntax the prefix "`e`" is an abbreviation for the formal URI of the namespace.</span></span> <span data-ttu-id="a5c92-112">`Body` 구문을 사용하여 `Envelope` 요소를 `e:Body` 네임스페이스의 멤버로 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-112">You can identify the `Body` element as a member of the `Envelope` namespace by using the syntax: `e:Body`.</span></span>  
  
 <span data-ttu-id="a5c92-113">다음 XML 문서는 다음 단원의 탐색 예제에서 `response.xml`로 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-113">The following XML document will be referenced as `response.xml` in the navigation example in the next section.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<e:Envelope xmlns:e="http://schemas.xmlsoap.org/soap/envelope/">  
  <e:Body>  
    <s:Search xmlns:s="http://schemas.microsoft.com/v1/Search">  
      <r:request xmlns:r="http://schemas.microsoft.com/v1/Search/metadata"
                 xmlns:i="http://www.w3.org/2001/XMLSchema-instance">  
      </r:request>  
    </s:Search>  
  </e:Body>  
</e:Envelope>  
```  
  
## <a name="navigation-by-namespace-prefix"></a><span data-ttu-id="a5c92-114">네임스페이스 접두사로 탐색</span><span class="sxs-lookup"><span data-stu-id="a5c92-114">Navigation by Namespace Prefix</span></span>  

 <span data-ttu-id="a5c92-115">이 단원의 코드는 <xref:System.Xml.XPath.XPathNavigator> 및 <xref:System.Xml.XmlNamespaceManager> 개체를 사용하여 이전 단원의 XML 문서에서 `Search` 요소를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-115">The code in this section uses <xref:System.Xml.XPath.XPathNavigator> and <xref:System.Xml.XmlNamespaceManager> objects to select the `Search` element from the XML document in the previous section.</span></span> <span data-ttu-id="a5c92-116">`xpath` 쿼리에는 경로의 각 요소에 대한 네임스페이스 접두사가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-116">The query `xpath` includes namespace prefixes on each element in the path.</span></span> <span data-ttu-id="a5c92-117">각 요소를 포함하는 네임스페이스의 ID를 정확히 지정하면 `Search` 메서드가 <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> 요소에 대한 탐색을 올바르게 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-117">Specifying the precise identity of the namespaces that contain each element assures correct navigation to the `Search` element by the <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> method.</span></span>  
  
```csharp  
using (XmlReader reader = XmlReader.Create("response.xml"))  
{  
    XPathDocument doc = new XPathDocument(reader);  
    XPathNavigator nav = doc.CreateNavigator();
  
    XmlNamespaceManager nsmgr = new XmlNamespaceManager(nav.NameTable);  
    nsmgr.AddNamespace("e", @"http://schemas.xmlsoap.org/soap/envelope/");  
    nsmgr.AddNamespace("s", @"http://schemas.microsoft.com/v1/Search");  
    nsmgr.AddNamespace("r", @"http://schemas.microsoft.com/v1/Search/metadata");  
    nsmgr.AddNamespace("i", @"http://www.w3.org/2001/XMLSchema-instance");  
  
    string xpath = "/e:Envelope/e:Body/s:Search";  
  
    XPathNavigator element = nav.SelectSingleNode(xpath, nsmgr);  
  
    Console.WriteLine("Element Prefix:" + element.Prefix +
    " Local name:" + element.LocalName);  
    Console.WriteLine("Namespace URI: " + element.NamespaceURI);  
}  
```  
  
 <span data-ttu-id="a5c92-118">정규화된 네임스페이스 및 이름의 정확한 사용은 단순히 편리한 것 이상의 이점이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-118">The precision of fully qualifying namespaces and names is more than a convenience.</span></span> <span data-ttu-id="a5c92-119">이전 예제의 문서 정의 및 코드를 사용한 작은 실험을 통해 정규화된 요소 이름이 없는 탐색에서 예외를 throw한다는 사실을 확인한 바 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-119">A little experimentation with the document definition and code in the previous examples will verify that navigation without fully qualified element names throws exceptions.</span></span> <span data-ttu-id="a5c92-120">예를 들어 요소 정의: `<Search xmlns="http://schemas.microsoft.com/v1/Search">` 및 쿼리: `xpath = "/s:Envelope/s:Body/Search";` 요소에 대한 네임스페이스 접두사가 없는 문자열 `Search`는 `null` 요소 대신 `Search`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="a5c92-120">For example, the element definition: `<Search xmlns="http://schemas.microsoft.com/v1/Search">`, and query: string `xpath = "/s:Envelope/s:Body/Search";` without the namespace prefix on the `Search` element returns `null` instead of the `Search` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5c92-121">참조</span><span class="sxs-lookup"><span data-stu-id="a5c92-121">See also</span></span>

- [<span data-ttu-id="a5c92-122">XPathNavigator를 사용하여 XML 데이터 액세스</span><span class="sxs-lookup"><span data-stu-id="a5c92-122">Accessing XML Data using XPathNavigator</span></span>](accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="a5c92-123">XPathNavigator를 사용하여 XML 데이터 선택, 평가 및 일치시키기</span><span class="sxs-lookup"><span data-stu-id="a5c92-123">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>](selecting-evaluating-and-matching-xml-data-using-xpathnavigator.md)
