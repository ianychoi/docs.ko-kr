---
description: '에 대 한 자세한 정보: 개체 및 클래스 Visual Basic'
title: 개체 및 클래스
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9cefcc117c9dd4ac42940f342dbf75d8ddb4f41d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462726"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="6c6be-103">Visual Basic의 개체 및 클래스</span><span class="sxs-lookup"><span data-stu-id="6c6be-103">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="6c6be-104">*개체* 는 하나의 단위로 취급될 수 있는 코드 및 데이터의 조합입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-104">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="6c6be-105">개체는 컨트롤 또는 폼과 같은 애플리케이션의 부분일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-105">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="6c6be-106">전체 애플리케이션이 하나의 개체가 될 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-106">An entire application can also be an object.</span></span>

<span data-ttu-id="6c6be-107">Visual Basic에서 응용 프로그램을 만들 때 개체를 계속 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-107">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="6c6be-108">Visual Basic에서 제공 하는 개체 (예: 컨트롤, 폼 및 데이터 액세스 개체)를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-108">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="6c6be-109">Visual Basic 응용 프로그램 내에서 다른 응용 프로그램의 개체를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-109">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="6c6be-110">개체를 직접 만들고 해당 개체에 대해 추가 속성 및 메서드를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-110">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="6c6be-111">개체는 프로그램에 대한 조립식 빌딩 블록처럼 작동합니다. 즉, 코드 조각을 한 번 작성한 후 반복해서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-111">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="6c6be-112">이 항목에서는 개체에 대해 좀 더 자세히 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-112">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="6c6be-113">개체 및 클래스</span><span class="sxs-lookup"><span data-stu-id="6c6be-113">Objects and classes</span></span>

<span data-ttu-id="6c6be-114">Visual Basic의 각 개체는 *클래스* 에 의해 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-114">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="6c6be-115">클래스는 개체의 변수, 속성, 프로시저 및 이벤트를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-115">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="6c6be-116">개체는 클래스의 인스턴스입니다. 클래스를 정의한 후에는 필요한 수만큼 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-116">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="6c6be-117">개체와 해당 클래스 간의 관계를 이해하기 위해 쿠키 커터와 쿠키를 생각해 보세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-117">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="6c6be-118">쿠키 커터는 클래스입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-118">The cookie cutter is the class.</span></span> <span data-ttu-id="6c6be-119">각 쿠키에 대해 크기와 모양 같은 특징을 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-119">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="6c6be-120">클래스는 개체를 만드는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-120">The class is used to create objects.</span></span> <span data-ttu-id="6c6be-121">개체는 쿠키입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-121">The objects are the cookies.</span></span>

<span data-ttu-id="6c6be-122">[`Shared`](../../../language-reference/modifiers/shared.md)클래스의 개체 없이 액세스할 수 있는 멤버를 제외 하 고 개체의 멤버에 액세스 하려면 먼저 개체를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-122">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="6c6be-123">클래스에서 개체 만들기</span><span class="sxs-lookup"><span data-stu-id="6c6be-123">Create an object from a class</span></span>

