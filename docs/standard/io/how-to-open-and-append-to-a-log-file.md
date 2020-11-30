---
title: '방법: 열기 및 로그 파일에 추가'
description: .NET에서 스트림에 문자를 쓰고 스트림에서 문자를 읽는 StreamWriter 및 StreamReader 클래스를 사용하여 로그 파일을 열고 로그 파일에 추가합니다.
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: be4cacee8d0a529730c66c5850f42330520ba2d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734610"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="acc23-103">방법: 열기 및 로그 파일에 추가</span><span class="sxs-lookup"><span data-stu-id="acc23-103">How to: Open and append to a log file</span></span>

<span data-ttu-id="acc23-104"><xref:System.IO.StreamWriter> 및 <xref:System.IO.StreamReader>는 스트림에서 문자를 쓰고 문자를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="acc23-104"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="acc23-105">다음 코드 예제는 입력을 위해 *log.txt* 파일을 열거나, 파일이 존재하지 않는 경우 파일을 만들고 파일의 끝에 로그 정보를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="acc23-105">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="acc23-106">이 예제는 파일의 콘텐츠를 디스플레이의 표준 출력에 씁니다.</span><span class="sxs-lookup"><span data-stu-id="acc23-106">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="acc23-107">이 예제의 대안으로, 정보를 단일 문자열 또는 문자열 배열로 저장하고, <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> 또는 <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> 메서드를 사용하여 동일한 기능을 수행할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc23-107">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acc23-108">Visual Basic 사용자는 로그 파일을 생성하거나 로그 파일에 쓰기 위해 <xref:Microsoft.VisualBasic.Logging.Log> 클래스 또는 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 클래스에서 제공하는 메서드 및 속성을 사용하도록 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="acc23-108">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="acc23-109">예제</span><span class="sxs-lookup"><span data-stu-id="acc23-109">Example</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="acc23-110">참조</span><span class="sxs-lookup"><span data-stu-id="acc23-110">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="acc23-111">방법: 디렉터리 및 파일 열거</span><span class="sxs-lookup"><span data-stu-id="acc23-111">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="acc23-112">방법: 새로 만든 데이터 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="acc23-112">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="acc23-113">방법: 파일에서 텍스트 읽기</span><span class="sxs-lookup"><span data-stu-id="acc23-113">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="acc23-114">방법: 파일에 텍스트 쓰기</span><span class="sxs-lookup"><span data-stu-id="acc23-114">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="acc23-115">방법: 문자열에서 문자 읽기</span><span class="sxs-lookup"><span data-stu-id="acc23-115">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="acc23-116">방법: 문자열에 문자 쓰기</span><span class="sxs-lookup"><span data-stu-id="acc23-116">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="acc23-117">파일 및 스트림 I/O</span><span class="sxs-lookup"><span data-stu-id="acc23-117">File and stream I/O</span></span>](index.md)
