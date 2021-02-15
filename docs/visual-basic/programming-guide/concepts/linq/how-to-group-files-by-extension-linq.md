---
description: '자세한 정보: 방법: 확장명에 따라 파일 그룹화 (LINQ) (Visual Basic)'
title: '방법: 확장명에 따라 파일 그룹화(LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 6736b4ff99d88f8e5b2b40aeb670d88589db02b1
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472997"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="bdaef-103">방법: 확장명에 따라 파일 그룹화 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdaef-103">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="bdaef-104">이 예제에서는 LINQ를 사용하여 파일 또는 폴더 목록에 대해 고급 그룹화 및 정렬 작업을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-104">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="bdaef-105">또한 <xref:System.Linq.Enumerable.Skip%2A> 및 <xref:System.Linq.Enumerable.Take%2A> 메서드를 사용하여 콘솔 창에서 출력을 페이징하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-105">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bdaef-106">예제</span><span class="sxs-lookup"><span data-stu-id="bdaef-106">Example</span></span>  

 <span data-ttu-id="bdaef-107">다음 쿼리는 지정된 디렉터리 트리의 내용을 파일 이름 확장명으로 그룹화하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-107">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="bdaef-108">이 프로그램의 출력은 로컬 파일 시스템의 세부 정보 및 `startFolder`의 설정에 따라 길어질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-108">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="bdaef-109">모든 결과를 볼 수 있도록, 이 예제에서는 결과를 페이징하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-109">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="bdaef-110">Windows 및 웹 애플리케이션에 동일한 기법을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-110">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="bdaef-111">코드에서 그룹의 항목을 페이징하기 때문에 중첩된 `For Each` 루프가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-111">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="bdaef-112">목록에서 현재 위치를 컴퓨팅하며 사용자가 페이징을 중지하고 프로그램을 종료할 수 있도록 하는 몇 가지 추가 논리도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-112">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="bdaef-113">이 특정 사례에서는 페이징 쿼리가 원래 쿼리에서 캐시된 결과에 대해 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-113">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="bdaef-114">LINQ to SQL 등의 다른 컨텍스트에서는 이러한 캐싱이 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-114">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="bdaef-115">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="bdaef-115">Compile the code</span></span>  

<span data-ttu-id="bdaef-116">System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="bdaef-116">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bdaef-117">추가 정보</span><span class="sxs-lookup"><span data-stu-id="bdaef-117">See also</span></span>

- [<span data-ttu-id="bdaef-118">LINQ to Objects(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdaef-118">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="bdaef-119">LINQ 및 파일 디렉터리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdaef-119">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
