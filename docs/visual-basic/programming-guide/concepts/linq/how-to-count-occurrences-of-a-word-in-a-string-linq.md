---
description: '방법에 대 한 자세한 정보: 방법: 문자열에서 단어가 나오는 횟수 세기 (LINQ) (Visual Basic)'
title: '방법: 문자열에서 단어의 발생 횟수 계산(LINQ)'
ms.date: 07/20/2015
ms.assetid: bc367e46-f7cc-45f9-936f-754e661b7bb9
ms.openlocfilehash: dd00d1840f8f4eacdf949b0c1200b26f3692e00d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464809"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-visual-basic"></a><span data-ttu-id="7f121-103">방법: 문자열에서 단어가 나오는 횟수 세기 (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f121-103">How to: Count Occurrences of a Word in a String (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="7f121-104">이 예제에서는 LINQ 쿼리를 사용하여 문자열에서 지정된 단어의 발생 수를 계산하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-104">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="7f121-105">계산을 수행하려면 먼저 <xref:System.String.Split%2A> 메서드를 호출하여 단어 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-105">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="7f121-106"><xref:System.String.Split%2A> 메서드를 사용하는 경우 성능이 저하됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-106">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="7f121-107">문자열의 유일한 작업이 단어 개수 계산인 경우 <xref:System.Text.RegularExpressions.Regex.Matches%2A> 또는 <xref:System.String.IndexOf%2A> 메서드를 대신 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-107">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="7f121-108">그러나 성능이 중요한 문제가 아니거나 다른 유형의 쿼리를 수행하기 위해 이미 문장을 분할한 경우 LINQ를 사용하여 단어 또는 구도 계산하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-108">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>

## <a name="example"></a><span data-ttu-id="7f121-109">예제</span><span class="sxs-lookup"><span data-stu-id="7f121-109">Example</span></span>

```vb
Class CountWords

    Shared Sub Main()

        Dim text As String = "Historically, the world of data and the world of objects" &
                  " have not been well integrated. Programmers work in C# or Visual Basic" &
                  " and also in SQL or XQuery. On the one side are concepts such as classes," &
                  " objects, fields, inheritance, and .NET Framework APIs. On the other side" &
                  " are tables, columns, rows, nodes, and separate languages for dealing with" &
                  " them. Data types often require translation between the two worlds; there are" &
                  " different standard functions. Because the object world has no notion of query, a" &
                  " query can only be represented as a string without compile-time type checking or" &
                  " IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" &
                  " objects in memory is often tedious and error-prone."

        Dim searchTerm As String = "data"

        ' Convert the string into an array of words.
        Dim dataSource As String() = text.Split(New Char() {" ", ",", ".", ";", ":"},
                                                 StringSplitOptions.RemoveEmptyEntries)

        ' Create and execute the query. It executes immediately
        ' because a singleton value is produced.
        ' Use ToLower to match "data" and "Data"
        Dim matchQuery = From word In dataSource
                      Where word.ToLowerInvariant() = searchTerm.ToLowerInvariant()
                      Select word

        ' Count the matches.
        Dim count As Integer = matchQuery.Count()
        Console.WriteLine(count & " occurrence(s) of the search term """ &
                          searchTerm & """ were found.")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()
    End Sub
End Class
' Output:
' 3 occurrence(s) of the search term "data" were found.
```

## <a name="compile-the-code"></a><span data-ttu-id="7f121-110">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="7f121-110">Compile the code</span></span>

<span data-ttu-id="7f121-111">System.xml `Imports` 네임 스페이스에 대 한 문을 사용 하 여 Visual Basic 콘솔 응용 프로그램 프로젝트를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f121-111">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f121-112">추가 정보</span><span class="sxs-lookup"><span data-stu-id="7f121-112">See also</span></span>

- [<span data-ttu-id="7f121-113">LINQ 및 문자열(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f121-113">LINQ and Strings (Visual Basic)</span></span>](linq-and-strings.md)
