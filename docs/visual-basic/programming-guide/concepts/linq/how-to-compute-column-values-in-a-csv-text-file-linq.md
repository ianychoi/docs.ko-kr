---
description: '자세한 정보: 방법: CSV 텍스트 파일의 열 값 계산 (LINQ) (Visual Basic)'
title: '방법: CSV 텍스트 파일에서 열 값 컴퓨팅(LINQ)'
ms.date: 07/20/2015
ms.assetid: 88b2b9f3-c82e-41f3-b1b4-26ede5973a02
ms.openlocfilehash: f2bed49cf69d812659aae0cee398a735b3b42dbe
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100484186"
---
# <a name="how-to-compute-column-values-in-a-csv-text-file-linq-visual-basic"></a><span data-ttu-id="7a343-103">방법: CSV 텍스트 파일의 열 값 계산 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a343-103">How to: Compute Column Values in a CSV Text File (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7a343-104">이 예제에서는 .csv 파일의 열에 대해 Sum, Average, Min 및 Max 등의 집계 계산을 수행하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-104">This example shows how to perform aggregate computations such as Sum, Average, Min, and Max on the columns of a .csv file.</span></span> <span data-ttu-id="7a343-105">여기 표시된 예제 원칙은 다른 형식의 구조화된 텍스트에 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-105">The example principles that are shown here can be applied to other types of structured text.</span></span>

### <a name="to-create-the-source-file"></a><span data-ttu-id="7a343-106">소스 파일을 만들려면</span><span class="sxs-lookup"><span data-stu-id="7a343-106">To create the source file</span></span>

1. <span data-ttu-id="7a343-107">다음 줄을 scores.csv 파일에 복사하고 파일을 프로젝트 폴더에 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-107">Copy the following lines into a file that is named scores.csv and save it in your project folder.</span></span> <span data-ttu-id="7a343-108">첫 번째 열은 학생 ID를 나타내고 후속 열은 4개 시험의 점수를 나타낸다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-108">Assume that the first column represents a student ID, and subsequent columns represent scores from four exams.</span></span>

    ```csv
    111, 97, 92, 81, 60
    112, 75, 84, 91, 39
    113, 88, 94, 65, 91
    114, 97, 89, 85, 82
    115, 35, 72, 91, 70
    116, 99, 86, 90, 94
    117, 93, 92, 80, 87
    118, 92, 90, 83, 78
    119, 68, 79, 88, 92
    120, 99, 82, 81, 79
    121, 96, 85, 91, 60
    122, 94, 92, 91, 91
    ```

## <a name="example"></a><span data-ttu-id="7a343-109">예제</span><span class="sxs-lookup"><span data-stu-id="7a343-109">Example</span></span>

```vb
Class SumColumns

    Public Shared Sub Main()

        Dim lines As String() = System.IO.File.ReadAllLines("../../../scores.csv")

        ' Specifies the column to compute
        ' This value could be passed in at runtime.
        Dim exam = 3

        ' Spreadsheet format:
        ' Student ID    Exam#1  Exam#2  Exam#3  Exam#4
        ' 111,          97,     92,     81,     60
        ' one is added to skip over the first column
        ' which holds the student ID.
        SumColumn(lines, exam + 1)
        Console.WriteLine()
        MultiColumns(lines)

        ' Keep the console window open in debug mode.
        Console.WriteLine("Press any key to exit...")
        Console.ReadKey()

    End Sub

    Shared Sub SumColumn(ByVal lines As IEnumerable(Of String), ByVal col As Integer)

        ' This query performs two steps:
        ' split the string into a string array
        ' convert the specified element to
        ' integer and select it.
        Dim columnQuery = From line In lines
                           Let x = line.Split(",")
                           Select Convert.ToInt32(x(col))

        ' Execute and cache the results for performance.
        ' Only needed with very large files.
        Dim results = columnQuery.ToList()

        ' Perform aggregate calculations
        ' on the column specified by col.
        Dim avgScore = Aggregate score In results Into Average(score)
        Dim minScore = Aggregate score In results Into Min(score)
        Dim maxScore = Aggregate score In results Into Max(score)

        Console.WriteLine("Single Column Query:")
        Console.WriteLine("Exam #{0}: Average:{1:##.##} High Score:{2} Low Score:{3}",
                     col, avgScore, maxScore, minScore)

    End Sub

    Shared Sub MultiColumns(ByVal lines As IEnumerable(Of String))

        Console.WriteLine("Multi Column Query:")

        ' Create the query. It will produce nested sequences.
        ' multiColQuery performs these steps:
        ' 1) convert the string to a string array
        ' 2) skip over the "Student ID" column and take the rest
        ' 3) convert each field to an int and select that
        '    entire sequence as one row in the results.
        Dim multiColQuery = From line In lines
                            Let fields = line.Split(",")
                            Select From str In fields Skip 1
                                        Select Convert.ToInt32(str)

        Dim results = multiColQuery.ToList()

        ' Find out how many columns we have.
        Dim columnCount = results(0).Count()

        ' Perform aggregate calculations on each column.
        ' One loop for each score column in scores.
        ' We can use a for loop because we have already
        ' executed the multiColQuery in the call to ToList.

        For j As Integer = 0 To columnCount - 1
            Dim column = j
            Dim res2 = From row In results
                       Select row.ElementAt(column)

            ' Perform aggregate calculations
            ' on the column specified by col.
            Dim avgScore = Aggregate score In res2 Into Average(score)
            Dim minScore = Aggregate score In res2 Into Min(score)
            Dim maxScore = Aggregate score In res2 Into Max(score)

            ' Add 1 to column numbers because exams in this course start with #1
            Console.WriteLine("Exam #{0} Average: {1:##.##} High Score: {2} Low Score: {3}",
                              column + 1, avgScore, maxScore, minScore)

        Next
    End Sub

End Class
' Output:
' Single Column Query:
' Exam #4: Average:76.92 High Score:94 Low Score:39

' Multi Column Query:
' Exam #1 Average: 86.08 High Score: 99 Low Score: 35
' Exam #2 Average: 86.42 High Score: 94 Low Score: 72
' Exam #3 Average: 84.75 High Score: 91 Low Score: 65
' Exam #4 Average: 76.92 High Score: 94 Low Score: 39
```

<span data-ttu-id="7a343-110">쿼리는 <xref:System.String.Split%2A> 메서드를 사용하여 텍스트의 각 줄을 배열로 변환하는 방식으로 작동합니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-110">The query works by using the <xref:System.String.Split%2A> method to convert each line of text into an array.</span></span> <span data-ttu-id="7a343-111">각 배열 요소는 열을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-111">Each array element represents a column.</span></span> <span data-ttu-id="7a343-112">마지막으로 각 열의 텍스트가 숫자 표현으로 변환됩니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-112">Finally, the text in each column is converted to its numeric representation.</span></span> <span data-ttu-id="7a343-113">탭으로 구분된 파일인 경우 `Split` 메서드의 인수를 `\t`로 업데이트하세요.</span><span class="sxs-lookup"><span data-stu-id="7a343-113">If your file is a tab-separated file, just update the argument in the `Split` method to `\t`.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="7a343-114">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="7a343-114">Compile the code</span></span>

<span data-ttu-id="7a343-115">System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7a343-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="7a343-116">참조</span><span class="sxs-lookup"><span data-stu-id="7a343-116">See also</span></span>

- [<span data-ttu-id="7a343-117">LINQ 및 문자열(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a343-117">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
- [<span data-ttu-id="7a343-118">LINQ 및 파일 디렉터리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a343-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
