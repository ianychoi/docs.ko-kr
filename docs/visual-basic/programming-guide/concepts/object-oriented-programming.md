---
description: '자세한 정보: 개체 지향 프로그래밍 (Visual Basic)'
title: 개체 지향 프로그래밍
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: af2fbac16bfefc90876bf22bb8c67de162ee6459
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100486799"
---
# <a name="object-oriented-programming-visual-basic"></a><span data-ttu-id="e6b50-103">개체 지향 프로그래밍 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6b50-103">Object-oriented programming (Visual Basic)</span></span>

<span data-ttu-id="e6b50-104">Visual Basic은 캡슐화, 상속 및 다형성을 포함 하는 개체 지향 프로그래밍에 대 한 완전 한 지원을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-104">Visual Basic provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

 <span data-ttu-id="e6b50-105">*캡슐화* 는 서로 관련된 속성, 메서드 및 기타 멤버의 그룹을 하나의 단위나 개체로 취급하는 것을 말합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-105">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

 <span data-ttu-id="e6b50-106">*상속* 은 기존 클래스를 기반으로 새로운 클래스를 만들 수 있는 능력을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-106">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

 <span data-ttu-id="e6b50-107">*다형성* 은 동일한 속성 또는 메서드를 각각 다른 방식으로 구현하는 여러 클래스를 서로 교체하여 사용할 수 있음을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-107">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

 <span data-ttu-id="e6b50-108">이 단원에서는 다음과 같은 개념에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-108">This section describes the following concepts:</span></span>

