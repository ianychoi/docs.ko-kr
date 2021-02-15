---
description: '자세히 알아보기: 컬렉션 이니셜라이저 (Visual Basic)'
title: 컬렉션 이니셜라이저
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: afae9278092934ead4572f16fb1ec4a29d631803
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475463"
---
# <a name="collection-initializers-visual-basic"></a><span data-ttu-id="6205d-103">컬렉션 이니셜라이저(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6205d-103">Collection Initializers (Visual Basic)</span></span>

<span data-ttu-id="6205d-104">*컬렉션 이니셜라이저* 는 컬렉션을 만들고 값의 초기 집합으로 채울 수 있도록 하는 약식 구문을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-104">*Collection initializers* provide a shortened syntax that enables you to create a collection and populate it with an initial set of values.</span></span> <span data-ttu-id="6205d-105">컬렉션 이니셜라이저는 알려진 값(예: 메뉴 옵션 또는 범주 목록, 숫자 값의 초기 집합, 일 또는 월 이름과 같은 문자열의 정적 목록 또는 유효성 검사에 사용되는 상태 목록과 같은 지리적 위치)의 집합에서 컬렉션을 만드는 경우에 유용합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-105">Collection initializers are useful when you are creating a collection from a set of known values, for example, a list of menu options or categories, an initial set of numeric values, a static list of strings such as day or month names, or geographic locations such as a list of states that is used for validation.</span></span>

