---
title: 연산자 오버로드
ms.date: 10/22/2008
helpviewer_keywords:
- operators [.NET Framework], overloads
- names [.NET Framework], overloaded operators
- member design guidelines, operators
- overloaded operators
ms.assetid: 37585bf2-4c27-4dee-849a-af70e3338cc1
ms.openlocfilehash: 7757e6cfdb9ae31f6e94c26a2684f8176174499a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734818"
---
# <a name="operator-overloads"></a><span data-ttu-id="f48ab-102">연산자 오버로드</span><span class="sxs-lookup"><span data-stu-id="f48ab-102">Operator Overloads</span></span>

<span data-ttu-id="f48ab-103">연산자 오버 로드를 사용 하면 프레임 워크 형식이 기본 제공 언어 기본 형식인 것 처럼 표시 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-103">Operator overloads allow framework types to appear as if they were built-in language primitives.</span></span>

 <span data-ttu-id="f48ab-104">일부 경우에는 허용 되 고 유용 하지만 연산자 오버 로드는 신중 하 게 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-104">Although allowed and useful in some situations, operator overloads should be used cautiously.</span></span> <span data-ttu-id="f48ab-105">프레임 워크 디자이너에서 간단한 메서드로 사용 해야 하는 작업에 대해 연산자를 사용 하기 시작 하는 경우와 같이 연산자 오버 로드가 악용 되는 경우가 많습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-105">There are many cases in which operator overloading has been abused, such as when framework designers started to use operators for operations that should be simple methods.</span></span> <span data-ttu-id="f48ab-106">다음 지침은 연산자 오버 로드를 사용 하는 시기 및 방법을 결정 하는 데 도움이 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-106">The following guidelines should help you decide when and how to use operator overloading.</span></span>

 <span data-ttu-id="f48ab-107">❌ 기본 (기본 제공) 형식 처럼 사용 해야 하는 형식을 제외 하 고 연산자 오버 로드를 정의 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="f48ab-107">❌ AVOID defining operator overloads, except in types that should feel like primitive (built-in) types.</span></span>

 <span data-ttu-id="f48ab-108">기본 형식 처럼 느낌을 주는 형식으로 연산자 오버 로드를 정의 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="f48ab-108">✔️ CONSIDER defining operator overloads in a type that should feel like a primitive type.</span></span>

 <span data-ttu-id="f48ab-109">예를 들어 <xref:System.String?displayProperty=nameWithType> , `operator==` 및가 `operator!=` 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-109">For example, <xref:System.String?displayProperty=nameWithType> has `operator==` and `operator!=` defined.</span></span>

 <span data-ttu-id="f48ab-110">숫자 (예:)를 나타내는 구조체에서 연산자 오버 로드를 정의 ✔️ <xref:System.Decimal?displayProperty=nameWithType> 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-110">✔️ DO define operator overloads in structs that represent numbers (such as <xref:System.Decimal?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="f48ab-111">❌ 연산자 오버 로드를 정의 하는 경우 귀여운 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f48ab-111">❌ DO NOT be cute when defining operator overloads.</span></span>

 <span data-ttu-id="f48ab-112">연산자 오버 로드는 작업의 결과를 즉시 알 수 있는 경우에 유용 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-112">Operator overloading is useful in cases in which it is immediately obvious what the result of the operation will be.</span></span> <span data-ttu-id="f48ab-113">예를 들어, 다른에서 1을 빼서를 가져올 수 있다는 것을 의미 <xref:System.DateTime> `DateTime` <xref:System.TimeSpan> 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-113">For example, it makes sense to be able to subtract one <xref:System.DateTime> from another `DateTime` and get a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="f48ab-114">그러나 논리 union 연산자를 사용 하 여 두 데이터베이스 쿼리를 통합 하거나 시프트 연산자를 사용 하 여 스트림에 쓰려면 적절 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-114">However, it is not appropriate to use the logical union operator to union two database queries, or to use the shift operator to write to a stream.</span></span>

 <span data-ttu-id="f48ab-115">❌ 피연산자 중 하나 이상이 오버 로드를 정의 하는 유형인 경우를 제외 하 고 연산자 오버 로드를 제공 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f48ab-115">❌ DO NOT provide operator overloads unless at least one of the operands is of the type defining the overload.</span></span>

 <span data-ttu-id="f48ab-116">✔️는 대칭 방식으로 연산자를 오버 로드 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-116">✔️ DO overload operators in a symmetric fashion.</span></span>

 <span data-ttu-id="f48ab-117">예를 들어를 오버 로드 하는 경우 `operator==` 도 오버 로드 해야 합니다 `operator!=` .</span><span class="sxs-lookup"><span data-stu-id="f48ab-117">For example, if you overload the `operator==`, you should also overload the `operator!=`.</span></span> <span data-ttu-id="f48ab-118">마찬가지로를 오버 로드 하는 경우 `operator<` 도 오버 로드 해야 합니다 `operator>` .</span><span class="sxs-lookup"><span data-stu-id="f48ab-118">Similarly, if you overload the `operator<`, you should also overload the `operator>`, and so on.</span></span>

 <span data-ttu-id="f48ab-119">오버 로드 된 각 연산자에 해당 하는 이름을 가진 메서드를 제공 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="f48ab-119">✔️ CONSIDER providing methods with friendly names that correspond to each overloaded operator.</span></span>

 <span data-ttu-id="f48ab-120">많은 언어에서 연산자 오버 로드를 지원 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-120">Many languages do not support operator overloading.</span></span> <span data-ttu-id="f48ab-121">따라서 연산자를 오버 로드 하는 형식에는 동등한 기능을 제공 하는 적절 한 도메인별 이름을 가진 보조 메서드가 포함 되는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-121">For this reason, it is recommended that types that overload operators include a secondary method with an appropriate domain-specific name that provides equivalent functionality.</span></span>

 <span data-ttu-id="f48ab-122">다음 표에는 연산자 목록과 해당 하는 친숙 한 메서드 이름이 나와 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-122">The following table contains a list of operators and the corresponding friendly method names.</span></span>

