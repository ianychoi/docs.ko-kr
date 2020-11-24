---
description: '! (null-forgiving) 연산자- C# 참조'
title: '! (null-forgiving) 연산자- C# 참조'
ms.date: 10/11/2019
f1_keywords:
- nullForgiving_CSharpKeyword
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: f2eb57bba462d471a041c17024fa7031c2c7f87d
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830586"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="7f078-105">!</span><span class="sxs-lookup"><span data-stu-id="7f078-105">!</span></span> <span data-ttu-id="7f078-106">(null-forgiving) 연산자(C# 참조)</span><span class="sxs-lookup"><span data-stu-id="7f078-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="7f078-107">C# 8.0 이상에서 사용할 수 있는 단항 후위 `!` 연산자는 null-forgiving 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="7f078-108">[null 허용 주석 컨텍스트](../../nullable-references.md#nullable-annotation-context)가 활성화된 경우에는 참조 형식의 `x` 식이 `null`: `x!`가 아님을 선언하는 데 null-forgiving 연산자를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="7f078-109">단항 접두사 `!` 연산자는 [논리 부정 연산자](boolean-logical-operators.md#logical-negation-operator-)입니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="7f078-110">null-forgiving 연산자는 런타임에 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="7f078-111">식의 null 상태를 변경하여 컴파일러의 정적 흐름 분석에만 영향을 줍니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="7f078-112">런타임에서 `x!` 식은 기본 식 `x`의 결과로 계산됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="7f078-113">C# 8에서 null 허용 연산자는 이전 [null 조건부](member-access-operators.md#null-conditional-operators--and-) 연산 목록을 종료합니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="7f078-114">예를 들어 `x?.y!.z` 식은 `(x?.y)!.z`로 구문 분석됩니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="7f078-115">이 해석으로 인해 `z`는 `x`가 `null`인 경우에도 평가되므로 <xref:System.NullReferenceException>이 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="7f078-116">nullable 참조 형식 기능에 대한 자세한 내용은 [nullable 참조 형식](../builtin-types/nullable-reference-types.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f078-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="7f078-117">예</span><span class="sxs-lookup"><span data-stu-id="7f078-117">Examples</span></span>

<span data-ttu-id="7f078-118">null-forgiving 연산자의 사용 사례 중 하나는 인수 유효성 검사 논리를 테스트하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="7f078-119">예를 들어 다음 클래스를 예로 들어 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="7f078-120">[MSTest 테스트 프레임워크](../../../core/testing/unit-testing-with-mstest.md)를 사용하여 생성자에서 유효성 검사 논리에 대해 다음 테스트를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="7f078-121">null-forgiving 연산자가 없으면 컴파일러가 이전 코드에 대해 다음 경고를 생성합니다. `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="7f078-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="7f078-122">null-forgiving 연산자를 사용하여 `null`이 전달될 것이고 경고를 표시하지 않아야 함을 컴파일러에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="7f078-123">식이 `null`이 될 수 없지만 컴파일러가 이를 인식할 수 없음이 확실할 경우에는 null-forgiving 연산자를 사용할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="7f078-124">다음 예에서는 `IsValid` 메서드가 `true`를 반환하는 경우 해당 인수는 `null`이 아니므로 안전하게 역참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="7f078-125">null-forgiving 연산자가 없으면 컴파일러가 `p.Name` 코드에 대해 다음 경고를 생성합니다. `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="7f078-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="7f078-126">`IsValid` 메서드를 수정할 수 있는 경우 [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) 특성을 사용하여 메서드가 `true`를 반환할 때 `IsValid` 메서드의 인수는 `null`일 수 없다는 것을 컴파일러에 알릴 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="7f078-127">앞의 예제에서는 컴파일러가 `if` 문 내에서 `p`가 `null`일 수 없다는 것을 확인할 수 있는 충분한 정보를 제공하기 때문에 null-forgiving 연산자를 사용할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7f078-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="7f078-128">변수의 null 상태에 대한 추가 정보를 제공하는 데 사용할 수 있는 특성에 대한 자세한 내용은 [null 예상을 정의하는 특성을 포함한 API 업그레이드](../attributes/nullable-analysis.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f078-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7f078-129">C# 언어 사양</span><span class="sxs-lookup"><span data-stu-id="7f078-129">C# language specification</span></span>

<span data-ttu-id="7f078-130">자세한 내용은 [Nullable 참조 형식 사양 초안](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator)의 [null-forgiving 연산자](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md) 섹션을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="7f078-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f078-131">참조</span><span class="sxs-lookup"><span data-stu-id="7f078-131">See also</span></span>

- [<span data-ttu-id="7f078-132">C# 참조</span><span class="sxs-lookup"><span data-stu-id="7f078-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7f078-133">C# 연산자 및 식</span><span class="sxs-lookup"><span data-stu-id="7f078-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="7f078-134">자습서: nullable 참조 형식을 사용하여 디자인</span><span class="sxs-lookup"><span data-stu-id="7f078-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
