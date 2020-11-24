---
title: XPath 쿼리에서 인식하는 노드 형식
ms.date: 03/30/2017
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: 87f4ed0c8182e250f6926d6c3d82893e6f8b985c
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830105"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="1c39c-102">XPath 쿼리에서 인식하는 노드 형식</span><span class="sxs-lookup"><span data-stu-id="1c39c-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="1c39c-103">XPath 쿼리에서 인식하는 노드 형식은 DOM(문서 개체 모델)에 있는 노드 형식과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="1c39c-104">W3C XPath 노드 형식</span><span class="sxs-lookup"><span data-stu-id="1c39c-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="1c39c-105">XPath 쿼리에서 인식하는 노드 형식은 DOM(문서 개체 모델)에 있는 노드 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="1c39c-106">다음은 <xref:System.Xml.XPath.XPathNodeType> 열거형이 나타내는 XPath 노드 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="1c39c-107">이 노드 형식은 XML 정보 집합에서 노드가 파생되는 XPath 데이터 모델을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="1c39c-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> 및 <xref:System.Xml.XPath.XPathNodeType.Whitespace> 노드 형식은 XPath 데이터 모델에서 설명하는 기본 노드 형식에 대한 Microsoft .NET Framework 확장입니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="1c39c-109">XPath 데이터 모델에서는 DOM에서와 다른 방식으로 특성 노드 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="1c39c-110">XPath 데이터 모델에서 요소 노드는 관련된 특성 노드 집합을 가지고 있으며 요소 노드는 각 특성 노드의 부모입니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="1c39c-111">그러나 DOM에서 요소 노드는 부모가 아니라 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="1c39c-112">두 모델에서 특성 및 네임스페이스 노드는 요소 노드의 자식 노드로 간주되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="1c39c-113">네임스페이스 노드 형식은 XPath 데이터 모델에 추가된 것이며 인식되는 DOM 노드 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="1c39c-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="1c39c-114">요소, 특성 및 네임스페이스 노드 탐색에 대한 자세한 내용은 [XPathNavigator를 사용하여 노드 집합 탐색](node-set-navigation-using-xpathnavigator.md) 및 [XPathNavigator를 사용하여 특성 및 네임스페이스 노드 탐색](attribute-and-namespace-node-navigation-using-xpathnavigator.md) 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1c39c-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c39c-115">참조</span><span class="sxs-lookup"><span data-stu-id="1c39c-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="1c39c-116">XPath 데이터 모델을 사용하여 XML 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="1c39c-116">Process XML Data Using the XPath Data Model</span></span>](process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="1c39c-117">XPathNavigator를 사용하여 XML 데이터 선택</span><span class="sxs-lookup"><span data-stu-id="1c39c-117">Select XML Data Using XPathNavigator</span></span>](select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="1c39c-118">XPathNavigator를 사용하여 XPath 식 계산</span><span class="sxs-lookup"><span data-stu-id="1c39c-118">Evaluate XPath Expressions using XPathNavigator</span></span>](evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="1c39c-119">XPathNavigator를 사용하여 노드 일치시키기</span><span class="sxs-lookup"><span data-stu-id="1c39c-119">Matching Nodes using XPathNavigator</span></span>](matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="1c39c-120">XPath 쿼리 및 네임스페이스</span><span class="sxs-lookup"><span data-stu-id="1c39c-120">XPath Queries and Namespaces</span></span>](xpath-queries-and-namespaces.md)
- [<span data-ttu-id="1c39c-121">컴파일된 XPath 식</span><span class="sxs-lookup"><span data-stu-id="1c39c-121">Compiled XPath Expressions</span></span>](compiled-xpath-expressions.md)
