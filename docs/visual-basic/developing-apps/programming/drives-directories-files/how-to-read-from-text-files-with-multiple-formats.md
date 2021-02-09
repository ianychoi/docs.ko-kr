---
description: '자세한 정보: 방법: Visual Basic에서 여러 형식의 텍스트 파일 읽기'
title: '방법: 여러 형식의 텍스트 파일에서 읽기'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: 90d981ad051fb395d57604434cf9ba6b74603e7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797447"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="8be91-103">방법: Visual Basic에서 여러 형식의 텍스트 파일 읽기</span><span class="sxs-lookup"><span data-stu-id="8be91-103">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="8be91-104"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 개체는 로그와 같은 구조적 텍스트 파일을 쉽고 효율적으로 구문 분석하는 방법을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-104">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="8be91-105">파일을 구문 분석할 때 `PeekChars` 메서드를 사용하여 각 줄의 형식을 확인하면 여러 형식이 포함된 파일을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-105">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="8be91-106">여러 형식이 포함된 텍스트 파일을 구문 분석하려면</span><span class="sxs-lookup"><span data-stu-id="8be91-106">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="8be91-107">*testfile.txt* 라는 텍스트 파일을 프로젝트에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-107">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="8be91-108">텍스트 파일에 다음 콘텐츠를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-108">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="8be91-109">필요한 형식 및 오류가 보고되었을 때 사용한 형식을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-109">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="8be91-110">각 배열의 마지막 항목이 -1이므로, 마지막 필드는 가변 너비로 가정됩니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-110">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="8be91-111">이 오류는 배열의 마지막 항목이 0보다 작거나 같을 때 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-111">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="8be91-112">너비와 형식을 정의하는 새 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-112">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="8be91-113">행을 반복하고 읽기 전에 형식을 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-113">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="8be91-114">콘솔에 오류를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-114">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="8be91-115">예제</span><span class="sxs-lookup"><span data-stu-id="8be91-115">Example</span></span>

<span data-ttu-id="8be91-116">다음은 `testfile.txt` 파일에서 읽기를 수행하는 전체 예제입니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-116">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="8be91-117">강력한 프로그래밍</span><span class="sxs-lookup"><span data-stu-id="8be91-117">Robust programming</span></span>

<span data-ttu-id="8be91-118">다음 조건에서 예외가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8be91-119">지정한 형식을 사용하여 행을 구문 분석할 수 없는 경우(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="8be91-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="8be91-120">예외 메시지에는 예외를 발생시키는 줄이 지정되어 있지만 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 속성은 해당 줄에 포함되어 있는 텍스트에 할당됩니다.</span><span class="sxs-lookup"><span data-stu-id="8be91-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="8be91-121">지정한 파일이 없는 경우(<xref:System.IO.FileNotFoundException>)</span><span class="sxs-lookup"><span data-stu-id="8be91-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="8be91-122">사용자에게 파일에 액세스할 수 있는 권한이 없는 부분 신뢰 상황인 경우</span><span class="sxs-lookup"><span data-stu-id="8be91-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="8be91-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8be91-123">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="8be91-124">경로가 너무 긴 경우(<xref:System.IO.PathTooLongException>)</span><span class="sxs-lookup"><span data-stu-id="8be91-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="8be91-125">사용자에게 파일에 액세스할 수 있는 권한이 없는 경우(<xref:System.UnauthorizedAccessException>)</span><span class="sxs-lookup"><span data-stu-id="8be91-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="8be91-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="8be91-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="8be91-127">방법: 쉼표로 구분된 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="8be91-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="8be91-128">방법: 고정 너비 텍스트 파일에서 읽기</span><span class="sxs-lookup"><span data-stu-id="8be91-128">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="8be91-129">TextFieldParser 개체를 사용하여 텍스트 파일 구문 분석</span><span class="sxs-lookup"><span data-stu-id="8be91-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
