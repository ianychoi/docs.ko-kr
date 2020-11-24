---
title: XML 스키마 개체 모델 개요
ms.date: 03/30/2017
ms.assetid: 896a1e12-5655-42c6-8cdd-89c12862b34b
ms.openlocfilehash: c54f92ede64e59478a0e9bfd919666caa9481137
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819216"
---
# <a name="xml-schema-object-model-overview"></a><span data-ttu-id="c96a4-102">XML 스키마 개체 모델 개요</span><span class="sxs-lookup"><span data-stu-id="c96a4-102">XML Schema Object Model Overview</span></span>
<span data-ttu-id="c96a4-103">Microsoft .NET Framework의 SOM(스키마 개체 모델)은 프로그래밍 방식으로 스키마를 만들고 편집하고 유효성을 검사할 수 있는 다양한 API입니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-103">The Schema Object Model (SOM) in the Microsoft .NET Framework is a rich API that allows you to create, edit, and validate schemas programmatically.</span></span> <span data-ttu-id="c96a4-104">SOM은 DOM(문서 개체 모델)이 XML 문서에서 작동하는 것과 비슷한 방식으로 XML 스키마 문서에서 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-104">The SOM operates on XML schema documents similarly to the way the Document Object Model (DOM) operates on XML documents.</span></span> <span data-ttu-id="c96a4-105">XML 스키마 문서는 유효한 XML 파일로, SOM에 로드된 후에는 스키마를 준수하는 다른 XML 문서의 구조와 유효성에 대한 의미를 전달합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-105">XML schema documents are valid XML files that, once loaded into the SOM, convey meaning about the structure and validity of other XML documents which conform to the schema.</span></span>  
  
 <span data-ttu-id="c96a4-106">스키마는 특정 스키마에 대한 XML 문서의 구조나 모델을 지정하여 XML 문서의 클래스를 정의하는 XML 문서입니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-106">A schema is an XML document that defines a class of XML documents by specifying the structure or model of XML documents for a particular schema.</span></span> <span data-ttu-id="c96a4-107">스키마는 XML 문서 내용에 대한 제약 조건을 식별하고 XML 규격 문서가 준수해야 하는 용어 모음(규칙 또는 문법)을 정의하여 문서가 해당 스키마에 대해 유효한지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-107">A schema identifies the constraints on the content of the XML documents, and describes the vocabulary (rules or grammar) that compliant XML documents must follow in order to be considered schema-valid with that particular schema.</span></span> <span data-ttu-id="c96a4-108">XML 문서의 유효성 검사는 문서가 스키마에 지정된 문법과 일치하는지를 확인하는 프로세스입니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-108">Validation of an XML document is the process that ensures that the document conforms to the grammar specified by the schema.</span></span>  
  
 <span data-ttu-id="c96a4-109">다음은 .NET Framework의 SOM API를 사용하여 스키마를 만들고 편집하고 유효성을 검사하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-109">The following are ways the SOM API in the .NET Framework enables you to create, edit, and validate schemas.</span></span>  
  
- <span data-ttu-id="c96a4-110">유효한 스키마를 파일로 또는 파일에서 로드 및 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-110">Load and save valid schemas to and from files.</span></span>  
  
- <span data-ttu-id="c96a4-111">강력한 형식의 클래스를 사용하여 메모리 내 스키마를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-111">Create in-memory schemas using strongly typed classes.</span></span>  
  
- <span data-ttu-id="c96a4-112"><xref:System.Xml.Schema.XmlSchemaSet>과 상호 작용하여 스키마를 캐시, 컴파일 및 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-112">Interact with the <xref:System.Xml.Schema.XmlSchemaSet> class to cache, compile, and retrieve schemas.</span></span>  
  
- <span data-ttu-id="c96a4-113"><xref:System.Xml.XmlReader.Create%2A> 클래스의 <xref:System.Xml.XmlReader> 메서드와 상호 작용하여 스키마에 대해 XML 인스턴스 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-113">Interact with the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class to validate XML instance documents against schemas.</span></span>  
  
