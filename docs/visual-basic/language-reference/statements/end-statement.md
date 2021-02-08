---
description: '다음에 대 한 자세한 정보: End 문'
title: End 문
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 29e0e203689d3516a19f7e6a2b5f1c231f349ddb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769184"
---
# <a name="end-statement"></a><span data-ttu-id="d06e3-103">End 문</span><span class="sxs-lookup"><span data-stu-id="d06e3-103">End Statement</span></span>

<span data-ttu-id="d06e3-104">실행을 즉시 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-104">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d06e3-105">구문</span><span class="sxs-lookup"><span data-stu-id="d06e3-105">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="d06e3-106">설명</span><span class="sxs-lookup"><span data-stu-id="d06e3-106">Remarks</span></span>  

 <span data-ttu-id="d06e3-107">`End`프로시저의 아무 곳에 나 문을 추가 하 여 전체 응용 프로그램의 실행을 강제로 중단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-107">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="d06e3-108">`End` 문을 사용 하 여 열린 파일 `Open` 을 닫고 모든 응용 프로그램의 변수를 지웁니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-108">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="d06e3-109">응용 프로그램은 해당 개체에 대 한 참조를 보유 하는 다른 프로그램이 없고 해당 코드가 실행 되 고 있지 않은 즉시 닫힙니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-109">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d06e3-110">`End`문은 코드 실행을 갑자기 중지 하 고 `Dispose` 또는 `Finalize` 메서드 또는 다른 Visual Basic 코드를 호출 하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-110">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="d06e3-111">다른 프로그램에서 보유 하 고 있는 개체 참조는 무효화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-111">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="d06e3-112">`End`또는 블록 내에서 문이 발견 되 `Try` 면 `Catch` 컨트롤이 해당 블록에 전달 되지 않습니다 `Finally` .</span><span class="sxs-lookup"><span data-stu-id="d06e3-112">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="d06e3-113">`Stop`문은 실행을 일시 중단 하지만,와는 달리 `End` 컴파일된 실행 파일 (.exe)에서 발생 한 경우를 제외 하 고는 파일을 닫지 않거나 모든 변수를 지우지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-113">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="d06e3-114">`End`는 열려 있을 수 있는 리소스에 대해 참석 하지 않고 응용 프로그램을 종료 하기 때문에 사용 하기 전에 완전히 닫아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-114">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="d06e3-115">예를 들어 응용 프로그램에 폼이 열려 있는 경우 제어가 문에 도달 하기 전에 닫아야 합니다 `End` .</span><span class="sxs-lookup"><span data-stu-id="d06e3-115">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="d06e3-116">`End`을 즉시 중지 해야 하는 경우에만를 사용 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-116">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="d06e3-117">프로시저를 종료 하는 일반적인 방법 ([Return 문](return-statement.md) 및 [Exit 문](exit-statement.md))은 프로시저를 완전히 종료 하는 것이 아니라 호출 하는 코드를 완전히 닫을 수 있는 기회를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-117">The normal ways to terminate a procedure ([Return Statement](return-statement.md) and [Exit Statement](exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="d06e3-118">예를 들어 콘솔 응용 프로그램은 단순히 프로시저에서 수행할 수 있습니다 `Return` `Main` .</span><span class="sxs-lookup"><span data-stu-id="d06e3-118">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d06e3-119">`End`문은 <xref:System.Environment.Exit%2A> <xref:System.Environment> 네임 스페이스에 있는 클래스의 메서드를 호출 합니다 <xref:System> .</span><span class="sxs-lookup"><span data-stu-id="d06e3-119">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="d06e3-120"><xref:System.Environment.Exit%2A>`UnmanagedCode`사용 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-120"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="d06e3-121">그렇지 않으면 <xref:System.Security.SecurityException> 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-121">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="d06e3-122">그 다음에 추가 키워드가 나오면 [end \<keyword> 문은](end-keyword-statement.md) 적절 한 프로시저 또는 블록 정의의 끝을 서술 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-122">When followed by an additional keyword, [End \<keyword> Statement](end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="d06e3-123">예를 들어는 `End Function` 프로시저의 정의를 종료 `Function` 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-123">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d06e3-124">예제</span><span class="sxs-lookup"><span data-stu-id="d06e3-124">Example</span></span>  

 <span data-ttu-id="d06e3-125">다음 예제에서는 문을 사용 하 여 `End` 사용자가 요청 하는 경우 코드 실행을 종료 합니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-125">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="d06e3-126">스마트 디바이스 개발자 노트</span><span class="sxs-lookup"><span data-stu-id="d06e3-126">Smart Device Developer Notes</span></span>  

 <span data-ttu-id="d06e3-127">이 문은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d06e3-127">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06e3-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d06e3-128">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="d06e3-129">Stop 문</span><span class="sxs-lookup"><span data-stu-id="d06e3-129">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="d06e3-130">End \<keyword> 문</span><span class="sxs-lookup"><span data-stu-id="d06e3-130">End \<keyword> Statement</span></span>](end-keyword-statement.md)