|<span data-ttu-id="f48ab-123">C # 연산자 기호</span><span class="sxs-lookup"><span data-stu-id="f48ab-123">C# Operator Symbol</span></span>|<span data-ttu-id="f48ab-124">메타 데이터 이름</span><span class="sxs-lookup"><span data-stu-id="f48ab-124">Metadata Name</span></span>|<span data-ttu-id="f48ab-125">친숙한 이름</span><span class="sxs-lookup"><span data-stu-id="f48ab-125">Friendly Name</span></span>|
|-------------------------|-------------------|-------------------|
|`N/A`|`op_Implicit`|`To<TypeName>/From<TypeName>`|
|`N/A`|`op_Explicit`|`To<TypeName>/From<TypeName>`|
|`+ (binary)`|`op_Addition`|`Add`|
|`- (binary)`|`op_Subtraction`|`Subtract`|
|`* (binary)`|`op_Multiply`|`Multiply`|
|`/`|`op_Division`|`Divide`|
|`%`|`op_Modulus`|`Mod or Remainder`|
|`^`|`op_ExclusiveOr`|`Xor`|
|`& (binary)`|`op_BitwiseAnd`|`BitwiseAnd`|
|<code>&#124;</code>|`op_BitwiseOr`|`BitwiseOr`|
|`&&`|`op_LogicalAnd`|`And`|
|<code>&#124;&#124;</code>|`op_LogicalOr`|`Or`|
|`=`|`op_Assign`|`Assign`|
|`<<`|`op_LeftShift`|`LeftShift`|
|`>>`|`op_RightShift`|`RightShift`|
|`N/A`|`op_SignedRightShift`|`SignedRightShift`|
|`N/A`|`op_UnsignedRightShift`|`UnsignedRightShift`|
|`==`|`op_Equality`|`Equals`|
|`!=`|`op_Inequality`|`Equals`|
|`>`|`op_GreaterThan`|`CompareTo`|
|`<`|`op_LessThan`|`CompareTo`|
|`>=`|`op_GreaterThanOrEqual`|`CompareTo`|
|`<=`|`op_LessThanOrEqual`|`CompareTo`|
|`*=`|`op_MultiplicationAssignment`|`Multiply`|
|`-=`|`op_SubtractionAssignment`|`Subtract`|
|`^=`|`op_ExclusiveOrAssignment`|`Xor`|
|`<<=`|`op_LeftShiftAssignment`|`LeftShift`|
|`%=`|`op_ModulusAssignment`|`Mod`|
|`+=`|`op_AdditionAssignment`|`Add`|
|`&=`|`op_BitwiseAndAssignment`|`BitwiseAnd`|
|<code>&#124;=</code>|`op_BitwiseOrAssignment`|`BitwiseOr`|
|`,`|`op_Comma`|`Comma`|
|`/=`|`op_DivisionAssignment`|`Divide`|
|`--`|`op_Decrement`|`Decrement`|
|`++`|`op_Increment`|`Increment`|
|`- (unary)`|`op_UnaryNegation`|`Negate`|
|`+ (unary)`|`op_UnaryPlus`|`Plus`|
|`~`|`op_OnesComplement`|`OnesComplement`|

