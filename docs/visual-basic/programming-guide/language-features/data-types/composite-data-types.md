---
description: '자세한 정보: 복합 데이터 형식 (Visual Basic)'
title: 복합 데이터 형식
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 981ee36c416f2524be155b1238f5b306c98aa92b
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456434"
---
# <a name="composite-data-types-visual-basic"></a><span data-ttu-id="57734-103">복합 데이터 형식(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="57734-103">Composite Data Types (Visual Basic)</span></span>

<span data-ttu-id="57734-104">기본 데이터 형식 Visual Basic 제공 하는 것 외에도 다양 한 형식의 항목을 조합 하 여 구조, 배열 및 클래스와 같은 *복합 데이터 형식을* 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-104">In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes.</span></span> <span data-ttu-id="57734-105">기본 형식 및 다른 복합 형식에서 복합 데이터 형식을 빌드할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-105">You can build composite data types from elementary types and from other composite types.</span></span> <span data-ttu-id="57734-106">예를 들어 구조체 요소 배열 또는 배열 멤버가 포함 된 구조체를 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-106">For example, you can define an array of structure elements, or a structure with array members.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="57734-107">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="57734-107">Data Types</span></span>  

 <span data-ttu-id="57734-108">복합 형식은 해당 구성 요소의 데이터 형식과 다릅니다.</span><span class="sxs-lookup"><span data-stu-id="57734-108">A composite type is different from the data type of any of its components.</span></span> <span data-ttu-id="57734-109">예를 들어 `Integer` 요소 배열은 `Integer` 데이터 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="57734-109">For example, an array of `Integer` elements is not of the `Integer` data type.</span></span>  
  
 <span data-ttu-id="57734-110">배열 데이터 형식은 일반적으로 필요에 따라 요소 형식, 괄호 및 쉼표를 사용 하 여 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57734-110">An array data type is normally represented using the element type, parentheses, and commas as necessary.</span></span> <span data-ttu-id="57734-111">예를 들어, 요소의 1 차원 배열은 `String` 로 표시 되 `String()` 고 요소의 2 차원 배열은 `Boolean` 로 표시 됩니다 `Boolean(,)` .</span><span class="sxs-lookup"><span data-stu-id="57734-111">For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.</span></span>  
  
## <a name="structure-types"></a><span data-ttu-id="57734-112">구조체 형식</span><span class="sxs-lookup"><span data-stu-id="57734-112">Structure Types</span></span>  

 <span data-ttu-id="57734-113">모든 구조를 구성 하는 단일 데이터 형식은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-113">There is no single data type comprising all structures.</span></span> <span data-ttu-id="57734-114">대신 두 구조체가 동일한 요소를 동일한 순서로 정의 하더라도 구조체의 각 정의는 고유한 데이터 형식을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="57734-114">Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order.</span></span> <span data-ttu-id="57734-115">그러나 동일한 구조에서 둘 이상의 인스턴스를 만들 경우 Visual Basic는 동일한 데이터 형식으로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="57734-115">However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.</span></span>  
  
## <a name="tuples"></a><span data-ttu-id="57734-116">튜플</span><span class="sxs-lookup"><span data-stu-id="57734-116">Tuples</span></span>

<span data-ttu-id="57734-117">튜플은 미리 정의 된 형식이 있는 두 개 이상의 필드를 포함 하는 간단한 구조입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-117">A tuple is a lightweight structure that contains two or more fields whose types are predefined.</span></span> <span data-ttu-id="57734-118">튜플은 Visual Basic 2017부터 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57734-118">Tuples are supported starting with Visual Basic 2017.</span></span> <span data-ttu-id="57734-119">튜플은 참조로 인수를 전달 하거나 더 많은 중량 클래스 또는 구조체에서 반환 된 필드를 패키지할 필요 없이 단일 메서드 호출에서 여러 값을 반환 하는 데 가장 일반적으로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57734-119">Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure.</span></span> <span data-ttu-id="57734-120">튜플에 대 한 자세한 내용은 [튜플](tuples.md) 항목을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57734-120">See the [Tuples](tuples.md) topic for more information on tuples.</span></span>

## <a name="array-types"></a><span data-ttu-id="57734-121">배열 유형</span><span class="sxs-lookup"><span data-stu-id="57734-121">Array Types</span></span>  

 <span data-ttu-id="57734-122">모든 배열을 구성 하는 단일 데이터 형식은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-122">There is no single data type comprising all arrays.</span></span> <span data-ttu-id="57734-123">배열의 특정 인스턴스에 대 한 데이터 형식은 다음에 의해 결정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57734-123">The data type of a particular instance of an array is determined by the following:</span></span>  
  
