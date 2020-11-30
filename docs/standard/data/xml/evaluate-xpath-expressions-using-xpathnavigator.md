---
title: XPathNavigator를 사용하여 XPath 식 계산
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 19e3287a990bbfd793bce892b14f08f31c53faa2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687205"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a><span data-ttu-id="83fb9-102">XPathNavigator를 사용하여 XPath 식 계산</span><span class="sxs-lookup"><span data-stu-id="83fb9-102">Evaluate XPath Expressions using XPathNavigator</span></span>

<span data-ttu-id="83fb9-103"><xref:System.Xml.XPath.XPathNavigator> 클래스는 XPath 식을 계산하는 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-103">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method to evaluate an XPath expression.</span></span> <span data-ttu-id="83fb9-104"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드는 XPath 식을 가져와서 계산하고 XPath 식 결과를 기준으로 부울, 숫자, 문자열, 노드 집합 등의 W3C XPath 형식을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-104">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it and returns a W3C XPath type of Boolean, Number, String, or Node Set based on the result of the XPath expression.</span></span>  
  
## <a name="the-evaluate-method"></a><span data-ttu-id="83fb9-105">Evaluate 메서드</span><span class="sxs-lookup"><span data-stu-id="83fb9-105">The Evaluate Method</span></span>  

 <span data-ttu-id="83fb9-106"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드는 XPath 식을 가져와서 계산하고 부울(<xref:System.Boolean>), 숫자(<xref:System.Double>), 문자열(<xref:System.String>), 노드 집합(<xref:System.Xml.XPath.XPathNodeIterator>) 등의 형식화된 결과를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-106">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method takes an XPath expression, evaluates it, and returns a typed result of Boolean (<xref:System.Boolean>), Number (<xref:System.Double>), String (<xref:System.String>), or Node Set (<xref:System.Xml.XPath.XPathNodeIterator>).</span></span> <span data-ttu-id="83fb9-107">예를 들어, 수학적 메서드에서 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-107">For example, the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method could be used in a mathematical method.</span></span> <span data-ttu-id="83fb9-108">다음 예제 코드에서는 `books.xml` 파일에 있는 모든 책의 총 가격을 계산합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-108">The following example code calculates the total price of all the books in the `books.xml` file.</span></span>  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 <span data-ttu-id="83fb9-109">이 예제에서는 `books.xml` 파일을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-109">The example takes the `books.xml` file as input.</span></span>  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a><span data-ttu-id="83fb9-110">position 및 last 함수</span><span class="sxs-lookup"><span data-stu-id="83fb9-110">position and last Functions</span></span>  

 <span data-ttu-id="83fb9-111"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드가 오버로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-111">The <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is overloaded.</span></span> <span data-ttu-id="83fb9-112"><xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드 중 하나가 <xref:System.Xml.XPath.XPathNodeIterator> 개체를 매개 변수로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-112">One of the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> methods takes an <xref:System.Xml.XPath.XPathNodeIterator> object as a parameter.</span></span> <span data-ttu-id="83fb9-113">이 특정 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 메서드는 매개 변수로 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> 개체만을 사용하는 <xref:System.Xml.XPath.XPathExpression> 메서드와 일치합니다. 단, 노드 집합 인수에서 계산을 실행할 현재 컨텍스트를 지정할 수 있다는 점이 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-113">This particular <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method is identical to the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method that takes only an <xref:System.Xml.XPath.XPathExpression> object as a parameter, except that it allows a node set argument to specify the current context to perform the evaluation on.</span></span> <span data-ttu-id="83fb9-114">이 컨텍스트는 XPath `position()` 및 `last()` 함수가 현재 컨텍스트 노드에 상대적인 경우 이러한 함수에 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-114">This context is required for the XPath `position()` and `last()` functions as they are relative to the current context node.</span></span> <span data-ttu-id="83fb9-115">`position()` 및 `last()` 함수가 위치 단계에서 조건자로 사용되지 않을 경우 이를 계산하기 위해서는 노드 집합에 대한 참조가 필요합니다. 그렇지 않으면 `position` 및 `last` 함수는 `0`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="83fb9-115">Unless used as a predicate in a location step, the `position()` and `last()` functions require a reference to a node set in order to be evaluated otherwise, the `position` and `last` functions return `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83fb9-116">참조</span><span class="sxs-lookup"><span data-stu-id="83fb9-116">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="83fb9-117">XPath 데이터 모델을 사용하여 XML 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="83fb9-117">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="83fb9-118">XPathNavigator를 사용하여 XML 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="83fb9-118">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="83fb9-119">XPathNavigator를 사용하여 노드 일치시키기</span><span class="sxs-lookup"><span data-stu-id="83fb9-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="83fb9-120">XPath 쿼리에서 인식하는 노드 형식</span><span class="sxs-lookup"><span data-stu-id="83fb9-120">Node Types Recognized with XPath Queries</span></span>](node-types-recognized-with-xpath-queries.md)
- [<span data-ttu-id="83fb9-121">XPath 쿼리 및 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="83fb9-121">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="83fb9-122">컴파일된 XPath 식</span><span class="sxs-lookup"><span data-stu-id="83fb9-122">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
