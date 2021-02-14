---
description: '자세한 정보: 파일 액세스에 Async 사용 (Visual Basic)'
title: 파일 액세스에 Async 사용
ms.date: 07/20/2015
ms.assetid: c989305f-08e3-4687-95c3-948465cda202
ms.openlocfilehash: f065ef8d8672569921e1652e62d24c10a506f828
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100474215"
---
# <a name="using-async-for-file-access-visual-basic"></a><span data-ttu-id="9373e-103">파일 액세스에 Async 사용(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9373e-103">Using Async for File Access (Visual Basic)</span></span>

<span data-ttu-id="9373e-104">비동기 기능을 사용 하 여 파일에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-104">You can use the Async feature to access files.</span></span> <span data-ttu-id="9373e-105">비동기 기능을 사용하면 콜백을 사용하거나 여러 메서드 또는 람다 식에 코드를 분할하지 않고도 비동기 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-105">By using the Async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="9373e-106">동기 코드를 비동기로 만들려면 동기 메서드 대신 비동기 메서드를 호출하고 몇 가지 키워드를 코드에 추가하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-106">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="9373e-107">파일 액세스 호출에 비동기를 추가하는 이유로 다음을 고려할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-107">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="9373e-108">비동기는 UI 애플리케이션의 응답성을 개선합니다. 작업을 시작하는 UI 스레드가 다른 작업을 수행할 수 있기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-108">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="9373e-109">UI 스레드가 시간이 오래 걸리는(예: 50밀리초 이상) 코드를 실행해야 하는 경우, I/O가 완료되고 UI 스레드가 키보드와 마우스 입력 및 기타 이벤트를 다시 처리할 수 있을 때까지 UI가 정지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-109">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="9373e-110">비동기는 스레드의 필요성을 줄임으로써 ASP.NET 및 기타 서버 기반 애플리케이션의 확장성을 개선합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-110">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="9373e-111">애플리케이션이 각 응답에 전용 스레드를 사용하고 1,000개의 요청이 동시에 처리되는 경우 수천 개의 스레드가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-111">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="9373e-112">비동기 작업은 대기 중에 종종 스레드를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-112">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="9373e-113">끝날 때 기존 I/O 완료 스레드를 잠시 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-113">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="9373e-114">파일 액세스 작업의 대기 시간은 현재 조건에서 매우 낮을 수 있지만 나중에 대기 시간이 크게 늘어날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-114">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="9373e-115">예를 들어 전 세계에 있는 서버로 파일을 이동할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-115">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="9373e-116">비동기 기능을 사용할 경우에는 추가되는 오버헤드가 적습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-116">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="9373e-117">비동기 작업은 쉽게 병렬로 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-117">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="9373e-118">예제 실행</span><span class="sxs-lookup"><span data-stu-id="9373e-118">Running the Examples</span></span>  

 <span data-ttu-id="9373e-119">이 항목의 예제를 실행하려면 **WPF 애플리케이션** 또는 **Windows Forms 애플리케이션** 을 만든 후 **단추** 를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-119">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="9373e-120">단추의 `Click` 이벤트에서 각 예제의 첫 번째 메서드에 대한 호출을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-120">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="9373e-121">다음 예제에서는 `Imports` 문을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-121">In the following examples, include the following `Imports` statements.</span></span>  
  
