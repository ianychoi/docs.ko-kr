---
description: '자세한 정보: 방법: Visual Basic에서 쉼표로 구분된 텍스트 파일 읽기'
title: '방법: 쉼표로 구분된 텍스트 파일 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: dc4d4d5a7639ab7b5aa342aa8646b02985e40797
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797486"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="bb16d-103">방법: Visual Basic에서 쉼표로 구분된 텍스트 파일 읽기</span><span class="sxs-lookup"><span data-stu-id="bb16d-103">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="bb16d-104">`TextFieldParser` 개체는 로그와 같은 구조적 텍스트 파일을 쉽고 효율적으로 구문 분석하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-104">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="bb16d-105">`TextFieldType` 속성은 구분된 파일인지 또는 고정 너비 텍스트 필드가 있는 파일인지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-105">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="bb16d-106">쉼표로 구분된 텍스트 파일을 구문 분석하려면</span><span class="sxs-lookup"><span data-stu-id="bb16d-106">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="bb16d-107">새 `TextFieldParser`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-107">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="bb16d-108">다음 코드는 `MyReader`라는 `TextFieldParser`를 만들고 `test.txt` 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-108">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="bb16d-109">`TextField` 형식과 구분 기호를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-109">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="bb16d-110">다음 코드는 `TextFieldType` 속성을 `Delimited`로, 구분 기호를 ","로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-110">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="bb16d-111">파일의 필드를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-111">Loop through the fields in the file.</span></span> <span data-ttu-id="bb16d-112">손상된 줄이 있는 경우 오류를 보고하고 구문 분석을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-112">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="bb16d-113">다음 코드는 파일을 반복하면서 각 필드를 차례로 표시하고 형식이 잘못된 필드를 모두 보고합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-113">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="bb16d-114">`End While` 및 `End Using`을 사용하여 `While` 및 `Using` 블록을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="bb16d-115">예제</span><span class="sxs-lookup"><span data-stu-id="bb16d-115">Example</span></span>  

 <span data-ttu-id="bb16d-116">이 예제에서는 `test.txt` 파일에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-116">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="bb16d-117">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="bb16d-117">Robust programming</span></span>  

 <span data-ttu-id="bb16d-118">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="bb16d-119">지정한 형식을 사용하여 행을 구문 분석할 수 없는 경우(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="bb16d-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="bb16d-120">예외 메시지에는 예외를 발생시키는 줄이 지정되어 있지만 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 속성은 해당 줄에 포함되어 있는 텍스트에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="bb16d-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="bb16d-121">지정한 파일이 없는 경우(<xref:System.IO.FileNotFoundException>)</span><span class="sxs-lookup"><span data-stu-id="bb16d-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="bb16d-122">사용자에게 파일에 액세스할 수 있는 권한이 없는 부분 신뢰 상황인 경우</span><span class="sxs-lookup"><span data-stu-id="bb16d-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="bb16d-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="bb16d-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="bb16d-124">경로가 너무 긴 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="bb16d-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="bb16d-125">사용자에게 파일에 액세스할 수 있는 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="bb16d-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb16d-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb16d-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="bb16d-127">방법: 고정 너비 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="bb16d-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="bb16d-128">방법: 여러 형식의 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="bb16d-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="bb16d-129">TextFieldParser 개체를 사용하여 텍스트 파일 구문 분석</span><span class="sxs-lookup"><span data-stu-id="bb16d-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="bb16d-130">연습: Visual Basic에서 파일과 디렉터리 조작</span><span class="sxs-lookup"><span data-stu-id="bb16d-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="bb16d-131">문제 해결: 텍스트 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="bb16d-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
