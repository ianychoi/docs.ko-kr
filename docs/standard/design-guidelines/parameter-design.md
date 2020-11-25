---
title: 매개 변수 디자인
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], parameters
- members [.NET Framework], parameters
- names [.NET Framework], parameters
- parameters, design guidelines
- reserved parameters
ms.assetid: 3f33bf46-4a7b-43b3-bb78-1ffebe0dcfa6
ms.openlocfilehash: 815075198f34c0c045603b9d377b9d5fbdf1a91d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707882"
---
# <a name="parameter-design"></a><span data-ttu-id="7366d-102">매개 변수 디자인</span><span class="sxs-lookup"><span data-stu-id="7366d-102">Parameter Design</span></span>

<span data-ttu-id="7366d-103">이 섹션에서는 인수 확인에 대 한 지침을 포함 하 여 매개 변수 디자인에 대 한 광범위 한 지침을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-103">This section provides broad guidelines on parameter design, including sections with guidelines for checking arguments.</span></span> <span data-ttu-id="7366d-104">또한 [명명 매개 변수](naming-parameters.md)에 설명 된 지침을 참조 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-104">In addition, you should refer to the guidelines described in [Naming Parameters](naming-parameters.md).</span></span>

 <span data-ttu-id="7366d-105">✔️ 멤버에 필요한 기능을 제공 하는 최소 파생 매개 변수 형식을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-105">✔️ DO use the least derived parameter type that provides the functionality required by the member.</span></span>

 <span data-ttu-id="7366d-106">예를 들어 컬렉션을 열거 하 고 각 항목을 콘솔에 출력 하는 메서드를 디자인 하려는 경우를 가정해 보겠습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-106">For example, suppose you want to design a method that enumerates a collection and prints each item to the console.</span></span> <span data-ttu-id="7366d-107">예를 들어 이러한 메서드는 <xref:System.Collections.IEnumerable> 또는이 아닌 매개 변수로를 사용 해야 <xref:System.Collections.ArrayList> <xref:System.Collections.IList> 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-107">Such a method should take <xref:System.Collections.IEnumerable> as the parameter, not <xref:System.Collections.ArrayList> or <xref:System.Collections.IList>, for example.</span></span>

 <span data-ttu-id="7366d-108">❌ 예약 된 매개 변수를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-108">❌ DO NOT use reserved parameters.</span></span>

 <span data-ttu-id="7366d-109">이후 버전에서 멤버에 대 한 추가 입력이 필요한 경우에는 새 오버 로드를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-109">If more input to a member is needed in some future version, a new overload can be added.</span></span>

 <span data-ttu-id="7366d-110">❌ 포인터, 포인터 배열 또는 다차원 배열을 매개 변수로 사용 하는 메서드를 공개적으로 노출 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-110">❌ DO NOT have publicly exposed methods that take pointers, arrays of pointers, or multidimensional arrays as parameters.</span></span>

 <span data-ttu-id="7366d-111">포인터와 다차원 배열을 제대로 사용 하기가 비교적 어렵습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-111">Pointers and multidimensional arrays are relatively difficult to use properly.</span></span> <span data-ttu-id="7366d-112">거의 모든 경우에 Api는 이러한 형식을 매개 변수로 사용 하지 않도록 다시 디자인 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-112">In almost all cases, APIs can be redesigned to avoid taking these types as parameters.</span></span>

 <span data-ttu-id="7366d-113">`out`오버 로드 간에 매개 변수 순서가 일치 하지 않는 경우에도 모든 매개 변수를 값으로 지정 하는 매개 변수 `ref` (매개 변수 배열 제외)에 모든 매개 변수를 ✔️ 합니다 ( [멤버 오버 로드](member-overloading.md)참조).</span><span class="sxs-lookup"><span data-stu-id="7366d-113">✔️ DO place all `out` parameters following all of the by-value and `ref` parameters (excluding parameter arrays), even if it results in an inconsistency in parameter ordering between overloads (see [Member Overloading](member-overloading.md)).</span></span>

 <span data-ttu-id="7366d-114">`out`매개 변수를 추가 반환 값으로 볼 수 있으며,이를 함께 그룹화 하면 메서드 서명을 보다 쉽게 이해할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-114">The `out` parameters can be seen as extra return values, and grouping them together makes the method signature easier to understand.</span></span>

 <span data-ttu-id="7366d-115">멤버를 재정의 하거나 인터페이스 멤버를 구현할 때 명명 매개 변수에서 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-115">✔️ DO be consistent in naming parameters when overriding members or implementing interface members.</span></span>

 <span data-ttu-id="7366d-116">이는 메서드 간의 관계를 더 잘 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-116">This better communicates the relationship between the methods.</span></span>

