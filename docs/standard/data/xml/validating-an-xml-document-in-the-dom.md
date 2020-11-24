---
title: DOM에서의 XML 문서 유효성 검사
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2c61c920-d0f8-4c72-bfcc-6524570f3060
ms.openlocfilehash: db3748d1d0e1a5687219d5b07d1261639a4ef670
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94819294"
---
# <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="f270d-102">DOM에서의 XML 문서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f270d-102">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="f270d-103">기본적으로 <xref:System.Xml.XmlDocument> 클래스는 DOM(문서 개체 모델)에서 XSD(XML 스키마 정의 언어) 스키마 또는 DTD(문서 종류 정의)에 대해 XML의 유효성을 검사하지 않으며 XML이 잘 구성되었는지만 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-103">The<xref:System.Xml.XmlDocument> class does not validate the XML in the Document Object Model (DOM) against an XML Schema definition language (XSD) schema or document type definition (DTD) by default; the XML is only verified to be well-formed.</span></span>

<span data-ttu-id="f270d-104">DOM에서 XML의 유효성을 검사하려면 스키마의 유효성을 검사하는 <xref:System.Xml.XmlReader>를 <xref:System.Xml.XmlDocument.Load%2A> 클래스의 <xref:System.Xml.XmlDocument> 메서드에 전달하여 DOM에 XML을 로드할 때 유효성을 검사하거나 <xref:System.Xml.XmlDocument.Validate%2A> 클래스의 <xref:System.Xml.XmlDocument> 메서드를 사용하여 DOM에서 이전에 유효성을 검사하지 않은 XML 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-104">To validate the XML in the DOM, you can validate the XML as it is loaded into the DOM by passing a schema-validating <xref:System.Xml.XmlReader> to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class, or validate a previously unvalidated XML document in the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

## <a name="validating-an-xml-document-as-it-is-loaded-into-the-dom"></a><span data-ttu-id="f270d-105">XML 문서를 DOM에 로드할 때 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f270d-105">Validating an XML Document As It Is Loaded into the DOM</span></span>

<span data-ttu-id="f270d-106">유효성을 검사하는 <xref:System.Xml.XmlDocument>가 <xref:System.Xml.XmlReader> 클래스의 <xref:System.Xml.XmlDocument.Load%2A> 메서드에 전달되면 <xref:System.Xml.XmlDocument> 클래스는 XML 데이터를 DOM에 로드할 때 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-106">The <xref:System.Xml.XmlDocument> class validates the XML data as it is loaded into the DOM when a validating <xref:System.Xml.XmlReader> is passed to the <xref:System.Xml.XmlDocument.Load%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span>

<span data-ttu-id="f270d-107">유효성 검사를 수행한 후에는 스키마 기본값이 적용되고 필요한 경우 텍스트 값이 atomic 값으로 변환되며 형식 정보는 유효성이 검사된 정보 항목과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-107">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="f270d-108">그 결과, 형식화된 XML 데이터가 이전에 형식화되지 않은 XML 데이터를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-108">As a result, typed XML data replaces previously untyped XML data.</span></span>

### <a name="creating-an-xml-schema-validating-xmlreader"></a><span data-ttu-id="f270d-109">XML 스키마의 유효성을 검사하는 XmlReader 만들기</span><span class="sxs-lookup"><span data-stu-id="f270d-109">Creating an XML Schema-Validating XmlReader</span></span>

<span data-ttu-id="f270d-110">XML 스키마의 유효성을 검사하는 <xref:System.Xml.XmlReader>를 만들려면 다음 단계를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-110">To create an XML schema-validating <xref:System.Xml.XmlReader>, follow these steps.</span></span>

1. <span data-ttu-id="f270d-111">새 <xref:System.Xml.XmlReaderSettings> 인스턴스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-111">Construct a new <xref:System.Xml.XmlReaderSettings> instance.</span></span>

2. <span data-ttu-id="f270d-112">XML 스키마를 <xref:System.Xml.XmlReaderSettings.Schemas%2A> 인스턴스의 <xref:System.Xml.XmlReaderSettings> 속성에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-112">Add an XML schema to the <xref:System.Xml.XmlReaderSettings.Schemas%2A> property of the <xref:System.Xml.XmlReaderSettings> instance.</span></span>

3. <span data-ttu-id="f270d-113">`Schema`를 <xref:System.Xml.XmlReaderSettings.ValidationType%2A>으로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-113">Specify `Schema` as the <xref:System.Xml.XmlReaderSettings.ValidationType%2A>.</span></span>

