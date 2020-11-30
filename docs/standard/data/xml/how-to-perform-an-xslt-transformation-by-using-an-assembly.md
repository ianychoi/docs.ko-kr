---
title: '방법: 어셈블리를 사용하여 XSLT 변형 수행'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 76ee440b-d134-4f8f-8262-b917ad6dcbf6
ms.openlocfilehash: 64ae2ecf4dac15170115e232fca0ddee272afd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722702"
---
# <a name="how-to-perform-an-xslt-transformation-by-using-an-assembly"></a><span data-ttu-id="45c2c-102">방법: 어셈블리를 사용하여 XSLT 변형 수행</span><span class="sxs-lookup"><span data-stu-id="45c2c-102">How to: Perform an XSLT Transformation by Using an Assembly</span></span>

<span data-ttu-id="45c2c-103">XSLT 컴파일러(xsltc.exe)에서는 XSLT 스타일시트를 컴파일하여 어셈블리를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-103">The XSLT compiler (xsltc.exe) compiles XSLT style sheets and generates an assembly.</span></span> <span data-ttu-id="45c2c-104">그런 다음 어셈블리를 <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> 메서드로 직접 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-104">The assembly can be passed directly into the <xref:System.Xml.Xsl.XslCompiledTransform.Load%28System.Type%29?displayProperty=nameWithType> method.</span></span>  
  
### <a name="to-copy-the-xml-and-xslt-files-to-your-local-computer"></a><span data-ttu-id="45c2c-105">XML 및 XSLT 파일을 로컬 컴퓨터에 복사하려면</span><span class="sxs-lookup"><span data-stu-id="45c2c-105">To copy the XML and XSLT files to your local computer</span></span>  
  
- <span data-ttu-id="45c2c-106">XSLT 파일을 로컬 컴퓨터에 복사하고 이름을 Transform.xsl로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-106">Copy the XSLT file to your local computer and name it Transform.xsl.</span></span>  
  
    ```xml  
    <xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
      xmlns:msxsl="urn:schemas-microsoft-com:xslt"  
      xmlns:user="urn:my-scripts">  
      <msxsl:script language="C#" implements-prefix="user">  
        <![CDATA[  
      public string discount(string price){  
        char[] trimChars = { '$' };  
        //trim leading $, convert price to type double  
        double discount_value = Convert.ToDouble(price.TrimStart(trimChars));  
        //apply 10% discount and round appropriately  
        discount_value = .9*discount_value;  
        //convert value to decimal and format as currency  
        string discount_price = discount_value.ToString("C");  
        return discount_price;  
      }  
      ]]>  
      </msxsl:script>  
      <xsl:template match="catalog">  
        <html>  
          <head></head>  
          <body>  
            <table border="1">  
              <tr>  
                <th align="left">Title</th>  
                <th align="left">Author</th>  
                <th align="left">Genre</th>  
                <th align="left">Publish Date</th>  
                <th align="left">Price</th>  
              </tr>  
              <xsl:for-each select="book">  
                <tr>  
                  <td>  
                    <xsl:value-of select="title"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="author"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="genre"/>  
                  </td>  
                  <td>  
                    <xsl:value-of select="publish_date"/>  
                  </td>  
                  <xsl:choose>  
                    <xsl:when test="genre = 'Fantasy'">  
                      <td>  
                        <xsl:value-of select="user:discount(price)"/>  
                      </td>  
                    </xsl:when>  
                    <xsl:otherwise>  
                      <td>  
                        <xsl:value-of select="price"/>  
                      </td>  
                    </xsl:otherwise>  
                  </xsl:choose>  
                </tr>  
              </xsl:for-each>  
            </table>  
          </body>  
        </html>  
      </xsl:template>  
    </xsl:stylesheet>  
    ```  
  
- <span data-ttu-id="45c2c-107">XML 파일을 로컬 컴퓨터에 복사하고 이름을 `books.xml`로 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-107">Copy the XML file to your local computer and name it `books.xml`.</span></span>  
  
    ```xml  
    <?xml version="1.0"?>  
    <catalog>  
       <book id="bk101">  
          <author>Gambardella, Matthew</author>  
          <title>XML Developer's Guide</title>  
          <genre>Computer</genre>  
          <price>$44.95</price>  
          <publish_date>2000-10-01</publish_date>  
       </book>  
       <book id="bk102">  
          <author>Ralls, Kim</author>  
          <title>Midnight Rain</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-12-16</publish_date>  
       </book>  
       <book id="bk103">  
          <author>Corets, Eva</author>  
          <title>Maeve Ascendant</title>  
          <genre>Fantasy</genre>  
          <price>$5.95</price>  
          <publish_date>2000-11-17</publish_date>  
       </book>  
       <book id="bk106">  
          <author>Randall, Cynthia</author>  
          <title>Lover Birds</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-09-02</publish_date>  
       </book>  
       <book id="bk107">  
          <author>Thurman, Paula</author>  
          <title>Splish Splash</title>  
          <genre>Romance</genre>  
          <price>$4.95</price>  
          <publish_date>2000-11-02</publish_date>  
       </book>  
    </catalog>  
    ```  
  