### <a name="choosing-between-enum-and-boolean-parameters"></a><span data-ttu-id="7366d-117">열거 및 부울 매개 변수 중에서 선택</span><span class="sxs-lookup"><span data-stu-id="7366d-117">Choosing Between Enum and Boolean Parameters</span></span>  

 <span data-ttu-id="7366d-118">멤버에 부울 매개 변수를 두 개 이상 포함 하는 경우 열거형을 사용 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-118">✔️ DO use enums if a member would otherwise have two or more Boolean parameters.</span></span>

 <span data-ttu-id="7366d-119">❌ 두 개 이상의 값이 필요 하지 않은 경우 부울을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-119">❌ DO NOT use Booleans unless you are absolutely sure there will never be a need for more than two values.</span></span>

 <span data-ttu-id="7366d-120">열거형은 나중에 값을 추가할 수 있는 공간을 제공 하지만 열거형 [디자인](enum.md)에 설명 된 열거형에 값을 추가할 경우의 모든 의미를 알고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-120">Enums give you some room for future addition of values, but you should be aware of all the implications of adding values to enums, which are described in [Enum Design](enum.md).</span></span>

 <span data-ttu-id="7366d-121">✔️ 실제로 두 개의 상태 값인 생성자 매개 변수에 부울을 사용 하는 것이 좋습니다. 부울 속성을 초기화 하는 데만 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-121">✔️ CONSIDER using Booleans for constructor parameters that are truly two-state values and are simply used to initialize Boolean properties.</span></span>

### <a name="validating-arguments"></a><span data-ttu-id="7366d-122">인수 유효성 검사</span><span class="sxs-lookup"><span data-stu-id="7366d-122">Validating Arguments</span></span>

 <span data-ttu-id="7366d-123">✔️는 public, protected 또는 명시적으로 구현 된 멤버에 전달 된 인수의 유효성을 검사 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-123">✔️ DO validate arguments passed to public, protected, or explicitly implemented members.</span></span> <span data-ttu-id="7366d-124"><xref:System.ArgumentException?displayProperty=nameWithType>유효성 검사에 실패 하면 또는 해당 하위 클래스 중 하나를 Throw 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-124">Throw <xref:System.ArgumentException?displayProperty=nameWithType>, or one of its subclasses, if the validation fails.</span></span>

 <span data-ttu-id="7366d-125">실제 유효성 검사가 public 또는 protected 멤버 자체에서 발생할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-125">Note that the actual validation does not necessarily have to happen in the public or protected member itself.</span></span> <span data-ttu-id="7366d-126">일부 전용 또는 내부 루틴에서 하위 수준으로 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-126">It could happen at a lower level in some private or internal routine.</span></span> <span data-ttu-id="7366d-127">주된 점은 최종 사용자에 게 노출 되는 전체 노출 영역에서 인수를 확인 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-127">The main point is that the entire surface area that is exposed to the end users checks the arguments.</span></span>

 <span data-ttu-id="7366d-128"><xref:System.ArgumentNullException>null 인수가 전달 되 고 멤버가 null 인수를 지원 하지 않는 경우 ✔️ throw 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-128">✔️ DO throw <xref:System.ArgumentNullException> if a null argument is passed and the member does not support null arguments.</span></span>

 <span data-ttu-id="7366d-129">열거형 매개 변수의 유효성을 검사 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-129">✔️ DO validate enum parameters.</span></span>

 <span data-ttu-id="7366d-130">Enum 인수가 열거형으로 정의 된 범위에 있을 것으로 가정 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-130">Do not assume enum arguments will be in the range defined by the enum.</span></span> <span data-ttu-id="7366d-131">CLR에서는 열거형에 값이 정의 되지 않은 경우에도 정수 값을 열거형 값으로 캐스팅할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-131">The CLR allows casting any integer value into an enum value even if the value is not defined in the enum.</span></span>

 <span data-ttu-id="7366d-132">❌<xref:System.Enum.IsDefined%2A?displayProperty=nameWithType>열거형 범위 검사에는를 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7366d-132">❌ DO NOT use <xref:System.Enum.IsDefined%2A?displayProperty=nameWithType> for enum range checks.</span></span>

 <span data-ttu-id="7366d-133">유효성을 검사 한 후 변경 가능한 인수가 변경 된 것을 알 수 ✔️.</span><span class="sxs-lookup"><span data-stu-id="7366d-133">✔️ DO be aware that mutable arguments might have changed after they were validated.</span></span>

 <span data-ttu-id="7366d-134">멤버가 보안에 중요 한 경우에는 복사본을 만든 다음 인수의 유효성을 검사 하 고 처리 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-134">If the member is security sensitive, you are encouraged to make a copy and then validate and process the argument.</span></span>

