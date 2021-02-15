---
description: '자세한 정보: 비동기 앱에서 재입력 처리 (Visual Basic)'
title: 비동기 앱에서 재진입 처리
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: aca917c1b22655547f155009c5877140d9ca5e43
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425804"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="b3809-103">비동기 응용 프로그램에서 재진입 처리(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3809-103">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="b3809-104">앱에 비동기 코드가 사용될 때, 비동기 작업이 완료되기 전에 동일한 비동기 작업을 다시 수행하는 재진입을 파악하고 방지할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-104">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="b3809-105">재진입 가능성을 식별하고 처리하지 못하면 예기치 않은 결과가 생길 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-105">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="b3809-106">예제를 실행하려면 Visual Studio 2012 이상 및 .NET Framework 4.5 이상이 컴퓨터에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-106">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="b3809-107">현재 앱 개발에 사용할 최소 버전은 TLS(전송 계층 보안) 버전 1.2입니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-107">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="b3809-108">앱이 .NET Framework 4.7 이전 버전을 대상으로 하는 경우, 다음 문서에서 [.NET Framework를 사용한 TLS(전송 계층 보안) 모범 사례](../../../../framework/network-programming/tls.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3809-108">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="b3809-109">재진입 인식</span><span class="sxs-lookup"><span data-stu-id="b3809-109">Recognizing Reentrancy</span></span>

<span data-ttu-id="b3809-110">이 항목의 예제에서는 사용자가 **시작** 버튼를 선택하여 일련의 웹 사이트를 다운로드하고 다운로드되는 총 바이트 수를 계산하는 비동기 앱을 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-110">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="b3809-111">예제의 동기 버전은 처음 실행 후 앱 실행이 완료될 때까지 UI 스레드에서 해당 이벤트를 무시하므로 사용자가 버튼를 선택하는 횟수에 관계없이 동일한 방식으로 응답합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-111">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="b3809-112">그러나 비동기 앱에서 UI 스레드는 계속 응답하므로 완료되기 전에 비동기 작업을 다시 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-112">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="b3809-113">다음 예제에서는 사용자가 **시작** 버튼를 한 번만 선택하는 경우 예상되는 출력을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-113">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="b3809-114">다운로드된 웹 사이트 목록이 각 사이트의 크기(바이트)와 함께 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-114">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="b3809-115">총 바이트 수는 끝에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-115">The total number of bytes appears at the end.</span></span>

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="b3809-116">그러나 사용자가 버튼을 두 번 이상 클릭하면 이벤트 처리기가 반복적으로 호출되고 다운로드 프로세스가 매번 다시 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-116">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="b3809-117">따라서 여러 개의 비동기 작업이 동시에 실행되면 출력에서 결과를 인터리브하며 총 바이트 수를 파악하기 어렵게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-117">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="b3809-118">이 항목의 끝으로 스크롤하면 이 출력을 생성하는 코드를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-118">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="b3809-119">로컬 컴퓨터에 솔루션을 다운로드한 다음 WebsiteDownload 프로젝트를 실행하거나 이 항목의 끝에 있는 코드를 사용하여 고유한 프로젝트를 만들면 코드를 테스트할 수 있습니다. 자세한 내용 및 지침은 [예제 앱 검토 및 실행](#BKMD_SettingUpTheExample)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="b3809-119">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a> <span data-ttu-id="b3809-120">재진입 처리</span><span class="sxs-lookup"><span data-stu-id="b3809-120">Handling Reentrancy</span></span>

<span data-ttu-id="b3809-121">앱에서 수행하려는 작업에 따라 다양한 방법으로 재진입을 처리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-121">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="b3809-122">이 항목에서는 다음 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-122">This topic presents the following examples:</span></span>

- [<span data-ttu-id="b3809-123">시작 버튼 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b3809-123">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)

  <span data-ttu-id="b3809-124">작업이 실행되는 동안 **시작** 버튼을 사용할 수 없도록 설정하여 사용자가 작업을 방해할 수 없도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-124">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="b3809-125">작업 취소 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="b3809-125">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="b3809-126">사용자가 **시작** 버튼을 다시 클릭하는 경우 현재 실행되고 있는 작업을 취소한 다음 가장 최근에 요청한 작업이 계속해서 실행되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-126">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="b3809-127">여러 작업을 실행하고 출력을 큐 대기</span><span class="sxs-lookup"><span data-stu-id="b3809-127">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="b3809-128">요청한 모든 작업이 비동기적으로 실행되도록 허용하지만 각 작업의 결과가 함께 순서대로 나타나도록 출력의 표시를 조정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-128">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="b3809-129">시작 버튼 사용 안 함</span><span class="sxs-lookup"><span data-stu-id="b3809-129">Disable the Start Button</span></span>

<span data-ttu-id="b3809-130">`StartButton_Click` 이벤트 처리기의 위쪽에 있는 버튼를 사용하지 않도록 설정하여 작업이 실행되는 동안 **시작** 버튼를 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-130">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="b3809-131">그런 다음 작업이 완료되면 `Finally` 블록 내에서 버튼를 다시 사용하도록 설정하여 사용자가 앱을 다시 실행하도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-131">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="b3809-132">다음 코드에서는 이러한 변경 내용을 보여 주며, 별표로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-132">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="b3809-133">변경 내용을 이 항목의 끝에 있는 코드에 추가하거나 완성된 앱을 [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)(비동기 샘플: .NET 데스크톱 앱의 재입력)에서 다운로드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-133">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="b3809-134">프로젝트 이름은 DisableStartButton입니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-134">The project name is DisableStartButton.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' This line is commented out to make the results clearer in the output.
    'ResultsTextBox.Text = ""

    ' ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = False

    Try
        Await AccessTheWebAsync()

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    ' ***Enable the Start button in case you want to run the program again.
    Finally
        StartButton.IsEnabled = True

    End Try
End Sub
```

<span data-ttu-id="b3809-135">변경의 결과로 `AccessTheWebAsync`에서 웹 사이트를 다운로드하는 동안 버튼이 응답하지 않으므로 프로세스를 다시 입력할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-135">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="b3809-136">작업 취소 및 다시 시작</span><span class="sxs-lookup"><span data-stu-id="b3809-136">Cancel and Restart the Operation</span></span>

<span data-ttu-id="b3809-137">**시작** 버튼을 사용하지 않도록 설정하는 대신 버튼을 활성 상태로 유지하지만 사용자가 버튼을 다시 클릭하는 경우 이미 실행되고 있는 작업을 취소하고 가장 최근에 시작한 작업이 계속되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-137">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="b3809-138">취소에 대 한 자세한 내용은 [비동기 응용 프로그램 미세 조정 (Visual Basic)](fine-tuning-your-async-application.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="b3809-138">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="b3809-139">이 시나리오를 설정하려면 [예제 앱 검토 및 실행](#BKMD_SettingUpTheExample)에서 제공하는 기본 코드를 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="b3809-140">[비동기 샘플: .NET 데스크톱 앱의 재진입](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)에서 완성된 앱을 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-140">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="b3809-141">이 프로젝트의 이름은 CancelAndRestart입니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-141">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="b3809-142">모든 메서드에 대한 범위 내에 있는 <xref:System.Threading.CancellationTokenSource> 변수 `cts`를 선언합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-142">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="b3809-143">`StartButton_Click`에서 작업이 이미 진행 중인지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-143">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="b3809-144">의 값이 이면 `cts` `Nothing` 아직 활성화 된 작업이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-144">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="b3809-145">값이이 아닌 경우 `Nothing` 이미 실행 중인 작업이 취소 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-145">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="b3809-146">`cts`를 현재 프로세스를 나타내는 다른 값으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-146">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="b3809-147">의 끝에서 `StartButton_Click` 현재 프로세스가 완료 되므로 값을 `cts` 다시로 설정 `Nothing` 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-147">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="b3809-148">다음 코드에서는 `StartButton_Click`의 모든 변경 내용을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-148">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="b3809-149">추가된 내용은 별표로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-149">The additions are marked with asterisks.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

    ' This line is commented out to make the results clearer.
    'ResultsTextBox.Text = ""

    ' *** If a download process is underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If

    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS

    Try
        ' *** Send a token to carry the message if the operation is canceled.
        Await AccessTheWebAsync(cts.Token)

    Catch ex As OperationCanceledException
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    End Try

    ' *** When the process is complete, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
End Sub
```

<span data-ttu-id="b3809-150">`AccessTheWebAsync`에서 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-150">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="b3809-151">`StartButton_Click`에서 취소 토큰을 허용하도록 매개 변수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-151">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="b3809-152">`GetAsync`가 <xref:System.Threading.CancellationToken> 인수를 허용하므로 <xref:System.Net.Http.HttpClient.GetAsync%2A> 메서드를 사용하여 웹 사이트를 다운로드합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-152">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="b3809-153">`DisplayResults`를 호출하여 다운로드한 각 웹 사이트에 대한 결과를 표시하려면 먼저 `ct`를 확인하여 현재 작업이 취소되었는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-153">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="b3809-154">다음 코드에서는 이러한 변경 내용을 보여 주며, 별표로 표시되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-154">The following code shows these changes, which are marked with asterisks.</span></span>

```vb
' *** Provide a parameter for the CancellationToken from StartButton_Click.
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task

    ' Declare an HttpClient object.
    Dim client = New HttpClient()

    ' Make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()

    Dim total = 0
    Dim position = 0

    For Each url In urlList
        ' *** Use the HttpClient.GetAsync method because it accepts a
        ' cancellation token.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' *** Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' *** Check for cancellations before displaying information about the
        ' latest site.
        ct.ThrowIfCancellationRequested()

        position += 1
        DisplayResults(url, urlContents, position)

        ' Update the total.
        total += urlContents.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="b3809-155">이 앱이 실행 되는 동안 **시작** 단추를 여러 번 선택 하면 다음 출력과 유사한 결과가 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-155">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

```console
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="b3809-156">부분 목록을 제거하려면 `StartButton_Click`에서 코드 첫 줄의 주석 처리를 제거하여 사용자가 작업을 다시 시작할 때마다 텍스트 상자의 내용을 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-156">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="b3809-157">여러 작업을 실행하고 출력을 큐 대기</span><span class="sxs-lookup"><span data-stu-id="b3809-157">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="b3809-158">이 세 번째 예제는 사용자가 **시작** 버튼을 선택할 때마다 앱이 다른 비동기 작업을 시작하고 모든 작업이 실행되어 완료된다는 점에서 가장 복잡합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-158">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="b3809-159">요청한 모든 작업은 목록에서 비동기적으로 웹 사이트를 다운로드하지만 작업의 출력은 순차적으로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-159">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="b3809-160">즉, 실제 다운로드 작업은 [재진입 인식](#BKMK_RecognizingReentrancy)의 출력에 표시된 대로 인터리브되지만 각 그룹에 대한 결과 목록은 별도로 제공됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-160">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="b3809-161">작업은 표시 프로세스의 게이트키퍼 역할을 하는 전역 <xref:System.Threading.Tasks.Task>, `pendingWork`를 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-161">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="b3809-162">[앱 빌드](#BKMK_BuildingTheApp)의 코드에 변경 내용을 붙여 넣어이 예제를 실행 하거나, [앱 다운로드](#BKMK_DownloadingTheApp) 의 지침에 따라 샘플을 다운로드 한 다음 QueueResults 프로젝트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-162">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="b3809-163">다음 출력은 사용자가 **시작** 버튼을 한 번만 선택하는 경우의 결과를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-163">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="b3809-164">문제 레이블 A는 처음으로 **시작** 버튼을 선택한 경우의 결과임을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-164">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="b3809-165">숫자는 다운로드 대상 목록에서 URL의 순서를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-165">The numbers show the order of the URLs in the list of download targets.</span></span>

```console
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

<span data-ttu-id="b3809-166">사용자가 **시작** 버튼을 세 번 선택하면 앱이 다음 줄과 유사한 출력을 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-166">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="b3809-167">파운드 기호(#)로 시작하는 정보 줄은 애플리케이션의 진행률을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-167">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```console
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

<span data-ttu-id="b3809-168">그룹 B와 C는 그룹 A가 완료되기 전에 시작되지만 각 그룹에 대한 출력은 별도로 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-168">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="b3809-169">그룹 A에 대한 모든 출력이 먼저 나타나고 그 뒤에 그룹 B에 대한 모든 출력과 그룹 C에 대한 모든 출력이 차례로 나타납니다. 앱은 항상 순서대로 그룹을 표시하고 각 그룹에 대해 URL이 URL 목록에 나타나는 순서대로 개별 웹 사이트에 대한 정보를 항상 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-169">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="b3809-170">그러나 다운로드가 실제로 수행되는 순서는 예측할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-170">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="b3809-171">여러 그룹이 시작된 후에는 그룹이 생성하는 다운로드 작업이 모두 활성화됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-171">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="b3809-172">A-1이 B-1보다 먼저 다운로드된다고 가정할 수 없으며 A-1이 A-2보다 먼저 다운로드된다고 가정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-172">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="b3809-173">전역 정의</span><span class="sxs-lookup"><span data-stu-id="b3809-173">Global Definitions</span></span>

<span data-ttu-id="b3809-174">샘플 코드는 모든 메서드에서 표시되는 다음과 같은 두 가지 전역 선언을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-174">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="b3809-175">`Task` 변수 `pendingWork`는 표시 프로세스를 감독하고 모든 그룹이 다른 그룹의 표시 작업을 방해하지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-175">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="b3809-176">문자 변수 `group`은 다른 그룹의 출력에 레이블을 지정하여 해당 결과가 예상 순서대로 나타나는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-176">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="b3809-177">Click 이벤트 처리기</span><span class="sxs-lookup"><span data-stu-id="b3809-177">The Click Event Handler</span></span>

<span data-ttu-id="b3809-178">이벤트 처리기 `StartButton_Click`은 사용자가 **시작** 버튼를 선택할 때마다 그룹 문자를 증가시킵니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-178">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="b3809-179">그런 다음 처리기에서 `AccessTheWebAsync`를 호출하여 다운로드 중인 작업을 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-179">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' ***Verify that each group's results are displayed together, and that
    ' the groups display in order, by marking each group with a letter.
    group = ChrW(AscW(group) + 1)
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)

    Try
        ' *** Pass the group value to AccessTheWebAsync.
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)

        ' The following line verifies a successful return from the download and
        ' display procedures.
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."

    End Try
