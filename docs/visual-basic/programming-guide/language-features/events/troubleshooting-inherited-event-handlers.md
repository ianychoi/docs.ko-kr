---
description: '자세한 정보: Visual Basic에서 상속 된 이벤트 처리기 문제 해결'
title: 상속된 이벤트 처리기 관련 문제 해결
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: b489b6c85510bb942b403a508b6bbe232c3e1853
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100424478"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="a99b0-103">Visual Basic에서 상속된 이벤트 처리기 관련 문제 해결</span><span class="sxs-lookup"><span data-stu-id="a99b0-103">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>

<span data-ttu-id="a99b0-104">이 항목에서는 상속 된 구성 요소의 이벤트 처리기에서 발생 하는 일반적인 문제를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-104">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a99b0-105">프로시저</span><span class="sxs-lookup"><span data-stu-id="a99b0-105">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="a99b0-106">이벤트 처리기의 코드는 모든 호출에 대해 두 번 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-106">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="a99b0-107">상속 된 이벤트 처리기에는 [Handles](../../../language-reference/statements/handles-clause.md) 절이 포함 되지 않아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-107">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="a99b0-108">기본 클래스의 메서드는 이미 이벤트와 연결 되어 있으며 그에 따라 실행 됩니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-108">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="a99b0-109">`Handles`상속 된 메서드에서 절을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-109">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="a99b0-110">상속 된 메서드에 키워드가 없는 경우 `Handles` 코드에 추가 [AddHandler 문이나](../../../language-reference/statements/addhandler-statement.md) 동일한 이벤트를 처리 하는 추가 메서드가 포함 되어 있지 않은지 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="a99b0-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a99b0-111">참조</span><span class="sxs-lookup"><span data-stu-id="a99b0-111">See also</span></span>

- [<span data-ttu-id="a99b0-112">이벤트</span><span class="sxs-lookup"><span data-stu-id="a99b0-112">Events</span></span>](index.md)
