---
title: 인덱스별로 정렬된 노드 검색
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5412c90f-2703-4aa8-a9c4-1b8a35183c37
ms.openlocfilehash: 73c31c5249262fe9b6624201bc5b9bd6b1374d1e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823747"
---
# <a name="ordered-node-retrieval-by-index"></a><span data-ttu-id="c5642-102">인덱스별로 정렬된 노드 검색</span><span class="sxs-lookup"><span data-stu-id="c5642-102">Ordered Node Retrieval by Index</span></span>
<span data-ttu-id="c5642-103">W3C(World Wide Web 컨소시엄) XML DOM(문서 개체 모델)에서는 **XmlNamedNodeMap** 으로 처리되는 정렬되지 않은 집합과 반대되는 정렬된 노드 목록을 처리할 수 있는 NodeList에 대해서도 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-103">The World Wide Web Consortium (W3C) XML Document Object Model (DOM) also describes a NodeList, which has the ability to handle an ordered list of nodes, as opposed to the unordered set handled by the **XmlNamedNodeMap**.</span></span> <span data-ttu-id="c5642-104">Microsoft .NET Framework에서는 NodeList를 **XmlNodeList** 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-104">The NodeList in the Microsoft .NET Framework is called **XmlNodeList**.</span></span> <span data-ttu-id="c5642-105">**XmlNodeList** 를 반환하는 메서드와 속성은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-105">Methods and properties that return an **XmlNodeList** are:</span></span>  
  
- <span data-ttu-id="c5642-106">XmlNode.ChildNodes</span><span class="sxs-lookup"><span data-stu-id="c5642-106">XmlNode.ChildNodes</span></span>  
  
- <span data-ttu-id="c5642-107">XmlDocument.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="c5642-107">XmlDocument.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="c5642-108">XmlElement.GetElementsByTagName</span><span class="sxs-lookup"><span data-stu-id="c5642-108">XmlElement.GetElementsByTagName</span></span>  
  
- <span data-ttu-id="c5642-109">XmlNode.SelectNodes</span><span class="sxs-lookup"><span data-stu-id="c5642-109">XmlNode.SelectNodes</span></span>  
  
 <span data-ttu-id="c5642-110">**XmlNodeList** 에는 다음 코드 샘플과 같이 **XmlNodeList** 의 노드를 반복하는 루프를 작성하는 데 사용할 수 있는 **Count** 속성이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-110">The **XmlNodeList** has a **Count** property that can be used to write loops to iterate over the nodes in the **XmlNodeList**, as shown in the following code sample:</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
   doc.Load("books.xml")  
  
    ' Retrieve all book titles.  
    Dim root as XmlElement = doc.DocumentElement  
    Dim elemList as XmlNodeList = root.GetElementsByTagName("title")  
    Dim i as integer  
    for i=0  to elemList.Count-1  
        ' Display all book titles in the Node List.  
        Console.WriteLine(elemList.ItemOf(i).InnerXml)  
    next  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.Load("books.xml");  
// Retrieve all book titles.  
XmlElement root = doc.DocumentElement;  
XmlNodeList elemList = root.GetElementsByTagName("title");  
for (int i=0; i < elemList.Count; i++)  
{
   // Display all book titles in the Node List.  
   Console.WriteLine(elemList[i].InnerXml);  
}
```  
  
 <span data-ttu-id="c5642-111">**Count** 속성과 더불어 **XmlNodeList** 의 노드 컬렉션에 대한 `foreach` 스타일 반복을 제공하는 **GetEnumerator** 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-111">In addition to the **Count** property, there is a **GetEnumerator** method that provides a, `foreach` style iteration over the collection of nodes in the **XmlNodeList**.</span></span> <span data-ttu-id="c5642-112">다음 코드 예제에서는 `foreach` 문을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="c5642-112">The following code example shows the use of the `foreach` statement.</span></span>  
  
```vb  
Dim doc As New XmlDocument()  
doc.Load("books.xml")  
  
' Get book titles.  
Dim root As XmlElement = doc.DocumentElement  
Dim elemList As XmlNodeList = root.GetElementsByTagName("title")  
Dim ienum As IEnumerator = elemList.GetEnumerator()  
' Loop over the XmlNodeList using the enumerator ienum
While ienum.MoveNext()  
    ' Display the book title.  
    Dim title As XmlNode = CType(ienum.Current, XmlNode)  
    Console.WriteLine(title.InnerText)  
End While  
```  
  
```csharp  
{  
     XmlDocument doc = new XmlDocument();  
     doc.Load("books.xml");  
  
     // Get book titles.  
     XmlElement root = doc.DocumentElement;  
     XmlNodeList elemList = root.GetElementsByTagName("title");  
     IEnumerator ienum = elemList.GetEnumerator();
     // Loop over the XmlNodeList using the enumerator ienum
     while (ienum.MoveNext())  
     {  
          // Display the book title.  
           XmlNode title = (XmlNode) ienum.Current;  
           Console.WriteLine(title.InnerText);  
     }  
  }  
```  
  
 <span data-ttu-id="c5642-113">**XmlNodeList** 에서 사용할 수 있는 메서드 및 속성에 대한 자세한 내용은 <xref:System.Xml.XmlNodeList>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c5642-113">For more information on the methods and properties available on the **XmlNodeList**, see <xref:System.Xml.XmlNodeList>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5642-114">참조</span><span class="sxs-lookup"><span data-stu-id="c5642-114">See also</span></span>

- [<span data-ttu-id="c5642-115">XML DOM(문서 개체 모델)</span><span class="sxs-lookup"><span data-stu-id="c5642-115">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
