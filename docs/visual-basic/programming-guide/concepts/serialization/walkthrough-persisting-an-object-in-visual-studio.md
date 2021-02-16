---
description: '자세한 정보: 연습: Visual Studio에서 개체 유지 (Visual Basic)'
title: Visual Studio에서 개체 유지
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 4145f84d14eadae6a305a4a1f5860cdcc38450c8
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486864"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="d6495-103">연습: Visual Studio에서 개체 유지(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6495-103">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>

<span data-ttu-id="d6495-104">디자인 타임에 개체의 속성을 기본값으로 설정할 수 있지만, 런타임에 입력한 값은 개체가 소멸될 때 손실됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-104">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="d6495-105">serialization을 사용하면 인스턴스 간에 개체의 데이터를 유지할 수 있으므로, 다음에 개체를 인스턴스화할 때 값을 저장하고 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-105">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6495-106">Visual Basic에서는 이름이나 숫자 등의 단순한 데이터를 저장하려는 경우 `My.Settings` 개체를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-106">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="d6495-107">자세한 내용은 [My.Settings 개체](../../../language-reference/objects/my-settings-object.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6495-107">For more information, see [My.Settings Object](../../../language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="d6495-108">이 연습에서는 간단한 `Loan` 개체를 만들고 데이터를 파일에 유지합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-108">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="d6495-109">그런 다음 개체를 다시 만들 때 파일에서 데이터를 검색합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-109">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6495-110">이 예제에서는 파일이 아직 없는 경우 새 파일을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-110">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="d6495-111">애플리케이션에서 파일을 만들어야 하는 경우 해당 애플리케이션은 폴더에 대한 `Create` 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-111">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="d6495-112">권한은 액세스 제어 목록을 사용하여 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-112">Permissions are set by using access control lists.</span></span> <span data-ttu-id="d6495-113">파일이 이미 있는 경우, 애플리케이션에는 더 낮은 권한인 `Write` 권한만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-113">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="d6495-114">가능한 경우 배포하는 동안 파일을 만드는 것이 안전하며, 폴더에 대한 Create 권한 대신 단일 파일에 대해 `Read` 권한만 부여하는 것이 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="d6495-115">또한 루트 폴더나 Program Files 폴더보다 사용자 폴더에 데이터를 쓰는 것이 더 안전합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-115">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d6495-116">이 예제에서는 이진 파일에 데이터를 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-116">This example stores data in a binary.</span></span> <span data-ttu-id="d6495-117">이러한 형식은 암호 또는 신용 카드 정보와 같은 중요한 데이터에 사용하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-117">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6495-118">표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-118">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d6495-119">설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-119">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d6495-120">자세한 내용은 [Visual Studio IDE 개인 설정](/visualstudio/ide/personalizing-the-visual-studio-ide)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6495-120">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="d6495-121">Loan 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="d6495-121">Creating the Loan Object</span></span>  

 <span data-ttu-id="d6495-122">첫 번째 단계는 `Loan` 클래스와 이 클래스를 사용하는 테스트 애플리케이션을 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-122">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="d6495-123">Loan 클래스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="d6495-123">To create the Loan class</span></span>  
  
1. <span data-ttu-id="d6495-124">새 클래스 라이브러리 프로젝트를 만들고 "LoanClass"라는 이름을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-124">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="d6495-125">자세한 내용은 [솔루션 및 프로젝트 만들기](/visualstudio/ide/creating-solutions-and-projects)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="d6495-125">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="d6495-126">**솔루션 탐색기** 에서 Class1 파일에 대한 바로 가기 메뉴를 열고 **이름 바꾸기** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-126">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="d6495-127">파일 이름을 `Loan`로 바꾸고 ENTER 키를 누릅니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-127">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="d6495-128">파일 이름을 바꾸면 클래스 이름도 `Loan`으로 바뀝니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-128">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="d6495-129">클래스에 다음 공용 멤버를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-129">Add the following public members to the class:</span></span>  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 <span data-ttu-id="d6495-130">`Loan` 클래스를 사용하는 간단한 애플리케이션도 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-130">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="d6495-131">테스트 애플리케이션을 만들려면</span><span class="sxs-lookup"><span data-stu-id="d6495-131">To create a test application</span></span>  
  
1. <span data-ttu-id="d6495-132">Windows Forms 애플리케이션 프로젝트를 솔루션에 추가하려면 **파일** 메뉴에서 **추가**, **새 프로젝트** 를 차례로 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-132">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="d6495-133">**새 프로젝트 추가** 대화 상자에서 **Windows Forms 애플리케이션** 을 선택하고, 프로젝트 이름으로 `LoanApp`를 입력한 다음, **확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-133">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="d6495-134">**솔루션 탐색기** 에서 LoanApp 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-134">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="d6495-135">**프로젝트** 메뉴에서 **시작 프로젝트로 설정** 을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-135">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="d6495-136">**프로젝트** 메뉴에서 **참조 추가** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-136">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="d6495-137">**참조 추가** 대화 상자에서 **프로젝트** 탭을 선택한 다음 LoanClass 프로젝트를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-137">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="d6495-138">**확인** 을 클릭하여 대화 상자를 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-138">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="d6495-139">디자이너에서 <xref:System.Windows.Forms.TextBox> 컨트롤 4개를 폼에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-139">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="d6495-140">코드 편집기에서 다음 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-140">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="d6495-141">다음 코드를 사용하여 `PropertyChanged` 이벤트에 대한 이벤트 처리기를 양식에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-141">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="d6495-142">이 시점에서 애플리케이션을 빌드 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-142">At this point, you can build and run the application.</span></span> <span data-ttu-id="d6495-143">`Loan` 클래스의 기본값이 텍스트 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-143">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="d6495-144">금리 값을 7.5에서 7.1로 변경한 다음 애플리케이션을 닫고 다시 실행합니다. 값이 기본값인 7.5로 돌아갑니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-144">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="d6495-145">현실 세계에서 금리는 주기적으로 변경되지만, 애플리케이션이 실행될 때마다 변경되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-145">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="d6495-146">애플리케이션이 실행될 때마다 사용자가 금리를 업데이트하도록 하는 대신 애플리케이션 인스턴스 간에 가장 최근의 금리를 유지하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-146">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="d6495-147">다음 단계에서는 Loan 클래스에 serialization을 추가하여 이를 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-147">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="d6495-148">Serialization을 사용하여 개체 유지</span><span class="sxs-lookup"><span data-stu-id="d6495-148">Using Serialization to Persist the Object</span></span>  

 <span data-ttu-id="d6495-149">Loan 클래스의 값을 유지하려면 먼저 클래스를 `Serializable` 속성으로 표시해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-149">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="d6495-150">클래스를 serialize로 표시하려면</span><span class="sxs-lookup"><span data-stu-id="d6495-150">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="d6495-151">Loan 클래스에 대한 클래스 선언을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-151">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="d6495-152">`Serializable` 특성은 클래스의 모든 내용을 파일에 유지할 수 있음을 컴파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-152">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="d6495-153">`PropertyChanged` 이벤트는 Windows Form 개체에 의해 처리되므로 serialize할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-153">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="d6495-154">`NonSerialized` 특성은 유지해서는 안 되는 클래스 멤버를 표시하는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-154">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="d6495-155">멤버가 serialize되지 않게 하려면</span><span class="sxs-lookup"><span data-stu-id="d6495-155">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="d6495-156">`PropertyChanged` 이벤트에 대한 선언을 다음과 같이 변경합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-156">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="d6495-157">다음 단계는 LoanApp 애플리케이션에 serialization 코드를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-157">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="d6495-158">클래스를 serialize하여 파일에 쓰려면 <xref:System.IO> 및 <xref:System.Xml.Serialization> 네임스페이스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-158">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="d6495-159">정규화된 이름을 입력하지 않으려면 필요한 클래스 라이브러리에 대한 참조를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-159">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="d6495-160">네임스페이스에 대한 참조를 추가하려면</span><span class="sxs-lookup"><span data-stu-id="d6495-160">To add references to namespaces</span></span>  
  
- <span data-ttu-id="d6495-161">`Form1` 클래스 맨 위에 다음 문을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-161">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="d6495-162">이 경우 이진 포맷터를 사용하여 개체를 이진 형식으로 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-162">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="d6495-163">다음 단계는 개체를 만들 때 파일에서 개체를 역직렬화할 코드를 추가하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-163">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="d6495-164">개체를 역직렬화하려면</span><span class="sxs-lookup"><span data-stu-id="d6495-164">To deserialize an object</span></span>  
  
1. <span data-ttu-id="d6495-165">Serialize된 데이터의 파일 이름에 대해 클래스에 상수를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-165">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="d6495-166">다음과 같이 `Form1_Load` 이벤트 프로시저에서 코드를 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-166">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     <span data-ttu-id="d6495-167">먼저 파일이 있는지를 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-167">Note that you first must check that the file exists.</span></span> <span data-ttu-id="d6495-168">파일이 있으면 이진 파일을 읽는 <xref:System.IO.Stream> 클래스와 파일을 변환하는 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 클래스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-168">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="d6495-169">또한 스트림 형식에서 Loan 개체 형식으로 변환해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-169">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="d6495-170">그런 다음 텍스트 상자에 입력된 데이터를 `Loan` 클래스에 저장하는 코드를 추가하고, 클래스를 파일로 serialize해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-170">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="d6495-171">데이터를 저장하고 클래스를 serialize하려면</span><span class="sxs-lookup"><span data-stu-id="d6495-171">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="d6495-172">다음 코드를 `Form1_FormClosing` 이벤트 프로시저에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-172">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 <span data-ttu-id="d6495-173">이 시점에서 다시 애플리케이션을 빌드 및 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-173">At this point, you can again build and run the application.</span></span> <span data-ttu-id="d6495-174">처음에는 텍스트 상자에 기본값이 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-174">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="d6495-175">값을 변경하고 네 번째 텍스트 상자에 이름을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-175">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="d6495-176">애플리케이션을 닫았다가 다시 엽니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-176">Close the application and then run it again.</span></span> <span data-ttu-id="d6495-177">이제 새 값이 텍스트 상자에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="d6495-177">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6495-178">추가 정보</span><span class="sxs-lookup"><span data-stu-id="d6495-178">See also</span></span>

- [<span data-ttu-id="d6495-179">Serialization(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6495-179">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="d6495-180">Visual Basic 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="d6495-180">Visual Basic Programming Guide</span></span>](../../index.md)
