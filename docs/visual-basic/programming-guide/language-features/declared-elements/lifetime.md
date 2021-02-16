---
description: '자세한 정보: 수명 Visual Basic'
title: 수명
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 7c95358209c61b42862f4e995d02a97dfb6e8487
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471463"
---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="25805-103">Visual Basic의 수명</span><span class="sxs-lookup"><span data-stu-id="25805-103">Lifetime in Visual Basic</span></span>

<span data-ttu-id="25805-104">선언 된 요소의 *수명은* 사용할 수 있는 기간입니다.</span><span class="sxs-lookup"><span data-stu-id="25805-104">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="25805-105">변수는 수명이 있는 유일한 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="25805-105">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="25805-106">이러한 목적을 위해 컴파일러는 프로시저 매개 변수와 함수 반환을 변수의 특수 한 경우로 처리 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-106">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="25805-107">변수의 수명은 값을 보유할 수 있는 기간을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="25805-107">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="25805-108">해당 값은 수명에 따라 변경 될 수 있지만 항상 일부 값을 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-108">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="25805-109">다른 수명</span><span class="sxs-lookup"><span data-stu-id="25805-109">Different Lifetimes</span></span>  

 <span data-ttu-id="25805-110">*멤버 변수* (프로시저 외부의 모듈 수준에서 선언 됨)는 일반적으로 선언 되는 요소의 수명과 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-110">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="25805-111">클래스 또는 구조체에서 선언 된 비공유 변수가 선언 된 클래스 또는 구조체의 각 인스턴스에 대해 별도의 복사본으로 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-111">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="25805-112">이러한 각 변수의 수명은 인스턴스와 동일 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-112">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="25805-113">그러나 변수에는 `Shared` 응용 프로그램이 실행 되는 전체 시간 동안 지속 되는 단일 수명이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-113">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="25805-114">프로시저 내에 선언 된 *지역 변수* 는 해당 변수가 선언 된 프로시저가 실행 되는 동안에만 존재 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-114">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="25805-115">이는 해당 프로시저의 매개 변수와 함수 반환에도 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-115">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="25805-116">그러나 해당 프로시저가 다른 프로시저를 호출 하는 경우 호출 된 프로시저를 실행 하는 동안에는 지역 변수가 해당 값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-116">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="25805-117">수명 시작</span><span class="sxs-lookup"><span data-stu-id="25805-117">Beginning of Lifetime</span></span>  

 <span data-ttu-id="25805-118">지역 변수의 수명은 컨트롤이 선언 된 프로시저를 시작할 때 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-118">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="25805-119">모든 지역 변수는 프로시저 실행이 시작 되는 즉시 해당 데이터 형식에 대 한 기본값으로 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-119">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="25805-120">프로시저에서 `Dim` 초기 값을 지정 하는 문이 발견 될 때 코드에 다른 값을 이미 할당 한 경우에도 해당 변수를 해당 값으로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-120">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="25805-121">구조체 변수의 각 멤버는 개별 변수인 것 처럼 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-121">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="25805-122">마찬가지로 배열 변수의 각 요소는 개별적으로 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-122">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="25805-123">프로시저 내의 블록 (예: 루프) 내에서 선언 `For` 된 변수는 프로시저에 대 한 항목에서 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-123">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="25805-124">이러한 초기화는 코드에서 블록을 실행 하는지 여부에 관계 없이 적용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-124">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="25805-125">수명 끝</span><span class="sxs-lookup"><span data-stu-id="25805-125">End of Lifetime</span></span>  

 <span data-ttu-id="25805-126">프로시저가 종료 되 면 해당 지역 변수의 값은 유지 되지 않으며 Visual Basic 메모리를 회수 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-126">When a procedure terminates, the values of its local variables are not preserved, and Visual Basic reclaims their memory.</span></span> <span data-ttu-id="25805-127">다음 번에 프로시저를 호출 하면 모든 지역 변수가 새로 생성 되어 다시 초기화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-127">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="25805-128">클래스 또는 구조체의 인스턴스가 종료 되 면 비공유 변수의 메모리와 값이 손실 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-128">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="25805-129">클래스 또는 구조체의 새 인스턴스는 모두 비공유 변수를 만들고 다시 초기화 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-129">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="25805-130">그러나 `Shared` 변수는 응용 프로그램 실행이 중지 될 때까지 유지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-130">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="25805-131">수명 확장</span><span class="sxs-lookup"><span data-stu-id="25805-131">Extension of Lifetime</span></span>  

 <span data-ttu-id="25805-132">키워드를 사용 하 여 지역 변수를 선언 하는 경우 `Static` 해당 수명은 프로시저의 실행 시간 보다 깁니다.</span><span class="sxs-lookup"><span data-stu-id="25805-132">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="25805-133">다음 표에서는 프로시저 선언에 변수가 존재 하는 기간을 결정 하는 방법을 보여 줍니다 `Static` .</span><span class="sxs-lookup"><span data-stu-id="25805-133">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="25805-134">프로시저 위치 및 공유</span><span class="sxs-lookup"><span data-stu-id="25805-134">Procedure location and sharing</span></span>|<span data-ttu-id="25805-135">정적 변수 수명이 시작 됩니다.</span><span class="sxs-lookup"><span data-stu-id="25805-135">Static variable lifetime begins</span></span>|<span data-ttu-id="25805-136">정적 변수 수명 종료</span><span class="sxs-lookup"><span data-stu-id="25805-136">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="25805-137">모듈 (기본적으로 공유)</span><span class="sxs-lookup"><span data-stu-id="25805-137">In a module (shared by default)</span></span>|<span data-ttu-id="25805-138">프로시저가 처음 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="25805-138">The first time the procedure is called</span></span>|<span data-ttu-id="25805-139">응용 프로그램 실행이 중지 되는 경우</span><span class="sxs-lookup"><span data-stu-id="25805-139">When your application stops running</span></span>|  
