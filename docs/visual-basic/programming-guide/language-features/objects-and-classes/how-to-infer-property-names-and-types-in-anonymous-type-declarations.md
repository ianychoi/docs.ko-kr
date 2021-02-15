---
description: '자세한 정보: 방법: 익명 형식 선언에서 속성 이름 및 형식 유추 (Visual Basic)'
title: '방법: 익명 형식 선언에서 속성 이름 및 형식 유추'
ms.date: 07/20/2015
helpviewer_keywords:
- inferring property names [Visual Basic]
- anonymous types [Visual Basic], inferring property names and types
- inferring property types [Visual Basic]
ms.assetid: 7c748b22-913f-4d9d-b747-6b7bf296a0bc
ms.openlocfilehash: e4bff8cd8dd879b97618a3bc69e1eaf1c7c269b7
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483900"
---
# <a name="how-to-infer-property-names-and-types-in-anonymous-type-declarations-visual-basic"></a><span data-ttu-id="abd99-103">방법: 익명 형식 선언에서 속성 이름 및 형식 유추(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abd99-103">How to: Infer Property Names and Types in Anonymous Type Declarations (Visual Basic)</span></span>

<span data-ttu-id="abd99-104">익명 형식은 속성의 데이터 형식을 직접 지정하는 메커니즘을 제공하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-104">Anonymous types provide no mechanism for directly specifying the data types of properties.</span></span> <span data-ttu-id="abd99-105">모든 속성의 형식이 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-105">Types of all properties are inferred.</span></span> <span data-ttu-id="abd99-106">다음 예제에서 `Name` 및 `Price` 의 형식은 이를 초기화하는 데 사용되는 값에서 직접 유추됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-106">In the following example, the types of `Name` and `Price` are inferred directly from the values that are used to initialize them.</span></span>

[!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]

<span data-ttu-id="abd99-107">익명 형식은 다른 소스에서 속성 이름 및 형식을 유추할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-107">Anonymous types can also infer property names and types from other sources.</span></span> <span data-ttu-id="abd99-108">다음 섹션에서는 유추가 가능한 환경의 목록과 유추가 가능하지 않은 상황의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-108">The sections that follow provide a list of the circumstances where inference is possible, and examples of situations where it is not.</span></span>

## <a name="successful-inference"></a><span data-ttu-id="abd99-109">유추 성공</span><span class="sxs-lookup"><span data-stu-id="abd99-109">Successful Inference</span></span>

#### <a name="anonymous-types-can-infer-property-names-and-types-from-the-following-sources"></a><span data-ttu-id="abd99-110">익명 형식은 다음 소스에서 속성 이름 및 형식을 유추할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-110">Anonymous types can infer property names and types from the following sources:</span></span>

- <span data-ttu-id="abd99-111">변수 이름에서.</span><span class="sxs-lookup"><span data-stu-id="abd99-111">From variable names.</span></span> <span data-ttu-id="abd99-112">익명 형식 `anonProduct` 에는 두 개의 속성 `productName` 및 `productPrice`가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-112">Anonymous type `anonProduct` will have two properties, `productName` and `productPrice`.</span></span> <span data-ttu-id="abd99-113">각각의 데이터 형식은 원래 변수 `String` 및 `Double`의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-113">Their data types will be those of the original variables, `String` and `Double`, respectively.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#11)]

- <span data-ttu-id="abd99-114">다른 개체의 속성 또는 필드 이름에서.</span><span class="sxs-lookup"><span data-stu-id="abd99-114">From property or field names of other objects.</span></span> <span data-ttu-id="abd99-115">`car` 및 `CarClass` 속성이 포함된 `Name` 형식의 `ID` 개체를 예로 들겠습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-115">For example, consider a `car` object of a `CarClass` type that includes `Name` and `ID` properties.</span></span> <span data-ttu-id="abd99-116">`car1`개체의 값으로 초기화되는 `Name` 및 `ID` 속성을 가진 새 익명 형식 인스턴스 `car` 을 만들려면 다음을 작성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-116">To create a new anonymous type instance, `car1`, with `Name` and `ID` properties that are initialized with the values from the `car` object, you can write the following:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#34)]

  <span data-ttu-id="abd99-117">이전 선언은 익명 형식 `car2`를 정의하는 더 긴 코드 줄과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-117">The previous declaration is equivalent to the longer line of code that defines anonymous type `car2`.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#35)]

