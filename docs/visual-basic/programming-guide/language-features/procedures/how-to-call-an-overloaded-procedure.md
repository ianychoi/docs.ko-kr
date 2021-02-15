---
description: '자세한 정보: 방법: 오버 로드 된 프로시저 호출 (Visual Basic)'
title: '방법: 오버로드된 프로시저 호출'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], calling
- procedures [Visual Basic], multiple versions
- procedure calls [Visual Basic], overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
ms.openlocfilehash: 6a67a598bd4a42964fd8fc01bc22b1b919f5e2a9
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100472594"
---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="be505-103">방법: 오버로드된 프로시저 호출(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="be505-103">How to: Call an Overloaded Procedure (Visual Basic)</span></span>

<span data-ttu-id="be505-104">프로시저 오버 로드의 이점은 호출의 유연성을 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-104">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="be505-105">호출 하는 코드는 프로시저에 전달 하는 데 필요한 정보를 얻은 다음 전달 하는 인수에 관계 없이 단일 프로시저 이름을 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="be505-105">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="be505-106">정의 된 버전이 둘 이상 있는 프로시저를 호출 하려면</span><span class="sxs-lookup"><span data-stu-id="be505-106">To call a procedure that has more than one version defined</span></span>  
  
1. <span data-ttu-id="be505-107">호출 코드에서 프로시저에 전달할 데이터를 결정 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-107">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2. <span data-ttu-id="be505-108">일반적인 방법으로 프로시저 호출을 작성 하 여 인수 목록에 데이터를 표시 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-108">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="be505-109">인수는 프로시저에 대해 정의 된 버전 중 하나의 매개 변수 목록과 일치 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-109">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3. <span data-ttu-id="be505-110">호출할 프로시저 버전을 결정할 필요가 없습니다.</span><span class="sxs-lookup"><span data-stu-id="be505-110">You do not have to determine which version of the procedure to call.</span></span> <span data-ttu-id="be505-111">Visual Basic는 인수 목록과 일치 하는 버전으로 제어를 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-111">Visual Basic passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="be505-112">다음 예에서는 `post` [방법: 여러 버전의 프로시저 정의](./how-to-define-multiple-versions-of-a-procedure.md)에 선언 된 프로시저를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-112">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="be505-113">고객 식별을 가져오고, 인지 여부를 확인 한 `String` `Integer` 다음 두 경우 모두 동일한 프로시저를 호출 합니다.</span><span class="sxs-lookup"><span data-stu-id="be505-113">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
     [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a><span data-ttu-id="be505-114">추가 정보</span><span class="sxs-lookup"><span data-stu-id="be505-114">See also</span></span>

- [<span data-ttu-id="be505-115">절차</span><span class="sxs-lookup"><span data-stu-id="be505-115">Procedures</span></span>](./index.md)
- [<span data-ttu-id="be505-116">프로시저 매개 변수 및 인수</span><span class="sxs-lookup"><span data-stu-id="be505-116">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="be505-117">프로시저 오버로딩</span><span class="sxs-lookup"><span data-stu-id="be505-117">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="be505-118">프로시저 문제 해결</span><span class="sxs-lookup"><span data-stu-id="be505-118">Troubleshooting Procedures</span></span>](./troubleshooting-procedures.md)
- [<span data-ttu-id="be505-119">방법: 여러 버전의 프로시저 정의</span><span class="sxs-lookup"><span data-stu-id="be505-119">How to: Define Multiple Versions of a Procedure</span></span>](./how-to-define-multiple-versions-of-a-procedure.md)
- [<span data-ttu-id="be505-120">방법: 선택적 매개 변수를 사용하는 프로시저 오버로드</span><span class="sxs-lookup"><span data-stu-id="be505-120">How to: Overload a Procedure that Takes Optional Parameters</span></span>](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [<span data-ttu-id="be505-121">방법: 매개 변수를 무제한으로 사용하는 프로시저 오버로드</span><span class="sxs-lookup"><span data-stu-id="be505-121">How to: Overload a Procedure that Takes an Indefinite Number of Parameters</span></span>](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [<span data-ttu-id="be505-122">프로시저 오버로드에서 고려해야 할 사항</span><span class="sxs-lookup"><span data-stu-id="be505-122">Considerations in Overloading Procedures</span></span>](./considerations-in-overloading-procedures.md)
- [<span data-ttu-id="be505-123">Overload Resolution</span><span class="sxs-lookup"><span data-stu-id="be505-123">Overload Resolution</span></span>](./overload-resolution.md)
- [<span data-ttu-id="be505-124">오버로드</span><span class="sxs-lookup"><span data-stu-id="be505-124">Overloads</span></span>](../../../language-reference/modifiers/overloads.md)