### <a name="to-compile-the-style-sheet-with-the-script-enabled"></a><span data-ttu-id="45c2c-108">스크립트가 활성화된 스타일시트를 컴파일하려면</span><span class="sxs-lookup"><span data-stu-id="45c2c-108">To compile the style sheet with the script enabled.</span></span>  
  
1. <span data-ttu-id="45c2c-109">명령줄에서 다음 명령을 실행하면 이름이 `Transform.dll` 및 `Transform_Script1.dll`인 두 개의 어셈블리가 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-109">Executing the following command from the command line creates two assemblies named `Transform.dll` and `Transform_Script1.dll` (This is the default behavior.</span></span> <span data-ttu-id="45c2c-110">이것이 기본 동작이며, 아무 것도 지정하지 않으면 클래스 및 어셈블리 이름은 기본 스타일시트 이름으로 지정됩니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-110">Unless otherwise specified, the name of the class and the assembly defaults to the name of the main style sheet):</span></span>  
  
    ```console  
    xsltc /settings:script+ Transform.xsl  
    ```
  
    <span data-ttu-id="45c2c-111">다음 명령에서는 명시적으로 클래스 이름을 Transform으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-111">The following command explicitly sets the class name to Transform:</span></span>  
  
    ```console  
    xsltc /settings:script+ /class:Transform Transform.xsl  
    ```  
  
### <a name="to-include-the-compiled-assembly-as-a-reference-when-you-compile-your-code"></a><span data-ttu-id="45c2c-112">코드를 컴파일할 때 컴파일된 어셈블리를 참조로 포함하려면</span><span class="sxs-lookup"><span data-stu-id="45c2c-112">To include the compiled assembly as a reference when you compile your code.</span></span>  
  
1. <span data-ttu-id="45c2c-113">Visual Studio의 솔루션 탐색기에서 참조를 추가하거나 명령줄을 사용하여 어셈블리를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-113">You can include an assembly in Visual Studio by adding a reference in the Solution Explorer, or from the command line.</span></span>  
  
2. <span data-ttu-id="45c2c-114">C#을 사용하는 명령줄의 경우 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-114">For the command line with C#, use the following:</span></span>  
  
    ```console  
    csc myCode.cs /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
3. <span data-ttu-id="45c2c-115">Visual Basic을 사용하는 명령줄의 경우 다음을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-115">For the command line with Visual Basic, use the following</span></span>  
  
    ```console  
    vbc myCode.vb /r:system.dll;system.xml.dll;Transform.dll  
    ```  
  
### <a name="to-use-the-compiled-assembly-in-your-code"></a><span data-ttu-id="45c2c-116">사용자 코드에서 컴파일된 어셈블리를 사용하려면</span><span class="sxs-lookup"><span data-stu-id="45c2c-116">To use the compiled assembly in your code.</span></span>  
  
<span data-ttu-id="45c2c-117">다음 예제에서는 컴파일된 스타일시트를 사용하여 XSLT 변환을 실행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-117">The following example shows how to execute the XSLT transformation by using the compiled style sheet.</span></span>  
  
[!code-csharp[XslTransform_XSLTC#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XslTransform_XSLTC/CS/XslTransform_XSLTC.cs#1)]
[!code-vb[XslTransform_XSLTC#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XslTransform_XSLTC/VB/XslTransform_XSLTC.vb#1)]  
  
<span data-ttu-id="45c2c-118">위 예제에서 컴파일된 어셈블리에 동적으로 연결하려면</span><span class="sxs-lookup"><span data-stu-id="45c2c-118">To dynamically link to the compiled assembly, replace</span></span>
  
```csharp  
xslt.Load(typeof(Transform));  
```  
  
<span data-ttu-id="45c2c-119">다음 문자열로 바꾸세요.</span><span class="sxs-lookup"><span data-stu-id="45c2c-119">with</span></span>  
  
```csharp
xslt.Load(System.Reflection.Assembly.Load("Transform").GetType("Transform"));  
```
  
<span data-ttu-id="45c2c-120">으로 대체합니다.</span><span class="sxs-lookup"><span data-stu-id="45c2c-120">in the example above.</span></span> <span data-ttu-id="45c2c-121">Assembly.Load 메서드에 대한 자세한 내용은 <xref:System.Reflection.Assembly.Load%2A>를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="45c2c-121">For more information on the Assembly.Load method, see <xref:System.Reflection.Assembly.Load%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c2c-122">참조</span><span class="sxs-lookup"><span data-stu-id="45c2c-122">See also</span></span>

- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="45c2c-123">XSLT 컴파일러(xsltc.exe)</span><span class="sxs-lookup"><span data-stu-id="45c2c-123">XSLT Compiler (xsltc.exe)</span></span>](xslt-compiler-xsltc-exe.md)
- [<span data-ttu-id="45c2c-124">XSLT 변환</span><span class="sxs-lookup"><span data-stu-id="45c2c-124">XSLT Transformations</span></span>](xslt-transformations.md)
- [<span data-ttu-id="45c2c-125">csc.exe를 사용한 명령줄 빌드</span><span class="sxs-lookup"><span data-stu-id="45c2c-125">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