4. <span data-ttu-id="f270d-114">필요에 따라 유효성 검사 중에 발생하는 스키마 유효성 검사 오류 및 경고를 처리하는 <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> 및 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>를 지정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-114">Optionally specify <xref:System.Xml.XmlReaderSettings.ValidationFlags%2A> and a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> to handle schema validation errors and warnings encountered during validation.</span></span>

5. <span data-ttu-id="f270d-115">마지막으로 XML 문서와 함께 <xref:System.Xml.XmlReaderSettings> 개체를 <xref:System.Xml.XmlReader.Create%2A> 클래스의 <xref:System.Xml.XmlReader> 메서드에 전달하여 스키마의 유효성을 검사하는 <xref:System.Xml.XmlReader>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-115">Finally, pass the <xref:System.Xml.XmlReaderSettings> object to the <xref:System.Xml.XmlReader.Create%2A> method of the <xref:System.Xml.XmlReader> class along with the XML document, creating a schema-validating <xref:System.Xml.XmlReader>.</span></span>

### <a name="example"></a><span data-ttu-id="f270d-116">예제</span><span class="sxs-lookup"><span data-stu-id="f270d-116">Example</span></span>

<span data-ttu-id="f270d-117">다음 코드 예제에서는 스키마의 유효성을 검사하는 <xref:System.Xml.XmlReader>가 DOM에 로드된 XML 데이터의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-117">In the code example that follows, a schema-validating <xref:System.Xml.XmlReader> validates the XML data loaded into the DOM.</span></span> <span data-ttu-id="f270d-118">또한 XML 문서를 잘못 수정하고 이 문서의 유효성을 다시 검사하므로 스키마 유효성 검사 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-118">Invalid modifications are made to the XML document and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="f270d-119">마지막으로 오류 중 하나를 수정한 다음 XML 문서의 일부에 대한 유효성을 부분적으로 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-119">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-cpp[XmlDocumentValidation.Load#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlDocumentValidation.Load/CPP/XmlDocumentValidationExample.cpp#1)]
[!code-csharp[XmlDocumentValidation.Load#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Load/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Load#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Load/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="f270d-120">이 예제에서는 `contosoBooks.xml` 파일을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-120">The example takes the `contosoBooks.xml` file as input.</span></span>

[!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]

<span data-ttu-id="f270d-121">이 예제에서는 `contosoBooks.xsd` 파일을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-121">The example also takes the `contosoBooks.xsd` file as input.</span></span>

[!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]

<span data-ttu-id="f270d-122">XML 데이터를 DOM에 로드할 때 유효성을 검사하는 경우 다음을 고려해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-122">Consider the following when validating XML data as it is loaded into the DOM.</span></span>

- <span data-ttu-id="f270d-123">위 예제에서 잘못된 형식이 발견될 때마다 <xref:System.Xml.XmlReaderSettings.ValidationEventHandler>가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-123">In the above example, the <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is called whenever an invalid type is encountered.</span></span> <span data-ttu-id="f270d-124"><xref:System.Xml.XmlReaderSettings.ValidationEventHandler>가 유효성을 검사하는 <xref:System.Xml.XmlReader>에 대해 설정되어 있지 않으면 특성 또는 요소 형식이 유효성 검사 스키마에 지정된 해당 형식과 일치하지 않은 경우 <xref:System.Xml.Schema.XmlSchemaValidationException>가 호출될 때 <xref:System.Xml.XmlDocument.Load%2A>이 throw됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-124">If a <xref:System.Xml.XmlReaderSettings.ValidationEventHandler> is not set on the validating <xref:System.Xml.XmlReader>,an <xref:System.Xml.Schema.XmlSchemaValidationException> is thrown when <xref:System.Xml.XmlDocument.Load%2A> is called if any attribute or element type does not match the corresponding type specified in the validating schema.</span></span>

- <span data-ttu-id="f270d-125">기본값을 정의하는 스키마가 연결되어 있는 XML 문서를 <xref:System.Xml.XmlDocument> 개체에 로드하면 <xref:System.Xml.XmlDocument>는 이 기본값이 XML 문서에 나타난 것처럼 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-125">When an XML document is loaded into an <xref:System.Xml.XmlDocument> object with an associated schema that defines default values, the <xref:System.Xml.XmlDocument> treats these defaults as if they appeared in the XML document.</span></span> <span data-ttu-id="f270d-126">그러므로 <xref:System.Xml.XmlReader.IsEmptyElement%2A> 속성은 항상 스키마의 기본값으로 설정된 요소에 대해 `false`를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-126">This means that the <xref:System.Xml.XmlReader.IsEmptyElement%2A> property always returns `false` for an element that was defaulted from the schema.</span></span> <span data-ttu-id="f270d-127">XML 문서에서도 빈 요소로 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-127">Even if in the XML document, it was written as an empty element.</span></span>

## <a name="validating-an-xml-document-in-the-dom"></a><span data-ttu-id="f270d-128">DOM에서의 XML 문서 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="f270d-128">Validating an XML Document in the DOM</span></span>

<span data-ttu-id="f270d-129"><xref:System.Xml.XmlDocument.Validate%2A> 클래스의 <xref:System.Xml.XmlDocument> 메서드는 <xref:System.Xml.XmlDocument> 개체의 <xref:System.Xml.XmlDocument.Schemas%2A> 속성에 있는 스키마에 대해 DOM에 로드된 XML 데이터의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-129">The <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class validates the XML data loaded in the DOM against the schemas in the <xref:System.Xml.XmlDocument> object's <xref:System.Xml.XmlDocument.Schemas%2A> property.</span></span> <span data-ttu-id="f270d-130">유효성 검사를 수행한 후에는 스키마 기본값이 적용되고 필요한 경우 텍스트 값이 atomic 값으로 변환되며 형식 정보는 유효성이 검사된 정보 항목과 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-130">After successful validation, schema defaults are applied, text values are converted to atomic values as necessary, and type information is associated with validated information items.</span></span> <span data-ttu-id="f270d-131">그 결과, 형식화된 XML 데이터가 이전에 형식화되지 않은 XML 데이터를 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-131">As a result, typed XML data replaces previously untyped XML data.</span></span>

<span data-ttu-id="f270d-132">아래 예제는 위의 "XML 문서를 DOM에 로드할 때 유효성 검사"의 예제와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-132">The example below is similar to the example in "Validating an XML Document As It Is Loaded into the DOM" above.</span></span> <span data-ttu-id="f270d-133">이 예제에서는 XML 문서를 DOM에 로드할 때 유효성을 검사하지 않고 DOM에 로드한 후 <xref:System.Xml.XmlDocument.Validate%2A> 클래스의 <xref:System.Xml.XmlDocument> 메서드를 사용하여 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-133">In this example, the XML document is not validated as it is loaded into the DOM, but rather is validated after it has been loaded into the DOM using the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="f270d-134"><xref:System.Xml.XmlDocument.Validate%2A> 메서드는 <xref:System.Xml.XmlDocument.Schemas%2A>의 <xref:System.Xml.XmlDocument> 속성에 포함된 XML 스키마에 대해 XML 문서의 유효성을 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-134">The <xref:System.Xml.XmlDocument.Validate%2A> method validates the XML document against the XML schemas contained in the <xref:System.Xml.XmlDocument.Schemas%2A> property of the <xref:System.Xml.XmlDocument>.</span></span> <span data-ttu-id="f270d-135">또한 XML 문서를 잘못 수정하고 이 문서의 유효성을 다시 검사하므로 스키마 유효성 검사 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-135">Invalid modifications are then made to the XML document, and the document is then revalidated, causing schema validation errors.</span></span> <span data-ttu-id="f270d-136">마지막으로 오류 중 하나를 수정한 다음 XML 문서의 일부에 대한 유효성을 부분적으로 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-136">Finally, one of the errors is corrected, and then part of the XML document is partially validated.</span></span>

[!code-csharp[XmlDocumentValidation.Validate#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlDocumentValidation.Validate/CS/XmlDocumentValidationExample.cs#1)]
[!code-vb[XmlDocumentValidation.Validate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlDocumentValidation.Validate/VB/XmlDocumentValidationExample.vb#1)]

<span data-ttu-id="f270d-137">이 예제에서는 위의 "XML 문서를 DOM에 로드할 때 유효성 검사"에 참조된 `contosoBooks.xml` 및 `contosoBooks.xsd` 파일을 입력으로 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-137">The example takes as input the `contosoBooks.xml` and `contosoBooks.xsd` files referred to in "Validating an XML Document as it is Loaded into the DOM" above.</span></span>

## <a name="handling-validation-errors-and-warnings"></a><span data-ttu-id="f270d-138">유효성 검사 오류 및 경고 처리</span><span class="sxs-lookup"><span data-stu-id="f270d-138">Handling Validation Errors and Warnings</span></span>

<span data-ttu-id="f270d-139">DOM에 로드된 XML 데이터의 유효성을 검사하면 XML 스키마 유효성 검사 오류가 보고됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-139">XML schema validation errors are reported when validating XML data loaded in the DOM.</span></span> <span data-ttu-id="f270d-140">XML 데이터를 로드할 때 수행한 유효성 검사 또는 이전에 유효성을 검사하지 않은 XML 문서의 유효성 검사에서 발견된 모든 스키마 유효성 검사 오류에 대해 알림을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-140">You are notified about all schema validation errors found while validating the XML data as it is being loaded, or when validating a previously unvalidated XML document.</span></span>

<span data-ttu-id="f270d-141">유효성 검사 오류는 <xref:System.Xml.Schema.ValidationEventHandler>에서 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-141">Validation errors are handled by the <xref:System.Xml.Schema.ValidationEventHandler>.</span></span> <span data-ttu-id="f270d-142"><xref:System.Xml.Schema.ValidationEventHandler>를 <xref:System.Xml.XmlReaderSettings> 인스턴스에 지정하거나 <xref:System.Xml.XmlDocument.Validate%2A> 클래스의 <xref:System.Xml.XmlDocument> 메서드에 전달한 경우 <xref:System.Xml.Schema.ValidationEventHandler>는 스키마 유효성 검사 오류를 처리하며 그렇지 않은 경우에는 스키마 유효성 검사 오류가 발생할 때 <xref:System.Xml.Schema.XmlSchemaValidationException>이 일어납니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-142">If a <xref:System.Xml.Schema.ValidationEventHandler> was assigned to the <xref:System.Xml.XmlReaderSettings> instance, or passed to the <xref:System.Xml.XmlDocument.Validate%2A> method of the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.Schema.ValidationEventHandler> will handle schema validation errors; otherwise an <xref:System.Xml.Schema.XmlSchemaValidationException> is raised when a schema validation error is encountered.</span></span>

> [!NOTE]
> <span data-ttu-id="f270d-143"><xref:System.Xml.Schema.ValidationEventHandler>에 의해 예외가 발생하여 프로세스가 중지되지 않은 경우에는 스키마 유효성 검사 오류가 발생해도 XML 데이터가 DOM에 로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-143">The XML data is loaded into the DOM despite schema validation errors unless your <xref:System.Xml.Schema.ValidationEventHandler> raises an exception to stop the process.</span></span>
>
> <span data-ttu-id="f270d-144"><xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> 플래그를 <xref:System.Xml.XmlReaderSettings> 개체에 지정하지 않으면 스키마 유효성 검사 경고가 보고되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f270d-144">Schema validation warnings are not reported unless the <xref:System.Xml.Schema.XmlSchemaValidationFlags.ReportValidationWarnings> flag is specified to the <xref:System.Xml.XmlReaderSettings> object.</span></span>

 <span data-ttu-id="f270d-145"><xref:System.Xml.Schema.ValidationEventHandler>를 설명하는 예제는 위의 "XML 문서를 DOM에 로드할 때 유효성 검사" 및 "DOM에서의 XML 문서 유효성 검사"를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="f270d-145">For examples illustrating the <xref:System.Xml.Schema.ValidationEventHandler>, see "Validating an XML Document As It Is Loaded into the DOM" and "Validating an XML Document in the DOM" above.</span></span>

## <a name="see-also"></a><span data-ttu-id="f270d-146">참조</span><span class="sxs-lookup"><span data-stu-id="f270d-146">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XmlReader>
- <xref:System.Xml.Schema.ValidationEventHandler>
- <xref:System.Xml.XmlReaderSettings>
- [<span data-ttu-id="f270d-147">DOM 모델을 사용하여 XML 데이터 처리</span><span class="sxs-lookup"><span data-stu-id="f270d-147">Process XML Data Using the DOM Model</span></span>](process-xml-data-using-the-dom-model.md)
- [<span data-ttu-id="f270d-148">XML 스키마 사용</span><span class="sxs-lookup"><span data-stu-id="f270d-148">Working with XML Schemas</span></span>](working-with-xml-schemas.md)