```vb  
Imports System  
Imports System.Collections.Generic  
Imports System.Diagnostics  
Imports System.IO  
Imports System.Text  
Imports System.Threading.Tasks  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="9373e-122">FileStream 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="9373e-122">Use of the FileStream Class</span></span>  

 <span data-ttu-id="9373e-123">이 항목의 예제에서는 운영 체제 수준에서 비동기 I/O를 일으키는 옵션이 있는 <xref:System.IO.FileStream> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-123">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="9373e-124">이 옵션을 사용하면 많은 경우 ThreadPool 스레드를 차단하지 않아도 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-124">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="9373e-125">이 옵션을 사용하도록 설정하려면 생성자 호출에서 `useAsync=true` 또는 `options=FileOptions.Asynchronous` 인수를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-125">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="9373e-126">파일 경로를 지정하여 직접 여는 경우에는 <xref:System.IO.StreamReader> 및 <xref:System.IO.StreamWriter>와 함께 이 옵션을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-126">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="9373e-127">그러나 <xref:System.IO.FileStream> 클래스에서 열린 <xref:System.IO.Stream>을 제공하면 이 옵션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-127">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="9373e-128">대기 중에는 UI 스레드가 차단되지 않으므로, ThreadPool 스레드가 차단된 경우에도 UI 앱에서 비동기 호출이 더 빠릅니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-128">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="9373e-129">텍스트 쓰기</span><span class="sxs-lookup"><span data-stu-id="9373e-129">Writing Text</span></span>  

 <span data-ttu-id="9373e-130">다음 예제에서는 파일에 텍스트를 씁니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-130">The following example writes text to a file.</span></span> <span data-ttu-id="9373e-131">각 await 문에서 메서드가 즉시 종료됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-131">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="9373e-132">파일 I/O가 완료되면 await 문 뒤에 오는 문에서 메서드가 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-132">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="9373e-133">async 한정자는 await 문을 사용하는 메서드의 정의에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-133">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```vb  
Public Async Sub ProcessWrite()  
    Dim filePath = "temp2.txt"  
    Dim text = "Hello World" & ControlChars.CrLf  
  
    Await WriteTextAsync(filePath, text)  
End Sub  
  
Private Async Function WriteTextAsync(filePath As String, text As String) As Task  
    Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize:=4096, useAsync:=True)  
  
        Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
    End Using  
End Function  
```  
  
 <span data-ttu-id="9373e-134">원래 예제에 있는 `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)` 문은 다음의 두 문이 축약된 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-134">The original example has the statement `Await sourceStream.WriteAsync(encodedText, 0, encodedText.Length)`, which is a contraction of the following two statements:</span></span>  
  
```vb  
Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
Await theTask  
```  
  
 <span data-ttu-id="9373e-135">첫 번째 문은 작업을 반환하여 파일 처리가 시작되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-135">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="9373e-136">await가 있는 두 번째 문은 메서드를 즉시 종료하고 다른 작업을 반환하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-136">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="9373e-137">나중에 파일 처리가 완료되면 await 뒤에 오는 문으로 실행이 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-137">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="9373e-138">자세한 내용은  [비동기 프로그램의 제어 흐름 (Visual Basic)](control-flow-in-async-programs.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9373e-138">For more information, see  [Control Flow in Async Programs (Visual Basic)](control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="9373e-139">텍스트 읽기</span><span class="sxs-lookup"><span data-stu-id="9373e-139">Reading Text</span></span>  

 <span data-ttu-id="9373e-140">다음 예제에서는 파일에서 텍스트를 읽습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-140">The following example reads text from a file.</span></span> <span data-ttu-id="9373e-141">텍스트가 버퍼링되고, 이 경우 <xref:System.Text.StringBuilder>에 배치됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-141">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="9373e-142">이전 예제와 달리 await의 계산에서 값이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-142">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="9373e-143"><xref:System.IO.Stream.ReadAsync%2A> 메서드는 <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>를 반환하므로 작업이 완료된 후 await 평가에서 `Int32` 값(`numRead`)이 생성됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-143">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="9373e-144">자세한 내용은 [비동기 반환 형식 (Visual Basic)](async-return-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9373e-144">For more information, see [Async Return Types (Visual Basic)](async-return-types.md).</span></span>  
  
```vb  
Public Async Sub ProcessRead()  
    Dim filePath = "temp2.txt"  
  
    If File.Exists(filePath) = False Then  
        Debug.WriteLine("file not found: " & filePath)  
    Else  
        Try  
            Dim text As String = Await ReadTextAsync(filePath)  
            Debug.WriteLine(text)  
        Catch ex As Exception  
            Debug.WriteLine(ex.Message)  
        End Try  
    End If  
End Sub  
  
