---
description: '자세한 정보: Dim 문 (Visual Basic)'
title: Dim 문
ms.date: 05/12/2018
f1_keywords:
- vb.Dim
- Dim
helpviewer_keywords:
- Public keyword [Visual Basic], in Dim statement
- Dim statement [Visual Basic]
- fixed-length strings [Visual Basic], declaring
- variables [Visual Basic], declaring
- WithEvents keyword [Visual Basic], Dim statement
- dynamic arrays [Visual Basic], Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields [Visual Basic], as member variables
- declarations [Visual Basic], dynamic arrays
- member variables [Visual Basic]
- default values [Visual Basic]
- data types [Visual Basic], assigning
- braces {}
- As keyword [Visual Basic], in Dim statement
- arrays [Visual Basic], declaring
- New keyword [Visual Basic], Dim statement
- To keyword [Visual Basic], in Dim statement
- storage [Visual Basic], allocating
- local variables [Visual Basic]
- declaration statements [Visual Basic]
- Dim statement [Visual Basic], syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
ms.openlocfilehash: b950ae95af01be4e064ac9177300f144e0cc08b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795198"
---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="9a231-103">Dim 문 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a231-103">Dim statement (Visual Basic)</span></span>

<span data-ttu-id="9a231-104">하나 이상의 변수에 대 한 저장소 공간을 선언 하 고 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-104">Declares and allocates storage space for one or more variables.</span></span>

