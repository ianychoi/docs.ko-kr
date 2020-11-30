---
title: XPathNavigator를 사용하여 노드 일치시키기
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 2d598a4ddfe84eec7288d111fc156dd0c555a10e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720128"
---
# <a name="matching-nodes-using-xpathnavigator"></a><span data-ttu-id="afcd3-102">XPathNavigator를 사용하여 노드 일치시키기</span><span class="sxs-lookup"><span data-stu-id="afcd3-102">Matching Nodes using XPathNavigator</span></span>

<span data-ttu-id="afcd3-103"><xref:System.Xml.XPath.XPathNavigator> 클래스는 노드가 XPath 식과 일치하는지 결정하는 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="afcd3-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method to determine if a node matches an XPath expression.</span></span> <span data-ttu-id="afcd3-104"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 메서드는 XPath 식을 입력으로 사용하며 현재 노드가 지정된 XPath 식 또는 지정된 컴파일된 <xref:System.Boolean> 개체와 일치하는지를 나타내는 <xref:System.Xml.XPath.XPathExpression>을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="afcd3-104">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method takes an XPath expression as input and returns a <xref:System.Boolean> that indicates if the current node matches the given XPath expression or the given compiled <xref:System.Xml.XPath.XPathExpression> object.</span></span>  
  
## <a name="matching-nodes"></a><span data-ttu-id="afcd3-105">노드 일치시키기</span><span class="sxs-lookup"><span data-stu-id="afcd3-105">Matching Nodes</span></span>  

 <span data-ttu-id="afcd3-106">현재 노드가 지정된 XPath 식과 일치하는 경우 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 메서드는 `true`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="afcd3-106">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method returns `true` if the current node matches the XPath expression specified.</span></span> <span data-ttu-id="afcd3-107">예를 들어, 다음 코드 예제에서 현재 노드가 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> 요소이고 `true` 요소에 `b` 특성이 있을 경우 `b` 메서드는 `c`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="afcd3-107">For example, in the code example that follows, the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method will return `true` if the current node is the element `b`, and element `b` has an attribute `c`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afcd3-108"><xref:System.Xml.XPath.XPathNavigator.Matches%2A> 메서드는 <xref:System.Xml.XPath.XPathNavigator> 상태를 변경하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="afcd3-108">The <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method does not change the state of the <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a><span data-ttu-id="afcd3-109">참조</span><span class="sxs-lookup"><span data-stu-id="afcd3-109">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="afcd3-110">XPath 데이터 모델을 사용하여 XML 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="afcd3-110">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="afcd3-111">XPathNavigator를 사용하여 XML 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="afcd3-111">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="afcd3-112">XPathNavigator를 사용하여 XPath 식 계산</span><span class="sxs-lookup"><span data-stu-id="afcd3-112">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="afcd3-113">XPath 쿼리에서 인식하는 노드 형식</span><span class="sxs-lookup"><span data-stu-id="afcd3-113">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="afcd3-114">XPath 쿼리 및 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="afcd3-114">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="afcd3-115">컴파일된 XPath 식</span><span class="sxs-lookup"><span data-stu-id="afcd3-115">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
