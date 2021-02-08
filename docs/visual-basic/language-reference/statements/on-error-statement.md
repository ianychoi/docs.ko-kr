---
description: '자세한 정보: On Error 문 (Visual Basic)'
title: On Error 문
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 593e90b07101d08d18a0db127bcb74cf6509f317
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768833"
---
# <a name="on-error-statement-visual-basic"></a><span data-ttu-id="9aa58-103">On Error 문(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9aa58-103">On Error Statement (Visual Basic)</span></span>

<span data-ttu-id="9aa58-104">오류 처리 루틴을 사용 하도록 설정 하 고 프로시저 내에서 루틴의 위치를 지정 합니다. 를 사용 하 여 오류 처리 루틴을 사용 하지 않도록 설정할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-104">Enables an error-handling routine and specifies the location of the routine within a procedure; can also be used to disable an error-handling routine.</span></span> <span data-ttu-id="9aa58-105">`On Error`문은 비구조적 오류 처리에 사용 되며 구조적 예외 처리 대신 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-105">The `On Error` statement is used in unstructured error handling and can be used instead of structured exception handling.</span></span> <span data-ttu-id="9aa58-106">[구조적 예외 처리](../../../standard/exceptions/index.md) 는 .net에 기본 제공 되며, 일반적으로 더 효율적 이므로 응용 프로그램에서 런타임 오류를 처리할 때 권장 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-106">[Structured exception handling](../../../standard/exceptions/index.md) is built into .NET, is generally more efficient, and so is recommended when handling runtime errors in your application.</span></span>

 <span data-ttu-id="9aa58-107">오류 처리 또는 예외 처리를 사용 하지 않을 경우 발생 하는 런타임 오류는 심각한 오류입니다. 오류 메시지가 표시 되 고 실행이 중지 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-107">Without error handling or exception handling, any run-time error that occurs is fatal: an error message is displayed, and execution stops.</span></span>

> [!NOTE]
> <span data-ttu-id="9aa58-108">`Error`키워드는 이전 버전과의 호환성을 위해 지원 되는 [오류 문에서](error-statement.md)도 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-108">The `Error` keyword is also used in the [Error Statement](error-statement.md), which is supported for backward compatibility.</span></span>

## <a name="syntax"></a><span data-ttu-id="9aa58-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="9aa58-109">Syntax</span></span>

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a><span data-ttu-id="9aa58-110">부분</span><span class="sxs-lookup"><span data-stu-id="9aa58-110">Parts</span></span>