## <a name="syntax"></a><span data-ttu-id="9a231-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9a231-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]
Dim [ WithEvents ] variablelist
```

## <a name="parts"></a><span data-ttu-id="9a231-106">부분</span><span class="sxs-lookup"><span data-stu-id="9a231-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="9a231-107">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-107">Optional.</span></span> <span data-ttu-id="9a231-108">[특성 목록](attribute-list.md)을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a231-108">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="9a231-109">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-109">Optional.</span></span> <span data-ttu-id="9a231-110">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-110">Can be one of the following:</span></span>

  - [<span data-ttu-id="9a231-111">공용</span><span class="sxs-lookup"><span data-stu-id="9a231-111">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="9a231-112">보호됨</span><span class="sxs-lookup"><span data-stu-id="9a231-112">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="9a231-113">Friend</span><span class="sxs-lookup"><span data-stu-id="9a231-113">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="9a231-114">개인</span><span class="sxs-lookup"><span data-stu-id="9a231-114">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="9a231-115">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="9a231-115">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="9a231-116">비공개 보호</span><span class="sxs-lookup"><span data-stu-id="9a231-116">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="9a231-117">[Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-117">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `Shared`

  <span data-ttu-id="9a231-118">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-118">Optional.</span></span> <span data-ttu-id="9a231-119">[공유](../modifiers/shared.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-119">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="9a231-120">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-120">Optional.</span></span> <span data-ttu-id="9a231-121">[그림자](../modifiers/shadows.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-121">See [Shadows](../modifiers/shadows.md).</span></span>

- `Static`

  <span data-ttu-id="9a231-122">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-122">Optional.</span></span> <span data-ttu-id="9a231-123">[Static](../modifiers/static.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-123">See [Static](../modifiers/static.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="9a231-124">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-124">Optional.</span></span> <span data-ttu-id="9a231-125">[ReadOnly](../modifiers/readonly.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-125">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WithEvents`

  <span data-ttu-id="9a231-126">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-126">Optional.</span></span> <span data-ttu-id="9a231-127">이러한 개체 변수가 이벤트를 발생 시킬 수 있는 클래스의 인스턴스를 참조 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-127">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="9a231-128">[WithEvents](../modifiers/withevents.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-128">See [WithEvents](../modifiers/withevents.md).</span></span>

- `variablelist`

  <span data-ttu-id="9a231-129">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-129">Required.</span></span> <span data-ttu-id="9a231-130">이 문에서 선언 되는 변수의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-130">List of variables being declared in this statement.</span></span>

  `variable [ , variable ... ]`

  <span data-ttu-id="9a231-131">각 `variable`에는 다음과 같은 구문과 요소가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-131">Each `variable` has the following syntax and parts:</span></span>

  <span data-ttu-id="9a231-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="9a231-132">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>

  |<span data-ttu-id="9a231-133">파트</span><span class="sxs-lookup"><span data-stu-id="9a231-133">Part</span></span>|<span data-ttu-id="9a231-134">설명</span><span class="sxs-lookup"><span data-stu-id="9a231-134">Description</span></span>|
  |---|---|
  |`variablename`|<span data-ttu-id="9a231-135">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-135">Required.</span></span> <span data-ttu-id="9a231-136">변수의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-136">Name of the variable.</span></span> <span data-ttu-id="9a231-137">[Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-137">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
  |`boundslist`|<span data-ttu-id="9a231-138">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-138">Optional.</span></span> <span data-ttu-id="9a231-139">배열 변수의 각 차원에 대 한 범위 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-139">List of bounds of each dimension of an array variable.</span></span>|
  |`New`|<span data-ttu-id="9a231-140">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-140">Optional.</span></span> <span data-ttu-id="9a231-141">문이 실행 될 때 클래스의 새 인스턴스를 만듭니다 `Dim` .</span><span class="sxs-lookup"><span data-stu-id="9a231-141">Creates a new instance of the class when the `Dim` statement runs.</span></span>|
  |`datatype`|<span data-ttu-id="9a231-142">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-142">Optional.</span></span> <span data-ttu-id="9a231-143">변수의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-143">Data type of the variable.</span></span>|
  |`With`|<span data-ttu-id="9a231-144">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-144">Optional.</span></span> <span data-ttu-id="9a231-145">개체 이니셜라이저 목록을 소개 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-145">Introduces the object initializer list.</span></span>|
  |`propertyname`|<span data-ttu-id="9a231-146">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-146">Optional.</span></span> <span data-ttu-id="9a231-147">인스턴스를 만드는 클래스의 속성 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-147">The name of a property in the class you are making an instance of.</span></span>|
  |`propinitializer`|<span data-ttu-id="9a231-148">= 이후에 필요 `propertyname` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-148">Required after `propertyname` =.</span></span> <span data-ttu-id="9a231-149">평가 되 고 속성 이름에 할당 되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-149">The expression that is evaluated and assigned to the property name.</span></span>|
  |`initializer`|<span data-ttu-id="9a231-150">`New`가 지정 되지 않은 경우 선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-150">Optional if `New` is not specified.</span></span> <span data-ttu-id="9a231-151">식이 생성 될 때 계산 되어 변수에 할당 되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-151">Expression that is evaluated and assigned to the variable when it is created.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9a231-152">설명</span><span class="sxs-lookup"><span data-stu-id="9a231-152">Remarks</span></span>

<span data-ttu-id="9a231-153">Visual Basic 컴파일러는 문을 사용 하 여 변수의 `Dim` 데이터 형식 및 변수에 액세스할 수 있는 코드와 같은 기타 정보를 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-153">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="9a231-154">다음 예에서는 변수를 선언 하 여 값을 저장 합니다 `Integer` .</span><span class="sxs-lookup"><span data-stu-id="9a231-154">The following example declares a variable to hold an `Integer` value.</span></span>

```vb
Dim numberOfStudents As Integer
```

<span data-ttu-id="9a231-155">모든 데이터 형식 또는 열거형, 구조체, 클래스 또는 인터페이스의 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-155">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

```vb
Dim finished As Boolean
Dim monitorBox As System.Windows.Forms.Form
```

<span data-ttu-id="9a231-156">참조 형식의 경우 키워드를 사용 하 여 `New` 데이터 형식으로 지정 된 클래스 또는 구조체의 새 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-156">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="9a231-157">를 사용 하 `New` 는 경우 이니셜라이저 식을 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-157">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="9a231-158">대신, 필요한 경우 변수를 만들 클래스의 생성자에 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-158">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>

```vb
Dim bottomLabel As New System.Windows.Forms.Label
```

<span data-ttu-id="9a231-159">프로시저, 블록, 클래스, 구조체 또는 모듈에서 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-159">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="9a231-160">소스 파일, 네임 스페이스 또는 인터페이스에서는 변수를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-160">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="9a231-161">자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](declaration-contexts-and-default-access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-161">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="9a231-162">프로시저 외부에서 모듈 수준에 선언 된 변수는 *멤버 변수* 또는 *필드* 입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-162">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="9a231-163">멤버 변수는 클래스, 구조체 또는 모듈 전체의 범위에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-163">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="9a231-164">프로시저 수준에서 선언 된 변수는 *지역 변수* 입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-164">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="9a231-165">지역 변수는 해당 프로시저 또는 블록 내 에서만 범위 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-165">Local variables are in scope only within their procedure or block.</span></span>

<span data-ttu-id="9a231-166">프로시저 외부에서 변수를 선언 하는 데 사용 되는 액세스 한정자는 `Public` ,, `Protected` `Friend` , `Protected Friend` 및 `Private` 입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-166">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="9a231-167">자세한 내용은 [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-167">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="9a231-168">,,,,,,,, `Dim` `Public` `Protected` `Friend` `Protected Friend` `Private` `Shared` `Shadows` `Static` `ReadOnly` 또는 `WithEvents` 한정자를 지정 하는 경우 키워드는 선택 사항이 며 일반적으로 생략 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-168">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>

```vb
Public maximumAllowed As Double
Protected Friend currentUserName As String
Private salary As Decimal
Static runningTotal As Integer
```

<span data-ttu-id="9a231-169">`Option Explicit`가 on (기본값) 이면 컴파일러에서 사용 하는 모든 변수에 대 한 선언이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-169">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="9a231-170">자세한 내용은 [Option Explicit 문](option-explicit-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-170">For more information, see [Option Explicit Statement](option-explicit-statement.md).</span></span>

## <a name="specifying-an-initial-value"></a><span data-ttu-id="9a231-171">초기 값 지정</span><span class="sxs-lookup"><span data-stu-id="9a231-171">Specifying an initial value</span></span>

<span data-ttu-id="9a231-172">변수를 만들 때 변수에 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-172">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="9a231-173">값 형식의 경우 *이니셜라이저* 를 사용 하 여 변수에 할당 되는 식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-173">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="9a231-174">식은 컴파일 시간에 계산 될 수 있는 상수로 계산 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-174">The expression must evaluate to a constant that can be calculated at compile time.</span></span>

```vb
Dim quantity As Integer = 10
Dim message As String = "Just started"
```

<span data-ttu-id="9a231-175">이니셜라이저가 지정 되 고 절에 데이터 형식이 지정 되지 않은 경우 `As` *형식 유추* 를 사용 하 여 이니셜라이저의 데이터 형식을 유추 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-175">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="9a231-176">다음 예제에서 `num1` 및 `num2` 는 모두 정수로 강력 하 게 형식화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-176">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="9a231-177">두 번째 선언에서 형식 유추는 값 3에서 형식을 유추 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-177">In the second declaration, type inference infers the type from the value 3.</span></span>

```vb
' Use explicit typing.
Dim num1 As Integer = 3

' Use local type inference.
Dim num2 = 3
```

<span data-ttu-id="9a231-178">형식 유추는 프로시저 수준에서 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-178">Type inference applies at the procedure level.</span></span> <span data-ttu-id="9a231-179">클래스, 구조체, 모듈 또는 인터페이스의 프로시저 외부에는 적용 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-179">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="9a231-180">형식 유추에 대 한 자세한 내용은 [Option 유추 문](option-infer-statement.md) 및 [지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-180">For more information about type inference, see [Option Infer Statement](option-infer-statement.md) and [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span>

<span data-ttu-id="9a231-181">데이터 형식 또는 이니셜라이저가 지정 되지 않은 경우 발생 하는 상황에 대 한 자세한 내용은이 항목의 뒷부분에 나오는 [기본 데이터 형식 및 값](dim-statement.md#default) 을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="9a231-181">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](dim-statement.md#default) later in this topic.</span></span>

<span data-ttu-id="9a231-182">*개체 이니셜라이저* 를 사용 하 여 명명 된 형식과 익명 형식의 인스턴스를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-182">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="9a231-183">다음 코드에서는 클래스의 인스턴스를 만들고 `Student` 개체 이니셜라이저를 사용 하 여 속성을 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-183">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>

```vb
Dim student1 As New Student With {.First = "Michael",
                                  .Last = "Tucker"}
```

<span data-ttu-id="9a231-184">개체 이니셜라이저에 대 한 자세한 내용은 [방법: 개체 이니셜라이저를 사용 하 여 개체 선언](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [개체 이니셜라이저: 명명 된 형식과 익명 형식](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)및 [익명 형식](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-184">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>

## <a name="declaring-multiple-variables"></a><span data-ttu-id="9a231-185">여러 변수 선언</span><span class="sxs-lookup"><span data-stu-id="9a231-185">Declaring multiple variables</span></span>

<span data-ttu-id="9a231-186">하나의 선언문에서 여러 변수를 선언 하 고 각각에 대 한 변수 이름을 지정 하 고 괄호를 사용 하 여 각 배열 이름을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-186">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="9a231-187">여러 변수는 쉼표로 구분됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-187">Multiple variables are separated by commas.</span></span>

```vb
Dim lastTime, nextTime, allTimes() As Date
```

<span data-ttu-id="9a231-188">절이 한 개 이상 있는 변수를 선언 하 `As` 는 경우 해당 변수 그룹에 대 한 이니셜라이저를 제공할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-188">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>

<span data-ttu-id="9a231-189">`As`선언 하는 각 변수에 대해 별도의 절을 사용 하 여 서로 다른 변수에 대해 서로 다른 데이터 형식을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-189">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="9a231-190">각 변수는 해당 부분 뒤에 오는 첫 번째 절에 지정 된 데이터 형식을 사용 합니다 `As` `variablename` .</span><span class="sxs-lookup"><span data-stu-id="9a231-190">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>

```vb
Dim a, b, c As Single, x, y As Double, i As Integer
' a, b, and c are all Single; x and y are both Double
```

## <a name="arrays"></a><span data-ttu-id="9a231-191">배열</span><span class="sxs-lookup"><span data-stu-id="9a231-191">Arrays</span></span>

<span data-ttu-id="9a231-192">여러 값이 포함 될 수 있는 *배열을* 포함 하는 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-192">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="9a231-193">변수가 배열을 포함 하도록 지정 하려면 괄호를 사용 하 여 바로 뒤에를 추가 합니다 `variablename` .</span><span class="sxs-lookup"><span data-stu-id="9a231-193">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="9a231-194">배열에 대한 자세한 내용은 [배열](../../programming-guide/language-features/arrays/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-194">For more information about arrays, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="9a231-195">배열의 각 차원에 대 한 하 한과 상한을 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-195">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="9a231-196">이렇게 하려면 괄호 안에를 포함 `boundslist` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-196">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="9a231-197">각 차원에 대해는 `boundslist` 상한을 지정 하 고 선택적으로 하한값을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-197">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="9a231-198">지정 여부에 관계 없이 하한값은 항상 0입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-198">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="9a231-199">각 인덱스는 0부터 상한 값까지 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-199">Each index can vary from zero through its upper bound value.</span></span>

<span data-ttu-id="9a231-200">다음 두 문은 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-200">The following two statements are equivalent.</span></span> <span data-ttu-id="9a231-201">각 문은 21 개 요소의 배열을 선언 `Integer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-201">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="9a231-202">배열에 액세스할 때 인덱스는 0부터 20까지 달라질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-202">When you access the array, the index can vary from 0 through 20.</span></span>

```vb
Dim totals(20) As Integer
Dim totals(0 To 20) As Integer
```

<span data-ttu-id="9a231-203">다음 문은 형식의 2 차원 배열을 선언 합니다 `Double` .</span><span class="sxs-lookup"><span data-stu-id="9a231-203">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="9a231-204">배열에는 각각 6 개의 행 (5 + 1)이 있습니다 (5 + 1).</span><span class="sxs-lookup"><span data-stu-id="9a231-204">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="9a231-205">상한은 차원의 길이가 아니라 인덱스에 사용할 수 있는 가장 높은 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-205">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="9a231-206">차원의 길이는 상한에 1을 더한 값입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-206">The length of the dimension is the upper bound plus one.</span></span>

```vb
Dim matrix2(3, 5) As Double
```

<span data-ttu-id="9a231-207">배열은 1 ~ 32 차원을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-207">An array can have from 1 to 32 dimensions.</span></span>

<span data-ttu-id="9a231-208">배열 선언에서 모든 범위를 비워 둘 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-208">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="9a231-209">이렇게 하면 배열에 지정 된 차원 수가 있지만 초기화 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-209">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="9a231-210">`Nothing`하나 이상의 요소를 초기화할 때까지 값은입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-210">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="9a231-211">`Dim`문은 모든 차원에 대해 범위를 지정 하거나 차원 없이 범위를 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-211">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>

```vb
' Declare an array with blank array bounds.
Dim messages() As String
' Initialize the array.
ReDim messages(4)
```

<span data-ttu-id="9a231-212">배열에 둘 이상의 차원이 있는 경우 괄호 사이에 쉼표를 포함 하 여 차원 수를 나타내야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-212">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>

```vb
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte
```

<span data-ttu-id="9a231-213">배열의 차원 중 하나를-1로 선언 하 여 *길이가 0 인 배열을* 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-213">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="9a231-214">길이가 0 인 배열을 포함 하는 변수에는 값이 없습니다 `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="9a231-214">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="9a231-215">특정 공용 언어 런타임 함수에는 길이가 0 인 배열이 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-215">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="9a231-216">이러한 배열에 액세스 하려고 하면 런타임 예외가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-216">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="9a231-217">자세한 내용은 [배열](../../programming-guide/language-features/arrays/index.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-217">For more information, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

<span data-ttu-id="9a231-218">배열 리터럴을 사용 하 여 배열 값을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-218">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="9a231-219">이렇게 하려면 초기화 값을 중괄호 ()로 묶습니다 `{}` .</span><span class="sxs-lookup"><span data-stu-id="9a231-219">To do this, surround the initialization values with braces (`{}`).</span></span>

```vb
Dim longArray() As Long = {0, 1, 2, 3}
```

<span data-ttu-id="9a231-220">다차원 배열의 경우 각 개별 차원에 대 한 초기화는 외부 차원에서 중괄호로 묶입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-220">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="9a231-221">요소는 행 중심 순서로 지정 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-221">The elements are specified in row-major order.</span></span>

```vb
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}
```

<span data-ttu-id="9a231-222">배열 리터럴에 대 한 자세한 내용은 [배열](../../programming-guide/language-features/arrays/index.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-222">For more information about array literals, see [Arrays](../../programming-guide/language-features/arrays/index.md).</span></span>

## <a name="default-data-types-and-values"></a><a name="default"></a> <span data-ttu-id="9a231-223">기본 데이터 형식 및 값</span><span class="sxs-lookup"><span data-stu-id="9a231-223">Default data types and values</span></span>

<span data-ttu-id="9a231-224">다음 테이블에는 `Dim` 문에서 데이터 형식과 이니셜라이저를 지정하는 다양한 조합의 결과에 대한 설명이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-224">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>

|<span data-ttu-id="9a231-225">데이터 형식 지정 여부</span><span class="sxs-lookup"><span data-stu-id="9a231-225">Data type specified?</span></span>|<span data-ttu-id="9a231-226">이니셜라이저 지정 여부</span><span class="sxs-lookup"><span data-stu-id="9a231-226">Initializer specified?</span></span>|<span data-ttu-id="9a231-227">예제</span><span class="sxs-lookup"><span data-stu-id="9a231-227">Example</span></span>|<span data-ttu-id="9a231-228">결과</span><span class="sxs-lookup"><span data-stu-id="9a231-228">Result</span></span>|
|---|---|---|---|
|<span data-ttu-id="9a231-229">아니요</span><span class="sxs-lookup"><span data-stu-id="9a231-229">No</span></span>|<span data-ttu-id="9a231-230">아니요</span><span class="sxs-lookup"><span data-stu-id="9a231-230">No</span></span>|`Dim qty`|<span data-ttu-id="9a231-231">[Option Strict](option-strict-statement.md) 가 off로 설정 된 경우 (기본값) 변수는로 설정 됩니다 `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="9a231-231">If [Option Strict](option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="9a231-232">`Option Strict`가 on이면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-232">If `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="9a231-233">아니요</span><span class="sxs-lookup"><span data-stu-id="9a231-233">No</span></span>|<span data-ttu-id="9a231-234">예</span><span class="sxs-lookup"><span data-stu-id="9a231-234">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="9a231-235">[유추 옵션](option-infer-statement.md) (기본값)이 설정 된 경우 변수는 이니셜라이저의 데이터 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-235">If [Option Infer](option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="9a231-236">[지역 형식 유추](../../programming-guide/language-features/variables/local-type-inference.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-236">See [Local Type Inference](../../programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="9a231-237">`Option Infer`가 off이고 `Option Strict`고 off이면 변수가 `Object`의 데이터 형식을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-237">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="9a231-238">`Option Infer`가 off이고 `Option Strict`는 on이면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-238">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|
|<span data-ttu-id="9a231-239">예</span><span class="sxs-lookup"><span data-stu-id="9a231-239">Yes</span></span>|<span data-ttu-id="9a231-240">아니요</span><span class="sxs-lookup"><span data-stu-id="9a231-240">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="9a231-241">변수는 데이터 형식의 기본값으로 초기화됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-241">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="9a231-242">이 단원의 뒷부분에 나오는 표를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-242">See the table later in this section.</span></span>|
|<span data-ttu-id="9a231-243">예</span><span class="sxs-lookup"><span data-stu-id="9a231-243">Yes</span></span>|<span data-ttu-id="9a231-244">예</span><span class="sxs-lookup"><span data-stu-id="9a231-244">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="9a231-245">이니셜라이저의 데이터 형식을 지정한 데이터 형식으로 변환할 수 없으면 컴파일 시간 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-245">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|

<span data-ttu-id="9a231-246">데이터 형식을 지정 하지만 이니셜라이저를 지정 하지 않는 경우 Visual Basic는 변수를 해당 데이터 형식에 대 한 기본값으로 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-246">If you specify a data type but do not specify an initializer, Visual Basic initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="9a231-247">다음 표에서는 기본 초기화 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-247">The following table shows the default initialization values.</span></span>

|<span data-ttu-id="9a231-248">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="9a231-248">Data type</span></span>|<span data-ttu-id="9a231-249">기본값</span><span class="sxs-lookup"><span data-stu-id="9a231-249">Default value</span></span>|
|---|---|
|<span data-ttu-id="9a231-250">모든 숫자 형식 ( `Byte` 및 포함 `SByte` )</span><span class="sxs-lookup"><span data-stu-id="9a231-250">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="9a231-251">0</span><span class="sxs-lookup"><span data-stu-id="9a231-251">0</span></span>|
|`Char`|<span data-ttu-id="9a231-252">이진 0</span><span class="sxs-lookup"><span data-stu-id="9a231-252">Binary 0</span></span>|
|<span data-ttu-id="9a231-253">모든 참조 형식 ( `Object` , `String` 및 모든 배열 포함)</span><span class="sxs-lookup"><span data-stu-id="9a231-253">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|
|`Boolean`|`False`|
|`Date`|<span data-ttu-id="9a231-254">1 년 1 월 1 일 오전 12:00 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="9a231-254">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|

<span data-ttu-id="9a231-255">구조체의 각 요소는 개별 변수인 것 처럼 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-255">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="9a231-256">배열의 길이를 선언 하지만 요소를 초기화 하지 않는 경우 각 요소는 개별 변수인 것 처럼 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-256">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>

## <a name="static-local-variable-lifetime"></a><span data-ttu-id="9a231-257">정적 지역 변수 수명</span><span class="sxs-lookup"><span data-stu-id="9a231-257">Static local variable lifetime</span></span>

<span data-ttu-id="9a231-258">`Static`지역 변수는 변수가 선언 된 프로시저 보다 수명이 깁니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-258">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="9a231-259">변수의 수명 범위는 프로시저가 선언 되는 위치 및이의 여부에 따라 달라 집니다 `Shared` .</span><span class="sxs-lookup"><span data-stu-id="9a231-259">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>

|<span data-ttu-id="9a231-260">프로시저 선언</span><span class="sxs-lookup"><span data-stu-id="9a231-260">Procedure declaration</span></span>|<span data-ttu-id="9a231-261">변수가 초기화 됨</span><span class="sxs-lookup"><span data-stu-id="9a231-261">Variable initialized</span></span>|<span data-ttu-id="9a231-262">변수가 기존에 중지 됨</span><span class="sxs-lookup"><span data-stu-id="9a231-262">Variable stops existing</span></span>|
|---|---|---|
|<span data-ttu-id="9a231-263">모듈에서</span><span class="sxs-lookup"><span data-stu-id="9a231-263">In a module</span></span>|<span data-ttu-id="9a231-264">프로시저가 처음 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="9a231-264">The first time the procedure is called</span></span>|<span data-ttu-id="9a231-265">프로그램 실행이 중지 되는 경우</span><span class="sxs-lookup"><span data-stu-id="9a231-265">When your program stops execution</span></span>|
|<span data-ttu-id="9a231-266">클래스 또는 구조체에서 프로시저는 `Shared`</span><span class="sxs-lookup"><span data-stu-id="9a231-266">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="9a231-267">프로시저가 특정 인스턴스나 클래스 또는 구조체 자체에서 처음 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="9a231-267">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="9a231-268">프로그램 실행이 중지 되는 경우</span><span class="sxs-lookup"><span data-stu-id="9a231-268">When your program stops execution</span></span>|
|<span data-ttu-id="9a231-269">클래스 또는 구조체에서 프로시저는 그렇지 않습니다. `Shared`</span><span class="sxs-lookup"><span data-stu-id="9a231-269">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="9a231-270">프로시저가 특정 인스턴스에서 처음으로 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="9a231-270">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="9a231-271">GC (가비지 수집)를 위해 인스턴스를 해제 하는 경우</span><span class="sxs-lookup"><span data-stu-id="9a231-271">When the instance is released for garbage collection (GC)</span></span>|

## <a name="attributes-and-modifiers"></a><span data-ttu-id="9a231-272">특성 및 한정자</span><span class="sxs-lookup"><span data-stu-id="9a231-272">Attributes and modifiers</span></span>

<span data-ttu-id="9a231-273">지역 변수가 아니라 멤버 변수에만 특성을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-273">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="9a231-274">특성은 어셈블리의 메타 데이터에 정보를 제공 하며,이는 로컬 변수와 같은 임시 저장소에는 의미가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-274">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>

<span data-ttu-id="9a231-275">모듈 수준에서 한정자를 사용 하 여 `Static` 멤버 변수를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-275">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="9a231-276">프로시저 수준에서 `Shared` ,, `Shadows` `ReadOnly` , `WithEvents` 또는 액세스 한정자를 사용 하 여 지역 변수를 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-276">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>

<span data-ttu-id="9a231-277">를 제공 하 여 변수에 액세스할 수 있는 코드를 지정할 수 있습니다 `accessmodifier` .</span><span class="sxs-lookup"><span data-stu-id="9a231-277">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="9a231-278">클래스 및 모듈 멤버 변수 (프로시저 외부)는 기본적으로 private access로, 구조체 멤버 변수의 기본값은 공용 액세스입니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-278">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="9a231-279">액세스 한정자를 사용 하 여 액세스 수준을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-279">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="9a231-280">프로시저 내에서 지역 변수에 액세스 한정자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-280">You cannot use access modifiers on local variables (inside a procedure).</span></span>

<span data-ttu-id="9a231-281">`WithEvents`프로시저 내의 지역 변수가 아니라 멤버 변수에만 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-281">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="9a231-282">을 지정 하는 경우 `WithEvents` 변수의 데이터 형식은가 아닌 특정 클래스 형식 이어야 합니다 `Object` .</span><span class="sxs-lookup"><span data-stu-id="9a231-282">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="9a231-283">를 사용 하 여 배열을 선언할 수 없습니다 `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="9a231-283">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="9a231-284">이벤트에 대 한 자세한 내용은 [이벤트](../../programming-guide/language-features/events/index.md)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-284">For more information about events, see [Events](../../programming-guide/language-features/events/index.md).</span></span>

> [!NOTE]
> <span data-ttu-id="9a231-285">클래스, 구조체 또는 모듈 외부의 코드는 멤버 변수의 이름을 해당 클래스, 구조체 또는 모듈의 이름으로 한 정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-285">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="9a231-286">프로시저 또는 블록 외부의 코드는 해당 프로시저나 블록 내의 지역 변수를 참조할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-286">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>

## <a name="releasing-managed-resources"></a><span data-ttu-id="9a231-287">관리 되는 리소스 해제</span><span class="sxs-lookup"><span data-stu-id="9a231-287">Releasing managed resources</span></span>

<span data-ttu-id="9a231-288">.NET Framework 가비지 수집기는 파트에서 추가 코딩 없이 관리 되는 리소스를 삭제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-288">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="9a231-289">그러나 가비지 수집기를 대기 하지 않고 관리 되는 리소스를 강제로 삭제할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-289">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

<span data-ttu-id="9a231-290">클래스에서 특히 중요 하 고 부족 한 리소스 (예: 데이터베이스 연결 또는 파일 핸들)를 사용 하는 경우 더 이상 사용 하지 않는 클래스 인스턴스를 정리할 다음 가비지 수집이 끝날 때까지 기다리지 않으려고 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-290">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="9a231-291">클래스는 인터페이스를 구현 <xref:System.IDisposable> 하 여 가비지 수집 전에 리소스를 해제 하는 방법을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-291">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="9a231-292">해당 인터페이스를 구현 하는 클래스는 `Dispose` 중요 한 리소스를 즉시 해제 하기 위해 호출할 수 있는 메서드를 노출 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-292">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>

<span data-ttu-id="9a231-293">`Using`문은 리소스를 확보 하 고, 문 집합을 실행 한 다음 리소스를 삭제 하는 프로세스를 자동화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-293">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="9a231-294">그러나 리소스는 인터페이스를 구현 해야 합니다 <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="9a231-294">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="9a231-295">자세한 내용은 [Using 문](using-statement.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9a231-295">For more information, see [Using Statement](using-statement.md).</span></span>

## <a name="example"></a><span data-ttu-id="9a231-296">예제</span><span class="sxs-lookup"><span data-stu-id="9a231-296">Example</span></span>

<span data-ttu-id="9a231-297">다음 예에서는 `Dim` 문을 여러 옵션과 함께 사용 하 여 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-297">The following example declares variables by using the `Dim` statement with various options.</span></span>

[!code-vb[VbVbalrStatements#141](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#141)]

## <a name="example"></a><span data-ttu-id="9a231-298">예제</span><span class="sxs-lookup"><span data-stu-id="9a231-298">Example</span></span>

<span data-ttu-id="9a231-299">다음 예에서는 1에서 30 사이의 소수를 나열 합니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-299">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="9a231-300">지역 변수의 범위는 코드 설명에 설명 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-300">The scope of local variables is described in code comments.</span></span>

[!code-vb[VbVbalrStatements#142](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#142)]

## <a name="example"></a><span data-ttu-id="9a231-301">예제</span><span class="sxs-lookup"><span data-stu-id="9a231-301">Example</span></span>

<span data-ttu-id="9a231-302">다음 예제에서는 `speedValue` 변수가 클래스 수준에서 선언 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-302">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="9a231-303">`Private`키워드는 변수를 선언 하는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9a231-303">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="9a231-304">이 변수는 클래스의 모든 프로시저에서 액세스할 수 있습니다 `Car` .</span><span class="sxs-lookup"><span data-stu-id="9a231-304">The variable can be accessed by any procedure in the `Car` class.</span></span>

[!code-vb[VbVbalrStatements#144](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#144)]

[!code-vb[VbVbalrStatements#145](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class11.vb#145)]

## <a name="see-also"></a><span data-ttu-id="9a231-305">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9a231-305">See also</span></span>

- [<span data-ttu-id="9a231-306">Const 문</span><span class="sxs-lookup"><span data-stu-id="9a231-306">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="9a231-307">ReDim 문</span><span class="sxs-lookup"><span data-stu-id="9a231-307">ReDim Statement</span></span>](redim-statement.md)
- [<span data-ttu-id="9a231-308">Option Explicit 문</span><span class="sxs-lookup"><span data-stu-id="9a231-308">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="9a231-309">Option Infer 문</span><span class="sxs-lookup"><span data-stu-id="9a231-309">Option Infer Statement</span></span>](option-infer-statement.md)
- [<span data-ttu-id="9a231-310">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="9a231-310">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="9a231-311">프로젝트 디자이너, 컴파일 페이지(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a231-311">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [<span data-ttu-id="9a231-312">변수 선언</span><span class="sxs-lookup"><span data-stu-id="9a231-312">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="9a231-313">배열</span><span class="sxs-lookup"><span data-stu-id="9a231-313">Arrays</span></span>](../../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9a231-314">개체 이니셜라이저: 명명된 형식 및 무명 형식</span><span class="sxs-lookup"><span data-stu-id="9a231-314">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9a231-315">익명 형식</span><span class="sxs-lookup"><span data-stu-id="9a231-315">Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [<span data-ttu-id="9a231-316">개체 이니셜라이저: 명명된 형식 및 무명 형식</span><span class="sxs-lookup"><span data-stu-id="9a231-316">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="9a231-317">방법: 개체 이니셜라이저를 사용하여 개체 선언</span><span class="sxs-lookup"><span data-stu-id="9a231-317">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
- [<span data-ttu-id="9a231-318">지역 형식 유추</span><span class="sxs-lookup"><span data-stu-id="9a231-318">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