- [<span data-ttu-id="e6b50-109">클래스 및 개체</span><span class="sxs-lookup"><span data-stu-id="e6b50-109">Classes and objects</span></span>](#classes-and-objects)
  - [<span data-ttu-id="e6b50-110">클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="e6b50-110">Class members</span></span>](#class-members)
    - [<span data-ttu-id="e6b50-111">속성 및 필드</span><span class="sxs-lookup"><span data-stu-id="e6b50-111">Properties and fields</span></span>](#properties-and-fields)
    - [<span data-ttu-id="e6b50-112">메서드</span><span class="sxs-lookup"><span data-stu-id="e6b50-112">Methods</span></span>](#methods)
    - [<span data-ttu-id="e6b50-113">생성자</span><span class="sxs-lookup"><span data-stu-id="e6b50-113">Constructors</span></span>](#constructors)
    - [<span data-ttu-id="e6b50-114">소멸자</span><span class="sxs-lookup"><span data-stu-id="e6b50-114">Destructors</span></span>](#destructors)
    - [<span data-ttu-id="e6b50-115">이벤트</span><span class="sxs-lookup"><span data-stu-id="e6b50-115">Events</span></span>](#events)
    - [<span data-ttu-id="e6b50-116">중첩 클래스</span><span class="sxs-lookup"><span data-stu-id="e6b50-116">Nested classes</span></span>](#nested-classes)
  - [<span data-ttu-id="e6b50-117">액세스 한정자 및 액세스 수준</span><span class="sxs-lookup"><span data-stu-id="e6b50-117">Access modifiers and access levels</span></span>](#access-modifiers-and-access-levels)
    - [<span data-ttu-id="e6b50-118">클래스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="e6b50-118">Instantiating classes</span></span>](#instantiating-classes)
    - [<span data-ttu-id="e6b50-119">공유 클래스 및 멤버</span><span class="sxs-lookup"><span data-stu-id="e6b50-119">Shared classes and members</span></span>](#shared-classes-and-members)
    - [<span data-ttu-id="e6b50-120">무명 형식</span><span class="sxs-lookup"><span data-stu-id="e6b50-120">Anonymous types</span></span>](#anonymous-types)
- [<span data-ttu-id="e6b50-121">상속</span><span class="sxs-lookup"><span data-stu-id="e6b50-121">Inheritance</span></span>](#inheritance)
  - [<span data-ttu-id="e6b50-122">멤버 재정의</span><span class="sxs-lookup"><span data-stu-id="e6b50-122">Overriding members</span></span>](#overriding-members)
- [<span data-ttu-id="e6b50-123">인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6b50-123">Interfaces</span></span>](#interfaces)
- [<span data-ttu-id="e6b50-124">제네릭</span><span class="sxs-lookup"><span data-stu-id="e6b50-124">Generics</span></span>](#generics)
- [<span data-ttu-id="e6b50-125">대리자</span><span class="sxs-lookup"><span data-stu-id="e6b50-125">Delegates</span></span>](#delegates)

## <a name="classes-and-objects"></a><span data-ttu-id="e6b50-126">클래스 및 개체</span><span class="sxs-lookup"><span data-stu-id="e6b50-126">Classes and objects</span></span>

<span data-ttu-id="e6b50-127">*클래스* 와 *개체* 를 혼용하는 경우가 있지만 클래스는 개체의 *형식* 을 나타내고 개체는 사용 가능한 클래스의 *인스턴스* 를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-127">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="e6b50-128">따라서 개체를 만드는 작업을 *인스턴스화* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-128">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="e6b50-129">청사진에 비유한다면 클래스는 청사진이고 개체는 해당 청사진을 사용하여 만든 빌딩입니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-129">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="e6b50-130">클래스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-130">To define a class:</span></span>

```vb
Class SampleClass
End Class
```

<span data-ttu-id="e6b50-131">또한 Visual Basic는 큰 개체 배열을 만들어야 하 고 해당 개체에 너무 많은 메모리를 사용 하지 않으려는 경우에 유용 하 게 사용 되는 *구조체* 라는 클래스의 light 버전을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-131">Visual Basic also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="e6b50-132">구조체를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-132">To define a structure:</span></span>

```vb
Structure SampleStructure
End Structure
```

<span data-ttu-id="e6b50-133">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-133">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-134">Class 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-134">Class Statement</span></span>](../../language-reference/statements/class-statement.md)
- [<span data-ttu-id="e6b50-135">Structure 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-135">Structure Statement</span></span>](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a><span data-ttu-id="e6b50-136">클래스 멤버</span><span class="sxs-lookup"><span data-stu-id="e6b50-136">Class members</span></span>

<span data-ttu-id="e6b50-137">각 클래스에는 클래스 데이터를 설명하는 속성, 클래스 동작을 정의하는 메서드 및 서로 다른 클래스와 개체 간의 통신을 제공하는 이벤트가 포함된 다양한 *클래스 멤버* 가 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-137">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="properties-and-fields"></a><span data-ttu-id="e6b50-138">속성 및 필드</span><span class="sxs-lookup"><span data-stu-id="e6b50-138">Properties and fields</span></span>

<span data-ttu-id="e6b50-139">필드 및 속성은 개체가 포함하는 정보를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-139">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="e6b50-140">필드는 직접 읽거나 설정할 수 있기 때문에 변수와 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-140">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="e6b50-141">필드를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-141">To define a field:</span></span>

```vb
Class SampleClass
    Public SampleField As String
End Class
```

<span data-ttu-id="e6b50-142">속성에는 값을 설정하고 가져오는 방법을 보다 세밀하게 제어할 수 있는 get 및 set 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-142">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="e6b50-143">Visual Basic를 사용 하면 속성 값을 저장 하기 위한 전용 필드를 만들거나이 필드를 내부적으로 자동으로 만들고 속성 프로시저에 대 한 기본 논리를 제공 하는 자동 구현 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-143">Visual Basic allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="e6b50-144">자동 구현 속성을 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-144">To define an auto-implemented property:</span></span>

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

<span data-ttu-id="e6b50-145">속성 값을 읽고 쓰기 위해 몇 가지 추가 작업을 수행해야 하는 경우 다음과 같이 속성 값을 저장하기 위한 필드를 정의하고, 속성 값을 저장 및 검색하기 위한 기본 논리를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-145">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

<span data-ttu-id="e6b50-146">대부분의 속성에는 속성 값을 설정하고 가져오는 메서드나 프로시저가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-146">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="e6b50-147">그러나 읽기 전용 또는 쓰기 전용 속성을 만들어 속성을 수정하거나 읽지 못하도록 제한할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-147">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="e6b50-148">이렇게 하려면 Visual Basic에서는 `ReadOnly` 및 `WriteOnly` 키워드를 사용하면 되고</span><span class="sxs-lookup"><span data-stu-id="e6b50-148">In Visual Basic you can use `ReadOnly` and `WriteOnly` keywords.</span></span> <span data-ttu-id="e6b50-149">하지만 자동 구현 속성은 읽기 전용 또는 쓰기 전용일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-149">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="e6b50-150">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-150">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-151">Property Statement</span><span class="sxs-lookup"><span data-stu-id="e6b50-151">Property Statement</span></span>](../../language-reference/statements/property-statement.md)
- [<span data-ttu-id="e6b50-152">Get 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-152">Get Statement</span></span>](../../language-reference/statements/get-statement.md)
- [<span data-ttu-id="e6b50-153">Set 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-153">Set Statement</span></span>](../../language-reference/statements/set-statement.md)
- [<span data-ttu-id="e6b50-154">읽기 전용</span><span class="sxs-lookup"><span data-stu-id="e6b50-154">ReadOnly</span></span>](../../language-reference/modifiers/readonly.md)
- [<span data-ttu-id="e6b50-155">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="e6b50-155">WriteOnly</span></span>](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a><span data-ttu-id="e6b50-156">메서드</span><span class="sxs-lookup"><span data-stu-id="e6b50-156">Methods</span></span>

 <span data-ttu-id="e6b50-157">*메서드* 는 개체에서 수행할 수 있는 작업입니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-157">A *method* is an action that an object can perform.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b50-158">Visual Basic에서는 두 가지 방법으로 메서드를 만들 수 있습니다. 메서드가 값을 반환하지 않으면 `Sub` 문을 사용하고 메서드가 값을 반환하면 `Function` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-158">In Visual Basic, there are two ways to create a method: the `Sub` statement is used if the method does not return a value; the `Function` statement is used if a method returns a value.</span></span>

<span data-ttu-id="e6b50-159">클래스의 메서드를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-159">To define a method of a class:</span></span>

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

<span data-ttu-id="e6b50-160">클래스에는 매개 변수 개수나 매개 변수 형식이 다른 동일한 메서드의 구현 또는 *오버로드* 가 여러 개 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-160">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="e6b50-161">메서드를 오버로드하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-161">To overload a method:</span></span>

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

<span data-ttu-id="e6b50-162">대부분의 경우 클래스 정의 내에서 메서드를 선언하지만</span><span class="sxs-lookup"><span data-stu-id="e6b50-162">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="e6b50-163">그러나 Visual Basic는 클래스의 실제 정의 밖에 있는 기존 클래스에 메서드를 추가할 수 있는 *확장 메서드도* 지원 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-163">However, Visual Basic also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="e6b50-164">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-164">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-165">Function 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-165">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="e6b50-166">Sub 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-166">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="e6b50-167">오버로드</span><span class="sxs-lookup"><span data-stu-id="e6b50-167">Overloads</span></span>](../../language-reference/modifiers/overloads.md)
- [<span data-ttu-id="e6b50-168">확장명 메서드</span><span class="sxs-lookup"><span data-stu-id="e6b50-168">Extension Methods</span></span>](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a><span data-ttu-id="e6b50-169">생성자</span><span class="sxs-lookup"><span data-stu-id="e6b50-169">Constructors</span></span>

<span data-ttu-id="e6b50-170">생성자는 지정된 형식의 개체를 만들 때 자동으로 실행되는 클래스 메서드로,</span><span class="sxs-lookup"><span data-stu-id="e6b50-170">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="e6b50-171">일반적으로 새 개체의 데이터 멤버를 초기화합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-171">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="e6b50-172">생성자는 클래스를 만들 때 한 번만 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-172">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="e6b50-173">또한 생성자의 코드는 항상 클래스의 다른 코드보다 먼저 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-173">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="e6b50-174">그러나 다른 메서드를 만들 때와 동일한 방법으로 여러 생성자 오버로드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-174">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="e6b50-175">클래스의 생성자를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-175">To define a constructor for a class:</span></span>

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

<span data-ttu-id="e6b50-176">자세한 내용은 [개체 수명: 개체가 만들어지고 소멸 되는 방법](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-176">For more information, see: [Object Lifetime: How Objects Are Created and Destroyed](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

#### <a name="destructors"></a><span data-ttu-id="e6b50-177">소멸자</span><span class="sxs-lookup"><span data-stu-id="e6b50-177">Destructors</span></span>

<span data-ttu-id="e6b50-178">소멸자는 클래스의 인스턴스를 소멸하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-178">Destructors are used to destruct instances of classes.</span></span> <span data-ttu-id="e6b50-179">.NET Framework에서는 애플리케이션의 관리되는 개체에 대해 가비지 수집기가 자동으로 메모리를 할당하고 해제하지만</span><span class="sxs-lookup"><span data-stu-id="e6b50-179">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="e6b50-180">애플리케이션에서 만들어지는 관리되지 않는 개체를 정리하려면 여전히 소멸자가 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-180">However, you may still need destructors to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="e6b50-181">각 클래스에는 소멸자가 하나씩만 있을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-181">There can be only one destructor for a class.</span></span>

<span data-ttu-id="e6b50-182">.NET Framework의 소멸자 및 가비지 수집에 대한 자세한 내용은 [가비지 수집](../../../standard/garbage-collection/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-182">For more information about destructors and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="events"></a><span data-ttu-id="e6b50-183">이벤트</span><span class="sxs-lookup"><span data-stu-id="e6b50-183">Events</span></span>

<span data-ttu-id="e6b50-184">클래스나 개체에서는 특정 상황이 발생할 때 이벤트를 통해 다른 클래스나 개체에 이를 알려 줄 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-184">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="e6b50-185">이벤트를 보내거나 발생시키는 클래스를 *게시자* 라고 하며 이벤트를 받거나 처리하는 클래스를 *구독자* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-185">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="e6b50-186">이벤트를 발생시키고 처리하는 방법에 대한 자세한 내용은 [이벤트](../../../standard/events/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-186">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="e6b50-187">이벤트를 선언 하려면 [이벤트 문을](../../language-reference/statements/event-statement.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-187">To declare events, use the [Event Statement](../../language-reference/statements/event-statement.md).</span></span>

- <span data-ttu-id="e6b50-188">이벤트를 발생 시키려면 [RaiseEvent 문을](../../language-reference/statements/raiseevent-statement.md)사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-188">To raise events, use the [RaiseEvent Statement](../../language-reference/statements/raiseevent-statement.md).</span></span>

- <span data-ttu-id="e6b50-189">선언적 방법을 사용 하 여 이벤트 처리기를 지정 하려면 [WithEvents](../../language-reference/modifiers/withevents.md) 문과 [Handles](../../language-reference/statements/handles-clause.md) 절을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-189">To specify event handlers using a declarative way, use the [WithEvents](../../language-reference/modifiers/withevents.md) statement and the [Handles](../../language-reference/statements/handles-clause.md) clause.</span></span>

- <span data-ttu-id="e6b50-190">이벤트와 연결 된 이벤트 처리기를 동적으로 추가, 제거 및 변경할 수 있으려면 AddressOf [문과](../../language-reference/statements/addhandler-statement.md) [RemoveHandler 문을](../../language-reference/statements/removehandler-statement.md) [AddressOf 연산자](../../language-reference/operators/addressof-operator.md)와 함께 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-190">To be able to dynamically add, remove, and change the event handler associated with an event, use the [AddHandler Statement](../../language-reference/statements/addhandler-statement.md) and [RemoveHandler Statement](../../language-reference/statements/removehandler-statement.md) together with the [AddressOf Operator](../../language-reference/operators/addressof-operator.md).</span></span>

#### <a name="nested-classes"></a><span data-ttu-id="e6b50-191">중첩 클래스</span><span class="sxs-lookup"><span data-stu-id="e6b50-191">Nested classes</span></span>

<span data-ttu-id="e6b50-192">다른 클래스 내에 정의된 클래스를 *중첩 클래스* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-192">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="e6b50-193">기본적으로 중첩 클래스는 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-193">By default, the nested class is private.</span></span>

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

<span data-ttu-id="e6b50-194">중첩 클래스의 인스턴스를 만들려면 다음과 같이 컨테이너 클래스의 이름, 점, 중첩 클래스의 이름을 차례로 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-194">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a><span data-ttu-id="e6b50-195">액세스 한정자 및 액세스 수준</span><span class="sxs-lookup"><span data-stu-id="e6b50-195">Access modifiers and access levels</span></span>

<span data-ttu-id="e6b50-196">모든 클래스 및 클래스 멤버는 *액세스 한정자* 를 사용하여 다른 클래스에 제공할 액세스 수준을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-196">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="e6b50-197">다음과 같은 액세스 한정자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-197">The following access modifiers are available:</span></span>

|<span data-ttu-id="e6b50-198">Visual Basic 한정자</span><span class="sxs-lookup"><span data-stu-id="e6b50-198">Visual Basic Modifier</span></span>|<span data-ttu-id="e6b50-199">정의</span><span class="sxs-lookup"><span data-stu-id="e6b50-199">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="e6b50-200">공용</span><span class="sxs-lookup"><span data-stu-id="e6b50-200">Public</span></span>](../../language-reference/modifiers/public.md)|<span data-ttu-id="e6b50-201">동일한 어셈블리의 다른 코드나 해당 어셈블리를 참조하는 다른 어셈블리의 코드에서 형식이나 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-201">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="e6b50-202">개인</span><span class="sxs-lookup"><span data-stu-id="e6b50-202">Private</span></span>](../../language-reference/modifiers/private.md)|<span data-ttu-id="e6b50-203">동일한 클래스의 코드에서만 형식이나 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-203">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="e6b50-204">보호</span><span class="sxs-lookup"><span data-stu-id="e6b50-204">Protected</span></span>](../../language-reference/modifiers/protected.md)|<span data-ttu-id="e6b50-205">동일한 클래스의 코드나 파생 클래스의 코드에서만 형식이나 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-205">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="e6b50-206">Friend</span><span class="sxs-lookup"><span data-stu-id="e6b50-206">Friend</span></span>](../../language-reference/modifiers/friend.md)|<span data-ttu-id="e6b50-207">동일한 어셈블리의 코드에서는 형식이나 멤버에 액세스할 수 있지만 다른 어셈블리의 코드에서는 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-207">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|`Protected Friend`|<span data-ttu-id="e6b50-208">동일한 어셈블리의 코드 또는 다른 어셈블리의 파생 클래스에서 형식이나 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-208">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|

<span data-ttu-id="e6b50-209">자세한 내용은 [Visual Basic의 액세스 수준](../language-features/declared-elements/access-levels.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-209">For more information, see [Access levels in Visual Basic](../language-features/declared-elements/access-levels.md).</span></span>

### <a name="instantiating-classes"></a><span data-ttu-id="e6b50-210">클래스 인스턴스화</span><span class="sxs-lookup"><span data-stu-id="e6b50-210">Instantiating classes</span></span>

<span data-ttu-id="e6b50-211">개체를 만들려면 클래스를 인스턴스화하거나 클래스 인스턴스를 만들어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-211">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```vb
Dim sampleObject as New SampleClass()
```

<span data-ttu-id="e6b50-212">클래스를 인스턴스화한 후에는 인스턴스의 속성과 필드에 값을 할당하고 클래스 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-212">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

<span data-ttu-id="e6b50-213">클래스를 인스턴스화하는 동안 속성에 값을 할당하려면 다음과 같이 개체 이니셜라이저를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-213">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="e6b50-214">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-214">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-215">새 운영자</span><span class="sxs-lookup"><span data-stu-id="e6b50-215">New Operator</span></span>](../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="e6b50-216">개체 이니셜라이저: 명명된 형식 및 무명 형식</span><span class="sxs-lookup"><span data-stu-id="e6b50-216">Object Initializers: Named and Anonymous Types</span></span>](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a><span data-ttu-id="e6b50-217">공유 클래스 및 멤버</span><span class="sxs-lookup"><span data-stu-id="e6b50-217">Shared classes and members</span></span>

 <span data-ttu-id="e6b50-218">클래스의 공유 멤버는 클래스의 모든 인스턴스에서 공유 하는 속성, 프로시저 또는 필드입니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-218">A shared member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

 <span data-ttu-id="e6b50-219">공유 멤버를 정의 하려면:</span><span class="sxs-lookup"><span data-stu-id="e6b50-219">To define a shared member:</span></span>

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 <span data-ttu-id="e6b50-220">공유 멤버에 액세스 하려면이 클래스의 개체를 만들지 않고 클래스의 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-220">To access the shared member, use the name of the class without creating an object of this class:</span></span>

```vb
MsgBox(SampleClass.SampleString)
```

 <span data-ttu-id="e6b50-221">Visual Basic 공유 모듈은 공유 멤버만 포함 하며 인스턴스화할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-221">Shared modules in Visual Basic have shared members only and cannot be instantiated.</span></span> <span data-ttu-id="e6b50-222">공유 멤버도 비공유 속성, 필드 또는 메서드에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-222">Shared members also cannot access non-shared properties, fields or methods</span></span>

 <span data-ttu-id="e6b50-223">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-223">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-224">공유</span><span class="sxs-lookup"><span data-stu-id="e6b50-224">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="e6b50-225">Module 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-225">Module Statement</span></span>](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a><span data-ttu-id="e6b50-226">무명 형식</span><span class="sxs-lookup"><span data-stu-id="e6b50-226">Anonymous types</span></span>

<span data-ttu-id="e6b50-227">익명 형식을 사용하면 데이터 형식에 대한 클래스 정의를 작성하지 않고 개체를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-227">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="e6b50-228">대신 컴파일러가 클래스를 생성합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-228">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="e6b50-229">이 클래스는 사용할 수 있는 이름이 없고 개체를 선언할 때 지정하는 속성을 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-229">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="e6b50-230">익명 형식의 인스턴스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-230">To create an instance of an anonymous type:</span></span>

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

<span data-ttu-id="e6b50-231">자세한 내용은 다음을 참조하세요. [익명 형식](../language-features/objects-and-classes/anonymous-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-231">For more information, see: [Anonymous Types](../language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="inheritance"></a><span data-ttu-id="e6b50-232">상속</span><span class="sxs-lookup"><span data-stu-id="e6b50-232">Inheritance</span></span>

<span data-ttu-id="e6b50-233">상속을 사용하면 다른 클래스에 정의된 동작을 다시 사용, 확장 및 수정하는 새 클래스를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-233">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="e6b50-234">멤버가 상속되는 클래스를 *기본 클래스* 라고 하고 해당 멤버를 상속하는 클래스를 *파생 클래스* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-234">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="e6b50-235">그러나 Visual Basic의 모든 클래스는 <xref:System.Object> .net 클래스 계층 구조를 지원 하 고 모든 클래스에 하위 수준 서비스를 제공 하는 클래스에서 암시적으로 상속 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-235">However, all classes in Visual Basic implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b50-236">Visual Basic는 다중 상속을 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-236">Visual Basic doesn't support multiple inheritance.</span></span> <span data-ttu-id="e6b50-237">즉, 파생된 클래스에 대해 하나의 기본 클래스만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-237">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="e6b50-238">기본 클래스에서 상속하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-238">To inherit from a base class:</span></span>

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

<span data-ttu-id="e6b50-239">기본적으로 모든 클래스는 상속될 수 있지만</span><span class="sxs-lookup"><span data-stu-id="e6b50-239">By default all classes can be inherited.</span></span> <span data-ttu-id="e6b50-240">클래스가 기본 클래스로 사용되지 않아야 하는지 여부를 지정하거나 기본 클래스로만 사용될 수 있는 클래스를 만들 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-240">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="e6b50-241">클래스가 기본 클래스로 사용될 수 없도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-241">To specify that a class cannot be used as a base class:</span></span>

```vb
NotInheritable Class SampleClass
End Class
```

<span data-ttu-id="e6b50-242">클래스가 기본 클래스로만 사용되고 인스턴스화되지 않도록 지정하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-242">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```vb
MustInherit Class BaseClass
End Class
```

<span data-ttu-id="e6b50-243">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-243">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-244">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="e6b50-244">Inherits Statement</span></span>](../../language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="e6b50-245">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="e6b50-245">NotInheritable</span></span>](../../language-reference/modifiers/notinheritable.md)
- [<span data-ttu-id="e6b50-246">MustInherit</span><span class="sxs-lookup"><span data-stu-id="e6b50-246">MustInherit</span></span>](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a><span data-ttu-id="e6b50-247">멤버 재정의</span><span class="sxs-lookup"><span data-stu-id="e6b50-247">Overriding members</span></span>

<span data-ttu-id="e6b50-248">기본적으로 파생 클래스는 해당 기본 클래스에서 모든 멤버를 상속합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-248">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="e6b50-249">상속된 멤버의 동작을 변경하려면 해당 멤버를 재정의해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-249">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="e6b50-250">즉, 파생 클래스에 해당 메서드, 속성 또는 이벤트의 새로운 구현을 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-250">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="e6b50-251">다음 한정자는 속성 및 메서드가 재정의되는 방식을 제어하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-251">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="e6b50-252">Visual Basic 한정자</span><span class="sxs-lookup"><span data-stu-id="e6b50-252">Visual Basic Modifier</span></span>|<span data-ttu-id="e6b50-253">정의</span><span class="sxs-lookup"><span data-stu-id="e6b50-253">Definition</span></span>|
|---------------------------|----------------|
|[<span data-ttu-id="e6b50-254">Overrides</span><span class="sxs-lookup"><span data-stu-id="e6b50-254">Overridable</span></span>](../../language-reference/modifiers/overridable.md)|<span data-ttu-id="e6b50-255">파생 클래스에서 클래스 멤버를 재정의할 수 있도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-255">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="e6b50-256">재정의</span><span class="sxs-lookup"><span data-stu-id="e6b50-256">Overrides</span></span>](../../language-reference/modifiers/overrides.md)|<span data-ttu-id="e6b50-257">기본 클래스에 정의된 가상(재정의 가능) 멤버를 재정의합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-257">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="e6b50-258">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e6b50-258">NotOverridable</span></span>](../../language-reference/modifiers/notoverridable.md)|<span data-ttu-id="e6b50-259">멤버가 상속 클래스에서 재정의되지 않도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-259">Prevents a member from being overridden in an inheriting class.</span></span>|
|[<span data-ttu-id="e6b50-260">New</span><span class="sxs-lookup"><span data-stu-id="e6b50-260">MustOverride</span></span>](../../language-reference/modifiers/mustoverride.md)|<span data-ttu-id="e6b50-261">파생 클래스에서 클래스 멤버가 재정의되도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-261">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="e6b50-262">Overloads</span><span class="sxs-lookup"><span data-stu-id="e6b50-262">Shadows</span></span>](../../language-reference/modifiers/shadows.md)|<span data-ttu-id="e6b50-263">기본 클래스에서 상속된 멤버를 숨깁니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-263">Hides a member inherited from a base class</span></span>|

## <a name="interfaces"></a><span data-ttu-id="e6b50-264">인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6b50-264">Interfaces</span></span>

<span data-ttu-id="e6b50-265">인터페이스는 클래스와 마찬가지로 속성, 메서드 및 이벤트를 정의하지만</span><span class="sxs-lookup"><span data-stu-id="e6b50-265">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="e6b50-266">클래스와는 달리 구현을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-266">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="e6b50-267">인터페이스는 클래스에 의해 구현되며 클래스와는 별개의 엔터티로 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-267">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="e6b50-268">인터페이스는 계약을 나타내므로 인터페이스를 구현하는 클래스에서는 해당 인터페이스의 모든 부분을 정의된 그대로 정확하게 구현해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-268">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="e6b50-269">인터페이스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-269">To define an interface:</span></span>

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

<span data-ttu-id="e6b50-270">클래스에서 인터페이스를 구현하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-270">To implement an interface in a class:</span></span>

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

<span data-ttu-id="e6b50-271">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-271">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-272">인터페이스</span><span class="sxs-lookup"><span data-stu-id="e6b50-272">Interfaces</span></span>](../language-features/interfaces/index.md)
- [<span data-ttu-id="e6b50-273">Interface 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-273">Interface Statement</span></span>](../../language-reference/statements/interface-statement.md)
- [<span data-ttu-id="e6b50-274">Implements 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-274">Implements Statement</span></span>](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a><span data-ttu-id="e6b50-275">제네릭</span><span class="sxs-lookup"><span data-stu-id="e6b50-275">Generics</span></span>

<span data-ttu-id="e6b50-276">.NET의 클래스, 구조체, 인터페이스 및 메서드는 저장 하거나 사용할 수 있는 개체 형식을 정의 하는 *형식 매개 변수* 를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-276">Classes, structures, interfaces and methods in .NET can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="e6b50-277">제네릭의 가장 일반적인 예는 컬렉션에 저장할 개체의 형식을 지정할 수 있는 컬렉션입니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-277">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="e6b50-278">제네릭 클래스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-278">To define a generic class:</span></span>

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

<span data-ttu-id="e6b50-279">제네릭 클래스의 인스턴스를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-279">To create an instance of a generic class:</span></span>

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

<span data-ttu-id="e6b50-280">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-280">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-281">제네릭</span><span class="sxs-lookup"><span data-stu-id="e6b50-281">Generics</span></span>](../../../standard/generics/index.md)
- [<span data-ttu-id="e6b50-282">Visual Basic의 제네릭 형식</span><span class="sxs-lookup"><span data-stu-id="e6b50-282">Generic Types in Visual Basic</span></span>](../language-features/data-types/generic-types.md)

## <a name="delegates"></a><span data-ttu-id="e6b50-283">대리자</span><span class="sxs-lookup"><span data-stu-id="e6b50-283">Delegates</span></span>

 <span data-ttu-id="e6b50-284">*대리자* 는 메서드 시그니처를 정의하는 형식으로, 호환되는 시그니처가 있는 모든 메서드에 대한 참조를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-284">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="e6b50-285">대리자를 통해 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-285">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="e6b50-286">대리자는 메서드를 다른 메서드에 인수로 전달하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-286">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="e6b50-287">이벤트 처리기는 대리자를 통해 호출되는 메서드라고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e6b50-287">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="e6b50-288">이벤트를 처리할 때 대리자를 사용하는 방법에 대한 자세한 내용은 [이벤트](../../../standard/events/index.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-288">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="e6b50-289">대리자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-289">To create a delegate:</span></span>

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

<span data-ttu-id="e6b50-290">대리자가 지정한 시그니처와 일치하는 메서드에 대한 참조를 만들려면</span><span class="sxs-lookup"><span data-stu-id="e6b50-290">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

<span data-ttu-id="e6b50-291">자세한 내용은 다음을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="e6b50-291">For more information, see:</span></span>

- [<span data-ttu-id="e6b50-292">대리자</span><span class="sxs-lookup"><span data-stu-id="e6b50-292">Delegates</span></span>](../language-features/delegates/index.md)
- [<span data-ttu-id="e6b50-293">Delegate 문</span><span class="sxs-lookup"><span data-stu-id="e6b50-293">Delegate Statement</span></span>](../../language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="e6b50-294">AddressOf 연산자</span><span class="sxs-lookup"><span data-stu-id="e6b50-294">AddressOf Operator</span></span>](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a><span data-ttu-id="e6b50-295">추가 정보</span><span class="sxs-lookup"><span data-stu-id="e6b50-295">See also</span></span>

- [<span data-ttu-id="e6b50-296">Visual Basic 프로그래밍 가이드</span><span class="sxs-lookup"><span data-stu-id="e6b50-296">Visual Basic Programming Guide</span></span>](../index.md)
