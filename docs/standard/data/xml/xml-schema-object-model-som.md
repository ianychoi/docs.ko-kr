---
title: XML SOM(스키마 개체 모델)
ms.date: 03/30/2017
ms.assetid: a897a599-ffd1-43f9-8807-e58c8a7194cd
ms.openlocfilehash: b2af024f9821401b1380347580cc0dc5aeb21c3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733024"
---
# <a name="xml-schema-object-model-som"></a><span data-ttu-id="efaf3-102">XML SOM(스키마 개체 모델)</span><span class="sxs-lookup"><span data-stu-id="efaf3-102">XML Schema Object Model (SOM)</span></span>

<span data-ttu-id="efaf3-103">XML 스키마는 표준 XML 문서의 구조를 만들고 유효성을 검사할 수 있는 강력한 복합 도구입니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-103">An XML schema is a powerful and complex tool for creating and validating structure in compliant XML documents.</span></span> <span data-ttu-id="efaf3-104">관계형 데이터베이스의 데이터 모델링과 마찬가지로 스키마는 문서에 사용할 수 있는 요소와 특정 스키마에서 유효한 해당 요소의 구조 및 형식을 지정함으로써 XML 문서의 구조를 정의하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-104">Similar to data modeling in a relational database, a schema provides a way to define the structure of XML documents, by specifying the elements that can be used in the documents, as well as the structure and types that these elements must follow in order to be valid for that specific schema.</span></span>  
  
 <span data-ttu-id="efaf3-105">SOM(스키마 개체 모델)에서는 파일로부터 스키마를 읽거나 프로그래밍 방식으로 메모리 내 스키마를 만들 수 있도록 <xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스에 클래스 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-105">The Schema Object Model (SOM) provides a set of classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace that allow you to read a schema from a file or to programmatically create a schema in-memory.</span></span> <span data-ttu-id="efaf3-106">그런 다음 이 스키마를 통과, 편집, 컴파일하고 유효성을 검사하거나 파일에 쓸 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-106">The schema can then be traversed, editing, compiled, validated, or written to a file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="efaf3-107">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="efaf3-107">In This Section</span></span>  

 [<span data-ttu-id="efaf3-108">XML 스키마 개체 모델 개요</span><span class="sxs-lookup"><span data-stu-id="efaf3-108">XML Schema Object Model Overview</span></span>](xml-schema-object-model-overview.md)  
 <span data-ttu-id="efaf3-109">SOM(스키마 개체 모델) 및 SOM이 제공하는 기능과 클래스에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-109">Describes the Schema Object Model (SOM) and the features and classes it provides.</span></span>  
  
 [<span data-ttu-id="efaf3-110">XML 스키마 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="efaf3-110">Reading and Writing XML Schemas</span></span>](reading-and-writing-xml-schemas.md)  
 <span data-ttu-id="efaf3-111">파일 또는 기타 소스에서 XML 스키마를 읽고 쓰는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-111">Describes how to read and write XML schemas from files or other sources.</span></span>  
  
 [<span data-ttu-id="efaf3-112">XML 스키마 빌드</span><span class="sxs-lookup"><span data-stu-id="efaf3-112">Building XML Schemas</span></span>](building-xml-schemas.md)  
 <span data-ttu-id="efaf3-113"><xref:System.Xml.Schema?displayProperty=nameWithType> 네임스페이스에서 클래스를 사용하여 메모리 내 XML 스키마를 빌드하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-113">Describes how to use the classes in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace to build XML schemas in-memory.</span></span>  
  
 [<span data-ttu-id="efaf3-114">XML 스키마 통과</span><span class="sxs-lookup"><span data-stu-id="efaf3-114">Traversing XML Schemas</span></span>](traversing-xml-schemas.md)  
 <span data-ttu-id="efaf3-115">XML 스키마를 통과하여 SOM에 저장된 요소, 특성 및 형식에 액세스하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-115">Describes how to traverse an XML schema to access the elements, attributes, and types stored in the SOM.</span></span>  
  
 [<span data-ttu-id="efaf3-116">XML 스키마 편집</span><span class="sxs-lookup"><span data-stu-id="efaf3-116">Editing XML Schemas</span></span>](editing-xml-schemas.md)  
 <span data-ttu-id="efaf3-117">XML 스키마를 편집하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-117">Describes how to edit an XML schema.</span></span>  
  
 [<span data-ttu-id="efaf3-118">XML 스키마 포함하기 또는 가져오기</span><span class="sxs-lookup"><span data-stu-id="efaf3-118">Including or Importing XML Schemas</span></span>](including-or-importing-xml-schemas.md)  
 <span data-ttu-id="efaf3-119">다른 XML 스키마를 포함하거나 가져와서 이 스키마를 포함하거나 가져오는 스키마의 구조를 보완하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="efaf3-119">Describes how to include or import other XML schemas to supplement the structure of the schema that includes or imports them.</span></span>
