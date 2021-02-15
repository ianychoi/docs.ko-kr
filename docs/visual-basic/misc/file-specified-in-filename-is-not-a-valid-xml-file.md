---
description: '자세히 알아보기: 파일 이름에 지정 된 파일이 올바른 XML 파일이 아닙니다.'
title: FileName에 지정된 파일은 유효한 XML 파일이 아닙니다.
ms.date: 07/20/2015
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
ms.openlocfilehash: c7d521986f3489345117a3947ed1e9b459af897e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472984"
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="9b218-103">FileName에 지정된 파일은 유효한 XML 파일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-103">File specified in FileName is not a valid XML file</span></span>

<span data-ttu-id="9b218-104">제공한 파일 이름이 유효한 XML 파일이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-104">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="9b218-105">XML 문서의 허용된 구조와 내용을 지정하려면 DTD(문서 종류 정의), Microsoft XDR(XML-Data Reduced) 스키마 또는 XSD(XML 스키마 정의 언어) 스키마를 사용하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-105">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="9b218-106">XSD 스키마는 .NET Framework에서 XML 문법을 지정 하는 기본 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-106">XSD schemas are the preferred way to specify XML grammars in the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="9b218-107">일부 이전 버전의 Visual Studio에서 **XML 디자이너** 는 입력된 데이터 세트 및 XML 스키마용 디자이너입니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-107">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="9b218-108">**XML 디자이너** 는 XML 스키마 파일을 만들고 편집하는 데 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-108">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="9b218-109">그러나 Visual Studio 2012에서 형식화 된 데이터 집합을 만들고 편집 하는 디자이너는 **데이터 세트 디자이너** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-109">However, in Visual Studio 2012, the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="9b218-110">자세한 내용은 [형식화 된 데이터 집합 만들기 및 편집](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120))을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9b218-110">For more information, see [Creating and Editing Typed Datasets](/previous-versions/visualstudio/visual-studio-2013/314t4see(v=vs.120)).</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="9b218-111">이 오류를 해결하려면</span><span class="sxs-lookup"><span data-stu-id="9b218-111">To correct this error</span></span>

- <span data-ttu-id="9b218-112">올바른 파일 이름을 제공했는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-112">Check that you are supplying the correct file name.</span></span>

- <span data-ttu-id="9b218-113">확인하려는 XML 파일을 **XML 디자이너** 로 로드하여 지정된 파일에 유효한 XML 파일이 포함되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-113">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="9b218-114">**XML** 메뉴에서 **XML 유효성 검사** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-114">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="9b218-115">**작업 목록** 에 오류가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-115">Errors are displayed in the **Task List**.</span></span>

- <span data-ttu-id="9b218-116">XML 파일에 연결된 XML 스키마가 있는 경우 요소가 정의된 구조에 표시되고 개별 요소의 콘텐츠가 스키마에서 지정된 선언된 데이터 형식에 맞는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="9b218-116">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b218-117">추가 정보</span><span class="sxs-lookup"><span data-stu-id="9b218-117">See also</span></span>

- <xref:System.Xml>
- [<span data-ttu-id="9b218-118">방법: 파일 경로 구문 분석</span><span class="sxs-lookup"><span data-stu-id="9b218-118">How to: Parse File Paths</span></span>](../developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
