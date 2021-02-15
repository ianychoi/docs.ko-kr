---
description: '자세한 정보: 키워드를 코드에서 요소 이름으로 (Visual Basic)'
title: 코드에서 요소 이름으로 사용되는 키워드
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 4782c0f3ea065e3e140d449575c187cf2254cd08
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433215"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a><span data-ttu-id="6290c-103">코드에서 요소 이름으로 사용되는 키워드(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6290c-103">Keywords as Element Names in Code (Visual Basic)</span></span>

<span data-ttu-id="6290c-104">변수, 클래스 또는 멤버와 같은 모든 프로그램 요소는 제한 된 키워드와 동일한 이름을 가질 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-104">Any program element — such as a variable, class, or member — can have the same name as a restricted keyword.</span></span> <span data-ttu-id="6290c-105">예를 들어 라는 변수를 만들 수 있습니다 `Loop` .</span><span class="sxs-lookup"><span data-stu-id="6290c-105">For example, you can create a variable named `Loop`.</span></span> <span data-ttu-id="6290c-106">그러나 제한 된 키워드와 동일한 이름을 사용 하는 버전의를 참조 하려면 `Loop` `[ ]` 다음 예제와 같이 전체 한정 문자열로 앞에 또는 대괄호 ()로 묶어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-106">However, to refer to your version of it — which has the same name as the restricted `Loop` keyword — you must either precede it with a full qualification string or enclose it in square brackets (`[ ]`), as the following example shows.</span></span>  
  
 [!code-vb[VbVbcnConventions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#8)]  
  
 <span data-ttu-id="6290c-107">이러한 방법 중 하나를 사용 하지 않는 경우 `Loop` 다음 예제와 같이 내장 키워드를 사용 하는 것으로 가정 하 고 오류를 생성 Visual Basic 합니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-107">If you do not do either of these, then Visual Basic assumes use of the intrinsic `Loop` keyword and produces an error, as in the following example:</span></span>  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 <span data-ttu-id="6290c-108">폼 및 컨트롤을 참조 하는 경우와 변수를 선언 하거나 제한 된 키워드와 동일한 이름을 사용 하 여 프로시저를 정의 하는 경우 대괄호를 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-108">You can use square brackets when referring to forms and controls, and when declaring a variable or defining a procedure with the same name as a restricted keyword.</span></span> <span data-ttu-id="6290c-109">이름을 한정 하거나 대괄호를 포함 하는 것을 잊은 경우에는 코드에 오류를 도입 하 여 읽기 어렵게 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-109">It can be easy to forget to qualify names or include square brackets, and thus introduce errors into your code and make it harder to read.</span></span> <span data-ttu-id="6290c-110">따라서 제한 된 키워드를 program 요소의 이름으로 사용 하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-110">For this reason, we recommend that you not use restricted keywords as the names of program elements.</span></span> <span data-ttu-id="6290c-111">그러나 Visual Basic의 이후 버전에서 기존 폼 이나 컨트롤 이름과 충돌 하는 새 키워드를 정의 하는 경우 새 버전에서 사용할 코드를 업데이트할 때이 기술을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-111">However, if a future version of Visual Basic defines a new keyword that conflicts with an existing form or control name, then you can use this technique when updating your code to work with the new version.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6290c-112">또한 프로그램에는 다른 참조 된 어셈블리에서 제공 하는 요소 이름이 포함 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-112">Your program also might include element names provided by other referenced assemblies.</span></span> <span data-ttu-id="6290c-113">이러한 이름이 제한 된 키워드와 충돌 하는 경우 대괄호를 사용 하면 Visual Basic 정의 된 요소로 해석 됩니다.</span><span class="sxs-lookup"><span data-stu-id="6290c-113">If these names conflict with restricted keywords, then placing square brackets around them causes Visual Basic to interpret them as your defined elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6290c-114">추가 정보</span><span class="sxs-lookup"><span data-stu-id="6290c-114">See also</span></span>

- [<span data-ttu-id="6290c-115">Visual Basic 명명 규칙</span><span class="sxs-lookup"><span data-stu-id="6290c-115">Visual Basic Naming Conventions</span></span>](naming-conventions.md)
- [<span data-ttu-id="6290c-116">프로그램 구조 및 코드 규칙</span><span class="sxs-lookup"><span data-stu-id="6290c-116">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="6290c-117">C++ 키워드</span><span class="sxs-lookup"><span data-stu-id="6290c-117">Keywords</span></span>](../../language-reference/keywords/index.md)
