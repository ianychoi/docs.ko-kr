---
description: '자세한 정보: 열거형을 사용 하는 경우 (Visual Basic)'
title: 열거형을 사용하는 경우
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: a29d0e3bb8ac99baf5d43827a8b58701eddcfbdd
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100480741"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a><span data-ttu-id="67ea1-103">열거형을 사용하는 경우(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67ea1-103">When to Use an Enumeration (Visual Basic)</span></span>

<span data-ttu-id="67ea1-104">열거형은 관련 된 상수 집합을 사용 하는 쉬운 방법을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-104">Enumerations offer an easy way to work with sets of related constants.</span></span> <span data-ttu-id="67ea1-105">열거형 (또는) `Enum` 은 값 집합에 대 한 기호화 된 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-105">An enumeration, or `Enum`, is a symbolic name for a set of values.</span></span> <span data-ttu-id="67ea1-106">열거형은 데이터 형식으로 처리 되며 변수 및 속성에 사용할 상수 집합을 만드는 데 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-106">Enumerations are treated as data types, and you can use them to create sets of constants for use with variables and properties.</span></span>  
  
## <a name="when-to-use-an-enumeration"></a><span data-ttu-id="67ea1-107">열거형을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="67ea1-107">When to Use an Enumeration</span></span>  

 <span data-ttu-id="67ea1-108">프로시저에서 제한 된 변수 집합을 허용 하는 경우에는 열거형을 사용 하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-108">Whenever a procedure accepts a limited set of variables, consider using an enumeration.</span></span> <span data-ttu-id="67ea1-109">열거를 사용 하면 특히 의미 있는 이름을 사용 하는 경우 더 명확 하 고 읽기 쉬운 코드를 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-109">Enumerations make for clearer and more readable code, particularly when meaningful names are used.</span></span>  
  
 <span data-ttu-id="67ea1-110">열거형 사용의 이점은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-110">The benefits of using enumerations include:</span></span>  
  
- <span data-ttu-id="67ea1-111">바꾸려면 또는 잘못 된 숫자로 인 한 오류를 줄입니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-111">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
- <span data-ttu-id="67ea1-112">를 사용 하면 나중에 값을 쉽게 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-112">Makes it easy to change values in the future.</span></span>  
  
- <span data-ttu-id="67ea1-113">코드를 더 쉽게 읽을 수 있습니다. 즉, 오류가 증가 하는 가능성이 줄어듭니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-113">Makes code easier to read, which means it is less likely that errors will creep into it.</span></span>  
  
- <span data-ttu-id="67ea1-114">이전 버전과의 호환성을 보장 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-114">Ensures forward compatibility.</span></span> <span data-ttu-id="67ea1-115">열거를 사용 하면 나중에 누군가가 멤버 이름에 해당 하는 값을 변경 하는 경우 코드가 실패할 가능성이 낮아집니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-115">With enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
## <a name="naming-enumerations"></a><span data-ttu-id="67ea1-116">열거형 이름 지정</span><span class="sxs-lookup"><span data-stu-id="67ea1-116">Naming Enumerations</span></span>  

 <span data-ttu-id="67ea1-117">열거형 멤버에 대 한 명명 규칙을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-117">Use a naming convention for enumeration members.</span></span> <span data-ttu-id="67ea1-118">Visual Basic 열거형 멤버 이름이 발견 되 면 참조 된 다른 형식 라이브러리에 같은 이름이 포함 되어 있으면 예외가 throw 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-118">When Visual Basic encounters an enumeration member name, an exception may be thrown if other referenced type libraries contain the same name.</span></span> <span data-ttu-id="67ea1-119">응용 프로그램 또는 구성 요소의 값을 식별 하는 고유한 접두사를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-119">Use a unique prefix that identifies the values from your application or component.</span></span>  
  
 <span data-ttu-id="67ea1-120">열거형의 멤버를 참조 하는 경우 열거형 이름으로 멤버 이름을 한정 하거나 문을 사용 해야 합니다 `Imports` .</span><span class="sxs-lookup"><span data-stu-id="67ea1-120">When referring to a member of an enumeration, you must qualify the member name with the enumeration name or else use the `Imports` statement.</span></span> <span data-ttu-id="67ea1-121">자세한 내용은 [열거 및 이름 한정](enumerations-and-name-qualification.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67ea1-121">For more information, see [Enumerations and Name Qualification](enumerations-and-name-qualification.md).</span></span>  
  
## <a name="predefined-enumerations"></a><span data-ttu-id="67ea1-122">미리 정의 된 열거형</span><span class="sxs-lookup"><span data-stu-id="67ea1-122">Predefined Enumerations</span></span>  

 <span data-ttu-id="67ea1-123">Visual Basic은 `FirstDayOfWeek` 코드를 용이 하 게 하는 및 등의 미리 정의 된 많은 열거형을 제공 `MsgBoxResult` 합니다.</span><span class="sxs-lookup"><span data-stu-id="67ea1-123">Visual Basic provides a number of predefined enumerations, such as `FirstDayOfWeek` and `MsgBoxResult`, to facilitate your code.</span></span> <span data-ttu-id="67ea1-124">이러한 목록은 [상수 및 열거형](../../../language-reference/constants-and-enumerations.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="67ea1-124">For a list of these see [Constants and Enumerations](../../../language-reference/constants-and-enumerations.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ea1-125">추가 정보</span><span class="sxs-lookup"><span data-stu-id="67ea1-125">See also</span></span>

- [<span data-ttu-id="67ea1-126">방법: 열거형 선언</span><span class="sxs-lookup"><span data-stu-id="67ea1-126">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="67ea1-127">방법: 열거형 멤버 참조</span><span class="sxs-lookup"><span data-stu-id="67ea1-127">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="67ea1-128">열거형 및 이름 한정</span><span class="sxs-lookup"><span data-stu-id="67ea1-128">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="67ea1-129">방법: Visual Basic에서 열거형 반복</span><span class="sxs-lookup"><span data-stu-id="67ea1-129">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="67ea1-130">방법: 열거형 값과 연결된 문자열 확인</span><span class="sxs-lookup"><span data-stu-id="67ea1-130">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="67ea1-131">Enum 문</span><span class="sxs-lookup"><span data-stu-id="67ea1-131">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="67ea1-132">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="67ea1-132">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