- <span data-ttu-id="57734-124">배열이 되는 사실입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-124">The fact of being an array</span></span>  
  
- <span data-ttu-id="57734-125">배열의 순위 (차원의 수)입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-125">The rank (number of dimensions) of the array</span></span>  
  
- <span data-ttu-id="57734-126">배열의 요소 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-126">The element type of the array</span></span>  
  
 <span data-ttu-id="57734-127">특히 지정 된 차원의 길이는 인스턴스의 데이터 형식에 포함 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-127">In particular, the length of a given dimension is not part of the instance's data type.</span></span> <span data-ttu-id="57734-128">다음은 이에 대한 예입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-128">The following example illustrates this.</span></span>  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 <span data-ttu-id="57734-129">위의 예제에서 배열 변수 `arrayA` 및 `arrayB` 은 `Byte()` 다른 길이로 초기화 되더라도 동일한 데이터 형식으로 간주 됩니다.</span><span class="sxs-lookup"><span data-stu-id="57734-129">In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths.</span></span> <span data-ttu-id="57734-130">변수와 `arrayB` `arrayC` 의 요소 형식이 다르기 때문에 동일한 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="57734-130">Variables `arrayB` and `arrayC` are not of the same type because their element types are different.</span></span> <span data-ttu-id="57734-131">및 변수는 `arrayC` `arrayD` 순위가 다르기 때문에 동일한 형식이 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="57734-131">Variables `arrayC` and `arrayD` are not of the same type because their ranks are different.</span></span> <span data-ttu-id="57734-132">`arrayD` `arrayE` `Short(,)` 가 아직 초기화 되지 않은 경우에도의 순위 및 요소 형식은 동일 하기 때문에 및 변수는 동일한 형식 `arrayD` 입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-132">Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.</span></span>  
  
 <span data-ttu-id="57734-133">배열에 대 한 자세한 내용은 [배열](../arrays/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57734-133">For more information on arrays, see [Arrays](../arrays/index.md).</span></span>  
  
## <a name="class-types"></a><span data-ttu-id="57734-134">클래스 형식</span><span class="sxs-lookup"><span data-stu-id="57734-134">Class Types</span></span>  

 <span data-ttu-id="57734-135">모든 클래스를 구성 하는 단일 데이터 형식은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="57734-135">There is no single data type comprising all classes.</span></span> <span data-ttu-id="57734-136">한 클래스가 다른 클래스에서 상속 될 수 있지만 각 클래스는 별도의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-136">Although one class can inherit from another class, each is a separate data type.</span></span> <span data-ttu-id="57734-137">동일한 클래스의 여러 인스턴스는 동일한 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="57734-137">Multiple instances of the same class are of the same data type.</span></span> <span data-ttu-id="57734-138">한 클래스 인스턴스 변수를 다른 클래스에 할당 하는 경우 데이터 형식이 같을 뿐만 아니라 메모리의 동일한 클래스 인스턴스를 가리킵니다.</span><span class="sxs-lookup"><span data-stu-id="57734-138">If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.</span></span>  
  
 <span data-ttu-id="57734-139">클래스에 대 한 자세한 내용은 [개체 및 클래스](../objects-and-classes/index.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="57734-139">For more information on classes, see [Objects and Classes](../objects-and-classes/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57734-140">추가 정보</span><span class="sxs-lookup"><span data-stu-id="57734-140">See also</span></span>

- [<span data-ttu-id="57734-141">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="57734-141">Data Types</span></span>](index.md)
- [<span data-ttu-id="57734-142">기본 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="57734-142">Elementary Data Types</span></span>](elementary-data-types.md)
- [<span data-ttu-id="57734-143">Visual Basic의 제네릭 형식</span><span class="sxs-lookup"><span data-stu-id="57734-143">Generic Types in Visual Basic</span></span>](generic-types.md)
- [<span data-ttu-id="57734-144">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="57734-144">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="57734-145">Visual Basic의 형식 변환</span><span class="sxs-lookup"><span data-stu-id="57734-145">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="57734-146">구조체</span><span class="sxs-lookup"><span data-stu-id="57734-146">Structures</span></span>](structures.md)
- [<span data-ttu-id="57734-147">데이터 형식 문제 해결</span><span class="sxs-lookup"><span data-stu-id="57734-147">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="57734-148">방법: 변수에 두 개 이상의 값 사용</span><span class="sxs-lookup"><span data-stu-id="57734-148">How to: Hold More Than One Value in a Variable</span></span>](how-to-hold-more-than-one-value-in-a-variable.md)
