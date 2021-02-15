---
description: '자세한 정보: 열거형 및 이름 한정 (Visual Basic)'
title: 열거형 및 이름 한정
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: 83f5b894dad821fea920386be905de0b51f9c42f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100477478"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a><span data-ttu-id="074cb-103">열거형 및 이름 한정(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="074cb-103">Enumerations and Name Qualification (Visual Basic)</span></span>

<span data-ttu-id="074cb-104">일반적으로 열거형의 멤버를 참조할 때는 열거형 이름으로 멤버 이름을 한 정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-104">Normally, when referring to a member of an enumeration, you must qualify the member name with the enumeration name.</span></span> <span data-ttu-id="074cb-105">예를 들어, `Sunday` 열거형의 멤버를 참조 하려면 `Days` 다음 구문을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-105">For example, to refer to the `Sunday` member of your `Days` enumeration, you would use the following syntax:</span></span>  
  
 [!code-vb[VbEnumsTask#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#18)]  
  
## <a name="using-the-imports-statement"></a><span data-ttu-id="074cb-106">Imports 문 사용</span><span class="sxs-lookup"><span data-stu-id="074cb-106">Using the Imports Statement</span></span>  

 <span data-ttu-id="074cb-107">`Imports`다음 예제와 같이 코드의 네임 스페이스 선언 섹션에 문을 추가 하 여 정규화 된 이름을 사용 하지 않을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-107">You can avoid using fully qualified names by adding an `Imports` statement to the namespace declarations section of your code, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 <span data-ttu-id="074cb-108">`Imports`문은 참조 된 프로젝트 및 어셈블리에서 그리고 문이 표시 되는 모듈과 동일한 프로젝트 내에서 네임 스페이스 이름을 가져옵니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-108">An `Imports` statement imports namespace names from referenced projects and assemblies and from within the same project as the module in which the statement appears.</span></span> <span data-ttu-id="074cb-109">이 문이 추가 되 면 다음 예제와 같이 한정자를 사용 하지 않고 열거형 멤버를 참조할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-109">Once this statement is added, you can refer to your enumeration members without qualification, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#24)]  
  
 <span data-ttu-id="074cb-110">관련 상수 집합을 열거형으로 구성 하면 서로 다른 컨텍스트에서 동일한 상수 이름을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-110">By organizing sets of related constants in enumerations, you can use the same constant names in different contexts.</span></span> <span data-ttu-id="074cb-111">예를 들어 및 열거형에서 요일 상수에 동일한 이름을 사용할 수 있습니다 `Days` `WorkDays` .</span><span class="sxs-lookup"><span data-stu-id="074cb-111">For example, you can use the same names for the weekday constants in the `Days` and `WorkDays` enumerations.</span></span> <span data-ttu-id="074cb-112">`Imports`열거형과 함께 문을 사용 하는 경우 모호한 참조가 발생 하지 않도록 주의 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-112">If you use the `Imports` statement with your enumerations, you must be careful to avoid ambiguous references.</span></span> <span data-ttu-id="074cb-113">다음 예제를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="074cb-113">Consider the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#22)]  
  
 [!code-vb[VbEnumsTask#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#25)]  
  
 <span data-ttu-id="074cb-114">`Monday`가 열거형과 열거형의 멤버 라고 가정 `Days` `Workdays` 하면이 코드는 컴파일러 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-114">Assuming that `Monday` is a member of both the `Days` enumeration and the `Workdays` enumeration, this code generates a compiler error.</span></span> <span data-ttu-id="074cb-115">개별 상수를 참조할 때 모호한 참조를 방지 하려면 해당 열거형을 사용 하 여 상수 이름을 한정 합니다.</span><span class="sxs-lookup"><span data-stu-id="074cb-115">To avoid ambiguous references when referring to an individual constant, qualify the constant name with its enumeration.</span></span> <span data-ttu-id="074cb-116">다음 코드에서는 `Saturday` 및 열거형의 상수를 참조 `Days` 합니다 `WorkDays` .</span><span class="sxs-lookup"><span data-stu-id="074cb-116">The following code refers to the `Saturday` constants in the `Days` and `WorkDays` enumerations.</span></span>  
  
 [!code-vb[VbEnumsTask#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="074cb-117">추가 정보</span><span class="sxs-lookup"><span data-stu-id="074cb-117">See also</span></span>

- [<span data-ttu-id="074cb-118">상수 및 열거형</span><span class="sxs-lookup"><span data-stu-id="074cb-118">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="074cb-119">방법: 열거형 선언</span><span class="sxs-lookup"><span data-stu-id="074cb-119">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="074cb-120">방법: 열거형 멤버 참조</span><span class="sxs-lookup"><span data-stu-id="074cb-120">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="074cb-121">방법: Visual Basic에서 열거형 반복</span><span class="sxs-lookup"><span data-stu-id="074cb-121">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="074cb-122">방법: 열거형 값과 연결된 문자열 확인</span><span class="sxs-lookup"><span data-stu-id="074cb-122">How to: Determine the String Associated with an Enumeration Value</span></span>](how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [<span data-ttu-id="074cb-123">열거형을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="074cb-123">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="074cb-124">상수 및 리터럴 데이터 형식</span><span class="sxs-lookup"><span data-stu-id="074cb-124">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="074cb-125">Enum 문</span><span class="sxs-lookup"><span data-stu-id="074cb-125">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
- [<span data-ttu-id="074cb-126">Imports 문(.NET 네임스페이스 및 형식)</span><span class="sxs-lookup"><span data-stu-id="074cb-126">Imports Statement (.NET Namespace and Type)</span></span>](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="074cb-127">데이터 형식</span><span class="sxs-lookup"><span data-stu-id="074cb-127">Data Types</span></span>](../../../language-reference/data-types/index.md)
