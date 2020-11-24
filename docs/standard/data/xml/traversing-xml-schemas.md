---
title: XML 스키마 통과
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
ms.assetid: cce69574-5861-4a30-b730-2e18d915d8ee
ms.openlocfilehash: 6371d7e16af45eebf09f95bce2864be3bf44321e
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94824677"
---
# <a name="traversing-xml-schemas"></a><span data-ttu-id="33e10-102">XML 스키마 통과</span><span class="sxs-lookup"><span data-stu-id="33e10-102">Traversing XML Schemas</span></span>

<span data-ttu-id="33e10-103">SOM(스키마 개체 모델) API를 사용하여 XML 스키마를 통과하면 SOM에 저장된 요소, 특성 및 형식에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-103">Traversing an XML schema using the Schema Object Model (SOM) API provides access to the elements, attributes, and types stored in the SOM.</span></span> <span data-ttu-id="33e10-104">SOM에 로드된 XML 스키마를 통과하는 것은 SOM API를 사용하여 XML 스키마를 편집하는 첫 번째 단계이기도 합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-104">Traversing an XML schema loaded into the SOM is also the first step in editing an XML schema using the SOM API.</span></span>

## <a name="traversing-an-xml-schema"></a><span data-ttu-id="33e10-105">XML 스키마 통과</span><span class="sxs-lookup"><span data-stu-id="33e10-105">Traversing an XML Schema</span></span>

<span data-ttu-id="33e10-106">다음 <xref:System.Xml.Schema.XmlSchema> 클래스 속성에서는 XML 스키마에 추가된 모든 전역 항목의 컬렉션에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-106">The following properties of the <xref:System.Xml.Schema.XmlSchema> class provide access to the collection of all global items added to the XML schema.</span></span>

|<span data-ttu-id="33e10-107">속성</span><span class="sxs-lookup"><span data-stu-id="33e10-107">Property</span></span>|<span data-ttu-id="33e10-108">컬렉션 또는 배열에 저장된 개체 형식</span><span class="sxs-lookup"><span data-stu-id="33e10-108">Object type stored in the collection or array</span></span>|
|--------------|---------------------------------------------------|
|<xref:System.Xml.Schema.XmlSchema.Elements%2A>|<xref:System.Xml.Schema.XmlSchemaElement>|
|<xref:System.Xml.Schema.XmlSchema.Attributes%2A>|<xref:System.Xml.Schema.XmlSchemaAttribute>|
|<xref:System.Xml.Schema.XmlSchema.AttributeGroups%2A>|<xref:System.Xml.Schema.XmlSchemaAttributeGroup>|
|<xref:System.Xml.Schema.XmlSchema.Groups%2A>|<xref:System.Xml.Schema.XmlSchemaGroup>|
|<xref:System.Xml.Schema.XmlSchema.Includes%2A>|<span data-ttu-id="33e10-109"><xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport> 또는 <xref:System.Xml.Schema.XmlSchemaRedefine></span><span class="sxs-lookup"><span data-stu-id="33e10-109"><xref:System.Xml.Schema.XmlSchemaExternal>, <xref:System.Xml.Schema.XmlSchemaInclude>, <xref:System.Xml.Schema.XmlSchemaImport>, or <xref:System.Xml.Schema.XmlSchemaRedefine></span></span>|
|<xref:System.Xml.Schema.XmlSchema.Items%2A>|<span data-ttu-id="33e10-110"><xref:System.Xml.Schema.XmlSchemaObject>(모든 전역 수준 요소, 특성 및 형식에 대한 액세스 제공)</span><span class="sxs-lookup"><span data-stu-id="33e10-110"><xref:System.Xml.Schema.XmlSchemaObject> (provides access to all global level elements, attributes, and types).</span></span>|
|<xref:System.Xml.Schema.XmlSchema.Notations%2A>|<xref:System.Xml.Schema.XmlSchemaNotation>|
|<xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A>|<span data-ttu-id="33e10-111"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span><span class="sxs-lookup"><span data-stu-id="33e10-111"><xref:System.Xml.Schema.XmlSchemaType>, <xref:System.Xml.Schema.XmlSchemaSimpleType>, <xref:System.Xml.Schema.XmlSchemaComplexType></span></span>|
|<xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A>|<span data-ttu-id="33e10-112"><xref:System.Xml.XmlAttribute>(스키마 네임스페이스에 속하지 않은 특성에 대한 액세스 제공)</span><span class="sxs-lookup"><span data-stu-id="33e10-112"><xref:System.Xml.XmlAttribute> (provides access to attributes that do not belong to the schema namespace)</span></span>|

