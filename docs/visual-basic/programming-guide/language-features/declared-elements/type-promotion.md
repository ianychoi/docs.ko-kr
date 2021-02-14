---
description: '자세히 알아보기: 형식 승격 (Visual Basic)'
title: 형식 승격
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: fd8a30fb7e442d82222ae55daabf70bd8e532138
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434721"
---
# <a name="type-promotion-visual-basic"></a><span data-ttu-id="eb62d-103">형식 승격(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb62d-103">Type Promotion (Visual Basic)</span></span>

<span data-ttu-id="eb62d-104">모듈에서 프로그래밍 요소를 선언 하는 경우 해당 범위를 모듈이 포함 된 네임 스페이스로 승격 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb62d-104">When you declare a programming element in a module, Visual Basic promotes its scope to the namespace containing the module.</span></span> <span data-ttu-id="eb62d-105">이를 *유형 승격* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-105">This is known as *type promotion*.</span></span>  
  
 <span data-ttu-id="eb62d-106">다음 예제에서는 모듈의 기본 정의와 해당 모듈의 두 멤버를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-106">The following example shows a skeleton definition of a module and two members of that module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="eb62d-107">에서 `projModule` 모듈 수준에 선언 된 프로그래밍 요소는로 승격 됩니다 `projNamespace` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-107">Within `projModule`, programming elements declared at module level are promoted to `projNamespace`.</span></span> <span data-ttu-id="eb62d-108">앞의 예제에서 `basicEnum` 및는 `innerClass` 승격 되지만 `numberSub` 모듈 수준에서 선언 되지 않았으므로는 그렇지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-108">In the preceding example, `basicEnum` and `innerClass` are promoted, but `numberSub` is not, because it is not declared at module level.</span></span>  
  
## <a name="effect-of-type-promotion"></a><span data-ttu-id="eb62d-109">유형 승격의 효과</span><span class="sxs-lookup"><span data-stu-id="eb62d-109">Effect of Type Promotion</span></span>  

 <span data-ttu-id="eb62d-110">형식 승격의 효과는 정규화 문자열에 모듈 이름을 포함할 필요가 없다는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-110">The effect of type promotion is that a qualification string does not need to include the module name.</span></span> <span data-ttu-id="eb62d-111">다음 예제에서는 앞의 예제에서 프로시저에 대 한 두 호출을 수행 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-111">The following example makes two calls to the procedure in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#2)]  
  
 <span data-ttu-id="eb62d-112">앞의 예제에서 첫 번째 호출은 전체 한정 문자열을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-112">In the preceding example, the first call uses complete qualification strings.</span></span> <span data-ttu-id="eb62d-113">그러나 형식 승격으로 인해이 작업이 필요 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-113">However, this is not necessary because of type promotion.</span></span> <span data-ttu-id="eb62d-114">또한 두 번째 호출은 한정 문자열에를 포함 하지 않고 모듈의 멤버에 액세스 합니다 `projModule` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-114">The second call also accesses the module's members without including `projModule` in the qualification strings.</span></span>  
  