|<span data-ttu-id="25805-140">클래스에서 `Shared` (프로시저는 인스턴스 멤버가 아님)</span><span class="sxs-lookup"><span data-stu-id="25805-140">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="25805-141">프로시저가 특정 인스턴스나 클래스 또는 구조체 이름 자체에서 처음 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="25805-141">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="25805-142">응용 프로그램 실행이 중지 되는 경우</span><span class="sxs-lookup"><span data-stu-id="25805-142">When your application stops running</span></span>|  
|<span data-ttu-id="25805-143">클래스의 인스턴스에서는 그렇지 않습니다 `Shared` (프로시저는 인스턴스 멤버).</span><span class="sxs-lookup"><span data-stu-id="25805-143">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="25805-144">프로시저가 특정 인스턴스에서 처음으로 호출 될 때</span><span class="sxs-lookup"><span data-stu-id="25805-144">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="25805-145">GC (가비지 수집)를 위해 인스턴스를 해제 하는 경우</span><span class="sxs-lookup"><span data-stu-id="25805-145">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="25805-146">이름이 같은 정적 변수</span><span class="sxs-lookup"><span data-stu-id="25805-146">Static Variables of the Same Name</span></span>  

 <span data-ttu-id="25805-147">둘 이상의 프로시저에서 동일한 이름으로 정적 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-147">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="25805-148">이 작업을 수행 하는 경우 Visual Basic 컴파일러는 이러한 각 변수를 별도 요소로 간주 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-148">If you do this, the Visual Basic compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="25805-149">이러한 변수 중 하나를 초기화 해도 다른 변수 값에는 영향을 주지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-149">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="25805-150">오버 로드 집합을 사용 하 여 프로시저를 정의 하 고 각 오버 로드에서 동일한 이름을 사용 하 여 정적 변수를 선언 하는 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="25805-150">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="25805-151">정적 변수에 대 한 요소 포함</span><span class="sxs-lookup"><span data-stu-id="25805-151">Containing Elements for Static Variables</span></span>  

 <span data-ttu-id="25805-152">클래스 내에서, 즉 해당 클래스의 프로시저 내에서 정적 지역 변수를 선언할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-152">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="25805-153">그러나 구조체 내에서 정적 지역 변수를 구조체 멤버 또는 해당 구조 내 프로시저의 지역 변수로 선언할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-153">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25805-154">예제</span><span class="sxs-lookup"><span data-stu-id="25805-154">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="25805-155">설명</span><span class="sxs-lookup"><span data-stu-id="25805-155">Description</span></span>  

 <span data-ttu-id="25805-156">다음 예에서는 [Static](../../../language-reference/modifiers/static.md) 키워드를 사용 하 여 변수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-156">The following example declares a variable with the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="25805-157">`Dim` [Dim 문이](../../../language-reference/statements/dim-statement.md) 와 같은 한정자를 사용 하는 경우에는 키워드가 필요 하지 않습니다 `Static` .</span><span class="sxs-lookup"><span data-stu-id="25805-157">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="25805-158">코드</span><span class="sxs-lookup"><span data-stu-id="25805-158">Code</span></span>  

 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a><span data-ttu-id="25805-159">주석</span><span class="sxs-lookup"><span data-stu-id="25805-159">Comments</span></span>  

 <span data-ttu-id="25805-160">위의 예제에서 변수는 `applesSold` 프로시저가 호출 코드에 반환 된 후에도 계속 존재 `runningTotal` 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-160">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="25805-161">다음 번에 `runningTotal` 를 호출 하면 `applesSold` 이전에 계산 된 값을 유지 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-161">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="25805-162">를 `applesSold` 사용 하지 않고 선언한 경우 `Static` 이전 누적 값은에 대 한 호출에서 유지 되지 않습니다 `runningTotal` .</span><span class="sxs-lookup"><span data-stu-id="25805-162">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="25805-163">다음에 `runningTotal` 를 호출 하면가 `applesSold` 다시 생성 되 고 0으로 초기화 되며, `runningTotal` 호출 된 것과 동일한 값을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="25805-163">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compile-the-code"></a><span data-ttu-id="25805-164">코드 컴파일</span><span class="sxs-lookup"><span data-stu-id="25805-164">Compile the code</span></span>  

 <span data-ttu-id="25805-165">정적 지역 변수의 값을 선언의 일부로 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-165">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="25805-166">배열을로 선언 하는 경우 `Static` 차수 (차원 수), 각 차원의 길이 및 개별 요소의 값을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-166">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="25805-167">보안</span><span class="sxs-lookup"><span data-stu-id="25805-167">Security</span></span>  

 <span data-ttu-id="25805-168">위의 예에서는 모듈 수준에서을 선언 하 여 동일한 수명을 생성할 수 있습니다 `applesSold` .</span><span class="sxs-lookup"><span data-stu-id="25805-168">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="25805-169">그러나 이러한 방식으로 변수의 범위를 변경한 경우 프로시저는 더 이상 단독으로 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-169">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="25805-170">다른 프로시저 `applesSold` 에서 해당 값에 액세스 하 고 해당 값을 변경할 수 있으므로 누계를 신뢰할 수 없으며 코드를 유지 관리 하기가 더 어려울 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="25805-170">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25805-171">추가 정보</span><span class="sxs-lookup"><span data-stu-id="25805-171">See also</span></span>

