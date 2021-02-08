---
description: '자세한 정보: 비즈니스 논리 구현 (LINQ to SQL)'
title: 비즈니스 논리 구현(LINQ to SQL)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c4577590-7b12-42e1-84a6-95aa2562727e
ms.openlocfilehash: 3f2b7085db3832f37da7520c8f75b6bc120125f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803882"
---
# <a name="implementing-business-logic-linq-to-sql"></a><span data-ttu-id="a7828-103">비즈니스 논리 구현(LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="a7828-103">Implementing Business Logic (LINQ to SQL)</span></span>

<span data-ttu-id="a7828-104">이 항목에서 "비즈니스 논리"는 데이터베이스에서 데이터를 삽입, 업데이트 또는 삭제하기 전에 데이터에 적용하는 모든 사용자 지정 규칙 또는 유효성 검사 테스트를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-104">The term "business logic" in this topic refers to any custom rules or validation tests that you apply to data before it is inserted, updated or deleted from the database.</span></span> <span data-ttu-id="a7828-105">비즈니스 논리를 "비즈니스 규칙" 또는 "도메인 논리"라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-105">Business logic is also sometimes referred to as "business rules" or "domain logic."</span></span> <span data-ttu-id="a7828-106">N 계층 애플리케이션의 경우 비즈니스 논리는 일반적으로 프레젠테이션 계층이나 데이터 액세스 계층과 독립적으로 수정될 수 있도록 논리 계층으로 디자인됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-106">In n-tier applications it is typically designed as a logical layer so that it can be modified independently of the presentation layer or data access layer.</span></span> <span data-ttu-id="a7828-107">비즈니스 논리는 데이터베이스 데이터의 업데이트, 삽입 또는 삭제 전과 후에 데이터 액세스 계층에서 호출될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-107">The business logic can be invoked by the data access layer before or after any update, insertion, or deletion of data in the database.</span></span>  
  
 <span data-ttu-id="a7828-108">비즈니스 논리는 필드의 형식이 테이블 열의 형식과 호환되는지 확인하는 스키마 유효성 검사처럼 간단한 논리부터</span><span class="sxs-lookup"><span data-stu-id="a7828-108">The business logic can be as simple as a schema validation to make sure that the type of the field is compatible with the type of the table column.</span></span> <span data-ttu-id="a7828-109">훨씬 더 복잡한 방식으로 상호 작용하는 개체의 집합으로 구성된 논리까지 매우 다양합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-109">Or it can consist of a set of objects that interact in arbitrarily complex ways.</span></span> <span data-ttu-id="a7828-110">규칙은 데이터베이스에 저장 프로시저로 구현되거나 메모리 내 개체로 구현될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-110">The rules may be implemented as stored procedures on the database or as in-memory objects.</span></span> <span data-ttu-id="a7828-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]을 사용하면 비즈니스 논리가 어떻게 구현되었는지에 관계없이 부분 클래스와 부분 메서드(Partial Method)를 사용하여 비즈니스 논리와 데이터 액세스 코드를 분리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-111">However the business logic is implemented, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] enables you use partial classes and partial methods to separate the business logic from the data access code.</span></span>  
  