|<span data-ttu-id="9aa58-111">용어</span><span class="sxs-lookup"><span data-stu-id="9aa58-111">Term</span></span>|<span data-ttu-id="9aa58-112">정의</span><span class="sxs-lookup"><span data-stu-id="9aa58-112">Definition</span></span>|
|---|---|
|<span data-ttu-id="9aa58-113">`GoTo`*줄*</span><span class="sxs-lookup"><span data-stu-id="9aa58-113">`GoTo` *line*</span></span>|<span data-ttu-id="9aa58-114">필요한 *줄* 인수에 지정 된 줄에서 시작 하는 오류 처리 루틴을 사용 하도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-114">Enables the error-handling routine that starts at the line specified in the required *line* argument.</span></span> <span data-ttu-id="9aa58-115">*줄* 인수는 줄 레이블이나 줄 번호입니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-115">The *line* argument is any line label or line number.</span></span> <span data-ttu-id="9aa58-116">런타임 오류가 발생 하는 경우 지정 된 줄로 분기를 제어 하 여 오류 처리기를 활성화 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-116">If a run-time error occurs, control branches to the specified line, making the error handler active.</span></span> <span data-ttu-id="9aa58-117">지정 된 줄은 문과 같은 프로시저에 `On Error` 있거나 컴파일 타임 오류가 발생 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-117">The specified line must be in the same procedure as the `On Error` statement or a compile-time error will occur.</span></span>|
|`GoTo 0`|<span data-ttu-id="9aa58-118">현재 프로시저에서 활성화 된 오류 처리기를 비활성화 하 고로 다시 설정 `Nothing` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-118">Disables enabled error handler in the current procedure and resets it to `Nothing`.</span></span>|
|`GoTo -1`|<span data-ttu-id="9aa58-119">현재 프로시저에서 활성화 된 예외를 비활성화 하 고로 다시 설정 `Nothing` 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-119">Disables enabled exception in the current procedure and resets it to `Nothing`.</span></span>|
|`Resume Next`|<span data-ttu-id="9aa58-120">런타임 오류가 발생할 때 제어가 오류가 발생 한 문 바로 다음에 오는 문으로 이동 하 고 해당 지점에서 실행이 계속 되도록 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-120">Specifies that when a run-time error occurs, control goes to the statement immediately following the statement where the error occurred, and execution continues from that point.</span></span> <span data-ttu-id="9aa58-121">`On Error GoTo`개체에 액세스할 때가 아닌이 폼을 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-121">Use this form rather than `On Error GoTo` when accessing objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9aa58-122">설명</span><span class="sxs-lookup"><span data-stu-id="9aa58-122">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="9aa58-123">구조화 되지 않은 예외 처리 및 문을 사용 하는 대신 가능한 경우 코드에서 구조적 예외 처리를 사용 하는 것이 좋습니다 `On Error` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-123">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` statement.</span></span> <span data-ttu-id="9aa58-124">자세한 내용은 [Try...Catch...Finally 문](try-catch-finally-statement.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9aa58-124">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>

 <span data-ttu-id="9aa58-125">"활성화 된" 오류 처리기는 문에 의해 설정 되는 오류 처리기입니다 `On Error` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-125">An "enabled" error handler is one that is turned on by an `On Error` statement.</span></span> <span data-ttu-id="9aa58-126">"활성" 오류 처리기는 오류를 처리 하는 프로세스에 있는 활성화 된 처리기입니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-126">An "active" error handler is an enabled handler that is in the process of handling an error.</span></span>

 <span data-ttu-id="9aa58-127">오류 처리기가 활성화 되어 있는 동안 오류가 발생 하는 경우 (오류 발생과 `Resume` ,, `Exit Sub` `Exit Function` 또는 `Exit Property` 문 사이) 현재 프로시저의 오류 처리기에서 오류를 처리할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-127">If an error occurs while an error handler is active (between the occurrence of the error and a `Resume`, `Exit Sub`, `Exit Function`, or `Exit Property` statement), the current procedure's error handler cannot handle the error.</span></span> <span data-ttu-id="9aa58-128">호출 하는 프로시저로 제어가 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-128">Control returns to the calling procedure.</span></span>
  
 <span data-ttu-id="9aa58-129">호출 하는 프로시저에 활성화 된 오류 처리기가 있으면 오류를 처리 하도록 활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-129">If the calling procedure has an enabled error handler, it is activated to handle the error.</span></span> <span data-ttu-id="9aa58-130">호출 하는 프로시저의 오류 처리기도 활성 상태인 경우에는 사용 되지만 비활성화 된 오류 처리기가 발견 될 때까지 이전 호출 프로시저를 통해 제어가 다시 전달 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-130">If the calling procedure's error handler is also active, control passes back through previous calling procedures until an enabled, but inactive, error handler is found.</span></span> <span data-ttu-id="9aa58-131">이러한 오류 처리기를 찾을 수 없는 경우 오류는 실제로 발생 한 지점에서 치명적입니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-131">If no such error handler is found, the error is fatal at the point at which it actually occurred.</span></span>
  
 <span data-ttu-id="9aa58-132">오류 처리기가 호출 프로시저로 제어를 다시 전달할 때마다 해당 프로시저는 현재 프로시저가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-132">Each time the error handler passes control back to a calling procedure, that procedure becomes the current procedure.</span></span> <span data-ttu-id="9aa58-133">프로시저의 오류 처리기에서 오류를 처리 한 후에는 문에 지정 된 지점에서 현재 프로시저의 실행이 다시 시작 됩니다 `Resume` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-133">Once an error is handled by an error handler in any procedure, execution resumes in the current procedure at the point designated by the `Resume` statement.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9aa58-134">오류 처리 루틴은 `Sub` 프로시저 또는 `Function` 프로시저가 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-134">An error-handling routine is not a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="9aa58-135">줄 레이블이나 줄 번호로 표시 되는 코드 섹션입니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-135">It is a section of code marked by a line label or a line number.</span></span>
  
## <a name="number-property"></a><span data-ttu-id="9aa58-136">Number 속성</span><span class="sxs-lookup"><span data-stu-id="9aa58-136">Number Property</span></span>

 <span data-ttu-id="9aa58-137">오류 처리 루틴은 개체의 속성 값을 사용 `Number` 하 여 오류의 `Err` 원인을 확인 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-137">Error-handling routines rely on the value in the `Number` property of the `Err` object to determine the cause of the error.</span></span> <span data-ttu-id="9aa58-138">루틴은 `Err` 다른 오류가 발생 하기 전이나 오류를 발생 시킬 수 있는 프로시저를 호출 하기 전에 개체의 관련 속성 값을 테스트 하거나 저장 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-138">The routine should test or save relevant property values in the `Err` object before any other error can occur or before a procedure that might cause an error is called.</span></span> <span data-ttu-id="9aa58-139">개체의 속성 값에는 `Err` 가장 최근의 오류만 반영 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-139">The property values in the `Err` object reflect only the most recent error.</span></span> <span data-ttu-id="9aa58-140">와 관련 된 오류 메시지는 `Err.Number` 에 포함 되어 `Err.Description` 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-140">The error message associated with `Err.Number` is contained in `Err.Description`.</span></span>  
  
## <a name="throw-statement"></a><span data-ttu-id="9aa58-141">Throw 문</span><span class="sxs-lookup"><span data-stu-id="9aa58-141">Throw Statement</span></span>  

 <span data-ttu-id="9aa58-142">메서드에서 발생 하는 오류는 `Err.Raise` `Exception` 속성을 클래스의 새로 만든 인스턴스로 설정 합니다 <xref:System.Exception> .</span><span class="sxs-lookup"><span data-stu-id="9aa58-142">An error that is raised with the `Err.Raise` method sets the `Exception` property to a newly created instance of the <xref:System.Exception> class.</span></span> <span data-ttu-id="9aa58-143">파생 된 예외 형식의 예외 발생을 지원 하기 위해 `Throw` 문은 언어로 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-143">In order to support the raising of exceptions of derived exception types, a `Throw` statement is supported in the language.</span></span> <span data-ttu-id="9aa58-144">이는 throw 되는 예외 인스턴스인 단일 매개 변수를 사용 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-144">This takes a single parameter that is the exception instance to be thrown.</span></span> <span data-ttu-id="9aa58-145">다음 예제에서는 기존 예외 처리 지원과 함께 이러한 기능을 사용할 수 있는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-145">The following example shows how these features can be used with the existing exception handling support:</span></span>

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 <span data-ttu-id="9aa58-146">`On Error GoTo`문은 예외 클래스에 관계 없이 모든 오류를 트래핑 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-146">Notice that the `On Error GoTo` statement traps all errors, regardless of the exception class.</span></span>
  
## <a name="on-error-resume-next"></a><span data-ttu-id="9aa58-147">오류 다시 시작 다음</span><span class="sxs-lookup"><span data-stu-id="9aa58-147">On Error Resume Next</span></span>

 <span data-ttu-id="9aa58-148">`On Error Resume Next` 실행 시 오류가 발생 한 문 바로 다음에 오는 문을 실행 하거나 문을 포함 하는 프로시저에서 가장 최근의 호출 바로 다음에 오는 문으로 실행을 계속 합니다 `On Error Resume Next` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-148">`On Error Resume Next` causes execution to continue with the statement immediately following the statement that caused the run-time error, or with the statement immediately following the most recent call out of the procedure containing the `On Error Resume Next` statement.</span></span> <span data-ttu-id="9aa58-149">이 문을 사용 하면 런타임 오류에도 불구 하 고 실행을 계속할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-149">This statement allows execution to continue despite a run-time error.</span></span> <span data-ttu-id="9aa58-150">프로시저 내의 다른 위치로 제어를 전송 하는 대신 오류가 발생 하는 오류 처리 루틴을 저장할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-150">You can place the error-handling routine where the error would occur rather than transferring control to another location within the procedure.</span></span> <span data-ttu-id="9aa58-151">`On Error Resume Next`다른 프로시저가 호출 될 때 문이 비활성화 되므로 `On Error Resume Next` 해당 루틴 내에서 인라인 오류를 처리 하려는 경우 호출 된 각 루틴에서 문을 실행 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-151">An `On Error Resume Next` statement becomes inactive when another procedure is called, so you should execute an `On Error Resume Next` statement in each called routine if you want inline error handling within that routine.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9aa58-152">합니다 `On Error Resume Next` 구문에 더 적합할 수 있습니다 `On Error GoTo` 다른 개체에 액세스 하는 동안 발생 한 오류를 처리 하는 경우.</span><span class="sxs-lookup"><span data-stu-id="9aa58-152">The `On Error Resume Next` construct may be preferable to `On Error GoTo` when handling errors generated during access to other objects.</span></span> <span data-ttu-id="9aa58-153">`Err`개체와의 각 상호 작용 후에 확인 하면 코드에서 액세스 된 개체에 대 한 모호성을 제거 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-153">Checking `Err` after each interaction with an object removes ambiguity about which object was accessed by the code.</span></span> <span data-ttu-id="9aa58-154">오류 코드를 배치 하는 개체와 `Err.Number` 원래 오류를 생성 한 개체 (에 지정 된 개체)를 확인할 수 있습니다 `Err.Source` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-154">You can be sure which object placed the error code in `Err.Number`, as well as which object originally generated the error (the object specified in `Err.Source`).</span></span>

## <a name="on-error-goto-0"></a><span data-ttu-id="9aa58-155">On Error GoTo 0</span><span class="sxs-lookup"><span data-stu-id="9aa58-155">On Error GoTo 0</span></span>

 <span data-ttu-id="9aa58-156">`On Error GoTo 0` 현재 프로시저에서 오류 처리를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-156">`On Error GoTo 0` disables error handling in the current procedure.</span></span> <span data-ttu-id="9aa58-157">오류 처리 코드의 시작으로 줄 0을 지정 하지 않습니다. 프로시저에 번호가 0 인 줄이 포함 된 경우에도 마찬가지입니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-157">It doesn't specify line 0 as the start of the error-handling code, even if the procedure contains a line numbered 0.</span></span> <span data-ttu-id="9aa58-158">문이 없으면 `On Error GoTo 0` 프로시저 종료 시 오류 처리기가 자동으로 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-158">Without an `On Error GoTo 0` statement, an error handler is automatically disabled when a procedure is exited.</span></span>

## <a name="on-error-goto--1"></a><span data-ttu-id="9aa58-159">On Error GoTo-1</span><span class="sxs-lookup"><span data-stu-id="9aa58-159">On Error GoTo -1</span></span>

 <span data-ttu-id="9aa58-160">`On Error GoTo -1` 현재 프로시저에서 예외를 사용 하지 않도록 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-160">`On Error GoTo -1` disables the exception in the current procedure.</span></span> <span data-ttu-id="9aa58-161">프로시저에-1로 번호가 지정 된 줄이 포함 된 경우에도 줄 1은 오류 처리 코드의 시작으로 지정 되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-161">It does not specify line -1 as the start of the error-handling code, even if the procedure contains a line numbered -1.</span></span> <span data-ttu-id="9aa58-162">문이 없으면 `On Error GoTo -1` 프로시저를 종료할 때 예외가 자동으로 비활성화 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-162">Without an `On Error GoTo -1` statement, an exception is automatically disabled when a procedure is exited.</span></span>

 <span data-ttu-id="9aa58-163">오류가 발생 하지 않은 경우 오류 처리 코드가 실행 되지 않도록 하려면 `Exit Sub` `Exit Function` `Exit Property` 다음 조각과 같이 오류 처리 루틴 바로 앞에, 또는 문을 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-163">To prevent error-handling code from running when no error has occurred, place an `Exit Sub`, `Exit Function`, or `Exit Property` statement immediately before the error-handling routine, as in the following fragment:</span></span>

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 <span data-ttu-id="9aa58-164">여기에서 오류 처리 코드는 문 뒤에 오는 `Exit Sub` `End Sub` 문 앞에 프로시저 흐름과 구분 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-164">Here, the error-handling code follows the `Exit Sub` statement and precedes the `End Sub` statement to separate it from the procedure flow.</span></span> <span data-ttu-id="9aa58-165">프로시저의 아무 곳에 나 오류 처리 코드를 넣을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-165">You can place error-handling code anywhere in a procedure.</span></span>

## <a name="untrapped-errors"></a><span data-ttu-id="9aa58-166">포착 되지 않은 오류</span><span class="sxs-lookup"><span data-stu-id="9aa58-166">Untrapped Errors</span></span>

 <span data-ttu-id="9aa58-167">개체를 실행 파일로 실행 하는 경우 개체의 포착 되지 않은 오류는 제어 응용 프로그램으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-167">Untrapped errors in objects are returned to the controlling application when the object is running as an executable file.</span></span> <span data-ttu-id="9aa58-168">개발 환경 내에서 적절 한 옵션이 설정 된 경우에만 포착 되지 않은 오류가 제어 응용 프로그램으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-168">Within the development environment, untrapped errors are returned to the controlling application only if the proper options are set.</span></span> <span data-ttu-id="9aa58-169">디버깅 중에 설정 해야 하는 옵션에 대 한 설명, 설정 하는 방법 및 호스트가 클래스를 만들 수 있는지 여부는 호스트 응용 프로그램의 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="9aa58-169">See your host application's documentation for a description of which options should be set during debugging, how to set them, and whether the host can create classes.</span></span>

 <span data-ttu-id="9aa58-170">다른 개체에 액세스 하는 개체를 만드는 경우 다시 전달 되는 처리 되지 않은 오류를 처리 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-170">If you create an object that accesses other objects, you should try to handle any unhandled errors they pass back.</span></span> <span data-ttu-id="9aa58-171">사용할 수 없는 경우의 오류 코드를 `Err.Number` 고유한 오류 중 하나에 매핑한 다음 개체의 호출자에 게 다시 전달 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-171">If you cannot, map the error codes in `Err.Number` to one of your own errors and then pass them back to the caller of your object.</span></span> <span data-ttu-id="9aa58-172">상수에 오류 코드를 추가 하 여 오류를 지정 해야 합니다 `VbObjectError` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-172">You should specify your error by adding your error code to the `VbObjectError` constant.</span></span> <span data-ttu-id="9aa58-173">예를 들어 오류 코드가 1052 인 경우 다음과 같이 할당 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-173">For example, if your error code is 1052, assign it as follows:</span></span>

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> <span data-ttu-id="9aa58-174">Windows Dll (동적 연결 라이브러리)을 호출 하는 동안 발생 하는 시스템 오류는 예외를 발생 시 키 지 않으며 Visual Basic 오류 트래핑으로 트랩할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-174">System errors during calls to Windows dynamic-link libraries (DLLs) do not raise exceptions and cannot be trapped with Visual Basic error trapping.</span></span> <span data-ttu-id="9aa58-175">DLL 함수를 호출 하는 경우 각 반환 값에 성공 또는 실패 (API 사양에 따라)를 확인 하 고, 실패 시 개체의 속성에서 값을 확인 해야 합니다 `Err` `LastDLLError` .</span><span class="sxs-lookup"><span data-stu-id="9aa58-175">When calling DLL functions, you should check each return value for success or failure (according to the API specifications), and in the event of a failure, check the value in the `Err` object's `LastDLLError` property.</span></span>

## <a name="example"></a><span data-ttu-id="9aa58-176">예제</span><span class="sxs-lookup"><span data-stu-id="9aa58-176">Example</span></span>

 <span data-ttu-id="9aa58-177">이 예에서는 먼저 문을 사용 하 여 `On Error GoTo` 프로시저 내에서 오류 처리 루틴의 위치를 지정 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-177">This example first uses the `On Error GoTo` statement to specify the location of an error-handling routine within a procedure.</span></span> <span data-ttu-id="9aa58-178">이 예에서는 0으로 나누려고 시도 하면 오류 번호 6이 생성 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-178">In the example, an attempt to divide by zero generates error number 6.</span></span> <span data-ttu-id="9aa58-179">오류는 오류 처리 루틴에서 처리 되 고 컨트롤은 오류를 발생 시킨 문으로 반환 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-179">The error is handled in the error-handling routine, and control is then returned to the statement that caused the error.</span></span> <span data-ttu-id="9aa58-180">`On Error GoTo 0`문은 오류 트래핑을 해제 합니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-180">The `On Error GoTo 0` statement turns off error trapping.</span></span> <span data-ttu-id="9aa58-181">그런 다음 `On Error Resume Next` 문을 사용 하 여 다음 문에 의해 생성 된 오류에 대 한 컨텍스트를 특정에 대해 알 수 있도록 오류 트래핑을 지연 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-181">Then the `On Error Resume Next` statement is used to defer error trapping so that the context for the error generated by the next statement can be known for certain.</span></span> <span data-ttu-id="9aa58-182">는 `Err.Clear` `Err` 오류를 처리 한 후 개체의 속성을 지우는 데 사용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9aa58-182">Note that `Err.Clear` is used to clear the `Err` object's properties after the error is handled.</span></span>

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a><span data-ttu-id="9aa58-183">요구 사항</span><span class="sxs-lookup"><span data-stu-id="9aa58-183">Requirements</span></span>

 <span data-ttu-id="9aa58-184">**네임 스페이스:** [microsoft.visualbasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="9aa58-184">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>

 <span data-ttu-id="9aa58-185">**어셈블리:** Visual Basic 런타임 라이브러리 (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="9aa58-185">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>

## <a name="see-also"></a><span data-ttu-id="9aa58-186">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9aa58-186">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [<span data-ttu-id="9aa58-187">End 문</span><span class="sxs-lookup"><span data-stu-id="9aa58-187">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="9aa58-188">Exit 문</span><span class="sxs-lookup"><span data-stu-id="9aa58-188">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="9aa58-189">Resume 문</span><span class="sxs-lookup"><span data-stu-id="9aa58-189">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="9aa58-190">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="9aa58-190">Error Messages</span></span>](../error-messages/index.md)
- [<span data-ttu-id="9aa58-191">Try...Catch...Finally 문</span><span class="sxs-lookup"><span data-stu-id="9aa58-191">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