1. <span data-ttu-id="6c6be-124">개체를 만들 클래스를 결정 하거나 고유한 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-124">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="6c6be-125">예를 들면 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-125">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="6c6be-126">클래스 인스턴스를 할당할 수 있는 변수를 만드는 [Dim 문](../../../language-reference/statements/dim-statement.md)을 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-126">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="6c6be-127">변수는 원하는 클래스의 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-127">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="6c6be-128">[New 연산자](../../../language-reference/operators/new-operator.md) 키워드를 추가하여 변수를 클래스의 새 인스턴스로 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-128">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="6c6be-129">이제 개체 변수를 통해 클래스의 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-129">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="6c6be-130">가능하면 항상 할당하려는 클래스 형식으로 변수를 선언해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-130">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="6c6be-131">이것을 *초기 바인딩* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-131">This is called *early binding*.</span></span> <span data-ttu-id="6c6be-132">컴파일 시간의 클래스 형식을 모르는 경우 변수를 [개체 데이터 형식](../../../language-reference/data-types/object-data-type.md)으로 선언하여 *런타임에 바인딩* 을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-132">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="6c6be-133">그러나 런타임에 바인딩을 사용하면 성능이 저하되고 런타임 개체 멤버에 대한 액세스가 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-133">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="6c6be-134">자세한 내용은 [개체 변수 선언](../variables/object-variable-declaration.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-134">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="6c6be-135">여러 인스턴스</span><span class="sxs-lookup"><span data-stu-id="6c6be-135">Multiple instances</span></span>

<span data-ttu-id="6c6be-136">클래스에서 새로 만든 개체들이 서로 동일한 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-136">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="6c6be-137">그렇지만 개별 개체로 존재할 경우 다른 인스턴스와 독립적으로 해당 변수 및 속성을 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-137">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="6c6be-138">예를 들어 양식에 세 개의 확인란을 추가하는 경우 각 확인란 개체는 <xref:System.Windows.Forms.CheckBox> 클래스의 인스턴스입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-138">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="6c6be-139">개별 <xref:System.Windows.Forms.CheckBox> 개체는 클래스가 정의하는 공통된 특징 및 기능(속성, 변수, 프로시저 및 이벤트) 집합을 공유합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-139">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="6c6be-140">그러나 각각은 고유한 이름을 가지며, 개별적으로 사용하거나 사용하지 않도록 설정하고, 폼의 다른 위치에 배치할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-140">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="6c6be-141">개체 멤버</span><span class="sxs-lookup"><span data-stu-id="6c6be-141">Object members</span></span>

<span data-ttu-id="6c6be-142">개체는 애플리케이션의 요소로, 클래스의 *인스턴스* 를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-142">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="6c6be-143">필드, 속성, 메서드 및 이벤트는 개체의 구성 요소이며 해당 *멤버* 로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-143">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="6c6be-144">멤버 액세스</span><span class="sxs-lookup"><span data-stu-id="6c6be-144">Member Access</span></span>

<span data-ttu-id="6c6be-145">개체 변수의 이름, 마침표 (`.`) 및 멤버 이름을 순서대로 지정하여 개체 멤버에 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-145">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="6c6be-146">다음 예제에서는 <xref:System.Windows.Forms.Control.Text%2A> 개체의 <xref:System.Windows.Forms.Label> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-146">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="6c6be-147">IntelliSense 멤버 목록</span><span class="sxs-lookup"><span data-stu-id="6c6be-147">IntelliSense listing of members</span></span>

<span data-ttu-id="6c6be-148">IntelliSense는 멤버 나열 옵션을 호출할 때(예를 들어 멤버 액세스 연산자로 마침표(`.`)를 입력할 때) 클래스의 멤버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-148">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="6c6be-149">해당 클래스의 인스턴스로 선언된 변수 이름 뒤에 마침표를 입력하는 경우 IntelliSense는 공유 멤버가 아닌 모든 인스턴스 멤버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-149">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="6c6be-150">클래스 이름 뒤에 마침표를 입력하는 경우 IntelliSense는 인스턴스 멤버가 아닌 모든 공유 멤버를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-150">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="6c6be-151">자세한 내용은 [Using IntelliSense](/visualstudio/ide/using-intellisense)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-151">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="6c6be-152">필드 및 속성</span><span class="sxs-lookup"><span data-stu-id="6c6be-152">Fields and properties</span></span>

<span data-ttu-id="6c6be-153">*필드* 및 *속성* 은 개체에 저장된 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-153">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="6c6be-154">프로시저에서 지역 변수를 검색하고 설정하는 것과 동일한 방식으로 대입문을 사용하여 해당 값을 검색하고 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-154">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="6c6be-155">다음 예제에서는 <xref:System.Windows.Forms.Control.Width%2A> 속성을 검색하고 <xref:System.Windows.Forms.Label> 개체의 <xref:System.Windows.Forms.Control.ForeColor%2A> 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-155">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="6c6be-156">필드를 *멤버 변수* 라고도 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-156">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="6c6be-157">다음 경우에 Property 프로시저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-157">Use property procedures when:</span></span>

- <span data-ttu-id="6c6be-158">값을 설정하거나 검색할 시기와 방법을 제어해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-158">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="6c6be-159">속성에는 유효성을 검사해야 하는 잘 정의된 값 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-159">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="6c6be-160">값을 설정하면 `IsVisible` 속성과 같은 개체의 상태가 획기적으로 변경될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-160">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="6c6be-161">속성을 설정하면 다른 내부 변수 또는 다른 속성의 값이 변경됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-161">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="6c6be-162">속성을 설정하거나 검색하려면 먼저 일련의 단계를 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-162">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="6c6be-163">다음 경우에 필드를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-163">Use fields when:</span></span>

- <span data-ttu-id="6c6be-164">값이 자체적으로 유효성을 검사하는 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-164">The value is of a self-validating type.</span></span> <span data-ttu-id="6c6be-165">예를 들어 `True` 또는 `False` 이외의 값이 `Boolean` 변수에 할당되면 오류 또는 자동 데이터 변환이 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-165">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="6c6be-166">데이터 형식이 지원하는 범위의 모든 값이 유효합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-166">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="6c6be-167">`Single` 또는 `Double` 형식의 많은 속성이 여기에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-167">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="6c6be-168">속성이 `String` 데이터 형식이고 문자열 크기 또는 값에 제약이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-168">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="6c6be-169">자세한 내용은 [Property 프로시저](../procedures/property-procedures.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-169">For more information, see [Property Procedures](../procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="6c6be-170">상수가 아닌 필드는 항상 private으로 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-170">Always keep the non-constant fields private.</span></span> <span data-ttu-id="6c6be-171">이를 공용으로 설정 하려면 대신 속성을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-171">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="6c6be-172">메서드</span><span class="sxs-lookup"><span data-stu-id="6c6be-172">Methods</span></span>

<span data-ttu-id="6c6be-173">*메서드* 는 개체에서 수행할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-173">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="6c6be-174">예를 들어 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>는 콤보 상자에 새 항목을 추가하는 <xref:System.Windows.Forms.ComboBox> 개체의 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-174">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="6c6be-175">다음 예제에서는 <xref:System.Windows.Forms.Timer> 개체의 <xref:System.Windows.Forms.Timer.Start%2A> 메서드를 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-175">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="6c6be-176">메서드는 개체에 의해 노출되는 *프로시저* 일 뿐입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-176">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="6c6be-177">자세한 내용은 [프로시저](../procedures/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-177">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="6c6be-178">이벤트</span><span class="sxs-lookup"><span data-stu-id="6c6be-178">Events</span></span>

<span data-ttu-id="6c6be-179">이벤트는 마우스 클릭이나 키 누르기와 같이 개체가 인식하는 동작이며 응답하기 위해 코드를 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-179">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="6c6be-180">이벤트는 사용자 동작 또는 프로그램 코드의 결과로 발생하거나 시스템에 의해 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-180">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="6c6be-181">이벤트에 신호를 보내는 코드를 이벤트 *발생* 이라고 하고, 신호에 응답하는 코드를 *처리* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-181">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="6c6be-182">개체에 의해 발생하고 다른 개체에서 처리되는 사용자 지정 이벤트를 개발할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-182">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="6c6be-183">자세한 내용은 [이벤트](../events/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-183">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="6c6be-184">인스턴스 멤버 및 공유 멤버</span><span class="sxs-lookup"><span data-stu-id="6c6be-184">Instance members and shared members</span></span>

<span data-ttu-id="6c6be-185">클래스에서 개체를 만들 때 결과는 해당 클래스의 인스턴스가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-185">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="6c6be-186">[Shared](../../../language-reference/modifiers/shared.md) 키워드로 선언되지 않은 멤버는 해당 특정 인스턴스에 반드시 속하는 *인스턴스 멤버* 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-186">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="6c6be-187">한 인스턴스의 인스턴스 멤버는 동일한 클래스의 다른 인스턴스에 있는 동일한 멤버와 무관합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-187">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="6c6be-188">예를 들어 인스턴스 멤버 변수는 서로 다른 인스턴스에서 다른 값을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-188">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="6c6be-189">`Shared` 키워드로 선언된 멤버는 특정 인스턴스가 아니라 전체 클래스에 속하는 *공유 멤버* 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-189">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="6c6be-190">공유 멤버는 사용자가 만드는 클래스의 인스턴스 수에 관계 없이, 사용자가 인스턴스를 만들지 않더라도 한 번만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-190">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="6c6be-191">예를 들어 공유 멤버 변수는 클래스에 액세스할 수 있는 모든 코드에서 사용할 수 있는 하나의 값만 갖습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-191">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="6c6be-192">비공유 멤버 액세스</span><span class="sxs-lookup"><span data-stu-id="6c6be-192">Accessing non-shared members</span></span>

1. <span data-ttu-id="6c6be-193">개체가 해당 클래스에서 생성되고 개체 변수에 할당되어 있는지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-193">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="6c6be-194">멤버에 액세스 하는 문에서 개체 변수 이름 뒤에 *멤버 액세스 연산자* ( `.` )와 멤버 이름을 차례로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-194">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="6c6be-195">공유 멤버 액세스</span><span class="sxs-lookup"><span data-stu-id="6c6be-195">Accessing shared members</span></span>

- <span data-ttu-id="6c6be-196">클래스 이름 뒤에 *멤버 액세스 연산자* ( `.` )와 멤버 이름을 차례로 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-196">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="6c6be-197">항상 클래스 이름을 통해 직접적으로 개체의 `Shared` 멤버에 액세스해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-197">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="6c6be-198">클래스에서 개체를 이미 만들었으면 개체의 변수를 통해 `Shared` 멤버에 액세스할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-198">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="6c6be-199">클래스와 모듈 간의 차이점</span><span class="sxs-lookup"><span data-stu-id="6c6be-199">Differences between classes and modules</span></span>

<span data-ttu-id="6c6be-200">클래스와 모듈 간의 주요 차이점은 클래스는 개체로 인스턴스화할 수 있지만 표준 모듈은 그럴 수 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-200">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="6c6be-201">표준 모듈의 데이터 복사본은 하나만 있으므로 프로그램의 한 부분이 표준 모듈의 공용 변수를 변경하면 프로그램의 다른 부분은 해당 변수를 읽을 때 동일한 값을 얻습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-201">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="6c6be-202">반면 개체 데이터는 인스턴스화된 각 개체에 대해 개별적으로 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-202">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="6c6be-203">또 다른 차이점은 표준 모듈과 달리 클래스는 인터페이스를 구현할 수 있다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-203">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="6c6be-204">클래스가 [MustInherit](../../../language-reference/modifiers/mustinherit.md) 한정자로 표시 된 경우 직접 인스턴스화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-204">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="6c6be-205">그러나 모듈은 상속 될 수 있지만 모듈은 상속 될 수 없으므로 모듈에서 여전히 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-205">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="6c6be-206">`Shared` 한정자가 클래스 멤버에 적용되면 클래스의 특정 인스턴스가 아닌 클래스 자체에 연결됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-206">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="6c6be-207">모듈 멤버에 액세스하는 것과 같은 방식으로 멤버에도 클래스 이름을 사용하여 직접 액세스합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-207">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="6c6be-208">클래스와 모듈은 또한 해당 멤버의 범위가 각기 다를 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-208">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="6c6be-209">클래스 내에 정의된 멤버는 클래스의 특정 인스턴스 범위를 벗어나지 않으며 개체의 수명 동안만 존재합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-209">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="6c6be-210">클래스 외부에서 클래스 멤버에 액세스하려면 *개체*.*멤버* 형식의 정규화된 이름을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-210">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="6c6be-211">반면에 모듈 내에서 선언된 멤버는 기본적으로 공개적으로 액세스할 수 있으며 모듈에 액세스할 수 있는 모든 코드에서 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-211">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="6c6be-212">즉, 표준 모듈의 변수는 프로젝트의 모든 위치에서 볼 수 있으며 프로그램의 수명 동안 존재하기 때문에 결과적으로 전역 변수에 해당합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-212">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="6c6be-213">클래스 및 개체 다시 사용</span><span class="sxs-lookup"><span data-stu-id="6c6be-213">Reusing classes and objects</span></span>

<span data-ttu-id="6c6be-214">개체를 사용하면 변수 및 프로시저를 한 번 선언한 후 필요할 때마다 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-214">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="6c6be-215">예를 들어 애플리케이션에 맞춤법 검사기를 추가하려는 경우 모든 변수 및 지원 함수를 정의하여 맞춤법 검사 기능을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-215">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="6c6be-216">맞춤법 검사기를 클래스로 만드는 경우 컴파일된 어셈블리에 대한 참조를 추가하여 다른 애플리케이션에서 다시 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-216">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="6c6be-217">다른 사람이 이미 개발한 맞춤법 검사기 클래스를 사용하여 일부 작업을 줄일 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-217">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="6c6be-218">.NET은 사용할 수 있는 구성 요소에 대 한 많은 예를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-218">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="6c6be-219">다음 예제에서는 <xref:System> 네임스페이스의 <xref:System.TimeZone> 클래스를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-219">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="6c6be-220"><xref:System.TimeZone>에서는 현재 컴퓨터 시스템의 표준 시간대에 대한 정보를 검색할 수 있도록 하는 멤버를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-220"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="6c6be-221">앞의 예제에서 첫 번째 [Dim 문](../../../language-reference/statements/dim-statement.md)은 <xref:System.TimeZone> 형식의 개체 변수를 선언하고 이를 <xref:System.TimeZone.CurrentTimeZone%2A> 속성에 의해 반환된 <xref:System.TimeZone> 개체에 할당합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-221">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="6c6be-222">개체 간 관계</span><span class="sxs-lookup"><span data-stu-id="6c6be-222">Relationships among objects</span></span>

<span data-ttu-id="6c6be-223">개체는 여러 가지 방법으로 서로 관련될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-223">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="6c6be-224">관계의 주요 종류로는 *계층적* 및 *포함* 이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-224">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="6c6be-225">계층적 관계</span><span class="sxs-lookup"><span data-stu-id="6c6be-225">Hierarchical relationship</span></span>

<span data-ttu-id="6c6be-226">클래스가 보다 기본적인 클래스에서 파생되면 *계층적 관계* 에 있다고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-226">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="6c6be-227">클래스 계층 구조는 보다 일반적인 클래스의 하위 항목을 설명하는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-227">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="6c6be-228">다음 예제에서는 일반적인 <xref:System.Windows.Forms.Button>처럼 작동하지만 전경색 및 배경색을 거꾸로 뒤집는 메서드도 제공하는 특수한 종류의 <xref:System.Windows.Forms.Button>을 정의하려 한다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-228">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="6c6be-229">이미 존재 하는 클래스에서 파생 된 클래스를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-229">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="6c6be-230">[Class 문](../../../language-reference/statements/class-statement.md)을 사용하여 필요한 개체를 만들 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-230">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="6c6be-231">`End Class` 문은 클래스의 마지막 코드 줄 다음에 나옵니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-231">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="6c6be-232">기본적으로 IDE(통합 개발 환경)는 사용자가 `Class` 문을 입력하면 `End Class`를 자동으로 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-232">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="6c6be-233">`Class` 문 바로 다음에 [Inherits 문](../../../language-reference/statements/inherits-statement.md)을 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-233">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="6c6be-234">새 클래스가 파생되는 클래스를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-234">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="6c6be-235">새 클래스는 기본 클래스에서 정의하는 모든 멤버를 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-235">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="6c6be-236">파생 클래스가 노출하는 추가 멤버에 대한 코드를 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-236">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="6c6be-237">예를 들어 `ReverseColors` 메서드를 추가할 수 있으며 이 경우 파생 클래스는 다음과 같이 표시될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-237">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="6c6be-238">클래스에서 개체를 만드는 경우 `ReversibleButton` 클래스의 모든 멤버 뿐만 아니라 <xref:System.Windows.Forms.Button> `ReverseColors` 메서드 및에서 정의 하는 다른 모든 새 멤버에 액세스할 수 있습니다 `ReversibleButton` .</span><span class="sxs-lookup"><span data-stu-id="6c6be-238">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="6c6be-239">파생 클래스는 해당 클래스의 기준이 되는 클래스에서 멤버를 상속하므로 클래스 계층 구조가 점점 복잡해질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-239">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="6c6be-240">자세한 내용은 [상속 기본 사항](inheritance-basics.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-240">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="6c6be-241">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="6c6be-241">Compile the code</span></span>

<span data-ttu-id="6c6be-242">컴파일러에서 새 클래스를 파생하려는 원본 클래스에 액세스할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-242">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="6c6be-243">이것은 이름을 완전히 한정하거나 앞의 예제에서와 같이 [Imports 문(.NET 네임스페이스 및 형식)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)에서 해당 네임스페이스를 식별하는 것을 의미할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-243">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="6c6be-244">클래스가 다른 프로젝트에 있으면 해당 프로젝트에 대한 참조를 추가해야 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-244">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="6c6be-245">자세한 내용은 [프로젝트의 참조 관리](/visualstudio/ide/managing-references-in-a-project)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6c6be-245">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="6c6be-246">포함 관계</span><span class="sxs-lookup"><span data-stu-id="6c6be-246">Containment relationship</span></span>

<span data-ttu-id="6c6be-247">개체를 연관지을 수 있는 또 다른 방법은 *포함 관계* 입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-247">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="6c6be-248">컨테이너 개체는 논리적으로 다른 개체를 캡슐화합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-248">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="6c6be-249">예를 들어 <xref:System.OperatingSystem> 개체에 논리적으로 <xref:System.Version> 개체를 포함하며, 이는 해당 <xref:System.OperatingSystem.Version%2A> 속성을 통해 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-249">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="6c6be-250">컨테이너 개체가 다른 개체를 물리적으로 포함하는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-250">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="6c6be-251">컬렉션</span><span class="sxs-lookup"><span data-stu-id="6c6be-251">Collections</span></span>

<span data-ttu-id="6c6be-252">특정 형식의 개체 포함을 *컬렉션* 으로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-252">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="6c6be-253">컬렉션은 열거할 수 있는 유사한 개체의 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-253">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="6c6be-254">Visual Basic는 [For Each ... ](../../../language-reference/statements/for-each-next-statement.md) 컬렉션의 항목을 반복 하는 데 사용할 수 있는 다음 문입니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-254">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="6c6be-255">또한 컬렉션을 사용하면<xref:Microsoft.VisualBasic.Collection.Item%2A>을 사용하여 인덱스별로 또는 고유 문자열에 연결하여 요소를 검색할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-255">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="6c6be-256">컬렉션은 인덱스를 사용하지 않고도 항목을 추가 또는 제거할 수 있도록 하므로 배열보다 더 쉽게 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-256">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="6c6be-257">사용 편의성 때문에 컬렉션을 폼 및 컨트롤을 저장하는 데 종종 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-257">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="6c6be-258">관련 항목</span><span class="sxs-lookup"><span data-stu-id="6c6be-258">Related topics</span></span>

<span data-ttu-id="6c6be-259">[연습: 클래스 정의](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-259">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="6c6be-260">클래스를 만드는 방법에 대한 단계별 설명을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-260">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="6c6be-261">[오버 로드 된 속성 및 메서드](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-261">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="6c6be-262">오버로드된 속성 및 메서드</span><span class="sxs-lookup"><span data-stu-id="6c6be-262">Overloaded Properties and Methods</span></span>

<span data-ttu-id="6c6be-263">[상속 기본 사항](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-263">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="6c6be-264">상속 한정자, 메서드 및 속성 재정의, MyClass 및 MyBase에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-264">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="6c6be-265">[개체 수명: 개체가 만들어지고 제거 되는 방법](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-265">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="6c6be-266">클래스 인스턴스의 생성 및 삭제에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-266">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="6c6be-267">[익명 형식](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-267">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="6c6be-268">익명 형식을 만들고 사용하여 데이터 형식에 대한 클래스 정의를 작성하지 않고 개체를 만들 수 있는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-268">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="6c6be-269">[개체 이니셜라이저: 명명 된 형식과 익명 형식](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-269">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="6c6be-270">단일 식을 사용하여 명명된 형식 및 무명 형식의 인스턴스를 만드는 데 사용되는 개체 이니셜라이저에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-270">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="6c6be-271">[방법: 익명 형식 선언에서 속성 이름 및 형식 유추](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="6c6be-271">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="6c6be-272">무명 형식 선언에서 속성 이름 및 형식을 유추하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-272">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="6c6be-273">성공 및 실패한 유추의 예제를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6c6be-273">Provides examples of successful and unsuccessful inference.</span></span>
