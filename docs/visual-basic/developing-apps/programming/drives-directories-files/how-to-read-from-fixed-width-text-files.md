---
description: '자세한 정보: 방법: Visual Basic에서 고정 너비 텍스트 파일 읽기'
title: '방법: 고정 너비 텍스트 파일 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 4f5868fa68009851cc65eeaf5ff6431ac22840d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797460"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="cbc27-103">방법: Visual Basic에서 고정 너비 텍스트 파일 읽기</span><span class="sxs-lookup"><span data-stu-id="cbc27-103">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="cbc27-104">`TextFieldParser` 개체는 로그와 같은 구조적 텍스트 파일을 쉽고 효율적으로 구문 분석하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-104">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="cbc27-105">`TextFieldType` 속성은 구문 분석된 파일이 구분된 파일인지 또는 고정 너비 텍스트 필드가 있는 파일인지를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-105">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="cbc27-106">고정 너비 텍스트 파일의 끝에 있는 필드는 가변 너비를 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-106">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="cbc27-107">끝에 있는 필드에 가변 너비를 지정하려면 0 이하의 너비로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-107">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="cbc27-108">고정 너비 텍스트 파일을 구문 분석하려면</span><span class="sxs-lookup"><span data-stu-id="cbc27-108">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="cbc27-109">새 `TextFieldParser`를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-109">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="cbc27-110">다음 코드는 `Reader`라는 `TextFieldParser`를 만들고 `test.log` 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-110">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="cbc27-111">너비와 형식을 정의하여 `TextFieldType` 속성을 `FixedWidth`로 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-111">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="cbc27-112">다음 코드는 텍스트 열을 정의합니다. 첫 번째 열은 너비가 5자이고, 두 번째 열은 10자, 세 번째 열은 11자, 네 번째 열은 가변 너비입니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-112">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="cbc27-113">파일의 필드를 반복합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-113">Loop through the fields in the file.</span></span> <span data-ttu-id="cbc27-114">손상된 줄이 있는 경우 오류를 보고하고 구문 분석을 계속합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-114">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="cbc27-115">`End While` 및 `End Using`을 사용하여 `While` 및 `Using` 블록을 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-115">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="cbc27-116">예제</span><span class="sxs-lookup"><span data-stu-id="cbc27-116">Example</span></span>  

 <span data-ttu-id="cbc27-117">이 예제에서는 `test.log` 파일에서 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-117">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cbc27-118">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="cbc27-118">Robust programming</span></span>  

 <span data-ttu-id="cbc27-119">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-119">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="cbc27-120">지정한 형식을 사용하여 행을 구문 분석할 수 없는 경우(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="cbc27-120">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="cbc27-121">예외 메시지에는 예외를 발생시키는 줄이 지정되어 있지만 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 속성은 해당 줄에 포함되어 있는 텍스트에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="cbc27-121">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="cbc27-122">지정한 파일이 없는 경우(<xref:System.IO.FileNotFoundException>)</span><span class="sxs-lookup"><span data-stu-id="cbc27-122">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="cbc27-123">사용자에게 파일에 액세스할 수 있는 권한이 없는 부분 신뢰 상황인 경우</span><span class="sxs-lookup"><span data-stu-id="cbc27-123">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="cbc27-124">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="cbc27-124">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="cbc27-125">경로가 너무 긴 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="cbc27-125">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="cbc27-126">사용자에게 파일에 액세스할 수 있는 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="cbc27-126">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbc27-127">참고 항목</span><span class="sxs-lookup"><span data-stu-id="cbc27-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="cbc27-128">방법: 쉼표로 구분된 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="cbc27-128">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="cbc27-129">방법: 여러 형식의 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="cbc27-129">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="cbc27-130">TextFieldParser 개체를 사용하여 텍스트 파일 구문 분석</span><span class="sxs-lookup"><span data-stu-id="cbc27-130">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="cbc27-131">연습: Visual Basic에서 파일과 디렉터리 조작</span><span class="sxs-lookup"><span data-stu-id="cbc27-131">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="cbc27-132">문제 해결: 텍스트 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="cbc27-132">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