End Sub
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="b3809-180">AccessTheWebAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="b3809-180">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="b3809-181">이 예제에서는 `AccessTheWebAsync`를 두 개의 메서드로 분할합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-181">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="b3809-182">첫 번째 메서드 `AccessTheWebAsync`는 그룹에 대해 모든 다운로드 작업을 시작하고 `pendingWork`를 설정하여 표시 프로세스를 제어합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-182">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="b3809-183">이 메서드는 LINQ(통합 언어 쿼리) 쿼리 및 <xref:System.Linq.Enumerable.ToArray%2A>를 사용하여 모든 다운로드 작업을 동시에 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-183">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="b3809-184">그런 다음 `AccessTheWebAsync`는 `FinishOneGroupAsync`를 호출하여 각 다운로드가 완료될 때까지 대기하고 해당 길이를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-184">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="b3809-185">`FinishOneGroupAsync`는 `AccessTheWebAsync`의 `pendingWork`에 할당되는 작업을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-185">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="b3809-186">해당 값은 작업이 완료되기 전에 다른 작업에 의한 중단을 방지합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-186">That value prevents interruption by another operation before the task is complete.</span></span>

```vb
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)

    Dim client = New HttpClient()

    ' Make a list of the web addresses to download.
    Dim urlList As List(Of String) = SetUpURLList()

    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Dim getContentTasks As Task(Of Byte())() =
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()

    ' ***Call the method that awaits the downloads and displays the results.
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)

    ResultsTextBox.Text &=
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)

    ' ***This task is complete when a group has finished downloading and displaying.
    Await pendingWork

    ' You can do other work here or just return.
    Return grp
End Function
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="b3809-187">FinishOneGroupAsync 메서드</span><span class="sxs-lookup"><span data-stu-id="b3809-187">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="b3809-188">이 메서드는 한 그룹의 다운로드 작업을 순환하여 각 작업을 대기하고 다운로드한 웹 사이트의 길이를 표시하고 길이를 합계에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-188">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="b3809-189">`FinishOneGroupAsync`의 첫 번째 문은 `pendingWork`를 사용하여 메서드 입력이 이미 표시 프로세스에 있거나 이미 대기 중인 작업을 방해하지 않는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-189">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="b3809-190">이러한 작업이 진행 중인 경우 입력 작업은 해당 순서를 기다려야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-190">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```vb
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task

    ' Wait for the previous group to finish displaying results.
    If pendingWork IsNot Nothing Then
        Await pendingWork
    End If

    Dim total = 0

    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    For i As Integer = 0 To contentTasks.Length - 1
        ' Await the download of a particular URL, and then display the URL and
        ' its length.
        Dim content As Byte() = Await contentTasks(i)
        DisplayResults(urls(i), content, i, grp)
        total += content.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="b3809-191">변경 내용을 [앱 빌드](#BKMK_BuildingTheApp)의 코드에 붙여 넣어 이 예제를 실행하거나, [앱 다운로드](#BKMK_DownloadingTheApp)의 지침에 따라 샘플을 다운로드한 다음 QueueResults 프로젝트를 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-191">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="b3809-192">관심 영역</span><span class="sxs-lookup"><span data-stu-id="b3809-192">Points of Interest</span></span>

<span data-ttu-id="b3809-193">출력에서 파운드 기호(#)로 시작하는 정보 줄은 이 예제의 작동 방식을 명확히 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-193">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="b3809-194">출력은 다음과 같은 패턴을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-194">The output shows the following patterns.</span></span>

- <span data-ttu-id="b3809-195">이전 그룹이 출력을 표시하는 동안 그룹이 시작될 수 있지만 이전 그룹의 출력 표시가 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-195">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

  ```console
  #Starting group A.
  #Task assigned for group A. Download tasks are active.

  A-1. msdn.microsoft.com/library/hh191443.aspx                87389
  A-2. msdn.microsoft.com/library/aa578028.aspx               207089
  A-3. msdn.microsoft.com/library/jj155761.aspx                30870
  A-4. msdn.microsoft.com/library/hh290140.aspx               119037
  A-5. msdn.microsoft.com/library/hh524395.aspx                71260

  #Starting group B.
  #Task assigned for group B. Download tasks are active.

  A-6. msdn.microsoft.com/library/ms404677.aspx               199186
  A-7. msdn.microsoft.com                                            53078
  A-8. msdn.microsoft.com/library/ff730837.aspx               148010

  TOTAL bytes returned:  915919

  B-1. msdn.microsoft.com/library/hh191443.aspx                87388
  B-2. msdn.microsoft.com/library/aa578028.aspx               207089
  B-3. msdn.microsoft.com/library/jj155761.aspx                30870

  #Group A is complete.

  B-4. msdn.microsoft.com/library/hh290140.aspx               119027
  B-5. msdn.microsoft.com/library/hh524395.aspx                71260
  B-6. msdn.microsoft.com/library/ms404677.aspx               199186
  B-7. msdn.microsoft.com                                            53078
  B-8. msdn.microsoft.com/library/ff730837.aspx               148010

  TOTAL bytes returned:  915908
  ```

- <span data-ttu-id="b3809-196">`pendingWork`작업은 처음에 시작 된 `Nothing` `FinishOneGroupAsync` 그룹 A에 대해서만 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-196">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="b3809-197">그룹 A는 `FinishOneGroupAsync`에 도달할 때 await 식을 아직 완료하지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-197">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="b3809-198">따라서 컨트롤이 `AccessTheWebAsync`로 반환되지 않았으며 `pendingWork`에 대한 첫 번째 할당이 발생되지 않았습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-198">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="b3809-199">다음 두 줄은 항상 출력에 함께 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-199">The following two lines always appear together in the output.</span></span> <span data-ttu-id="b3809-200">코드는 `StartButton_Click`의 그룹 작업 시작과 `pendingWork`에 그룹에 대한 작업 할당 사이에서 중단되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-200">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="b3809-201">그룹이 `StartButton_Click`을 입력한 후 작업은 `FinishOneGroupAsync`를 입력한 다음에야 await 식을 완료합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-201">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="b3809-202">따라서 코드의 해당 세그먼트 중에는 다른 작업에서 제어할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-202">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="b3809-203">예제 앱 검토 및 실행</span><span class="sxs-lookup"><span data-stu-id="b3809-203">Reviewing and Running the Example App</span></span>

<span data-ttu-id="b3809-204">예제 앱을 더 잘 이해하려면 다운로드하거나, 직접 빌드하거나, 앱을 구현하지 않고 이 항목의 끝에 있는 코드를 검토할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-204">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="b3809-205">예제를 WPF(Windows Presentation Foundation) 데스크톱 앱으로 실행하려면 Visual Studio 2012 이상 및 .NET Framework 4.5 이상이 컴퓨터에 설치되어 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-205">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="b3809-206">앱 다운로드</span><span class="sxs-lookup"><span data-stu-id="b3809-206">Downloading the App</span></span>

1. <span data-ttu-id="b3809-207">[Async Samples: .NET 데스크톱 앱의 재진입](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)에서 완성된 앱을 다운로드할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-207">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="b3809-208">다운로드한 파일의 압축을 푼 다음 Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-208">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="b3809-209">메뉴 모음에서 **파일**, **열기**, **프로젝트/솔루션** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-209">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="b3809-210">압축을 푼 샘플 코드가 저장된 폴더로 이동한 다음 솔루션(.sln) 파일을 엽니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-210">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="b3809-211">**솔루션 탐색기** 에서 실행하려는 프로젝트의 바로 가기 메뉴를 연 후 **StartUpProject로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-211">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="b3809-212">CTRL+F5를 선택하여 프로젝트를 빌드하고 실행합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-212">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="b3809-213">앱 빌드</span><span class="sxs-lookup"><span data-stu-id="b3809-213">Building the App</span></span>

<span data-ttu-id="b3809-214">다음 섹션에서는 예제를 WPF 앱으로 빌드하는 코드를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-214">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="b3809-215">WPF 응용 프로그램을 빌드하려면</span><span class="sxs-lookup"><span data-stu-id="b3809-215">To build a WPF app</span></span>

1. <span data-ttu-id="b3809-216">Visual Studio를 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-216">Start Visual Studio.</span></span>

2. <span data-ttu-id="b3809-217">메뉴 모음에서 **파일**, **새로 만들기**, **프로젝트** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-217">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="b3809-218">**새 프로젝트** 대화 상자가 열립니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-218">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="b3809-219">**설치 된 템플릿** 창에서 **Visual Basic** 을 확장 한 다음 **Windows** 를 확장 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-219">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="b3809-220">프로젝트 형식 목록에서 **WPF 애플리케이션** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-220">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="b3809-221">프로젝트 이름을 `WebsiteDownloadWPF`로 지정하고 .NET Framework 버전 4.6 이상을 선택한 다음, **확인** 단추를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-221">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="b3809-222">**솔루션 탐색기** 에 새 프로젝트가 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-222">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="b3809-223">Visual Studio 코드 편집기에서 **MainWindow.xaml** 탭을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-223">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="b3809-224">탭이 표시되지 않는 경우 **솔루션 탐색기** 에서 MainWindow.xaml의 바로 가기 메뉴를 열고 **코드 보기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-224">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="b3809-225">MainWindow.xaml의 **XAML** 보기에서 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-225">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```xaml
    <Window x:Class="MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     <span data-ttu-id="b3809-226">텍스트 상자와 버튼이 포함된 간단한 창이 MainWindow.xaml의 **디자인** 보기에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-226">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="b3809-227">**솔루션 탐색기** 에서 **참조** 를 마우스 오른쪽 단추로 클릭하고 **참조 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-227">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="b3809-228">아직 선택하지 않은 경우 <xref:System.Net.Http>에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-228">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="b3809-229">**솔루션 탐색기** 에서 mainwindow.xaml의 바로 가기 메뉴를 열고 **코드 보기** 를 선택 합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-229">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="b3809-230">Mainwindow.xaml에서 코드를 다음 코드로 바꿉니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-230">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

            ' This line is commented out to make the results clearer in the output.
            'ResultsTextBox.Text = ""

            Try
                Await AccessTheWebAsync()

            Catch ex As Exception
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."

            End Try
        End Sub

        Private Async Function AccessTheWebAsync() As Task

            ' Declare an HttpClient object.
            Dim client = New HttpClient()

            ' Make a list of web addresses.
            Dim urlList As List(Of String) = SetUpURLList()

            Dim total = 0
            Dim position = 0

            For Each url In urlList
                ' GetByteArrayAsync returns a task. At completion, the task
                ' produces a byte array.
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

                position += 1
                DisplayResults(url, urlContents, position)

                ' Update the total.
                total += urlContents.Length
            Next

            ' Display the total count for all of the websites.
            ResultsTextBox.Text &=
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
        End Function

        Private Function SetUpURLList() As List(Of String)
            Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. <span data-ttu-id="b3809-231">CTRL+F5 키를 선택하여 프로그램을 실행한 다음 **시작** 버튼을 여러 번 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-231">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="b3809-232">[시작 버튼 사용 안 함](#BKMK_DisableTheStartButton), [작업 취소 및 다시 시작](#BKMK_CancelAndRestart) 또는 [여러 작업을 실행하고 출력을 큐 대기](#BKMK_RunMultipleOperations)의 내용을 변경하여 재진입을 처리합니다.</span><span class="sxs-lookup"><span data-stu-id="b3809-232">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3809-233">참조</span><span class="sxs-lookup"><span data-stu-id="b3809-233">See also</span></span>

- [<span data-ttu-id="b3809-234">연습: Async 및 Await를 사용하여 웹에 액세스(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3809-234">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="b3809-235">Async 및 Await를 사용한 비동기 프로그래밍(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3809-235">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](index.md)
