---
description: '자세한 정보: Error 문'
title: Error 문
ms.date: 07/20/2015
f1_keywords:
- vb.error
helpviewer_keywords:
- Error statement [Visual Basic], syntax
- Error statement [Visual Basic]
- Error keyword [Visual Basic]
- run-time errors [Visual Basic], codes
- errors [Visual Basic], simulating
ms.assetid: 85cd5c59-5224-4f02-aaf5-fcfefab17a29
ms.openlocfilehash: 6c152e9e4fb4fa3a937042761c7d776b337f4fef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769145"
---
# <a name="error-statement"></a><span data-ttu-id="55e95-103">Error 문</span><span class="sxs-lookup"><span data-stu-id="55e95-103">Error Statement</span></span>

<span data-ttu-id="55e95-104">오류가 발생 한 경우를 시뮬레이션 합니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-104">Simulates the occurrence of an error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55e95-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="55e95-105">Syntax</span></span>  
  
```vb  
Error errornumber  
```  
  
## <a name="parts"></a><span data-ttu-id="55e95-106">부분</span><span class="sxs-lookup"><span data-stu-id="55e95-106">Parts</span></span>  

 `errornumber`  
 <span data-ttu-id="55e95-107">필수 사항입니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-107">Required.</span></span> <span data-ttu-id="55e95-108">모든 유효한 오류 번호가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-108">Can be any valid error number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55e95-109">설명</span><span class="sxs-lookup"><span data-stu-id="55e95-109">Remarks</span></span>  

 <span data-ttu-id="55e95-110">`Error`문은 이전 버전과의 호환성을 위해 지원 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-110">The `Error` statement is supported for backward compatibility.</span></span> <span data-ttu-id="55e95-111">새 코드에서 특히 개체를 만들 때 `Err` 개체의 메서드를 사용 `Raise` 하 여 런타임 오류를 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-111">In new code, especially when creating objects, use the `Err` object's `Raise` method to generate run-time errors.</span></span>  
  
 <span data-ttu-id="55e95-112">`errornumber`를 정의 하면 `Error` 개체의 속성에 다음 기본값이 할당 된 후에 문이 오류 처리기를 호출 합니다 `Err` .</span><span class="sxs-lookup"><span data-stu-id="55e95-112">If `errornumber` is defined, the `Error` statement calls the error handler after the properties of the `Err` object are assigned the following default values:</span></span>  
  
|<span data-ttu-id="55e95-113">속성</span><span class="sxs-lookup"><span data-stu-id="55e95-113">Property</span></span>|<span data-ttu-id="55e95-114">값</span><span class="sxs-lookup"><span data-stu-id="55e95-114">Value</span></span>|  
|--------------|-----------|  
|`Number`|<span data-ttu-id="55e95-115">문에 대 한 인수로 지정 된 값 `Error` 입니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-115">Value specified as argument to `Error` statement.</span></span> <span data-ttu-id="55e95-116">모든 유효한 오류 번호가 될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-116">Can be any valid error number.</span></span>|  
|`Source`|<span data-ttu-id="55e95-117">현재 Visual Basic 프로젝트의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-117">Name of the current Visual Basic project.</span></span>|  
|`Description`|<span data-ttu-id="55e95-118">지정 된에 대 한 함수의 반환 값에 해당 하는 문자열 식 `Error` `Number` (있는 경우)입니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-118">String expression corresponding to the return value of the `Error` function for the specified `Number`, if this string exists.</span></span> <span data-ttu-id="55e95-119">문자열이 없으면에 `Description` 길이가 0 인 문자열 ("")이 포함 됩니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-119">If the string does not exist, `Description` contains a zero-length string ("").</span></span>|  
|`HelpFile`|<span data-ttu-id="55e95-120">적절 한 Visual Basic 도움말 파일의 정규화 된 드라이브, 경로 및 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-120">The fully qualified drive, path, and file name of the appropriate Visual Basic Help file.</span></span>|  
|`HelpContext`|<span data-ttu-id="55e95-121">속성에 해당 하는 오류에 대 한 적절 한 Visual Basic 도움말 파일 컨텍스트 ID입니다 `Number` .</span><span class="sxs-lookup"><span data-stu-id="55e95-121">The appropriate Visual Basic Help file context ID for the error corresponding to the `Number` property.</span></span>|  
|`LastDLLError`|<span data-ttu-id="55e95-122">단계 없음.</span><span class="sxs-lookup"><span data-stu-id="55e95-122">Zero.</span></span>|  
  
 <span data-ttu-id="55e95-123">오류 처리기가 없거나 사용할 수 없는 경우 오류 메시지가 생성 되 고 개체 속성에서 표시 됩니다 `Err` .</span><span class="sxs-lookup"><span data-stu-id="55e95-123">If no error handler exists, or if none is enabled, an error message is created and displayed from the `Err` object properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55e95-124">일부 Visual Basic 호스트 응용 프로그램에서 개체를 만들 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-124">Some Visual Basic host applications cannot create objects.</span></span> <span data-ttu-id="55e95-125">클래스 및 개체를 만들 수 있는지 여부를 확인 하려면 호스트 응용 프로그램의 설명서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="55e95-125">See your host application's documentation to determine whether it can create classes and objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55e95-126">예제</span><span class="sxs-lookup"><span data-stu-id="55e95-126">Example</span></span>  

 <span data-ttu-id="55e95-127">이 예에서는 문을 사용 하 여 `Error` 오류 번호 11을 생성 합니다.</span><span class="sxs-lookup"><span data-stu-id="55e95-127">This example uses the `Error` statement to generate error number 11.</span></span>  
  
```vb  
On Error Resume Next   ' Defer error handling.  
Error 11   ' Simulate the "Division by zero" error.  
```  
  
## <a name="requirements"></a><span data-ttu-id="55e95-128">요구 사항</span><span class="sxs-lookup"><span data-stu-id="55e95-128">Requirements</span></span>  

 <span data-ttu-id="55e95-129">**네임 스페이스:** [microsoft.visualbasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="55e95-129">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="55e95-130">**어셈블리:** Visual Basic 런타임 라이브러리 (Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="55e95-130">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55e95-131">참고 항목</span><span class="sxs-lookup"><span data-stu-id="55e95-131">See also</span></span>

- <xref:Microsoft.VisualBasic.ErrObject.Clear%2A>
- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Raise%2A>
- [<span data-ttu-id="55e95-132">On Error 문</span><span class="sxs-lookup"><span data-stu-id="55e95-132">On Error Statement</span></span>](on-error-statement.md)
- [<span data-ttu-id="55e95-133">Resume 문</span><span class="sxs-lookup"><span data-stu-id="55e95-133">Resume Statement</span></span>](resume-statement.md)
- [<span data-ttu-id="55e95-134">오류 메시지</span><span class="sxs-lookup"><span data-stu-id="55e95-134">Error Messages</span></span>](../error-messages/index.md)