## <a name="how-linq-to-sql-invokes-your-business-logic"></a><span data-ttu-id="a7828-112">LINQ to SQL로 비즈니스 논리를 호출하는 방법</span><span class="sxs-lookup"><span data-stu-id="a7828-112">How LINQ to SQL Invokes Your Business Logic</span></span>  

 <span data-ttu-id="a7828-113">디자인 타임에 수동으로 또는 개체 관계형 디자이너 또는 SQLMetal을 사용 하 여 엔터티 클래스를 생성 하는 경우 partial 클래스로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-113">When you generate an entity class at design time, either manually or by using the Object Relational Designer or SQLMetal, it is defined as a partial class.</span></span> <span data-ttu-id="a7828-114">즉, 별도의 코드 파일에서 사용자 지정 비즈니스 논리가 포함된 엔터티 클래스의 다른 부분을 사용자가 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-114">This means that, in a separate code file, you can define another part of the entity class that contains your custom business logic.</span></span> <span data-ttu-id="a7828-115">컴파일할 때 이 두 부분은 하나의 클래스로 병합됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-115">At compile time, the two parts are merged into a single class.</span></span> <span data-ttu-id="a7828-116">그러나 개체 관계형 디자이너 또는 SQLMetal을 사용 하 여 엔터티 클래스를 다시 생성 해야 하는 경우에는이 작업을 수행할 수 있습니다. 그러면 클래스의 일부가 수정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-116">But if you have to regenerate your entity classes by using the Object Relational Designer or SQLMetal, you can do so and your part of the class will not be modified.</span></span>  
  
 <span data-ttu-id="a7828-117">엔터티와 <xref:System.Data.Linq.DataContext>를 정의하는 부분 클래스에는 부분 메서드가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-117">The partial classes that define entities and the <xref:System.Data.Linq.DataContext> contain partial methods.</span></span> <span data-ttu-id="a7828-118">부분 메서드는 엔터티 또는 엔터티 속성을 업데이트, 삽입 또는 삭제하기 전과 후에 비즈니스 논리를 적용하는 데 사용할 수 있는 확장성 지점입니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-118">These are the extensibility points that you can use to apply your business logic before and after any update, insert, or delete for an entity or entity property.</span></span> <span data-ttu-id="a7828-119">부분 메서드는 컴파일 시간 이벤트 정도로 생각할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-119">Partial methods can be thought of as compile-time events.</span></span> <span data-ttu-id="a7828-120">코드 생성기에서는 메서드 시그니처를 정의하고 `DataContext` 생성자인 get/set 속성 접근자에서 메서드를 호출하며 경우에 따라 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>가 호출되면 메서드를 내부적으로 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-120">The code-generator defines a method signature and calls the methods in the get and set property accessors, the `DataContext` constructor, and in some cases behind the scenes when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="a7828-121">그러나 특정 부분 메서드를 구현하지 않으면 컴파일할 때 관련된 모든 참조 및 정의가 제거됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-121">However, if you do not implement a particular partial method, then all the references to it and the definition are removed at compile time.</span></span>  
  
 <span data-ttu-id="a7828-122">별도의 코드 파일에 작성하는 구현 정의에는 필요한 모든 사용자 지정 논리를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-122">In the implementing definition that you write in your separate code file, you can perform whatever custom logic is required.</span></span> <span data-ttu-id="a7828-123">부분 클래스 자체를 도메인 계층으로 사용하거나 부분 메서드의 구현 정의에서 별도의 개체로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-123">You can use your partial class itself as your domain layer, or you can call from your implementing definition of the partial method into a separate object or objects.</span></span> <span data-ttu-id="a7828-124">어느 방법을 사용하든 비즈니스 논리는 데이터 액세스 코드 및 프레젠테이션 계층 코드에서 완벽하게 분리됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-124">Either way, your business logic is cleanly separated from both your data access code and your presentation layer code.</span></span>  
  
## <a name="a-closer-look-at-the-extensibility-points"></a><span data-ttu-id="a7828-125">확장성 지점 자세히 보기</span><span class="sxs-lookup"><span data-stu-id="a7828-125">A Closer Look at the Extensibility Points</span></span>  

 <span data-ttu-id="a7828-126">다음 예제에서는 `DataContext` 두 개의 테이블 및를 포함 하는 클래스에 대 한 개체 관계형 디자이너에 의해 생성 된 코드의 일부를 보여 줍니다. `Customers` `Orders`</span><span class="sxs-lookup"><span data-stu-id="a7828-126">The following example shows part of the code generated by the Object Relational Designer for the `DataContext` class that has two tables: `Customers` and `Orders`.</span></span> <span data-ttu-id="a7828-127">이 코드에서는 클래스의 각 테이블에 대해 Insert, Update 및 Delete 메서드를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-127">Note that Insert, Update, and Delete methods are defined for each table in the class.</span></span>  
  
```vb  
Partial Public Class Northwnd  
    Inherits System.Data.Linq.DataContext  
  
    Private Shared mappingSource As _  
        System.Data.Linq.Mapping.MappingSource = New _  
        AttributeMappingSource  
  
    #Region "Extensibility Method Definitions"  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub InsertCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub UpdateCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub DeleteCustomer(instance As Customer)  
    End Sub  
    Partial Private Sub InsertOrder(instance As [Order])  
    End Sub  
    Partial Private Sub UpdateOrder(instance As [Order])  
    End Sub  
    Partial Private Sub DeleteOrder(instance As [Order])  
    End Sub  
    #End Region  
```  
  
