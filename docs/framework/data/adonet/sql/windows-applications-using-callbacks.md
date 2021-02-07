---
description: '자세한 정보: 콜백을 사용 하는 Windows 응용 프로그램'
title: 콜백을 사용하는 Windows 애플리케이션
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ae2ea457-0764-4b06-8977-713c77e85bd2
ms.openlocfilehash: d4e88e869fa61701b492083329188531c279f793
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99766974"
---
# <a name="windows-applications-using-callbacks"></a><span data-ttu-id="7f78b-103">콜백을 사용하는 Windows 애플리케이션</span><span class="sxs-lookup"><span data-stu-id="7f78b-103">Windows Applications Using Callbacks</span></span>

<span data-ttu-id="7f78b-104">대부분의 비동기 처리 시나리오에서는 데이터베이스 작업을 시작하고 데이터베이스 작업이 완료될 때까지 기다리지 않고 다른 프로세스를 계속 실행하려고 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-104">In most asynchronous processing scenarios, you want to start a database operation and continue running other processes without waiting for the database operation to complete.</span></span> <span data-ttu-id="7f78b-105">그러나 많은 시나리오에서는 데이터베이스 작업이 종료된 후 다른 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-105">However, many scenarios require doing something once the database operation has ended.</span></span> <span data-ttu-id="7f78b-106">예를 들어 Windows 애플리케이션에서 장기 실행 작업을 백그라운드 스레드에 위임하는 동시에 사용자 인터페이스 스레드가 응답성을 유지하기를 원합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-106">In a Windows application, for example, you may want to delegate the long-running operation to a background thread while allowing the user interface thread to remain responsive.</span></span> <span data-ttu-id="7f78b-107">그러나 데이터베이스 작업이 완료되면 결과를 사용하여 양식을 채워야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-107">However, when the database operation is complete, you want to use the results to populate the form.</span></span> <span data-ttu-id="7f78b-108">이 시나리오 유형은 콜백을 사용하여 구현하는 것이 가장 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-108">This type of scenario is best implemented with a callback.</span></span>  
  
 <span data-ttu-id="7f78b-109"><xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A> 또는 <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> 메서드에서 <xref:System.AsyncCallback> 대리자를 지정하여 콜백을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-109">You define a callback by specifying an <xref:System.AsyncCallback> delegate in the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, or <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> method.</span></span> <span data-ttu-id="7f78b-110">작업이 완료되면 대리자가 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-110">The delegate is called when the operation is complete.</span></span> <span data-ttu-id="7f78b-111"><xref:System.Data.SqlClient.SqlCommand> 자체에 대한 참조를 대리자에게 전달할 수 있습니다. 그러면 대리자가 쉽게 <xref:System.Data.SqlClient.SqlCommand> 개체에 액세스하고 전역 변수를 사용하지 않고 적절한 `End` 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-111">You can pass the delegate a reference to the <xref:System.Data.SqlClient.SqlCommand> itself, making it easy to access the <xref:System.Data.SqlClient.SqlCommand> object and call the appropriate `End` method without having to use a global variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f78b-112">예제</span><span class="sxs-lookup"><span data-stu-id="7f78b-112">Example</span></span>  

 <span data-ttu-id="7f78b-113">다음 Windows 애플리케이션에서는 <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> 메서드를 사용하여 몇 초의 지연이 포함된 Transact-SQL 문을 실행하는 방법을 보여 줍니다(장기 실행 명령을 에뮬레이션).</span><span class="sxs-lookup"><span data-stu-id="7f78b-113">The following Windows application demonstrates the use of the <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A> method, executing a Transact-SQL statement that includes a delay of a few seconds (emulating a long-running command).</span></span>  
  
 <span data-ttu-id="7f78b-114">이 예제에서는 별도의 스레드에서 양식과 상호 작용하는 메서드를 호출하는 등의 여러 가지 중요한 기술을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-114">This example demonstrates a number of important techniques, including calling a method that interacts with the form from a separate thread.</span></span> <span data-ttu-id="7f78b-115">또한 이 예제에서는 사용자가 여러 명령을 동시에 실행하는 것을 차단하는 방법과 콜백 프로시저를 호출하기 전에 양식이 닫히지 않도록 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-115">In addition, this example demonstrates how you must block users from concurrently executing a command multiple times, and how you must ensure that the form does not close before the callback procedure is called.</span></span>  
  
 <span data-ttu-id="7f78b-116">이 예제를 설정하려면 새 Windows 애플리케이션을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-116">To set up this example, create a new Windows application.</span></span> <span data-ttu-id="7f78b-117">각 컨트롤에 대해 기본 이름을 적용하여 양식에 <xref:System.Windows.Forms.Button> 컨트롤과 2개의 <xref:System.Windows.Forms.Label> 컨트롤을 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-117">Place a <xref:System.Windows.Forms.Button> control and two <xref:System.Windows.Forms.Label> controls on the form (accepting the default name for each control).</span></span> <span data-ttu-id="7f78b-118">사용자의 환경에 필요한 대로 연결 문자열을 수정하여 양식의 클래스에 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="7f78b-118">Add the following code to the form's class, modifying the connection string as necessary for your environment.</span></span>  
  
