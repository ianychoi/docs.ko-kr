---
title: XSLT 변환
ms.date: 03/30/2017
ms.assetid: 202f8820-224c-494f-b61e-cd127eac6e03
ms.openlocfilehash: b87768b402f92e0e59279aab0f0062e510fda2e6
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94818195"
---
# <a name="xslt-transformations"></a><span data-ttu-id="b9d6d-102">XSLT 변환</span><span class="sxs-lookup"><span data-stu-id="b9d6d-102">XSLT Transformations</span></span>
<span data-ttu-id="b9d6d-103">XSLT(Extensible Stylesheet Language Transformation)를 사용하면 소스 XML 문서의 내용을 형식이나 구조가 다른 문서로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-103">The Extensible Stylesheet Language Transformation (XSLT) lets you transform the content of a source XML document into another document that is different in format or structure.</span></span> <span data-ttu-id="b9d6d-104">예를 들어, XSLT를 사용하여 XML을 웹 사이트에서 사용할 HTML로 변형하거나 애플리케이션에서 필요한 필드만 포함하는 문서로 변형할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-104">For example, you can use XSLT to transform XML into HTML for use on a Web site or to transform it into a document that contains only the fields required by an application.</span></span> <span data-ttu-id="b9d6d-105">이 변환 프로세스는 [W3C XSLT(XSL 변환) 버전 1.0 권장 사항](https://www.w3.org/TR/xslt-10/)에 따라 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-105">This transformation process is specified by the [W3C XSL Transformations (XSLT) Version 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
 <span data-ttu-id="b9d6d-106"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 .NET의 XSLT 프로세서입니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-106">The <xref:System.Xml.Xsl.XslCompiledTransform> class is the XSLT processor in .NET.</span></span> <span data-ttu-id="b9d6d-107"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 [W3C XSLT 1.0 권장 사항](https://www.w3.org/TR/xslt-10/)을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-107">The <xref:System.Xml.Xsl.XslCompiledTransform> class supports the [W3C XSLT 1.0 recommendation](https://www.w3.org/TR/xslt-10/).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9d6d-108"><xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 버전 2.0에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-108">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in .NET Framework version 2.0.</span></span> <span data-ttu-id="b9d6d-109"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 XSLT 엔진의 새로운 구현으로서,</span><span class="sxs-lookup"><span data-stu-id="b9d6d-109">The <xref:System.Xml.Xsl.XslCompiledTransform> class is a new implementation of the XSLT engine.</span></span> <span data-ttu-id="b9d6d-110">성능 향상은 물론 새로운 보안 기능까지 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-110">It includes performance improvements and new security features.</span></span> <span data-ttu-id="b9d6d-111">XSLT 애플리케이션은 <xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 만드는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-111">The recommended practice is to create XSLT applications using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9d6d-112">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="b9d6d-112">In This Section</span></span>  
 [<span data-ttu-id="b9d6d-113">XslCompiledTransform 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="b9d6d-113">Using the XslCompiledTransform Class</span></span>](using-the-xslcompiledtransform-class.md)  
 <span data-ttu-id="b9d6d-114"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스 사용 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-114">Provides information on using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>  
  
 [<span data-ttu-id="b9d6d-115">XslTransform 클래스에서 마이그레이션</span><span class="sxs-lookup"><span data-stu-id="b9d6d-115">Migrating From the XslTransform Class</span></span>](migrating-from-the-xsltransform-class.md)  
 <span data-ttu-id="b9d6d-116"><xref:System.Xml.Xsl.XslTransform> 클래스에서 코드를 마이그레이션하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-116">Discusses how to migrate code from the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
 [<span data-ttu-id="b9d6d-117">XSLT 컴파일러(xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="b9d6d-117">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)  
 <span data-ttu-id="b9d6d-118">XSLT 컴파일러 사용 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-118">Provides information on using the XSLT compiler.</span></span>  
  
 [<span data-ttu-id="b9d6d-119">XslTransform 클래스를 사용하여 XSLT 변형</span><span class="sxs-lookup"><span data-stu-id="b9d6d-119">XSLT Transformations with the XslTransform Class</span></span>](xslt-transformations-with-the-xsltransform-class.md)  
 <span data-ttu-id="b9d6d-120"><xref:System.Xml.Xsl.XslTransform> 클래스 사용 방법에 대한 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b9d6d-120">Provides information on using the <xref:System.Xml.Xsl.XslTransform> class.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b9d6d-121">참고</span><span class="sxs-lookup"><span data-stu-id="b9d6d-121">Reference</span></span>  
 <xref:System.Xml.Xsl.XslCompiledTransform>  
 <xref:System.Xml.Xsl.XsltArgumentList>  
 <xref:System.Xml.Xsl.XsltSettings>  
  
## <a name="related-sections"></a><span data-ttu-id="b9d6d-122">관련 단원</span><span class="sxs-lookup"><span data-stu-id="b9d6d-122">Related Sections</span></span>  
 [<span data-ttu-id="b9d6d-123">XML 문서 및 데이터</span><span class="sxs-lookup"><span data-stu-id="b9d6d-123">XML Documents and Data</span></span>](index.md)