```csharp  
public partial class MyNorthWindDataContext : System.Data.Linq.DataContext  
    {  
        private static System.Data.Linq.Mapping.MappingSource mappingSource = new AttributeMappingSource();  
  
        #region Extensibility Method Definitions  
        partial void OnCreated();  
        partial void InsertCustomer(Customer instance);  
        partial void UpdateCustomer(Customer instance);  
        partial void DeleteCustomer(Customer instance);  
        partial void InsertOrder(Order instance);  
        partial void UpdateOrder(Order instance);  
        partial void DeleteOrder(Order instance);  
        #endregion  
```  
  
 <span data-ttu-id="a7828-128">부분 클래스에 Insert, Update 및 Delete 메서드를 구현할 경우 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 런타임에서는 <xref:System.Data.Linq.DataContext.SubmitChanges%2A>가 호출되면 기본 메서드 대신 사용자가 구현한 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-128">If you implement the Insert, Update and Delete methods in your partial class, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime will call them instead of its own default methods when <xref:System.Data.Linq.DataContext.SubmitChanges%2A> is called.</span></span> <span data-ttu-id="a7828-129">이렇게 하면 만들기, 읽기, 업데이트 및 삭제 작업의 기본 동작을 재정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-129">This enables you to override the default behavior for create / read / update / delete operations.</span></span> <span data-ttu-id="a7828-130">자세한 내용은 [연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작 사용자 지정](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="a7828-130">For more information, see [Walkthrough: Customizing the insert, update, and delete behavior of entity classes](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes).</span></span>  
  
 <span data-ttu-id="a7828-131">`OnCreated` 메서드는 클래스 생성자에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-131">The `OnCreated` method is called in the class constructor.</span></span>  
  
```vb  
Public Sub New(ByVal connection As String)  
    MyBase.New(connection, mappingSource)  
    OnCreated()  
End Sub  
```  
  
```csharp  
public MyNorthWindDataContext(string connection) :  
            base(connection, mappingSource)  
        {  
            OnCreated();  
        }  
```  
  
 <span data-ttu-id="a7828-132">엔터티 클래스에는 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]가 호출되면 엔터티가 생성되고 로드되고 유효성이 검사될 때 `SubmitChanges` 런타임에서 호출하는 세 개의 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-132">The entity classes have three methods that are called by the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] runtime when the entity is created, loaded, and validated (when `SubmitChanges` is called).</span></span> <span data-ttu-id="a7828-133">또한 엔터티 클래스에는 각 속성에 대해 두 개의 부분 메서드, 즉 속성을 설정하기 전에 호출되는 부분 메서드와 속성을 설정한 후에 호출되는 부분 메서드가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-133">The entity classes also have two partial methods for each property, one that is called before the property is set, and one that is called after.</span></span> <span data-ttu-id="a7828-134">다음 코드 예제에서는 `Customer` 클래스에 대해 생성되는 몇 가지 메서드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-134">The following code example shows some of the methods generated for the `Customer` class:</span></span>  
  
```vb  
#Region "Extensibility Method Definitions"  
    Partial Private Sub OnLoaded()  
    End Sub  
    Partial Private Sub OnValidate(action As _  
        System.Data.Linq.ChangeAction)  
    End Sub  
    Partial Private Sub OnCreated()  
    End Sub  
    Partial Private Sub OnCustomerIDChanging(value As String)  
    End Sub  
    Partial Private Sub OnCustomerIDChanged()  
    End Sub  
    Partial Private Sub OnCompanyNameChanging(value As String)  
    End Sub  
    Partial Private Sub OnCompanyNameChanged()  
    End Sub  
' ...Additional Changing/Changed methods for each property.  
```  
  
