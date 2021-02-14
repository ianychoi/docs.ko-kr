---
description: '자세히 알아보기: 방법: 두 폴더의 내용 비교 (LINQ) (Visual Basic)'
title: '방법: 두 폴더의 콘텐츠 비교(LINQ)'
ms.date: 07/20/2015
ms.assetid: 903c7e9a-f48d-4a07-a8a8-5450d2646efa
ms.openlocfilehash: 8891617b7b95bf4543603ca40e7b85abb914da34
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424491"
---
# <a name="how-to-compare-the-contents-of-two-folders-linq-visual-basic"></a><span data-ttu-id="303b8-103">방법: 두 폴더의 내용 비교 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303b8-103">How to: Compare the Contents of Two Folders (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="303b8-104">이 예제에서는 두 파일 목록을 비교하는 세 가지 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-104">This example demonstrates three ways to compare two file listings:</span></span>

- <span data-ttu-id="303b8-105">두 파일 목록이 똑같은지 여부를 지정하는 부울 값 쿼리.</span><span class="sxs-lookup"><span data-stu-id="303b8-105">By querying for a Boolean value that specifies whether the two file lists are identical.</span></span>

- <span data-ttu-id="303b8-106">양쪽 폴더에 있는 파일을 검색하기 위해 교집합 쿼리.</span><span class="sxs-lookup"><span data-stu-id="303b8-106">By querying for the intersection to retrieve the files that are in both folders.</span></span>

- <span data-ttu-id="303b8-107">두 개 중 한 폴더에만 있는 파일을 검색하기 위해 차집합 쿼리.</span><span class="sxs-lookup"><span data-stu-id="303b8-107">By querying for the set difference to retrieve the files that are in one folder but not the other.</span></span>

    > [!NOTE]
    > <span data-ttu-id="303b8-108">여기 표시된 방법은 형식에 관계없이 개체의 시퀀스를 비교하도록 조정될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-108">The techniques shown here can be adapted to compare sequences of objects of any type.</span></span>

<span data-ttu-id="303b8-109">여기 표시된 `FileComparer` 클래스는 표준 쿼리 연산자와 함께 사용자 지정 비교자 클래스를 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-109">The `FileComparer` class shown here demonstrates how to use a custom comparer class together with the Standard Query Operators.</span></span> <span data-ttu-id="303b8-110">이 클래스는 실제 시나리오에서 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-110">The class is not intended for use in real-world scenarios.</span></span> <span data-ttu-id="303b8-111">단지 각 파일의 이름 및 길이(바이트)를 사용하여 각 폴더의 내용이 똑같은지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-111">It just uses the name and length in bytes of each file to determine whether the contents of each folder are identical or not.</span></span> <span data-ttu-id="303b8-112">실제 시나리오에서는 더 엄격한 일치 검사를 수행하도록 이 비교자를 수정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-112">In a real-world scenario, you should modify this comparer to perform a more rigorous equality check.</span></span>

## <a name="example"></a><span data-ttu-id="303b8-113">예제</span><span class="sxs-lookup"><span data-stu-id="303b8-113">Example</span></span>

```vb
Module CompareDirs
    Public Sub Main()

        ' Create two identical or different temporary folders
        ' on a local drive and add files to them.
        ' Then set these file paths accordingly.
        Dim pathA As String = "C:\TestDir"
        Dim pathB As String = "C:\TestDir2"

        ' Take a snapshot of the file system.
        Dim dir1 As New System.IO.DirectoryInfo(pathA)
        Dim dir2 As New System.IO.DirectoryInfo(pathB)

        Dim list1 = dir1.GetFiles("*.*", System.IO.SearchOption.AllDirectories)
        Dim list2 = dir2.GetFiles("*.*", System.IO.SearchOption.AllDirectories)

        ' Create the FileCompare object we'll use in each query
        Dim myFileCompare As New FileCompare

        ' This query determines whether the two folders contain
        ' identical file lists, based on the custom file comparer
        ' that is defined in the FileCompare class.
        ' The query executes immediately because it returns a bool.
        Dim areIdentical As Boolean = list1.SequenceEqual(list2, myFileCompare)
        If areIdentical = True Then
            Console.WriteLine("The two folders are the same.")
        Else
            Console.WriteLine("The two folders are not the same.")
        End If

        ' Find common files in both folders. It produces a sequence and doesn't execute
        ' until the foreach statement.
        Dim queryCommonFiles = list1.Intersect(list2, myFileCompare)

        If queryCommonFiles.Count() > 0 Then

            Console.WriteLine("The following files are in both folders:")
            For Each fi As System.IO.FileInfo In queryCommonFiles
                Console.WriteLine(fi.FullName)
            Next
        Else
            Console.WriteLine("There are no common files in the two folders.")
        End If

        ' Find the set difference between the two folders.
        ' For this example we only check one way.
        Dim queryDirAOnly = list1.Except(list2, myFileCompare)
        Console.WriteLine("The following files are in dirA but not dirB:")
        For Each fi As System.IO.FileInfo In queryDirAOnly
            Console.WriteLine(fi.FullName)
        Next

        ' Keep the console window open in debug mode
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub

    ' This implementation defines a very simple comparison
    ' between two FileInfo objects. It only compares the name
    ' of the files being compared and their length in bytes.
    Public Class FileCompare
        Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo)

        Public Function Equals1(ByVal x As System.IO.FileInfo, ByVal y As System.IO.FileInfo) _
            As Boolean Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).Equals

            If (x.Name = y.Name) And (x.Length = y.Length) Then
                Return True
            Else
                Return False
            End If
        End Function

        ' Return a hash that reflects the comparison criteria. According to the
        ' rules for IEqualityComparer(Of T), if Equals is true, then the hash codes must
        ' also be equal. Because equality as defined here is a simple value equality, not
        ' reference identity, it is possible that two or more objects will produce the same
        ' hash code.
        Public Function GetHashCode1(ByVal fi As System.IO.FileInfo) _
            As Integer Implements System.Collections.Generic.IEqualityComparer(Of System.IO.FileInfo).GetHashCode
            Dim s As String = fi.Name & fi.Length
            Return s.GetHashCode()
        End Function
    End Class
End Module
```

## <a name="compile-the-code"></a><span data-ttu-id="303b8-114">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="303b8-114">Compile the code</span></span>

<span data-ttu-id="303b8-115">System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="303b8-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="303b8-116">추가 정보</span><span class="sxs-lookup"><span data-stu-id="303b8-116">See also</span></span>

- [<span data-ttu-id="303b8-117">LINQ to Objects(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303b8-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="303b8-118">LINQ 및 파일 디렉터리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="303b8-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