```vb  
' Add these to the top of the class:  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
  
' Add this code to the form's class:  
  
    ' You'll need this delegate in order to display text from a
    ' thread other than the form's thread. See the HandleCallback  
    ' procedure for more information.  
    ' This same delegate matches both the DisplayStatus
    ' and DisplayResults methods.  
    Private Delegate Sub DisplayInfoDelegate(ByVal Text As String)  
  
    ' This flag ensures that the user doesn't attempt  
    ' to restart the command or close the form while the
    ' asynchronous command is executing.  
    Private isExecuting As Boolean  
  
    ' This example maintains the connection object
    ' externally, so that it's available for closing.  
    Private connection As SqlConnection  
  
    Private Function GetConnectionString() As String  
        ' To avoid storing the connection string in your code,
        ' you can retrieve it from a configuration file.
  
        ' If you have not included "Asynchronous Processing=true"  
        ' in the connection string, the command will not be able  
        ' to execute asynchronously.  
        Return "Data Source=(local);Integrated Security=SSPI;" & _  
          "Initial Catalog=AdventureWorks;" & _  
          "Asynchronous Processing=true"  
    End Function  
  
    Private Sub DisplayStatus(ByVal Text As String)  
        Me.Label1.Text = Text  
    End Sub  
  
    Private Sub DisplayResults(ByVal Text As String)  
        Me.Label1.Text = Text  
        DisplayStatus("Ready")  
    End Sub  
  
    Private Sub Form1_FormClosing(ByVal sender As Object, _  
        ByVal e As System.Windows.Forms.FormClosingEventArgs) _  
        Handles Me.FormClosing  
        If isExecuting Then  
            MessageBox.Show(Me, "Can't close the form until " & _  
             "the pending asynchronous command has completed. " & _  
             "Please wait...")  
            e.Cancel = True  
        End If  
    End Sub  
  
    Private Sub Button1_Click( _  
        ByVal sender As System.Object, _  
        ByVal e As System.EventArgs) Handles Button1.Click  
        If isExecuting Then  
            MessageBox.Show(Me, _  
                "Already executing. " & _  
                "Please wait until the current query " & _  
                "has completed.")  
        Else  
            Dim command As SqlCommand  
            Try  
                DisplayResults("")  
                DisplayStatus("Connecting...")  
                connection = New SqlConnection(GetConnectionString())  
                ' To emulate a long-running query, wait for
                ' a few seconds before working with the data.  
                ' This command doesn't do much, but that's the point--  
                ' it doesn't change your data, in the long run.  
                Dim commandText As String = _  
                    "WAITFOR DELAY '0:0:05';" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint + 1 " & _  
                    "WHERE ReorderPoint Is Not Null;" & _  
                    "UPDATE Production.Product " & _  
                    "SET ReorderPoint = ReorderPoint - 1 " & _  
                    "WHERE ReorderPoint Is Not Null"  
  
                command = New SqlCommand(commandText, connection)  
                connection.Open()  
  
                DisplayStatus("Executing...")  
                isExecuting = True  
                ' Although it's not required that you pass the
                ' SqlCommand object as the second parameter in the
                ' BeginExecuteNonQuery call, doing so makes it easier  
                ' to call EndExecuteNonQuery in the callback procedure.  
                Dim callback As New _  
                      AsyncCallback(AddressOf HandleCallback)  
  
                ' Once the BeginExecuteNonQuery method is called,  
                ' the code continues--and the user can interact with  
                ' the form--while the server executes the query.  
  
                command.BeginExecuteNonQuery(callback, command)  
  
            Catch ex As Exception  
                isExecuting = False  
                DisplayStatus($"Ready (last error: {ex.Message})")
                If connection IsNot Nothing Then  
                    connection.Close()  
                End If  
            End Try  
        End If  
    End Sub  
  
    Private Sub HandleCallback(ByVal result As IAsyncResult)  
        Try  
            ' Retrieve the original command object, passed  
            ' to this procedure in the AsyncState property  
            ' of the IAsyncResult parameter.  
            Dim command As SqlCommand = _  
                CType(result.AsyncState, SqlCommand)  
            Dim rowCount As Integer = _  
                command.EndExecuteNonQuery(result)  
            Dim rowText As String = " rows affected."  
            If rowCount = 1 Then  
                rowText = " row affected."  
            End If  
            rowText = rowCount & rowText  
  
            ' You may not interact with the form and its contents  
            ' from a different thread, and this callback procedure  
            ' is all but guaranteed to be running from a different
            ' thread than the form. Therefore you cannot simply call
            ' code that displays the results, like this:  
            ' DisplayResults(rowText)  
  
            ' Instead, you must call the procedure from the form's  
            ' thread. One simple way to accomplish this is to call
            ' the Invoke method of the form, which calls the delegate
            ' you supply from the form's thread.
            Dim del As New _  
                DisplayInfoDelegate(AddressOf DisplayResults)  
            Me.Invoke(del, rowText)  
  
        Catch ex As Exception  
            ' Because you're now running code in a separate thread,
            ' if you don't handle the exception here, none of your
            ' other code will catch the exception. Because none of
            ' your code is on the call stack in this thread, there's
            ' nothing higher up the stack to catch the exception if
            ' you don't handle it here. You can either log the
            ' exception or invoke a delegate (as in the non-error
            ' case in this example) to display the error on the form.
            ' In no case can you simply display the error without
            ' executing a delegate as in the Try block here.  
  
            ' You can create the delegate instance as you
            ' invoke it, like this:  
            Me.Invoke(New _  
                DisplayInfoDelegate(AddressOf DisplayStatus), _  
                $"Ready (last error: {ex.Message}")
        Finally  
            isExecuting = False  
            If connection IsNot Nothing Then  
                connection.Close()  
            End If  
        End Try  
    End Sub  
```  
  
