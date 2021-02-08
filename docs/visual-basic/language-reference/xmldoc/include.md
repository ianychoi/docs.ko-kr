---
description: 다음에 대해 자세히 알아보세요. <include> (Visual Basic)
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 8207b74ed74bd529f2da865777e287320b23d293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787463"
---
# <a name="include-visual-basic"></a><span data-ttu-id="7391d-103">\<include>(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7391d-103">\<include> (Visual Basic)</span></span>

<span data-ttu-id="7391d-104">소스 코드의 형식 및 멤버를 설명 하는 다른 파일을 참조 합니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-104">Refers to another file that describes the types and members in your source code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7391d-105">구문</span><span class="sxs-lookup"><span data-stu-id="7391d-105">Syntax</span></span>  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a><span data-ttu-id="7391d-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="7391d-106">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="7391d-107">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-107">Required.</span></span> <span data-ttu-id="7391d-108">문서가 포함된 파일의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-108">The name of the file containing the documentation.</span></span> <span data-ttu-id="7391d-109">경로를 사용하여 파일 이름을 정규화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-109">The file name can be qualified with a path.</span></span> <span data-ttu-id="7391d-110">큰따옴표 `filename` ("")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-110">Enclose `filename` in double quotation marks (" ").</span></span>  
  
 `tagpath`  
 <span data-ttu-id="7391d-111">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-111">Required.</span></span> <span data-ttu-id="7391d-112">`filename`의 태그 경로로, `name` 태그에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-112">The path of the tags in `filename` that leads to the tag `name`.</span></span> <span data-ttu-id="7391d-113">경로를 큰따옴표 ("")로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-113">Enclose the path in double quotation marks (" ").</span></span>  
  
 `name`  
 <span data-ttu-id="7391d-114">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-114">Required.</span></span> <span data-ttu-id="7391d-115">주석 앞에 오는 태그의 이름 지정자입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-115">The name specifier in the tag that precedes the comments.</span></span> <span data-ttu-id="7391d-116">`Name` 에는가 `id` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-116">`Name` will have an `id`.</span></span>  
  
 `id`  
 <span data-ttu-id="7391d-117">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-117">Required.</span></span> <span data-ttu-id="7391d-118">주석 앞에 오는 태그의 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-118">The ID for the tag that precedes the comments.</span></span> <span data-ttu-id="7391d-119">ID를 작은따옴표 (' ')로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-119">Enclose the ID in single quotation marks (' ').</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7391d-120">설명</span><span class="sxs-lookup"><span data-stu-id="7391d-120">Remarks</span></span>  

 <span data-ttu-id="7391d-121">태그를 사용 `<include>` 하 여 소스 코드의 형식 및 멤버를 설명 하는 다른 파일의 주석을 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-121">Use the `<include>` tag to refer to comments in another file that describe the types and members in your source code.</span></span> <span data-ttu-id="7391d-122">소스 코드 파일에 직접 문서 주석을 포함하는 대신 사용되는 대안입니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-122">This is an alternative to placing documentation comments directly in your source code file.</span></span>  
  
 <span data-ttu-id="7391d-123">`<include>`태그는 W3C XPath (XML Path Language) 버전 1.0 권장 사항을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7391d-123">The `<include>` tag uses the W3C XML Path Language (XPath) Version 1.0 Recommendation.</span></span> <span data-ttu-id="7391d-124">사용을 사용자 지정 하는 방법에 대 한 자세한 내용은 `<include>` 을 참조 하십시오 <https://www.w3.org/TR/xpath> .</span><span class="sxs-lookup"><span data-stu-id="7391d-124">For more information about ways to customize your `<include>` use, see <https://www.w3.org/TR/xpath>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7391d-125">예제</span><span class="sxs-lookup"><span data-stu-id="7391d-125">Example</span></span>  

 <span data-ttu-id="7391d-126">이 예제에서는 태그를 사용 하 여 `<include>` 라는 파일에서 멤버 문서 주석을 가져옵니다 `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="7391d-126">This example uses the `<include>` tag to import member documentation comments from a file called `commentFile.xml`.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 <span data-ttu-id="7391d-127">의 형식은 다음과 같습니다 `commentFile.xml` .</span><span class="sxs-lookup"><span data-stu-id="7391d-127">The format of the `commentFile.xml` is as follows.</span></span>  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7391d-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7391d-128">See also</span></span>

- [<span data-ttu-id="7391d-129">XML 주석 태그</span><span class="sxs-lookup"><span data-stu-id="7391d-129">XML Comment Tags</span></span>](index.md)