<span data-ttu-id="6205d-106">항목 컬렉션에 대한 자세한 내용은 [컬렉션](../../concepts/collections.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6205d-106">For more information about collections, see [Collections](../../concepts/collections.md).</span></span>

<span data-ttu-id="6205d-107">`From` 키워드 뒤에 중괄호(`{}`)를 사용하여 컬렉션 이니셜라이저를 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-107">You identify a collection initializer by using the `From` keyword followed by braces (`{}`).</span></span> <span data-ttu-id="6205d-108">이것은 [배열](../arrays/index.md)에서 설명된 배열 리터럴 구문과 비슷합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-108">This is similar to the array literal syntax that is described in [Arrays](../arrays/index.md).</span></span> <span data-ttu-id="6205d-109">다음 예제에서는 컬렉션 이니셜라이저를 사용하여 컬렉션을 만드는 다양한 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-109">The following examples show various ways to use collection initializers to create collections.</span></span>

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> <span data-ttu-id="6205d-110">C#에서도 컬렉션 이니셜라이저를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-110">C# also provides collection initializers.</span></span> <span data-ttu-id="6205d-111">C# 컬렉션 이니셜라이저는 Visual Basic 컬렉션 이니셜라이저와 같은 기능을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-111">C# collection initializers provide the same functionality as Visual Basic collection initializers.</span></span> <span data-ttu-id="6205d-112">C# 컬렉션 이니셜라이저에 대한 자세한 내용은 [개체 및 컬렉션 이니셜라이저](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6205d-112">For more information about C# collection initializers, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="6205d-113">Syntax</span><span class="sxs-lookup"><span data-stu-id="6205d-113">Syntax</span></span>

<span data-ttu-id="6205d-114">컬렉션 이니셜라이저는 다음 코드에서처럼 `From` 키워드 뒤에서 중괄호(`{}`)로 묶인 쉼표로 구분된 값 목록으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-114">A collection initializer consists of a list of comma-separated values that are enclosed in braces (`{}`), preceded by the `From` keyword, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

<span data-ttu-id="6205d-115"><xref:System.Collections.Generic.List%601> 또는 <xref:System.Collections.Generic.Dictionary%602>와 같은 컬렉션을 만들 경우 다음 코드와 같이 컬렉션 이니셜라이저 앞에 컬렉션 형식을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-115">When you create a collection, such as a <xref:System.Collections.Generic.List%601> or a <xref:System.Collections.Generic.Dictionary%602>, you must supply the collection type before the collection initializer, as shown in the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> <span data-ttu-id="6205d-116">같은 컬렉션 개체를 초기화하기 위해 컬렉션 이니셜라이저 및 개체 이니셜라이저를 결합할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-116">You cannot combine both a collection initializer and an object initializer to initialize the same collection object.</span></span> <span data-ttu-id="6205d-117">개체 이니셜라이저를 사용하여 컬렉션 이니셜라이저에서 개체를 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-117">You can use object initializers to initialize objects in a collection initializer.</span></span>

## <a name="creating-a-collection-by-using-a-collection-initializer"></a><span data-ttu-id="6205d-118">컬렉션 이니셜라이저를 사용 하 여 컬렉션 만들기</span><span class="sxs-lookup"><span data-stu-id="6205d-118">Creating a Collection by Using a Collection Initializer</span></span>

<span data-ttu-id="6205d-119">컬렉션 이니셜라이저를 사용하여 컬렉션을 만들 경우 컬렉션 이니셜라이저로 제공되는 각 값은 컬렉션의 적절한 `Add` 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-119">When you create a collection by using a collection initializer, each value that is supplied in the collection initializer is passed to the appropriate `Add` method of the collection.</span></span> <span data-ttu-id="6205d-120">예를 들어 컬렉션 이니셜라이저를 사용하여 <xref:System.Collections.Generic.List%601>를 만들 경우 컬렉션 이니셜라이저의 각 문자열 값은 <xref:System.Collections.Generic.List%601.Add%2A> 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-120">For example, if you create a <xref:System.Collections.Generic.List%601> by using a collection initializer, each string value in the collection initializer is passed to the <xref:System.Collections.Generic.List%601.Add%2A> method.</span></span> <span data-ttu-id="6205d-121">컬렉션 이니셜라이저를 사용하여 컬렉션을 만들려면 지정된 형식이 유효한 컬렉션 형식이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-121">If you want to create a collection by using a collection initializer, the specified type must be valid collection type.</span></span> <span data-ttu-id="6205d-122">유효한 컬렉션 형식의 예에는 <xref:System.Collections.Generic.IEnumerable%601> 인터페이스를 구현하거나 <xref:System.Collections.CollectionBase> 클래스를 상속하는 클래스가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-122">Examples of valid collection types include classes that implement the <xref:System.Collections.Generic.IEnumerable%601> interface or inherit the <xref:System.Collections.CollectionBase> class.</span></span> <span data-ttu-id="6205d-123">또한 지정된 형식은 다음 조건을 충족하는 `Add` 메서드를 노출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-123">The specified type must also expose an `Add` method that meets the following criteria.</span></span>

- <span data-ttu-id="6205d-124">`Add` 메서드는 컬렉션 이니셜라이저가 호출되고 있는 범위에서 사용할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-124">The `Add` method must be available from the scope in which the collection initializer is being called.</span></span> <span data-ttu-id="6205d-125">컬렉션의 public이 아닌 메서드에 액세스할 수 있는 시나리오에서 컬렉션 이니셜라이저를 사용하는 경우 `Add` 메서드는 public일 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-125">The `Add` method does not have to be public if you are using the collection initializer in a scenario where non-public methods of the collection can be accessed.</span></span>

- <span data-ttu-id="6205d-126">`Add` 메서드는 컬렉션 클래스의 인스턴스 멤버 또는 `Shared` 멤버이거나 확장 메서드여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-126">The `Add` method must be an instance member or `Shared` member of the collection class, or an extension method.</span></span>

- <span data-ttu-id="6205d-127">오버로드 확인 규칙에 따라 컬렉션 이니셜라이저에서 제공되는 형식과 일치할 수 있는 `Add` 메서드가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-127">An `Add` method must exist that can be matched, based on overload resolution rules, to the types that are supplied in the collection initializer.</span></span>

 <span data-ttu-id="6205d-128">예를 들어 다음 코드 예제에서는 컬렉션 이니셜라이저를 사용하여 `List(Of Customer)` 컬렉션을 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-128">For example, the following code example shows how to create a `List(Of Customer)` collection by using a collection initializer.</span></span> <span data-ttu-id="6205d-129">코드가 실행되면 각 `Customer` 개체가 제네릭 목록의 `Add(Customer)` 메서드에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-129">When the code is run, each `Customer` object is passed to the `Add(Customer)` method of the generic list.</span></span>

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

<span data-ttu-id="6205d-130">다음 코드 예제에서는 컬렉션 이니셜라이저를 사용하지 않는 동일한 코드를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-130">The following code example shows equivalent code that does not use a collection initializer.</span></span>

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

<span data-ttu-id="6205d-131">`Customer` 개체에 대한 생성자와 일치하는 매개 변수가 있는 `Add` 메서드가 컬렉션에 포함된 경우 다음 섹션에 설명된 대로 `Add` 메서드에 대한 매개 변수 값을 컬렉션 이니셜라이저 내에 중첩할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-131">If the collection has an `Add` method that has parameters that match the constructor for the `Customer` object, you could nest parameter values for the `Add` method within collection initializers, as discussed in the next section.</span></span> <span data-ttu-id="6205d-132">컬렉션에 이런 `Add` 메서드가 없는 경우 확장 메서드로 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-132">If the collection does not have such an `Add` method, you can create one as an extension method.</span></span> <span data-ttu-id="6205d-133">`Add` 메서드를 컬렉션의 확장 메서드로 만드는 방법에 대한 예제는 [방법: 컬렉션 이니셜라이저에 사용되는 Add 확장 메서드 만들기](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6205d-133">For an example of how to create an `Add` method as an extension method for a collection, see [How to: Create an Add Extension Method Used by a Collection Initializer](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md).</span></span> <span data-ttu-id="6205d-134">컬렉션 이니셜라이저에서 사용할 수 있는 사용자 지정 컬렉션을 만드는 방법에 대한 예제는 [방법: 컬렉션 이니셜라이저에 사용되는 컬렉션 만들기](how-to-create-a-collection-used-by-a-collection-initializer.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6205d-134">For an example of how to create a custom collection that can be used with a collection initializer, see [How to: Create a Collection Used by a Collection Initializer](how-to-create-a-collection-used-by-a-collection-initializer.md).</span></span>

## <a name="nesting-collection-initializers"></a><span data-ttu-id="6205d-135">컬렉션 이니셜라이저 중첩</span><span class="sxs-lookup"><span data-stu-id="6205d-135">Nesting Collection Initializers</span></span>

<span data-ttu-id="6205d-136">값을 컬렉션 이니셜라이저 내에 중첩하여 만들고 있는 컬렉션에 대한 `Add` 메서드의 특정 오버로드를 식별할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-136">You can nest values within a collection initializer to identify a specific overload of an `Add` method for the collection that is being created.</span></span> <span data-ttu-id="6205d-137">`Add` 메서드에 전달된 값은 배열 리터럴 또는 컬렉션 이니셜라이저에서 하는 것과 같이 쉼표로 구분하고 중괄호(`{}`)로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-137">The values passed to the `Add` method must be separated by commas and enclosed in braces (`{}`), like you would do in an array literal or collection initializer.</span></span>

<span data-ttu-id="6205d-138">중첩된 값을 사용하여 컬렉션을 만들 경우 중첩된 값 목록의 각 요소는 요소 형식과 일치하는 `Add` 메서드에 인수로 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-138">When you create a collection by using nested values, each element of the nested value list is passed as an argument to the `Add` method that matches the element types.</span></span> <span data-ttu-id="6205d-139">예를 들어 다음 코드 예제에서는 키가 `Integer` 형식이고 값이 `String` 형식인 <xref:System.Collections.Generic.Dictionary%602>를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-139">For example, the following code example creates a <xref:System.Collections.Generic.Dictionary%602> in which the keys are of type `Integer` and the values are of type `String`.</span></span> <span data-ttu-id="6205d-140">각 중첩된 값 목록은 `Dictionary`에 대한 <xref:System.Collections.Generic.Dictionary%602.Add%2A> 메서드와 일치합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-140">Each of the nested value lists is matched to the <xref:System.Collections.Generic.Dictionary%602.Add%2A> method for the `Dictionary`.</span></span>

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

<span data-ttu-id="6205d-141">이전 코드 예제는 다음 코드와 동일합니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-141">The previous code example is equivalent to the following code.</span></span>

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

<span data-ttu-id="6205d-142">첫 번째 중첩 수준의 중첩된 값 목록만 컬렉션 형식에 대한 `Add` 메서드에 전송됩니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-142">Only nested value lists from the first level of nesting are sent to the `Add` method for the collection type.</span></span> <span data-ttu-id="6205d-143">더 깊은 중첩 수준은 배열 리터럴로 처리되고 중첩된 값 목록이 컬렉션의 `Add` 메서드와 일치하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-143">Deeper levels of nesting are treated as array literals and the nested value lists are not matched to the `Add` method of any collection.</span></span>

## <a name="related-topics"></a><span data-ttu-id="6205d-144">관련 항목</span><span class="sxs-lookup"><span data-stu-id="6205d-144">Related Topics</span></span>

|<span data-ttu-id="6205d-145">제목</span><span class="sxs-lookup"><span data-stu-id="6205d-145">Title</span></span>|<span data-ttu-id="6205d-146">설명</span><span class="sxs-lookup"><span data-stu-id="6205d-146">Description</span></span>|
|---|---|
|[<span data-ttu-id="6205d-147">방법: 컬렉션 이니셜라이저에서 사용되는 확장 메서드 만들기 및 추가</span><span class="sxs-lookup"><span data-stu-id="6205d-147">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|<span data-ttu-id="6205d-148">컬렉션 이니셜라이저의 값으로 컬렉션을 채우는 데 사용될 수 있는 `Add`라는 확장 메서드를 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-148">Shows how to create an extension method called `Add` that can be used to populate a collection with values from a collection initializer.</span></span>|
|[<span data-ttu-id="6205d-149">방법: 컬렉션 이니셜라이저에서 사용되는 컬렉션 만들기</span><span class="sxs-lookup"><span data-stu-id="6205d-149">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)|<span data-ttu-id="6205d-150">`IEnumerable`을 구현하는 컬렉션 클래스에 `Add` 메서드를 포함하여 컬렉션 이니셜라이저를 사용할 수 있도록 설정하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6205d-150">Shows how to enable use of a collection initializer by including an `Add` method in a collection class that implements `IEnumerable`.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6205d-151">추가 정보</span><span class="sxs-lookup"><span data-stu-id="6205d-151">See also</span></span>

- [<span data-ttu-id="6205d-152">컬렉션</span><span class="sxs-lookup"><span data-stu-id="6205d-152">Collections</span></span>](../../concepts/collections.md)
- [<span data-ttu-id="6205d-153">배열</span><span class="sxs-lookup"><span data-stu-id="6205d-153">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="6205d-154">개체 이니셜라이저: 명명된 형식 및 무명 형식</span><span class="sxs-lookup"><span data-stu-id="6205d-154">Object Initializers: Named and Anonymous Types</span></span>](../objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="6205d-155">New 연산자</span><span class="sxs-lookup"><span data-stu-id="6205d-155">New Operator</span></span>](../../../language-reference/operators/new-operator.md)
- [<span data-ttu-id="6205d-156">자동으로 구현된 속성</span><span class="sxs-lookup"><span data-stu-id="6205d-156">Auto-Implemented Properties</span></span>](../procedures/auto-implemented-properties.md)
- [<span data-ttu-id="6205d-157">방법: Visual Basic에서 배열 변수 초기화</span><span class="sxs-lookup"><span data-stu-id="6205d-157">How to: Initialize an Array Variable in Visual Basic</span></span>](../arrays/how-to-initialize-an-array-variable.md)
- [<span data-ttu-id="6205d-158">지역 형식 유추</span><span class="sxs-lookup"><span data-stu-id="6205d-158">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="6205d-159">익명 형식</span><span class="sxs-lookup"><span data-stu-id="6205d-159">Anonymous Types</span></span>](../objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="6205d-160">Visual Basic의 LINQ 소개</span><span class="sxs-lookup"><span data-stu-id="6205d-160">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="6205d-161">방법: 항목 목록 만들기</span><span class="sxs-lookup"><span data-stu-id="6205d-161">How to: Create a List of Items</span></span>](../../concepts/linq/how-to-create-a-list-of-items.md)