> [!NOTE]
> <span data-ttu-id="33e10-113"><xref:System.Xml.Schema.XmlSchema.Items%2A> 속성을 제외하고 위의 표에 나열된 모든 속성은 스키마를 컴파일해야 사용할 수 있는 PSCI(Post-Schema-Compilation-Infoset) 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-113">All of the properties listed in the table above, except for the <xref:System.Xml.Schema.XmlSchema.Items%2A> property, are Post-Schema-Compilation-Infoset (PSCI) properties that are not available until the schema has been compiled.</span></span> <span data-ttu-id="33e10-114"><xref:System.Xml.Schema.XmlSchema.Items%2A> 속성은 스키마를 컴파일하기 전에 모든 전역 수준 요소, 특성 및 형식에 액세스하여 이를 편집하는 데 사용할 수 있는 pre-schema-compilation 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-114">The <xref:System.Xml.Schema.XmlSchema.Items%2A> property is a pre-schema-compilation property that can be used before the schema has been compiled to access and edit all global level elements, attributes, and types.</span></span>
>
> <span data-ttu-id="33e10-115"><xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> 속성은 스키마 네임스페이스에 속하지 않은 모든 특성에 대한 액세스를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-115">The <xref:System.Xml.Schema.XmlSchema.UnhandledAttributes%2A> property provides access to all the attributes that do not belong to the schema namespace.</span></span> <span data-ttu-id="33e10-116">이러한 특성은 스키마 프로세서로 처리되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-116">These attributes are not processed by the schema processor.</span></span>

<span data-ttu-id="33e10-117">다음 코드 예제에서는 [XML 스키마 빌드](building-xml-schemas.md) 항목에서 만든 고객 스키마를 트래버스하는 예를 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-117">The code example that follows demonstrates traversing the customer schema created in the [Building XML Schemas](building-xml-schemas.md) topic.</span></span> <span data-ttu-id="33e10-118">이 코드 예제에서는 위에서 설명한 컬렉션을 사용하여 스키마를 통과하는 것을 보여 주고 스키마의 모든 요소와 특성을 콘솔에 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-118">The code example demonstrates traversing the schema using the collections described above and writes all the elements and attributes in the schema to the console.</span></span>

<span data-ttu-id="33e10-119">이 샘플은 다음과 같은 단계로 고객 스키마를 통과합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-119">The sample traverses the customer schema in the following steps.</span></span>

1. <span data-ttu-id="33e10-120">고객 스키마를 새 <xref:System.Xml.Schema.XmlSchemaSet> 개체에 추가한 다음 컴파일합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-120">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="33e10-121">스키마를 읽거나 컴파일할 때 발생하는 모든 스키마 유효성 검사 경고 및 오류는 <xref:System.Xml.Schema.ValidationEventHandler> 대리자에서 처리됩니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-121">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>

2. <span data-ttu-id="33e10-122"><xref:System.Xml.Schema.XmlSchema> 속성을 반복하여 <xref:System.Xml.Schema.XmlSchemaSet>에서 컴파일된 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> 개체를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-122">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="33e10-123">스키마가 컴파일되므로 PSCI(Post-Schema-Compilation-Infoset) 속성에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-123">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>

3. <span data-ttu-id="33e10-124">각 요소 이름을 콘솔에 작성하는 post-schema-compilation <xref:System.Xml.Schema.XmlSchemaElement> 컬렉션의 <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> 컬렉션에서 각 <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-124">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection writing the name of each element to the console.</span></span>

4. <span data-ttu-id="33e10-125">`Customer` 클래스를 사용하여 <xref:System.Xml.Schema.XmlSchemaComplexType> 요소의 복합 형식을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-125">Gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>

5. <span data-ttu-id="33e10-126">복합 형식에 특성이 있을 경우 <xref:System.Collections.IDictionaryEnumerator>가 각 <xref:System.Xml.Schema.XmlSchemaAttribute>를 열거하도록 하고 그 이름을 콘솔에 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-126">If the complex type has any attributes, gets an <xref:System.Collections.IDictionaryEnumerator> to enumerate over each <xref:System.Xml.Schema.XmlSchemaAttribute> and writes its name to the console.</span></span>

6. <span data-ttu-id="33e10-127"><xref:System.Xml.Schema.XmlSchemaSequence> 클래스를 사용하여 복합 형식의 sequence 파티클을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-127">Gets the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>

7. <span data-ttu-id="33e10-128">각 자식 요소의 이름을 콘솔에 작성하는 <xref:System.Xml.Schema.XmlSchemaElement> 컬렉션에서 각 <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType>를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-128">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection writing the name of each child element to the console.</span></span>

<span data-ttu-id="33e10-129">다음은 전체 코드 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-129">The following is the complete code example.</span></span>