### <a name="parameter-passing"></a><span data-ttu-id="7366d-135">매개 변수 전달</span><span class="sxs-lookup"><span data-stu-id="7366d-135">Parameter Passing</span></span>

 <span data-ttu-id="7366d-136">프레임 워크 디자이너의 관점에서 세 가지 주요 매개 변수는 값으로 매개 변수, `ref` 매개 변수 및 `out` 매개 변수입니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-136">From the perspective of a framework designer, there are three main groups of parameters: by-value parameters, `ref` parameters, and `out` parameters.</span></span>

 <span data-ttu-id="7366d-137">인수가 값으로 매개 변수를 통해 전달 되 면 멤버는 전달 된 실제 인수의 복사본을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-137">When an argument is passed through a by-value parameter, the member receives a copy of the actual argument passed in.</span></span> <span data-ttu-id="7366d-138">인수가 값 형식인 경우에는 인수의 복사본이 스택에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-138">If the argument is a value type, a copy of the argument is put on the stack.</span></span> <span data-ttu-id="7366d-139">인수가 참조 형식이 면 참조의 복사본이 스택에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-139">If the argument is a reference type, a copy of the reference is put on the stack.</span></span> <span data-ttu-id="7366d-140">C #, VB.NET 및 c + +와 같은 가장 인기 있는 CLR 언어는 기본적으로 매개 변수를 값으로 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-140">Most popular CLR languages, such as C#, VB.NET, and C++, default to passing parameters by value.</span></span>

 <span data-ttu-id="7366d-141">인수가 매개 변수를 통해 전달 되 면 `ref` 멤버는 전달 된 실제 인수에 대 한 참조를 받습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-141">When an argument is passed through a `ref` parameter, the member receives a reference to the actual argument passed in.</span></span> <span data-ttu-id="7366d-142">인수가 값 형식인 경우 인수에 대 한 참조가 스택에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-142">If the argument is a value type, a reference to the argument is put on the stack.</span></span> <span data-ttu-id="7366d-143">인수가 참조 형식이 면 참조에 대 한 참조가 스택에 배치 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-143">If the argument is a reference type, a reference to the reference is put on the stack.</span></span> <span data-ttu-id="7366d-144">`Ref` 매개 변수를 사용 하 여 멤버가 호출자가 전달한 인수를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-144">`Ref` parameters can be used to allow the member to modify arguments passed by the caller.</span></span>

 <span data-ttu-id="7366d-145">`Out` 매개 변수는 매개 변수와 비슷하며 약간의 `ref` 차이가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-145">`Out` parameters are similar to `ref` parameters, with some small differences.</span></span> <span data-ttu-id="7366d-146">매개 변수는 처음에 할당 되지 않은 것으로 간주 되며, 일부 값이 할당 되기 전에 멤버 본문에서 읽을 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-146">The parameter is initially considered unassigned and cannot be read in the member body before it is assigned some value.</span></span> <span data-ttu-id="7366d-147">또한 멤버에서 반환 하기 전에 매개 변수에 값을 할당 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-147">Also, the parameter has to be assigned some value before the member returns.</span></span>

 <span data-ttu-id="7366d-148">❌`out`또는 `ref` 매개 변수를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-148">❌ AVOID using `out` or `ref` parameters.</span></span>

 <span data-ttu-id="7366d-149">`out`또는 `ref` 매개 변수를 사용 하려면 포인터를 사용 하 고, 값 형식과 참조 형식이 어떻게 다른 지 이해 하 고, 여러 개의 반환 값이 있는 메서드를 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-149">Using `out` or `ref` parameters requires experience with pointers, understanding how value types and reference types differ, and handling methods with multiple return values.</span></span> <span data-ttu-id="7366d-150">또한 `out` 와 매개 변수의 차이는 `ref` 널리 이해 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-150">Also, the difference between `out` and `ref` parameters is not widely understood.</span></span> <span data-ttu-id="7366d-151">일반 사용자를 위해 설계 된 프레임 워크 설계자는 사용자가 `out` 또는 매개 변수로 작업 하는 것을 원하지 않습니다 `ref` .</span><span class="sxs-lookup"><span data-stu-id="7366d-151">Framework architects designing for a general audience should not expect users to master working with `out` or `ref` parameters.</span></span>

 <span data-ttu-id="7366d-152">❌ 참조 형식을 참조로 전달 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-152">❌ DO NOT pass reference types by reference.</span></span>

 <span data-ttu-id="7366d-153">참조를 교환 하는 데 사용할 수 있는 메서드와 같이 규칙에 몇 가지 제한 된 예외가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-153">There are some limited exceptions to the rule, such as a method that can be used to swap references.</span></span>