- [<span data-ttu-id="25805-172">공유</span><span class="sxs-lookup"><span data-stu-id="25805-172">Shared</span></span>](../../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="25805-173">Nothing</span><span class="sxs-lookup"><span data-stu-id="25805-173">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="25805-174">Declared Element Names</span><span class="sxs-lookup"><span data-stu-id="25805-174">Declared Element Names</span></span>](declared-element-names.md)
- [<span data-ttu-id="25805-175">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="25805-175">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="25805-176">Visual Basic의 범위</span><span class="sxs-lookup"><span data-stu-id="25805-176">Scope in Visual Basic</span></span>](scope.md)
- [<span data-ttu-id="25805-177">Visual Basic의 액세스 수준</span><span class="sxs-lookup"><span data-stu-id="25805-177">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="25805-178">변수</span><span class="sxs-lookup"><span data-stu-id="25805-178">Variables</span></span>](../variables/index.md)
- [<span data-ttu-id="25805-179">변수 선언</span><span class="sxs-lookup"><span data-stu-id="25805-179">Variable Declaration</span></span>](../variables/variable-declaration.md)
- [<span data-ttu-id="25805-180">데이터 형식 문제 해결</span><span class="sxs-lookup"><span data-stu-id="25805-180">Troubleshooting Data Types</span></span>](../data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="25805-181">정적</span><span class="sxs-lookup"><span data-stu-id="25805-181">Static</span></span>](../../../language-reference/modifiers/static.md)
