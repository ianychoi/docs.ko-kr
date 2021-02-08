---
description: '자세한 정보: Enum 문 (Visual Basic)'
title: Enum 문
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: dcaf28e949f8d34b8d72b07d8029ea10d6baeabf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769171"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="6f751-103">Enum 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f751-103">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="6f751-104">열거형을 선언 하 고 해당 멤버의 값을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-104">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="6f751-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f751-105">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="6f751-106">부분</span><span class="sxs-lookup"><span data-stu-id="6f751-106">Parts</span></span>

- `attributelist`

  <span data-ttu-id="6f751-107">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-107">Optional.</span></span> <span data-ttu-id="6f751-108">이 열거형에 적용 되는 특성의 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-108">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="6f751-109">[특성 목록을](attribute-list.md) 꺾쇠 괄호 (" `<` " 및 "")로 묶어야 합니다 `>` .</span><span class="sxs-lookup"><span data-stu-id="6f751-109">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="6f751-110"><xref:System.FlagsAttribute>특성은 열거형의 인스턴스 값에 여러 열거형 멤버가 포함 될 수 있고 각 멤버가 열거형 값의 비트 필드를 나타내는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-110">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="6f751-111">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-111">Optional.</span></span> <span data-ttu-id="6f751-112">이 열거형에 액세스할 수 있는 코드를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-112">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="6f751-113">다음 중 하나일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-113">Can be one of the following:</span></span>

  - [<span data-ttu-id="6f751-114">공용</span><span class="sxs-lookup"><span data-stu-id="6f751-114">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="6f751-115">보호됨</span><span class="sxs-lookup"><span data-stu-id="6f751-115">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="6f751-116">Friend</span><span class="sxs-lookup"><span data-stu-id="6f751-116">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="6f751-117">개인</span><span class="sxs-lookup"><span data-stu-id="6f751-117">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="6f751-118">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="6f751-118">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="6f751-119">비공개 보호</span><span class="sxs-lookup"><span data-stu-id="6f751-119">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="6f751-120">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-120">Optional.</span></span> <span data-ttu-id="6f751-121">이 열거형이 기본 클래스에서 동일 하 게 명명 된 프로그래밍 요소 또는 오버 로드 된 요소 집합을 요소가 하 고 숨기도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-121">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="6f751-122">열거형은 해당 멤버가 아니라 열거형 자체 [에서만 지정할 수](../modifiers/shadows.md) 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-122">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="6f751-123">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-123">Required.</span></span> <span data-ttu-id="6f751-124">열거형의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-124">Name of the enumeration.</span></span> <span data-ttu-id="6f751-125">올바른 이름에 대 한 자세한 내용은 [선언 된 요소 이름](../../programming-guide/language-features/declared-elements/declared-element-names.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f751-125">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="6f751-126">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-126">Optional.</span></span> <span data-ttu-id="6f751-127">열거형 및 모든 해당 멤버의 데이터 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-127">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="6f751-128">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-128">Required.</span></span> <span data-ttu-id="6f751-129">이 문에서 선언 되는 멤버 상수 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-129">List of member constants being declared in this statement.</span></span> <span data-ttu-id="6f751-130">개별 소스 코드 줄에 여러 멤버가 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-130">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="6f751-131">각 `member` 에는 다음과 같은 구문과 파트가 있습니다. `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="6f751-131">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="6f751-132">파트</span><span class="sxs-lookup"><span data-stu-id="6f751-132">Part</span></span>|<span data-ttu-id="6f751-133">설명</span><span class="sxs-lookup"><span data-stu-id="6f751-133">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="6f751-134">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-134">Required.</span></span> <span data-ttu-id="6f751-135">이 멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-135">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="6f751-136">선택 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-136">Optional.</span></span> <span data-ttu-id="6f751-137">컴파일 시간에 평가 되 고이 멤버에 할당 되는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-137">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="6f751-138">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="6f751-138">`End` `Enum`</span></span>

  <span data-ttu-id="6f751-139">`Enum` 블록을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-139">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="6f751-140">설명</span><span class="sxs-lookup"><span data-stu-id="6f751-140">Remarks</span></span>

<span data-ttu-id="6f751-141">논리적으로 서로 관련 된 변경 되지 않은 값 집합이 있는 경우 열거형에서 함께 정의할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-141">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="6f751-142">이는 열거형 및 해당 멤버에 대 한 의미 있는 이름을 제공 하며, 값 보다 쉽게 기억할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-142">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="6f751-143">그런 다음 코드의 여러 위치에서 열거형 멤버를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-143">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="6f751-144">열거를 사용 하는 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-144">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="6f751-145">바꾸려면 또는 잘못 된 숫자로 인 한 오류를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-145">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="6f751-146">를 사용 하면 나중에 값을 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-146">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="6f751-147">코드를 더 쉽게 읽을 수 있습니다. 즉, 오류가 발생할 가능성이 낮습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-147">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="6f751-148">이전 버전과의 호환성을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-148">Ensures forward compatibility.</span></span> <span data-ttu-id="6f751-149">열거를 사용 하는 경우 나중에 누군가가 멤버 이름에 해당 하는 값을 변경 하면 코드가 실패할 가능성이 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-149">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="6f751-150">열거형에는 이름, 기본 데이터 형식 및 멤버 집합이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-150">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="6f751-151">각 멤버는 상수를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-151">Each member represents a constant.</span></span>

<span data-ttu-id="6f751-152">프로시저 외부의 클래스, 구조체, 모듈 또는 인터페이스 수준에서 선언 된 열거형은 *멤버 열거형* 입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-152">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="6f751-153">선언 하는 클래스, 구조체, 모듈 또는 인터페이스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-153">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="6f751-154">멤버 열거형은 클래스, 구조체, 모듈 또는 인터페이스 내의 어디에서 나 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-154">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="6f751-155">클래스, 구조체 또는 모듈 외부의 코드는 해당 클래스, 구조체 또는 모듈의 이름을 사용 하 여 멤버 열거형의 이름을 한정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-155">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="6f751-156">소스 파일에 [Imports](imports-statement-net-namespace-and-type.md) 문을 추가 하 여 정규화 된 이름을 사용 하지 않아도 되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-156">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="6f751-157">모든 클래스, 구조체, 모듈 또는 인터페이스 외부에서 네임 스페이스 수준에 선언 된 열거형은 해당 열거형이 표시 되는 네임 스페이스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-157">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="6f751-158">열거형의 *선언 컨텍스트* 는 소스 파일, 네임 스페이스, 클래스, 구조체, 모듈 또는 인터페이스 여야 하며 프로시저 일 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-158">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="6f751-159">자세한 내용은 [선언 컨텍스트 및 기본 액세스 수준](declaration-contexts-and-default-access-levels.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="6f751-159">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="6f751-160">특성을 열거형 전체에 적용할 수 있지만 해당 멤버를 개별적으로 적용할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-160">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="6f751-161">특성은 어셈블리의 메타 데이터에 정보를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-161">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="6f751-162">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="6f751-162">Data Type</span></span>

<span data-ttu-id="6f751-163">`Enum`문은 열거형의 데이터 형식을 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-163">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="6f751-164">각 멤버는 열거형의 데이터 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-164">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="6f751-165">`Byte`,, `Integer` `Long` ,,,, `SByte` `Short` `UInteger` `ULong` 또는 `UShort` 를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-165">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="6f751-166">열거형에 대해를 지정 하지 않는 경우 `datatype` 각 멤버는의 데이터 형식을 사용 `initializer` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-166">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="6f751-167">및를 둘 다 지정 하 `datatype` `initializer` 는 경우의 데이터 형식을 `initializer` 으로 변환할 수 있어야 합니다 `datatype` .</span><span class="sxs-lookup"><span data-stu-id="6f751-167">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="6f751-168">`datatype`및가 모두 `initializer` 없는 경우에는 데이터 형식이 기본적으로로 설정 `Integer` 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-168">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="6f751-169">멤버 초기화</span><span class="sxs-lookup"><span data-stu-id="6f751-169">Initializing Members</span></span>

<span data-ttu-id="6f751-170">`Enum`문은에서 선택한 멤버의 콘텐츠를 초기화할 수 있습니다 `memberlist` .</span><span class="sxs-lookup"><span data-stu-id="6f751-170">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="6f751-171">를 사용 `initializer` 하 여 멤버에 할당할 식을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-171">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="6f751-172">멤버에 대해를 지정 하지 않는 경우 Visual Basic는를 `initializer` 0 (첫 번째의 경우)으로 초기화 `member` `memberlist` 하거나 바로 앞에 있는 값 보다 큰 값으로 초기화 `member` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-172">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="6f751-173">각에서 제공 하는 식은 `initializer` 리터럴, 이미 정의 된 다른 상수 및이 열거형의 이전 멤버를 포함 하 여 이미 정의 된 열거형 멤버의 조합일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-173">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="6f751-174">산술 연산자와 논리 연산자를 사용 하 여 이러한 요소를 결합할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-174">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="6f751-175">에서는 변수나 함수를 사용할 수 없습니다 `initializer` .</span><span class="sxs-lookup"><span data-stu-id="6f751-175">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="6f751-176">그러나 및와 같은 변환 키워드를 사용할 수 `CByte` 있습니다 `CShort` .</span><span class="sxs-lookup"><span data-stu-id="6f751-176">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="6f751-177">`AscW`상수 또는 인수를 사용 하 여 호출 하는 경우 `String` `Char` 컴파일 시간에 계산할 수 있으므로를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-177">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="6f751-178">열거형에는 부동 소수점 값을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-178">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="6f751-179">멤버에 부동 소수점 값이 할당 되 고 `Option Strict` 가 on으로 설정 된 경우 컴파일러 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-179">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="6f751-180">`Option Strict`가 off 인 경우 값은 자동으로 형식으로 변환 됩니다 `Enum` .</span><span class="sxs-lookup"><span data-stu-id="6f751-180">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="6f751-181">멤버의 값이 기본 데이터 형식에 대해 허용 가능한 범위를 초과 하거나 멤버를 기본 데이터 형식에서 허용 하는 최대 값으로 초기화 하는 경우 컴파일러에서 오류를 보고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-181">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="6f751-182">한정자</span><span class="sxs-lookup"><span data-stu-id="6f751-182">Modifiers</span></span>

<span data-ttu-id="6f751-183">클래스, 구조체, 모듈 및 인터페이스 멤버 열거형은 기본적으로 공용 액세스로 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-183">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="6f751-184">액세스 한정자를 사용 하 여 액세스 수준을 조정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-184">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="6f751-185">네임 스페이스 멤버 열거형은 기본적으로 friend 액세스를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-185">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="6f751-186">액세스 수준을 공용으로 조정할 수 있지만 비공개 또는 protected로는 조정할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-186">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="6f751-187">자세한 내용은 [Visual Basic의 액세스 수준](../../programming-guide/language-features/declared-elements/access-levels.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="6f751-187">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="6f751-188">모든 열거형 멤버는 공용 액세스 권한을 가지 며 액세스 한정자를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-188">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="6f751-189">그러나 열거 자체의 액세스 수준이 더 제한적인 경우에는 지정 된 열거형 액세스 수준이 우선 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-189">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="6f751-190">기본적으로 모든 열거형은 형식이 고 해당 필드는 상수입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-190">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="6f751-191">따라서 `Shared` `Static` `ReadOnly` 열거형 또는 해당 멤버를 선언 하는 경우, 및 키워드를 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-191">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="6f751-192">다중 값 할당</span><span class="sxs-lookup"><span data-stu-id="6f751-192">Assigning Multiple Values</span></span>

<span data-ttu-id="6f751-193">열거형은 일반적으로 상호 배타적인 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-193">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="6f751-194">선언에 특성을 포함 하 여 <xref:System.FlagsAttribute> `Enum` 대신 열거형의 인스턴스에 여러 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-194">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="6f751-195"><xref:System.FlagsAttribute>특성은 열거형을 비트 필드 즉, 플래그 집합으로 처리 하도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-195">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="6f751-196">이를 *비트* 열거형 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-196">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="6f751-197">특성을 사용 하 여 열거형을 선언 하는 경우 <xref:System.FlagsAttribute> 값에 대해 2의 거듭제곱, 즉 1, 2, 4, 8, 16 등을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-197">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="6f751-198">또한 값이 0 인 멤버의 이름을 "None"으로 지정할 것을 권장 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-198">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="6f751-199">추가 지침은 및를 참조 <xref:System.FlagsAttribute> 하십시오 <xref:System.Enum> .</span><span class="sxs-lookup"><span data-stu-id="6f751-199">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="6f751-200">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-200">Example</span></span>

<span data-ttu-id="6f751-201">다음 예제에서는 `Enum` 문을 사용하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-201">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="6f751-202">멤버는가 `EggSizeEnum.Medium` 아닌 이라고 `Medium` 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-202">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="6f751-203">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-203">Example</span></span>

<span data-ttu-id="6f751-204">다음 예제의 메서드는 클래스 외부에 `Egg` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-204">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="6f751-205">따라서 `EggSizeEnum` 는로 정규화 됩니다 `Egg.EggSizeEnum` .</span><span class="sxs-lookup"><span data-stu-id="6f751-205">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="6f751-206">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-206">Example</span></span>

<span data-ttu-id="6f751-207">다음 예에서는 문을 사용 하 여 `Enum` 명명 된 상수 값의 관련 된 집합을 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-207">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="6f751-208">이 경우 값은 데이터베이스에 대 한 데이터 입력 양식을 디자인 하도록 선택할 수 있는 색입니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-208">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="6f751-209">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-209">Example</span></span>

<span data-ttu-id="6f751-210">다음 예에서는 양수 및 음수를 모두 포함 하는 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-210">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="6f751-211">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-211">Example</span></span>

<span data-ttu-id="6f751-212">다음 예제에서는 `As` 절을 사용 하 여 열거형의를 지정 합니다 `datatype` .</span><span class="sxs-lookup"><span data-stu-id="6f751-212">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="6f751-213">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-213">Example</span></span>

<span data-ttu-id="6f751-214">다음 예제에서는 비트 열거를 사용 하는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-214">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="6f751-215">비트 열거의 인스턴스에 여러 값을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-215">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="6f751-216">선언에는 `Enum` <xref:System.FlagsAttribute> 열거형을 플래그 집합으로 처리할 수 있음을 나타내는 특성이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-216">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="6f751-217">예제</span><span class="sxs-lookup"><span data-stu-id="6f751-217">Example</span></span>

<span data-ttu-id="6f751-218">다음 예제에서는 열거형을 반복 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-218">The following example iterates through an enumeration.</span></span> <span data-ttu-id="6f751-219">메서드를 사용 하 여 <xref:System.Enum.GetNames%2A> 열거형에서 멤버 이름 배열을 검색 하 고 <xref:System.Enum.GetValues%2A> 멤버 값의 배열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="6f751-219">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="6f751-220">참고 항목</span><span class="sxs-lookup"><span data-stu-id="6f751-220">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="6f751-221">Const 문</span><span class="sxs-lookup"><span data-stu-id="6f751-221">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="6f751-222">Dim 문</span><span class="sxs-lookup"><span data-stu-id="6f751-222">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="6f751-223">암시적 변환과 명시적 변환</span><span class="sxs-lookup"><span data-stu-id="6f751-223">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="6f751-224">형식 변환 함수</span><span class="sxs-lookup"><span data-stu-id="6f751-224">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="6f751-225">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="6f751-225">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
