---
description: '자세한 정보: 방법: 속성 만들기 (Visual Basic)'
title: '방법: 속성 만들기'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
ms.openlocfilehash: cf6c76f6a6284cf055f16cf3973da1bb1c54e48d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472477"
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="3b14f-103">방법: 속성 만들기(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b14f-103">How to: Create a Property (Visual Basic)</span></span>

<span data-ttu-id="3b14f-104">문과 문 사이에 속성 정의를 묶습니다 `Property` `End Property` .</span><span class="sxs-lookup"><span data-stu-id="3b14f-104">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="3b14f-105">이 정의 내에서 `Get` 프로시저, `Set` 프로시저 또는 둘 다를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-105">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="3b14f-106">모든 속성의 코드는 이러한 프로시저 내에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-106">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="3b14f-107">`Get`프로시저는 속성의 값을 검색 하 고 `Set` 프로시저는 값을 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-107">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="3b14f-108">속성에 읽기/쓰기 액세스 권한을 지정 하려면 두 프로시저를 모두 정의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-108">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="3b14f-109">읽기 전용 속성의 경우만 정의 하 `Get` 고 쓰기 전용 속성의 경우만 정의 `Set` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-109">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="3b14f-110">속성을 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b14f-110">To create a property</span></span>  
  
1. <span data-ttu-id="3b14f-111">속성이 나 프로시저 외부에서 [속성 문과](../../../language-reference/statements/property-statement.md)문을 차례로 사용 `End Property` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-111">Outside any property or procedure, use a [Property Statement](../../../language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2. <span data-ttu-id="3b14f-112">속성이 매개 변수를 사용 하는 경우에는 `Property` 프로시저 이름으로 키워드를 따르고 매개 변수 목록을 괄호로 묶습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-112">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="3b14f-113">절을 사용 하 여 괄호를 따라 `As` 속성 값의 데이터 형식을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-113">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="3b14f-114">쓰기 전용 속성의 경우에도 데이터 형식을 지정 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-114">You must specify the data type even for a write-only property.</span></span>  
  
4. <span data-ttu-id="3b14f-115">`Get`및 `Set` 프로시저를 적절 하 게 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-115">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="3b14f-116">다음 지침을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="3b14f-116">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="3b14f-117">속성 값을 검색 하는 Get 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b14f-117">To create a Get procedure that retrieves a property value</span></span>  
  
1. <span data-ttu-id="3b14f-118">문과 문 사이에 `Property` `End Property` [Get 문과](../../../language-reference/statements/get-statement.md)문을 차례로 작성 `End Get` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-118">Between the `Property` and `End Property` statements, write a [Get Statement](../../../language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="3b14f-119">프로시저에 대 한 매개 변수를 정의할 필요가 없습니다 `Get` .</span><span class="sxs-lookup"><span data-stu-id="3b14f-119">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2. <span data-ttu-id="3b14f-120">및 문 사이에 속성의 값을 검색 하는 코드 문을 추가 합니다 `Get` `End Get` .</span><span class="sxs-lookup"><span data-stu-id="3b14f-120">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="3b14f-121">이 코드에는 속성 값을 생성 하 고 반환 하는 것 외에 다른 계산과 데이터 조작을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-121">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3. <span data-ttu-id="3b14f-122">문을 사용 `Return` 하 여 속성의 값을 호출 코드에 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-122">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="3b14f-123">읽기/ `Get` 쓰기 속성 및 읽기 전용 속성에 대 한 프로시저를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-123">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="3b14f-124">`Get`쓰기 전용 속성에 대 한 프로시저를 정의 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-124">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="3b14f-125">속성 값을 쓰는 Set 프로시저를 만들려면</span><span class="sxs-lookup"><span data-stu-id="3b14f-125">To create a Set procedure that writes a property's value</span></span>  
  
1. <span data-ttu-id="3b14f-126">문과 문 사이에 `Property` `End Property` 문이 오는 [Set 문](../../../language-reference/statements/set-statement.md)을 작성 `End Set` 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-126">Between the `Property` and `End Property` statements, write a [Set Statement](../../../language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2. <span data-ttu-id="3b14f-127">`Set`문에서 `Set` 키워드를 괄호 안에 매개 변수 목록과 함께 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-127">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="3b14f-128">이 매개 변수 목록은 호출 코드에서 전달 된 값에 대해 적어도 하나의 값 매개 변수를 포함 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-128">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="3b14f-129">이 값 매개 변수에 대 한 기본 이름은 이지만 해당 하는 `Value` 경우 다른 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-129">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="3b14f-130">값 매개 변수는 속성 자체와 동일한 데이터 형식 이어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-130">The value parameter must have the same data type as the property itself.</span></span>  
  
3. <span data-ttu-id="3b14f-131">및 문 사이에 속성의 값을 저장 하는 코드 문을 추가 합니다 `Set` `End Set` .</span><span class="sxs-lookup"><span data-stu-id="3b14f-131">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="3b14f-132">이 코드에는 속성 값의 유효성을 검사 하 고 저장 하는 것 외에 다른 계산과 데이터 조작을 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-132">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4. <span data-ttu-id="3b14f-133">값 매개 변수를 사용 하 여 호출 코드에서 제공 하는 값을 적용 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-133">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="3b14f-134">이 값을 대입문에 직접 저장 하거나 식에 사용 하 여 저장할 내부 값을 계산할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-134">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="3b14f-135">`Set`읽기/쓰기 속성 및 쓰기 전용 속성에 대 한 프로시저를 작성 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-135">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="3b14f-136">`Set`읽기 전용 속성에 대 한 프로시저를 정의 하면 안 됩니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-136">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b14f-137">예</span><span class="sxs-lookup"><span data-stu-id="3b14f-137">Example</span></span>  

 <span data-ttu-id="3b14f-138">다음 예에서는 전체 이름을 두 개의 구성 이름, 이름 및 성으로 저장 하는 읽기/쓰기 속성을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-138">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="3b14f-139">호출 코드가 읽는 경우 `fullName` `Get` 프로시저는 두 가지 구성 이름을 결합 하 고 전체 이름을 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-139">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="3b14f-140">호출 코드에서 새 전체 이름을 할당 하면 `Set` 프로시저는 두 개의 구성 된 이름으로 코드를 분리 하려고 시도 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-140">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="3b14f-141">공백을 찾지 못하면 모두 이름으로 저장 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-141">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#8)]  
  
 <span data-ttu-id="3b14f-142">다음 예에서는의 속성 프로시저에 대 한 일반적인 호출을 보여 줍니다 `fullName` .</span><span class="sxs-lookup"><span data-stu-id="3b14f-142">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="3b14f-143">첫 번째 호출은 속성 값을 설정 하 고 두 번째 호출은이를 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="3b14f-143">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3b14f-144">추가 정보</span><span class="sxs-lookup"><span data-stu-id="3b14f-144">See also</span></span>

- [<span data-ttu-id="3b14f-145">절차</span><span class="sxs-lookup"><span data-stu-id="3b14f-145">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3b14f-146">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="3b14f-146">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3b14f-147">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="3b14f-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3b14f-148">Visual Basic에서 속성과 변수의 차이점</span><span class="sxs-lookup"><span data-stu-id="3b14f-148">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="3b14f-149">방법: 액세스 수준이 혼합된 속성 선언</span><span class="sxs-lookup"><span data-stu-id="3b14f-149">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="3b14f-150">방법: 속성 프로시저 호출</span><span class="sxs-lookup"><span data-stu-id="3b14f-150">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)
- [<span data-ttu-id="3b14f-151">방법: Visual Basic에서 기본 속성 선언 및 호출</span><span class="sxs-lookup"><span data-stu-id="3b14f-151">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="3b14f-152">방법: 속성 값 입력</span><span class="sxs-lookup"><span data-stu-id="3b14f-152">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- [<span data-ttu-id="3b14f-153">방법: 속성에서 값 가져오기</span><span class="sxs-lookup"><span data-stu-id="3b14f-153">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
