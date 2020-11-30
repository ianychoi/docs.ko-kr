---
title: XmlSchemaCollection을 사용하여 XSD(XML 스키마) 유효성 검사
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ad0b5717-3d32-41ad-a4d7-072c3e492b82
ms.openlocfilehash: bd6bb440a00b3e485f4e6794e538f761267236b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733011"
---
# <a name="xml-schema-xsd-validation-with-xmlschemacollection"></a><span data-ttu-id="981ec-102">XmlSchemaCollection을 사용하여 XSD(XML 스키마) 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="981ec-102">XML Schema (XSD) Validation with XmlSchemaCollection</span></span>

<span data-ttu-id="981ec-103"><xref:System.Xml.Schema.XmlSchemaCollection>을 사용하여 XSD(XML 스키마 정의 언어) 스키마에 대해 XML 문서의 유효성을 검사할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-103">You can use the <xref:System.Xml.Schema.XmlSchemaCollection> to validate an XML document against XML Schema definition language (XSD) schemas.</span></span> <span data-ttu-id="981ec-104"><xref:System.Xml.Schema.XmlSchemaCollection>은 스키마를 컬렉션에 저장함으로써 유효성을 검사할 때마다 메모리에 로드되지 않으므로 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-104">The <xref:System.Xml.Schema.XmlSchemaCollection> improves performance by storing schemas in the collection so they are not loaded into memory each time validation occurs.</span></span> <span data-ttu-id="981ec-105">스키마가 스키마 컬렉션에 있을 경우 `schemaLocation` 특성을 사용하여 컬렉션에서 스키마를 찾을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-105">If the schema exists in the schema collection, the `schemaLocation` attribute is used to look up the schema in the collection.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="981ec-106">이제 <xref:System.Xml.Schema.XmlSchemaCollection> 클래스는 사용되지 않으며 <xref:System.Xml.Schema.XmlSchemaSet> 클래스로 대체되었습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-106">The <xref:System.Xml.Schema.XmlSchemaCollection> class is now obsolete and has been replaced with the <xref:System.Xml.Schema.XmlSchemaSet> class.</span></span> <span data-ttu-id="981ec-107"><xref:System.Xml.Schema.XmlSchemaSet> 클래스에 대한 자세한 내용은 [스키마 컴파일을 위한 XmlSchemaSet](xmlschemaset-for-schema-compilation.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="981ec-107">For more information about the <xref:System.Xml.Schema.XmlSchemaSet> class see, [XmlSchemaSet for Schema Compilation](xmlschemaset-for-schema-compilation.md).</span></span>  
  
 <span data-ttu-id="981ec-108">다음 예제에서는 데이터 파일의 루트 요소를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-108">The following example shows the root element of a data file.</span></span>  
  
```xml  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"  
    xmlns="urn:bookstore-schema"  
    elementFormDefault="qualified"  
    targetNamespace="urn:bookstore-schema">  
```  
  
 <span data-ttu-id="981ec-109">이 예제에서는 `targetNamespace` 특성 값이 `urn:bookstore-schema`입니다. 이 값은 스키마를 <xref:System.Xml.Schema.XmlSchemaCollection>에 추가할 때 사용되는 네임스페이스와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-109">For this example, the value of the `targetNamespace` attribute is `urn:bookstore-schema`, which is the same namespace that is used when adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
 <span data-ttu-id="981ec-110">다음 코드 예제에서는 XML 스키마를 <xref:System.Xml.Schema.XmlSchemaCollection>에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-110">The following code example adds an XML Schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span>  
  
```vb  
Dim xsc As New XmlSchemaCollection()  
' XML Schema.  
xsc.Add("urn:bookstore-schema", schema)
reader = New XmlTextReader(filename)  
vreader = New XmlValidatingReader(reader)  
vreader.Schemas.Add(xsc)  
```  
  
```csharp  
XmlSchemaCollection xsc = new XmlSchemaCollection();  
// XML Schema.  
xsc.Add("urn:bookstore-schema", schema);  
reader = new XmlTextReader (filename);  
vreader = new XmlValidatingReader (reader);  
vreader.Schemas.Add(xsc);  
```  
  
 <span data-ttu-id="981ec-111">`targetNamespace`에 대한 `namespaceURI` 메서드에 <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> 속성을 추가할 때 일반적으로 <xref:System.Xml.Schema.XmlSchemaCollection> 특성을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-111">The `targetNamespace` attribute is generally used when you add the `namespaceURI` property in the <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> method for the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="981ec-112"><xref:System.Xml.Schema.XmlSchemaCollection>에 스키마를 추가하기 전에 null 참조를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-112">You can specify a null reference before adding the schema to the <xref:System.Xml.Schema.XmlSchemaCollection>.</span></span> <span data-ttu-id="981ec-113">네임스페이스가 없는 스키마에는 빈 문자열("")을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-113">An empty string ("") should be used for schemas without a namespace.</span></span> <span data-ttu-id="981ec-114"><xref:System.Xml.Schema.XmlSchemaCollection>에는 네임스페이스가 없는 스키마가 한 개만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-114">The <xref:System.Xml.Schema.XmlSchemaCollection> can have only one schema without a namespace.</span></span>  
  
 <span data-ttu-id="981ec-115">다음 코드 예제에서는 XML 스키마 HeadCount.xsd를 <xref:System.Xml.Schema.XmlSchemaCollection>에 추가하고 HeadCount.xml의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-115">The following code example adds an XML Schema, HeadCount.xsd, to the <xref:System.Xml.Schema.XmlSchemaCollection> and validates HeadCount.xml.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd")  
         vr.ValidationType = ValidationType.Schema  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xsdHeadCount", "HeadCount.xsd");  
         vr.ValidationType = ValidationType.Schema;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read());  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage  :{0}", args.Message);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="981ec-116">다음에서는 유효성을 검사할 입력 파일 HeadCount.xml의 내용을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-116">The following outlines the contents of the input file, HeadCount.xml, to be validated.</span></span>  
  