Private Async Function ReadTextAsync(filePath As String) As Task(Of String)  
  
    Using sourceStream As New FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize:=4096, useAsync:=True)  
  
        Dim sb As New StringBuilder  
  
        Dim buffer As Byte() = New Byte(&H1000) {}  
        Dim numRead As Integer  
        numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        While numRead <> 0  
            Dim text As String = Encoding.Unicode.GetString(buffer, 0, numRead)  
            sb.Append(text)  
  
            numRead = Await sourceStream.ReadAsync(buffer, 0, buffer.Length)  
        End While  
  
        Return sb.ToString  
    End Using  
End Function  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="9373e-145">병렬 비동기 I/O</span><span class="sxs-lookup"><span data-stu-id="9373e-145">Parallel Asynchronous I/O</span></span>  

 <span data-ttu-id="9373e-146">다음 예제에서는 10개의 텍스트 파일을 작성하여 병렬 처리를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-146">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="9373e-147">각 파일에서 <xref:System.IO.Stream.WriteAsync%2A> 메서드는 작업 목록에 추가되는 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-147">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="9373e-148">`Await Task.WhenAll(tasks)` 문은 메서드를 종료하고, 파일 처리가 모든 작업에 대해 완료되면 메서드 내에서 다시 시작됩니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-148">The `Await Task.WhenAll(tasks)` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="9373e-149">이 예제는 작업이 완료된 후 `Finally` 블록에서 모든 <xref:System.IO.FileStream> 인스턴스를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-149">The example closes all <xref:System.IO.FileStream> instances in a `Finally` block after the tasks are complete.</span></span> <span data-ttu-id="9373e-150">대신 `Imports` 문에 각 `FileStream`이 만들어진 경우 작업이 완료되기 전에 `FileStream`이 삭제될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-150">If each `FileStream` was instead created in a `Imports` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="9373e-151">성능 향상은 거의 대부분 비동기 처리가 아닌 병렬 처리에서 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-151">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="9373e-152">비동기의 장점은 다중 스레드를 묶어 두지 않고 사용자 인터페이스 스레드를 묶어 두지 않는다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-152">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```vb  
Public Async Sub ProcessWriteMult()  
    Dim folder = "tempfolder\"  
    Dim tasks As New List(Of Task)  
    Dim sourceStreams As New List(Of FileStream)  
  
    Try  
        For index = 1 To 10  
            Dim text = "In file " & index.ToString & ControlChars.CrLf  
  
            Dim fileName = "thefile" & index.ToString("00") & ".txt"  
            Dim filePath = folder & fileName  
  
            Dim encodedText As Byte() = Encoding.Unicode.GetBytes(text)  
  
            Dim sourceStream As New FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize:=4096, useAsync:=True)  
  
            Dim theTask As Task = sourceStream.WriteAsync(encodedText, 0, encodedText.Length)  
            sourceStreams.Add(sourceStream)  
  
            tasks.Add(theTask)  
        Next  
  
        Await Task.WhenAll(tasks)  
    Finally  
        For Each sourceStream As FileStream In sourceStreams  
            sourceStream.Close()  
        Next  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="9373e-153"><xref:System.IO.Stream.WriteAsync%2A> 및 <xref:System.IO.Stream.ReadAsync%2A> 메서드를 사용하는 경우 중간에 작업을 취소하는 데 사용할 수 있는 <xref:System.Threading.CancellationToken>을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9373e-153">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="9373e-154">자세한 내용은 [비동기 응용 프로그램 미세 조정 (Visual Basic)](fine-tuning-your-async-application.md) 및 [관리 되는 스레드의 취소](../../../../standard/threading/cancellation-in-managed-threads.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9373e-154">For more information, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9373e-155">추가 정보</span><span class="sxs-lookup"><span data-stu-id="9373e-155">See also</span></span>

- [<span data-ttu-id="9373e-156">Async 및 Await를 사용한 비동기 프로그래밍(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9373e-156">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="9373e-157">비동기 반환 형식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9373e-157">Async Return Types (Visual Basic)</span></span>](async-return-types.md)
- [<span data-ttu-id="9373e-158">비동기 프로그램의 제어 흐름(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9373e-158">Control Flow in Async Programs (Visual Basic)</span></span>](control-flow-in-async-programs.md)
