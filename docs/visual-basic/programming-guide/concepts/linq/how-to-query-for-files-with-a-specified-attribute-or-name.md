---
description: '자세히 알아보기: 방법: 지정 된 특성 또는 이름으로 파일 쿼리 (Visual Basic)'
title: '방법: 지정된 특성 또는 이름이 있는 파일 쿼리'
ms.date: 07/20/2015
ms.assetid: b26026a3-3f43-448f-a582-259997af6be0
ms.openlocfilehash: 3eb58bf683b97c5806145395cb489f0e85c2071b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425726"
---
# <a name="how-to-query-for-files-with-a-specified-attribute-or-name-visual-basic"></a><span data-ttu-id="89407-103">방법: 지정 된 특성 또는 이름으로 파일 쿼리 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89407-103">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>

<span data-ttu-id="89407-104">이 예제에서는 지정된 디렉터리 트리에서 지정된 파일 이름 확장명(예: ".txt")을 가진 파일을 모두 찾는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89407-104">This example shows how to find all files that have a specified file name extension (for example ".txt") in a specified directory tree.</span></span> <span data-ttu-id="89407-105">또한 생성 시간을 기준으로 트리에서 가장 최신 파일이나 가장 오래된 파일을 반환하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="89407-105">It also shows how to return either the newest or oldest file in the tree based on the creation time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89407-106">예제</span><span class="sxs-lookup"><span data-stu-id="89407-106">Example</span></span>  
  
```vb  
Module FindFileByExtension  
    Sub Main()  
  
        ' Change the drive\path if necessary  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0"  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(root)  
  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' This query will produce the full path for all .txt files  
        ' under the specified folder including subfolders.  
        ' It orders the list according to the file name.  
        Dim fileQuery = From file In fileList _  
                        Where file.Extension = ".txt" _  
                        Order By file.Name _  
                        Select file  
  
        For Each file In fileQuery  
            Console.WriteLine(file.FullName)  
        Next  
  
        ' Create and execute a new query by using  
        ' the previous query as a starting point.  
        ' fileQuery is not executed again until the  
        ' call to Last  
        Dim fileQuery2 = From file In fileQuery _  
                         Order By file.CreationTime _  
                         Select file.Name, file.CreationTime  
  
        ' Execute the query  
        Dim newestFile = fileQuery2.Last  
  
        Console.WriteLine("\r\nThe newest .txt file is {0}. Creation time: {1}", _  
                newestFile.Name, newestFile.CreationTime)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
  
    End Sub  
End Module  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="89407-107">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="89407-107">Compile the code</span></span>  

<span data-ttu-id="89407-108">System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="89407-108">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89407-109">참조</span><span class="sxs-lookup"><span data-stu-id="89407-109">See also</span></span>

- [<span data-ttu-id="89407-110">LINQ to Objects(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89407-110">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="89407-111">LINQ 및 파일 디렉터리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89407-111">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