```xml  
<!--Load HeadCount.xsd in SchemaCollection for Validation-->  
<hc:HeadCount xmlns:hc='xsdHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</hc:HeadCount>  
```  
  
 <span data-ttu-id="981ec-117">다음에서는 유효성을 검사할 XML 스키마 파일 HeadCount.xsd의 내용을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-117">The following outlines the contents of the XML Schema file, HeadCount.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema xmlns="xsdHeadCount" targetNamespace="xsdHeadCount" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
   <xs:element name='HeadCount' type="HEADCOUNT"/>  
   <xs:complexType name="HEADCOUNT">  
      <xs:sequence>  
         <xs:element name='Name' type='xs:string' maxOccurs='unbounded'/>  
      </xs:sequence>  
      <xs:attribute name='division' type='xs:int' use='optional' default='8'/>  
   </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="981ec-118">다음 코드 예제에서는 <xref:System.Xml.XmlValidatingReader>를 사용하는 <xref:System.Xml.XmlTextReader>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-118">The following code example creates an <xref:System.Xml.XmlValidatingReader> that takes an <xref:System.Xml.XmlTextReader>.</span></span> <span data-ttu-id="981ec-119">XML 스키마 sample4.xsd에 대해 입력 파일 sample4.xml의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-119">The input file, sample4.xml, is validated against the XML Schema, sample4.xsd.</span></span>  
  
```vb  
Dim tr As New XmlTextReader("sample4.xml")  
Dim vr As New XmlValidatingReader(tr)  
vr.ValidationType = ValidationType.Schema  
vr.Schemas.Add("datatypesTest", "sample4.xsd")  
AddHandler vr.ValidationEventHandler, AddressOf ValidationCallBack  
While vr.Read()  
   Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name)  
End While  
```  
  
```csharp  
XmlTextReader tr = new XmlTextReader("sample4.xml");  
XmlValidatingReader vr = new XmlValidatingReader(tr);  
vr.ValidationType = ValidationType.Schema;  
        vr.Schemas.Add("datatypesTest", "sample4.xsd");  
vr.ValidationEventHandler += new ValidationEventHandler(ValidationCallBack);  
while(vr.Read()) {  
    Console.WriteLine("NodeType: {0} NodeName: {1}", vr.NodeType, vr.Name);  
    }  
```  
  
 <span data-ttu-id="981ec-120">다음에서는 유효성을 검사할 입력 파일 sample4.xml의 내용을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-120">The following outlines the contents of the input file, sample4.xml, to be validated.</span></span>  
  
```xml  
<datatypes xmlns="datatypesTest">  
    <number>  
        <number_1>123</number_1>  
    </number>  
</datatypes>  
```  
  
 <span data-ttu-id="981ec-121">다음에서는 유효성을 검사할 XML 스키마 파일 sample4.xsd의 내용을 요약합니다.</span><span class="sxs-lookup"><span data-stu-id="981ec-121">The following outlines the contents of the XML Schema file, sample4.xsd, to be validated against.</span></span>  
  
```xml  
<xs:schema
    xmlns:xs="http://www.w3.org/2001/XMLSchema"
    xmlns:tns="datatypesTest"
    targetNamespace="datatypesTest"  
    elementFormDefault="qualified">  
  
<xs:element name = "datatypes">  
  <xs:complexType>  
    <xs:all>  
        <xs:element name="number">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="number_1" type="xs:decimal" maxOccurs="unbounded"/>  
                </xs:sequence>  
            </xs:complexType>  
        </xs:element>  
    </xs:all>  
  </xs:complexType>  
</xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="981ec-122">참조</span><span class="sxs-lookup"><span data-stu-id="981ec-122">See also</span></span>

- <xref:System.Xml.XmlParserContext>
- <xref:System.Xml.XmlValidatingReader.ValidationEventHandler?displayProperty=nameWithType>
- <xref:System.Xml.XmlValidatingReader.Schemas%2A?displayProperty=nameWithType>
- [<span data-ttu-id="981ec-123">XmlSchemaCollection 스키마 컴파일</span><span class="sxs-lookup"><span data-stu-id="981ec-123">XmlSchemaCollection Schema Compilation</span></span>](xmlschemacollection-schema-compilation.md)