### <a name="members-with-variable-number-of-parameters"></a><span data-ttu-id="7366d-154">매개 변수 개수가 가변적인 멤버</span><span class="sxs-lookup"><span data-stu-id="7366d-154">Members with Variable Number of Parameters</span></span>

 <span data-ttu-id="7366d-155">가변 개수의 인수를 사용할 수 있는 멤버는 배열 매개 변수를 제공 하 여 표현 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-155">Members that can take a variable number of arguments are expressed by providing an array parameter.</span></span> <span data-ttu-id="7366d-156">예를 들어 <xref:System.String> 는 다음 메서드를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-156">For example, <xref:System.String> provides the following method:</span></span>

```csharp
public class String {
    public static string Format(string format, object[] parameters);
}
```

 <span data-ttu-id="7366d-157">그러면 사용자가 다음과 <xref:System.String.Format%2A?displayProperty=nameWithType> 같이 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-157">A user can then call the <xref:System.String.Format%2A?displayProperty=nameWithType> method, as follows:</span></span>

 `String.Format("File {0} not found in {1}",new object[]{filename,directory});`

 <span data-ttu-id="7366d-158">배열 매개 변수에 c # Params 키워드를 추가 하면 매개 변수를 매개 변수를 호출한 params 배열 매개 변수로 변경 하 고 임시 배열을 만드는 바로 가기를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-158">Adding the C# params keyword to an array parameter changes the parameter to a so-called params array parameter and provides a shortcut to creating a temporary array.</span></span>

