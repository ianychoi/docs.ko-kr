---
title: XML 스키마 읽기 및 쓰기
description: SOM(스키마 개체 모델) API를 사용하여 .NET의 파일 또는 다른 소스에서 XSD(XML 스키마 정의 언어) 스키마를 읽고 씁니다.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: b5757c4a-ea59-467e-ac62-be2bfe24eb77
ms.openlocfilehash: ae951efafd68d0ddf4f74876edd4c12564d68dde
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830885"
---
# <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="3ae86-103">XML 스키마 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="3ae86-103">Reading and Writing XML Schemas</span></span>
<span data-ttu-id="3ae86-104">SOM(스키마 개체 모델) API를 사용하여 파일 또는 기타 소스에서 XSD(XML 스키마 정의 언어) 스키마를 읽고 쓸 수 있으며 W3C(World Wide Web 컨소시엄) XML 스키마 권장 사항에 정의된 구조에 매핑되는 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스에서 클래스를 사용하여 메모리 내 XML 스키마를 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-104">The Schema Object Model (SOM) API can be used to read and write XML Schema definition language (XSD) schemas from files or other sources and build XML schemas in-memory using the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that map to the structures defined in the World Wide Web Consortium (W3C) XML Schema Recommendation.</span></span>  
  
## <a name="reading-and-writing-xml-schemas"></a><span data-ttu-id="3ae86-105">XML 스키마 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="3ae86-105">Reading and Writing XML Schemas</span></span>  
 <span data-ttu-id="3ae86-106"><xref:System.Xml.Schema.XmlSchema> 클래스는 XML 스키마를 읽고 쓰는 <xref:System.Xml.Schema.XmlSchema.Read%2A> 및 <xref:System.Xml.Schema.XmlSchema.Write%2A> 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-106">The <xref:System.Xml.Schema.XmlSchema> class provides the <xref:System.Xml.Schema.XmlSchema.Read%2A> and <xref:System.Xml.Schema.XmlSchema.Write%2A> methods to read and write XML schemas.</span></span> <span data-ttu-id="3ae86-107"><xref:System.Xml.Schema.XmlSchema.Read%2A> 메서드는 XML 스키마를 나타내는 <xref:System.Xml.Schema.XmlSchema> 개체를 반환하며 선택적 <xref:System.Xml.Schema.ValidationEventHandler>를 매개 변수로 사용하여 XML 스키마를 읽는 동안 발생한 스키마 유효성 검사 경고 및 오류를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-107">The <xref:System.Xml.Schema.XmlSchema.Read%2A> method returns an <xref:System.Xml.Schema.XmlSchema> object representing the XML schema and takes an optional <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to handle schema validation warnings and errors encountered while reading an XML schema.</span></span>  
  
 <span data-ttu-id="3ae86-108"><xref:System.Xml.Schema.XmlSchema.Write%2A> 메서드는 XML 스키마를 <xref:System.IO.Stream>, <xref:System.IO.TextWriter> 및 <xref:System.Xml.XmlWriter> 개체에 작성하고 선택적 <xref:System.Xml.XmlNamespaceManager> 개체를 매개 변수로 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-108">The <xref:System.Xml.Schema.XmlSchema.Write%2A> method writes XML schemas to <xref:System.IO.Stream>, <xref:System.IO.TextWriter> and <xref:System.Xml.XmlWriter> objects and can take an optional <xref:System.Xml.XmlNamespaceManager> object as a parameter.</span></span> <span data-ttu-id="3ae86-109"><xref:System.Xml.XmlNamespaceManager>를 사용하여 XML 스키마에서 발생한 네임스페이스를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-109">An <xref:System.Xml.XmlNamespaceManager> is used to handle namespaces encountered in an XML schema.</span></span> <span data-ttu-id="3ae86-110"><xref:System.Xml.XmlNamespaceManager> 클래스에 대한 자세한 내용은 [XML 문서의 네임스페이스 관리](managing-namespaces-in-an-xml-document.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3ae86-110">For more information about the <xref:System.Xml.XmlNamespaceManager> class, see [Managing Namespaces in an XML Document](managing-namespaces-in-an-xml-document.md).</span></span>  
  
 <span data-ttu-id="3ae86-111">다음 코드 예제에서는 파일에서 XML 스키마를 읽고 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-111">The following code example illustrates reading and writing XML schemas from and to a file.</span></span> <span data-ttu-id="3ae86-112">이 코드 예제에서는 `example.xsd` 파일을 가져와서 <xref:System.Xml.Schema.XmlSchema>`static` 메서드를 사용하여 <xref:System.Xml.Schema.XmlSchema.Read%2A> 개체로 읽어온 다음 이 파일을 콘솔 및 새 `new.xsd` 파일에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-112">The code example takes the `example.xsd` file, reads it into an <xref:System.Xml.Schema.XmlSchema> object using the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method, and then writes the file to the console and a new `new.xsd` file.</span></span> <span data-ttu-id="3ae86-113">또한 이 코드 예제에서는 <xref:System.Xml.Schema.ValidationEventHandler>를 `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> 메서드에 매개 변수로 제공하여 XML 스키마를 읽는 동안 발생한 스키마 유효성 검사 경고 또는 오류를 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-113">The code example also provides a <xref:System.Xml.Schema.ValidationEventHandler> as a parameter to the `static`<xref:System.Xml.Schema.XmlSchema.Read%2A> method to handle any schema validation warnings or errors encountered while reading the XML schema.</span></span> <span data-ttu-id="3ae86-114"><xref:System.Xml.Schema.ValidationEventHandler>를 지정하지 않으면(`null`) 경고 또는 오류가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-114">If the <xref:System.Xml.Schema.ValidationEventHandler> is not specified (`null`), no warnings or errors are reported.</span></span>  
  
 [!code-cpp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaReadWriteExample/CPP/XmlSchemaReadWriteExample.cpp#1)]
 [!code-csharp[XmlSchemaReadWriteExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaReadWriteExample/CS/XmlSchemaReadWriteExample.cs#1)]
 [!code-vb[XmlSchemaReadWriteExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaReadWriteExample/VB/XmlSchemaReadWriteExample.vb#1)]  
  
 <span data-ttu-id="3ae86-115">이 예제에서는 `example.xsd`를 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3ae86-115">The example takes the `example.xsd` as input.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<xs:schema id="play" targetNamespace="http://tempuri.org/play.xsd" elementFormDefault="qualified" xmlns="http://tempuri.org/play.xsd" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:element name='myShoeSize'>  
        <xs:complexType>  
            <xs:simpleContent>  
                <xs:extension base='xs:decimal'>  
                    <xs:attribute name='sizing' type='xs:string' />  
                </xs:extension>  
            </xs:simpleContent>  
        </xs:complexType>  
    </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ae86-116">참조</span><span class="sxs-lookup"><span data-stu-id="3ae86-116">See also</span></span>

- [<span data-ttu-id="3ae86-117">XML 스키마 개체 모델 개요</span><span class="sxs-lookup"><span data-stu-id="3ae86-117">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="3ae86-118">XML 스키마 빌드</span><span class="sxs-lookup"><span data-stu-id="3ae86-118">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="3ae86-119">XML 스키마 통과</span><span class="sxs-lookup"><span data-stu-id="3ae86-119">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="3ae86-120">XML 스키마 편집</span><span class="sxs-lookup"><span data-stu-id="3ae86-120">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="3ae86-121">XML 스키마 포함하기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="3ae86-121">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="3ae86-122">스키마 컴파일을 위한 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="3ae86-122">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="3ae86-123">Post-Schema Compilation Infoset</span><span class="sxs-lookup"><span data-stu-id="3ae86-123">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
- [<span data-ttu-id="3ae86-124">XML 문서의 네임스페이스 관리</span><span class="sxs-lookup"><span data-stu-id="3ae86-124">Managing Namespaces in an XML Document</span></span>](managing-namespaces-in-an-xml-document.md)
