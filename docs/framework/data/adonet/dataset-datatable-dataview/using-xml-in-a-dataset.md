---
description: '자세히 알아보기: 데이터 집합에서 XML 사용'
title: 데이터 세트에서 XML 사용
ms.date: 03/30/2017
ms.assetid: 35138159-e199-49ec-baf7-1ec6777e171e
ms.openlocfilehash: 5c4216fce9c1512c95da8e27a622ba228411b641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99651420"
---
# <a name="using-xml-in-a-dataset"></a><span data-ttu-id="752be-103">데이터 세트에서 XML 사용</span><span class="sxs-lookup"><span data-stu-id="752be-103">Using XML in a DataSet</span></span>

<span data-ttu-id="752be-104">ADO.NET을 사용하면 XML 스트림이나 문서에서 <xref:System.Data.DataSet>을 채울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="752be-104">With ADO.NET you can fill a <xref:System.Data.DataSet> from an XML stream or document.</span></span> <span data-ttu-id="752be-105">XML 스트림이나 문서를 사용하여 데이터, 스키마 정보 또는 두 가지 모두를 <xref:System.Data.DataSet>에 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="752be-105">You can use the XML stream or document to supply to the <xref:System.Data.DataSet> either data, schema information, or both.</span></span> <span data-ttu-id="752be-106">XML 스트림이나 문서에서 제공되는 정보를 <xref:System.Data.DataSet>에 있는 기존 데이터나 스키마 정보와 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="752be-106">The information supplied from the XML stream or document can be combined with existing data or schema information already present in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="752be-107">또한 ADO.NET을 사용하면 스키마 사용 여부에 관계없이 <xref:System.Data.DataSet>의 XML 표현을 만들어 다른 애플리케이션이나 XML 사용 플랫폼에서 사용할 수 있도록 HTTP를 통해 <xref:System.Data.DataSet>을 전송할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="752be-107">ADO.NET also allows you to create an XML representation of a <xref:System.Data.DataSet>, with or without its schema, in order to transport the <xref:System.Data.DataSet> across HTTP for use by another application or XML-enabled platform.</span></span> <span data-ttu-id="752be-108"><xref:System.Data.DataSet>의 XML 표현에서 데이터는 XML로 작성되며, 스키마는 XML 표현의 인라인에 포함되어 있는 경우 XSD(XML 스키마 정의 언어)를 사용하여 작성됩니다.</span><span class="sxs-lookup"><span data-stu-id="752be-108">In an XML representation of a <xref:System.Data.DataSet>, the data is written in XML and the schema, if it is included inline in the representation, is written using the XML Schema definition language (XSD).</span></span> <span data-ttu-id="752be-109">XML 및 XML 스키마에서는 <xref:System.Data.DataSet>의 내용을 원격 클라이언트와 주고 받기에 알맞은 형식을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-109">XML and XML Schema provide a convenient format for transferring the contents of a <xref:System.Data.DataSet> to and from remote clients.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="752be-110">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="752be-110">In This Section</span></span>  

 [<span data-ttu-id="752be-111">DiffGram</span><span class="sxs-lookup"><span data-stu-id="752be-111">DiffGrams</span></span>](diffgrams.md)  
 <span data-ttu-id="752be-112"><xref:System.Data.DataSet>의 내용을 읽거나 쓰는 데 사용하는 XML 형식인 DiffGram에 대해 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-112">Provides details on the DiffGram, an XML format used to read and write the contents of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="752be-113">XML에서 데이터 세트 로드</span><span class="sxs-lookup"><span data-stu-id="752be-113">Loading a DataSet from XML</span></span>](loading-a-dataset-from-xml.md)  
 <span data-ttu-id="752be-114">XML 문서에서 <xref:System.Data.DataSet>의 내용을 로드할 때 고려할 여러 가지 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-114">Discusses different options to consider when loading the contents of a <xref:System.Data.DataSet> from an XML document.</span></span>  
  
 [<span data-ttu-id="752be-115">데이터 세트 콘텐츠를 XML 데이터로 작성</span><span class="sxs-lookup"><span data-stu-id="752be-115">Writing DataSet Contents as XML Data</span></span>](writing-dataset-contents-as-xml-data.md)  
 <span data-ttu-id="752be-116"><xref:System.Data.DataSet>의 내용을 XML 데이터로 생성하는 방법과 사용할 수 있는 여러 XML 형식 옵션에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-116">Discusses how to generate the contents of a <xref:System.Data.DataSet> as XML data, and the different XML format options you can use.</span></span>  
  
 [<span data-ttu-id="752be-117">XML에서 데이터 세트 스키마 정보 로드</span><span class="sxs-lookup"><span data-stu-id="752be-117">Loading DataSet Schema Information from XML</span></span>](loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="752be-118">XML에서 <xref:System.Data.DataSet>의 스키마를 로드하는 데 사용하는 <xref:System.Data.DataSet> 메서드에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-118">Discusses the <xref:System.Data.DataSet> methods used to load the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="752be-119">데이터 세트 스키마 정보를 XSD로 작성</span><span class="sxs-lookup"><span data-stu-id="752be-119">Writing DataSet Schema Information as XSD</span></span>](writing-dataset-schema-information-as-xsd.md)  
 <span data-ttu-id="752be-120">XML 스키마의 용도와 <xref:System.Data.DataSet>에서 XML 스키마를 생성하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-120">Discusses the uses for an XML Schema and how to generate one from a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="752be-121">데이터 세트 및 XmlDataDocument 동기화</span><span class="sxs-lookup"><span data-stu-id="752be-121">DataSet and XmlDataDocument Synchronization</span></span>](dataset-and-xmldatadocument-synchronization.md)  
 <span data-ttu-id="752be-122">단일 데이터 집합에 대한 관계형 뷰와 계층적 뷰에 동기적으로 액세스할 수 있는 .NET Framework의 기능과 <xref:System.Data.DataSet> 및 <xref:System.Xml.XmlDataDocument> 간에 동기적 관계를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-122">Discusses the capability available in the .NET Framework of synchronous access to both relational and hierarchical views of a single set of data, and shows how to create a synchronous relationship between a <xref:System.Data.DataSet> and an <xref:System.Xml.XmlDataDocument>.</span></span>  
  
 [<span data-ttu-id="752be-123">DataRelation 중첩</span><span class="sxs-lookup"><span data-stu-id="752be-123">Nesting DataRelations</span></span>](nesting-datarelations.md)  
 <span data-ttu-id="752be-124"><xref:System.Data.DataRelation>의 내용을 XML 데이터로 표현할 경우 중첩된 <xref:System.Data.DataSet> 개체의 중요성과 이러한 개체를 만드는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-124">Discusses the importance of nested <xref:System.Data.DataRelation> objects when representing the contents of a <xref:System.Data.DataSet> as XML data, and describes how to create them.</span></span>  
  
 [<span data-ttu-id="752be-125">XML 스키마에서 데이터 세트 관계형 구조 파생(XSD)</span><span class="sxs-lookup"><span data-stu-id="752be-125">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="752be-126">XML 스키마에서 만들어진 <xref:System.Data.DataSet>의 관계 구조 또는 스키마에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-126">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema.</span></span>  
  
 [<span data-ttu-id="752be-127">XML에서 데이터 세트 관계형 구조 유추</span><span class="sxs-lookup"><span data-stu-id="752be-127">Inferring DataSet Relational Structure from XML</span></span>](inferring-dataset-relational-structure-from-xml.md)  
 <span data-ttu-id="752be-128">XML 요소에서 유추할 때 만들어지는 <xref:System.Data.DataSet>의 관계형 구조 또는 스키마에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-128">Describes the resulting relational structure, or schema, of a <xref:System.Data.DataSet> that is created when inferred from XML elements.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="752be-129">관련 섹션</span><span class="sxs-lookup"><span data-stu-id="752be-129">Related Sections</span></span>  

 [<span data-ttu-id="752be-130">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="752be-130">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="752be-131">ADO.NET 아키텍처 및 구성 요소에 대해 설명하고, 이를 사용하여 기존 데이터 소스에 액세스하고 애플리케이션 데이터를 관리하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="752be-131">Describes the ADO.NET architecture and components, and how to use them to access existing data sources as well as to manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="752be-132">참고 항목</span><span class="sxs-lookup"><span data-stu-id="752be-132">See also</span></span>

- [<span data-ttu-id="752be-133">DataSets, DataTables 및 DataViews</span><span class="sxs-lookup"><span data-stu-id="752be-133">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="752be-134">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="752be-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
