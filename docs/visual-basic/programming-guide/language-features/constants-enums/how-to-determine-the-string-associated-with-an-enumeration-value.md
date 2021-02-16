---
description: '자세한 정보: 방법: 열거형 값과 연결 된 문자열 확인 (Visual Basic)'
title: '방법: 열거형 값과 연결된 문자열 확인'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 391cb097fa8163f7131cc30f85f8a4f85ba826a4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471606"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="b065c-103">방법: 열거형 값과 연결된 문자열 확인(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b065c-103">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>

<span data-ttu-id="b065c-104"><xref:System.Enum.GetValues%2A>및 메서드를 사용 하 여 <xref:System.Enum.GetNames%2A> 열거형 멤버와 연결 된 문자열 및 값을 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="b065c-104">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="b065c-105">열거형과 연결 된 문자열을 확인 하려면</span><span class="sxs-lookup"><span data-stu-id="b065c-105">To determine the string associated with an enumeration</span></span>  
  
- <span data-ttu-id="b065c-106">메서드를 사용 <xref:System.Enum.GetNames%2A> 하 여 열거형 멤버와 연결 된 문자열을 검색 합니다.</span><span class="sxs-lookup"><span data-stu-id="b065c-106">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="b065c-107">이 예제에서는 열거형를 선언한 `flavorEnum` 다음 메서드를 사용 하 여 <xref:System.Enum.GetNames%2A> 각 멤버와 관련 된 문자열을 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="b065c-107">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b065c-108">추가 정보</span><span class="sxs-lookup"><span data-stu-id="b065c-108">See also</span></span>

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [<span data-ttu-id="b065c-109">방법: 열거형 선언</span><span class="sxs-lookup"><span data-stu-id="b065c-109">How to: Declare an Enumeration</span></span>](how-to-declare-enumerations.md)
- [<span data-ttu-id="b065c-110">방법: 열거형 멤버 참조</span><span class="sxs-lookup"><span data-stu-id="b065c-110">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="b065c-111">열거형 및 이름 한정</span><span class="sxs-lookup"><span data-stu-id="b065c-111">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="b065c-112">방법: Visual Basic에서 열거형 반복</span><span class="sxs-lookup"><span data-stu-id="b065c-112">How to: Iterate Through An Enumeration in Visual Basic</span></span>](how-to-iterate-through-an-enumeration.md)
- [<span data-ttu-id="b065c-113">열거형을 사용하는 경우</span><span class="sxs-lookup"><span data-stu-id="b065c-113">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="b065c-114">Enum 문</span><span class="sxs-lookup"><span data-stu-id="b065c-114">Enum Statement</span></span>](../../../language-reference/statements/enum-statement.md)