```csharp
public class String {
    public static string Format(string format, params object[] parameters);
}
```

 <span data-ttu-id="7366d-159">이렇게 하면 사용자가 인수 목록에서 직접 배열 요소를 전달 하 여 메서드를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-159">Doing this allows the user to call the method by passing the array elements directly in the argument list.</span></span>

 `String.Format("File {0} not found in {1}",filename,directory);`

 <span data-ttu-id="7366d-160">Params 키워드는 매개 변수 목록의 마지막 매개 변수에만 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-160">Note that the params keyword can be added only to the last parameter in the parameter list.</span></span>

 <span data-ttu-id="7366d-161">최종 사용자가 적은 수의 요소로 배열을 전달할 것으로 간주 되는 경우에는 params 키워드를 배열 매개 변수에 추가 하는 것이 좋습니다 ✔️.</span><span class="sxs-lookup"><span data-stu-id="7366d-161">✔️ CONSIDER adding the params keyword to array parameters if you expect the end users to pass arrays with a small number of elements.</span></span> <span data-ttu-id="7366d-162">일반적인 시나리오에서 많은 요소가 전달 될 것으로 예상 되는 경우 사용자는 이러한 요소를 인라인으로 전달 하지 않을 수 있으므로 params 키워드가 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-162">If it's expected that lots of elements will be passed in common scenarios, users will probably not pass these elements inline anyway, and so the params keyword is not necessary.</span></span>

 <span data-ttu-id="7366d-163">❌ 호출자에 게 이미 배열에 입력이 이미 있는 경우에는 params 배열을 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-163">❌ AVOID using params arrays if the caller would almost always have the input already in an array.</span></span>

 <span data-ttu-id="7366d-164">예를 들어 바이트 배열 매개 변수가 있는 멤버는 개별 바이트를 전달 하 여 거의 호출 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-164">For example, members with byte array parameters would almost never be called by passing individual bytes.</span></span> <span data-ttu-id="7366d-165">따라서 .NET Framework의 바이트 배열 매개 변수는 params 키워드를 사용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-165">For this reason, byte array parameters in the .NET Framework do not use the params keyword.</span></span>

 <span data-ttu-id="7366d-166">❌ Params 배열 매개 변수를 사용 하는 멤버가 배열을 수정 하는 경우에는 params 배열을 사용 하지 마세요.</span><span class="sxs-lookup"><span data-stu-id="7366d-166">❌ DO NOT use params arrays if the array is modified by the member taking the params array parameter.</span></span>

 <span data-ttu-id="7366d-167">대부분의 컴파일러는 멤버에 대 한 인수를 호출 사이트의 임시 배열로 변환 하기 때문에 배열이 임시 개체 일 수 있으므로 배열에 대 한 모든 수정 내용이 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-167">Because of the fact that many compilers turn the arguments to the member into a temporary array at the call site, the array might be a temporary object, and therefore any modifications to the array will be lost.</span></span>

 <span data-ttu-id="7366d-168">더 복잡 한 오버 로드에서 사용할 수 없는 경우에도 간단한 오버 로드에서 params 키워드를 사용 하는 것이 좋습니다. ✔️</span><span class="sxs-lookup"><span data-stu-id="7366d-168">✔️ CONSIDER using the params keyword in a simple overload, even if a more complex overload could not use it.</span></span>

 <span data-ttu-id="7366d-169">사용자가 모든 오버 로드에 포함 되지 않은 경우에도 하나의 오버 로드에서 params 배열을 포함 하 고 있는지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-169">Ask yourself if users would value having the params array in one overload even if it wasn't in all overloads.</span></span>

 <span data-ttu-id="7366d-170">매개 변수를 정렬 하 여 params 키워드를 사용할 수 있도록 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-170">✔️ DO try to order parameters to make it possible to use the params keyword.</span></span>

 <span data-ttu-id="7366d-171">✔️ 매우 적은 수의 인수를 사용 하 여 호출에 대해 특별 한 오버 로드 및 코드 경로를 제공 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-171">✔️ CONSIDER providing special overloads and code paths for calls with a small number of arguments in extremely performance-sensitive APIs.</span></span>

 <span data-ttu-id="7366d-172">이를 통해 적은 수의 인수를 사용 하 여 API를 호출 하는 경우 배열 개체를 만들지 않도록 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-172">This makes it possible to avoid creating array objects when the API is called with a small number of arguments.</span></span> <span data-ttu-id="7366d-173">단일 형식의 배열 매개 변수를 가져와 숫자 접미사를 추가 하 여 매개 변수의 이름을 구성 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-173">Form the names of the parameters by taking a singular form of the array parameter and adding a numeric suffix.</span></span>

 <span data-ttu-id="7366d-174">배열을 만들고 보다 일반적인 메서드를 호출 하는 것이 아니라 전체 코드 경로를 특별 한 경우에만이 작업을 수행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-174">You should only do this if you are going to special-case the entire code path, not just create an array and call the more general method.</span></span>

 <span data-ttu-id="7366d-175">✔️ null은 params 배열 인수로 전달 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-175">✔️ DO be aware that null could be passed as a params array argument.</span></span>

 <span data-ttu-id="7366d-176">처리 하기 전에 배열이 null이 아닌 지 유효성을 검사 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-176">You should validate that the array is not null before processing.</span></span>

 <span data-ttu-id="7366d-177">❌`varargs`줄임표 (...)를 사용 하지 마십시오.</span><span class="sxs-lookup"><span data-stu-id="7366d-177">❌ DO NOT use the `varargs` methods, otherwise known as the ellipsis.</span></span>

 <span data-ttu-id="7366d-178">C + +와 같은 일부 CLR 언어는 메서드 라는 변수 매개 변수 목록을 전달 하는 대체 규칙을 지원 `varargs` 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-178">Some CLR languages, such as C++, support an alternative convention for passing variable parameter lists called `varargs` methods.</span></span> <span data-ttu-id="7366d-179">규칙은 CLS 규격이 아니므로 프레임 워크에서 사용 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-179">The convention should not be used in frameworks, because it is not CLS compliant.</span></span>