## <a name="defeat-of-type-promotion"></a><span data-ttu-id="eb62d-115">유형 승격의 물리</span><span class="sxs-lookup"><span data-stu-id="eb62d-115">Defeat of Type Promotion</span></span>  

 <span data-ttu-id="eb62d-116">네임 스페이스에 모듈 멤버와 이름이 같은 멤버가 이미 있는 경우 해당 모듈 멤버에 대해 형식 승격이 발생 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-116">If the namespace already has a member with the same name as a module member, type promotion is defeated for that module member.</span></span> <span data-ttu-id="eb62d-117">다음 예제에서는 동일한 네임 스페이스 내에서 열거형 및 모듈의 기본 정의를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-117">The following example shows a skeleton definition of an enumeration and a module within the same namespace.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#3)]  
  
 <span data-ttu-id="eb62d-118">앞의 예제에서 `abc` `thisNameSpace` 네임 스페이스 수준에 동일한 이름을 가진 열거가 이미 있기 때문에 클래스를로 승격할 수 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="eb62d-118">In the preceding example, Visual Basic cannot promote class `abc` to `thisNameSpace` because there is already an enumeration with the same name at namespace level.</span></span> <span data-ttu-id="eb62d-119">에 액세스 하려면 `abcSub` 전체 한정 문자열을 사용 해야 합니다 `thisNamespace.thisModule.abc.abcSub` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-119">To access `abcSub`, you must use the full qualification string `thisNamespace.thisModule.abc.abcSub`.</span></span> <span data-ttu-id="eb62d-120">그러나 클래스 `xyz` 는 여전히 승격 되며, `xyzSub` 더 짧은 정규화 문자열로 액세스할 수 있습니다 `thisNamespace.xyz.xyzSub` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-120">However, class `xyz` is still promoted, and you can access `xyzSub` with the shorter qualification string `thisNamespace.xyz.xyzSub`.</span></span>  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a><span data-ttu-id="eb62d-121">부분 형식에 대 한 형식 승격의 물리</span><span class="sxs-lookup"><span data-stu-id="eb62d-121">Defeat of Type Promotion for Partial Types</span></span>  

 <span data-ttu-id="eb62d-122">모듈 내의 클래스 또는 구조체에서 [Partial](../../../language-reference/modifiers/partial.md) 키워드를 사용 하는 경우 네임 스페이스에 이름이 같은 멤버가 포함 되어 있는지 여부에 관계 없이 해당 클래스 또는 구조체에 대해 형식 승격이 자동으로 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-122">If a class or structure inside a module uses the [Partial](../../../language-reference/modifiers/partial.md) keyword, type promotion is automatically defeated for that class or structure, whether or not the namespace has a member with the same name.</span></span> <span data-ttu-id="eb62d-123">모듈의 다른 요소는 형식 승격에 대 한 자격이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-123">Other elements in the module are still eligible for type promotion.</span></span>  
  
 <span data-ttu-id="eb62d-124">**미치는.**</span><span class="sxs-lookup"><span data-stu-id="eb62d-124">**Consequences.**</span></span> <span data-ttu-id="eb62d-125">부분 정의의 형식 승격을 물리 하면 예기치 않은 결과 및 컴파일러 오류가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-125">Defeat of type promotion of a partial definition can cause unexpected results and even compiler errors.</span></span> <span data-ttu-id="eb62d-126">다음 예제에서는 클래스의 기본 부분 정의를 보여 줍니다. 그 중 하나는 모듈 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-126">The following example shows skeleton partial definitions of a class, one of which is inside a module.</span></span>  
  
 [!code-vb[VbVbalrDeclaredElements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDeclaredElements/VB/Class1.vb#4)]  
  
 <span data-ttu-id="eb62d-127">앞의 예제에서 개발자는 컴파일러에서의 두 부분 정의를 병합 하는 것을 예측할 수 있습니다 `sampleClass` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-127">In the preceding example, the developer might expect the compiler to merge the two partial definitions of `sampleClass`.</span></span> <span data-ttu-id="eb62d-128">그러나 컴파일러는 내의 부분 정의에 대 한 승격을 고려 하지 않습니다 `sampleModule` .</span><span class="sxs-lookup"><span data-stu-id="eb62d-128">However, the compiler does not consider promotion for the partial definition inside `sampleModule`.</span></span> <span data-ttu-id="eb62d-129">결과적으로 명명 `sampleClass` 되었지만 서로 다른 정규화 경로를 사용 하 여 두 개의 개별 및 고유 클래스를 컴파일하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-129">As a result, it attempts to compile two separate and distinct classes, both named `sampleClass` but with different qualification paths.</span></span>  
  
 <span data-ttu-id="eb62d-130">컴파일러는 정규화된 경로가 동일한 경우에만 부분 정의를 병합합니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-130">The compiler merges partial definitions only when their fully qualified paths are identical.</span></span>  
  
## <a name="recommendations"></a><span data-ttu-id="eb62d-131">권장 사항</span><span class="sxs-lookup"><span data-stu-id="eb62d-131">Recommendations</span></span>  

 <span data-ttu-id="eb62d-132">다음 권장 사항은 바람직한 프로그래밍 습관을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-132">The following recommendations represent good programming practice.</span></span>  
  
- <span data-ttu-id="eb62d-133">**고유 이름.**</span><span class="sxs-lookup"><span data-stu-id="eb62d-133">**Unique Names.**</span></span> <span data-ttu-id="eb62d-134">프로그래밍 요소의 명명에 대 한 모든 권한을 보유 한 경우 항상 고유한 이름을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-134">When you have full control over the naming of programming elements, it is always a good idea to use unique names everywhere.</span></span> <span data-ttu-id="eb62d-135">동일한 이름에는 추가 한정자가 필요 하며 코드를 읽기 어렵게 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-135">Identical names require extra qualification and can make your code harder to read.</span></span> <span data-ttu-id="eb62d-136">또한 미묘한 오류 및 예기치 않은 결과가 발생할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-136">They can also lead to subtle errors and unexpected results.</span></span>  
  
- <span data-ttu-id="eb62d-137">**모든 자격.**</span><span class="sxs-lookup"><span data-stu-id="eb62d-137">**Full Qualification.**</span></span> <span data-ttu-id="eb62d-138">같은 네임 스페이스에서 모듈 및 기타 요소를 사용 하는 경우 가장 안전한 방법은 항상 모든 프로그래밍 요소에 대 한 전체 한정자를 사용 하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-138">When you are working with modules and other elements in the same namespace, the safest approach is to always use full qualification for all programming elements.</span></span> <span data-ttu-id="eb62d-139">모듈 멤버에 대해 형식 승격을 사용할 수 없고 해당 멤버를 완전히 정규화 하지 않은 경우 실수로 다른 프로그래밍 요소에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="eb62d-139">If type promotion is defeated for a module member and you do not fully qualify that member, you could inadvertently access a different programming element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb62d-140">추가 정보</span><span class="sxs-lookup"><span data-stu-id="eb62d-140">See also</span></span>

- [<span data-ttu-id="eb62d-141">Module 문</span><span class="sxs-lookup"><span data-stu-id="eb62d-141">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="eb62d-142">Namespace 문</span><span class="sxs-lookup"><span data-stu-id="eb62d-142">Namespace Statement</span></span>](../../../language-reference/statements/namespace-statement.md)
- [<span data-ttu-id="eb62d-143">부분</span><span class="sxs-lookup"><span data-stu-id="eb62d-143">Partial</span></span>](../../../language-reference/modifiers/partial.md)
- [<span data-ttu-id="eb62d-144">Visual Basic의 범위</span><span class="sxs-lookup"><span data-stu-id="eb62d-144">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="eb62d-145">방법: 변수의 범위 제어</span><span class="sxs-lookup"><span data-stu-id="eb62d-145">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="eb62d-146">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="eb62d-146">References to Declared Elements</span></span>](references-to-declared-elements.md)
