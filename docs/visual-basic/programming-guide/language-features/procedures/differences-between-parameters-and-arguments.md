---
description: '자세한 정보: 매개 변수와 인수 간의 차이점 (Visual Basic)'
title: 매개 변수와 인수의 차이점
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
ms.openlocfilehash: 01efc7dc3f451d6aae20cfd091355f531af4431c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100438764"
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="e2885-103">매개 변수와 인수의 차이점(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e2885-103">Differences Between Parameters and Arguments (Visual Basic)</span></span>

<span data-ttu-id="e2885-104">대부분의 경우 프로시저에는 호출 된 상황에 대 한 정보가 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-104">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="e2885-105">반복 되거나 공유 된 작업을 수행 하는 프로시저는 각 호출에 대해 서로 다른 정보를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-105">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="e2885-106">이 정보는 프로시저를 호출할 때 프로시저에 전달 하는 변수, 상수 및 식으로 구성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-106">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="e2885-107">프로시저에이 정보를 전달 하기 위해 프로시저는 *매개 변수* 를 정의 하 고 호출 하는 코드는 *인수* 를 해당 매개 변수에 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-107">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="e2885-108">매개 변수를 파킹 공간으로, 인수를 자동차로 간주할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-108">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="e2885-109">서로 다른 시간에 서로 다른 자동차이 주차 공간을 파킹 할 수 있는 것 처럼 호출 코드는 프로시저를 호출할 때마다 동일한 매개 변수에 다른 인수를 전달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-109">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="e2885-110">매개 변수</span><span class="sxs-lookup"><span data-stu-id="e2885-110">Parameters</span></span>  

 <span data-ttu-id="e2885-111">*매개 변수* 는 프로시저에서 호출할 때 전달할 것으로 예상 하는 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-111">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="e2885-112">프로시저의 선언에서 매개 변수를 정의 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-112">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="e2885-113">또는 프로시저를 정의할 `Function` 때는 `Sub` 프로시저 이름 바로 뒤에 괄호 안에 *매개 변수 목록을* 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-113">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="e2885-114">각 매개 변수에 대해 이름, 데이터 형식 및 전달 메커니즘 ([ByVal](../../../language-reference/modifiers/byval.md) 또는 [ByRef](../../../language-reference/modifiers/byref.md))을 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-114">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../language-reference/modifiers/byval.md) or [ByRef](../../../language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="e2885-115">매개 변수가 선택적 임을 나타낼 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-115">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="e2885-116">즉, 호출 하는 코드에서 값을 전달할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-116">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="e2885-117">각 매개 변수의 이름은 프로시저에서 *지역 변수로* 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-117">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="e2885-118">다른 변수를 사용 하는 것과 동일한 방식으로 매개 변수 이름을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-118">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="e2885-119">인수</span><span class="sxs-lookup"><span data-stu-id="e2885-119">Arguments</span></span>  

 <span data-ttu-id="e2885-120">*인수* 는 프로시저를 호출할 때 프로시저 매개 변수에 전달 하는 값을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-120">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="e2885-121">호출 코드는 프로시저를 호출할 때 인수를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-121">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="e2885-122">또는 프로시저를 호출 하는 경우 `Function` `Sub` 프로시저 이름 바로 뒤에 괄호 안에 *인수 목록을* 포함 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-122">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="e2885-123">각 인수는 목록에서 같은 위치에 있는 매개 변수에 해당 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-123">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="e2885-124">매개 변수 정의와 달리 인수에는 이름이 없습니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-124">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="e2885-125">각 인수는 0 개 이상의 변수, 상수 및 리터럴을 포함할 수 있는 식입니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-125">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="e2885-126">계산 된 식의 데이터 형식은 일반적으로 해당 매개 변수에 대해 정의 된 데이터 형식과 일치 해야 하며, 모든 경우에 매개 변수 형식으로 변환할 수 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e2885-126">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2885-127">추가 정보</span><span class="sxs-lookup"><span data-stu-id="e2885-127">See also</span></span>

- [<span data-ttu-id="e2885-128">절차</span><span class="sxs-lookup"><span data-stu-id="e2885-128">Procedures</span></span>](./index.md)
- [<span data-ttu-id="e2885-129">하위 프로시저</span><span class="sxs-lookup"><span data-stu-id="e2885-129">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="e2885-130">함수 프로시저</span><span class="sxs-lookup"><span data-stu-id="e2885-130">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="e2885-131">속성 프로시저</span><span class="sxs-lookup"><span data-stu-id="e2885-131">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="e2885-132">연산자 프로시저</span><span class="sxs-lookup"><span data-stu-id="e2885-132">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="e2885-133">방법: 프로시저의 매개 변수 정의</span><span class="sxs-lookup"><span data-stu-id="e2885-133">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)
- [<span data-ttu-id="e2885-134">방법: 프로시저에 인수 전달</span><span class="sxs-lookup"><span data-stu-id="e2885-134">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)
- [<span data-ttu-id="e2885-135">값 또는 참조로 인수 전달</span><span class="sxs-lookup"><span data-stu-id="e2885-135">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="e2885-136">재귀 프로시저</span><span class="sxs-lookup"><span data-stu-id="e2885-136">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="e2885-137">프로시저 오버로딩</span><span class="sxs-lookup"><span data-stu-id="e2885-137">Procedure Overloading</span></span>](./procedure-overloading.md)
