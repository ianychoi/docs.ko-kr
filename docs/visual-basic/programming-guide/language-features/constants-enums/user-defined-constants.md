---
description: '다음에 대 한 자세한 정보: 상수 User-Defined (Visual Basic)'
title: 사용자 정의 상수
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 290d4122249315ae3c6dc5e18ca4faefecb72044
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485226"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="e7a44-103">사용자 정의 상수(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7a44-103">User-Defined Constants (Visual Basic)</span></span>

<span data-ttu-id="e7a44-104">상수는 변경 되지 않는 숫자 또는 문자열을 대신 사용 하는 의미 있는 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-104">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="e7a44-105">상수는 애플리케이션 실행 중 변함없이 유지되는 값을 저장합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-105">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="e7a44-106">작업 하는 컨트롤이 나 구성 요소에 의해 정의 된 상수를 사용 하거나 직접 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-106">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="e7a44-107">직접 만든 상수는 *사용자 정의* 로 설명 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-107">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="e7a44-108">`Const`변수 이름을 만드는 것과 동일한 지침을 사용 하 여 문을 사용 하 여 상수를 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-108">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="e7a44-109">`Option Strict`가 이면 `On` 상수 형식을 명시적으로 선언 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-109">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="e7a44-110">Const 문 사용</span><span class="sxs-lookup"><span data-stu-id="e7a44-110">Const Statement Usage</span></span>  

 <span data-ttu-id="e7a44-111">`Const`문은 수학 또는 날짜/시간 수량을 나타낼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-111">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="e7a44-112">상수를 정의할 수도 있습니다 `String` .</span><span class="sxs-lookup"><span data-stu-id="e7a44-112">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="e7a44-113">등호 ()의 오른쪽에 있는 식은 `=` 종종 숫자 또는 리터럴 문자열 이지만 숫자나 문자열이 발생 하는 식일 수도 있습니다 (식에서 함수에 대 한 호출을 포함할 수는 없음).</span><span class="sxs-lookup"><span data-stu-id="e7a44-113">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="e7a44-114">이전에 정의 된 상수를 기준으로 상수를 정의할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-114">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="e7a44-115">User-Defined 상수 범위</span><span class="sxs-lookup"><span data-stu-id="e7a44-115">Scope of User-Defined Constants</span></span>  

 <span data-ttu-id="e7a44-116">`Const`문의 범위는 동일한 위치에 선언 된 변수의 변수와 같습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-116">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="e7a44-117">다음 방법 중 하나를 지정 하 여 범위를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-117">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="e7a44-118">프로시저 내에만 존재 하는 상수를 만들려면 해당 프로시저 내에서 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-118">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="e7a44-119">클래스 내의 모든 프로시저에서 사용할 수 있지만 해당 모듈 외부의 코드에는 사용할 수 없는 상수를 만들려면 클래스의 선언 섹션에서 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-119">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e7a44-120">어셈블리의 모든 멤버에 사용할 수 있지만 어셈블리의 외부 클라이언트에는 사용할 수 없는 상수를 만들려면 `Friend` 클래스의 선언 섹션에서 키워드를 사용 하 여 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-120">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e7a44-121">응용 프로그램 전체에서 사용할 수 있는 상수를 만들려면 `Public` 클래스의 선언 섹션에서 키워드를 사용 하 여 선언 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-121">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="e7a44-122">자세한 내용은 [방법: 상수 선언](how-to-declare-a-constant.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7a44-122">For more information, see [How to: Declare A Constant](how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="e7a44-123">순환 참조 방지</span><span class="sxs-lookup"><span data-stu-id="e7a44-123">Avoiding Circular References</span></span>  

 <span data-ttu-id="e7a44-124">상수 *는 다른* 상수를 기준으로 정의 될 수 있으므로 실수로 두 개 이상의 상수 사이에 순환 또는 순환 참조를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-124">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="e7a44-125">다음 예제와 같이 둘 이상의 public 상수를 사용 하는 경우 각 상수는 서로를 기준으로 정의 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-125">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="e7a44-126">순환이 발생 하면 Visual Basic는 컴파일러 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7a44-126">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a44-127">추가 정보</span><span class="sxs-lookup"><span data-stu-id="e7a44-127">See also</span></span>

- [<span data-ttu-id="e7a44-128">Const 문</span><span class="sxs-lookup"><span data-stu-id="e7a44-128">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
- [<span data-ttu-id="e7a44-129">상수 및 리터럴 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="e7a44-129">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="e7a44-130">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="e7a44-130">Constants and Enumerations</span></span>](index.md)
- [<span data-ttu-id="e7a44-131">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="e7a44-131">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="e7a44-132">열거형 개요</span><span class="sxs-lookup"><span data-stu-id="e7a44-132">Enumerations Overview</span></span>](enumerations-overview.md)
- [<span data-ttu-id="e7a44-133">상수 개요</span><span class="sxs-lookup"><span data-stu-id="e7a44-133">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="e7a44-134">방법: 열거형 선언</span><span class="sxs-lookup"><span data-stu-id="e7a44-134">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="e7a44-135">열거형 및 이름 한정</span><span class="sxs-lookup"><span data-stu-id="e7a44-135">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="e7a44-136">Option Strict 문</span><span class="sxs-lookup"><span data-stu-id="e7a44-136">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