- <span data-ttu-id="c96a4-114">스키마를 만들고 유지 관리할 수 있는 편집기를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-114">Build editors for creating and maintaining schemas.</span></span>  
  
- <span data-ttu-id="c96a4-115">XML 인스턴스 문서의 유효성 검사에 사용될 수 있도록 컴파일 및 저장할 수 있는 스키마를 동적으로 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-115">Dynamically edit a schema that can be complied and saved for use in the validation of XML instance documents.</span></span>  
  
## <a name="the-schema-object-model"></a><span data-ttu-id="c96a4-116">스키마 개체 모델</span><span class="sxs-lookup"><span data-stu-id="c96a4-116">The Schema Object Model</span></span>  
 <span data-ttu-id="c96a4-117">SOM은 XML 스키마의 요소에 해당하는 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스의 다양한 클래스 집합으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-117">The SOM consists of an extensive set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace corresponding to the elements in an XML schema.</span></span> <span data-ttu-id="c96a4-118">예를 들어, `<xsd:schema>...</xsd:schema>` 요소는 <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> 클래스에 매핑되며 `<xsd:schema/>` 요소 내에 포함할 수 있는 모든 정보는 <xref:System.Xml.Schema.XmlSchema> 클래스를 사용하여 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-118">For example, the `<xsd:schema>...</xsd:schema>` element maps to the <xref:System.Xml.Schema.XmlSchema?displayProperty=nameWithType> class, and all the information that can be contained within an `<xsd:schema/>` element can be represented using the <xref:System.Xml.Schema.XmlSchema> class.</span></span> <span data-ttu-id="c96a4-119">마찬가지로 `<xsd:element>...</xsd:element>` 및 `<xsd:attribute>...</xsd:attribute>` 요소는 각각 <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> 및 <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> 클래스에 매핑됩니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-119">Similarly, the `<xsd:element>...</xsd:element>` and `<xsd:attribute>...</xsd:attribute>` elements map to the <xref:System.Xml.Schema.XmlSchemaElement?displayProperty=nameWithType> and <xref:System.Xml.Schema.XmlSchemaAttribute?displayProperty=nameWithType> classes respectively.</span></span> <span data-ttu-id="c96a4-120">다음 다이어그램에 표시된 <xref:System.Xml.Schema> 네임스페이스에서 XML 스키마 개체 모델을 만드는 XML 스키마의 모든 요소에 대해 이 매핑이 계속 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="c96a4-120">This mapping continues for all the elements of an XML schema creating an XML schema object model in the <xref:System.Xml.Schema> namespace illustrated in the diagram that follows.</span></span>  
  
 ![System.Xml.Schema 개체 모델](./media/xml-schema-object-model-overview/xml-schema-object-model.gif)  
  
 <span data-ttu-id="c96a4-122"><xref:System.Xml.Schema> 네임스페이스의 각 클래스에 대한 자세한 내용은 .NET Framework 클래스 라이브러리의 <xref:System.Xml.Schema> 네임스페이스 참조 문서를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="c96a4-122">For more information about each class in the <xref:System.Xml.Schema> namespace, see the <xref:System.Xml.Schema> namespace reference documentation in the .NET Framework class library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96a4-123">참조</span><span class="sxs-lookup"><span data-stu-id="c96a4-123">See also</span></span>

- [<span data-ttu-id="c96a4-124">XML 스키마 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="c96a4-124">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="c96a4-125">XML 스키마 빌드</span><span class="sxs-lookup"><span data-stu-id="c96a4-125">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="c96a4-126">XML 스키마 통과</span><span class="sxs-lookup"><span data-stu-id="c96a4-126">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)
- [<span data-ttu-id="c96a4-127">XML 스키마 편집</span><span class="sxs-lookup"><span data-stu-id="c96a4-127">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="c96a4-128">XML 스키마 포함하기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="c96a4-128">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="c96a4-129">스키마 컴파일을 위한 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="c96a4-129">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="c96a4-130">Post-Schema Compilation Infoset</span><span class="sxs-lookup"><span data-stu-id="c96a4-130">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