### <a name="overloading-operator-"></a><span data-ttu-id="f48ab-126">오버 로드 연산자 = =</span><span class="sxs-lookup"><span data-stu-id="f48ab-126">Overloading Operator ==</span></span>

 <span data-ttu-id="f48ab-127">오버 로드 `operator ==` 는 매우 복잡 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-127">Overloading `operator ==` is quite complicated.</span></span> <span data-ttu-id="f48ab-128">연산자의 의미 체계는와 같은 다른 여러 멤버와 호환 되어야 합니다 <xref:System.Object.Equals%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f48ab-128">The semantics of the operator need to be compatible with several other members, such as <xref:System.Object.Equals%2A?displayProperty=nameWithType>.</span></span>

### <a name="conversion-operators"></a><span data-ttu-id="f48ab-129">변환 연산자</span><span class="sxs-lookup"><span data-stu-id="f48ab-129">Conversion Operators</span></span>

 <span data-ttu-id="f48ab-130">변환 연산자는 한 형식에서 다른 형식으로의 변환을 허용 하는 단항 연산자입니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-130">Conversion operators are unary operators that allow conversion from one type to another.</span></span> <span data-ttu-id="f48ab-131">연산자는 피연산자 또는 반환 형식에서 정적 멤버로 정의 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-131">The operators must be defined as static members on either the operand or the return type.</span></span> <span data-ttu-id="f48ab-132">변환 연산자에는 암시적 및 명시적 이라는 두 가지 유형이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-132">There are two types of conversion operators: implicit and explicit.</span></span>

 <span data-ttu-id="f48ab-133">❌ 최종 사용자가 이러한 변환을 명확 하 게 예상 하지 않을 경우 변환 연산자를 제공 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f48ab-133">❌ DO NOT provide a conversion operator if such conversion is not clearly expected by the end users.</span></span>

 <span data-ttu-id="f48ab-134">❌ 형식 도메인 외부에서 변환 연산자를 정의 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f48ab-134">❌ DO NOT define conversion operators outside of a type’s domain.</span></span>

 <span data-ttu-id="f48ab-135">예를 들어,, <xref:System.Int32> <xref:System.Double> 및는 <xref:System.Decimal> 모두 숫자 형식 이지만 <xref:System.DateTime> 는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-135">For example, <xref:System.Int32>, <xref:System.Double>, and <xref:System.Decimal> are all numeric types, whereas <xref:System.DateTime> is not.</span></span> <span data-ttu-id="f48ab-136">따라서를로 변환 하는 변환 연산자가 없어야 합니다 `Double(long)` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f48ab-136">Therefore, there should be no conversion operator to convert a `Double(long)` to a `DateTime`.</span></span> <span data-ttu-id="f48ab-137">이 경우 생성자는 기본 설정입니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-137">A constructor is preferred in such a case.</span></span>

 <span data-ttu-id="f48ab-138">❌ 변환이 잠재적으로 손실 될 수 있는 경우 암시적 변환 연산자를 제공 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="f48ab-138">❌ DO NOT provide an implicit conversion operator if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="f48ab-139">예를 들어는 `Double` `Int32` `Double` 보다 광범위 한 범위가 있으므로에서로의 암시적 변환이 되어서는 안 됩니다 `Int32` .</span><span class="sxs-lookup"><span data-stu-id="f48ab-139">For example, there should not be an implicit conversion from `Double` to `Int32` because `Double` has a wider range than `Int32`.</span></span> <span data-ttu-id="f48ab-140">변환이 잠재적으로 손실 될 수 있는 경우에도 명시적 변환 연산자를 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-140">An explicit conversion operator can be provided even if the conversion is potentially lossy.</span></span>

 <span data-ttu-id="f48ab-141">❌ 암시적 캐스팅에서 예외를 throw 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-141">❌ DO NOT throw exceptions from implicit casts.</span></span>

 <span data-ttu-id="f48ab-142">최종 사용자는 변환이 발생 하는 것을 인식 하지 못할 수 있으므로 최종 사용자가 원인을 이해 하는 것은 매우 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-142">It is very difficult for end users to understand what is happening, because they might not be aware that a conversion is taking place.</span></span>

 <span data-ttu-id="f48ab-143"><xref:System.InvalidCastException?displayProperty=nameWithType>캐스트 연산자를 호출 하 여 손실 변환이 발생 하 고 연산자의 계약이 손실 변환을 허용 하지 않는 경우 ✔️ throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="f48ab-143">✔️ DO throw <xref:System.InvalidCastException?displayProperty=nameWithType> if a call to a cast operator results in a lossy conversion and the contract of the operator does not allow lossy conversions.</span></span>

 <span data-ttu-id="f48ab-144">*2005, 2009 Microsoft Corporation © 부분입니다. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="f48ab-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f48ab-145">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="f48ab-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f48ab-146">참조</span><span class="sxs-lookup"><span data-stu-id="f48ab-146">See also</span></span>

- [<span data-ttu-id="f48ab-147">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f48ab-147">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="f48ab-148">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="f48ab-148">Framework Design Guidelines</span></span>](index.md)