[!code-cpp[XmlSchemaTraverseExample#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaTraverseExample/CPP/XmlSchemaTraverseExample.cpp#1)]
[!code-csharp[XmlSchemaTraverseExample#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaTraverseExample/CS/XmlSchemaTraverseExample.cs#1)]
[!code-vb[XmlSchemaTraverseExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaTraverseExample/VB/XmlSchemaTraverseExample.vb#1)]

<span data-ttu-id="33e10-130"><xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> 속성이 사용자 정의 단순 형식 또는 복합 형식인 경우 이 속성은 <xref:System.Xml.Schema.XmlSchemaSimpleType> 또는 <xref:System.Xml.Schema.XmlSchemaComplexType>일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-130">The <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A?displayProperty=nameWithType> property can be <xref:System.Xml.Schema.XmlSchemaSimpleType>, or <xref:System.Xml.Schema.XmlSchemaComplexType> if it is a user-defined simple type or a complex type.</span></span> <span data-ttu-id="33e10-131">또한 W3C XML 스키마 권장 사항에 정의된 기본 제공 데이터 형식 중 하나인 경우 <xref:System.Xml.Schema.XmlSchemaDatatype>일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-131">It can also be <xref:System.Xml.Schema.XmlSchemaDatatype> if it is one of the built-in datatypes defined in the W3C XML Schema Recommendation.</span></span> <span data-ttu-id="33e10-132">고객 스키마에서 <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> 요소의 `Customer`은 <xref:System.Xml.Schema.XmlSchemaComplexType>이고 `FirstName` 및 `LastName` 요소는 <xref:System.Xml.Schema.XmlSchemaSimpleType>입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-132">In the customer schema, the <xref:System.Xml.Schema.XmlSchemaElement.ElementSchemaType%2A> of the `Customer` element is <xref:System.Xml.Schema.XmlSchemaComplexType>, and the `FirstName` and `LastName` elements are <xref:System.Xml.Schema.XmlSchemaSimpleType>.</span></span>

<span data-ttu-id="33e10-133">[XML 스키마 빌드](building-xml-schemas.md) 항목의 코드 예제에서는 <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> 컬렉션을 사용하여 `Customer` 요소에 `CustomerId` 특성을 추가했습니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-133">The code example in the [Building XML Schemas](building-xml-schemas.md) topic used the <xref:System.Xml.Schema.XmlSchemaComplexType.Attributes%2A?displayProperty=nameWithType> collection to add the attribute `CustomerId` to the `Customer` element.</span></span> <span data-ttu-id="33e10-134">이 속성은 pre-schema-compilation 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-134">This is a pre-schema-compilation property.</span></span> <span data-ttu-id="33e10-135">해당 Post-Schema-Compilation-Infoset 속성은 형식 파생을 통해 상속된 특성을 비롯하여 복합 형식의 모든 특성을 보유하는 <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="33e10-135">The corresponding Post-Schema-Compilation-Infoset property is the <xref:System.Xml.Schema.XmlSchemaComplexType.AttributeUses%2A?displayProperty=nameWithType> collection, which holds all the attributes of the complex type, including the ones that are inherited through type derivation.</span></span>

## <a name="see-also"></a><span data-ttu-id="33e10-136">참조</span><span class="sxs-lookup"><span data-stu-id="33e10-136">See also</span></span>

- [<span data-ttu-id="33e10-137">XML 스키마 개체 모델 개요</span><span class="sxs-lookup"><span data-stu-id="33e10-137">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)
- [<span data-ttu-id="33e10-138">XML 스키마 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="33e10-138">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)
- [<span data-ttu-id="33e10-139">XML 스키마 빌드</span><span class="sxs-lookup"><span data-stu-id="33e10-139">Building XML Schemas</span></span>](building-xml-schemas.md)
- [<span data-ttu-id="33e10-140">XML 스키마 편집</span><span class="sxs-lookup"><span data-stu-id="33e10-140">Editing XML Schemas</span></span>](editing-xml-schemas.md)
- [<span data-ttu-id="33e10-141">XML 스키마 포함하기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="33e10-141">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)
- [<span data-ttu-id="33e10-142">스키마 컴파일을 위한 XmlSchemaSet</span><span class="sxs-lookup"><span data-stu-id="33e10-142">XmlSchemaSet for Schema Compilation</span></span>](xmlschemaset-for-schema-compilation.md)
- [<span data-ttu-id="33e10-143">Post-Schema Compilation Infoset</span><span class="sxs-lookup"><span data-stu-id="33e10-143">Post-Schema Compilation Infoset</span></span>](post-schema-compilation-infoset.md)