```csharp  
#region Extensibility Method Definitions  
    partial void OnLoaded();  
    partial void OnValidate();  
    partial void OnCreated();  
    partial void OnCustomerIDChanging(string value);  
    partial void OnCustomerIDChanged();  
    partial void OnCompanyNameChanging(string value);  
    partial void OnCompanyNameChanged();  
// ...additional Changing/Changed methods for each property  
```  
  
 <span data-ttu-id="a7828-135">`CustomerID` 속성에 대한 다음 예제에서 볼 수 있는 것처럼 이러한 메서드는 set 속성 접근자에서 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-135">The methods are called in the property set accessor as shown in the following example for the `CustomerID` property:</span></span>  
  
```vb  
Public Property CustomerID() As String  
    Set  
        If (String.Equals(Me._CustomerID, value) = False) Then  
            Me.OnCustomerIDChanging(value)  
            Me.SendPropertyChanging()  
            Me._CustomerID = value  
            Me.SendPropertyChanged("CustomerID")  
            Me.OnCustomerIDChanged()  
        End If  
    End Set  
End Property  
```  
  
```csharp  
public string CustomerID  
{  
    set  
    {  
        if ((this._CustomerID != value))  
        {  
            this.OnCustomerIDChanging(value);  
            this.SendPropertyChanging();  
            this._CustomerID = value;  
            this.SendPropertyChanged("CustomerID");  
            this.OnCustomerIDChanged();  
        }  
     }  
}  
```  
  
 <span data-ttu-id="a7828-136">사용자가 작성하는 클래스 부분에 메서드의 구현 정의를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-136">In your part of the class, you write an implementing definition of the method.</span></span> <span data-ttu-id="a7828-137">Visual Studio에서를 입력 하면 `partial` 클래스의 다른 부분에 있는 메서드 정의에 대 한 IntelliSense가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a7828-137">In Visual Studio, after you type `partial` you will see IntelliSense for the method definitions in the other part of the class.</span></span>  
  
```vb  
Partial Public Class Customer  
    Private Sub OnCustomerIDChanging(value As String)  
        ' Perform custom validation logic here.  
    End Sub  
End Class  
```  
  
```csharp  
partial class Customer
    {  
        partial void OnCustomerIDChanging(string value)  
        {  
            //Perform custom validation logic here.  
        }  
    }  
```  
  
 <span data-ttu-id="a7828-138">부분 메서드를 사용하여 애플리케이션에 비즈니스 논리를 추가하는 방법에 대한 자세한 내용을 보려면 다음 항목을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a7828-138">For more information about how to add business logic to your application by using partial methods, see the following topics:</span></span>  
  
 [<span data-ttu-id="a7828-139">방법: 엔터티 클래스에 유효성 검사 추가</span><span class="sxs-lookup"><span data-stu-id="a7828-139">How to: Add validation to entity classes</span></span>](/visualstudio/data-tools/how-to-add-validation-to-entity-classes)  
  
 [<span data-ttu-id="a7828-140">연습: 엔터티 클래스의 삽입, 업데이트 및 삭제 동작을 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="a7828-140">Walkthrough: Customizing the insert, update, and delete behavior of entity classes</span></span>](/visualstudio/data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes)  
  
 <span data-ttu-id="a7828-141">[연습: 엔터티 클래스에 유효성 검사 추가](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="a7828-141">[Walkthrough: Adding Validation to Entity Classes](/previous-versions/visualstudio/visual-studio-2013/bb629301(v=vs.120))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7828-142">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a7828-142">See also</span></span>

- [<span data-ttu-id="a7828-143">Partial 클래스 및 메서드</span><span class="sxs-lookup"><span data-stu-id="a7828-143">Partial Classes and Methods</span></span>](../../../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md)
- [<span data-ttu-id="a7828-144">부분 메서드</span><span class="sxs-lookup"><span data-stu-id="a7828-144">Partial Methods</span></span>](../../../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
- <span data-ttu-id="a7828-145">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)(Visual Studio의 LINQ to SQL 도구)</span><span class="sxs-lookup"><span data-stu-id="a7828-145">[LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)</span></span>
- [<span data-ttu-id="a7828-146">SqlMetal.exe(코드 생성 도구)</span><span class="sxs-lookup"><span data-stu-id="a7828-146">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../tools/sqlmetal-exe-code-generation-tool.md)
