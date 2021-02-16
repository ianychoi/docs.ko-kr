---
description: '자세히 알아보기: 방법: XML 리터럴 만들기 (Visual Basic)'
title: '방법: XML 리터럴 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: 0e57b037d0567002fd570025e147771c4fab38f4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433293"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="05c81-103">방법: XML 리터럴 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05c81-103">How to: Create XML Literals (Visual Basic)</span></span>

<span data-ttu-id="05c81-104">XML 리터럴을 사용 하 여 코드에서 직접 XML 문서, 조각 또는 요소를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-104">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="05c81-105">이 항목의 예제에서는 세 개의 자식 요소가 있는 XML 요소를 만드는 방법 및 XML 문서를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-105">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="05c81-106">Api를 사용 하 여 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 개체를 만들 수도 있습니다 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="05c81-106">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="05c81-107">자세한 내용은 <xref:System.Xml.Linq.XElement>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="05c81-107">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="05c81-108">XML 요소를 만들려면</span><span class="sxs-lookup"><span data-stu-id="05c81-108">To create an XML element</span></span>  
  
- <span data-ttu-id="05c81-109">실제 XML 구문과 동일한 XML 리터럴 구문을 사용 하 여 XML 인라인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-109">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="05c81-110">코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-110">Run the code.</span></span> <span data-ttu-id="05c81-111">이 코드의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="05c81-112">XML 문서를 만들려면</span><span class="sxs-lookup"><span data-stu-id="05c81-112">To create an XML document</span></span>  
  
- <span data-ttu-id="05c81-113">XML 문서 인라인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-113">Create the XML document inline.</span></span> <span data-ttu-id="05c81-114">다음 코드는 리터럴 구문, XML 선언, 처리 명령, 주석 및 다른 요소를 포함 하는 요소를 포함 하는 XML 문서를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="05c81-115">코드를 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-115">Run the code.</span></span> <span data-ttu-id="05c81-116">이 코드의 출력은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="05c81-116">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="05c81-117">추가 정보</span><span class="sxs-lookup"><span data-stu-id="05c81-117">See also</span></span>

- [<span data-ttu-id="05c81-118">XML</span><span class="sxs-lookup"><span data-stu-id="05c81-118">XML</span></span>](index.md)
- [<span data-ttu-id="05c81-119">Visual Basic에서 XML 만들기</span><span class="sxs-lookup"><span data-stu-id="05c81-119">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="05c81-120">XML 요소 리터럴</span><span class="sxs-lookup"><span data-stu-id="05c81-120">XML Element Literal</span></span>](../../../language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="05c81-121">XML 문서 리터럴</span><span class="sxs-lookup"><span data-stu-id="05c81-121">XML Document Literal</span></span>](../../../language-reference/xml-literals/xml-document-literal.md)
