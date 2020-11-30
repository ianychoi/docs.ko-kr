---
title: msxsl:node-set() 함수에 대한 지원
ms.date: 03/30/2017
ms.assetid: d0cbf517-d9f6-4097-9851-4fa62903decd
ms.openlocfilehash: 6c84e3789916e8d842e51e8417cb27505cb5cba6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673399"
---
# <a name="support-for-the-msxslnode-set-function"></a><span data-ttu-id="5f2c0-102">msxsl:node-set() 함수에 대한 지원</span><span class="sxs-lookup"><span data-stu-id="5f2c0-102">Support for the msxsl:node-set() Function</span></span>

<span data-ttu-id="5f2c0-103">`msxsl:node-set` 함수를 사용하면 결과 트리 조각을 노드 집합으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-103">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="5f2c0-104">결과로 만들어지는 노드 집합은 트리의 루트 노드로서 항상 단일 노드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-104">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f2c0-105"><xref:System.Xml.Xsl.XslTransform> 클래스는 .NET Framework 2.0에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-105">The <xref:System.Xml.Xsl.XslTransform> class is obsolete in the .NET Framework 2.0.</span></span> <span data-ttu-id="5f2c0-106"><xref:System.Xml.Xsl.XslCompiledTransform> 클래스를 사용하여 XSLT(Extensible Stylesheet Language for Transformations) 변환을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-106">You can perform Extensible Stylesheet Language for Transformations (XSLT) transformations using the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="5f2c0-107">자세한 내용은 [XslCompiledTransform 클래스 사용](using-the-xslcompiledtransform-class.md) 및 [XslTransform 클래스에서 마이그레이션](migrating-from-the-xsltransform-class.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-107">See [Using the XslCompiledTransform Class](using-the-xslcompiledtransform-class.md) and [Migrating From the XslTransform Class](migrating-from-the-xsltransform-class.md) for more information.</span></span>  
  
 <span data-ttu-id="5f2c0-108">`msxsl:node-set` 함수를 사용하면 결과 트리 조각을 노드 집합으로 변환할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-108">The `msxsl:node-set` function enables you to convert a result tree fragment into a node set.</span></span> <span data-ttu-id="5f2c0-109">결과로 만들어지는 노드 집합은 트리의 루트 노드로서 항상 단일 노드를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-109">The resulting node set always contains a single node and is the root node of the tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f2c0-110">예제</span><span class="sxs-lookup"><span data-stu-id="5f2c0-110">Example</span></span>  

 <span data-ttu-id="5f2c0-111">다음 예제에서 `$books`는 스타일시트의 노드 트리인 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-111">In the following example, `$books` is a variable that is a node tree in the style sheet.</span></span> <span data-ttu-id="5f2c0-112">for-each 문과 `node-set` 함수를 함께 사용하면 이 노드 트리를 노드 집합으로 반복할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="5f2c0-112">The for-each statement combined with the `node-set` function allows the user to iterate over this node tree as a node set.</span></span>  
  
## <a name="nodesetxsl"></a><span data-ttu-id="5f2c0-113">nodeset.xsl</span><span class="sxs-lookup"><span data-stu-id="5f2c0-113">nodeset.xsl</span></span>  
  
```xml  
<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
                xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
                xmlns:user="http://www.contoso.com"  
                version="1.0">  
    <xsl:variable name="books">  
        <book author="Michael Howard">Writing Secure Code</book>  
        <book author="Michael Kay">XSLT Reference</book>  
    </xsl:variable>  
  
    <xsl:template match="/">  
        <authors>  
            <xsl:for-each select="msxsl:node-set($books)/book">
                <author><xsl:value-of select="@author"/></author>  
            </xsl:for-each>  
        </authors>  
    </xsl:template>  
</xsl:stylesheet>  
```  
  
## <a name="output"></a><span data-ttu-id="5f2c0-114">출력</span><span class="sxs-lookup"><span data-stu-id="5f2c0-114">Output</span></span>  

 <span data-ttu-id="5f2c0-115">변환 결과</span><span class="sxs-lookup"><span data-stu-id="5f2c0-115">The output of the transformation is</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<authors><author>Michael Howard</author><author>Michael Kay</author></authors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5f2c0-116">참조</span><span class="sxs-lookup"><span data-stu-id="5f2c0-116">See also</span></span>

- [<span data-ttu-id="5f2c0-117">XslTransform 클래스의 XSLT 프로세서 구현</span><span class="sxs-lookup"><span data-stu-id="5f2c0-117">XslTransform Class Implements the XSLT Processor</span></span>](xsltransform-class-implements-the-xslt-processor.md)
