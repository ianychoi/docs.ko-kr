---
description: '자세한 정보: 사용자 지정 식 편집기 사용'
title: 사용자 지정 식 편집기 사용
ms.date: 03/30/2017
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
ms.openlocfilehash: 0455088d879e51a31b0139f85f871be3fb87e7e6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99755098"
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="ca540-103">사용자 지정 식 편집기 사용</span><span class="sxs-lookup"><span data-stu-id="ca540-103">Using a Custom Expression Editor</span></span>

<span data-ttu-id="ca540-104">사용자 지정 식 편집기를 구현하여 보다 다양하거나 단순한 식 편집 환경을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-104">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="ca540-105">사용자 지정 식 편집기는 다음과 같은 경우에 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-105">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
- <span data-ttu-id="ca540-106">IntelliSense와 다시 호스트된 Workflow Designer의 다른 다양한 편집 기능을 지원하려는 경우.</span><span class="sxs-lookup"><span data-stu-id="ca540-106">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="ca540-107">다시 호스팅된 응용 프로그램에서는 기본 Visual Studio 식 편집기를 사용할 수 없으므로이 기능을 제공 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-107">This functionality must be provided because the default Visual Studio expression editor cannot be used in rehosted applications.</span></span>  
  
- <span data-ttu-id="ca540-108">예를 들어 Visual Basic를 배우고 Visual Basic 식을 처리 하는 데 필요 하지 않은 비즈니스 분석가 사용자를 위한 식 편집 환경을 간소화 합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-108">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn Visual Basic or deal with Visual Basic expressions.</span></span>  
  
 <span data-ttu-id="ca540-109">사용자 지정 식 편집기를 구현하는 데는 기본적으로 다음과 같은 세 단계가 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-109">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1. <span data-ttu-id="ca540-110"><xref:System.Activities.Presentation.View.IExpressionEditorService> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-110">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="ca540-111">이 인터페이스는 식 편집기의 생성과 삭제를 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-111">This interface manages the creation and destruction of expression editors.</span></span>  
  
2. <span data-ttu-id="ca540-112"><xref:System.Activities.Presentation.View.IExpressionEditorInstance> 인터페이스를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-112">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="ca540-113">이 인터페이스는 식 편집 UI용 UI를 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-113">This interface implements the UI for expression editing UI.</span></span>  
  
3. <span data-ttu-id="ca540-114">다시 호스트된 워크플로 애플리케이션에 <xref:System.Activities.Presentation.View.IExpressionEditorService>를 게시합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-114">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="ca540-115">클래스 라이브러리의 사용자 지정 식 편집기 구현</span><span class="sxs-lookup"><span data-stu-id="ca540-115">Implementing a Custom Expression Editor in a Class Library</span></span>  

 <span data-ttu-id="ca540-116">다음 샘플 코드에서는 MyExpressionEditorService 라이브러리 프로젝트에 포함된 `MyEditorService` 인터페이스를 구현하는 <xref:System.Activities.Presentation.View.IExpressionEditorService> 클래스를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-116">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="ca540-117">다음 `MyExpressionEditorInstance` 인터페이스를 구현하는 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 클래스의 코드는 MyExpressionEditorService 라이브러리 프로젝트에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-117">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```csharp  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="ca540-118">WPF 프로젝트에서 사용자 지정 식 편집기 게시</span><span class="sxs-lookup"><span data-stu-id="ca540-118">Publishing a Custom Expression Editor in a WPF Project</span></span>  

 <span data-ttu-id="ca540-119">WPF 응용 프로그램에서 디자이너를 rehost 하는 방법 및 서비스를 만들고 게시 하는 방법을 보여 주는 코드는 다음과 같습니다 `MyEditorService` .</span><span class="sxs-lookup"><span data-stu-id="ca540-119">Here is the code that shows how to rehost the designer in a WPF application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="ca540-120">이 코드를 사용하기 전에 avalon2를 포함하는 프로젝트에서 MyExpressionEditorService 라이브러리 프로젝트에 대한 참조를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-120">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```csharp  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="ca540-121">참고</span><span class="sxs-lookup"><span data-stu-id="ca540-121">Notes</span></span>  

 <span data-ttu-id="ca540-122">사용자 지정 활동 디자이너에서 **Expressiontextbox** 컨트롤을 사용 하는 경우 <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> 인터페이스의 및 메서드를 사용 하 여 식 편집기를 만들고 제거할 필요가 없습니다 <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> <xref:System.Activities.Presentation.View.IExpressionEditorService> .</span><span class="sxs-lookup"><span data-stu-id="ca540-122">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="ca540-123"><xref:System.Activities.Presentation.View.ExpressionTextBox> 클래스가 이 부분을 자동으로 관리합니다.</span><span class="sxs-lookup"><span data-stu-id="ca540-123">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca540-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ca540-124">See also</span></span>

- <xref:System.Activities.Presentation.View.IExpressionEditorService>
- <xref:System.Activities.Presentation.View.IExpressionEditorInstance>
- [<span data-ttu-id="ca540-125">사용자 지정 활동 디자이너에서 ExpressionTextBox 사용</span><span class="sxs-lookup"><span data-stu-id="ca540-125">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](./samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