- <span data-ttu-id="abd99-118">XML 멤버 이름에서.</span><span class="sxs-lookup"><span data-stu-id="abd99-118">From XML member names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#12)]

  <span data-ttu-id="abd99-119">`anon` 의 결과 형식은 `Book`(Of XElement) 형식의 <xref:System.Collections.IEnumerable>속성 하나를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-119">The resulting type for `anon` would have one property, `Book`, of type <xref:System.Collections.IEnumerable>(Of XElement).</span></span>

- <span data-ttu-id="abd99-120">다음 예제에서처럼 `SomeFunction` 과 같은 매개 변수가 없는 함수에서.</span><span class="sxs-lookup"><span data-stu-id="abd99-120">From a function that has no parameters, such as `SomeFunction` in the following example.</span></span>

  ```vb
  Dim sc As New SomeClass
  Dim anon1 = New With {Key sc.SomeFunction()}
  ```

  <span data-ttu-id="abd99-121">다음 코드에서 변수 `anon2` 은 하나의 속성(이름이 `First`인 문자)을 가지는 익명 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-121">The variable `anon2` in the following code is an anonymous type that has one property, a character named `First`.</span></span> <span data-ttu-id="abd99-122">이 코드는 함수 <xref:System.Linq.Enumerable.First%2A>에서 반환하는 문자인 “E”를 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-122">This code will display a letter "E," the letter that is returned by function <xref:System.Linq.Enumerable.First%2A>.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#13)]

## <a name="inference-failures"></a><span data-ttu-id="abd99-123">유추 실패</span><span class="sxs-lookup"><span data-stu-id="abd99-123">Inference Failures</span></span>

#### <a name="name-inference-will-fail-in-many-circumstances-including-the-following"></a><span data-ttu-id="abd99-124">다음을 포함한 여러 경우에 이름 유추가 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-124">Name inference will fail in many circumstances, including the following:</span></span>

- <span data-ttu-id="abd99-125">인수가 필요한 메서드, 생성자 또는 매개 변수가 있는 속성의 호출에서 유추가 도출되는 경우.</span><span class="sxs-lookup"><span data-stu-id="abd99-125">The inference derives from the invocation of a method, a constructor, or a parameterized property that requires arguments.</span></span> <span data-ttu-id="abd99-126">`anon1` 에 하나 이상의 인수가 있는 경우 `someFunction` 의 이전 선언이 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-126">The previous declaration of `anon1` fails if `someFunction` has one or more arguments.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon3 = New With {Key sc.someFunction(someArg)}
  ```

  <span data-ttu-id="abd99-127">새 속성 이름에 할당하면 문제가 해결됩니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-127">Assignment to a new property name solves the problem.</span></span>

  ```vb
  ' Valid.
  Dim anon4 = New With {Key .FunResult = sc.someFunction(someArg)}
  ```

- <span data-ttu-id="abd99-128">복잡한 식에서 유추가 도출되는 경우.</span><span class="sxs-lookup"><span data-stu-id="abd99-128">The inference derives from a complex expression.</span></span>

  ```vb
  Dim aString As String = "Act "
  ' Not valid.
  ' Dim label = New With {Key aString & "IV"}
  ```

  <span data-ttu-id="abd99-129">식의 결과를 속성 이름에 할당하여 오류를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-129">The error can be resolved by assigning the result of the expression to a property name.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#14)]

- <span data-ttu-id="abd99-130">이름이 동일한 둘 이상의 속성을 생성하는 여러 속성에 대한 유추.</span><span class="sxs-lookup"><span data-stu-id="abd99-130">Inference for multiple properties produces two or more properties that have the same name.</span></span> <span data-ttu-id="abd99-131">이전 예의 선언을 다시 보면 `product.Name` 과 `car1.Name` 모두를 동일한 익명 형식의 속성으로 나열할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-131">Referring back to declarations in earlier examples, you cannot list both `product.Name` and `car1.Name` as properties of the same anonymous type.</span></span> <span data-ttu-id="abd99-132">이는 이 두 가지 각각에 대한 유추된 식별자가 `Name`이기 때문입니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-132">This is because the inferred identifier for each of these would be `Name`.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon5 = New With {Key product.Name, Key car1.Name}
  ```

  <span data-ttu-id="abd99-133">고유한 속성 이름에 값을 할당하여 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-133">The problem can be solved by assigning the values to distinct property names.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#36)]

  <span data-ttu-id="abd99-134">대/소문자를 변경하더라도 두 이름이 고유해지지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-134">Note that changes in case (changes between uppercase and lowercase letters) do not make two names distinct.</span></span>

  ```vb
  Dim price = 0
  ' Not valid, because Price and price are the same name.
  ' Dim anon7 = New With {Key product.Price, Key price}
  ```

