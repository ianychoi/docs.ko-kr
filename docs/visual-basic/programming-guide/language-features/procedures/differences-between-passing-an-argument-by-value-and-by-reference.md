---
description: '자세히 알아보기: 인수를 값으로 전달할 때와 참조로 전달할 때의 차이점 (Visual Basic)'
title: 인수를 값으로 전달할 때와 참조로 전달할 때의 차이점
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 632895eae82a20c9bcd773da71f88ebef26d786c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100464731"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="16048-103">인수를 값으로 전달할 때와 참조로 전달할 때의 차이점(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16048-103">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>

<span data-ttu-id="16048-104">하나 이상의 인수를 프로시저에 전달 하는 경우 각 인수는 호출 코드의 기본 프로그래밍 요소에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-104">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="16048-105">이 기본 요소의 값 이나 참조를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-105">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="16048-106">이를 *전달 메커니즘* 이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-106">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="16048-107">값으로 전달</span><span class="sxs-lookup"><span data-stu-id="16048-107">Passing by Value</span></span>  

 <span data-ttu-id="16048-108">프로시저 정의에서 해당 매개 변수에 대해 [ByVal](../../../language-reference/modifiers/byval.md) 키워드를 지정 하 여 인수를 *값으로* 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-108">You pass an argument *by value* by specifying the [ByVal](../../../language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="16048-109">이 전달 메커니즘을 사용 하는 경우 Visual Basic는 기본 프로그래밍 요소의 값을 프로시저의 지역 변수로 복사 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-109">When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="16048-110">프로시저 코드에는 호출 코드의 기본 요소에 대 한 액세스 권한이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-110">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="16048-111">참조로 전달</span><span class="sxs-lookup"><span data-stu-id="16048-111">Passing by Reference</span></span>  

 <span data-ttu-id="16048-112">프로시저 정의에서 해당 매개 변수에 대해 [ByRef](../../../language-reference/modifiers/byref.md) 키워드를 지정 하 여 인수를 *참조로* 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-112">You pass an argument *by reference* by specifying the [ByRef](../../../language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="16048-113">이 전달 메커니즘을 사용 하는 경우 Visual Basic은 호출 코드의 기본 프로그래밍 요소에 대 한 직접 참조를 프로시저에 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-113">When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="16048-114">메커니즘 및 요소 형식 전달</span><span class="sxs-lookup"><span data-stu-id="16048-114">Passing Mechanism and Element Type</span></span>  

 <span data-ttu-id="16048-115">전달 메커니즘의 선택은 기본 요소 형식의 분류와 동일 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-115">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="16048-116">값 또는 참조로 전달 하는 것은 프로시저 코드에 제공 Visual Basic는 것을 의미 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-116">Passing by value or by reference refers to what Visual Basic supplies to the procedure code.</span></span> <span data-ttu-id="16048-117">값 형식 또는 참조 형식은 프로그래밍 요소를 메모리에 저장 하는 방법을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="16048-117">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="16048-118">그러나 전달 메커니즘 및 요소 형식은 서로 연관 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-118">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="16048-119">참조 형식의 값은 메모리의 다른 위치에 있는 데이터에 대 한 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="16048-119">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="16048-120">즉, 참조 형식을 값으로 전달 하는 경우 기본 요소 자체에 액세스할 수 없는 경우에도 프로시저 코드에 기본 요소 데이터에 대 한 포인터가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-120">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="16048-121">예를 들어 요소가 배열 변수인 경우 프로시저 코드는 변수에 대 한 액세스 권한을 갖지 않지만 배열 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-121">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="16048-122">수정 기능</span><span class="sxs-lookup"><span data-stu-id="16048-122">Ability to Modify</span></span>  

 <span data-ttu-id="16048-123">수정할 수 없는 요소를 인수로 전달 하는 경우 프로시저는 해당 요소를 전달 하는지 여부에 관계 없이 호출 코드에서 수정할 수 없습니다 `ByVal` `ByRef` .</span><span class="sxs-lookup"><span data-stu-id="16048-123">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="16048-124">수정 가능한 요소에 대해 다음 표에서는 요소 형식과 전달 메커니즘 간의 상호 작용을 요약 합니다.</span><span class="sxs-lookup"><span data-stu-id="16048-124">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="16048-125">요소 형식</span><span class="sxs-lookup"><span data-stu-id="16048-125">Element type</span></span>|<span data-ttu-id="16048-126">성공한 `ByVal`</span><span class="sxs-lookup"><span data-stu-id="16048-126">Passed `ByVal`</span></span>|<span data-ttu-id="16048-127">성공한 `ByRef`</span><span class="sxs-lookup"><span data-stu-id="16048-127">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="16048-128">값 형식 (값만 포함)</span><span class="sxs-lookup"><span data-stu-id="16048-128">Value type (contains only a value)</span></span>|<span data-ttu-id="16048-129">프로시저는 변수나 해당 멤버를 변경할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-129">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="16048-130">프로시저는 변수와 해당 멤버를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-130">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="16048-131">참조 형식 (클래스 또는 구조체 인스턴스에 대 한 포인터 포함)</span><span class="sxs-lookup"><span data-stu-id="16048-131">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="16048-132">프로시저는 변수를 변경할 수 없지만 해당 변수를 가리키는 인스턴스의 멤버를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-132">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="16048-133">프로시저는 변수가 가리키는 인스턴스의 멤버 및 멤버를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="16048-133">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16048-134">추가 정보</span><span class="sxs-lookup"><span data-stu-id="16048-134">See also</span></span>

- [<span data-ttu-id="16048-135">절차</span><span class="sxs-lookup"><span data-stu-id="16048-135">Procedures</span></span>](./index.md)
- [<span data-ttu-id="16048-136">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="16048-136">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="16048-137">방법: 프로시저에 인수 전달</span><span class="sxs-lookup"><span data-stu-id="16048-137">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="16048-138">값 또는 참조로 인수 전달</span><span class="sxs-lookup"><span data-stu-id="16048-138">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="16048-139">수정할 수 있는 인수와 수정할 수 없는 인수의 차이점</span><span class="sxs-lookup"><span data-stu-id="16048-139">Differences Between Modifiable and Nonmodifiable Arguments</span></span>](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [<span data-ttu-id="16048-140">방법: 프로시저 인수의 값 변경</span><span class="sxs-lookup"><span data-stu-id="16048-140">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)
- [<span data-ttu-id="16048-141">방법: 값 변경으로부터 프로시저 인수 보호</span><span class="sxs-lookup"><span data-stu-id="16048-141">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [<span data-ttu-id="16048-142">방법: 인수가 값으로 전달되도록 설정</span><span class="sxs-lookup"><span data-stu-id="16048-142">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)
- [<span data-ttu-id="16048-143">위치 및 이름으로 인수 전달</span><span class="sxs-lookup"><span data-stu-id="16048-143">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="16048-144">Value Types and Reference Types</span><span class="sxs-lookup"><span data-stu-id="16048-144">Value Types and Reference Types</span></span>](../data-types/value-types-and-reference-types.md)