```csharp  
// Add these to the top of the class, if they're not already there:  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
// Hook up the form's Load event handler (you can double-click on
// the form's design surface in Visual Studio), and then add
// this code to the form's class:  
  
// You'll need this delegate in order to display text from a thread  
// other than the form's thread. See the HandleCallback  
// procedure for more information.  
// This same delegate matches both the DisplayStatus
// and DisplayResults methods.  
private delegate void DisplayInfoDelegate(string Text);  
  
// This flag ensures that the user doesn't attempt  
// to restart the command or close the form while the
// asynchronous command is executing.  
private bool isExecuting;  
  
// This example maintains the connection object
// externally, so that it's available for closing.  
private SqlConnection connection;  
  
private static string GetConnectionString()  
{  
    // To avoid storing the connection string in your code,
    // you can retrieve it from a configuration file.
  
    // If you have not included "Asynchronous Processing=true" in the  
    // connection string, the command will not be able  
    // to execute asynchronously.  
    return "Data Source=(local);Integrated Security=SSPI;" +  
    "Initial Catalog=AdventureWorks; Asynchronous Processing=true";  
}  
  
private void DisplayStatus(string Text)  
{  
    this.label1.Text = Text;  
}  
  
private void DisplayResults(string Text)  
{  
    this.label1.Text = Text;  
    DisplayStatus("Ready");  
}  
  
private void Form1_FormClosing(object sender, System.Windows.Forms.FormClosingEventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Can't close the form until " +  
        "the pending asynchronous command has completed. Please " +  
        "wait...");
        e.Cancel = true;  
    }  
}  
  
private void button1_Click(object sender, System.EventArgs e)  
{  
    if (isExecuting)  
    {  
        MessageBox.Show(this, "Already executing. Please wait until " +  
        "the current query has completed.");  
    }  
    else  
    {  
        SqlCommand command = null;  
        try  
        {  
            DisplayResults("");  
            DisplayStatus("Connecting...");  
            connection = new SqlConnection(GetConnectionString());  
            // To emulate a long-running query, wait for
            // a few seconds before working with the data.  
            // This command doesn't do much, but that's the point--  
            // it doesn't change your data, in the long run.  
            string commandText =  
                "WAITFOR DELAY '0:0:05';" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint + 1 " +  
                "WHERE ReorderPoint Is Not Null;" +  
                "UPDATE Production.Product " +  
                "SET ReorderPoint = ReorderPoint - 1 " +  
                "WHERE ReorderPoint Is Not Null";  
  
            command = new SqlCommand(commandText, connection);  
            connection.Open();  
  
            DisplayStatus("Executing...");  
            isExecuting = true;  
            // Although it's not required that you pass the
            // SqlCommand object as the second parameter in the
            // BeginExecuteNonQuery call, doing so makes it easier  
            // to call EndExecuteNonQuery in the callback procedure.  
            AsyncCallback callback = new AsyncCallback(HandleCallback);  
  
            // Once the BeginExecuteNonQuery method is called,  
            // the code continues--and the user can interact with  
            // the form--while the server executes the query.  
            command.BeginExecuteNonQuery(callback, command);  
  
        }  
        catch (Exception ex)  
        {  
            isExecuting = false;  
            DisplayStatus($"Ready (last error: {ex.Message})");
            if (connection != null)  
            {  
                connection.Close();  
            }  
        }  
    }  
}  
  
private void HandleCallback(IAsyncResult result)  
{  
    try  
    {  
        // Retrieve the original command object, passed  
        // to this procedure in the AsyncState property  
        // of the IAsyncResult parameter.  
        SqlCommand command = (SqlCommand)result.AsyncState;  
        int rowCount = command.EndExecuteNonQuery(result);  
        string rowText = " rows affected.";  
        if (rowCount == 1)  
        {  
            rowText = " row affected.";  
        }  
        rowText = rowCount + rowText;  
  
        // You may not interact with the form and its contents  
        // from a different thread, and this callback procedure  
        // is all but guaranteed to be running from a different thread  
        // than the form. Therefore you cannot simply call code that
        // displays the results, like this:  
        // DisplayResults(rowText)  
  
        // Instead, you must call the procedure from the form's thread.  
        // One simple way to accomplish this is to call the Invoke  
        // method of the form, which calls the delegate you supply  
        // from the form's thread.
        DisplayInfoDelegate del =
         new DisplayInfoDelegate(DisplayResults);  
        this.Invoke(del, rowText);  
    }  
    catch (Exception ex)  
    {  
        // Because you're now running code in a separate thread,
        // if you don't handle the exception here, none of your other  
        // code will catch the exception. Because none of your  
        // code is on the call stack in this thread, there's nothing  
        // higher up the stack to catch the exception if you don't
        // handle it here. You can either log the exception or
        // invoke a delegate (as in the non-error case in this
        // example) to display the error on the form. In no case  
        // can you simply display the error without executing a
        // delegate as in the try block here.
  
        // You can create the delegate instance as you
        // invoke it, like this:  
        this.Invoke(new DisplayInfoDelegate(DisplayStatus),  
            $"Ready (last error: {ex.Message}");
    }  
    finally  
    {  
        isExecuting = false;  
        if (connection != null)  
        {  
            connection.Close();  
        }  
    }  
}  
  
private void Form1_Load(object sender, System.EventArgs e)  
{  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    this.FormClosing += new System.Windows.Forms.  
        FormClosingEventHandler(this.Form1_FormClosing);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f78b-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="7f78b-119">See also</span></span>

- [<span data-ttu-id="7f78b-120">비동기 작업</span><span class="sxs-lookup"><span data-stu-id="7f78b-120">Asynchronous Operations</span></span>](asynchronous-operations.md)
- [<span data-ttu-id="7f78b-121">ADO.NET 개요</span><span class="sxs-lookup"><span data-stu-id="7f78b-121">ADO.NET Overview</span></span>](../ado-net-overview.md)