- <span data-ttu-id="abd99-135">속성의 초기 형식 및 값이 아직 설정되지 않은 다른 속성에 따라 달라지는 경우.</span><span class="sxs-lookup"><span data-stu-id="abd99-135">The initial type and value of one property depends on another property that is not yet established.</span></span> <span data-ttu-id="abd99-136">예를 들어 `.IDName = .LastName` 이 아직 초기화되지 않은 경우 `.LastName` 은 익명 형식 선언에서 유효하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-136">For example, `.IDName = .LastName` is not valid in an anonymous type declaration unless `.LastName` is already initialized.</span></span>

  ```vb
  ' Not valid.
  ' Dim anon8 = New With {Key .IDName = .LastName, Key .LastName = "Jones"}
  ```

  <span data-ttu-id="abd99-137">이 예에서는 속성이 선언되는 순서를 반전시켜서 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-137">In this example, you can fix the problem by reversing the order in which the properties are declared.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#15)]

- <span data-ttu-id="abd99-138">익명 형식의 속성 이름은 <xref:System.Object>의 멤버 이름과 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-138">A property name of the anonymous type is the same as the name of a member of <xref:System.Object>.</span></span> <span data-ttu-id="abd99-139">예를 들어 `Equals` 은 <xref:System.Object>의 메서드이므로 다음 선언은 실패합니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-139">For example, the following declaration fails because `Equals` is a method of <xref:System.Object>.</span></span>

  ```vb
  ' Not valid.
  ' Dim relationsLabels1 = New With {Key .Equals = "equals", Key .Greater = _
  '                       "greater than", Key .Less = "less than"}
  ```

  <span data-ttu-id="abd99-140">속성 이름을 변경하여 문제를 해결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="abd99-140">You can fix the problem by changing the property name:</span></span>

  [!code-vb[VbVbalrAnonymousTypes#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#16)]

## <a name="see-also"></a><span data-ttu-id="abd99-141">추가 정보</span><span class="sxs-lookup"><span data-stu-id="abd99-141">See also</span></span>

- [<span data-ttu-id="abd99-142">개체 이니셜라이저: 명명된 형식 및 무명 형식</span><span class="sxs-lookup"><span data-stu-id="abd99-142">Object Initializers: Named and Anonymous Types</span></span>](object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="abd99-143">지역 형식 유추</span><span class="sxs-lookup"><span data-stu-id="abd99-143">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="abd99-144">익명 형식</span><span class="sxs-lookup"><span data-stu-id="abd99-144">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="abd99-145">키</span><span class="sxs-lookup"><span data-stu-id="abd99-145">Key</span></span>](../../../language-reference/modifiers/key.md)
