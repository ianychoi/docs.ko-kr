---
title: '방법: 파일에 텍스트 쓰기'
description: .NET 앱에서 텍스트를 쓰거나 파일에 추가하는 방법을 알아봅니다. StreamWriter 또는 File 클래스의 메서드를 사용하여 동기 또는 비동기적으로 텍스트를 씁니다.
ms.date: 01/04/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: bd9abc2aac4b02f71e41f71e518a76b2477420da
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829715"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="4f82d-104">방법: 파일에 텍스트 쓰기</span><span class="sxs-lookup"><span data-stu-id="4f82d-104">How to: Write text to a file</span></span>

<span data-ttu-id="4f82d-105">이 항목에서는 .NET 앱의 파일에 텍스트를 작성하는 다양한 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-105">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="4f82d-106">파일에 텍스트를 쓸 때는 일반적으로 다음 클래스 및 메서드가 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-106">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="4f82d-107"><xref:System.IO.StreamWriter>에는 동기식(<xref:System.IO.StreamWriter.Write%2A> 및 <xref:System.IO.TextWriter.WriteLine%2A>) 또는 비동기식(<xref:System.IO.StreamWriter.WriteAsync%2A> 및 <xref:System.IO.StreamWriter.WriteLineAsync%2A>)으로 파일에 쓰는 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-107"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="4f82d-108"><xref:System.IO.File>은 <xref:System.IO.File.WriteAllLines%2A> 및 <xref:System.IO.File.WriteAllText%2A>와 같은 파일에 텍스트를 쓰거나 <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A> 및 <xref:System.IO.File.AppendText%2A>와 같은 파일에 텍스트를 추가하는 정적 메서드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-108"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="4f82d-109"><xref:System.IO.Path>는 파일 또는 디렉터리 경로 정보가 포함된 문자열에 대한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-109"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="4f82d-110">파일이나 디렉터리 경로를 빌드하기 위해 문자열의 연결을 허용하는 <xref:System.IO.Path.Combine%2A> 메서드 및 .NET Core 2.1 이상에서는 <xref:System.IO.Path.Join%2A> 및 <xref:System.IO.Path.TryJoin%2A> 메서드가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-110">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="4f82d-111">다음 예제에서는 필요한 최소 코드 양만 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-111">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="4f82d-112">실제 앱은 일반적으로 더 강력한 오류 검사 및 예외 처리 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-112">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="4f82d-113">예: StreamWriter를 사용하여 텍스트를 동기식으로 쓰기</span><span class="sxs-lookup"><span data-stu-id="4f82d-113">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="4f82d-114">다음 예제에서는 <xref:System.IO.StreamWriter> 클래스를 사용하여 한 번에 한 줄씩 새 파일에 텍스트를 동기식으로 쓰는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-114">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="4f82d-115"><xref:System.IO.StreamWriter> 개체는 `using` 문에서 선언되고 인스턴스화되므로 스트림을 자동으로 플러시하고 닫는 <xref:System.IO.StreamWriter.Dispose%2A> 메서드가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-115">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="4f82d-116">예: StreamWriter를 사용하여 텍스트를 동기식으로 추가</span><span class="sxs-lookup"><span data-stu-id="4f82d-116">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="4f82d-117">다음 예제에서는 <xref:System.IO.StreamWriter> 클래스를 사용하여 첫 번째 예제에서 만든 텍스트 파일에 텍스트를 동기식으로 추가하는 방법을 보여줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-117">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="4f82d-118">예: StreamWriter를 사용하여 텍스트를 비동기식으로 쓰기</span><span class="sxs-lookup"><span data-stu-id="4f82d-118">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="4f82d-119">다음 예제에서는 <xref:System.IO.StreamWriter> 클래스를 사용하여 새 파일에 비동기적으로 텍스트를 쓰는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-119">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="4f82d-120"><xref:System.IO.StreamWriter.WriteAsync%2A> 메서드를 호출하려면 메서드 호출이 `async` 메서드 내에 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-120">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="4f82d-121">C# 예제에는 C# 7.1 이상이 필요하며, 이 경우 프로그램 진입점에서 `async` 한정자에 대한 지원이 추가됩니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-121">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="4f82d-122">예: 파일 클래스로 텍스트 쓰기 및 추가</span><span class="sxs-lookup"><span data-stu-id="4f82d-122">Example: Write and append text with the File class</span></span>

<span data-ttu-id="4f82d-123">다음 예제에서는 <xref:System.IO.File> 클래스를 사용하여 새 파일에 텍스트를 쓰고 동일한 파일에 새 텍스트 줄을 추가하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-123">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="4f82d-124"><xref:System.IO.File.WriteAllText%2A> 및 <xref:System.IO.File.AppendAllLines%2A> 메서드는 자동으로 파일을 열고 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-124">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="4f82d-125"><xref:System.IO.File.WriteAllText%2A> 메서드에 제공한 경로가 이미 있는 경우 파일을 덮어씁니다.</span><span class="sxs-lookup"><span data-stu-id="4f82d-125">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="4f82d-126">참조</span><span class="sxs-lookup"><span data-stu-id="4f82d-126">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f82d-127">방법: 디렉터리 및 파일 열거</span><span class="sxs-lookup"><span data-stu-id="4f82d-127">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="4f82d-128">방법: 새로 만든 데이터 파일 읽기 및 쓰기</span><span class="sxs-lookup"><span data-stu-id="4f82d-128">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="4f82d-129">방법: 로그 파일 열기 및 추가</span><span class="sxs-lookup"><span data-stu-id="4f82d-129">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="4f82d-130">방법: 파일에서 텍스트 읽기</span><span class="sxs-lookup"><span data-stu-id="4f82d-130">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="4f82d-131">파일 및 스트림 I/O</span><span class="sxs-lookup"><span data-stu-id="4f82d-131">File and stream I/O</span></span>](index.md)
