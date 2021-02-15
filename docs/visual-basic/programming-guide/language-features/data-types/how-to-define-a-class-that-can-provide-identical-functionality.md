---
description: '자세한 정보: 방법: 다른 데이터 형식에 동일한 기능을 제공할 수 있는 클래스 정의 (Visual Basic)'
title: '방법: 다른 데이터 형식에 동일한 기능을 제공할 수 있는 클래스 정의'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: 14be6c748ccb311c6a2974e8947b01a1c55a90b6
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100469749"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="3e9ea-103">방법: 다른 데이터 형식에 동일한 기능을 제공할 수 있는 클래스 정의(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e9ea-103">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>

<span data-ttu-id="3e9ea-104">여러 데이터 형식에 대해 동일한 기능을 제공하는 개체를 만들 수 있는 클래스를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-104">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="3e9ea-105">이렇게 하려면 정의에 하나 이상의 *형식 매개 변수* 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-105">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="3e9ea-106">그러면 클래스는 여러 데이터 형식을 사용하는 개체의 템플릿 역할을 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-106">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="3e9ea-107">이 방법으로 정의된 클래스를 *제네릭 클래스* 라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-107">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="3e9ea-108">제네릭 클래스를 정의할 때의 장점은 한 번만 정의하면 코드에서 이를 사용하여 다양한 데이터 형식을 사용하는 여러 개체를 만들 수 있다는 점입니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-108">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="3e9ea-109">그 결과 `Object` 형식으로 클래스를 정의할 때보다 성능이 향상됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-109">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="3e9ea-110">클래스 이외에도 제네릭 구조체, 인터페이스, 프로시저 및 대리자도 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-110">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="3e9ea-111">형식 매개 변수로 클래스를 정의하려면</span><span class="sxs-lookup"><span data-stu-id="3e9ea-111">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="3e9ea-112">일반적인 방법으로 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-112">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="3e9ea-113">`(Of`  `)` 형식 매개 변수를 지정 하려면 클래스 이름 바로 뒤에 typeparameter를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-113">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="3e9ea-114">형식 매개 변수가 두 개 이상인 경우에는 쉼표로 구분된 목록을 괄호 안에 넣으세요.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-114">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="3e9ea-115">`Of` 키워드는 반복하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-115">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="3e9ea-116">코드가 단순한 할당 이외의 형식 매개 변수에 대한 작업을 수행하는 경우 해당 형식 매개 변수 뒤에 `As` 절을 사용하여 하나 이상의 *제약 조건* 을 추가하세요.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-116">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="3e9ea-117">제약 조건을 사용하면 해당 형식 매개 변수에 대해 제공되는 형식이 다음과 같은 요구 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-117">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="3e9ea-118">코드에서 수행하는 `>`등의 작업을 지원</span><span class="sxs-lookup"><span data-stu-id="3e9ea-118">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="3e9ea-119">코드에서 액세스하는 메서드와 같은 멤버를 지원</span><span class="sxs-lookup"><span data-stu-id="3e9ea-119">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="3e9ea-120">매개 변수 없는 생성자 노출</span><span class="sxs-lookup"><span data-stu-id="3e9ea-120">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="3e9ea-121">제약 조건을 지정하지 않으면 [Object Data Type](../../../language-reference/data-types/object-data-type.md)에서 지원되는 작업 및 멤버만 코드에서 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-121">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="3e9ea-122">자세한 내용은 [Type List](../../../language-reference/statements/type-list.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-122">For more information, see [Type List](../../../language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="3e9ea-123">제공 된 형식으로 선언 될 모든 클래스 멤버를 식별 하 고이를 선언 `As` `typeparameter` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-123">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="3e9ea-124">이는 내부 스토리지, 프로시저 매개 변수 및 반환 값에 적용됩니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-124">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="3e9ea-125">`itemType`에 제공할 수 있는 모든 데이터 형식이 지원하는 작업 및 메서드만 코드에서 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-125">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="3e9ea-126">다음 예에서는 매우 간단한 목록을 관리하는 클래스를 정의합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-126">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="3e9ea-127">내부 배열 `items`에 목록을 저장하며 코드를 사용하여 목록 요소의 데이터 형식을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-127">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="3e9ea-128">매개 변수가 있는 생성자를 사용 하면 코드를 사용 하 여의 상한을 설정할 수 `items` 있으며, 매개 변수가 없는 생성자는이를 9 (총 10 개 항목)로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-128">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="3e9ea-129">`simpleList` 값 목록을 저장할 클래스, `Integer` 값 목록을 저장할 클래스, `String` 값을 저장할 클래스를 `Date` 로부터 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-129">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="3e9ea-130">목록 요소의 데이터 형식을 제외하고 이러한 모든 클래스에서 만들어진 개체는 동일하게 동작합니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-130">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="3e9ea-131">코드에서 `itemType` 에 제공하는 형식 인수는 `Boolean` 또는 `Double`, 구조체, 열거형 또는 애플리케이션이 정의하는 형식을 포함한 모든 클래스 형식과 같은 내부 형식일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-131">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="3e9ea-132">다음 코드로 클래스 `simpleList` 를 테스트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3e9ea-132">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="3e9ea-133">추가 정보</span><span class="sxs-lookup"><span data-stu-id="3e9ea-133">See also</span></span>

- [<span data-ttu-id="3e9ea-134">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="3e9ea-134">Data Types</span></span>](index.md)
- [<span data-ttu-id="3e9ea-135">Visual Basic의 제네릭 형식</span><span class="sxs-lookup"><span data-stu-id="3e9ea-135">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="3e9ea-136">언어 독립성 및 언어 독립적 구성 요소</span><span class="sxs-lookup"><span data-stu-id="3e9ea-136">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="3e9ea-137">으로</span><span class="sxs-lookup"><span data-stu-id="3e9ea-137">Of</span></span>](../../../language-reference/statements/of-clause.md)
- [<span data-ttu-id="3e9ea-138">Type List</span><span class="sxs-lookup"><span data-stu-id="3e9ea-138">Type List</span></span>](../../../language-reference/statements/type-list.md)
- [<span data-ttu-id="3e9ea-139">방법: 제네릭 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="3e9ea-139">How to: Use a Generic Class</span></span>](how-to-use-a-generic-class.md)
- [<span data-ttu-id="3e9ea-140">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="3e9ea-140">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