### <a name="pointer-parameters"></a><span data-ttu-id="7366d-180">포인터 매개 변수</span><span class="sxs-lookup"><span data-stu-id="7366d-180">Pointer Parameters</span></span>

 <span data-ttu-id="7366d-181">일반적으로 잘 디자인 된 관리 코드 프레임 워크의 공개 노출 영역에는 포인터가 표시 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-181">In general, pointers should not appear in the public surface area of a well-designed managed code framework.</span></span> <span data-ttu-id="7366d-182">대부분의 경우 포인터는 캡슐화 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-182">Most of the time, pointers should be encapsulated.</span></span> <span data-ttu-id="7366d-183">그러나 일부 경우에는 상호 운용성을 위해 포인터가 필요 하며, 이러한 경우에는 포인터를 사용 하는 것이 적절 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-183">However, in some cases pointers are required for interoperability reasons, and using pointers in such cases is appropriate.</span></span>

 <span data-ttu-id="7366d-184">포인터는 CLS 규격이 아니므로 포인터 인수를 사용 하는 모든 멤버에 대 한 대안을 제공 ✔️ 합니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-184">✔️ DO provide an alternative for any member that takes a pointer argument, because pointers are not CLS-compliant.</span></span>

 <span data-ttu-id="7366d-185">❌ 포인터 인수를 많이 사용 하는 인수 검사를 수행 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-185">❌ AVOID doing expensive argument checking of pointer arguments.</span></span>

 <span data-ttu-id="7366d-186">✔️ 포인터를 사용 하 여 멤버를 디자인할 때 일반적인 포인터 관련 규칙을 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-186">✔️ DO follow common pointer-related conventions when designing members with pointers.</span></span>

 <span data-ttu-id="7366d-187">예를 들어 단순한 포인터 산술 연산을 사용 하 여 동일한 결과를 얻을 수 있으므로 시작 인덱스를 전달할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="7366d-187">For example, there is no need to pass the start index, because simple pointer arithmetic can be used to accomplish the same result.</span></span>

 <span data-ttu-id="7366d-188">*&copy;2005 부분, 2009 Microsoft Corporation. All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7366d-188">*Portions &copy; 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="7366d-189">*Pearson Education, Inc의 동의로 재인쇄. 출처: [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 작성자: Krzysztof Cwalina 및 Brad Abrams, 출판 정보: Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="7366d-189">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="7366d-190">참조</span><span class="sxs-lookup"><span data-stu-id="7366d-190">See also</span></span>

- [<span data-ttu-id="7366d-191">멤버 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="7366d-191">Member Design Guidelines</span></span>](member.md)
- [<span data-ttu-id="7366d-192">프레임 워크 디자인 지침</span><span class="sxs-lookup"><span data-stu-id="7366d-192">Framework Design Guidelines</span></span>](index.md)
