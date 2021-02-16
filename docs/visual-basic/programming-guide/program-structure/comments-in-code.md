---
description: '자세한 정보: 코드 주석 (Visual Basic)'
title: 코드 주석
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 66e12a18c2532bb5b694affccb84153f01bcddd5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461933"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="50850-103">코드 주석(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50850-103">Comments in Code (Visual Basic)</span></span>

<span data-ttu-id="50850-104">코드 예제를 읽다 보면 종종 주석 기호(`'`)를 보게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50850-104">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="50850-105">이 기호는 Visual Basic 컴파일러가 뒤에 나오는 텍스트 또는 *주석을* 무시 하도록 지시 합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-105">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="50850-106">주석이란 해당 코드를 읽을 사람의 편의를 위해 코드에 추가되는 간단한 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="50850-106">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="50850-107">모든 프로시저를 시작할 때 프로시저의 기능적 특징, 즉 해당 프로시저가 수행하는 작업에 대한 간단한 주석을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-107">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="50850-108">이는 사용자 자신이나 코드를 보게 될 다른 사용자를 위한 것입니다.</span><span class="sxs-lookup"><span data-stu-id="50850-108">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="50850-109">프로시저의 구현 방식 등 구현에 대한 자세한 정보는 기능적 특징을 설명하는 주석과 분리되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-109">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="50850-110">이 정보를 설명하는 부분에 포함시킨 경우에는 함수를 업데이트할 때 이 정보도 업데이트해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-110">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="50850-111">주석은 문과 같은 줄에서 문 다음에 나올 수도 있고 한 줄을 차지할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-111">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="50850-112">다음 코드에서는 이 두 가지 경우를 모두 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50850-112">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="50850-113">주석에 둘 이상의 줄이 필요하면 다음 예제와 같이 각 줄에 주석 기호를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="50850-114">주석 지침</span><span class="sxs-lookup"><span data-stu-id="50850-114">Commenting Guidelines</span></span>  

 <span data-ttu-id="50850-115">다음 표에서는 코드 부분의 앞에 올 수 있는 주석의 종류에 대한 일반적인 지침을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="50850-115">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="50850-116">제안 사항은 다음과 같습니다. Visual Basic은 주석을 추가 하는 규칙을 적용 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-116">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="50850-117">사용자 자신이나 해당 코드를 읽을 다른 모든 사용자에게 적합하도록 주석을 쓰면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="50850-117">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="50850-118">주석 형식</span><span class="sxs-lookup"><span data-stu-id="50850-118">Comment type</span></span>|<span data-ttu-id="50850-119">주석 설명</span><span class="sxs-lookup"><span data-stu-id="50850-119">Comment description</span></span>|  
|<span data-ttu-id="50850-120">용도</span><span class="sxs-lookup"><span data-stu-id="50850-120">Purpose</span></span>|<span data-ttu-id="50850-121">프로시저의 작업 수행 방식이 아니라 해당 프로시저에서 수행하는 작업에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-121">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="50850-122">Assumptions</span><span class="sxs-lookup"><span data-stu-id="50850-122">Assumptions</span></span>|<span data-ttu-id="50850-123">프로시저에서 액세스하는 외부 변수, 컨트롤, 열린 파일 또는 기타 요소를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-123">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="50850-124">효과</span><span class="sxs-lookup"><span data-stu-id="50850-124">Effects</span></span>|<span data-ttu-id="50850-125">영향을 받은 외부 변수, 컨트롤 또는 파일을 나열하고, 분명하지 않은 경우에는 그 효과를 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-125">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="50850-126">입력</span><span class="sxs-lookup"><span data-stu-id="50850-126">Inputs</span></span>|<span data-ttu-id="50850-127">인수의 용도를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-127">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="50850-128">반환</span><span class="sxs-lookup"><span data-stu-id="50850-128">Returns</span></span>|<span data-ttu-id="50850-129">프로시저에 의해 반환된 값에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-129">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="50850-130">다음은 주의해야 할 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="50850-130">Remember the following points:</span></span>  
  
- <span data-ttu-id="50850-131">중요한 모든 변수 선언에는 선언되는 변수의 용도에 대해 설명하는 주석이 앞에 와야 합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-131">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="50850-132">변수, 컨트롤 및 프로시저의 이름은 쉽게 알 수 있는 이름으로 지정하며, 복잡한 구현에 대해 자세히 설명하는 경우에만 주석을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="50850-132">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="50850-133">줄 연속 시퀀스를 사용한 후에는 같은 줄에 주석을 쓸 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-133">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="50850-134">코드 줄을 하나 이상 선택 하 고 **주석** ( ![ visual Studio의 Visual Basic 주석 단추)을 선택 하 ](./media/comments-in-code/visual-basic-comment-button.gif) 고  ![ ](./media/comments-in-code/visual-basic-uncomment-button.gif) **편집** 도구 모음에서 주석 처리를 제거 (visual studio의 Visual Basic 주석 제거 단추) 하는 방법으로 코드 블록의 주석 기호를 추가 하거나 제거할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-134">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50850-135">`REM` 키워드로 텍스트를 시작하여 코드에 주석을 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-135">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="50850-136">그러나 `'` 기호 및 **주석** / **주석 처리** 되지 않은 단추는 사용 하기 쉬우며 공간 및 메모리를 줄일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="50850-136">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50850-137">추가 정보</span><span class="sxs-lookup"><span data-stu-id="50850-137">See also</span></span>

- [<span data-ttu-id="50850-138">Basic 직감-XML 주석을 사용 하 여 코드 문서화</span><span class="sxs-lookup"><span data-stu-id="50850-138">Basic Instincts - Documenting Your Code With XML Comments</span></span>](/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="50850-139">방법: XML 설명서 만들기</span><span class="sxs-lookup"><span data-stu-id="50850-139">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="50850-140">XML 주석 태그</span><span class="sxs-lookup"><span data-stu-id="50850-140">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="50850-141">프로그램 구조 및 코드 규칙</span><span class="sxs-lookup"><span data-stu-id="50850-141">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="50850-142">REM 문</span><span class="sxs-lookup"><span data-stu-id="50850-142">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
